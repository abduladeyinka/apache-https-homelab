# Apache HTTPS Homelab Project

This project documents my hands‑on homelab setup where I deployed a basic website using **Apache**, enabled **HTTPS** with a self‑signed certificate, and managed files between a Linux VM and my Windows host system. The goal of this project is to demonstrate practical skills in Linux administration, web server configuration, SSL/TLS, and Git/GitHub workflow.

---

## 🚀 Project Overview

This homelab project includes:

- Installing and configuring **Apache Web Server** on Ubuntu  
- Creating and deploying a custom `index.html` webpage  
- Generating and enabling a **self‑signed SSL certificate**  
- Configuring Apache for HTTPS  
- Managing file permissions and ownership  
- Transferring files between Linux and Windows using SFTP  
- Publishing the project to **GitHub** for documentation and portfolio use  

---

## 🛠️ Technologies Used

- **Ubuntu Linux**
- **Apache2 Web Server**
- **OpenSSL** (self‑signed certificate)
- **SFTP / FileZilla**
- **Git & GitHub**
- **Windows 10/11 (host system)**

---

## 📂 Project Structure
## 📂 Project Structure

```
apache-https-homelab/
│
├── index.html              # Website homepage
├── configs/                # Apache configuration files
│   ├── 000-default.conf
│   └── default-ssl.conf
├── screenshots/            # Project screenshots (optional)
│   └── *.png
└── README.md               # Project documentation
```

## 📸 Screenshots

---

## 📸 Screenshots

### ✅ Apache Webpage Loaded Over HTTPS
![Apache HTTPS Screenshot](screenshots/apache-https-browser.png)

This shows the webpage hosted on Apache, accessed via `https://10.0.0.38`, with a self-signed certificate triggering the browser warning.

---

### 🧠 Learning Outcomes Displayed on the Page
![Learning Outcomes Screenshot](screenshots/apache-learning-page.png)

The webpage includes a summary of what I learned during the homelab project:
- Apache installation and configuration  
- SFTP file transfer with FileZilla  
- Linux file permissions  
- Hosting a site on a local network  

---

## 🔐 HTTPS Configuration Summary

I generated a self‑signed SSL certificate using:

```bash
sudo openssl req -x509 -nodes -days 365 \
  -newkey rsa:2048 \
  -keyout /etc/ssl/private/apache-selfsigned.key \
  -out /etc/ssl/certs/apache-selfsigned.crt


Then I enabled SSL and the default HTTPS site:

sudo a2enmod ssl
sudo a2ensite default-ssl.conf
sudo systemctl reload apache2

This allowed the site to be served securely over:
 https://10.0.0.38

Then, 	I used FileZilla to transfer  and config files from the VM to Windows and ensured correct permissions using:
sudo chmod 644 index.html
sudo chown www-data:www-data index.html

To verify the setup, I checked the Apache service:
systemctl status apache2

Then, the Http site loaded at:
http://10.0.0.38

Also, i noticed the HTTPS site loaded wih a browser warning using same code line :
https://10.0.0.38

