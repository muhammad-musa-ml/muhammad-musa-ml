<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/hero-dark.svg">
  <img alt="Muhammad Musa: LLM security researcher and lead software engineer at WUMI Health" src="assets/hero-light.svg" width="100%">
</picture>

<p align="center">
  <a href="https://iammusa.vercel.app"><b>iammusa.vercel.app</b></a>
  &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/mmusa2/">LinkedIn</a>
  &nbsp;·&nbsp;
  <a href="mailto:mmusa2@wisc.edu">mmusa2@wisc.edu</a>
  &nbsp;·&nbsp;
  <a href="https://orcid.org/0009-0009-5542-8040">ORCID</a>
  &nbsp;·&nbsp;
  <a href="./MY-CLAUDE-SETUP.md">Setup notes</a>
</p>

I'm Musa, and I'm finishing my M.S. in Computer Sciences at UW-Madison this December. Most of my research has been on LLM security, prompt injection in particular, and since last fall I've been working with Prof. Somesh Jha on agentic knowledge-graph extraction from energy-regulatory rate cases.

Outside research I lead engineering at WUMI Health. I also TA the graduate Big Data Systems course, where I look after the programming projects and their autograders (before this semester I was head TA for Data Science Programming II).

## Projects

<table>
<tr><th align="left">Project</th><th align="left">What it is</th></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/distributed-lender-service">distributed-lender-service</a></td><td>A C++20 gRPC service over MySQL, Parquet and HDFS, about 440k mortgage records. Its cache sits at replication 1 on purpose, so when a DataNode dies the service has to notice and rebuild it. There's a lock-free ring buffer and an epoll server in there too.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/agent-distillation-lab">agent-distillation-lab</a></td><td>I distilled a 4B model's tool-use policy into a 0.6B one with LoRA. All of it ran on my laptop's 6 GB GPU.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/triage-guard-agent">triage-guard-agent</a></td><td>A LangGraph support agent. Refunds over $50 wait for a human.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/artifact-conformance-toolkit">artifact-conformance-toolkit</a></td><td>Checks that read a benchmark repo's docs, raw results and git history, and fail it when a published number can't be traced back to the records behind it.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/kiln">kiln</a></td><td>I save a lot of reels and never open them again. Kiln reads them for me and turns them into notes I can search. A copy of my library is up at <a href="https://kiln-by-m.vercel.app">kiln-by-m.vercel.app</a>.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/internships">internships</a></td><td>Work from my internships at DeepLearnHQ (2025) and SAUDCONSULT (2024), rebuilt on my own machine.</td></tr>
<tr><td nowrap><a href="https://github.com/muhammad-musa-ml/musa-portfolio">musa-portfolio</a></td><td>My personal site: Three.js, plus an AI twin you can ask about my work.</td></tr>
</table>

Older: [AugData](https://github.com/muhammad-musa-ml/AugData) (a benchmark dataset for multimodal models), [customized_transport_layer](https://github.com/muhammad-musa-ml/customized_transport_layer) (reliable transport over UDP, in Python) and [reprod](https://github.com/muhammad-musa-ml/reprod), the code behind the ransomware paper below. WUMI Health, resume-gauntlet and the knowledge-graph project are private.

## Research

Last spring a partner and I did a course project on [indirect prompt injection in RAG](https://github.com/muhammad-musa-ml/IPI-763), and I built most of the attacks and defenses. The system-prompt defense OWASP recommends backfired on us. In a paired test on llama3.2:3b it took one attack's success rate from 12% to 38%.

I've also compared protein language model embeddings as GraphSAGE features for protein-interaction link prediction, where the structure-aware SaProt model did best (AUPRC 0.838). And with a collaborator I built the first labeled topic-classification dataset for Punjabi written in Shahmukhi script.

Papers: [Towards Reproducible Ransomware Analysis](https://doi.org/10.1145/3607505.3607510), ACM CSET 2023, co-author with SRI International. [Extremism on Social Media: Lynching of Priyantha Kumara Diyawadana](https://doi.org/10.1109/ASONAM55673.2022.10068622), IEEE/ACM ASONAM 2022, first author.

## WUMI Health

WUMI Health is a patient-owned health record for Pakistan, built in Flutter on Supabase with consent enforced by Postgres row-level security. We're seven phases into a thirteen-phase build, and seven clinics, two hospitals and three labs are on board. I work on it with three interns.

## Coding agents

I build with Claude Code and have spent a lot of time on how it's set up. There's a write-up in the [setup notes](./MY-CLAUDE-SETUP.md).

## Background

Undergrad was computer science at LUMS in Lahore. I was on the Dean's Honor List, ran the IEEE student chapter, and was project head for a UAV team that made the top 20 at TEKNOFEST. Fun fact: I love sports, travelling and CS, three things that are impossible to manage together, so you know I have good time management skills.

## Toolbox

<!-- toolbox:start -->

<p><sub><b>LANGUAGES</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/py-dark.svg"><img src="assets/tools/py-light.svg" width="76" height="70" alt="Python"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/cpp-dark.svg"><img src="assets/tools/cpp-light.svg" width="76" height="70" alt="C++"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/ts-dark.svg"><img src="assets/tools/ts-light.svg" width="76" height="70" alt="TypeScript"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/rust-dark.svg"><img src="assets/tools/rust-light.svg" width="76" height="70" alt="Rust"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/java-dark.svg"><img src="assets/tools/java-light.svg" width="76" height="70" alt="Java"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/c-dark.svg"><img src="assets/tools/c-light.svg" width="76" height="70" alt="C"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/js-dark.svg"><img src="assets/tools/js-light.svg" width="76" height="70" alt="JavaScript"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/dart-dark.svg"><img src="assets/tools/dart-light.svg" width="76" height="70" alt="Dart"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/bash-dark.svg"><img src="assets/tools/bash-light.svg" width="76" height="70" alt="Bash"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/powershell-dark.svg"><img src="assets/tools/powershell-light.svg" width="76" height="70" alt="PowerShell"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/r-dark.svg"><img src="assets/tools/r-light.svg" width="76" height="70" alt="R"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/matlab-dark.svg"><img src="assets/tools/matlab-light.svg" width="76" height="70" alt="MATLAB"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/haskell-dark.svg"><img src="assets/tools/haskell-light.svg" width="76" height="70" alt="Haskell"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/swift-dark.svg"><img src="assets/tools/swift-light.svg" width="76" height="70" alt="Swift"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/solidity-dark.svg"><img src="assets/tools/solidity-light.svg" width="76" height="70" alt="Solidity"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/html-dark.svg"><img src="assets/tools/html-light.svg" width="76" height="70" alt="HTML"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/css-dark.svg"><img src="assets/tools/css-light.svg" width="76" height="70" alt="CSS"></picture>
</p>

<p><sub><b>MACHINE LEARNING &amp; DATA SCIENCE</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/pytorch-dark.svg"><img src="assets/tools/pytorch-light.svg" width="76" height="70" alt="PyTorch"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/tensorflow-dark.svg"><img src="assets/tools/tensorflow-light.svg" width="76" height="70" alt="TensorFlow"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/sklearn-dark.svg"><img src="assets/tools/sklearn-light.svg" width="76" height="70" alt="scikit-learn"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/huggingface-dark.svg"><img src="assets/tools/huggingface-light.svg" width="76" height="70" alt="Hugging Face"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/pandas-dark.svg"><img src="assets/tools/pandas-light.svg" width="76" height="70" alt="pandas"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/numpy-dark.svg"><img src="assets/tools/numpy-light.svg" width="76" height="70" alt="NumPy"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/opencv-dark.svg"><img src="assets/tools/opencv-light.svg" width="76" height="70" alt="OpenCV"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/keras-dark.svg"><img src="assets/tools/keras-light.svg" width="76" height="70" alt="Keras"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/pyg-dark.svg"><img src="assets/tools/pyg-light.svg" width="76" height="70" alt="PyG"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/scipy-dark.svg"><img src="assets/tools/scipy-light.svg" width="76" height="70" alt="SciPy"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/plotly-dark.svg"><img src="assets/tools/plotly-light.svg" width="76" height="70" alt="Plotly"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/jupyter-dark.svg"><img src="assets/tools/jupyter-light.svg" width="76" height="70" alt="Jupyter"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/anaconda-dark.svg"><img src="assets/tools/anaconda-light.svg" width="76" height="70" alt="Anaconda"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/nvidia-dark.svg"><img src="assets/tools/nvidia-light.svg" width="76" height="70" alt="CUDA"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/mlflow-dark.svg"><img src="assets/tools/mlflow-light.svg" width="76" height="70" alt="MLflow"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/weightsandbiases-dark.svg"><img src="assets/tools/weightsandbiases-light.svg" width="76" height="70" alt="Weights &amp; Biases"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/optuna-dark.svg"><img src="assets/tools/optuna-light.svg" width="76" height="70" alt="Optuna"></picture>
</p>

<p><sub><b>LANGUAGE MODELS &amp; AGENTS</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/claude-dark.svg"><img src="assets/tools/claude-light.svg" width="76" height="70" alt="Claude Code"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/googlegemini-dark.svg"><img src="assets/tools/googlegemini-light.svg" width="76" height="70" alt="Gemini API"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/ollama-dark.svg"><img src="assets/tools/ollama-light.svg" width="76" height="70" alt="Ollama"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/langchain-dark.svg"><img src="assets/tools/langchain-light.svg" width="76" height="70" alt="LangChain"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/langgraph-dark.svg"><img src="assets/tools/langgraph-light.svg" width="76" height="70" alt="LangGraph"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/modelcontextprotocol-dark.svg"><img src="assets/tools/modelcontextprotocol-light.svg" width="76" height="70" alt="MCP"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/vllm-dark.svg"><img src="assets/tools/vllm-light.svg" width="76" height="70" alt="vLLM"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/qwen-dark.svg"><img src="assets/tools/qwen-light.svg" width="76" height="70" alt="Qwen"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/crewai-dark.svg"><img src="assets/tools/crewai-light.svg" width="76" height="70" alt="CrewAI"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/pydantic-dark.svg"><img src="assets/tools/pydantic-light.svg" width="76" height="70" alt="Pydantic"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/gradio-dark.svg"><img src="assets/tools/gradio-light.svg" width="76" height="70" alt="Gradio"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/qdrant-dark.svg"><img src="assets/tools/qdrant-light.svg" width="76" height="70" alt="Qdrant"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/opentelemetry-dark.svg"><img src="assets/tools/opentelemetry-light.svg" width="76" height="70" alt="OpenTelemetry"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/modal-dark.svg"><img src="assets/tools/modal-light.svg" width="76" height="70" alt="Modal"></picture>
</p>

<p><sub><b>DATA ENGINEERING</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/kafka-dark.svg"><img src="assets/tools/kafka-light.svg" width="76" height="70" alt="Kafka"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apachespark-dark.svg"><img src="assets/tools/apachespark-light.svg" width="76" height="70" alt="Spark"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apacheairflow-dark.svg"><img src="assets/tools/apacheairflow-light.svg" width="76" height="70" alt="Airflow"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/snowflake-dark.svg"><img src="assets/tools/snowflake-light.svg" width="76" height="70" alt="Snowflake"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/googlebigquery-dark.svg"><img src="assets/tools/googlebigquery-light.svg" width="76" height="70" alt="BigQuery"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apachehadoop-dark.svg"><img src="assets/tools/apachehadoop-light.svg" width="76" height="70" alt="Hadoop / HDFS"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apachehive-dark.svg"><img src="assets/tools/apachehive-light.svg" width="76" height="70" alt="Hive"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apacheparquet-dark.svg"><img src="assets/tools/apacheparquet-light.svg" width="76" height="70" alt="Parquet"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/apachearrow-dark.svg"><img src="assets/tools/apachearrow-light.svg" width="76" height="70" alt="Arrow"></picture>
</p>

<p><sub><b>DATABASES &amp; SEARCH</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/postgres-dark.svg"><img src="assets/tools/postgres-light.svg" width="76" height="70" alt="PostgreSQL"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/supabase-dark.svg"><img src="assets/tools/supabase-light.svg" width="76" height="70" alt="Supabase"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/mysql-dark.svg"><img src="assets/tools/mysql-light.svg" width="76" height="70" alt="MySQL"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/mongodb-dark.svg"><img src="assets/tools/mongodb-light.svg" width="76" height="70" alt="MongoDB"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/redis-dark.svg"><img src="assets/tools/redis-light.svg" width="76" height="70" alt="Redis"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/elasticsearch-dark.svg"><img src="assets/tools/elasticsearch-light.svg" width="76" height="70" alt="Elasticsearch"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/cassandra-dark.svg"><img src="assets/tools/cassandra-light.svg" width="76" height="70" alt="Cassandra"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/sqlite-dark.svg"><img src="assets/tools/sqlite-light.svg" width="76" height="70" alt="SQLite"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/neo4j-dark.svg"><img src="assets/tools/neo4j-light.svg" width="76" height="70" alt="Neo4j"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/dynamodb-dark.svg"><img src="assets/tools/dynamodb-light.svg" width="76" height="70" alt="DynamoDB"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/firebase-dark.svg"><img src="assets/tools/firebase-light.svg" width="76" height="70" alt="Firebase"></picture>
</p>

<p><sub><b>BACKEND &amp; APIS</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/fastapi-dark.svg"><img src="assets/tools/fastapi-light.svg" width="76" height="70" alt="FastAPI"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/flask-dark.svg"><img src="assets/tools/flask-light.svg" width="76" height="70" alt="Flask"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/django-dark.svg"><img src="assets/tools/django-light.svg" width="76" height="70" alt="Django"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/graphql-dark.svg"><img src="assets/tools/graphql-light.svg" width="76" height="70" alt="GraphQL"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/nodejs-dark.svg"><img src="assets/tools/nodejs-light.svg" width="76" height="70" alt="Node.js"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/pytest-dark.svg"><img src="assets/tools/pytest-light.svg" width="76" height="70" alt="pytest"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/sqlalchemy-dark.svg"><img src="assets/tools/sqlalchemy-light.svg" width="76" height="70" alt="SQLAlchemy"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/gunicorn-dark.svg"><img src="assets/tools/gunicorn-light.svg" width="76" height="70" alt="Gunicorn"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/openapiinitiative-dark.svg"><img src="assets/tools/openapiinitiative-light.svg" width="76" height="70" alt="OpenAPI"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/postman-dark.svg"><img src="assets/tools/postman-light.svg" width="76" height="70" alt="Postman"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/gradle-dark.svg"><img src="assets/tools/gradle-light.svg" width="76" height="70" alt="Gradle"></picture>
</p>

<p><sub><b>WEB, MOBILE &amp; 3D</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/react-dark.svg"><img src="assets/tools/react-light.svg" width="76" height="70" alt="React"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/nextjs-dark.svg"><img src="assets/tools/nextjs-light.svg" width="76" height="70" alt="Next.js"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/threejs-dark.svg"><img src="assets/tools/threejs-light.svg" width="76" height="70" alt="three.js"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/flutter-dark.svg"><img src="assets/tools/flutter-light.svg" width="76" height="70" alt="Flutter"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/tailwind-dark.svg"><img src="assets/tools/tailwind-light.svg" width="76" height="70" alt="Tailwind CSS"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/vite-dark.svg"><img src="assets/tools/vite-light.svg" width="76" height="70" alt="Vite"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/greensock-dark.svg"><img src="assets/tools/greensock-light.svg" width="76" height="70" alt="GSAP"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/webrtc-dark.svg"><img src="assets/tools/webrtc-light.svg" width="76" height="70" alt="WebRTC"></picture>
</p>

<p><sub><b>CLOUD &amp; DEVOPS</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/docker-dark.svg"><img src="assets/tools/docker-light.svg" width="76" height="70" alt="Docker"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/kubernetes-dark.svg"><img src="assets/tools/kubernetes-light.svg" width="76" height="70" alt="Kubernetes"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/aws-dark.svg"><img src="assets/tools/aws-light.svg" width="76" height="70" alt="AWS"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/gcp-dark.svg"><img src="assets/tools/gcp-light.svg" width="76" height="70" alt="Google Cloud"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/azure-dark.svg"><img src="assets/tools/azure-light.svg" width="76" height="70" alt="Azure"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/githubactions-dark.svg"><img src="assets/tools/githubactions-light.svg" width="76" height="70" alt="GitHub Actions"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/git-dark.svg"><img src="assets/tools/git-light.svg" width="76" height="70" alt="Git"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/github-dark.svg"><img src="assets/tools/github-light.svg" width="76" height="70" alt="GitHub"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/gitlab-dark.svg"><img src="assets/tools/gitlab-light.svg" width="76" height="70" alt="GitLab CI"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/vercel-dark.svg"><img src="assets/tools/vercel-light.svg" width="76" height="70" alt="Vercel"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/linux-dark.svg"><img src="assets/tools/linux-light.svg" width="76" height="70" alt="Linux"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/githubpages-dark.svg"><img src="assets/tools/githubpages-light.svg" width="76" height="70" alt="GitHub Pages"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/k6-dark.svg"><img src="assets/tools/k6-light.svg" width="76" height="70" alt="k6"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/precommit-dark.svg"><img src="assets/tools/precommit-light.svg" width="76" height="70" alt="pre-commit"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/uv-dark.svg"><img src="assets/tools/uv-light.svg" width="76" height="70" alt="uv"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/raspberrypi-dark.svg"><img src="assets/tools/raspberrypi-light.svg" width="76" height="70" alt="Raspberry Pi"></picture>
</p>

<p><sub><b>AUTOMATION &amp; SCRAPING</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/selenium-dark.svg"><img src="assets/tools/selenium-light.svg" width="76" height="70" alt="Selenium"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/scrapy-dark.svg"><img src="assets/tools/scrapy-light.svg" width="76" height="70" alt="Scrapy"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/ffmpeg-dark.svg"><img src="assets/tools/ffmpeg-light.svg" width="76" height="70" alt="FFmpeg"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/openstreetmap-dark.svg"><img src="assets/tools/openstreetmap-light.svg" width="76" height="70" alt="OpenStreetMap"></picture>
</p>

<p><sub><b>DESIGN &amp; DOCS</b></sub></p>
<p>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/figma-dark.svg"><img src="assets/tools/figma-light.svg" width="76" height="70" alt="Figma"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/tools/notion-dark.svg"><img src="assets/tools/notion-light.svg" width="76" height="70" alt="Notion"></picture>
</p>

<sub>Also used, without a logo above: OpenAI API · LlamaIndex · gRPC · Protocol Buffers · XGBoost · LightGBM · PEFT/LoRA · TRL · FAISS · ChromaDB · pgvector · DeepEval · Playwright · dbt · Great Expectations · Power BI · Matplotlib · seaborn · Altair · statsmodels · Groq API · Hugging Face Accelerate · React Three Fiber · Framer Motion · Detectron2 · Riverpod · Canva</sub>

<!-- toolbox:end -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/muhammad-musa-ml/muhammad-musa-ml/output/github-snake-dark.svg">
  <img alt="A snake eating my contribution graph" src="https://raw.githubusercontent.com/muhammad-musa-ml/muhammad-musa-ml/output/github-snake.svg" width="100%">
</picture>

<p align="center"><sub>The snake gets redrawn every night from my contribution graph.</sub></p>
