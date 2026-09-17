---
name: Feature request
about: Suggest an improvement
title: "[feat] "
labels: enhancement
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
    id: problem
    attributes:
      label: What problem does this solve?
      description: Describe the use case; voice-assistant workflows are especially relevant.
    validations:
      required: true
  - type: textarea
    id: proposal
    attributes:
      label: Proposed solution
      description: What should change, and what should stay the same?
