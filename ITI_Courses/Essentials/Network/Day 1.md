* Computer network
	Collection of devices connected together through connection media (network) to perform a certain task such as resources sharing
		Resources => File, devices, software, voice and video calls sharing
* NIC
	Network card
* MAC Address
	Device bound physical address, burned on the NIC card, unique across the world
	Consists of 8 hex decimal numbers and chars, 
	First 4 are manifacturing company code
	Last 4 are unique serial number per device
* IP Address
	Logical address to identify device over the IP network layer
* Protocols
	Communication roles
* Hub
	Allow different ==nodes== to communicate with each other
	Works at network layer 1
	It doesn't understand where to send what, it broadcasts data to all devices that are connected through it, even to the device that sent them.
	Slows the network
* Switch
	Allows different ==nodes== to communicate with each other at the same network
	Understands MAC address and can specify where to send what
	Layer 2 device
	Wired connection
	Doesn't slow network
* Router
	Allows different ==networks== to communicate with each other
	Wired or wireless connection
* Topology
	How devices are connected (infrastructure) and how message flows from one device to another

## Network classification
### According to covered area
* LAN => Local area netword
	Group of PANS connected together in a small geo area
* MAN => Metroploitan Area network
	Between LAN and WAN
	Microwaves sent from one place to another
	should share same type of hardware and antenna
	City level
* PAN
	Personal Area Networks
* WAN Wide area networks
	Country level
	Connects to LANs (WAN Link)
	Wan can contain multiple smaller networks such as LAN or MAN
	Under ISP Adminstrative control

### According to Topology
#### Types:
* Physical topology
	How computers connect together physically (wired)
* Logical topology
* Bus Topology
	All devices are connected to a central cable
	Data moves in one direction at the same time
	Single point of failure
	Less expensive 
* Star topology
	Like how home devices are connected to router
	Nodes communicate by passing data through central device
	Single point of failure
	2 way connection
* Hubbed star 
* Switch star
* Ring topology
	If any device fails, network fails
	Each device is connected directly to two other devices
	No data collision
	High trafic
* Dual ring topology
	Performs better than ring (no data collision) as data flows in two directions
* Mesh topology
	Data goes strictly from 1 devices to the target (more secure) as each 2 diveces are connected to each other (Redunant)
	More secure
	No single point of failure as it's easy to find another path do send data of one fails
* Hybrid topology
	..
	![[Network topology.excalidraw]]

### According to network model
* Peer to peer networks
	All nodes are the same and equals no need for a centralized unit to send data between us
	In home or small office
* Client/Server
	Connect to central server to get a service (connect to drive server to get your data)
	Expensive (needs multiple licenses)

## OSI Layers
### Application layer
* Interface to endusers
* Decides which protocol to use to do the request (HTTPS/HTTP/FTP/...)

### Presentation
* Mediator between source and destination that is responsible for finfing a common presentation between them
* Provide transformation of data (Encoding and decoding)
* Ensures information sent by source is readable by destination
* Converts data to binary / encryption / Compression
### Session Layer
* Connection management (start/manages and terminates sessions/connections) between cooperating applications
* C
### Transport layer
* Organizes and breaks data into segments to fit into network
	* Each segment has a sequence number
* Should be able to detect a corrupt or a not sent segment, and according to the protocol should handle error recovery (Three way handshake)
* Three way handshake is done in TCP and not UDP
	As tcp is more concerned with data integrity more than speed (udp is the opposite)
* Error recovery and flow control

### Network layer
* Responsible for Internet protocol (IP)
* Organize data into packets (datagram)
	Organizes segments into packets adding some metadata to each packet like source/dest IP
* Knows the best path to destination
* End to end Addressing (Logical addressing and path selection)

### Data Link
* Data transfer using MAC address
* Organize data into frames to put on the physical medium/link
* Error control over frames
* Hop to Hop addressing
* Layer 2 device

### Physical layer
* From bits to signals across the medium /electric signals/light pulses/radiowaves

## IP Addresses
### IP Classes
* Subnet mask:
	To determine IP class
	Each part opposite to the 255 part of subnet means this part of the network address

* Number of devices per network: (2^n) -2 where n is number of zeros in subnet mask 
* Can be represented as 192.168.1.2/24 ??
	The /24 represents subnet mask and IP class at the same time
	32 - 24 = 8 (which is the n used in the equation)

* Classes points to how many devices can the network support
* Class A from 1 to 126 in the first part 001.xxx.x.x to 126.xxx.x.x
* 127 doesnt belong to any class ( a loop back address to your own device)
* Class B from 128 to 
* Class C from 

#### Default gateway:
* Router IP, the ip used to connect you outside the local network


router ocnfig steps
enable
	config t or configure terminal
		hostname iti => change router name
		interface gig 0/0 => select this interface to config => when we look at the caple we see that this is router side interface
			ip address 192.169.1.1 255.255.255.0 => ip address and subnet mask
			no sh (no shutdown - open router port on)

lap:
	ip class B