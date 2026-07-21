# Security Policy

Argus is a security tool, so we take issues in it seriously.

## Reporting a vulnerability

Please **do not** open a public issue for security vulnerabilities.

Instead, use GitHub's **private vulnerability reporting**: on this repo, go to the
**Security** tab and click **"Report a vulnerability"**. Include:

- a description of the issue and its impact,
- steps to reproduce (or a proof of concept),
- the Argus version (the release tag).

You'll get an acknowledgement, and we'll work with you on a fix and coordinated
disclosure.

## Scope / good to know

- Argus runs **locally** and makes no outbound connections of its own.
- The dashboard and rule-editor API have **no authentication** and are intended
  to be bound to `127.0.0.1` only. Exposing them on `0.0.0.0` is unsupported and
  insecure.
- Reading the Windows Security log (authentication detections) requires the
  service to run as SYSTEM/administrator. Sysmon-based detection does not.
