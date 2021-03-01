   
 VueDraggableResizable 2 

[![Latest Version on NPM](https://img.shields.io/npm/v/vue-draggable-resizable.svg?style=flat-square)](https://npmjs.com/package/vue-draggable-resizable)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![npm](https://img.shields.io/npm/dt/vue-draggable-resizable.svg?style=flat-square)](https://www.npmjs.com/package/vue-draggable-resizable)

> Vue2 Component for draggable and resizable elements.

If you are looking for the version 1 of the component, it is available on the [v1 branch](https://github.com/mauricius/vue-draggable-resizable/tree/v1).

## Table of Contents

* [Features](#features)
* [Live Playground](#live-playground)
* [Install and basic usage](#install-and-basic-usage)
  * [Props](#props)
  * [Events](#events)
  * [Styling](#styling)
* [Contributing](#contributing)
* [License](#license)

### Features

* No dependencies
* Use draggable, resizable or both
* Define handles for resizing
* Restrict size and movement to parent element or custom selector
* Snap element to custom grid
* Restrict drag to vertical or horizontal axis
* Maintain aspect ratio
* Touch enabled
* Use your own classes
* Provide your own markup for handles

### Live Playground

For examples of the component go to the [live playground](https://mauricius.github.io/vue-draggable-resizable/)

Alternatively you can run the playground on your own computer:

* Clone this repository
* `npm install`
* `npm run storybook`
* Visit [http://localhost:9001/](http://localhost:9001/)

---

## Install and basic usage

```bash
$ npm install --save vue-draggable-resizable
```


Register the component

```js
import Vue from 'vue'
import VueDraggableResizable from 'vue-draggable-resizable'

// optionally import default styles
import 'vue-draggable-resizable/dist/VueDraggableResizable.css'

Vue.component('vue-draggable-resizable', VueDraggableResizable)
```

You may now use the component in your markup

```vue
 
   
     
       Hello! I'm a flexible component. You can drag me around and you can resize me. 
      X: {{ x }} / Y: {{ y }} - Width: {{ width }} / Height: {{ height }} 
     
   
 

 
import VueDraggableResizable from 'vue-draggable-resizable'

export default {
  data: function () {
    return {
      width: 0,
      height: 0,
      x: 0,
      y: 0
    }
  },
  methods: {
    onResize: function (x, y, width, height) {
      this.x = x
      this.y = y
      this.width = width
      this.height = height
    },
    onDrag: function (x, y) {
      this.x = x
      this.y = y
    }
  }
}
 
```

### Props

#### className
Type: `String` 
Required: `false` 
Default: `vdr`

Used to set the custom `class` of a draggable-resizable component.

```html
 
```

#### classNameDraggable
Type: `String` 
Required: `false` 
Default: `draggable`

Used to set the custom `class` of a draggable-resizable component when `draggable` is enable.

```html
 
```

#### classNameResizable
Type: `String` 
Required: `false` 
Default: `resizable`

Used to set the custom `class` of a draggable-resizable component when `resizable` is enable.

```html
 
```

#### classNameDragging
Type: `String` 
Required: `false` 
Default: `dragging`

Used to set the custom `class` of a draggable-resizable component when is dragging.

```html
 
```

#### classNameResizing
Type: `String` 
Required: `false` 
Default: `resizing`

Used to set the custom `class` of a draggable-resizable component when is resizing.

```html
 
```

#### classNameActive
Type: `String` 
Required: `false` 
Default: `active`

Used to set the custom `class` of a draggable-resizable component when is active.

```html
 
```

#### classNameHandle
Type: `String` 
Required: `false` 
Default: `handle`

Used to set the custom common `class` of each handle element. This way you can style each handle individually using the selector ` - `, where `handle code` identifies one of the handles provided by the `handle` prop.

So for example, this component:

```html
  
```

renders the following:

```html
 
    
    
    
  [...]
 
```

#### disableUserSelect
Type: `Boolean` 
Required: `false` 
Default: `true`

By default, the component adds the style declaration `'user-select:none'` to itself to prevent text selection during drag. You can disable this behaviour by setting this prop to `false`.

```html
 
```

#### enableNativeDrag
Type: `Boolean` 
Required: `false` 
Default: `false`

By default, the browser's native drag and drop funcionality (usually used for images and some other elements) is disabled, as it may conflict with the one provided by the component. If you need, for whatever reason, to have this functionality back you can set this prop to `true`.

```html
 
```

#### active
Type: `Boolean` 
Required: `false` 
Default: `false`

Determines if the component should be active or not. The prop reacts to changes and also can be used with the `sync`[modifier](https://vuejs.org/v2/guide/components.html#sync-Modifier) to keep the state in sync with the parent. You can use along with the `preventDeactivation` prop in order to fully control the active behavior from outside the component.

```html
 
```

#### preventDeactivation
Type: `Boolean` 
Required: `false` 
Default: `false`

Determines if the component should be deactivated when the user clicks/taps outside it.

```html
 
```

#### draggable
Type: `Boolean` 
Required: `false` 
Default: `true`

Defines it the component should be draggable or not.

```html
 
```

#### resizable
Type: `Boolean` 
Required: `false` 
Default: `true`

Defines it the component should be resizable or not.

```html
 
```

#### w
Type: `Number` 
Required: `false` 
Default: `200`

Define the initial width of the element.

```html
 
```

#### h
Type: `Number` 
Required: `false` 
Default: `200`

Define the initial height of the element.

```html
 
```

#### minWidth
Type: `Number` 
Required: `false` 
Default: `50`

Define the minimal width of the element.

```html
 
```

#### minHeight
Type: `Number` 
Required: `false` 
Default: `50`

Define the minimal height of the element.

```html
 
```

#### maxWidth
Type: `Number` 
Required: `false` 
Default: `null`

Define the maximum width of the element.

```html
 
```

#### maxHeight
Type: `Number` 
Required: `false` 
Default: `null`

Define the maximum height of the element.

```html
 
```

#### x
Type: `Number` 
Required: `false` 
Default: `0`

Define the initial x position of the element.

```html
 
```

#### y
Type: `Number` 
Required: `false` 
Default: `0`

Define the initial y position of the element.

```html
 
```

#### z
Type: `Number|String` 
Required: `false` 
Default: `auto`

Define the zIndex of the element.

```html
 
```

#### handles
Type: `Array` 
Required: `false` 
Default: `['tl', 'tm', 'tr', 'mr', 'br', 'bm', 'bl', 'ml']`

Define the array of handles to restrict the element resizing:
* `tl` - Top left
* `tm` - Top middle
* `tr` - Top right
* `mr` - Middle right
* `br` - Bottom right
* `bm` - Bottom middle
* `bl` - Bottom left
* `ml` - Middle left

```html
 
```

#### axis
Type: `String` 
Required: `false` 
Default: `both`

Define the axis on which the element is draggable. Available values are `x`, `y` or `both`.

```html
 
```

#### grid
Type: `Array` 
Required: `false` 
Default: `[1,1]`

Define the grid on which the element is snapped.

```html
 
```

#### parent
Type: `Boolean | String` 
Required: `false` 
Default: `false`

Restricts the movement and the dimensions of the component to the parent (if `true` is provided), or to an element identified by a valid CSS selector.

```html
 
```

```html
 
```

#### dragHandle
Type: `String` 
Required: `false`

Defines the selector that should be used to drag the component.

```html
 
```

#### dragCancel
Type: `String` 
Required: `false`

Defines a selector that should be used to prevent drag initialization.

```html
 
```

#### lockAspectRatio
Type: `Boolean` 
Required: `false` 
Default: `false`

The `lockAspectRatio` property is used to lock aspect ratio. This property doesn't play well with `grid`, so make sure to use only one at a time.

```html
 
```

#### onDragStart
Type: `Function` 
Required: `false` 
Default: `null`

Called when dragging starts (element is clicked or touched). If `false` is returned by any handler, the action will cancel. You can use this function to prevent bubbling of events.

```html
 
```

```js
function onDragStartCallback(ev){
   ...
   // return false; — for cancel
}
```


#### onResizeStart
Type: `Function` 
Required: `false` 
Default: `null`

Called when resizing starts (handle is clicked or touched). If `false` is returned by any handler, the action will cancel.

```html
 
```

```js

function onResizeStartCallback(handle, ev){
   ...
   // return false; — for cancel
}
```
---

### Events

#### activated

Parameters: `-`

Called whenever the component gets clicked, in order to show handles.

```html
 
```

#### deactivated

Parameters: `-`

Called whenever the user clicks anywhere outside the component, in order to deactivate it.

```html
 
```

#### resizing

Parameters:
* `left` the X position of the element
* `top` the Y position of the element
* `width` the width of the element
* `height` the height of the element

Called whenever the component gets resized.

```html
 
```

#### resizestop

Parameters:
* `left` the X position of the element
* `top` the Y position of the element
* `width` the width of the element
* `height` the height of the element

Called whenever the component stops getting resized.

```html
 
```

#### dragging

Parameters:
* `left` the X position of the element
* `top` the Y position of the element

Called whenever the component gets dragged.

```html
 
```

#### dragstop

Parameters:
* `left` the X position of the element
* `top` the Y position of the element

Called whenever the component stops getting dragged.

```html
 
```

---

### Styling

You can style the component using appropriate class names passed as props to the component. Moreover you can replace the default styles for the handles, provided in the source file `vue-draggable-resizable.css`, but you should take care to define position and size for them. The default classes for handles are `handle` and `handle-tl`, `handle-br` and so on.

The component also provides [named slots](https://vuejs.org/v2/guide/components-slots.html#Named-Slots) for each handle, so you can use your markup inside each one.

## Thanks

Thanks to @kirillmurashov for his work on [vue-drag-resize](https://github.com/kirillmurashov/vue-drag-resize) component.

## Security

If you discover any security related issues, please email maurizio.bonani@gmail.com instead of using the issue tracker.

## Contributing

Any contribution to the code or any part of the documentation and any idea and/or suggestion are very welcome.

``` bash
# serve with hot reload at localhost:8080
npm run serve

# distribution build
npm run build

# build the storybook docs into gh-pages
npm run gh-pages:build

# run unit tests
npm run unit

# run storybook at localhost:9001
npm run storybook
```

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)