[![Build](https://github.com/uroesch/PuTTYPortable/workflows/build-linux/badge.svg)](https://github.com/uroesch/PuTTYPortable/actions?query=workflow%3Abuild-linux)
[![Build](https://github.com/uroesch/PuTTYPortable/workflows/build-windows/badge.svg)](https://github.com/uroesch/PuTTYPortable/actions?query=workflow%3Abuild-windows)
[![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/uroesch/PuTTYPortable?include_prereleases)](https://github.com/uroesch/PuTTYPortable/releases)
[![Runs on](https://img.shields.io/badge/runs%20on-Win64%20%26%20Win32-blue)](#runtime-dependencies)
![GitHub All Releases](https://img.shields.io/github/downloads/uroesch/PuTTYPortable/total)

# PuTTY Portable for PortableApps.com

<img src="App/AppInfo/appicon_128.png" align=left>

[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
is a free and open-source terminal emulator, serial console and network file
transfer application. It supports several network protocols, including SCP,
SSH, Telnet, rlogin, and raw socket connection. It can also connect to a
serial port. The name "PuTTY" has no official meaning.

PuTTY was originally written for Microsoft Windows, but it has been ported
to various other operating systems. Official ports are available for some
Unix-like platforms, with work-in-progress ports to Classic Mac OS and
macOS, and unofficial ports have been contributed to platforms such as
Symbian Windows Mobile and Windows Phone.

PuTTY was written and is maintained primarily by Simon Tatham, a British
programmer.

## Differences to the official PuTTYPortable

There is an official release on PortableApps.com for the
[PuTTY suite](https://portableapps.com/apps/internet/putty_portable)
of tools. Said implementation only has a menu entry for the PuTTY Terminal,
but not for other useful GUI applications such as PuTTYgen or Pageant.
This implementation's only difference is the addition of the 2 addtional
GUI application to the PortableApps application menu.

## Runtime dependencies
* 32-bit or 64-bit version of (pretty much any) Windows.

## Support matrix

| OS              | 32-bit             | 64-bit              |
|-----------------|:------------------:|:-------------------:|
| ReactOS 0.4.14  | ![fs][fs]          | ![na][na]           |
| ReactOS 0.4.15  | ![fs][fs]          | ![ps][ps]           |
| Windows XP      | ![fs][fs]          | ![fs][fs]           |
| Windows Vista   | ![fs][fs]          | ![fs][fs]           |
| Windows 7       | ![fs][fs]          | ![fs][fs]           |
| Windows 8       | ![fs][fs]          | ![fs][fs]           |
| Windows 10      | ![fs][fs]          | ![fs][fs]           |
| Windows 11      | ![na][na]          | ![fs][fs]           |

Legend: ![ns][ns] not supported; ![na][na] not applicable; ![nd][nd] no data; ![ps][ps] supported but not verified; ![fs][fs] verified;

## Status
This PortableApps project is in alpha stage.

<!-- Start include INSTALL.md -->
## Installation

### Download

Since this is not an official PortableApp the PortableApps installer must
be download first. Navigate to https://github.com/uroesch/PuTTYPortable/releases
for a selection of releases.

### Install via the PortableApps.com Platform

After downloading the `.paf.exe` installer navigate to your PortableApps.com Platform
`Apps` Menu &#10102; and select `Install a new app (paf.exe)` &#10103;.

<img src="Other/Images/install_newapp_menu.png" width="400">

From the dialog choose the previously downloaded `.paf.exe` file. &#10104;

<img src="Other/Images/install_newapp_dialog.png" width="400">

After a short while the installation dialog will appear.

<img src="Other/Images/install_newapp_installation.png" width="400">


### Install outside of the PortableApps.com Platform

The Packages found under the release page are not digitally signed so there the installation
is a bit involved.

After downloading the `.paf.exe` installer trying to install may result in a windows defender
warning.

<img src="Other/Images/info_defender-protected.png" width="260">

To unblock the installer and install the application follow the annotated screenshot below.

<img src="Other/Images/howto_unblock-file.png" width="600">

1. Right click on the executable file.
2. Choose `Properties` at the bottom of the menu.
3. Check the unblock box.
<!-- End include INSTALL.md -->

<!-- Start include BUILD.md -->
### Build

#### Windows

##### Windows 10

The only supported build platform for Windows is version 10 other releases
have not been tested.

###### Clone repositories

```
git clone https://github.com/uroesch/PortableApps.comInstaller.git
git clone -b patched https://github.com/uroesch/PortableApps.comLauncher.git
git clone https://github.com/uroesch/PuTTYPortable.git
```

###### Build installer

```
cd PuTTYPortable
powershell -ExecutionPolicy ByPass -File Other/Update/Update.ps1
```

#### Linux

##### Docker

Note: This is currently the preferred way of building the PortableApps installer.

For a Docker build run the following command.

###### Clone repo

```
git clone https://github.com/uroesch/PuTTYPortable.git
```

###### Build installer

```
cd PuTTYPortable
curl -sJL https://raw.githubusercontent.com/uroesch/PortableApps/master/scripts/docker-build.sh | bash
```

#### Local build

##### Ubuntu 20.04

To build the installer under Ubuntu 20.04 `Wine`, `PowerShell`, `7-Zip` and when building headless
`Xvfb` are required.

###### Setup
```
sudo snap install powershell --classic
sudo apt --yes install git wine p7zip-full xvfb
```

When building headless run the below command starts a virtual Xserver required for the build to
succeed.

```
export DISPLAY=:7777
Xvfb ${DISPLAY} -ac &
```

###### Clone repositories

```
git clone https://github.com/uroesch/PortableApps.comInstaller.git
git clone -b patched https://github.com/uroesch/PortableApps.comLauncher.git
git clone https://github.com/uroesch/PuTTYPortable.git
```

###### Build installer

```
cd PuTTYPortable
pwsh Other/Update/Update.ps1
```

##### Ubuntu 18.04

To build the installer under Ubuntu 18.04 `Wine`, `PowerShell`, `7-Zip` and when building headless
`Xvfb` are required.

###### Setup
```
sudo snap install powershell --classic
sudo apt --yes install git p7zip-full xvfb
sudo dpkg --add-architecture i386
sudo apt update
sudo apt --yes install wine32
```

When building headless run the below command starts a virtual Xserver required for the build to
succeed.

```
export DISPLAY=:7777
Xvfb ${DISPLAY} -ac &
```

###### Clone repositories

```
git clone https://github.com/uroesch/PortableApps.comInstaller.git
git clone -b patched https://github.com/uroesch/PortableApps.comLauncher.git
git clone https://github.com/uroesch/PuTTYPortable.git
```

###### Build installer

```
cd PuTTYPortable
pwsh Other/Update/Update.ps1
```
<!-- End include BUILD.md -->

[nd]: Other/Icons/no_data.svg
[na]: Other/Icons/not_applicable.svg
[ns]: Other/Icons/no_support.svg
[ps]: Other/Icons/probably_supported.svg
[fs]: Other/Icons/full_support.svg
[defender_warning]: Other/Images/info_defender-protected.png
[howto_unlock]: Other/Images/info_defender-protected.png
