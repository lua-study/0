[![Build Status](https://travis-ci.org/natario1/CameraView.svg?branch=master)](https://travis-ci.org/natario1/CameraView)
[![Code Coverage](https://codecov.io/gh/natario1/CameraView/branch/master/graph/badge.svg)](https://codecov.io/gh/natario1/CameraView)

 
   
 

# CameraView

CameraView is a well documented, high-level library that makes capturing pictures and videos easy,
addressing most of the common issues and needs, and still leaving you with flexibility where needed.
See [CHANGELOG](https://github.com/natario1/CameraView/blob/master/CHANGELOG.md).

```groovy
compile 'com.otaliastudios:cameraview:1.5.1'
```

Make sure your project repositories include the `jcenter()`:

```groovy
allprojects {
  repositories {
    jcenter()
  }
}
```


 
   
   
   
 

*This was a fork of [CameraKit-Android](https://github.com/gogopop/CameraKit-Android), originally a
fork of [Google's CameraView](https://github.com/google/cameraview), but has been
[completely rewritten](https://github.com/natario1/CameraView/graphs/contributors?type=d).
See below for a [list of what was done](#roadmap) and [licensing info](#contributing-and-licenses).*

### Features

- Seamless image and video capturing
- **Gestures** support (tap to focus, pinch to zoom and much more)
- System permission handling
- **Smart sizing** behavior
  - Preview: Create a `CameraView` of **any size**
  - Preview: Center inside or center crop behaviors
  - Output: Handy utilities to set the output size
  - Output: Automatic cropping to match your `CameraView` preview bounds
- Built-in **grid drawing**
- Multiple capture methods
  - Take high-resolution pictures with `capturePicture`
  - Take **quick snapshots** as a freeze frame of the preview with `captureSnapshot`
- Control HDR, flash, zoom, white balance, exposure correction and more
- **Frame processing** support
- **Metadata** support for pictures and videos
  - Automatically detected orientation tags
  - Plug in **location tags** with `setLocation()` API
- `CameraUtils` to help with Bitmaps and orientations
- Error handling
- Thread safe, **well tested**
- **Lightweight**, no dependencies, just support `ExifInterface`
- Works down to API level 15

# Docs

- [Usage](#usage)
  - [Capturing Images](#capturing-images)
  - [Capturing Video](#capturing-video)
  - [Other camera events](#other-camera-events)
- [Gestures](#gestures)  
- [Sizing Behavior](#sizing-behavior)
  - [Preview Size](#preview-size)
  - [Picture Size](#picture-size)
- [Camera Controls](#camera-controls)
- [Frame Processing](#frame-processing)
- [Other APIs](#other-apis)  
- [Permissions Behavior](#permissions-behavior)
- [Logging](#logging)
- [Device-specific issues](#device-specific-issues)
- [Roadmap](#roadmap)

## Usage

To use the CameraView engine, simply add a `CameraView` to your layout:

```xml
 
```

`CameraView` has lots of XML attributes, so keep reading. Make sure you override `onResume`,
`onPause` and  `onDestroy` in your activity or fragment, and call `CameraView.start()`, `stop()`
and `destroy()`.

```java
@Override
protected void onResume() {
    super.onResume();
    cameraView.start();
}

@Override
protected void onPause() {
    super.onPause();
    cameraView.stop();
}

@Override
protected void onDestroy() {
    super.onDestroy();
    cameraView.destroy();
}
```

### Capturing Images

To capture an image just call `CameraView.capturePicture()`. Make sure you setup a `CameraListener`
to handle the image callback.

```java
camera.addCameraListener(new CameraListener() {
    @Override
    public void onPictureTaken(byte[] picture) {
        // Create a bitmap or a file...
        // CameraUtils will read EXIF orientation for you, in a worker thread.
        CameraUtils.decodeBitmap(picture, ...);
    }
});

camera.capturePicture();
```

You can also use `camera.captureSnapshot()` to capture a preview frame. This is faster, though will
ensure lower quality output.

### Capturing Video

To capture video just call `CameraView.startCapturingVideo(file)` to start, and
`CameraView.stopCapturingVideo()` to finish. Make sure you setup a `CameraListener` to handle
the video callback.

```java
camera.addCameraListener(new CameraListener() {
    @Override
    public void onVideoTaken(File video) {
        // The File is the same you passed before.
        // Now it holds a MP4 video.
    }
});

// Select output file. Make sure you have write permissions.
File file = ...;
camera.startCapturingVideo(file);

// Later... stop recording. This will trigger onVideoTaken().
camera.stopCapturingVideo();

// You can also use one of the video constraints:
// videoMaxSize and videoMaxDuration will automatically stop recording when satisfied.
camera.setVideoMaxSize(100000);
camera.setVideoMaxDuration(5000);
camera.startCapturingVideo(file);
```

### Other camera events

Make sure you can react to different camera events by setting up one or more `CameraListener`
instances. All these are executed on the UI thread.

```java
camera.addCameraListener(new CameraListener() {

    /**
     * Notifies that the camera was opened.
     * The options object collects all supported options by the current camera.
     */
    @Override
    public void onCameraOpened(CameraOptions options) {}

    /**
     * Notifies that the camera session was closed.
     */
    @Override
    public void onCameraClosed() {}

    /**
     * Notifies about an error during the camera setup or configuration.
     * At the moment, errors that are passed here are unrecoverable. When this is called,
     * the camera has been released and is presumably showing a black preview.
     *
     * This is the right moment to show an error dialog to the user.
     */
    @Override
    public void onCameraError(CameraException error) {}

    /**
     * Notifies that a picture previously captured with capturePicture()
     * or captureSnapshot() is ready to be shown or saved.
     *
     * If planning to get a bitmap, you can use CameraUtils.decodeBitmap()
     * to decode the byte array taking care about orientation.
     */
    @Override
    public void onPictureTaken(byte[] picture) {}

    /**
     * Notifies that a video capture has just ended. The file parameter is the one that
     * was passed to startCapturingVideo(File), or a fallback video file.
     */
    @Override
    public void onVideoTaken(File video) {}
    
    /**
     * Notifies that the device was tilted or the window offset changed.
     * The orientation passed can be used to align views (e.g. buttons) to the current
     * camera viewport so they will appear correctly oriented to the user.
     */
    @Override
    public void onOrientationChanged(int orientation) {}

    /**
     * Notifies that user interacted with the screen and started focus with a gesture,
     * and the autofocus is trying to focus around that area.
     * This can be used to draw things on screen.
     */    
    @Override
    public void onFocusStart(PointF point) {}
    
    /**
     * Notifies that a gesture focus event just ended, and the camera converged
     * to a new focus (and possibly exposure and white balance).
     */
    @Override
    public void onFocusEnd(boolean successful, PointF point) {}
    
    /**
     * Noitifies that a finger gesture just caused the camera zoom
     * to be changed. This can be used, for example, to draw a seek bar.
     */
    @Override
    public void onZoomChanged(float newValue, float[] bounds, PointF[] fingers) {}
    
    /**
     * Noitifies that a finger gesture just caused the camera exposure correction
     * to be changed. This can be used, for example, to draw a seek bar.
     */
    @Override 
    public void onExposureCorrectionChanged(float newValue, float[] bounds, PointF[] fingers) {}

});
```

## Gestures

`CameraView` listen to lots of different gestures inside its bounds. You have the chance to map
these gestures to particular actions or camera controls, using `mapGesture()`.
This lets you emulate typical behaviors in a single line:

```java
cameraView.mapGesture(Gesture.PINCH, GestureAction.ZOOM); // Pinch to zoom!
cameraView.mapGesture(Gesture.TAP, GestureAction.FOCUS_WITH_MARKER); // Tap to focus!
cameraView.mapGesture(Gesture.LONG_TAP, GestureAction.CAPTURE); // Long tap to shoot!
```

Simple as that. More gestures are coming. There are two things to be noted:

- Not every mapping is valid. For example, you can't control zoom with long taps, or start focusing by pinching.
- Some actions might not be supported by the sensor. Check out `CameraOptions` to know what's legit and what's not.

|Gesture (XML)|Description|Can be mapped to|
|-------------|-----------|----------------|
|`PINCH` (`cameraGesturePinch`)|Pinch gesture, typically assigned to the zoom control.|`zoom` `exposureCorrection` `none`|
|`TAP` (`cameraGestureTap`)|Single tap gesture, typically assigned to the focus control.|`focus` `focusWithMarker` `capture` `none`|
|`LONG_TAP` (`cameraGestureLongTap`)|Long tap gesture.|`focus` `focusWithMarker` `capture` `none`|
|`SCROLL_HORIZONTAL` (`cameraGestureScrollHorizontal`)|Horizontal movement gesture.|`zoom` `exposureCorrection` `none`|
|`SCROLL_VERTICAL` (`cameraGestureScrollVertical`)|Vertical movement gesture.|`zoom` `exposureCorrection` `none`|


## Sizing Behavior

### Preview Size

`CameraView` has a smart measuring behavior that will let you do what you want with a few flags.
Measuring is controlled simply by `layout_width` and `layout_height` attributes, with this meaning:

- `WRAP_CONTENT` : try to stretch this dimension to respect the preview aspect ratio.
- `MATCH_PARENT` : fill this dimension, even if this means ignoring the aspect ratio.
- Fixed values (e.g. `500dp`) : respect this dimension.

You can have previews of all sizes, not just the supported presets. Whaterever you do,
the preview will never be distorted.

#### Center Inside

You can emulate a **center inside** behavior (like the `ImageView` scaletype) by setting
both dimensions to `wrap_content`. The camera will get the biggest possible size that fits
into your bounds, just like what happens with image views.


```xml
 
```

This means that the whole preview is visible, and the image output matches what was visible
during the capture.

#### Center Crop

You can emulate a **center crop** behavior by setting both dimensions to fixed values or to
`MATCH_PARENT`. The camera view will fill the rect. If your dimensions don't match the aspect ratio
of the internal preview surface, the surface will be cropped to fill the view,
just like `android:scaleType="centerCrop"` on an `ImageView`.

```xml
 
```

This means that part of the preview is hidden, and the image output will contain parts of the scene
that were not visible during the capture. If this is a problem, see [cameraCropOutput](#cameracropoutput).

### Picture Size

On top of this, you can control the actual size of the output picture, among the list of available sizes.
It is the size of the final JPEG picture. This can be achieved directly through XML, or
using the `SizeSelector` class:

```java
cameraView.setPictureSize(new SizeSelector() {
    @Override
    public List  select(List  source) {
        // Receives a list of available sizes.
        // Must return a list of acceptable sizes.
    }
});
```

In practice, this is way easier using XML attributes or leveraging the `SizeSelectors` utilities:

|Constraint|XML attr|SizeSelector|
|----------|--------|------------|
|min. width|`app:cameraPictureSizeMinWidth="100"`|`SizeSelectors.minWidth(100)`|
|min. height|`app:cameraPictureSizeMinHeight="100"`|`SizeSelectors.minHeight(100)`|
|max. width|`app:cameraPictureSizeMaxWidth="3000"`|`SizeSelectors.maxWidth(3000)`|
|max. height|`app:cameraPictureSizeMaxHeight="3000"`|`SizeSelectors.maxHeight(3000)`|
|min. area|`app:cameraPictureSizeMinArea="1000000"`|`SizeSelectors.minArea(1000000)`|
|max. area|`app:cameraPictureSizeMaxArea="5000000"`|`SizeSelectors.maxArea(5000000)`|
|aspect ratio|`app:cameraPictureSizeAspectRatio="1:1"`|`SizeSelectors.aspectRatio(AspectRatio.of(1,1), 0)`|
|smallest|`app:cameraPictureSizeSmallest="true"`|`SizeSelectors.smallest()`|
|biggest (**default**)|`app:cameraPictureSizeBiggest="true"`|`SizeSelectors.biggest()`|

If you declare more than one XML constraint, the resulting selector will try to match **all** the
constraints. Be careful - it is very likely that applying lots of constraints will give
empty results.

#### SizeSelectors utilities

For more versatility, or to address selection issues with multiple constraints,
we encourage you to use `SizeSelectors` utilities, that will let you merge different selectors.

This selector will try to find square sizes bigger than 1000x2000. If none is found, it falls back
to just square sizes:

```java
SizeSelector width = SizeSelectors.minWidth(1000);
SizeSelector height = SizeSelectors.minHeight(2000);
SizeSelector dimensions = SizeSelectors.and(width, height); // Matches sizes bigger than 1000x2000.
SizeSelector ratio = SizeSelectors.aspectRatio(AspectRatio.of(1, 1), 0); // Matches 1:1 sizes.

SizeSelector result = SizeSelectors.or(
    SizeSelectors.and(ratio, dimensions), // Try to match both constraints
    ratio, // If none is found, at least try to match the aspect ratio
    SizeSelectors.biggest() // If none is found, take the biggest
);
camera.setPictureSize(result);
```

## Camera controls

Most camera parameters can be controlled through XML attributes or linked methods.

```xml
 
```

|XML Attribute|Method|Values|Default Value|
|-------------|------|------|-------------|
|[`cameraSessionType`](#camerasessiontype)|`setSessionType()`|`picture` `video`|`picture`|
|[`cameraFacing`](#camerafacing)|`setFacing()`|`back` `front`|`back`|
|[`cameraFlash`](#cameraflash)|`setFlash()`|`off` `on` `auto` `torch`|`off`|
|[`cameraGrid`](#cameragrid)|`setGrid()`|`off` `draw3x3` `draw4x4` `drawPhi`|`off`|
|[`cameraCropOutput`](#cameracropoutput)|`setCropOutput()`|`true` `false`|`false`|
|[`cameraJpegQuality`](#camerajpegquality)|`setJpegQuality()`|`0  
```

- If you want your app to be installed only on devices that have a camera, you should add:

```xml
 
```

If you don't request this feature, you can use `CameraUtils.hasCameras()` to detect if current
device has cameras, and then start the camera view.

### Handling

On Marshmallow+, the user must explicitly approve our permissions. You can

- handle permissions yourself and then call `cameraView.start()` once they are acquired
- or call `cameraView.start()` anyway: `CameraView` will present a permission request to the user based on
  whether they are needed or not with the current configuration.

In the second case, you should restart the camera if you have a successful response from `onRequestPermissionResults()`.

## Logging

`CameraView` will log a lot of interesting events related to the camera lifecycle. These are important
to identify bugs. The default logger will simply use Android `Log` methods posting to logcat.

You can attach and detach external loggers using `CameraLogger.registerLogger()`:

```java
CameraLogger.registerLogger(new Logger() {
    @Override
    public void log(@LogLevel int level, String tag, String message, @Nullable Throwable throwable) {
        // For example...
        Crashlytics.log(message);
    }
});
```

Make sure you enable the logger using `CameraLogger.setLogLevel(@LogLevel int)`. The default will only
log error events.

## Device-specific issues

There are a couple of known issues if you are working with certain devices. The emulator is one of
the most tricky in this sense.

- Devices, or activities, with hardware acceleration turned off: this can be the case with emulators.
  In this case we will use SurfaceView as our surface provider. That is intrinsically flawed and can't
  deal with all we want to do here (runtime layout changes, scaling, etc.). So, nothing to do in this case.
- Devices with no support for MediaRecorder: the emulator does not support it, officially. This means
  that video/audio recording is flawed. Again, not our fault.

## Roadmap

This is what was done since the library was forked. I have kept the original structure, but practically
all the code was changed.

- *a huge number of serious bugs fixed*
- *decent orientation support for both pictures and videos*
- *less dependencies*
- *EXIF support*
- *real tap-to-focus support*
- *pinch-to-zoom support*
- *simpler APIs, docs and heavily commented code*
- *new `captureSnapshot` API*
- *new `setLocation` and `setWhiteBalance` APIs*
- *new `setGrid` APIs, to draw 3x3, 4x4 or golden ratio grids*
- *option to pass a `File` when recording a video*
- *other minor API additions*
- *replacing Method and Permissions stuff with simpler `sessionType`* 
- *smart measuring and sizing behavior, replacing bugged `adjustViewBounds`*
- *measure `CameraView` as center crop or center inside*
- *add multiple `CameraListener`s for events*
- *gesture framework support, map gestures to camera controls*
- *pinch gesture support*
- *tap & long tap gesture support*
- *scroll gestures support*
- *MediaActionSound support*
- *Hdr controls*
- *zoom and exposure correction controls*
- *Tests!*
- *`CameraLogger` APIs for logging and bug reports*
- *Better threading, start() in worker thread and callbacks in UI*
- *Frame processor support*
- *inject external loggers*
- *error handling*
- *capture size selectors*

These are still things that need to be done, off the top of my head:

- [ ] `Camera2` integration
- [ ] animate grid lines similar to stock camera app
- [ ] add onRequestPermissionResults for easy permission callback
- [ ] decent code coverage

# Contributing and licenses

The original project which served as a starting point for this library,
[CameraKit-Android](https://github.com/wonderkiln/CameraKit-Android), is licensed under the
[MIT](https://github.com/wonderkiln/CameraKit-Android/blob/master/LICENSE) license.
Additional work is now licensed under the [MIT](https://github.com/natario1/CameraView/blob/master/LICENSE)
license as well.

You are welcome to contribute with suggestions or pull requests, this is under active development.
To contact me,  send an email. 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)