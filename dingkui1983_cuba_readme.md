     
   

 Java RAD framework for enterprise web applications 
  
 
   
   
 


 
   
     
      Website
     
      |  
     
      Online Demo
     
      |  
     
      Documentation
     
      |  
     
      Guides
     
      |  
     
      Forum
     
   
 

 
   
   
   
   
 
  
[CUBA Platform](https://www.cuba-platform.com) is a high level framework for rapid development of enterprise applications with rich web interface.

The simplest way to start using the platform is to [download](https://www.cuba-platform.com/download) CUBA Studio and create a new project in it. A released version of the platform will be downloaded automatically from the artifact repository.

You can also build a snapshot version of the platform from the source code and use it in your project.

To contribute, first refer to [Contributing Code](https://github.com/cuba-platform/cuba/blob/master/CONTRIBUTING.md) for general instructions and requirements for contributing code to the platform.

## Building from Source

In order to build the platform from source, you need to install the following:
* Java 8 Development Kit (JDK)
* [CUBA Gradle Plugin](https://github.com/cuba-platform/cuba-gradle-plugin)

Let's assume that you have cloned CUBA Gradle Plugin and CUBA into the following directories:
```
work/
    cuba/
    cuba-gradle-plugin/
```

Open terminal in the `work` directory and run the following command to build and install the plugin into your local Maven repository (`~/.m2`):
```
cd cuba-gradle-plugin
gradlew install
```

After that, go to the CUBA directory and build and install it with the same command:
```
cd ../cuba
gradlew install
```

## Using Snapshot Version

Edit the `build.gradle` file of your project. Change the `ext.cubaVersion` property and add `mavenLocal()` to the `repositories` section, for example:
```
buildscript {
    ext.cubaVersion = '7.2-SNAPSHOT'
    repositories {
        mavenLocal()
        maven { ...
```
That's all. Now you can build and deploy your application based on the snapshot version of the platform from your local repository:
 ```
 gradlew deploy
 ```

## Third-party dependencies

The platform uses a number of forked third-party libraries. They can be found in the following source code repositories:

* [eclipselink](https://github.com/cuba-platform/eclipselink)
* [vaadin](https://github.com/cuba-platform/vaadin)
* [vaadin-dragdroplayouts](https://github.com/cuba-platform/vaadin-dragdroplayouts)
* [vaadin-aceeditor](https://github.com/cuba-platform/vaadin-aceeditor)
* [swingx-core](https://github.com/cuba-platform/swingx-core)

All dependencies are also located in our artifacts repository, so you don't have to build them from sources in order to build and use the platform.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)