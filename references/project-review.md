# 项目审查：方法和信号清单

目标：把用户的项目从"简历上的几句话"变成一份**有代码依据的项目画像**，用来定优先级、选考核场景、出拷打题。

## 审查顺序

1. **先看全貌**：README、架构文档、`pom.xml` / `build.gradle` 的依赖、`application.yml`、数据库迁移脚本（建表语句和索引）、`resources` 下的脚本（Lua、SQL）。用户有项目面试题库或设计文档，也一起读。
2. **再按项目经历的 bullet 逐句找代码**：每一条 bullet 里的技术点和数字，都要在代码里找到对应的实现。找不到就记为"简历写了、代码里没找到"，交给用户决定怎么处理（见 SKILL.md 第 1 步）。数字也要找依据，比如压测脚本、压测记录、日志。
3. **技能栏只核对、不展开**：技能栏里的每一项，看看项目 bullet 或代码里有没有出现。出现了就并入对应条目；没出现的，在画像里合成一行备注，不单独拆解，也不据此定优先级。
4. **最后按信号清单扫一遍**：用下表的关键词在代码里搜，找出简历没写、但面试官看代码或追问时可能问到的点。
5. 项目较小（几十个类）时，核心业务类建议整篇读完，很多真正的 bug 只有通读才看得出来；项目很大时不必逐个文件读，但**每一条写进画像的结论都要打开代码确认过**，不能只凭搜索命中就下结论。

## 信号清单（关键词 → 题库题）

| 搜什么 | 看什么 | 对应题库 |
|---|---|---|
| `ThreadPoolExecutor`、`Executors.new`、`ThreadPoolTaskExecutor` | 核心数、队列类型和容量、拒绝策略、线程工厂、是否守护线程、有没有监控 | 并发-线程池-01、02 |
| `ThreadLocal`、`TransmittableThreadLocal` | 存什么、在哪里 `remove`、会不会跨线程 | 并发-工具-01 |
| `volatile`、`Atomic`、`LongAdder` | 用来做什么（停止标志、计数、版本号） | 并发-JMM-02、并发-工具-02 |
| `synchronized`、`ReentrantLock`、`Semaphore`、`CountDownLatch` | 锁的范围、为什么选这种 | 并发-锁-02、03、04 |
| `CompletableFuture`、`@Async`、虚拟线程 | 异步编排、用的哪个线程池 | 并发-异步-01、Spring-Boot-03、并发-虚拟线程-01 |
| `@Transactional`、`TransactionSynchronization` | 传播行为、事务里有没有远程调用、提交后回调 | Spring-事务-01 |
| 迁移脚本里的 `INDEX`、`UNIQUE`、`PRIMARY KEY` | 联合索引列顺序、唯一键做幂等、主键生成方式 | MySQL-索引-01～06 |
| `FOR UPDATE`、`SKIP LOCKED`、`NOWAIT`、`UPDATE ... WHERE state =` | 锁定读、条件更新、状态机 | MySQL-锁-01～03（`SKIP LOCKED` 等追加为 🔧） |
| `isolation`、`READ_COMMITTED` | 隔离级别的选择 | MySQL-事务-01、02 |
| `.lua`、`DefaultRedisScript` | 每个脚本保证了什么原子性 | Redis-基础-01 |
| `SETNX`、`setIfAbsent`、`unlock`、`Redisson` | 锁的 value、过期时间、释放方式、续期 | Redis-应用-01 |
| `SETBIT`、`PFADD`、`GEOADD`、`ZADD`、`HSET`、`XADD` | 用了哪些数据结构、为什么 | Redis-数据结构-01、02，Redis-应用-02 |
| `EXPIRE`、`TTL`、`maxmemory` | 过期策略、淘汰策略 | Redis-内存-01 |
| `Caffeine`、`Guava Cache`、`@Cacheable` | 多级缓存、失效方式、一致性 | Redis-缓存-01、02 |
| `RocketMQ`、`Kafka`、`RabbitMQ`、Outbox 表 | 发送方式、消费幂等、重试与死信、顺序 | MQ 全模块、分布式-事务-01 |
| `Canal`、binlog | 增量订阅、缓存兜底 | MySQL-日志-01、02，Redis-缓存-02 |
| `@Scheduled`、XXL-Job、Quartz | 定时任务的线程模型、多实例下会不会重复执行 | Spring-Boot-03、设计-业务-01 |
| `RestTemplate`、`WebClient`、`HttpClient`、`Feign` | 超时、重试、幂等 | 网络-HTTP-01、高可用-调用-01、02 |
| `rate`、`limit`、`Sentinel`、`Resilience4j` | 限流算法、降级熔断 | 高可用-流量-01、02 |
| `JWT`、`Session`、`Spring Security`、`Cookie` | 认证方式、令牌存储 | 网络-HTTP-04、设计-安全-01 |
| `Dockerfile`、`docker-compose`、JVM 参数 | 容器资源限制、`-Xmx` | 工具-Docker-01、JVM-调优-01 |

## 项目画像的格式（`01-项目画像.md`）

```markdown
# 项目画像

- 审查日期：
- 简历：（路径）
- 项目：（路径 / 描述；没有代码的写"未对照实现"）

- 用户对"简历有、代码没有"的决定：（改简历 / 补实现，逐项写）

## 项目经历 bullet 拆解

| 简历原话 | 技术点 | 数字及依据 | 代码位置 | 牵出的题 |
|---|---|---|---|---|

## 技能栏核对

（一行备注：哪些项在项目里出现了、已并入上表；哪些只在技能栏出现。）

## 代码里有、简历没写的

| 技术点 | 代码里的事实（文件:行） | 牵出的题 |
|---|---|---|

## 对质点（出拷打题的素材）

| 类型 | 内容 | 用在哪道题 |
|---|---|---|
| 资料与代码冲突 | 例：JavaGuide 不推荐 `FixedThreadPool`，`XxxScheduler` 第 39 行用了 | 并发-线程池-02 |
| 简历有、代码没找到 | | |
| 旧笔记已过时 | | |

## 待追加的 🔧 题（题库里没有）

| 建议题号 | 内容 | 资料 |
|---|---|---|
```
