NaCL Cert System Specification based on TweetNaCL
-------------------------------------------------

NACL Certification System


### Certification file format as JSON consists of description and signature parts

* Description object defined as below

```js
  {  
      // common part or request part  
        "version": string,       // version: '1.0'  
           "type": string,       // type: 'self', 'ca'  
            "tte": Date as ms,   // cert live time to expire from UTC 1970-01-01T00:00:00Z, ms  
             "ca": string        // CA domain name, like appnet.link,  
                                 // in case self-sign it MUST be filled in advance  
      "publickey": byte array,   // NACL Box public key to sign with CA,  
                                 // or Sign public key to sign by self  
          "names": string array, // domain name to ask sign, ignore for self-sign cert  
            "ips": string array, // domain ip address to ask sign, ignore for self-sign cert
           "macs": string array, // domain mac address to ask sign, ignore for self-sign cert  
              
      // append fields when sign  
            "gid": uuid string,  // cert global id: 16 bytes of uuid string  
       "signtime": Date as ms,   // signed time as ms from UTC 1970-01-01T00:00:00Z  
  }
  ```

* Signature object defined as below

```js
  {  
      signature: byte array      // NACL signature  
  }
  ```
  
* Entire cert object defined as below
```js
  {  
      desc: Description object,  
      sign: Signature object  
  }
  ```

### Cert request object defined as Common part of Description

```js
self-signed:  {  
     // common part or request part  
        "version": string,       // version: '1.0'  
           "type": 'self',       // type: 'self'  
            "tte": Date as ms,   // cert live time to expire from UTC 1970-01-01T00:00:00Z, ms  
             "ca": string        // CA domain name, like appnet.link  
      "publickey": byte array,   // NACL Sign public key to sign by self  
  }  
  
ca-signed:  {  
     // common part or request part  
        "version": string,       // version: '1.0'  
           "type": 'ca',         // type: 'ca'  
            "tte": Date as ms,   // cert live time to expire from UTC 1970-01-01T00:00:00Z, ms  
             "ca": string        // CA domain name, like appnet.link  
      "publickey": byte array,   // NACL box public key to sign
        
          "names": string array, // domain name to ask sign, ignore for self-sign cert      
            "ips": string array, // domain ip address to ask sign, ignore for self-sign cert
           "macs": string array, // domain mac address to ask sign, ignore for self-sign cert  
  }
  ```

 


### Reference implementations

* [JS/NodeJS](https://github.com/InstantWebP2P/nacl-cert)
* [Java/Android](https://github.com/InstantWebP2P/node-android/blob/master/app/src/main/java/com/iwebpp/crypto/NaclCert.java)

### License
(MIT)

Copyright (c) 2014-present Tom Zhou(appnet.link@gmail.com)




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)