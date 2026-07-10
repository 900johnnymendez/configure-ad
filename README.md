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
create virtual netowrk.
</p>
<br />

<p>
<img width="852" height="294" alt="Screenshot 2026-06-25 200319" src="https://github.com/user-attachments/assets/fc629dda-ceb1-411b-bdf0-63f866dacd47" />

</p>
<p>
created two virtual machines. Domain controller running windows server named dc-1 and windows 10 pro named client-1. Both VMs were created under the same virtual network (active-direcotry VNET) and both have same login credentials as labuser username and Cyberlab123! as password.</p>
<br />

<p>

<img width="1015" height="494" alt="Screenshot 2026-06-25 204147" src="https://github.com/user-attachments/assets/9ed2d075-2c88-47bc-a81e-ef99100dad44" />


</p>
<p>
Set the domain controller's (dc-1) NIC private ip adress as static so it wont change since in azure the default  private ip adress changes and since its the domain controller its crucial it doesnt change so that client 1 vm can connect to its domain
</p>
<br />

<img width="686" height="467" alt="Screenshot 2026-06-25 204639" src="https://github.com/user-attachments/assets/8e64b100-42d9-4100-98ca-baa1d176c226" />

Set client-1's DNS settings to dc-1's private ip adress (10.0.0.4) and restart client -1 virtual machine to apply the changes

<img width="778" height="247" alt="Screenshot 2026-06-26 003017" src="https://github.com/user-attachments/assets/00965886-e0f2-40d6-988e-19fe201ec80e" />

Login to dc-1 vm and disable windows firewall to test connectivity with its public ip adress. copy the adress.

<img width="344" height="74" alt="Screenshot 2026-06-25 222730" src="https://github.com/user-attachments/assets/7f71f318-bd1b-4e42-875b-41b028070a28" />

To login and connect to dc-1 vm, on ur computer open the remote desktop connection app

<img width="406" height="247" alt="Screenshot 2026-06-26 003121" src="https://github.com/user-attachments/assets/9c537c99-de4f-4d2e-8be4-0740b9ee48ff" />

Paste the dc-1's public ip adress in the box and click connect

<img width="450" height="469" alt="Screenshot 2026-06-26 003244" src="https://github.com/user-attachments/assets/8afd7fe2-904a-4efa-b546-d12dd7ab18e6" />

Enter the credentials that were created with the virtual machines (labuser , Password: Cyberlab123!)

<img width="1366" height="768" alt="Screenshot (3)" src="https://github.com/user-attachments/assets/daa075fa-8f15-4f16-897e-2e5b77bdf209" />

once ur logged in, click start and search for windows defender firewall with advanced secuirty and open it. Once its open, click on Windows defender firewall properties. On Domain profile tab, where it says firewall state, select off and do the same for  private profile tab and public profile tab and then click apply and okay.
