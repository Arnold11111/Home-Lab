# Suricata Deployment

---

# Install and Run Suricata (Local System)

## Prerequisites

* Linux system (Ubuntu/Debian recommended)
* Root/sudo access
* Internet connection

---

## 1. Install Suricata

On **Ubuntu/Debian**:

```bash
sudo apt update
sudo apt install suricata -y
```

On **CentOS/RHEL**:

```bash
sudo yum install epel-release -y
sudo yum install suricata -y
```

---

## 2. Verify Installation

```bash
suricata --build-info
```

This should show Suricata version and compile info.

---

## 3. Configure Suricata

Main config file:

```
/etc/suricata/suricata.yaml
```

* Set the network interface to monitor, for example:

```yaml
af-packet:
  - interface: eth0
```

---

## 4. Update Rules

Install/update Emerging Threats ruleset:

```bash
sudo suricata-update
```

Rules are stored in:

```
/var/lib/suricata/rules/
```

---

## 5. Run Suricata

Run Suricata in IDS mode on interface `eth0`:

```bash
sudo suricata -c /etc/suricata/suricata.yaml -i eth0
```

---

## 6. Check Logs

Suricata logs are stored in:

```
/var/log/suricata/
```

Quick check:

```bash
tail -f /var/log/suricata/fast.log
```

---

✅ Now you have Suricata running locally.

---

👉 Do you want me to continue with **Snort installation (local system)** next?
