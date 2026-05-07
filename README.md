# Installing WSL on Custom Windows (ReviOS / AtlasOS / Tiny11)

Simple and clean guide to install **WSL (Windows Subsystem for Linux)** on modified versions of Windows.

---

# What is WSL?

WSL allows you to run a Linux distribution directly inside Windows without dual booting.

With WSL you can:

* use a Linux terminal
* install developer tools
* run Python / NodeJS / GCC
* create scripts
* use Docker
* develop in a Linux environment

---

# Requirements

* Windows 10 or Windows 11
* Virtualization enabled in BIOS
* Hyper-V / Virtual Machine Platform enabled
* Internet connection

On modded Windows builds like ReviOS or AtlasOS, some required features may be disabled.

---

# Check if Virtualization is Enabled

Open:

```bash
CTRL + SHIFT + ESC
```

Go to:

```bash
Performance -> CPU
```

Make sure it says:

```bash
Virtualization: Enabled
```

If disabled:

* enter BIOS
* enable:

  * Intel VT-x
  * AMD-V

---

# Enable Required Features

Open PowerShell as Administrator.

Run:

```powershell
DISM /Online /Enable-Feature /FeatureName:Microsoft-Windows-Subsystem-Linux /All /NoRestart
```

Then:

```powershell
DISM /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /All /NoRestart
```

Restart your PC.

---

# Install WSL

After restarting, open PowerShell as Administrator:

```powershell
wsl --install
```

Windows will automatically install:

* WSL
* Linux Kernel
* Ubuntu

Restart again if requested.

---

# Install a Specific Linux Distro

List available distros:

```powershell
wsl --list --online
```

Install Ubuntu:

```powershell
wsl --install -d Ubuntu
```

Install Debian:

```powershell
wsl --install -d Debian
```

---

# Fixes for Modded Windows

## Error: WSL Not Working

Some custom ISOs remove essential Windows components.

Check that these are enabled:

```powershell
OptionalFeatures.exe
```

Enable:

* Windows Subsystem for Linux
* Virtual Machine Platform
* Hyper-V

---

## Error 0x80370102

This means virtualization is disabled.

Fix:

* enable VT-x / AMD-V in BIOS
* save changes
* restart your PC

---

## WSL Stuck on Startup

Update the kernel:

```powershell
wsl --update
```
Or install and Update your WSL [here](https://github.com/microsoft/WSL/releases/)

Restart WSL:

```powershell
wsl --shutdown
```

---

# Useful Commands

Show installed distros:

```powershell
wsl -l -v
```

Launch Ubuntu:

```powershell
wsl
```

Shutdown WSL:

```powershell
wsl --shutdown
```

Update WSL:

```powershell
wsl --update
```

---

# Tips

For better compatibility:

* avoid heavily stripped ISOs
* do not remove Hyper-V
* use Windows 11 if possible
* keep WSL updated

---

```bash
Leave a star on the repository
```
