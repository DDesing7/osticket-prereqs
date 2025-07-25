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

- Create an Azure Virtual Machine Windows 10, 4 vCPUs
- download the osTicket-Installation-Files.zip
- Install / Enable IIS in Windows WITH CGI

<h2>Installation Steps</h2>

- install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- install the Rewrite Module (rewrite_amd64_en-US.msi) 
- Create the directory C:\PHP
- unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
- install VC_redist.x86.exe
- install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  > Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Username: root Password: root
- Open IIS as an Admin
- Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
- Reload IIS
- From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
  > Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
- Reload IIS
- Go to sites -> Default -> osTicket -> On the right, click “Browse *:80”
- Go back to IIS, sites -> Default -> osTicket -> Double-click PHP Manager -> Click “Enable or disable an extension”
  > Enable: php_imap.dll -> Enable: php_intl.dll -> Enable: php_opcache.dll -> refresh OSTicket and observe changes
- Rename: "C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php" To: "C:\inetpub\wwwroot\osTicket\include\ost-config.php"
- Assign Permissions: ost-config.php
  > Disable inheritance -> Remove All -> New Permissions -> Everyone -> All
- Continue Setting up osTicket in the browser (click Continue)
  > Name Helpdesk -> Default email (receives email from customers)
- From the “osTicket-Installation-Files” folder, install HeidiSQL.
  > Open Heidi SQL -> Create a new session, root/root -> Connect to the session -> Create a database called “osTicket”
- Continue Setting up osTicket in the browser
  > MySQL Database: osTicket -> MySQL Username: root -> MySQL Password: root -> Click “Install Now!”
- Browse to your help desk login page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/ 
