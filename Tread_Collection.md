##同步容器类
  包括：Vector和HashTable
* 同步容器类在进行复合操作时，可能会发生意料之外的行为
* 同步容器类支持客户端加锁
* 如果不希望在迭代期间对容器加锁，另一种方法就是**“克隆”**容器

##并发容器
1. ConcurrentHashMap，CopyOnWriteArrayList
    * CopyOnWrite（写入时复制），当迭代次数远远多于修改操作时，才应该使用“写入时复制”容器
2. Queue：ConcurrentLinkedQueue
3. BlockingQueue：
    * 阻塞队列提供了可阻塞的put和take方法，以及支持定时的offer和poll方法
    * 支持生产者-消费者设计模式：消除代码依赖性（解耦）
4. Duque和BlockingDeque（双端队列）：用于工作密取设计中
