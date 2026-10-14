# Lunary Lab OSS

Open-source building blocks for a local, voice-driven AI coding assistant.

The goal is a fast assistant that can listen, think, and write code in real
time on consumer hardware, with no cloud dependency. These libraries are the
reusable pieces of that stack: clean interfaces for speech recognition and
local LLM inference.

## Repositories

### [signal-asr-strategies](https://github.com/Lunary-Lab-OSS/signal-asr-strategies)

Cross-platform speech recognition behind one strategy interface.

- WhisperKit (Core ML / Apple Neural Engine) on macOS
- sherpa-onnx with NVIDIA Parakeet TDT on Linux, WSL2, and CUDA
- faster-whisper (CTranslate2) as a portable CPU/GPU option
- OpenAI-compatible local transcription server with streaming upload caps,
  decode budgets, and bounded admission control
- Non-root Docker image, exercised end to end in CI

### [signal-local-llm](https://github.com/Lunary-Lab-OSS/signal-local-llm)

Local LLM inference and routing for the same stack.

- Transformers, ExLlamaV2, and MLX loaders with backend-first dispatch,
  collision-resistant model caches, and resumable downloads
- Cascading intent router (reflex patterns, difficulty estimation, and a
  thinking-budget curve) with strict label parsing
- RouteLLM-style model routing with a single-tower difficulty regressor and
  provenance-checked checkpoints
- Remote model code is opt-in and requires a pinned revision

## Engineering practices

Every pull request in both libraries runs:

- ruff lint and format checks, plus blocking mypy typechecks
- the full offline unit suite on Python 3.12 and 3.13 with enforced coverage
  gates (no model downloads, no GPU required)
- wheel and sdist builds with out-of-tree import checks
- `pip-audit` dependency audits of every locked runtime profile
- a Linux integration track against real models: Qwen2.5-0.5B-Instruct for
  LLM inference, and sherpa-onnx speech recognition through the Docker image
  for ASR

Dependencies are locked with [uv](https://docs.astral.sh/uv/), and heavy
backends are tested through injectable seams so the unit suites stay fast and
deterministic.

## Contributing

See [CONTRIBUTING.md](https://github.com/Lunary-Lab-OSS/.github/blob/main/.github/CONTRIBUTING.md).
Bug reports and feature requests are welcome as issues in the relevant
repository. Report security issues privately as described in
[SECURITY.md](https://github.com/Lunary-Lab-OSS/.github/blob/main/.github/SECURITY.md).

Both libraries are licensed GPL-3.0-or-later.
