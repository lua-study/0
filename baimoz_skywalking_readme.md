Apache SkyWalking
==========

 

**SkyWalking**: an APM(application performance monitor) system, especially designed for
microservices, cloud native and container-based (Docker, Kubernetes, Mesos) architectures.

[![GitHub stars](https://img.shields.io/github/stars/apache/skywalking.svg?style=for-the-badge&label=Stars&logo=github)](https://github.com/apache/skywalking)
[![Twitter Follow](https://img.shields.io/twitter/follow/asfskywalking.svg?style=for-the-badge&label=Follow&logo=twitter)](https://twitter.com/AsfSkyWalking)

[![Maven Central](https://img.shields.io/maven-central/v/org.apache.skywalking/apache-skywalking-apm.svg)](http://skywalking.apache.org/downloads/)
[![CI/IT Tests](https://github.com/apache/skywalking/workflows/CI%20AND%20IT/badge.svg?branch=master)](https://github.com/apache/skywalking/actions?query=branch%3Amaster+event%3Apush+workflow%3A%22CI+AND+IT%22)
[![E2E Tests](https://github.com/apache/skywalking/workflows/E2E/badge.svg?branch=master)](https://github.com/apache/skywalking/actions?query=branch%3Amaster+event%3Apush+workflow%3AE2E)

# Abstract
**SkyWalking** is an open source APM system, including monitoring, tracing, diagnosing capabilities for distributed system
in Cloud Native architecture.
The core features are following.

- Service, service instance, endpoint metrics analysis
- Root cause analysis
- Service topology map analysis
- Service, service instance and endpoint dependency analysis
- Slow services and endpoints detected
- Performance optimization
- Distributed tracing and context propagation
- Database access metrics. Detect slow database access statements(including SQL statements).
- Alarm


 

SkyWalking supports to collect telemetry (traces and metrics) data from multiple sources
and multiple formats,
including
1. Java, [.NET Core](https://github.com/SkyAPM/SkyAPM-dotnet), [NodeJS](https://github.com/SkyAPM/SkyAPM-nodejs) and [PHP](https://github.com/SkyAPM/SkyAPM-php-sdk) auto-instrument agents in SkyWalking format
1. Manual-instrument [Go agent](https://github.com/tetratelabs/go2sky) in SkyWalking format.
1. Istio telemetry format
1. Envoy gRPC Access Log Service (ALS) format in Istio controlled service mesh
1. Envoy Metrics Service format.
1. Zipkin v1/v2 format.
1. Jaeger gRPC format.


# Document
- [7.x Documents](docs/README.md).
- [6.x Documents](https://github.com/apache/skywalking/blob/6.x/docs/README.md).



# Downloads
Please head to the [releases page](http://skywalking.apache.org/downloads/) to download a release of Apache SkyWalking.


# Code of conduct
This project adheres to the Contributor Covenant [code of conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.
Please follow the [REPORTING GUIDELINES](CODE_OF_CONDUCT.md#reporting-guidelines) to report unacceptable behavior.

# Live Demo
Host in Beijing. Go to [demo](http://122.112.182.72:8080).

**Video on youtube.com**

[![RocketBot UI](http://img.youtube.com/vi/JC-Anlshqx8/0.jpg)](http://www.youtube.com/watch?v=JC-Anlshqx8)


# Screenshot
 
   
      Dashboard  
   
   
       
       
   
   
        Topology Map  
        Trace  
   
   
        
        
   
 

# Compiling project
Follow this [document](docs/en/guides/How-to-build.md).

# Contact Us
* Submit an [issue](https://github.com/apache/skywalking/issues)
* Mail list: **dev@skywalking.apache.org**. Mail to `dev-subscribe@skywalking.apache.org`, follow the reply to subscribe the mail list.
* Join `skywalking` channel at [Apache Slack](https://join.slack.com/t/the-asf/shared_invite/enQtNzc2ODE3MjI1MDk1LTAyZGJmNTg1NWZhNmVmOWZjMjA2MGUyOGY4MjE5ZGUwOTQxY2Q3MDBmNTM5YTllNGU4M2QyMzQ4M2U4ZjQ5YmY). If the link is not working, find the latest one at [Apache INFRA WIKI](https://cwiki.apache.org/confluence/display/INFRA/Slack+Guest+Invites).
* QQ Group: 392443393(2000/2000, not available), 901167865(available)

# Who Uses SkyWalking?
Hundreds of companies and organizations use SkyWalking for research, production, and commercial product.

 

The [PoweredBy](docs/powered-by.md) page includes more users of the project.
Users are encouraged to add themselves to there.

# Landscapes

 
  
 &nbsp;&nbsp; 
  
SkyWalking enriches the  CNCF CLOUD NATIVE Landscape.

 

 
   
   Our project enriches the  OpenAPM Landscape! 
 

# License
[Apache 2.0 License.](/LICENSE)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)