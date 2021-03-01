# KJServlet - A Javascript web framework for Java

## Nashorn died

**For Nashorn is deprecated, and will be removed from JDK, this Project will not be maintained.**

## Intro

KJServlet is lightweight javascript web framework which allows you to write sever side code using Javascript. It is based on Nashorn which is a script engine introduced in Java 8. In other words unlike Node.js which runs in V8 engine,  this framework runs on JVM environment. Which means that you can use all kinds of Java libs to construct you own web applications. 

It is also a very free style framework, it allows you to write your Javascript in many ways. Take writing controller for example, you can use functions, or you can use method in a Javascript object; you can write the response in a callback function, or you can just return a JSON object and let the framework do the rendering. 

This document is a reference guide to KJServlet framework features. Because of this is a very new framework and written by one person (which is me), so there might be some bugs that I have not discovered. If you find some problems, or have any questions or suggestions, or you want to get involved in this project, please let me know, here is my email: keijack.wu@gmail.com 

 *About the license: we provide two kinds of license, GPL by default. But if you want to use this framework in your business and don't want to open the source of your own system, please contact for a Apache license.*  
 
## Getting Start
 
 As the project name shows, it is a servlet, so you can very easily embed it into any J2EE projects.  Follow these steps to run the demo:
 
1. Download the `kjservlet-[version].jar` and put it into your project, in the most time, the location is 
```
 [webapps]/WEB-INF/lib
 ```   
2.  If you are using maven, for the reason that this project have not put into the maven central repository (will do it latter), you have  to checkout this project and make it as your local maven modual, then add the following dependency to your `pom.xml`
```xml
	 
		 me.keijack.kjservlet 
		 kjservlet 
		 0.1.0 
	 
```
3. Add the servlet and servlet-mapping to your `web.xml`
```xml
	 
		 k-js-servlet 
		 KJServlet 
		 org.keijack.kjservlet.KJServlet 
	 
	 
		 KJServlet 
		 /* 
	 
```
4. Add a Javascript file `demo.js` into the classpath folder, which mostly is `[webcontent]/WEB-INF/classes`
5. Add a function to `demo.js` like: 
```javascript
function sayHello(req){
    var name=req.param["name"];
    return "    Say Hello   Hello, " + name + "  ";
}
``` 
6, Start up the server, and use you browser to visit `http://[your_server_host]:[your_server_port]/[your_servlet_context]/demo/sayHello?name=World`, then you will see the "Hello World" in the browser.

For more information, please read the User Guide.

## Route

As you can see, there are no route configurations in the demo, so how the framework actually find the route? Here, directories are used. 

Take the demo in the **Getting Start** for example, if you put the demo.js to a folder `path` in the class path (so that the real path of the demo.js will be `[webcontent]/WEB-INF/classes/path/demo.js`), then you will use `http://[your_server_host]:[your_server_port]/[your_servlet_context]/path/demo/sayHello?name=World` to visit the controller function. 

In fact, you do have some ways to configure the route. A `global.js` in the classpath root folder will be run when the runtime environment is being prepared. In this file, you can redefined a global variable $webapp, which will affect the routing. 
```javascript
$webapp = {
    controller : {
        fileHome : "classpath:/org/keijack/kjservlet/demo/controller", // Where your js files are, default is "classpath:"
        fileSuffix : ".js", // What suffix is your js file, default is ".js"
        suffix : "", // If your url have a suffix, like ".do", please set it here
    },
    resources : [ "*.html", "/images/*" ], // the url match these pattern will be treated as the static files
};
```  
If you want to get more information about this `global.js` file, please read the **The global.js file** chapter.

The last portion of the url is the controller function name, which is `sayHello` in the example above. In this example the function `sayHellow` in the `demo.js` will be called.

There is also another way to route to the controller function, we will talk about that later. 

KJServlet is function related design, it's OK for you to use global functions. In fact, every request will run in its own scope -- We will go deeper into that latter -- so it doesn't matter even you have duplicated function names in different controller files. But if you want to arrange your codes well by using spaces and objects, the framework supports that as well. 

In the example above, if you defined an object like the following in your `demo.js` file:
```javascript
var person = {
    yieldName : function(req) {
        var name = req.parameters.name;
        return "    Say Hello   My name is " + name + "!  ";
    }
};
```
Then you can use the following url to visit:
```
http://[your_server_host]:[your_server_port]/[your_servlet_context]/demo/person.yieldName?name=John
```
You can add alias to routes, at your $webapp object, add a property named `alias`. for example:
```javascript
$webapp = {
    controller : {
        fileHome : "classpath:/org/keijack/kjservlet/demo/controller", // Where your js files are, default is "classpath:"
        fileSuffix : ".js", // What suffix is your js file, default is ".js" 
        suffix : "", // If your url have a suffix, like ".do", please set it here
    },
    aliases : {
    	"/yieldMyName" : "/demo/person.yieldName",
    },
    resources : [ "*.html", "/images/*" ], // the url match these pattern will be treated as the static files
};
```
Then the following url can also visit the controller defined in the example above. 
```
http://[your_server_host]:[your_server_port]/[your_servlet_context]/yieldMyName?name=John
```

## Import Other Script Files
The last chapter shows you how to route a url to a function in a Javascript file. You won't just define one function as the controller in most cases. You will have to call other functions, but how could you call the function in other script files?

Nashorn provides a function load(path), but normally, we recommend you to use a function name imports(path) instead. 

There are several reasons that you should use imports():

* In one scope -- global.js runs on the global scope, and every request runs on its own scope --, no matter how many times you call the import function, it only import the same file once. It's more efficient when your scripts import some common function that you define in a common script file.
* It's much easier to handle location, it use the relative path rather than absolute path. *Notice! In controller script files and the files imported by them, the relative root is the fileHome you define in `$webapp`. While in global.js and the files it imports, `classpaht:` is the relative root.* 
* in imports function, the path can use `.` to separate path just like the package path in Java. Both `org.keijack.kjservlet.service` and `org/keijack/kjservlet/service` are accepted. *Notice! In controller script files and the files imported by them, the suffix is the one you define in `$webapp`. While in global.js and the files it imports, `.js` is only suffix that supported.*
 

## Writing Controllers  
 
### The Request and the Response arguments
Just like the normal servlet that you will write when you implements javax.servlet.Servlet Interface in Java code, the framework will give you two arguments to your controller function. You should get user data from the first argument the framework past to your controller function, which is known as the Request object, and write data back by using the second argument which is known as the Response object. Of course, we have another way provided by using return values to send back data, and you can completely ignore the response object just like we did in the **Getting Start** chapter, we will talk about that latter.

The very example of using request and response objects is like this:
```javascript
function dosth(req, res){
    var someParamVal = req.parameters["name-defined-in-form-input"]; // if your parameters name is simple enough, you can use "." also, like: req.parameters.simpleName
    var serviceResult = someServiceObject.doService(someParamVal);
    res.write(serviceResult);
    /*
    if the serviceResult is the Java byte array, instead, please use
    res.writeByte(serviceResult);
    */
}
```
If you prefer callback functions, you might write codes like:
```javascript
function dosth(req, res){
    var someParamVal = req.parameters["name-defined-in-form-input"]; // if your parameters name is simple enough, you can use "." also, like: req.parameters.simpleName
    someServiceObject.doService(someParamVal, function (serviceCallbackResult) {
        res.write(serviceCallbackResult);
    });
}
```

The completed fields and functions of the request and response objects are bellow. 

#### The Properties and Functions of the Request Object
* **req.oriRequest**, the original HttpServletRequest object comes from the servlet.  
* **req.session**, the HttpSession object comes from the original request's getSession() method.
* **req.authType**, the authType comes from the original request's getAuthType() method.
* **req.method**, the request method comes from the original request's getMethod() method.
* **req.contentLength**, the content length comes from the original request's getContentLength() method.
* **req.contentType**, the request content type, comes from the original request.getContentType() method.
* **req.queryString**, the query string, the string after the url's "?", comes from the original request's getQueryString() method.
* **req.protocol**, the protocol of this request, it would be "HTTP/1.1", comes from the original request's getProtocol() method;
* **req.schema**, the schema of this request, it would be "http" or "https", comes from the original request's getSchema() method;
* **req.serverName**, the server name, comes from the original request's getServerName() method.
* **req.serverPort**, the server port, comes from the original request's getServerPort() method.
* **req.contextPath**, the context path, if you put all the web content to the `$TOMCAT_HOME/webapps/ROOT/` for example, the context path is `/`, if the web content locates in `$TOMCAT_HOME/webapps/demo/`, the context path is `/demo/`;
* **req.requestURI**, the request uri, not includes the schema, server name, server port and query string  but inclues the context path. comes from the original request's getRequestURI() method.
* **req.requestUri**, an alias of `req.requestURI`.
* **req.ctxUri**, request uri without context path.
* **req.uri**, another alias of `req.requestURI`.
* **req.servletPath**, the servlet path comes from the original request's getServletPaht() method.
* **req.requestURL**, the string before the url's "?", comes from the original request's getRequestURL() method, already change it to a string using toString() method.
* **req.requestUrl**, an alias of `req.requestURL`.
* **req.url**, another alias of `req.requestURL`.
* **req.headers**, the request's headers, has been initialized by using the original request's getHeader(name) method. For example, You can use `req.headers["user-agent"]` to get the user agent.
* **req.header**, an alias of `req.headers`.
* **req.parameterValues**, the parameter values, including the values from the query string and the request body when content type is `application/x-www-form-urlencoded` and `multipart/form-data`. This property holds arrays, even only one value. If the values contains a file uploaded by user when the request's content type is `multipart/form-data`, the value will be an objeck like
```javascript
{
    "filename": "somePicture.jpg", // the file's name
    "contentType": "image/jpg", // the content type
    "content": "xxxxxx" // a string that get from the multipart content, 
                        // you can use getBytes() method to get the byte array, 
                        // and write it into a file.
}
```
* **req.parameterValue**, an alias of `req.parameterValues`.
* **req.paramVals**, another alias of `req.parameterValues`.
* **req.parameters**, similar whith `req.parameterValues`, but only have one value. If there are more than one value with the parameter name, the first one would be the value here.
* **req.parameter**, an alias of `req.parameters`.
* **req.params**, another alias of `req.parameters`.
* **req.param**, another alias of `req.parameters`.
* **req.pathValues**, the values comes from the url path itself, will discuss latter.
* **req.pathValue**, an alias of `req.pathValues`.
* **req.setAttribute(name, val)**, the wrap of the original request's setAttribute(name, value) method.
* **req.setAttr(name, val)**, an alias of `req.setAttribute(name, val)`;
* **req.getAttribute(name, defaultValue)**, the wrap of the original request's getAttribute(name) method, if there is no value then return the defaultValue that given.
* **req.getAttr(name, defaultValue)**, an alias of `req.getAttribute(name, defaultValue)`.
* **req.removeAttribute(name)**, the wrap of the original request's removeAttribute(name) method.
* **req.removeAttr(name)**, an alias of `req.removeAttribute(name)`.
* **req.rmAttr(name)**, another alias of `req.removeAttribute(name)`.
* **req.readRequestBody()**, return the request body string, if the content type is `application/x-www-form-urlencoded`, this method will return null.
* **req.data**, if the request content type is `application/json`, this property will be JSON.parse(req.readRequestBody).

#### The Properties and Functions of the Response Object
* **res.oriResponse**, the original HttpServletResponse object.
* **res.contentType**, the content type of this response, will set this value using original response's setContentType() method.
* **res.headers**, headers of this response, will use original response's addHeader(name, value) to add all these properties to the original response. 
* **res.header**, an alias of `res.headers`.
* **res.addHeader(name, value)**, the wrap of the original response's addHeader(name, value) method.
* **res.setHeader(name, value)**, the wrap of the original response's setHeader(name, value) method.
* **res.sendError(code, message)**, the wrap of the original response's sendError(code, message) method, it's OK that you ignore the message parameter by just using `res.sendError(code)`.
* **res.redirect(url)**, the wrap of the original response's sendRedirect(url) method.
* **res.write(data)**, write data to the response's output stream. Data could be a JSON object, in this case, the JSON.stringify(data) will be used before to change the JSON object to string. 
* **res.writeByte(bytes)**, only accept byte array as the only parameter, write data by using original response's getOutputStream().write(bytes); *About the Content-Length, the response object will calculate that automatically.*

### Another Way to Response
In this section, you can see how to ignore the response object, and use return value to send back data.

As you can see in the **Getting Start** chapter, you can completely ignore the response object, and return some values which will be written back to original response by the framework.

The value returned will be a structure JSON object, you don't need to know how the JSON like. Because a global object $renderer is provided, which will do the wrapping. 

The methods of the $renderer object is bellow:
* **$renderer.render(contentType, content, headers)**, render a customized content type response. However, if you pass null, "", false to the contentType parameter, the framework will try to guess what you content is. The content parameter should be a string; parameter headers is optional, it is a JSON object, all its values will use the original response's addHeader(name, value) method to add to the response.
* **$renderer.text(text, headers)**, render a text response, the content type will be "text/plain"; the headers is optional. 
* **$renderer.html(data, headers)**, render a html response, the content type will be "text/html"; the headers is optional. 
* **$renderer.json(data, headers)**, render a JSON response, the content type will be "application/json"; the data should be a JSON object, and the headers is optional.
* **$renderer.bytes(data, headers)**, data should be a Java byte array, and the headers is optional. The framework will use the original response's getOutputStream().write(data) to write the data back.
* **$renderer.redirect(url, headers)**, the framework will use the original response's sendRedirect(url) to send a redirect. Before that headers -- if you pass it to the method -- will be added to the response's headers. 
* **$renderer.forward(url, data, headers)**, the framework will use the original request.getRequestDispatcher(url).forward(request, response) to forward the request. The data parameter and the headers parameter are optional. When you pass this two parameters, the values in data object will be added to request using the original request's setAttribute(name, value) method, while headers will be added to the **response**'s header by using the original response's addAttribute(name, value) method.
* **$renderer.error(code, message)**, send back an error, message is optional.
* **$renderer.view(viewFileLocation, data, headers)**, using MVC design pattern, support JSP, Freemarker and Velocity, customized resolve function. will discuss this latter.

By using the $renderer object , your code style would probably like:
```javascript
function dosth(req){
	var param = req.parameters;
	var serviceResult = someServiceObject.doService(param);
	return $renderer.json(serviceResult);
}
```
You can even use even much simpler way to do this, like:
```javascript
function dosth(req){
	var param = req.parameters;
	var serviceResult = someServiceObject.doService(param);
	return serviceResult;
}
```
The framework will do the wrap for you. You can also return some string like:
```javascript
    return "  .... "; // will render as "text/html".
```
```javascript
    return "  ... "; // will render as "text/xml"
```
```javascript
    return "redirect:/url"; // will redirect to /url
```
```javascript
    return "forward:/url"; // will forward to /url
```
```javascript
    return "some text"; // will render as "text/plain" 
```

## MVC
MVC is a well know design pattern, whose main principle is to separate the business logic layer(Model), control layer(controller), and the presentation layer(View) to make codes much clearer and easier to read, maintain and extend.  
  
Web developers loves to use MVC patterns, especially Java web developers, so they have done so much work on building up all kinds of template engines. Thanks to this, we can very easily using MVC in our framework.
 
KJServlet support JSP, Freemarker and Velocity template engine. 

It's very easy to use the template, just like:
```javascript
function dosth(req){
    var param = req.parameters;
	var serviceResult = someServiceObject.doService(param);
	return $renderer.view("/WEB-INF/pages/view.jsp", serviceResult);
}
```
The template engine is JSP by default, if you want to change it, please set it up in $webapp in your `global.js` file.
```javascript
$webapp = {
    controller : {
        fileHome : "classpath:/org/keijack/kjservlet/demo/controller", // Where your js files are, default is "classpath:"
        fileSuffix : ".js", // What suffix is your js file, default is ".js" 
        suffix : "", 
    },
    resources : [ "*.html", "/images/*" ],
    view : {
        resolver : "jsp", // The resolver, "jsp" by default, you can change it to "freemarker" or "velocity"
        prefix : "/WEB-INF/pages/", // the prefix of the view
        suffix : ".jsp", // the suffix of theview
    }, 
}
```
With the configuration above, you controller will be:
```javascript
function dosth(req){
    var param = req.parameters;
	var serviceResult = someServiceObject.doService(param);
	return $renderer.view("view", serviceResult); // and the template file will be /WEB-INF/pages/view.jsp 
}
```
*Notice! When you change the resolver to `freemarker` or `velocity`, you must import the relative jars to your project. If you use freemarker resolver, and using maven to build your webapp, the following dependency mush be added to your `pom.xml`*
```xml
     
         org.freemarker 
         freemarker 
         2.3.26-incubating 
     
```
The second parameter which names data of the **$renderer.view(templateFileLocation, data, header)** should be a JSON object, the framework will convert this into a Java Map, so when you are writing the template file, just use it as a Map. 

For Example, if you data object is:
```javascript
function dosth(req){
    var data = {"userName": "Jhon",
                "sex": "male",
                "age": 28,
                "department": { "name": "HR",
                                "phone": "+01xxxxxx",
                },
                "subordinates": ["Mike", "Lily"]
    };
    return $renderer.view("view", data);
}
```
So in your template file -- take freemarker for example -- would probably like:
```html
 
 
 
     Personal Details 
 
 
     Personal Details of ${userName} 
     sex: ${sex} 
     age: ${age} 
     department: ${department.name} 
     subordinates:  ${sbn},  
 
 
``` 
Functions are also allowed in the data object, please use method `call` or `apply` to use functions.

*Notice: `call` method accepts at most 10 arguments. And `apply` method accepts an array as the only argument.*  

Assume that your data object 
```javascript
    var data = {"userName": "Jhon",
                "sex": "male",
                "isAdult": function(){
                	// Notice: please don't use `this` here, for the function will be wrapped into a Java Object called JSFunctionWrapper. 
                	return data.age >= 18;
                },
                "age": 28,
                "department": { "name": "HR",
                                "phone": "+01xxxxxx",
                },
                "subordinates": ["Mike", "Lily"]
    };
```

*Notice: please don't use `this` in this kind of functions, for they will be wrapped into a Java Object `JSFunctionWrapper` which `this` will point to.*

Then in your template file,
```html
 
 
 
     Personal Details 
 
 
     Personal Details of ${userName} 
     sex: ${sex} 
     is adult: ${isAult.call()} 
     age: ${age} 
     department: ${department.name} 
     subordinates:  ${sbn},  
 
 
```  
 
You can even customized your own resolver:
```javascript
$webapp = {
    controller : {
        fileHome : "classpath:/org/keijack/kjservlet/demo/controller", // Where your js files are, default is "classpath:"
        fileSuffix : ".js", // What suffix is your js file, default is ".js" 
        suffix : "", 
    },
    resources : [ "*.html", "/images/*" ],
    view : {
        resolver : function(viewFileLocation, data, headers){
            // viewFileLocation is the one that has already contacted with the prefix and suffix.
            // you can do your own logic here
            var html = ...;
            // finally don't forget to return the result object.
            return $renderer.html(html, headers); 
        },
        prefix : "/WEB-INF/pages/", // the prefix of the view
        suffix : ".jsp", // the suffix of theview
    }, 
}
```
## Annotations and AOP
Unlike Java, Javascript has no build-in annotations, and it's pretty hard to intercept into the logic in runtime while in Javascript you can defined your object any time and any where. However, we play a little trick for that. 
  
If you are familiar with Javascript, you must have heard of the **strict mode**. If you want to run a function in a strict mode, you just need to add a line "use strict" to first line of the function body. Our annotations just like that. 
```javascript
function dosth(req){
    "use strict";
    "@post"; // KJSeverlet build-in annotations, this controller accepts only "POST" request.
    "@myOwnAnno"; // user-defined annotations
    //your function codes here
    ...
    "@Anno2"; // this cannot be read.    
    ...
}
```
So, the annotations of this controller function are ["@post", "@myOwnAnno"]. 

*Notice! Annotations can only be read in the Controller functions!*

Now, you know how to put annotations, but how to use it? Let go back to $webapp in the `global.js`;
```javascript
$webapp = {
    controller : {
        fileHome : "classpath:/org/keijack/kjservlet/demo/controller", // Where your js files are, default is "classpath:"
        fileSuffix : ".js", // What suffix is your js file, default is ".js" 
        suffix : "", 
    },
    resources : [ "*.html", "/images/*" ],
    view : {
        resolver : "jsp", 
        prefix : "/WEB-INF/pages/", 
        suffix : ".jsp", 
    },
    interceptors : [ {
        intercept : ["@myOwnAnno"], // It's OK to use just a string here, rather than an array.
        before : function(req, res, ctx) {
            // do things here before the controller function being called
            return true; // you must return true to tell the framework that continue to call the controller function, or not the controller function will not be called.
        },
        after : function(req, res, result, ctx) {
            // do things after the controller function been called
        },
        onError : function(req, res, error, ctx) {
            // do things when error occurs.
        } 
    } ],  // if you only have one interceptor, you can put an object here rather that an array.
}
```

The `ctx` object pass to all your AOP functions is a global object in your Request Scope, you can use `$context` to access it in your controller script files.

For example, you can use this object to open a connection that you can use in a whole request thread.  (About the $db object, check the **The `$db` Object** section)
```javascript
// In the global.js
$webapp = {
    ...
    interceptors : [ {
        intercept : ["@myOwnAnno"], // It's OK to use just a string here, rather than an array.
        before : function(req, res, ctx) {
            ctx.conn = $db.connect(); // "default" data source is used.
            ctx.conn.autoCommit = false;
            return true; 
        },
        after : function(req, res, result, ctx) {
            ctx.conn.commit();
        },
        onError : function(req, res, error, ctx) {
            ctx.conn.rollback();
        }
    }
};
// In your controller script and the script files it imports.
$context.conn.insert("TableName", {...});
```

There are some build-in annotations, which are **"@get", "@head", "@post", "@put", "@delete", "@connect", "@options", "@trace", "@patch"**. As you can see, they are all request methods in lower case. So if you put at lease one of this annotations to a controller function, but the method of a request is not among them, a 404 error will be sent back.  

## Events
Many Javascript developers like to use events. But, Nashorn runs on Java environment, so it's weak on supporting events.

However, KJServlet provides a simple event handler. 
```javascript
/**
 * Register a function to an event
 **/
var listener = $event.on("eventName", function(data) {
	// Your codes  here will be called when an event with the eventName is published.
});

/**
 * remove the listener from the event. 
 **/
listener.off();
/**
 * Or you can use this function.
 **/
$event.remove(listener);

/**
 * Unregister an event, remove all its listeners.
 **/
$event.off("eventName");

/**
 * Publish an event
 **/
$event.publish("eventName", data);
```
*Notice! The $event works only in the request scope, that means if you cannot use $event object in `global.js` and the script files that imported to it. *

## Websocket
### Configuration
To use websocket, add the object `$websocket` definition in your `global.xml`:
```javascript
$websocket = {
    fileHome : "classpath:", // Where your handler js files are. 'classpath:' by default.
    fileExtension : ".js", // The extension of your handler js files. default '.js' by default.
    endpoints : [
        {
            endpoint : "/ws/echo/{pathValue0}/{pathValue1}", // The url that your client connect to the server. 
            handler : "/ws/echo/echo.upper", // You handler js file path and object.  
            onHandShake : function(conf, request, response) { // this method is optional
            	// your codes here. The conf, request, response objects are Java objects. 
            }
        },
        "/ws/chatRoom/checkin", // simple way, no onHanShake, the `endpoint` value and the `handler` value are the same.
    ]
}
```
In the example configuration above, your websocket handler javascript files will be stored in the java classpath, which may probably be `/WEB-INF/classes`, and with the extension `.js`. There are two endpoints registered, the first one, the websocket client will connect with the url `ws://[server-name]:[server-port]/[webapp-context]/ws/echo/pv0/pv1`, and the handler javascript file will has a name `echo.js` and be placed in the folder `classpath:/ws`. There is at least an object in this javascript, just like: 
```javascript
var echo = {
	upper : {
		onOpen : function(session, conf) {
			// This method will be called when session opens
		}, 
		onMessage : function(session, message) {
			// your codes
		},
		onClose : function(session, closeReason) {
			// your codes
		}, 
		onError : function(session, throwable) {
			// your codes
		}
	}
}
```
### Handler Methods  
Four methods will be called from there session start until the session ended. They are
* **onOpen(session, conf)**, called when session opens. `session` is a wrapped json object, conf is a Java object, the same object that pass to the `onHandShake` method that configured in the `global.js`.
* **onMessage(session, message)**, called when message are received, `session` is the same object that pass to the `onOpen` method. the `message` variable is the text message that the client send to the server.
* **onClose(session, closeReason)**, called when the session closes, `session` is the same object that pass to the `onOpen` method. `closeReason` is the J2EE original CloseReason object.
* **onError(session, throwable)**, called when exception occurs, `session` is the same object that pass to the `onOpen`method. `throwable` is the exception or error that throws by the business logic.

All these four methods are optional, you can choose those you need. 

### Fields and Methods in `session` Variable
* **session.oriSession**, the original Java Session Object.
* **session.id**, the id of this session.
* **session.sessionId**, the alias of session.id.
* **session.getId()**, the method that return the session.id.
* **session.sendText(text, isLast)**, the method that send text to client, `isLast` is optional. if the `isLast` variable is passed, the session will only send all text when `isLast` == true.
* **session.sendPing(pingMsg)**, send a ping message. 
* **session.sendPong(pongMsg)**, send a pong message.
* **session.sendBytes(bytes)**, send Java byte array, if the `bytes` variable is not a `byte[]` object, this method will not do anything.
* **session.sendBinary(binary)**, send binary data, `binary` must be the Object of `java.nio.ByteBuffer`, or this method will not do anything.
* **session.sendJSON(jsonObject)**, send a JSON object as a string. 
* **session.sendJson(jsonObject)**, alias of `session.sendJSON(jsonObject)`.
* **session.sendJavaObject(javaObject)**, send a Java Object.
* **session.send(data)**, this method will find the suitable send method to send the message.
* **session.uri**, the uri of this websocket.
* **session.requestURI**, the alias of `session.uri`.
* **session.pathValues**, the path values that configured in the endpoint. It is a JSON object, key is the words that configure in the endpoint and surrounded by the `{}`. And the value is the words that you pass in your connection. 
* **session.pathValue**, the alias of `session.pathValues`.
* **session.pathVals**, the alias of `session.pathValues`.
* **session.pathVal**, the alias of `session.pathValues`.
* **session.pathValue**, the alias of `session.pathValues`.
* **session.queryString**, the query string from the connection url.
* **session.pathParameters**, the alias of `session.pathValues`.
* **session.pathParams**, the alias of `session.pathValues`.
* **session.pathParam**, the alias of `session.pathValues`.
* **session.parameterValues**, just like the Http request, it comes from the QueryString, the values of this object is always an array. 
* **session.paramValues**, the alias of `session.parameterValues`.
* **session.paramVals**, the alias of `session.parameterValues`.
* **session.requestParameterMap**, the alias of `session.parameterValues`.
* **session.parameters**, similar with `session.parameterValues`, but the value of this object always is a string. If there are more than one value with the same name in the query string, the first one is here.

*You may save the session for a global use and send text in other threads, however, because that Nashorn is not multi-thread safe, please check the `Multi-Thread Safety` to find a solution* 


##  Global Scope And Request Scope

There are two kinds of scopes in KJservlet. One is the global scope, which would be initialized after the servlet loaded. Some inner script and the most important global script -- `gloabl.js` -- would be run at this time. 

The other scope is the request scope. When a request is come, the servlet will call dispatch method of the singleton KJServletRuntime. The dispatch method will compute the route, find the controller js, and then run it in a new scope.  

Then, there is a little trick here. After the controller script loaded, the controller function itself will run in the global scope. So your controller functions have the ability to access the objects and functions in both scope. That means outside the controller function and the functions it calls, you cannot use the objects and functions that defined in `global.js`.

While in the websocket connections, every session will all run in one scope, which will be started before `onOpen` callback, and ended after `onClose` callback.

### The `global.js` file
The `global.js` is the file for you to affect the global scope, this file is located at the class path's root folder, and must have the name `global.js`.   You are allowed to import script files here, but unlike the controller script files, you have to put all of your global files under the class path and its sub-folder, and all your global files must use the ".js" suffix. 

As this file runs only once when the runtime environment initializing, so it is recommended that all the objects that used by all (or at lease most) of the controller's function should be put here, just like the database connection pool object, some of your own configurations just like the AWS's access key and access secret. 

The most common configuration you would use here is the $webapp, which affects your routes, the location of your controller scripts, the MVC resolver, and the interceptors, all of which have already discussed in above chapters.

## Other Object That Provided
We provide some objects to simplify your coding. And more and more plugins are coming. 

### The `$db` Object
You can use `imports("$db");` to import this object to both of your scope context. But it's recommended that you should import it into your global scope, and configure you connection there.

All the dependencies won't be imported to the project automatically, so when you use this object, just handle your own dependency in your `pom.xml`. 
```xml
     
     
         mysql 
         mysql-connector-java 
         5.1.43 
     
     
     
         com.alibaba 
         druid 
         1.1.2 
     
``` 

If you want to use it in a very simple way, just use: 
```javascript
    // Although you should put the import the $db file in your global.js, but every connection has its own life style, so the following code should put to your controller function. 
    var conn = $db.connect("jdbc:mysql://127.0.0.1:3306/db", "username", "password");
``` 
But as we talked above, we don't want to scatter all the url, username, password everywhere in the code. So the following solution is a better way.
```javascript
    // This should be put to your `global.js`
    $db.addDatasource("default", {
        url : "jdbc:mysql://127.0.0.1:3306/kjtest",
        user : "username",
        password : "password"
    }); 
    // and in your controller function, you can use this
    var con = $db.connect("default");
    // because the datasource name is "default", you can ignore that argument when getting the connection:
    var con = $db.connect(); 
```

*Notice! This method only supports MySql and its variant, MariaDB, and you must handle the mysql driver dependency in your pom.xml.*

If you are not using mysql, or if you want to use some connection pool, you use this:
```javascript
    // If you use the Druid connection pool, put this to your `global.js`
    $db.addDatasource("druid", "com.alibaba.druid.pool.DruidDataSource", {
        url : "jdbc:mysql://127.0.0.1:3306/kjtest",
        username : "username",
        password : "password",
        filters : "stat",
        maxActive : 20,
        initialSize : 1,
        maxWait : 60000,
        minIdel : 1,
        timeBetweenEvictionRunsMillis : 60000,
        minEvictableIdleTimeMillis : 30000,
        testWhileIdle : true,
        testOnBorrow : false,
        testOnReturn : false,
        poolPreparedStatements : true,
        maxOpenPreparedStatements : 20
    }).init(); // Not every datasouce has this init method, please check before you write this.
    // Then in your controller function
    var conn = $db.connect("druid");
```

**The Connection Object** 

After you get the connection object, you can use **select, insert, update, delete** to do your business. 
* **conn.select(sql [, params][, firstResult[,maxResult]])**, this method will return a object array, each of the object contains one row of the result. If your table `User` like:

id | userName | userEmail | sex
------ | ------ | ------ | ------
1 | John | john@abc.com | male
2 | Mike | mike@abc.com | male
3 | Mary | mary@abc.com | female

And in your code
```javascript
    var conn = $db.connect("druid");
    var result = conn.select("select * from User where sex = ?", [ "male" ]); // If the second argument is the parameter array, its length must equal the counting of '?' in the previous string argument which is the SQL sentence.
    print(JSON.stringify(result);
```
Then you will find the output will be:
```javascript
[ 
    {"id": 1, "userName": "John", "userEmail": "john@abc.com", "sex": "male"}, 
    {"id": 2, "userName": "Mike", "userEmail": "mike@abc.com", "sex": "male"}
]
```

* **conn.insert(tableName, object || object-array)**, insert one or more object to the database, the object's properties must match the columns of this table. If want to update insert a list, please make sure that all the objects in that list has the same properties.
```javascript
    var conn = $db.connect();  // A data source named "default" is present.
    // Insert a new row to the table.
    // The result updateCount to shows how many rows have been inserted. 
    var updateCount = conn.insert("User", {
        "userName" : "Ben",
        "userEmail" : "ben@xyz.com",
        "sex" : "male"
    });
    // Insert several rows to the table
    conn.insert("User", [{
        "userName" : "Ben",
        "userEmail" : "ben@xyz.com",
        "sex" : "male"
    }, {
        "userName" : "Kate",
        "userEmail" : "kate@xyz.com",
        "sex" : "female"
    }]);
```

* **conn.update(tableName, object || object-array[, whereQuery[, queryPrameters]])**,  update a table by given object or object array. If where query sql passed, will update via that condition, or the `id` property in the objects will use. 
```javascript
    var conn = $db.connect();  // A data source named "default" is present.
    // The following sentence will update the row with the id equals 2 in the table `User`, 
    // because column `sex` hasn't passed, it will keep its old value. 
    // The result updateCount to shows how many rows have been changed. 
    var updateCount = conn.update("User", {
        "id" : 2,
        "userName" : "Michael",
        "userEmail" : "mike@bcd.com"
    });
    // Update several rows and ignore the result
    conn.update("User", [ {
        "id" : 2,
        "userName" : "Michael",
        "userEmail" : "mike@bcd.com"
    }, {
        "id" : 3,
        "userName" : "Maria",
        "userEmail" : "mary@bcd.com"
    }]);
	// Update via sql query condition
    conn.update("User", {
        "userName" : "Maria",
        "userEmail" : "mary@xyz.com"
    }, "where sex = ?", [ "female" ]);    
```

* **conn.delete(tableName, id || idArray[, idColumnName])**, delete rows via id, you can specify the id column name. 
```javascript
    var conn = $db.connect();  // A data source named "default" is present.
    // Delete the row with id equals 1
    conn.delete("User", 1);
    // Delete tow rows
    conn.delete("User", [ 1, 2 ]);
    // If your primary key is not `id`, but `pk`
    conn.delete("User", [ 1, 2 ], "pk");
```

* **conn.del(tableName, whereSql [, parameters])**, delete rows via the give query conditions. 
```javascript
    var conn = $db.connect();  // A data source named "default" is present.
    // delete all the rows with sex equals `male`
    conn.del("User", "where sex = ?", ["male"]);
```

* **conn.execute(sql [, parameters])**, if you want to execute a complicated sql, use this method to do it.
```javascript
    var conn = $db.connect();  // A data source named "default" is present.
    conn.excute("update table `User` set `name` = ? where id in (select id....)", ['John', ...]);
```

**Caching and AutoCommit**

All connections here will do the caching and auto-commit. 

With the caching, every query will be cached to the connection object, and if you query that again, the result in the cache will be returned. If you don't want caching, you can specify it in the $db object `$db.cache = false` in your `global.js`, or in the connection object to disable only one connection `conn.cache = false`. 

If you want the auto-commit off, set it in the connection object: `conn.autoCommit = false`, then you can use `conn.commit()` and `conn.rollback()` to commit,or roll back.

### The `$log` Object
KJServlet provides a simple logger for you to record your messages. By default, it use only the system standard output stream. All of its methods are:

* **$log.d(tag, message, error)**, log a debug message, `error` is a optional parameter. 
* **$log.i(tag, message, error)**, log a info message, `error` is a optional parameter.
* **$log.w(tag, message, error)**, log a warn message, `error` is a optional parameter.
* **$log.e(tag, message, error)**, log a error message, `error` is a optional parameter.
* **$log.f(tag, message, error)**, log a fatal message, `error` is a optional parameter.

The default log level is "info", that means if you use `$log.d(tag, message)`, there will be no log shows in the console. Please set the debug level in the `global.js`
```javascript
$log.level = "debug";
```

We also support log4j logger, if you want to use it, replace the default `$log` object in the `global.js`:
```javascript
$log = $logFac.getLogger("log4j");
```
The interface of the log4j logger is just as the same as the default logger. However, the $log.level will not work, and you have to create a log4j.properties to handle where and how the messages being logged. (Please read the log4j user guids for more information).

You should also handle the dependency yourself, in your `pom.xml`, you should add this dependency:
```xml
     
         log4j 
         log4j 
         1.2.17 
     
```
### The `$validator` Object
This object is provided to make validating object more easier. Please check the code bellow:
```javascript
var obj = { "name": "keijack", "password": "kj$servlet0.10", "password2": "123456789", "age": "13", "savage": "10000", "code": "1234" };
var rules = {
    "name": [
        {
            "rule": "required"
        }, {
            "rule": "length",
            "min": 3,
            "max": 20,
            "message": "The length of Name must be between {min} and {max}"
        }, {
            "rule": "regex",
            "pattern": "/^[a-zA-Z]*$/",
            "message": "Only a-z and A-Z are accepted"
        }, {
            "rule": function (val) {
                var user = loadUserByName(val);
                return user != null;
            },
            "message": "Someone has use this word, please choose other one for a name."
        }
    ],
    "passwrod": [
        {
            "rule": "required"
        }, {
            "rule": "length",
            "min": 6,
            "max": 20,
            "message": "The length of Password must be between {min} and {max}"
        }],
    "password2": [
        {
            "rule": "equalsTo",
            "target": "password"
        }
    ],
    "age": [
        {
            "rule": "number",
            "min": 18,
            "max": 60,
            "message": "Your age must be between {min} and {max}. "
        }
    ],
    "savage": [
        {
            "rule": "number"
        }
    ],
    "code": [
        {
            "rule": "required"
        }
    ]
};
var result = $validator.hasError(obj, rules);
```
The `obj` above is the object that need to be validated, and `rules` is the configuration object which contains all fields to validate and each field has a array of the rules. There are several rules are inner supported, they are 
* `required`, the object must has this field, and the value of this field should not be null. you can also use `notNull` to name this rule. 
* `length`, if this field is not null (if you want this field required, please use `required`rule to specify), the length of this field should be between the `min` and the `max` that you offer in this rule. 
* `number`, this field must be a number, you can specify the `min` and `max` to handle the range of this field.
* `equalTo`, you can specify a `target` which value must be the same of this field.
* `regex`, this field must match a regular expression which you should specify in `pattern` property. 
* A function, which will accept the value as the parameter, if you return true, that means this value is valid, and false means unvalid. if you return false.
In very rule, you can specify your own `message` property, when the field is not valid by the rule, this message will add to the result. In fact the result will look like:
```javascript
{
    name: ["This field is required", "he length of Name must be between 3 and 20"]
}
```
Of course, if there is nothing wrong with the object being validate, result will be `false`.

You can also simplify the rules object, when only one property is needed, you can just use that property as the value but not the rule format object, just like: 
```javascript
var rules = {
    "name": [
        "required",
        {
            "rule": "length",
            "min": 3,
            "max": 20,
            "message": "The length of Name must be between {min} and {max}"
        },
        /^[a-zA-Z]*$/,
        function (val) {
            var user = loadUserByName(val);
            return user != null;
        }
    ],
    "passwrod": [
        "required",
        {
            "rule": "length",
            "min": 6,
            "max": 20,
            "message": "The length of Password must be between {min} and {max}"
        }
    ],
    "password2": {
        "rule": "equalsTo",
        "target": "password"
    },
    "age":
    {
        "rule": "number",
        "min": 18,
        "max": 60,
        "message": "Your age must be between {min} and {max}. "
    },
    "savage": "number", // the same as `"savage": { "rule": "number"}`
    "code": "required"
};
```
Beside, a callback code style is provided:
```javascript
$validator.validate(obj, rules, function(result){
    // handle error here, the result is the same as the hasError() method.
});
```
## Multi-Thread Safety
Nashorn is not multi-thread safe, and for some complicated reason, it seems that Nashorn developer team will not add this feature in a short time.
 
*Please check this https://blogs.oracle.com/nashorn/nashorn-multithreading-and-mt-safety*
 
But KJServlet is run in a J2EE web container, it will start new threads when request coming. Follow the suggestion in the above article, we create new context for every request, that makes the KJServlet multi-thread safe. 

However, sometimes we have to share our own data, so we provide a global `$MTSGlobal` object. It is a sub-class of Java ConcurrentHashMap object, which is a multi-thread safe implementation of the Map interface. If you really want to share data via threads, define your sharing model in your `global.js`
```javascript
var mySharingData = $MTSGlobal.allocate();
``` 
Then use `put(key, value)`, `get(key)`, `remove(key)` methods to handle your sharing data.  


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)