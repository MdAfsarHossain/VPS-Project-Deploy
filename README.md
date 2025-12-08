# VPS Project Deploy

## Step-1

First enter VPS IP address

```js
sss root@<ip address>
```

Then enter your password

```js
root@<ip address>'s password:
```

## Step-2

Go to www folder

```js
cd /var/www
```

Check all project

```js
ls;
```

## Step-3

Clone your github project

```js
git clone git@github.com:MdAfsarHossain/VPS-Project-Deploy.git
```

## Step-4

```js
ls;
```

```js
cd vps-project-deploy/
```

```js
npm i
```

```js
npm run build
```

## Step-5

```js
sudo ufw enable
```

```js
sudo ufw status
```

```js
sudo ufw allow 5008
```

```js
sudo ufw status
```

```js
npm run start
```

```js
sudo ufw reload
```

## Step-6

```js
npm i -g pm2
```

```js
pm2 start npm --name "vps-project-deploy" -- start
```

```js
pm2 logs vps-project-deploy
```

```js
pm2 ls
```

# After Successfully Deploy for re-deploy follow this steps:

```js
git pull
```

```js
npm i
```

```js
npm run build
```

```js
pm2 ls
```

```js
pm2 restart <id_no>
```

## Git Switch

```js
git switch afsar/main
```

```js
git pull
```

```js
npm i
```

```js
npm run build
```

```js
pm2 ls
```

```js
pm2 restart <id_no>
```

# For Nginx Setup

```js
sudo apt install nginx -y
```

```js
sudo systemctl enable nginx
```

```js
sudo systemctl start nginx
```

```js
sudo systemctl status nginx
```

```js
sudo rm /etc/nginx/sites-enabled/default
```

```js
sudo rm /etc/nginx/sites-available/default
```

```js
sudo nano /etc/nginx/sites-available/api.voksa.app
```

```js
server {
    listen 80;
    server_name api.voksa.app;

    location / {
        proxy_pass http://localhost:5008;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

}
```

```js
sudo ln -s /etc/nginx/sites-available/api.voksa.app /etc/nginx/sites-enabled/
```

```js
sudo nginx -t
```

```js
sudo systemctl restart nginx
```

```js
sudo apt install certbot python3-certbot-nginx -y
```

```js
sudo certbot --nginx -d api.voksa.app
```

```js
sudo certbot renew --dry-run
```

#### For checking DNS:

```js
https://www.whatsmydns.net/
```

# If face local changes overwritten by merge.

<img src="https://github.com/MdAfsarHossain/VPS-Project-Deploy/blob/main/stash.png" />

```js
git stash
```

```js
git pull
```
