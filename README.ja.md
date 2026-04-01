# Awesome Vibe Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<p align="center">
  <a href="./README.md">English</a> • <a href="./README.zh-CN.md">简体中文</a> • <strong>日本語</strong> • <a href="./README.es.md">Español</a>
</p>

<p align="center">
  <sub>英語版を基準として更新しています。翻訳版は少し遅れる場合があります。</sub>
</p>

> **vibe research** のための厳選リソース集です。ここでいう vibe research とは、人間が方向性、制約、評価基準を定め、AI agents が文献調査、実験実行、結果の統合、レポート作成を進め、その全体を研究環境、ワークフロー、計算基盤、レビューの仕組みで支える研究スタイルを指します。

<a id="what-is-vibe-research"></a>
## Vibe Research とは?

Vibe Coding は、開発者が主に意図を示し、実行のより多くを AI に任せられることを示しました。

**Vibe Research** は、その考え方を研究ワークフローに持ち込んだものです。

- 人間が問題設定、スコープ、基準、制約、判断軸を定義する。
- AI agents が文献検索、関連研究の整理、研究課題の提案、実験実行、結果の要約、レポート草稿作成を行う。
- 人間は方向付け、承認、解釈、最終判断に責任を持つ。

難しいのはモデル単体ではなく、協調の設計そのものです。文脈の分断、手作業による引き継ぎ、遊休計算資源、文献レビューと実験の断絶、人間と agent が同じ研究状態を共有できないことが、実際のボトルネックになります。

<a id="core-principles"></a>
## 基本原則

agent harness engineering の考え方を研究向けに言い換えると、次のような原則になります。

1. **Humans steer, agents execute** - 研究者が方向を持ち、agents がスループットを担う。
2. **Research context is the system of record** - 論文、ノート、実験状態、レポート、コードは一つの検査可能なスタックに集約されるべき。
3. **Research is iterative, not linear** - 優れたシステムは分岐、ループ、再試行、並列実行を前提にする。
4. **Approval gates matter** - 自動提案は有用だが、自動承認は危険。
5. **Observability matters** - 検索経路、実験進行、出力の過程が見えなければ、結果を信頼できない。
6. **Compute is part of the workflow** - GPU キュー、クラスター、予算、実行状態は研究システムの外に置くべきではない。
7. **Agent legibility is a feature** - ワークフロー、プロンプト、ツール、成果物は次の人や次の agent が引き継ぎやすい形であるべき。
8. **Context continuity beats prompt cleverness** - 文献レビュー、計画、実行、報告のあいだで文脈が保たれることが重要。

<a id="contents"></a>
## 目次

- [Vibe Research とは?](#what-is-vibe-research)
- [基本原則](#core-principles)
- [フルライフサイクル・プラットフォーム](#full-lifecycle-platforms)
- [Agent Orchestrators](#agent-orchestrators)
- [実験とワークフロー実行基盤](#experiment--workflow-runners)
- [Agent Runtimes](#agent-runtimes)
- [Coding & Lab Agents](#coding--lab-agents)
- [文献・知識システム](#literature--knowledge-systems)
- [再現性と実験運用](#reproducibility--experiment-ops)
- [研究執筆とレポート生成](#research-writing--report-generation)
- [RAG と知識基盤](#rag--knowledge-infrastructure)
- [標準とプロトコル](#standards--protocols)
- [方法論とワークフロー](#methodologies--workflows)
- [参考資料と知識](#reference--knowledge)
- [Contributing](#contributing)

<a id="full-lifecycle-platforms"></a>
## フルライフサイクル・プラットフォーム

文献探索、研究課題形成、実験オーケストレーション、レポート生成、人間のレビューまで、研究ライフサイクルの主要部分をカバーするプラットフォームです。

- [Synapse](https://github.com/Vincentwei1021/Synapse) - **最初に評価する候補として推奨。** human researchers と AI agents の協働を前提に設計された研究オーケストレーション基盤です。文献レビュー、研究課題形成、実験実行、レポート生成をカバーし、agent 管理、計算資源のオーケストレーション、リアルタイム observability、自律ループ、60+ MCP tools を備えています。`vibe research` 向けに一つだけ見るなら、まずここから始める価値があります。
- [Denario](https://github.com/AstroPilot-AI/Denario) - scientific research assistance 向けの modular multi-agent system。Synapse よりも論文成果物寄りで、idea から method、results、research artifact へ進める流れをより強く意識しています。
- [OpenAGS](https://github.com/openags/OpenAGS) - 旧 Auto-Research。文献、実験、執筆、ロボティクスまで含むより広い scientist agent の方向性を探るプロジェクト。プロダクション志向というより探索的ですが、この分野の将来像を理解するうえで有益です。

<a id="agent-orchestrators"></a>
## Agent Orchestrators

複雑な agent ワークフローを整理し、役割を分担し、探索から統合、実行までを見通しやすくするためのツール群です。

- [LangGraph](https://github.com/langchain-ai/langgraph) - resilient language agents のための graph-based framework。研究ワークフローに明確な段階、チェックポイント、再試行、human approval がある場合に向いています。
- [Deep Agents](https://github.com/langchain-ai/deepagents) - LangChain と LangGraph 上の agent harness。planning、filesystem access、subagent spawning を備え、progressive disclosure と再帰的タスク分解が必要な研究スタックに適しています。
- [AutoGen](https://github.com/microsoft/autogen) - Microsoft の agentic AI framework。scout、critic、experimenter、writer のように役割分担した研究 agents を作りたいときに便利です。
- [CrewAI](https://github.com/crewAIInc/crewAI) - role-playing 型の multi-agent orchestration framework。文献分析、benchmark 設計、実装、執筆を別 agent に分ける構成に向いています。
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - connector が強い agent / workflow framework。企業システム、memory 層、複数モデル backend と統合した研究スタックに向いています。
- [cmbagent](https://github.com/CMBAgents/cmbagent) - AG2 ベースの multi-agent research system。一般的なオーケストレーションより、科学研究そのものに近い agent システムです。
- [GPT Researcher](https://github.com/assafelovic/gpt-researcher) - web とローカルデータを横断する autonomous deep research agent。調査、収集、絞り込み、統合、レポート生成型の agent を考えるうえで参考になります。
- [DeerFlow](https://github.com/bytedance/deer-flow) - sandboxes、memory、tools、skills、subagents を備えた long-horizon super-agent harness。長時間にわたる調査や生成タスクに適しています。
- [OpenScholar](https://github.com/AkariAsai/OpenScholar) - scientific literature synthesis 向けの retrieval-augmented system。引用付きで grounded な学術要約や回答に適しています。
- [PaperQA2](https://github.com/Future-House/paper-qa) - scientific documents に対する高精度の citation-based QA agent。paper-grounded research workflow の基盤として非常に有力です。
- [RD-Agent](https://github.com/microsoft/RD-Agent) - hypothesis iteration、コード生成、実験実行、refinement を行う Microsoft の R&D automation framework。software agents と research agents の橋渡しとして重要です。
- [AutoRA](https://github.com/AutoResearch/autora) - closed-loop scientific discovery のための Automated Research Assistant。モデリング、実験設計、データ収集を回す実証研究に向いています。

<a id="experiment--workflow-runners"></a>
## 実験とワークフロー実行基盤

研究がチャット内で完結せず、ジョブ、データセット、クラスター、定期パイプラインを実際に動かし始めると、これらのツールが harness の一部になります。

- [Metaflow](https://github.com/Netflix/metaflow) - AI/ML systems を構築・管理・運用するためのツール。lineage、再開可能性、notebook から継続運用への移行が必要な実験系に向いています。
- [Dagster](https://github.com/dagster-io/dagster) - asset-oriented な orchestration platform。研究成果を reusable data assets や evaluation sets として扱いたいときに便利です。
- [Prefect](https://github.com/PrefectHQ/prefect) - Python-native の workflow orchestration framework。agent 起点の research jobs に対して実用的な選択肢です。
- [SkyPilot](https://github.com/skypilot-org/skypilot) - Kubernetes、Slurm、public cloud、on-prem にまたがる AI workloads を統一的に扱うインターフェース。GPU-heavy な vibe research に特に有効です。
- [Modal](https://modal.com/) - batch jobs、agents、data workloads のための managed compute platform。フルな基盤運用を避けたい小規模チームに向いています。
- [Ray](https://github.com/ray-project/ray) - AI compute engine と distributed runtime。並列探索、学習、シミュレーション、評価 sweep、高スループット実行に向いています。
- [ClearML](https://github.com/clearml/clearml) - experiment management、pipelines、scheduling、remote execution をまとめて扱える open-source platform。より統合された ops layer が必要な研究チームに有用です。
- [TruLens](https://github.com/truera/trulens) - LLM experiments と AI agents の evaluation / tracking ツール。research agents や RAG pipelines の品質を測りたいときに重要です。

<a id="agent-runtimes"></a>
## Agent Runtimes

Runtimes は agents を複数セッション、複数チャネル、長時間タスクにまたがって生存させます。研究では価値ある作業が一回の prompt で終わらないため、特に重要です。

- [OpenClaw](https://github.com/openclaw/openclaw) - skills、sub-agent spawning、multi-channel session management を持つ persistent agent runtime。計画、実行、メッセージングをまたいで働く research agents に向いています。

<a id="coding--lab-agents"></a>
## Coding & Lab Agents

研究チームでも、実験コード、接着コード、評価コード、分析スクリプトを書く時間は多く残ります。これらはその実行レイヤーです。

- [Codex](https://github.com/openai/codex) - terminal 上で動く軽量 coding agent。実験コード、データスクリプト、自動化、repo-grounded なラボ作業に向いています。
- [Claude Code](https://code.claude.com/) - skill files、terminal tooling、成熟しつつある multi-agent pattern を持つ強力な repo-grounded coding agent。研究リポジトリの慣習を維持しやすいです。
- [OpenHands](https://github.com/OpenHands/OpenHands) - sandboxed 環境で動作できる AI-driven development platform。研究計画を実際のコード変更や動くプロトタイプに落とし込むのに向いています。
- [Aider](https://github.com/Aider-AI/aider) - terminal 上の軽量 AI pair programming ツール。小さめの研究 repo や短い解析作業に適しています。

<a id="literature--knowledge-systems"></a>
## 文献・知識システム

研究 agents の質は、背後にある文献コーパスと知識システムに大きく依存します。

- [PapersGPT for Zotero](https://github.com/papersgpt/papersgpt-for-zotero) - Zotero 内で PDF との対話、要約、文献レビュー自動化を行える Zotero AI / MCP plugin。
- [Zotero](https://www.zotero.org/) - 個人・チーム双方にとって依然として最も実用的な文献管理基盤。多くの vibe research stack で canonical bibliography layer になります。
- [Semantic Scholar API](https://www.semanticscholar.org/product/api) - 論文検索、metadata retrieval、citation neighborhood、related-work discovery に役立つ実用的 API。
- [OpenAlex](https://docs.openalex.org/) - works、authors、institutions、venues、citations を含む open scholarly graph / API。再現可能な学術 metadata pipeline の基盤として非常に有力です。
- [Connected Papers](https://www.connectedpapers.com/) - 関連論文や citation neighborhood を可視化するグラフツール。seed paper から研究地図を広げるのに向いています。
- [Elicit](https://elicit.com/) - literature review と evidence extraction に強い research assistant。初期の論点整理や要約に有用です。
- [Research Rabbit](https://www.researchrabbit.ai/) - 論文 collection を作り、citation neighborhood を探索し、近い研究を継続的に発見できる文献探索ツール。
- [Litmaps](https://www.litmaps.com/) - seed set を起点に citation network と新着論文を追跡する動的 literature mapping ツール。
- [Inciteful](https://inciteful.xyz/) - seed papers から文献グラフを作り、研究領域間のつながりも探索できるツール。
- [Paperpile](https://paperpile.com/) - チーム協業や Google Docs / Word 連携に強い reference management system。
- [AgentSLR](https://github.com/OxRML/AgentSLR) - systematic literature reviews 向けの agentic system。search、screening、extraction、synthesis が必要なレビューに適しています。
- [arXiv](https://arxiv.org/) - 変化の速い分野で不可欠な preprint corpus。最先端を追う研究 agents にとってほぼ必須です。
- [OpenReview](https://openreview.net/) - peer review 文脈、workshop papers、議論スレッドの重要な情報源。特に ML 分野で有用です。
- [Papers with Code](https://paperswithcode.com/) - 論文、コード、benchmarks、datasets を結びつけるサイト。文献レビューから再現実験へ進む際に重要です。

<a id="reproducibility--experiment-ops"></a>
## 再現性と実験運用

研究の質は、結果を再実行、比較、検証、引き継ぎできるかどうかに大きく左右されます。

- [MLflow](https://github.com/mlflow/mlflow) - experiments、evaluation、monitoring、model / app lifecycle management を扱う open-source AI engineering platform。
- [Weights & Biases](https://wandb.ai/site) - experiment tracking、dashboards、artifacts、sweeps の代表的プラットフォーム。多数の run を共有可視化したいチームに向いています。
- [DVC](https://github.com/treeverse/dvc) - Git ベースの data versioning と ML experiments ツール。datasets、artifacts、metrics を repo と一緒に管理できます。
- [JupyterLab](https://github.com/jupyterlab/jupyterlab) - exploratory analysis、素早い実験、interactive report のための標準的な計算環境。
- [Marimo](https://github.com/marimo-team/marimo) - pure Python として保存される reactive notebook。diff しやすく、script や app のようにも実行できるため、agent workflows と相性が良いです。

<a id="research-writing--report-generation"></a>
## 研究執筆とレポート生成

研究は実験が終わった時点で終わりではありません。ノート、引用、結果を読みやすい成果物に変えるためのツールです。

- [Typst](https://github.com/typst/typst) - 従来の LaTeX より簡潔な構文と高速な反復を持つ modern typesetting system。agent-assisted research writing に向いています。
- [Overleaf](https://www.overleaf.com/) - 多くの学術チームで標準的に使われる collaborative LaTeX editor。
- [STORM](https://github.com/stanford-oval/storm) - トピックを調査し、引用付きの長文記事を生成する Stanford の citation-grounded report generation system。構造化された synthesis pipeline の参考になります。

<a id="rag--knowledge-infrastructure"></a>
## RAG と知識基盤

論文ライブラリ、ノート、web corpus を、research agents が実際に使える queryable knowledge system に変えるためのツールです。

- [LlamaIndex](https://github.com/run-llama/llama_index) - ingestion、indexing、retrieval、document agents のための広く使われる framework。paper-grounded research assistants に向いています。
- [Firecrawl](https://github.com/firecrawl/firecrawl) - web を clean で LLM-friendly なコンテンツへ変換する Web data API。PDF 以外の大規模収集に有用です。
- [Jina Reader](https://github.com/jina-ai/reader) - 任意の URL を軽量に clean markdown 化するツール。agent の後段処理に使いやすいです。

<a id="standards--protocols"></a>
## 標準とプロトコル

ツール、agents、repositories が共通言語を持つほど、研究 harness は再利用しやすくなります。

- [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) - モデルを外部ツール・データにつなぐ open standard。研究 agents が文献、ファイル、計算資源にアクセスする基盤になりつつあります。
- [ACP (Agent Communication Protocol)](https://agentcommunicationprotocol.dev/) - agents と harness 間の通信のための open protocol。複数の専門 agent が協調する研究システムに向いています。
- [agents.md](https://agents.md/) - project-level agent instructions の open standard。研究 repo の流儀や文脈を明示するのに役立ちます。
- [AGENTS.md](https://openai.com/index/introducing-agents-md/) - OpenAI の repository-level agent instructions 規約。研究 repo の構造、評価手順、ツール期待値を書くのに向いています。
- [Semantic Scholar API](https://api.semanticscholar.org/) - academic paper search、metadata、citation relationships の programmatic API。research-agent backend に実用的です。
- [arXiv API](https://info.arxiv.org/help/api/) - arXiv preprints を発見・取得するための API。変化の速い分野で重要です。
- [CrossRef API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - DOI 中心の metadata infrastructure。bibliographic enrichment や citation workflow に向いています。

### 研究向け MCP Servers

- [Zotero MCP](https://github.com/cookjohn/zotero-mcp) - AI assistants が Zotero library を直接扱えるようにする MCP bridge。
- [ScholarMCP](https://github.com/lstudlo/ScholarMCP) - literature search、PDF ingestion、citation management を扱う academic research MCP server。
- [OpenAlex Research MCP](https://github.com/oksure/openalex-research-mcp) - OpenAlex を使った scholarly search、citation analysis、trend discovery、collaboration mapping の MCP server。
- [arXiv MCP Server](https://github.com/anuj0456/arxiv-mcp-server) - arXiv papers の検索、分析、エクスポート用 MCP server。
- [Unpaywall MCP](https://github.com/ElliotPadfield/unpaywall-mcp) - Unpaywall 経由で DOI metadata と open-access PDFs を取得する MCP server。

<a id="methodologies--workflows"></a>
## 方法論とワークフロー

`vibe research` は単に「LLM に web 検索させること」ではなく、workflow design の問題です。

- [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) - AWS による AI-DLC の workflow 実装。元は software delivery 向けですが、研究の phased loops、artifacts、review points にうまく対応します。
- [AI-Driven Development Lifecycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) - human-in-the-loop agent systems を理解するための方法論的参照。understand、plan、execute の境界を明確にします。
- [Harness Engineering: Leveraging Codex in an Agent-First World](https://openai.com/index/harness-engineering/) - 環境設計、repo 構造、feedback loops、機械的 enforcement が prompt の巧妙さより重要であることを示す重要な記事です。
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - シンプルで composable、現実のタスクに根ざした agent systems を作るための重要な参考資料です。

<a id="reference--knowledge"></a>
## 参考資料と知識

### 研究システム

- [The AI Scientist](https://github.com/SakanaAI/AI-Scientist) - fully automated open-ended scientific discovery を目指す Sakana AI の代表的 system。human-in-the-loop を重視する場合でも、自動研究の上限を考えるうえで重要です。
- [The AI Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - workshop-level automated scientific discovery と agentic tree search に焦点を当てた続編。研究アイデア探索の深さを考える参考になります。
- [Deep Research Agent](https://github.com/tarun7r/deep-research-agent) - citation-backed な multi-agent research system を、概念実証ではなく runnable system として示した production-oriented な例です。

### 一般的な Harness 関連資料

- [Building an AI-Native Engineering Team](https://developers.openai.com/codex/guides/build-ai-native-engineering-team/) - agents を中心にチームの働き方を組み直したい人に有用な資料です。
- [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - state、tool execution、feedback loops、enforceable constraints の実践的な分解。

### キュレーションされたリスト

- [Awesome Deep Research Agent](https://github.com/ai-agents-2030/awesome-deep-research-agent) - deep research agents、papers、benchmarks の curated list。
- [Vibe Coding for Research](https://github.com/dlab-berkeley/Vibe-Coding-for-Research) - 現代的 AI tools を研究 workflow に取り込むための実践的入門。

<a id="contributing"></a>
## Contributing

PR を出す前に、[CONTRIBUTING.md](./CONTRIBUTING.md) を確認してください。

## License

[CC0 1.0](./LICENSE)
