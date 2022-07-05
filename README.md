# **Windows 11 Installation Guide**

**Windows 11 requires a TPM and secure boot enabled** (*This can be bypassed at install if desired*)

<img src="https://i.pcmag.com/imagery/reviews/00xBy0JjVybodfIwWxeGCkZ-1.fit_scale.size_760x427.v1628697239.png" width="500" height="300">


&nbsp;

## **ISO Creation**

* Download the ISO from https://www.microsoft.com/software-download/windows11
* Create a bootable USB using 
  * **Rufus** https://rufus.ie/en/ (*Windows Only*)
  * **WoeUSB** https://github.com/WoeUSB/WoeUSB (*Linux*)
  * **CLI** https://www.sysgeeker.com/how-to-create-windows-11-bootable-usb-on-mac.html (*macOS*)

&nbsp;

## **Installation**
* On the initial screen press **Shift+F10** to enter a cmd prompt
```ps1
# Run diskpart
diskpart

# Show attached disks
list disk

# Select disk (make sure not to select your USB drive or any disks you are using for other data)
select disk n   # Disk "n" can range from 0-10

# Once selected clean the disk and convert to GPT
clean
convert gpt
```

* Choose **Install now**
* Enter product key or choose "I don't have a product key"
* Choose Version **Pro**
* Accept EULA
* Choose "**Custom: Install Windows only (advanced)**
  * Choose **Drive 0 Unallocated Space** & choose "New"
  * Enter **205824**[^1] for a 200GB C: Drive
  * Click "Apply" & "OK"
  * Choose "Next"
* Choose "Sign-in options"
  * Choose "Offline account"
  * Choose "Skip for now"
  * Enter Credentials
  * Turn off all privacy settings

### Security Settings
  - [x] Enable Bitlocker
  - [x] Enable VBS (Virtualization-based Security)

&nbsp;

## Environment Setup

- [x] Install motherboard drivers + GPU drivers
- [x] Turn off "Pointer Precision" in windows mouse settings
- [x] Set power plan to high performance
- [x] Change PC to desired name
- [x] Create D: 
- [x] Plug in ETH & run windows updates
- [x] Reboot

### WSL 2
```ps1
# Install wsl2 & debian from a powershell admin command prompt
wsl --install -d debian
```

### Hyper-V
```ps1
# Install hyper-v from a powershell admin command prompt (Reboot required)
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

### Winget
```ps1
# Use the winget command to install applications (Not all apps are supported yet)
winget install -e --id Mozilla.Firefox;winget install -e --id Malwarebytes.Malwarebytes;winget install -e --id AMD.RyzenMaster;winget install -e --id CPUID.CPU-Z;winget install -e --id TechPowerUp.GPU-Z;winget install -e --id FinalWire.AIDA64.Extreme;winget install -e --id REALiX.HWiNFO;winget install -e --id Valve.Steam;winget install -e --id ElectronicArts.EADesktop;winget install -e --id Ubisoft.Connect;winget install -e --id Playnite.Playnite;winget install -e --id PrivateInternetAccess.PrivateInternetAccess;winget install -e --id Discord.Discord;winget install -e --id DuongDieuPhap.ImageGlass;winget install -e --id clsid2.mpc-hc;winget install -e --id RevoUninstaller.RevoUninstaller;winget install -e --id WiresharkFoundation.Wireshark;winget install -e --id PeterPawlowski.foobar2000;winget install -e --id 7zip.7zip.Alpha.exe;winget install -e --id Notepad++.Notepad++;winget install -e --id Microsoft.VisualStudioCode;winget install -e --id Microsoft.PowerToys;winget install -e --id WinSCP.WinSCP;winget install -e --id Adobe.Acrobat.Reader.64-bit;winget install -e --id qBittorrent.qBittorrent;winget install -e --id JAMSoftware.TreeSize.Free;winget install -e --id CrystalDewWorld.CrystalDiskMark;winget install -e --id GorillaDevs.GDLauncher
```
### Applications (Non-winget)
1. **Veeam Agent for Microsoft Windows Free** https://www.veeam.com/downloads.html?ad=top-sub-menu
1. **Zen Timings** https://zentimings.protonrom.com/
1. **Battle.net** https://www.blizzard.com/en-us/apps/battle.net/desktop
1. **Sysinternals** https://docs.microsoft.com/en-us/sysinternals/downloads/
1. **Madvr** http://madvr.com/
1. **MsiAfterburner**[^2] https://www.msi.com/Landing/afterburner/graphics-cards 
1. **Samsung Magician** https://semiconductor.samsung.com/consumer-storage/magician/
1. **Razer Synapse** https://www.razer.com/synapse-3
1. **VMware Remote Console** https://customerconnect.vmware.com/en/downloads/details?downloadGroup=VMRC1201&productId=876
1. **OpenRGB** https://openrgb.org/releases.html
1. **Aqua Suite** https://aquacomputer.de/software.html
1. **Equalizer APO** https://sourceforge.net/projects/equalizerapo/
1. **Equalizer APO Peace GUI** https://sourceforge.net/projects/peace-equalizer-apo-extension/

### Windows Store Applications
1. **Cider**
1. **Evernote**
1. **Xbox Accessories**


### Application Skins/Mods
1. **foobar2000 (eole skin)** https://github.com/Ottodix/Eole-foobar-theme
1. **Steam Metro & Unofficial Patch** https://metroforsteam.com/ ------ https://github.com/redsigma/UPMetroSkin 
1. **Better Discord** https://betterdiscord.app/



[^1]: The formula to determine the size is *TB in MB x 1.048576 + 4096*  **OR** *GB in MB x 1.024 + 1024*
[^2]: GPU Overclock (1080ti) **Core +125 | Mem + 500**