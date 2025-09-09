# Snort Deployment

---

# Install and Run Snort (Local System)

## Prerequisites

* Linux system (Ubuntu/Debian recommended)
* Root/sudo access
* Network interface to monitor (e.g., `eth0`)

---

## 1. Install Snort

On **Ubuntu/Debian**:

```bash
sudo apt update
sudo apt install snort -y
```

On **CentOS/RHEL**:

```bash
sudo yum install epel-release -y
sudo yum install snort -y
```

During installation on Ubuntu, it may ask for your network interface (e.g., `eth0`).

---

## 2. Verify Installation

```bash
snort -V
```

This should display the installed version.

---

## 3. Configure Snort

Main config file:

```
/etc/snort/snort.conf
```

Inside, you can:

* Set **HOME\_NET** (your local network, e.g., `192.168.1.0/24`)
* Add or modify rule paths

---

## 4. Snort Rules

Default rules are usually in:

```
/etc/snort/rules/
```

You can also download community rules:

```bash
wget https://www.snort.org/downloads/community/snort3-community-rules.tar.gz
tar -xvzf snort3-community-rules.tar.gz
sudo mv snort3-community-rules/* /etc/snort/rules/
```

---

## 5. Run Snort

Run in **IDS mode** (live traffic on `eth0`):

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

Explanation:

* `-A console` → print alerts to terminal
* `-q` → quiet mode (suppresses extra info)
* `-c` → specify config file
* `-i` → interface to listen on

---

## 6. Check Logs

Snort logs alerts in:

```
/var/log/snort/
```

You can tail logs:

```bash
tail -f /var/log/snort/alert
```

---

✅ Now you have **Snort running locally** in IDS mode.

---
