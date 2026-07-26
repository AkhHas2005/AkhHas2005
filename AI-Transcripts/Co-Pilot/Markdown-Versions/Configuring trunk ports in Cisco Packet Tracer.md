# Configuring trunk ports in Cisco Packet Tracer  

## Me
In cisco packet tracer, how can I do this on my network (attached image, inserted below):  

3.	Configure Trunk Ports:  
Configure the link between SW1 and SW2 as a trunk link to allow VLAN traffic to pass between the switches.  

[![download-(2).jpg](https://i.postimg.cc/R0QWyC0q/download-(2).jpg)](https://postimg.cc/2qyjBDhf)  

## Copilot
To configure the link between SW1 and SW2 as a trunk link in Cisco Packet Tracer, follow these steps:  

1. **Access the CLI of SW1**:  

- Click on SW1.
- Go to the CLI tab.

2. **Enter Configuration Mode**:  

```
enable
configure terminal
```  

3. **Configure the Interface as a Trunk Port**:  

- Assuming the link is on interface `FastEthernet0/1`, enter the following commands:  

```
interface FastEthernet0/1
switchport mode trunk
```  

4. **Repeat the Steps for SW2**:  

- Click on SW2.
- Go to the CLI tab.
- Enter Configuration Mode:  

```
enable
configure terminal
```  

- Configure the interface as a trunk port:  

```
interface FastEthernet0/1
switchport mode trunk
```  

5. **Verify the Configuration**:  

- On both switches, you can verify the trunk configuration with:  

```
show interfaces trunk
```  

This will allow VLAN traffic to pass between SW1 and SW2. If you have any more questions or need further assistance, feel free to ask!  

*End of this Conversation*
