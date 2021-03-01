# vue-video

> A HTML5 video player component for Vue.js

## Demo

live demo is here: [https://hilongjw.github.io/vue-video/ocean.html](https://hilongjw.github.io/vue-video/ocean.html )
![](https://raw.githubusercontent.com/hilongjw/vue-video/master/preview.png)
![](https://raw.githubusercontent.com/hilongjw/vue-video/master/preview2.png)


## Instllation
```bash

npm i vue-video --save-dev

```


## Usage

```
// script
import myVideo from 'vue-video'
export default {
    data () {
        return {
            video: {
                sources: [{
                    src: 'http://covteam.u.qiniudn.com/oceans.mp4',
                    type: 'video/mp4'
                }],
                options: {
                    autoplay: true,
                    volume: 0.6,
                    poster: 'http://covteam.u.qiniudn.com/poster.png'
                }
            }
        }
    },
    components: {
        myVideo
    }
}
```

```html
 
     
         
              
         
     
 
```

## API

> sources

```
sources: [{
    // video uri
    src: 'http://covteam.u.qiniudn.com/oceans.mp4',
    // video meta type
    type: 'video/mp4'
}]

```

> options

```
options: {
    // autoplay
    autoplay: true,
    // default volume
    volume: 0.6,
    // poster (cover image)
    poster: 'http://covteam.u.qiniudn.com/poster.png'
}
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)