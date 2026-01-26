# Plugins

Winslop supports plugins to extend the app with actions that go beyond simple “toggle a registry value”.
Typical use cases:
- run PowerShell based tools / scripts
- perform multi-step fixes
- integrate external utilities

> Tip: If you're looking for the built-in Windows tweaks, see the Feature Reference: [features.md](features.md).  
> For extensions in general, see: [extensions.md](extensions.md).

---

## Plugin file format

Plugins are PowerShell scripts (`.ps1`) that Winslop can run as “Tools / Extensions”.
They use a simple INI-like header format that defines **what to check** and **what to do**.

- `[Commands]` (required for Winslop plugin actions)
- `[Expect]` (optional, enables validation of the `Check` output)

Everything outside these sections is treated as a normal PowerShell script body.


> For built-in tweaks (toggles), see: [features.md](features.md)  
> For extensions/add-ons in general, see: [extensions.md](extensions.md)

---

## Recommended plugin structure

Keep plugins:
- transparent (explain what they do)
- reversible (provide undo if possible)
- quiet (no unnecessary output)
- safe (avoid remote downloads unless required)

---

## Basic execution model 

The demo pack uses a simple rule-driven model:

1. **Check** is executed first  
   The tool evaluates the output against **Expect**. 
2. If a fix is triggered, **Do** is executed.
3. Optionally, an **Undo** command can be provided.

---


## Naming and Help anchors

Winslop’s help system can link directly into GitHub docs by using the plugin title as an anchor.
That means:

- The plugin **display title** should match the markdown heading in `features.md` (plugins section)
- Anchors are generated like GitHub:
  - lowercase
  - spaces become `-`
  - apostrophes are removed (`Don't` → `dont`)

Example:
- Plugin title: `Don't Show Sponsored links in new tab page`
- Anchor: `#dont-show-sponsored-links-in-new-tab-page`

---

## [Commands] section

The `[Commands]` section contains metadata and the actual commands Winslop will run.

**Supported keys:**
- `Info` — short description shown to the user
- `Check` — command(s) executed first to read current state
- `Do` — command(s) executed when the user applies the fix/action
- `Undo` — command(s) executed to revert the change (if supported)

**Notes:**
- Multiple commands can be chained with `&&`
- Output from all commands is logged
- `Check` output is used for validation if `[Expect]` is present

Example:

```ini
# Disable Bing Search.ps1

[Commands]
Info=Disables Bing integration in Windows Search
Check=reg query "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled
Do=reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 0 /f && echo BingSearchEnabled set to 0
Undo=reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 1 /f && echo BingSearchEnabled set to 1

[Expect]
BingSearchEnabled=0x0


# Disable File Explorer Ads.ps1

[Commands]
Info=Disables File Explorer ads (sync provider notifications) and restarts Explorer
Check=reg query "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowSyncProviderNotifications
Do=reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowSyncProviderNotifications /t REG_DWORD /d 0 /f && taskkill /f /im explorer.exe && start explorer.exe && echo Explorer restarted
Undo=reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowSyncProviderNotifications /t REG_DWORD /d 1 /f && taskkill /f /im explorer.exe && start explorer.exe && echo Explorer restarted

[Expect]
ShowSyncProviderNotifications=0x0

