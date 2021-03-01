# unlib.js

Untitled's personal JavaScript library. Still under construction.

## Table of Contents

- [unlib.js](#unlibjs)
  - [Table of Contents](#table-of-contents)
  - [Description](#description)
  - [Usage](#usage)
    - [Install](#install)
    - [Build](#build)
    - [Pure JavaScript](#pure-javascript)
    - [TypeScript/ES6](#typescriptes6)
    - [Import a sub-module](#import-a-sub-module)
  - [Features (extending)](#features-extending)
    - [Random](#random)
    - [Generators](#generators)
    - [Binary](#binary)
    - [Time](#time)
      - [Timer](#timer)
      - [sleep](#sleep)
      - [timeoutify](#timeoutify)
    - [Promise](#promise)
    - [fs](#fs)
      - [mkdirs](#mkdirs)
      - [rm](#rm)
    - [Object](#object)
    - [Math](#math)
    - [TaskQueue](#taskqueue)
    - [Sync](#sync)
      - [EventBarrier](#eventbarrier)
      - [Lock](#lock)
      - [Semaphore](#semaphore)
    - [SortedList](#sortedlist)
    - [AsyncStreamReader](#asyncstreamreader)
    - [Constants](#constants)
  - [TODO](#todo)

## Description

A JavaScript library for personal use and learning. Written in [TypeScript](www.typescriptlang.org) (I am a newbie at TypeScript). This library contains several functions and classes which implement some easy-to-understand but non-easy-to-realize functions and mechanisms.

Anyone who finds a bug of this library is welcomed to open an issue :P.

## Usage

Assume that you have already cloned this repository to your local workspace.

### Install

```bash
git clone https://github.com/Luluno01/unlib.js.git && cd unlib.js && npm install
```

### Build

```bash
npm run build
```

### Pure JavaScript

```JavaScript
const unlib = require('./unlib.js')
```

or

```JavaScript
const { Random, Generators, Binary, Time, Promise, fs, Constants } = require('./unlib.js')
```

or

### TypeScript/ES6

```TypeScript
import * as unlib from './unlib.js'

console.log(unlib.Random.randint(1, 101))
```

or

```TypeScript
import { Random, Generators, Binary, Time, Promise, fs, Constants } from './unlib.js'

console.log(Random.randint(1, 101))
```

or

```TypeScript
import unlib from './unlib.js'

console.log(unlib.Random.randint(1, 101))
```

### Import a sub-module

Just simply `require` or `import-from` `'./unlib.js/build/sub-module'`.

e.g. Import the module `Random`:

```JavaScript
const Random = require('./unlib.js/build/Random')
```

or

```TypeScript
import Random from './unlib.js/build/Random'
```

## Features (extending)

This library has only 13 types of functionalities currently. I will implement some more ~~wheels~~ functionalities once I have to deal with some boring and repeated works.

Somehow, I can not provide detailed documentation for now. If you are interested in this library and require more details, feel free to open an issue to let me know which part of this library makes you confused or whatever you want to know about this repository.

### `Random`

Some helper functions to generate random numbers and sequences. You can also do some sampling or shuffle an array with `sample` and `shuffle`.

### `Generators`

Some generators/iterators including `range` and `charRange`, as well as a generator version of `Random.randSeq` which generates a random sequence of specified length.

### `Binary`

Some functions and classes for binary processing (circular shifting, complement, etc.)

### `Time`

Sub-module `Time` including `sleep` and `Timer`.

#### `Timer`

A timer class that calls your callback function at specified interval with an optional max timing duration.

#### `sleep`

Promise version of `setTimeout`.

#### `timeoutify`

Add a timeout constraint to asynchronous function.

### `Promise`

Some promisify functions.

### `fs`

Promise version of built-in object `fs` as well as some promisified custom functions.

#### `mkdirs`

Make a directory recursively.

#### `rm`

Remove a file or directory recursively.

### `Object`

Some other helpful functions and prototype functions enhancing built-in object `Object` including `getEnumerablePropertyDescriptors`, `assignAll`, `copy`, `append`, `update`, etc.

### `Math`

Factorial, permutation, combination calculation, sum, mean, variance calculation functions for now.

### `TaskQueue`

Task queue with max number of concurrent pending tasks limit.

### `Sync`

Event-synchronization mechanisms.

#### `EventBarrier`

Event barrier that brings `notify` and `waitFor` primitives to you.

#### `Lock`

Lock / Binary semaphore with optional maximum queue size constraint.

#### `Semaphore`

Generic and one-consumer counted semaphore.

### `SortedList`

Sorted list that maintains an always sorted list for you.

### `AsyncStreamReader`

Asynchronous stream reader (uses `async-await` for reading data).

### `Constants`

Some constants.

## TODO

- [ ] A new binary class using `Buffer` or `TypedArray` as storage instead of `number`.
- [ ] More constants.
- [ ] More detailed documentation.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)