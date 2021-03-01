# 水印

生成base64格式的图片。

## 使用

> 生成水印图片的generateWatermark方法，兼容支付宝小程序。

- 浏览器端：

```sh
tnpm i @ali/h5-watermark -S
```

```js
import { generateWatermark } from "@ali/h5-watermark";
type showType = 'h5Page' | 'meetingDetail'
console.log(generateWatermark(config: object, onlyThePage?: showType));
// 可选参数onlyThePage若不传、则仅且“h5Page”为1时即显示水印，否则对onlyThePage精确匹配并且值等于1
```

- 支付宝小程序(rax)

```sh
tnpm i @ali/h5-watermark -S
```

 
 case 

```jsx
import { Component, createRef } from 'rax';
import View from 'rax-view';
import Watermark from '@ali/h5-watermark';

export default class Home extends Component {
  constructor(props) {
    super(props);
    this.refWatermark = createRef();
    this.state = {
      bg: "background: url('')",
      config: {
        watermark: {
          watermarkStatus: 1,
          targetPages: [
            {"name":"contactList","value":"1"},
            {"name":"contactDetail","value":"1"},
            {"name":"chat","value":"1"},
            {"name":"meetingDetail","value":"1"}
          ],
          contentType: [1, 2, 0],
          contentCustom: "IOS-H5",
          watermarkShowDensity: 0,
          fontSize: 0,
          fontColor: 1,
          fontDiaphaneity: "90",
          fontStyle: 1,
          userName: "测试04",
          account: "234435660"
        }
      }
    };
  }

  componentDidMount() {
    // this.refWatermark.current.generateWatermark方法的参数、为可选参数，不传或为'h5Page'或'meetingDetail'
    this.refWatermark.current.generateWatermark('h5Page').then((res)=> {
      console.log(res);
      this.setState({
        bg: `background: url(${res})`,
      });
    })
  }

  render() {
    const {config, bg} = this.state;
    return (
       
         
       
    );
  }
}
```

 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)