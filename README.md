# hostandaccesswebsiteinlocalnetwork-and-on-yourphone

Documentation: How to Host a Local PHP Website and Access it on Your Phone
This guide provides step-by-step instructions for hosting a PHP website locally on your PC and accessing it on your phone, both for Windows and Linux (Ubuntu) environments.

Steps for Windows
1. Set Up a Local Server
Install a web server like XAMPP, WAMP, or MAMP.
Install XAMPP:
Download and install XAMPP from apachefriends.org.
During installation, ensure Apache and PHP are selected.
2. Place Your .PHP File
Locate the htdocs directory in the XAMPP installation folder, typically:
C:\xampp\htdocs
Create a new folder for your website, e.g., mywebsite:
C:\xampp\htdocs\mywebsite
Copy your index.php file and other project files into this folder.
3. Start XAMPP
Open the XAMPP Control Panel and start the Apache server.
4. Access Your Website on PC
Open a browser and navigate to:
http://localhost/mywebsite
Your PHP file should render as a webpage.
5. Find Your PC's Local IP Address
Open Command Prompt (Win + R, type cmd, press Enter).
Run the command:
ipconfig
Note the IPv4 Address under your active network connection (e.g., 192.168.x.x).
6. Access Your Website from Phone
Connect your phone to the same Wi-Fi network as your PC.
Open a browser on your phone and navigate to:
http://<your-pc-ip-address>/mywebsite
(Replace <your-pc-ip-address> with your IPv4 address).
7. Configure Firewall (if needed)
Allow Apache through Windows Firewall:
Go to Control Panel > Windows Defender Firewall > Allow an app through Firewall.
Find Apache HTTP Server in the list and ensure both Private and Public are checked.
Restart Apache in the XAMPP Control Panel.
Steps for Linux (Ubuntu)
1. Set Up a Local Server
Install Apache and PHP:
```bash
sudo apt update  
sudo apt install apache2 php libapache2-mod-php
```
Start and enable Apache:
```bash
sudo systemctl start apache2  
sudo systemctl enable apache2  
```
Place Your .PHP File:
Navigate to Apache's document root:
```bash
cd /var/www/html  
```
Create a folder for your website (optional):
```bash
sudo mkdir mywebsite  
```
Copy your files:
```bash
sudo cp /path/to/your/index.php /var/www/html/mywebsite/  
```
Set permissions:
```bash
sudo chown -R www-data:www-data /var/www/html/mywebsite  
sudo chmod -R 755 /var/www/html/mywebsite  
```
Access Your Website on PC
Open a browser on your PC and navigate to:
http://localhost/mywebsite

 Find Your PC's Local IP Address
Open a terminal and run:
```bash
ip addr  
```
OR:
```bash
ifconfig  
```
Note the IPv4 Address, but for internal network.

 Access Your Website from Phone
Ensure your phone is connected to the same Wi-Fi network as your PC.
Open a browser on your phone and navigate to:
http://<your-pc-ip-address>/mywebsite
(Replace <your-pc-ip-address> with your actual IP).
6. Configure Firewall (if needed)
Allow Apache in the firewall:
```bash
sudo ufw allow "Apache"  
sudo ufw reload  
```
Notes and Troubleshooting
Note 1: Using Private IPs
Ensure your phone is connected to the same hotspot or local network as the PC.
Example:
If your PC's IP is 10.42.0.1, access the website on your phone at:
http://10.42.0.1/databasesite/index1.php.

Note 2: Firewall and Apache Configuration
Allow HTTP connections through the firewall:
```bash
sudo ufw allow 80/tcp  
```
Verify Apache permissions:
Open the Apache configuration file:
```bash
sudo nano /etc/apache2/apache2.conf  
```
Ensure the following Directory blocks are present:
```bash
<Directory "/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

Note 3: Handling "URL Not Found" Errors
Ensure the file path in the URL matches the location of your PHP files.
Restart Apache after changes:
```bash
sudo systemctl restart apache2  
```
Check Apache error logs for debugging:
```bash
sudo tail -f /var/log/apache2/error.log  
```



### Proudly made by JohnBoscocjt
"Jesus is the King of all kings..."

















