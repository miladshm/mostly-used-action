# Configure phpMyAdmin with Nginx

## Create .conf file

```bash
sudo nano /etc/nginx/snippets/phpmyadmin.conf
```

Add the following to the new file. Make sure you use the correct PHP version;

```nginx
location /phpmyadmin {
    root /usr/share/;
    index index.php index.html index.htm;
    location ~ ^/phpmyadmin/(.+.php)$ {
        try_files $uri =404;
        root /usr/share/;
        fastcgi_pass unix:/run/php/php8.1-fpm.sock; #correct the PHP version
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }

    location ~* ^/phpmyadmin/(.+.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        root /usr/share/;
    }
}
```

Save the file and exit.

Include the new file inside your server block from where you wish to access phpMyAdmin.

```bash
sudo nano /etc/nginx/sites-available/default
```

Edit your server block configuration which will be located inside `/etc/nginx/sites-available` and include the snippet so your configuration looks something similar to the one below.

```nginx
server {
    . . .

    include snippets/phpmyadmin.conf;

    . . .
}
```

Save the file and exit.

```bash
sudo service nginx restart
```
