# 顾君豪

求职意向：**Java 后端开发实习（AI 应用方向）**  
2028 届 | 江苏大学 · 软件工程（本科） | 可实习：**每周 5 天，可连续 6 个月以上**  
17388087295 | z86838598@163.com | [github.com/GuJunhao123](https://github.com/GuJunhao123)

---

## 关于我

2028 届软件工程本科，主攻 **Java + AI 应用工程**，构建过多个从零到可运行的完整项目：多模型批量评测平台、NoCode 网页生成平台、TSB 故障诊断助手。关注异步任务拆分、并发处理、缓存限流与数据库访问，能够结合业务实现后端接口、模型接入和前端流式交互，把 LLM 的不可控性工程化。

- **Java 与后端开发**：掌握常用集合、面向对象与异常处理；熟悉 Spring Boot、Spring MVC、MyBatis-Flex，理解 IoC / AOP、本地事务及提交后回调；具备 CompletableFuture 异步编排、Semaphore 并发控制、Java 21 虚拟线程及进程 I/O 实践。
- **数据库与中间件**：熟悉 MySQL 表结构设计、联合索引与游标分页；使用 Redis 实现缓存与会话记忆，结合自定义注解、AOP 与 Redisson 实现接口限流；使用 RabbitMQ 拆分异步任务，了解消息持久化、预取与并发消费。
- **全栈与工程交付**：使用 Vue 3 + TypeScript 开发页面，具备接口设计与前后端联调实践；使用 Reactor / SSE 实现流式响应；使用 Git、Maven、Docker Compose、Nginx。
- **AI 集成与辅助开发**：使用 Spring AI / LangChain4j 集成大模型能力；了解 Prompt、Agent、RAG、工作流编排与工具调用、MCP 工具接入；长期使用 Cursor、Codex 等 AI 开发工具辅助编码与排错。

## 代表项目

### ModelBench ｜ 三位一体模型评测台

面向模型选型与 Prompt 调试，支持多模型流式对比、提示词实验与异步批量评测，记录回答、耗时、Token 及估算费用，并生成对比报告。

**技术栈：** Spring Boot · Spring AI · MyBatis-Flex · MySQL · Redis · RabbitMQ · Reactor

- **流式对比**：基于 Spring AI 为不同模型及 Prompt 变体创建独立响应流，通过 Flux.merge 合并为 SSE 输出；按变体索引隔离历史上下文，将单路调用异常转换为带模型及变体标识的错误事件，避免影响其他正常响应。
- **异步消费**：按"模型 × 提示词"拆分 RabbitMQ 子任务，在 Spring 本地事务提交后通过 afterCommit 投递持久化消息，避免消费者提前读取未提交任务；使用 SQL 原子累加维护并发消费进度，并通过 WebSocket 推送执行状态。
- **并发评分与报告**：使用 CompletableFuture 并行调用两个 AI 评委，将五维评价映射为结构化结果并过滤调用异常；聚合被测回答的耗时、Token 与估算费用，生成模型对比报告。
- **限流与错误适配**：基于自定义注解、Spring AOP 与 Redisson 实现用户维度限流，将接口方法标识纳入限流 Key；针对流式请求，将限流等业务异常转换为 SSE 错误事件，解决 JSON 错误响应与流式客户端不匹配的问题。

### WordFlow ｜ 语言网页编织平台

面向自然语言生成网页应用，支持 HTML、多文件及 Vue 工程生成，提供对话记录、源码保存、应用构建与部署功能。

**技术栈：** Spring Boot · LangChain4j · MyBatis-Flex · MySQL · Redis · Caffeine

- **工程生成**：采用门面统一 HTML、多文件及 Vue 工程生成入口，Vue 模式通过 LangChain4j 调用文件读写、修改与删除工具，支持工程生成及增量修改；将 TokenStream 的文本与工具执行回调转换为统一消息流，展示生成过程，并设置连续工具调用上限。
- **应用级记忆与恢复**：使用 MySQL 保存对话历史，按应用 ID 过滤、创建时间游标倒序分页，配套设计（appId, createTime）联合索引；为各应用建立 Redis 对话记忆窗口，初始化时恢复最近历史，承接多轮对话上下文；通过 Caffeine 按应用与生成类型缓存 AI 服务实例，减少重复初始化。
- **工程构建与应用交付**：在 Vue 生成完成后异步执行工程构建，使用 ProcessBuilder 调用 npm，并行读取标准输出与错误输出，设置超时终止及依赖安装重试；部署前校验应用归属，将源码或 Vue 构建产物复制至部署目录，更新部署信息并返回访问地址。

### ContextFlow ｜ 故障诊断 Agent

基于技术服务通报（TSB）构建故障诊断辅助应用，本人负责后端、检索与 Agent 编排。

**技术栈：** Spring Boot · LangChain4j · LangGraph4j · PostgreSQL（pgvector）

- **检索模块**：基于 pgvector 构建向量召回 pipeline，保留文档表头、TSB 编号与页码以支持溯源，叠加车型元数据过滤与领域同义词扩展（如"异响→敲击声"）提升术语匹配。
- **工作流编排**：基于 LangGraph4j 实现"信息检查—检索—证据判断—建议生成"，通过条件边处理追问和证据不足兜底，设置执行步数与历史 Token 预算。

## 技术能力

| 方向 | 技术与实践 |
| --- | --- |
| Java 后端 | Spring Boot、Spring MVC、MyBatis-Flex；IoC / AOP、本地事务、CompletableFuture、Semaphore、Java 21 虚拟线程 |
| 数据库与中间件 | MySQL 表结构设计、联合索引、游标分页；Redis 缓存与会话记忆、Redisson 限流；RabbitMQ 异步任务拆分 |
| 全栈与工程交付 | Vue 3、TypeScript；Reactor、SSE、WebSocket；Git、Maven、Docker Compose、Nginx |
| AI 集成 | Spring AI、LangChain4j；Prompt、Agent、RAG、工作流编排、工具调用、MCP |

## 教育与竞赛

**江苏大学 · 软件工程 · 本科** ｜ 2024.09 – 2028.06

- GPA **4.0 / 5.0**（专业排名 **5 / 117，前 4%**），多次获校级一等奖学金。
- 主修课程：数据结构、操作系统、计算机网络、数据库系统原理、机器学习基础。
- **中国机器人及人工智能创新赛 · 国家二等奖（2026）** —— 参赛 800 支队伍；本人负责医学影像大模型的接入，基于 CUDA 实现推理加速，推理耗时降低为 1/3。

## 联系我

欢迎交流 Java 后端、AI 应用工程与模型评测，也欢迎相关实习机会。

- 邮箱：[z86838598@163.com](mailto:z86838598@163.com)
- GitHub：[GuJunhao123](https://github.com/GuJunhao123)
