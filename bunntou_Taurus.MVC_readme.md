# Taurus.MVC
Taurus.mvc is a high-performance mvc and webapi framework for asp.net or asp.net core（适合场景：对性能和并发有较高要求的电商、站点、WebAPI等系统，支持.Net Core）,created by Aster（路过秋天） 

QQ交流群：6033006 

Windows 部署：http://taurus.cyqdata.com/  
Linux（CentOS7) 部署：http://mvc.taurus.cyqdata.com
 
Demo：https://github.com/cyq1162/Taurus.MVC.Demo  

 
   Why create Taurus.MVC:   
   I remember when I was fooled by the last company to take charge of the company's e-commerce platform, the situation is this:   
   The original version of the project is outsourced to a third party. Using: WebForm+NHibernate, the code is unsightly, the bug is infinite, and it is often hung up.   
   At the beginning, I recruited a few internship college students to play there. I couldn&rsquo;t make it anymore, and finally I was fooled, haha.   .   .   
   The first feeling that I went in at the time was to redo, but hehe, the boss&rsquo;s mind can&rsquo;t guess.   
   Then the first stage is to maintain the stability of the old project. As long as it is not a problem that needs to be solved by hundreds of servers, it can be handled weakly. After all, there are no three or two, and it is not good for the beam.   
   In the second stage, nature is thinking about redoing:   
    The e-commerce background has been open source:      ASP.NET Aries      framework (supported .NET Core), don't worry too much about brushing;    
     What framework does the e-commerce front desk choose?     
   1: WebForm is too conservative;   
   2: .NET Core 1.1 is too aggressive (now Taurus.MVC already supports .NET Core);   
   3: QBlog (autumn garden) threshold is high;   
   4: Re-write a set, busy business, no time to calm down and think, and time is limited, has submitted a plan to BOSS.   
    Finally, only helplessly choose: ASP.NET MVC.    
   Think about the .NET environment, the popular development framework on the market, all of Microsoft's own (say a good flower?)   
   I also know that some older people also make frameworks, but they are all made for themselves or their own companies (and the angle of thinking and the breadth involved are not the same).   
   There are also some free gifts to the people, but there is no sound in propaganda after three or two;   
   The garden has never taken the initiative to help third-party open source frameworks to promote, relying on the blogger's own passion and sentiment, how long it can support is an unknown number, after all, the framework is no income.   
   A stroke of the pen:   
   Later, the boss fell down..... (tears rush ~~~).   
   Then, there is time to calm down and build a framework with emotions!   
   Finally, Taurus.MVC came out, and it was open source when it came out!   !   !   Open source!   !   open!   Three times.   
   About the frame name: Taurus   
   When I made CYQ.Data ten years ago, the name was not good (blame me), which led to the promotion of resistance.   
   So now, to create a new framework, you must have a good name, after all, you have to take a picture like: Qi Delong, Qi Dongqiang, Qi Delong Dongqiang is so loud and thorough.   
   Previously released a little: ASP.NET Aries business development framework: named: Aries (Aries, gentle with a little pride).   
   So thinking, is the continuation of the Aries series called: Aries.MVC?   
   still is.   .   .   Create a golden zodiac?   
   Then I checked the English words of the thirteen constellations and the eight planets and found that they were not satisfied. If the jumping name is obstructed, then the name should be named.   
   Taurus (Taurus), in fact, the final decision is the pronunciation of the word: off (very big-looking feeling, and full of imagination, the feeling of a little Mimi in the explosion).   
   
   Applicable scenarios for the framework:   
   Choosing a framework is a matter of learning for the master; it is only a choice for the novice.   
   When I was young, I was forced to choose only the framework created by Microsoft. Now, I became the creator:   
   CYQ.Data+Aries+Taurus can adapt to almost all business scenarios.   
   Already without ASP.NET WebForm, ASP.NET MVC.   
   However, it still remains inseparable from the ASP.NET platform.   
   As mentioned above:   
   1: ASP.NET Aries is suitable for rapid development of business systems and backgrounds.   
   2: Taurus.MVC is suitable for front-end systems and WebAPIs such as e-commerce with high performance requirements.   
   About the advantages of the framework:   
   Usually speaking, the advantage of the framework is that when you start to blow B, as long as the market slogan is loud, the product is not a problem as long as it is not weak.   
   What are the advantages of the framework?   Ordinary people ask this first, you want to blow my heart, blow my heart, only to return to you, and then silently download the source code to save the hard drive.   
   Because the market is basically a unified Microsoft world, so it is more to find Microsoft's MVC.   
   In fact, compared with .NET MVC, you can only say: one heaven, one underground.   
   MVC4 installed: 800M (do not figure out what is to be installed so much);   
   Taurus.MVC installed: 400K (Taurus.Core.dll + CYQ.Data).   
   Obviously: Microsoft has been doing additions for the past few years, did not want to do subtraction, has been doing innovation, did not want to be compatible, many products are big and big, people are reluctant.   
   Far away, talk about the advantages, let me think about it, let me think about it with silence...   
   Use a few words that are overused: lightweight?   high performance?   high efficiency?   
    No, it&rsquo;s different, a little bit of what others don&rsquo;t do is called an advantage:    
    Oh, yes, you have to use a graph to show that you can be professional, yes, this way, that way, good, finished, above:    
     
   Taurus.MVC Source code:   
   1: Source code SVN:      https://github.com/cyq1162/Taurus.MVC    
   2: Demo demo station:      http://taurus.cyqdata.com    
   The Demo screenshot is like this (the new version now has a WebAPI Demo):   
   
   Taurus.MVC framework introduction method:   
   1: Search on Nuget: Taurus.MVC, reference (will be introduced: Taurus.Core and CYQ.Data)   
   Then come out a Readme.txt, follow the prompts to configure the URL interception and specify the dll of the Controller place.   
    .NET Core version search: Taurus.MVC.Core    
   2: Directly use the source project (there will be Demo in the source project).   
   .NET version running: Taurus.MVC.sln   
   .NET Core version running: Taurus.MVC_Core_VS2017.sln   
   Introduction to the Taurus.MVC framework:   
   1: After downloading the source code: Solution diagram:   
   
   2: Solution Description:   
   1: CYQ.Data: The main XHtmlAction is the template engine, additionally when the data layer can provide a Model or provide automatic binding syntax.   
   2: Taurus.Core: Mainly implements core methods such as route rewriting, Controller calling, and ViewEngine.   
   3: Taurus.Controllers method entry, where to write the code.   
   4: Taurus.View only stores html and css and js   
   3: Supplementary note:   
   1: Usually MVC Controller, Modle, View files are placed in a project, here split into two projects.   
   2: In order to clear the project level, you can build Model project (put entity) and Logic project (write business logic code) and Utility (put tool class).   
   3: The Demo provided by the framework is fully loaded into the Controllers project.   
    In the following, according to the MVC routine, simply explain the basic principles and usage:    
   1: Route of Taurus.MVC:   
   1: Hidden route:   
   In .NET MVC, routing is a very important but cumbersome feature.   
   The first step in simplifying MVC is to think about how to implicitly eliminate routing.   
   Finally, the internal default has 3 routes:   
   0:{Action}/{Para}   
   1:{Controller}/{Action}/{Para}   
   2: {Module}/{Controller}/{Action}/{Para}   
   The default is 1.   
   2: Extended routing:   
   When deployed as a sub-application, or when the first one is a username, an additional prefix directory is created.   
   At this time, it is possible to configure the RouteMode value to 2 by AppSetting, which is easy and excessive.   
   The context provides three parameters for you to get information: ControllerType, Action, Para.   
     Ok, the routing is finished, want to customize the route?   Do some innovation on Para~~~~     
   2: Taurus.Controllers   
   1: Looking for the Controller:   
   The rules have been fixed, and the rest is to find the Controller according to the rules.   
   1: Collect all the Controllers.   
   2: Specify where to collect: The default is to go to Taurus.Controllers to find inheritance from the base class: Taurus.Core.Controller.   
   3: Customize the Controllers: AppSetting to configure the value of Taurus.Controllers, assuming: Taurus.View   
   4: When you can't find the Controller, you can find the DefaultController. If this is all there is (there is some in Demo), it will throw an exception.   
   
   2: Call the Controller's Action:   
   1: The method names are all public void, which can have parameters (overloading multiple parameters, only the first one is collected by default).   
   2: If there is input, use the Write method.   
   3: When the Action is not found, the Default method will be found (this base class is there, so there must be, and it will be rewritten if necessary).   
   
   3: Taurus.View   
   1: Template: html (strictly speaking, it should be xhtml)   
   2: Template loading method: The addressing path corresponding to the URL: Views/{Controller}/{Action}.html, which can change the agreed path through configuration.   
   3: Reference method of master page: itemref="page.node name".   (      itemref is the attribute of a div. If no one uses it, it will be used to reference node replacement      .)   
   4: Load replacement syntax:   
   A: For the input tag, you can use CYQ.Data.MDataRow.SetToAll to assign values ​​in bulk.   
   B: For ${name}, you can use View.LoadData (data, "prefix"), which will be formatted automatically.   
   C: For list loop tags: you can bind using the CYQ.Data.MDataTable.Bind method.   
   
   to sum up:   
   1: This article does not explain the usage method in detail. For the usage, it will be introduced in the next article:   
   Well, an introduction is enough, because there is nothing to say, you don't need to write a book.   
   2: Demo provides the function of adding, deleting, and revising list paging. If the ability is good or has MVC basics, the source code will be used.   
   3: Today's focus is on open source.   .   .   Open source.   .   .   Open source.   .   .   The important thing is to say 123.   
   Finally say:   
   The open source of this framework gives the people of .NET a choice.   



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)