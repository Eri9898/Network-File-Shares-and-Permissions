# Network File Shares and Permissions
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket -Ticket Life Cycle</h1>
This tutorial outlines how to create file shares, security groups and configuring permissions for files and users.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Windows Machine
- DOmain Controller

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
-windows server 2022

<h2>Create File Shares With Various Permissions</h2>

</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/RS4g3vK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
1. Go to portal azure and use RDP to connect to DC! Log into DC w your admin account (MyDomain.com/jane_admin)
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/cm3QHkg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
2. Log into CLient 1 as a normal user.
Pick a user from the domain from  server manager>adminastrstive tools> Active DIrectory Users and Coimputers file>my domain.com> employees 
and the list to the right should populate. Choose a random one and RDP to client 1 with mydomain.com/username
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/4leHHpe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
3.On DC on the C:\ drive, create 4 folders: "Read access", "Write Access" "No access" and "Accounting". They are just names for the 
files, they have no permissions applied to them yet. Go to file explorer and click on this PC then click on the C drive. Right click
under other folders new>folder and create those 4 folders. 
</p>
<br /> 

4a. Next we will set the following permissions for the "Domain Users" Group:

</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/3ttGgGA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
4b. The "Read Access" folder will only have reading access available for Domain Users.To do that go to DC. Right click on "read access" folder>go to properties>sharing and click share button.
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
4d. Folder "No access" will give the  Group "Domain ADMINS" Permissions to "Read/Write". Open folder properties, go to share and type in domain admins when prompted. Add to the list and change permissions to read/write and share.Normal users have no access to this!

Skip the accouting folder for now.


<h2>Accessing Files as a Domain User</h2>
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
</p>
<br />
<img src="https://imgur.com/eCZKtRo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
6b. *On DC-1 as an admin, create a file within "read access" folder so that on client 1 you can try to edit the text file and observe. So on file explorer go to ThisPC>C: Drive> "Read Access" Folder> within the white spacee> new> Text File. Write anything in there for the lab and save the file.

Try to access the file via Client 1. You shoulde be able to read the file but not add any files or edit any documents. 


<h2>Creating Security Groups</h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/XxyV5zf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/></p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/ZWdTtbm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
7a. Go to DC in AD and create an OU named "security groups" "Accountants". Go to active directory users and computers> right click my domain>new> organzational unit, click on that and name it "Security Group". Right click my domain again and refresh! 
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
7b. Go to security groups to the right, right click go to new>group click that and name new group ACCOUNTANTS and griup type will be security! and click ok!)


<h2>Accessing Files as a Domain User cnt'd </h2>
</p>
<br />
</p>
<br />
</p>
<br />
<img src="https://imgur.com/5DOFZPQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
8. On the accounting folder set the following permissions, 'read and write'. Right click on the accouting folder> properties> sharing tab> click share. 
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
10b. Right click the accountant folder> Members" tab> add button
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




