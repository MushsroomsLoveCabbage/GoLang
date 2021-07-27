### goroutine

------

#### 1) 背景知识

* 系统CPU内核空间线程，用户空间线程。两个的关系是 1:1，1:M，N:M
* go通过在自身空间实现调度器来实现M:N。

#### 2) 概念

* go 语言中的协程

* 每个线程都有一个 P(context),由P来管理goroutine，维护一个runqueue, 

  <img src="pic/go上下文进程线程关系图.jpeg" alt="go上下文进程线程关系图" style="zoom: 67%;" />

* 如果当前线程阻塞，会调度P绑定到一个新的线程上去，以此来保持继续

<img src="pic/go线程阻塞处理图.jpeg" alt="go线程阻塞处理图" style="zoom:67%;" />

* 当某个P的任务跑完后，会从别的P出偷取任务

  <img src="pic/go协程任务分配图.jpeg" alt="go协程任务分配图" style="zoom:67%;" />

#### 3) 疑惑

* go 中的用户空间的线程数M是否是和具体的线程进行了绑定以减少不同线程间的切换。

