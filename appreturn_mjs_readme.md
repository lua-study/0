# mjs - 小巧方便的音乐播放js类

### 项目介绍

轻巧方便的music封装类库，利用它可以快速打造一个功能全，个性化的music播放器

提供了很多播放事件以及回调，确保你能更加灵活的使用它

演示地址：https://mjs.uquhu.cn

下载地址：https://gitee.com/lovefc/mjs


 
    

### 安装教程
直接下载源码或者使用git克隆

### 使用方法(具体看案例)

    // 实例化mjs类库
    let music = new mjs();

    // 歌词显示的回调函数，写在init函数调用前面
    music.lycCallback = (lycText) => {
        $('#lyctext').html(lycText);
    };

    // 切歌的回调，写在init函数调用前面
    music.switchCallback = (attr) => {
        music.autoPlay(); // 可以在这里写 自动播放
        $('#songname').html(attr.title + "-" + attr.author);
        $('#pic').html(' ');
    };

    music.playVolume(0.5); // 初始音量，写在init函数调用前面

    music.orderMusic(1); // 定义初始循环方式，写在init函数调用前面, 0为列表循环，1为随机循环，2为单曲循环
    
    // 传入歌曲json，初始化
    // json为多维json
    //[{'title':'歌曲名称','author':'作者','pic':'歌曲封面','url':'播放直链地址'}]
    music.init(musiclist);

    // 获取当前歌曲的播放时间和进度的回调，写在init函数后面
    music.timeCallback = (music) => {
        $('#times').html(music.nowtime + "/" + music.alltime);
    };

    // 播放
    $("#play").click(function () {
        music.autoPlay();
    });
    // 暂停
    $("#stop").click(function () {
        music.stopPlay();
    });

    // 随机循环
    $("#order").click(function () {
        music.orderMusic(1);
        alert('开启随机循环成功');
    });

    // 单曲循环
    $("#order2").click(function () {
        music.orderMusic(2);
        alert('开启单曲循环成功');
    });

    // 列表循环
    $("#order3").click(function () {
        music.orderMusic(0);
        alert('开启列表循环成功');
    });

    // 下一首
    $("#xia").click(function () {
        music.nextMusic(function (music) {
            // 播放下一首的事件回调
        });
    });

    // 上一首
    $("#shang").click(function () {
        music.prevMusic(function (music) {
            // 播放上一首的事件回调
        });
    });

    // 放大音量
    $("#da").click(function () {
        let num = 1;
        music.playVolume(num, function (num) {
            console.log('放大音量' + num);
        });
    });

    // 缩小音量
    $("#xiao").click(function () {
        music.playVolume(0.3, function (num) {
            console.log('缩小音量' + num);
        });
    });

    // 跳到开头
    $("#kaitou").click(function () {
        music.playProgress(1);
    });

    // 跳到中间
    $("#zhongjian").click(function () {
        music.playProgress(50);
    });

    // 跳到结尾
    $("#mowei").click(function () {
        music.playProgress(98);
    });


    // 加快速度,最大为200
    $("#jiakuai").click(function () {
        music.playRate(200);
    });

    // 正常速度
    $("#zhengchang").click(function () {
        music.playRate(100);
    });

    // 减慢速度
    $("#bianman").click(function () {
        music.playRate(50);
    });


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)