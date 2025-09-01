# **🧪 Penetration Testing Operating Systems**

---

A curated list of popular Linux distributions tailored for **ethical hacking**, **penetration testing**, and **cybersecurity research**.

## **🔹 BackTrack Linux**

---

> 🕰️ Legacy OS – No longer maintained
> 

The original penetration testing distribution that laid the foundation for Kali Linux. While deprecated, BackTrack holds historical significance in the hacking community.

- **Website**: backtrack-linux.org

## **🐉 Kali Linux**

---

> 🎯 The industry standard for ethical hackers
> 

Developed by **Offensive Security**, Kali Linux is the most widely used OS for penetration testing, forensics, and red teaming.

- **Full Tool Listing**: kali.org/tools/all-tools/
- **Release Archive**: kali.org/releases/
- **History & Intro**: docs.kali.org/introduction/kali-linux-introduction

## **🦜 Parrot OS**

---

> 🛡️ Privacy + Security + Development
> 

A Debian-based distro for penetration testing, **digital forensics**, secure communications, and programming. Lightweight and focused on anonymity and encryption.

- **Website**: parrotsec.org

## **🧨 BlackArch Linux**

---

> 🧰 Over 3,000 pre-installed tools
> 

An Arch-based distro tailored for **advanced users**, offering a massive repository of tools for **black-box testing**, red teaming, and exploit development.

- **Website**: blackarch.org

## **🎛️ BackBox Linux**

---

> ⚡ Simple. Lightweight. Effective.
> 

Ubuntu-based penetration testing distro with a focus on **performance** and **usability**. Comes with a minimal **XFCE desktop** and tools for auditing and assessments.

- **Website**: backbox.org

## **✅ Recommended Usage**

---

| Purpose | Recommended OS |
| --- | --- |
| Beginners / Industry standard | **Kali Linux** |
| Lightweight & privacy-focused users | **Parrot OS** |
| Advanced users / Arch lovers | **BlackArch Linux** |
| Ubuntu base + XFCE lovers | **BackBox Linux** |
| Legacy knowledge / nostalgia | **BackTrack Linux** |

> 💡 Pro Tip: For more control, start with a minimal Debian install and build your own pentesting box.
> 

# **🐉 Kali Linux Fundamentals**

---

A complete beginner-to-pro overview of **Kali Linux** — from its roots to real-world usage.

## **📜 What is Kali Linux?**

---

Kali Linux is a **Debian-based distribution** maintained by Offensive Security, designed for:

- 🛠️ Penetration Testing
- 🕵️ Ethical Hacking
- 🧪 Digital Forensics
- 🔍 Security Research

Kali comes **pre-installed** with hundreds of tools for reconnaissance, exploitation, forensics, wireless attacks, post-exploitation, and more.

## **🧬 BackTrack Linux: The Origin (2006–2013)**

---

Before Kali, there was **BackTrack Linux**, a legendary pentesting distro created by merging:

- **WHAX (Whoppix)**: Wireless auditing distro
- **Auditor Security Collection**: A security toolkit with a GUI

### **🔧 BackTrack v1 (2006)**

---

- Combined WHAX and Auditor tools
- Bootable Live CD
- Focused on wireless hacking, scanning, and exploitation
- Tools: **Aircrack-ng**, **Kismet**, **Nmap**, **Metasploit**

### **⚠️ Limitations**

---

- No package management system
- Minimal persistence and customization
- Non-compliant with Filesystem Hierarchy Standard (FHS)

## **🔁 Evolution of BackTrack Versions**

---

| Version | Release Year | Base System | Highlights |
| --- | --- | --- | --- |
| BackTrack v1 | 2006 | Slackware | First version; Live CD; merged toolsets |
| BackTrack v2 | 2007 | Slackware | Better hardware support |
| BackTrack v3 | 2008 | Slackware | KDE GUI improvements, more tools |
| BackTrack v4 | 2009 | Ubuntu | Persistence introduced, better updates |
| BackTrack 5 | 2011 | Ubuntu | GNOME/KDE desktops, code-named "Revolution" |

## **🎉 Birth of Kali Linux (2013)**

---

In **March 2013**, **Kali Linux** was born as the spiritual successor of BackTrack Linux.

### **🚨 Why the Change?**

---

- BackTrack lacked proper package management
- Script maintenance was messy
- Needed FHS-compliance and modularity
- Developers wanted a cleaner, more modern base

## **💡 Key Improvements in Kali**

---

- ✅ Based on **Debian**
- ✅ Uses **APT** package manager
- ✅ Fully **FHS-compliant**
- ✅ ISO customization via **live-build**
- ✅ Rolling release model
- ✅ Initially ran as **root by default**

## **🧑‍💻 Maintainers & Community**

---

- **Developed by**: Offensive Security
- **Website**: kali.org
- **Tool List**: kali.org/tools/all-tools/
- **Community**: Strong community, docs, and training content available

## **🧩 Overview of Kali Linux Use Cases**

---

Kali is a full-fledged toolkit for:

- 🔓 Penetration Testing
- 🔍 Security Auditing
- 🔬 Digital Forensics
- 📡 Wireless Attacks
- 🎯 Red Team Operations

## **🛠️ Essential Kali Tools**

---

| Tool | Purpose |
| --- | --- |
| nmap | Network scanning |
| metasploit | Exploitation framework |
| burpsuite | Web application testing |
| wireshark | Packet capture and analysis |
| aircrack-ng | Wireless network cracking |
| hydra | Brute force login attacks |
| john | Password cracking |
| nikto | Web server vulnerability scanner |

## **🐧 Basic Linux Commands Cheat Sheet**

---

### **📁 Filesystem**

```
`pwd`                      # Show current directory
`ls -l`                    # List files with details
`cd /path/to/dir`          # Change directory
`cat file.txt`             # View file content
`cp file.txt /dest/`       # Copy file
`mv old.txt new.txt`       # Move/rename file
`rm file.txt`              # Delete file
`rm -r folder/`            # Delete directory
`grep "string" file.txt`   # Search string in file
`find / -name "file.txt"`  # Search for file by name
```

### **👥 Users & Permissions**

```
`who`                      # View current users
`whoami`                   # Show logged-in user
`adduser hacker`           # Add new user
`chmod 755 script.sh`      # Change file permissions
`chown user:user file.txt` # Change file ownership
```

### **🌐 Networking**

```
`ping google.com`          # Ping a host
`nmap -sS 192.168.1.1`     # Scan open ports
`ifconfig`                 # Show IP address (or use `ip a`)
`route -n`                 # Display routing table
```

### **🔧 System & Process**

```
`ps aux`                   # Show running processes
`kill -9 <PID>`            # Kill a process
`uname -a`                 # OS and kernel info
`cat /etc/os-release`      # Distro version info
```

## **📦 Package Management (APT)**

---

```
`apt update`               # Update package lists
`apt upgrade`              # Upgrade all packages
`apt install nmap`         # Install package
`apt remove hydra`         # Remove package
```

## **🚦 Service Management (systemd)**

---

```
`systemctl start apache2`  # Start service
`systemctl enable apache2` # Enable service at boot
`systemctl status ssh`     # Check service status
```

## **📦 File Compression**

---

```
`tar -czvf archive.tar.gz folder/`  # Create tar.gz
`tar -xzvf archive.tar.gz`          # Extract tar.gz
```

## **⚙️ Kali-Specific Tools & Commands**

---

```
`msfconsole`               # Launch Metasploit
`setoolkit`                # Start Social Engineering Toolkit
`burpsuite`                # Launch Burp Suite
`airmon-ng start wlan0`    # Start wireless monitor mode
```

## **⬆️ Privilege Escalation Tips**

---

```
`find / -perm -4000 2>/dev/null`        # Find SUID binaries
`find / -type f -perm -o+w 2>/dev/null` # World-writable files
`uname -a`                              # Kernel version
`cat /etc/os-release`                   # Distro info
```

## **💎 Pro Tips for Pentesters**

---

- ⚠️ Run tools as **root** when required: sudo
- 💾 Use **VirtualBox Snapshots** before testing risky exploits
- 📝 Keep a **notes file** with observations, commands, and results
- 🔄 Practice safe and repeatable testing setups

# **🔽 Kali Linux Download & Installation**

---

### **🖥️ 1. Installer Images (Bare Metal)**

---

- **What it is**: Full offline installation ISOs.
- **Why use it**: Best performance—complete hardware access (Wi‑Fi, GPU), fully FHS-compliant, easy customization.
- **Ideal for**: Dedicated hacking workstations or dual‑boot rigs.
- **Link**: kali.org/get-kali/#kali-installer-images

### **🛡️ 2. Virtual Machines**

---

- **What it is**: Pre-built VMware/VirtualBox images (plus Vagrant).
- **Why use it**: Snapshots, isolated environments, no changes to host.
- **Ideal for**: Safe testing environments or multi‑platform labs.
- **Link**: kali.org/get-kali/#kali-virtual-machines

### **⚙️ 3. ARM**

---

- **What it is**: Builds for ARM architectures (Raspberry Pi, Pinebook, etc.).
- **Why use it**: Ultra-portable, efficient, long battery life.
- **Ideal for**: Field testing with SBCs or ARM laptops.
- **Link**: kali.org/get-kali/#kali-arm

### **📱 4. Mobile (Kali NetHunter)**

---

- **What it is**: Kali on Android + Kali Container + KeX + App Store.
- **Why use it**: Pocket penetration testing.
- **Ideal for**: Red teams or demos on-the-go.
- **Link**: kali.org/get-kali/#kali-mobile

### **☁️ 5. Cloud**

---

- **What it is**: Hosted Kali images on AWS, Azure, Linode, etc.
- **Why use it**: Instant scalability without local hardware.
- **Ideal for**: Red-team campaigns, shared labs, remote testing.
- **Link**: kali.org/get-kali/#kali-cloud

### **📦 6. Containers**

---

- **What it is**: Docker/LXD containers with Kali tools.
- **Why use it**: Lightweight, fast, no VM overhead.
- **Ideal for**: Quick Kali sessions in CI pipelines or DevOps workflows.
- **Link**: kali.org/get-kali/#kali-containers

### **🔄 7. Live Boot (USB/DVD)**

---

- **What it is**: Bootable media—no installation required.
- **Why use it**: Non-invasive, full hardware access, optional persistence.
- **Ideal for**: On-the-fly assessments, forensics, demo environments.
- **Link**: kali.org/get-kali/#kali-live

### **🪟 8. WSL (Windows Subsystem for Linux)**

---

- **What it is**: Kali runs within Windows.
- **Why use it**: Seamless integration, no need for VM or dual‑boot.
- **Ideal for**: Windows users needing command‑line Kali tools.
- **Link**: kali.org/get-kali/#kali-wsl

### **🛠️ 9. Build Scripts**

---

- **What it is**: live-build scripts to customize or build your own ISO.
- **Why use it**: Craft custom desktop setups, embed unique toolchains.
- **Ideal for**: Custom toolkits, branding, enterprise use-cases.
- **Link**: kali.org/get-kali/#kali-build-scripts

## **✅ Choosing Your Platform**

---

| Scenario | Recommended Platform |
| --- | --- |
| Dedicated pentesting workstation | Installer (Bare Metal) |
| Virtualized lab or sandboxed testing | Virtual Machines |
| Portable ARM-based pen-testing | ARM Image |
| Red teaming from your phone/tablet | Mobile (NetHunter) |
| Remote infra, full-scale engagements | Cloud |
| CI pipelines or ephemeral Kali environments | Containers |
| On-the-fly testing or forensics | Live Boot USB |
| Integration into Windows workflows | WSL |
| Custom Kali ISO creation/branding | Build Scripts |

# **🔽 Kali Linux Download & Installation Guide (Installer Image)**

---

## **✅ Step 1: Go to the Official Kali Installer Page**

---

Visit: kali.org/get-kali/#kali-installer-images

This takes you to the **Kali Installer Images** section on the official Kali website.

## **📥 Step 2: Choose Your ISO to Download**

---

You’ll see multiple ISO options. Here are the two main ones:

### **🟢 Installer (Recommended)**

---

- **File**: kali-linux-<version>-installer-amd64.iso
- **Use Case**: Install Kali like a normal OS (bare metal or VM)
- **Advantages**: Fast, ideal for most users, clean and minimal setup

### **🟡 Everything ISO (Advanced Users)**

---

- **File**: kali-linux-<version>-everything-amd64.iso
- **Use Case**: Comes with **every Kali tool pre-installed**
- **Advantages**: Much larger (~9GB+), ideal for offline use in isolated environments or pentest labs

> Choose one:
> 

| Scenario | ISO to Choose |
| --- | --- |
| Regular install (recommended) | Installer ISO |
| Want all tools preloaded | Everything ISO |

# **🐉 Kali Linux Installation & Setup Guide (VirtualBox, Repos, SSH, Drivers)**

---

> 📝 Blog Post: Creating a Dual Bootable PC (Windows + Kali Linux)
> 
> 
> A complete guide on installing and configuring Windows and Kali Linux on the same system.
> 

## **🖥️ Create Virtual Machine (VM) – VirtualBox**

---

1. Open **VirtualBox** → Click **New**
2. **Name**: Kali Linux
3. **Type**: Linux
4. **Version**: Debian (64-bit)

### **💾 Hardware Settings**

---

- **RAM**: 8 GB (8192 MB)
- **CPU**: 2 Cores
- **Hard Disk**: 100 GB (Create new VDI)

### **📀 ISO Image**

---

- Download the latest Kali ISO: kali.org/get-kali/#kali-virtual-machines
- Attach the ISO under **Settings > Storage > Optical Drive**

## **🚀 Installation Process**

---

Start the VM and choose:

### **🎛️ Boot Options**

---

- **Graphical Install**: Recommended UI-based setup
- **Install**: TUI (Tab-based)
- **Advanced Options**: Troubleshooting tools

### **🌍 Language & Location**

---

- **Language**: English
- **Location**: United States
- **Keyboard**: American English

### **💻 User & Host Info**

---

- **Hostname**: kali
- **Domain**: (leave blank)
- **Full Name**: Nikhil
- **Username**: nikhil
- **Password**: 123 (confirm: 123)

### **🧱 Disk Partitioning**

---

### **Option 1: Manual**

---

Create **3 Partitions**:

1. **/boot**: 1 GB (Primary)
2. **swap**: 5 GB (Primary)
3. **/**: Remaining space (Root)

> 💡 Use manual mode for full control in dual-boot or performance tuning.
> 

### **Option 2: Guided – Use Entire Disk**

---

- Automatically partitions with recommended layout

### **🧰 Software Selection**

---

- **Desktop Environment**:
    - XFCE (default)
    - GNOME
    - KDE Plasma
- **Tool Collections**:
    - Top 10 tools
    - Default tools
    - Large selection (optional)

> ⚠️ Desktop environment selection affects installation size and user experience.
> 

### **🔧 Grub Bootloader**

---

- Select Yes to install GRUB
- Choose your disk (usually /dev/sda) to install bootloader

### **✅ Finish Installation**

---

- Installation complete → Reboot the VM


🌐 IP Configuration (Manual)







Go to Settings > Network > Adapter 1



Set to Bridged Adapter for real network access

In Kali:





Settings > Network > IPv4





Method: Manual



Enter IP, Netmask, Gateway manually

🔐 Enable SSH + Root Access





By default, root login is disabled in Kali.

🧑 Switch to Root User



`sudo su -`
`passwd`  # Set root password

🎨 Font Size / Display







XFCE/Settings > Appearance > Fonts



Increase font size for terminals and system UI

🐉 Kali Linux Full Setup Guide for Bug Bounty & Pentesting





✨ Power-up your hacking machine with the ultimate Kali Linux setup. From system tuning to tool installation, this guide gets your box ready for real-world action.

🧠 What is Kali Linux?



Kali Linux is a Debian-based Linux distro built for penetration testers, bug bounty hunters, ethical hackers, and cybersecurity professionals. It comes preloaded with 600+ tools for digital forensics and offensive security. It’s often the first choice for hacking, testing, and red teaming.

🛠️ Step-by-Step Configuration Guide



1. 🔐 Set Root Password & Switch to Root User



`sudo passwd`
`sudo su -`



Set root user password and switch to root environment.

2. 🧰 Install Basic Packages



`apt install apt-transport-https vim curl`



Enables HTTPS-based repo access and basic CLI tools.

3. 🔧 Edit Sources List & Use Faster Mirror



`vim /etc/apt/sources.list`

Default:

deb http://http.kali.org/kali kali-rolling main contrib non-free

Fast Mirror:

deb https://kali.download/kali kali-rolling main contrib non-free



💡 Mirror List: http.kali.org/README.mirrorlist
Use mirrors for better speed. Revert if downloads fail or slow down.

4. 🔑 Add Kali Repo GPG Key (Security Check)



`curl -fsSL https://archive.kali.org/archive-key.asc | sudo gpg --dearmor -o /usr/share/keyrings/kali-archive-keyring.gpg`

5. 🔃 Clean Old Cache & Update System



`apt-get clean`
`rm -rf /var/lib/apt/lists/*`
`apt update`

6. 🔁 Perform Full System Upgrade



`apt upgrade -y`
`apt dist-upgrade -y`
`apt full-upgrade -y`



Ensures everything is fully up-to-date.

7. 🧱 Install Kernel Headers (For Driver Compatibility)



`apt install linux-headers-$(uname -r)`

8. 🛑 Reboot If Required



`[ -f /var/run/reboot-required ] && reboot`

9. 🧑‍💻 Enable & Start SSH Service



`sudo systemctl start ssh`
`sudo systemctl enable ssh`
`sudo systemctl restart ssh`



Enables remote access for SSH.

10. 🖥️ Use screen for Persistent Terminals



`apt install screen`
`screen --help`
`screen`  # Start new session

11. 🧰 Install Kali Metapackages



Full Toolkit



`apt install kali-linux-everything`

Large Toolset



`apt install kali-linux-large`

GNOME Desktop



`apt install kali-desktop-gnome`

12. 📶 Realtek RTL8812AU Wi-Fi Adapter Setup (Monitor Mode + Packet Injection)



a. Update System



`apt update`

b. Install Dependencies



`apt install dkms git build-essential libelf-dev linux-headers-$(uname -r)`

c. Install Drivers



`apt install realtek-rtl88xxau-dkms`



💡 DKMS will auto-rebuild after kernel updates.

✅ Final Reboot



`reboot`

NVIDIA Drivers Installation on Optimus Laptop (Kali Linux)





An NVIDIA driver is software that acts as a bridge between your operating system and your NVIDIA graphics card (GPU).

Step 1: Check Your System Info



`uname -a`
`lspci | grep -E "VGA|3D"`

Example Output:

VGA compatible controller: Intel Corporation TigerLake-H GT1 [UHD Graphics]
VGA compatible controller: NVIDIA Corporation GA107M [GeForce RTX 3050 Mobile]

Step 2: Disable the Nouveau Driver (Open Source NVIDIA)



`echo -e "blacklist nouveau\noptions nouveau modeset=0\nalias nouveau off" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf`
`sudo update-initramfs -u`
`sudo reboot`



After reboot, verify:

`lsmod | grep -i nouveau`



If it returns nothing, Nouveau is disabled successfully.

Step 3: Install NVIDIA Driver



`sudo apt install nvidia-driver nvidia-xconfig`



If errors occur:

`sudo apt install nvidia-xconfig`

Step 4: Find NVIDIA BusID



`nvidia-xconfig --query-gpu-info | grep 'BusID' | cut -d ' ' -f6-`

Example Output:

PCI:1:0:0

Step 5: Final Driver Reboot



`[ -f /var/run/reboot-required ] && sudo reboot -f`

Or:

`sudo reboot`

CUDA Toolkit Setup (For GPU Acceleration)





Official Site: CUDA Downloads

Step 1: Add CUDA Repository Keyring



`wget https://developer.download.nvidia.com/compute/cuda/repos/debian12/x86_64/cuda-keyring_1.1-1_all.deb`
`sudo apt install ./cuda-keyring_1.1-1_all.deb`

Step 2: (Optional) Comment Out Kali Default Repos



`sudo vim /etc/apt/sources.list`

Comment out:

# deb https://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware



Reference: Kali Source Guide

Step 3: Install CUDA Toolkit & DKMS



`sudo apt update`
`sudo apt install cuda-toolkit-12-9`
`sudo apt install cuda-drivers nvidia-kernel-dkms`
`sudo reboot`

Final Verification



Check if NVIDIA driver is working:

`nvidia-smi`

Check kernel modules:

`lsmod | grep -i nvidia`

Extra: Test GPU Acceleration



Hashcat



`hashcat -I`
`hashcat -b`  # Benchmark

NVIDIA Driver Cleanup Commands





⚠️ Caution: Use these commands only in case of misconfiguration or errors to remove NVIDIA drivers:

`apt-get remove --purge nvidia*`
`rm -rf /etc/X11/xorg.conf`
`dpkg --configure -a`
`apt autoremove`



⚠️ After successful NVIDIA driver installation, do not run:

`apt autoremove`
`apt autoclean`



These commands may delete the drivers.

Installing FFmpeg with NVENC Support (Kali Linux)





FFmpeg with NVENC allows hardware-accelerated video encoding using supported NVIDIA GPUs. Ideal for faster video processing, screen recording, and streaming.

Step 1: Install FFmpeg



`sudo apt update`
`sudo apt install ffmpeg`

Step 2: Check NVENC Encoder Support



`ffmpeg -encoders 2>/dev/null | grep nvenc`



If output shows encoders like h264_nvenc or hevc_nvenc, NVENC is enabled.

Step 3: Benchmark GPU with Hashcat



Check CUDA acceleration and GPU benchmark:

`hashcat -I`
`hashcat -b`

Installing NVIDIA Video Codec SDK (For NVENC/NVDEC Support)





The NVIDIA Video Codec SDK allows low-level access to hardware-accelerated encoding (NVENC) and decoding (NVDEC), useful for compiling or extending media tools like FFmpeg.

Step 1: Download the SDK





Visit: developer.nvidia.com/nvidia-video-codec-sdk
Requires an NVIDIA Developer account to download.

Download file:

Video_Codec_SDK_13.0.19.zip

Step 2: Extract and Move to Standard Path



`unzip Video_Codec_SDK_13.0.19.zip`
`sudo mv -v Video_Codec_SDK_13.0.19 /opt/`

Step 3: Verify CUDA Headers



Ensure CUDA Toolkit is installed and include path exists:

`ls /usr/local/cuda/include`



If not found, install CUDA Toolkit first (see CUDA section above).

Step 4: Copy SDK Headers to CUDA Include Path



`cd /opt/Video_Codec_SDK_13.0.19/Interface`
`sudo cp -v *.h /usr/local/cuda/include/`



Enables FFmpeg or other tools to compile with NVENC/NVDEC support.

Final Verifications



Check NVENC support:

`ffmpeg -hide_banner -hwaccels`

Check NVIDIA driver + GPU health:

`nvidia-smi`

Useful Tools and System Setup for Linux



Install System Utilities



Install commonly used tools, libraries, fonts, network utilities, development packages, and penetration testing tools:

`sudo apt install -y \
build-essential cmake ninja-build libgtkmm-3.0-dev libgtksourceviewmm-3.0-dev libxml++2.6-dev libsqlite3-dev gettext \
libgspell-1-dev libcurl4-openssl-dev libuchardet-dev libfribidi-dev libvte-2.91-dev libfmt-dev libspdlog-dev \
rclone vim fonts-lato fonts-open-sans fonts-roboto fonts-mononoki fonts-indic grc python3 python-is-python3 \
gcc-multilib g++-multilib libtesseract-dev jq python3-pip openvpn network-manager-openvpn network-manager-openvpn-gnome \
testssl.sh dirsearch virtualbox virtualbox-ext-pack virtualbox-guest-additions-iso golang remmina remmina-plugin-rdp \
remmina-plugin-secret flameshot ruby whois git curl libpcap-dev wget zip python3-dev pv dnsutils libssl-dev libffi-dev \
libxml2-dev libxslt1-dev zlib1g-dev nmap apt-transport-https lynx tor medusa xvfb libxml2-utils procps bsdmainutils \
libdata-hexdump-perl tmux masscan unzip chromium rsync coreutils net-tools htop prips xmlstarlet gnome-power-manager \
jython mesa-utils wmctrl libgl1-mesa-dev xorg-dev espeak libespeak1 python3-full tesseract-ocr gimagereader \
gnome-tweaks gnome-shell-extensions sshuttle chisel network-manager-l2tp network-manager-l2tp-gnome firmware-linux \
thunderbird obs-studio pkg-config checkinstall autoconf automake libtool-bin libreadline-dev libusb-1.0-0-dev \
libplist-dev libimobiledevice-dev libimobiledevice-glue-dev libtatsu-dev libzip-dev libimobiledevice-utils \
mediainfo alacarte`





Google Chrome



Install the stable version:

`wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
`sudo apt install ./google-chrome-stable_current_amd64.deb`

Optionally, install all Chrome variants:

`sudo apt install google-chrome-beta google-chrome-unstable google-chrome-stable`

Remove beta and unstable repo entries:

`sudo rm -vf /etc/apt/sources.list.d/google-chrome-beta.list`
`sudo rm -vf /etc/apt/sources.list.d/google-chrome-unstable.list`
`sudo apt update`

Sublime Text





Visit: sublimetext.com

`wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg > /dev/null`
`echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list`
`sudo apt update`
`sudo apt install sublime-text`

Slack



`wget https://downloads.slack-edge.com/linux_releases/slack-desktop-4.33.90-amd64.deb`
`sudo apt install ./slack-desktop-4.33.90-amd64.deb`

If dependencies are missing:

`wget http://ftp.us.debian.org/debian/pool/main/libi/libindicator/libindicator3-7_0.5.0-4_amd64.deb`
`wget http://ftp.us.debian.org/debian/pool/main/liba/libappindicator/libappindicator3-1_0.4.92-7_amd64.deb`
`sudo dpkg -i libindicator3-7_0.5.0-4_amd64.deb`
`sudo dpkg -i libappindicator3-1_0.4.92-7_amd64.deb`
`sudo apt install -f`

VirtualBox



`sudo apt install virtualbox virtualbox-ext-pack virtualbox-guest-additions-iso`

OpenVPN



`sudo apt install openvpn network-manager-openvpn network-manager-openvpn-gnome`

Flameshot



Install:

`sudo apt install flameshot`

Run:

`/usr/bin/flameshot gui`

Set up Flameshot to use PrintScreen key:





Open Settings > Devices > Keyboard > Shortcuts



Search "print", click it, press Backspace to unbind



Click "+" to add a new shortcut:





Name: Flameshot



Command: /usr/bin/flameshot gui



Set shortcut: Press PrtSc key

Example config:

[General]
checkForUpdates=true
contrastOpacity=188
filenamePattern=file_%Y-%m-%d_%H-%M-%S
saveAfterCopy=true
savePathFixed=true
showStartupLaunchMessage=true
squareMagnifier=false
uploadHistoryMax=25

Visual Studio Code



Install via .deb from the official website:

`wget "https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64" -O vscode.deb`
`sudo apt install ./vscode.deb`

Youtube-DL



`sudo apt install youtube-dl`

Remmina



`sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret`

Testssl.sh and Dirsearch



`git clone https://github.com/drwetter/testssl.sh`
`git clone https://github.com/maurosoria/dirsearch.git`

wkhtmltopdf



`wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.buster_amd64.deb`
`sudo apt install ./wkhtmltox_0.12.6-1.buster_amd64.deb`

Geckodriver (For Selenium)



`wget https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-linux64.tar.gz`
`tar -xvzf geckodriver-v0.34.0-linux64.tar.gz`
`sudo mv geckodriver /usr/local/bin/`

Tesseract OCR



`sudo apt install tesseract-ocr gimagereader libtesseract-dev`

Mirror & Control Android Phone



Use tools like:





scrcpy: USB-based screen mirroring



sndcpy: For audio



KDE Connect: Wireless integration

Go (Golang) Installation Guide for Linux



This guide covers:





Installing a specific version of Go (Golang)



Configuring your environment



Installing Go-based tools for Offensive Security

1. Check Existing Go Installation



`go version`





If installed, it returns the version (e.g., go version go1.20.4 linux/amd64)



If not, you'll get an error

2. Download Go



Official Download Page: go.dev/dl

Direct download (example for Go 1.24.5):

`wget https://go.dev/dl/go1.24.5.linux-amd64.tar.gz`



Update the version URL based on your preferred Go release.

3. Remove Existing Go Installation



To avoid version conflicts:

`sudo apt remove golang-go`

4. Remove Old Go Directory (if exists)



Check if the Go directory is present:

`ls /usr/local/go`

If it exists, remove it and extract the new tarball:

`sudo rm -rf /usr/local/go`
`sudo tar -C /usr/local -xzf go1.24.5.linux-amd64.tar.gz`

Verify:

`ls /usr/local/go`

5. Confirm Go Installation



`/usr/local/go/bin/go version`

6. Set Environment Variables



Detect your shell:

`echo $SHELL`

Add the following to your shell configuration file:

For Zsh (~/.zshrc)



`echo "export GOROOT=/usr/local/go" >> ~/.zshrc`
`echo "export GOPATH=\$HOME/go" >> ~/.zshrc`
`echo "export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin" >> ~/.zshrc`
`source ~/.zshrc`

For Bash (~/.bashrc)



`echo "export GOROOT=/usr/local/go" >> ~/.bashrc`
`echo "export GOPATH=\$HOME/go" >> ~/.bashrc`
`echo "export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin" >> ~/.bashrc`
`source ~/.bashrc`

7. Verify Go Installation



`go version`

You should see the version installed (e.g., go version go1.24.5 linux/amd64)

Installing Go Tools for Offensive Security



Install popular Go-based pentesting tools using a script from InfoSecWarrior.

1. Become Root



`sudo su -`

2. Download the Installation Script



Navigate to /opt:

`cd /opt`

Download the script:

`wget https://raw.githubusercontent.com/InfoSecWarrior/Offensive-Pentesting-Scripts/main/Gotools-Install/gotools-install.sh`

Make it executable:

`chmod +x gotools-install.sh`

3. Run the Script



`./gotools-install.sh`

This script installs commonly used Go-based security tools, such as:





httpx



subfinder



naabu



amass



dnsx



and more...

Final Check



`which go`
`go version`
`which httpx`

🐍 Python Installation and Environment Setup



This guide covers:





Installing Python 2.7 and Python 3.x



Setting up pip for both versions



Installing BeautifulSoup4



Creating an isolated Python environment using venv

✅ Checking Existing Python & Pip Versions



`python -V`
`python2.7 -V`
`pip -V`
`pip2.7 -V`

🌿 Installing BeautifulSoup4



`pip install beautifulsoup4`
`pip2.7 install beautifulsoup4`

📦 Installing pip for Python 2.7



If pip2.7 is not available:





Download the installer:

`wget https://bootstrap.pypa.io/pip/2.7/get-pip.py -O get-pip.py`



Run the installer:

`python2.7 get-pip.py`



Verify pip:

`pip2.7 -V`



Test installation:

`pip2.7 install beautifulsoup4`

🐍 Installing pip for Default Python (Python 3.x)



If pip is not available for Python 3:

`wget https://bootstrap.pypa.io/pip/get-pip.py -O get-pip.py`
`python get-pip.py`

🧱 Installing Python 3 Full Package and venv



`sudo apt install python3.13-venv`
`sudo apt install python3-full python-is-python3`

🏗️ Creating a Virtual Environment







Make a directory for the environment:

`mkdir /opt/python-environment`



Create the virtual environment:

`python3 -m venv /opt/python-environment`

📥 Installing pip in the Virtual Environment



If pip is missing in the virtual environment:





Download get-pip:

`wget https://bootstrap.pypa.io/pip/get-pip.py -O get-pip.py`



Run the installer using the virtual environment’s Python:

`/opt/python-environment/bin/python get-pip.py`



Check pip version:

`/opt/python-environment/bin/pip -V`

🔄 Setting System-wide pip to Virtual Environment







Check existing pip path:

`which pip`



Remove current symlink if needed:

`ls -lh /usr/local/bin/pip`
`sudo rm -f /usr/local/bin/pip`



Create a new symlink:

`sudo ln -s /opt/python-environment/bin/pip /usr/local/bin/pip`



Confirm:

`pip -V`



Install globally using this pip:

`pip install beautifulsoup4`

🔎 Version Check Summary



`pip -V`
# Output: pip 25.1.1 from /opt/python-environment/lib/python3.13/site-packages/pip (python 3.13)

`pip2.7 -V`
# Output: pip 20.3.4 from /usr/local/lib/python2.7/dist-packages/pip (python 2.7)

`python -V`
# Output: Python 3.13.5

`python2.7 -V`
# Output: Python 2.7.18

🧬 Making the Virtual Environment Globally Accessible



Add virtual environment path to your shell config:

For Zsh users



`echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.zshrc`
`source ~/.zshrc`

For Bash users



`echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.bashrc`
`source ~/.bashrc`

ZSH Shell Installation and Configuration



Step 1: Install ZSH



`sudo apt install zsh`

Step 2: Download .zshrc Configuration File



`cd ~`
`wget https://raw.githubusercontent.com/nikhilpatidar01/Ethical-Hacking/Master/3.%20Kali%20Linux/.zshrc`

Check downloaded .zshrc:

`ls -la ~ | grep zshrc`

Remove .zshrc if needed:

`rm -f ~/.zshrc`

Step 3: Set ZSH as Default Shell



`chsh -s $(which zsh)`

Step 4: Apply Config Without Restart



`source ~/.zshrc`

🖥️ What is linux-desktop-shortcuts?







Linux: Related to Linux systems.



Desktop: .desktop files are used by Linux desktop environments (GNOME, KDE, XFCE, etc.) to integrate apps into the application menu, dock, or taskbar.



Shortcuts: .desktop files act like shortcuts/launchers for applications (similar to .lnk files in Windows).

1. VirtualBox Launcher Setup







Edit the file:

`sudo vim /usr/share/applications/virtualbox.desktop`






