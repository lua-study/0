# el-form-renderer

[![Build Status](https://badgen.net/travis/FEMessage/el-form-renderer/master)](https://travis-ci.com/FEMessage/el-form-renderer)
[![NPM Download](https://badgen.net/npm/dm/@femessage/el-form-renderer)](https://www.npmjs.com/package/@femessage/el-form-renderer)
[![NPM Version](https://badgen.net/npm/v/@femessage/el-form-renderer)](https://www.npmjs.com/package/@femessage/el-form-renderer)
[![NPM License](https://badgen.net/npm/license/@femessage/el-form-renderer)](https://github.com/FEMessage/el-form-renderer/blob/master/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/FEMessage/el-form-renderer/pulls)
[![Automated Release Notes by gren](https://img.shields.io/badge/%F0%9F%A4%96-release%20notes-00B2EE.svg)](https://github-tools.github.io/github-release-notes/)

![](https://i.loli.net/2019/11/14/Nz6n9l7KixqIHsa.png)

[中文文档](./README-zh.md)

## Table of Contents

- [Introduction](#introduction)
  - [WHAT](#what)
  - [WHY](#why)
- [Features](#features)
- [Links](#links)
- [Quick Start](#quick-start)
- [Inspiration](#inspiration)
- [Contributing](#contributing)
- [Contributors](#contributors)
- [License](#license)

## Introduction

### WHAT

`el-form-renderer` is based on [element-ui](https://github.com/ElemeFE/element), but not limited [element-ui](https://github.com/ElemeFE/element) components. On the basis of completely inheriting the form attribute of element-ui, extension is made. Some non-form components or custom components, such as picture uploading and rich text editor, can also be integrated, thus, users can render a complete form by using a piece of json.

### WHY

In our daily development, there are lots page with form, and usually the form structure is similar, the logic is repeated. el-form-renderer does not have complicated logic. It only convert JSON to render form item, save time and energy to write business logic, and reduce duplicate code.

## Features

- Render form with json
- Support integrate with custom components
- Support batch update form data with updateForm method
- Support setOptions method, dynamically change select options
- Content support `inputFormat` , `outputFormat` , `trim` to process component's input and output values

[⬆Back to Top](#table-of-contents)

## Links

- [Docs](https://femessage.github.io/el-form-renderer/)
- [Guide to developing custom component](https://github.com/femessage/el-form-renderer/blob/dev/docs/guide-en-custom-component.md)
- [Setting validation rules in custom component](https://github.com/FEMessage/el-form-renderer/blob/dev/docs/guide-en-custom-rules-in-custom-component.md)
- [fem-vscode-helper](https://marketplace.visualstudio.com/items?itemName=FEMessage.fem-vscode-helper)

[⬆Back to Top](#table-of-contents)

## Quick Start

```sh
yarn add @femessage/el-form-renderer
```

```html
 
    
 
 
  import ElFormRenderer from '@femessage/el-form-renderer'
  export default {
    components: {
      ElFormRenderer
    },
    data() {
      return {
        content: []
      }
    }
  }
 
```

[⬆Back to Top](#table-of-contents)

## Inspiration

thanks to [element-patch](https://github.com/leezng/element-patch)

## Contributing

For those who are interested in contributing to this project, such as:

- report a bug
- request new feature
- fix a bug
- implement a new feature

Please refer to our [contributing guide](https://github.com/FEMessage/.github/blob/master/CONTRIBUTING.md).

[⬆ Back to Top](#table-of-contents)

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

 
 
        Alvin     💻   👀   🐛   📝   🤔        levy     👀   🚇   🤔        EVILLT     💻   🐛   📝   🤔        Donald Shen     💻   📖   💡   📝        ColMugX     💻   ⚠️   📖        OuZuYu     🐛        Han     💻   📖    

 

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

## License

[MIT](./LICENSE)

[⬆ Back to Top](#table-of-contents)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)