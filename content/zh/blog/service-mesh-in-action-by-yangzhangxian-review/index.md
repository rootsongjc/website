---
title: "《Service Mesh 实战—基于 Linkerd 和 Kubernetes 的微服务实践》读后感"
date: 2019-01-08T20:50:44+08:00
draft: false
description: "顺便对比了下 Linkerd 和 Envoy，给读者一些我自己的建议。"
tags: ["图书"]
categories: ["service mesh"]
type: "post"
aliases: "/posts/service-mesh-in-action-by-yangzhangxian-review"
bg_image: "images/backgrounds/page-title.jpg"
image: "images/banner/blog-banner.jpg"
---

最近在回顾 Service Mesh 技术在 2018 年的发展，想再看看 Linkerd，正好**杨彰显**的这本《Service Mesh 实战——基于 Linkerd 和 Kubernetes 的微服务实践》上市发售了，**机械工业出版社**的编辑送了我一本，🙏**杨福川**编辑，我看了下抽空写了点读后感，我看了下抽空写了点读后感，其实也说不上是读后感，就当是自己的一点感悟吧，就当拿此书借题发挥吧，这个知识爆炸的年代，技术发展如此迅速，可以说是 IT 人员的幸运，也是不幸！有多少写开源软件的书推出一版后能撑过三年的？如果软件红得发紫，持续迭代 N 个版本，例如 Kubernetes，最近两年以每三个月一个版本的速度迭代，之前的书早就跟不上节奏，要么就要不断推出新版，直到软件稳定后不再有大的改动。还有种可能就是软件推广和发展的不理想，无人问津，写这样软件的书就不会有再版了。

拿到本书后我的第一反应就是看看这本书定稿的时候 Istio 是什么版本，Linkerd 又是什么版本。因为在这一年内两款开源软件都有较大的版本变动，如果书籍定稿的时候基于的软件版本太低，软件架构可能会有较大的变化，影响书中示例和部分章节的时效性。这也是大多技术书籍名短的症结所在，技术发展是在太快，传统的书籍出版流程往往过于繁琐和冗长，等到书籍出版后所介绍的软件都出了好几个版本。例如 Kubernetes 这种的软件，每三个月一个版本，而写一般书从策划到发行少说半年，一般也要一年的时间。

## 关于书籍定稿时的软件版本

**Istio 0.8**

本书第一章「Service Mesh 简介」对 Service Mesh 相关开源产品介绍时提到本书定稿时 Istio 是 0.8 版本，而 Istio 在 2018 年 7 月 31 日发布了 [1.0 版本](https://istio.io/zh/about/notes/1.0/)。

这本书定稿时，Istio 的最新版本是 0.8。

**Linkerd 1.3.6**

本书从序言开始一直到第二章结束也没有提及写作时基于的 Linkerd 版本，我在第二章的安装步骤中看到了说明。

可以看到本书写作时是基于 Linkerd 1.3.6 版本，而 Linkerd 在同年的 9 月 18 日发布了 [2.0 GA](http://www.servicemesher.com/blog/linkerd-2-0-in-general-availability/)，这一版本跟 1.x 版本相比有重大变化——它还将项目从集群范围的 service mesh 转换为可组合的 *service sidecar* ，旨在为开发人员和服务所有者提供在云原生环境中成功所需的关键工具。

## Linkerd vs Envoy

Linkerd 2.0 的 service sidecar 设计使开发人员和服务所有者能够在他们的服务上运行 Linkerd，提供自动可观察性、可靠性和运行时诊断，而无需更改配置或代码。通过提供轻量级的增量路径来获得平台范围的遥测、安全性和可靠性的传统 service mesh 功能，service sidecar 方法还降低了平台所有者和系统架构师的风险。该版本还用 Rust 重写了代理部分，在延迟，吞吐量和资源消耗方面产生了数量级的改进。

而 Linkerd 1.x 继承自 Twitter 开源的 Finagle 高性能 RPC，所有想要深度学习 Linkerd 1.x 还需要了解 Finagle，这就跟 Istio 将 Envoy 作为默认的数据平面一样，要想深度学习 Istio 必须了解 Envoy。

二者几乎使用了完全不同的术语，假如你已经了解了 [Envoy](http://www.servicemesher.com/envoy/) 想要再切换到 Linkerd 上，那么就要再费很多心力来学习它的概念和原理，例如如下这些术语或配置（Linkerd 中独有的配置）：

- **dtab（委托表）**：由一系列路由组成，由一系列路由规则组成，以逻辑路径为输入，然后经过路由规则做一系列转换生成具体名字。这是 Linkerd 路由机制的根本，就像 Envoy 中的 [xDS 协议](https://jimmysong.io/istio-handbook/data-plane/envoy-xds.html)一样，本书的第四章「深入 Linkerd 数据访问流」专门讲解了 dtab 的实现机制。
- **dentry（委托表记录）**：委托表的每条路由规则称为 dentry，如 /consul => /#/io.l5d.consul/dc1。
- **namer**：配置 Linkerd 支持的服务发现工具。
- **namerd**：Linkerd 的控制平面，相当于 Istio 中的 Pilot，对接各种服务发现。当然 Linkerd 也可以直接与某个服务发现平台对接如 consul，而不使用 namerd 这个集中路由和配置管理组件。
- **interpreter**：interpreter 决定如何解析服务名字和客户端名字。

虽然 Linkerd 也是 [CNCF 中的项目](https://www.cncf.io/projects/)，但它目前还处于孵化阶段，而 Envoy 的 [xDS 协议](https://jimmysong.io/istio-handbook/data-plane/envoy-xds.html)已经被众多开源项目所支持，如 [Istio](https://istio.io/zh)、[SOFAMesh](https://github.com/alipay/sofa-mesh)、[NginxMesh](https://github.com/nginxinc/nginmesh) 等，且 Envoy 已经从 CNCF 中毕业，以后可能成为 Service Mesh 领域的标准协议，Linkerd 的生存状况堪忧。

## 关于本书

本书中所有示例都提供了虚拟机的快速上手环境，只要使用 Vagrant 即可创建虚拟机和应用，所以在本书的[示例代码](https://github.com/yangzhares/linkerd-in-action)有大量的 Vagrantfile。

本书第三部分「实战篇」花了大量篇幅（本书一半的页数）来讲解如何使用 Linkerd 和 Kubernetes 来管理微服务，可以参考我 2017 年 8 月 1 日写的这篇[微服务管理框架 service mesh——Linkerd 安装试用笔记](https://jimmysong.io/posts/linkerd-user-guide/)，那时候还是基于 Linkerd 1.1.2，还有 [Linkerd 官方示例](https://github.com/linkerd/linkerd-examples/)，这些示例基本都不怎么更新了。

因为该书定稿时所基于的 Linkerd 版本距离本书发售时的 Linkerd 已经落后一个大版本（最新版本是 [Linkerd 2.1](https://blog.linkerd.io/2018/12/06/announcing-linkerd-2-1/)），所以读者一定要注意这一点，老实说我只花了两个夜晚快速过了一下本书，无法对本书内容给出具体评论，所以本书是否是你所需要的就要你自己去思考了。

