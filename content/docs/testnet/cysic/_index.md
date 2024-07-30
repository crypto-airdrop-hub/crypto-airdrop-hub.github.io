---
title: 区块链开发者带你撸空投：Cysic 测试网
date: 2024-07-20
sitemap:
  priority: 0.8
  changefreq: "hourly"
keywords:
- Cysic Network
- CysicTestnet
- Cysic 测试网
- 教程
- 区块链
slug: cysic-testnet-tutorial
description: "区块链开发者带你撸空投：参加 Cysic 测试网活动，获取空投奖励"

weight: 1
bookToc: true
# bookFlatSection: true
summary: "Cysic 测试网教程"
---

# 参与 Cysic 测试网

- Cysic Network 是一种动态协议，提供一站式零知识证明和验证功能。协议参与者可以通过为协议贡献计算能力、质押和参与治理来获得奖励。
- Cysic 在 ZK 硬件加速赛道上拥有压倒性的速度优势，服务 ZK 赛道 50 多个头部项目，拥有超过 10 万颗 3090/4090 GPU 储备，目前已完成 1800 万美元融资。

### 一、测试网教程（使用 Docker）

> 对 [官方教程](https://medium.com/@cysic/join-the-cysic-testnet-as-a-verifier-7b9f31674b41) 的补充：使用 Docker 运行 Verifier，参与 Cysic 测试网

- 镜像基于官方提供二进制文件构建，构建过程完全开源 ( [GitHub](https://github.com/whoami39/blockchain-tools/tree/main/cysic/verifier) )，无任何风险
- 自动重启，不用担心掉线

#### 安装 Docker

- 适用于国内：https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/
- 官方教程：https://docs.docker.com/engine/install/

#### 运行

新建 `docker-compose.yml` 文件（注意填写你的 EVM 地址）

```yml
services:
  verifier:
    image: whoami39/cysic-verifier:latest
    environment:
      - EVM_ADDR="<your-evm-address>"
    volumes:
      - ./data/data:/app/data
      - ./data/cysic/:/root/.cysic/
      - ./data/scroll_prover:/root/.scroll_prover
    network_mode: "host"
    restart: unless-stopped
```
执行 `docker compose up -d` 即可后台启动

你可以通过 `docker compose logs -f` 命令查看当前容器的运行日志

### 二、整体规划

此次测试网分三个阶段：

- 第一阶段（Incentive Devnet）
> 将于 7 月底启动。此阶段提供网络的基本功能，包括基于 Cosmos 的区块链、用于分配任务的集中调度程序、项目、证明者和验证者的注册流程、用于证明任务的任务跟踪流程、仪表板、Cysic Sc​​an、激励积分等。Cosmos CDK 固有的共识机制用于提出区块并达成共识。Cysic 将邀请社区成员加入 Cysic 的开发网作为验证者，以帮助解决证明问题。Cysic 选择的几个受信任方将运行验证者。

- 第二阶段（Canarynet）
> 计划于 2024 年 9 月初上线。此测试网添加的主要功能是计算证明机制。引入新的共识机制可增强 Cysic 网络的安全性和去中心化。在这个网络中，Cysic 将邀请拥有大量计算资源的社区成员加入，成为证明者和验证者。

- 第三阶段（Testnet）
> 主网之前的最后一个测试网，计划于 2024 年 11 月下旬上线。与之前的网络相比，主要增加的功能是任务分配流程、无需许可即可加入网络以及投票功能。在之前的测试网中，证明任务由集中式调度程序分配。然而，在最后一个测试网中，证明者和验证者计算可验证的随机函数来确定他们是否有资格执行特定任务，其中概率基于信用系统。除此之外，证明者和验证者不需要许可即可加入网络，并具有一些必要的防御策略。最后，实现投票功能以让社区管理 Cysic 网络。

如果最后一次测试网一切顺利，Cysic 的目标是在 2025 年初推出 Cysic 网络的主网。


---
> 你可以加入 *[区块链开发交流群](https://t.me/+ZOQ2jcLKI3hkNjFl)* 获取更多信息（自动化工具、最新空投信息分享，探讨区块链开发...）
