# 🖧 DHCP Server Practice

**Authors:** Álvaro Mateos Gálvez & Raúl Ibáñez Sola  
**Date:** October 2025  
**System:** Debian + Vagrant  

---

## 📘 Project Overview
This project demonstrates how to configure a **DHCP server** on Debian using **Vagrant** and **VirtualBox**.

- `c1` → Dynamic IP  
- `c2` → Fixed IP based on MAC address  

**Objective:**  
- Learn DHCP server setup on Linux  
- Configure dynamic and fixed IP assignment  
- Test automatic IP allocation in an isolated virtual network

---

## What is DHCP?
DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses to devices in a network, avoiding manual configuration.

**Basic DHCP steps:**  
1. Client sends `DHCPDISCOVER`  
2. Server responds with `DHCPOFFER`  
3. Client requests IP with `DHCPREQUEST`  
4. Server confirms with `DHCPACK`

---

## ⚙️ Estructura de red

| Máquina | Función | Red interna | Dirección IP |
|----------|----------|-------------|---------------|
| `server` | Servidor DHCP | `192.168.57.0/24` | `192.168.57.10` |
| `c1` | Cliente DHCP dinámico | `192.168.57.0/24` | Rango `192.168.57.25-50` |
| `c2` | Cliente DHCP con IP fija | `192.168.57.0/24` | `192.168.57.4` |

---

## 🧪 Useful Commands

| Action | Command |
|--------|----------|
| Verify DHCP configuration syntax | `sudo dhcpd -t` |
| Restart the service | `sudo systemctl restart isc-dhcp-server` |
| Check service status | `sudo systemctl status isc-dhcp-server` |
| View logs | `sudo journalctl -u isc-dhcp-server` |
| View active leases | `cat /var/lib/dhcp/dhcpd.leases` |
| Release IP (client) | `sudo dhclient -r` |
| Renew IP (client) | `sudo dhclient -v` |

---

## Setup & Run
1. Create a project folder & `Vagrantfile` for 3 VMs:  
   - `server` → DHCP server  
   - `c1` → Client with dynamic IP  
   - `c2` → Client with fixed IP  

2. Start the VMs:

```bash
vagrant up
vagrant status


