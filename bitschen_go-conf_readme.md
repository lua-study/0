# Util for config

用于读取Toml配置文件，将其转换成 ImmutableMap 对象。ImmutableMap 对象提供一些类型转换函数。

## Install

```bash
go get -u github.com/parkingwang/go-conf
```

OR

```bash
dep ensure -add github.com/parkingwang/go-conf
```

## Usage

### Map对象

conf.Map 是 `map[string]interface{}` 类型的别名。

conf.ImmutableMap 包装`map[string]interface{}`，提供一个不可变访问接口，通过 GetXXX, MustXXX 等函数来读取内部数据。

详细见 **MustXX** 函数和 **GetXXOrDefault** 函数。

![ImmutableMap](ImmutableMap.png)

### LoadConfig 加载TOML配置文件

- *LoadConfig* 加载指定配置文件夹名称或者TOML文件路径，返回全部配置文件的Map对象；
- *LoadDirConfigText* 加载指定TOML配置文件目录，返回所有配置文件的合并Text文本； 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)