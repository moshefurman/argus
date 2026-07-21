# Releasing Argus (maintainer notes)

Argus is **closed source**. This public repo holds only the README, the
`install.ps1`, the LICENSE, and the compiled **Releases** that users download.
The Go source lives in a separate **private** repo.

## The flow

1. In the **private source repo**, build and publish a release with the helper:

   ```powershell
   .\release.ps1 -Version v0.1.0 -PublicRepo moshefurman/argus
   ```

   That script:
   - builds `argus.exe` (CGO off) via `build.ps1`,
   - bundles it with `configs/` (Sysmon config, patterns, lolbin rules, example
     config) and `install.ps1` into `argus-windows-amd64.zip`,
   - creates a GitHub Release `v0.1.0` on the **public** repo and uploads the zip
     (and the bare `argus.exe`) via the `gh` CLI.

2. The public repo's `install.ps1` downloads
   `releases/latest/download/argus-windows-amd64.zip`, so the one-liner keeps
   working with no further changes.

## One-time setup

- Install the GitHub CLI (`gh`) and `gh auth login` with an account that can
  create releases on the public repo.
- The `install.ps1`, README, and links are already set to `moshefurman/argus`
  (change only if you fork under a different owner/repo).
- Turn on **Discussions** in the public repo (Settings -> Features) so the
  community links work.

## Versioning

Use `vMAJOR.MINOR.PATCH` tags. The installer's `-Version latest` always fetches
the newest release; users can pin with `-Version v0.1.0`.
