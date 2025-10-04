# Active-Directory-Home-Lab-

## Objective
The objective for this home lab is to simulate a corporate network as well as manage the tasks that one might face while working in and IT environment. This home lab looks at alot of thing such as virtualisation, networking, Scripting, user access control and Troubleshooting. 

### Skills Learned
- using Virtualisation and Containerisation
- setting up devices on a Network and joining them together
- setting up User Accounts with different Privileges
- creating User Accounts using Powershell for Automation
- diverting Internet Traffic from one Domain Controller to a Private Network
- Designing a Network
- Troubleshooting 

### Tools Used
- Virtual Box
- Windows Server 2022
- Windows 10
- Active Directory
- Powershell
- DHCP
- Remote Services
- Command Prompt



## Steps
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1c6e0827-4d6f-47a5-b1b4-495019655910" />

*Ref 1: Network Diagram*

Here is the Network Diagram on how the home lab will be set up. This consists of two virtual machines: one running the Windows 2022 Server, which will act as the Domain Controller (DC), and the other running Windows 10, which will serve as the client. The DC will also consist of the following services: Domain/Active Directory Domain Services (AD DS), Remote Access Services/Network Address Translation (RAS/NAT), and a Dynamic Host Configuration Protocol service (DHCP) where the DC will define the scope of the client machines that join the domain. For this home lab to run smoothly, ensure virtualization is enabled in the BIOS of the system running this lab.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/80ddeadc-e68a-4f76-a6f1-ac6f2ef27dae" />

*Ref 2: Virtual Box tool bar*

Once Virtual Box is installed, the DC and client machines will need to be set up. This can be done by visiting <a href="https://www.virtualbox.org/wiki/Downloads"> The Oracle VirtualBox website</a> and installing the correct host. The DC will be set up first, and the client machine will be set up later. By selecting "New," we can set up a new virtual machine.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/d5eb369e-5e43-4ba0-b1eb-3237e0d3ed8d" />

*Ref 3: Virtual Machine Setup (ISO & Hardware)*

In order to create the DC virtual machine, the ISO image for the  <a href="https://info.microsoft.com/ww-landing-windows-server-2022.html"> Windows 2022 Server </a>   will be needed. Once the ISO is acquired, it is also important to tick the "Skip Unattended Installation" box. If this is kept unchecked, the virtual machine will install the command line interface version of the server. Then set the memory and number of cores according to the system running this lab.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f258cb4a-5d90-4759-87a8-5346db45e48a" />

*Ref 4: Virtual Machine Setup (Hard Disk)*

Here one can set the storage for the hard disk and then click "Finish."

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/b1d0288e-3981-4558-921e-6c6db5b739f3" />

*Ref 5: Virtual Machine Settings*

Before starting the machine, there are a few configurations that are required.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/9586991e-9531-4224-aa23-d2f262544836" />

*Ref 6: Virtual Machine Settings (Biredirectional)*

This will enable us to drag and drop items from the physical machine to the virtual machine and escape the virtual machine without having to use the host key.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/c863dd2f-650f-4a01-81cd-c7b4edae3d43" />

*Ref 7: Virtual Machine Settings (Network)*

Here, the network settings are being configured to match the network diagram in Ref 1. Adapter 1 is attached to the NAT by default, which is the Internet (blue cloud). Adapter 2 needs to be attached to the internal network as shown in Ref 6. Once done, click "OK" and start the virtual machine.. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1e59d079-5517-41ef-968f-b063688bc3ad" />

*Ref 8: Virtual Machine running*

Here, the Windows Server 2022 DC machine is running. The next step is to follow the setup.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/aa6f3518-5b7d-4d05-b343-31f4a2109bd0" />

*Ref 9: DC Setup*

Hint: Install now :)

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/d561646d-e471-4e35-bb3d-89a78ec09f3b" />

*ref 10: DC Standard Evaulation Desktop experience*

Select the standard evaulation desktop experience.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/e573c197-c476-4e62-9cf9-99431bd7e8fd" />

*ref 11: DC setup (Custom Install)*

Select "Custom Install" and select the disk space that was set at the beginning in Ref 3 and click "Next." Here, the server should begin installing.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/dede46e5-4ce3-4502-ae68-542d9365acf6" />

*ref 12: inital Setup Page*

Once Windows 2022 Server has been installed and has been rebooted for the first time, we will be presented with this page where we can set a password and then proceed to log in.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/64c91a7b-0091-46e8-a466-4e4f4213dda9" />

*ref 13: Window Server 2022 Successfully Installed*

Here, the Windows server (DC) has successfully been installed.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/9e43bef9-846f-49d2-834d-7c18ae396db8" />

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/8951736d-52d8-4100-a607-e2edc5720636" />

*ref 14: Changing the Names of the Adpaters Inside the DC Virtual Machine.*

Here, I changed the names of the adapters by using the Run command "ncpa.cpl" and then right-clicking each adapter to change the name to match the network diagram in Ref 1.

<img width="1022" height="768" alt="image" src="https://github.com/user-attachments/assets/98303bae-a6ea-4d28-959c-231ae164e5da" />

*Ref 15: Network Configurations for the Internal Network*

I then clicked on the internal network adapter ("Adapter 2") and then selected the IPv4 setting as I needed to set the network configurations according to the network diagram in Ref 1. Here, I manually set the IP address to "172.15.0.1," the Mask to "255.255.255.0," and the gateway is empty as the DC (Windows Server 2022) is going to act as the default gateway. It has two network interface cards, one facing the internet (Adapter 1) and the other facing internally (Adapter 2). I then used the loopback address "127.0.0.1" as the Domain Name Server because once Active Directory is installed, it automatically installs DNS with it, meaning this DC will use itself as a DNS.

<img width="1030" height="770" alt="image" src="https://github.com/user-attachments/assets/bcb136f3-6b23-4f8f-8f74-cf4598d15fff" />

*Ref 16: Changing the System Name of the Domain Controller*

Here I changed the system name to the DC to keep track of things 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/24126261-22b4-4422-a6c4-ca138595d287" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/6e884a57-4ae0-4314-b33c-8a51f7468d09" />

*ref 17: Installing AD DS using Server Manager*

To begin installing Active Directory Domain Services using the Server Manager, we need to add Active Directory through the "Add Roles and Features" option. I then selected the DC server and proceeded to select the Active Directory Domain Services. Then I continued and clicked "Next" until I installed AD DS.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/0b532c21-883e-4d5e-a9f0-452749aeee79" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/2be90a18-baec-4f84-9d7d-f1ef751a7ac5" />

*ref 18: Deploying a Domain for Active Directory*

I then had to promote the Windows Server to a Domain Controller and clicked "Next" until I got to the Domain Controller Options and created a password before installing. As this is a fresh Domain Controller, I made sure to add a new forest, as this DC will act as the root level. Once this was done, the server then restarted

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/e859d092-5415-4cc2-ac0a-c370acfd6642" />

*ref 19 : DC login page after Restart and Server Manager page*

As you can see, our domain appears on the login page, meaning Active Directory and Domain Services have been successfully configured. This also shows up on the Server Manager dashboard.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/710f847c-aef0-48cc-af3f-0d91d252811b" />
      
*ref 20: Active Driectory Users and Computers*

The next stage was to add another user; this specifically is another Domain admin account. To do this, I navigated to the Active Directory Users and Computers program from the Start menu. I then right-clicked on the domain "ezeworker.com," went to New -> Organizational Unit, and added a group called "_ADMINS."

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f2f799af-1600-4b4f-9eac-744a9bbd725f" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/f6306985-61a3-4629-a049-69a3f48b9b7a" />

*Ref 21: AD DS Domain User Account Creation*

Here, I created a Domain admin account and then logged into that account to ensure it was working. Because it is a lab environment, things like the password never expiring are tolerated. In a production environment, this would not be checked.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/4e5a11dd-3860-476d-a138-7fac5fc7280b" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/1946b2f1-bb56-4c07-9ac1-2eae17bb21e1" />

*Ref 22: Installing RAS/NAT*

The next stage is to install RAS/NAT services on the Domain Controller so we can divert internet traffic from the Domain Controller to the client machine (Windows 10) while the client machine is still on a private network. This can be done by adding another role and then selecting Remote Access. I then ensured routing was checked and installed it successfully. Immediately after, I began to configure the service.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/22cde060-2307-4bf6-a51c-8bda7e33f4b1" />

*Ref 23: Configuring RAS with NAT*

In the configuration tab, I chose the NAT option, meaning all clients will be able to access the internet through the DC IP address. I then had to choose the internet adapter "Adapter 1," as this is connected to the internet, to complete the configurations.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/a92d21b8-77e2-4a14-8098-6148643041b6" />

*Ref 24: Windows 10 (Client 1 Virtual Machine)*

Following the exact same steps from Ref 1 to Ref 12, I then installed Windows 10. The only difference here is that the Windows 10 ISO setup asked for personal details and more information about the device. Here, I mostly set everything to limited mode for the purpose of the lab.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/fb5133f3-7100-4dd4-8b9a-fb073d4d15e8" />

*Ref 25: Installing DHCP*

The next step was to install DHCP this will be used to automatically assign our client machine an ip address. 

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/a0fd1aa9-7305-4f0a-bf5b-7488447f9f0a" />

*Ref 26: DHCP configurations*

I had already completed this, but I had to define my scope, which was "172.15.0.100-172.15.0.200," and a prefix of 24. I did not add any exclusions or delays. I kept the lease duration for 8 days before the client IP changes. I then added the default gateway and my domain name "ezeworker.com," keeping everything else blank.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/2d78eae7-4c3c-42b4-950f-6c245db29f21" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/3d978473-31cb-44ca-b42f-1e593b3fe669" />


*Ref 27: Active Directory user account creation using powershell*

I then ran a script on the DC virtual machine to create 1000 users for Active Directory.

<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/5aad4def-d94b-4f88-b31b-108a3e2b2271" />
<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/730b0274-00fb-4e8c-8963-95b9ca72d023" />


*Ref 28: DHCP Address leases*

Here, I checked the DHCP address lease after logging into the client machine. In Ref 27, the DHCP had automatically assigned the client machine an IP address within the specified scope. This means the DHCP has been configured properly. On the client machine, I ran the "ipconfig /all" command in the command prompt. I found that the DHCP is the same as the default gateway, which aligns with the network diagram in Ref 1, and our DNS name is listed there.


<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/d83daace-4b4e-41b7-a15f-b46b0e6271ac" />
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/998cc8ba-e163-42aa-9ba8-13e6ec463262" />

*Ref 29: Joining the domain on client machine*

I then changed the Windows 10 virtual machine (Client) name to "Client" from the original host name and joined the domain at the same time using the credentials of the Domain Admin that I created earlier in Active Directory, which successfully joined the domain.


<img width="720" height="720" alt="image" src="https://github.com/user-attachments/assets/c005cf90-9c4a-4b91-afe6-4082f793ff2b" />

The final step of the lab was to check that a normal user account on the client machine was working, as the client machine had successfully joined the domain.
