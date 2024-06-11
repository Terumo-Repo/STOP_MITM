## MITM_Stop

## What is this?
This little program is NOT a 100% foolproof plan to stop attackers! 
The goal is to be a free, easy to setup, multi-platform (Linux, Windows and MacOS) tool to stop MITM attacks, that is used to prevent, detect, and warn when some forms of attacks occur, such as:
- Rogue AP
- Evil Twin
- DNS poisoning
- ARP poisoning
- Rogue DHCP Servers
While no solution is entirely secure, this program helps minimize the risk of these attacks.


## Why a ".txt" file?
MITM_Stop is provided as a ".txt" file and not as an ".exe" to be readable and editable by anyone! It is also not provided as a ".bat" file because most antivirus programs distrust ".bat" files. This way, the script is both trustworthy (you can read the full code and verify it has no hidden functions) and easily editable on any computer.
When finished configuring, you can change the file extension from ".txt" to ".bat" (for Windows) or ".sh" (for macOS/Linux) and run it when needed.
This also allows more portability and enables the user to have separate MITM_Stop scripts for each network (e.g., one for work, one for home) by copying and editing the configuration.


## Why this method?
MITM attacks are hard to detect and prevent. Most attacks are successful because the user is not aware of the attacker.
This script allows you to run it only when needed to ensure more secure browsing (e.g., when requiring passwords or accessing sensitive files) and close it when not needed. This approach avoids the continuous monitoring by a background program, which consumes memory.


## How to configure it?
You can edit your MITM_Stop.txt file with notepad (or any text editor), filling in the blank spaces with your gateway IP, DNS IP, MAC address of your router and network name. This should always be "human-based" to guarantee the security of human verification (e.g., check the tag on the back of the router for the MAC address).

## Commands in Windows to get necessary information:
- Gateway IP: 	ipconfig | findstr /i "Default Gateway"
- DNS IP: 	nslookup google.com | findstr /i "Server"
- Gateway MAC:	arp -a | findstr /i "[gateway IP]"  
- SSID:		netsh wlan show interfaces | findstr /i "SSID"
- BSSID:	netsh wlan show interfaces | findstr /i "BSSID"

## Commands in Linux to get necessary information:
- Gateway IP: 	ip route | grep default
- DNS IP: 	grep "nameserver" /etc/resolv.conf
- Gateway MAC:	arp -n | grep "[gateway IP]"
- SSID: 	iwgetid -r

## Commands in MacOS to get necessary information:
- Gateway IP: 	netstat -nr | grep default
- DNS IP:	scutil --dns | grep 'nameserver\[[0-9]*\]' | awk '{print $3}
- Gateway MAC: 	arp -an | grep "[gateway IP]"
- SSID:		/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -I | grep SSID | awk '{print $2}'
- BSSID:	/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -I | grep BSSID | awk '{print $2}'


## Example configuration
router_ip="192.168.1.1"
dns_ip="8.8.8.8"
router_MAC="00:11:22:33:44:55"
expected_ssid="MyNetwork"

## If You wish to report issues, contribute improvements, or/and ask questions, please feel free to contact me at Github (https://github.com/Terumo-Repo) or by e-mail (telmoabc@gmail.com).

## License
This project is licensed under the GNU General Public License v3.0 - Please see the LICENSE.txt file for details.
