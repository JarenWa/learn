

# Abstraction and Implementation
分布式系统的基础架构：存储、通信、计算

## 抽象之后的实现
- RPC（Remote Procedure Call）。RPC的目标就是掩盖我们正在不可靠网络上通信的事实。
- 另一个我们会经常看到的实现相关的内容就是线程。这是一种编程技术，使得我们可以利用多核心计算机。对于本课程而言，更重要的是，线程提供了一种结构化的并发操作方式，这样，从程序员角度来说可以简化并发操作。
- 因为我们会经常用到线程，我们需要在实现的层面上，花费一定的时间来考虑并发控制，比如锁。


# MapReduce
论文：
<a href="./mapreduce.pdf" target="_blank">MapReduce: Simplified Data Processing on Large Clusters</a>

## 思想
应用程序设计人员和分布式运算的使用者只需要编写 Map 函数和 Reduce 函数，剩下的分布式实现细节由 MapReduce 框架完成。