# 当我有服务器时我做了什么 · <small>个人服务器运维指南</small>

去年我写了一篇文章: [当我有一台服务器时做了什么](https://shanyue.tech/op/when-server.html)。当时为了不至于浪费我在阿里云低价优惠买的服务器，于是使用 docker 跑了一个应用，并参照我司的技术架构搭建了相关的基础设施。

**现在仔细想来，这些经验也非常有益于有一台服务器却不知所措的人，于是有了本系列文章，希望能够帮助到那些服务器买来已久却在吃灰的人。** 另外如果你是一个自由开发者，本系列文章或许对你环境搭建也会有些许启发。

> 如果对你能够有所帮助，可以帮我在 [shfshanyue/op-note](https://github.com/shfshanyue/op-note) 上点个 star。

> 阿里云优惠活动，点击链接进行购买: <a href="https://www.aliyun.com/minisite/goods?userCode=4sm8juxu&share_source=copy_link">一年仅需89元即可以购买服务器~</a>。我个人服务器为2核4G配置，也更加推荐购买 <a href="https://www.aliyun.com/minisite/goods?userCode=4sm8juxu&share_source=copy_link">2核4G三年799元</a> 配置的服务器。

## 目录

1. 序
    1. [导读](https://shanyue.tech/op/introduction.html)
    1. [序·当我有一台服务器时我做了什么](https://shanyue.tech/op/when-server.html)
    1. [序·当我有一台服务器时我做了什么(2019)](https://shanyue.tech/op/when-server-2019.html)
    1. [序·个人服务器应用开发架构推荐]() - TODO
1. 如果你只想搭建博客
    1. [如果你只想搭一个博客](https://shanyue.tech/op/if-you-want-a-blog.html)
    1. [使用 netlify 托管博客与持续集成](https://shanyue.tech/op/deploy-fe-with-netlify.html)
    1. [使用 alioss 托管博客](https://shanyue.tech/op/deploy-fe-with-alioss.html)
    1. [使用 github action 持续集成](https://shanyue.tech/op/github-action-guide.html)
1. 服务器初始化配置
    1. [服务器快速登录配置：ssh-config](https://shanyue.tech/op/init.html)
    1. [git 基本命令及安装](https://shanyue.tech/op/git.html)
    1. [服务器ssh key 及 github 配置](https://shanyue.tech/op/ssh-setting.html)
    1. [系统信息查看相关命令](https://shanyue.tech/op/system-info.html)
    1. [vim 基本操作及配置](https://shanyue.tech/op/vim-setting.html)
    1. [tmux 与多窗口管理](https://shanyue.tech/op/tmux-vim-setting.html)
1. 自动化运维
    1. [ansible 简易入门](https://shanyue.tech/op/ansible-guide.html)
    1. [ansible 必知必会](https://shanyue.tech/op/ansible-problem.html) - TODO
1. 了解 docker 
    1. [docker 简易入门](https://shanyue.tech/op/docker.html)
    1. [Dockerfile 最佳实践](https://shanyue.tech/op/dockerfile-practice.html)
    1. [案例: 使用 docker 高效部署前端应用](https://shanyue.tech/op/deploy-fe-with-docker.html)
1. 使用 docker compose 编排容器
    1. [compose 编排架构简介](https://shanyue.tech/op/docker-compose-arch.html)
    1. [docker-compose 简易入门](https://shanyue.tech/op/docker-compose.html)
    1. [使用 traefik 做反向代理](https://shanyue.tech/op/traefik.html)
    1. [使用 traefik 自动生成 https 的证书]() - TODO
    1. [使用 dnsmasq 搭建本地 DNS 服务](https://shanyue.tech/op/dnsmasq.html)
    1. [使用 openvpn 访问内部集群私有服务](https://shanyue.tech/op/openvpn.html)
    1. [使用 postgres 与 redis 做数据存储服务]() - TODO
    1. [使用 sentry 做异常监控](https://shanyue.tech/op/deploy-sentry.html)
    1. [案例：一个 Node 应用的持续集成与部署实践]() - TODO
1. 使用 kubernetes 编排容器
    1. [搭建一个 k8s 集群](https://github.com/shfshanyue/learn-k8s)
    1. [部署你的第一个应用: Pod ，Deployment，Service](https://github.com/shfshanyue/learn-k8s/blob/master/pod.md)
    1. [部署你的第一个应用: Ingress](https://github.com/shfshanyue/learn-k8s/blob/master/ingress.md)
    1. [部署你的第一个应用: https](https://github.com/shfshanyue/learn-k8s/blob/master/https.md)
    1. [使用 Helm 作为包管理器](https://github.com/shfshanyue/learn-k8s/blob/master/helm.md)
    1. [持续集成 drone.ci 简介及部署](https://shanyue.tech/op/deploy-drone.html)
    1. [案例：前端部署发展史](https://shanyue.tech/op/deploy-fe.html)
1. 服务器及容器监控
    1. [linux 各项监控指标](https://shanyue.tech/op/linux-monitor.html)
    1. [使用 htop 监控服务器指标](https://shanyue.tech/op/ctop.html)
    1. [使用 ctop 监控容器指标](https://shanyue.tech/op/ctop.html)
1. 高频 linux 命令
    1. [sed 命令详解及示例](https://shanyue.tech/op/linux-sed.html)
    1. [awk 命令详解及示例](https://shanyue.tech/op/linux-awk.html)
    1. [jq 命令详解及示例](https://shanyue.tech/op/jq.html)
    1. [iptables 命令详解及示例](https://shanyue.tech/op/iptables.html) - TODO
    1. [tcpdump 命令详解及示例](https://shanyue.tech/op/linux-tcpdump.html)
    1. [htop 命令详解及示例](https://shanyue.tech/op/htop.html) - TODO
    1. [案例: 使用jq与sed制作掘金面试文章榜单](https://shanyue.tech/op/jq-sed-case.html)

## 关注我

我是山月，我会定期分享文章在个人公众号【全栈成长之路】中。你可以添加我微信 `shanyue94` 或者在公众号中联系我

![如果你对全栈面试，前端工程化，graphql，devops，个人服务器运维以及微服务感兴趣的话，可以关注我](https://shanyue.tech/qrcode.jpg)
