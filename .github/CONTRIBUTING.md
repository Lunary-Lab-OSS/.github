# Contributing to Lunary Lab OSS

Thanks for your interest! These libraries power a personal voice-driven
coding stack, and contributions that make them more dependable, better
tested, or usable on more platforms are welcome.

## Getting started

1. Fork and clone the repository you want to work on.
2. Install the dev environment (requires Python 3.12+ and [uv](https://docs.astral.sh/uv/)):

   ```bash
   uv sync --locked --extra dev --extra server   # signal-asr-strategies
   uv sync --locked --group dev                  # signal-local-llm
   ```

3. Run the checks before you write code, so you start from a known-good
   baseline:

   ```bash
   uv run pytest tests/ -q
   uvx ruff@0.15.14 check .
   ```

## What we look for

- **Tests that prove behaviour.** A regression test accompanies every fix
  and fails on the previous behaviour. Crash-only oracles are not enough;
  compare against a reference when possible.
- **No silent fallbacks.** Unknown engines/backends/devices raise; broken
  checkpoints fail; partial downloads resume. Please keep it that way.
- **Offline unit suite.** Unit tests must not download models or need a
  GPU. Use injectable seams and strict fakes; put real-model coverage in
  the integration track.
- **Honest docs.** If a platform or parameter is unsupported, say so in
  the README rather than letting users discover it at runtime.

## Pull requests

- Use [conventional commit](https://www.conventionalcommits.org/) titles
  (`fix: ...`, `feat: ...`, `test: ...`).
- Keep PRs focused; split unrelated changes into separate PRs.
- CI must pass: lint, format, mypy, tests with the coverage gate, and the
  wheel build. The integration track runs the real-model tests.

## Reporting bugs

Open an issue with the reproduction steps, the exact version/commit, and
the platform (Linux/WSL2/Windows/macOS, CPU/GPU). Log output is helpful —
but please redact tokens and personal content first.

## Security

Do not open public issues for suspected vulnerabilities; use GitHub
security advisories in the affected repository.
