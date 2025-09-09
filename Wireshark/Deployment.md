# Wireshark Deployment

---

# Install and Run Wireshark (Local System)

## Prerequisites

* Linux system (Ubuntu/Debian recommended, but works on Windows/macOS too)
* Root/sudo access

---

## 1. Install Wireshark

On **Ubuntu/Debian**:

```bash
sudo apt update
sudo apt install wireshark -y
```

During installation, it may ask:
*“Should non-superusers be able to capture packets?”*

* If you select **Yes**, you can add your user to the `wireshark` group to capture without sudo.
* If **No**, you will need `sudo` to capture traffic.

On **CentOS/RHEL**:

```bash
sudo yum install wireshark-gtk -y
```

On **macOS (Homebrew)**:

```bash
brew install --cask wireshark
```

On **Windows**:

* Download from [https://www.wireshark.org/download.html](https://www.wireshark.org/download.html) and install.

---

## 2. Add User to Wireshark Group (Linux only)

```bash
sudo usermod -aG wireshark $USER
```

Log out and log back in for changes to take effect.

---

## 3. Run Wireshark

Start the graphical interface:

```bash
wireshark
```

For command-line mode (tshark):

```bash
tshark -i eth0
```

---

## 4. Capture Traffic

* Select your network interface (e.g., `eth0` or `wlan0`).
* Click **Start Capture**.
* Stop when finished and analyze packets.

---

## 5. Save and Analyze

* Save captured traffic as a `.pcap` file.
* You can analyze `.pcap` files later with Wireshark or other tools (like Suricata or Snort).

---

## 6. Logs and Filters

* Use display filters, for example:

  * `http` → show only HTTP traffic
  * `ip.addr == 192.168.1.10` → filter traffic from/to an IP
  * `tcp.port == 80` → filter TCP traffic on port 80

---

Now you have Wireshark installed and ready for packet capture and analysis.

---

