# 前言
 之前一直想对OpenCV进行学习和使用，一直没有实践。这次痛下决心，一定要搞定。经过两天的折腾，遇到各种bug终于搞定了，希望能帮助到初学者，如果里面有那些写的不对的地方，还希望各位看官指正。
#简介
  * 准备条件
  * Android Studio NDK环境搭建
  * Android Studio OpenCV使用
  * 常见问题

## 准备条件
   + [openCV压缩包下载](https://pan.baidu.com/s/1pMNObsZ)密码【7xkh】
   + Android Studio
## NDK环境搭建
       首先，在Android Studio中打开File->setting->Android SDK->SDK Tools
    选择CMake和NDK然后点击Apply等待下载完成即可。
 ![Android Studio Ndk配置.png](http://upload-images.jianshu.io/upload_images/1716569-f3db8a0991ccb129.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 + 首先

          OpenCV是一个基于BSD许可（开源）发行的跨平台计算机视觉库，可以
        运行在Linux、Windows、Android和Mac OS操作系统上。它轻量级而且
        高效——由一系列 C 函数和少量 C++ 类，同时提供了Python、Ruby、
        MATLAB等语言的接口，实现了图像处理和计算机视觉方面的很多通用算法。
        OpenCV用C++语言编写，它的主要接口也是C++语言，但是依然保留了大量的C语言接口。
        该库也有大量的Python、Java and MATLAB/OCTAVE（版本2.5）的接口。
        这些语言的API接口函数可以通过在线文档获得。如今也提供对于C#、Ch、Ruby的支持。
+ 其次

          在Android Studio中新建Project，选中Include c++ support,之后一直默认选择，
      在C++版本选中c++11,然后finish完成创建，如下图所示。
![Android Studio创建工程.png](http://upload-images.jianshu.io/upload_images/1716569-3f43cc05dac1b245.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 然后

         导入OpenCV中的Java库，这个库是OpenCV-android-sdk --->sdk--->java,选择java之后直接导入。
      之后点击Android Studio中的Project Structure，或者直接按ctrl+alt+shift+s打开库依赖面板，
      选择moudle Dependency,选择OpenCVLibrary330添加即可，如下图所示。
![Android Studio 依赖项目.png](http://upload-images.jianshu.io/upload_images/1716569-eea5e8241e3995fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 再次
  
      在AS中打开CMakeLists.txt设置OpenCV的路径（此路径为你本地的路径）
      # ##################### OpenCV 环境 
     
      #设置OpenCV-android-sdk路径
      set( OpenCV_DIR E:/Source/OpenCV-android-sdk/sdk/native/jni )

      find_package(OpenCV REQUIRED )
      if(OpenCV_FOUND)
      include_directories(${OpenCV_INCLUDE_DIRS})
      message(STATUS "OpenCV library status:")
      message(STATUS "    version: ${OpenCV_VERSION}")
      message(STATUS "    libraries: ${OpenCV_LIBS}")
      message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")
      else(OpenCV_FOUND)
      message(FATAL_ERROR "OpenCV library not found")
      endif(OpenCV_FOUND)

_注意：_  上面的set（ OpenCV_DIR E:/Source/OpenCV-android-sdk/sdk/native/jni）把此路径换成你本地的路径。

 + 最后

           将OpenCV-android-sdk下面的sdk-->native-->libs下面的文件复制到AS中libs路径下。
        然后在app 的build.gradle的android下添加如下代码：

         task nativeLibsToJar(type: Jar, description: 'create a jar archive of the native libs') {
            destinationDir file("$buildDir/native-libs")
            baseName 'native-libs'
            from fileTree(dir: 'libs', include: '**/*.so')
            into 'lib/'
        }

        tasks.withType(JavaCompile) {
            compileTask -> compileTask.dependsOn(nativeLibsToJar)
        }

         最后还需要在dependencies添加 
        implementation fileTree(dir: "$buildDir/native-libs", include: 'native-libs.jar')
_提示 :_ 到这里OpenCV的环境已经配置完了，下面我们来写一个简单的DEMO验证一下。

## 简单DEMO验证
_注意 :_ 本demo只是简单验证，6.0的运行时权限等等没有进行配置。
  + 新建MainActivity

        public class MainActivity extends AppCompatActivity implements 
         View.OnClickListener { 
          //最大
           private double max_size = 1024;
          //回调
           private int PICK_IMAGE_REQUEST = 1;
          //原图、处理后的图片
           private ImageView mImgOriginal, mImgDeals;
          //原始Bitmap、处理后的Bitmap
          private Bitmap mOriginalBitmap,mDealBitmap;
         //选择图片、处理
          private Button mBtnChoose, mBtnDeals;
          @Override
         protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          onLoadOpenCVLibrary();
          initView();
         }

        /**
         * 初始化
         */
         private void initView() {
        mImgDeals = findViewById(R.id.img_deals);
        mImgOriginal = findViewById(R.id.img_original);
        mBtnChoose = findViewById(R.id.btn_choose);
        mBtnDeals = findViewById(R.id.btn_deals);

        mBtnDeals.setOnClickListener(this);
        mBtnChoose.setOnClickListener(this);

         }


         @Override
        public void onClick(View view) {
        switch (view.getId()) {
            case R.id.btn_choose: {//选择
                selectImage();
                break;
            }
            case R.id.btn_deals: {//处理
                convertGray();
                break;
            }
        }
        }

          @Override
         protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == PICK_IMAGE_REQUEST && resultCode == RESULT_OK && data != null
                && data.getData() != null) {
            Uri uri = data.getData();
            try {
                Log.e("image-tag", "start to decode selected image now...");
                InputStream input = getContentResolver().openInputStream(uri);
                BitmapFactory.Options options = new BitmapFactory.Options();
                options.inJustDecodeBounds = true;
                BitmapFactory.decodeStream(input, null, options);
                int raw_width = options.outWidth;
                int raw_height = options.outHeight;
                int max = Math.max(raw_width, raw_height);
                int newWidth = raw_width;
                int newHeight = raw_height;
                int inSampleSize = 1;
                if (max > max_size) {
                    newWidth = raw_width / 2;
                    newHeight = raw_height / 2;
                    while ((newWidth / inSampleSize) > max_size || (newHeight / inSampleSize) > max_size) {
                        inSampleSize *= 2;
                    }
                }

                options.inSampleSize = inSampleSize;
                options.inJustDecodeBounds = false;
                options.inPreferredConfig = Bitmap.Config.ARGB_8888;
                mOriginalBitmap = BitmapFactory.decodeStream(getContentResolver().openInputStream(uri),
                        null, options);
                mDealBitmap = BitmapFactory.decodeStream(getContentResolver().openInputStream(uri),
                        null, options);
                mImgOriginal.setImageBitmap(mOriginalBitmap);

            } catch (Exception e) {
                e.printStackTrace();
            }
        }

        }

        /**
         * OpenCV库静态加载并初始化
         */
         private void onLoadOpenCVLibrary() {
          boolean load = OpenCVLoader.initDebug();
          if (load) {
            Log.e("CV", "Open CV Libraries loaded...");
           }
         }

         /**
          * 选择图片
          */
        private void selectImage() {
        Intent intent = new Intent();
        intent.setType("image/*");
        intent.setAction(Intent.ACTION_GET_CONTENT);
        startActivityForResult(Intent.createChooser(intent, "选择图像"), PICK_IMAGE_REQUEST);
         }

        /**
         * 转换
         */
         private void convertGray(){
        Mat src = new Mat();
        Mat temp = new Mat();
        Mat dst = new Mat();
        Utils.bitmapToMat(mDealBitmap, src);
        Imgproc.cvtColor(src, temp, Imgproc.COLOR_BGRA2BGR);
        Imgproc.cvtColor(temp, dst, Imgproc.COLOR_BGR2GRAY);
        Utils.matToBitmap(dst, mDealBitmap);
        mImgDeals.setImageBitmap(mDealBitmap);
         }
         }
+ 新建资源文件
  
       
       

       

         

         

       

       

       
       

+ 资源文件的效果如下图所示
  ![AS资源文件.png](http://upload-images.jianshu.io/upload_images/1716569-1d4ceece061a91f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
+ 最终运行的效果如下图所示
![AS效果图.png](http://upload-images.jianshu.io/upload_images/1716569-b43e1f03a33a4539.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 感言
 +  经过两天的折腾，遇到了各种Bug，终于搞定的，除了这种方式添加OpenCV之外还有添加.mk文件的方式等等。这里就不多做介绍了，想了解的看官可以去自行搜索。
 + 感谢gloomyfish的[OpenCV On Android开发 - Android Studio上环境配置](http://blog.csdn.net/jia20003/article/details/53126321)
 + [github目录](https://github.com/muyishuangfeng/OpenCV)
 + [简书](https://www.jianshu.com/p/f65788d7dc25)
 + [掘金](https://juejin.im/post/5a991c146fb9a028b54755e2)
 + [个人博客主页](https://muyishuangfeng.github.io)
 


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)