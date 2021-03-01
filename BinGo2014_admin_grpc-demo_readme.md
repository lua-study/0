# grpc demo

> 使用环境

- jdk 1.8
- gradle 5.3
- springboot 1.5.10.RELEASE
- protobuf 3.0.0
- protoc-gen-grpc-java 1.0.3
- protobuf-gradle-plugin 0.8.8

> the `protobuf-gradle-plugin 0.8.0`may incompatible with the `gradle 5.3`, i update the `protobuf-gradle-pluin 0.8.8`, which work well;


## grpc-server

### 使用 grpc-server-spring-boot-starter 快速构建
```
compile group: 'net.devh', name: 'grpc-server-spring-boot-starter', version: '1.3.0-RELEASE'
```

### `.proto` 文件目录:

```
src/main/proto
```

一个简单的例子, 详细的语法构建推荐一篇博客 [Protobuf3学习笔记](https://www.jianshu.com/p/ea656dc9b037) 
```proto
syntax="proto3";

option java_package="com.bingo.test.protobuf";

service Greeter {
    rpc sayHello(HelloRequest) returns (HelloResponse);
}

message HelloRequest {
    string name = 1;
}
message HelloResponse{
    string message = 1;
}
```


### `.proto` 生成 `.java` 文件目录：
```
src/main/protoGen
```

> 使用idea gradle工具一键自动生成，`Task -> other -> generatorProto`， 相关的路径在`build.gradle`中可自行配置


### grpc服务端配置
```properties
grpc.server.port=8082
grpc.server.address=127.0.0.1
```

### java服务端代码

```java
import com.bingo.test.protobuf.GreeterGrpc;
import com.bingo.test.protobuf.Hello;
import io.grpc.stub.StreamObserver;
import net.devh.springboot.autoconfigure.grpc.server.GrpcService;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@GrpcService(GreeterGrpc.class)
public class GrpcHelloService extends GreeterGrpc.GreeterImplBase {

    private static final Logger LOGGER = LoggerFactory.getLogger(GrpcHelloService.class);

    @Override
    public void sayHello(Hello.HelloRequest request, StreamObserver  responseObserver) {
        LOGGER.info("request:{}", request.toString());
        Hello.HelloResponse response = Hello.HelloResponse.newBuilder().setMessage("Hello =============> " + request.getName()).build();
        LOGGER.info("response:{}", response.toString());

        responseObserver.onNext(response);
        responseObserver.onCompleted();
    }

}
```



## grpc-client

> 同 sever 一样，自定义`hello.proto`，通过插件生成java代码，服务端客户端交互的代码只需要生成一份就可以了，相互引用公共部分即可。

### grpc客户端端配置
```properties
grpc.client.grpc-server-demo.host[0]=127.0.0.1
grpc.client.grpc-server-demo.port[0]=8082
```


### java客户端调用服务
```java
import com.bingo.test.protobuf.GreeterGrpc;
import com.bingo.test.protobuf.Hello;
import com.bingo.test.protobuf.PhoneServiceGrpc;
import com.bingo.test.protobuf.TestServer;
import io.grpc.Channel;
import net.devh.springboot.autoconfigure.grpc.client.GrpcClient;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GRpcClientController {

    @GrpcClient("grpc-server-demo")
    private Channel serverChannel;

    @GetMapping("/hello/{name}")
    public String sayHello(@PathVariable String name){
        GreeterGrpc.GreeterBlockingStub stub = GreeterGrpc.newBlockingStub(serverChannel);
        Hello.HelloResponse response = stub.sayHello(Hello.HelloRequest.newBuilder().setName(name).build());
        return response.getMessage();
    }

    @GetMapping("/addPhone/{uid}/{phoneNumber}/{phoneType}")
    public String addPhone(@PathVariable Integer uid, @PathVariable String phoneNumber, @PathVariable TestServer.PhoneType phoneType) {
        PhoneServiceGrpc.PhoneServiceBlockingStub stub = PhoneServiceGrpc.newBlockingStub(serverChannel);
        TestServer.AddPhoneToUserRequest request = TestServer.AddPhoneToUserRequest.newBuilder().setUid(uid).setPhoneType(phoneType)
                .setPhoneNumber(phoneNumber).build();
        TestServer.AddPhoneToUserResponse addPhoneToUserResponse = stub.addPhoneToUser(request);
        return addPhoneToUserResponse.toString();
    }
}
```


## 测试效果

> GET localhost:8080/hello/zhangsan

*response*

```
Hello =============> zhangsan
```

服务端打印日志：
```
2019-07-26 15:47:58.185  INFO 9728 --- [ault-executor-0] c.b.g.server.service.GrpcHelloService    : request:name: "zhangsan"

2019-07-26 15:47:58.188  INFO 9728 --- [ault-executor-0] c.b.g.server.service.GrpcHelloService    : response:message: "Hello =============> zhangsan"
```


*服务端down response*
```
{
    "timestamp": 1564127547190,
    "status": 500,
    "error": "Internal Server Error",
    "exception": "io.grpc.StatusRuntimeException",
    "message": "UNAVAILABLE",
    "path": "/hello/zhangsan"
}
```



---

> 本例只是一个简单的demo，离生产还有很长的路要走。服务注册，负载均衡，服务熔断，复杂格式交互，都是需要考虑的内容


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)