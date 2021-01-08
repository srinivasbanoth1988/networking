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
 
 
 ### 2.4 ARP(Address Resolution Protocol)
 
 In Below Nework topology, PC1 communicates with PC2 via Switch. The subnet mask tells us which part of the IP address is the network and host part, the host that uses 92.168.1.1 sees that 92.168.1.2 is using the exact same network address and will know that it can use ARP to find the MAC address, create an Ethernet frame, encapsulate the IP packet and send it towards the switch.
 
 
 

	                 ┌────────────────┐     ┌────────────────┐    ┌────────────────┐
	                 │                |     │                |    │                |
	                 │      PC1       |-----│    Switch      |----│         PC2    |
	                 └────────────────┘     └────────────────┘    └────────────────┘
			 92.168.1.0                                    92.168.1.2
 
