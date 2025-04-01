<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Curating Users, using Group policy and Managing Accounts</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Active Directory Users and Computers(ADUC)

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2> Set up </h2>
To create users for our domain we need to make sure that users in the domain are able to connect to RDP(remote desktop protocol). First we are going to log into CLient-1 under our admin account Not_spiderman. Open system properties, click remote desktop and allow domain users to acces RDP.

![a1](https://github.com/user-attachments/assets/5cae0676-d3ca-4486-8620-ea2611952ab8)
![ade1](https://github.com/user-attachments/assets/b738e3d6-855f-47af-ac11-0ed9ef9a1e84)
![ade3](https://github.com/user-attachments/assets/cb49230f-875a-4d0a-86f8-6b68fd4817ba)

<h2> Creating Users </h2>

Now that we have the set up done lets creat those users. First lets log into DC-1 and open powershell_ise as administrator. Go to new script and paste the [script](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) I chose to do 10 employees for this lab and kept the password the same. Go under ADUC go to _EMPLOYEES and you can see the random ones that were made. Choose one of them to log into Client-1 to make sure it works.

![ade4](https://github.com/user-attachments/assets/5e76d72e-5158-4805-9ee2-e78872c213c1)
![a5](https://github.com/user-attachments/assets/2d3e4d7f-f8af-4788-b0dd-e5811bcdfa5f)
![a6](https://github.com/user-attachments/assets/d600d0b8-7755-4613-9e47-5383ae751ee7)
![a7](https://github.com/user-attachments/assets/0b76e7d1-22db-4165-bdc8-b55ebb32c812)

![a8](https://github.com/user-attachments/assets/ae4f9b43-7136-4715-bd78-8a755e8f2308)

![a9](https://github.com/user-attachments/assets/dcbf54b1-5ff2-4303-a3d6-ed71df57bca0)

<h2> Group Policy and Account Managment</h2>

 To practice with group policy we are going to set a new group policy and intentionally lock one of our employees out and set reset/ unlock there account. First log into DC-1 and open run, and enter gpmc.msc. This should open the group policy management console then open until you get to Default Domain Policy then right click it and click edit. Once you get to the Domain Policy Management Editor go to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.
Then click Account Lockout THreshold and set it to 5. Once youve applied the policy open client one to force it with your admin account in Command prompt use gpupdate /force. Now try to log in 6 times with one of your employee accounts and enter the wrong password 6 times. Then head back into DC-1 and go to ADUC and click the users go to the user thats locked out double click go to the account tab and unlock Account and try to log in after it should work. Now we are going to  disable the same account and try to log in and re enable and log in. 










