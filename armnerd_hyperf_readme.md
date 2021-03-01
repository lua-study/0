# Hyperf Develop
 > k8s单机部署
 > 热更新
 > 目录映射
 > 方便开发微服务

### minikube
 - https://github.com/kubernetes/minikube
 - https://minikube.sigs.k8s.io

```bash
// 安装
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikub
sudo mv minikube /usr/local/bin
minikube start --registry-mirror=https://registry.docker-cn.com
minikube stop
minikube delete

// 使用Minikube中的Docker守护进程
eval $(minikube docker-env)

// 查看pods
kubectl get po -A
minikube kubectl -- get po -A

// 面板
minikube dashboard

// ingress
minikube addons enable ingress
```

### Hyperf
```bash
// 进入虚拟机
minikube ssh

// 克隆脚手架构建镜像
git clone https://gitee.com/armnerd/hyperf.git
cd hyperf/build
docker image build -t mine/hyperf .

// 创建应用
kubectl apply -f build/hyperf.yaml
```

### Ingress
 - Nginx Ingress Controller
 - https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-manifests/
 - Copy && Paste && Apply

##### 部署
```bash
kubectl apply -f build/ingress.yaml
```

##### Host:80
```bash
kubectl edit deployment nginx-ingress -n nginx-ingress
hostNetwork: true
```

##### 配置Hosts
```bash
127.0.0.1   local.hyperf.com
```

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)