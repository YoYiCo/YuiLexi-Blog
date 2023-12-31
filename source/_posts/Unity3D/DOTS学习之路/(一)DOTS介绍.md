---
title: (一)DOTS基础—1. 认识DOTS
date: 2023-8-21 ：00:00:00
updated: 2023-8-21 ：00:00:00
categories: [Unity3D, DOTS]
tags: [Unity3D, DOTS]
description: 此文章主要介绍DOTS架构的基础认识
image_path: Unity3D/DOTS/(一)DOTS基础—1-认识DOTS
---

# 前言

# DOTS架构

## 介绍

Unity中，`DOTS`代表的是"**Data-Oriented Technology Stack**"，官方中文名字是**多线程面向数据的技术堆栈 **，是一种用于游戏开发的技术堆栈。DOTS的目标是优化游戏引擎的性能，使开发者能够更好地利用现代硬件的多核处理能力和内存体系结构。

DOTS包含了一系列的工具、框架和技术，其中最重要的包括：

1. **Entity Component System (ECS)**：这是DOTS的核心，它是一种用于构建游戏对象和组件的新的架构。ECS将游戏对象拆分为实体（Entities）和组件（Components），并通过系统（Systems）来处理数据和逻辑。这种数据导向的方式可以更好地利用多核处理器，提高性能。
2. **Burst Compiler**：Burst Compiler是一种使用LLVM从IL/.NET字节码转换为高度优化的本机代码的编译器，可以生成高度优化的本地机器码，提高代码的执行效率。它能通过编译本地代码，极大提高代码的运行效率 10-1000倍不等，当我们在加入Jobsystem进行并行计算的时候，运行效率会进一步提升。
3. **Jobs System**：Jobs System允许开发者编写高性能的并行代码，能够更有效地利用多核处理器。通过JobSystem让我们需要大量计算的程序，以并行的方式，放入多个子线程中进行计算，这样能大大提升为我们的计算效率，其实也就是提升性能！
4. Unity Physics：Unity Physics是一个用于模拟物理行为的引擎，可以与ECS结合使用，实现高性能的物理模拟。
5. Unity Collections：这是一组优化过的集合类型，用于在ECS架构中存储和处理数据。

DOTS的引入旨在解决传统游戏引擎在大规模游戏中性能问题的挑战，但也需要开发者学习新的编程模式和工具。虽然DOTS在性能方面有很多优势，但在选择是否使用时，开发者需要权衡其带来的学习成本和适用性。



在Unity发布的 `2022LTS` 版本中，全面支持 `ECS` 架构，并且实现对 DOTS 的支持。

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=656996791&bvid=BV1eh4y197BK&cid=1154581200&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>

## DOTS应用

- 具有大世界流式加载的游戏
- 具有复杂的大规模模拟的游戏
- 具有多种网络类型的多人连线游戏
- 具有需要客户端模拟预测的网络游戏，如射击游戏

# ECS架构

## 什么是ECS？

说起 ECS 架构（面向数据编程），就不得不提到传统的面向对象编程（Object-Oriented Programming，简称OOP）。

### 面向对象编程

面向对象编程（Object-Oriented Programming，简称OOP）是一种编程范式，它的核心思想是通过将**数据**和**操作数据的方法**组合成对象，以模拟现实世界的实体和交互。OOP强调数据和方法的封装、继承和多态性，旨在提高代码的可维护性、可扩展性和重用性。

<img src="https://imageshack.yuilexi.cn/(%E4%B8%80)DOTS%E5%9F%BA%E7%A1%80%E2%80%941-%E8%AE%A4%E8%AF%86DOTSOOP%E7%BB%93%E6%9E%84.svg" alt="OOP结构" style="zoom:50%" />

在Unity中，使用传统的面向对象编程技术，是依赖**多重继承**的方式实现的，虽然Unity中有**组件系统**，但是本质上，每一个对象都是**数据和方法**的集合体。

<img src="https://imageshack.yuilexi.cn/(%E4%B8%80)DOTS%E5%9F%BA%E7%A1%80%E2%80%941-%E8%AE%A4%E8%AF%86DOTSOOP%E7%9A%84%E5%A4%9A%E9%87%8D%E7%BB%A7%E6%89%BF.svg" alt="OOP的多重继承" style="zoom:50%" />

> 总结：面向数据编程，就是将**数据**和**方法**绑定在一起，形成一个集合体，称之为**对象**。其功能的实现通过封装、**多重继承**、多态的手段实现。



### 面向数据编程——ECS

ECS即实体（Entity），组件（Component），系统（System），其中**Entity，Component皆为纯数据向的类**，**System负责操控它们**，这种模式会一定程度上优化我们的代码速度。

- Entities：游戏中的事物，但在ECS中它只作为一个Id，用于表示对应的对象。
- Components：与Entity相关的数据，但是这些数据应该由Component本身而不是Entity来组织。（这种组织上的差异正是面向对象和面向数据的设计之间的关键差异之一）。
- Systems：Systems是把Components的数据从当前状态转换为下一个状态的逻辑，但System本身应当是无状态的。例如，一个system可能会通过他们的速度乘以从前一帧到这一帧的时间间隔来更新所有的移动中的entities的位置。

## ECS为什么快？

首先明确几个知识点：

1. CPU与Memory的速度发展不均衡以及带宽限制
    1. CPU处理数据的速度非常快，即CPU的处理速度远高于内存的读写速度，所以需要设计能跟上CPU的高速缓存区，来尽量保证CPU有事干，同时也提高了数据访问效率。
    2. CPU自身有三级缓存，俗称高速缓存，CPU访问第一级（L1）缓存最快，容量最小，第三级（L3）缓存最慢，容量最大。
    3. 常说的内存是指CPU拿取数据的起源点，CPU访问内存所需的时钟周期，**远大于**访问高速缓存所需的时钟周期。
    4. CPU操作数据会先从一，二，三级缓存中取得数据，速度非常快，尤其在一级缓存处速率基本可以满足CPU的需求（即不让CPU等待数据），但是有些情况下我们请求的数据不在这三级缓存中（即 `Cache Miss` ），就需要寻址到内存中的数据（**包含这个数据的一整块数据都将被存入缓存**），并且把目标数据放到高速缓存中，提高下一次的访问速度（因为这一次调用的数据块往往在不久的将来还会用到）。
    5. 因此，CPU指令跳转的次数越少，运算速度越快。最常见的例子就是在数据量小的情况下遍历数组会比遍历List快上很多，因为数组是有序的，而列表则是分散的，无序的。
2. 摩尔定律的延续和现代CPU工艺的设计
    1. 越来越好的工艺
    2. 越来越多的核
    3. 分工越来越细的处理单元和存储
    4. SIMD/SIMT

### ECS的数据组织与使用形式

在传统模式中，假设想要移动场景中的一个物体，那么我们会修改它的 `Position` ，但是使用的时候整个 `Transform` 都会被加到缓存当中，而 `Transform` 中有很多我们不需要的属性占用了很大的缓存空间，所以就造成了严重的内存浪费。

而ECS架构在执行逻辑时，只会操作需要操作的数据：System在操作数据的时候只会收集它关心的Component数据，CPU运行时就会将这一整块内存装入高速缓存中，这样就减少了`Cache Miss`次数，增加了缓存命中率，整体上提高了程序效率。

> ECS是数据组件化的，需要哪些数据，就声明哪些数据，不会造成上面那样严重的内存浪费！
>

## ECS有什么优势

对比传统的面向对象编程，ECS模式无疑更加适合现代CPU架构，因为它可以做到高效的处理数据，而不用把多余的数据字段存入宝贵的缓存，从而导致多次 `Cache Miss` 。 举个例子就是传统模式下我们操作Unity对象的Position属性，它会把GameObject所有相关数据都加入缓存，浪费了宝贵的缓存空间。 而如果在ECS模式下，将只会把Position属性集放入内存，节省了缓存空间，也一定程度上减少了Cache Miss，即常说的`提高缓存命中率`。



# Job System

## 什么是Job System？

Job System （作业系统） 可以理解为多线程管理系统。通过Job System就可以编写与Unity其他部件交互的多线程代码，同时让编写正确的多线程代码变得更容易。编写多线程代码可以提供更好的性能表现。这包括极大的提升提升和手机上更久的续航。

Job System的一个非常关键的方面是它可以融入Unity内部的原生Job System。这使得用户的代码可以和Unity共享worker threads。这种合作避免了创建更多线程，因为这可能会造成对于CPU资源的争抢。



# 说明

## 参考文章

[Unity DOTS：入门简介（ECS，Burst Complier，JobSystem） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/138029194)
