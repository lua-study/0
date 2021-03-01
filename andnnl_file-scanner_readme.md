# File Scanner

## 描述

用 Java 代码实现下面的 shell 脚本逻辑:
 
```
 cat *.log | grep 'Login' | sort | uniq -c | sort -nr
```

实现可以使用支持多线程.

### 测试 log

```
Login 123
1212 Login
3 eceaa
4sa Login
asdsad adad
adasd2 Login
asdsd Login
Login 123
asdsd Login
Login 123
abcd eee
```

### 期望结果

```
3 Login 123
2 asdsd Login
1 adasd2 Login
1 4sa Login
1 1212 Login
```


## 运行

首先需要将项目引入 IDE (推荐使用 IntelliJ IDEA).

### 生成测试数据

在 IDE 中运行 `playground.fs.SampleLogGenerator`. 运行之后项目中会有一个 `logs` 目录, 其中生成了 `100` 个 log 文件, 每个文件有 200 万行, 总共 5G 的数据文件. 可以在 SampleLogGenerator 中改写文件数目和每个文件的行数.

### 运行 FileScanner

在 IDE 中运行 `FileScannerRunner`. 运行结果的前 13 行会被打印出来, 同时运行的时间也会被打印出来.

## 添加自己的 FileScanner 实现.

可以 clone 项目, 并添加自己的 `FileScanner` 实现. 只需要实现 `LogFileScanner` 接口即可.

### 添加单元测试

添加自己的实现之后需要添加实现单元测试类. 参见 [`GreenLogFileScannerOsglBigLinesTest`](https://gitee.com/greenlaw110/file-scanner/tree/master/src/test/java/playground/fs/green/GreenLogFileScannerOsglBigLinesTest):

```java
package playground.fs.green;

import playground.fs.LogFileScanner;
import playground.fs.LogFileScannerTestBase;

public class GreenLogFileScannerOsglBigLinesTest extends LogFileScannerTestBase {
    @Override
    protected LogFileScanner getScanner() {
        return new GreenLogFileScannerOsglBigLines();
    }
}
```

### 添加 Benchmark 测试

添加 Benchmark 测试类. 参见 [`GreenLogFileScannerOsglBigLinesBenchmark`](https://gitee.com/greenlaw110/file-scanner/tree/master/src/main/java/playground/fs/benchmark/green/GreenLogFileScannerOsglBigLinesBenchmark):

```java
package playground.fs.benchmark.green;

import playground.fs.LogFileScanner;
import playground.fs.benchmark.LogFileScannerBenchmarkBase;
import playground.fs.green.GreenLogFileScannerOsglBigLines;

public class GreenLogFileScannerOsglBigLinesBenchmark extends LogFileScannerBenchmarkBase {

    private LogFileScanner scanner = new GreenLogFileScannerOsglBigLines();

    @Override
    protected LogFileScanner getScanner() {
        return scanner;
    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)