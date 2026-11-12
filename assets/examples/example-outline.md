# 示范：题目大纲的粒度和分级

> 这是方法作者真实大纲的摘录（Java 后端方向），原样保留。生成大纲时，**模仿这里的粒度、分级和列的写法**。文中的链接是作者仓库里的相对路径，在这里打不开，不影响参考。**题号以标准题库为准**：这份摘录早于题库，Redis、MQ 等模块用的是临时题号（如 `Redis-01`）。

## 这份示范要学的点

| 位置 | 要学什么 |
|---|---|
| 粒度 | **一题 = 一个知识小节**，打包 3～5 个紧密相关的点（比如"ACID；脏读、不可重复读、幻读；四种隔离级别；RR 怎么防幻读"），出题时再拆成 2～4 个小问。现在统一以标准题库 `references/syllabus.md` 的粒度为准。不要拆成一个概念一题 |
| 模块开头一行 | 先列出简历里和这个模块有关的原话（"简历：死锁排查、SKIP LOCKED 认领……"），这个模块为什么重要一目了然 |
| 多个来源标记 | 一道题可以同时是 🩹📄🔧：既是补漏，又在简历里写了，项目里也用到了 |
| ⚠️ 不要照学的地方 | 这份大纲里，有些题只因为**技能栏**写了就标成 P0（比如 `Redis-05` 技能栏"数据结构"、`并发-03` 技能栏"锁机制"）。这是旧规则。现在的规则是：P0 只给项目经历 bullet 和项目代码链路上的题，只在技能栏出现的保持默认级别（见 SKILL.md 第 2 步） |
| 「项目 / 简历关联」列 | 写到具体的东西：表的索引 `(channel_id, state, id)`、类名 `RedisIdWorker`、数字"107 次死锁降到 0"、项目题库编号 Q1.3。写不出具体关联的就写 — |
| 「查哪里」列 | 指到具体文件，最好到小节 |
| 章节顺序 | 按依赖排：锁依赖索引，所以索引在锁前面 |
| 牵连出来的通用知识 | `网络-01` TCP 拥塞控制，是从简历里的"AIMD 自适应并发"牵出来的，所以是 P0 |
| P2 粒度 | P2 不限于模块，可以是单个技术点：Redis 里的"主从、哨兵、集群"是 P2；Kafka 项目里用了、简历没写，也是 P2 |
| 被排除但简历写了 | 用户排除了 MyBatis、Docker、Linux、Git 这些模块，但简历技能栏写了，所以单独开一节"简历技能栏里写了、原计划排除的"，每项只准备 3～5 个常见问题，不深挖 |
| 状态 | ⬜ 未开始 / 🟡 进行中 / ✅ 完成（★★☆ 以上） |

---

## 标记说明

| 标记 | 含义 |
|---|---|
| 📄 简历 | 简历项目经历或技能栏里直接写了 |
| 🔧 项目 | Tessera 项目里用到了 |
| 📚 通用 | 和项目无关的常见八股 |
| 🩹 补漏 | 追问时暴露的薄弱点，补的前置知识 |
| **P0** | 几乎一定会被问，先做 |
| **P1** | 被追问时可能问到 |
| **P2** | 有余力再做 |
| ⬜ / 🟡 / ✅ | 未开始 / 进行中 / 完成（掌握度 ★★☆ 以上） |

一道题可以有多个来源标记。

**做题顺序**：模块内按章节从上到下做，章节之间有依赖（比如锁依赖索引）。先做完所有 P0，再回头做 P1、P2。

## 一、MySQL → [MySQL.md](MySQL.md)

简历：死锁排查、SKIP LOCKED 认领、流水唯一键、条件状态迁移、Canal 订阅 binlog；技能栏写了"索引、MVCC、锁、隔离级别、死锁排查"。

### 基础

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P1 | 📚 | MySQL-基础-01 | InnoDB 和 MyISAM 的区别，为什么默认用 InnoDB | — | [mysql-questions-01.md](../后端开发/数据库/MySQL/mysql-questions-01.md) |
| ⬜ | P1 | 📚 | MySQL-基础-02 | 一条 SQL 的执行过程：连接器、分析器、优化器、执行器 | — | [how-sql-executed-in-mysql.md](../后端开发/数据库/MySQL/how-sql-executed-in-mysql.md) |

### 索引

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| 🟡 | P0 | 🩹📄 | MySQL-索引-01 | 索引和数据库的关系：页、B+ 树，表本身就是一棵按主键组织的 B+ 树；为什么选 B+ 树 | 技能栏"索引" | [mysql-index.md](../后端开发/数据库/MySQL/mysql-index.md) |
| 🟡 | P0 | 🩹📄🔧 | MySQL-索引-02 | 聚簇索引和二级索引，回表，覆盖索引；主键为什么推荐自增；没定义主键时怎么办 | 技能栏"索引"；`RedisIdWorker` 订单号 | 同上 |
| 🟡 | P0 | 🩹📄🔧 | MySQL-索引-03 | 联合索引，最左前缀，索引下推 | `(channel_id, state, id)`、`(状态, 到期时间, id)` | 同上 |
| 🟡 | P0 | 🩹📄 | MySQL-索引-04 | 索引失效的常见场景，`EXPLAIN` 怎么看 | 技能栏"索引" | [mysql-index-invalidation.md](../后端开发/数据库/MySQL/mysql-index-invalidation.md)、[mysql-query-execution-plan.md](../后端开发/数据库/MySQL/mysql-query-execution-plan.md) |
| 🟡 | P0 | 🩹📄🔧 | MySQL-索引-05 | 唯一索引和普通索引的区别；用唯一键做幂等；索引的维护代价 | 流水唯一键、请求键 | [mysql-index.md](../后端开发/数据库/MySQL/mysql-index.md) |
| 🟡 | P0 | 🩹📄🔧 | MySQL-索引-06 | 索引和锁怎么连起来：行锁为什么加在索引上，各种查询各加什么锁；外键为什么依托索引，外键检查为什么加 S 锁 | 外键检查导致共享锁升级 | 同上；MySQL-锁-01 |

### 事务与 MVCC

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| 🟡 | P0 | 📄🔧 | MySQL-事务-01 | ACID；脏读、不可重复读、幻读；四种隔离级别；RR 怎么防幻读 | 认领事务从 RR 改成 RC | [transaction-isolation-level.md](../后端开发/数据库/MySQL/transaction-isolation-level.md) |
| ✅ | P0 | 📄🔧 | MySQL-事务-02 | MVCC 原理：隐藏列、undo log、ReadView；RC 和 RR 生成 ReadView 的时机；快照读和当前读 | 同上 | [innodb-implementation-of-mvcc.md](../后端开发/数据库/MySQL/innodb-implementation-of-mvcc.md) |

### 锁

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| 🟡 | P0 | 📄🔧 | MySQL-锁-01 | 行锁的种类，共享锁和排他锁，锁定读，`SKIP LOCKED` 和 `NOWAIT` | `SKIP LOCKED` 认领、`NOWAIT` 锁权益包；项目题库 Q2.2 | [mysql-questions-01.md](../后端开发/数据库/MySQL/mysql-questions-01.md)「MySQL 锁」 |
| 🟡 | P0 | 📄🔧 | MySQL-锁-02 | 死锁的成因和四个条件，InnoDB 怎么检测和处理，怎么排查，怎么规避 | 107 次死锁降到 0；项目题库 Q1.3 | 同上；MySQL 官方文档 |
| 🟡 | P0 | 📄🔧 | MySQL-锁-03 | 乐观锁和悲观锁；条件更新（`UPDATE ... WHERE state = ?`）实现状态机 | "条件状态迁移实现幂等结算" | [optimistic-lock-and-pessimistic-lock.md](../后端开发/Java/并发编程/optimistic-lock-and-pessimistic-lock.md) |

### 日志

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| 🟡 | P0 | 📄🔧 | MySQL-日志-01 | binlog、redo log、undo log 的作用；两阶段提交；刷盘策略 | Canal 订阅 binlog；Docker 磁盘 fsync 变慢拖慢建单 | [mysql-logs.md](../后端开发/数据库/MySQL/mysql-logs.md) |
| ⬜ | P1 | 🔧 | MySQL-日志-02 | binlog 的三种格式；主从复制的过程 | Canal 要求 ROW 格式 | 同上 |

### 优化

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P1 | 📚 | MySQL-优化-01 | 慢查询怎么定位和优化；深分页怎么优化 | — | [mysql-high-performance-optimization-specification-recommendations.md](../后端开发/数据库/MySQL/mysql-high-performance-optimization-specification-recommendations.md) |

---

## 二、Redis

简历：Lua 原子预占库存、单飞互斥锁防击穿、版本号防旧值回填、Redis 故障降级；技能栏写了"数据结构、Lua、缓存穿透/击穿/雪崩、分布式锁"。

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P0 | 📄🔧 | Redis-01 | Redis 为什么快，单线程模型，Lua 为什么是原子的，Lua 中途出错会怎样 | Lua 脚本原子预占库存 | [redis-questions-01.md](../后端开发/数据库/Redis/redis-questions-01.md) |
| ⬜ | P0 | 📄🔧 | Redis-02 | 缓存穿透、击穿、雪崩，各自的解决方案 | 多级缓存，单飞互斥锁，有界回源降级 | [redis-questions-02.md](../后端开发/数据库/Redis/redis-questions-02.md)、[cache-basics.md](../后端开发/数据库/Redis/cache-basics.md) |
| ⬜ | P0 | 📄🔧 | Redis-03 | 缓存和数据库一致性，三种读写策略，先删缓存还是先更新数据库 | 版本号防旧值回填，Outbox 异步失效，Canal 兜底 | [3-commonly-used-cache-read-and-write-strategies.md](../后端开发/数据库/Redis/3-commonly-used-cache-read-and-write-strategies.md) |
| ⬜ | P0 | 📄🔧 | Redis-04 | 分布式锁：SETNX、过期时间、误删、续期，Redisson | `SimpleRedisLock`，带 owner 校验 | [distributed-lock-implementations.md](../后端开发/分布式/distributed-lock-implementations.md) |
| ⬜ | P0 | 📄 | Redis-05 | 五种基本数据结构和底层实现，跳表 | 技能栏"数据结构" | [redis-data-structures-01.md](../后端开发/数据库/Redis/redis-data-structures-01.md)、[redis-skiplist.md](../后端开发/数据库/Redis/redis-skiplist.md) |
| ⬜ | P1 | 🔧 | Redis-06 | Stream 消费组、待确认列表，和 List、Pub/Sub 做队列的区别 | Stream 异步建单，`XCLAIM` 接管 | [redis-stream-mq.md](../后端开发/数据库/Redis/redis-stream-mq.md) |
| ⬜ | P1 | 🔧 | Redis-07 | RDB 和 AOF 持久化 | Redis 损坏后按数据库重建库存 | [redis-persistence.md](../后端开发/数据库/Redis/redis-persistence.md) |
| ⬜ | P1 | 🔧 | Redis-08 | 全局 ID 方案：自增、UUID、雪花算法、Redis 自增 | `RedisIdWorker` 生成订单号 | [distributed-id.md](../后端开发/分布式/distributed-id.md) |
| ⬜ | P2 | 📚 | Redis-09 | 主从、哨兵、集群 | — | [redis-cluster.md](../后端开发/数据库/Redis/redis-cluster.md) |

## 三、消息队列与分布式事务

简历：事务 Outbox 解决数据库和消息队列双写不一致，消费端 Inbox 去重，8 万条事件 0 死信；技能栏写了 RocketMQ。

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P0 | 📄🔧 | 分布式-01 | 分布式事务方案：2PC、TCC、本地消息表、事务消息；CAP 和 BASE | 事务 Outbox（本地消息表） | [distributed-transaction.md](../后端开发/分布式/distributed-transaction.md)、[cap-and-base-theorem.md](../后端开发/分布式/理论算法与协议/cap-and-base-theorem.md) |
| ⬜ | P0 | 📄🔧 | MQ-01 | 消息怎么保证不丢（生产、存储、消费三段） | Outbox → RocketMQ，租约中继，退避重试 | [message-queue-interview-questions.md](../后端开发/高性能/消息队列/message-queue-interview-questions.md)、[rocketmq-questions.md](../后端开发/高性能/消息队列/rocketmq-questions.md) |
| ⬜ | P0 | 📄🔧 | MQ-02 | 重复消费怎么处理，死信队列，消息积压怎么办 | Inbox 去重，幂等消费，0 死信 | 同上 |
| ⬜ | P0 | 📄 | MQ-03 | RocketMQ 架构（NameServer、Broker、Topic、队列），事务消息，顺序消息 | 技能栏 RocketMQ | [rocketmq-questions.md](../后端开发/高性能/消息队列/rocketmq-questions.md) |
| ⬜ | P2 | 🔧 | MQ-04 | Kafka 基本架构，为什么吞吐高 | Kafka 承载行为分析和热榜（简历没写） | [kafka-questions-01.md](../后端开发/高性能/消息队列/kafka-questions-01.md) |

（中间省略 Spring、集合与并发、JVM 三个模块）

## 七、计算机网络

简历：AIMD 自适应并发、429 时并发减半。

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P0 | 📄🔧 | 网络-01 | TCP 拥塞控制：慢启动、拥塞避免、快重传、快恢复；和流量控制的区别 | AIMD 自适应并发 | [tcp-reliability-guarantee.md](../计算机基础/计算机网络/tcp-reliability-guarantee.md) |
| ⬜ | P0 | 📄🔧 | 网络-02 | HTTP 常见状态码；超时、重试和幂等 | 上游 429 重排，超时转入核对 | [http-status-codes.md](../计算机基础/计算机网络/http-status-codes.md) |
| ⬜ | P1 | 📚 | 网络-03 | TCP 三次握手四次挥手，TIME_WAIT | — | [tcp-connection-and-disconnection.md](../计算机基础/计算机网络/tcp-connection-and-disconnection.md)、[tcp-time-wait.md](../计算机基础/计算机网络/tcp-time-wait.md) |
| ⬜ | P2 | 🔧 | 网络-04 | Cookie 和 Session，JWT，XSS 和 CSRF | 令牌放 HttpOnly Cookie，校验写请求来源 | [network-attack-means.md](../计算机基础/计算机网络/network-attack-means.md)、[advantages-and-disadvantages-of-jwt.md](../后端开发/系统设计/安全/advantages-and-disadvantages-of-jwt.md) |
| ⬜ | P2 | 🔧 | 网络-05 | HTTP 和 HTTPS，TLS 握手 | Nginx 反向代理，签名回调 | [http-vs-https.md](../计算机基础/计算机网络/http-vs-https.md) |

## 八、简历技能栏里写了、原计划排除的

每项准备 3～5 个常见问题就够了，不用深挖。

| 状态 | 级别 | 来源 | 题号 | 要掌握的内容 | 项目 / 简历关联 | 查哪里 |
|---|---|---|---|---|---|---|
| ⬜ | P1 | 📄 | 工具-01 | `#{}` 和 `${}` 的区别（SQL 注入），分页插件原理，一级缓存和二级缓存 | MyBatis-Plus | [MyBatis 目录](../后端开发/系统设计/常用框架/MyBatis/) |
| ⬜ | P1 | 📄 | 工具-02 | 镜像、容器、Compose 的概念，为什么容器比虚拟机轻 | Docker | [Docker 目录](../后端开发/开发工具/Docker/) |
| ⬜ | P1 | 📄 | 工具-03 | 常用命令：查进程、查端口、看日志、查 CPU 和内存 | Linux | 本仓库没有专门文档，做到时单独整理 |
| ⬜ | P2 | 📄 | 工具-04 | merge 和 rebase，常见冲突处理 | Git | [Git 目录](../后端开发/开发工具/Git/) |
