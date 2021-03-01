# Enterprise-Registration-Data-of-Chinese-Mainland

中国大陆 31 个省份 1978 年至 2019 年一千多万工商企业注册信息，包含企业名称、注册地址、统一社会信用代码、地区、注册日期、经营范围、法人代表、注册资金、企业类型。

数据以 CSV 、Excel 及 JSON 三种文件类型存储，相应文件分别保存在 Enterprise-Registration-Data/csv、Enterprise-Registration-Data/xls、Enterprise-Registration-Data/json 。

其中 CSV 与 Excel 的格式为：企业名称、统一社会信用代码、注册日期、企业类型、法人代表、注册资金、经营范围、所在省份、地区、注册地址，编码为 UTF-8

JSON 的编码为 UTF-8，文件格式如下：

```json
{
    "name":"企业名称",
    "code":"统一社会信用代码",
    "registrationDay":"注册日期",
    "character":"企业类型",
    "legalRepresentative":"法人代表",
    "capital":"注册资金",
    "businessScope":"经营范围",
    "province":"所在省份",
    "city":"地区",
    "address":"注册地址"
}

```
最新数据会不定期进行更新。

This repository is an dataset of over 10,000,000 enterprise registration data of 31 provinces in Chinese mainland from 1978 to 2019.

The enterprise registration data including 10 items: the name of enterprise,uniform social credit code,registration date,character of economy,legal representative,registered capital,business scope,province,city and registration address.

The dataset represents in three different types: CSV,Excel and JSON,which are located at Enterprise-Registration-Data/csv,Enterprise-Registration-Data/xls and Enterprise-Registration-Data/json respectively.

The order of 10 items in CSV and Excel are : 

name,code,registrationDay,character,legalRepresentative,capital,businessScope,province,city,address. And the record in the JSON file is represented as below:

```json
{
    "name":"the name of enterprise",
    "code":"uniform social credit code",
    "registrationDay":"registration date",
    "character":"character of economy",
    "legalRepresentative":"legal representative",
    "capital":"registered capital",
    "businessScope":"business scope",
    "province":"province",
    "city":"city",
    "address":"registration address"
}

```

The encoding of all those files are UTF-8.

This repository will be updated from time to time.Give me a star or fork this repository if you like it.

### Citation format:

如果您需要在论文中引用本数据集，您可以使用下列引用格式进行引用：

刘文. 中国大陆企业工商注册信息数据集[EB/OL].https://github.com/imhuster/Enterprise-Registration-Data-of-Chinese-Mainland, 2019-06-01.

If you want to use this dataset in you paper,you can use the flowing citation format:

Wen Liu. Enterprise-Registration-Data-of-Chinese-Mainland[EB/OL].https://github.com/imhuster/Enterprise-Registration-Data-of-Chinese-Mainland, 2019-06-01.


### License

本仓库数据集源自网络，本人不对数据的真实性负责，您引用本仓库内容或者对内容进行修改演绎时，请署名并以相同方式共享，谢谢。

The data of this repository is collected from the several open data web sites of Chinese government and this repository is released under [Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

### Announcement

本仓库数据的收集行为严格遵守《中华人民共和国网络安全法》及《中华人民共和国刑法》中的相关规定，特此声明以下三点：

1. 本仓库的数据的爬取严格遵守相关政府公开数据网站的“Robots协议”、没有采取任何规避或突破反“爬虫”安防措施的技术手段、没有任何越权的行为；

2. 爬取的数据是公开的、非隐私的、不属于著作权保护范围的信息，数据也仅用于学术目的，本人未从数据中获取任何经济利益；

3. 爬虫的爬取行为未对相关网站的正常运行造成影响。

   

   



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)