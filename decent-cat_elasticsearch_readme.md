### ES案例

#### 1. 自定义analyzer

```javascript
PUT news
{
  "settings": {
    "analysis": {
      "analyzer": {
        "hanlp_standard_pinyin":{
          "type": "custom",
          "tokenizer": "hanlp_standard",
          "filter": ["my_pinyin"]
        }
      },
      "filter": {
        "my_pinyin": {
          "type" : "pinyin",
          "keep_separate_first_letter" : false,
          "keep_full_pinyin" : true,
          "keep_original" : true,
          "limit_first_letter_length" : 16,
          "lowercase" : true,
          "remove_duplicated_term" : true
        }
      }
    }
  }
}
```

#### 2. 定义mappings

```
PUT news/_mapping
{
  "dynamic": false,
  "properties": {
    "id": {
      "type": "long"
    },
    "title": {
      "type": "text",
      "analyzer": "hanlp_standard"
    },
    "content": {
      "type": "text",
      "analyzer": "hanlp_standard"
    },
    "tags": {
      "type": "completion",
      "analyzer": "hanlp_standard",
      "fields": {
        "tag_pinyin": {
          "type": "completion",
          "analyzer": "hanlp_standard_pinyin"
        }
      }
    }
  }
}
```

#### 3. 导入mysql的数据集

```
D:\logstash-datas\bin>logstash.bat -f ../config/logstash-mysql.conf
```

**脚本参照第三章，数据库的脚本为news.sql**

#### 4.编写suggestion与query

**搜索要使用的suggestion**

```
GET news/_search
{
  "_source": ["id"], 
  "suggest": {
    "tag_pinyin_suggestion": {
      "text": "欧洲",
      "completion": {
        "field": "tags.tag_pinyin",
        "skip_duplicates": true
      }
    },
    "tag_suggestion": {
      "text": "欧洲",
      "completion": {
        "field": "tags",
        "skip_duplicates": true
      }
    }
  }
}
```

**搜索要使用的query**

```
GET news/_search
{
  "query": {
    "multi_match": {
      "query": "李小璐",
      "fields": ["title", "content"]
    }
  },
  "highlight": {
    "fields": {
      "content": {},
      "title": {}
    },
    "post_tags": " ", 
    "pre_tags": " "
  }
}
```

#### 5.依赖

```xml
 
	 
		 org.springframework.boot 
		 spring-boot-starter-web 
	 
 
	 
          org.springframework.boot 
          spring-boot-starter-data-elasticsearch 
     
 
	 
		 com.alibaba 
		 fastjson 
		 1.2.62 
	 
 
```

#### 6.获取ElasticsearchTemplate

```java
@Configuration
public class ElasticsearchTemplateConfig extends ElasticsearchConfigurationSupport {

    @Bean
    public Client elasticsearchClient() throws UnknownHostException {
        //Settings settings = Settings.builder().put("cluster.name", "my-application").build();

        Settings settings = Settings.builder().build();
        TransportClient client = new PreBuiltTransportClient(settings);
        // 回环路由IP
        client.addTransportAddress(new TransportAddress(
            InetAddress.getByName("127.0.0.1"), 9300));
        return client;
    }

    @Bean(name = {"elasticsearchOperations", "elasticsearchTemplate"})
    public ElasticsearchTemplate elasticsearchTemplate() throws UnknownHostException {
        return new ElasticsearchTemplate(elasticsearchClient(), entityMapper());
    }

    /**
     * EntityMapper是扫描所有的 Java的对象，这个对象是与elasticsearch中映射的对象
     */
    @Bean
    @Override
    public EntityMapper entityMapper() {
        ElasticsearchEntityMapper entityMapper = new ElasticsearchEntityMapper(
           elasticsearchMappingContext(), new DefaultConversionService());
        entityMapper.setConversions(elasticsearchCustomConversions());
        return entityMapper;
    }
}
```

#### 7.POJO类的编写

```java
@Document(indexName = "news", type = "_doc")
public class News {

    private Integer id;
    private String url;
    private String content;
    private String title;
}
```

#### 8.建议搜索

```java
@Resource
private ElasticsearchTemplate elasticsearchTemplate;

// 推荐搜索, 使用前缀搜索
@RequestMapping
public Object suggest(String text) {
	// 中文的Completion Suggestion
	CompletionSuggestionBuilder cnCompletionSuggestion = new 
      	CompletionSuggestionBuilder("tags")
        .prefix(text)
        .skipDuplicates(true);
	// 基于拼音的Completion Suggestion
	CompletionSuggestionBuilder pyCompletionSuggestion = new 	
         CompletionSuggestionBuilder("tags.tag_pinyin")
        .prefix(text)
        .skipDuplicates(true);

	SuggestBuilder suggestBuilder = new SuggestBuilder()
		.addSuggestion("cn_suggestion", cnCompletionSuggestion)
		.addSuggestion("py_suggestion", pyCompletionSuggestion);

	// 构建搜索
	SearchRequestBuilder searchRequestBuilder = elasticsearchTemplate
		.getClient() //
		.prepareSearch("news")
		.suggest(suggestBuilder)
		.setFetchSource(new String[]{"id"}, new String[]{});

	SearchResponse response = searchRequestBuilder.get();

	Set  suggestionWord = new HashSet<>();
	
    //获取中文建议
	Suggest.Suggestion cnSuggestion = response.getSuggest()
    	.getSuggestion("cn_suggestion");
	generateSuggestion(cnSuggestion, suggestionWord);
	
    // 获取拼音建议
	Suggest.Suggestion pySuggestion = response.getSuggest()
    	.getSuggestion("py_suggestion");
	generateSuggestion(pySuggestion, suggestionWord);

	return getResult(suggestionWord);
}
```

```java
/**
* @param suggestion  搜索出的建议
*/
public void generateSuggestion(Suggest.Suggestion suggestion, 
                               Set  	suggestionWord) {

	// suggestion.getEntries()方法得到的是对应的建议，因为在分词的情况下，可能有多个建议
	List  entries = suggestion.getEntries();

	if(entries.size() > 0) {
		for(Object obj : entries) {
		// 其实查出来的 obj 的类型为 CompletionSuggestion.Entry
			if(obj instanceof CompletionSuggestion.Entry) {
				CompletionSuggestion.Entry entry = (CompletionSuggestion.Entry)obj;
				// 获取具体的 option
				List  optionsList
                    				= entry.getOptions();
				if(optionsList.size() > 0) {
					for(CompletionSuggestion.Entry.Option op : optionsList) {
						Text text = op.getText();
						suggestionWord.add(text.toString());
					}
				}
			}
		}
	}
}

/**
* @param set
* @return   用于存储所有的建议，之所以使用 List > 这种数据类型，
*    是因为 ElementUI 在autocomplete接收到的数据格式为  [{"value":"abc"}, {"value":"xyz"}]
*/
public List > getResult(Set  set) {
	List > resultList = new LinkedList<>();
	set.forEach(suggestion -> {
		Map  map = new HashMap<>();
		map.put("value", suggestion);
		resultList.add(map);
	});
	return resultList;
}
```

#### 9.高亮搜索

```java
@RequestMapping("/execute")
public Object executeSearch(@RequestParam(required = true) String text,
				@RequestParam(required = false, defaultValue = "0") Integer page,
				@RequestParam(required = false, defaultValue = "10") Integer size) {
	SearchQuery searchQuery = new NativeSearchQueryBuilder()
		.withQuery(new MultiMatchQueryBuilder(text, "title", "content"))
		.withSourceFilter(
            new FetchSourceFilter(
                 new String[]{"id", "content", "title", "url"}, new String[]{}))
		.withIndices("news")
		.withHighlightBuilder(
            	new HighlightBuilder().field("title").field("content")
						.postTags(" ").preTags(" "))
			.withPageable(PageRequest.of(page, size))
			.build();

	return elasticsearchTemplate.query(searchQuery, new CustomResultExtractor());
}
```

```java
// 处理高亮结果
public class CustomResultExtractor implements ResultsExtractor > {

    @Override
    public List  extract(SearchResponse response) {
        return StreamSupport.stream(response.getHits().spliterator(), true)
            .map(this::searchHitToMyClass)
            .collect(Collectors.toList());
    }

    private News searchHitToMyClass(SearchHit searchHit) {
        News news = JSONObject.parseObject(searchHit.getSourceAsString(), News.class);

        Map  highlightFieldMap = searchHit.getHighlightFields();
		
        // 之所以要判断是因为，有些内容中可能没有指定的关键字
        if(highlightFieldMap.containsKey("content")) {
            //获取到所有的content中包含高亮的语句
            Text[] texts = searchHit.getHighlightFields().get("content").fragments();

            StringBuffer content = new StringBuffer();

            for(Text text : texts) {
                if(null != text) {
                    content.append(text.toString());
                }
            }
            news.setContent(content.toString());
        }

        if(highlightFieldMap.containsKey("title")) {
            Text[] texts = searchHit.getHighlightFields().get("title").fragments();

            StringBuffer title = new StringBuffer();

            for(Text text : texts) {
                if(null != text) {
                    title.append(text.toString());
                }
            }
            news.setTitle(title.toString());
        }
        return news;
    }
}
```

#### 10.前端VUE的实现

A. 安装ElementUI和axios

```
npm install ElementUI VueAxios axios --save
```

B. 导入ElementUI和axios

```javascript
import Vue from 'vue'
import App from './App.vue'
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
import VueAxios from "vue-axios";
import axios from 'axios'

Vue.use(VueAxios, axios)
Vue.use(ElementUI);

new Vue({
  render: h => h(App),
}).$mount('#app')
```

C.页面的编写

```html
 
     
         
             
                 
                     
                      
                     搜索一下 
                 
             
         
          
         
             
                 
                 
                        
                      
                 
             
         
     
 

 
    export default {
        data() {
            return {
                searchValue: '',
                dataList: []
            }
        },
        methods: {
            querySearch(queryString, cb) {
                this.axios.get("http://localhost:8081/search?text=" + queryString)
                    .then(resp => {
                        let datas = resp.data;
                        cb(datas);
                    })
            },
            executeSearch() {
                this.axios.get("http://localhost:8081/search/execute?text=" + this.searchValue)
                    .then(resp => {
                        this.dataList = resp.data;
                    });
            }
        }
    }

 

 
    .search-box {
        margin-top: 10px;
    }
    .el-autocomplete {
        width: 80% !important;
    }
    .el-button {
        width: 20% !important;
    }
    .el-card {
        height: 250px;
        overflow: hidden;
        margin-bottom: 10px;
    }
 
```

#### 11.页面效果

![](case/success.png)



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)