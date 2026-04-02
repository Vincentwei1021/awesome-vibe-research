# Awesome Vibe Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<p align="center">
  <a href="./README.md">English</a> • <strong>简体中文</strong> • <a href="./README.ja.md">日本語</a> • <a href="./README.es.md">Español</a>
</p>

<p align="center">
  <sub>英文版为主版本，其余翻译可能会有少量滞后。</sub>
</p>

> 一个聚焦 **vibe research** 的精选资源列表。这里的 vibe research 指的是这样一种研究工作方式: 由人类定义方向、约束和评估标准, 由 AI agents 执行文献检索、实验推进、结果综合与报告生成, 再通过研究环境、工作流、算力与审阅机制把整套流程可靠地组织起来。

<a id="what-is-vibe-research"></a>
## 什么是 Vibe Research?

Vibe Coding 证明了开发者可以更多地表达意图, 再把越来越多的执行工作交给 AI。

**Vibe Research** 则把这个思路带到了研究场景中:

- 人类定义问题、范围、标准、约束与决策依据。
- AI agents 检索文献、梳理相关工作、提出研究问题、运行实验、总结结果并起草报告。
- 人类继续对研究方向、审批、解释与最终判断负责。

真正困难的部分通常不只是模型本身, 而是协作系统本身: 上下文分散、人工交接过多、算力空转、文献回顾与实验执行之间缺乏连续性, 以及人和 agent 无法共享同一份研究状态。

### Agent 自主性的三个阶段

随着信任和工具链的成熟, vibe research 自然会经历三个阶段:

| 阶段 | 角色定位 | Agent 做什么 | 人类负责什么 |
|------|---------|-------------|-------------|
| **阶段一: Agent 作为实习生** | 仅执行 | 执行人类设计好的实验。不提出 idea, 不提出研究问题——只在明确范围内提供可靠的执行吞吐。 | 问题定义、实验设计、结果解读、所有决策。 |
| **阶段二: Agent 作为研究员** | 在单个研究问题内独立工作 | 端到端地负责一个 research question。在 experiment 粒度完成自循环: 提出实验方案、执行、解读结果、迭代优化——全部限定在一个研究问题的边界内。 | 研究问题的提出、跨问题优先级排序、最终判断。 |
| **阶段三: Agent 作为研究负责人** | 整个项目的自主驱动 | 驱动整个 research project。自主构建研究问题、提出并验证假说、决定 accept 还是 reject hypothesis, 并规划研究方向。 | 战略性把控、伦理审查、发表决策。 |

目前大多数团队处于阶段一。Vibe research 工具的目标是让阶段二可靠运行, 让阶段三成为可能。

<a id="core-principles"></a>
## 核心原则

这里借鉴了 agent harness engineering 的思路, 并把它们改写成适用于研究场景的原则:

1. **Humans steer, agents execute** - 研究者负责方向, agents 负责吞吐。
2. **Research context is the system of record** - 论文、笔记、实验状态、报告和代码应当集中在一个可检查的系统中。
3. **Research is iterative, not linear** - 优秀系统应支持分支问题、循环推进、重试与并行研究。
4. **Approval gates matter** - 自动提出方案很有价值, 自动接受方案则风险很大。
5. **Observability matters** - 如果你看不到检索轨迹、实验进度和输出过程, 就无法真正信任结果。
6. **Compute is part of the workflow** - GPU 队列、集群、预算和运行状态不该游离于研究系统之外。
7. **Agent legibility is a feature** - 工作流、提示词、工具和产物都应便于下一个人或下一个 agent 接手。
8. **Context continuity beats prompt cleverness** - 最好的系统能在文献回顾、规划、执行和报告之间持续保留上下文。

<a id="contents"></a>
## 目录

- [什么是 Vibe Research?](#what-is-vibe-research)
- [核心原则](#core-principles)
- [全生命周期平台](#full-lifecycle-platforms)
- [Agent 编排框架](#agent-orchestrators)
- [实验与工作流运行器](#experiment--workflow-runners)
- [Agent 运行时](#agent-runtimes)
- [Coding 与 Lab Agents](#coding--lab-agents)
- [文献与知识系统](#literature--knowledge-systems)
- [可复现性与实验运维](#reproducibility--experiment-ops)
- [研究写作与报告生成](#research-writing--report-generation)
- [RAG 与知识基础设施](#rag--knowledge-infrastructure)
- [标准与协议](#standards--protocols)
- [方法论与工作流](#methodologies--workflows)
- [参考资料与知识](#reference--knowledge)
- [贡献](#contributing)

<a id="full-lifecycle-platforms"></a>
## 全生命周期平台

这类平台覆盖研究生命周期中的关键环节: 文献发现、问题形成、实验编排、报告生成与人工审阅。

- [Synapse](https://github.com/Vincentwei1021/Synapse) - **推荐作为首选入口。** 这是一个专门面向 human researchers 与 AI agents 协作的研究编排平台。它覆盖文献综述、研究问题形成、实验执行与报告生成, 并内置 agent 管理、算力编排、实时可观测性、自主循环以及 60+ MCP tools。如果你只打算评估一个 `vibe research` 平台, 建议从它开始。
- [Denario](https://github.com/AstroPilot-AI/Denario) - 面向 scientific research assistance 的模块化 multi-agent system。相较于 Synapse, 它更偏向论文产出导向, 更强调从 idea 到 method, 再到 results 与 research artifact 的推进。
- [OpenAGS](https://github.com/openags/OpenAGS) - 即原来的 Auto-Research。一个更具探索性的通用 scientist agent 方向, 试图覆盖文献、实验、写作乃至机器人等更完整的科研闭环。相比生产化系统更偏前沿探索, 但对理解这一类别的发展很有帮助。

<a id="agent-orchestrators"></a>
## Agent 编排框架

这些工具帮助你组织复杂的 agent 工作流, 将职责拆分给不同角色, 并让研究任务从检索到综合再到执行的路径更清晰。

- [LangGraph](https://github.com/langchain-ai/langgraph) - 基于图的 resilient language agent framework。适合有明确阶段、检查点、重试机制和人工审批节点的研究工作流。
- [Deep Agents](https://github.com/langchain-ai/deepagents) - 基于 LangChain 与 LangGraph 的 agent harness, 支持 planning、filesystem access 与 subagent spawning。很适合需要 progressive disclosure 与递归任务拆解的研究栈。
- [AutoGen](https://github.com/microsoft/autogen) - Microsoft 的 agentic AI framework。适合构建 scout、critic、experimenter、writer 这类角色分工明确的研究 agents。
- [CrewAI](https://github.com/crewAIInc/crewAI) - 面向角色协作的 multi-agent orchestration framework。适合把文献分析、benchmark 设计、实现与写作拆给不同 agents。
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - 具备较强 connector 能力的 agent 与 workflow framework。适合需要接入企业系统、记忆层和多模型后端的研究栈。
- [cmbagent](https://github.com/CMBAgents/cmbagent) - 基于 AG2 的 multi-agent research system。相比通用编排框架, 它更接近面向科学研究本身的 agent 体系。
- [GPT Researcher](https://github.com/assafelovic/gpt-researcher) - 面向 web 与本地数据的 autonomous deep research agent。很适合作为“检索-筛选-综合-成文”型研究 agent 的参考实现。
- [DeerFlow](https://github.com/bytedance/deer-flow) - 面向长时任务的 super-agent harness, 包含 sandboxes、memory、tools、skills 和 subagents。适合持续数十分钟到数小时的研究任务。
- [OpenScholar](https://github.com/AkariAsai/OpenScholar) - 面向 scientific literature synthesis 的 retrieval-augmented system。尤其适合需要 grounded、citation-heavy 输出的学术问答与总结场景。
- [PaperQA2](https://github.com/Future-House/paper-qa) - 针对 scientific documents 的高精度 citation-based QA agent。是 paper-grounded research workflow 中很强的基础组件。
- [RD-Agent](https://github.com/microsoft/RD-Agent) - Microsoft 的 R&D automation framework, 支持 hypothesis iteration、代码生成、实验执行与迭代 refinement, 是 software agents 与 research agents 之间的重要桥梁。
- [AutoRA](https://github.com/AutoResearch/autora) - 面向 closed-loop scientific discovery 的 Automated Research Assistant, 很适合需要在建模、实验设计与数据采集之间循环迭代的实证研究流程。

<a id="experiment--workflow-runners"></a>
## 实验与工作流运行器

当研究流程不再停留在聊天窗口, 而是开始真正调度任务、数据集、集群和定时管线时, 这些工具就成了研究 harness 的一部分。

- [Metaflow](https://github.com/Netflix/metaflow) - 用于构建、管理和部署 AI/ML systems。适合需要 lineage、可恢复执行以及从 notebook 原型平滑走向长期 workflow 的实验体系。
- [Dagster](https://github.com/dagster-io/dagster) - 以 assets 为中心的 orchestration platform, 具备很强的 observability。适合把研究输出沉淀为可复用 data assets、evaluation sets 或 recurring pipelines。
- [Prefect](https://github.com/PrefectHQ/prefect) - Python-native 的 workflow orchestration framework, 很适合作为 agent 触发型 research jobs 的务实选择。
- [SkyPilot](https://github.com/skypilot-org/skypilot) - 统一管理 Kubernetes、Slurm、公有云与本地基础设施上 AI workloads 的接口。对 GPU-heavy 的 vibe research 特别实用。
- [Modal](https://modal.com/) - 面向 batch jobs、agents 与 data workloads 的托管计算平台。对不想自己维护完整基础设施的小团队非常友好。
- [Ray](https://github.com/ray-project/ray) - AI compute engine 与 distributed runtime。适合并行检索、训练、仿真、评测 sweep 和高吞吐实验执行。
- [ClearML](https://github.com/clearml/clearml) - 覆盖 experiment management、pipelines、scheduling 与 remote execution 的开源平台。适合需要更完整 ops layer 的 vibe research 团队。
- [TruLens](https://github.com/truera/trulens) - 面向 LLM experiments 与 AI agents 的 evaluation 与 tracking。尤其适合评估 research agents 与 RAG pipelines 的输出质量。

<a id="agent-runtimes"></a>
## Agent 运行时

Runtimes 让 agents 能跨会话、跨渠道、跨长任务持续运行。对研究场景来说, 这很重要, 因为真正有价值的工作通常会跨越数天而不是一个 prompt。

- [OpenClaw](https://github.com/openclaw/openclaw) - 带 skills、sub-agent spawning 与 multi-channel session management 的 persistent agent runtime。适合需要在消息、规划与执行界面之间持续工作的 research agents。

<a id="coding--lab-agents"></a>
## Coding 与 Lab Agents

即使是研究团队, 依然会花大量时间写实验代码、胶水代码、评测代码与分析脚本。这些工具就是那一层的执行者。

- [Codex](https://github.com/openai/codex) - 运行在终端中的轻量 coding agent。适合实验代码、数据脚本、自动化和 repo-grounded 的实验室任务。
- [Claude Code](https://code.claude.com/) - 具备 skill files、terminal tooling 与逐渐成熟 multi-agent pattern 的强力 repo-grounded coding agent。很适合有稳定研究约定的代码仓库。
- [OpenHands](https://github.com/OpenHands/OpenHands) - 可在 sandboxed 环境中运行的 AI-driven development platform。适合把研究计划落成真实代码改动或可运行原型。
- [Aider](https://github.com/Aider-AI/aider) - 终端中的轻量 AI pair programming 工具。非常适合较小的研究仓库、一次性分析与快速试验。

<a id="literature--knowledge-systems"></a>
## 文献与知识系统

研究 agents 的上限, 很大程度上取决于它们背后的文献语料和知识系统。

- [PapersGPT for Zotero](https://github.com/papersgpt/papersgpt-for-zotero) - 一个 Zotero AI 与 MCP plugin, 可直接在论文库中完成 PDF 对话、总结与文献综述自动化。
- [Zotero](https://www.zotero.org/) - 依旧是个人与团队最务实的论文资料库系统。很多 vibe research stack 都应把它当作 canonical bibliography layer。
- [Semantic Scholar API](https://www.semanticscholar.org/product/api) - 很实用的论文搜索、metadata retrieval、citation neighborhood 与 related-work discovery API。
- [OpenAlex](https://docs.openalex.org/) - 开放的 scholarly graph 与 API, 覆盖 works、authors、institutions、venues 与 citations, 很适合搭建可复现的学术元数据管线。
- [Connected Papers](https://www.connectedpapers.com/) - 用图结构探索相邻工作与 citation neighborhood 的工具。很适合从一篇 seed paper 快速扩展出一个研究地图。
- [Elicit](https://elicit.com/) - 侧重文献综述与 evidence extraction 的 research assistant。对前期问题收敛和初步综合很有帮助。
- [Research Rabbit](https://www.researchrabbit.ai/) - 用于构建论文集合、探索 citation neighborhood 并持续发现相近工作的文献发现系统。
- [Litmaps](https://www.litmaps.com/) - 动态文献图谱工具, 适合围绕 seed set 跟踪 citation network 与新发表论文。
- [Inciteful](https://inciteful.xyz/) - 基于 seed papers 的 literature graph exploration 工具, 适合做发现与跨子领域连接分析。
- [Paperpile](https://paperpile.com/) - 在团队协作、Google Docs/Word 结合方面体验较好的参考文献管理系统。
- [AgentSLR](https://github.com/OxRML/AgentSLR) - 面向 systematic literature reviews 的 agentic system。适合需要 search、screening、extraction 与 synthesis 的规范化综述流程。
- [arXiv](https://arxiv.org/) - 快速演进领域中的核心 preprint corpus。若 agents 需要追踪前沿, 它几乎是必备数据源。
- [OpenReview](https://openreview.net/) - 提供 peer review 上下文、workshop papers 与讨论线程的重要来源, 在 ML 相关研究中尤其重要。
- [Papers with Code](https://paperswithcode.com/) - 把论文与代码实现、benchmarks、datasets 连接起来。对于从文献综述走向可复现实验非常关键。

<a id="reproducibility--experiment-ops"></a>
## 可复现性与实验运维

研究质量很大程度上取决于结果是否能够被重跑、对比、检查和顺利交接。

- [MLflow](https://github.com/mlflow/mlflow) - 开源 AI engineering platform, 覆盖实验、评测、监控以及模型或应用生命周期管理。
- [Weights & Biases](https://wandb.ai/site) - 常用的 experiment tracking、dashboard、artifacts 与 sweeps 平台。很适合多实验并行的团队可视化协作。
- [DVC](https://github.com/treeverse/dvc) - 面向 Git 工作流的数据版本管理与 ML experiments 工具。适合让 datasets、artifacts 与 metrics 跟随仓库一起演进。
- [JupyterLab](https://github.com/jupyterlab/jupyterlab) - 最标准的计算式分析环境, 适合探索性分析、快速实验与交互式报告。
- [Marimo](https://github.com/marimo-team/marimo) - 以纯 Python 文件形式存储的 reactive notebook。对 agent workflows 特别友好, 因为它更易 diff, 也能像脚本或应用一样执行。

<a id="research-writing--report-generation"></a>
## 研究写作与报告生成

研究工作不会在实验跑完时结束。这些工具帮助把笔记、引文和结果组织成可审阅、可发布的输出。

- [Typst](https://github.com/typst/typst) - 相比传统 LaTeX 语法更简洁、迭代更快的现代 typesetting system, 很适合 agent-assisted research writing。
- [Overleaf](https://www.overleaf.com/) - 支持多人协作的 LaTeX 编辑器, 仍然是很多学术团队的默认写作界面。
- [STORM](https://github.com/stanford-oval/storm) - Stanford 的 citation-grounded report generation system, 能围绕一个主题进行研究并生成长篇带引用文章, 很适合作为结构化综合流程的参考。

<a id="rag--knowledge-infrastructure"></a>
## RAG 与知识基础设施

这些工具帮助你把论文库、笔记和网页语料转成 research agents 真正可查询、可利用的知识系统。

- [LlamaIndex](https://github.com/run-llama/llama_index) - 常用的 ingestion、indexing、retrieval 与 document agent framework, 很适合构建 paper-grounded research assistants。
- [Firecrawl](https://github.com/firecrawl/firecrawl) - 可把网站转成干净、LLM-friendly 内容的 Web data API。适合 PDF 之外的大规模研究资料收集。
- [Jina Reader](https://github.com/jina-ai/reader) - 将任意 URL 轻量转换为干净 markdown 的工具, 便于 agent 后续消费。

<a id="standards--protocols"></a>
## 标准与协议

当工具、agents 和 repositories 能说同一种语言时, 研究 harness 才更容易复用与扩展。

- [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) - 连接模型与外部工具/数据的开放标准, 正在成为 research agents 接入文献、文件与算力的重要骨架。
- [ACP (Agent Communication Protocol)](https://agentcommunicationprotocol.dev/) - 面向 agents 与 harness 之间通信的开放协议, 适合多专长 research systems 的协作场景。
- [agents.md](https://agents.md/) - project-level agent instructions 的开放标准。适合显式描述研究仓库的工作方式和约定。
- [AGENTS.md](https://openai.com/index/introducing-agents-md/) - OpenAI 提出的 repository-level agent instructions 约定, 适合定义研究仓库结构、评测步骤与工具预期。
- [Semantic Scholar API](https://api.semanticscholar.org/) - 学术论文搜索、metadata 与 citation relationship 的程序化接口, 是 research-agent backend 中非常实用的一类 API。
- [arXiv API](https://info.arxiv.org/help/api/) - 用于发现与获取 arXiv preprints 的 API, 对快速演进领域尤其重要。
- [CrossRef API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - 围绕 DOI 的 metadata 基础设施, 适合 bibliographic enrichment、reference completion 与 citation workflow。

### 面向研究的 MCP Servers

- [Zotero MCP](https://github.com/cookjohn/zotero-mcp) - 让 AI assistants 直接操作 Zotero library 的 MCP bridge。
- [ScholarMCP](https://github.com/lstudlo/ScholarMCP) - 覆盖 literature search、PDF ingestion 与 citation management 的 academic research MCP server。
- [OpenAlex Research MCP](https://github.com/oksure/openalex-research-mcp) - 基于 OpenAlex 的 scholarly search、citation analysis、trend discovery 与 collaboration mapping MCP server。
- [arXiv MCP Server](https://github.com/anuj0456/arxiv-mcp-server) - 用于搜索、分析和导出 arXiv papers 的 MCP server。
- [Unpaywall MCP](https://github.com/ElliotPadfield/unpaywall-mcp) - 通过 Unpaywall 获取 DOI metadata 与 open-access PDFs 的 MCP server。

<a id="methodologies--workflows"></a>
## 方法论与工作流

这些参考很重要, 因为 `vibe research` 不是“让 LLM 上网搜一下”这么简单, 它本质上是一个 workflow design 问题。

- [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) - AWS 对 AI-DLC 的 workflow 实现。虽然最初来自软件交付, 但它非常适合映射到研究中的 phased loops、artifacts 与 review points。
- [AI-Driven Development Lifecycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) - 研究 human-in-the-loop agent systems 时非常有价值的方法论参考, 强调 understand、plan、execute 之间的边界。
- [Harness Engineering: Leveraging Codex in an Agent-First World](https://openai.com/index/harness-engineering/) - 解释为什么环境设计、仓库结构、反馈回路与机械化约束, 往往比 prompt 小技巧更关键。
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - 关于如何构建简单、可组合且贴近真实任务的 agent systems 的重要参考。

<a id="reference--knowledge"></a>
## 参考资料与知识

### 研究系统

- [The AI Scientist](https://github.com/SakanaAI/AI-Scientist) - Sakana AI 提出的 influential system, 目标是 fully automated open-ended scientific discovery。即便你的系统更强调 human-in-the-loop, 它依然是理解研究自动化上限的重要参考。
- [The AI Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - 聚焦 workshop-level automated scientific discovery 与 agentic tree search 的后续版本, 对理解“更深层研究分支搜索”很有帮助。
- [Deep Research Agent](https://github.com/tarun7r/deep-research-agent) - 一个 production-oriented 的例子, 展示 citation-backed multi-agent research system 如何被包装成可运行系统而不只是概念验证。

### 通用 Harness 阅读材料

- [Building an AI-Native Engineering Team](https://developers.openai.com/codex/guides/build-ai-native-engineering-team/) - 对想围绕 agents 重新组织团队的读者很有参考价值, 即便你的工作不只局限于软件工程。
- [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - 对 state、tool execution、feedback loops 与 enforceable constraints 的实用拆解。

### 精选列表

- [Awesome Deep Research Agent](https://github.com/ai-agents-2030/awesome-deep-research-agent) - 深度研究 agents、论文与 benchmarks 的精选列表。
- [Vibe Coding for Research](https://github.com/dlab-berkeley/Vibe-Coding-for-Research) - 一个将现代 AI 工具应用到研究工作流中的实用入门集合。

<a id="contributing"></a>
## 贡献

欢迎贡献。提交 PR 前, 请先阅读 [CONTRIBUTING.md](./CONTRIBUTING.md)。

## 许可证

[CC0 1.0](./LICENSE)
