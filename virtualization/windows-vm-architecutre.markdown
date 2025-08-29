# Windows VM Architecture on Ubuntu Host

This document describes the architecture of a Windows virtual machine (VM) running on an Ubuntu host.

## Core Components

* **Host OS (Ubuntu):** The base system managing the physical hardware.
* **Guest OS (Windows):** The virtualized system running inside the VM.
* **Hypervisor:** The software that creates the virtual environment. **KVM**, **VirtualBox**, or **VMware** are common examples.

## How it Works

1.  The **Hypervisor** creates virtual hardware (CPU, RAM, storage) for the Windows guest.
2.  Windows runs using this virtual hardware as if it were real.
3.  Any requests from Windows (e.g., for disk access) are translated by the hypervisor into commands for the Ubuntu host.
4.  Ubuntu then executes these commands on the physical hardware.

<img width="865" height="598" alt="image" src="https://github.com/user-attachments/assets/d3a283d7-ca38-4f6e-ac65-ebd931aba9af" />
