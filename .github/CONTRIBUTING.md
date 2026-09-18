# Contributing

Fork and clone the affected repository. Use Python 3.12+ and
[uv](https://docs.astral.sh/uv/); follow repository-specific instructions
where they differ from these organization defaults.

## Local checks

Run commands inside the relevant repository. ASR unit checks need ffmpeg:

```bash
uv sync --locked --extra dev --extra server
uv run --locked --extra dev --extra server pytest tests/ -q -m "not integration" --cov=signal_asr --cov-fail-under=85
uv run --locked --extra dev --extra server mypy signal_asr
```

For `signal-local-llm`, use the CPU development profile:

```bash
uv sync --locked --group dev --extra cpu
uv run --locked --group dev --extra cpu pytest tests/ -q -m "not integration" --cov=signal_llm --cov-fail-under=80
uv run --locked --group dev --extra cpu mypy signal_llm
```

For either repository:

```bash
uvx ruff@0.15.14 check .
uvx ruff@0.15.14 format --check .
uv build
```

Unit tests must not download models or require a GPU. Integration tests
download real models and are separate from unit checks. The ASR Linux CPU
integration profile matches its workflow:

```bash
uv sync --locked --extra dev --extra server --extra cpu
SIGNAL_ASR_INTEGRATION=1 uv run --locked --extra dev --extra server --extra cpu pytest tests/test_integration.py -q
```

That track requires ffmpeg, espeak-ng, and Docker; speech fixtures are
synthesized, not human recordings. LLM integration uses
`uv sync --locked --group dev --extra cpu --extra transformers`;
see its `.github/workflows/ci.yml` for the model, cache, and skip-rejection
checks. Neither track establishes CUDA or native Windows/macOS hardware support.

## Pull requests

- Keep changes focused; use conventional titles such as `fix: ...`.
- Add regression tests that assert the intended result, not just absence of crashes.
- Keep unsupported configurations explicit; do not add silent fallbacks.
- Update documentation when behaviour or dependency profiles change.
- Run the checks above and consult the affected repository's current workflow
  for build/import, integration, and dependency-audit requirements.

## Reporting

Use issues for reproducible bugs and feature requests. Redact secrets,
prompts, transcripts, and personal data. For suspected vulnerabilities,
follow [SECURITY.md](SECURITY.md), including its reporting-availability warning;
do not disclose them in public issues.
