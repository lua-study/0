# evil-eval

A JavaScript interpreter written in JavaScript.

## Why

Yout might working in a JavaScript environment where `eval()` and `new Function()` are not allowed (eg: WeChat Mini Program), and you probably have a good reason to use it.

## Usage

```js
import { runInContext } from 'evil-eval';

const code = `
    function hello(name) {
        return 'Hello ' + (name || defaultName) + '!';
    }

    module.exports = hello;
`;
const sandbox = { defaultName: 'World' };
const hello = runInContext(code, sandbox);
hello();
```

## Inspired by

- [jsjs](https://github.com/bramblex/jsjs)
- [vm.js](https://github.com/axetroy/vm.js)

## License

MIT


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)