# Network Analysis Report  

## Introduction
This report documents the analysis of basic networking concepts using Linux command-line tools. 
The objective of this task is to understand how systems communicate over a network and to gain hands-on experience in network troubleshooting, which is a core skill for DevOps engineers.


## Objective
- To understand IP addressing and network interfaces
- To test network connectivity
- To inspect open ports and services
- To verify DNS resolution
- To analyze network routing paths
- To simulate and understand network failure scenarios

## Environment Details
- Operating System: Ubuntu Linux  
- Platform: AWS EC2  
- Interface: Linux CLI  
- Tools Used:  `ip`, `ping`, `ss`, `nslookup`, `dig`, `traceroute`

## 1.IP Address and Network Interface Analysis

### Command Used
`ip a`    (or)    `ifconfig` [use "sudo apt install net-tools"]   

### Observation
- Identified available network interfaces.            
- The primary network interface was enX0.             
- A private IP address was assigned to the system.           

### Analysis
- IP addressing helps uniquely identify systems on a network.          
- Verifying network interfaces is the first step in diagnosing connectivity issues.   

## 2.Network Connectivity Test

### Command Used
`ping google.com`

`ping -c 4 google.com`    # Send 4 packets only              
`ping -i 2 google.com`    # 2 seconds interval              
`ping -s 100 google.com`  # Packet size           


### Observation
- ICMP packets were successfully sent and received.         
- No packet loss was observed.          
- Network latency was displayed.         

### Analysis
- Successful ping results confirm that the system has active network connectivity and can communicate with external servers.       

## 3.Open Ports and Services Inspection

### Command Used
`ss -tuln` or `netstat -tuln`            
ss is the modern replacement for netstat; it is faster, more efficient, and preferred in DevOps environments.

### Observation
- Listed all listening TCP and UDP ports.          
- SSH service was running on port 22.           

### Analysis
- Inspecting open ports helps verify whether required services are running and accessible.     

## 4.DNS Resolution Test

### Commands Used
`nslookup google.com`  or  `dig google.com`             

### Observation
- Domain name was successfully resolved to IP addresses.         
- DNS server responded correctly.        

### Analysis
- DNS resolution is critical for application communication.                
- DNS failures can cause service outages even if the network is up.       

## 5.Network Path Analysis

### Command Used
sudo apt update            
sudo apt install traceroute               
`traceroute google.com`           

### Observation
- Multiple hops were observed between the local system and the destination.         
- Network latency varied across hops.            

### Analysis
- Network path analysis helps identify routing paths and possible network delays.                  

## 6.Network Failure Simulation

### Action Performed
`sudo ip link set enX0 down`          
The primary network interface (enX0) was temporarily disabled to simulate a network failure.                     

### Observation
- Network connectivity was lost.           
- SSH access to the instance was unavailable.             

### Recovery
- The instance was recovered by stopping and starting it from the AWS console, which restored the network interface.              

### Analysis
- This simulation demonstrated how network failures impact system accessibility and how recovery actions are performed in real-world scenarios.   

## Issues Faced and Troubleshooting
| Issue                                     | Resolution                                 |
| ----------------------------------------- | ------------------------------------------ |
| ifconfig was not found                    | installed net-tools                        |
| Traceroute package not available          | updated server and installed traceroute    |
| SSH access lost after disabling interface | Recovered instance via AWS stop/start      |

## Key Learnings

- Understanding of IP addressing and interfaces            
- How to test connectivity using ping              
- How to inspect open ports and services          
- Importance of DNS in networking             
- How network failures affect remote access             
- Real-world recovery techniques in cloud environments              

## Conclusion

This task provided practical exposure to Linux networking fundamentals and strengthened troubleshooting skills required for DevOps and cloud operations.                






