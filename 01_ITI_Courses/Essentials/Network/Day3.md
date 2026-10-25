# VLANs
* Create virtual networks without the need of physical connections (logical connections)
* Done with switches
* Each network has it's own ID (a number thats unique given to it)
* Breaks down a organization (a big network) into smaller groups for easier management which results in:
	* Communication within each VLAN is isolated (unicast/multicast/broadcast)
	* Each VLAN network has it's own unique range of address
		* VLAN 20 has ips from 192.168.1 to 192.168.10
		* VLAN 30 has ips from 192.168.11 to 192.168.15
	* Isolated communication = More secure
* ![[Pasted image 20261013174957.png|524]]

### ID VS IP
* IP => machine address  on the network
* ID => unique identifier given for each vlan network to differentiate between them

LIFI => ely b3d el wifi => moving data through light

## VLAN Modes
1. Switches have ==physical ports== (limited number obv)
2. When we first buy the switch it's just one big VLAN with all ports belonging to it
3. Using that same 1 switch, we can create multiple VLANs by telling the switch:
	anything that passes through port 14 to port 19 belongs to VLAN 20
	and anything through ports 1 - 6 belongs to VLAN 10
4. Now we have many VLANs which cannot communicate with each other, because each port belongs to 1 network/VLAN
5. Here comes the VLAN interface mode
	we can tell port 14 to accept traffic from ==VLAN 20 AND VLAN 10== by assigning the ==port== =="TRUNK MODE"==
	The default mode where each port belongs to ==ONE== VLAN is =="ACCESS MODE"==
* Here we talked about one switch doing all the work, but what if we have many switches each switch connecting 10 devices with 3 VLAN networks, and i wanna send some data from VLAN 100 which belongs to switch 1, to VLAN 10 which belongs to switch 5? = ==🔵TRUNK MODE== :D
	How can a switch port knows which packets are for this specific port/vlan tho? ==🟣TAGS== 

## VLAN Tags
* In case we are operating in trunk mode, and we wanna send some data to another VLAN
* A tag is added to each packet/segment leaving the VLAN, containing some packet information and the destination VLAN ID, so the packet is not lost through the network
![[Pasted image 20261013181710.png]]
* When destination port receives the packet, it removes the tag as it's no longer necessary
* Tags format: VLAN ID (802.1Q)
* Needless to say packet is only added in trunk mode where we have an outside destination, it isn't needed in access mode, we are all in the same network anyways.
* There is only one case when an untagged frame can go to a trunk port, in ==🔵Native VLANs== (Covered below)


> [!Note]
> 
> Without a layer 3 device to connect VLANs, devices in different VLANs cannot communicate
> 	Used to isolate certain VLANs for security reasons

## Types of VLANs
* Having VLAN types is done by configuring which type of data is allowed to pass through, by routing constraints, or firewall rules
### Default VLAN
* Default ID is 1 (VLAN 1)
* Native VLAN (explained below)
* Cannot be renamed or deleted
* Default for any new switch
* Up by default with no IP address (sees the whole network)
### Date VLAN
* For user generated traffic (emails and web traffic)
* An access port can belong to one data VLAN at a time, but may also have a Voice VLAN.
### Native 
* VLAN 1 by default 
* The one VLAN on a trunk whose frames are sent ==🔵untagged==, and any untagged frame arriving on that trunk is assumed to belong to it
* Trunk mode only
* both ends of a trunk should be configured with the same native VLAN
	Below switch 1, 2 both have VLAN 00 configured as the native VLAN

```
Switch 1: interface Gi0/1
		  switchport mode trunk
		  switchport trunk native vlan 99
Switch 2: interface Gi0/1
		  switchport mode trunk
		  switchport trunk native vlan 99
```

	Why?
		Both ends of a trunk link must be configured with the same native VLAN, so that whenever a trunk port receives an untagged frame, it sends it to the native VLAN on it's side

### Management VLAN
???
### Voice VLAN
* Over UDP
* Separate VLANs because voice traffic requires a dictated network to work in good quality:
* ![[Pasted image 20261013184951.png|316]]

* Each packet sent over this VLAN is sent with some special data set in the tag, to give packets priority value (we want a fast connection here) and some other stuff i dont understand

![[Pasted image 20261013185315.png|544]]





show interface f0/1 switchport => command to show info about vlans
crating vlan steps
1.switch # config t
vlan vlan-id
name vlan-name
end
config t => to return

port assignment
config t
interface interface-id 
switchport mode access
switchport access vlan vlan-id
switchport voice vlan-id
(binding port/interface to a specific vlan)
one port can be used in many vlans

show vlan  => show all vlans
show interface vlan => 


startup config => default startup config => saved in nvram (non volatile ram)
running config => config updated as we go => saved in ram (erased on restart)
to save running config we use the follwoign commands
	copy running config startup config

no vlan => remove all ports from the vlan without deleting the vlan


switch types:
	Plug and play => No config needed
	Management switch => needs manual configuration
	Layer 3 swtich

router can route switch cant