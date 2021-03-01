# authcode

> 项目中用base64传输数据，使用后发现 base64 会有 +、/、= 三种特殊字符，会影响数据验证签名。所以在base64基础上进行了一次封装。保证数据传输过程无异常，并参考discuz的加密方法，为数据设置过期时间。

# 案例

```php
include 'AuthCode.php';

//打包数据，获得串
$pack = AuthCode::pack([
    'name' => 'wolferhua',
    'mail' => '358273385@qq.com',
    'sex' => 'man',
    'site'=>'http://www.hashmop.com/'
]);

echo $pack . PHP_EOL;
//e3Z6sGiJJAkhIiIcImlJdHEiOBJObTCwUyN0MEZNTGIwMGUwSWRhbUgwSk5VME16VVkwanh6TVdnMVFsRngwbWp2YnlJczR6NWhiV29pT2lKM2IyY3paWEpvZFdFaUxDSnpaWGdpT2lKdFlXNGlMQ0p6YVhSbElqb2lhSFIwY0RwY0wxd3ZkM2QzTG1oaGMyaHRiM0F1WTI5dFhDOGlmUSIsInNpZ24iOiI3OWMwNjM4NzIwNDJhZmEyNjI3ZDFmYzYwMjhkZmVkNyIsInRpbWVzdGFtcCI6MTUxMDIxMTc2OX0

//解包串
$data = AuthCode::unpack($pack);
var_dump($data);
/**
array(4) {
  ["appId"]=>
  string(0) ""
  ["data"]=>
  array(4) {
    ["mail"]=>
    string(16) "358273385@qq.com"
    ["name"]=>
    string(9) "wolferhua"
    ["sex"]=>
    string(3) "man"
    ["site"]=>
    string(23) "http://www.hashmop.com/"
  }
  ["sign"]=>
  string(32) "79c063872042afa2627d1fc6028dfed7"
  ["timestamp"]=>
  int(1510211769)
}

*/
//解包串，获得原始数据。
$data = AuthCode::getDataByPack($pack);
var_dump($data);
/**
array(4) {
  ["mail"]=>
  string(16) "358273385@qq.com"
  ["name"]=>
  string(9) "wolferhua"
  ["sex"]=>
  string(3) "man"
  ["site"]=>
  string(23) "http://www.hashmop.com/"
}
*/
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)