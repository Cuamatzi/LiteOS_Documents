# 什么是 RTOS ，为什么使用 RTOS

## RTOS 概念

RTOS （ Real-time operating system , 实时操作系统），又称实时操作系统，是管理系统硬件和软件资源的系统软件，以方便开发者使用，操作系统管理的资源包括处理器、存储器、外设、甚至包括文件系统等等。

实时操作系统最大的特色就是其“实时性”。也就是说，如果有任务需要执行，实时操作系统会立即（在较短时间内）执行该任务，保证了任务在指定时间内完成。

实时操作系统根据任务执行的实时性，分为“硬实时”操作系统和“软实时”操作系统，“硬实时”操作系统比“软实时”操作系统响应更快、实时性更高，“硬实时”操作系统大多应用于工业领域。

- “硬实时”操作系统必须使任务在确定的时间内完成。
- “软实时”操作系统能让绝大多数任务在确定时间内完成。

Huawei LiteOS 是一款“软实时”操作系统。

实时操作系统通常都会有最基础的内核（ Kernel ），以及扩展模块，例如文件系统、网络协议栈和应用、设备驱动程序等模块。

传统的单片机开发和部分物联网硬件开发，直接裸跑代码，主要采用下面两种编程模式：

- 轮询模式：main函数死循环，不断的查询状态位（如寄存器），满足条件就去执行相应的函数，完成后继续执行main函数剩下的逻辑。

- 中断模式：main作为为主任务死循环，外部信号触发中断，打断主任务，去处理中断任务，中断处理完自动回到主任务。

## 为什么使用 RTOS

随着物联网和人工智能技术快速发展，人们对身边的各种设备要求也越来越高。家里的台灯不仅要能远程开关，还能够通过感知周围环境和记录用户使用习惯自动进行调节；为了随时掌握身体健康状况，各种可穿戴智能手环推陈出新，能够定位，测步，记录心跳等等。

程序的复杂性也在指数级暴增。RTOS（嵌入式实时操作系统）就好比一座“大厦”的地基，只有构筑在坚固可靠的基石上，我们的物联网产品才能应对各种考验。

在8位或16位嵌入式系统应用中，由于CPU能力有限，往往采用单片机开发模式。但是，当嵌入式系统比较复杂、采用32位CPU时，由于处理能力强大，单线程的编程方式不但代码逻辑复杂、容易出错，同时也很难发挥出32位CPU的处理能力。而引入操作系统后，最主要的变化就在于”多线程“，让多任务并行，充分发挥系统资源的能力。

## 使用 RTOS带来的好处

- 降低开发难度，直接使用系统API，即可完成系统资源的申请、多任务的配合（基于优先级的实时抢占调度，同优先级的时间片调度)，以及任务间的通信等（如锁、事件等机制）。
- 增加代码可读性，易于维护和管理。
- 提升可移植性，对接不同芯片的工作由操作系统完成，应用开发者只需要关注 OS 层接口。

对于物联网端侧设备厂家来说，其产品是否需要使用操作系统，建议从以下这几个角度进行考虑和分析，相信就会有答案了。

- 开发效率
- 代码可维护性
- 可移植性
- 提升硬件资源效率
- 应用复杂性/是否需要多线程调度/联网/文件系统/加密/安全等
