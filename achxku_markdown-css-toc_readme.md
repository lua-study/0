# markdown-css-toc

把 toc.style 中的代码插入到 markdown 生成的 HTML 文件的 head 标签中，将会自动根据 markdown 的标题按级别生成导航目录

在 MarkdownPad2 中，可以通过 菜单->工具->选项->高级->HTML head编辑器 来自动插入以上代码。

```

  
 
 //是否显示导航栏
 var showNavBar = true;
 //是否展开导航栏
 var expandNavBar = true;
 
 $(document).ready(function(){
    var h1s = $("body").find("h1");
    var h2s = $("body").find("h2");
    var h3s = $("body").find("h3");
    var h4s = $("body").find("h4");
    var h5s = $("body").find("h5");
    var h6s = $("body").find("h6");

    var headCounts = [h1s.length, h2s.length, h3s.length, h4s.length, h5s.length, h6s.length];
    var vH1Tag = null;
    var vH2Tag = null;
    for(var i = 0; i   0){
            if(vH1Tag == null){
                vH1Tag = 'h' + (i + 1);
            }else{
                vH2Tag = 'h' + (i + 1);
            }
        }
    }
    if(vH1Tag == null){
        return;
    }

    $("body").prepend(' ' + 
		'  ' +
        ' ' + 
            ' 目录▲ ' + 
        ' ' + 
        '   ' + 
    ' ' );

    var vH1Index = 0;
    var vH2Index = 0;
    $("body").find("h1,h2,h3,h4,h5,h6").each(function(i,item){
        var id = '';
        var name = '';
        var tag = $(item).get(0).tagName.toLowerCase();
        var className = '';
        if(tag == vH1Tag){
            id = name = ++vH1Index;
            name = id;
            vH2Index = 0;
            className = 'item_h1';
        }else if(tag == vH2Tag){
            id = vH1Index + '_' + ++vH2Index;
            name = vH1Index + '.' + vH2Index;
            className = 'item_h2';
        }
        $(item).attr("id","wow"+id);
		$(item).addClass("wow_head");
        $("#AnchorContent").css('max-height', ($(window).height() - 180) + 'px');
        $("#AnchorContent").append('  '+name+" · "+$(this).text()+'  ');
    });

    $("#AnchorContentToggle").click(function(){
        var text = $(this).html();
        if(text=="目录▲"){
            $(this).html("目录▼");
            $(this).attr({"title":"展开"});
        }else{
            $(this).html("目录▲");
            $(this).attr({"title":"收起"});
        }
        $("#AnchorContent").toggle();
    });
    $(".anchor-link").click(function(){
        $("html,body").animate({scrollTop: $($(this).attr("link")).offset().top}, 500);
    });
	
	var headerNavs = $(".BlogAnchor li .nav_item");
	var headerTops = [];
	$(".wow_head").each(function(i, n){
		headerTops.push($(n).offset().top);
	});
	$(window).scroll(function(){
		var scrollTop = $(window).scrollTop();
		$.each(headerTops, function(i, n){
			var distance = n - scrollTop;
			if(distance >= 0){
				$(".BlogAnchor li .nav_item.current").removeClass('current');
				$(headerNavs[i]).addClass('current');
				return false;
			}
		});
	});

	if(!showNavBar){
		$('.BlogAnchor').hide();
	}
	if(!expandNavBar){
		$(this).html("目录▼");
        $(this).attr({"title":"展开"});
		$("#AnchorContent").hide();
	}
 });
 
 
    /*导航*/
    .BlogAnchor {
        background: #f1f1f1;
        padding: 2px;
        line-height: 180%;
        position: fixed;
        left: 25px;
        top: 48px;
        border: 2px solid #7EA8E1;
    }
    .BlogAnchor p {
        font-size: 18px;
        color: #7EA8E1;
        margin: 0 0 0.3rem 0;
        text-align: left;
    }
    .BlogAnchor .AnchorContent {
        padding: 5px 0px;
        overflow: auto;
    }
    .BlogAnchor li{
        text-indent: 0.5rem;
        font-size: 14px;
        list-style: none;
    }
	.BlogAnchor li .nav_item{
		padding: 3px;
	}
    .BlogAnchor li .item_h1{
        margin-left: 0rem;
    }
    .BlogAnchor li .item_h2{
        margin-left: 2rem;
        font-size: 0.8rem;
    }
	.BlogAnchor li .nav_item.current{
		color: white;
		background-color: #5cc26f;
	}
    #AnchorContentToggle {
        font-size: 15px;
        font-weight: bold;
        color: #7FA9E2;
        display: inline-block;
        line-height: 20px;
        background: #F1F1F1;
        font-style: normal;
        border: 1px solid #7EA8E1;
        padding: 1px 8px;
    }
    .BlogAnchor a:hover {
        color: #5cc26f;
    }
    .BlogAnchor a {
        text-decoration: none;
    }
 

```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)