# 文档介绍

## 本文档适合vuejs入门，循环渐进，慢慢深入学习！

现在前端比较流行的框架有 Vue、React、Angular三种。个人比较看好Vue，性能强大，而且可学性很强，比较适合新手学习。

首先vue是一款轻量级的**MVVM框架**，压缩完之后只有20k+,这个是对比angular、react的明显优势，而且学习曲线平滑，不用像学react一样，还要学习react全家桶套餐。也不用像学习angular一样，要记很多概念，angular的开发思维很像后台的开发思维（例：依赖注入），也不适合前端小白。Vue还结合了**angular的指令**跟**react的组件化思想**，以上大概介绍了vue的优势，想了解vue对比其他框架的细节，可以去官网上查看[https://cn.vuejs.org/v2/guide...](https://cn.vuejs.org/v2/guide/comparison.html)。

Vue的核心思想是**数据驱动（DOM是数据的一种自然映射）**，*怎么理解尼？*如果不用vue，那么像我们从后台接口获取数据的时候，需要手动的去修改DOM来触发视图的变化，或者前端交互需要改变数据的时候，一样需要手动去操作DOM，这样做不仅繁琐而且非常容易出错！用了vue就省去了去手动操作DOM的步骤，你只需要去修改数据，Vue会自动去触发Dom的改变，Vue会通过VM层中的Directives去对Dom做一层封装，当数据发生变化时，会通知指令去触发对应DOM的变化。**数据驱动DOM的变化，DOM是数据的一种自然映射**这句话是不是就懂了一些！Vue还会对视图（View）去做一些监听，当我们修改视图的时候，vue会通过VM层中的DOM Listeners监听到视图的变化，进而通知数据（Model）改变。这就形成了数据的**双向绑定**。具体看下图：

![shuangxiang](./assets/shuangxiang.png)




*那么Vue是怎么做到的尼？数据相应原理（ \**数据（Model）改变如何驱动视图（view）自动更新** ）？*

其实监听到DOM的变化相对简单，通过监听绑定的事件就可以实现。关键在于如何获取到数据的变化，这就用到了ES5的**Object.definePrototype**属性，这也是Vue不支持IE6-IE8的原因。(ps:具体怎么驱动改变在本章就不介绍了，后续会写一篇专门的文章来介绍)

Vue的另一个核心思想是**组件化，目的是拓展HTML元素，封装一些可重用的代码**。*那么什么是组件，怎么写组件？*我在刚学习的时候就有这个疑问，其实跟react一样，整个**页面任何一个独立的可视/可交互区域都是一个组件**，它们可以相互嵌套。每一个组件在创建的时候都会生成一个viewModel树（类似DOM树），它与DOM树是一一对应的关系，这个类似DOM的树就是**虚拟DOM**（vDOM）。