# Initial Setup: OS, NVMe, and Firewall

## 1. Operating System Choice

My initial idea was to install Debian since it's the server standard and the base for distros like Kali, Ubuntu, etc. However, after looking into the specifics of the Raspberry Pi 5, I decided to go with Raspberry Pi OS (based on Debian 13). 
The main reason is hardware compatibility. It ensures that the Active Cooler and the PCIe bus work without any weird workarounds. This way, I keep the same apt ecosystem and Debian stability but with drivers optimized for aarch64.

<img width="430" height="210" alt="image" src="https://github.com/user-attachments/assets/fe530458-24af-4f5f-a4d2-387d847aa218" />

## 2. Storage: The Jump to NVMe

Booting a Raspberry Pi from a MicroSD card for a hacking lab is a huge bottleneck. Massive read/write operations are slow, and heavy log usage ends up corrupting the cards.
The solution was to install a PCIe HAT and migrate the system to a 500GB Crucial P3 Plus NVMe SSD. This gives me real read/write speeds and lets me better utilize the board's 16GB of RAM.

<img width="475" height="137" alt="image" src="https://github.com/user-attachments/assets/dcd952ef-32df-4986-845e-8aa664195c5a" />

## 3. Baseline Security: Firewall (UFW)
Before exposing the machine or spinning up services, I configured UFW (Uncomplicated Firewall) to secure the server. 
The policy is to deny all incoming traffic by default and only open SSH for remote administration.

<img width="577" height="202" alt="image" src="https://github.com/user-attachments/assets/13e12783-033e-4df4-bd15-62cdc45d493c" />
