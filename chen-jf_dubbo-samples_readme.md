# Dubbo Samples

Samples for Apache Dubbo

[![Build Status](https://travis-ci.org/apache/dubbo-samples.svg?branch=master)](https://travis-ci.org/apache/dubbo-samples) 
![license](https://img.shields.io/github/license/apache/dubbo-samples.svg)

This repository contains a number of projects to illustrate various usages of Dubbo from basic to advanced, pls. check README in each individual sub projects. It is also helpful to cross reference to [Dubbo User Manual](http://dubbo.apache.org/en-us/docs/user/quick-start.html) to understand the features demoed in this project.

## Build and Run Samples

To compile all samples, run the following command in the top directory of this project, or step into the sub directories to compile one single sample:

```bash
mvn clean package
```

You may need to read each individual README under the sub directories if it has to understand how to build and run.

## Integration Test

This project is also used for integration test for dubbo. 

**How to build and run a integration test**

Most of integration tests will reply on a home-brew maven plugin to perform correctly when dubbo service is deployed in docker environment. This maven plugin is provided in 'dubbo-maven-address-plugin' module and should be installed before running any integration test:

```bash
cd dubbo-maven-address-plugin
mvn clean install
```

It is as simple as stepping into a sub directory and then executing the following command, for example:

```bash
cd dubbo-samples-annotation
mvn -Pdubbo-integration-test clean verify
```

If docker container fails to startup successfully in any case, you can use *-Ddocker.showLogs* to check its logging output to understand what happens.

```bash
mvn -Ddocker.showLogs -Pdubbo-integration-test clean verify
```

Pls. note integration test relies on docker environment, make sure docker environment is available before run it.

**How to add more integration test**

If you are interested in contributing more integration test for dubbo, pls. read further to understand how to enable integration test for one particular sample from the scratch.

1. Related maven properties relevant to integration test:

```xml
 4.3.16.RELEASE 
 4.12 
 0.30.0 
 1.2.0 
 2.21.0 
 ${artifactId}:${dubbo.version} 
 20880 
 org.apache.dubbo.samples.attachment.AttachmentProvider 
```

Integration test leverages [docker](https://docs.docker.com/get-started/) to setup test environment, more accurately, to start dubbo provider instance, and any other supporting systems like registry center if necessary, in docker. Therefore, there are two maven plugins required for composing docker image and start-and-stop the docker instances before-and-after the integration test: 1. [jib-maven-plugin](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin) from google 2. [docker-maven-plugin](https://github.com/fabric8io/docker-maven-plugin) from fabric8.

2. Configure maven profile:

Since we use profile 'dubbo-integration-test' to enable integration test, make sure the following plugins are configured under the desire profile, which is **'dubbo-integration-test'**:

```xml
 
     
     dubbo-integration-test 
     
           
      
     
 
```

3. Configure dubbo-maven-address-plugin

```xml
 
     org.apache.dubbo 
     dubbo-maven-address-plugin 
     1.0-SNAPSHOT 
     
         
             
                 local-address 
             
             
                 dubbo-local-address 
             
             initialize 
         
     
 
```

'dubbo-local-address' is a maven property in which dubbo provider's IP address is stored. 

4. Configure jib-maven-plugin

```xml
 
     com.google.cloud.tools 
     jib-maven-plugin 
     ${jib-maven-plugin.version} 
     
         
             ${java-image.name} 
         
         
             ${image.name} 
         
         
             ${main-class} 
             
                 ${dubbo.port}   
                 2181   
             
             
                 ${dubbo-local-address} 
             
         
    
     
         
             package 
                 
                     dockerBuild 
                 
         
     
 
```

' ' is an environment variable to instruct dubbo provider the IP address used for registering to service registration center. Since the dubbo provider will run within a docker instance, a host's IP address (detected from dubbo-maven-address-plugin) must be used in order to allow it discovered by the dubbo client running outside docker instance. 

5. Configure docker-maven-plugin

```xml
 
     io.fabric8 
     docker-maven-plugin 
     ${docker-maven-plugin.version} 
     
         
             
                 ${image.name} 
                 
                     
                         ${dubbo.port}:${dubbo.port}   
                         2181:2181   
                     
                     
                         
                         dubbo service started  
                     
                 
             
         
     
     
         
             start 
             pre-integration-test 
             
                 start 
             
         
         
             stop 
             post-integration-test 
             
                 stop 
             
         
     
 
```

'docker-maven-plugin' will start the specified docker image before integration test (phase 'pre-integration-test') and stop it after integration test (phase 'post-integration-test').

6. Configure maven-failsafe-plugin

```xml
 
     org.apache.maven.plugins 
     maven-failsafe-plugin 
     ${maven-failsafe-plugin.version} 
     
         
             
                 integration-test 
                 verify 
             
             
                 
                     **/*IT.java 
                 
             
         
     
 
```

A integration test is basically a JUnit based test class, but with its name suffixed by 'IT'.

That's it, then feel free to add more integration test for the Dubbo project. You may need to refer to 'dubbo-samples-annotation' or 'dubbo-samples-attachment' for more details, have fun.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)