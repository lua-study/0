##WayGif

Android端通过jni解析显示gif图片，更高效，更速度。
原项目来自Github: :blush: [android-gif-drawable](https://github.com/koral--/android-gif-drawable "android-gif-drawable")

##简单使用

###在layout布局XML文件中：
跟使用普通的 `ImageView` 一样使用 `GifImageView` (或者 `GifImageButton`):
```xml
 
```

如果 `android:src` 或者 `android:background` 使用的是GIF文件，运行程序后，将会自动播放。

`GifTextView` 允许使用gif文件作为背景.
```xml
 
```

###在Java代码中：
`GifImageView`, `GifImageButton` and `GifTextView` 可以直接调用 `setImageResource(int resId)` and `setBackgroundResource(int resId)` 设置GIF文件图片。

`GifDrawable` 也能在代码中直接实例化:

```java
		//asset file
		GifDrawable gifFromAssets = new GifDrawable( getAssets(), "anim.gif" );
		
		//resource (drawable or raw)
		GifDrawable gifFromResource = new GifDrawable( getResources(), R.drawable.anim );

		//byte array
		byte[] rawGifBytes = ...
		GifDrawable gifFromBytes = new GifDrawable( rawGifBytes );
		
		//FileDescriptor
		FileDescriptor fd = new RandomAccessFile( "/path/anim.gif", "r" ).getFD();
		GifDrawable gifFromFd = new GifDrawable( fd );
		
		//file path
		GifDrawable gifFromPath = new GifDrawable( "/path/anim.gif" );
		
		//file
		File gifFile = new File(getFilesDir(),"anim.gif");
		GifDrawable gifFromFile = new GifDrawable(gifFile);
		
		//AssetFileDescriptor
		AssetFileDescriptor afd = getAssets().openFd( "anim.gif" );
		GifDrawable gifFromAfd = new GifDrawable( afd );
				
		//InputStream (it must support marking)
		InputStream sourceIs = ...
		BufferedInputStream bis = new BufferedInputStream( sourceIs, GIF_LENGTH );
		GifDrawable gifFromStream = new GifDrawable( bis );
		
		//direct ByteBuffer
		ByteBuffer rawGifBytes = ...
		GifDrawable gifFromBytes = new GifDrawable( rawGifBytes );
		
````
`InputStreams` 会在 `GifDrawable` 不再使用时自动关闭，因此你不用特意去关闭它，当然也可以调用 `recycle()`   
 

Note that all input sources need to have ability to rewind to the begining. It is required to correctly play animated GIFs 
(where animation is repeatable) since subsequent frames are decoded on demand from source.

####Animation control
`GifDrawable` implements an `Animatable` and `MediaPlayerControl` so you can use its methods and more:

+ `stop()` - stops the animation, can be called from any thread
+ `start()` - starts the animation, can be called from any thread
+ `isRunning()` - returns whether animation is currently running or not
+ `reset()` - rewinds the animation, does not restart stopped one
+ `setSpeed(float factor)` - sets new animation speed factor, eg. passing 2.0f will double the animation speed
+ `seekTo(int position)` - seeks animation (within current loop) to given `position` (in milliseconds) __Only seeking forward is supported__
+ `getDuration()` - returns duration of one loop of the animation
+ `getCurrentPosition()` - returns elapsed time from the beginning of a current loop of animation

#####Using [MediaPlayerControl](http://developer.android.com/reference/android/widget/MediaController.MediaPlayerControl.html)
Standard controls for a MediaPlayer (like in [VideoView](http://developer.android.com/reference/android/widget/VideoView.html)) can be used to control GIF animation and show its current progress.

Just set `GifDrawable` as MediaPlayer on your [MediaController](http://developer.android.com/reference/android/widget/MediaController.html) like this:
```java
	@Override
	protected void onCreate ( Bundle savedInstanceState )
	{
		super.onCreate( savedInstanceState );
		GifImageButton gib = new GifImageButton( this );
		setContentView( gib );
		gib.setImageResource( R.drawable.sample );
		final MediaController mc = new MediaController( this );
		mc.setMediaPlayer( ( GifDrawable ) gib.getDrawable() );
		mc.setAnchorView( gib );
		gib.setOnClickListener( new OnClickListener()
		{
			@Override
			public void onClick ( View v )
			{
				mc.show();
			}
		} );
	}
```

####Retrieving GIF metadata

+ `getLoopCount()` - returns a loop count as defined in `NETSCAPE 2.0` extension
+ `getNumberOfFrames()` - returns number of frames (at least 1)
+ `getComment()` - returns comment text (`null` if GIF has no comment)
+ `getFrameByteCount()` - returns minimum number of bytes that can be used to store pixels of the single frame
+ `getAllocationByteCount()` - returns size (in bytes) of the allocated memory used to store pixels of given GifDrawable
+ `getInputSourceByteCount()` - returns length (in bytes) of the backing input data
+ `toString()` - returns human readable information about image size and number of frames (intended for debugging purpose)

####Advanced

## 测试截图

![Screenshot 1](http://git.oschina.net/way/WayGif/raw/master/screenshots/1.png "Screenshot 1")

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)