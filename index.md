---
title: Windows endpoint automation
description: Focused PowerShell tools and maintained forks for ConfigMgr operating system deployment and Windows endpoint management.
---

I'm **Claudio Mendes (@vartaxe)**. I write PowerShell tools for the repeatable jobs
around Windows deployment, with clear inputs, useful logs, and explicit outcomes.
Most of the work here brings together Microsoft Configuration Manager and Active Directory.

## Projects

The projects are self-contained **Windows PowerShell 5.1** scripts under the
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
  <section class="project-card" aria-labelledby="disk-layout-title">
    <h3 id="disk-layout-title"><img src="assets/disk-layout.svg" alt="" aria-hidden="true" width="24" height="24"> Disk partition layout</h3>
    <p>Apply a disk layout in WinPE during a task sequence. It irreversibly cleans and
      repartitions the target disk, so test it on disposable hardware first.</p>
    <p><strong>Runtime:</strong> WinPE in a ConfigMgr task sequence.</p>
    <p><a href="https://vartaxe.github.io/ConfigMgr-OSD-DiskPartitionLayout/">Read the disk layout guide</a>
      &middot; <a href="https://github.com/vartaxe/ConfigMgr-OSD-DiskPartitionLayout">Browse source</a>
      &middot; <a href="https://vartaxe.github.io/ConfigMgr-OSD/">ConfigMgr-OSD hub</a></p>
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

## Maintained forks

These upstream-derived repositories contain focused endpoint-management maintenance.
They remain forks, so review the fork history and upstream guidance before deployment.

<div class="project-grid">
  <section class="project-card" aria-labelledby="modern-driver-title">
    <h3 id="modern-driver-title">Modern Driver Management</h3>
    <p>ConfigMgr driver-management automation maintained as a fork of the
      MSEndpointMgr project.</p>
    <p><a href="https://github.com/vartaxe/ModernDriverManagement">Browse the maintained fork</a>
      &middot; <a href="https://github.com/MSEndpointMgr/ModernDriverManagement">View upstream</a>
      &middot; <a href="https://www.msendpointmgr.com/modern-driver-management">Read upstream guidance</a></p>
  </section>
  <section class="project-card" aria-labelledby="modern-bios-title">
    <h3 id="modern-bios-title">Modern BIOS Management</h3>
    <p>ConfigMgr BIOS-management automation maintained as a fork of the
      MSEndpointMgr project.</p>
    <p><a href="https://github.com/vartaxe/ModernBIOSManagement">Browse the maintained fork</a>
      &middot; <a href="https://github.com/MSEndpointMgr/ModernBIOSManagement">View upstream</a>
      &middot; <a href="https://www.msendpointmgr.com/modern-bios-management">Read upstream guidance</a></p>
  </section>
  <section class="project-card" aria-labelledby="driver-automation-title">
    <h3 id="driver-automation-title">Driver Automation Tool</h3>
    <p>Driver and BIOS package automation maintained as a fork of Maurice Daly's
      community project.</p>
    <p><a href="https://github.com/vartaxe/DriverAutomationTool">Browse the maintained fork</a>
      &middot; <a href="https://github.com/maurice-daly/DriverAutomationTool">View upstream</a>
      &middot; <a href="https://www.driverautomationtool.com">Visit the project website</a></p>
  </section>
</div>

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
For bugs or usage questions, follow the affected repository's documented support
path. For vulnerabilities, follow its security policy: use **private vulnerability
reporting** when available, or the private contact method documented there. Do not
report security issues in a public issue.

[GitHub Sponsors](https://github.com/sponsors/vartaxe) helps cover testing,
documentation, and maintenance. All tools remain free and open source.
