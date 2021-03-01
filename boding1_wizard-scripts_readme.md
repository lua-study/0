# wizard-scripts

[作者简书博客原文](http://www.jianshu.com/p/46a120f9e5a3)

无论是技术开发人员还是架构设计人员都是在实践中成长起来的，他们通过实践进行总结，总结后把经验升华并再次应用到实践中去，进一步提供生产效率。

本文介绍笔者在互联网公司里线上应急和技术攻关过程中积累的应用层脚本和Java虚拟机命令，这些脚本和命令在发现问题和定位问题的过程中起到关键作用，在特定的问题环境下，堪称快速定位问题的小倚天剑以及快速解决问题的微屠龙刀。

本文在介绍脚本和命令之前，先给大家介绍笔者的Linux环境以及在Linux环境下搭建的一个原创Java发号器服务，用来向大家演示脚本和命令的使用方法，力争做到让大家拿来即用的效果。另外，在介绍完所有的脚本和命令之后，我会把所有的命令和脚本收集在一个表格中，便于大家随时参考和使用，并推荐大家把这个表格打印出来放在自己的办公桌上，需要的时候看一眼，便可快速发现和解决问题的工具。

脚本和命令系列主题中计划提供两篇文章，这篇文章是脚本和命令系列主题中的其中一篇，本文聚焦在那些“神奇的”应用层脚本和Java虚拟机命令，曾经在不同程度上帮助笔者在线上应急和技术攻关的过程中解决过不小的问题，通过这篇文章把这些脚本和命令推广给读者，让读者也能够应用在实践中，切实有效的帮助读者解决实际问题。

另外一篇文章聚焦在线上应急和技术攻关过程中，你必须学会使用的那些Linux底层基础命令，包括Linux内存、CPU利用率、IO、网络IO等的监控工具、性能测试工具、安全工具、以及其他实用工具等，这篇文章会在后续尽快发布给读者。

## 1 环境搭建和示例服务启动

首先，使用的Linux版本为：

>OS：Ubuntu 14.04.2 LTS	
内核：3.16.0-30-generic	
硬件架构：x86_64

使用的JDK版本为：

>jdk1.8.0_20

为了让大家了解使用命令的真实环境，我们在Linux系统中搭建了原创发号器服务[Vesta](http://vesta.cloudate.net/)，在介绍下面的每个命令的同时，都会以监控和维护原创发号器服务为例来说明，如果大家对发号器服务的设计、实现和使用方式感兴趣，或者大家想了解如何开发一款专业的开源软件，请参考文章[如何设计一款多场景分布式发号器](http://www.jianshu.com/p/44fd44b4cd05)，本文聚焦在如何使用这些高效的脚本和Linux命令来维护一款线上服务。

为了搭建Vesta发号器服务，我们需要从Github地址[https://github.com/robertleepeak/vesta-id-generator.git](https://github.com/robertleepeak/vesta-id-generator.git)下载源代码：

```bash
robert@robert-ubuntu1410:~/working/workspace$ git clone https://github.com/robertleepeak/vesta-id-generator.git
正克隆到 'vesta-id-generator'...
remote: Counting objects: 944, done.
remote: Compressing objects: 100% (53/53), done.
接收对象中: 100% (944/944), 474.66 KiB | 337.00 KiB/s, done.
remote: Total 944 (delta 19), reused 0 (delta 0), pack-reused 881
处理 delta 中: 100% (221/221), done.
检查连接... 完成。
```

下载后工作目录为：

```bash
robert@robert-ubuntu1410:~/working/workspace$ ll
总用量 12
drwxrwxr-x  3 robert robert 4096  4月  8 18:31 ./
drwxr-xr-x  6 robert robert 4096  4月  8 17:33 ../
drwxrwxr-x 12 robert robert 4096  4月  8 18:31 vesta-id-generator/
```

进入Vesta发号器项目根目录并列出目录结构：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator$ ll
总用量 108
drwxrwxr-x 12 robert robert  4096  4月  8 18:31 ./
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 ../
-rwxrwxr-x  1 robert robert  3843  4月  8 18:31 assembly.xml*
-rwxrwxr-x  1 robert robert   494  4月  8 18:31 brief.txt*
-rwxrwxr-x  1 robert robert    65  4月  8 18:31 deploy-maven.sh*
-rw-rw-r--  1 robert robert 12292  4月  8 18:31 .DS_Store
drwxrwxr-x  8 robert robert  4096  4月  8 18:31 .git/
-rwxrwxr-x  1 robert robert   231  4月  8 18:31 .gitignore*
-rwxrwxr-x  1 robert robert 11358  4月  8 18:31 LICENSE*
-rwxrwxr-x  1 robert robert   902  4月  8 18:31 make-release.sh*
-rwxrwxr-x  1 robert robert  1985  4月  8 18:31 pom.xml*
-rwxrwxr-x  1 robert robert  2515  4月  8 18:31 README.md*
-rwxrwxr-x  1 robert robert  1429  4月  8 18:31 todo.txt*
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-client/
drwxrwxr-x  2 robert robert  4096  4月  8 18:31 vesta-doc/
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-intf/
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-rest/
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-rest-netty/
drwxrwxr-x  4 robert robert  4096  4月  8 18:31 vesta-sample/
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-server/
drwxrwxr-x  4 robert robert  4096  4月  8 18:31 vesta-service/
drwxrwxr-x  3 robert robert  4096  4月  8 18:31 vesta-theme/
```
然后，直接运行发布脚本`make-release.sh`进行打包发布：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator$ ./make-release.sh 
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] vesta-id-generator
[INFO] vesta-intf
[INFO] vesta-service
[INFO] vesta-rest
[INFO] vesta-rest-netty
[INFO] vesta-client
[INFO] vesta-server
[INFO] vesta-sample
[INFO] vesta-sample-embed
[INFO] vesta-sample-client
......
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary:
[INFO] 
[INFO] vesta-id-generator ................................. SUCCESS [ 11.630 s]
[INFO] vesta-intf ......................................... SUCCESS [  3.489 s]
[INFO] vesta-service ...................................... SUCCESS [  1.140 s]
[INFO] vesta-rest ......................................... SUCCESS [  4.749 s]
[INFO] vesta-rest-netty ................................... SUCCESS [  2.482 s]
[INFO] vesta-client ....................................... SUCCESS [  0.111 s]
[INFO] vesta-server ....................................... SUCCESS [  1.879 s]
[INFO] vesta-sample ....................................... SUCCESS [  0.005 s]
[INFO] vesta-sample-embed ................................. SUCCESS [  0.475 s]
[INFO] vesta-sample-client ................................ SUCCESS [  0.200 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 27.026 s
[INFO] Finished at: 2017-04-08T21:31:34+08:00
[INFO] Final Memory: 42M/616M
[INFO] ------------------------------------------------------------------------
```

最后，启动发号器REST服务：

```bash

robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin$ ll
总用量 110968
drwxrwxr-x 2 robert robert     4096  4月  8 21:34 ./
drwxrwxr-x 6 robert robert     4096  4月  8 21:34 ../
-rw-rw-r-- 1 robert robert 47117221  4月  8 21:34 vesta-all-src-0.0.1.tar.gz
-rw-rw-r-- 1 robert robert 34524462  4月  8 21:34 vesta-lib-0.0.1.tar.gz
-rw-rw-r-- 1 robert robert 14745549  4月  8 21:33 vesta-rest-0.0.1-bin.tar.gz
-rw-rw-r-- 1 robert robert  8656473  4月  8 21:33 vesta-rest-netty-0.0.1-bin.tar.gz
-rw-rw-r-- 1 robert robert  8539966  4月  8 21:33 vesta-server-0.0.1-bin.tar.gz
-rw-rw-r-- 1 robert robert    27079  4月  8 21:34 vesta-src-0.0.1.tar.gz
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin$ tar xzvf vesta-rest-0.0.1-bin.tar.gz
vesta-rest-0.0.1/bin/
vesta-rest-0.0.1/bin/server.sh
vesta-rest-0.0.1/bin/start.sh
vesta-rest-0.0.1/bin/check.sh
vesta-rest-0.0.1/bin/stop.sh
vesta-rest-0.0.1/lib/vesta-rest-0.0.1.jar
vesta-rest-0.0.1/lib/vesta-rest-0.0.1-sources.jar

robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin/vesta-rest-0.0.1/bin$ ./start.sh
apppath: /home/robert/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin/vesta-rest-0.0.1
Vesta Rest Server is started.
```

然后，使用curl语句测试发号器服务是否正常运行：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin/vesta-rest-0.0.1/bin$ curl "http://localhost:8080/genid"
2382742310220727293

robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin/vesta-rest-0.0.1/bin$ curl "http://localhost:8080/expid?id=2382742310220727293"
{"machine":1021,"seq":0,"time":71618055,"genMethod":2,"type":0,"version":0}
```

看见发号器正确产生ID=2382742310220727293，并能反解成JSON字符串：

>{"machine":1021,"seq":0,"time":71618055,"genMethod":2,"type":0,"version":0}

这说明发号器服务启动正常，然后使用Linux命令查看服务进程，确保服务进程运行正常：

```bash
robert@robert-ubuntu1410:~$ ps -elf | grep java
0 S robert    8244  1847  2  80   0 - 231991 futex_ 21:54 pts/7   00:00:23 java -server -Xms512m -Xmx512m -Xmn128m -XX:PermSize=128m -Xss256k -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+CMSParallelRemarkEnabled -XX:+UseCMSCompactAtFullCollection -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=60 -verbose:gc -XX:+PrintGCDateStamps -XX:+PrintTenuringDistribution -XX:+PrintGCDetails -Xloggc:./logs/gc.log -cp /home/robert/working/workspace/vesta-id-generator/releases/vesta-id-generator-0.0.1-release/bin/vesta-rest-0.0.1/extlib -jar ./lib/vesta-rest-0.0.1.jar
```

接下来的章节我们围绕这个服务来介绍后续的每个脚本和命令。

## 2 神奇的脚本解决不可思议的问题

本章介绍那些“神奇的”脚本，这些“神奇的”脚本伴我度过了多少个日日夜夜已经不记得了，凡是线上有紧急问题的时候，或者做一个疑难问题的技术攻关的时候，我都会与他们并肩作战，同时也为多个同事解决了不少“不可思议的”问题，因此，这里我希望能够把这些脚本分享给每一个奋斗在一线的技术人员，帮助他们解决手头上的棘手问题。 

如果大家对脚本开发感兴趣，可以加入我的开源项目[wizard-scripts](https://github.com/robertleepeak/wizard-scripts)，我们把实践过程中使用的脚本逐渐的汇总，最后形成一个专业的开源项目，来帮助更多的同行们，欢迎大家加入开源队伍。

### 2.1 show-busiest-java-threads

此命令通过结合Linux操作系统的ps命令和jvm自带的jstack命令，查找Java进程内CPU利用率最高的线程，一般适用于服务器负载较高的场景，并需要快速定位导致负载高的原因。

本脚本来自一个叫候鸟树（笔者在互联网行业入行前的引路人）的网友，原作者不详，这里保留原作者名为了表示对技术人的尊重。

***命令格式：***

>./show-busiest-java-threads -p 进程号 -c 显示条数

>./show-busiest-java-threads -h

***使用示例：***

> ./show-busiest-java-threads -p 8244 -c 3

示例输出：

```bash
robert@robert-ubuntu1410:~/working/scripts$ ./show-busiest-java-threads -p 8244 -c 3
The stack of busy(0.3%) thread(8257/0x2041) of java process(8244) of user(robert):
"C2 CompilerThread1" #7 daemon prio=9 os_prio=0 tid=0xc545d400 nid=0x2041 waiting on condition [0x00000000]
   java.lang.Thread.State: RUNNABLE

The stack of busy(0.3%) thread(8256/0x2040) of java process(8244) of user(robert):
"C2 CompilerThread0" #6 daemon prio=9 os_prio=0 tid=0xc545bc00 nid=0x2040 waiting on condition [0x00000000]
   java.lang.Thread.State: RUNNABLE

The stack of busy(0.1%) thread(8260/0x2044) of java process(8244) of user(robert):
"VM Periodic Task Thread" os_prio=0 tid=0xc5463c00 nid=0x2044 waiting on condition 
```

***脚本源码：***

```bash
#!/bin/bash
# @Function
# Find out the highest cpu consumed threads of java, and print the stack of these threads.
#
# @Usage
#   $ ./show-busy-java-threads
#
# @author Jerry Lee

PROG=`basename $0`

usage() {
    cat   /dev/null
}
trap "cleanupWhenExit" EXIT

printStackOfThread() {
    while read threadLine ; do
        pid=`echo ${threadLine} | awk '{print $1}'`
        threadId=`echo ${threadLine} | awk '{print $2}'`
        threadId0x=`printf %x ${threadId}`
        user=`echo ${threadLine} | awk '{print $3}'`
        pcpu=`echo ${threadLine} | awk '{print $5}'`
        
        jstackFile=/tmp/${uuid}_${pid}
        
        [ ! -f "${jstackFile}" ] && {
            jstack ${pid} > ${jstackFile} || {
                redEcho "Fail to jstack java process ${pid}!"
                rm ${jstackFile}
                continue
            }
        }
        
        redEcho "The stack of busy(${pcpu}%) thread(${threadId}/0x${threadId0x}) of java process(${pid}) of user(${user}):"
        sed "/nid=0x${threadId0x}/,/^$/p" -n ${jstackFile}
    done
}

[ -z "${pid}" ] && {
    ps -Leo pid,lwp,user,comm,pcpu --no-headers | awk '$4=="java"{print $0}' |
    sort -k5 -r -n | head --lines "${count}" | printStackOfThread
} || {
    ps -Leo pid,lwp,user,comm,pcpu --no-headers | awk -v "pid=${pid}" '$1==pid,$4=="java"{print $0}' |
    sort -k5 -r -n | head --lines "${count}" | printStackOfThread
}
```

### 2.2 find-in-jar

此脚本在Jar包中的包名和类名中查找某一关键字，并高亮显示匹配的Jar包名称和路径，多用于定位`java.lang.NoClassDefFoundError`和`java.lang.ClassNotFoundException`的问题，以及类版本重复或者冲突的问题等。

此脚本是笔者的原创，在不同的公司里帮助很多同事解决了大项目中类版本重复和冲突的问题。

***命令格式：***

>find-in-jar 关键字或者类名 路径

***使用示例：***

> find-in-jar ByteBufferHolder .
 
示例输出：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator$ find-in-jar ByteBufferHolder .
./releases/vesta-id-generator-0.0.1-release/lib/tomcat-embed-core-8.0.20.jar
     1165  2015-02-15 18:11   org/apache/coyote/ByteBufferHolder.class
./target/vesta-id-generator-0.0.1-release/lib/tomcat-embed-core-8.0.20.jar
     1165  2015-02-15 18:11   org/apache/coyote/ByteBufferHolder.class
```

***脚本源码：***

```bash
#!/bin/bash

find . -name "*.jar" > /tmp/find_in_jar_temp

while read line
do
  if unzip -l $line | grep $1 &> /tmp/find_in_jar_temp_second
  then
    echo $line | sed 's#\(.*\)#\x1b[1;31m\1\x1b[00m#'
    cat /tmp/find_in_jar_temp_second
  fi
done  grep-in-jar 关键字 路径

***使用示例：***

> grep-in-jar "vesta" .

示例输出：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator$ grep-in-jar "vesta" .
find 'vesta' in . 
==> Found "vesta" in ./vesta-sample/vesta-sample-embed/target/vesta-sample-embed-0.0.1.jar
==> Found "vesta" in ./vesta-sample/vesta-sample-embed/target/vesta-sample-embed-0.0.1-sources.jar
==> Found "vesta" in ./vesta-sample/vesta-sample-client/target/vesta-sample-client-0.0.1.jar
==> Found "vesta" in ./vesta-sample/vesta-sample-client/target/vesta-sample-client-0.0.1-sources.jar
==> Found "vesta" in ./vesta-rest-netty/target/vesta-rest-netty-0.0.1-sources.jar
==> Found "vesta" in ./vesta-rest-netty/target/vesta-rest-netty-0.0.1.jar
```

***脚本源码：***

```bash
#!/bin/bash
### grep text in jars

if [ $# -lt 2 ];then
    echo 'Usage : jargrep text path'
    exit 1;
fi

LOOK_FOR=$1
LOOK_FOR=`echo ${LOOK_FOR//\./\/}`
folder=$2
echo "find '$LOOK_FOR' in $folder "
for i in `find $2 -name "*jar"`
do
    unzip -p $i | grep "$LOOK_FOR" > /dev/null
    if [ $? = 0   ]
    then
        echo "==> Found \"$LOOK_FOR\" in $i"
    fi
done
```

### 2.4 jar-conflict-detect

此脚本用于识别冲突的Jar包，可以在一个根目录下找到所有包含相同类的Jar包，并且根据相同类的多少来判断Jar包的相似度，常常用于某些功能上线不可用或者没有按照预期起到作用，使用此脚本分析是否存在两个版本的类，而老版本的类被Java虚拟机加载，其实，JVM规范并没有规定类路径下相同类的加载顺序，实现JVM规范的虚拟机的实现机制也各不相同，因此无法判断相同的类中哪个版本的类会被先加载，因此Jar包冲突是个非常讨厌的问题。 

此脚本最初来自于作者[hongjiang](http://hongjiang.info/duplicate-classes-check-script/)，为了能够在我的Linux版本上正常运行，后来进行了些许修改，它在很多棘手的问题上表现了强大的战斗力。

***命令格式：***

>jar-conflict-detect 路径

***使用示例：***

> jar-conflict-detect .

示例输出：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/target/vesta-id-generator-0.0.1-release/lib$ jar-conflict-detect .
Similarity  DuplicateClasses  File1                        File2
%21         6                 commons-logging-1.1.3.jar    jcl-over-slf4j-1.7.11.jar
%02         10                commons-beanutils-1.8.0.jar  commons-collections-3.2.1.jar
See /tmp/cp-verbose.log for more details.
```

***脚本源码：***

```bash
#!/bin/bash
if [ $# -eq 0 ];then
    echo "please enter classpath dir"
    exit -1
fi

if [ ! -d "$1" ]; then
    echo "not a directory"
    exit -2
fi

tmpfile="/tmp/.cp$(date +%s)"
tmphash="/tmp/.hash$(date +%s)"
verbose="/tmp/cp-verbose.log"

declare -a files=(`find "$1" -name "*.jar"`)
for ((i=0; i  > $tmphash
    echo "$list"
done | sort | awk 'NF{
    a[$1]++;m[$1]=m[$1]","$2}END{for(i in a) if(a[i] > 1) print i,substr(m[i],2)
}' > $tmpfile

awk '{print $2}' $tmpfile |
awk -F',' '{i=1;for(;i  $len_jar2 ? $len_jar1 : $len_jar2))
    len_jar1=`echo $len_jar1 | awk -F' ' '{print $1}'`
    len_jar2=`echo $len_jar2 | awk -F' ' '{print $1}'`
    if [ $len_jar1 -gt $len_jar2 ]
    then
      len=$len_jar1
    else
      len=$len_jar2
    fi
    per=$(echo "scale=2; $dup/$len" | bc -l)
    echo ${per/./} $dup $jar1 $jar2
done | sort -nr -k1 -k2 |
awk 'NR==1{print "Similarity DuplicateClasses File1 File2"}{print "%"$0}'| column -t

sort $tmpfile | awk '{print $1,"\n\t\t",$2}' > $verbose
echo "See $verbose for more details."

rm -f $tmpfile
rm -f $tmphash
```

### 2.5 http-spy

此脚本利用Linux命令nc检查HTTP请求参数、请求头和请求体等信息，常常用于调试基于HTTP协议的服务调用，如果一次HTTP调用没有的达到预期的效果，首先检查传递的参数是否正确，这包括请求参数、请求头、请求体等信息，这种场景正式此脚本的用武之地。

***命令格式：***

>http-spy

***使用示例：***

>http-spy

示例输出：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/target/vesta-id-generator-0.0.1-release/lib$ curl "http://localhost:8888?abc=def"
```

```bash
robert@robert-ubuntu1410:~/working/scripts$ ./http-spy 
GET /?abc=def HTTP/1.1
User-Agent: curl/7.35.0
Host: localhost:8888
Accept: */*
```

***脚本源码：***

```bash
#!/bin/bash

while true; do nc -l 8888; done
```

### 2.6 show-mysql-qps

此脚本可以用于快速查看Mysql实例的负载情况，包括QPS、TPS、提交数、回滚数、并发线程、执行线程等。

***命令格式：***

>show-mysql-qps 用户名 密码

***使用示例：***

>show-mysql-qps root ****

示例输出：

```bash
robert@robert-ubuntu1410:~/working/scripts$ show-mysql-qps.sh root ******
QPS Commit Rollback TPS Threads_con Threads_run 
------------------------------------------------------- 
1      0        0       0        1          1 
1      0        0       0        1          1 
1      0        0       0        1          1 
1      0        0       0        1          1 
```

***脚本源码：***

```bash
#!/bin/bash
mysqladmin -uroot extended-status -i1 |
awk 'BEGIN{local_switch=0;print "QPS Commit Rollback TPS Threads_con Threads_run \n------------------------------------------------------- "}
$2 ~ /Queries$/ {q=$4-lq;lq=$4;}
$2 ~ /Com_commit$/ {c=$4-lc;lc=$4;}
$2 ~ /Com_rollback$/ {r=$4-lr;lr=$4;
$2 ~ /Threads_connected$/ {tc=$4;}
$2 ~ /Threads_running$/ {tr=$4;
        if(local_switch==0){
          local_switch=1; 
          count=0
        } else {
          if(count>10) {
            count=0;
            print "------------------------------------------------------- \nQPS Commit Rollback TPS Threads_con Threads_run \n------------------------------------------------------- ";
          } else {
            count+=1;
            printf "%-6d %-8d %-7d %-8d %-10d %d \n", q,c,r,c+r,tc,tr;
          }
        }
}'
```

## 3 Java虚拟机相关的命令

本节介绍Java世界里那些有用的虚拟机命令，有了他们的伴随，你会感觉到解决Java世界里面的问题事半功倍。

本章并不会介绍所有的JDK自带的工具命令，而是结合实践给读者介绍那些最常用最重要的Java虚拟机相关的命令，以及一些开源的Java虚拟机工具，目的是帮助大家在现实中解决问题。

如果想全面了解JDK各种命令，请参考[JDK官方文档](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/toc.html)。

### 3.1 jad

jad反编译工具可以将字节码的二进制类反编译回Java源代码，常常用于遇到问题但是无法在源代码中定位的场景，通过反编译字节码可以分析程序事实上执行的流程，从而定位深层次的问题。

由于历史原因或者其他原因，有些时候项目依赖了没有源代码的jar包，如果出现问题需要定位，那么jad命令可是个小倚天剑。

jad下载地址：[JAD](http://www.javadecompilers.com/jad)

如果不习惯使用命令行，可以下载界面版本jd-gui，可以一次反编译一个JAR包，并在类之间有简单的导航操作。

界面版本jd-gui下载地址：[JD-GUI](https://github.com/java-decompiler/jd-gui)

如果开发者对字节码进行了混淆，反编译的源代码将很难读懂，混淆的代码只能通过混淆后给出的摘要文件进行分析，这种场景下使用反编译工具作用不大。

***使用示例：***

>jad AbstractIdServiceImpl.class

示例输出：

```bash
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/target/vesta-id-generator-0.0.1-release/lib/com/robert/vesta/service/impl$ jad AbstractIdServiceImpl.class
Parsing AbstractIdServiceImpl.class...The class file version is 49.0 (only 45.3, 46.0 and 47.0 are supported)
 Generating AbstractIdServiceImpl.jad
```

```bash 
robert@robert-ubuntu1410:~/working/workspace/vesta-id-generator/target/vesta-id-generator-0.0.1-release/lib/com/robert/vesta/service/impl$ ll
总用量 40
-rw-rw-r-- 1 robert robert 5375  4月  8 21:33 AbstractIdServiceImpl.class
-rw-rw-r-- 1 robert robert 5197  4月  9 10:01 AbstractIdServiceImpl.jad
-rw-rw-r-- 1 robert robert 2965  4月  8 21:33 IdServiceImpl.class
```

### 3.2 btrace

java应用服务在生产环境中可能会出现各种各样的问题，有些问题在找到根源原因之前看似很“不可思议”，有些时候并没有产生异常或者错误消息，这时我们无法根据已有的日志来定位问题，那么我们需要更多的信息，例如：参数、返回值、程序逻辑判断、循环次数等信息，来追踪问题，如果临时增加日志，需要重新上线，成本较高，使用远程调试（后续会在专用文章中介绍gdb等远程调试工具）又会影响线上流量甚至导致客户程序超时，这个时候btrace应运而生，btrace可以动态地跟踪java运行时程序，将定制化的跟踪字节码切面注入到运行类中，对运行代码无侵入，根据官方信息判断对性能上的影响也可以忽略不计。

了解和下载btrace：[BTRACE下载主页](https://kenai.com/projects/btrace/downloads/directory/releases)

btrace源代码：[BTRACE Github主页](https://github.com/btraceio/btrace)

下面介绍btrace的使用方法：

***命令格式:***

> btrace [-p port] [-cp classpath] pid btrace-script

参数解析：	

>1. port指定btrace agent的服务端监听端口号，供客户端连接
2. classpath用来指定依赖的类加载路径
3. pid表示进程号，可通过jps或者ps命令获取
4. btrace-script即为btrace跟踪切面脚本

在运行命令之前，我们需要编写btrace的跟踪脚本：

```java
import java.util.Date;

import com.sun.btrace.BTraceUtils;
import static com.sun.btrace.BTraceUtils.*;
import com.sun.btrace.annotations.*;

@BTrace
public class Btrace {

   @OnMethod(
       clazz = "com.cloudate.controller.AdminController",
       method = "sayHello",
       location = @Location(Kind.RETURN)
   )
   public static void sayHello(@Duration long duration) {//单位是纳秒，要转为毫秒
       println(strcat("duration(ms): ", str(duration / 1000000)));
   }

}
```

这个跟踪脚本对业务代码的方法进行拦截，并打印方法执行时间：

```java
package com.cloudate.controller;

public class AdminController {
	public String sayHello(String name, int age) {
	   return "hello everyone";
	}
}
```

*** 使用示例：***

```bash
btrace -p 2020 -cp ~/servlet-api.jar 1507 ~/BTrace.java
```

当AdminController类的sayHello被调用的时候，控制台就会打印方法执行时间，这对定位线上的棘手问题有非常大的帮助。

### 3.3 jmap

生产中java应用服务发生OutOfMemoryError那是家常便饭，发生了OutOfMemoryError或者发现内存不足报警，我们经常需要找到是什么原因造成的，要找到内存都去哪儿了，jmap在这个场景是用来定位问题的主要工具，它主要用来查看Java进程内存的使用情况。

jmap是JDK自带的监控工具，在JDK的根目录里可以找到。

***使用示例1：***

按照占用空间大小打印程序中类的列表，从这个列表中可以分析哪些类占用了比较多的内存，再结合代码找到问题的所在。

```bash
jmap -histo:live 2743
```

示例输出：

```bash
 num     #instances         #bytes  class name
----------------------------------------------
   1:         44398        7206296  [C
   2:         23166        2789688  [B
   3:         14511        1276968  java.lang.reflect.Method
   4:         43256         692096  java.lang.String
   5:         22102         530448  org.springframework.boot.loader.util.AsciiBytes
   6:         11047         530256  org.springframework.boot.loader.jar.JarEntryData
   7:          5800         510592  java.lang.Class
   8:         18088         434112  java.util.HashMap$Node
   9:          6465         356336  [Ljava.lang.Object;
  10:         14582         349968  java.util.concurrent.ConcurrentHashMap$Node
  11:          2914         319928  [Ljava.util.HashMap$Node;
  12:          6920         221440  java.util.LinkedHashMap$Entry
  13:          2008         192768  org.springframework.boot.loader.jar.JarEntry
  14:          5691         182112  java.lang.ref.SoftReference
  15:          7467         179208  java.lang.ref.WeakReference
  16:          9410         166712  [Ljava.lang.Class;
  17:          2786         156016  java.util.LinkedHashMap
  18:           101         136256  [Ljava.util.concurrent.ConcurrentHashMap$Node;
  19:          1761         112704  java.lang.reflect.Field
  20:          3081         105056  [Ljava.lang.String;
  21:          4357         104568  java.beans.MethodRef
  ......
```

***使用示例2：***

按照占用空间大小打印程序中加载的动态链接库的列表，其实，Java进程在操作系统中会加载多个动态链接库，Java进程本身和动态链接库都会在其占用的虚拟地址空间上分配内存，Java堆和栈等内存空间分配在Java进程本身，Java直接内存会分配在Java进程堆内存外或者依赖的动态链接库上，因此，此命令帮助大家定位是Java进程本身占用内存较大，还是哪个动态链接库占用内存较多，在定位直接内导致的内存泄露的场景有很大的作用。

```bash
jmap 2743
```

示例输出：

```bash
robert@robert-ubuntu1410:~$ jmap 2743
Attaching to process ID 2743, please wait...
Debugger attached successfully.
Server compiler detected.
JVM version is 25.20-b23
0x08048000	5K	/home/robert/working/softwares/jdk1.8.0_20/bin/java
0xe6b2e000	78K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libnio.so
0xe6d06000	100K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libnet.so
0xf65b5000	113K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libzip.so
0xf65cf000	41K	/lib32/libnss_files-2.19.so
0xf65db000	41K	/lib32/libnss_nis-2.19.so
0xf65e7000	89K	/lib32/libnsl-2.19.so
0xf6705000	42K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libmanagement.so
0xf671a000	183K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libjava.so
0xf673f000	29K	/lib32/librt-2.19.so
0xf6789000	273K	/lib32/libm-2.19.so
0xf67cf000	12213K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/server/libjvm.so
0xf759b000	1709K	/lib32/libc-2.19.so
0xf7748000	13K	/lib32/libdl-2.19.so
0xf774d000	91K	/home/robert/working/softwares/jdk1.8.0_20/lib/i386/jli/libjli.so
0xf7762000	687K	/lib32/libpthread-2.19.so
0xf777e000	29K	/lib32/libnss_compat-2.19.so
0xf7789000	54K	/home/robert/working/softwares/jdk1.8.0_20/jre/lib/i386/libverify.so
0xf779a000	131K	/lib32/ld-2.19.so
```

***使用示例3：***

java堆的内存结构很复杂，包括新生代、老年代、持久代、直接内存等，jmap命令可以查看堆的概要信息。

```bash
jmap -heap 38574
```

示例输出：

```bash
robert@robert-ubuntu1410:~$ jmap -heap 38574
Attaching to process ID 38574, please wait...
Debugger attached successfully.
Server compiler detected.
JVM version is 25.65-b01

using parallel threads in the new generation.
using thread-local object allocation.
Concurrent Mark-Sweep GC

Heap Configuration:
   MinHeapFreeRatio         = 40
   MaxHeapFreeRatio         = 70
   MaxHeapSize              = 536870912 (512.0MB)
   NewSize                  = 134217728 (128.0MB)
   MaxNewSize               = 134217728 (128.0MB)
   OldSize                  = 402653184 (384.0MB)
   NewRatio                 = 2
   SurvivorRatio            = 8
   MetaspaceSize            = 21807104 (20.796875MB)
   CompressedClassSpaceSize = 1073741824 (1024.0MB)
   MaxMetaspaceSize         = 17592186044415 MB
   G1HeapRegionSize         = 0 (0.0MB)

Heap Usage:
New Generation (Eden + 1 Survivor Space):
   capacity = 120848384 (115.25MB)
   used     = 111727304 (106.55146026611328MB)
   free     = 9121080 (8.698539733886719MB)
   92.45246010074905% used
Eden Space:
   capacity = 107479040 (102.5MB)
   used     = 104015920 (99.19731140136719MB)
   free     = 3463120 (3.3026885986328125MB)
   96.77786478182165% used
From Space:
   capacity = 13369344 (12.75MB)
   used     = 7711384 (7.354148864746094MB)
   free     = 5657960 (5.395851135253906MB)
   57.67959893918505% used
To Space:
   capacity = 13369344 (12.75MB)
   used     = 0 (0.0MB)
   free     = 13369344 (12.75MB)
   0.0% used
concurrent mark-sweep generation:
   capacity = 402653184 (384.0MB)
   used     = 15998072 (15.256950378417969MB)
   free     = 386655112 (368.74304962158203MB)
   3.973164161046346% used

15700 interned Strings occupying 2047808 bytes.
```

***使用示例4：***

有些Java内存问题不是显而易见的，从类、动态链接库、堆的概要信息的角度上，无法定位具体产生的原因，我们需要对Java堆的内部结构进行剖析才能进一步分析问题的根源原因，这通常通过jmap命令导出Java堆的快照，然后通过其他工具或者甚至可视化内存分析工具（例如：JHAT、JMAT、JProfiler、Jconsole、JVisualVM）等进行详细分析。

```bash
jmap -dump:format=b,file=./heap.hprof 2743
```

示例输出：

```bash
robert@robert-ubuntu1410:~$ jmap -dump:format=b,file=./heap.hprof 2743
Dumping heap to /home/robert/heap.hprof ...
Heap dump file created
```

```bash
robert@robert-ubuntu1410:~$ ll
总用量 27184
......
-rw-------  1 robert robert 27632924  4月  9 11:15 heap.hprof
```

### 3.4 jstat

jstat利用了JVM内建的指令对Java应用程序的资源和性能进行实时的命令行的监控，包括了对堆大小和垃圾回收状况的监控等等，与jmap对比，jstat更倾向于输出积累的信息与打印GC等的统计信息等。

jstat是JDK自带的监控工具，在JDK的根目录里可以找到。

***使用示例：***

```bash
jstat -gcutil 2743 5000 10
```

示例输出：

```bash
robert@robert-ubuntu1410:~$ jstat -gcutil 2743 5000 10
  S0     S1     E      O      M     CCS    YGC     YGCT    FGC    FGCT     GCT   
  0.00   0.00   0.75   4.82  98.92      -      8    0.174     6    0.332    0.506
  0.00   0.00   0.75   4.82  98.92      -      8    0.174     6    0.332    0.506
```

名词解析：

>S0C：年轻代中第一个survivor（幸存区）的容量 (字节)	
S1C：年轻代中第二个survivor（幸存区）的容量 (字节)	
S0U：年轻代中第一个survivor（幸存区）目前已使用空间 (字节)	
S1U：年轻代中第二个survivor（幸存区）目前已使用空间 (字节)	
EC：年轻代中Eden（伊甸园）的容量 (字节)	
EU：年轻代中Eden（伊甸园）目前已使用空间 (字节)	
OC：Old代的容量 (字节)		
OU：Old代目前已使用空间 (字节)		
PC：Perm(持久代)的容量 (字节)		
PU：Perm(持久代)目前已使用空间 (字节)		
YGC：从应用程序启动到采样时年轻代中gc次数		
YGCT：从应用程序启动到采样时年轻代中gc所用时间(s)		
FGC：从应用程序启动到采样时old代(全gc)gc次数	
FGCT：从应用程序启动到采样时old代(全gc)gc所用时间(s)		
GCT：从应用程序启动到采样时gc用的总时间(s)	
NGCMN：年轻代(young)中初始化(最小)的大小 (字节)	
NGCMX：年轻代(young)的最大容量 (字节)	
NGC：年轻代(young)中当前的容量 (字节)	
OGCMN：old代中初始化(最小)的大小 (字节)	
OGCMX：old代的最大容量 (字节)	
OGC：old代当前新生成的容量 (字节)		
PGCMN：perm代中初始化(最小)的大小 (字节)		
PGCMX：perm代的最大容量 (字节)		
PGC：perm代当前新生成的容量 (字节)	
S0：年轻代中第一个survivor（幸存区）已使用的占当前容量百分比		
S1：年轻代中第二个survivor（幸存区）已使用的占当前容量百分比		
E：年轻代中Eden（伊甸园）已使用的占当前容量百分比		
O：old代已使用的占当前容量百分比	
P：perm代已使用的占当前容量百分比		
S0CMX：年轻代中第一个survivor（幸存区）的最大容量 (字节)	
S1CMX ：年轻代中第二个survivor（幸存区）的最大容量 (字节)	
ECMX：年轻代中Eden（伊甸园）的最大容量 (字节)	
DSS：当前需要survivor（幸存区）的容量 (字节)（Eden区已满）	
TT： 持有次数限制	
MTT ： 最大持有次数限制

### 3.5 jstack

jstack命令用于打印出给定的java进程ID的线程堆栈快照信息，从而可以看到Java进程内线程的执行状态、这个你在执行的任务等等，可以据此分析线程等待、死锁等问题。

jstack也是JDK自带的命令，在JDK的根目录里可以找到。本文第二章“神奇的”脚本中的show-busiest-java-threads脚本也是基于此命令实现的。

***使用示例：***

```bash
jstack 2743
```

示例输出：

```bash
robert@robert-ubuntu1410:~$ jstack 2743
2017-04-09 12:06:51
Full thread dump Java HotSpot(TM) Server VM (25.20-b23 mixed mode):

"Attach Listener" #23 daemon prio=9 os_prio=0 tid=0xc09adc00 nid=0xb4c waiting on condition [0x00000000]
   java.lang.Thread.State: RUNNABLE

"http-nio-8080-Acceptor-0" #22 daemon prio=5 os_prio=0 tid=0xc3341000 nid=0xb02 runnable [0xbf1bd000]
   java.lang.Thread.State: RUNNABLE
	at sun.nio.ch.ServerSocketChannelImpl.accept0(Native Method)
	at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:241)
	- locked   (a java.lang.Object)
	at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:688)
	at java.lang.Thread.run(Thread.java:745)

"http-nio-8080-ClientPoller-1" #21 daemon prio=5 os_prio=0 tid=0xc35bc400 nid=0xb01 runnable [0xbf1fe000]
   java.lang.Thread.State: RUNNABLE
	at sun.nio.ch.EPollArrayWrapper.epollWait(Native Method)
	at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:269)
	at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:79)
	at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:86)
	- locked   (a sun.nio.ch.Util$2)
	- locked   (a java.util.Collections$UnmodifiableSet)
	- locked   (a sun.nio.ch.EPollSelectorImpl)
	at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:97)
	at org.apache.tomcat.util.net.NioEndpoint$Poller.run(NioEndpoint.java:1052)
	at java.lang.Thread.run(Thread.java:745)
......
```

### 3.5 jinfo

jinfo可以输出并修改运行时的java进程的环境变量和虚拟机参数。

***使用示例：***

```bash
jinfo 38574
```

示例输出：

```bash
$ jinfo 38574
     
Attaching to process ID 38574, please wait...
Debugger attached successfully.
Server compiler detected.
JVM version is 25.65-b01
Java System Properties:

java.runtime.name = Java(TM) SE Runtime Environment
java.vm.version = 25.65-b01
sun.boot.library.path = /Library/Java/JavaVirtualMachines/jdk1.8.0_65.jdk/Contents/Home/jre/lib
java.protocol.handler.pkgs = null|org.springframework.boot.loader
user.country.format = CN
gopherProxySet = false
java.vendor.url = http://java.oracle.com/

......

VM Flags:
Non-default VM flags: -XX:CICompilerCount=3 -XX:CMSInitiatingOccupancyFraction=60 -XX:+CMSParallelRemarkEnabled -XX:+DisableExplicitGC -XX:InitialHeapSize=536870912 -XX:MaxHeapSize=536870912 -XX:MaxNewSize=134217728 -XX:MaxTenuringThreshold=6 -XX:MinHeapDeltaBytes=196608 -XX:NewSize=134217728 -XX:OldPLABSize=16 -XX:OldSize=402653184 -XX:+PrintGC -XX:+PrintGCDateStamps -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+PrintTenuringDistribution -XX:ThreadStackSize=256 -XX:+UseCMSCompactAtFullCollection -XX:+UseCMSInitiatingOccupancyOnly -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+UseConcMarkSweepGC -XX:+UseFastUnorderedTimeStamps -XX:+UseParNewGC 
Command line:  -Xms512m -Xmx512m -Xmn128m -XX:PermSize=128m -Xss256k -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+CMSParallelRemarkEnabled -XX:+UseCMSCompactAtFullCollection -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=60 -verbose:gc -XX:+PrintGCDateStamps -XX:+PrintTenuringDistribution -XX:+PrintGCDetails -Xloggc:./logs/gc.lo
```

### 3.6 其他命令

除了上面介绍的常用Java虚拟机相关命令以外，我们还有两类工具，这节只会做功能介绍，不做详细的展开。

1. 基本命令：

	>1. javah：生成java类的C头文件，一般用于开发JNI库
	>2. jps：用来查找Java进程，通常使用ps命令代替
	>3. jhat：用来分析内存堆快照文件
	>4. jdb：远程调试，用于线上定位问题
	>5. jstatd：jstat的服务器版本

2. Java虚拟机图形界面分析工具：

	>1. JConsole：JDK自带的可以查看Java内存和线程堆栈的工具，已经过时
	>2. JVisualVM：JDK自带的可以查看Java内存和线程堆栈的工具，是JConsole的替代版本
	>3. JMAT：Eclipse组织开发的全功能的开源Java性能跟踪、分析和定位工具
	>4. JProfiler：全功能的商业化Java性能跟踪、分析和定位工具	

## 4 一次OOM定位与修复过程中与监控同事现场编写的脚本

本节提供一个笔者在实践过程中解决OOM问题的一个简单脚本，这个脚本是为了解决OOM（unable to create native thread)的问题而在问题机器上临时编写，并临时使用的，脚本并没有写的很专业，只是为了抓取需要的信息并解决问题，但是在线上问题十分火急的情况下，这个脚本会有大用处。

```bash
#!/bin/bash

ps -Leo pid,lwp,user,pcpu,pmem,cmd >> /tmp/pthreads.log
echo "ps -Leo pid,lwp,user,pcpu,pmem,cmd >> /tmp/pthreads.log" >> /tmp/pthreads.log
echo `date` >> /tmp/pthreads.log
echo 1

pid=`ps aux|grep tomcat|grep cwh|awk -F ' ' '{print $2}'`
echo 2

echo "pstack $pid >> /tmp/pstack.log" >> /tmp/pstack.log
pstack $pid >> /tmp/pstack.log
echo `date` >> /tmp/pstack.log
echo 3

echo "lsof >> /tmp/sys-o-files.log" >> /tmp/sys-o-files.log
lsof >> /tmp/sys-o-files.log
echo `date` >> /tmp/sys-o-files.log
echo 4

echo "lsof -p $pid >> /tmp/service-o-files.log" >> /tmp/service-o-files.log
lsof -p $pid >> /tmp/service-o-files.log
echo `date` >> /tmp/service-o-files.log
echo 5

echo "jstack -l $pid  >> /tmp/js.log" >> /tmp/js.log
jstack -l -F $pid  >> /tmp/js.log
echo `date` >> /tmp/js.log
echo 6 

echo "free -m >> /tmp/free.log" >> /tmp/free.log
free -m >> /tmp/free.log
echo `date` >> /tmp/free.log
echo 7

echo "vmstat 2 1 >> /tmp/vm.log" >> /tmp/vm.log
vmstat 2 1 >> /tmp/vm.log
echo `date` >> /tmp/vm.log
echo 8

echo "jmap -dump:format=b,file=/tmp/heap.hprof 2743" >> /tmp/jmap.log
jmap -dump:format=b,file=/tmp/heap.hprof >> /tmp/jmap.log
echo `date` >> /tmp/jmap.log
echo 9

echo end
```

对于这次线上产生的OOM问题，与运维和监控部们的同事奋斗了几天几夜，终于通过在线上抓取信息、分析问题、在性能压测部门同事的帮助下，最小化重现问题并找到问题的根源原因，最后，针对问题产生的根源提供了有效的方案，随后，会在新的一篇文章中专门讨论如何解决线上的OutOfMemeoryError的问题，这篇新文章将会包括OutOfMemoryError的种类，对于每种OutOfMemoryError产生的原因，以及解决的办法等。

而本节只给读者介绍这个看似简陋而又信息满满的Java服务的监控脚本，如果读者在线上已经遇到了OOM的问题，可以顺着这个脚本的思路，利用本文提供的各种脚本和命令来深挖问题的根本原因。

## 5 场景与命令汇总表

正如文章开始提到，我会把所有的命令和脚本收集在一个表格中，称为“场景与命令汇总表”，便于大家随时参考和使用，并推荐大家把这个表格打印出来放在自己的办公桌上，需要的时候看一眼，便可快速发现和解决问题的工具。

|序号|场景|脚本| 
| :--------:| :-------- | :--------| 
|1|服务器负载高、服务超时、CPU利用率高|show-busiest-java-threads|
|2|java.lang.NoClassDefFoundError、java.lang.ClassNotFoundException、程序未按照预期运行|find-in-jar|
|3|程序未按照预期运行、上线后未执行新逻辑、查找某些关键字|grep-in-jar|
|4|Jar包版本冲突、程序未按照预期运行|jar-conflict-detect|
|5|HTTP调用后发现未按照预期输出结果|http-spy|
|6|数据库负载高、SQL超时|show-mysql-qps|
|7|没有源码的Jar包出了问题、破解别人的代码|jad|
|8|线上出问题还无法上线打点日志、线上调试、做切面|btrace|
|9|内存不足、OutOfMemoryError|jmap|
|10|内存不足、OutOfMemoryError、GC频繁、服务超时、响应长尾|jstat|
|11|服务超时、线程死锁、服务器负载高|jstack|
|12|查看或者修改Java进程环境变量和Java虚拟机变量|jinfo|
|13|使用JNI开发Java本地程序库|javah|
|14|查找java进程ID|jps|
|15|分析jmap产生的java堆的快照|jhat|
|16|QA环境无法重现，需要在准生产线上远程调试|jdb|
|17|与jstat相同，但是可以在线下用客户端连接，可线下操作|jstatd|
|18|简单的有界面的内存分析工具，JDK自带|JConsole|
|19|全面的有界面的内存分析工具，JDK自带|JVisualVM|
|20|专业的Java进程性能分析和跟踪工具|JMAT|
|21|商业化的Java进程性能分析和跟踪工具|JProfiler|

## 6 总结经验

本文开始介绍了学习那些高效应用层脚本和Java虚拟机命令的示例服务Vesta的配置和上线，然后，在以Vesta服务运行为背景下重点介绍了笔者积累的高效的应用层脚本，可以帮助读者解决服务负载高、JAR包冲突、验证线上服务代码、动态添加线上日志的问题，然后给读者介绍了关键的几个Java虚拟机命令，帮助大家查看Java虚拟机运行状态、线程堆栈、内存使用情况、GC频率等，能够帮助大家对自己的服务保驾护航。

正如文章开始提到，另外一篇文章聚焦在线上应急和技术攻关过程中，你必须学会使用的那些Linux基础命令，将会尽快在后续的文章中与读者见面，敬请期待。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)