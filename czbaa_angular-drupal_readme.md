# angular-drupal

An Angular JS module for Drupal 7 Services.

# Intro

This Angular module makes it easy to `read/write` entity data `to/from` Drupal,
handles user authentication and registration, and makes it easy to retrieve
JSON data from Views.

Here's a very *simple* Angular app that loads `node # 123` from Drupal and then
displays the node's title (via an `alert`):

```javascript
// My simple app.
angular.module('myApp', ['angular-drupal']).run(['drupal', function(drupal) {

  drupal.node_load(123).then(function(node) {
    alert(node.title);
  });

}]);

// The angular-drupal configuration settings for my simple app.
angular.module('angular-drupal').config(function($provide) {

  $provide.value('drupalSettings', {
    sitePath: 'http://my-drupal-site.com',
    endpoint: 'api'
  });

});
```

# Installation and Setup

There are two main parts to the installation and usage of this module. First,
on your Drupal site you need to install the *Angular Drupal* module, then
install and configure the *Services* module. Finally, include the
*angular-drupal* module in your Angular JS application.

## 0. Angular Drupal Module

https://www.drupal.org/project/angular_drupal

```
drush dl angular_drupal
drush en -y angular_drupal
```

## 1. Drupal Services Module Setup

By enabling the `angular_drupal` module, that will enable the `services` module by default:

- https://www.drupal.org/project/services

Then just enable the `rest_server` sub module that comes with `services`:

```
drush en -y rest_server
```

Then create a new endpoint by going to `admin/structure/services/add` with the following info:

```
machine name: api
server: REST
path: api
debug: unchecked
session authentication: checked
```

Save it, then click the edit resources link and check the box next to each resource that should be available to your app:

```
comment
file
node
system
taxonomy_term
taxonomy_vocabulary
user
```

Then click *Save*. After that, click the *Server* tab and make sure the following boxes are checked:

```
json
application/json
application/x-www-form-urlencoded
multipart/form-data
```

Then click *Save*. After that flush all of Drupal's caches.

```
drush cc all
```

## 2. Angular JS Setup

As usual, be sure to include the `angular-drupal.js` file in your app. This
typically is included via the `index.html` file somewhere after you include the
`angular.js` file:

```html
  
```

The `angular-drupal` module comes with a Service called `drupal`. You can
include this service throughout your app using Angular's dependency injection
mechanism.

The simple app, listed above, injects the `drupal` service into the app's `run`
function. Then when the app runs it loads `node # 123` from Drupal and then
alerts the node's title.

Notice how we used a `config` function on the `angular-drupal` module in the
simple app to provide the URL to our Drupal site, as well as the machine name of
the Services endpoint. Without this, the module won't know how to connect to
our Drupal site, so this must be added to our app as in the example above.

# Usage

## AUTHENTICATION

### CONNECT
```javascript
drupal.connect().then(function(data) {
  if (data.user.uid) { alert('Hello ' + data.user.name + '!'); }
  else { alert('Please login.');  }
});
```

### USER REGISTRATION
```javascript
var account = {
  name: 'bob',
  mail: 'bob@example.com',
  pass: 'secret'
};
drupal.user_register(account).then(function(data) {
    alert('Registered user # ' + data.uid);
});
```

### USER LOGIN
```javascript
drupal.user_login('bob', 'secret').then(function(data) {
  if (data.user.uid) {
    alert('Hello ' + data.user.name + '!');
  }
});
```

### USER LOGOUT
```javascript
drupal.user_logout().then(function(data) {
  if (!data.user.uid) {
    alert('Logged out!');
  }
});
```

### USER REQUEST NEW PASSWORD
```
drupal.user_request_new_password('username_or_email').then(successFn, errorFn);
```

### USER PASSWORD RESET

Process the reset link sent by email. User ID, timestamp and hashed pass need to be extracted from links like:

http://www.example.com/1/1441253855/Al-982NmYehyB3mC9suEO_cuQznbR6OlUP3C7CGYA_M
```

drupal.user_pass_reset(1, '1441253855', 'Al-982NmYehyB3mC9suEO_cuQznbR6OlUP3C7CGYA_M').then(successFn, errorFn);
```

Success function will receive a token (pass_reset_token) which you have to save, it will allow you to create an user edit form without the Current Password field, but you need to send this token to the user edit method like this:
```

var account = {
  uid: 123,
  name: 'john',
  resetToken: pass_reset_token
};
drupal.user_save(account).then(function(data) {
  alert('Name changed to: ' + data.name);
});
```

Also you need the following services patch in order to use this function https://www.drupal.org/node/2402339#comment-10302551

## NODES

### CREATE
```javascript
var node = {
  type: 'article',
  title: 'Hello world',
  language: 'und',
  body: { und: [ { value: 'How are you?' }] }
};
drupal.node_save(node).then(function(data) {
    alert('Created node: ' + data.nid);
});
```

### RETRIEVE
```javascript
drupal.node_load(123).then(function(node) {
    alert('Loaded node: ' + node.title);
});
```

### UPDATE
```javascript
var node = {
  nid: 123,
  title: 'Goodbye world',
  language: 'und',
  body: {
    und: [ { value: 'I am fine, thank you.' }]
  }
};
drupal.node_save(node).then(function(data) {
    alert('Updated node: ' + data.nid);
});
```

### DELETE
```javascript
drupal.node_delete(123).then(function(data) {
    if (data[0]) {
      alert('Deleted node.');
    }
});
```

### INDEX
```javascript
var query = {
  parameters: {
    'type': 'article'
  }
};
drupal.node_index(query).then(function(nodes) {
    var msg = '';
    for (var i = 0; i  
```

## Views

If you install the Views JSON module, which is available as a sub module of the
Views Datasource module (https://www.drupal.org/project/views_datasource), you
can easily set up a View page display to return JSON to your app:

```javascript
var path = 'articles'; // The Drupal path to the Views JSON page display.
drupal.views_json(path).then(function(rows) {
  angular.forEach(rows, function(row, i) {
    console.log(row.title);
  });
});
```

For more information on creating Views JSON page displays, read this:

http://drupalgap.org/node/220

## X-CSRF-Token
The `angular-drupal` module automatically takes care of the `X-CSRF-Token` when
it is needed. If you need to manually get the token it can easily be retrieved:
```javascript
drupal.token().then(function(token) {
  console.log('Got the token: ' + token);
});
```

# DISCLAIMER
This module has unit test coverage to maintain quality, and welcomes comments,
criticisms and pull requests.

Thank you!


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)