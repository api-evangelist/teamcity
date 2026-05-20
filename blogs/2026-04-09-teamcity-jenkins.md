---
title: "集中的力量：TeamCity 架构如何解决 Jenkins 的扩缩难题"
url: "https://blog.jetbrains.com/teamcity/2026/04/jenkins-scaling-problems"
date: "Thu, 09 Apr 2026 04:52:22 +0000"
author: "Sue"
feed_url: "https://blog.jetbrains.com/teamcity/feed/"
---
这篇博文由 draft.dev 的 Aykut Bulgu 撰写。 当 Jenkins 安装开始出现变慢的情况时，最先表现出的问题通常是队列积压。构建等待时间过长，反馈无法及时传达给开发者，CI 系统开始需要平台团队投入远超预期的精力。 这种情况对于早期采用 Jenkins 并持续扩展的团队十分常见。Jenkins 可以扩缩，但在规模较大时，通常需要细心规划控制器规模、管理插件，在很多组织中，还需要使用多个控制器来分散负载。这种方式虽然可行，但也增加了运行开销。 对于 DevOps 工程师和架构师来说，这类开销至关重要。CI/CD 是交付流程的一部分，当平台维护的难度加大时，工程团队很快就会感受到。 在这篇博文中，我们将探讨团队在使用 Jenkins 时经常遇到的扩缩挑战，以及 TeamCity 的服务器–代理架构如何在帮助减少运行负担的同时支持从少量流水线扩展为数百个流水线。 Jenkins 的扩缩挑战 概括来讲，Jenkins 采用控制器–代理模型。中央控制器负责管理配置、调度和协调，代理则负责运行实际的构建。TeamCity 也采用中央服务器与构建代理搭配的模式，因此两者的架构相似。两者的差异体现在两套系统在大规模运行和扩展时的实现方式上。 在 Kubernetes 上运行 Jenkins…
