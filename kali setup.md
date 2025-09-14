# Kali Linux Full Setup Guide for Bug Bounty & Pentesting

✨ Power-up your hacking machine with the ultimate Kali Linux setup. From system tuning to tool installation, this guide gets your box ready for real-world action.

## 🧠 What is Kali Linux?

Kali Linux is a Debian-based Linux distro built for penetration testers, bug bounty hunters, ethical hackers, and cybersecurity professionals. It comes preloaded with 600+ tools for digital forensics and offensive security. It’s often the first choice for hacking, testing, and red teaming.

## 🛠️ Initial Setup After Installation

### Installation Complete → Reboot the VM

After completing the installation, reboot the virtual machine.

### 🌐 IP Configuration (Manual)

1. Go to VM Settings > Network > Adapter 1.
2. Set to Bridged Adapter for real network access.

In Kali Linux:

1. Go to Settings > Network > IPv4.
2. Set Method: Manual.
3. Enter IP, Netmask, and Gateway manually.

### 🔐 Enable SSH + Root Access

By default, root login is disabled in Kali.

#### 🧑 Switch to Root User and Set Password

```
sudo su -
```

```
passwd
```

(Enter and confirm the root password.)

### 🎨 Font Size / Display Adjustments

In XFCE: Go to Settings > Appearance > Fonts.

Increase font size for terminals and system UI as needed.

## 🛠️ Step-by-Step Configuration Guide

### 🔐 Set Root Password & Switch to Root User

```
sudo passwd
```

```
sudo su -
```

Set root user password and switch to root environment.

### 🧰 Install Basic Packages

```
apt install apt-transport-https vim curl
```

Enables HTTPS-based repo access and basic CLI tools.

### 🔧 Edit Sources List & Use Faster Mirror

Edit the file:

```
vim /etc/apt/sources.list
```

Default content:

```
deb http://http.kali.org/kali kali-rolling main contrib non-free
```

Recommended faster mirror:

```
deb https://kali.download/kali kali-rolling main contrib non-free
```

💡 Mirror List: http.kali.org/README.mirrorlist. Use mirrors for better speed. Revert if downloads fail or slow down.

### 🔑 Add Kali Repo GPG Key (Security Check)

```
curl -fsSL https://archive.kali.org/archive-key.asc | sudo gpg --dearmor -o /usr/share/keyrings/kali-archive-keyring.gpg
```

### 🔃 Clean Old Cache & Update System

```
apt-get clean
```

```
rm -rf /var/lib/apt/lists/*
```

```
apt update
```

### 🔁 Perform Full System Upgrade

```
apt upgrade -y
```

```
apt dist-upgrade -y
```

```
apt full-upgrade -y
```

Ensures everything is fully up-to-date.

### 🧱 Install Kernel Headers (For Driver Compatibility)

```
apt install linux-headers-$(uname -r)
```

### 🛑 Reboot If Required

```
[ -f /var/run/reboot-required ] && reboot
```

### 🧑‍💻 Enable & Start SSH Service

```
sudo systemctl start ssh
```

```
sudo systemctl enable ssh
```

```
sudo systemctl restart ssh
```

Enables remote access for SSH.

### 🖥️ Use screen for Persistent Terminals

```
apt install screen
```

```
screen --help
```

```
screen
```

(Start a new session.)

### 🧰 Install Kali Metapackages

#### Full Toolkit

```
apt install kali-linux-everything
```

#### Large Toolset

```
apt install kali-linux-large
```

#### GNOME Desktop

```
apt install kali-desktop-gnome
```

### 📶 Realtek RTL8812AU Wi-Fi Adapter Setup (Monitor Mode + Packet Injection)

a. Update System

```
apt update
```

b. Install Dependencies

```
apt install dkms git build-essential libelf-dev linux-headers-$(uname -r)
```

c. Install Drivers

```
apt install realtek-rtl88xxau-dkms
```

💡 DKMS will auto-rebuild after kernel updates.

### ✅ Final Reboot

```
reboot
```

## NVIDIA Drivers Installation on Optimus Laptop (Kali Linux)

An NVIDIA driver is software that acts as a bridge between your operating system and your NVIDIA graphics card (GPU).

### Step 1: Check Your System Info

```
uname -a
```

```
lspci | grep -E "VGA|3D"
```

Example Output:

- VGA compatible controller: Intel Corporation TigerLake-H GT1 [UHD Graphics]
- VGA compatible controller: NVIDIA Corporation GA107M [GeForce RTX 3050 Mobile]

### Step 2: Disable the Nouveau Driver (Open Source NVIDIA)

```
echo -e "blacklist nouveau\noptions nouveau modeset=0\nalias nouveau off" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
```

```
sudo update-initramfs -u
```

```
sudo reboot
```

After reboot, verify:

```
lsmod | grep -i nouveau
```

(If it returns nothing, Nouveau is disabled successfully.)

### Step 3: Install NVIDIA Driver

```
sudo apt install nvidia-driver nvidia-xconfig
```

If errors occur:

```
sudo apt install nvidia-xconfig
```

### Step 4: Find NVIDIA BusID

```
nvidia-xconfig --query-gpu-info | grep 'BusID' | cut -d ' ' -f6-
```

Example Output: PCI:1:0:0

### Step 5: Final Driver Reboot

```
[ -f /var/run/reboot-required ] && sudo reboot -f
```

Or:

```
sudo reboot
```

## CUDA Toolkit Setup (For GPU Acceleration)

Official Site: CUDA Downloads

### Step 1: Add CUDA Repository Keyring

```
wget https://developer.download.nvidia.com/compute/cuda/repos/debian12/x86_64/cuda-keyring_1.1-1_all.deb
```

```
sudo apt install ./cuda-keyring_1.1-1_all.deb
```

### Step 2: (Optional) Comment Out Kali Default Repos

Edit:

```
sudo vim /etc/apt/sources.list
```

Comment out:

```
deb https://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware
```

Reference: Kali Source Guide

### Step 3: Install CUDA Toolkit & DKMS

```
sudo apt update
```

```
sudo apt install cuda-toolkit-12-9
```

```
sudo apt install cuda-drivers nvidia-kernel-dkms
```

```
sudo reboot
```

### Final Verification

Check if NVIDIA driver is working:

```
nvidia-smi
```

Check kernel modules:

```
lsmod | grep -i nvidia
```

### Extra: Test GPU Acceleration with Hashcat

```
hashcat -I
```

```
hashcat -b
```

(Benchmark)

## NVIDIA Driver Cleanup Commands

⚠️ Caution: Use these commands only in case of misconfiguration or errors to remove NVIDIA drivers:

```
apt-get remove --purge nvidia*
```

```
rm -rf /etc/X11/xorg.conf
```

```
dpkg --configure -a
```

```
apt autoremove
```

⚠️ After successful NVIDIA driver installation, do not run:

```
apt autoremove
```

```
apt autoclean
```

These commands may delete the drivers.

## Installing FFmpeg with NVENC Support (Kali Linux)

FFmpeg with NVENC allows hardware-accelerated video encoding using supported NVIDIA GPUs. Ideal for faster video processing, screen recording, and streaming.

### Step 1: Install FFmpeg

```
sudo apt update
```

```
sudo apt install ffmpeg
```

### Step 2: Check NVENC Encoder Support

```
ffmpeg -encoders 2>/dev/null | grep nvenc
```

If output shows encoders like h264_nvenc or hevc_nvenc, NVENC is enabled.

### Step 3: Benchmark GPU with Hashcat

```
hashcat -I
```

```
hashcat -b
```

## Installing NVIDIA Video Codec SDK (For NVENC/NVDEC Support)

The NVIDIA Video Codec SDK allows low-level access to hardware-accelerated encoding (NVENC) and decoding (NVDEC), useful for compiling or extending media tools like FFmpeg.

### Step 1: Download the SDK

Visit: developer.nvidia.com/nvidia-video-codec-sdk (Requires an NVIDIA Developer account to download.)

Download file: Video_Codec_SDK_13.0.19.zip

### Step 2: Extract and Move to Standard Path

```
unzip Video_Codec_SDK_13.0.19.zip
```

```
sudo mv -v Video_Codec_SDK_13.0.19 /opt/
```

### Step 3: Verify CUDA Headers

Ensure CUDA Toolkit is installed and include path exists:

```
ls /usr/local/cuda/include
```

(If not found, install CUDA Toolkit first; see CUDA section above.)

### Step 4: Copy SDK Headers to CUDA Include Path

```
cd /opt/Video_Codec_SDK_13.0.19/Interface
```

```
sudo cp -v *.h /usr/local/cuda/include/
```

Enables FFmpeg or other tools to compile with NVENC/NVDEC support.

### Final Verifications

Check NVENC support:

```
ffmpeg -hide_banner -hwaccels
```

Check NVIDIA driver + GPU health:

```
nvidia-smi
```

## Useful Tools and System Setup for Linux

### Install System Utilities

Install commonly used tools, libraries, fonts, network utilities, development packages, and penetration testing tools:

```
sudo apt install -y \
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
mediainfo alacarte
```

### Google Chrome

Install the stable version:

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

```
sudo apt install ./google-chrome-stable_current_amd64.deb
```

Optionally, install all Chrome variants:

```
sudo apt install google-chrome-beta google-chrome-unstable google-chrome-stable
```

Remove beta and unstable repo entries:

```
sudo rm -vf /etc/apt/sources.list.d/google-chrome-beta.list
```

```
sudo rm -vf /etc/apt/sources.list.d/google-chrome-unstable.list
```

```
sudo apt update
```

### Sublime Text

Visit: sublimetext.com

```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg > /dev/null
```

```
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
```

```
sudo apt update
```

```
sudo apt install sublime-text
```

### Slack

```
wget https://downloads.slack-edge.com/linux_releases/slack-desktop-4.33.90-amd64.deb
```

```
sudo apt install ./slack-desktop-4.33.90-amd64.deb
```

If dependencies are missing:

```
wget http://ftp.us.debian.org/debian/pool/main/libi/libindicator/libindicator3-7_0.5.0-4_amd64.deb
```

```
wget http://ftp.us.debian.org/debian/pool/main/liba/libappindicator/libappindicator3-1_0.4.92-7_amd64.deb
```

```
sudo dpkg -i libindicator3-7_0.5.0-4_amd64.deb
```

```
sudo dpkg -i libappindicator3-1_0.4.92-7_amd64.deb
```

```
sudo apt install -f
```

### VirtualBox

```
sudo apt install virtualbox virtualbox-ext-pack virtualbox-guest-additions-iso
```

### OpenVPN

```
sudo apt install openvpn network-manager-openvpn network-manager-openvpn-gnome
```

### Flameshot

Install:

```
sudo apt install flameshot
```

Run:

```
/usr/bin/flameshot gui
```

Set up Flameshot to use PrintScreen key:

- Open Settings > Devices > Keyboard > Shortcuts.
- Search "print", click it, press Backspace to unbind.
- Click "+" to add a new shortcut:
  - Name: Flameshot
  - Command: /usr/bin/flameshot gui
  - Set shortcut: Press PrtSc key.

Example config (in ~/.config/flameshot/flameshot.ini):

```
[General]
checkForUpdates=true
contrastOpacity=188
filenamePattern=file_%Y-%m-%d_%H-%M-%S
saveAfterCopy=true
savePathFixed=true
showStartupLaunchMessage=true
squareMagnifier=false
uploadHistoryMax=25
```

### Visual Studio Code

Install via .deb from the official website:

```
wget "https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64" -O vscode.deb
```

```
sudo apt install ./vscode.deb
```

### Youtube-DL

```
sudo apt install youtube-dl
```

### Remmina

```
sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret
```

### Testssl.sh and Dirsearch

```
git clone https://github.com/drwetter/testssl.sh
```

```
git clone https://github.com/maurosoria/dirsearch.git
```

### wkhtmltopdf

```
wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.buster_amd64.deb
```

```
sudo apt install ./wkhtmltox_0.12.6-1.buster_amd64.deb
```

### Geckodriver (For Selenium)

```
wget https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-linux64.tar.gz
```

```
tar -xvzf geckodriver-v0.34.0-linux64.tar.gz
```

```
sudo mv geckodriver /usr/local/bin/
```

### Tesseract OCR

```
sudo apt install tesseract-ocr gimagereader libtesseract-dev
```

### Mirror & Control Android Phone

Use tools like:

- scrcpy: USB-based screen mirroring
- sndcpy: For audio
- KDE Connect: Wireless integration

## Go (Golang) Installation Guide for Linux

This guide covers:

- Installing a specific version of Go (Golang)
- Configuring your environment
- Installing Go-based tools for Offensive Security

### Check Existing Go Installation

```
go version
```

(If installed, it returns the version (e.g., go version go1.20.4 linux/amd64). If not, you'll get an error.)

### Download Go

Official Download Page: go.dev/dl

Direct download (example for Go 1.24.5):

```
wget https://go.dev/dl/go1.24.5.linux-amd64.tar.gz
```

Update the version URL based on your preferred Go release.

### Remove Existing Go Installation

To avoid version conflicts:

```
sudo apt remove golang-go
```

### Remove Old Go Directory (if exists)

Check if the Go directory is present:

```
ls /usr/local/go
```

If it exists, remove it and extract the new tarball:

```
sudo rm -rf /usr/local/go
```

```
sudo tar -C /usr/local -xzf go1.24.5.linux-amd64.tar.gz
```

Verify:

```
ls /usr/local/go
```

### Confirm Go Installation

```
/usr/local/go/bin/go version
```

### Set Environment Variables

Detect your shell:

```
echo $SHELL
```

#### For Zsh (~/.zshrc)

```
echo "export GOROOT=/usr/local/go" >> ~/.zshrc
```

```
echo "export GOPATH=\$HOME/go" >> ~/.zshrc
```

```
echo "export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin" >> ~/.zshrc
```

```
source ~/.zshrc
```

#### For Bash (~/.bashrc)

```
echo "export GOROOT=/usr/local/go" >> ~/.bashrc
```

```
echo "export GOPATH=\$HOME/go" >> ~/.bashrc
```

```
echo "export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin" >> ~/.bashrc
```

```
source ~/.bashrc
```

### Verify Go Installation

```
go version
```

You should see the version installed (e.g., go version go1.24.5 linux/amd64)

## Installing Go Tools for Offensive Security

Install popular Go-based pentesting tools using a script from InfoSecWarrior.

### Become Root

```
sudo su -
```

### Download the Installation Script

Navigate to /opt:

```
cd /opt
```

Download the script:

```
wget https://raw.githubusercontent.com/InfoSecWarrior/Offensive-Pentesting-Scripts/main/Gotools-Install/gotools-install.sh
```

Make it executable:

```
chmod +x gotools-install.sh
```

### Run the Script

```
./gotools-install.sh
```

This script installs commonly used Go-based security tools, such as:

- httpx
- subfinder
- naabu
- amass
- dnsx
- and more...

### Final Check

```
which go
```

```
go version
```

```
which httpx
```

## 🐍 Python Installation and Environment Setup

This guide covers:

- Installing Python 2.7 and Python 3.x
- Setting up pip for both versions
- Installing BeautifulSoup4
- Creating an isolated Python environment using venv

### ✅ Checking Existing Python & Pip Versions

```
python -V
```

```
python2.7 -V
```

```
pip -V
```

```
pip2.7 -V
```

### 🌿 Installing BeautifulSoup4

```
pip install beautifulsoup4
```

```
pip2.7 install beautifulsoup4
```

### 📦 Installing pip for Python 2.7

If pip2.7 is not available:

Download the installer:

```
wget https://bootstrap.pypa.io/pip/2.7/get-pip.py -O get-pip.py
```

Run the installer:

```
python2.7 get-pip.py
```

Verify pip:

```
pip2.7 -V
```

Test installation:

```
pip2.7 install beautifulsoup4
```

### 🐍 Installing pip for Default Python (Python 3.x)

If pip is not available for Python 3:

```
wget https://bootstrap.pypa.io/pip/get-pip.py -O get-pip.py
```

```
python get-pip.py
```

### 🧱 Installing Python 3 Full Package and venv

```
sudo apt install python3.13-venv
```

```
sudo apt install python3-full python-is-python3
```

### 🏗️ Creating a Virtual Environment

Make a directory for the environment:

```
mkdir /opt/python-environment
```

Create the virtual environment:

```
python3 -m venv /opt/python-environment
```

### 📥 Installing pip in the Virtual Environment

If pip is missing in the virtual environment:

Download get-pip:

```
wget https://bootstrap.pypa.io/pip/get-pip.py -O get-pip.py
```

Run the installer using the virtual environment’s Python:

```
/opt/python-environment/bin/python get-pip.py
```

Check pip version:

```
/opt/python-environment/bin/pip -V
```

### 🔄 Setting System-wide pip to Virtual Environment

Check existing pip path:

```
which pip
```

Remove current symlink if needed:

```
ls -lh /usr/local/bin/pip
```

```
sudo rm -f /usr/local/bin/pip
```

Create a new symlink:

```
sudo ln -s /opt/python-environment/bin/pip /usr/local/bin/pip
```

Confirm:

```
pip -V
```

Install globally using this pip:

```
pip install beautifulsoup4
```

### 🔎 Version Check Summary

```
pip -V
```

Output: pip 25.1.1 from /opt/python-environment/lib/python3.13/site-packages/pip (python 3.13)

```
pip2.7 -V
```

Output: pip 20.3.4 from /usr/local/lib/python2.7/dist-packages/pip (python 2.7)

```
python -V
```

Output: Python 3.13.5

```
python2.7 -V
```

Output: Python 2.7.18

### 🧬 Making the Virtual Environment Globally Accessible

Add virtual environment path to your shell config:

#### For Zsh users

```
echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.zshrc
```

```
source ~/.zshrc
```

#### For Bash users

```
echo "export PATH=\$PATH:/opt/python-environment/bin" >> ~/.bashrc
```

```
source ~/.bashrc
```

## ZSH Shell Installation and Configuration

### Step 1: Install ZSH

```
sudo apt install zsh
```

### Step 2: Download .zshrc Configuration File

```
cd ~
```

```
wget https://raw.githubusercontent.com/nikhilpatidar01/Ethical-Hacking/Master/3.%20Kali%20Linux/.zshrc
```

Check downloaded .zshrc:

```
ls -la ~ | grep zshrc
```

Remove .zshrc if needed:

```
rm -f ~/.zshrc
```

### Step 3: Set ZSH as Default Shell

```
chsh -s $(which zsh)
```

### Step 4: Apply Config Without Restart

```
source ~/.zshrc
```

## 🖥️ What is linux-desktop-shortcuts?

- Linux: Related to Linux systems.
- Desktop: .desktop files are used by Linux desktop environments (GNOME, KDE, XFCE, etc.) to integrate apps into the application menu, dock, or taskbar.
- Shortcuts: .desktop files act like shortcuts/launchers for applications (similar to .lnk files in Windows).

## VirtualBox Launcher Setup

Edit the file:

```
sudo vim /usr/share/applications/virtualbox.desktop
```



