# Nextcloud Server ☁
[![Scrutinizer Code Quality](static/images/wiki/IMG_20190102_214100.svg)](https://scrutinizer-ci.com/g/nextcloud/server/?branch=master)
[![codecov](static/images/wiki/IMG_20190102_214101.svg)](https://codecov.io/gh/nextcloud/server)
[![CII Best Practices](static/images/wiki/IMG_20190102_214102.svg)](https://bestpractices.coreinfrastructure.org/projects/209)
[![irc](static/images/wiki/IMG_20190102_214103.svg)](https://webchat.freenode.net/?channels=nextcloud)
[![irc](static/images/wiki/IMG_20190102_214105.svg)](https://webchat.freenode.net/?channels=nextcloud-dev)

**A safe home for all your data.**

![](static/images/wiki/IMG_20190102_214106.png)

## Why is this so awesome? 

*   **Access your Data** You can store your files, contacts, calendars and more on a server of your choosing.
*   **Sync your Data** You keep your files, contacts, calendars and more synchronized amongst your devices.
*   **Share your Data** …by giving others access to the stuff you want them to see or to collaborate with.
*   **Expandable with dozens of Apps** ...like [Calendar](https://github.com/nextcloud/calendar), [Contacts](https://github.com/nextcloud/contacts), [Mail](https://github.com/nextcloud/mail) and all those you can discover in our [App Store](https://apps.nextcloud.com)
*   **Security** with our encryption mechanisms, [HackerOne bounty program](https://hackerone.com/nextcloud) and two-factor authentication.

You want to learn more about how you can use Nextcloud to access, share and protect your files, calendars, contacts, communication & more at home and at your Enterprise? [**Learn about all our Features**](https://nextcloud.com/features).

## Get your Nextcloud  

-   [**Simply sign up**](https://nextcloud.com/signup/) either through our website or through the apps directly.
-   [**Install** a server by yourself](https://nextcloud.com/install/#instructions-server) on your own hardware or by using one of our ready to use **appliances**
-   Buy one of the [awesome **devices** coming with a preinstalled Nextcloud](https://nextcloud.com/devices/)
-   Find a [service **provider**](https://nextcloud.com/providers/) who hosts Nextcloud for you or your company

Enterprise? Public Sector or Education user? You may want to have a look into the [**Enterprise Support Subscription**](https://nextcloud.com/enterprise/) provided by the Nextcloud GmbH.

## Get in touch  

* [  Forum](https://help.nextcloud.com)
* [  Facebook](https://facebook.com/nextclouders)
* [  Twitter](https://twitter.com/Nextclouders)
* [  Mastodon](https://mastodon.xyz/@nextcloud)

You can also [get support for Nextcloud](https://nextcloud.com/support)!


## Join the team  

There are many ways to contribute, of which development is only one! Find out [how to get involved](https://nextcloud.com/contribute/), including as translator, designer, tester, helping others and much more!  


### Development setup  

1.   [Set up your local development environment](https://docs.nextcloud.com/server/latest/developer_manual/general/devenv.html)
2.   [Pick a good first issue](https://github.com/nextcloud/server/labels/good%20first%20issue)
3.   Create a branch and make your changes. Remember to sign off your commits using `git commit -sm "Your commit message"`
4. ⬆ Create a [pull request](https://opensource.guide/how-to-contribute/#opening-a-pull-request) and `@mention` the people from the issue to review
5.   Fix things that come up during review
6.   Wait for it to get merged!

Third-party components are handled as git submodules which have to be initialized first. So aside from the regular git checkout invoking `git submodule update --init` or a similar command is needed, for details see Git documentation.

Several apps that are included by default in regular releases such as [First run wizard](https://github.com/nextcloud/firstrunwizard) or [Activity](https://github.com/nextcloud/activity) are missing in `master` and have to be installed manually by cloning them into the `apps` subfolder.

Otherwise, git checkouts can be handled the same as release archives, by using the `stable*` branches. Note they should never be used on production systems.


### Building front-end code  

We move more and more towards using Vue.js in the frontend, starting with Settings. For building the code on changes, use these terminal commands in the `settings` subfolder:

``` bash
# install dependencies
make dev-setup

# build for development
make build-js

# build for development and watch edits
make watch-js

# build for production with minification
make build-js-production

# clean output files
make clean
```

**When making changes, also commit the compiled files!**

We still use Handlebars templates some places in Files and Settings. We will replace these step-by-step with Vue.js, but in the meantime you need to compile them separately.

If you don’t have Handlebars installed yet, you can do it with this terminal command:
```
sudo npm install -g handlebars
```

Then inside the root folder of your local Nextcloud development installation, run this command in the terminal every time you changed a `.handlebars` file to compile it:
```
./build/compile-handlebars-templates.sh
```


### Tools we use  

- [  BrowserStack](https://browserstack.com) for cross-browser testing
- [  WAVE](https://wave.webaim.org/extension/) for accessibility testing
- [  Lighthouse](https://developers.google.com/web/tools/lighthouse/) for testing of performance, accessibility and more


## Contribution guidelines  

All contributions to this repository from June, 16 2016 on are considered to be
licensed under the AGPLv3 or any later version.

Nextcloud doesn't require a CLA (Contributor License Agreement).
The copyright belongs to all the individual contributors. Therefore we recommend
that every contributor adds following line to the header of a file, if they
changed it substantially:

```
@copyright Copyright (c)  ,   ( )
```

Please read the [Code of Conduct](https://nextcloud.com/community/code-of-conduct/). This document offers some guidance to ensure Nextcloud participants can cooperate effectively in a positive and inspiring atmosphere, and to explain how together we can strengthen and support each other.

Please review the [guidelines for contributing](.github/CONTRIBUTING.md) to this repository.

More information how to contribute: [https://nextcloud.com/contribute/](https://nextcloud.com/contribute/)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)