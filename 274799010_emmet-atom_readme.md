# Emmet plugin Atom editor

[Emmet](http://emmet.io) support for [Atom](http://atom.io).

## Installation

* In Atom, open *Preferences* (*Settings* on Windows)
* Go to *Install* section
* Search for `Emmet` package. Once it found, click `Install` button to install package.

### Manual installation

You can install the latest Emmet version manually from console:

```bash
cd ~/.atom/packages
git clone https://github.com/emmetio/emmet-atom
cd emmet-atom
npm install
```

Then restart Atom editor.

## Features:

* Expand abbreviations by  Tab  key.
* Multiple cursor support: most [Emmet actions](http://docs.emmet.io/actions/) like Expand Abbreviation, Wrap with Abbreviation, Update Tag can run in multi-cursor mode.
* Interactive actions (Interactive Expand Abbreviation, Wrap With Abbreviation, Update Tag) allows you to preview result real-time as you type.
* Better tabstops in generated content: when abbreviation expanded, hit  Tab  key to quickly traverse between important code points.
* [Emmet v1.1 core](http://emmet.io/blog/beta-v1-1/).

Please report any problems at [issue tracker](https://github.com/emmetio/emmet-atom/issues).

## Tab key

Currently, Emmet expands abbreviations by Tab key only for HTML, CSS, Sass/SCSS and LESS syntaxes. Tab handler scope is limited because it overrides default snippets.

If you want to make Emmet expand abbreviations with Tab key for other syntaxes, you can do the following:

1. Use *Open Your Keymap* menu item to open your custom `keymap.cson` file.
2. Add the following section into it:

```coffee
'atom-text-editor[data-grammar="YOUR GRAMMAR HERE"]:not([mini])':
    'tab': 'emmet:expand-abbreviation-with-tab'
```

Replace `YOUR GRAMMAR HERE` with actual grammar attribute value. The easiest way to get grammar name of currently opened editor is to open DevTools and find corresponding ` ` element: it will contain `data-grammar` attribute with value you need. For example, for HTML syntax it’s a `text html basic`.

You can add as many sections as you like for different syntaxes. Note that default snippets will no longer work, but you can add [your own snippets in Emmet](http://docs.emmet.io/customization/).

## Default Keybindings

You can change these in Preferences > Keybindings.

Command | Darwin | Linux/Windows
------- | ------ | -------------
Expand Abbreviation |  tab  or  shift  +  ⌘  +  e  |  tab  or  ctrl  +  e 
Expand Abbreviation (interactive) |  alt  +  ⌘  +  enter  |  ctrl  +  alt  +  enter 
Wrap with Abbreviation |  ctrl  +  w  |  ctrl  +  alt  +  w 
Balance (outward) |  ctrl  +  d  |  ctrl  +  shift  +  e 
Balance (inward) |  alt  +  d  |  ctrl  +  shift  +  0 
Go to Matching Pair |  ctrl  +  alt  +  j  |  ctrl  +  alt  +  j 
Next Edit Point |  ctrl  +  →  |  ctrl  +  alt  +  → 
Previous Edit Point |  ctrl  +  ←  |  ctrl  +  alt  +  ← 
Select Next Item |  ctrl  +  shift  +  →  |  ctrl  +  shift  +  . 
Select Previous Item |  ctrl  +  shift  +  ←  |  ctrl  +  shift  +  , 
Toggle Comment |  ⌘  +  /  |  ctrl  +  shift  +  / 
Split/Join Tag |  shift  +  ⌘  +  j  |  ctrl  +  shift  +  ` 
Remove Tag |  ⌘  +  '  |  ctrl  +  shift  +  ; 
Evaluate Math Expression |  shift  +  ⌘  +  y  |  ctrl  +  shift  +  y 
Increment Number by 0.1 |  ctrl  +  alt  +  ↑  |  alt  +  ↑ 
Decrement Number by 0.1 |  ctrl  +  alt  +  ↓  |  alt  +  ↓ 
Increment Number by 1 |  ctrl  +  alt  +  ⌘  +  ↑  |  ctrl  +  ↑ 
Decrement Number by 1 |  ctrl  +  alt  +  ⌘  +  ↓  |  ctrl  +  ↓ 
Increment Number by 10 |  ctrl  +  alt  +  ⌘  +  shift  +  ↑  |  shift  +  alt  +  ↑ 
Decrement Number by 10 |  ctrl  +  alt  +  ⌘  +  shift  +  ↓  |  shift  +  alt  +  ↓ 
Reflect CSS value |  shift  +  ⌘  +  r  |  ctrl  +  shift  +  r 
Update Image Size |  ctrl  +  i  |  ctrl  +  u 
Encode/Decode image to data:URL |  ctrl  +  shift  +  i  |  ctrl  +  ' 
Update Tag |  ctrl  +  shift  +  u  |  ctrl  +  shift  +  ' 
Merge Lines |  shift  +  ⌘  +  m  |  ctrl  +  shift  +  m 

All actions and their keyboard shortcuts are available under Packages > Emmet menu item.

## Extensions support

You can easily [extend](http://docs.emmet.io/customization/) Emmet with new actions and filters or customize existing ones. In Preferences > Emmet, set Extensions path to folder with Emmet extensions. By default, it’s `~/emmet`, e.g. `emmet` folder in your system HOME folder.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)