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

- Item 1. Create Resource Groups and Virtual Machines. 
- Item 2. Install/Enable Internet Information Services ( IIS ).
- Item 3. Download and Install PHP Manager for IIS.
- Item 4. Download and Install URL Rewrite Module.
- Item 5. Create Directory C:\PHP.
- Item 6. Download and Install PHP 7.3.8 and unzip the contents into C:\PHP.
- Item 7. Download and Install VC_redist.x86.exe.
- Item 8. Download and Install MySQL 5.5.62
- Item 9. Register PHP from within IIS
- Item 10. Download and Install osTicket v1.15.8
- Item 11. Download and Install Heidi SQL
- Item 12. Enable Extensions and Configure osTicket settings.

<h2>Installation Steps</h2>

Step 1: Crate a Resource Group in Azure.

    Open a web browser and navigate to the Azure portal.
    Sign in with your Azure account credentials.
    
![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/f1111462-6a76-45f8-946a-1b6bd1a07987)

Create a Resource Group using the step-by-step tutorial on [Creating Resource Group within Azure](https://github.com/John-Duria/Azure---Resource-Group) on my repository.

Step 2: Create a Windows 10 Virtual Machine with 2-4 Virtual CPUs
   
    Navigate to Virtual Machines:
        Click on "Virtual machines" in the left-hand menu.
        Or Search for Virtual Machine from the Search menu above.
    Click "+ Create" to create a new virtual machine.
    Configure the following settings:
        Subscription: Choose your Azure subscription.
        Resource group: Select the resource group created in Step 1.
        Region: Choose the same region as the resource group.
        Image: Select a Windows 10 image from the list (e.g., Windows 10 Pro).
        Size: Choose a VM size with 2-4 virtual CPUs (e.g., Standard_DS2_v2 or Standard_DS3_v2).
        Username: Enter a username for the VM administrator.
        Password: Enter a strong password for the administrator account.
        Virtual network: Select Create new to create a new Virtual Network (VNet).
        Subnet: Enter a name for the new subnet (e.g., DefaultSubnet).
    
    Review and Create: 
        Click Review + create to review the VM configuration.
        Review the virtual machine configuration details.
        Click Create to provision the Windows 10 VM.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/50d476ee-a1db-4dde-a1d8-7322933fbb40)

Part 2 (Installation)

Open this: Installation Files
We will use these files to install osTicket and some of the dependencies. I’m using this offline version to make sure everyone is using the same version of all the files :)

Remote Desktop Connection:
Launch Remote Desktop on your local machine.
Enter the Public IP address of your Windows 10 VM.
Enter the username and password configured during VM setup to log in.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/87c6d8cb-792c-4090-84a5-68fbb4177f75)

Install IIS (Internet Information Services) with CGI and Common HTTP Features
•	Launch Control Panel on your Windows VM.
•	Click on Programs.
•	On Programs and Features click on Turn Windowns features on of off.
•	Choose the Internet Information Services (IIS ).
•	Select Services as the role to install.
•	In the features section, ensure to select the following:
o	CGI
o	All Common HTTP Features
o	IIS Management Console
•	Click OK.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/152f9487-de4a-4568-a0ab-29c746d2b5cb)

Check IIS Installation
•	Open a web browser on your Windows Server.
•	Navigate to http://127.0.0.1 or http://localhost.
•	Ensure the IIS default page loads successfully.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/fd423d6b-fd18-4235-9e63-36db1d777cab)

Install PHP Manager for IIS and URL Rewrite Module
•	Download and install PHP Manager for IIS and URL Rewrite Module from your installation files.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/7d98db84-9476-44b1-8896-845360362b03)

Install PHP
•	Create a directory C:\PHP.
•	Download PHP 7.3.8 (or your preferred version) from the installation files (php-7.3.8-nts-Win32-VC15-x86.zip).
•	Extract the contents of the PHP zip file into C:\PHP.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/87a42dea-2c5e-4013-b06c-445c5d5d2130)

Install Microsoft Visual C++
•Download and install VC_redist.x86.exe from your installation files.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/68b480d1-3cb0-4088-bcdd-e034a49fe61e)

Install MySQL
•	Download and install MySQL 5.5.62 from your installation files (mysql-5.5.62-win32.msi).
•	During installation:
o	Choose Typical Setup.
o	Launch the Configuration Wizard after installation.
o	Select Standard Configuration.
o	Select Install As Windows Service and leave the service name as MySQL.
o	Set the root password to Password1.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/5cdcf660-1caf-4004-91e9-d04805d51af6)

Register PHP with IIS
•	Open IIS Manager as an administrator.
•	Navigate to PHP Manager.
•	Specify the PHP executable path (C:\PHP\php-cgi.exe).
•	Click Apply to register PHP with IIS.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/9c1e2e77-cd4b-4ed6-9693-1a109aab510b)

Click on the name of the server in IIS and click restart on right-hand side.

7. Install osTicket
•	Download osTicket from the installation files.
•	Extract the contents and copy the upload folder to C:\inetpub\wwwroot.
•	Rename the upload folder to osTicket.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/72d3f928-656b-4d80-a98a-0441d3772f79)

Note that some extensions are not enabled

Configure PHP Extensions
•	Open IIS Manager.
•	Navigate to your osTicket site under Sites.
•	Double-click PHP Manager.
•	Click Enable or disable an extension.
•	Enable the following PHP extensions:
o	php_imap.dll
o	php_intl.dll
o	php_opcache.dll
  Refresh the osTicket site in your browse, observe the changes

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/96bf33f9-3141-4f1e-a030-567da1d5f9a9)

. Rename ost-config.php
•	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
•	To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/75e68221-aa94-4aa4-a5bb-91cfa9f096e4)

Set Permissions for ost-config.php
•	Disable inheritance for ost-config.php and remove all existing permissions.
•	Add a new permission entry for Everyone with Full Control.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/47c1a2f0-053e-4adb-a181-3726bf7bb35a)

Continue osTicket Setup in Browser
•	Open your web browser and navigate to http://localhost/osTicket.
•	Click Continue to proceed with the osTicket setup.
•	Enter the required information:
o	Helpdesk name
o	Default email (for receiving customer emails)

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/aa0f0167-dae9-4ead-8ff2-cd400cfcb77f)

Download and install HeidiSQL from the Installation Files.
•	Open Heidi SQL
•	Create a new session, root/Password1
•	Connect to the session
•	Create a database called “osTicket”

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/29df6a12-1008-46dc-86e6-87b57844d128)

Continue Setting up osticket in the browser
•	MySQL Database: osTicket
•	MySQL Username: root
•	MySQL Password: Password1

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/0724adf9-f532-42ce-927f-c4b279762c70)
•	Click Install Now to complete the setup.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/9f404174-39f7-4538-9cfa-ba8602597962)

Access osTicket Help Desk
•	Browse to your osTicket help desk login page: http://localhost/osTicket/scp/login.php.
•	Access the end-user osTicket URL: http://localhost/osTicket/.

Clean Up
•	Delete the setup directory from C:\inetpub\wwwroot\osTicket.
•	Set permissions for ost-config.php to Read Only.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/eb13a73a-4ed3-4cd5-b999-c5abe50a4c6b)

Verify Username and Password works.
•	Browse to your osTicket help desk login page: http://localhost/osTicket/scp/login.php.

![image](https://github.com/John-Duria/osticket-prereqs/assets/168502429/1e71c331-8e68-4053-a302-3b5d389dc257)

