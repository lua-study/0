    Copyright (C) 2010-2016 Michael Wiklund.
    All rights reserved.
    Contact: arnlib@wiklunden.se

# ArnLib - Active Registry Network.

This Qt based library makes it easy to distribute changing data objects. It also gives a
central place to find all your systems' current data. By using the ArnBrowser, all data
objects are real time presented in a tree view.

### Comparison to similar concepts

* **Data mart:** Statistical data gathered from different systems. This makes it possible
to run cross system analysis.

* **Windows Active Directory (R):** Centralized configuration data. All in one place easily shared.

* **ArnLib:** Hot changing data from different systems. Enables easy cross system data
exchange, debugging, etc.
  


## Installation and usage

Read [doc/Install.md](\ref ins_build) how to build, install and use.

ArnLib could be beneficial in a lot of projects.
It should be well suited to the following conditions:

* _A lot of configurations and changing values._   
ArnLib helps giving out-of-the-box diagnostics and ability to change values not yet
available in the custom application user interface.

* _Hardware with a lot of sensors and controls._   
Arnlib helps giving a common interface and diagnostic.

* _Distributed systems._   
ArnLib helps giving an out-of-the-box data sharing system that replicates Arn objects.

* _Networked services by RPC (remote procedure call)._   
Will be quite the same as setting up signals and slots for local calls. You can find an
easy example in the ArnLib package, showing a simple chat Client and Server.

* _ZeroConfig detection of present services._   
Helps advertise and browse a service (ftp, http, arn, ...) on a local network.
This is similar to UPNP discovery of units.
  


## Main features

* Based on Qt (4 & 5), multiple platform and OS support.
* Qt based Arn browser available. Allows you to access all data objects in a tree view (see ArnBrowser).
* Web based Arn browser available, allowing you to use a standard web browser (see WebArnBrowser).

#### Arn Data Objects

* Hierarchical storage of hot changing data objects.

* _Arn Data objects_ can be: integers, floats, strings, byte arrays and variants
(most Qt data types, e.g. QImage).

* Data objects can typically be: measures, settings, data streams, documents, scripts (js), etc.

* _Arn Data objects_ are thread-safe.

* Native support for data validation and double direction pipes (streams).

* Metrics of Arn available in Arn tree.

#### Sharing

* Data objects can be shared in a single program, among threads or between programs, at
different computers. This division of program modules can be changed and is transparent
to usage of ArnLib.

* Support for temporary session data objects.
Optional auto-delete of objects when tcp/ip closes and unique uuid names.

* Dependency system with custom offered services and getting signals when all needed services
are available.

* Monitoring of newly created data objects and any mode change.

* Login system, to give access protection and different privileges.

* Remote access to Arn sessions, to view and control currently connected clients.

#### Persistent storage

* Optional persistent storage of object in SQLight or in a file.

* Support for version control (VCS) of objects stored in files.
This can be git.

#### Java Script

* Native support in JavaScript for: _Arn Data Objects_, Dependency system and
Monitoring of changed objects.

* Java Script jobstack with preemptive and cooperative scripts running at different priorities.

#### Data streams and _Remote Procedure Call_

* All data streams (pipes) can easily be monitored and manual test data can be inserted
(see ArnBrowser).

* Service Api, for calling routines anywhere in connected Arn.
_Remote Procedure Call_ (RPC) simple to use as "remote signal slots".

* Service Api has an automatically generated help for giving syntax when doing debug manual
typed calls to a RPC service.

#### ZeroConfig and Discover

* Any service (ftp, http, arn, etc) can be advertised, browsed and resolved for its host
address and port number.

* High level, fully automatic support specialised for _arn_ service, can e.g. remotely
  change the advertised _service name_.

* Optional internal DNS_SD/mDNS routines for no dependency to any extra library.

#### Qml

* Support in Qml for: _Arn Data Objects_, monitoring of changed objects and Service Api (RPC).

* Added support in Qml for url like "arn:///test.qml".

* Possibility to create a remote generic Qml running environment, comparable to a web browser
  running an arbitrary web application. This is done by ArnBrowser.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)