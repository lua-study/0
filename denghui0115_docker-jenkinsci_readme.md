# Official Jenkins Docker image

[![Docker Stars](https://img.shields.io/docker/stars/jenkins/jenkins.svg)](https://hub.docker.com/r/jenkins/jenkins/)
[![Docker Pulls](https://img.shields.io/docker/pulls/jenkins/jenkins.svg)](https://hub.docker.com/r/jenkins/jenkins/)
[![Join the chat at https://gitter.im/jenkinsci/docker](https://badges.gitter.im/jenkinsci/docker.svg)](https://gitter.im/jenkinsci/docker?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

The Jenkins Continuous Integration and Delivery server [available on Docker Hub](https://hub.docker.com/r/jenkins/jenkins).

This is a fully functional Jenkins server.
[https://jenkins.io/](https://jenkins.io/).

 


# Usage

```
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
```

NOTE: read below the _build executors_ part for the role of the `50000` port mapping.

This will store the workspace in /var/jenkins_home. All Jenkins data lives in there - including plugins and configuration.
You will probably want to make that an explicit volume so you can manage it and attach to another container for upgrades :

```
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

this will automatically create a 'jenkins_home' [docker volume](https://docs.docker.com/storage/volumes/) on the host machine, that will survive the container stop/restart/deletion.

NOTE: Avoid using a [bind mount](https://docs.docker.com/storage/bind-mounts/) from a folder on the host machine into `/var/jenkins_home`, as this might result in file permission issues (the user used inside the container might not have rights to the folder on the host machine). If you _really_ need to bind mount jenkins_home, ensure that the directory on the host is accessible by the jenkins user inside the container (jenkins user - uid 1000) or use `-u some_other_user` parameter with `docker run`.

```
docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
```

this will run Jenkins in detached mode with port forwarding and volume added. You can access logs with command 'docker logs CONTAINER_ID' in order to check first login token. ID of container will be returned from output of command above.

## Backing up data

If you bind mount in a volume - you can simply back up that directory
(which is jenkins_home) at any time.

This is highly recommended. Treat the jenkins_home directory as you would a database - in Docker you would generally put a database on a volume.

If your volume is inside a container - you can use ```docker cp $ID:/var/jenkins_home``` command to extract the data, or other options to find where the volume data is.
Note that some symlinks on some OSes may be converted to copies (this can confuse jenkins with lastStableBuild links etc)

For more info check Docker docs section on [Managing data in containers](https://docs.docker.com/engine/tutorials/dockervolumes/)

# Setting the number of executors

You can specify and set the number of executors of your Jenkins master instance using a groovy script. By default its set to 2 executors, but you can extend the image and change it to your desired number of executors :

`executors.groovy`
```
import jenkins.model.*
Jenkins.instance.setNumExecutors(5)
```

and `Dockerfile`

```
FROM jenkins/jenkins:lts
COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/executors.groovy
```


# Attaching build executors

You can run builds on the master out of the box.

But if you want to attach build slave servers **through JNLP (Java Web Start)**: make sure you map the port: ```-p 50000:50000``` - which will be used when you connect a slave agent.

If you are only using [SSH slaves](https://wiki.jenkins-ci.org/display/JENKINS/SSH+Slaves+plugin), then you do **NOT** need to put that port mapping.

# Passing JVM parameters

You might need to customize the JVM running Jenkins, typically to pass system properties ([list of props](https://wiki.jenkins.io/display/JENKINS/Features+controlled+by+system+properties)) or tweak heap memory settings. Use JAVA_OPTS environment
variable for this purpose :

```
docker run --name myjenkins -p 8080:8080 -p 50000:50000 --env JAVA_OPTS=-Dhudson.footerURL=http://mycompany.com jenkins/jenkins:lts
```

# Configuring logging

Jenkins logging can be configured through a properties file and `java.util.logging.config.file` Java property.
For example:

```
mkdir data
cat > data/log.properties   If this property is already set in **JAVA_OPTS**, then the value of
`JENKINS_SLAVE_AGENT_PORT` will be ignored.

# Installing more tools

You can run your container as root - and install via apt-get, install as part of build steps via jenkins tool installers, or you can create your own Dockerfile to customise, for example:

```
FROM jenkins/jenkins:lts
# if we want to install via apt
USER root
RUN apt-get update && apt-get install -y ruby make more-thing-here
# drop back to the regular jenkins user - good practice
USER jenkins
```

In such a derived image, you can customize your jenkins instance with hook scripts or additional plugins.
For this purpose, use `/usr/share/jenkins/ref` as a place to define the default JENKINS_HOME content you
wish the target installation to look like :

```
FROM jenkins/jenkins:lts
COPY custom.groovy /usr/share/jenkins/ref/init.groovy.d/custom.groovy
```

## Preinstalling plugins

You can rely on the `install-plugins.sh` script to pass a set of plugins to download with their dependencies.
This script will perform downloads from update centers, and internet access is required for the default update centers.

### Setting update centers

During the download, the script will use update centers defined by the following environment variables:

* `JENKINS_UC` - Main update center.
  This update center may offer plugin versions depending on the Jenkins LTS Core versions.
  Default value: https://updates.jenkins.io
* `JENKINS_UC_EXPERIMENTAL` - [Experimental Update Center](https://jenkins.io/blog/2013/09/23/experimental-plugins-update-center/).
  This center offers Alpha and Beta versions of plugins.
  Default value: https://updates.jenkins.io/experimental
* `JENKINS_INCREMENTALS_REPO_MIRROR` -
  Defines Maven mirror to be used to download plugins from the
  [Incrementals repo](https://jenkins.io/blog/2018/05/15/incremental-deployment/).
  Default value: https://repo.jenkins-ci.org/incrementals
* `JENKINS_UC_DOWNLOAD` - Download url of the Update Center. 
  Default value: `$JENKINS_UC/download`
  
It is possible to override the environment variables in images.

:exclamation: Note that changing this variables **will not** change the Update Center being used by Jenkins runtime.

### Plugin version format

Use plugin artifact ID, without `-plugin` extension, and append the version if needed separated by `:`.
Dependencies that are already included in the Jenkins war will only be downloaded if their required version is newer than the one included.

There are also custom version specifiers:

* `latest` - download the latest version from the main update center.
  For Jenkins LTS images
  (example: `git:latest`)
* `experimental` - download the latest version from the experimental update center defined by the `JENKINS_UC_EXPERIMENTAL` environment variable (example: `filesystem_scm:experimental`)
* `incrementals;org.jenkins-ci.plugins.workflow;2.19-rc289.d09828a05a74[;githubUserId][;branchName]`
- download the plugin from the [Incrementals repo](https://jenkins.io/blog/2018/05/15/incremental-deployment/).
  * For this option you need to specify `groupId` of the plugin.
    Note that this value may change between plugin versions without notice.
  * In order to automatically update Incrementals in plugins.txt, it is possible to use the Incrementals Maven Plugin:
    `mvn incrementals:updatePluginsTxt -DpluginsFile=plugins.txt`.
    [More Info](https://github.com/jenkinsci/incrementals-tools#updating-versions-for-jenkins-docker-images)

### Fine-tune the downloads

The script uses `curl` to download the plugins. You can configure the options with some environment variables:
* `CURL_OPTIONS`: When downloading the plugins with curl. Curl options. Default value: `-sSfL`
* `CURL_CONNECTION_TIMEOUT`: When downloading the plugins with curl.   Maximum time allowed for connection. Default value: `20`
* `CURL_RETRY`: When downloading the plugins with curl. Retry request if transient problems occur. Default value: `3`
* `CURL_RETRY_DELAY`: When downloading the plugins with curl.   Wait time between retries. Default value: `0`
* `CURL_RETRY_MAX_TIME`: When downloading the plugins with curl.   Retry only within this period. Default value: `60`
 
### Other environment variables
In case you have changed some default paths in the image, you can modify their values with these environment variables:
* `REF`: directory with preinstalled plugins. Default value: `/usr/share/jenkins/ref/plugins`
* `JENKINS_WAR`: full path to the jenkins.war. Default value: `/usr/share/jenkins/jenkins.war`
 
### Script usage

You can run the script manually in Dockerfile:

```Dockerfile
FROM jenkins/jenkins:lts
RUN /usr/local/bin/install-plugins.sh docker-slaves github-branch-source:1.8
```

Furthermore it is possible to pass a file that contains this set of plugins (with or without line breaks).

```Dockerfile
FROM jenkins/jenkins:lts
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh  ([\w-]+).*? ([^ )+/\1 \2\n/g'|sed 's/ /:/'
```

Example Output:

```
cucumber-testresult-plugin:0.8.2
pam-auth:1.1
matrix-project:1.4.1
script-security:1.13
...
```

For 2.x-derived images, you may also want to

    RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state

to indicate that this Jenkins installation is fully configured.
Otherwise a banner will appear prompting the user to install additional plugins,
which may be inappropriate.

# Upgrading

All the data needed is in the /var/jenkins_home directory - so depending on how you manage that - depends on how you upgrade. Generally - you can copy it out - and then "docker pull" the image again - and you will have the latest LTS - you can then start up with -v pointing to that data (/var/jenkins_home) and everything will be as you left it.

As always - please ensure that you know how to drive docker - especially volume handling!

## Upgrading plugins

By default, plugins will be upgraded if they haven't been upgraded manually and if the version from the docker image is newer than the version in the container. Versions installed by the docker image are tracked through a marker file.

To force upgrades of plugins that have been manually upgraded, run the docker image with `-e PLUGINS_FORCE_UPGRADE=true`.

The default behaviour when upgrading from a docker image that didn't write marker files is to leave existing plugins in place. If you want to upgrade existing plugins without marker you may run the docker image with `-e TRY_UPGRADE_IF_NO_MARKER=true`. Then plugins will be upgraded if the version provided by the docker image is newer.

## Hacking

If you wish to contribute fixes to this repository, please refer to the [dedicated documentation](HACKING.adoc).

# Questions?

Jump on irc.freenode.net and the #jenkins room. Ask!

[system-property]: https://wiki.jenkins.io/display/JENKINS/Features+controlled+by+system+properties


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)