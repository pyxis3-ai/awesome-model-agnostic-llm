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
- [Observability](#observability)
- [Standards & protocols](#standards--protocols)
- [Open weights, open licenses](#open-weights-open-licenses)
- [Articles & talks](#articles--talks)

---

## Serving runtimes

- **[vLLM](https://github.com/vllm-project/vllm)** — High-throughput, memory-efficient LLM inference engine with paged attention. Apache-2.0. OpenAI-compatible API.
- **[Hugging Face Text Generation Inference (TGI)](https://github.com/huggingface/text-generation-inference)** — Production-grade serving for HF models. Apache-2.0.
- **[llama.cpp server](https://github.com/ggml-org/llama.cpp)** — C++ inference for GGUF-quantised models. MIT. Built-in OpenAI-compatible server.
- **[Ollama](https://github.com/ollama/ollama)** — Wraps llama.cpp with model packaging. MIT.
- **[NVIDIA Triton Inference Server](https://github.com/triton-inference-server/server)** — Multi-framework inference server. BSD-3.
- **[KServe](https://github.com/kserve/kserve)** — Kubernetes-native serverless inference. Apache-2.0.
- **[BentoML](https://github.com/bentoml/BentoML)** — Python framework for building production-ready ML services. Apache-2.0.

## Inference routers & gateways

- **[LiteLLM](https://github.com/BerriAI/litellm)** — Unified OpenAI-compatible interface to 100+ LLM providers. MIT.
- **[Portkey AI Gateway](https://github.com/Portkey-AI/gateway)** — Routing, fallbacks, caching, observability. MIT.
- **[OpenRouter](https://openrouter.ai/)** — Hosted multi-model API gateway.
- **[Helicone](https://github.com/Helicone/helicone)** — Open-source LLM gateway with observability. Apache-2.0.

## Evaluation & benchmarking

- **[`pyxis3-ai/vllm-bench`](https://github.com/pyxis3-ai/vllm-bench)** — TTFT, TPOT, throughput, percentile benchmark for OpenAI-compatible endpoints. MIT.
- **[lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)** — Standardised benchmark suite. MIT.
- **[OpenCompass](https://github.com/open-compass/opencompass)** — Multi-task LLM evaluation. Apache-2.0.
- **[BIG-bench](https://github.com/google/BIG-bench)** — Beyond the Imitation Game benchmark. Apache-2.0.

## Observability

- **[Langfuse](https://github.com/langfuse/langfuse)** — Open-source LLM observability + tracing. MIT.
- **[Phoenix](https://github.com/Arize-ai/phoenix)** — ML/LLM tracing. ELv2.
- **[OpenTelemetry GenAI conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/)** — Standard semantic conventions for LLM spans.
- **[Helicone](https://github.com/Helicone/helicone)** — Self-hosted LLM observability. Apache-2.0.

## Standards & protocols

- **[OpenAI Chat Completions API](https://platform.openai.com/docs/api-reference/chat)** — De-facto standard interface. Used by vLLM, TGI, llama.cpp, Ollama, and most routers.
- **[Model Context Protocol (MCP)](https://modelcontextprotocol.io/)** — Open standard for connecting AI tools to data sources. Anthropic-originated but vendor-neutral.
- **[GGUF format](https://github.com/ggml-org/ggml/blob/master/docs/gguf.md)** — Quantised-model file format used by llama.cpp ecosystem.

## Open weights, open licenses

Models with weights you can actually run, not just API access:

- **[Meta Llama 3.x family](https://ai.meta.com/llama/)** — Custom license, broadly commercial.
- **[Mistral / Mixtral](https://mistral.ai/)** — Apache-2.0 weights for base models.
- **[Qwen 2.5](https://github.com/QwenLM/Qwen2.5)** — Apache-2.0.
- **[DeepSeek family](https://github.com/deepseek-ai)** — MIT.
- **[Gemma 2/3](https://ai.google.dev/gemma)** — Custom-permissive Google license.

## Articles & talks

- *[The PYXIS3 Architecture Thesis](https://github.com/pyxis3-ai/pyxis-arch)* — Why model-agnostic has to be an operating-model choice, not just an API contract.
- *[vLLM: Easy, Fast, and Cheap LLM Serving with PagedAttention](https://blog.vllm.ai/2023/06/20/vllm.html)* — Original vLLM paper-blog.

---

## Contributing

PRs welcome. The list aims for:
- ✅ Open-source preferred (vendor-hosted services accepted if they offer a meaningful free tier or strong vendor-portability)
- ✅ Production-relevant (not research-only)
- ✅ Active maintenance (commits in the last 6 months)

Please follow the existing format. Link the project, give a one-line description, note the license.

---

## License

[CC0-1.0](LICENSE) — public domain.
