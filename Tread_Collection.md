[TOC]



##同步容器类

  包括：Vector和HashTable

```java
public static <T> Collection<T> synchronizedCollection(Collection<T> c)
public static <T> List<T> synchronizedList(List<T> list)
public static <K,V> Map<K,V> synchronizedMap(Map<K,V> m)
```

* 同步容器类在进行复合操作时，可能会发生意料之外的行为
* 同步容器类支持客户端加锁
* 如果不希望在迭代期间对容器加锁，另一种方法就是**“克隆”**容器

##并发容器

线程安全，没有使用synchronized、没有迭代问题、直接支持一些复合操作

1. ConcurrentHashMap，CopyOnWriteArrayList
    * CopyOnWrite（写入时复制），当迭代次数远远多于修改操作时，才应该使用“写入时复制”容器
2. Queue：ConcurrentLinkedQueue
3. BlockingQueue：
    * 阻塞队列提供了可阻塞的put和take方法，以及支持定时的offer和poll方法
    * 支持生产者-消费者设计模式：消除代码依赖性（解耦）
4. Duque和BlockingDeque（双端队列）：用于工作密取设计中
5. ConcurrentSkipListSet

##同步工具类
1. 闭锁（Latch）：延迟线程的进度直到其到达终止状态[CountDownLatch]
2. FutureTask：在Executor框架中表示异步任务；future.get()方法
3. 信号量（Semaphore）：可以用于实现资源池；add（）和release（）方法
4. 栅栏（barrier）：用于等待其他线程，在模拟系统中通常需要使用栅栏
