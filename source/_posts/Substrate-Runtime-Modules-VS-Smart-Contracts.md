---
layout: Substrate
title: Substrate Runtime Modules VS Smart Contracts
categories:
  - 区块链
tags:
  - Substrate
translate_title: substrate-runtime-modules-vs-smart-contracts
date: 2019-08-14 11:44:14
---

`Substrate Runtime Modules`和`Substrate Smart Contracts`是使用`Substrate`框架构建“分布式应用程序”的两种不同方法。

本文介绍了两者的区别和各自的使用场景。
<!--more-->

## Smart Contracts
传统的智能合约平台允许用户在一些核心区块链逻辑之上发布额外的逻辑。由于任何人都可以发布智能合约逻辑，包括恶意行为者和缺乏经验的开发人员，因此围绕智能合约平台建立了许多有意识的保护措施。一些例子是：

- Fees：确保合约开发人员对运行合约的计算机上的计算和存储负责，并且不允许滥用块创建者。
- Sandbox：合约无法直接修改核心区块链存储或其他合约的存储。它的功能仅限于修改它自己的状态，以及对其他合约或运行时函数进行外部调用的能力。
- State Rent：合约占用区块链的空间，因此应该收取简单存在的费用。这确保了人们不会利用“免费，无限存储”。
- Revert：合约可能容易出现导致逻辑错误的情况。合约开发人员的期望很低，因此添加了额外的开销以支持在事务失败时恢复事务，因此在出现问题时不会更新状态。

这些不同的措施使得运行合同变得更慢且成本更高，但同样，合约开发的“目标受众”与运行时开发人员不同。

合约可以允许您的社区在您的运行时逻辑之上进行扩展和开发，而无需经历提案，运行时升级等......它甚至可以用作未来运行时更改的测试基础。

总之，智能合约：
- 本质上对网络更安全。
- 建立了反对滥用的经济激励措施。
- 具有计算开销以支持逻辑中的故障。
- 有一个较低的开发门槛。
- 开发简单易操作。

## Runtime Modules

运行时模块不提供Smart Contracts为您提供的这些保护或安全防护。作为运行时开发人员，对编码能力要求很高。

您可以完全控制网络上每个节点将运行的基础逻辑。您可以完全访问所有模块中的每个存储项，您可以对其进行修改和控制。你甚至可以用错误的逻辑或糟糕的错误处理来阻止你的链。

运行时模块开发旨在生成精简，高性能和快速的节点。它不提供事务恢复的保护或开销，并且不会隐含地引入任何费用系统来计算链上的哪些节点运行。这意味着在开发运行时函数时，您需要正确评估并向运行时逻辑的不同部分应用费用，这样它就不会被不良行为者滥用并损害您的网络。

总之，Substrate Runtime Modules：

- 提供对整个区块链的底层访问。
- 已经消除了内置安全性的开销以提高性能。
- 为开发人员提供高标准的门槛。
- 没有固有的经济动机可以击退坏人。

## The Right Tool For You
`Substrate Runtime Modules`和`Substrate Smart Contracts`都是您可以使用来解决问题的工具。

每个人可以解决的问题种类可能有一些重叠，但也有一组明显的问题只适用于两者中的一个，例如：

- Runtime Module：在区块链中的交易之上构建隐私层。
- Shared：构建像Cryptokitties这样的DApp可能需要建立一个用户社区（倾向于智能合约），或者可能需要每天扩展到数百万个交易（倾向于运行时模块）。
- Smart Contract：向您的网络引入第二层tokens和自定义资产。

除了上面写的所有内容之外，您还需要考虑使用某个工具设置DApp的成本。由于您利用现有网络，因此部署合同是一个相对简单且容易的过程。您唯一的成本是您为部署和维护合同而支付的费用。

另一方面，设置自己的区块链会产生建立社区的成本，这些社区可以在您的服务中找到价值，或者建立一个拥有云计算系统和一般网络维护成本的专用网络。

我认为现在真的是第一次构建运行时逻辑变得如此简单。在过去，每个人都使用他们可用的工具Smart Contracts构建他们的“分布式应用程序”，即使这不是最好的工具。

随着Substrate的推出，有一种新工具可用于构建分散的应用程序;但同样，认为您的所有想法都应该是substrate运行时模块是错误的。相反，作为社区的第一次，我们有两个工具，我们需要弄清楚哪个最适合每个方案。