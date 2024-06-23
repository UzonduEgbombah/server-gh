#### COMMANDS

Instance freetier <t2.micro> 22.04/ *20.04* is outdated

- To install Nginx

```sh
sudo apt update -y
sudo apt install nginx -y
```

- To check the status of the Nginx run

```sh
sudo systemctl status nginx
```

- To access Nginx in ubuntu

```sh
curl http://127.0.0.1:80
```

- Installing MySQL

```sh
sudo apt install mysql-server -y
```

- To enter MySQL

```sh
sudo mysql
```

- To install php-fpm and php-mysql

```sh
sudo apt install php-fpm php-mysql -y
```

- To create web directory for *your_domain* 

```sh
sudo mkdir /var/www/projectLEMP
```

- To assign ownership to the directory run

```sh
sudo chown -R $USER:$USER /var/www/projectLEMP
```

- To open new config file in Nginx sites-available directory

```sh
sudo nano /etc/nginx/sites-available/projectLEMP
```

add this file

```sh
server {
    listen 80;
    server_name projectLEMP www.projectLEMP;

    root /var/www/projectLEMP;
    index index.html index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}
```

- Enable the configuration:

Create a symbolic link to sites-enabled:

```sh
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
```

- Test the configuration:

Run the following command to check for syntax errors:

```sh
sudo nginx -t
```

trouble shoot

ls -l /etc/nginx/sites-enabled/

sudo rm /etc/nginx/sites-enabled/example.com


- Unlink the nginx conf

```sh
sudo unlink /etc/nginx/sites-enabled/default
```

Reload Nginx to apply changes

```sh
sudo systemctl reload nginx
```

- For index.html File

```sh
sudo sh -c "echo 'Hello LEMP from hostname $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) with public IP $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)' > /var/www/projectLEMP/index.html"
```

Test php with nginx

```sh
sudo nano /var/www/projectLEMP/info.php
```

input this

```sh
<?php
phpinfo();
?>
```


![](https://github.com/UzonduEgbombah/server-gh/assets/137091610/f6c390d3-a554-42c7-bf97-11e0e36bd736)


Remove with the command

```sh
sudo rm /var/www/projectLEMP/info.php
```

#### steps

```sh
sudo mysql
```

create database

```sh
CREATE DATABASE 'example_database';
```

create new user

```sh
CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
```

give user permission

```sh
GRANT ALL ON 'example_database.* TO 'example_user'@'%';
```

exit

























