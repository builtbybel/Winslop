# Features

## Table of contents
- [Start Menu & Taskbar](#start-menu--taskbar)
- [Search & Web Integration](#search--web-integration)
- [Window Management](#window-management)
- [Privacy & Telemetry](#privacy--telemetry)
- [Power & Shutdown](#power--shutdown)
- [UI & Personalization](#ui--personalization)
- [File Explorer & Context Menus](#file-explorer--context-menus)
- [Performance & Multimedia Scheduling](#performance--multimedia-scheduling)
- [System & Diagnostics](#system--diagnostics)

---

## Start Menu & Taskbar

### Hide Most used apps in start menu
**Info:** This feature will hide Most used apps in start menu for all users  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Explorer`  
**Value:** `ShowOrHideMostUsedApps`  
**Recommended:** `2`  
**Undo:** `1`

### Hide Task view button on taskbar
**Info:** This feature will hide the Task view button on taskbar  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`  
**Value:** `ShowTaskViewButton`  
**Recommended:** `0`  
**Undo:** `1`

### Hide search box on taskbar
**Info:** This feature will hide search box on taskbar  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search`  
**Value:** `SearchboxTaskbarMode`  
**Recommended:** `0`  
**Undo:** `2`

### Align Start button to left
**Info:** This feature will align the Start button to left  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`  
**Value:** `TaskbarAl`  
**Recommended:** `0`  
**Undo:** `1`

### Enable End Task
**Info:** Adds 'End Task' to the Windows 11 taskbar context menu, allowing you to directly kill unresponsive apps.  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\TaskbarDeveloperSettings`  
**Value:** `TaskbarEndTask`  
**Recommended:** `1`  
**Undo:** `0`

### Pin more Apps on start menu
**Info:** This feature will allow pinning more Apps on start menu  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`  
**Value:** `Start_Layout`  
**Recommended:** `1`  
**Undo:** `0`

---

## Search & Web Integration

### Disable Bing Search
**Info:** This feature disables Bing integration in Windows Search.  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search`  
**Value:** `BingSearchEnabled`  
**Recommended:** `0`  
**Undo:** `1`

### Disable Search Box Suggestions
**Info:** This feature disables Bing search and web suggestions in the Windows Start Menu.  
**Registry:** `HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Explorer`  
**Value:** `DisableSearchBoxSuggestions`  
**Recommended:** `1`  
**Undo:** `0`

---

## Window Management

### Disable Snap Assist Flyout
**Info:** This feature disables the Snap Assist flyout, which appears when you snap a window.  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`  
**Value:** `EnableSnapAssistFlyout`  
**Recommended:** `0`  
**Undo:** `1`

---

## Privacy & Telemetry

### Turn off Telemetry data collection
**Info:** This feature will turn off telemetry data collection and prevent the data from being sent to Microsoft.  
**Registry 1:** `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\DataCollection` → `AllowTelemetry = 0`  
**Registry 2:** `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\DiagTrack` → `Start = 4`  
**Undo:** `AllowTelemetry = 1`, `Start = 2`

### Disable activity history
**Info:** Disable activity history (prevents Windows from tracking and storing your activity)  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System`  
**Value:** `PublishUserActivities`  
**Recommended:** `0`  
**Undo:** `1`

### Disable location tracking
**Info:** Disable location tracking (prevents Windows from accessing your location)  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\LocationAndSensors`  
**Value:** `LocationEnabled`  
**Recommended:** `0`  
**Undo:** `1`

### Disable Privacy Settings Experience at sign-in
**Info:** This feature will disable Privacy Settings Experience at sign-in.  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\OOBE`  
**Value:** `DisablePrivacyExperience`  
**DoFeature sets:** `1`  
**Undo:** `0`

---

## Power & Shutdown

### Disable Hibernation
**Info:** Hibernation is mostly useful for laptops... Disabling it frees resources and avoids confusion by hiding the Hibernate option...  
**Registry 1:** `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power` → `HibernateEnabled = 0`  
**Registry 2:** `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FlyoutMenuSettings` → `ShowHibernateOption = 0`  
**Command:** `powercfg /hibernate off`  
**Undo:** `HibernateEnabled = 1`, `ShowHibernateOption = 1`, `powercfg /hibernate on`

### Speed Up Shutdown Time
**Info:** This feature reduces the WaitToKillServiceTimeout value...  
**Registry:** `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control`  
**Value:** `WaitToKillServiceTimeout`  
**Recommended:** `"1000"`  
**Undo:** `"5000"`

---

## UI & Personalization

### Enable Dark Mode for Apps
**Info:** This feature enables Dark Mode for apps in Windows 11.  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize`  
**Value:** `AppsUseLightTheme`  
**Recommended:** `0`  
**Undo:** `1`

### Enable Dark Mode for System
**Info:** This feature enables Dark Mode for Windows system UI (e.g., taskbar, start menu).  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize`  
**Value:** `SystemUsesLightTheme`  
**Recommended:** `0`  
**Undo:** `1`

### Disable Transparency Effects
**Info:** This feature disables transparency effects for Start menu, taskbar, and other surfaces.  
**Registry:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize`  
**Value:** `EnableTransparency`  
**Recommended:** `0`  
**Undo:** `1`

### Don't use personalized lock screen
**Info:** This feature will disable the personalized lock screen.  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Personalization`  
**Value:** `NoLockScreen`  
**DoFeature sets:** `1`  
**Undo:** `0`

### Enable Verbose Logon status messages
**Info:** This method allows you to see what processes are hanging when shutting down and turning on the machine.  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`  
**Value:** `VerboseStatus`  
**Recommended:** `1`  
**Undo:** `0`

---

## File Explorer & Context Menus

### Show Full context menus in Windows 11
**Info:** This feature will enable full context menus  
**Registry:** `HKEY_CURRENT_USER\SOFTWARE\CLASSES\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32`  
**Value:** `(Default)` set to empty string  
**Undo:** Deletes `Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}`

### Speed Up Menu Show Delay
**Info:** Speeds up the appearance of menus and submenus...  
**Registry:** `HKEY_CURRENT_USER\Control Panel\Desktop`  
**Value:** `MenuShowDelay`  
**Recommended:** `"10"`  
**Undo:** `"400"`

---

## Performance & Multimedia Scheduling

### Optimize System Responsiveness
**Info:** Enhances system responsiveness by prioritizing CPU resources for foreground tasks...  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`  
**Value:** `SystemResponsiveness`  
**Recommended:** `10`  
**Undo:** `20`

### Disable Network Throttling
**Info:** Disables the Windows network throttling mechanism...  
**Registry:** `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`  
**Value:** `NetworkThrottlingIndex`  
**Recommended:** `0xFFFFFFFF` (decimal 4294967295)  
**Undo:** `10`

---

## System & Diagnostics

### Show BSOD details instead of sad smiley
**Info:** This method displays the full classic BSOD with technical error details instead of the simplified sad face version.  
**Registry:** `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\CrashControl`  
**Values:** `DisplayParameters = 1`, `DisableEmoticon = 1`  
**Undo:** `DisplayParameters = 0`, `DisableEmoticon = 0`
