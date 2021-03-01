#### 用create-react-app创建一个项目
1. 执行 ```npm i create-react-app -g```
2. 执行 ```create-react-app redux-example```
3. 执行 ```cd redux-example```
4. 执行 ```npm start```
浏览器出现以下界面,说明项目创建好了并成功运行
![](https://upload-images.jianshu.io/upload_images/7177443-fd5f9d3d387e597a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

#### 创建相关组件
1. 在根目录下创建routes文件夹
2. 在routes下创建header和side文件夹
3. 在header和side下创建header的容器组件和ui组件,代码见https://gitee.com/huruqing/redux-example

#### redux相关配置
1. 安装redux和react-redux
```npm i redux react-redux --save-dev```
2. 创建side的reducer
```
// 创建action creator

export function showSideAction(payload) {
    return {
        type: 'SHOW-SIDE',
        payload,
    }
}

// 设置state初始值
const initState = {
    show: false
}

// reducer
export default (state=initState,action)=> {
    switch (action.type) {
        case 'SHOW-SIDE':
        return {
            ...state,
            show: action.payload
        }
       default:
          return state;
     }
}
```
header的reducer
```
// 创建action creator

export function setTitleAtion(payload) {
    return {
        type: 'SET-TITLE',
        payload,
    }
}

// 设置state初始值
const initState = {
    title: '卖座网'
}

// reducer 纯函数
export default (state=initState,action)=> {
    switch (action.type) {
        case 'SET-TITLE':
        return {
            ...state,
            title: action.payload
        }
       default:
        return state;
    }
}
```
#### 在目录的index.js配置prover和store
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import * as serviceWorker from './serviceWorker';
import { Privider } from 'react-redux';
import {createStore} from 'redux';
import { combineReducers } from 'redux';
import headerReducer from './routes/header/reducer';
import sideReducer from './routes/side/reducer';

const reducers = combineReducers({
    header: headerReducer,
    side: sideReducer
}) 
// 创建store
const store = createStore(reducers);


ReactDOM.render(
 
     
 ,
 document.getElementById('root'));

serviceWorker.unregister();
```

#### 把side下面的index.js改造成容器组件
```
/**
 * Side容器组件
 */
import React from 'react';
import View from './View'
import { connect } from 'react-redux';
import { showSideAction } from './reducer';
import { bindActionCreators } from 'redux';

class Side extends React.Component {

    render() {
        return  
    }
}

function mapStateToProps(state) {
	return {
		show: state.side.show
	}
}
function mapDispatchToProps(dispatch) {
	return {
		showSide: bindActionCreators(showSideAction,dispatch)
	}
}

export default connect(
	mapStateToProps,
	mapDispatchToProps
)(Side);
```

修改side下的View.js,它的显示和隐藏使用state里的show来控制
```
/**
 * Side UI组件
 */
import React from 'react';
import './View.css'


class View extends React.Component {

    render() {
    	let { show,showSide } = this.props;
    	if (show) {
    		return (
    			  {showSide(false)}}>
                     
                         首页 
                         影片 
                         影院 
                         E座卡 
                     
                 
    		)
    	} else {
    		return '';
    	}
        
    }
}


export default View;
```
#### 修改header容器组件和UI组件
```
/**
 * header容器组件
 */
import React from 'react';
import View from './View';
import { connect } from 'react-redux';
import { showSideAction } from '../side/reducer';
import { bindActionCreators } from 'redux';

class Header extends React.Component {
	
	render(){
		return  
	}
}

function mapStateToProps(state) {
	return {
		title: state.header.title,
		show: state.side.show
	}
}

function mapDispatchToProps(dispatch) {
	return {
		showSide: bindActionCreators(showSideAction, dispatch)
	}
}

export default connect(
	mapStateToProps,
	mapDispatchToProps
)(Header);

```

```
/**
 * headerUi组件
 */
import React from 'react';

class View extends React.Component {

	render() {
		let { title,showSide,show } = this.props;
		return ( 
			 {showSide(!show)}}>{show?'隐藏':'显示'}菜单 
			 {title} 
		 );
	}
}

export default View;

```

此demo地址: [https://gitee.com/huruqing/redux-example](https://gitee.com/huruqing/redux-example)









 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)