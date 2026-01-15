<h1>"Basic Router-on-a-Stick VLAN EPCC Lab</h1>

<h2>Description</h2>
This project is a simulated college campus network (EPCC) I built in Cisco Packet Tracer. This design helped me practice and strengthen my foundational networking skills. This lab represents two buildings within the same campus, each containing multiple VLANs to separate different types of users/departments.
<br />


<h2>Tools & Technologies Used</h2>

- <b>Cisco Packet Tracer</b> 
- <b>Router-on-a-Stick</b>
- <b>VLANs & Trunking</b> 
- <b>DHCP</b>

<h2>Objectives</h2>

- <b>Design a campus-style network based on a real-world college environment similar to EPCC.</b>
- <b>Practice VLANs and inter-VLAN routing by configuring my first router-on-a-stick design.</b>
- <b>Improve hands-on Cisco Packet Tracer and CLI skills, including implementing DHCP.</b>

<h2>Step 1: Design the General "Network/Logical" Plan</h2>

<p align="center">
1) Creating The VLAN Plan, IP Addressing Plan, Physical Topology, and Connections. <br/>
<img src="https://i.imgur.com/F0cxVKW.png" height="80%" width="80%" alt="#1"/>
<br/> - I am planning on creating a Inter-VLAN network design using my campus, EPCC, with using only 2 of the many buildings within the Valle Verde Campus, AST and the Enrollment Services Center.<br/>
<br />
________________________________________________________________________________________________________
<h2>Step 2: Setting Up The Logical Topology in Cisco Packet Tracer</h2>

 <p align="center">
1) I created 2 major VLAN Areas to represent the two different buildings I am using for this project which is the AST and Enrollment Services Center. Within these two buildings, I planned on creating 3 different VLANs for each to easily separate and manage it corresponding to their department.<br/> 
<img src="https://i.imgur.com/TNpFzIL.png" height="80%" width="80%" alt="#5"/>
<br />
2) After I created the different VLAN Areas, I used 2 endpoint devices (PCs and Printer) for each VLAN, and placed a main switch within each building that connects to the main router for this campus Valle Verde.
<img src="https://i.imgur.com/E83GUo0.png" height="80%" width="80%" alt="#7"/>
<br />
<br />
________________________________________________________________________________________________________
<h2>Step 3: Securing & Configuring the Switch</h2>

<p align="center">
1) Implementing basic configurations for AST-Switch including renaming the switch, and security hardening such as passwords, console security, etc. <br/>
<img src="https://i.imgur.com/viawBW1.png" height="80%" width="80%" alt="#8"/>
<br />
<p align="center">
2) Creating the VLANs within the AST-Switch. <br/>
<img src="https://i.imgur.com/pED3qRX.png" height="80%" width="80%" alt="#8"/>
<br />
<p align="center">
3) Repeat #1 & #2 for the ESC-Switch. <br/>
<img src="https://i.imgur.com/OYYR0wT.png" height="80%" width="80%" alt="#8"/>
<br />
________________________________________________________________________________________________________
<h2>Step 4: Connecting the Devices & Labeling Ports</h2>

<p align="center">
1) Start connecting the devices to their respected VLANs from the VLAN Plan from Step #1 and labeling the connected ports.<br/>
<img src="https://i.imgur.com/GPoVAmb.png" height="80%" width="80%" alt="#10"/>
<br />
________________________________________________________________________________________________________
<h2>Step 5: Configuring the Switch's Ports with their VLANs</h2>

<p align="center">
1) Start configuring the port interfaces with their respected VLAN planning from Step #1 with f0/1 interface to be trunk ports for the router.<br/>
<img src="https://i.imgur.com/1Nl0UO1.png" height="80%" width="80%" alt="#10"/>
<img src="https://i.imgur.com/ShHbfHD.png" height="80%" width="80%" alt="#10"/>
<br />
________________________________________________________________________________________________________
<h2>Step 6: Configuring the Router's Interfaces and creating sub-interfaces</h2>

<p align="center">
1) Enabling the G0/0 and G0/1 interfaces, and configuring the router's sub-interfaces with their corresponding VLAN. using the encapsulation dot1Q <vlan-id> command which tells the router which VLAN ID to associate with that sub-interface for routing between them. <br/>
<img src="https://i.imgur.com/61vChiu.png" height="80%" width="80%" alt="#10"/>
<br/> - Configuring AST Building VLAN
<img src="https://i.imgur.com/JOUSIDw.png" height="80%" width="80%" alt="#10"/>
<br/> - Configuring ESC Building VLAN
<img src="https://i.imgur.com/K2JyzdI.png" height="80%" width="80%" alt="#10"/>
<br />
________________________________________________________________________________________________________
<h2>Step 7: Setting up DHCP for the VLANs</h2>

<p align="center">
1) Excluding the first 10 ip addresses for each network from DHCP as a best practice so we are able to reserve them for other things such as gateways, SVIs, etc, later on. <br/>
<img src="https://i.imgur.com/McOKYWL.png" height="80%" width="80%" alt="#10"/>
<br/> - Creating the DHCP pool for each VLAN in the AST Building and assigning their network and default router.
<img src="https://i.imgur.com/J42hVMb.png" height="80%" width="80%" alt="#10"/>
<br/> - Creating the DHCP pool for each VLAN in the ESC Building and assigning their network and default router.
<img src="https://i.imgur.com/O0UAAJh.png" height="80%" width="80%" alt="#10"/>
<br />

________________________________________________________________________________________________________
<h2>Step 8: Verifying DHCP & Connectivity</h2>

<p align="center">
1) First, I tested DHCP within the PCs throughout the different VLANs and verified that it had assigned the IP Addresses correctly. <br/>
<img src="https://i.imgur.com/4S0kxAg.png" height="80%" width="80%" alt="#10"/><br/>
2) Verifying connectivity between the different VLANs by having PC0 (Student VLAN) pinging PC4 (Financial Aid VLAN).
<img src="https://i.imgur.com/F2fUJcY.png" height="80%" width="80%" alt="#10"/>
<br />
________________________________________________________________________________________________________
<h2>OVERVIEW:</h2>
<p align="center">
Basic Router-on-a-Stick VLAN for EPCC:  <br/>
<p align="left">
<b> 1) Designed a two-building campus topology | Created multiple VLANs | Assigned switch ports to the correct VLANs</b>
<p align="left">
<b> 2) Configured my first Router-on-a-Stick | Created router subinterfaces using encapsulation dot1Q | Assigned IP Addresses to each VLAN gateway.</b>
<p align="left">
<b> 3) Configured DHCP pools on the router for each VLAN | Set default gateways and DNS settings | Used ip dhcp excluded-address to reserve static IPs.</b>
<p align="left">
<b> 4) Refreshed and practiced common Cisco IOS Commands </b>
<br />


- https://github.com/galbachjr
________________________________________________________________________________________________________
  

</p>
