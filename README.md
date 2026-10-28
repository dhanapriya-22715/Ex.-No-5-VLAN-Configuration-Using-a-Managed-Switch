## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date: 28/10/2026
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
<img width="1917" height="1135" alt="image" src="https://github.com/user-attachments/assets/ea0c7746-0d21-440f-a47c-3ba7688b30c2" />
<img width="1917" height="1145" alt="image" src="https://github.com/user-attachments/assets/0568e8ec-65a4-4611-9e2a-020413ab9352" />
<img width="1917" height="1147" alt="image" src="https://github.com/user-attachments/assets/f001f884-6561-48a1-bbea-1bd14e102ffe" />



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
<img width="1917" height="1150" alt="image" src="https://github.com/user-attachments/assets/1cc5d9cf-9cae-4b47-a3fd-c14a4ab2c850" />

•	PC IP settings<br>
<img width="1917" height="1138" alt="image" src="https://github.com/user-attachments/assets/1f2a4ac7-90ca-4596-81dc-e1373954c044" />

•	Successful ping between PCs in the same VLAN<br>
<img width="1917" height="1137" alt="image" src="https://github.com/user-attachments/assets/068ddfed-d860-451b-a381-98c7943630d0" />

•	Failed ping between PCs in different VLANs<br>
<img width="1917" height="1142" alt="image" src="https://github.com/user-attachments/assets/3b8da678-19fb-49df-a879-00a70ed62846" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

