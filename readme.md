# 学习docker

> 参考 https://yeasy.gitbook.io/docker_practice/compose
> docker基础：https://juejin.cn/post/7147483669299462174

## 安装

1. 前期电脑有问题，安装desktop安装包老是失败，hyperv的虚拟化程序电脑系统里缺失导致失败，后来重装系统win10pro安装成功了

## 跟学实操

### docker-compose-node-web

> web项目参考：https://www.51cto.com/article/640843.html

- 开发同一份定制镜像文件-Dockerfile，使用他两种方式
    - 1、直接构建镜像运行容器
      - `docker build -t my-node-app:dev --target dev .` 构建镜像
      - `docker run -d --name my-node-app-dev -p 3000:3000 my-node-app:dev` 启动运行容器
        - 这个启动运行会自动退出，后面再看吧，相同的镜像用docker-compose不会自动退出
        - 自动退出的话切换成交互式运行，直接看有没有报错信息即可，自动退出一般都是有报错
    - 2、用docker-compose编排的方式构建镜像运行容器
      - `docker-compose build` 编排构建
      - `docker-compose up` 编排运行容器

###  玩转docker基础项目

> 参考：https://juejin.cn/post/7147483669299462174
> 参考：https://juejin.cn/post/7160972042757079077



#### 小试开发环境玩玩

见vue-demo目录

1. 基于dockerfile构建镜像
  - `docker build -f ./Dockerfile -t test:0.0.1 .`
2. 运行镜像容器直接就可以访问vuei项目了
  - `docker run -d -p 8080:8080 test:0.0.1`
3. 以后部署的时候，就把这个镜像上传上去了运行镜像就直接能访问项目了

#### 生产环境部署

见vite-demo-prod

1. Dockerfile.anywhere 用来直接构建镜像的，用的node服务托管的dist目录
  - `docker build -f ./Dockerfile.anywhere -t vite-prod:1 .`
2. docker-compose.yml文件用来部署nginx服务器的
  - 通过挂载数据卷技术实现宿主机上自定义容器内的nginx配置和www资源目录
  - 直接 `docker-compose up` 启动容器 打开localhost就能访问到宿主机内的自定义的html了
3. TODO：尝试新建Dockerfile.web和扩展docker-compose.yml实现打包vite项目，用nginx搭建vite项目的托管服务

### 实操Makefile脚本

用于编写自动化脚本执行工具，比shell脚本强
运行默认目标（通常是 all）：`make`
运行特定目标：`make install`

Makefile 更适合需要清晰依赖关系管理的项目，并且能够很好地与 CI/CD 系统集成。
Shell 脚本 更适合需要高度定制化逻辑和灵活处理文件操作的项目