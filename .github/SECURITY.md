# Security policy

## Supported versions

Report issues against the affected repository's current `main` branch.
No maintenance schedule for older versions or response-time guarantee is
stated. Repository-specific security policies take precedence over this
organization default.

## Private reporting

GitHub private vulnerability reporting is not enabled in these repositories
as of the last checked date: 2026-10-13. Therefore no confidential
vulnerability-reporting route is currently published. Until the maintainers
publish a verified private route, do not include security-sensitive details
in public issues, discussions, or email.

Once private vulnerability reporting is enabled for the affected repository,
use **Security → Report a vulnerability** there. Include the repository and
tested commit, impact, reproduction steps, and any suggested mitigation.
Remove unrelated secrets and personal data.

## Trust boundaries

Operators choose model sources, revisions, and deployment exposure. Explicit
opt-in to trusted custom model code is a trust decision, not a sandbox;
model files are not inherently safe because they are locally downloaded or
configured. Unexpected code execution, unsafe deserialization, bypasses of
remote-code opt-in or revision/provenance checks, and crossing configured
trust boundaries remain in scope.

The ASR server has no built-in authentication. Non-loopback deployment needs
an authenticated TLS reverse proxy and network access controls. Choosing a
non-loopback bind is not itself a vulnerability; defects in request handling
or documented security controls are not excluded on that basis.

Upload/decode limits and bounded admission do not make native inference or
model loading interruptible. Hard runtime and memory isolation require an
external supervisor/process boundary. Failures of documented limits remain
reportable; do not assume a hard execution deadline where none is promised.
