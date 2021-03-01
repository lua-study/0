# smart-license

smart-license 是一款用于安全加固的开源项目。
主要服务于非开源产品、商业软件、具备试用功能的付费软件等，为软件提供授权制的使用方式。

名词解释：

- License，通过 smart-license 生成的授权文件，导入至要授权使用的软件产品中。
- 源数据，需要进行 License 加工处理的基础数据。例如，将软件产品运行的配置文件作为**源数据**，经由 smart-license 授权处理后生成 License 文件。
- License源文件，生成 License 的同时，创建一份文件用于记录：源数据，授权时间，过期时间，秘钥对等信息。由软件授权方持有，当客户遗失 License 文件之后可以根据**License源文件**重新生成 License。

适用场景：

- 非开源产品、商业软件、收费软件。
- 限制产品的传播性，每个客户拥有专属 License。
- 同一款软件发行包根据 License 的不同提供不同的服务能力。
- 限定软件授权时效

产品特色：

- 开源，代码完全公开，License的生成原理是透明的。
- 易用，提供二进制包，直接基于命令行生成 License。
- 安全，生成的 License 在一定程度上具备防篡改能力，破解难度大。
- [安全加固](security.md)，采用非对称加密方式对 License源数据 进行预处理，防止伪造License。

如果喜欢该作品，欢迎底下捐赠一杯3.8折的瑞幸咖啡。
#### License运行流程

![](images/smart-license.png)
   
- License申请流程

    ![](images/license_apply.png)

- 找回License

    ![](images/license_forget.png)


#### 使用方式
##### 生成License
1. 下载[smart-license.tar.gz](https://gitee.com/smartboot/smart-license/attach_files)包，解压。
2. 进入bin目录执行以下命令，例如：`./license.sh 1d HelloWorld`。
![](images/demo.gif)
    - 1d：表示授权效期1天，即一天后该License便过期。支持的效期格式包括:
        - h，1h:1小时; 2h:2小时
        - d，1d:1天; 10d:10天
        - y，1y:1年; 2y:2年
    - HelloWorld：表示待加密的license内容。

    实际场景下可以通过license授权不同的产品功能和有效期，例如：`./license.sh 1y features_1:on;features_2:off;`
    如果待授权的license内容为文件，可以采用同样的命令，例如：`./license.sh 1y config.properties` 

3. 执行成功后，会在当前目录下生成 License:`license.txt`以及 License源文件:`source.txt`。
**注意：license.txt是提供给客户的授权文件；而source.txt是由软件提供方持有，其中包含加密私钥，需要妥善保管**
![](images/demo_result.png)

#### 使用License
1. 引入Maven依赖

    ```xml
    
         org.smartboot.license 
         license-client 
         1.0.3 
     
    ```
2. 载入License。如若License已过期，则会触发异常。

    ```java
    public class LicenseTest {
        public static void main(String[] args) throws Exception {
            File file=new File("license.txt");
            License license = new License();
            LicenseEntity licenseEntity=license.loadLicense(file);
            System.out.println(new String(licenseEntity.getData()));
        }
    }
    ```
3. 获取licenseEntity并以此配置启动软件。

#### 还原license
1. 进入bin目录执行以下命令，例如：`./license_revert.sh source.txt`。
![](images/revert.gif)
2. 执行成功后会在当前目录下生成License文件`license_revert.txt`。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)