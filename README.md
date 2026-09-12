# Lunary Lab OSS

Open-source libraries from a hands-free, voice-driven AI coding stack.

Everything here is built for one goal: a fast voice assistant that can listen,
think, and write code in real time on consumer hardware.

## Repositories

### [signal-asr-strategies](https://github.com/Lunary-Lab-OSS/signal-asr-strategies)

Cross-platform speech recognition behind one strategy interface:

- WhisperKit (Core ML / Apple Neural Engine) on macOS
- Sherpa-ONNX with NVIDIA Parakeet TDT on Linux, WSL2, and CUDA
- NeMo and faster-whisper backends
- OpenAI-compatible local transcription server

### [signal-local-llm](https://github.com/Lunary-Lab-OSS/signal-local-llm)

Local LLM inference strategies for the same stack:

- ExLlamaV2, vLLM, MLX, and Transformers loaders with speculative decoding
- Cascading intent router: reflex pattern match, difficulty estimator, and a
  thinker layer that maps difficulty to a reasoning token budget
- RouteLLM-style routing with a single-tower difficulty regressor

## Engineering notes

- Both libraries are test-first: 49 and 47 unit tests, no model downloads or
  GPU needed to run the suite
- CI runs ruff lint plus the full test matrix on Python 3.12 and 3.13
- Pre-commit hooks include a secrets scan on every commit
- GPL-3.0 licensed: use and build on them freely, keep derivatives open

## Why this exists

The full stack is a personal voice coding assistant: Windows audio capture
streams over Hyper-V sockets into a WSL2 inference engine, where speech
recognition, intent routing, and code generation models share one GPU. These
two libraries are the pieces that generalize: clean interfaces for speech
recognition and local LLM inference that work on any platform.

Feedback and issues welcome.
