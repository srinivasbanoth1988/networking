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




