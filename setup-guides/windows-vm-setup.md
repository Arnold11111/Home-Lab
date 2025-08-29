# 🖥️ Windows VM Setup in VirtualBox (Complete Steps 1–7)

## 📌 Objective
Create a Windows Virtual Machine in VirtualBox for use in a cybersecurity home lab (SOC monitoring, malware analysis, or attack simulations).

---

## ⚙️ Requirements
- **Host OS:** Ubuntu / Windows / MacOS  
- **Virtualization Software:** VirtualBox  
- **Windows ISO:** Download from Microsoft  
- **System Resources:**  
  - Minimum: 2 CPU cores, 4 GB RAM, 40 GB Disk  
  - Recommended: 4 CPU cores, 8 GB RAM, 60+ GB Disk  

---

## 🚀 Steps

### 1. Install VirtualBox
**Ubuntu**:
```bash
sudo apt update
sudo apt install virtualbox -y
```

**Windows/Mac**:  
Download from [VirtualBox Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### 2. Create a New Virtual Machine
1. Open **VirtualBox** → Click **New**  
2. Name: `Windows-10-Lab`  
3. Type: `Microsoft Windows`  
4. Version: `Windows 10 (64-bit)`

---

### 3. Allocate Resources
- **Memory (RAM):** 4096 MB+  
- **CPU:** 2+ cores  
- **Disk:** Create a new virtual disk (VDI), dynamically allocated, 40–60 GB  

---

### 4. Mount Windows ISO
1. Settings → Storage  
2. Under *Controller: IDE* → Click **Empty**  
3. Select **Windows ISO**  

---

### 5. Network Configuration
- **NAT** → Default, gives VM internet access  
- **Bridged Adapter** → VM acts like a LAN device (useful for lab scenarios)  

---

### 6. Start VM & Install Windows
1. Boot VM → Windows installer starts  
2. Follow instructions, enter product key (or skip for evaluation)  
3. Complete installation  

---

### 7. Post-Installation
- Install **Guest Additions** → Devices → Insert Guest Additions CD  
- Enable **Clipboard Sharing** & **Drag-and-Drop** (optional)  
- Take a **snapshot** for a clean state backup  

---

## ✅ Verification
- VM boots into Windows desktop  
- Internet access works  
- Clipboard/file sharing functional (if enabled)  

---

## 🔗 References
- [VirtualBox Official Docs](https://www.virtualbox.org/manual/UserManual.html)  
- [Microsoft Windows ISO Download](https://www.microsoft.com/software-download/)
