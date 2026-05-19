# Awesome Model-Agnostic LLM 🦜

A curated list of tools, frameworks, and resources for running large language models without locking into a single model vendor, cloud, or inference runtime.

**Curated by [PYXIS3](https://pyxis3.ai)** — model-agnostic LLM serving infrastructure.

---

## Why model-agnostic?

The cost of locking into one model vendor compounds. When a better/cheaper/faster model ships, you want to switch in minutes — not migrate over a quarter. Model-agnostic tooling makes that switch cheap.

This list catalogues the building blocks: serving runtimes, routing layers, evaluation harnesses, observability stacks, and standards that keep your stack portable.

---

## Contents

- [Serving runtimes](#serving-runtimes)
- [Inference routers & gateways](#inference-routers--gateways)
- [Evaluation & benchmarking](#evaluation--benchmarking)
- [Observability & monitoring](#observability--monitoring)
- [Model formats & quantisation](#model-formats--quantisation)
- [Open standards & specifications](#open-standards--specifications)
- [Vector databases & embeddings](#vector-databases--embeddings)
- [Orchestration & deployment](#orchestration--deployment)
- [Cost & token economics](#cost--token-economics)
- [Adjacent reading](#adjacent-reading)

---

## Serving runtimes

The runtime that loads weights and serves inference. Model-agnostic means: works with multiple model families, supports an OpenAI-compatible wire format, doesn't tie you to a vendor.

- **[vLLM](https://github.com/vllm-project/vllm)** — High-throughput inference with PagedAttention. The default for OpenAI-compatible serving on GPU.
- **[TGI (Text Generation Inference)](https://github.com/huggingface/text-generation-inference)** — HuggingFace's production-grade serving. Strong on streaming.
- **[Triton Inference Server](https://github.com/triton-inference-server/server)** — NVIDIA's general inference server with TensorRT-LLM backend for LLMs.
- **[SGLang](https://github.com/sgl-project/sglang)** — Structured generation language + runtime. RadixAttention for prefix caching.
- **[llama.cpp](https://github.com/ggerganov/llama.cpp)** — CPU/GPU/Metal inference. The reference for quantised CPU serving.
- **[Ollama](https://github.com/ollama/ollama)** — Wraps llama.cpp with model-management UX. OpenAI-compatible API.
- **[MLC LLM](https://github.com/mlc-ai/mlc-llm)** — Universal deployment via Apache TVM. Cross-platform including mobile.
- **[LMDeploy](https://github.com/InternLM/lmdeploy)** — Production-grade with TurboMind backend.
- **[CTranslate2](https://github.com/OpenNMT/CTranslate2)** — Fast transformer inference, CPU-first.

## Inference routers & gateways

Route requests across models / runtimes / providers. The Funnel layer in a model-agnostic stack.

- **[LiteLLM](https://github.com/BerriAI/litellm)** — Unified API across 100+ LLM providers. The reference for client-side routing.
- **[OpenRouter](https://openrouter.ai/)** — Hosted multi-provider router with OpenAI-compatible API.
- **[Quotaflow](https://quotaflow.ai/)** — OpenAI-compatible relay for governed quota pools, temporary access, overflow credits, and resource efficiency.
- **[Portkey](https://github.com/Portkey-AI/gateway)** — Gateway with fallback, retry, load-balancing, semantic caching.
- **[Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/)** — Edge-deployed router with caching + rate-limiting.
- **[Helicone](https://github.com/Helicone/helicone)** — Observability gateway, OpenAI-compatible proxy.

## Evaluation & benchmarking

Measure honestly — same prompts, same metrics, multiple runtimes/models.

- **[vllm-bench](https://github.com/pyxis3-ai/vllm-bench)** — TTFT + TPOT benchmark for OpenAI-compatible endpoints (this org's tool).
- **[lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)** — EleutherAI's standard for academic benchmarks.
- **[OpenAI evals](https://github.com/openai/evals)** — Eval framework + curated benchmark suite.
- **[lighteval](https://github.com/huggingface/lighteval)** — HuggingFace's eval framework.
- **[Promptfoo](https://github.com/promptfoo/promptfoo)** — Prompt-level evaluation + regression testing.
- **[DeepEval](https://github.com/confident-ai/deepeval)** — Unit-test framework for LLMs.

## Observability & monitoring

What's serving, how fast, at what cost, drifting how. The Lens layer.

- **[lens](https://github.com/pyxis3-ai/lens)** — Kubernetes-native observability with LLM-endpoint discovery (this org's tool).
- **[Langfuse](https://github.com/langfuse/langfuse)** — Tracing + analytics for LLM applications.
- **[Arize Phoenix](https://github.com/Arize-ai/phoenix)** — Open-source LLM/ML observability + evaluation.
- **[OpenLLMetry](https://github.com/traceloop/openllmetry)** — OpenTelemetry conventions for LLM observability.
- **[Helicone](https://github.com/Helicone/helicone)** — Logging + analytics + caching gateway.

## Model formats & quantisation

Portable model weights and the tools that compress them.

- **[GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md)** — Successor to GGML. llama.cpp's format. Mainstream for CPU/Mac inference.
- **[safetensors](https://github.com/huggingface/safetensors)** — Safe alternative to pickle. Default for HuggingFace weights.
- **[bitsandbytes](https://github.com/bitsandbytes-foundation/bitsandbytes)** — 8-bit and 4-bit quantisation kernels.
- **[GPTQ](https://github.com/IST-DASLab/gptq)** — Post-training quantisation, 4-bit.
- **[AWQ](https://github.com/mit-han-lab/llm-awq)** — Activation-aware Weight Quantisation. Better quality than GPTQ at 4-bit.
- **[ExLlamaV2](https://github.com/turboderp/exllamav2)** — Fast 4-bit/EXL2 quantisation runtime.

## Open standards & specifications

The interface standards that make model-agnostic possible.

- **[OpenAI Chat Completions](https://platform.openai.com/docs/api-reference/chat)** — De facto standard for chat completions API.
- **[OpenAI Embeddings](https://platform.openai.com/docs/api-reference/embeddings)** — De facto standard for embedding API.
- **[Anthropic Messages API](https://docs.anthropic.com/en/api/messages)** — Increasingly adopted; many gateways translate to/from this.
- **[Model Context Protocol (MCP)](https://github.com/modelcontextprotocol)** — Open standard for tool/context integration.
- **[ONNX](https://onnx.ai/)** — Open Neural Network Exchange. Cross-runtime model format.

## Vector databases & embeddings

The retrieval side of model-agnostic AI.

- **[sentence-transformers](https://github.com/UKPLab/sentence-transformers)** — Default for open-weight embeddings.
- **[sqlite-vec](https://github.com/asg017/sqlite-vec)** — SQLite vector search extension. Embeddable.
- **[Qdrant](https://github.com/qdrant/qdrant)** — Open-source vector database, Rust.
- **[Milvus](https://github.com/milvus-io/milvus)** — Scalable vector database, CNCF graduated.
- **[Chroma](https://github.com/chroma-core/chroma)** — Developer-friendly vector store.
- **[pgvector](https://github.com/pgvector/pgvector)** — PostgreSQL vector extension.

## Orchestration & deployment

Run LLMs on Kubernetes / cloud / on-prem.

- **[KServe](https://github.com/kserve/kserve)** — Kubernetes-native ML serving. Generic; LLM support via runtimes.
- **[Seldon Core](https://github.com/SeldonIO/seldon-core)** — MLOps platform with LLM inference path.
- **[BentoML](https://github.com/bentoml/BentoML)** — Model serving framework.
- **[Ray Serve](https://docs.ray.io/en/latest/serve/index.html)** — Distributed serving on Ray.
- **[KEDA](https://github.com/kedacore/keda)** — Event-driven autoscaling — essential for scale-to-zero LLM serving.
- **[Knative](https://github.com/knative/serving)** — Serverless Kubernetes. Scale-to-zero primitive.

## Cost & token economics

Measure and control LLM spend.

- **[OpenCost](https://github.com/opencost/opencost)** — Kubernetes cost monitoring.
- **[Helicone cost dashboards](https://github.com/Helicone/helicone)** — Per-application LLM cost.
- **[Langfuse cost tracking](https://langfuse.com/docs/integrations/litellm)** — Per-trace cost.

## Adjacent reading

- **[PYXIS3 architecture thesis](https://github.com/pyxis3-ai/pyxis-arch)** — the operating-model argument behind this category
- **[Stas Bekman: LLM/VLM training and inference scaling](https://github.com/stas00/ml-engineering)** — practical large-scale ML engineering reference
- **[The Vector Database Cambrian Explosion](https://www.gradient.pub/p/the-vector-database-cambrian-explosion)** — context for the retrieval side

---

## Contributing

PRs welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md). Add new entries in alphabetical order within each section, with a 1-line description.
