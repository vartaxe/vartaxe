---
title: Windows endpoint automation
description: Focused PowerShell tools for ConfigMgr operating system deployment, Active Directory group membership, and OSD log collection.
---

I'm **Claudio Mendes (@vartaxe)**. I write PowerShell tools for the repeatable jobs
around Windows deployment, with clear inputs, useful logs, and explicit outcomes.
Most of the work here brings together Microsoft Configuration Manager and Active Directory.

## Projects

Both projects are self-contained **Windows PowerShell 5.1** scripts under the
**MIT license**. Pick the task you need to automate:

<div class="project-grid">
  <section class="project-card" aria-labelledby="ad-groups-title">
    <h3 id="ad-groups-title"><img src="assets/people-team.svg" alt="" aria-hidden="true" width="24" height="24"> Add computers to AD groups</h3>
    <p>Add a domain-joined computer to Active Directory groups during a ConfigMgr
      task sequence, with Kerberos over LDAPS by default, direct membership
      verification, bounded retries, and CMTrace logging.</p>
    <p><strong>Runtime:</strong> full Windows, after domain join and restart.</p>
    <p><a href="https://vartaxe.github.io/ConfigMgr-OSD-AddComputerToADGroup/">Read the AD group guide</a>
      &middot; <a href="https://github.com/vartaxe/ConfigMgr-OSD-AddComputerToADGroup">Browse source</a>
      &middot; <a href="https://gist.github.com/vartaxe/99dc4be2d6dbf8cda0b93e2de3f0d906">Standalone gist</a></p>
  </section>
  <section class="project-card" aria-labelledby="osd-logs-title">
    <h3 id="osd-logs-title"><img src="assets/folder-arrow-right.svg" alt="" aria-hidden="true" width="24" height="24"> Copy OSD logs to a file share</h3>
    <p>Collect OSD logs, create a local ZIP and manifest, and upload to an SMB share
      with retries and remote size checks. Keep the local archive if the upload fails.</p>
    <p><strong>Runtime:</strong> a ConfigMgr task sequence; WinPE needs the documented prerequisites.</p>
    <p><a href="https://vartaxe.github.io/ConfigMgr-OSD-CopyOSDLogToFileShare/">Read the OSD log guide</a>
      &middot; <a href="https://github.com/vartaxe/ConfigMgr-OSD-CopyOSDLogToFileShare">Browse source</a>
      &middot; <a href="https://gist.github.com/vartaxe/cd41f830cddc7853f5189713421a601b">Standalone gist</a></p>
  </section>
</div>

Gists are standalone snapshots with MIT notices and checksums. The repositories
and release packages remain the authoritative source for deployment guidance.

<aside class="callout" aria-label="Validation status">
  <p><strong>Validate before rollout.</strong> Automated checks cover syntax, static
    analysis, and mocked scenarios. Live ConfigMgr, Active Directory, WinPE, and SMB
    testing has not been performed for this release. Start with each project's
    deployment, compatibility, and validation guides.</p>
</aside>

## A consistent approach

- **Self-contained tools.** Package a single script for each task.
- **Explicit security choices.** Runtime credentials, certificate checks, and
  documented compatibility settings.
- **Troubleshooting first.** Sanitized CMTrace-compatible logs, documented exit codes,
  and deployment examples.
- **Honest status.** CI results and live-environment validation are different things.

## Development

[Set up a Windows workstation](docs/workstation.md) for Git, repository access,
PowerShell editing, and the same validation tools used in CI.

## Contact and support

For general contact, email [vartaxe@outlook.com](mailto:vartaxe@outlook.com).
For bugs or usage questions, use the affected repository's issue templates and
support guide. Report vulnerabilities through its **private vulnerability reporting**
page, not a public issue.

[GitHub Sponsors](https://github.com/sponsors/vartaxe) helps cover testing,
documentation, and maintenance. Both tools remain free and open source.
