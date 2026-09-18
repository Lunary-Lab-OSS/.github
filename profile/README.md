# Lunary Lab OSS

Libraries for a local, voice-driven coding stack.

## Repositories

- [signal-asr-strategies](https://github.com/Lunary-Lab-OSS/signal-asr-strategies):
  speech-recognition strategies and a local transcription server. The Linux
  CPU integration track exercises sherpa-onnx and the container using
  synthesized espeak-ng speech, not human recordings.
- [signal-local-llm](https://github.com/Lunary-Lab-OSS/signal-local-llm):
  local model loading, generation, and intent routing. Its Linux CPU
  integration track uses Transformers with Qwen/Qwen2.5-0.5B-Instruct;
  the model revision is currently unpinned.

## Limits and verification

The ASR server limits uploads and decoded audio and bounds admission to
decode/inference work. Native inference and model loading are not generally
interruptible; admission deadlines are not hard execution deadlines or RAM
guarantees. Non-loopback access requires external authentication and network
controls.

Both repositories define offline unit tests, coverage gates, lint/format,
typechecks, build/import checks, and dependency audits in CI. These definitions
are not a claim that every current run passes. Mocked backend coverage and
Linux CPU integration do not prove CUDA or native Windows/macOS hardware
support; those paths remain unverified by these tracks.

NeMo and vLLM integrations are currently unsupported. Matrix Factorization
routing is disabled; SOTA routing requires a trained compatible checkpoint
and a locally cached backbone. Consult each repository's README for supported
dependency profiles and migration constraints.

Both libraries are licensed GPL-3.0-or-later; see their license files for terms.

## Participation

Open ordinary bug reports and feature requests in the affected repository.
See the [contribution guide](https://github.com/Lunary-Lab-OSS/.github/blob/main/.github/CONTRIBUTING.md)
for local checks.

Do not post vulnerabilities publicly. Read the
[security policy](https://github.com/Lunary-Lab-OSS/.github/blob/main/.github/SECURITY.md):
private vulnerability reporting was disabled at the last verified check,
and maintainers need to configure a private route.
