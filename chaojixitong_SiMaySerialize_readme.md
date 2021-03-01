 **二进制序列化可以方便快捷的将对象进行持久化或者网络传输，并且体积小、性能高，.net自身也带有BinaryFormatter类来实现的二进制序列化、反序列化，但是发现BinaryFormatter有很多地方不妥,比如:** 

1. 类名上面要加上[Serializable]，不加不给序列化
2. 序列化byte[]非常大，使用System.Text.Encoding.UTF8.GetString(bytes)查看下，发现里面有一大堆的元数据
3. 序列化对象需要完全一致，连类的命名空间都要相同，这点对于分面式开发的应用来说也是不可接受的

 **SiMaySerialize** 
- SimaySerialize是一个轻量级的对象二进制序列化库，支持自定义类型，支持常用基本数据类型
- 不需要标记[Serializable]

 **欢迎点star,关注，项目不定时更新** 


```
            List  list = new List ();
            for (int i = 0; i  (bytes);
            sw.Stop();
            Console.WriteLine("反序列化耗时:" + sw.Elapsed.TotalSeconds);
```
#未来目标
 - 加入动态调用缓存
 - 支持DotCore

#开发环境
 - Visual Studio 2013 以上

#参与贡献
 - Fork 本仓库
 - 新建 Feat_xxx 分支
 - 提交代码
 - 新建 Pull Request

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)