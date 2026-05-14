# RHEL & Ubuntu — Website Hosting Project

Save as `apache-rhel.sh`

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl status httpd
cd /var/www/html || exit
sudo chmod 755 /var/www/html
echo "<h1>Website Hosted Successfully on RHEL/Amazon Linux</h1>" | sudo tee index.html
sudo systemctl restart httpd
curl http://localhost
```

# Ubuntu / Debian — Full Website Hosting Script

```bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl status apache2
sudo ufw allow 'Apache'
cd /var/www/html || exit
sudo rm -f index.html
sudo chmod 755 /var/www/html
echo "<h1>Website Hosted Successfully on Ubuntu</h1>" | sudo tee index.html
sudo systemctl restart apache2
curl http://localhost
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
