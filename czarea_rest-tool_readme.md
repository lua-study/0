>[源码地址：rest-tool](https://gitee.com/czarea/rest-tool.git)

- springboot2.1.4
- java11
- gradle5.4.1

### 简介

java中http请求封装历史

![RestTemplate.png](http://www.wailian.work/images/2019/06/05/RestTemplate.png)

Spring提供的RestTemplate是基于HttpClient等基础上封装，它简化了与http服务的通信方式，统一了RESTful的标准，封装了http链接，我们只需要传入url及返回值类型即可。相较于之前常用的HttpClient，RestTemplate是一种更优雅的调用RESTful服务的方式。

RestTemplate默认依赖JDK提供http连接的能力（HttpURLConnection），如果有需要的话也可以替换为例如 Apache HttpComponents、OkHttp或者Netty等其它HTTP library。默认SpringBoot封装了HttpClient,OkHttp，只用把HttpClient或者OkHttp加入到依赖jar即可。

```text
implementation("org.apache.httpcomponents:httpclient:4.5.8")
implementation("com.squareup.okhttp3:okhttp:3.14.2")
```

### 实现逻辑

RestTemplate包含以下几个部分：

- UriTemplateHandler 地址模版转换器 默认使用@PathVariable("xx")方式
- RequestFactory
- HttpMessageConverter 对象转换器
- ClientHttpRequestFactory 默认是JDK的HttpURLConnection
- ResponseErrorHandler 异常处理
- ClientHttpRequestInterceptor 请求拦截器

一般使用RestTemplateBuilder构建RestTemplate。

```
@bean
public RestTemplateBuilder restTemplateBuilder(MyResponseErrorHandler myResponseErrorHandler,HttpClientRequestFactory httpClientRequestFactory) {
    HttpMessageConverters converters = this.messageConverters.getIfUnique();
    return new RestTemplateBuilder()
        .rootUri("http://localhost:8080")
        .uriTemplateHandler(new MyUriTemplateHandler())
        .errorHandler(myResponseErrorHandler)
        .requestFactory(httpClientRequestFactory)
        .messageConverters(converters.getConverters())
        .additionalInterceptors(new RestHttpRequestInterceptor());
}
```

实现业务逻辑

![rest_logic.png](http://www.wailian.work/images/2019/06/05/rest_logic.png)

### 简单使用

**GET**
```
@Test
public void testSGet() {
    Foo foo = restTemplate.getForEntity(rootUrl + "/foos/s/1", Foo.class).getBody();
    Assert.assertEquals(foo.getName(), "name1");
}
```

**POST**
```
@Test
public void testSave() {
    Foo foo = new Foo(1000L, "foo");
    Response response = restTemplate.postForEntity(rootUrl + "/foos", foo, Response.class).getBody();
    Assert.assertEquals(response.getCode(), 200);
}
```

**泛型结果请求**

泛型使用：ParameterizedTypeReference 

```
@Test
public void testList() {
    Foo foo = new Foo(1L, "name1");
    Page page = new Page(0, 10, foo);
    String url = uriTemplateHandler.expand(rootUrl + "/foos", page).toString();
    Response > response = restTemplateService
        .request(url, HttpMethod.GET, null, new ParameterizedTypeReference >>() {
        });
    Assert.assertEquals(100, response.getData().getTotal());
}

```

**文件上传**
```
@Test
public void testUploadByResource() {
    LinkedMultiValueMap  map = new LinkedMultiValueMap<>();
    map.add("file", new ClassPathResource("test.txt"));
    HttpHeaders headers = new HttpHeaders();
    headers.setContentType(MediaType.MULTIPART_FORM_DATA);
    HttpEntity > requestEntity = new HttpEntity<>(map, headers);
    ResponseEntity  result = restTemplate.exchange(rootUrl + "/foos/upload", HttpMethod.POST, requestEntity, Response.class);
    Assert.assertEquals(result.getBody().getCode(), 200);
}
```


**文件下载**
```
@Test
public void testDownload() throws UnsupportedEncodingException {
    // 小文件
    RequestEntity requestEntity = RequestEntity.get(URI.create(rootUrl + "/foos/download")).build();
    ResponseEntity  responseEntity = restTemplate.exchange(requestEntity, byte[].class);
    byte[] downloadContent = responseEntity.getBody();

    String str = new String(downloadContent, "UTF-8");

    // 大文件
    ResponseExtractor > responseExtractor = response -> {
        File rcvFile = File.createTempFile("rcvFile", "zip");
        FileCopyUtils.copy(response.getBody(), new FileOutputStream(rcvFile));
        return ResponseEntity.status(response.getStatusCode()).headers(response.getHeaders()).body(rcvFile);
    };
    ResponseEntity  getFile = this.restTemplate
        .execute(rootUrl + "/foos/download", HttpMethod.GET, null, responseExtractor);
}
```



**设置自定义异常处理**
```
public class MyResponseErrorHandler implements ResponseErrorHandler {

    private final Set  acceptableStatus;

    public MyResponseErrorHandler(HttpClientProperties httpClientProperties) {
        this.acceptableStatus = httpClientProperties.getAcceptableStatus();
    }

    @Override
    public boolean hasError(ClientHttpResponse response) throws IOException {
        return !acceptableStatus.contains(response.getRawStatusCode());
    }

    @Override
    public void handleError(ClientHttpResponse response) throws IOException {
        log.error("Response error: {} {}", response.getStatusCode(), response.getStatusText());
        StringBuilder inputStringBuilder = new StringBuilder();
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(response.getBody(), "UTF-8"));
        String line = bufferedReader.readLine();
        while (line != null) {
            inputStringBuilder.append(line);
            inputStringBuilder.append('\n');
            line = bufferedReader.readLine();
        }
        if (log.isDebugEnabled()) {
            log.debug("============================response begin==========================================");
            log.debug("Status code  : {}", response.getStatusCode());
            log.debug("Status text  : {}", response.getStatusText());
            log.debug("Headers      : {}", response.getHeaders());
            log.debug("Response body: {}", inputStringBuilder.toString());
            log.debug("=======================response end=================================================");
        }
        throw new MyException(inputStringBuilder.toString());
    }
}
```

**设置拦截器**
```
public class RestHttpRequestInterceptor implements ClientHttpRequestInterceptor {

    @Override
    public ClientHttpResponse intercept(HttpRequest request, byte[] body,
        ClientHttpRequestExecution execution) throws IOException {
        logRequestDetails(request);
        return execution.execute(request, body);
    }

    private void logRequestDetails(HttpRequest request) {
        log.info("Headers: {}", request.getHeaders());
        log.info("Request Method: {}", request.getMethod());
        log.info("Request URI: {}", request.getURI());
    }
}
```



### 封装扩展

**GET请求替换为query params方法**
```
public class MyUriTemplateHandler implements UriTemplateHandler {

    @Autowired
    private ObjectMapper mapper;

    @Override
    public URI expand(String uri, Map  params) {
        UriComponentsBuilder uriComponentsBuilder = UriComponentsBuilder.fromHttpUrl(uri);
        for (Map.Entry  entry : params.entrySet()) {
            String firstKey = entry.getKey();
            if (entry.getValue() instanceof Map) {
                Map values = (Map) entry.getValue();
                values.forEach((k, v) -> {
                    if (v != null) {
                        uriComponentsBuilder.queryParam(firstKey + "." + k, v);
                    }
                });
            } else {
                if (entry.getValue() != null) {
                    uriComponentsBuilder.queryParam(firstKey, entry.getValue());
                }
            }
        }
        uri = uriComponentsBuilder.build().toUriString();
        return URI.create(uri);
    }

    @Override
    public URI expand(String uri, Object... params) {
        if (params.length != 0 && params[0] != null) {
            Map map = mapper.convertValue(params[0], Map.class);
            return expand(uri, map);
        } else {
            return URI.create(uri);
        }
    }
}
```

**替换FastJson**

这个比较简单，注册FastJson，加入到MessageConverters列中，但是涉及到上传和下载的时候还是不要使用FastJson的比较好，会有各种坑。这里是简单的解决办法。继承FastJsonHttpMessageConverter覆盖supports方法，只解析自己想要的包下的类。去除（ClassPathResource等文件上传下载解析）

```
public class MyFastJsonHttpMessageConverter extends FastJsonHttpMessageConverter {

    @Override
    protected boolean supports(Class  clazz) {
        if (clazz == null) {
            return true;
        }
        if (clazz.getPackageName().contains("com.czarea.rest")) {
            return true;
        } else {
            return false;
        }
    }
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)