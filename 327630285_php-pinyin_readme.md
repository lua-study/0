#php-pinyin

php 支持中文汉字转拼音单元（支持生僻字）。

之前用的汉字转拼音单元 已经不能满足需求了，自己重新整理+优化了一下。

方式：先用gbk判断码表，取不到的字用生僻字字典。


（需要 php-mb_string 扩展支持）


## 方法： ##


class pinyin{

	// $str : 需要转换的汉字（只支持utf-8）
	// $first_char : 是否只取首字母
    // $split_char : 生成每个字间的分隔符
	static function get($str, $first_char = 0, $split_char = '')

}



## 例： ##


`$str = '是默认的编码方式。对于英文文件是ASCII编码，对于简体中文文件是GB2312编码（只针对Windows简体中文版，如果是繁体中文版会采用Big5码）魍魉,交媾,蒯草';`

// 默认模式

`pinyin::get($str), NL;`

// 全拼音+带分隔线

`pinyin::get($str, 0, '-'), NL;`


// 拼音字母+带分隔线

`pinyin::get($str, 1, '-'), NL;`



## 已知问题 ##

1. 多音字未处理, 重庆 会被转成 zhongqing 

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)