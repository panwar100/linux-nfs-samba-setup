# File Sharing Configuration: NFS and Samba
This repository provides step-by-step instructions to configure NFS (Network File System) and Samba for file sharing across Linux and Windows systems.

# Table of Contents

1.[NFS Configuration](#1-nfs-configuration)

- [Master (Sender) Setup](#master-(sender)-setup)
- [Server (Receiver) Setup](#server-(receiver)-setup)

2.[Samba Configuration](#2-samba-configuration)

- [Master (Sender) Setup](#master-(sender)-setup)
- [Windows Client (Receiver1)](#window-client-(receiver1))
- [Linux Client (Receiver2)](#linux-client-(receiver2))

# 1.NFS Configuration
## one (Sender) Setup
a) Install NFS utilities:

![Screenshot from 2024-12-08 21-26-19](https://github.com/user-attachments/assets/f11a27e5-e1e9-447e-8a5d-25f271e46514)

b) Start and check the status of the NFS server:

![Screenshot from 2024-12-08 21-27-36](https://github.com/user-attachments/assets/628f2e80-5a1c-4ee2-baad-185622de8fb8)


c) Create a directory to share via NFS:

![Screenshot from 2024-12-08 21-28-25](https://github.com/user-attachments/assets/e371ef3d-424e-4f18-9f0f-d681aa1f4df1)


d) Edit the NFS export file to configure the shared directory:

vi /etc/exports

e) Add the following line:

![Screenshot from 2024-12-08 21-30-30](https://github.com/user-attachments/assets/43d4d31e-34eb-4fd5-8e0f-19442af1a123)


f) Apply export changes and verify exports:

![Screenshot from 2024-12-08 21-32-19](https://github.com/user-attachments/assets/71d86566-2120-4250-b4b4-009609641d78)


g) Configure the firewall for NFS services:

![Screenshot from 2024-12-08 21-35-15](https://github.com/user-attachments/assets/077d1b4f-1eb0-4cfa-ba7c-45d9f43abf82)


h) Note the server IP:
ip = 192.168.1.124

## Lenovo (Receiver) Setup
a) Install NFS utilities:(ubuntu)

![Screenshot from 2024-12-08 21-43-58](https://github.com/user-attachments/assets/0dff5358-2f80-49b4-a4fa-b55589e8b55f)

![Screenshot from 2024-12-08 22-18-22](https://github.com/user-attachments/assets/03b33bc8-1806-4ff3-a082-58c87715d6bb)


b) Configure firewall for NFS services:

![Screenshot from 2024-12-08 21-50-48](https://github.com/user-attachments/assets/47a3dbf5-e735-4b5c-8eeb-daec774fe4ac)

![Screenshot from 2024-12-08 22-02-42](https://github.com/user-attachments/assets/51e2409a-6eea-49fe-b4bb-3b9e2773f188)

c) Verify the NFS exports from the sender:

![Screenshot from 2024-12-08 22-26-51](https://github.com/user-attachments/assets/d45d0a93-bd86-4f41-985f-9901f4ab4f38)


d) Create a mount point and mount the shared directory:

![Screenshot from 2024-12-08 22-29-06](https://github.com/user-attachments/assets/9a206bbb-5d04-46b9-8fff-82e81369ee5c)

e) Test the NFS setup:

![Screenshot from 2024-12-08 22-30-16](https://github.com/user-attachments/assets/b64b9fd8-2a60-45de-b269-e461a6680166)


f) Verify on the one system:

![Screenshot from 2024-12-08 22-31-00](https://github.com/user-attachments/assets/fb297a46-4a5a-4f85-98a8-05c1dd73c7d0)

# 2.Samba Configuration
## One (Sender) Setup
a) Create a directory for sharing:

![Screenshot from 2024-12-09 18-28-30](https://github.com/user-attachments/assets/8514c041-437a-4ad5-a046-464505590d21)

b) Install Samba:

![Screenshot from 2024-12-08 22-33-34](https://github.com/user-attachments/assets/e2c46180-1954-4a37-8fb0-90ef170e5004)

![Screenshot from 2024-12-08 22-34-14](https://github.com/user-attachments/assets/833d01cc-0c40-4788-a16d-9996ce9b5b6c)


c) Configure Samba user credentials:


![Screenshot from 2024-12-09 18-31-28](https://github.com/user-attachments/assets/6a8bed89-bdd2-47e4-b654-ffd4af4fc0e8)



d) Set permissions for the shared directory:

![Screenshot from 2024-12-09 18-35-21](https://github.com/user-attachments/assets/f847bab8-284a-4d68-a042-9730b13cdc2e)


e)Label the directory for Samba:

![Screenshot from 2024-12-09 18-36-46](https://github.com/user-attachments/assets/96e6cfa7-2cce-4f13-a5bf-bb65fa41919d)


![Screenshot from 2024-12-09 18-37-25](https://github.com/user-attachments/assets/6a16fdb1-1abc-4d98-8f36-d12eba67775c)


f) Add Samba to the firewall:

![Screenshot from 2024-12-08 22-42-37](https://github.com/user-attachments/assets/6c961b7e-354f-4a85-a3df-59ea11e07b5d)


g) Edit the Samba configuration file:

![Screenshot from 2024-12-09 18-38-27](https://github.com/user-attachments/assets/e82d47b8-814e-4426-b3ed-5ec16dadc318)


h) Add the following section:

![Screenshot from 2024-12-09 16-39-21](https://github.com/user-attachments/assets/3c46ddea-8aa3-4d95-8078-4dffc2790a45)


## Windows Client (Receiver1)
a) Access the shared folder from Windows:

![Screenshot from 2024-12-09 10-45-44](https://github.com/user-attachments/assets/5847ce3c-b529-4b99-a2bf-c313adcc2b0b)




b) Enter credentials:

![Screenshot from 2024-12-09 17-08-24](https://github.com/user-attachments/assets/a47be340-ef11-4704-9a47-d59d7b83aef5)


![Screenshot from 2024-12-09 17-09-17](https://github.com/user-attachments/assets/cd0d75a5-650f-42a0-a29a-2d87f941625e)

![Screenshot from 2024-12-09 17-09-38](https://github.com/user-attachments/assets/1ad4a513-619e-45fa-ae1e-4b62f4a040b5)

![Screenshot from 2024-12-09 17-14-10](https://github.com/user-attachments/assets/bb91293e-b8b7-47c7-bc4d-01f43376e97e)

![Screenshot from 2024-12-09 17-14-46](https://github.com/user-attachments/assets/606ebdf5-49b4-4865-aaca-46d69f78f56b)

c) verify:

![Screenshot from 2024-12-09 18-40-11](https://github.com/user-attachments/assets/e0880c25-cb35-48e3-b7cc-033171106e74)


## Linux Client (Receiver2) (ubuntu)
a) Create a mount point:

![Screenshot from 2024-12-09 17-59-29](https://github.com/user-attachments/assets/ef66ee4e-28d3-45ff-9cc8-ac2de3d95a92)

b) Install Samba client:

![Screenshot from 2024-12-09 18-01-23](https://github.com/user-attachments/assets/79ccaedd-d8f9-4ae9-b925-9efa0dba19b0)

![Screenshot from 2024-12-09 18-07-28](https://github.com/user-attachments/assets/ad26e358-488b-44cf-9cf0-26e77f12ecf2)


Avoid full version if you are a client;instead,use the Samba client  
 
c) Add Samba to the firewall:

![Screenshot from 2024-12-09 18-08-27](https://github.com/user-attachments/assets/1977a3e1-81d3-40a2-9531-4061e9be8a03)


d) Mount the shared folder:

 ![Screenshot from 2024-12-09 18-09-20](https://github.com/user-attachments/assets/e4a96d4a-a6b9-46d9-b984-aede92d2d9df)

