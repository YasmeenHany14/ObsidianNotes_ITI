![[Pasted image 20261007092401.png]]![[Pasted image 20261007093716.png]]
Or software to execute other software
	How is operating system different from user apps software?
		Because it contains kernel which is core component of any operating system which can communicate with hardware
		![[Drawing 2026-10-07 09.41.01.excalidraw]]
![[Pasted image 20261007095310.png|434]]
![[Pasted image 20261007102813.png]]
![[Pasted image 20261007102931.png]]
![[Pasted image 20261007103036.png]]

![[Pasted image 20261007103331.png]]

![[Pasted image 20261007103422.png]]

![[Pasted image 20261007104755.png]]![[Pasted image 20261007105140.png]]

![[Pasted image 20261007105409.png]]

![[Pasted image 20261007105805.png]]
	MAN => a street or university
	WAN => wide area network like a whole city or even wider
	client-server => like how google stores data in servers for clients(us) to access it
	peer-to-peer => 
![[Pasted image 20261007110743.png]]
* Clustering / Resource bool
	A logical way of grouping related things together
	Provides a way for scalability => whenever we need resources add another system to the cluster which increases total available resources
	[Clustered vs Distributed systems](https://www.geeksforgeeks.org/computer-networks/distributed-system-vs-clustered-system/)

![[Pasted image 20261007111447.png]]
	Like how air bag systems work, it should detectd incident before happening, and timing is crucial because seconds later the damage will be already done and seconds earlier may cause bigger problems
* Hard real-time => Timing should be very percise with no error margin
* Soft => Allows some timing error margin
![[Pasted image 20261007112050.png|480]]

![[Pasted image 20261007112302.png]]


-------------------------------------------------
Each hardware component has a controller that is responsible for handling all I/O communications for it
Each controller has a local buffer which stores information about current operations required from the hardware

![[Pasted image 20261007120559.png]]
![[Pasted image 20261007120933.png]]
* POST => Power On System Test -> Runs hardware tests on startup
* Registers => CPU cache -> small and fast memory that stores instructions for CPU
	Each register has a job it's supposed to do and a specific part of the instruction to save
![[Pasted image 20261007121350.png]]
* A table with each hardware, it's interrupt types and what to do when  each happens

![[Pasted image 20261007121955.png]]
![[Pasted image 20261007122257.png]]

![[Pasted image 20261007123246.png]]

![[Pasted image 20261007123701.png]]
* Synchronous is like how the printer works, we cant modify whats being printed the moment the command is given to it, we should wait or interrupt to take back control
* Asynchronous is like how whatsapp messaging works, we can both read and write at the same time

DMA Direct Mem Access


![[Pasted image 20261007124355.png]]

![[Pasted image 20261007124541.png]]

![[Pasted image 20261007125204.png]]
* MMU (Memory Management Unit) => Responsible from translating between logical and physical address

### Hardware protection


![[Pasted image 20261007143256.png]]

![[Pasted image 20261008091615.png]]

![[Pasted image 20261008094554.png]]

![[Pasted image 20261008095700.png]]

![[Pasted image 20261008101244.png]]

![[Pasted image 20261008101520.png]]


1h:28

![[Pasted image 20261008102601.png]]


memory => main memory + reallocation register (inside mmu)
memory is pages from 4 / 8 bytes per page
page is just some data grouped together


## Cloud computing
### IAAS
1. VM
	You have control over software, os and basic config and you get back a vm with these specs
2. Baremel service
	A dedicated hardware not a vm


