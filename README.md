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

*ref 10: DC setup (Custom Install)*

Select Custom Install and select the disk space that was set at the begining in ref 3 and click next here the server should begin installing.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/dede46e5-4ce3-4502-ae68-542d9365acf6" />

*ref 11: inital setup page*

Once Windows 2022 Server has been installed and has been rebooted for the first time we wil be presented with this page were we can set a password and then proceed to login.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/64c91a7b-0091-46e8-a466-4e4f4213dda9" />

*ref 12: Window Server 2022 successfully installed*

Here the windows server (DC) has successfully been installed

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/9e43bef9-846f-49d2-834d-7c18ae396db8" />

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/8951736d-52d8-4100-a607-e2edc5720636" />

*ref 13: Changing the names of the adpater inside the DC virtual machine.*

Here I changed the names of the adapters by using the run command "ncpa.cpl" and then right clicking each adapter to changne the name to match the network diagarm in ref 1 

<img width="1022" height="768" alt="image" src="https://github.com/user-attachments/assets/98303bae-a6ea-4d28-959c-231ae164e5da" />

*Ref 14: Network Configurations for the internal network*

I then clicked on the Internal network adapter ("adapter 2") and then selcted the IPv4 setting as I needed to set the network configurations to the one on the network diagram in ref 1. Here i mannualy set the ip address: "172.15.0.1" , the Mask:255.255.255.0, The gateway whihc is empty as the DC (WIndows Server 2022) is going to act as a default gateway it has to network interface cards one facing the internet "adapter 1" and the other facing internally "adapter 2". I then used the loopback address: 127.0.0.1 as the Domain Name Server because once active directory is installed it automatically installs a DNS with it meaning this DC will use its iself as a DNS.

<img width="1030" height="770" alt="image" src="https://github.com/user-attachments/assets/bcb136f3-6b23-4f8f-8f74-cf4598d15fff" />

*Ref 15: Changing the system name*

Here I changed the system name to the DC to keep track of things 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/24126261-22b4-4422-a6c4-ca138595d287" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/6e884a57-4ae0-4314-b33c-8a51f7468d09" />

*ref 16: Installing AD DS using server manager*

To begin installing Active directory domain services using the Server Manager we need to add active directory through the "Add roles and features"  option. I then selected the DC server and procced to select the Active Directory Domain Services. Then continued clicked next until I installed AD DS.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/0b532c21-883e-4d5e-a9f0-452749aeee79" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/2be90a18-baec-4f84-9d7d-f1ef751a7ac5" />

*ref 17: Deploying a domain for Active Directory*

I then had to promote the Windows Server into a Domain Controller and clicked next till I got to the Domain Controller Options and created a password before installing. As this is a fresh Domain controller I made sure the add a new forest was created as this DC will act as the root level. Once this was done the server then restarted.   

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/e859d092-5415-4cc2-ac0a-c370acfd6642" />

*ref 18 : DC login page after restart and Server Manager page*

AS you can see our domain comes up in the login page meaning Active Directory and Domain Services has been sucessfully configured. This is also shows up on the Server manager Dashboard.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/710f847c-aef0-48cc-af3f-0d91d252811b" />
      
*ref 19: Active Driectory users and computers*

Then next stage was to add another user this specifaclly is another Domain admin account. To do this i navigated to the active directory users and computers progarm from the start menu. I then right clicked on the domain "ezeworker.com" then went to new->organisational Unit and added a group called "_ADMINS"

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f2f799af-1600-4b4f-9eac-744a9bbd725f" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f6306985-61a3-4629-a049-69a3f48b9b7a" />

*Ref 20: AD DS Domain User account creation*

Here I created a Domain admin account and then logged into that account to ensure it was working. Because it is a lab environment things like the password never expiring are tolerated. In a production environment this would not be ticked. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/4e5a11dd-3860-476d-a138-7fac5fc7280b" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1946b2f1-bb56-4c07-9ac1-2eae17bb21e1" />

*Ref 21: Installing RAS/NAT*

The next stage is to install RAS/NAT services on the domain controller so we can divert the internet traffic from the domain controller to the client machine (Windows 10) while the client machine is still on a private network. This can be done by adding another role and then selecting the Remote Access. I then ensured routing was ticked and installed it succesfully. Straight after i began to configure the service.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/22cde060-2307-4bf6-a51c-8bda7e33f4b1" />

*Ref 22: Configuring RAS with NAT*

In the configuration tab I choose the NAT option meaning all clients will be able to access the internet through the DC ip address. I then had to choose the internet adapter "adpater 1" as this is connected to the internet to complete the configurations.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/a92d21b8-77e2-4a14-8098-6148643041b6" />

*Ref 23: Windows 10 (Client 1 Virtual machine)*

Following the exact same steps from ref 1 to ref 12 . I then installed windows 10 the only diffrence here is windows 10 ISO setup asked for personal details and more information about the device. Here i mostly put everything in limited mode for the purpose of the Lab. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/fb5133f3-7100-4dd4-8b9a-fb073d4d15e8" />

*Ref 24: Installing DHCP*

The next step was to install DHCP this will be used to automatically assign our client machine a ip address when they join the domain. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/a0fd1aa9-7305-4f0a-bf5b-7488447f9f0a" />

*Ref 25: DCHP configurations*

I have already completed this but i had to define my scope which was "172.15.0.100-172.15.0.200" and a prefix of 24. I did not add any exclusions and delays. I kept the lease duration for 8 days before the client ip changes. I then added the default gateway and my domain name "ezeworker.com" and kept everything else blank.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/2d78eae7-4c3c-42b4-950f-6c245db29f21" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/3d978473-31cb-44ca-b42f-1e593b3fe669" />


*Ref 26: Active Directory user account creation using powershell*

I then ran a script on the DC virtual machine to create 1000 Active Directory.

