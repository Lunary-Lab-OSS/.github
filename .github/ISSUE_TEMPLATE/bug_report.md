---
name: Bug report
about: Something does not work as documented
title: "[bug] "
labels: bug
body:
  - type: dropdown
    id: repository
    attributes:
      label: Repository
      options:
        - signal-asr-strategies
        - signal-local-llm
      default: 0
    validations:
      required: true
  - type: textarea
    id: what-happened
    attributes:
      label: What happened?
      description: A clear description of the bug. Redact tokens and personal content from logs.
      placeholder: |
        1. Ran `...`
        2. Expected `...`
        3. Got `...`
    validations:
      required: true
  - type: textarea
    id: environment
    attributes:
      label: Environment
      description: Platform, CPU/GPU, Python version, library version or commit.
      placeholder: "WSL2, RTX 4090, Python 3.12.13, signal-asr-strategies @ abc1234"
    validations:
      required: true
  - type: textarea
    id: logs
    attributes:
      label: Relevant log output
      description: Please no secrets in logs.
      render: shell
