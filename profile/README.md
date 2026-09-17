# Lunary Lab OSS

Open-source libraries from a hands-free, voice-driven AI coding stack.

Everything here is built for one goal: a fast voice assistant that can listen,
think, and write code in real time on consumer hardware.

## Repositories

### [signal-asr-strategies](https://github.com/Lunary-Lab-OSS/signal-asr-strategies)

Cross-platform speech recognition behind one strategy interface:

- WhisperKit (Core ML / Apple Neural Engine) on macOS
- Sherpa-ONNX with NVIDIA Parakeet TDT on Linux, WSL2, and CUDA
- faster-whisper and NeMo backends
- OpenAI-compatible local transcription server with bounded-resource
  guarantees (streaming body caps, decode budgets, admission control)

### [signal-local-llm](https://github.com/Lunary-Lab-OSS/signal-local-llm)

Local LLM inference strategies for the same stack:

- ExLlamaV2, vLLM, MLX, and Transformers loaders with backend-first
  dispatch, collision-resistant model caches, and resumable downloads
- Cascading intent router: reflex patterns, difficulty estimators, and a
  quadratic difficulty-to-thinking-budget curve with strict label parsing
- RouteLLM-style routing with a single-tower difficulty regressor and
  strict checkpoint validation

## Engineering notes

- Both libraries run their full unit suites offline (no model downloads,
  no GPU) with enforced coverage gates and blocking typechecks in CI.
- CI runs ruff lint/format, mypy, the test matrix on Python 3.12 and 3.13,
  wheel build + out-of-tree import checks, and dependency audits on every
  pull request.
- Heavy backends are exercised through injectable seams in unit tests and
  against real models in the integration track.
- Pre-commit hooks include lint, format, and the unit suite.
- GPL-3.0 licensed: use and build on them freely, keep derivatives open.

## Why this exists

The full stack is a personal voice coding assistant: Windows audio capture
streams over Hyper-V sockets into a WSL2 inference engine, where speech
recognition, intent routing, and code generation models share one GPU. These
two libraries are the pieces that generalize: clean interfaces for speech
recognition and local LLM inference that work on any platform.

## Support

These are actively maintained personal projects. Open an issue in the
relevant repository; voice-related feature requests are especially welcome.

## Security

Report vulnerabilities privately through GitHub security advisories in the
affected repository. Please do not open public issues for suspected
vulnerabilities.
