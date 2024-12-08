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
## Master (Sender) Setup
a) Create a directory for sharing:

![Screenshot from 2024-12-08 22-32-28](https://github.com/user-attachments/assets/c685e6ba-d569-4346-9f15-77d27aab7d72)

b) Install Samba:

![Screenshot from 2024-12-08 22-33-34](https://github.com/user-attachments/assets/e2c46180-1954-4a37-8fb0-90ef170e5004)

![Screenshot from 2024-12-08 22-34-14](https://github.com/user-attachments/assets/833d01cc-0c40-4788-a16d-9996ce9b5b6c)


c) Configure Samba user credentials:

![Screenshot from 2024-12-08 22-35-50](https://github.com/user-attachments/assets/74b638ab-5974-453e-8ca5-c27ccaa020d8)


d) Set permissions for the shared directory:

![Screenshot from 2024-12-08 22-37-34](https://github.com/user-attachments/assets/9f968821-0e72-4474-be53-d682e9cb9b03)


e)Label the directory for Samba:

![Screenshot from 2024-12-08 22-39-50](https://github.com/user-attachments/assets/18b0ac49-e09a-4a4d-bde2-336e85753ea6)


![Screenshot from 2024-12-08 22-40-25](https://github.com/user-attachments/assets/25f6f783-71d9-4615-b6b8-6dd2a68f0595)


f) Add Samba to the firewall:

![Screenshot from 2024-12-08 22-42-37](https://github.com/user-attachments/assets/6c961b7e-354f-4a85-a3df-59ea11e07b5d)


g) Edit the Samba configuration file:

vi /etc/samba/smb.conf

h) Add the following section:

![Screenshot from 2024-12-08 22-46-18](https://github.com/user-attachments/assets/acaab6d0-8bb9-4300-be63-705dd2c539b5)

## Windows Client (Receiver1)
a) Access the shared folder from Windows:
Open Run (Win + R) and type: \\192.168.0.18

b) Enter credentials:
yaml

Username: varun
Password: 1234

## Linux Client (Receiver2)
a) Create a mount point:

mkdir data3

b) Install Samba client:

yum install samba-client -y

c) Add Samba to the firewall:

firewall-cmd --add-service=samba

d) Mount the shared folder:

mount -t cifs //192.168.0.18/my_repo1 /data3 -o username="varun"
