<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
Outline for the prerequisites and installation of the open-source help desk ticketing system osTicket.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- IIS (Internet Information System)
- Microsoft Visual C++ 2015-2022 Redistributable (x86)
- PHP Manager
- My SQL 5.5 Database
- HeidiSQL Client
- osTicket v1.15.8
  <br />
  <br />
  Links to the downloads can be found <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here</a>
  
<h2>‼️ READ ME ‼️</h2>
<strong>✋🏼Before starting it is crucial to follow the steps in order<br /> as any possible errors may lead to having to start over from scratch.</strong>


<h2>Installation Steps</h2>

<strong>Step 1: Creating the Virtual Machine in Azure</strong>
- Create a Windows 10 Virtual Machine with 2 or 4 virtual CPUS
<br />(<strong>Note:</strong> Allow the VM to create a new Vnet which should be done by default)

<p>
Here we create the Virtual Machine, you can have the option to make the resource group or allow it to create one on it's own.
For username I am just using labuser1, and the password can be whatever so long as we remember it.
When it is ready to be created it should look something like in the photos below. Don't forget to click create after reviewing. 
</p>

<p>
<img src="https://i.imgur.com/bAANgTB.jpg" height="60%" width="60%" alt="osTicket Steps"
</p>

<p>
<img src="https://i.imgur.com/4dzDE3D.jpg" height="60%" width="60%" alt="osTicket Steps"
</p>

<br />

<strong>Step 2:</strong> Connect to your new Virtual Machine with Remote Desktop.
<p>(In the search on the task bar type in Remote Desktop Connection and open. You will need the IP address of the VM to connect to it.
Then use the credentials created in Step 1 to log in.)</p>

<br />

<strong>Step 3:</strong> Now that you are inside the VM install/enable IIS in Windows.
<p>Control Center ⇒ Uninstall or change a Program ⇒ Turn Windows features on or off ⇒ Enable Internet Information Systems</p>
(<strong>Note: </strong> expand IIS ⇒ expand World Wide Web Services ⇒ expand Application Development Features ⇒ check CGI

<p>
<img src="https://i.imgur.com/h9jP3Ao.jpg" height="70%" width="70%" alt="Enable IIS"/>
</p>

<br />

<strong>Step 4:</strong> Next it is time to download and install some files from the <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">files</a> provided.<br />
(<strong>Note:</strong> Follow the bullet points below in order for this part.)<br />

- Download & install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Download & install Rewrite Module (rewrite_amd64_en-US.msi)
- Create a new folder in the C: drive called PHP
- Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC-x86.zip) and unzip/extract it into C:\PHP 
- Download & install VC_redist.x86.exe
- Download & install MySQL 5.5.62 (mysql-5.5.62-win32.msi)<br />
(<strong>Note: </strong> for MySQL do Typical Setup ⇒ Launch Configuration Wizard after installation ⇒ check Standard Configuration ⇒ enter Password1 as password)

<p><strong>4.1 (Below) Extraction of PHP 7.3.8 into C:\PHP</strong><br /> <img src="https://i.imgur.com/jIJR2qX.jpg"  height="90%" width="90%" alt="Extraction of PHP"></p>

<br />

<strong>Step 5:</strong> Open IIS as an Admin register PHP from within. Then reload IIS (Stop and Start the server, or Refresh)<br />
Open IIS as Admin ⇒ PHP Manager ⇒ Register new PHP version ⇒ Browse for PHP folder in C: drive ⇒ select php-cgi ⇒ restart server after

<p><img src="https://i.imgur.com/4PorFBr.jpg" height="90%" width="90%" alt="Registering PHP from within"></p>

<br />

<strong>Step 6:</strong> Install osTicket v1.15.8<br />
- Download osTicket from <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">files</a>
- Extract or copy 'upload' folder to C:\inetpub\wwwroot
- Within C:\inetpub\wwwroot -- Rename 'upload' to 'osTicket'
- Restart IIS server
- Go to sites ⇒ Default ⇒ osTicket then on the right click browse *.80<br />

<strong>6.1 (Below) Extraction of upload and rename to osTicket</strong>
<p><img src="https://i.imgur.com/lw0yykp.jpg" height="90%" width="90%" alt="upload extraction and rename"</p><br />

<strong>6.2 (Below) Steps to reach browse *.80</strong>
<p><img src="https://i.imgur.com/IDH9fhY.jpg" height="90%" width="90%" alt="browse *.80"</p><br />

<strong>6.3 (Below) You should get this after clicking browse *.80</strong>
<p><img src="https://i.imgur.com/7vXhF0N.jpg" height="60%" width="60%" alt="osTicket Browser"</p>

<br />

<strong>Step 7:</strong> Enabling PHP extensions for osTicket<br />
- Go to IIS ⇒ sites ⇒ default ⇒ osTicket
- Open PHP Manager
- Click Enable or disable an extension<br />
(Enable: <strong>php_imap.dll</strong>, <strong>php.intl.dll</strong>, <strong>php_opcache.dll</strong>)
- Refresh the osTicket browser<br />

<p><img src="https://i.imgur.com/e6dwsqd.jpg" height="60%" width="60%" alt="php enablers"</p><br />

<strong>(Below) osTicket should now look like this with some changes</strong>
<p><img src="https://i.imgur.com/zdIs9ET.jpg" height="60%" width="60%" alt="osTicket with php enablers"</p>

<br />

<strong>Step 8:</strong> Rename sampleost-config.php & assign permissions
- Go to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
(<strong>Note: </strong>change ost-sampleconfig to ost-config)
