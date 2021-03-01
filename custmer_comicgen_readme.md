# comicgen

 
We love comics. We badly wanted to create comic strips. But there was one
problem. Some of us can't draw a straight line for nuts.

But why should that stop us from creating comics? So here's a gift to ourselves
and the world &mdash; a **Comic Creator**.

We are sure you'd love the company of our friends [Dee](#?name=dee) &
[Dey](#?name=dey). Go on & have some fun.
 

 
## Installation

Load the comicgen library by adding this line in your HTML page's ` `:

```html
 
  
```

You can also install comicgen locally using `npm` or `yarn`:

```bash
npm install comicgen
yarn install comicgen
```

... and then include:

```html
 
  
```

## Usage

To embed a character, add:

```html
  
```

This inserts the following image in your HTML.
You can embed it anywhere, including inside an ` ` element.

![name=dee angle=straight emotion=smile pose=thumbsup](docs/dee-straight-smile-thumbsup.png)

The character is defined by 4 attributes:

- `name`: the name of the character (e.g. `dee`, `dey`)
- `angle`: which angle are they are facing (e.g. `straight`, `side`)
- `emotion`: what emotion their face expresses (e.g. `sad`, `happy`)
- `pose`: what pose their body shows (e.g. `pointingup`, `holdinglaptop`)

The list of valid combinations are available on the
[comicgen interactive gallery](https://gramener.com/comicgen/).

The characters are drawn on a 500 x 600 canvas. You can change this using:

- `width`: width of the image. Default: 500
- `height`: height of the image. Default: 600
- `x`: left position or x-offset. Default: 0
- `y`: top position or y-offset. Default: 1
- `mirror`: shsow mirror image. Value can be empty string or 1. Default: empty string
- `scale`: how much larger to make the image. Default: 1

Comicgen is tested on Chrome, Edge, and Firefox. It does not work on Internet Explorer.

## Composition

To combine multiple characters in a panel, embed them in an ` ` element.

You can change the `x`, `y`, `width`, `height`, `mirror` and `scale` to position each character.

```html
 
    
    
 
```

![Dee and Dey together](docs/dee-and-dey-together.png)

You can resize the combined image by changing the `width` and `height` of the
SVG container.

```html
 
    
    
 
```

Set `viewBox` to the width and height of the comicgen elements. Then you can set
the outer `width` and `height` to anything.

![Dee and Dey scaled down](docs/dee-and-dey-meet.png)

This normally scales the image to fit both the width and height. To fit only one
side, use [preserveAspectRatio](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/preserveAspectRatio).
For example, `preserveAspectRatio="xMidYMin slice"` in this case fits to width
and slices the height, preserving the top (YMin) of the image.

```html
 
    
    
 
```

![Dee and Dey fit width](docs/dee-and-dey-slice.png)

## Panels

[comicgen.css](https://cdn.jsdelivr.net/npm/comicgen/dist/comicgen.min.css)
provides 2 classes for layout:

- `comic-panel`
- `comic-row`

Use `class="comic-panel"` to can embed characters in a thick grey border. For example

```html
 
    
 
```

![Dee in a panel](docs/dee-panel.png)

Panels are typically placed inside a `class="comic-row"`:

Here's an example with 2 panels. The second panel has 2 characters.

```html
 
   
      
   
   
     
        
        
     
   
 
```

![Dee and Dey in panels](docs/dee-and-dey-panels.png)

You can override the panel's background, border width and color using CSS
variables in your stylesheet.

```css
:root {
  --comic-background: #eee;     /* Light grey background. Default: transparent */
  --comic-border-color: #ccc;   /* Light grey border. Default: grey */
  --comic-border-width: 1px;    /* Thin border. Default 2px */
}
```

![Dee and Dey in panels, with CSS styling](docs/dee-and-dey-panels-styled.png)


## Captions

[comicgen.css](https://cdn.jsdelivr.net/npm/comicgen/dist/comicgen.min.css)
provides `comic-caption-top` and `comic-caption-bottom` to add captions inside
a `.comic-panel`.

For example, this defines a caption on top:

```html
 
   Hi! I'm Dee. 
    
 
```

![Dee with a caption on top](docs/dee-caption-top.png)

... or the bottom:

```html
 
   Hi! I'm Dee. 
    
 
```

![Dee with a caption at the bottom](docs/dee-caption-bottom.png)

You can override the caption's background, font and padding using CSS variables
in your stylesheet.

```css
:root {
  --comic-caption-background: #eee;         /* Light grey background. Default: white */
  --comic-caption-font: Neucha, cursive;    /* Custom Google font. Default: cursive */
  --comic-caption-padding: 0.25rem 0.5rem;  /* Custom margin. Default: 0.25rem */
}
.comic-caption-top, .comic-caption-bottom { /* Apply any custom styles you want */
  text-transform: uppercase;
}
```

![Dee with a caption on top, styled with CSS](docs/dee-caption-top-styled.png)

[Google fonts has handwriting fonts](https://fonts.google.com/?category=Handwriting)
that can be used for the caption lettering.

## Strips

You can combine [captions](#captions) with [panels](#panels) to create a strip
like this:

```html
 
   
     Hi! I'm Dee. 
      
   
   
     I'm in a comic strip called Dee & Dey. 
      
   
   
     And this is Dey, my co-star on this strip. 
     
        
        
     
   
 
```

![Dee and Dey with captions](docs/dee-and-dey-captions.png)

 


## API

To explicitly run comicgen on a selector, run `comicgen(selector)`. This lets
you dynamically create or change a a character.

Here's an example in jQuery showing how you can create a character dynamically:

```js
// Add the character
$('  ').appendTo('body')
// Call comicgen()
comicgen('.new')
```

![Dynamic character rendered via JS](docs/dee-sad-yuhoo-400-300.png)

You can pass an `options` parameter to `comicgen()` to provide default values.
For example:

```js
$('  ').appendTo('body')
comicgen('.new', {
  name: 'dey',      // Set the default name.   overrides this
  emotion: 'sad',   // Set the default emotion
  pose: 'yuhoo',    // Set the default pose, etc
  width: 400,
  height: 300
})
```

![Dynamic character rendered via JS, with default options](docs/dee-sad-yuhoo-400-300.png)

## Release

To publish a new version on npm:

```bash
# Update package.json version
# Run tests on dev branch
npm run lint
npm test
npm run test-chrome
npm run test-edge
npm run test-firefox

# Ensure that there are no build errors on the server
git commit . -m"DOC: Release version x.x.x"
git push

# Merge into dev branch
git checkout master
git merge dev
git tag -a v0.x.x -m"Add a one-line summary"
git push --follow-tags

# Publish to https://www.npmjs/package/comicgen maintained by @sanand0
npm publish

git checkout dev
```


 

## Credits

- Library developed by Kriti Rohilla   and S Anand  
- Conceived & designed by Ramya Mylavarapu   & Richie Lionell  

### Character credits

- Dee: By Ramya Mylavarapu  
  under [CC0 license](https://creativecommons.org/choose/zero/)
- Dey: By Ramya Mylavarapu  
  under [CC0 license](https://creativecommons.org/choose/zero/)
- [Humaaans](https://www.humaaans.com/): By [Pablo Stanley](https://twitter.com/pablostanley)
  under [CC-BY license](https://creativecommons.org/licenses/by/4.0/)

 

 
## Contributing

We'd love your help in improving Comicgen.

If you're a developer, you could help
[fix bugs](https://github.com/gramener/comicgen/labels/bug) or
[add features](https://github.com/gramener/comicgen/labels/enhancements).
Some issues are marked
[help wanted](https://github.com/gramener/comicgen/labels/help%20wanted).
These are a good starting point.

If you're a designer, you could help add new characters.

### Add new characters

Characters are made of 1 or more SVG images.

The easiest way to create a character is to draw a dozen SVGs and save them as
individual files **of the same dimensions**. For example:

![Series of SVG images for a character](docs/character-single-images.png)

A better way would be to break up the character into different parts. For
example, you could draw faces with different emotions and save them under an
`faces/` folder:

![Faces for a character](docs/character-faces.png)

Then you could draw the bodies under a `bodies/` folder:

![Bodies for a character](docs/character-bodies.png)

If you do this, you must make sure that:

- All faces have the **same dimensions**, and are at the **same position** within the SVG
- All bodies have the **same dimensions**, and are at the **same position** within the SVG
- When you super-impose any face on any body, the **images should align**.

You can choose to break up the images in any number of ways. For example:

- `faces/`, `bodies/`
- `face/`, `trunk/`, `leg`, `shoes`
- `hair`, `face`, `eyes`, `mouth`, `trunk/`, `legs/`

The more combinations you have, the more complex your image becomes. You could
start small and then add variety.

### Submit new characters

Give your character a name (e.g. "Ant Man"). Save the SVG files under a folder
with the character name (e.g. "ant-man" - lower-case, use hyphens as separator).
Add this folder under the
[files/](https://github.com/gramener/comicgen/tree/master/files/) folder.

Then [send a pull request](https://help.github.com/en/articles/creating-a-pull-request)
or email S Anand  .

When doing this, please mention one of the following:

- "I release these images under the [CC0](https://creativecommons.org/choose/zero/) license", OR
- "I release these images under the [CC-BY](https://creativecommons.org/licenses/by/4.0/) license"


 

 
## Share

 
   
      
   
   
      
   
   
      
   
   
      
   
 
 

 
 
 
    Share on Twitter  
    Share on Facebook 
    Share on LinkedIn 
    Fork on Github  
 
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)