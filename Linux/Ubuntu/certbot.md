# certbot

## installation

```shell
sudo apt install certbot python3-certbot-nginx
```

## Obtaining an SSL Certificate

```
sudo certbot --nginx -d [example.com] -d [www.example.com]
```

```
Output
Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel):
```

## Verifying Certbot Auto-Renewal

```
sudo systemctl status certbot.timer
```

To test the renewal process, you can do a dry run with certbot:

```
sudo certbot renew --dry-run
```
