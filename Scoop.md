---
tags: windows
---

## Install

```pwsh
Set-ExecutionPolicy ByPass -Scope Process -Force
# If Scoop is installed or you need to re-install Scoop on an NTFS mount,
# remove `scoop` from PATH and modify the two ENV vars below before installing.
# See https://github.com/ScoopInstaller/Install#advanced-installation
$env:SCOOP='<path_to>\Scoop'
$env:SCOOP_GLOBAL='<path_to>\Scoop'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
Get-ChildItem Env:
iex "& {$(irm get.scoop.sh)} -RunAsAdmin"
```

## Usage

```
scoop list <app>
gsudo scoop reset <app>@version
```