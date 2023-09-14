<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Files</h2>

https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h1>Installation Steps</h1>


<h3>Step 1: Creating a Virtual machine</h3>
• To begin, our first task is to set up a Virtual Machine (VM) through the Microsoft Azure portal. 
A VM acts as a remote computer, and we use it to safeguard our physical 
machine from potential issues. Start by creating a resource group, and for simplicity, let's name it "osTicket."
</p>
<br />

![VM creation](https://github.com/jordonporter/osticket-prereqs/assets/144548453/7fffa98c-070b-40d0-bc59-79f054d27a71)
</p>
<br />


• Next, simply connect to your newly created VM using RDP using the public IPv4 address. 
If you are a Mac user you will have to download Microsoft RDP.
</p>
<br />

![remote desktop sign-in](https://github.com/jordonporter/osticket-prereqs/assets/144548453/ebaf5920-f808-47a5-8060-8e7ca4343ebd)
![userlab](https://github.com/jordonporter/osticket-prereqs/assets/144548453/c03d28ec-fe07-4b50-bda3-b4f87555fbd0)
</p>
<br />

<h3>Step 2: Enable IIS on Windows </h3>
• Navigate to the "Control Panel" and then select "Programs" followed by "Programs and Features."
Choose "Turn Windows features on or off" on the left side.
• In the pop-up window, check the box for "Internet Information Services." 
</p>
• Check the box for Web Management Tools -> IIS Management Console -> IIS Management Console
</p>
• Check the box for World Wide Web Services -> Application Development Features -> CGI
</p>
• Check the box for "Common HTTP Features"
</p>
<br />

![control panel](https://github.com/jordonporter/osticket-prereqs/assets/144548453/f5204b83-bbfc-4bac-b162-6fe6b5757870)
![Capture](https://github.com/jordonporter/osticket-prereqs/assets/144548453/009ea6d6-5aa7-44cb-b704-f63f69f026a8)
![Capt6ure](https://github.com/jordonporter/osticket-prereqs/assets/144548453/34123663-af74-41d3-9a5f-a861b7c80dc3)
</p>
<br />

<h3>Step 3: Install the PHP Manager for IIS</h3>
• From the Installation Files, download and install the PHP Manager installer from the downloads link (PHPManagerForIIS_V1.5.0.msi)
</p>

![Installing PHP manager](https://github.com/jordonporter/osticket-prereqs/assets/144548453/503037bc-77f4-40e4-9a60-9d18697b67b7)
</p>
<br />

<h3>Step 4: Install the Rewrite Module </h3>
• From the Installation Files, download and install the PHP Manager installer from the downloads link (rewrite_amd64_en-US.msi)
</p>

![Installing rewrite module](https://github.com/jordonporter/osticket-prereqs/assets/144548453/a7835b19-f10b-4940-af3a-9b4f5027516c)
</p>
<br />


<h3>Step 5: Create C:\PHP directory and download PHP 7.3.8</h3>
• Locate your VM's C: Drive and create a new folder "PHP". Then from the installation files, download PHP 7.3.8
(php-7.3.8-nts-Win32-VC15-x86.zip) and extract the contents into the PHP directory folder you just created.
</p>

![creating PHP folder in C Drive](https://github.com/jordonporter/osticket-prereqs/assets/144548453/b084617d-8a75-4a1f-8040-337ff4d9cbf2)
![extracting PGP 7 3 8 into PHP folder](https://github.com/jordonporter/osticket-prereqs/assets/144548453/053da23c-4db1-42cc-a158-35367a28b67b)
</p>
<br />

<h3>Step 8: Install MySQL 5.5.62</h3>
• From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
</p>
• Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Password1 (create a password)
</p>

![MYSQL Standard config](https://github.com/jordonporter/osticket-prereqs/assets/144548453/5a1f62ef-c3fa-4e44-a644-21291f3da3ad)
![MYSQL install typical](https://github.com/jordonporter/osticket-prereqs/assets/144548453/0258945c-8af6-468c-8429-2cabbb6204aa)
![MySQL install as Windows service](https://github.com/jordonporter/osticket-prereqs/assets/144548453/ac716c48-2ebd-44a9-abfd-f880ab2dbbfb)
![MYSQL root password](https://github.com/jordonporter/osticket-prereqs/assets/144548453/bf2a6196-3ca9-4b3f-b761-550aa1f18289)
</p>
<br />

<h3>Step 9: Register PHP from within IIS</h3>
• Open IIS as an Admin and double-click on PHP Manager. Then click "Register new PHP version" and locate the PHP folder you created on your 
C: Drive, select "php-cgi", then click open and OK.
<p>

![phpcgi](https://github.com/jordonporter/osticket-prereqs/assets/144548453/a6114e2e-f23d-422e-8e26-14e660581dec)
</p>
</p>
<br />

<h3>Step 10: Reload IIS</h3>
• Click on the name of the server on the left and click "restart" on the top right. 
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/9531ecd8-4b20-4fb6-a4c8-aadcf3ea452d)
</p>
<br />

<h3>Step 11: Install osTicket v1.15.8</h3>
• Click the link within the lab files to download osTicket.
 Once downloaded to your "Downloads" folder, right-click the folder and choose "Extract All" to create another folder.
 Inside the "Downloads" folder, open the osTicket folder.
 Copy the "upload" folder.
Navigate to "This PC," "Windows (C:)," "inetpub," and "wwwroot," then paste the "upload" folder here.
Rename the "upload" folder to "osTicket."
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/8b6e0b81-049e-4953-8a96-86883edec3f8)
![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/a318f7b0-953b-41e9-bc7c-66e1dad7b369)
</p>
<br />

<h3>Step 12: Reload IIS</h3>
• Open IIS by searching for it in the Start menu.
On the right side, click "Restart."
On the left side, click "Sites," "Default Web Site," "osTicket," then on the right side, click "Browse *:80" to open a web browser to osTicket.

</p>  

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/5d6d2ea2-a83a-48ba-94e9-9b01faa9a14c)
</p>
<br />

<h3>Step 13: Enable Extensions in IIS</h3>
• Open IIS Manager again.
Navigate to "Sites," "Default," "osTicket."
Double-click on "PHP Manager" and then click "Enable or Disable an Extension."
Enable the following extensions: "php_imap.dll," "php_intl.dll," and "php_opcache.dll."
Refresh the osTicket site in your browser.
</p>

![IIS extensions](https://github.com/jordonporter/osticket-prereqs/assets/144548453/822fc838-f630-4cd7-8f82-5283c38cf88a)
</p>
<br />

<h3>Step 14: Rename ost-config.php</h3>
• In File Explorer, go back to the osTicket folder.
Click on the "Include" folder.
Rename "ost-sampleconfig.php" to "ost-config.php." Be precise to avoid errors.
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/a716289a-355d-4fdb-81f7-afe724c5e5cc)
</p>
<br />

<h3>Step 15: Assign Permissions to ost-config.php</h3>
• Right-click on ost-config.php and go to "Properties."
Navigate to "Security," "Advanced," and then "Disable Inheritance."
Click "Add" to add custom permissions.
Click "Select Principal," type in "Everyone," and then click "Check Names" and "Ok."
Allow "Full Control."
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/335d91a3-1d57-4e13-8d7c-4bea3bc90a98)
![giving ost-config permissions 2](https://github.com/jordonporter/osticket-prereqs/assets/144548453/4b7661f6-4030-4aef-819e-c20daf015705)
</p>
<br />

<h3>Step 16: Download and Install HeidiSQL</h3>
• Download HeidiSQL from the provided installation files.
Open the downloaded file from your "Downloads" folder and complete the installation.
In HeidiSQL, click "New," enter the MySQL password you created at the beginning of this lab, and open the connection.
Create a new database called "osTicket."
In the osTicket browser interface, enter the MySQL database information (named "osTicket"), MySQL Username (set as "root" at the beginning of the lab), and the password you created.
Click "Install Now," and osTicket should now be successfully installed.
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/36b4284a-5042-4896-b5df-a3124e57946f)
![heidisql new session](https://github.com/jordonporter/osticket-prereqs/assets/144548453/0a945c6a-bac2-43b8-bdb7-5f6ce40c5970)
</p>
<br />

<h3>Step 17: Create an osTicket Database</h3>
• Right-click anywhere under the database filter, click on "Create a new database" and name it "osTicket."
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/a8d719c6-3485-464a-8ad9-85e23ae77ff1)


<h3>Step 18: Continue Setting up osTicket in the browser</h3>
• In the osTicket browser, enter the MySQL database information (named "osTicket"), MySQL Username (set as "root" at the beginning of the lab), and the password you created.
Click "Install Now," and osTicket should now be successfully installed.
</p>

![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/b1d592d7-99ad-4d9f-98fa-34a69e73861b)
![image](https://github.com/jordonporter/osticket-prereqs/assets/144548453/2e0f4d2e-5a58-4986-9850-84a4bfcb8279)

<h2> That completes the pre configuration of osTicket! </h2>





