To Deploy Angular Application on nginx server 

To deploy an Angular application on an Nginx server, you'll need to follow these general steps: 
setting up your environment, building your Angular application, installing and configuring Nginx, and finally deploying the application. Here’s a detailed guide:

Environment Setup 
Install Dependencies :

Install Node.js and npm

Ensure that Node.js and npm (Node Package Manager) are installed on your server. These are required for building Angular applications.

Install Node.js:

```bash
sudo apt update
sudo apt install nodejs
``` 
Install npm:

```bash
  sudo apt install npm
``` 
Verify the installations:

```bash
node -v
npm -v
``` 
Install angular cli 
```bash
sudo npm install -g @angular/cli
``` 
To check the version of aws cli, enter the below command 
```bash
ng version
``` 
![Screenshot 2024-07-17 231323](https://github.com/user-attachments/assets/cb1f2461-cb8e-4a71-a099-6c1bac8e367b)

Now clone the project into opt directory
```bash
git clone https://github.com/ndommetidivi/Angular_1.git
``` 
![Screenshot 2024-07-17 225133](https://github.com/user-attachments/assets/382830eb-cc96-493c-8c1f-4f926d7d0fd6)

```bash
cd /opt/Angular_1
``` 
Build the Project for Production:
```bash
ng build
``` 
This command generates a dist folder with your production build, typically named dist/Angular_1.

Configure Nginx
Install Nginx:
```bash
sudo apt install -y nginx
``` 
 You are able to see the page in browser like this if nginx installation done successfully:

 ![Screenshot 2024-07-31 003621](https://github.com/user-attachments/assets/c989c5fe-2b79-4461-b215-dc63248ec2b6)

sudo /etc/nginx/sites-available/default 
```
server {
        listen 80;
        listen [::]:80;

        root /var/www/your_domain/html;
        index index.html index.htm index.nginx-debian.html;

        server_name your_domain www.your_domain;

        location / {
                try_files $uri $uri/ =404;
        }
}
``` 
Replace yourdomain.com with your actual domain name or IP address.

Now copy the dist file into this path 
```
sudo cp -r dist/* /var/www/html/
``` 
Give the suitable permissions to it.
```
sudo chown -R www-data:www-data /var/www/html/
``` 
Now change the directory into /var/www/html/ by using the command given below : 
```
 cd /var/www/html/
``` 
Now Enable the Configuration:

```
vi /etc/nginx/sites-available/default
``` 
Test Nginx Configuration:
```bash
     sudo nginx -t
``` 
Restart the nginx server
```
systemctl restart nginx
``` 
Start Nginx

Your Angular application should now be accessible via your domain name or server IP address.

![Screenshot 2024-07-18 001810](https://github.com/user-attachments/assets/dd6063a2-cbf3-4aaa-b9de-2448c8342f1d)





