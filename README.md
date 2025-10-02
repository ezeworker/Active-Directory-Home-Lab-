# Active-Directory-Home-Lab-

## Objective



### Skills Learned



### Tools Used

## Steps
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1c6e0827-4d6f-47a5-b1b4-495019655910" />

*Ref 1: Network Diagram*

Here is the Network Diagram on how the Home lab will be set up.This consists of two virtual machines. One running the Windows 2022 Server which will act as the Domain Controller (DC) and the other unning Windows 10 this will serve as the client. The DC will also consist of the following services: Domain/Active Directory Domain servcies (AD DS), Remote Access Services/ Network Address Translation (RAS/NAT) and a Dynamic Host Control Protocol service (DHCP) where the DC will define the scope of the client machines that join the domain. For this home lab to be smooth ensure virtualisation is enabled in the BIOS of the system running this Lab.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/80ddeadc-e68a-4f76-a6f1-ac6f2ef27dae" />

*Ref 2: Virtual Box tool bar*

Once Virtual Box is installed the DC and Client machines will need to be set up. This can be done by visting  <a href="https://www.virtualbox.org/wiki/Downloads"> The Oracle VirtualBox website</a> and installing the correct host. The DC will be done first and the client machines will be done later. By selecting New we can set up a new virtual machine. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/d5eb369e-5e43-4ba0-b1eb-3237e0d3ed8d" />


*Ref 3: Virtual Machine Setup (ISO & Hardware)*

In order to create the DC virtual machine the iso image for the <a href="https://info.microsoft.com/ww-landing-windows-server-2022.html"> Windows 2022 Server </a> will be needed. Once the ISO is acquired. It is also important to tick the "Skip Unattended Installation" if this is kept unchecked the vritual machine will install the command line interface version of the server. Then set the memory and number of cores according to the system running this lab. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f258cb4a-5d90-4759-87a8-5346db45e48a" />

*Ref 3: Virtual Machine Setup (Hard Disk)*

Here one can set the storage for the Hard Disk and the click finish. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/b1d0288e-3981-4558-921e-6c6db5b739f3" />

*Ref 4: Virtual Machine Settings*

Before starting the machine there are few configurations that are required. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/9586991e-9531-4224-aa23-d2f262544836" />

*Ref 5: Virtual Machine Settings (Biredirectional)*

This will enables us to drag and drop items from the physical machine to the virtual machine and escape the Virtual machine without having to use the Host key 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/c863dd2f-650f-4a01-81cd-c7b4edae3d43" />

*Ref 6: Virtual Machine Settings (Network)*

Here the Network settings are being configured to match the network diagram in ref 1. Adapter 1 is attached to the NAT by default which is the Internet (blue cloud). Adapter 2 needs to be attached to the internal network as shown in Ref 6. Once done click ok and start the virtual machine. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1e59d079-5517-41ef-968f-b063688bc3ad" />

*Ref 7: Virtual Machine running*

Here the Windows Server 2022 DC machine is running. The next step is to follow the setup.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/aa6f3518-5b7d-4d05-b343-31f4a2109bd0" />

*Ref 8: DC setup*

Hint install now :)

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/d561646d-e471-4e35-bb3d-89a78ec09f3b" />

*ref 9: DC standard evaulation Desktop experience*

Select the standard evaulation desktop experience 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/e573c197-c476-4e62-9cf9-99431bd7e8fd" />

*ref 10: DC setup (Custom Insatll)*

Select Custom Install and select the disk space that was set at the begining in ref 3.








