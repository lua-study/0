# Boost for React Native

This is a copy of [Boost](http://www.boost.org/) that is used to build React Native (Android) from source. It includes just the Boost source code (without the docs, for example) so that downloading and extracting the files doesn't take too long.

You probably don't want to directly use this repository. Its sole purpose is to distribute the Boost code for building React Native.

## Upgrading Boost

First, download a new version of Boost, e.g.: http://www.boost.org/users/history/version_1_63_0.html

Then create a dummy commit and a git tag so you can create a new release.

React Native build tools (Gradle) expect specific folder structure.
Run this command to get a .tar.gz file:

```
tar -cvzf boost_1_63_0.tar.gz boost_1_63_0/
```

Then drag&drop the tar.gz file to the releases page.

```
pod 'boost-for-react-native', :git => 'https://gitee.com/conan_ma/boost-for-react-native.git'
```

## License

The Boost Software License 1.0 is included with this repository and its releases.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)