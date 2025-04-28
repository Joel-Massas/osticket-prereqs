# os-ticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

This project outlines the full installation and configuration of the open-source help desk ticketing system osTicket on a Windows 10 Virtual Machine.

<h2>Project Highlights</h2>

- Provisioned Azure VMs and configured Windows 10 as a web server.
- Installed and configured all necessary prerequisites (IIS, PHP, MySQL, HeidiSQL).
- Deployed osTicket as a working website accessible via localhost.
- Configured file permissions and security settings post-installation.
- Demonstrated full lifecycle from server setup to application deployment and testing.

---

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- PHP Manager, MySQL, HeidiSQL

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)

---

<h2>Prerequisites Overview</h2>

![image](https://github.com/user-attachments/assets/7b976a77-2c3c-4ce2-bcf8-41a32fa83966)

- Internet Information Services (IIS)
- PHP Manager for IIS
- URL Rewrite Module
- Visual C++ Redistributable
- PHP
- MySQL Database
- HeidiSQL
- osTicket files

---

<h2>Installation and Configuration Steps</h2>

<h3>1. Create Azure Resources</h3>

- Create a Resource Group.
- Create a Windows 10 Virtual Machine with 2 CPUs.
- Allow Azure to automatically create a Virtual Network (VNet).

---

<h3>2. Prepare Windows 10 as a Web Server</h3>

- Install and enable **Internet Information Services (IIS)** and the **IIS Management Console**.

<p align="center">
<img src="https://github.com/user-attachments/assets/ad2d8571-e072-4853-8eb8-2d8913fcf459" alt="Enable IIS"/>
</p>

---

<h3>3. Install Prerequisite Programs</h3>

- Install **PHP Manager** for IIS.
- Install **URL Rewrite** module.
- Install **Visual C++ Redistributable**.
- Install **PHP**:
  - Create directory `C:\PHP`.
  - Extract PHP files into `C:\PHP`.
  - Register PHP within IIS.
  - Restart IIS (stop and start the server).

---

<h3>4. Install and Configure MySQL</h3>

- Perform a typical setup of MySQL.
- Launch MySQL Configuration Wizard:
  - Use **Standard Configuration**.
  - Set a **secret password** for the root account.

- Install **HeidiSQL**:
  - Create a new session.
  - Connect using root/secret password.
  - Create a database named `osTicket`.

---

<h3>5. Install osTicket</h3>

- Download and extract osTicket.
- Copy the "upload" folder contents into `C:\inetpub\wwwroot`.
- Restart IIS.
- Confirm osTicket is accessible:
  - In IIS: Sites ➔ Default Web Site ➔ osTicket ➔ Browse *:80

---

<h3>6. Configure osTicket Features and Permissions</h3>

- Enable the following extensions via PHP Manager:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`

- Rename the configuration file:
  - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

- Assign permissions to `ost-config.php`:
  - Disable inheritance ➔ Remove all existing permissions.
  - Add new permission ➔ Grant "Everyone" full control.

---

<h3>7. Complete osTicket Installation via Browser</h3>

- Access osTicket installation page through your browser.
- Fill out setup information:
  - Helpdesk Name
  - Default System Email (customer-facing)
  - MySQL Database: `osTicket`
  - MySQL Username: `root`
  - MySQL Password: *(secret password)*

- Click "Install Now" to complete installation.

---

<h3>8. Verify osTicket Accessibility</h3>

- Confirm that the following URLs are working:
  - Agent Panel: `http://localhost/osTicket/scp/login.php`
  - End-User Portal: `http://localhost/osTicket/`

---

<h3>9. Post-Installation Security Clean-Up</h3>

- Delete the setup directory:
  - `C:\inetpub\wwwroot\osTicket\setup`
- Change permissions on `ost-config.php` to "Read" only.

---

<h2>Conclusion</h2>

This project showcases the setup of a full-stack help desk system, osTicket, hosted on a custom-configured Windows 10 server in Azure.
The lab emphasizes web server configuration, PHP/MySQL backend setup, application deployment, and post-deployment security hardening — providing real-world experience in server and application administration.
