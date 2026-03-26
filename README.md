![Release v1.0](https://badgen.net/github/release/ShadowLithi/Intel-AX200-Win-Patch?icon=github) ![Windows 11](https://badgen.net/badge/icon/Windows-11?icon=windows&label)

# Intel-AX100 Sleep Crash Patch
Band-Aid patch for a severe Intel AX100 driver bug where it crashes after Windows 11 wakes from sleep

# Installation

* Find a permanent place in your computer for the .ps1 script and move it there. I recommend creating a folder in your root directory. IE: **`C:\Scripts\`**
* Open the Start Menu and search "**Task Scheduler**" and open it
   * Or you can find it in the **Windows** **Administrative Tools** folder in the Start Menu
   * Or you could press Win+R and type "**taskschd.msc**"
* On the right side, press on "**Create Task**".
   * ***Do not*** *use* "**Create Basic Task**"
* On the **General** tab
   * Name it something relevant like "Bluetooth Sleep Check"
   * Add a description for your future self to read if you want
   * Set user to `NT-AUTHORITY\SYSTEM`
   * Make sure "**Run with highest privileges**" is checked
   * Switch "**Configure for**" to your Windows version, or highest available
* On the **Triggers** tab
   * Press New
   * Switch "**Begin the Task**" to ***On workstation unlock***
   * Make sure "**Any user**" is selected
   * Make sure "**Enabled**" on the bottom is checked
   * Press OK
   * Press New
   * Switch "**Begin the Task**" to ***On event***
   * Set Log Name to **System**
   * Set Source to **Kernel-Power**
   * Set Event ID to **107**
   * Press OK
* On the **Actions** tab
   * Press New
   * Make sure "**Action**" is set to ***Start a Program***
   * On "**Program/script**" Powershell: *`powershell.exe`*
   * On "**Add arguments**" paste this argument list and be sure to put the full location path of your script file, be sure to keep the "" surrounding your path:
      * `-NonInteractive -WindowStyle Hidden -ExecutionPolicy Bypass -File "*your script location*"`
   * Press OK
* You can change things in the **Conditions** and **Settings** tabs if you want but it's not necessary.
* Press OK

# 🎉Now Windows will disable and re-enable the Bluetooth driver for you! 🎉
## If you have any issues with the script then please submit an issue
