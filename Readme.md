# Server Virtualization 

##  Experiment Title
Server Virtualization using VirtualBox with Network Configuration, Web Server Deployment, SSH Access, and Packet Capture



## Aim
To implement server virtualization by creating multiple virtual machines and configuring NAT, Bridged, and Host-Only networking, enabling communication between VMs, SSH access from host to VM, deploying a web server, and capturing network packets using Wireshark.

### Environment

* **Host OS:** Ubuntu
* **Hypervisor:** QEMU/KVM + virt-manager
* **Server VM IP:** `192.168.56.102`
* **Client VM IP:** `192.168.56.103`
* **Networking:** NAT (libvirt `virbr0`) and Bridge (`br0`)

##  Software & Tools Used
- Host OS: Ubuntu Linux
- Virtualization Tool: Oracle VirtualBox
- Guest OS: Alpine Linux
- Web Server: nginx
- Remote Access: OpenSSH
- Packet Analyzer: Wireshark
- Version Control: Git & GitHub



##  Virtual Machine Setup

### Virtual Machines
| VM Name | Purpose |
|-------|---------|
| webserver-vm | Acts as web server |
| client-vm | Acts as client machine |

### Network Configuration
Each VM was configured with:
- Adapter 1: NAT
- Adapter 2: Host-Only



##  Procedure

### Step 1: Create Virtual Machines
- Installed VirtualBox on host system
- Created two VMs using Alpine Linux ISO
- Allocated 512 MB RAM and 1 CPU core to each VM



### Step 2: Network Configuration
- Enabled NAT and Host-Only adapters
- Verified IP addresses using:
```bash
ip a
```
### Step 3: Enable Network Interfaces
```bash 
ip link set eth1 up
```
### Step 4: Ping between VMs
```bash
ping <other_vm_ip>
```
### Step 5: SSH from host to VM
```bash
apk update
apk add openssh
rc-service sshd start
```
### connect from the host

ssh user@<`192.168.56.102`>

### Step 6: Web Server Setup
install nginx
```bash
apk add nginx
rc-service nginx start
```
### Step 7 Client Access web Server
 from client VM
 ```bash
 curl http://192.168.56.102
 ```


