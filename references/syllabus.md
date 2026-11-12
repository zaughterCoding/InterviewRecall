# Java 后端标准题库（基于 JavaGuide）

所有用户都从这份题库出发：**题号、粒度、要掌握的内容保持一致**，个人差异只体现在三处：
1. **优先级**：根据简历、项目、个人侧重点，把题目从默认级别升为 P0，或降为 P2。
2. **范围**：核心模块默认全学；可选模块由用户决定加不加。用户可以删掉不要的模块或题目。
3. **分叉**：学习中暴露的缺口开成 🩹 补漏题；项目里有、题库里没有的做法，追加成 🔧 项目题。

## 用法

- **默认级别**：「高频」默认是 P1，「低频」默认是 P2。项目经历 bullet 或项目代码里出现的，以及由它们牵出来的题，升为 P0；只在技能栏出现的不升级。具体规则见 SKILL.md 第 2 步。
- **JavaGuide 列**：用户需要自己 clone [JavaGuide 仓库](https://github.com/Snailclimb/JavaGuide)，并在配置里给出本地路径（记为 `{JavaGuide}`）。表里的路径对应本地文件 `{JavaGuide}/docs/<路径>.md`，例如 `database/mysql/mysql-index` 对应 `{JavaGuide}/docs/database/mysql/mysql-index.md`。多个文件用"、"隔开。出题时把完整的本地路径写给用户，最好指到文中的小节标题。
- 本地文件找不到时（JavaGuide 调整过目录），先在 `{JavaGuide}/docs/` 下按文件名搜索；还找不到，就提醒用户 `git pull` 更新，或者对照在线版 `https://javaguide.cn/<路径>.html`。
- 一题 = 一个知识小节，打包 3～5 个相关的点，出题时拆成 2～4 个小问。
- 不要改题号，也不要合并或拆分题目，否则不同用户的路径就对不齐了。需要新增的题，用这个模块、章节下的下一个序号，并在来源里标 🩹 或 🔧。
- **只收 JavaGuide 有正文的内容**：JavaGuide 里标"付费"的页面（如 Redis 集群详解、SpringBoot 常见面试题、系统设计、Netty、Elasticsearch、设计模式面试题总结）只有简介、没有正文，题库已经避开。JavaGuide 没讲的知识点（如 MySQL 的 `SKIP LOCKED`）不进标准题库；个人简历或项目需要的，作为 🔧 题追加，资料查官方文档。
- 模块顺序只是参考，实际顺序由 AI 按"简历 → 项目 → 其余"和知识依赖决定。

---

# 核心模块（默认全学）

## Java 基础

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 基础-语法-01 | JDK、JRE、JVM 的关系；字节码；编译与解释并存；Java 和 C++ 的区别 | 高频 | java/basis/java-basic-questions-01 |
| 基础-语法-02 | 八种基本类型；包装类与自动装箱拆箱；包装类缓存（`Integer` 的 -128～127） | 高频 | java/basis/java-basic-questions-01 |
| 基础-语法-03 | 浮点数精度问题；`BigDecimal` 的正确用法；金额用 `long` 还是 `BigDecimal` | 低频 | java/basis/bigdecimal、java/basis/money-long-vs-bigdecimal |
| 基础-面向对象-01 | 封装、继承、多态；接口和抽象类的区别；重载和重写 | 高频 | java/basis/java-basic-questions-02 |
| 基础-面向对象-02 | `==` 和 `equals`；`hashCode` 和 `equals` 为什么要一起重写；深拷贝和浅拷贝 | 高频 | java/basis/java-basic-questions-02 |
| 基础-面向对象-03 | `String` 为什么不可变；`String`、`StringBuilder`、`StringBuffer`；字符串常量池与 `intern` | 高频 | java/basis/java-basic-questions-02 |
| 基础-面向对象-04 | Java 只有值传递 | 低频 | java/basis/why-there-only-value-passing-in-java |
| 基础-异常-01 | `Exception` 和 `Error`；受检与非受检异常；`finally` 和 `return`；try-with-resources | 高频 | java/basis/java-basic-questions-03 |
| 基础-泛型反射-01 | 泛型与类型擦除；通配符与上下界 | 高频 | java/basis/java-basic-questions-03、java/basis/generics-and-wildcards |
| 基础-泛型反射-02 | 反射的原理、优缺点和应用场景；注解的原理 | 高频 | java/basis/reflection、java/basis/java-basic-questions-03 |
| 基础-泛型反射-03 | 静态代理、JDK 动态代理、CGLIB 的原理和区别 | 高频 | java/basis/proxy |
| 基础-其他-01 | 序列化与反序列化；`transient`；常见序列化协议 | 低频 | java/basis/serialization |
| 基础-其他-02 | SPI 机制，和 API 的区别 | 低频 | java/basis/spi |
| 基础-其他-03 | 常见语法糖；`Unsafe` | 低频 | java/basis/syntactic-sugar、java/basis/unsafe |

## Java 集合

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 集合-概览-01 | 集合体系；List、Set、Queue、Map 的区别；怎么选集合 | 高频 | java/collection/java-collection-questions-01 |
| 集合-List-01 | `ArrayList` 和 `LinkedList`、数组的区别；`ArrayList` 扩容机制 | 高频 | java/collection/arraylist-source-code、java/collection/linkedlist-source-code |
| 集合-Set-01 | `HashSet` 怎么去重；`Comparable` 和 `Comparator` | 低频 | java/collection/java-collection-questions-01 |
| 集合-Queue-01 | `ArrayDeque`、`PriorityQueue`；`BlockingQueue` 的几种实现；`DelayQueue` | 低频 | java/collection/java-collection-questions-01、java/collection/arrayblockingqueue-source-code、java/collection/delayqueue-source-code |
| 集合-Map-01 | `HashMap` 底层结构、`put` 流程、扩容、长度为什么是 2 的幂、为什么转红黑树 | 高频 | java/collection/java-collection-questions-02、java/collection/hashmap-source-code |
| 集合-Map-02 | `HashMap` 为什么线程不安全，JDK 1.7 的死循环；`HashMap`、`Hashtable`、`ConcurrentHashMap` 对比 | 高频 | java/collection/java-collection-questions-02 |
| 集合-Map-03 | `ConcurrentHashMap` 在 JDK 1.7 和 1.8 的实现，怎么保证线程安全 | 高频 | java/collection/concurrent-hash-map-source-code |
| 集合-Map-04 | `LinkedHashMap` 与 LRU 缓存；`TreeMap` | 低频 | java/collection/linkedhashmap-source-code、cs-basics/data-structure/lru-cache |
| 集合-使用-01 | 集合使用注意事项：判空、遍历时删除与 fail-fast、`Arrays.asList`、`toArray` | 低频 | java/collection/java-collection-precautions-for-use |
| 集合-并发容器-01 | `CopyOnWriteArrayList` 原理；常见并发容器 | 低频 | java/collection/copyonwritearraylist-source-code、java/concurrent/java-concurrent-collections |

## Java 并发

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 并发-线程-01 | 进程和线程；线程的生命周期和状态；创建线程的几种方式 | 高频 | java/concurrent/java-concurrent-questions-01 |
| 并发-线程-02 | `sleep` 和 `wait`；`start` 和 `run`；上下文切换 | 高频 | java/concurrent/java-concurrent-questions-01 |
| 并发-线程-03 | 死锁的四个条件；怎么预防、避免、排查 | 高频 | java/concurrent/java-concurrent-questions-01、cs-basics/operating-system/dead-lock |
| 并发-JMM-01 | JMM；原子性、可见性、有序性；指令重排；happens-before | 高频 | java/concurrent/jmm |
| 并发-JMM-02 | `volatile` 的原理，能做什么、不能做什么；双重检查锁单例 | 高频 | java/concurrent/java-concurrent-questions-02 |
| 并发-锁-01 | 乐观锁和悲观锁；CAS 原理与 ABA 问题 | 高频 | java/concurrent/optimistic-lock-and-pessimistic-lock、java/concurrent/cas |
| 并发-锁-02 | `synchronized` 的原理、锁升级 | 高频 | java/concurrent/java-concurrent-questions-02、java/concurrent/java-lock |
| 并发-锁-03 | `ReentrantLock`，公平锁和非公平锁，和 `synchronized` 的区别；读写锁、`StampedLock` | 高频 | java/concurrent/reentrantlock、java/concurrent/java-lock |
| 并发-锁-04 | AQS 原理与 CLH 队列；`Semaphore`、`CountDownLatch`、`CyclicBarrier` | 高频 | java/concurrent/aqs、java/concurrent/java-concurrent-questions-03 |
| 并发-工具-01 | `ThreadLocal` 原理、内存泄漏、为什么要 `remove`；线程池中的传递问题 | 高频 | java/concurrent/threadlocal |
| 并发-工具-02 | 原子类的分类与原理（基于 CAS）；高并发计数为什么推荐 `LongAdder`（JavaGuide 只简单提到，不展开源码） | 低频 | java/concurrent/atomic-classes、java/concurrent/optimistic-lock-and-pessimistic-lock |
| 并发-线程池-01 | 线程池七个参数、执行流程、拒绝策略；为什么不建议用 `Executors` | 高频 | java/concurrent/java-thread-pool-summary |
| 并发-线程池-02 | 线程池大小怎么定；动态调参与监控；最佳实践和常见坑 | 高频 | java/concurrent/java-thread-pool-best-practices |
| 并发-异步-01 | `Future` 与 `CompletableFuture`，任务编排与异常处理 | 低频 | java/concurrent/completablefuture-intro |
| 并发-虚拟线程-01 | 虚拟线程是什么、适合什么场景、有什么坑 | 低频 | java/concurrent/virtual-thread |

## JVM

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| JVM-内存-01 | 运行时数据区；堆的分代；方法区与元空间；直接内存 | 高频 | java/jvm/memory-area |
| JVM-内存-02 | 对象的创建过程、内存布局、访问定位；常见 OOM 的区域 | 高频 | java/jvm/memory-area |
| JVM-GC-01 | 怎么判断对象可回收（引用计数、可达性分析）；四种引用 | 高频 | java/jvm/jvm-garbage-collection |
| JVM-GC-02 | 垃圾回收算法；分代收集；Minor GC 和 Full GC 的触发 | 高频 | java/jvm/jvm-garbage-collection |
| JVM-GC-03 | 常见垃圾回收器：CMS、G1、ZGC | 高频 | java/jvm/jvm-garbage-collection |
| JVM-类加载-01 | 类加载过程：加载、验证、准备、解析、初始化 | 高频 | java/jvm/class-loading-process |
| JVM-类加载-02 | 类加载器；双亲委派模型；怎么打破，为什么要打破 | 高频 | java/jvm/classloader |
| JVM-调优-01 | 常用 JVM 参数；OOM、CPU 飙高、频繁 GC 怎么排查；常用工具 | 高频 | java/jvm/jvm-parameters-intro、java/jvm/jdk-monitoring-and-troubleshooting-tools、java/jvm/jvm-in-action |
| JVM-类文件-01 | Class 文件结构 | 低频 | java/jvm/class-file-structure |

## Java IO

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| IO-基础-01 | 字节流和字符流；IO 中的装饰器、适配器等设计模式 | 低频 | java/io/io-basis、java/io/io-design-patterns |
| IO-模型-01 | BIO、NIO、AIO；NIO 的 Buffer、Channel、Selector | 高频 | java/io/io-model、java/io/nio-basis |

## MySQL

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| MySQL-基础-01 | InnoDB 和 MyISAM 的区别，为什么默认用 InnoDB | 高频 | database/mysql/mysql-questions-01 |
| MySQL-基础-02 | 一条 SQL 的执行过程：连接器、分析器、优化器、执行器 | 高频 | database/mysql/how-sql-executed-in-mysql |
| MySQL-基础-03 | 字段类型怎么选：`CHAR` 和 `VARCHAR`、`DATETIME` 和 `TIMESTAMP`、自增主键为什么不连续 | 低频 | database/mysql/mysql-questions-01、database/mysql/some-thoughts-on-database-storage-time、database/mysql/mysql-auto-increment-primary-key-continuous |
| MySQL-索引-01 | 页与 B+ 树；表本身就是一棵按主键组织的 B+ 树；为什么选 B+ 树 | 高频 | database/mysql/mysql-index |
| MySQL-索引-02 | 聚簇索引和二级索引；回表；覆盖索引；主键为什么推荐自增 | 高频 | database/mysql/mysql-index |
| MySQL-索引-03 | 联合索引；最左前缀；索引下推 | 高频 | database/mysql/mysql-index |
| MySQL-索引-04 | 索引失效的常见场景（含隐式转换）；`EXPLAIN` 怎么看 | 高频 | database/mysql/mysql-index-invalidation、database/mysql/index-invalidation-caused-by-implicit-conversion、database/mysql/mysql-query-execution-plan |
| MySQL-索引-05 | 唯一索引和普通索引的区别；用唯一键做幂等；索引的维护代价 | 高频 | database/mysql/mysql-index |
| MySQL-索引-06 | 索引和锁的关系：行锁为什么加在索引上，各种查询分别加什么锁 | 高频 | database/mysql/mysql-index、database/mysql/mysql-questions-01 |
| MySQL-事务-01 | ACID；脏读、不可重复读、幻读；四种隔离级别；RR 怎么防幻读 | 高频 | database/mysql/transaction-isolation-level |
| MySQL-事务-02 | MVCC：隐藏列、undo log、ReadView；RC 和 RR 生成 ReadView 的时机；快照读和当前读 | 高频 | database/mysql/innodb-implementation-of-mvcc |
| MySQL-锁-01 | 行锁的种类（记录锁、间隙锁、临键锁）；共享锁和排他锁；锁定读 | 高频 | database/mysql/mysql-questions-01 |
| MySQL-锁-02 | 死锁的成因，InnoDB 怎么检测和处理，怎么排查、怎么规避 | 高频 | database/mysql/mysql-questions-01 |
| MySQL-锁-03 | 乐观锁和悲观锁在数据库里的实现；条件更新实现状态机 | 高频 | java/concurrent/optimistic-lock-and-pessimistic-lock |
| MySQL-日志-01 | binlog、redo log、undo log 的作用；两阶段提交；刷盘策略 | 高频 | database/mysql/mysql-logs |
| MySQL-日志-02 | binlog 的三种格式；主从复制的过程；备份与恢复 | 低频 | database/mysql/mysql-logs、database/mysql/mysql-backup-and-restore |
| MySQL-优化-01 | 慢查询怎么定位和优化；深分页怎么优化；高性能使用规范 | 高频 | database/mysql/mysql-high-performance-optimization-specification-recommendations、high-performance/deep-pagination-optimization、high-performance/sql-optimization |

## Redis

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| Redis-基础-01 | Redis 为什么快；单线程模型与 6.0 的多线程；Lua 脚本为什么原子、中途出错会怎样；事务与 pipeline | 高频 | database/redis/redis-questions-01、database/redis/redis-questions-02 |
| Redis-数据结构-01 | 五种基本数据结构及底层实现；跳表，ZSet 为什么用跳表 | 高频 | database/redis/redis-data-structures-01、database/redis/redis-skiplist |
| Redis-数据结构-02 | Bitmap、HyperLogLog、GEO 及应用场景 | 低频 | database/redis/redis-data-structures-02 |
| Redis-内存-01 | 过期键删除策略；内存淘汰策略；bigkey 和 hotkey | 高频 | database/redis/redis-questions-01、database/redis/redis-questions-02 |
| Redis-持久化-01 | RDB 和 AOF；AOF 重写；混合持久化 | 高频 | database/redis/redis-persistence |
| Redis-缓存-01 | 缓存穿透、击穿、雪崩及解决方案 | 高频 | database/redis/redis-questions-02、database/redis/cache-basics |
| Redis-缓存-02 | 缓存与数据库一致性；三种读写策略；先删缓存还是先更新数据库 | 高频 | database/redis/3-commonly-used-cache-read-and-write-strategies |
| Redis-应用-01 | 分布式锁：`SETNX`、过期时间、误删、续期；Redisson；Redlock | 高频 | distributed-system/distributed-lock、distributed-system/distributed-lock-implementations |
| Redis-应用-02 | Stream 做消息队列，和 List、Pub/Sub 的区别；延时任务 | 低频 | database/redis/redis-stream-mq、database/redis/redis-delayed-task |
| Redis-应用-03 | 全局 ID 方案：自增、UUID、雪花算法、号段、Redis 自增 | 低频 | distributed-system/distributed-id |
| Redis-集群-01 | 主从复制、哨兵、Cluster | 高频 | database/redis/redis-questions-02 |
| Redis-性能-01 | 常见阻塞原因；内存碎片 | 低频 | database/redis/redis-common-blocking-problems-summary、database/redis/redis-memory-fragmentation |

## 计算机网络

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 网络-基础-01 | OSI 七层与 TCP/IP 四层模型，各层的协议 | 高频 | cs-basics/network/osi-and-tcp-ip-model |
| 网络-基础-02 | 从输入 URL 到页面显示发生了什么 | 高频 | cs-basics/network/the-whole-process-of-accessing-web-pages |
| 网络-HTTP-01 | HTTP 常见状态码；超时、重试与幂等 | 高频 | cs-basics/network/http-status-codes |
| 网络-HTTP-02 | HTTP/1.0、1.1、2、3 的区别；TCP Keepalive 和 HTTP Keep-Alive | 高频 | cs-basics/network/http1.0-vs-http1.1、cs-basics/network/other-network-questions、cs-basics/network/tcp-keepalive-vs-http-keepalive |
| 网络-HTTP-03 | HTTP 和 HTTPS；TLS 握手；RSA 和 ECDHE | 高频 | cs-basics/network/http-vs-https、cs-basics/network/https-rsa-vs-ecdhe |
| 网络-HTTP-04 | Cookie、Session、JWT；XSS 和 CSRF | 高频 | cs-basics/network/network-attack-means、system-design/security/advantages-and-disadvantages-of-jwt |
| 网络-HTTP-05 | HTTP 和 RPC；WebSocket 等应用层协议 | 低频 | cs-basics/network/http-vs-rpc、cs-basics/network/application-layer-protocol |
| 网络-DNS-01 | DNS 解析过程 | 高频 | cs-basics/network/dns |
| 网络-TCP-01 | 三次握手、四次挥手；为什么是三次、四次；TIME_WAIT | 高频 | cs-basics/network/tcp-connection-and-disconnection、cs-basics/network/tcp-time-wait |
| 网络-TCP-02 | TCP 怎么保证可靠：重传、流量控制、拥塞控制 | 高频 | cs-basics/network/tcp-reliability-guarantee |
| 网络-TCP-03 | TCP 和 UDP 的区别；字节流和数据报；最大连接数 | 高频 | cs-basics/network/other-network-questions、cs-basics/network/tcp-byte-stream-udp-datagram、cs-basics/network/maximum-number-of-tcp-connections-per-host |
| 网络-网络层-01 | IP 与 ARP；NAT；能 ping 通但 TCP 连不上 | 低频 | cs-basics/network/arp、cs-basics/network/nat、cs-basics/network/can-ping-but-tcp-may-not-connect |

## 操作系统

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| OS-基础-01 | 用户态和内核态；系统调用；中断与异常 | 高频 | cs-basics/operating-system/operating-system-basic-questions-01、cs-basics/operating-system/interrupt-exception-syscall |
| OS-进程-01 | 进程、线程、协程；进程状态；进程调度算法 | 高频 | cs-basics/operating-system/process-and-thread、cs-basics/operating-system/cpu-scheduling-and-load |
| OS-进程-02 | 进程间通信方式 | 高频 | cs-basics/operating-system/ipc |
| OS-进程-03 | 线程同步：互斥锁、信号量、条件变量 | 低频 | cs-basics/operating-system/os-lock-and-sync |
| OS-内存-01 | 内存管理：分页、分段、段页式；页表与 TLB | 高频 | cs-basics/operating-system/memory-management |
| OS-内存-02 | 虚拟内存；缺页异常；页面置换算法；Swap 与 OOM | 高频 | cs-basics/operating-system/virtual-memory、cs-basics/operating-system/operating-system-basic-questions-02 |
| OS-IO-01 | IO 多路复用：select、poll、epoll 的原理和区别 | 高频 | cs-basics/operating-system/io-multiplexing |
| OS-IO-02 | 零拷贝：mmap、sendfile | 低频 | cs-basics/operating-system/zero-copy |
| OS-文件-01 | 文件系统：inode、VFS、Page Cache | 低频 | cs-basics/operating-system/file-system |

## Spring

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| Spring-IoC-01 | IoC 与依赖注入；Bean 的作用域；单例 Bean 的线程安全 | 高频 | system-design/framework/spring/ioc-and-aop、system-design/framework/spring/spring-knowledge-and-questions-summary |
| Spring-IoC-02 | Bean 的生命周期 | 高频 | system-design/framework/spring/spring-knowledge-and-questions-summary |
| Spring-IoC-03 | 循环依赖与三级缓存 | 高频 | system-design/framework/spring/spring-knowledge-and-questions-summary |
| Spring-AOP-01 | AOP 的原理；JDK 动态代理和 CGLIB 怎么选 | 高频 | system-design/framework/spring/ioc-and-aop |
| Spring-事务-01 | 声明式事务原理；传播行为；事务失效的场景；事务里为什么不做网络调用 | 高频 | system-design/framework/spring/spring-transaction |
| Spring-MVC-01 | Spring MVC 的执行流程；常用注解 | 高频 | system-design/framework/spring/spring-knowledge-and-questions-summary、system-design/framework/spring/spring-common-annotations |
| Spring-Boot-01 | 自动装配原理；自定义 starter | 高频 | system-design/framework/spring/spring-boot-auto-assembly-principles |
| Spring-Boot-02 | Spring Boot 的可执行 JAR 为什么能直接运行 | 低频 | system-design/framework/spring/spring-boot-executable-jar |
| Spring-Boot-03 | `@Async` 的原理与线程池；`@Scheduled` 的线程模型 | 低频 | system-design/framework/spring/Async、system-design/schedule-task |
| Spring-设计模式-01 | Spring 中用到的设计模式 | 低频 | system-design/framework/spring/spring-design-patterns-summary |

## 消息队列

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| MQ-基础-01 | 为什么用消息队列，带来哪些问题；常见消息队列对比 | 高频 | high-performance/message-queue/message-queue、high-performance/message-queue/message-queue-interview-questions |
| MQ-可靠-01 | 消息怎么保证不丢（生产、存储、消费三段） | 高频 | high-performance/message-queue/message-queue-interview-questions、high-performance/message-queue/rocketmq-questions |
| MQ-可靠-02 | 重复消费与幂等；死信队列；消息积压怎么办 | 高频 | high-performance/message-queue/message-queue-interview-questions、high-availability/idempotency |
| MQ-可靠-03 | 顺序消息怎么保证 | 高频 | high-performance/message-queue/rocketmq-questions |
| MQ-RocketMQ-01 | RocketMQ 架构：NameServer、Broker、Topic、队列；存储设计 | 高频 | high-performance/message-queue/rocketmq-questions |
| MQ-RocketMQ-02 | 事务消息；延时消息 | 高频 | high-performance/message-queue/rocketmq-questions |
| MQ-Kafka-01 | Kafka 架构；分区与副本；为什么吞吐高 | 低频 | high-performance/message-queue/kafka-questions-01 |
| MQ-RabbitMQ-01 | RabbitMQ 的交换机模型 | 低频 | high-performance/message-queue/rabbitmq-questions |

## 分布式事务

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 分布式-理论-01 | CAP 与 BASE | 高频 | distributed-system/protocol/cap-and-base-theorem |
| 分布式-事务-01 | 2PC、3PC、XA；TCC；Saga；本地消息表；事务消息 | 高频 | distributed-system/distributed-transaction |

---

# 可选模块（默认不学，用户决定加不加）

加进来的模块按同样的方式定优先级。简历里写了的技术，即使所在模块默认不学，也要提醒用户。

## 分布式（理论与组件）

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 分布式-理论-02 | Paxos 与 Raft；ZAB | 低频 | distributed-system/protocol/raft-algorithm、distributed-system/protocol/paxos-algorithm、distributed-system/protocol/zab |
| 分布式-理论-03 | 一致性哈希；Gossip | 低频 | distributed-system/protocol/consistent-hashing、distributed-system/protocol/gossip-protocol |
| 分布式-RPC-01 | RPC 原理；Dubbo 架构；序列化与负载均衡 | 高频 | distributed-system/rpc/rpc-intro、distributed-system/rpc/dubbo |
| 分布式-组件-01 | ZooKeeper 的核心概念与应用 | 低频 | distributed-system/distributed-process-coordination/zookeeper/zookeeper-intro、distributed-system/distributed-process-coordination/zookeeper/zookeeper-plus |
| 分布式-组件-02 | API 网关；配置中心 | 低频 | distributed-system/api-gateway、distributed-system/distributed-configuration-center |
| 分布式-ID-01 | 分布式 ID 的设计要求与实战 | 低频 | distributed-system/distributed-id-design |
| 分布式-微服务-01 | 微服务的拆分、通信、治理 | 高频 | distributed-system/microservices-interview-questions |

## 高性能

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 高性能-数据库-01 | 读写分离；分库分表；分片键与扩容 | 高频 | high-performance/read-and-write-separation-and-library-subtable |
| 高性能-数据库-02 | 冷热分离 | 低频 | high-performance/data-cold-hot-separation |
| 高性能-架构-01 | 负载均衡的原理与算法 | 高频 | high-performance/load-balancing |
| 高性能-架构-02 | CDN 的工作原理 | 低频 | high-performance/cdn |

## 高可用

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 高可用-流量-01 | 限流算法：固定窗口、滑动窗口、令牌桶、漏桶；分布式限流 | 高频 | high-availability/limit-request |
| 高可用-流量-02 | 降级与熔断 | 高频 | high-availability/fallback-and-circuit-breaker |
| 高可用-调用-01 | 超时与重试；重试风暴 | 高频 | high-availability/timeout-and-retry |
| 高可用-调用-02 | 接口幂等的实现方式 | 高频 | high-availability/idempotency |
| 高可用-架构-01 | 冗余设计；SLA；压测指标 | 低频 | high-availability/redundancy、high-availability/high-availability-system-design、high-availability/performance-test |

## 系统设计

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 设计-模式-01 | 常用设计模式：单例、工厂、代理、模板方法、观察者、适配器、装饰器（结合 Spring 和 IO 里的应用来学） | 高频 | system-design/framework/spring/spring-design-patterns-summary、java/basis/proxy、java/io/io-design-patterns |
| 设计-安全-01 | 认证与授权；JWT；SSO | 高频 | system-design/security/basis-of-authority-certification、system-design/security/jwt-intro、system-design/security/sso-intro |
| 设计-安全-02 | 权限系统设计（RBAC）；加密算法；数据脱敏 | 低频 | system-design/security/design-of-authority-system、system-design/security/encryption-algorithms、system-design/security/data-desensitization |
| 设计-业务-01 | 定时任务方案；状态机与流程编排 | 低频 | system-design/schedule-task、system-design/state-machine-and-workflow |
| 设计-业务-02 | Web 实时消息推送 | 低频 | system-design/web-real-time-message-push |

## 其他框架与存储

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 框架-MyBatis-01 | `#{}` 和 `${}`；分页插件原理；一级和二级缓存 | 低频 | system-design/framework/mybatis/mybatis-interview |
| 存储-SQL-01 | SQL 基础语法；连接、子查询、聚合 | 低频 | database/sql/sql-syntax-summary |
| 存储-ES-01 | MySQL 数据同步到 Elasticsearch 的方案与一致性 | 低频 | database/mysql/mysql-to-elasticsearch-sync |
| 存储-Mongo-01 | MongoDB 的文档模型、索引、复制与分片 | 低频 | database/mongodb/mongodb-questions-01、database/mongodb/mongodb-questions-02 |

## 工具与 Linux

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 工具-Docker-01 | 镜像、容器、仓库；Compose；容器为什么比虚拟机轻 | 低频 | tools/docker/docker-intro |
| 工具-Git-01 | merge 和 rebase；常见冲突处理 | 低频 | tools/git/git-intro |
| 工具-Maven-01 | 依赖传递与冲突；生命周期 | 低频 | tools/maven/maven-core-concepts |
| 工具-Linux-01 | 常用命令：查进程、查端口、看日志、查 CPU 和内存 | 低频 | cs-basics/operating-system/linux-intro、cs-basics/operating-system/shell-intro |

## Java 新特性

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 新特性-01 | Java 8：Lambda、Stream、Optional、新日期 API | 高频 | java/new-features/java8-common-new-features |
| 新特性-02 | Java 17 和 21 的重要特性：record、密封类、模式匹配、虚拟线程 | 低频 | java/new-features/java17、java/new-features/java21 |

## 数据结构与算法

这部分以刷题为主，不适合"口述 + 追问"的方式。默认不学，只在用户明确要求时，挑数据结构里的原理题（如红黑树、跳表、布隆过滤器）加进来。

| 题号 | 要掌握的内容 | 默认 | JavaGuide |
|---|---|---|---|
| 数据结构-01 | 红黑树、B 树和 B+ 树 | 低频 | cs-basics/data-structure/red-black-tree、cs-basics/data-structure/tree |
| 数据结构-02 | 布隆过滤器的原理与应用 | 低频 | cs-basics/data-structure/bloom-filter |
