# Windows File Sharing & Access Control Using Active Directory (Azure)
<p align="center">
<img src="https://imgur.com/oNr4Sqk.png" alt="osTicket logo"/>
</p>

<h1></h1>
This tutorial creates a multi-user network file access system using Active Directory and security groups to manage user permissions across a Windows Server domain environment in Azure. It demonstrates how to:
</p>

- Configure and share folders on a domain controller
- Create and manage security groups in Active Directory
- Set file level access (read, write, deny) for users and groups
- Test access using standard domain users from a domain-joined client

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Windows Machine
- Domain Controller

<h2> Skills Used </h2>

- Azure
- Windows Server
- ADUC 
- File Sharing
- Group Management
- Troubleshooting Permissions


</p>
<br />
<h2>Create File Shares With Various Permissions</h2>
</p>
<br />
<img src="https://imgur.com/RS4g3vK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
1. Go to portal azure and use RDP to connect to the Domain Controller ( DC)! Log into DC with your admin account (MyDomain.com/jane_admin)
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/cm3QHkg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
2. Log into Client 1 as a normal user.
To do that pick a user from the domain from server manager>adminastrstive tools> Active DIrectory Users and Computers file>my domain.com> employees 
and the list to the right should populate. Choose a random one and RDP to client 1 with mydomain.com/username
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/4leHHpe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
3a.On DC on the C:\ drive, create 4 folders with text documents in them: "Read access", "Write Access" "No access" and "Accounting". They are just names for the 
files, they have no permissions applied to them yet. Go to file explorer and click on this PC then click on the C drive. Right click
under other folders new>folder and create those 4 folders. 
</p>
<br /> 

3b. To create the file documents just open the folders. ThisPC>C: Drive> "Read Access" Folder> within the white spacee> new> Text File. Write anything in there for the lab and save the file. Repeat the process for the other 2 folders.
</p>
<br />
</p>
<br />
4a. Next we will set the following permissions for the "Domain Users" Group:
</p>
<br />
</p>
<br />
<img src="https://imgur.com/3ttGgGA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
4b. The "Read Access" folder will only have reading access available for Domain Users. To do that go to DC's C drive. Right click on "read access" folder>go to properties>sharing and click share button.
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/2W16743.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
It'll open a seperate page that'll prompt you to write a name (write whom the folder will be shrared with) which will be "domain users". Click add and it'll pop up on the list below and to the right it has permission level which will be "read" and then click share at the bottom.

</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/ZbFPaIO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
4c. Folder "Write access" will give "Domain Users" Permsissions to "Read/Write". Right click folder>properities>share> add domain users to the list and on permission level select read/write. 
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/mvSAuJo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
4d. Folder "No access" will give the  Group "Domain ADMINS" Permissions to "Read/Write". Open folder properties, go to share and type in domain admins when prompted. Add to the list and change permissions to read/write and share. Normal users have no access to this! 

In enterprise environments, NTFS permissions are also configured under the 'Security' tab to fine-tune access control. We will touch upon that after the next section!

Skip the accouting folder for now.


<h2> Accessing Files as a Domain User </h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/a4l1on5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
5. Next you will attempt to access file shares as a normal user. On client 1 (logged on as a domain user) navigate to shared folder. Go to file explorer and paste \\dc-1 in the search bar. Then you'll see all the folders shared on the domain.
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/uGmwBKR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

6a. Try to access the folders you made, which can you access and which folders can you create stuff in?
The no access shouldn't be able to be opened and read you can read but not edit and read/write you could do both.
</p>
<br />
</p>
<br />
<h2>Creating Security Groups</h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/ZWdTtbm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>
<img src="https://imgur.com/XxyV5zf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
7a. Go to DC in AD and create an OU named "security groups". Go to active directory users and computers> right click my domain>new> organzational unit, click on that and name it "Security Group". Right click my domain again and refresh! 
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/7HuF53x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/NJciIgd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
7b. On the security folder right click go to new>group click that and name new group ACCOUNTANTS and group type will be security! and click ok! By using security groups, access can be controlled at scale. It's best practice in any org above 5 users.

<h2>Accessing Files as a Domain User </h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/5DOFZPQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
8. On the DC's C Drive in the accounting folder, set the following permissions, 'read and write'. Right click on the accouting folder> properties> sharing tab> click share. 
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/ux7pZlT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
8b. In the text box add "accountants", select their permission as read/write  then click share.  
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/s2zMIXs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
9. Search //dc-1 in file explorer on client-1 as a domain user to see files shared. Click on the accounting folder and you shouldn't be able to open it!
</p>
<br />
<h2>Adding Users to Security Groups  </h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/IG9XsOk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
10a. Next you will add that domain user to the accountant group so they can access file.
On the DC make this user member of the accountants security group.
On DC, head to active directory users and computers> my domain.com> security groups> Accountants
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/hpYceqs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
10b. Right click the accountant folder> "Members" tab> add button
In object name type the user's username and click apply>ok.
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/wYofGVv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
11. Log out User in CLient-1 to reset computer and add new permissions. Log  in again as that user. you can hold windows key and R simultaneously to go directly to file explorer. type \\DC-1 and
go directly to shared files on domain! You can now access the accountant folder
</p>
<br />
Network shares and security groups can add another level of customization when it comes to users' access on a network. You now have some permissions set on your files!




