---
title: Windows development workstation
---

# Windows development workstation

Set up a Windows 11 desktop to edit and validate the scripts. Use **Windows
PowerShell 5.1** for validation to match the deployment runtime.

## Required tools

| Tool | Purpose |
|---|---|
| Git for Windows | Clone, inspect changes, commit, and push |
| GitHub CLI | Confirm the account, access repositories, and inspect CI/releases |
| Windows PowerShell 5.1 | Parse, analyze, and test the deployment scripts |
| Pester 5.7.1 | The pinned regression-test engine |
| PSScriptAnalyzer 1.25.0 | The pinned static-analysis engine |
| VS Code with Microsoft's PowerShell extension | Edit, navigate, and debug PowerShell |

Windows includes Windows PowerShell 5.1 as `powershell.exe`. The editor extension
requires .NET Framework 4.8 or later for its Windows PowerShell 5.1 support.

## Install the command-line tools and editor

On a new Windows desktop, open a terminal and install the tools that are missing:

```powershell
winget install --id Git.Git --exact --source winget
winget install --id GitHub.cli --exact --source winget
winget install --id Microsoft.VisualStudioCode --exact --source winget
```

Reopen the terminal after installation so its `PATH` is refreshed. Then install
the editor extension:

```powershell
code --install-extension ms-vscode.PowerShell
```

## Confirm the GitHub identity

Sign in through the browser flow and check the result before pushing:

```powershell
gh auth login --hostname github.com --git-protocol https --web
gh api user --jq .login
```

Confirm that the command reports the account you intend to use. Contributors use
their own accounts; owner-only operations use `vartaxe`. `GH_TOKEN` or `GITHUB_TOKEN`
in the current terminal can override a stored login. Keep tokens private and
authorize additional permissions through GitHub only when an operation requires them.

## Clone and configure a checkout

Choose a normal development folder outside a synced deployment-package directory:

```powershell
gh repo clone vartaxe/vartaxe
gh repo clone vartaxe/ConfigMgr-OSD-AddComputerToADGroup
gh repo clone vartaxe/ConfigMgr-OSD-CopyOSDLogToFileShare
```

Inside each repository, set your own commit identity and review the configuration:

```powershell
git config user.name "YOUR NAME"
git config user.email "YOUR VERIFIED OR NOREPLY EMAIL"
git config --get user.name
git config --get user.email
git status --short
```

Follow `.gitattributes`: PowerShell files use CRLF and other text uses LF. If moving
from a checkout with older rewritten history, preserve your local work and clone
the current repository afresh.

## Install the pinned validation modules

Start **Windows PowerShell 5.1** and inspect the engine:

```powershell
powershell.exe -NoProfile
$PSVersionTable.PSVersion
$PSVersionTable.PSEdition
```

Expect version `5.1` and edition `Desktop`. In that 5.1 session:

```powershell
Install-Module Pester -RequiredVersion '5.7.1' -Repository PSGallery -Scope CurrentUser -Force
Install-Module PSScriptAnalyzer -RequiredVersion '1.25.0' -Repository PSGallery -Scope CurrentUser -Force
Import-Module Pester -RequiredVersion '5.7.1' -Force
Import-Module PSScriptAnalyzer -RequiredVersion '1.25.0' -Force
```

Use your approved package source and retain certificate and publisher verification.
If installation fails, check the configured proxy, NuGet provider, and repository
access before retrying.

## Validate before editing or publishing

From either script repository's root, run:

```powershell
powershell.exe -NoProfile -NonInteractive -ExecutionPolicy Bypass -File .\build\Invoke-Validation.ps1
```

The execution-policy option applies to this process and remains subject to
organizational Group Policy. Use the validator for desktop testing; run deployment
entry points only inside a ConfigMgr task sequence.

In VS Code, select Windows PowerShell 5.1 through **PowerShell: Show Session Menu**.
The repositories also provide a **Validate with Windows PowerShell 5.1** task.

After edits, regenerate banners when needed, preserve the checkout line endings,
and update `CHECKSUMS.txt` using the repository's release guide. Keep reports and
build output outside the source tree so they do not enter the checksum inventory.
Complete the project's environment-validation checklist before deploying changes.

## Publish changes

Submit reviewed changes against `main` and check the resulting CI run. GitHub Pages
publishes the documentation from that branch. For a script release, follow the
project's release guide to publish and verify the ZIP and SHA-256 sidecar.

## Official references

- [WinGet installation commands](https://learn.microsoft.com/en-us/windows/package-manager/winget/install)
- [PowerShell in VS Code](https://code.visualstudio.com/docs/languages/powershell)
- [PSScriptAnalyzer](https://learn.microsoft.com/en-us/powershell/utility-modules/psscriptanalyzer/overview)
- [GitHub CLI authentication](https://cli.github.com/manual/gh_auth_login)

[Profile and project directory](../index.md)
