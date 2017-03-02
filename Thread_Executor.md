# 线程

### 创建线程

- 继承 Thread 并重写 run 方法
- 实现 Runnable 接口并重写 run 方法

### 属性与方法

- Id 和 Name
- 优先级
- 状态
- 守护线程
- sleep、yield、join 方法

##线程池

* 线程池简化了线程的管理工作，将任务的提交过程与执行过程解耦开来
* Executor基于生产者-消费者模式

## Executors中静态方法来创建一个线程池
1. newFixedThreadPool
2. newCacheThreadPool
3. newSingleThreadPool
4. newScheduleThreadPool

ExecuatorService用来管理生命周期

##显示锁
###Lock接口与ReentrantLock实现
* 在内置锁中，死锁是一个严重的问题，且不可中断取消任务
* 可定时的与可轮询的锁提供了另一种选择：避免死锁的发生
* 可中断的锁lockInterruptedException()，可以取消任务
* 定时的tryLock同样能够响应中断
* ReentrantLock比内置锁，在Java6中略有胜出，在Java5中则是远远胜出（性能是一个不断变化的指标，如果在昨天的测试基准中发现X比Y更快，那么在今天可能已经过时了）
* 公平性：在大多数情况下，非公平锁的性能要远远高于公平锁的性能
* 仅当内置锁不能满足需求时，才可以考虑使用ReentrantLock

###读-写锁ReadWriteLock接口
* ReentrantReadWriteLock实现
* 当访问以读取操作为主的数据结构

##volitale变量
* 与锁相比，是一种更轻量级的同步机制
* 使用这些变量时不会发生上下文切换或线程调度等操作
* 不能用于构建原子的复合操作

##非阻塞算法
* 广泛地用于在操作系统和JVM中实现线程/进程调度机制、垃圾回收机制以及锁和其他并发数据结构
* 不存在死锁和其他活跃性问题
* 比较并交换（Compare-and-Swap），实现原子的读-改-写操作


##Synchronized
* Java中每个对象都有一个内部锁，synchronized关键字就是使用对象的内部锁完成同步功能
* synchronized代码块只会影响同一对象的所有synchronized代码块的同步访问，不影响不同对象的同步访问，不影响同一对象的非synchronized代码块的同步访问
* synchronized关键字不能被继承，子类必须显式地加上synchronized关键字才会同步
* 定义接口方法时，不能使用synchronized关键字修饰；构造方法也不能使用synchronized关键字
* synchronized修饰静态方法时，synchronized的内部锁锁定这个类所有对象
* 每个类会有一个锁，它可以用来控制对static数据成员的并发访问，主要是static synchronized代码块
* 对于synchronized方法或synchronized代码块，当出现异常时，JVM会自动释放当前线程占用的锁，因此不会犹豫异常呆滞出现死锁现象

### synchronized 使用技巧

- 实例方法、静态方法、代码块
- 多个线程是可以同时执行同一个synchronized实例方法的，只要它们访问的对象是不同的
- synchronized实例方法实际保护的是同一个对象的方法调用
- synchronized保护的是对象而非代码，只要访问的是同一个对象的synchronized方法，即使是不同的代码，也会被同步顺序访问
- synchronized静态方法和synchronized实例方法保护的是不同的对象，不同的两个线程，可以同时，一个执行synchronized静态方法，另一个执行synchronized实例方法

## Wait/Notify

- wait/notify方法只能在synchronized代码块内被调用
- 生产者/消费者模式调用的是 notifyAll 方法
- 只能有一个条件等待队列，这是Java wait/notify 机制的局限性

### 同时开始

- 子线程等待通知，主线程通知所有子线程开始

### 等待结束

- CountDownLatch：用于同时开始或者等待结束模式

##ThreadLocal
* 原理：每一个Thread都有一个Map，以一个ThreadLocal为key，\<T\>为value
* Looper，HandlerThread，Handler
    * Looper利用ThreadLocal为每一个线程建立一个MessageQueue
    * HandlerThread封装了上面的机制
