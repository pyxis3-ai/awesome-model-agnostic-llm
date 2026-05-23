# Awesome Model-Agnostic LLM

A curated list of tools, frameworks, and resources for running large language models without locking into a single model vendor, cloud, or inference runtime.

**Curated by [PYXIS3](https://pyxis3.ai)**, model-agnostic LLM serving infrastructure.

---

## Why model-agnostic?

The cost of locking into one model vendor compounds. When a better, cheaper, or faster model ships, you want to switch in minutes, not migrate over a quarter. Model-agnostic tooling makes that switch cheap.

This list catalogues the building blocks: serving runtimes, routing layers, evaluation harnesses, observability stacks, and standards that keep your stack portable.

---

## Contents

- [Serving runtimes](#serving-runtimes)
- [Inference routers and gateways](#inference-routers-and-gateways)
- [Evaluation and benchmarking](#evaluation-and-benchmarking)
- [Observability and monitoring](#observability-and-monitoring)
- [Model formats and quantisation](#model-formats-and-quantisation)
- [Open standards and specifications](#open-standards-and-specifications)
- [Vector databases and embeddings](#vector-databases-and-embeddings)
- [Orchestration and deployment](#orchestration-and-deployment)
- [Cost and token economics](#cost-and-token-economics)
- [Adjacent reading](#adjacent-reading)

---

## Serving runtimes

The runtime that loads weights and serves inference. Model-agnostic means it works with multiple model families, supports an OpenAI-compatible wire format, and doesn't tie you to a vendor.

- **[vLLM](https://github.com/vllm-project/vllm)**: high-throughput inference with PagedAttention. The default for OpenAI-compatible serving on GPU.
- **[TGI (Text Generation Inference)](https://github.com/huggingface/text-generation-inference)**: HuggingFace's production-grade serving. Strong on streaming.
- **[Triton Inference Server](https://github.com/triton-inference-server/server)**: NVIDIA's general inference server with TensorRT-LLM backend for LLMs.
- **[SGLang](https://github.com/sgl-project/sglang)**: structured generation language and runtime. RadixAttention for prefix caching.
- **[llama.cpp](https://github.com/ggerganov/llama.cpp)**: CPU, GPU, and Metal inference. The reference for quantised CPU serving.
- **[Ollama](https://github.com/ollama/ollama)**: wraps llama.cpp with model-management UX. OpenAI-compatible API.
- **[MLC LLM](https://github.com/mlc-ai/mlc-llm)**: universal deployment via Apache TVM. Cross-platform including mobile.
- **[LMDeploy](https://github.com/InternLM/lmdeploy)**: production-grade with TurboMind backend.
- **[CTranslate2](https://github.com/OpenNMT/CTranslate2)**: fast transformer inference, CPU-first.

## Inference routers and gateways

Route requests across models, runtimes, or providers. The Funnel layer in a model-agnostic stack.

- **[LiteLLM](https://github.com/BerriAI/litellm)**: unified API across 100+ LLM providers. The reference for client-side routing.
- **[OpenRouter](https://openrouter.ai/)**: hosted multi-provider router with OpenAI-compatible API.
- **[Portkey](https://github.com/Portkey-AI/gateway)**: gateway with fallback, retry, load-balancing, and semantic caching.
- **[Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/)**: edge-deployed router with caching and rate-limiting.
- **[Helicone](https://github.com/Helicone/helicone)**: observability gateway, OpenAI-compatible proxy.

## Evaluation and benchmarking

Measure honestly with the same prompts, the same metrics, and multiple runtimes or models.

- **[vllm-bench](https://github.com/pyxis3-ai/vllm-bench)**: TTFT and TPOT benchmark for OpenAI-compatible endpoints (this org's tool).
- **[lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)**: EleutherAI's standard for academic benchmarks.
- **[OpenAI evals](https://github.com/openai/evals)**: eval framework and curated benchmark suite.
- **[lighteval](https://github.com/huggingface/lighteval)**: HuggingFace's eval framework.
- **[Promptfoo](https://github.com/promptfoo/promptfoo)**: prompt-level evaluation and regression testing.
- **[DeepEval](https://github.com/confident-ai/deepeval)**: unit-test framework for LLMs.

## Observability and monitoring

What's serving, how fast, at what cost, drifting how. The Lens layer.

- **[lens](https://github.com/pyxis3-ai/lens)**: Kubernetes-native observability with LLM-endpoint discovery (this org's tool).
- **[Langfuse](https://github.com/langfuse/langfuse)**: tracing and analytics for LLM applications.
- **[Arize Phoenix](https://github.com/Arize-ai/phoenix)**: open-source LLM and ML observability with evaluation.
- **[OpenLLMetry](https://github.com/traceloop/openllmetry)**: OpenTelemetry conventions for LLM observability.
- **[Helicone](https://github.com/Helicone/helicone)**: logging, analytics, and caching gateway.

## Model formats and quantisation

Portable model weights and the tools that compress them.

- **[GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md)**: successor to GGML. llama.cpp's format. Mainstream for CPU and Mac inference.
- **[safetensors](https://github.com/huggingface/safetensors)**: safe alternative to pickle. Default for HuggingFace weights.
- **[bitsandbytes](https://github.com/bitsandbytes-foundation/bitsandbytes)**: 8-bit and 4-bit quantisation kernels.
- **[GPTQ](https://github.com/IST-DASLab/gptq)**: post-training quantisation, 4-bit.
- **[AWQ](https://github.com/mit-han-lab/llm-awq)**: Activation-aware Weight Quantisation. Better quality than GPTQ at 4-bit.
- **[ExLlamaV2](https://github.com/turboderp/exllamav2)**: fast 4-bit and EXL2 quantisation runtime.

## Open standards and specifications

The interface standards that make model-agnostic possible.

- **[OpenAI Chat Completions](https://platform.openai.com/docs/api-reference/chat)**: de facto standard for chat completions API.
- **[OpenAI Embeddings](https://platform.openai.com/docs/api-reference/embeddings)**: de facto standard for embedding API.
- **[Anthropic Messages API](https://docs.anthropic.com/en/api/messages)**: increasingly adopted; many gateways translate to and from this.
- **[Model Context Protocol (MCP)](https://github.com/modelcontextprotocol)**: open standard for tool and context integration.
- **[ONNX](https://onnx.ai/)**: Open Neural Network Exchange. Cross-runtime model format.

## Vector databases and embeddings

The retrieval side of model-agnostic AI.

- **[sentence-transformers](https://github.com/UKPLab/sentence-transformers)**: default for open-weight embeddings.
- **[sqlite-vec](https://github.com/asg017/sqlite-vec)**: SQLite vector search extension. Embeddable.
- **[Qdrant](https://github.com/qdrant/qdrant)**: open-source vector database, Rust.
- **[Milvus](https://github.com/milvus-io/milvus)**: scalable vector database, CNCF graduated.
- **[Chroma](https://github.com/chroma-core/chroma)**: developer-friendly vector store.
- **[pgvector](https://github.com/pgvector/pgvector)**: PostgreSQL vector extension.

## Orchestration and deployment

Run LLMs on Kubernetes, cloud, or on-prem.

- **[KServe](https://github.com/kserve/kserve)**: Kubernetes-native ML serving. Generic, with LLM support via runtimes.
- **[Seldon Core](https://github.com/SeldonIO/seldon-core)**: MLOps platform with LLM inference path.
- **[BentoML](https://github.com/bentoml/BentoML)**: model serving framework.
- **[Ray Serve](https://docs.ray.io/en/latest/serve/index.html)**: distributed serving on Ray.
- **[KEDA](https://github.com/kedacore/keda)**: event-driven autoscaling, essential for scale-to-zero LLM serving.
- **[Knative](https://github.com/knative/serving)**: serverless Kubernetes. Scale-to-zero primitive.

## Cost and token economics

Measure and control LLM spend.

- **[OpenCost](https://github.com/opencost/opencost)**: Kubernetes cost monitoring.
- **[Helicone cost dashboards](https://github.com/Helicone/helicone)**: per-application LLM cost.
- **[Langfuse cost tracking](https://langfuse.com/docs/integrations/litellm)**: per-trace cost.

## Adjacent reading

- **[PYXIS3 architecture thesis](https://github.com/pyxis3-ai/pyxis-arch)**: the operating-model argument behind this category.
- **[Stas Bekman: LLM/VLM training and inference scaling](https://github.com/stas00/ml-engineering)**: practical large-scale ML engineering reference.
- **[The Vector Database Cambrian Explosion](https://www.gradient.pub/p/the-vector-database-cambrian-explosion)**: context for the retrieval side.

---

## Contributing

PRs welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md). Add new entries in alphabetical order within each section, with a one-line description.

## Maintenance

Supporting documentation lives in `docs/`, example inputs live in `examples/`, and lightweight validation notes live in `tests/smoke/`.
