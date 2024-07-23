Angular Application Deployment on NGINX Server
This README file provides instructions for deploying an Angular application on an NGINX server.

Prerequisites
An Ubuntu server
sudo privileges
An Angular application built for production
Step 1: Install NGINX
 Update the Package Index
bash
Copy code
sudo apt update
 Install NGINX
bash
Copy code
sudo apt install nginx -y
 Start and Enable NGINX
bash
Copy code
sudo systemctl start nginx
sudo systemctl enable nginx
 Verify NGINX Installation
Open your web browser and navigate to your server's IP address. You should see the NGINX welcome page.

Step 2: Build Your Angular Application
 Navigate to Your Angular Project Directory
bash
Copy code
cd /path/to/your/angular-project
Build the Angular Application for Production
bash
Copy code
ng build 
This will create a dist directory with your production-ready application.

Step 3: Configure NGINX
 Remove the Default NGINX Configuration
bash
Copy code
sudo rm /etc/nginx/sites-enabled/default
 Create a New NGINX Configuration File
bash
Copy code
sudo nano /etc/nginx/sites-available/angular-app
Add the following content:

bash
Copy code
server {
    listen 80;
    server_name your_server_domain_or_IP;

    root /var/www/angular-app;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
3.3 Create a Symbolic Link to Enable the New Configuration
bash
Copy code
sudo ln -s /etc/nginx/sites-available/angular-app /etc/nginx/sites-enabled/
 Test the NGINX Configuration
bash
Copy code
sudo nginx -t
Reload NGINX
bash
Copy code
sudo systemctl reload nginx
Step 4: Deploy Your Angular Application
 Create a Directory for Your Application
bash
Copy code
sudo mkdir -p /var/www/angular-app
 Copy the Build Files to the New Directory
bash
Copy code
sudo cp -r /path/to/your/angular-project/dist/* /var/www/angular-app/
 Set Permissions
bash
Copy code
sudo chown -R www-data:www-data /var/www/angular-app
Step 5: Access Your Application
Open your web browser and navigate to your server's IP address or domain. You should see your Angular application.

