# Core Animation Code

These are code examples for the book _iOS Core Animation Advanced Techniques_ written by [Nick Lockwood](https://github.com/nicklockwood), include code examples from Chapter 1 to Chapter 10. 

Recently, I'm reading the awesome book. I think I should write some code. So I copy and paste the easy part from the book to Xcode, and write the hard part bodily after I understand well. Gradually, I accumulate these code examples.

## Directory Tree 

```
.
├── 1 The Layer Tree
│   └── BlueLayer
├── 2 The Backing Image
│   ├── CALayerDelegate
│   ├── LayerContent
│   └── Sprite
├── 3 Layer Geometry
│   ├── AnchorPoint
│   ├── Clock
│   ├── ContainsPoint
│   ├── ContentsCenter
│   └── ZPosition
├── 4 Visual Effects
│   ├── DropShadows
│   ├── GroupOpacity
│   ├── LCDClock
│   ├── LayerMask
│   ├── RoundedCorners
│   ├── ShadowClipping
│   └── ShadowPath
├── 5 Transforms
│   ├── CompoundTransform
│   ├── Cube
│   ├── OppositeRoationAroundY
│   ├── OppositeRotationAroundZ
│   └── SublayerTransform
├── 6 Specialized Layers
│   ├── AVPlayerLayer
│   ├── CAEAGLLayer
│   ├── CAEmitterLayer
│   ├── CAGradientLayer
│   ├── CAReplicatorLayer
│   ├── CAScrollLayer
│   ├── CAShapeLayer
│   ├── CATextLayer
│   ├── CATiledLayer
│   ├── CATransformLayer
│   ├── LayerLabel
│   ├── Reflection
│   ├── RichText
│   └── TileCutter
├── 7 Implicit Animations
│   ├── ActionForLayer
│   ├── CustomAction
│   ├── LayerActions
│   ├── PresentationLayer
│   └── Transactions
├── 8 Explicit Animations
│   ├── AnimateTransform
│   ├── AnimateUITabBarController
│   ├── AnimationDidStop
│   ├── AnimationGroup
│   ├── CABasicAnimation
│   ├── CAKeyframeAnimation
│   ├── CATransition
│   ├── CancelAnimation
│   ├── Clock
│   ├── CustomTransition
│   ├── TransformRotation
│   └── UIBezierPath
├── 9 Layer Time
│   ├── DurationAndRepeatCount
│   ├── ManualAnimation
│   ├── SwingingDoor
│   └── TimeOffsetAndSpeed
├── 10 Easing
│   ├── BouncingBall
│   ├── EasingFunction
│   ├── TimingWithCAKeyframeAnimation
│   └── UIViewEasing
├── CoreAnimationCode.xcworkspace
└── README.md

72 directories
```

You can open `CoreAnimationCode.xcworkspace` to see all projects in one workspace.

## Some Interesting Examples

CAEmitterCell:

![codexx](https://cloud.githubusercontent.com/assets/5022872/10262422/051ddb80-69f9-11e5-80d1-f0b61df6f072.gif)


timeOffset & speed test:

![code2](https://cloud.githubusercontent.com/assets/5022872/10262407/5d5a9fdc-69f8-11e5-8161-0d4b8b9ec4eb.gif)


Manual Animation:

![code3](https://cloud.githubusercontent.com/assets/5022872/10262408/68b2759e-69f8-11e5-8760-1f9f4ce1482f.gif)


Custom Transition:

![code4](https://cloud.githubusercontent.com/assets/5022872/10262410/7ab6030a-69f8-11e5-8395-0dadc09c46dd.gif)

Bouncing ball(Complex timing curve):

![bouncing](https://cloud.githubusercontent.com/assets/5022872/10268622/d65765ac-6af0-11e5-9da5-e7e0dbe1f9ee.gif)

Cancel Animation:

![cancel](https://cloud.githubusercontent.com/assets/5022872/10263022/6f77f354-6a11-11e5-83e9-8dd4fbe88ab5.gif)


CATransition:

![switch](https://cloud.githubusercontent.com/assets/5022872/10263030/98b0c642-6a11-11e5-9773-c58962e14485.gif)


Reflection:

![simulator-screen-shot-2015 10 3 - 8 52 33](https://cloud.githubusercontent.com/assets/5022872/10263042/d2d6c092-6a11-11e5-981c-3ae97b1fc3ea.jpg)


CAEAGLLayer(OpenGL):

![simulator-screen-shot-2015 10 3 - 8 50 35](https://cloud.githubusercontent.com/assets/5022872/10263047/e43eaf2a-6a11-11e5-8edf-05e2dec122ad.jpg)

The whole code examples can be downloaded from here: http://www.informit.com/store/ios-core-animation-advanced-techniques-9780133440751 . This repo is some kind of duplicate work. Hope it let you know the great book.



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)