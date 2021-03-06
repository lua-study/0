## 介绍
dogboot是一款用于nodejs的web框架，使用TypeScript编写，支持最新的js/ts语法。在设计理念上，我们致敬了著名的Java框架Spring Boot，装饰器、依赖注入等等，都是web开发中最流行的技术。
## 技术要点
- 支持且仅支持TypeScript
- 基于koa2
- async/await
- 装饰器
- 依赖注入
- 约定优于配置
## 从0开始
新建项目并且安装dogboot
```bash
mkdir dogboot-demo
cd dogboot-demo
npm init -y
npm i dogboot
npm i typescript -D
```
接下来，根据约定优于配置的理念，创建一些目录以及文件，最终，你的目录结构大概如下
```
├──src
|  ├── controller
|  |   └── HomeController.ts
|  └── App.ts
├──package-lock.json
├──package.json
└──tsconfig.json
```
package.json是npm的包管理清单文件。现在，请打开这个文件，大概里面的内容会是这个样子
```json
{
  "name": "dogboot-demo",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dogboot": "^1.1.5"
  },
  "devDependencies": {
    "typescript": "^3.3.4000"
  }
}
```
将scripts节替换为
```
"scripts": {
  "tsc": "tsc",
  "start": "node dist/App.js"
}
```
tsconfig.json是TypeScript项目的可选配置文件，对于dogboot我们建议填入以下内容，
```json
{
  "compilerOptions": {
    "module": "commonjs",
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "target": "esnext",
    "lib": ["es2017"],
    "outDir": "dist"
  },
  "include": ["src"]
}
```
如果想要深入了解tsconfig.json，请移步[TypeScript官网关于tsconfig的讲解](http://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

是时候写（复制/粘贴）点代码了

打开App.ts，输入以下内容
```typescript
import path = require('path');
import { DogBootApplication } from "dogboot";

let appRoot = path.resolve(__dirname, '..')
new DogBootApplication(appRoot).run()
```
打开HomeController.ts，输入以下内容
```typescript
import { Controller, GetMapping, BindQuery } from "dogboot";

@Controller('/home')
export class HomeController {
    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        return `Hello ${name}`
    }
}
```
现在，最小可运行项目已经准备好，是时候检查一下成果了，依次执行以下命令完成编译以及启动程序
```bash
npm run tsc
npm start
```
你会在控制台看到你的一行日志打印
```
Your application has started at 3000 in xxxms
```
然后，请在浏览器打开[http://localhost:3000/home/index?name=World](http://localhost:3000/home/index?name=World)

你将看到
```
Hello World
```
这就是一个最小可运行的dogboot程序，怎么样，简单吧🙃

当然你肯定不会满足于这个Hello World例子，那就请继续阅读我们的进阶文档吧

## DogBootApplication
一个dogboot程序始于DogBootApplication类，只需要提供一个appRootPath参数就可以了。执行run方法的时候，dogboot会扫描appRootPath目录下的以下文件夹。

dist/controller：此目录包含所有的控制器文件，关于controller的更多介绍，请参考[@Controller](#Controller)

dist/startup：此目录包含所有的预启动组件，关于startup的更多介绍，请参考[@StartUp](#StartUp)

程序会自动判断当前的运行环境，如果是直接运行ts文件，会扫描src目录，如果是运行编译后的js文件，会扫描dist目录。

⚠️所以实际上，我们指定了编译后的文件存放的目录为dist，不能修改。
## @Controller
使用@Controller装饰器标记一个类为控制器，并且传入一个可选的path参数，用于指定路由前缀。按照约定，控制器文件名应该以Controller结尾，但这不是必须的。path参数是可选的，如果不传，dogboot会指定这个类名的前面一部分并且转为小写作为路由前缀。比如：HomeController的默认路由前缀是/home。
## @StartUp
使用@StartUp装饰器标记一个类为预启动组件，并且传入一个可选的order参数。dogboot程序在正式接受用户的请求之前会先执行预启动组件的启动方法，使用order参数定制你希望的启动顺序。
一个常规的预启动组件使用方式如下
```typescript
import { StartUp, Init } from "dogboot";

@StartUp()
export class StartUp1 {
    index: number;

    @Init
    private init() {
        this.index = 0;
    }

    doSth() {
        return this.index++
    }
}
```
在其他地方被调用
```typescript
import { Controller, GetMapping, BindQuery } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";

@Controller('/home')
export class HomeController {
    constructor(private readonly startUp1: StartUp1) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth();
        return `Hello ${name} ${index}`
    }
}
```
执行之前的启动命令
```
npm run tsc
npm start
```
再次在浏览器打开[http://localhost:3000/home/index?name=World](http://localhost:3000/home/index?name=World)

你会看到
```
Hello World 0
```
刷新页面，你会看到
```
Hello World 1
```
我们的预启动组件生效了，它通过构造器被注入到HomeController，并且保持了一个index变量，每次执行doSth方法，index会加1
## @Config
使用@Config标记一个类为配置文件映射器，并且传入一个可选的field参数。使用配置文件映射器，而不是require('config.json')，前者得到的对象具有类型声明，更便于使用。

field参数表示映射器映射的配置节，如果不传，表示整个配置文件，使用a.b.c映射a节下的b节下的c。

⚠️所以，不要在你的配置文件中使用任何类似于a.b表示一个节，这会使配置映射器出错。

⚠️哦，别忘记，我们也限定了你的配置文件名必须叫config.json，并且位于程序根目录，就是那个package.json同级的目录。

一个常规的配置文件映射器使用方式如下

1、在项目根目录下新建一个config.json文件，输入
```json
{
    "mysql": {
        "host": "127.0.0.1",
        "port": 3306,
        "user": "root",
        "password": "524163",
        "db": "test1"
    }
}
```
2、在src目录下新建文件MyConfig.ts
```typescript
import { Config, Typed } from "dogboot";

@Config('mysql')
export class MyConfig {
    @Typed()
    host: string

    @Typed()
    port: number

    @Typed()
    user: string

    @Typed()
    password: string

    @Typed()
    db: string
}
```
3、在其他地方被调用
```typescript
import { Controller, GetMapping, BindQuery } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";

@Controller('/home')
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth();
        return `Hello ${name} ${index} ${this.myConfig.host}`
    }
}
```
重复之前的编译以及启动操作，然后在浏览器打开[http://localhost:3000/home/index?name=World](http://localhost:3000/home/index?name=World)

你会看到
```
Hello World 0 127.0.0.1
```
我们的配置文件映射器生效了，MyConfig类映射了config.json，你在使用MyConfig的时候，所有的字段都是有类型声明的，并且已经转换为你希望的类型，这得益于我们使用了[@Typed](#Typed),dogboot会帮我们自动处理被@Typed标记的字段的类型。

如果这个config.json写法如下
```json
{
    "mysql": {
        "host": "127.0.0.1",
        "port": "3306",
        "user": "root",
        "password": "524163",
        "db": "test1"
    }
}
```
然后在HomeController里面测试typeof myConfig.port，会发现得到number而不是string
## @Component
使用@Component标记一个类为可注入组件，同时也表示此组件的生命周期完全交给dogboot内置的依赖注入管理器管理。一个常规的Component使用方式如下

1、创建一个组件
```typescript
import { Component, Init } from "dogboot";

@Component
export class HomeService {
    @Init
    doInit() { }

    getSth() {
        return 1
    }
}
```
2、在其他地方被调用
```typescript
import { Controller, GetMapping, BindQuery } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";
import { HomeService } from "../service/HomeService";

@Controller('/home')
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig, private readonly homeService: HomeService) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth();
        return `Hello ${name} ${index} ${this.myConfig.host} ${this.homeService.getSth()}`
    }
}
```
几乎与StartUp一样，区别只是使用了@Component来标记类。

事实上，Controller、StartUp、Config本质上也是Component。
## @Init
在组件中，使用@Init标记一个方法，此方法用于初始化组件，支持异步方法。

## @Autowired
用于属性注入，用法如下
```typescript
@Controller()
export class HomeController{
  @Autowired(UserService)
  userService: UserService

  GetMapping()
  index(){
    return this.userService.doSomething()
  }
}
```
前面的例子我们都是使用构造器注入，如果你喜欢，你也可以使用属性注入。

大部分情况下，两者功能一致，唯一的不同是：Autowired可以实现循环依赖。虽然应该尽量避免出现循环依赖，但是我们也为那些特殊情况做了考虑。

假如UserService依赖ItemService，同时ItemService又依赖UserService，你可以使用一种“稍微难懂”的写法来实现循环依赖。用法如下

UserService.ts
```typescript
@Component
export class UserService {

    constructor() {
        console.log('UserService', Math.random())
    }

    @Autowired(() => ItemService)
    itemService: ItemService
    index() {
        console.log('UserService')
    }
}
```
ItemService.ts
```typescript
@Component
export class ItemService {

    constructor() {
        console.log('ItemService', Math.random())
    }

    @Autowired(() => UserService)
    userService: UserService;
    index() {
        console.log('ItemService')
    }
}
```
仔细看，使用了@Autowired(() => UserService)而不是@Autowired(UserService)

使用@Autowired(UserService)会出现在ItemService中解析UserService时UserService为空或者在UserService中解析ItemService时ItemService的情况，这取决于两者的加载顺序。

## @Mapping
用于将Controller内的方法映射为Action，需要传入method以及path参数。这两个参数不是必须的，默认会映射为get方法，并且使用方法名作为路由，为了方便书写，我们提前准备好了几种常用的method对应的Mapping。分别是@GetMapping、@PostMapping、@PutMapping、@PatchMapping、@DeleteMapping、@HeadMapping。如果你要映射所有的method，可以使用AllMapping。
## @BindContext
用于获取请求上下文信息使用方式如下
```typescript
@Controller()
export class HomeController{
  GetMapping()
  index(@BindContext ctx:any){
    console.log(ctx.query.name)
    return 'ok'
  }
}
```
这个上下文信息完全是koa提供的请求上下文，所以你可以从[koa官网](https://koajs.com/)找到关于请求上下文的详细介绍，所以如果你需要一些类型检查以及智能提示，你可以安装koa的typing库
```bash
npm i @types/koa -D
```
然后你的HomeController可以写成
```typescript
@Controller()
export class HomeController{
  GetMapping()
  index(@BindContext ctx:koa.Context){
    console.log(ctx.query.name)
    return 'ok'
  }
}
```
类似的获取koa原生请求对象的装饰器还有：@BindRequest、@BindResponse。
## @BindQuery
使用@BindQuery获取url中查询参数，dogboot将会自动转换参数类型为期望的类型。在我们的从0开始中已经介绍过这个用法，就不重复介绍了。类似的装饰器还有：

@BindPath 用于获取path参数

@BindBody 用于获取请求体对象

⚠️注意：@BindContext、@BindRequest、@BindResponse、@BindQuery、@BindPath、@BindBody只能用于Controller
## @Typed
表示此字段需要转换为指定类型
## @TypedArray
如果需要转换的字段是一个数组，@Typed就无法胜任了，因为ts的Array是一个泛型，且程序运行时无法知道泛型确切类型，所以转换数组时还需要指定确切类型
## @NotNull
对于请求参数，你可能需要做一些通用的验证，避免冗余代码，此装饰器用于指定此字段不可为空。

举个例子
```typescript
import { Typed, NotNull } from "dogboot";

export class IndexIM {
    @Typed()
    pageSize: number

    @Typed()
    pageIndex: number

    @Typed()
    @NotNull()
    status: number
}
```
类似的装饰器还有：@NotEmpty、@NotBlank、@Length、@MinLength、@MaxLength、@Range、@Min、@Max、@Decimal、@MinDecimal、@MaxDecimal、@Reg、你也可以使用更加灵活的@Func，支持传入自定义的验证方法。除了这些已经预先定义的验证装饰器，你还可以封装自己的验证装饰器，参考dogboot中@NotNull的源码
```typescript
/**
 * a != null
 * @param errorMesage 
 */
export function NotNull(errorMesage: string = null) {
    errorMesage = errorMesage || '字段不能为空'
    return Func(a => {
        if (a != null) {
            return [true]
        }
        return [false, errorMesage]
    })
}
```
实现一个你自己的验证器
```typescript
import { Func } from "dogboot";

export function MyValidator(errorMesage: string = null) {
    errorMesage = errorMesage || '自定义验证不通过'
    return Func(a => {
        if (a == null) {
            return [true]
        }
        if (a.includes('1')) {
            return [true]
        }
        return [false, errorMesage]
    })
}
```
使用

1、新建一个数据传输类，内容如下
```typescript
import { Typed } from "dogboot";
import { MyValidator } from "../../common/validator/MyValidator";

export class UpdateNameIM {
    @Typed()
    @MyValidator()
    name: string
}
```
2、修改我们的控制器为
```typescript
import { Controller, GetMapping, BindQuery, PostMapping, BindBody } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";
import { HomeService } from "../service/HomeService";
import { UpdateNameIM } from "../model/home/UpdateNameIM";

@Controller('/home')
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig, private readonly homeService: HomeService) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth();
        return `Hello ${name} ${index} ${this.myConfig.host} ${this.homeService.getSth()}`
    }

    @PostMapping('/updateName')
    async updateName(@BindBody im: UpdateNameIM) {
        return im
    }
}
```
我们加上了一个名字为updateName的action，并且映射为post方法，我们可以在postman测试这个接口

post参数为
```json
{
	"name":"2"
}
```
那么我们会看到我们程序的控制台有错误打印，类似于
```
  Error: 自定义验证不通过
      at C:\Users\zhang\Desktop\dogboot-demo\node_modules\dogboot\dist\lib\DogBoot.js:589:23
      at Generator.next ( )
      at fulfilled (C:\Users\zhang\Desktop\dogboot-demo\node_modules\dogboot\dist\lib\DogBoot.js:13:58)
      at process._tickCallback (internal/process/next_tick.js:68:7)
```
postman测试工具收到的回复是
```
Internal Server Error
```
当然，正常的程序不应该这样任由错误出现而不处理，我们会在稍后介绍如何优雅的进行错误处理。
## @UseExceptionFilter
使用@UseExceptionFilter标记一个Controller或者Action使用指定的异常过滤器。

在ExceptionFilter组件中添加@ExceptionHandler标记到方法上，用于处理指定的异常。

用法如下

1、创建一个ExceptionFilter组件，内容如下
```typescript
import { Component, ExceptionHandler } from "dogboot";

@Component
export class MyExceptionFilter {
    @ExceptionHandler(Error)
    async handleError(error: Error, ctx: any) {
        error.stack && console.log(error.stack)
        ctx.body = { success: false, message: error.message }
    }
}
```
2、在HomeController中使用
```typescript
import { Controller, GetMapping, BindQuery, PostMapping, BindBody, UseExceptionFilter } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";
import { HomeService } from "../service/HomeService";
import { UpdateNameIM } from "../model/home/UpdateNameIM";
import { MyExceptionFilter } from "../filter/MyExceptionFilter";

@Controller('/home')
//放在这里对此Controller下所有Action生效
@UseExceptionFilter(MyExceptionFilter)
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig, private readonly homeService: HomeService) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth()
        return `Hello ${name} ${index} ${this.myConfig.host} ${this.homeService.getSth()}`
    }

    @PostMapping('/updateName')
    async updateName(@BindBody im: UpdateNameIM) {
        return im
    }
}
```
也可用于Action
```typescript
import { Controller, GetMapping, BindQuery, PostMapping, BindBody, UseExceptionFilter } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";
import { HomeService } from "../service/HomeService";
import { UpdateNameIM } from "../model/home/UpdateNameIM";
import { MyExceptionFilter } from "../filter/MyExceptionFilter";

@Controller('/home')
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig, private readonly homeService: HomeService) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth()
        return `Hello ${name} ${index} ${this.myConfig.host} ${this.homeService.getSth()}`
    }

    //放在这里仅对此Action生效
    @UseExceptionFilter(MyExceptionFilter)
    @PostMapping('/updateName')
    async updateName(@BindBody im: UpdateNameIM) {
        return im
    }
}
```
现在，使用postman测试之前的例子，postmen接收到的返回是
```json
{
    "success": false,
    "message": "自定义验证不通过"
}
```
这样，就实现了一个异常过滤器

异常过滤器也可以通过DogBootApplication.useExceptionFilter(MyExceptionFilter)设置，这样的设置将会全局有效

对于每个Action，只会有一个ExceptionFilter生效，优先级为
```
ExceptionFilter on Action > ExceptionFilter on Controller > globalExceptionFilter
```
## @UseActionFilter
使用@UseActionFilter标记一个Controller或者Action使用指定的Action过滤器。

ActionFilter在权限处理时非常有用，设置了ActionFilter的Action在执行前后会执行ActionFilter内的@DoBefore、@DoAfter方法。

举个例子，我们要在每一个接口请求判断用户的身份信息，如果身份信息不存在或者不合法，就不允许继续执行Action。

1、创建一个ActionFilter，内容如下
```typescript
import { Component, DoBefore, ActionFilterContext } from "dogboot";

@Component
export class MyActionFilter {
    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        let ticket = actionFilterContext.ctx.get('ticket')
        //请求的header中的ticket不能为空，且需要包含admin
        if (!ticket || !ticket.includes('admin')) {
            actionFilterContext.ctx.throw(401)
        }
    }
}
```
2、使用
```typescript
import { Controller, GetMapping, BindQuery, PostMapping, BindBody, UseExceptionFilter, UseActionFilter } from "dogboot";
import { StartUp1 } from "../startup/StartUp1";
import { MyConfig } from "../MyConfig";
import { HomeService } from "../service/HomeService";
import { UpdateNameIM } from "../model/home/UpdateNameIM";
import { MyExceptionFilter } from "../filter/MyExceptionFilter";
import { MyActionFilter } from "../filter/MyActionFilter";

@Controller('/home')
//放在这里对此Controller下所有Action生效
@UseExceptionFilter(MyExceptionFilter)
@UseActionFilter(MyActionFilter)
export class HomeController {
    constructor(private readonly startUp1: StartUp1, private readonly myConfig: MyConfig, private readonly homeService: HomeService) { }

    @GetMapping('/index')
    async index(@BindQuery('name') name: string) {
        let index = this.startUp1.doSth()
        return `Hello ${name} ${index} ${this.myConfig.host} ${this.homeService.getSth()}`
    }

    @PostMapping('/updateName')
    async updateName(@BindBody im: UpdateNameIM) {
        return im
    }
}
```
现在，使用postman测试之前的例子，postmen接收到的返回是
```json
{
    "success": false,
    "message": "Unauthorized"
}
```
这样，就实现了一个ActionFilter，此例子仅用于介绍UseExceptionFilter用法，实际生产中不建议使用这样简单的处理。

与UseExceptionFilter一样，UseActionFilter也可用于Action，或者使用DogBootApplication.useActionFilter(MyActionFilter)全局添加。

对于每个Action，可以使用多个ActionFilter，多个ActionFilter的执行顺序使用以下例子说明
```typescript
new DogBootApplication(appRoot)
    .useActionFilter(ActionFilter0)
    .useActionFilter(ActionFilter1)
    .run()
```
```typescript
@Controller('/home')
@UseActionFilter(ActionFilter2)
@UseActionFilter(ActionFilter3)
export class HomeController {
    @GetMapping('/index')
    @UseActionFilter(ActionFilter4)
    @UseActionFilter(ActionFilter5)
    async index() {
        console.log('执行/home/index')
        return 'ok'
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter0 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore0', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter0', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter1 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore1', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter1', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter2 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore2', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter2', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter3 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore3', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter3', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter4 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore4', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter4', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
```typescript
import { ActionFilterContext, DoBefore, DoAfter, Component } from "../lib/DogBoot";

@Component
export class ActionFilter5 {

    @DoBefore
    doBefore(actionFilterContext: ActionFilterContext) {
        console.log('doBefore5', actionFilterContext.controller.name, actionFilterContext.action)
    }

    @DoAfter
    doAfter(actionFilterContext: ActionFilterContext) {
        console.log('doAfter5', actionFilterContext.controller.name, actionFilterContext.action)
    }
}
```
启动程序，在浏览器打开http://localhost:3000/home/index，可以在控制台看到的打印
```
doBefore0 HomeController index
doBefore1 HomeController index
doBefore2 HomeController index
doBefore3 HomeController index
doBefore4 HomeController index
doBefore5 HomeController index
doBefore5 HomeController index
执行/home/index
doAfter5 HomeController index
doAfter4 HomeController index
doAfter3 HomeController index
doAfter2 HomeController index
doAfter1 HomeController index
doAfter0 HomeController index
```
对于过滤器中的@DoBefore方法，先添加的先执行，全局 > ActionFilter On Controller > ActionFilter On Action

对于过滤器中的@DoAfter方法，先添加的后执行，全局 < ActionFilter On Controller < ActionFilter On Action

⚠️注意，不要在过滤器中保存请求上下文信息，因为dogboot所有的组件都是单例的。

另外，在这些过滤器中，可能会有一些请求上下文相关数据的流转，需要从Action带到Filter或者从Filter带到Action，或者Filter到Filter，可以把这些数据保存到ctx.state上，这也是koa官方的推荐方式。

比如，在ActionFilter中设置
```typescript
actionFilterContext.ctx.state.userName = 'dogzhang'
```
然后在HomeController中使用
```typescript
index(@BindContext ctx:any){
    let userName = ctx.userName
}
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)