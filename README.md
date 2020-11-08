# fed-e-task-04-01

## 1. 请简述 React 16 版本中初始渲染的流程

答：首先生成虚拟 Dom，然后根据虚拟 Dom 生成 Fiber 树，遍历 Fiber 树并收集副作用依赖，最后生成 Dom。

## 2. 为什么 React 16 版本中 render 阶段放弃了使用递归

答：因为使用递归要等到所有递归处理完才会一层层返回结果，这样如果页面节点比较多，就会造成页面假死现象。而采用链表的方法，可以随时中断，提高了性能。

## 3. 请简述 React 16 版本中 commit 阶段的三个子阶段分别做了什么事情

答：

- 第一个阶段：执行了 getSnapshotBeforeUpdate
- 第二个阶段：执行了渲染 Dom 相关的操作
- 第三个阶段：执行了渲染 Dom 之后的操作

## 4. 请简述 workInProgress Fiber 树存在的意义是什么

答：react 会存储两个 Fiber 树，一个是 current，是当前渲染的 Fiber 树，另一个就是 workInProgress，是将要渲染的 Fiber 树。当视图更新时直接将 workInProgress 替换为 current，这样可以减少白屏时间。
