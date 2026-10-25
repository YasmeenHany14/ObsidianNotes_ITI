## TCP/IP Architecture
* Merged layers which do the same jobs together (user side layers), which gave us 5 layers
* Application
* Transport
* Internet
* Data link
* Physical layer

## Protocols
### HTTP
* Hypertext transfer protocole
* Delivers web pages from server to client and vice versa
### URL 
* Consists of:
	Protocole:// Host:Port/Path

### FTP
* File transfer protocol
* port 21 for command and control, 20 for data transport (server side)
	Clients port number is randomly selected each operation
### SMTP
* Simple mail transfer protocol
* Responsible for sending mails over the network using mail clients, web or non web based
* User sender side
	Receiver uses POP3/IMAP
		Collect mails from mail servers
		Download msgs
		Work offline

### Telnet/SSH
* Secure s
* Used for accessing remote computers securely
* SSH is secure, telnet is not

## DNS
* Domain name servers
* Translate human readable names to IP addresses (domain names to numbers)
* A single domain can have many IPs if they have multiple servers, so we group them under one name
* Steps that browser takes to search for a name domain name:
	1. Check in browser cache
	2. Check in device cache
	3. Check in local DNS server
	4. Check in top level DNS server (google dns server for example)
	5. Go check in root DNS servers if all above failed

## NIC
* Operates in physical layer because => it's just hardware component that cant understand IP or MAC
	Mac address is burnet to it for other devices to read

## LAN Limitations
1. Segment Length
	Signals degrade with distance
* Problem solved with a repeater => repeats/regenerates signal over the same network to it's original strength
* Same as hub the only difference hub takes many devices 1 in many out , repeater only 1 in 1 out

### CSMA/CD
* Carrier sense multiple access / collision detection
* Stations listens for transmissions/traffic to determine when gaps between frame transmissions occurs
* Stations wait until they detect network is quite, to resend data again

#### CSMA/CA
* Avoids collisions by broadcasting a signal that a device is sending some data wait until the transimission ends before they try sending data


### Switch
* Difference between layer 3 switch and router
	1. Switch cannot allow different networks to communicate, only different nodes in the same network
	2. Can be used to determine best path for routing data without the need to overhead router each time for local networks,
	3. Used with VLAN


## Transmission media
### Wired
1. UTP
	Unshielded twisted pair
	Categorized into multiple categories => refer to slides
2. STP
	Shielded twisted pair
	Adding shield to reduce noise
3. Coaxial Cables
	TV Cables
4. Fiber Optic Cables
	Light pulses
	Inframagnitic waves doesnt affect it
	isn't affected by it's surroundings
	very fast (light speed)
	Not flexiable/bendable => breaks easily
	Fastest and the most expensive option
### Wireless
1. WIFI
2. Infra red
	Tv remote
3. Microwaves
	Tv signals / MAN Networks 
4. Bluetooth

#### Service Set Identifier (SSID)
* Used to distinguish between multiple wireless networks in the same vicinity
* SSID is configured on the access point and can be broadcasted or hidden

## Lab steps
1.  Configure pc, router, and server
2. Go to server services, ftp service and add a new user with needed permissions
3. Go to pc, cmd, write the command ftp 1.0.0.1 (server ip)
4. Enter username and password (both case sensitive)
5. ? or help for commands list
6. get filename (get file)
7. edit file then put filename (send file)



NAT => from private ips (locally) to public ip outside
DHCP => auto ip on all devices
ftp/https/and protocols we 
TCP and UDP diff

==read more about it because whats written maybe wrong==
ARP => translate IP address to MAC address => router makes because our private ip is not constant if using dhcp
and mac address cannot read mac address
thats why to send data to the correct device it creates a translating table, containing each ip and it's respective mac address
whenever we move data it uses this table to know where to send what

why use ips if router depends on mac address?