# Security Policy

## Supported versions

The `main` branch of each repository is the supported version. Security
fixes are released as patch versions.

## Reporting a vulnerability

Please use GitHub's **private security advisories** in the affected
repository (Security → Report a vulnerability). If that is unavailable,
open a private security advisory on the organization's most-active
repository referencing the affected project.

Include:

- the repository and the commit you tested,
- a description of the issue and its impact,
- reproduction steps or a proof of concept,
- any suggested mitigation.

You should receive a response within a few days. Please avoid opening
public issues for anything security-sensitive until a fix is released.

## Scope notes

These libraries deliberately run local models and local servers. The
following are considered expected behaviour, not vulnerabilities, when
documented: binding the transcription server to a non-loopback interface,
executing locally downloaded model weights, and loading model checkpoints
the operator configured. Configured-model provenance (e.g. refusing
checkpoints that advertise different remote code than configured) is in
scope, however.
