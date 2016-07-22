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
