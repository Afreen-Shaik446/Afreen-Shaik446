# Hi, I'm Afreen Shaik

**Prospective PhD Applicant | ML Systems | LLM Inference & Serving | Distributed Systems**

I am a computer science graduate and software engineer interested in **research at the intersection of machine learning and systems**. My work combines academic training in parallel computing, deep learning, and algorithms with experience building and operating distributed backend and cloud systems.

My central research interest is **efficient LLM inference under changing workloads**: when should a serving system adapt its scheduling decisions, and when is a well-tuned fixed policy the better choice?

## Independent research | 2026 - ongoing

### Adaptive Scheduling for LLM Inference Under Bursty Workloads

**Research question:** Can lightweight workload signals guide request scheduling to improve high-percentile time-to-first-token (TTFT) while preserving throughput and responsiveness for long requests?

I developed and evaluated an experimental, workload-aware scheduling prototype for **vLLM 0.32.0**, examining queue pressure, heterogeneous request lengths, per-step scheduled-token budgets, and latency-throughput tradeoffs. The prototype implementation included AI-assisted coding; the study is an independent research effort, not a faculty-supervised or published project.

**Exploratory GPU pilot (November 2026)**

- **Environment:** NVIDIA RTX A6000; Qwen2.5-1.5B-Instruct; vLLM 0.32.0.
- **Design:** One identical synthetic bursty mixed-length request trace per policy; 128 requests in each of five conditions (four fixed scheduled-token limits and one adaptive policy).
- **Execution:** All **640 / 640 requests completed**. Engine logs documented live adaptive scheduled-token limits of **512, 1,024, and 2,048**. An audit of the request records reproduced the reported measurements.

| Scheduling policy | Client-observed P99 TTFT | Output throughput |
| --- | ---: | ---: |
| Fixed 256 | 7.99 s | 1,286 tokens/s |
| Fixed 512 | 6.14 s | 1,409 tokens/s |
| Fixed 1,024 | 4.23 s | 1,585 tokens/s |
| **Fixed 2,048** | **3.10 s** | **1,776 tokens/s** |
| Experimental adaptive | 5.68 s | 1,435 tokens/s |

**Finding:** The adaptive policy changed scheduling budgets during real GPU serving, but **did not outperform the strongest fixed baseline** in this pilot. Compared with fixed 2,048, its P99 TTFT was 83.3% higher and output throughput was 19.2% lower. This negative result motivates a more precise systems question: **under what workload regimes does adaptive scheduling justify its overhead and tradeoffs?**

**Scope and limitations:** These are exploratory **single-seed, single-model, single-GPU, single-workload** findings, not a statistically established improvement, a general comparison against published adaptive schedulers, or a peer-reviewed publication. TTFT is client-observed; throughput is total output tokens divided by experiment wall-clock duration. Further repeated experiments, workload sweeps, and fairness measurements are planned. The code snapshot and raw logs are retained, while a public reproducibility package is being prepared.

### Current research directions

- Adaptive scheduling and batching for prefill/decode interference
- P95/P99 tail latency, throughput, and long-request fairness
- KV-cache pressure, queueing, and heterogeneous request lengths
- Controlled benchmarks, workload shifts, baselines, and reproducibility

## Education and academic foundations

**Pace University | Seidenberg School of Computer Science and Information Systems**  
**M.S. in Computer Science, May 2024 | GPA: 3.81 / 4.00**

Graduate coursework includes Parallel Computing, Deep Learning, Artificial Intelligence, Algorithms and Computing Theory, Data Science, and Database Management Systems.

- **Healthify healthcare portal (CS 691 capstone):** Faculty-supervised team project under **Professor Yuri Chernak**; earned an **A**. Worked on a multi-module healthcare management application and collaborative engineering delivery.
- **NYC Yellow Taxi data analysis:** Graduate coursework investigating 2020 taxi records through data exploration, cleaning, validation, and distribution-shift analysis.

**Vignan's Lara Institute of Technology & Science | Jawaharlal Nehru Technological University, Kakinada**  
**B.Tech. in Computer Science and Engineering, May 2019 | First Class with Distinction**

My undergraduate studies and team-based final-year engineering project helped build a foundation in problem solving, software development, and technical collaboration.

## Selected software and systems projects

My public engineering repositories demonstrate practical foundations relevant to experimental systems research; they are **demonstration projects**, not claims of deployed research systems.

| Project | Focus and connection to systems research |
| --- | --- |
| [async-worker-pipeline](https://github.com/Afreen-Shaik446/async-worker-pipeline) | RabbitMQ work queues, backoff/retries, dead-letter handling, MongoDB task persistence; useful for thinking about queueing and backpressure. |
| [api-observability-starter](https://github.com/Afreen-Shaik446/api-observability-starter) | FastAPI metrics, request IDs, structured logging, Prometheus/Grafana; instrumentation for understanding system behavior. |
| [fastapi-service-template](https://github.com/Afreen-Shaik446/fastapi-service-template) | API service structure, health/readiness probes, JWT, Docker, Kubernetes, CI; reliable service engineering. |
| [k8s-reliability-toolkit](https://github.com/Afreen-Shaik446/k8s-reliability-toolkit) | Autoscaling, rollout strategies, disruption budgets, network policy, dashboards, and runbooks. |

## Technical background

**Languages and tools:** Python, Java, SQL, vLLM, PyTorch, FastAPI, Flask, Docker, Kubernetes, Git, Linux  
**Systems and data:** Distributed systems, REST APIs, MongoDB, Kafka, Spark, async messaging, metrics, tracing, and reliability engineering

---

*My goal is to pursue rigorous, reproducible ML-systems research that explains not only when an approach works, but also when it does not.*
