<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configuring Active Directory Within Azure Virtual Machines </h1>
This tutorial describes the process for deploying and configuring of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="860" height="197" alt="Screenshot 2026-06-26 002735" src="https://github.com/user-attachments/assets/46aadd0e-43fc-4eb9-b859-9373af68e3ff" />

</p>
<p>
Created a virtual network named Active-directory-VNET for Windows 10 Pro virtual machine and Windows Server virtual machine to join to.
</p>
<br />

<p>
<img width="852" height="294" alt="Screenshot 2026-06-25 200319" src="https://github.com/user-attachments/assets/fc629dda-ceb1-411b-bdf0-63f866dacd47" />

</p>
<p>
Created two virtual machines, the Domain controller running Windows Server named dc-1 and Windows 10 Pro named client-1. Both VMs were created under the same virtual network (active-direcotry VNET) and the username is labuser and password is Cyberlab123! for both VMs to login.</p>
<br />

<p>

<img width="1015" height="494" alt="Screenshot 2026-06-25 204147" src="https://github.com/user-attachments/assets/9ed2d075-2c88-47bc-a81e-ef99100dad44" />


</p>
<p>
Set the domain controller's (dc-1) NIC private ip address as static so it wont change because in Azure the default private ip address could change. This will make it so that client-1 is able to use dc-1 as the DNS server.
</p>
<br />

<img width="686" height="467" alt="Screenshot 2026-06-25 204639" src="https://github.com/user-attachments/assets/8e64b100-42d9-4100-98ca-baa1d176c226" />

Set client-1's DNS settings to dc-1's private ip address (10.0.0.4) and this will make client-1 look to dc-1 whenever the computer needs to look up anything like google.com for example and for to be able to locate the domain to be able to join it.

<img width="778" height="247" alt="Screenshot 2026-06-26 003017" src="https://github.com/user-attachments/assets/00965886-e0f2-40d6-988e-19fe201ec80e" />

Login to dc-1 vm and disable windows firewall to test connectivity. Copied its public Ip address to login.

<img width="344" height="74" alt="Screenshot 2026-06-25 222730" src="https://github.com/user-attachments/assets/7f71f318-bd1b-4e42-875b-41b028070a28" />

Used the remote desktop connection application to login and connect to dc-1 virtual machine.

<img width="406" height="247" alt="Screenshot 2026-06-26 003121" src="https://github.com/user-attachments/assets/9c537c99-de4f-4d2e-8be4-0740b9ee48ff" />

Pasted dc-1's public ip address in the box and clicked connect

<img width="450" height="469" alt="Screenshot 2026-06-26 003244" src="https://github.com/user-attachments/assets/8afd7fe2-904a-4efa-b546-d12dd7ab18e6" />

Entered the credentials that were created with the virtual machines (username: labuser Password: Cyberlab123!)

<img width="1366" height="768" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/daa075fa-8f15-4f16-897e-2e5b77bdf209" />

Once logged in, clicked start and searched for Windows Defender Firewall with Advanced Secuirty and opened it. Once open, clicked on Windows defender firewall properties. On Domain profile tab where it says firewall state,selected off and did the same for private profile and public profile tab and then clicked apply and okay.

<img width="1084" height="417" alt="Screenshot 2026-06-25 222623" src="https://github.com/user-attachments/assets/9d623448-7ead-4267-baa8-df3340a0e87a" />

Then logged in to client-1 by copying it's Public IP address and opening the Remote Desketop Conecction application.

<img width="404" height="250" alt="Screenshot 2026-06-26 003426" src="https://github.com/user-attachments/assets/7a7270de-0a30-43ee-a9a6-8afeea1b8433" />

Pasted client-1's Public IP address and clicked connect.

<img width="453" height="465" alt="Screenshot 2026-06-26 003501" src="https://github.com/user-attachments/assets/0923d154-3423-4382-9681-a1929043784b" />

Logged in with the credentials (Username: labuser Password: Cyberlab123!) and clicked okay to connect. Once in, clicked start and typed Powershell and opened it.

<img width="848" height="695" alt="Annotation 2026-06-26 035726" src="https://github.com/user-attachments/assets/b2bc9a6e-337a-4824-b253-732117de59b1" />

In powershell Typed ping 10.0.0.4 which is dc-1's private IP address to test connectivity. The ping succeeded, both virtual machines are on the same virtual network. Typed ipconfig /all and under DNS servers it should show 10.0.0.4 (dc-1's private ip) to make sure client-1 is using dc-1 as the DNS server. If the ping failed it would've said timeout either because both virtual machines aren't on the same virtual network or because Windows Firewall is still on.
