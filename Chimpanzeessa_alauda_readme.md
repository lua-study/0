# alauda-cli
The command-line interface for Alauda.io.

## Usage
```
$ alauda
Alauda CLI

Usage:
  alauda [command]

Available Commands:
  apps        List apps
  cluster     Manage clusters
  clusters    List clusters
  compose     Manage application compose
  config      Manage configurations
  configs     List configurations
  create      Create a new service
  help        Help about any command
  image       Manage images
  images      List images
  inspect     Inspect a service
  lb          Manage load balancers
  lbs         List load balancers
  login       Log onto the Alauda platform
  logout      Log out of the Alauda platform
  node        Manage nodes
  nodes       List nodes
  ps          List services
  registries  List registries
  registry    Manage registries
  restart     Restart a service
  rm          Remove a service
  run         Create and start a new service
  scale       Scale a service to the specified number of instances
  service     Manage services
  space       Manage spaces
  spaces      List spaces
  start       Start a service
  stop        Stop a service
  template    Manage application templates
  templates   List app templates
  update      Update a service
  version     Display version of Alauda CLI
  volume      Manage volumes
  volumes     List volumes

Flags:
      --config string   config file (default: $HOME/.alauda.yml)
  -h, --help            help for alauda

Use "alauda [command] --help" for more information about a command.
```

## Running Tests
1. Use `alauda login` to log into an Alauda account.
2. Add the following settings to the config file (default at `$HOME/.alauda.yml`):
```
test:
  app:  
  cluster:  
  config:  
  image:  
  lb:  
  registry:  
  registryproject:  
  repo:  
  service:  
  space:  
  template:  
  volume:  
```
3. Run `go test`.

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)