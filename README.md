## Networking

### 1. Default Gateway IP:

   
A node to another network(eg . Internet via Router). The default gateway IP is used when there is no other gateway is specified. The default Gateway(like Router) is a mediator between Local Network and WAN(Internet). 

In general, Router/gateway device connects two ip networks. Computer that are attached to the same wifi/switch are local to each other. The devices with in the same network sends data packets to each other without going to outside network. In below image PC1 and PC2 connectes to Roter via Wifi or switch. Router default ip is 203.0.113.42, and this ip is exposed to outside local network.
   
   
 
                       
                       
	                 ┌────────────────┐
	                 │                |-------------> INTERNET
	                 │      Router    |203.0.113.42
	                 └────────────────┘  
                          |
                          |192.168.1.196
                          |
                          |
	    192.168.1.10 ┌────────────────┐ 192.168.1.20
	  PC2------------│                |----------- PC1
	                 │  Wifi/switch   |
	                 └────────────────┘  





### 2.1 SNAT(Source Network Adrress Transaltion)

SNAT changes the private IP address of the source host to public IP address. It can also change the source port in the TCP/UDP headers. SNAT comesinot picture when devices insdie of the secured network access the public network. 



	                 ┌────────────────┐
	                 │                |-------------> SNAT -------> INTERNET
	                 │      Source    |
	                 └────────────────┘  
    
    
 ### 2.1 DNAT(Destination Network Adrress Transaltion)  
 
 Destination NAT changes the destination address in the IP header of a packet. DNAT happens when public network communicates devices hosted in securced network zone.



	                 ┌────────────────┐
	                 │                |<------------- DNAT <------- INTERNET
	                 │ Destination    |
	                 └────────────────┘  
 
 ### 2.3 
 
 A.192.168.101.2/24
 B.192.168.101.3/24
 C.192.168.102.2/24
 D.192.168.102.3/24
 
 
 We need Following elements to have above network configurations. We need to configure two VLAN interfces for 192.168.101.X and 192.168.102.X. 
 


	                 ┌────────────────┐     ┌────────────────┐    ┌────────────────┐
	                 │ VLAN 101       |     │                |    │VLAN Inter 102  |
	                 │192.168.101.0   |     │   L3 Switch    |    │192.168.102.0   |
	                 └────────────────┘     └────────────────┘    └────────────────┘
			                                |
							|
							|
							|
							|
							|
							|
							|
							|
	192.168.101.2/24 ┌────────────────┐     ┌────────────────┐    ┌────────────────┐
	PC2--------------|  VLAN 101      |     │                |    │   VLAN 102     |------PC3 - 192.168.102.2/24
	                 │                |-----│    L2 Switch   |----│                |------PC3 - 192.168.102.3/24
	                 └────────────────┘     └────────────────┘    └────────────────┘
			          |
				  |192.168.101.3/24
				  |
				  PC1
 
 PC1,PC2 are configured in VLAN 101 interface, so the ip's can be 192.168.101.2/24 and 192.168.101.3/24
 PC1,PC2 are configured in VLAN 102 interface, so the ip's can be 192.168.102.2/24 and 192.168.102.3/24
 
 PC1 of VLAN 101 wants to communicate with the PC2 of some other VLAN 102. As both end devices are of different VLAN, we need L-3 switch for routing the data from PC1 to host PC2.

the L-2 switch will locate the destination host. Then, it will learn the destination address of the receipt host from the MAC table. After that, the layer-3 switch will perform the switching and routing part on the basis of IP address and subnet mask. Once it has all the necessary information, it will establish the link between them and route the data to the PC1 from the PC2 end.
 
 ### 2.4 ARP(Address Resolution Protocol)
 
 In Below Nework topology, PC1 communicates with PC2 via Switch. The subnet mask tells us which part of the IP address is the network and host part, the host that uses 92.168.1.1 sees that 92.168.1.2 is using the exact same network address and will know that it can use ARP to find the MAC address, create an Ethernet frame, encapsulate the IP packet and send it towards the switch.
 
 
 

	                 ┌────────────────┐     ┌────────────────┐    ┌────────────────┐
	                 │                |     │                |    │                |
	                 │      PC1       |-----│    Switch      |----│         PC2    |
	                 └────────────────┘     └────────────────┘    └────────────────┘
			 92.168.1.0                                    92.168.1.2
 
