# HTTPD Configuration Linux-Server-Management ( Configure by Sajan Kumar Tak )
This repository contains - **HTTPD Configuration**: Installing and configuring Apache HTTP Server for hosting websites. documentation and configuration files for setting up various server services on CentOS machines. Whether you're a beginner or just looking for a reference, you'll find step-by-step guides and configuration examples here.

# Steps by Step Follow  

# First of all Install HTTPD Webserver Package
sudo yum -y install httpd

# Start & Enabled httpd webserver Service
sudo systemctl enable --now httpd

# Create website directory inside document root with document root permission and navigating in this directory for Virtual Host
sudo mkdir -p /var/www/html/website
sudo cd /var/www/html/website

# paste code inside document root ,im creating my own code named index.html
sudo vim index.html
<center><h1> Hello Guys im Sajan Kumar Tak</h1></center>
<center><h2> This is my HTTPD Webserver Working So Smoothly</h2></center>
:wq!

# Create a new configuration file for your virtual host
sudo vim /etc/httpd/conf.d/mywebsite.conf
<virtualhost *:80>
ServerName www.sajan.shop.com
DocumentRoot /var/www/html/website
<directory /var/www/html/website>
require all granted
</directory>
</virtualhost>
:wq!

# Restart httpd service
sudo systemctl restart httpd

# if you have configure Custom dns for www.sajan.shop.com then its work on publicly,otherwise you need to map your domain with machine ip in /etc/hosts..
sudo vim /etc/hosts
<yours_ip> www.sajan.shop.com
:wq!
bash

# Restart httpd service
sudo systemctl restart httpd

# im using AWS so dont we need to managment firewalld, im aws we need to create Security Group with inbound or outbound rules and Allow http service or 80 port.

# Checking Internally : 
sudo curl www.sajan.shop.com

# Checking Externally: ( if you dont have configure own dnd for your domain then you will access wbesite by public ip )
# go to browzer
http://<public_ip>


## Feedback
If you have any feedback, questions, or suggestions, please feel free to open an issue or contact us.
Happy server configuring!
