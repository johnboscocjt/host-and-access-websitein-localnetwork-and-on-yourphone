# host-and-access-websitein-localnetwork-and-on-yourphone

### Documentation: 
"How to run a .php html index file on a local PC and access it from my phone as a live website, or how to host your website locally on a private network."

How to Host a Local PHP Website and Access it on Your Phone
This guide provides step-by-step instructions for hosting a PHP website locally on your PC and accessing it on your phone, both for Windows and Linux (Ubuntu) environments.

### Steps for Windows users.
1. Set Up a Local Server
Install a web server like XAMPP, WAMP, or MAMP.

Install XAMPP:
Download and install XAMPP from apachefriends.org.
During installation, ensure Apache and PHP are selected.

3. Place Your .PHP File
Locate the htdocs directory in the XAMPP installation folder, typically:
C:\xampp\htdocs

Create a new folder for your website, e.g., mywebsite:
C:\xampp\htdocs\mywebsite
Copy your index.php file and other project files into this folder.

5. Start XAMPP
Open the XAMPP Control Panel and start the Apache server.

7. Access Your Website on PC
Open a browser and navigate to:
http://localhost/mywebsite
Your PHP file should render as a webpage.

9. Find Your PC's Local IP Address
Open Command Prompt (Win + R, type cmd, press Enter).
Run the command:
ipconfig
Note the IPv4 Address under your active network connection (e.g., x.x.x.x).

11. Access Your Website from Phone
Connect your phone to the same Wi-Fi network as your PC.
Open a browser on your phone and navigate to:
http://<your-pc-ip-address>/mywebsite

(Replace <your-pc-ip-address> with your IPv4 address).

13. Configure Firewall (if needed)
Allow Apache through Windows Firewall:
Go to Control Panel > Windows Defender Firewall > Allow an app through Firewall.

Find Apache HTTP Server in the list and ensure both Private and Public are checked.

Restart Apache in the XAMPP Control Panel.




### Steps for Linux (Ubuntu) users.
If you're using Ubuntu, here's how to run a .php website on your local PC and access it from your phone:

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
Apache needs proper permissions to read the files.
Change ownership of the files to Apache's user:
```bash
sudo chown -R www-data:www-data /var/www/html/mywebsite  
```
Ensure the files are readable:
```bash
sudo chmod -R 755 /var/www/html/mywebsite  
```

Access Your Website on PC
Open a browser on your PC and navigate to:
http://localhost/mywebsite
Example: http://localhost/databasesite/index1.php

 Find Your PC's Local IP Address
Open a terminal and run:
```bash
ip addr  
```

OR:
```bash
ifconfig  
```

Note: the IPv4 Address, but for internal network.

### Access Your Website from Phone.
Ensure your phone is connected to the same Wi-Fi network as your PC.
Open a browser on your phone and navigate to:
http://<your-pc-ip-address>/mywebsite

(Replace <your-pc-ip-address> with your actual IP).

6. Configure Firewall (if needed)
Allow Apache in the firewall:
Enable Apache in the firewall:
```bash
sudo ufw allow "Apache"  
```
Reload the firewall:
```bash
sudo ufw reload  
```

Test Connectivity
From your phone, you should now be able to view the website.

### Notes and Troubleshooting.
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



### Other.
## note:1
Your correct IP address may look like this -> 10.42.0.1, which is a private IP address, which means it is only accessible within your local network (in this case, your hotspot). To access a website hosted on your PC from your phone, you'll need to ensure that the phone is connected to the same hotspot and that the Apache server is properly configured.

Steps to Access Your Apache Server from Your Phone:
1. Verify Apache is Running: Make sure your Apache server is running on your PC. 
2. Check the Local IP Address: Since you mentioned 10.42.0.1, ensure that this is the correct IP address of your PC when the hotspot is active.
3. Test Locally: Before accessing from your phone, test if you can access the website locally on your PC:

Open a browser on your PC and go to:
http://localhost/databasesite/index1.php

If it works, then proceed to the next step.

4. Connect Your Phone to the Hotspot: Ensure your phone is connected to the hotspot created by your PC.

5. Access from Your Phone: Open a browser on your phone and enter the following URL:
example: http://10.42.0.1/databasesite/index1.php

Important: 10.42.0.1 is the ip of the host pc with the server running the index.php


## note:2
Troubleshooting Access Issues
If you encounter issues accessing the page from your phone, consider the following:

Firewall Settings: Ensure that any firewall on your PC is configured to allow incoming connections on port 80 (HTTP). You can check and adjust firewall settings using:
sudo ufw allow 80/tcp

Apache Configuration: Double-check the Apache configuration to ensure it allows access from the local network. You can follow the steps you provided to verify the configuration and permissions.

Check Apache Logs: If you still can’t access the page, check the Apache error logs for any hints about what might be going wrong:
sudo tail -f /var/log/apache2/error.log

To summarize, your PC's IP address for accessing the web server from your phone is 10.42.0.1 (assuming that's the correct IP for your hotspot). Ensure your phone is connected to the hotspot, and use that IP in the browser. If you encounter any issues, check your Apache server status, firewall settings, and Apache configuration.


## note: 3
# Dont worry if you face the following error on your phone or other device that want to access the hosted website in the local network.
That is your  phone is connected to the pc's hotspot and you typed http://192.168.105.1/dtabasesite/index1.php to the web browser
but it return to you the following:
"requested url was not found on this server.
apache/2.4.58(ubuntu)Server at 192.168.105.1 port 80"

Check Apache Configuration
If the issue persists, verify your Apache configuration:

Open the Apache configuration file:
sudo nano /etc/apache2/apache2.conf

Look for the <Directory "/var/www/html"> block. Ensure it allows access:
<Directory "/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

Also, make sure other directory in /etc/apache2 are also configured to look like the following if the error is persistent:
<Directory />
        Options FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

<Directory /usr/share>
        AllowOverride All
        Require all granted
</Directory>

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

<Directory /srv/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

# This is where you put your files in the apache
<Directory /var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>



# These are examples of blocks that you should create depending on the path of your folder of filename
<Directory /var/www/html/phpdanikrossingjb>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

<Directory /var/www/html/phpdanikrossingjb/databasesite>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

<Directory /var/www/html/phpdanikrossingjb/databasesite/index1.php>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

After all the configurations now;
Save and exit the editor (Ctrl+O, Enter, Ctrl+X).

Restart Apache:
sudo systemctl restart apache2

(Optional) Debug Logs
If it still doesn’t work, check the Apache error logs:
sudo tail -f /var/log/apache2/error.log





### Proudly made by Johnboscocjt
"TanzaniaMadeTechScientist"
"you happen, to make it happen"
"Jesus is the King of all kings..."

















