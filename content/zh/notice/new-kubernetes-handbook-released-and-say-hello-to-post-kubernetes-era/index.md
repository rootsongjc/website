---
title: "Kubernetes Handbook v1.4 发布同时后 Kubernetes 时代大幕拉启"
date: 2018-09-04T10:23:23+08:00
draft: false
description: "这是一篇后 Kubernetes 时代的檄文，Kubernetes handbook by Jimmy Song v1.4 发布，云原生的下一个重心是 Service Mesh！"
aliase: "/posts/new-kubernetes-handbook-released-and-say-hello-to-post-kubernetes-era"
type: "notice"
link: "https://jimmysong.io/kubernetes-handbook"
image: "images/backgrounds/notification.jpg"
---

这是一篇后**Kubernetes**时代的檄文。就在今天傍晚我看到了一篇 Bilgin Ibryam 的文章 *[Microservices in a Post-Kuberentes Era](https://www.infoq.com/articles/microservices-post-kubernetes)* 有感而发。

2017 年 4 月 9 日，[Kubernetes Handbook - Kubernetes中文指南/云原生应用架构实践手册](https://github.com/rootsongjc/kubernetes-handbook)第一次提交。在过去的 16 个月的时间里，有 53 位贡献者参与，1088 次 commit，共写了 23,9014 个汉字，同时在**Kubernetes&Cloud Native 实战群**里也聚集了几千名爱好者。

距离上一版本发布已经有 4 个多月的时间了，在此期间[Kubernetes](https://kubernetes.io/)和[Prometheus](https://prometheus.io/)分别从 CNCF 中毕业，已经在商业上成熟，这两个项目基本成型，未来也不会有太大的变动。而当初为容器编排而开发，为了解决微服务部署问题的 Kubernetes 已经深入人心，目前的微服务已经逐步进入**后 Kubernetes 时代**，Service Mesh 和云原生重新定义微服务和分布式应用。

本版本发布时 PDF 大小为 108M，共 239,014 个汉字，建议[在线浏览](https://jimmysong.io/kubernetes-handbook/)，或克隆本项目安装 Gitbook 命令后自行编译。

本版本主要有以下改进：

- 增加了[Istio Service Mesh 教程](https://jimmysong.io/kubernetes-handbook/usecases/istio-tutorial.html)
- 增加了
  [使用 Vagrant 和 VirtualBox 在本地搭建分布式 Kubernetes 集群和 Istio Service Mesh](https://github.com/rootsongjc/kubernetes-vagrant-centos-cluster/blob/master/README-cn.md)
- 增加了对云原生编程语言[Ballerina](https://jimmysong.io/kubernetes-handbook/cloud-native/cloud-native-programming-language-ballerina.html)和[Pulumi](https://jimmysong.io/kubernetes-handbook/cloud-native/cloud-native-programming-language-pulumi.html)的介绍
- 增加了[快速开始指南](https://jimmysong.io/kubernetes-handbook/cloud-native/cloud-native-local-quick-start.html)
- 增加了对 Kubernetes 1.11 的支持
- 增加了[企业级 Service Mesh 采用路径指南](https://jimmysong.io/kubernetes-handbook/usecases/the-enterprise-path-to-service-mesh-architectures.html)
- 增加了[SOFAMesh 章节](https://jimmysong.io/kubernetes-handbook/usecases/sofamesh.html)
- 增加了对[云原生未来的展望](https://jimmysong.io/kubernetes-handbook/cloud-native/the-future-of-cloud-native.html)
- 增加了[CNCF 章程](https://jimmysong.io/kubernetes-handbook/cloud-native/cncf-charter.html)和参与事项
- 增加了 Docker 镜像仓库的注意事项
- 增加了[Envoy 章节](https://jimmysong.io/kubernetes-handbook/usecases/envoy.html)
- 增加了[KCSP（Kubernetes 认证服务提供商）](https://jimmysong.io/kubernetes-handbook/appendix/about-kcsp.html)和[CKA（认证 Kubernetes 管理员）](https://jimmysong.io/kubernetes-handbook/appendix/about-cka-candidate.html)相关说明
- 更新了一些配置文件、YAML 和参考链接
- 更新了[CRI 章节](https://jimmysong.io/kubernetes-handbook/concepts/cri.html)
- 删除了过时的描述
- 改进了 etcdctl 的命令使用教程
- 修复了一些笔误

### 浏览与下载

- 在线浏览：<https://jimmysong.io/kubernetes-handbook>
- GitHub 地址：<https://github.com/rootsongjc/kubernetes-handbook>
- 为了方便大家下载，我放了一份在[微云](https://share.weiyun.com/5YbhTIG)上，提供 PDF（108MB）、MOBI（42MB）、EPUB（53MB）格式下载。

感谢 Kubernetes 热心用户对本书的支持，感谢各位[Contributors](https://github.com/rootsongjc/kubernetes-handbook/graphs/contributors)，在该版本发布之前的几个月内又合作成立了[ServiceMesher 社区](http://www.servicemesher.com/)，作为**后 Kubernetes 时代**的一支生力军，欢迎[联系我](http://www.servicemesher.com/contact)加入社区，共同开创**云原生新时代**。

目前**ServiceMesher 社区**微信群也有几千名成员，Kubernete Handbook 仍然会继续下去，但是 Service Mesh 已然是一颗冉冉上升的新星，在对 Kubernetes 已了然于胸的情况下，欢迎加入[ServiceMesher 社区](https://www.servicemesher.com)。
