# Security policy

## Supported versions

Security fixes are made on the `main` branch of each repository.
Repository-specific security policies take precedence over this
organization default.

## Reporting a vulnerability

Please report vulnerabilities privately through GitHub's
**Security → Report a vulnerability** form in the affected repository.
Do not open public issues, discussions, or pull requests for suspected
vulnerabilities.

Include:

- the repository and commit you tested
- the impact and affected configuration
- steps to reproduce, ideally a minimal proof of concept
- any suggested mitigation

Remove unrelated secrets and personal data from your report.

## Scope

In scope:

- unexpected code execution or unsafe deserialization
- bypasses of the remote-code opt-in or the pinned-revision and checkpoint
  provenance checks
- defects in request handling, upload limits, decode budgets, or admission
  control in the ASR server

Deployment guidance:

- Model sources and revisions are chosen by the operator. Enabling trusted
  remote model code is an explicit trust decision.
- The ASR server binds to loopback by default and does not implement
  authentication. For network deployments, place it behind an authenticated
  TLS reverse proxy with appropriate access controls.
- For hard CPU-time and memory isolation of native inference, run the server
  under a process supervisor or container resource limits.
