# Awesome Vibe Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<p align="center">
  <strong>English</strong> • <a href="./README.zh-CN.md">简体中文</a> • <a href="./README.ja.md">日本語</a> • <a href="./README.es.md">Español</a>
</p>

<p align="center">
  <sub>The English version is the source of truth. Translations may lag slightly behind.</sub>
</p>

> A curated list of tools, frameworks, and resources for **vibe research** - the discipline of designing research environments, agent workflows, compute loops, and review systems so humans and AI agents can collaborate on literature, experiments, and reporting at scale.

## What is Vibe Research?

Vibe Coding showed that developers can express intent while AI handles more of the implementation.

**Vibe Research** applies the same idea to research work:

- Humans define the problem, scope, standards, constraints, and decision criteria.
- AI agents search literature, map prior work, propose questions, run experiments, summarize results, and draft reports.
- Humans remain responsible for steering, approval, interpretation, and final judgment.

The hard part is rarely the model alone. The real bottlenecks are coordination, fragmented context, manual handoffs, idle compute, broken continuity between literature review and experimentation, and the lack of a shared system where humans and agents can see the same research state.

## Core Principles

Borrowing from agent harness engineering and adapting it to research:

1. **Humans steer, agents execute** - researchers own direction, agents own throughput.
2. **Research context is the system of record** - papers, notes, experiment status, reports, and code should be inspectable in one stack.
3. **Research is iterative, not linear** - strong systems support branching questions, loops, retries, and parallel work.
4. **Approval gates matter** - autonomous proposal is useful; autonomous acceptance is dangerous.
5. **Observability matters** - if you cannot inspect search traces, experiment progress, and outputs, you cannot trust the workflow.
6. **Compute is part of the workflow** - GPU queues, clusters, budgets, and execution status should not live outside the research system.
7. **Agent legibility is a feature** - workflows, prompts, tools, and artifacts should be easy for the next human or agent to pick up.
8. **Context continuity beats prompt cleverness** - the best systems keep state across literature review, planning, execution, and reporting.

## Contents

- [What is Vibe Research?](#what-is-vibe-research)
- [Core Principles](#core-principles)
- [Full Lifecycle Platforms](#full-lifecycle-platforms)
- [Agent Orchestrators](#agent-orchestrators)
- [Experiment & Workflow Runners](#experiment--workflow-runners)
- [Agent Runtimes](#agent-runtimes)
- [Coding & Lab Agents](#coding--lab-agents)
- [Literature & Knowledge Systems](#literature--knowledge-systems)
- [Reproducibility & Experiment Ops](#reproducibility--experiment-ops)
- [Research Writing & Report Generation](#research-writing--report-generation)
- [RAG & Knowledge Infrastructure](#rag--knowledge-infrastructure)
- [Standards & Protocols](#standards--protocols)
- [Methodologies & Workflows](#methodologies--workflows)
- [Reference & Knowledge](#reference--knowledge)
- [Contributing](#contributing)

## Full Lifecycle Platforms

Platforms that span a meaningful portion of the research lifecycle: literature discovery, question formation, experiment orchestration, reporting, and human review.

- [Synapse](https://github.com/Vincentwei1021/Synapse) - **Recommended starting point.** A research orchestration platform built specifically for human researchers and AI agents. It covers literature review, research question formulation, experiment execution, and report generation, with built-in agent management, compute orchestration, real-time observability, an autonomous loop, and 60+ MCP tools. If you only evaluate one platform for `vibe research`, start here.
- [Denario](https://github.com/AstroPilot-AI/Denario) - A modular multi-agent system for scientific research assistance. More paper-oriented than Synapse, with a stronger emphasis on pushing from idea to method to results to research artifact.
- [OpenAGS](https://github.com/openags/OpenAGS) - Formerly Auto-Research. An ambitious open-ended effort around autonomous generalist scientist systems across literature, experiment, writing, and robotics. More exploratory than production-ready, but important for the direction of the category.

## Agent Orchestrators

These tools help structure complex agent workflows, split responsibilities across roles, and keep research tasks legible as they move from search to synthesis to execution.

- [LangGraph](https://github.com/langchain-ai/langgraph) - Graph-based framework for resilient language agents. Useful when research workflows have explicit stages, checkpoints, retries, and human approval steps.
- [Deep Agents](https://github.com/langchain-ai/deepagents) - Agent harness built on LangChain and LangGraph, with planning, filesystem access, and subagent spawning. A good fit for research stacks that need progressive disclosure and recursive task decomposition.
- [AutoGen](https://github.com/microsoft/autogen) - Microsoft's framework for agentic AI. Helpful when you want role-specialized research agents such as scout, critic, experimenter, and writer.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Framework for orchestrating role-playing autonomous agents. Well-suited to research flows where different agents own literature review, benchmark design, implementation, and write-up.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - Agent and workflow framework with strong connector support. Useful if your research stack needs to integrate enterprise systems, memory, and multiple model backends.
- [cmbagent](https://github.com/CMBAgents/cmbagent) - Multi-agent research system powered by AG2. Especially relevant when you want domain-oriented scientific agents rather than only generic planning abstractions.
- [GPT Researcher](https://github.com/assafelovic/gpt-researcher) - Autonomous agent for deep research across web and local data. A good reference point for report-oriented research agents that plan, gather, filter, and synthesize.
- [DeerFlow](https://github.com/bytedance/deer-flow) - Long-horizon super-agent harness with sandboxes, memories, tools, skills, and subagents. Useful when research tasks span browsing, coding, and artifact generation over long sessions.
- [OpenScholar](https://github.com/AkariAsai/OpenScholar) - Retrieval-augmented system for scientific literature synthesis. Especially relevant for grounded, citation-heavy responses over academic corpora.
- [PaperQA2](https://github.com/Future-House/paper-qa) - High-accuracy literature agent for answering questions from scientific documents with citations. One of the strongest building blocks for paper-grounded research workflows.
- [RD-Agent](https://github.com/microsoft/RD-Agent) - Microsoft's R&D automation framework for hypothesis iteration, code writing, experiment execution, and refinement. A strong bridge between software agents and research agents.
- [AutoRA](https://github.com/AutoResearch/autora) - Automated Research Assistant for closed-loop scientific discovery. Particularly relevant for empirical workflows that iterate between modeling, experiment design, and data collection.

## Experiment & Workflow Runners

Once a research workflow leaves the chat window and starts touching jobs, clusters, datasets, or scheduled pipelines, these tools become part of the harness.

- [Metaflow](https://github.com/Netflix/metaflow) - Build, manage, and deploy AI/ML systems. Strong choice when experiments need lineage, resumability, and a clean path from notebook prototype to recurring workflow.
- [Dagster](https://github.com/dagster-io/dagster) - Asset-oriented orchestration platform with strong observability. Useful when research outputs become reusable data assets, evaluation sets, or recurring pipelines.
- [Prefect](https://github.com/PrefectHQ/prefect) - Python-native workflow orchestration framework for resilient pipelines and scheduled jobs. A practical middle ground for agent-triggered research jobs.
- [SkyPilot](https://github.com/skypilot-org/skypilot) - Unified interface for running AI workloads across Kubernetes, Slurm, public cloud, and on-prem infrastructure. Very relevant for GPU-heavy vibe research.
- [Modal](https://modal.com/) - Managed compute platform for batch jobs, agents, and data workloads without owning the full infrastructure stack. Great for small teams that want fast iteration over research code.
- [Ray](https://github.com/ray-project/ray) - AI compute engine and distributed runtime. Useful for parallel search, training, simulation, evaluation sweeps, and high-throughput experiment execution.
- [ClearML](https://github.com/clearml/clearml) - Open-source platform covering experiment management, pipelines, scheduling, and remote execution. Helpful when vibe research needs a more integrated ops layer.
- [TruLens](https://github.com/truera/trulens) - Evaluation and tracking for LLM experiments and AI agents. Especially useful when you need to measure the quality of research-agent outputs and RAG pipelines.

## Agent Runtimes

Runtimes keep agents alive across sessions, channels, and long-running tasks. In research settings, that matters because useful work spans days, not just one prompt.

- [OpenClaw](https://github.com/openclaw/openclaw) - Persistent agent runtime with skills, sub-agent spawning, and multi-channel session management. A strong fit when research agents need to stay available across messaging, planning, and execution surfaces.

## Coding & Lab Agents

Even research-heavy teams still spend a large amount of time writing experiment code, glue code, evaluation code, and analysis scripts. These are the execution layer for that work.

- [Codex](https://github.com/openai/codex) - Lightweight coding agent that runs in the terminal. Useful for experiment code, data scripts, automation, and repo-grounded lab tasks.
- [Claude Code](https://code.claude.com/) - Strong repo-grounded coding agent with skill files, terminal tooling, and increasingly mature multi-agent patterns. Pairs well with research repos that need persistent conventions.
- [OpenHands](https://github.com/OpenHands/OpenHands) - AI-driven development platform that can operate inside sandboxed environments. Helpful when research plans need to become concrete code changes or runnable prototypes.
- [Aider](https://github.com/Aider-AI/aider) - Lightweight AI pair programming in the terminal. Great for smaller research repos, one-off analyses, and iterative experiment hacking.

## Literature & Knowledge Systems

Research agents are only as good as the corpora and context systems behind them. These tools help build that layer.

- [PapersGPT for Zotero](https://github.com/papersgpt/papersgpt-for-zotero) - Zotero AI and MCP plugin for chatting with PDFs, generating summaries, and automating literature review directly inside a paper library.
- [Zotero](https://www.zotero.org/) - Still the most practical system of record for personal and team paper collections. Many vibe research stacks should treat Zotero as the canonical bibliography layer.
- [Semantic Scholar API](https://www.semanticscholar.org/product/api) - Useful API for paper search, metadata retrieval, citation neighborhood lookup, and related-work discovery.
- [OpenAlex](https://docs.openalex.org/) - Open scholarly graph and API for works, authors, institutions, venues, and citations. Very strong default source for reproducible research metadata pipelines.
- [Connected Papers](https://www.connectedpapers.com/) - Visual graph for exploring adjacent work and citation neighborhoods. Good for quickly expanding a seed paper into a landscape map.
- [Elicit](https://elicit.com/) - Research assistant focused on literature review and evidence extraction. Helpful for early-phase synthesis and question refinement.
- [Research Rabbit](https://www.researchrabbit.ai/) - Literature discovery system that builds collections, explores citation neighborhoods, and recommends adjacent work over time.
- [Litmaps](https://www.litmaps.com/) - Dynamic literature mapping for tracking citation networks and newly emerging papers around a seed set.
- [Inciteful](https://inciteful.xyz/) - Literature graph exploration tools for discovery from seed papers and for finding connections across bodies of work.
- [Paperpile](https://paperpile.com/) - Reference management system with good collaborative ergonomics and strong Google Docs or Word workflows for research teams.
- [AgentSLR](https://github.com/OxRML/AgentSLR) - Agentic system for systematic literature reviews. A good fit when the workflow needs search, screening, extraction, and synthesis rather than only ad hoc browsing.
- [arXiv](https://arxiv.org/) - Core preprint corpus for fast-moving fields. Essential if agents need to track the frontier rather than only published papers.
- [OpenReview](https://openreview.net/) - Important source of peer review context, workshop papers, and discussion threads in ML-adjacent fields.
- [Papers with Code](https://paperswithcode.com/) - Connects papers to code, tasks, datasets, and benchmarks. Very useful when turning literature review into reproducible experimentation.

## Reproducibility & Experiment Ops

Research quality depends on being able to rerun, compare, inspect, and hand off work cleanly.

- [MLflow](https://github.com/mlflow/mlflow) - Open-source AI engineering platform for experiments, evaluation, monitoring, and model or app lifecycle management.
- [Weights & Biases](https://wandb.ai/site) - Popular platform for experiment tracking, dashboards, artifacts, and sweeps. Strong choice when a team needs shared visibility across many runs.
- [DVC](https://github.com/treeverse/dvc) - Data versioning and ML experiments for Git-based workflows. Useful when datasets, artifacts, and metrics need to travel with the repo.
- [JupyterLab](https://github.com/jupyterlab/jupyterlab) - The standard computational environment for exploratory analysis, quick experiment iteration, and interactive reporting.
- [Marimo](https://github.com/marimo-team/marimo) - Reactive notebook stored as pure Python rather than JSON. Particularly friendly to agent workflows because notebooks diff cleanly and can execute like scripts or apps.

## Research Writing & Report Generation

Research does not end at a successful run. These tools help turn notes, citations, and results into readable outputs that humans can review and publish.

- [Typst](https://github.com/typst/typst) - Modern typesetting system with cleaner syntax and faster iteration than traditional LaTeX. A strong option for agent-assisted research writing.
- [Overleaf](https://www.overleaf.com/) - Collaborative LaTeX editor that remains the default writing surface for many academic teams.
- [STORM](https://github.com/stanford-oval/storm) - Stanford's citation-grounded report generation system for researching a topic and producing a long-form article. Useful as a reference for structured synthesis pipelines.

## RAG & Knowledge Infrastructure

These tools help turn paper libraries, notes, and web corpora into queryable knowledge systems that research agents can actually use.

- [LlamaIndex](https://github.com/run-llama/llama_index) - Widely used framework for ingestion, indexing, retrieval, and document agents. Useful for building paper-grounded research assistants.
- [Firecrawl](https://github.com/firecrawl/firecrawl) - Web data API that converts sites into clean, LLM-friendly content. Helpful for large-scale research collection beyond PDFs.
- [Jina Reader](https://github.com/jina-ai/reader) - Lightweight way to turn arbitrary URLs into clean markdown for downstream agent consumption.

## Standards & Protocols

Research harnesses become much more reusable when tools, agents, and repositories can speak a shared language.

- [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) - Open standard for connecting models to external tools and data. Increasingly central for research agents that need live literature, file, and compute access.
- [ACP (Agent Communication Protocol)](https://agentcommunicationprotocol.dev/) - Open protocol for communication between agents and harnesses. Relevant when research systems need multiple specialized agents to coordinate cleanly.
- [agents.md](https://agents.md/) - Open standard for project-level agent instructions. Helpful for making research repo conventions explicit and portable.
- [AGENTS.md](https://openai.com/index/introducing-agents-md/) - OpenAI's repository-level convention for agent instructions. Good for codifying research repo structure, evaluation steps, and tool expectations.
- [Semantic Scholar API](https://api.semanticscholar.org/) - Programmatic access to academic paper search, metadata, and citation relationships. One of the most practical APIs for research-agent backends.
- [arXiv API](https://info.arxiv.org/help/api/) - Access to arXiv preprints for discovery and retrieval workflows in fast-moving fields.
- [CrossRef API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI-centric metadata infrastructure for bibliographic enrichment, reference completion, and citation workflows.

### Research-Focused MCP Servers

- [Zotero MCP](https://github.com/cookjohn/zotero-mcp) - MCP bridge for letting AI assistants interact directly with a Zotero library.
- [ScholarMCP](https://github.com/lstudlo/ScholarMCP) - Academic research MCP server spanning literature search, PDF ingestion, and citation management.
- [OpenAlex Research MCP](https://github.com/oksure/openalex-research-mcp) - MCP server for scholarly search, citation analysis, trend discovery, and collaboration mapping via OpenAlex.
- [arXiv MCP Server](https://github.com/anuj0456/arxiv-mcp-server) - MCP server for searching, analyzing, and exporting arXiv papers.
- [Unpaywall MCP](https://github.com/ElliotPadfield/unpaywall-mcp) - MCP server for DOI metadata and open-access PDF retrieval via Unpaywall.

## Methodologies & Workflows

These references are useful because `vibe research` is not just "let an LLM browse the web." It is a workflow design problem.

- [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) - AWS's workflow implementation of AI-DLC. Even though it comes from software delivery, the structure maps cleanly to research loops with explicit phases, artifacts, and review points.
- [AI-Driven Development Lifecycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) - A methodology reference for human-in-the-loop agent systems with clear boundaries between understanding, planning, and execution.
- [Harness Engineering: Leveraging Codex in an Agent-First World](https://openai.com/index/harness-engineering/) - Important framing for why environment design, repository structure, feedback loops, and mechanical enforcement matter more than prompt cleverness.
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - A strong reference for keeping agent systems simple, composable, and grounded in real tasks.

## Reference & Knowledge

### Research Systems

- [The AI Scientist](https://github.com/SakanaAI/AI-Scientist) - Sakana AI's influential system for fully automated open-ended scientific discovery. Important as a direction-setting reference, even if your own stack keeps humans more tightly in the loop.
- [The AI Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - Follow-up work focused on workshop-level automated scientific discovery via agentic tree search. Useful for thinking about deeper search over research ideas and experiment branches.
- [Deep Research Agent](https://github.com/tarun7r/deep-research-agent) - A production-oriented example of how citation-backed multi-agent research can be packaged as a runnable system rather than just a paper idea.

### General Harness Reading

- [Building an AI-Native Engineering Team](https://developers.openai.com/codex/guides/build-ai-native-engineering-team/) - Useful for teams reorganizing around agents, even outside software engineering.
- [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - Practical breakdown of state, tool execution, feedback loops, and enforceable constraints in agent systems.

### Curated Lists

- [Awesome Deep Research Agent](https://github.com/ai-agents-2030/awesome-deep-research-agent) - Curated collection of deep research agent papers, systems, and benchmarks.
- [Vibe Coding for Research](https://github.com/dlab-berkeley/Vibe-Coding-for-Research) - Practical introduction to applying modern AI tooling to research workflows.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a PR.

## License

[CC0 1.0](./LICENSE)
