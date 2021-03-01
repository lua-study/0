# FoolNLTK-java
[FoolNLTK](https://github.com/rockyzhengwu/FoolNLTK) java 版本

## maven

```
   
        me.midday 
        JFoolNLTK 
        1.0 
   
```


## 使用方法
```java
import me.midday.FoolNLTK;
import me.midday.lexical.AnalysisResult;
import me.midday.lexical.Entity;
import me.midday.lexical.LexicalAnalyzer;
import me.midday.lexical.Word;

import java.util.List;

public class LSTMLexicalParserDemo {
    public static void main(String[] args){
       String text = "北京欢迎你";
       LexicalAnalyzer lexicalAnalyzer = FoolNLTK.getLSTMLexicalAnalyzer();
       // 分词
       List > words = lexicalAnalyzer.cut(text);
       for(List  ws: words){
           ws.forEach(System.out::println);
       }

       // 词性标注
       List > posWords = lexicalAnalyzer.pos(text);
       for(List  ws: posWords){
           ws.forEach(System.out::println);
       }
       // 实体识别
       List >  entities = lexicalAnalyzer.ner(text);

       for(List  ents :entities){
           ents.forEach(System.out::println);
       }


       // 分词，词性，实体识别
       List   results = lexicalAnalyzer.analysis(text);
       results.forEach(System.out::println);


       // 多文本

       System.out.println();
       System.out.println("多文本：");
       List  docs = new ArrayList<>();
       docs.add(text);
       docs.add(text);
       // 分词
       List > dWords = lexicalAnalyzer.cut(docs);
       for(List  ws: dWords){
           ws.forEach(System.out::println);
       }
       // 词性标注
       List > dPosWords = lexicalAnalyzer.pos(docs);
       for(List  ws: dPosWords){
           ws.forEach(System.out::println);
       }
       List >  dEntities = lexicalAnalyzer.ner(docs);

       for(List  ents :dEntities){
           ents.forEach(System.out::println);
       }

       // 分词, 词性标注，实体识别
       List   dResults = lexicalAnalyzer.analysis(docs);
       dResults.forEach(System.out::println);

    }
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)