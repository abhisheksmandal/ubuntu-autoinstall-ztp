# 🚀 Ubuntu AutoInstall ZTP (Zero-Touch Provisioning)

This repository provides a **fully automated Ubuntu installation** using `autoinstall.yaml`.  
It is designed for **Zero-Touch Provisioning (ZTP)**, enabling **completely unattended installations** with **automatic disk setup, network configuration, SSH installation, and essential package installation**.

---

## 🎯 Features

✅ **Fully automated installation** (No manual input required)  
✅ **Uses entire disk with LVM** (Wipes all existing data)  
✅ **Preserves network settings** (Uses network configured at boot)  
✅ **Installs essential packages** (SSH, curl, git, htop, vim, GNOME)  
✅ **Enables SSH for remote access** (Password authentication supported)  
✅ **Auto-updates system after installation**

---

## 📜 Usage Instructions

### **1️⃣ Clone the Repository**

```bash
git clone https://github.com/abhisheksmandal/ubuntu-autoinstall-ztp.git
cd ubuntu-autoinstall-ztp
```

### **2️⃣ Modify Password (Optional)**

The `autoinstall.yaml` file requires a **hashed password**. Generate one using:

```bash
mkpasswd -m sha-512
```

Replace the password in `autoinstall.yaml`:

```yaml
identity:
  username: youruser
  password: "$6$randomsalt$hashedpassword"
```

### **3️⃣ Copy the YAML to the Installer**

1. Boot Ubuntu **Live USB** and enter "Try Ubuntu" mode.
2. Copy `autoinstall.yaml` to the installer:

```bash
sudo cp autoinstall.yaml /var/lib/curtin/
sudo curtin install
```

### **4️⃣ Start the Automated Installation**

- If using an ISO with **autoinstall support**, add `autoinstall` to the boot parameters.
- The system will **automatically install Ubuntu** using the YAML configuration.

---

## 🔧 Customization

### **Edit Installed Packages**

Modify the list in `autoinstall.yaml` under `packages`:

```yaml
packages:
  - openssh-server
  - curl
  - git
  - htop
  - vim
  - gnome-shell
  - gnome-terminal
```

### **Change Timezone & Locale**

```yaml
timezone: Asia/Kolkata
locale: en_US.UTF-8
keyboard:
  layout: us
```

### **Modify Storage Layout**

By default, it uses **LVM and wipes all disks**:

```yaml
storage:
  wipe: true
  layout:
    name: lvm
```

You can change this to **manual partitioning** if needed.

## 🚀 Future Improvements

- Add **Cloud-Init support** for cloud deployments.
- Provide **custom partitioning options**.
- Automate **post-installation scripts**.

---

💡 **Contributions are welcome!** If you find this useful, give it a ⭐ on GitHub! 🚀
