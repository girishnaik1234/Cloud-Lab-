sudo dnf update -y
sudo dnf install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

sudo systemctl status httpd

cd /var/www/html
sudo nano index.html
