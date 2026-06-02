# Apache2 Installation & Configuration

## 1. Overview

This document explains how to install Apache2, create a simple website, and expose it using a VirtualHost configuration.

---

## 2. Prerequisites

Install Apache2 on your machine:

```bash id="a1b2c3"
sudo apt update
sudo apt install apache2
```

---

## 3. Installation Verification

Check that Apache is running:

```bash id="d4e5f6"
sudo systemctl status apache2
```

Then retrieve your machine IP address:

```bash id="g7h8i9"
ip a
```

Access the server in a browser:

```text id="j1k2l3"
http://<your-ip-address>
```

---

## 4. Website Creation

Create the website directory:

```bash id="m4n5o6"
sudo mkdir /var/www/home-security-lab
cd /var/www/home-security-lab
```

Create the homepage file:

```bash id="p7q8r9"
sudo vim index.html
```

HTML content:

```html id="s1t2u3"
<html>
<head>
    <title>Home Security Lab</title>
</head>
<body>
    <p><b>Welcome to Home Security Lab!</b></p>
</body>
</html>
```

---

## 5. VirtualHost Configuration

Go to Apache configuration directory:

```bash id="v4w5x6"
cd /etc/apache2/sites-available/
```

Copy the default configuration:

```bash id="y7z8a9"
sudo cp 000-default.conf home-security-lab.conf
```

Edit the configuration file:

```bash id="b1c2d3"
sudo vim home-security-lab.conf
```

Update the following values:

```apache id="e4f5g6"
ServerAdmin bhatoo.hakeem@outlook.fr
DocumentRoot /var/www/home-security-lab
ServerName home-security-lab.com
```

---

## 6. Enable the VirtualHost

Enable the site:

```bash id="h7i8j9"
sudo a2ensite home-security-lab.conf
```

Reload Apache:

```bash id="k1l2m3"
sudo systemctl reload apache2
```

---

## 7. Hosts Configuration

Edit the hosts file:

```bash id="n4o5p6"
sudo vim /etc/hosts
```

Add the following line:

```text id="q7r8s9"
127.0.0.1 home-security-lab.com
```

---

## 8. Final Verification

Open a browser and go to:

```text id="t1u2v3"
http://home-security-lab.com
```

If the setup is correct, the “Home Security Lab” page will be displayed.

---

## 9. Resource

* https://ubuntu.com/tutorials/install-and-configure-apache#1-overview
