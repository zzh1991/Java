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
* 可定时的与课轮询的锁提供了另一种选择：避免死锁的发生
* 可中断的锁lockInterruptedException()，可以取消任务
* 定时的tryLock同样能够响应中断
