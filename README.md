# Network Scanner & Firewall Protection Project 🚀

{{toc}}

## 1. Introduction

The objective of this project is to create a server environment that scans the network to which we are connected and provides a detailed view through a PHP web interface, while ensuring network protection via the firewall. This project requires knowledge of the Linux environment, commands, and the Linux interface.

### 1.1 Objective

* Host a *web interface* with real-time network scanning 🌐
* Automate periodic *network scans* using *cron jobs* 🕒
* Use *UFW firewall* for secure connections 🔐
* Provide detailed *network* and *device details* along with potential risks 🚨

### 1.2 Tools and Technologies

|Tool|Description|Icon|
|---|---|---|
|Apache2|To build a secure, efficient, and extensible HTTP server|🌐|
|PHP|Server-side scripting for dynamic content generation|🖥️|
|Nmap|Network scanning tool to identify devices and open ports|🔍|
|Cron Jobs|Automate the periodic Nmap scans|⏰|
|UFW|Uncomplicated Firewall for managing secure network traffic|🔒|

### 1.3 System Requirements

* *Operating System:* Ubuntu 20.04 LTS or higher 🖥️
* *Hardware:* VirtualBox running Ubuntu or a Linux server 💻
* *Software Requirements:*
** Apache2 Web Server
** PHP 7.4 or higher
** Nmap tool
** Cron for scheduling tasks
** UFW for firewall management

## 2. Installation Guide

### 2.1 Checking IP Address

Before starting, check your IP address:

<pre>
ip a
</pre>

### 2.2 Installing Apache2 Web Server

Update system:
<pre>
sudo apt-get update && sudo apt-get upgrade
</pre>

Install Apache2:
<pre>
sudo apt-get install apache2
</pre>

Check status:
<pre>
sudo systemctl status apache2
</pre>

### 2.3 Installing PHP

Install PHP and verify version:
<pre>
sudo apt-get install php
php --version
</pre>

### 2.4 Installing Nmap

Install Nmap and verify:
<pre>
sudo apt-get install nmap
nmap --version
</pre>

## 3. Cron Jobs Configuration

### 3.1 Setting Up Automated Scans

Edit crontab:
<pre>
sudo crontab -e
</pre>

Add scan schedule (every 10 minutes):
<pre>
*/10 * * * * nmap 192.168.1.0/24 -oN /var/www/html/nmap.html
</pre>

## 4. Web Interface Setup

### 4.1 Creating PHP Interface

Navigate to web directory and create file:
<pre>
cd /var/www/html
sudo nano network.php
</pre>

### 4.2 PHP Script Template

<pre>
<?php
echo "Current Time: " . date("h:i:sa");
include("nmap.html");
?>
</pre>

## 5. Firewall (UFW) Configuration

### 5.1 Installation

Install UFW:
<pre>
sudo apt-get install ufw
</pre>

### 5.2 Basic Configuration

Set up essential rules:
<pre>
sudo ufw allow 22/tcp    # SSH
sudo ufw allow 80/tcp    # HTTP
sudo ufw allow 443/tcp   # HTTPS
</pre>

### 5.3 Default Policies

Configure default policies:
<pre>
sudo ufw default deny incoming
sudo ufw default allow outgoing
</pre>

### 5.4 Activation

Enable and verify UFW:
<pre>
sudo ufw enable
sudo ufw status
</pre>

## 6. Accessing the Interface

Access the network scanner interface:
<pre>
http://<server-ip>/network.php
</pre>

Example:
<pre>
http://192.168.1.102/network.php
</pre>

## Implementation Checklist ✅

|Task|Status|Notes|
|---|---|---|
|Apache Installation|[ ]|Required for web interface|
|PHP Setup|[ ]|Needed for dynamic content|
|Nmap Installation|[ ]|Core scanning functionality|
|Cron Job Configuration|[ ]|For automated scanning|
|UFW Setup|[ ]|Security implementation|
|Web Interface Creation|[ ]|Final user interface|

## Troubleshooting Guide

|Issue|Solution|Priority|
|---|---|---|
|Apache not starting|Check system logs with @sudo systemctl status apache2@|High|
|Nmap scan failing|Verify network connectivity and permissions|High|
|UFW blocking access|Review firewall rules with @sudo ufw status@|Medium|
|PHP errors|Check error logs in @/var/log/apache2/error.log@|Medium|

## Notes and References

* Remember to regularly update system packages
* Keep UFW rules minimalistic for better security
* Monitor scan results for any suspicious activities
* Backup configuration files before making changes

## Project Status: 🎉 Completed Successfully!

[Download Project Files](https://github.com/your-repo-link)
[Report Issues](https://github.com/your-repo-link/issues)
