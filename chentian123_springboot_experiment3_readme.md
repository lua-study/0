#            东莞理工学院网络空间安全学院实验报告

院（系）名称：网络空间安全学院  
专业班级： 17软卓2班  
学号： 201741404247  
姓名： 陈钿  
实验题目： 实验三 全球新型冠状病毒实时数据统计应用程序的设计与实现  
实验日期：2020.5.10  
实验（上机）学时： 4  
成绩： 


------

# 1.实验目的

1. 掌握使用Spring框架自带的RestTemplate工具类爬取网络数据；
2. 掌握使用Spring框架自带的计划任务功能；
3. 掌握使用Apache Commons CSV组件解释CSV文件；
4. 掌握Java 8的Stream API处理集合类型数据；
5. 了解使用模板引擎或前端框架展示数据。

------

# 2.实验环境

1.  JDK 1.8或更高版本
2.  Maven 3.6+
3.  IntelliJ IDEA
4.  commons-csv 1.8+

***

# 3.实验任务

### 1. 通过IntelliJ IDEA的Spring Initializr向导创建Spring Boot项目。
### 2. 添加功能模块：spring MVC、lombok、commons-csv等。

- 截图如下：
 

- pom.xml文件代码如下：
```xml
     
         org.apache.commons 
         commons-csv 
         1.8 
     
```

### 3. 使用Spring框架自带的RestTemplate工具类爬取数据。

- 代码如下：
``` java
   RequestEntity  requestEntity = RequestEntity
                    .get(URI.create(URL))
                    .headers(httpsHeaders -> httpsHeaders.add("User-Agent", "陈钿"))
                    .build();
   ResponseEntity  exchange = new RestTemplate().exchange(requestEntity, Resource.class);
   Resource body = exchange.getBody();
```

说明：先实例化一个RequestEntity对象，再通过RestTemplate的exchange方法获取csv文件，这个文件的数据会封装到一个Resource对象中，即"body"。 
     
***


### 4.分析csv文件的数据结构，定义model类

- 自定义的model类：
```java
@Data
@Builder
public class RegionStats {
    private String state;      //    州/省
    private String country;    //    国家
    private int latestTotalCases;  //   最新确诊数
    private int diffFromPrevDay;   //   新增确诊数
}
```
***

### 5. 使用Apache Commons CSV组件解释CSV文件

- 判断前面爬取的Resource对象"body"是否有数据；
- 通过该Resource对象的getInputStream方法获取csv文件的输入流；
- 利用for循环流中的数据封装成自定义的model对象，并将对象写入到List列表中。
- 代码如下：
```java
if (body != null) {
    InputStreamReader inputStreamReader = new InputStreamReader(body.getInputStream(), "UTF-8");
    CSVParser parser = new CSVParser(inputStreamReader, CSVFormat.EXCEL.withHeader());
    regionStatsList.clear();
    for (CSVRecord record : parser) {
        regionStatsList.add(RegionStats.builder()
                .state(record.get("Province/State"))
                .country(record.get("Country/Region"))
                .latestTotalCases(Integer.parseInt(record.get(record.size() - 1)))
                .diffFromPrevDay(Integer.parseInt(record.get(record.size() - 1)) - Integer.parseInt(record.get(record.size() - 2)))
                .build());
            }
        }
```
说明：方法 record.get("...")用于获取指定列的数据。

***

### 6. 使用Spring框架自带的计划任务功能定时更新统计数据并确保应用程序启动时，获取一次统计数据。

- 给爬数据的方法加上@Scheduled注解（每天凌晨1点更新数据）和@PostConstruct注解（启动项目时获取数据）
 
```java
    @Scheduled(cron = "${chen.Schedules.updateVirusDataCron}")
    @PostConstruct
    public void fetchCoronaVirusData() throws IOException {
```
说明：@Scheduled的参数在配置文件中(chen.Schedules.updateVirusDataCron=0 0 1 * * *)
     @PostConstruct该注解被用来修饰一个非静态的void（）方法。被@PostConstruct修饰的方法会在服务器加载Servlet的时候运行，并且只会被服务器执行一次。PostConstruct在构造函数之后执行，init（）方法之前执行。
   

### 7. 单元测试

- 自动装配Service组件，因有@PostConstruct注解，项目启动后对象就被初始化，打印数据看是否成功获取到数据。
- 单元测试代码如下：
```java
@SpringBootTest
class SpringbootExperiment3ApplicationTests {

    @Autowired
    GetDataService getDataService;

    @Test
    void contextLoads(){

        System.out.println(getDataService.regionStatsList);
    }
```
- 测试结果如图：
 

***

### 8. 定义Cotroller控制器。

- 控制器功能：统计全球总确诊人数、当日新增确诊人数；若未带搜索参数（国家名），则返回全部数据，有带搜索参数（国家名）则返回搜索结果；
```java
@Controller
public class GetDataController {

    @Autowired
    GetDataService getDataService;
    @GetMapping("/")
    public String index(Model model,String country){
        Integer latestTotalCases;
        Integer diffFromPrevDay;
        Date nowTime = new Date();
        List   totalList = getDataService.regionStatsList;
        if(country!=null){
            List   countList = totalList.stream().
                                            filter(regionStats -> regionStats.getCountry().equals(country))
                                            .collect(Collectors.toList());
            model.addAttribute("totalList",countList);
        }
        else {
            model.addAttribute("totalList",totalList);
        }
        latestTotalCases = totalList.stream().mapToInt(RegionStats::getLatestTotalCases).sum();
        diffFromPrevDay = totalList.stream().mapToInt(RegionStats::getDiffFromPrevDay).sum();
        model.addAttribute("latestTotalCases",latestTotalCases);
        model.addAttribute("diffFromPrevDay",diffFromPrevDay);
        model.addAttribute("nowTime",nowTime);
        System.out.println(country);
        return "index";
    }
}
```

说明：搜索功能通过Stream API实现，利用.filter()筛选出数据，并用.collect(Collectors.toList())封装到List列表。


### 9. 定义前端数据展示页面

- 页面通过thymeleaf模板引擎实现数据展示
 

- 搜索结果：
 

***


# 4. 实验总结

- 完成该实验让我学到了很多东西，第一次接触java爬虫，没有想象中的难。老师的实验也比较潮流，实用性高，老师很棒，愿意花更多时间跟着老师学习。


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)