# Awesome Vibe Research [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

<p align="center">
  <a href="./README.md">English</a> • <a href="./README.zh-CN.md">简体中文</a> • <a href="./README.ja.md">日本語</a> • <strong>Español</strong>
</p>

<p align="center">
  <sub>La versión en inglés es la referencia principal. Las traducciones pueden ir ligeramente por detrás.</sub>
</p>

> Una lista curada de recursos sobre **vibe research**. Aquí, vibe research significa una forma de trabajar en investigación donde las personas definen la dirección, las restricciones y los criterios de evaluación, mientras que los AI agents se encargan de la búsqueda bibliográfica, la ejecución experimental, la síntesis y la generación de informes, todo ello apoyado por un buen entorno de investigación, workflows, cómputo y revisión humana.

<a id="what-is-vibe-research"></a>
## ¿Qué Es Vibe Research?

Vibe Coding demostró que los desarrolladores pueden expresar intención y dejar que la IA ejecute una parte cada vez mayor del trabajo.

**Vibe Research** aplica esa misma idea al trabajo de investigación:

- Las personas definen el problema, el alcance, los estándares, las restricciones y los criterios de decisión.
- Los AI agents buscan literatura, organizan el trabajo relacionado, proponen preguntas, ejecutan experimentos, resumen resultados y redactan informes.
- Las personas siguen siendo responsables de la dirección, la aprobación, la interpretación y el juicio final.

La dificultad rara vez está solo en el modelo. Los cuellos de botella reales están en la coordinación: contexto fragmentado, demasiados handoffs manuales, cómputo ocioso, poca continuidad entre revisión de literatura y experimentación, y la falta de un sistema compartido donde humanos y agents vean el mismo estado de investigación.

### Etapas de Autonomía del Agent

A medida que la confianza y las herramientas maduran, vibe research avanza naturalmente por tres etapas:

| Etapa | Rol | Qué hace el Agent | Qué controlan los humanos |
|-------|-----|-------------------|--------------------------|
| **Etapa 1: Agent como Pasante** | Solo ejecución | Ejecuta experimentos diseñados por humanos. Sin propuestas de ideas ni preguntas de investigación — solo throughput confiable en tareas bien definidas. | Definición del problema, diseño experimental, interpretación, todas las decisiones. |
| **Etapa 2: Agent como Investigador** | Investigación independiente dentro de una pregunta | Se hace cargo de una research question de principio a fin. Auto-itera a nivel de experimento: propone experimentos, los ejecuta, interpreta resultados y mejora — todo dentro del límite de una pregunta de investigación. | Formulación de preguntas de investigación, priorización entre preguntas, juicio final. |
| **Etapa 3: Agent como Líder de Investigación** | Autonomía completa del proyecto | Dirige un proyecto de investigación completo. Formula preguntas de investigación, construye y prueba hipótesis, decide cuáles aceptar o rechazar, y traza la dirección de la investigación. | Supervisión estratégica, revisión ética, decisiones de publicación. |

La mayoría de los equipos hoy operan en la Etapa 1. El objetivo del tooling de vibe research es hacer la Etapa 2 confiable y la Etapa 3 factible.

<a id="core-principles"></a>
## Principios Básicos

Tomando ideas de agent harness engineering y adaptándolas al trabajo de investigación:

1. **Humans steer, agents execute** - los investigadores marcan la dirección; los agents aportan throughput.
2. **Research context is the system of record** - papers, notas, estado experimental, informes y código deben vivir en un stack único e inspeccionable.
3. **Research is iterative, not linear** - los buenos sistemas soportan bifurcaciones, bucles, reintentos y trabajo en paralelo.
4. **Approval gates matter** - la propuesta autónoma es útil; la aceptación autónoma es arriesgada.
5. **Observability matters** - si no puedes inspeccionar la búsqueda, el progreso experimental y las salidas, no puedes confiar de verdad en el flujo.
6. **Compute is part of the workflow** - colas de GPU, clústeres, presupuestos y estado de ejecución no deberían quedar fuera del sistema de investigación.
7. **Agent legibility is a feature** - workflows, prompts, tools y artefactos deben ser fáciles de retomar por otra persona o por otro agent.
8. **Context continuity beats prompt cleverness** - los mejores sistemas conservan contexto entre revisión bibliográfica, planificación, ejecución e informe.

<a id="contents"></a>
## Contenido

- [¿Qué Es Vibe Research?](#what-is-vibe-research)
- [Principios Básicos](#core-principles)
- [Plataformas de Ciclo Completo](#full-lifecycle-platforms)
- [Auto-Research y AI Scientists](#auto-research--ai-scientists)
- [Orquestadores de Agents](#agent-orchestrators)
- [Ejecución de Experimentos y Workflows](#experiment--workflow-runners)
- [Runtimes de Agents](#agent-runtimes)
- [Coding & Lab Agents](#coding--lab-agents)
- [Sistemas de Literatura y Conocimiento](#literature--knowledge-systems)
- [Reproducibilidad y Operación Experimental](#reproducibility--experiment-ops)
- [Escritura Académica y Generación de Informes](#research-writing--report-generation)
- [RAG e Infraestructura de Conocimiento](#rag--knowledge-infrastructure)
- [Estándares y Protocolos](#standards--protocols)
- [Metodologías y Workflows](#methodologies--workflows)
- [Referencias y Conocimiento](#reference--knowledge)
- [Contribuciones](#contributing)

<a id="full-lifecycle-platforms"></a>
## Plataformas de Ciclo Completo

Plataformas que cubren una parte relevante del ciclo completo de investigación: descubrimiento de literatura, formulación de preguntas, orquestación experimental, reporting y revisión humana.

- [Synapse](https://github.com/Vincentwei1021/Synapse) - **Punto de partida recomendado.** Es una plataforma de orquestación de investigación diseñada específicamente para la colaboración entre human researchers y AI agents. Cubre revisión bibliográfica, formulación de preguntas de investigación, ejecución experimental y generación de informes, con agent management, orquestación de cómputo, observabilidad en tiempo real, un loop autónomo y más de 60 MCP tools. Si solo vas a evaluar una plataforma para `vibe research`, empieza aquí.
- [Denario](https://github.com/AstroPilot-AI/Denario) - Sistema modular multi-agent para asistencia en investigación científica. Más orientado que Synapse hacia artefactos de investigación y papers, con más énfasis en el paso de idea a method, results y research artifact.
- [OpenAGS](https://github.com/openags/OpenAGS) - Antes llamado Auto-Research. Un esfuerzo más exploratorio hacia scientist agents generalistas que abarcan literatura, experimentación, escritura e incluso robótica. Menos orientado a producción, pero importante para entender hacia dónde va la categoría.

<a id="auto-research--ai-scientists"></a>
## Auto-Research y AI Scientists

Esta categoría agrupa sistemas orientados explícitamente a research loops autónomos o semi-autónomos: idea discovery, hypothesis generation, experiment iteration y, en algunos casos, paper writing. Están más cerca de `auto-research` que de los agent frameworks genéricos.

- [AutoResearchClaw](https://github.com/aiming-lab/AutoResearchClaw) - Sistema de investigación fully autonomous y self-evolving que empuja desde la idea hasta el paper. Es uno de los proyectos más cercanos al patrón de "chat an idea, get a paper".
- [ARIS (Auto-Research-In-Sleep)](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) - Conjunto ligero de Markdown-only skills para autonomous ML research, con foco en cross-model review loops, idea discovery y experiment automation. Aquí se enlaza el canonical upstream de la familia ARIS, no sus forks.
- [AgentLaboratory](https://github.com/SamuelSchmidgall/AgentLaboratory) - End-to-end autonomous research workflow pensado para ayudar a human researchers a convertir ideas en research loops ejecutables.
- [EvoScientist](https://github.com/EvoScientist/EvoScientist) - Sistema self-evolving de AI scientist centrado en autonomous discovery e iterative research workflows.
- [The AI Scientist](https://github.com/SakanaAI/AI-Scientist) - El sistema influyente de Sakana AI para fully automated open-ended scientific discovery, y una referencia central para la categoría de AI scientist.
- [The AI Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - Continuación centrada en workshop-level automated scientific discovery mediante agentic tree search, empujando más lejos la ramificación autónoma de investigación.
- [autonomous-researcher](https://github.com/mshumer/autonomous-researcher) - Proyecto ligero de autonomous researcher más orientado a ejecución independiente de investigación que a chat-style synthesis genérico.
- [Auto-Deep-Research](https://github.com/HKUDS/Auto-Deep-Research) - Personal AI assistant fully automated con una fuerte orientación a deep research. Funciona bien como puente entre autonomous research y assistant-style workflows.
- [AutoResearch-SibylSystem](https://github.com/Sibyl-Research-Team/AutoResearch-SibylSystem) - Fully autonomous AI research system con self-evolution, construido de forma nativa sobre Claude Code.
- [freephdlabor](https://github.com/ltjed/freephdlabor) - Sistema multi-agent personalizado que investiga de forma continua sobre un problema científico definido por el usuario. Está muy alineado con el patrón de "research while you sleep".
- [InnoClaw](https://github.com/SpectrAI-Initiative/InnoClaw) - AI research agent para scientific innovation, más cercano a workflows de ideación y descubrimiento autónomos.
- [BioAgents](https://github.com/bio-xyz/BioAgents) - Framework domain-specific de AI scientist para autonomous deep research en ciencias biológicas, combinando agents de análisis de literatura con agents de ciencia de datos.
- [biomedical-aiq-research-agent](https://github.com/NVIDIA-AI-Blueprints/biomedical-aiq-research-agent) - Blueprint de NVIDIA para biomedical research-agent workflows. Buen ejemplo de diseño domain-specific de automated researcher.
- [Marco-DeepResearch](https://github.com/AIDC-AI/Marco-DeepResearch) - Deep research agent muy orientado a búsqueda, útil cuando la calidad del autonomous research depende fuertemente de search y retrieval.
- [AI-Co-Scientist](https://github.com/ai-in-pm/AI-Co-Scientist) - Sistema multi-agent para investigación científica e hypothesis generation. Sigue siendo early-stage, pero encaja bien en la categoría de AI scientist.

<a id="agent-orchestrators"></a>
## Orquestadores de Agents

Estas herramientas ayudan a estructurar workflows complejos con agents, dividir responsabilidades por rol y hacer legible el paso de búsqueda a síntesis y ejecución.

- [LangGraph](https://github.com/langchain-ai/langgraph) - Framework basado en grafos para resilient language agents. Útil cuando el workflow de investigación tiene etapas, checkpoints, reintentos y aprobación humana.
- [Deep Agents](https://github.com/langchain-ai/deepagents) - Agent harness sobre LangChain y LangGraph con planning, acceso al filesystem y subagent spawning. Encaja bien en stacks de investigación que necesitan progressive disclosure y descomposición recursiva.
- [AutoGen](https://github.com/microsoft/autogen) - Framework de Microsoft para agentic AI. Útil para agents especializados como scout, critic, experimenter o writer.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Framework para orquestar agents autónomos con roles. Va bien cuando quieres separar revisión bibliográfica, diseño de benchmarks, implementación y redacción.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - Framework de agents y workflows con buen soporte de conectores. Útil si tu stack de investigación necesita integrarse con sistemas empresariales, memoria y múltiples backends de modelos.
- [cmbagent](https://github.com/CMBAgents/cmbagent) - Sistema multi-agent orientado a investigación y construido sobre AG2. Está más cerca de un sistema científico que de una abstracción genérica de orquestación.
- [GPT Researcher](https://github.com/assafelovic/gpt-researcher) - Agent autónomo de deep research sobre web y datos locales. Buen punto de referencia para workflows centrados en buscar, filtrar, sintetizar y redactar.
- [DeerFlow](https://github.com/bytedance/deer-flow) - Super-agent harness de largo horizonte con sandboxes, memory, tools, skills y subagents. Útil para tareas de investigación que duran mucho tiempo y mezclan navegación, código y generación de artefactos.
- [OpenScholar](https://github.com/AkariAsai/OpenScholar) - Sistema retrieval-augmented para síntesis de literatura científica. Especialmente relevante para respuestas grounded y ricas en citas.
- [PaperQA2](https://github.com/Future-House/paper-qa) - Agent de QA con citas y alta precisión sobre documentos científicos. Uno de los mejores bloques de construcción para workflows paper-grounded.
- [RD-Agent](https://github.com/microsoft/RD-Agent) - Framework de automatización de I+D de Microsoft para iteración de hipótesis, escritura de código, ejecución experimental y refinement. Un puente importante entre software agents y research agents.
- [AutoRA](https://github.com/AutoResearch/autora) - Automated Research Assistant para descubrimiento científico en closed loop. Muy relevante para workflows empíricos que iteran entre modelado, diseño experimental y recolección de datos.

<a id="experiment--workflow-runners"></a>
## Ejecución de Experimentos y Workflows

Cuando el trabajo de investigación deja de estar solo en la conversación y empieza a lanzar jobs, tocar datasets, clústeres o pipelines programados, estas herramientas pasan a ser parte del harness.

- [Metaflow](https://github.com/Netflix/metaflow) - Herramienta para construir, gestionar y desplegar sistemas AI/ML. Muy útil cuando necesitas lineage, reanudación y una transición limpia desde notebooks hacia workflows recurrentes.
- [Dagster](https://github.com/dagster-io/dagster) - Plataforma de orquestación orientada a assets y con buena observabilidad. Útil cuando los resultados de investigación se convierten en data assets reutilizables o evaluation sets.
- [Prefect](https://github.com/PrefectHQ/prefect) - Framework Python-native de workflow orchestration. Una opción práctica para research jobs disparados por agents.
- [SkyPilot](https://github.com/skypilot-org/skypilot) - Interfaz unificada para ejecutar AI workloads sobre Kubernetes, Slurm, cloud pública y on-prem. Muy relevante para vibe research con uso intensivo de GPU.
- [Modal](https://modal.com/) - Plataforma gestionada de cómputo para batch jobs, agents y data workloads. Muy útil para equipos pequeños que quieren iterar rápido sin operar toda la infraestructura.
- [Ray](https://github.com/ray-project/ray) - Motor de cómputo AI y runtime distribuido. Útil para búsqueda paralela, training, simulación, evaluation sweeps y ejecución experimental de alto throughput.
- [ClearML](https://github.com/clearml/clearml) - Plataforma open source que cubre experiment management, pipelines, scheduling y remote execution. Útil cuando se necesita una capa de ops más integrada.
- [TruLens](https://github.com/truera/trulens) - Evaluación y tracking para experimentos con LLMs y AI agents. Muy útil para medir la calidad de outputs de research agents y RAG pipelines.

<a id="agent-runtimes"></a>
## Runtimes de Agents

Los runtimes permiten que los agents sigan vivos entre sesiones, canales y tareas largas. En investigación eso importa mucho, porque el trabajo valioso suele durar días, no un solo prompt.

- [OpenClaw](https://github.com/openclaw/openclaw) - Persistent agent runtime con skills, sub-agent spawning y multi-channel session management. Encaja bien cuando los research agents deben seguir trabajando entre mensajería, planificación y ejecución.

<a id="coding--lab-agents"></a>
## Coding & Lab Agents

Incluso en equipos de investigación se dedica mucho tiempo a escribir código experimental, glue code, código de evaluación y scripts de análisis. Esta es la capa de ejecución para ese trabajo.

- [Codex](https://github.com/openai/codex) - Coding agent ligero para terminal. Útil para experiment code, data scripts, automatización y tareas de laboratorio repo-grounded.
- [Claude Code](https://code.claude.com/) - Coding agent repo-grounded con skill files, terminal tooling y patrones multi-agent cada vez más maduros. Encaja bien con repositorios de investigación con convenciones estables.
- [OpenHands](https://github.com/OpenHands/OpenHands) - Plataforma de desarrollo impulsada por IA que puede correr en entornos sandboxed. Útil para convertir planes de investigación en cambios de código o prototipos ejecutables.
- [Aider](https://github.com/Aider-AI/aider) - Herramienta ligera de AI pair programming en terminal. Muy útil para repos pequeños, análisis puntuales e iteración rápida.

<a id="literature--knowledge-systems"></a>
## Sistemas de Literatura y Conocimiento

La calidad de los research agents depende en gran medida de los corpus y sistemas de conocimiento que tienen detrás.

- [PapersGPT for Zotero](https://github.com/papersgpt/papersgpt-for-zotero) - Plugin de Zotero con IA y MCP para hablar con PDFs, generar resúmenes y automatizar revisión bibliográfica dentro de la biblioteca.
- [Zotero](https://www.zotero.org/) - Sigue siendo el sistema de registro más práctico para bibliotecas personales y de equipo. Muchos vibe research stacks deberían tratarlo como la capa bibliográfica canónica.
- [Semantic Scholar API](https://www.semanticscholar.org/product/api) - API muy útil para búsqueda de papers, recuperación de metadatos, exploración de citas y related-work discovery.
- [OpenAlex](https://docs.openalex.org/) - Scholarly graph y API abiertos para works, authors, institutions, venues y citations. Muy fuerte como base de pipelines reproducibles de metadatos académicos.
- [Connected Papers](https://www.connectedpapers.com/) - Herramienta visual para explorar papers relacionados y vecindarios de citas. Ideal para expandir un seed paper en un mapa de investigación.
- [Elicit](https://elicit.com/) - Research assistant centrado en literature review y evidence extraction. Útil para síntesis temprana y refinamiento de preguntas.
- [Research Rabbit](https://www.researchrabbit.ai/) - Sistema de descubrimiento bibliográfico para construir colecciones, explorar citas y encontrar trabajo cercano de forma continua.
- [Litmaps](https://www.litmaps.com/) - Herramienta dinámica de literature mapping para seguir redes de citas y nuevos papers alrededor de un seed set.
- [Inciteful](https://inciteful.xyz/) - Herramienta de exploración de grafos bibliográficos basada en seed papers y conexiones entre cuerpos de trabajo.
- [Paperpile](https://paperpile.com/) - Sistema de gestión bibliográfica con buena experiencia colaborativa y fuertes integraciones con Google Docs y Word.
- [AgentSLR](https://github.com/OxRML/AgentSLR) - Sistema agentic para systematic literature reviews. Encaja bien cuando el workflow necesita search, screening, extraction y synthesis formales.
- [arXiv](https://arxiv.org/) - Corpus fundamental de preprints para campos de evolución rápida. Esencial si los agents deben seguir la frontera.
- [OpenReview](https://openreview.net/) - Fuente importante de contexto de peer review, workshop papers y discusiones, especialmente en investigación relacionada con ML.
- [Papers with Code](https://paperswithcode.com/) - Conecta papers con código, benchmarks y datasets. Muy útil para pasar de revisión bibliográfica a experimentación reproducible.

<a id="reproducibility--experiment-ops"></a>
## Reproducibilidad y Operación Experimental

La calidad de la investigación depende en gran medida de poder rerun, comparar, inspeccionar y transferir el trabajo con limpieza.

- [MLflow](https://github.com/mlflow/mlflow) - Plataforma open source para experiments, evaluation, monitoring y gestión del ciclo de vida de modelos o aplicaciones.
- [Weights & Biases](https://wandb.ai/site) - Plataforma popular para experiment tracking, dashboards, artifacts y sweeps. Muy útil cuando un equipo necesita visibilidad compartida sobre muchas ejecuciones.
- [DVC](https://github.com/treeverse/dvc) - Versionado de datos y experimentos ML en workflows basados en Git. Útil para llevar datasets, artifacts y metrics junto al repo.
- [JupyterLab](https://github.com/jupyterlab/jupyterlab) - Entorno computacional estándar para análisis exploratorio, iteración rápida y reporting interactivo.
- [Marimo](https://github.com/marimo-team/marimo) - Notebook reactivo almacenado como Python puro en lugar de JSON. Muy amigable para workflows con agents porque diffea mejor y puede ejecutarse como script o app.

<a id="research-writing--report-generation"></a>
## Escritura Académica y Generación de Informes

La investigación no termina cuando una ejecución sale bien. Estas herramientas ayudan a convertir notas, citas y resultados en outputs legibles y publicables.

- [Typst](https://github.com/typst/typst) - Sistema moderno de typesetting con sintaxis más limpia y ciclos más rápidos que LaTeX tradicional. Muy útil para agent-assisted research writing.
- [Overleaf](https://www.overleaf.com/) - Editor colaborativo de LaTeX que sigue siendo la superficie de escritura por defecto para muchos equipos académicos.
- [STORM](https://github.com/stanford-oval/storm) - Sistema de Stanford para investigar un tema y producir un informe largo con citas. Muy útil como referencia para pipelines de síntesis estructurada.

<a id="rag--knowledge-infrastructure"></a>
## RAG e Infraestructura de Conocimiento

Estas herramientas convierten bibliotecas de papers, notas y corpus web en sistemas de conocimiento consultables que los research agents realmente pueden usar.

- [LlamaIndex](https://github.com/run-llama/llama_index) - Framework muy utilizado para ingestion, indexing, retrieval y document agents. Muy útil para construir assistants paper-grounded.
- [Firecrawl](https://github.com/firecrawl/firecrawl) - Web Data API que convierte sitios en contenido limpio y LLM-friendly. Muy útil para recolección de datos de investigación más allá de PDFs.
- [Jina Reader](https://github.com/jina-ai/reader) - Forma ligera de convertir cualquier URL en markdown limpio para consumo posterior por agents.

<a id="standards--protocols"></a>
## Estándares y Protocolos

Los research harnesses son mucho más reutilizables cuando tools, agents y repositories pueden hablar un lenguaje común.

- [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) - Open standard para conectar modelos con tools y datos externos. Cada vez más central para research agents con acceso en vivo a literatura, archivos y cómputo.
- [ACP (Agent Communication Protocol)](https://agentcommunicationprotocol.dev/) - Protocolo abierto para comunicación entre agents y harnesses. Relevante cuando múltiples agents especializados deben coordinarse.
- [agents.md](https://agents.md/) - Open standard para instrucciones de agents a nivel de proyecto. Útil para hacer explícitas las convenciones de un research repo.
- [AGENTS.md](https://openai.com/index/introducing-agents-md/) - Convención de OpenAI para instrucciones de agents a nivel de repositorio. Buena para codificar estructura, pasos de evaluación y expectativas de herramientas.
- [Semantic Scholar API](https://api.semanticscholar.org/) - API programática para academic paper search, metadatos y relaciones de citas. Muy práctica para backends de research agents.
- [arXiv API](https://info.arxiv.org/help/api/) - Acceso a preprints de arXiv para workflows de descubrimiento y recuperación.
- [CrossRef API](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) - Infraestructura de metadatos centrada en DOI para enriquecimiento bibliográfico y workflows de citas.

### MCP Servers Enfocados en Investigación

- [Zotero MCP](https://github.com/cookjohn/zotero-mcp) - MCP bridge para que asistentes de IA interactúen directamente con una biblioteca Zotero.
- [ScholarMCP](https://github.com/lstudlo/ScholarMCP) - Academic research MCP server que cubre literature search, PDF ingestion y citation management.
- [OpenAlex Research MCP](https://github.com/oksure/openalex-research-mcp) - MCP server para scholarly search, citation analysis, trend discovery y collaboration mapping vía OpenAlex.
- [arXiv MCP Server](https://github.com/anuj0456/arxiv-mcp-server) - MCP server para buscar, analizar y exportar papers de arXiv.
- [Unpaywall MCP](https://github.com/ElliotPadfield/unpaywall-mcp) - MCP server para obtener metadatos DOI y PDFs open access a través de Unpaywall.

<a id="methodologies--workflows"></a>
## Metodologías y Workflows

Estas referencias importan porque `vibe research` no es simplemente "hacer que un LLM navegue la web". Es un problema de diseño de workflow.

- [AI-DLC Workflows](https://github.com/awslabs/aidlc-workflows) - Implementación de AWS del workflow AI-DLC. Aunque venga del software delivery, encaja muy bien con loops de investigación por fases, artefactos y review points.
- [AI-Driven Development Lifecycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) - Referencia metodológica valiosa para sistemas agentic con human-in-the-loop y fronteras claras entre understand, plan y execute.
- [Harness Engineering: Leveraging Codex in an Agent-First World](https://openai.com/index/harness-engineering/) - Explica por qué diseño del entorno, estructura del repo, feedback loops y enforcement mecánico suelen importar más que la astucia del prompt.
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - Buena referencia para construir systems de agents simples, componibles y orientados a tareas reales.

<a id="reference--knowledge"></a>
## Referencias y Conocimiento

### Lecturas Generales sobre Harnesses

- [Building an AI-Native Engineering Team](https://developers.openai.com/codex/guides/build-ai-native-engineering-team/) - Útil para equipos que se están reorganizando alrededor de agents, incluso fuera del software engineering tradicional.
- [The Anatomy of an Agent Harness](https://blog.langchain.com/the-anatomy-of-an-agent-harness/) - Desglose práctico de state, tool execution, feedback loops y restricciones enforceable en sistemas agentic.

### Listas Curadas

- [Awesome Deep Research Agent](https://github.com/ai-agents-2030/awesome-deep-research-agent) - Colección curada de papers, systems y benchmarks sobre deep research agents.
- [Vibe Coding for Research](https://github.com/dlab-berkeley/Vibe-Coding-for-Research) - Introducción práctica al uso de herramientas modernas de IA en workflows de investigación.

<a id="contributing"></a>
## Contribuciones

Las contribuciones son bienvenidas. Antes de abrir un PR, revisa [CONTRIBUTING.md](./CONTRIBUTING.md).

## Licencia

[CC0 1.0](./LICENSE)
