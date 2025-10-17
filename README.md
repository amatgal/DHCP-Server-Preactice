DHCP Server Practice

Authors: Álvaro Mateos Gálvez & Raúl Ibáñez Sola
Date: October 2025
System: Debian + Vagrant

🔹 Project Overview

Set up a DHCP server on Debian using Vagrant and VirtualBox.

c1 → Dynamic IP

c2 → Fixed IP based on MAC address

⚡ Setup & Run

Create project folder & Vagrantfile for 3 VMs: server, c1, c2

Start VMs:

vagrant up
vagrant status

🖥️ Server Config

SSH into server:

vagrant ssh server


Install DHCP:

sudo apt update
sudo apt install isc-dhcp-server -y


Select interface (eth2) in /etc/default/isc-dhcp-server

Configure /etc/dhcp/dhcpd.conf:

IP range, gateway, DNS, domain

Restart service:

sudo systemctl restart isc-dhcp-server

💻 Client Config

Request IP on c1 and c2:

sudo dhclient -v
ip a

📌 Fixed IP for c2

Get MAC address:

ip link show


Add host in DHCP config with MAC & fixed IP

Restart server & renew IP on c2:

sudo dhclient -r
sudo dhclient -v

📊 Logs & Leases

View logs:

sudo journalctl -u isc-dhcp-server


Check leases:

cat /var/lib/dhcp/dhcpd.leases

✅ Conclusion

DHCP works for dynamic and fixed IPs

Safe testing in a virtual network

Fixed IP ensures consistent device addressing

🔧 Quick Commands
ip a                   # Check interfaces
sudo nano [file]        # Edit files
sudo dhcpd -t           # Validate DHCP config
sudo systemctl restart isc-dhcp-server
sudo journalctl -u isc-dhcp-server
cat /var/lib/dhcp/dhcpd.leases
sudo dhclient -r        # Release IP
sudo dhclient -v        # Renew IP
