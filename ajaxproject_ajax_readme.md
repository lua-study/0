# 原生ajax以及跨域访问百度ajax

原生ajax:

```
function ajax(mJson){
	var xhr = window.XMLHttpRequest?new XMLHttpRequest():new ActiveXObject("Microsoft.XMLHTTP");
	var method = mJson.method || "get";
	var url = mJson.url;
	var asyn = mJson.asyn || true;
	var data = mJson.data;
	var success = mJson.success;

	if(method == "get" && data){
		url += "?"+data+"&"+Math.random();
	}
	xhr.open(method,url,asyn);
	//设置请求头
	xhr.setRequestHeader("content-type","application/x-www-form-urlencoded");
	if(method == "post" && data){
		xhr.send(data);
	}else{
		xhr.send();
	}
	xhr.onreadystatechange = function(){
		if(xhr.readyState==4 && xhr.status==200){
			if(success)success(xhr.responseText);
		}
	}
};
```

跨域访问百度 效果如下：

![](images/img.gif)

js demo code:

```
	var oTxt = document.getElementById("txt");
	var oList = document.getElementById("list");
	oTxt.onkeyup = function(){
		var val = this.value;
		var oS = document.createElement("script");
		oS.src = "https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd="+val+"&cb=andong";
		document.body.appendChild(oS);
		document.body.removeChild(oS);
	};
	function andong(mJson){
		var data = mJson.s;
		var str = "";
		for(var i=0;i  "+data[i]+"  ";
		}
		oList.innerHTML = str;
	}
	oList.onmouseover = function(ev){
		ev = ev||event;
		var target = ev.target || srcElement;
		//console.log(target.tagName+"===="+ev.currentTarget.tagName);
		target.style.background = "#ccc";
	};
	oList.onmouseout = function(ev){
		ev = ev||event;
		var target = ev.target || srcElement;
		//console.log(target.tagName+"===="+ev.currentTarget.tagName);
		target.style.background = "";
	};
```

jquery demo code:

```
    $(function(){
        $("input").keyup(function(){
            $.ajax({
                type:"get",
                data:"wd="+$(this).val(),
                dataType:"jsonP",
                url:"http://suggestion.baidu.com/su",
                success:function(data){
                }
            });
        });
    });
    var baidu={
        sug:function(data){
            for(var i=0;i 8||$("input").val().length==0){
                    $("li").removeAttr("class")
                }
            }

        }
    }
```



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)