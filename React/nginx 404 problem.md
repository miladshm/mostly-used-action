add this to `.conf` file: 
```
    location / {
     try_files $uri /index.html;
    }
```