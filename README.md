# Deloy-VueJs-app-using-Nginx
## 📌Install Node.js version 18.3 or higher
### Step 1 - Add NodeSource PPA
```
curl -s https://deb.nodesource.com/setup_18.x | sudo bash
```
### Step 2 - Install NodeJS 18
```
sudo apt install nodejs -y
```
### Step 3 - Confirm the installed version of NodeJS
```
node -v
```
## 📌VueJS project setup
```
npm install
```
### Compiles and minifies for production
```
npm run build
```
### Compiles and hot-reloads for development
```
npm run serve
```
## 📌Run VueJS project with Nginx
### Step 0 - Move the todolist project to the /var/www directory
```
mv todolist /var/www
```
### Step 1 – Installing Nginx
```
sudo apt update
sudo apt install nginx
```
### Step 2 – Adjusting the Firewall
```
sudo ufw allow 'Nginx HTTP'
```
### Step 3: Start NGINX
```
systemctl status nginx
```
```
sudo systemctl start nginx
```
### Step 4: NGINX Configuration
```
touch /etc/nginx/conf.d/todolist.conf
```
### Step 5: Write the content of the todolist.conf
```
server {
    listen      80;
    server_name your_domain_or_ip;
    charset utf-8;
    root    /var/www/todolist/dist;
    index   index.html;
    #Always serve index.html for any request
    location / {
        root /var/www/todolist/dist;
        try_files $uri  /index.html;
    }
    error_log  /var/log/nginx/vue-app-error.log;
    access_log /var/log/nginx/vue-app-access.log;
}
```
### Step 6 - Reload NGINX and test
```
sudo systemctl restart nginx
```
Open your browser and check your awesome Vue.js app.
