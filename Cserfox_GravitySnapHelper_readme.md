# GravitySnapHelper

A SnapHelper that snaps a RecyclerView to an edge.

## Setup

Add this to your build.gradle:

```groovy
implementation 'com.github.rubensousa:gravitysnaphelper:2.2.0'
```

## How to use

You can either create a GravitySnapHelper, or use GravitySnapRecyclerView.

If you want to use GravitySnapHelper directly, 
you just need to create it and attach it to your RecyclerView:

```kotlin
val snapHelper = GravitySnapHelper(Gravity.START)
snapHelper.attachToRecyclerView(recyclerView)
```

If you want to use GravitySnapRecyclerView, you can use the following xml attributes for customisation:

```xml
 
 
 
 
 
 
```

Example:

```xml
 
```

## Start snapping

```kotlin
val snapHelper = GravitySnapHelper(Gravity.START)
snapHelper.attachToRecyclerView(recyclerView)
```

  

## Center snapping

```kotlin
val snapHelper = GravitySnapHelper(Gravity.CENTER)
snapHelper.attachToRecyclerView(recyclerView)
```

  

## Limiting fling distance

If you use  **setMaxFlingSizeFraction** or **setMaxFlingDistance** 
you can change the maximum fling distance allowed.

  


## With decoration

  

## Features 

1. **setMaxFlingDistance** or **setMaxFlingSizeFraction** - changes the max fling distance allowed.
2. **setScrollMsPerInch** - changes the scroll speed.
3. **setGravity** - changes the gravity of the SnapHelper.
4. **setSnapToPadding** - enables snapping to padding (default is false)
5. **smoothScrollToPosition** and **scrollToPosition**
6. RTL support out of the box

## Nested RecyclerViews

Take a look at these blog posts if you're using nested RecyclerViews

1. [Improving scrolling behavior of nested RecyclerViews](https://rubensousa.com/2019/08/16/nested_recyclerview_part1/)

2. [Saving scroll state of nested RecyclerViews](https://rubensousa.com/2019/08/27/saving_scroll_state_of_nested_recyclerviews/)


## License

    Copyright 2018 The Android Open Source Project
    Copyright 2019 Rúben Sousa
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
        http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)