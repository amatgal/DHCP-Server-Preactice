# 🖧 DHCP Practice A – Vagrant + Debian

**Author:** *Álvaro Mateos Gálvez & Raúl Ibáñez Sola*  
**Subject:** Network Services and Internet 

---

## 📘 Project Description

This project aims to configure a **DHCP server on Debian** using **Vagrant** for virtualization.  
The setup includes three virtual machines:

- **server** → Debian DHCP server  
- **c1** → DHCP client (dynamic IP)  
- **c2** → DHCP client with a fixed IP based on its MAC address  

The DHCP server automatically provides network configurations to the clients within the internal network `192.168.57.0/24`.

---

## ⚙️ Network Structure

| Machine | Role | Network | IP Address |
|----------|------|----------|-------------|
| `server` | DHCP Server | `192.168.57.0/24` | `192.168.57.10` |
| `c1` | DHCP Client (dynamic) | `192.168.57.0/24` | Range `192.168.57.25–50` |
| `c2` | DHCP Client (fixed) | `192.168.57.0/24` | `192.168.57.4` |

The server also has a second interface (`192.168.56.10`) connected to the host machine for Internet access and package downloads.

---

