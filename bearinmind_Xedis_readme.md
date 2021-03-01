#Xedis

-------------

**Xedis**是一个内存kv数据库


你可曾觉得：

    - redis的Keys命令性能太低？

    - DEL命令不够好用、不支持pattern？

    - 支持的数据结构太少，不能满足业务需求？

等等各种不尽如人意、不够契合业务场景的问题。是组合多种不同数据结构最后勉强满足业务需求，还是变更业务形态使之契合redis？都不如定制化来的靠谱。

* 核心功能

Xedis就是用来解决这种**不够契合**的问题的，Xedis在数据结构(项目中称为Structures)、命令(Cmd)、Key的组织方式(项目中称为View)三个维度上提供了非常简单的扩展方法，只要用户懂一点点golang的语法即可（从零学golang语法通常只需要花费1-3个小时的学习时间）。

* 默认兼容redis协议，便于使用。

在通信协议(默认使用redis协议)、通信方式(默认使用TCP)上都保留了扩展性。

目前，实现了两种通信协议：simple协议(一个简单的字符协议, 可以使用telnet交互)和redis协议(提供二进制读写功能)

## 获取Xedis包

  go get git.oschina.net/yyzybb537/Xedis

## 编译&安装

  cd $GOPATH/src/https://git.oschina.net/yyzybb537/Xedis.git

  ./build.sh

## 启动Xedis服务端

```
  // 启动Xedis监听8030端口
  $ ./Xedis
  $ ./Xedis -L ":8030"

  // 启动Xedis监听回环网卡的8030端口
  $ ./Xedis -L "127.0.0.1:8030"

  // 更多启动参数请看help手册
  $ ./Xedis -h

  // 命令帮助手册, 可以显示所有当前支持的命令、数据结构、协议、通信方式、View
  $ ./Xedis -D
```

## 使用Xedis客户端

Xedis有3种client：Xedis自带的golang客户端、 任一语言的redis客户端、 redis-cli/telnet命令行工具，后续还会提供xedis专属的命令行工具。

推荐使用Xedis自带的golang客户端，因为每一个自定义的命令在build之后都会生成相应格式的接口，并且可以使用代码补全工具来给出补全提示。

* Example1：单链接的使用方式

```
package main

import (
        xedis "git.oschina.net/yyzybb537/Xedis/client"
        "fmt"
)

func main() {
        // 连接Xedis
        c, err := xedis.Dial("127.0.0.1:8030")
        if err != nil {
                fmt.Printf("Dial error:%s", err.Error())
                return 
        }
        defer c.Close()

        // 执行命令: SET A str
        err = c.Set("A", "str")
        if err != nil {
                fmt.Printf("Set error:%s", err.Error())
                return 
        }

        // 执行命令: GET A
        // * 将刚刚写入的内容读取出来
        s, err := c.Get("A")
        if err != nil {
                fmt.Printf("Get error:%s", err.Error())
                return 
        }

        fmt.Printf("A: %s", s)
}
```

* Example2: 使用连接池

```
package main

import (
        xedis "git.oschina.net/yyzybb537/Xedis/client"
        "fmt"
)

func main() {
        // 使用DialPool接口创建连接池
        // * 连接成功后, 连接池的使用方式和单链接的方式完全一样!
        nRepeated := 10 // 连接池中链接的数量
        c, err := xedis.DialPool(nRepeated, "127.0.0.1:8030")
        if err != nil {
                fmt.Printf("Dial error:%s", err.Error())
                return 
        }
        defer c.Close()

        // 执行命令: SET A str
        err = c.Set("A", "str")
        if err != nil {
                fmt.Printf("Set error:%s", err.Error())
                return 
        }

        // 执行命令: GET A
        s, err := c.Get("A")
        if err != nil {
                fmt.Printf("Get error:%s", err.Error())
                return 
        }

        fmt.Printf("A: %s", s)
}
```

## 定制Xedis

对xedis的扩展需要使用golang语言，数据结构的扩展代码置于extend/structures目录下，View的扩展代码置于extend/view目录下。

### 扩展一个数据结构和相应的Cmd

扩展新的数据结构需要自定义一个struct，并符合如下interface：

```
type Structures interface {                                                        
    Name() string                                                                  
}
```

这个interface定义在interfaces/structures.go文件中，Name接口返回小写的结构名。

下面的代码定制了一个String结构, 其中的13-15行代码是将String结构体的工厂函数注册到系统中, 注意在14行代码的地方完成相关的初始化代码。

这个String结构定义了两个命令：Get Set，命令名大小写不敏感，且命令不可重复定义。
定义命令的方式是给String结构提供一个接口，接口名以Cmd开头，紧接着的下一个字符(**Tag**)必须是C、W、R中的一个，然后下一个字符必须是一个下划线，最后是命令名。

**Tag**:
C表示这个命令可以触发创建一个新的String对象; W表示会改变String的内容; R表示对String是只读操作。
生成后的代码会给每个命令接口加上读写锁，CW的接口会加写锁，只读接口会加上读锁；**因此，命令接口之间不要互相调用，以免死锁。**
如果不希望代码生成阶段被加锁, 给String定义一个名为NoMutex的接口即可.

命令接口的输入参数只支持有限的内置类型，list如下：
bool
int
int8
int16
int32
int64
uint
uint8
uint16
uint32
uint64
string
以及这些类型的切片(Slice), 比如：[]string, []int等等. 
在一个参数表中，切片类型只能有一个。

命令接口的输出参数除了上面的类型以外，还可以在末尾增加一个error类型的参数，用于输出命令执行过程中的错误信息。

接口的帮助信息要以注释的形式写在接口定义的前一行，只能以"//"开头，这部分信息可以在执行./Xedis -D时看到，也可以在客户端调用xedis.HelpInfo()接口来获取。

```
     1  package structures
     2
     3  import (
     4          "fmt"
     5          I "git.oschina.net/yyzybb537/Xedis/interfaces"
     6          "strconv"
     7  )
     8
     9  type String struct {
    10          Value string
    11  }
    12
    13  var stringRegister interface{} = I.RegisterStructures("string", func() I.Structures {
    14          return &String{}
    15  })
    16
    17  func (this *String) Name() string {
    18          return "string"
    19  }
    20
    21  // Set string value or create
    22  func (this *String) CmdC_Set(v string) {
    23          this.Value = v
    24  }
    25
    26  // Get value of string
    27  func (this *String) CmdR_Get() string {
    28          return this.Value
    29  }
```

### 让定制生效

将上文定制的代码保存到extend/structures/string.go文件中，重新执行./build.sh进行编译，即可完成定制。
注意保存的文件名需要与结构体同名，而且是全小写。

此时执行./Xedis -D可以看到增加了一个Structure和两个命令:

```
$ ./Xedis -D
----- Commands -----
[Structure] string:
  SET func(v string) ()
  summary: Set string value or create

  GET func() (string)
  summary: Get value of string

--------------------
```

### 扩展一个View

View是Xedis中所有Key-Value的组织结构，默认使用的是hash表。 当我们有高性能的前缀搜索、后缀搜索、前缀批量操作等需求时，hash表就不再适用，此时需要自定义全新的View来替换掉默认的View。

为了讲解简单，我们扩展一个用slice管理key-value的View。
View需要符合以下interface：

```
type View interface {
        Name() string
        GetKey(key string) Structures
        SetKey(key string, s Structures)
        DelKey(key string) bool
}
```

这个interface定义在interfaces/view.go文件中，Name接口返回小写的view名。
View的扩展与structures的扩展基本相同，代码如下：

```
package view

import (
        I "git.oschina.net/yyzybb537/Xedis/interfaces"
)

type structWrap struct {
        key string
        s I.Structures
}

type ListView struct {
        list    []*structWrap
}

var listViewRegister interface{} = I.RegisterView("list", func() I.View {
        return &ListView{ list : make([]*structWrap, 0) }
})

func (this *ListView) Name() string {
        return "list"
}

func (this *ListView) GetKey(key string) I.Structures {
        for _, s := range this.list {
                if s.key == key {
                        return s.s
        }
    }

        return nil
}

func (this *ListView) SetKey(key string, s I.Structures) {
        for _, s := range this.list {
                if s.key == key {
                        return
        }
    }

        this.list = append(this.list, &structWrap{
                key : key,
                s : s,
        })
}

func (this *ListView) DelKey(key string) bool {
        for i, s := range this.list {
                if s.key == key {
                        this.list[i] = this.list[len(this.list) - 1]
                        this.list = this.list[:len(this.list) - 1]
                        return true
        }
    }

        return false
}

func patternMatch(s, pattern string) bool {
        return true
}

// Get some key name by pattern
func (this *ListView) CmdR_Keys(pattern string) (keys []string) {
        keys = make([]string, 0)
        for _, s := range this.list {
                if patternMatch(s.key, pattern) {
                        keys = append(keys, s.key)
                }
        }

        return
}
```

可以看到，这个View定义了CmdW_Keys接口，与数据结构的扩展一样的是，这个接口会生成一个名为KEYS的命令。但是不同之处在于，这个KEYS命令是专属于list这个View的，也就是说Xedis选用list来启动时这个命令才会生效。

客户端的调用View专属命令时要用c.ViewList().Keys接口来调用。
不同View之间，View专属命令是可以重名的。

GetKey/SetKey/DelKey以及自定义的命令接口都会被加上读写锁，因此**不能相互调用，不然会死锁!**

### 扩展一个全局命令

有时候我们需要一些操作多个key或不操作任何key的命令，我们称之为全局命令。
redis中有个MGET命令，用于一次性获取多个String的值。
下面以此为例讲解一下全局命令的扩展。

全局命令的扩展和普通命令基本一样，唯一的差别在于全局命令定义的是一个全局的函数，不再是类成员函数。

```
// Multiply GET command
func CmdR_MGet(keys []string) []string {
        r := make([]string, 0)
        for _, key := range keys {
				// 通过View找到key对应的数据结构
                s := I.GetView().GetKey(key)
                if s == nil {
                        r = append(r, "")
                        continue
                }

				// 判断数据结构是否是string
                if s.Name() != "string" {
                        r = append(r, "")
                        continue
                }

                r = append(r, s.(*String).CmdR_Get())
        }
        return r
}
```

代码中的`I.GetView()`是View的全局访问点，在这里可以调用当前View的接口找到key对应的数据结构.

将这段代码追加到string.go的文件尾部，重新执行./build.sh，一个全局命令就创建好了。

```
$ ./Xedis -D
----- Commands -----
[Structure] string:
  SET func(v string) ()
  summary: Set string value or create

  GET func() (string)
  summary: Get value of string

--------------------
----- Commands -----
[View] Global:
  MGET func(keys []string) ([]string)
  summary: Multiply GET command

--------------------
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)