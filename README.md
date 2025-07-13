# Speeding-up-Kali-Linux
Speeding up Kali Linux can significantly improve your workflow, especially if you’re running it on a virtual machine or older hardware. Here's a **complete list of tips** to speed up Kali Linux:

---

## 🧹 1. **System Cleanup**

### 🔸 Remove Unused Packages:

```bash
sudo apt autoremove
sudo apt clean
```

### 🔸 Clear Thumbnail Cache:

```bash
rm -rf ~/.cache/thumbnails/*
```

---

## 🪄 2. **Disable Unnecessary Services**

List running services:

```bash
systemctl list-units --type=service --state=running
```

Disable unused services:

```bash
sudo systemctl disable bluetooth.service
sudo systemctl disable cups.service
```

---

## ⚙️ 3. **Use a Lightweight Desktop Environment**

Kali uses Xfce by default, which is lightweight. If you're using GNOME or KDE, consider switching:

```bash
sudo apt install xfce4
```

To set XFCE as default:

```bash
sudo update-alternatives --config x-session-manager
```

---

## 🧠 4. **Increase SWAP or Use ZRAM**

### 🔸 Create Swap File (if you don’t have one):

```bash
sudo fallocate -l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

### 🔸 Use ZRAM (better than swap):

```bash
sudo apt install zram-tools
sudo systemctl enable zram-config
```

---

## 🔥 5. **Reduce Startup Applications**

Edit autostart:

```bash
nano ~/.config/autostart/*.desktop
```

Or use:

```bash
sudo apt install gnome-session-properties
```

---

## 🚫 6. **Disable Animations**

If using XFCE:

```bash
xfce4-settings-manager → Window Manager Tweaks → Disable display compositing
```

Or edit `.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml` and set:

```xml
<property name="use_compositing" type="bool" value="false"/>
```

---

## 🧪 7. **Use Lighter Alternatives for Tools**

Examples:

* Replace **Wireshark** with **tshark**
* Replace **Metasploit GUI** with CLI use
* Use **Featherpad** instead of Gedit or Leafpad

---

## 🧼 8. **Optimize APT Sources**

Use a fast mirror:

```bash
sudo apt install netselect-apt
sudo netselect-apt kali
```

Or edit manually:

```bash
sudo nano /etc/apt/sources.list
```

And use:

```
deb http://http.kali.org/kali kali-rolling main non-free contrib
```

---

## 📦 9. **Use Lightweight File Managers**

Replace Thunar or Nautilus with **pcmanfm**:

```bash
sudo apt install pcmanfm
```

---

## 🪫 10. **Disable Snap and Flatpak (if unused)**

```bash
sudo apt purge snapd flatpak
```

---

## 🖥️ 11. **Optimize Virtual Machine (if used)**

If running in VMware or VirtualBox:

* Enable 3D acceleration
* Allocate more RAM & CPU cores
* Use **Guest Additions/VM Tools**
* Install host-specific drivers

---

## ⚡ 12. **Use Preload to Speed Up Application Launching**

```bash
sudo apt install preload
sudo systemctl enable preload
```

---

## 🧰 Optional Tools:

* **Stacer** – GUI system optimizer:

  ```bash
  sudo apt install stacer
  ```

* **BleachBit** – System cleaner:

  ```bash
  sudo apt install bleachbit
  ```

---

Would you like me to generate a script that automatically applies many of these optimizations?
