# Nidi for Windows

Nidi installs through [Scoop](https://scoop.sh). It needs 64-bit Windows 10 or 11.

## Before you start

You need Scoop. If `scoop --version` in PowerShell gives an error, install Scoop first. Open PowerShell (not as administrator) and run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

Scoop also needs git to add a bucket:

```powershell
scoop install git
```

## Install

```powershell
scoop bucket add marsderp https://github.com/marsderp/scoop-bucket
scoop install marsderp/nidi
scoop hold nidi
```

Windows asks once for administrator permission, because Nidi installs into Program Files with its normal installer. Then open Nidi from the Start menu.

`scoop hold nidi` stops `scoop update *` from reinstalling Nidi, because Nidi updates itself.

## Updates

Nidi updates itself. When a new version is out, an arrow button appears in the sidebar. Click it, then Install, and Nidi restarts on the new version.

## Uninstall

Remove the app but keep your services, logins and settings:

```powershell
scoop uninstall nidi
```

Windows asks for administrator permission again. To also remove all of Nidi's data (logins, settings, caches), run this after uninstalling:

```powershell
Remove-Item -Recurse -Force "$env:APPDATA\com.marsderp.nidi", "$env:LOCALAPPDATA\com.marsderp.nidi" -ErrorAction SilentlyContinue
```

To also remove this bucket from Scoop:

```powershell
scoop bucket rm marsderp
```

## If Windows shows a warning

Installing through Scoop normally shows no SmartScreen warning. If you see "Windows protected your PC", click More info, then Run anyway.

## For the maintainer

Nidi's release workflow sets the version, URL and hash in `bucket/nidi.json`. Don't edit them by hand.
