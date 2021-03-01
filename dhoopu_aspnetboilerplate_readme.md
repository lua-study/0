# ASP.NET Boilerplate

[![Build Status](http://ci.volosoft.com:5480/job/aspnet-boilerplate-nightly/badge/icon)](http://ci.volosoft.com:5480/blue/organizations/jenkins/aspnet-boilerplate-nightly/activity)
[![NuGet](https://img.shields.io/nuget/v/Abp.svg?style=flat-square)](https://www.nuget.org/packages/Abp)
[![NuGet Download](https://img.shields.io/nuget/dt/Abp.svg?style=flat-square)](https://www.nuget.org/packages/Abp)
[![MyGet (with prereleases)](https://img.shields.io/myget/abp-nightly/vpre/Abp.svg?style=flat-square)](https://aspnetboilerplate.com/Pages/Documents/Nightly-Builds)
## What is ABP?

ASP.NET Boilerplate is a general purpose **application framework** specially designed for new modern web applications. It uses already **familiar tools** and implements **best practices** around them to provide you a **SOLID development experience**.

ASP.NET Boilerplate works with the latest **ASP.NET Core** & **EF Core** but also supports ASP.NET MVC 5.x & EF 6.x as well.

###### Modular Design

Designed to be  **modular**  and **extensible**, ABP provides the infrastructure to build your own modules, too.

###### Multi-Tenancy

**SaaS** applications made easy! Integrated  multi-tenancy  from database to UI.

###### Well-Documented

Comprehensive  **documentation**  and quick start tutorials.

## How It Works

Don't Repeat Yourself! ASP.NET Boilerplate automates common software development tasks by convention. You focus on your business code!

![ASP.NET Boilerplate](doc/img/abp-concerns.png)

See the  Introduction  document for more details.

## Layered Architecture

ABP provides a layered architectural model based on **Domain Driven Design** and provides a **SOLID** model for your application.

![NLayer Architecture](doc/img/abp-nlayer-architecture.png)

See the  NLayer Architecture  document for more details.

## Nuget Packages

ASP.NET Boilerplate is distributed as NuGet packages.

|Package|Status|
|:------|:-----:|
|Abp|[![NuGet version](https://badge.fury.io/nu/Abp.svg)](https://badge.fury.io/nu/Abp)|
|Abp.AspNetCore|[![NuGet version](https://badge.fury.io/nu/Abp.AspNetCore.svg)](https://badge.fury.io/nu/Abp.AspNetCore)|
|Abp.Web.Common|[![NuGet version](https://badge.fury.io/nu/Abp.Web.Common.svg)](https://badge.fury.io/nu/Abp.Web.Common)|
|Abp.Web|[![NuGet version](https://badge.fury.io/nu/Abp.Web.svg)](https://badge.fury.io/nu/Abp.Web)|
|Abp.Web.Mvc|[![NuGet version](https://badge.fury.io/nu/Abp.Web.Mvc.svg)](https://badge.fury.io/nu/Abp.Web.Mvc)|
|Abp.Web.Api|[![NuGet version](https://badge.fury.io/nu/Abp.Web.Api.svg)](https://badge.fury.io/nu/Abp.Web.Api)|
|Abp.Web.Api.OData|[![NuGet version](https://badge.fury.io/nu/Abp.eb.Api.OData.svg)](https://badge.fury.io/nu/Abp.Web.Api.OData)|
|Abp.Web.Resources|[![NuGet version](https://badge.fury.io/nu/Abp.Web.Resources.svg)](https://badge.fury.io/nu/Abp.Web.Resources)|
|Abp.Web.SignalR|[![NuGet version](https://badge.fury.io/nu/Abp.Web.SignalR.svg)](https://badge.fury.io/nu/Abp.Web.SignalR)|
|Abp.Owin|[![NuGet version](https://badge.fury.io/nu/Abp.Owin.svg)](https://badge.fury.io/nu/Abp.Owin)|
|Abp.EntityFramework.Common|[![NuGet version](https://badge.fury.io/nu/Abp.EntityFramework.Common.svg)](https://badge.fury.io/nu/Abp.EntityFramework.Common)|
|Abp.EntityFramework|[![NuGet version](https://badge.fury.io/nu/Abp.EntityFramework.svg)](https://badge.fury.io/nu/Abp.EntityFramework)|
|Abp.EntityFramework.GraphDiff|[![NuGet version](https://badge.fury.io/nu/Abp.EntityFramework.GraphDiff.svg)](https://badge.fury.io/nu/Abp.EntityFramework.GraphDiff)|
|Abp.EntityFrameworkCore|[![NuGet version](https://badge.fury.io/nu/Abp.EntityFrameworkCore.svg)](https://badge.fury.io/nu/Abp.EntityFrameworkCore)|
|Abp.NHibernate|[![NuGet version](https://badge.fury.io/nu/Abp.NHibernate.svg)](https://badge.fury.io/nu/Abp.NHibernate)|
|Abp.Dapper|[![NuGet version](https://badge.fury.io/nu/Abp.Dapper.svg)](https://badge.fury.io/nu/Abp.Dapper)|
|Abp.FluentMigrator|[![NuGet version](https://badge.fury.io/nu/Abp.FluentMigrator.svg)](https://badge.fury.io/nu/Abp.FluentMigrator)|
|Abp.AspNetCore|[![NuGet version](https://badge.fury.io/nu/Abp.AspNetCore.svg)](https://badge.fury.io/nu/Abp.AspNetCore)|
|Abp.AspNetCore.SignalR|[![NuGet version](https://badge.fury.io/nu/Abp.AspNetCore.SignalR.svg)](https://badge.fury.io/nu/Abp.AspNetCore.SignalR)|
|Abp.AutoMapper|[![NuGet version](https://badge.fury.io/nu/Abp.AutoMapper.svg)](https://badge.fury.io/nu/Abp.AutoMapper)|
|Abp.HangFire|[![NuGet version](https://badge.fury.io/nu/Abp.HangFire.svg)](https://badge.fury.io/nu/Abp.HangFire)|
|Abp.HangFire.AspNetCore|[![NuGet version](https://badge.fury.io/nu/Abp.HangFire.AspNetCore.svg)](https://badge.fury.io/nu/Abp.HangFire.AspNetCore)|
|Abp.Castle.Log4Net|[![NuGet version](https://badge.fury.io/nu/Abp.Castle.Log4Net.svg)](https://badge.fury.io/nu/Abp.Castle.Log4Net)|
|Abp.RedisCache|[![NuGet version](https://badge.fury.io/nu/Abp.RedisCache.svg)](https://badge.fury.io/nu/Abp.RedisCache)|
|Abp.RedisCache.ProtoBuf|[![NuGet version](https://badge.fury.io/nu/Abp.RedisCache.ProtoBuf.svg)](https://badge.fury.io/nu/Abp.RedisCache.ProtoBuf)|
|Abp.MailKit|[![NuGet version](https://badge.fury.io/nu/Abp.MailKit.svg)](https://badge.fury.io/nu/Abp.MailKit)|
|Abp.Quartz|[![NuGet version](https://badge.fury.io/nu/Abp.Quartz.svg)](https://badge.fury.io/nu/Abp.Quartz)|
|Abp.TestBase|[![NuGet version](https://badge.fury.io/nu/Abp.TestBase.svg)](https://badge.fury.io/nu/Abp.TestBase)|
|Abp.AspNetCore.TestBase|[![NuGet version](https://badge.fury.io/nu/Abp.AspNetCore.TestBase.svg)](https://badge.fury.io/nu/Abp.AspNetCore.TestBase)|

# Module Zero

## What is 'Module Zero'?

This is an  ASP.NET Boilerplate  module integrated with Microsoft  ASP.NET Identity .

Implements abstract concepts of ASP.NET Boilerplate framework:

*  Setting store 
*  Audit log store 
*  Background job store 
*  Feature store 
*  Notification store 
*  Permission checker 

Also adds common enterprise application features:

* ** User ,  Role  and  Permission ** management for applications that require authentication and authorization.
* ** Tenant  and  Edition ** management for SaaS applications.
* ** Organization Units ** management.
* ** Language and localization  text** management.
* ** Identity Server 4 ** integration.

Module Zero packages define entities and implement base domain logic for these concepts.

## NuGet Packages

### ASP.NET Core Identity Packages

Packages integrated into  ASP.NET Core Identity  and  Identity Server 4  (supports .NET Standard).

|Package|Status|
|:------|:-----:|
|Abp.ZeroCore|[![NuGet version](https://badge.fury.io/nu/Abp.ZeroCore.svg)](https://badge.fury.io/nu/Abp.ZeroCore)|
|Abp.ZeroCore.EntityFrameworkCore|[![NuGet version](https://badge.fury.io/nu/Abp.ZeroCore.EntityFrameworkCore.svg)](https://badge.fury.io/nu/Abp.ZeroCore.EntityFrameworkCore)|
|Abp.ZeroCore.IdentityServer4|[![NuGet version](https://badge.fury.io/nu/Abp.ZeroCore.IdentityServer4.svg)](https://badge.fury.io/nu/Abp.ZeroCore.IdentityServer4)|
|Abp.ZeroCore.IdentityServer4.EntityFrameworkCore|[![NuGet version](https://badge.fury.io/nu/Abp.ZeroCore.IdentityServer4.EntityFrameworkCore.svg)](https://badge.fury.io/nu/Abp.ZeroCore.IdentityServer4.EntityFrameworkCore)|

### ASP.NET Identity Packages

Packages integrated into  ASP.NET Identity  2.x.

|Package|Status|
|:------|:-----:|
|Abp.Zero|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.svg)](https://badge.fury.io/nu/Abp.Zero)|
|Abp.Zero.Owin|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.Owin.svg)](https://badge.fury.io/nu/Abp.Zero.Owin)|
|Abp.Zero.AspNetCore|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.AspNetCore.svg)](https://badge.fury.io/nu/Abp.Zero.AspNetCore)|
|Abp.Zero.EntityFramework|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.EntityFramework.svg)](https://badge.fury.io/nu/Abp.Zero.EntityFramework)|

### Shared Packages

Shared packages between the Abp.ZeroCore.\* and Abp.Zero.\* packages.

|Package|Status|
|:------|:-----:|
|Abp.Zero.Common|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.Common.svg)](https://badge.fury.io/nu/Abp.Zero.Common)|
|Abp.Zero.Ldap|[![NuGet version](https://badge.fury.io/nu/Abp.Zero.Ldap.svg)](https://badge.fury.io/nu/Abp.Zero.Ldap)|

## Startup Templates

You can create your project from startup templates to easily start with Module Zero:

*  ASP.NET Core & Angular  based startup project.
*  ASP.NET Core MVC & jQuery  based startup project.
*  ASP.NET Core MVC 5.x / AngularJS  based startup project.
 
A screenshot of the ASP.NET Core based startup template:

![](doc/img/module-zero-core-template.png)

### Docker Image

You can directly run the startup template on your computer as a docker container:

````
docker run -p 9902:80 volosoft/abp-template
````

See https://hub.docker.com/r/volosoft/abp-template/ for more info.

## Links

* Web site & Documentation: https://aspnetboilerplate.com
* Questions & Answers: https://stackoverflow.com/questions/tagged/aspnetboilerplate?sort=newest

## License

[MIT](LICENSE).


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)