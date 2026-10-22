# 顾君豪 · GuJunhao123

**AI Agent 开发 / Java AI 全栈 · 后端为主，专注 LLM 应用工程**

江苏大学 · 软件工程本科 · 2028 届  
寻找相关实习机会：每周可实习 **4 天**，可连续 **6 个月以上**。

[GitHub 主页](https://github.com/GuJunhao123) · [公开仓库](https://github.com/GuJunhao123?tab=repositories) · [邮件联系](mailto:z86838598@163.com)

---

## 关于我

我主要使用 Java 构建 LLM 应用，关注从模型接入、检索与工具调用，到效果评测和前端交互的完整链路。

- **Agent 与 RAG**：围绕车辆故障辅助排查，实践混合检索、条件路由、证据引用与工具调用边界。
- **模型评测**：围绕模型选型和 Prompt 调试，实践多路流式对比、异步批量评测与 LLM-as-a-Judge。
- **后端工程**：关注并发控制、异常隔离、事务一致性、超时与任务进度，让模型调用成为可观察、可控制的业务流程。

## 代表项目

### ContextFlow ｜ 新能源 TSB 诊断辅助 Agent

围绕技术服务通报（TSB）构建故障问答与辅助排查流程，重点解决“信息是否完整、资料是否相关、回答能否追溯”的问题。

**技术栈：** Spring Boot · LangGraph4j · PostgreSQL / pgvector · Apache Lucene

- **混合检索**：结合 BM25 与向量召回，使用 RRF 融合排序，并按车型、年份约束检索范围。
- **流程编排**：通过 StateGraph 串联信息检查、检索、证据判断、建议生成与引用校验；信息不足时追问，无匹配资料时返回明确状态。
- **可追溯性**：关联证据 ID、页码与原文片段，以 requestId 和节点耗时辅助排查检索、生成及工具错误。
- **可靠性**：使用参数校验、有界线程池、超时控制和受限纠正流程，区分无结果与调用失败。

> 公开演示使用合成资料；真实业务数据与演示数据分开说明，不将合成集成绩作为真实诊断效果。在线模型和向量检索需要配置相应服务，具体能力与验证范围以项目文档为准。

### ModelBench ｜ 多模型对比与场景化评测平台

面向模型选型与 Prompt 调试的个人全栈项目，通过 OpenRouter 接入多模型，留存回答、耗时、Token 与估算费用，为模型和提示词选择提供对比依据。

**技术栈：** Spring Boot · Spring AI · Reactor · RabbitMQ · Redis · MySQL · Vue 3 · TypeScript

- **流式对比**：为模型和 Prompt 变体创建独立响应流，通过 Reactor 合并为 SSE；单路失败转换为独立错误事件，前端分路展示结果。
- **上下文隔离**：按提示词变体隔离历史，支持同题多模型与同模型多提示词实验。
- **异步评测**：按“模型 × 场景提示词”拆分 RabbitMQ 子任务，在数据库事务提交后投递持久化消息；通过 SQL 原子自增维护进度，并用 WebSocket 推送。
- **双评委评分**：并行调用两个评委模型，进行五维结构化评分；过滤失败评委，保留有效评分、平均评级与评级标准差，结合耗时和估算费用比较结果。

### MCP Tool Server ｜ 面向 Agent 的自建工具集

为 ModelBench 提供评测数据查询与任务状态工具，实践模型应用与业务系统之间的标准化连接。

**技术栈：** Java · Spring AI MCP Server · TypeScript MCP SDK

- **协议接入**：使用 SDK 实现 stdio 与 Streamable HTTP transport，暴露 tools 和 resources，支持客户端运行时发现与调用。
- **业务工具**：封装“评测数据集查询”“批量任务状态”，接入 Agent 侧使用。
- **调用约束**：设计工具权限白名单、入参 Schema 校验，并针对提示词注入与工具滥用场景做拦截验证。

## 技术能力

| 方向        | 技术与实践                                                   |
| ----------- | ------------------------------------------------------------ |
| Java 后端   | Java 集合、JUC、线程池、CompletableFuture；Spring Boot、AOP、事务 |
| LLM 应用    | Spring AI、LangChain4j；流式调用、结构化输出、Function Calling、Prompt 对比 |
| Agent / RAG | LangGraph4j、pgvector、Lucene BM25、RRF、证据引用、固定集评测 |
| 数据与消息  | MySQL、PostgreSQL、Redis、Redisson、RabbitMQ                 |
| 实时交互    | Reactor、SSE、WebSocket；Vue 3、TypeScript                   |
| 开发与交付  | Git、Maven、Docker Compose、Nginx                            |

## 教育与竞赛

**江苏大学 · 软件工程 · 本科** ｜ 2024.09 – 2028.06

- GPA **4.0 / 5.0**，专业排名 **3 / 117（前 3%）**。
- 主修课程：数据结构、操作系统、计算机网络、数据库系统原理、机器学习基础。
- **中国机器人及人工智能创新赛 · 国家二等奖（2026）**，负责系统功能接入。

## 联系我

欢迎交流 Java AI 后端、Agent / RAG 工程与模型评测，也欢迎相关实习机会。

- 邮箱：[z86838598@163.com](mailto:z86838598@163.com)
- GitHub：[GuJunhao123](https://github.com/GuJunhao123)
