# Arch Linux: Network Setup

Run these commands immediately after the `root@archiso~#` prompt appears.

## Option A: USB Tethering / Ethernet

For most wired connections, the setup is automatic. Simply verify the connection:

```bash
ping -c 3 google.com
```

## Option B: Wi-Fi (One-Liner)

If you are using Wi-Fi, use this direct command to skip the interactive menu:

### Identify your interface name:

```bash
device list
```

_(Usually `wlan0`)_

### Connect to the network:

```bash
iwctl --passphrase "PASSWORD" station wlan0 connect SSID
```

### Verify:

```bash
ping -c 3 google.com
```

## Start Installation

Once the ping is successful, launch the installer:

```bash
archinstall
```

## Post-Installation

After `archinstall` completes successfully:

### 1. Reboot the System

```bash
reboot
```

### 2. Log in to TTY

After reboot, you'll be presented with a TTY login screen. Log in with the user credentials you created during installation.

### 3. Install Git

```bash
sudo pacman -S git
```

### 4. Install Yay (AUR Helper)

```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
cd ..
```

### 5. Install Google Chrome

```bash
yay -S google-chrome
```

### 6. Install Visual Studio Code

```bash
yay -S visual-studio-code-bin
```

### 7. Install Required Packages

```bash
sudo pacman -S polybar alacritty thunar flameshot dunst \
               network-manager-applet feh i3lock pulseaudio dmenu rofi
```

### 8. Clone This Repository

```bash
git clone https://github.com/mahdibm-dev/arch-bspwm.git
```

### 9. Copy Configuration Files

Create the config directory and copy the configuration files:

```bash
mkdir -p ~/.config
cp -r arch-bspwm/.config/* ~/.config/
```

### 10. Reboot System

Reboot to load the bspwm desktop environment:

```bash
reboot
```
