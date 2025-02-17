---
title: |-
  SequenceDiagram: 一键可以生成时序图
category: IDEA 指南
tag:
  - IDEA
  - IDEA 插件
---

在平时的学习/工作中，我们会经常面临如下场景:

1. 阅读别人的代码
1. 阅读框架源码
1. 阅读自己很久之前写的代码。

千万不要觉得工作就是单纯写代码，实际工作中，你会发现你的大部分时间实际都花在了阅读和理解已有代码上。

为了能够更快更清晰地搞清对象之间的调用关系，我经常需要用到序列图。手动画序列图还是很麻烦费时间的，不过 IDEA 提供了一个叫做**SequenceDiagram** 的插件帮助我们解决这个问题。通过 SequenceDiagram 这个插件，我们一键可以生成时序图。

## 何为序列图？

网上对于序列图的定义有很多，我觉得都不太好理解，太抽象了。最神奇的是，大部分文章对于序列图的定义竟然都是一模一样，看来大家是充分发挥了写代码的“精髓”啊！

我还是简单说一说我的理解吧！不过，说实话，我自己对于 Sequence Diagram 也不是很明朗。下面的描述如有问题和需要完善的地方，还请指出。

::: info 序列图

**序列图**（Sequence Diagram），亦称为**循序图**，是一种[UML](https://zh.m.wikipedia.org/wiki/UML)行为图。表示系统执行某个方法/操作（如登录操作）时，对象之间的顺序调用关系。

:::

这个顺序调用关系可以这样理解: 你需要执行系统中某个对象 a 提供的方法/操作 login（登录），但是这个对象又依赖了对象 b 提供的方法 getUser(获取用户)。因此，这里就有了 a -> b 调用关系之说。

再举两个例子来说一下！

下图是微信支付的业务流程时序图。这个图描述了微信支付相关角色（顾客，商家...）在微信支付场景下，基础支付和支付的的顺序调用关系。

![](https://img-blog.csdnimg.cn/img_convert/3a48c8d17aea2064ff11b6d3fd1fb2cb.png)

下图是我写的一个 HTTP 框架中的执行某个方法的序列图。这个图描述了我们在调用 `InterceptorFactory`类的 `loadInterceptors()` 方法的时候，所涉及到的类之间的调用关系。

![](https://oss.javaguide.cn/idea/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MzM3Mjcy,size_16,color_FFFFFF,t_70.png)

另外，国内一般更喜欢称呼序列图为"时序图"。

- 如果你按照纯翻译的角度来说， sequence 这个单词并无"时间"的意思，只有序列，顺序等意思，因此也有人说“时序图”的说法是不准确的。
- 如果从定义角度来说，时序图这个描述是没问题的。因为 Sequence Diagram 中每条消息的触发时机确实是按照时间顺序执行的。

我觉得称呼 Sequence Diagram 为时序图或者序列图都是没问题的，不用太纠结。

## 哪些场景下需要查看类的时序图?

我们在很多场景下都需要时序图，比如说:

1. **阅读源码**: 阅读源码的时候，你可能需要查看调用目标方法涉及的相关类的调用关系。特别是在代码的调用层级比较多的时候，对于我们理解源码非常有用。（_题外话:实际工作中，大部分时间实际我们都花在了阅读理解已有代码上。_）
2. **技术文档编写**: 我们在写项目介绍文档的时候，为了让别人更容易理解你的代码，你需要根据核心方法为相关的类生成时序图来展示他们之间的调用关系。
3. **梳理业务流程**: 当我们的系统业务流程比较复杂的时候，我们可以通过序列图将系统中涉及的重要的角色和对象的之间关系可视化出来。
4. ......

## 如何使用 IDEA 根据类中方法生成时序图？

**通过 SequenceDiagram 这个插件，我们一键可以生成时序图。**

并且，你还可以:

1. 点击时序图中的类/方法即可跳转到对应的地方。
2. 从时序图中删除对应的类或者方法。
3. 将生成的时序图导出为 PNG 图片格式。

### 安装

我们直接在 IDEA 的插件市场即可找到这个插件。我这里已经安装好了。

::: tip

如果你因为网络问题没办法使用 IDEA 自带的插件市场的话，也可以通过[IDEA 插件市场的官网](https://plugins.jetbrains.com/idea)手动下载安装。

:::

![](https://oss.javaguide.cn/idea/20201021165654262.png)

### 简单使用

1. 选中方法名（注意不要选类名），然后点击鼠标右键，选择 **Sequence Diagram** 选项即可！

   ![](https://oss.javaguide.cn/idea/20201021170110697-20211010211819042.png)

1. 配置生成的序列图的一些基本的参数比如调用深度之后，我们点击 ok 即可！

   ![](https://oss.javaguide.cn/idea/c5040f1105c762ddf8689892913bc02d-20211010211823985.png)

你还可以通过生成的时序图来定位到相关的代码，这对于我们阅读源码的时候尤其有帮助！

![](https://oss.javaguide.cn/idea/20201021171623809-20211010211828759.png)

时序图生成完成之后，你还可以选择将其导出为图片。

![](https://oss.javaguide.cn/idea/20201021170228723-20211010211832965.png)
