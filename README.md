# 🛡️ NETWORKWALKS-WK1-CYBERSECURITY-LAB-SETUP

**Author:** Shahzeb Ali  
**Internship Program:** NETWORKWALKS Cybersecurity Internship  
**Project:** Week 1 - Cybersecurity Lab Environment Setup  

---

## 📑 Project Overview
The objective of this project was to establish an isolated, secure, and fully functional virtual laboratory environment for practicing ethical hacking, authorized penetration testing, and security analysis. This controlled environment ensures that all subsequent internship tasks—such as reconnaissance, network scanning, and vulnerability assessments—can be conducted safely without impacting the host system.

## 🛠️ Tools & Technologies Used
* **Host Operating System:** macOS (Apple Silicon & Intel support)
* **Virtualization Platforms:** UTM (Primary for ARM64) & Oracle VM VirtualBox (Secondary for x86_64)
* **Guest Operating System:** Kali Linux (Rolling Release)
* **Command Line Interface (CLI):** Mac Terminal & Kali Terminal

---

## 🍎 Special Notes & Guidelines for macOS Users

Setting up a cybersecurity lab on macOS depends heavily on your processor architecture. I have provided two methods below so new users can easily go through these steps regardless of their hardware.
* **Apple Silicon (M1/M2/M3/M4):** Use **UTM** (Path A). Do not use the pre-built VirtualBox files.
* **Intel Macs:** Use **VirtualBox** (Path B).

---

## ⚙️ Path A: VM Provisioning via UTM (Apple Silicon / ARM64)
For newer Macs, UTM provides the best native virtualization experience. 

### 1. VM Creation & Architecture
* Launch UTM and select "Create a New Virtual Machine" from the welcome screen.
* Choose "Virtualize" to take advantage of faster, native CPU architecture.

<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 55 50" src="https://github.com/user-attachments/assets/cc87b24a-e2c7-4bb2-9691-2518764ffc7f" />
<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 56 00" src="https://github.com/user-attachments/assets/eb3aa807-22b4-410b-b4bb-411157215744" />


### 2. Operating System & ISO Selection
* Select "Linux" from the preconfigured operating system options.
* Under the Linux settings, choose "Boot from ISO image" and click "Browse..." to select your downloaded Kali Linux ARM64 ISO file.

<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 56 07" src="https://github.com/user-attachments/assets/ed9cec76-0939-422e-8d37-52d3546424b9" />

### 3. Hardware & Storage Allocation
* Allocate **4096 MiB (~4GB)** of Memory to ensure smooth operation.
* Specify the storage size for the virtual drive (shown as **64 GiB** in the example). 
  * *Note:* You do not have to strictly use 64 GB. You can allocate as much space as you want, but ensure you provide **at least 20 GB** so the OS has enough room for the initial installation and future tools. You can always change the storage size later if needed.
* Review the configuration on the Summary page, name the VM "Kali Linux", and click Save.

<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 56 14" src="https://github.com/user-attachments/assets/ae6a0b7c-5326-4376-951a-917aa11886a6" />
<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 56 43" src="https://github.com/user-attachments/assets/9cb55872-7dcf-4173-8c12-80f6d044d0be" />
<img width="1012" height="985" alt="Screenshot 2026-10-28 at 09 57 11" src="https://github.com/user-attachments/assets/980fc7dd-5860-4cea-8589-baa95d29d3de" />

### 4. Advanced Display & Serial Configuration
Before booting, adjust the VM settings to ensure GUI and terminal stability:
* Navigate to the **Display** settings and ensure the Emulated Display Card is set to `virtio-gpu-pci`.
* Navigate to the **Serial** settings and ensure the Connection Mode is set to `Built-in Terminal`.

<img width="1337" height="985" alt="Screenshot 2026-10-28 at 09 58 25" src="https://github.com/user-attachments/assets/64df5263-1c46-4210-bb53-e89b4bc10f13" />

---

## ⚙️ Path B: VM Provisioning via VirtualBox (Intel / AMD64)
For older Macs, VirtualBox remains a reliable Type-2 hypervisor.

### 1. Hardware & Network Setup
* **Base Memory:** Allocate ~4GB (4089 MB) to balance host and guest performance.
* **Network (NAT):** Enable Network Adapter 1 and attach it to **NAT** to provide the VM with external internet access while keeping it isolated from the local host network.
* **Features:** Enable bidirectional Shared Clipboard and Drag-and-Drop functionality.

<img width="1061" height="684" alt="Screenshot 2026-10-27 at 11 44 18" src="https://github.com/user-attachments/assets/df790689-f23b-4838-8d10-ecd013455521" />

<img width="1583" height="1050" alt="Screenshot 2026-10-28 at 09 52 18" src="https://github.com/user-attachments/assets/4b11c838-4a25-43fd-9b42-f686b4533491" />


---

## 🐧 Kali Linux OS Installation (Both Paths)
Once the VM is provisioned via either UTM or VirtualBox, start the machine to begin the OS installation.
* Successfully boot the Kali Linux installer and execute the initial software selection and system unpacking phase.

<img width="1950" height="1080" alt="Screenshot 2026-10-27 at 10 34 39" src="https://github.com/user-attachments/assets/16bd8231-3be6-45c1-8bd6-b506d6d7ded6" />

---

## 💻 System Initialization & Package Updates
After the OS is installed, the system repository packages must be secured and updated via the terminal.

* **Initial CLI Access:** Launched the terminal under the user `shahzeb`.
<img width="1661" height="1095" alt="Screenshot 2026-10-27 at 10 44 29" src="https://github.com/user-attachments/assets/f52be434-9843-4f11-a93a-f0c11931b539" />

* **Updating Package Lists:** 
Ran `sudo apt update` to fetch the latest version details of available packages from the Kali repositories. 
<img width="1727" height="1161" alt="Screenshot 2026-10-27 at 10 45 05" src="https://github.com/user-attachments/assets/0c979eed-9c75-41d4-8b15-fc1dd712f695" />

* **Full System Upgrade:** 
Executed `sudo apt full-upgrade -y` to download and install all system updates and dependencies, ensuring the penetration testing tools are up-to-date and secure.
<img width="1727" height="1161" alt="Screenshot 2026-10-27 at 10 45 05" src="https://github.com/user-attachments/assets/31b548be-e4b7-4169-a60b-40e5fc7afb7a" />

---

## 💡 Key Learnings & Outcomes
1. **Multi-Platform Virtualization:** Gained practical experience in deploying VMs using both UTM (for ARM64) and VirtualBox (for x86_64) on macOS.
2. **Hardware Configuration:** Learned to properly allocate memory, storage, display drivers (`virtio-gpu-pci`), and serial interfaces for optimized VM performance.
3. **Network Isolation:** Understood the importance of NAT networks in creating a safe sandbox for cybersecurity testing.
4. **Linux Command Line Operations:** Successfully navigated the Debian-based package management system to provision and update the operating system securely.

**Acknowledgments:** Special thanks to Waqas Karim (CCIE) and the NETWORKWALKS team for the guidance throughout Week 1!
