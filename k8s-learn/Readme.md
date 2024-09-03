# 学习

1. Pod学习：参考链接：https://mp.weixin.qq.com/s?__biz=MzUzNTY5MzU2MA==&mid=2247485464&idx=1&sn=00ca443bbcd4b2996efdede396b6c667&chksm=fa80d98fcdf7509944d63f618264e36cd8082a77e23aa36428a3d57a2f4189bcce4e52986967&token=2033333242&lang=zh_CN&scene=21#wechat_redirect

2. Service学习参考链接：https://mp.weixin.qq.com/s?__biz=MzUzNTY5MzU2MA==&mid=2247486082&idx=1&sn=42a9bc8fcfc9da09445e9e2f4cf2fb96&chksm=fa80db15cdf752039494992f71a3bc488cf386841bd1aaaa44115f5e7f155ba55ce468ec89ee&token=2033333242&lang=zh_CN&scene=21#wechat_redirect
    - 见service-learn目录
    - `kubectl apply -f my-deployment.yaml`
    - `kubectl apply -f my-service.yaml`
    - 最后外部想访问Pod容器服务的话，需要通过NodeIP:nodePort的方式，由于本地测试的是minikube或docker-desktop这种单节点集群的方式
    - 所以对于docker-desktop的节点IP默认就是localhost，对于minikube需要`minikube ip` 获取
    - `localhost:30080` 就能访问了Pod副本中的某一个应用了

3. deployment：参考https://mp.weixin.qq.com/s?__biz=MzUzNTY5MzU2MA==&mid=2247485643&idx=1&sn=6460bf2e170e4b2e8ebb2882bfe7c60f&chksm=fa80d95ccdf7504ad9b5e3ba7ad3dad6a25347a7b0aad4636523cb1ba878cebbc480bf2153a0&token=2057376102&lang=zh_CN&scene=21#wechat_redirect
    - `kubectl get deployments`