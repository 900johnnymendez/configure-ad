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
Set the domain controllers (dc-1) private ip adress as static so it wont change since in azure the default  private ip adress changes and since its the domain controller its crucial it doesnt change so that client 1 vm can connect to its domain
</p>
<br />
