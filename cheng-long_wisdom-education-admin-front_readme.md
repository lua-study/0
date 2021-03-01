### 安装


1. 克隆项目到本地 git clone https://gitee.com/zhuimengshaonian/wisdom-education-admin-front
2. 安装node依赖 npm install (注意：可能遇到安装错误问题 可以尝试删除依赖多试几遍，或着安装依赖错误之后启动下项目，然后找到错误信息百度下即可解决)
3. 启动服务 npm run dev

### 开发时，如何解决跨域？

1. 修改/config/dev.env.js目录文件中OPEN_PROXY: true开启代理
2. 修改/config/index.js目录文件中proxyTable对象target: '代理api接口请求地址'
3. 重启本地服务

### 打包 & 发布

构建生成的资源文件保存在/dist目录下，可通过config/index.js目录文件修改相关配置信息

# 构建生产环境(默认)
npm run build




 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)