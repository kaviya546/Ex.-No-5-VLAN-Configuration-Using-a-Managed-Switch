## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:06.09.2025
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
![WhatsApp Image 2025-09-06 at 13 52 31_f7e5fbfe](https://github.com/user-attachments/assets/3e30605f-f699-4fc9-a423-65329c4a1cb5)

•	PC IP settings<br>
![WhatsApp Image 2025-09-06 at 13 53 39_0cf63fdd](https://github.com/user-attachments/assets/17c76b6a-2b2a-4d1a-ae23-9562cbc90716)
![WhatsApp Image 2025-09-06 at 13 54 00_1e0755d4](https://github.com/user-attachments/assets/f0bec0ba-934a-4ae8-9def-819147e8afbf)
![WhatsApp Image 2025-09-06 at 13 54 14_0eab1224](https://github.com/user-attachments/assets/c6f86aac-da67-4f18-a5b5-17da8558161e)
![WhatsApp Image 2025-09-06 at 13 54 31_247eb19c](https://github.com/user-attachments/assets/d212a8f5-857a-458b-a7a4-be38cdcfa3fa)


•	Successful ping between PCs in the same VLAN<br>
![WhatsApp Image 2025-09-06 at 13 54 57_277ab8eb](https://github.com/user-attachments/assets/1ab90e84-7669-4bbf-a208-1749e7c9d74f)

•	Failed ping between PCs in different VLANs<br>
![WhatsApp Image 2025-09-06 at 13 55 13_617935d0](https://github.com/user-attachments/assets/066a374c-ab62-4001-813d-5bde8232807c)

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

