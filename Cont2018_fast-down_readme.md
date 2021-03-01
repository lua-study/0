# fast-down

nodejs 大文件分片下载工具，使用进程process的方式分片下载，文件合并使用filestream，不受nodejs单进程的内存限制可以下载较大的文件。

## 用法

## 安装

全局安装

```
npm install fast-down
```
如果要全局安装请加上-g参数

全局安装模式下，可以直接当做下载工具使用：

```
fast-down "http://xxx/big-file.zip" big-file.zip 4
```
表示４个分片并发下载

在项目中引用：

```
const fast_down = require('fast-down');

(async() => {
        var url = 'http://bla..../file.mp4';
        var filepath = 'filename.mp4';
        var con_num = 4;

        let stime = new Date().getTime();
        console.log('start download, concurrency: ' + con_num);

        var downloader = new fast_down.Downloader(url, filepath, {
            'concurrency': con_num,
            'progress_throttle': 4000
        });

        downloader.onProgress((pct, tinfo, pinfo) => {
            console.log('progress:',pct);
        });

        let ret = await downloader.download();

        console.log('download ' + (ret ? 'success' : 'fail') + ', cost: ' + (new Date().getTime() - stime) + 'ms');
})();
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)