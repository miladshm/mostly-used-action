# Fix nginx 404 page problem in reactjs websites

add this to `.conf` file:

```nginx
    location / {
     try_files $uri /index.html;
    }
```
