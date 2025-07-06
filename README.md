# sophos-xg-home-lab
Repurposing a Sophos XG 115 and AP 55C for home use with XG Home Edition, Ubuntu wipe workflow, and wireless integration.
# 🛡️ Sophos XG 115 Home Firewall Setup with AP 55C

A hands-on guide to repurposing a Sophos XG 115 appliance and AP 55C for home use using Sophos XG Home Edition. This project documents disk wiping, bootloader recovery, wireless integration, and network configuration — all done manually for full control and learning.

---

## 🧰 Hardware Used

| Device         | Purpose                                |
|----------------|----------------------------------------|
| Sophos XG 115  | Firewall appliance                     |
| AP 55C         | Wireless access point                  |
| Ubuntu Live USB| Used to wipe disk and reset bootloader |
| Sophos Home USB| Installer for XG Home Edition          |
| Ethernet Switch| LAN distribution                       |
| PC / Laptop    | Setup interface                        |

---

## 🎯 Project Goals

- Remove previous commercial license from XG 115
- Install Sophos XG Home Edition cleanly
- Configure LAN/WAN zones and DHCP
- Integrate legacy AP 55C for wireless access
- Document the process for portfolio and community use

---

## 🔨 Step-by-Step Setup 

### 1. Boot Ubuntu via GRUB (to install Linux temporarily)
Used manual GRUB commands to bypass EFI bootloader:
```bash
set root=(hd1,msdos1)
chainloader +1
boot
```

### 2. Wipe Internal Disk from Ubuntu
```bash
sudo wipefs -af /dev/sda
```

### 3. Reboot and Install Sophos XG Home
Created USB in DD mode using Rufus

Booted from USB and launched Sophos installer

No license conflict detected

Proceeded through guided Sophos Install

### 4. Initial Setup
Connected PC directly to Port 1 of the Sophos XG115

Accessed setup wizard at https://172.16.16.16:4444

Created admin password and registered Home license

### 5. Wireless Integration (AP 55C)
Setup Flow:
Connected AP directly to Port 1 in order to have the DHCP server assign the AP an IP

Once AP was initialized I registered AP via Sophos Central using the AP serial number

I was then able to connect the AP into my 5 Port POE switch

---

### Troubleshooting:
Factory reset AP (hold button 15–20 sec)

Verified DHCP lease in firewall console

Confirmed LAN zone and DHCP scope

Wireless tab appeared after successful handshake

---

### 🧠 Observations
Secure Boot did not need to be disabled

GRUB chainloading allowed Ubuntu install without BIOS changes

DD mode USB creation was essential for installer compatibility

Legacy APs like 55C may require use of Sophos Central to deploy
