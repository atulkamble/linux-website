# RHEL / Amazon Linux — Website Hosting

Save as `apache-rhel.sh`

```bash id="f9s3mq"
#!/bin/bash

# -------------------------------------------------
# Apache Website Hosting Setup Script
# For: RHEL / CentOS / Amazon Linux
# -------------------------------------------------

# Update system packages
sudo yum update -y

# Install Apache HTTP Server
sudo yum install httpd -y

# Start Apache service
sudo systemctl start httpd

# Enable Apache on boot
sudo systemctl enable httpd

# Check Apache service status
sudo systemctl status httpd

# Configure firewall (if firewalld is enabled)
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload

# Navigate to web root directory
cd /var/www/html || exit

# Set proper permissions
sudo chmod 755 /var/www/html

# Create sample webpage
echo "<h1>Website Hosted Successfully on RHEL/Amazon Linux</h1>" | sudo tee index.html

# Restart Apache service
sudo systemctl restart httpd

# Test locally
curl http://localhost

echo "-------------------------------------------------"
echo "Apache installation and website setup completed."
echo "Access website using: http://<server-public-ip>"
echo "-------------------------------------------------"
```

## Run the Script

```bash id="5l4s2f"
chmod +x apache-rhel.sh
./apache-rhel.sh
```

---

# Ubuntu / Debian — Full Website Hosting Script

Save as `apache-ubuntu.sh`

```bash id="x8v1pk"
#!/bin/bash

# -------------------------------------------------
# Apache Website Hosting Setup Script
# For: Ubuntu / Debian
# -------------------------------------------------

# Update package repository
sudo apt update -y

# Upgrade installed packages (optional)
sudo apt upgrade -y

# Install Apache HTTP Server
sudo apt install apache2 -y

# Start Apache service
sudo systemctl start apache2

# Enable Apache on boot
sudo systemctl enable apache2

# Check Apache service status
sudo systemctl status apache2

# Configure firewall
sudo ufw allow 'Apache'

# Enable firewall (optional if already enabled)
sudo ufw --force enable

# Navigate to web root directory
cd /var/www/html || exit

# Remove default Apache page
sudo rm -f index.html

# Set proper permissions
sudo chmod 755 /var/www/html

# Create sample webpage
echo "<h1>Website Hosted Successfully on Ubuntu</h1>" | sudo tee index.html

# Restart Apache service
sudo systemctl restart apache2

# Test locally
curl http://localhost

echo "-------------------------------------------------"
echo "Apache installation and website setup completed."
echo "Access website using: http://<server-public-ip>"
echo "-------------------------------------------------"
```

## Run the Script

```bash id="2zq7hy"
chmod +x apache-ubuntu.sh
./apache-ubuntu.sh
```

---

# Verify Website

Open browser:

```text id="tncllm"
http://<server-public-ip>
```

Example:

```text id="5kxyjk"
http://13.233.120.10
```

Expected Output:

```html id="ghot8z"
<h1>Website Hosted Successfully</h1>
```
