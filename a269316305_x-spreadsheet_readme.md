# x-spreadsheet

[![npm package](https://img.shields.io/npm/v/x-data-spreadsheet.svg)](https://www.npmjs.org/package/x-data-spreadsheet)
[![NPM downloads](http://img.shields.io/npm/dm/x-data-spreadsheet.svg)](https://npmjs.org/package/x-data-spreadsheet)
[![NPM downloads](http://img.shields.io/npm/dt/x-data-spreadsheet.svg)](https://npmjs.org/package/x-data-spreadsheet)
[![Build passing](https://travis-ci.org/myliang/x-spreadsheet.svg?branch=master)](https://travis-ci.org/myliang/x-spreadsheet)
[![codecov](https://codecov.io/gh/myliang/x-spreadsheet/branch/master/graph/badge.svg)](https://codecov.io/gh/myliang/x-spreadsheet)
![GitHub](https://img.shields.io/github/license/myliang/x-spreadsheet.svg)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/myliang/x-spreadsheet.svg)
[![Join the chat at https://gitter.im/x-datav/spreadsheet](https://badges.gitter.im/x-datav/spreadsheet.svg)](https://gitter.im/x-datav/spreadsheet?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

> A web-based JavaScript spreadsheet

 
   
     
   
 

## Document
* en
* [zh-cn 中文](https://hondrytravis.github.io/x-spreadsheet-doc/)

## CDN
```html
 
  

 
   x_spreadsheet('#xspreadsheet');
 
```

## NPM

```shell
npm install x-data-spreadsheet
```

```html
  
```

```javascript
import Spreadsheet from "x-data-spreadsheet";
// If you need to override the default options, you can set the override
// const options = {};
// new Spreadsheet('#x-spreadsheet-demo', options);
const s = new Spreadsheet("#x-spreadsheet-demo")
  .loadData({}) // load data
  .change(data => {
    // save data to db
  });

// data validation
s.validate()
```

```javascript
// default options
{
  mode: 'edit', // edit | read
  showToolbar: true,
  showGrid: true,
  showContextmenu: true,
  view: {
    height: () => document.documentElement.clientHeight,
    width: () => document.documentElement.clientWidth,
  },
  row: {
    len: 100,
    height: 25,
  },
  col: {
    len: 26,
    width: 100,
    indexWidth: 60,
    minWidth: 60,
  },
  style: {
    bgcolor: '#ffffff',
    align: 'left',
    valign: 'middle',
    textwrap: false,
    strike: false,
    underline: false,
    color: '#0a0a0a',
    font: {
      name: 'Helvetica',
      size: 10,
      bold: false,
      italic: false,
    },
  },
}
```

## import | export xlsx

https://github.com/SheetJS/sheetjs/tree/master/demos/xspreadsheet#saving-data

thanks https://github.com/SheetJS/sheetjs

## Bind events
```javascript
const s = new Spreadsheet("#x-spreadsheet-demo")
// event of click on cell
s.on('cell-selected', (cell, ri, ci) => {});
s.on('cells-selected', (cell, { sri, sci, eri, eci }) => {});
// edited on cell
s.on('cell-edited', (text, ri, ci) => {});
```

## update cell-text
```javascript
const s = new Spreadsheet("#x-spreadsheet-demo")
// cellText(ri, ci, text, sheetIndex = 0)
s.cellText(5, 5, 'xxxx').cellText(6, 5, 'yyy').reRender();
```

## get cell and cell-style
```javascript
const s = new Spreadsheet("#x-spreadsheet-demo")
// cell(ri, ci, sheetIndex = 0)
s.cell(ri, ci);
// cellStyle(ri, ci, sheetIndex = 0)
s.cellStyle(ri, ci);
```

## Internationalization
```javascript
// npm 
import Spreadsheet from 'x-data-spreadsheet';
import zhCN from 'x-data-spreadsheet/dist/locale/zh-cn';

Spreadsheet.locale('zh-cn', zhCN);
new Spreadsheet(document.getElementById('xss-demo'));
```
```html
 
 
  
  

 
  x_spreadsheet.locale('zh-cn');
 
```

## Features
  - Undo & Redo
  - Paint format
  - Clear format
  - Format
  - Font
  - Font size
  - Font bold
  - Font italic
  - Underline
  - Strike
  - Text color
  - Fill color
  - Borders
  - Merge cells
  - Align
  - Text wrapping
  - Freeze cell
  - Functions
  - Resize row-height, col-width
  - Copy, Cut, Paste
  - Autofill
  - Insert row, column
  - Delete row, column
  - hide row, column
  - multiple sheets
  - print
  - Data validations

## Development

```sheel
git clone https://github.com/myliang/x-spreadsheet.git
cd x-spreadsheet
npm install
npm run dev
```

Open your browser and visit http://127.0.0.1:8080.

## Browser Support

Modern browsers(chrome, firefox, Safari).

## LICENSE

MIT


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)