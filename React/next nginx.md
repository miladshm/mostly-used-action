```nginx
server {
        server_name www.DOMAINNAME.com DOMAINNAME.com;

        index index.html index.htm;
        root /home/ubuntu/PROJECT_FOLDER; #Make sure your using the full path

        # Serve any static assets with NGINX
        location /_next/static {
            alias /home/ubuntu/PROJECT_FOLDER/.next/static;
            add_header Cache-Control "public, max-age=3600, immutable";
        }

        location / {
            try_files $uri.html $uri/index.html # only serve html files from this dir
            @public
            @nextjs;
            add_header Cache-Control "public, max-age=3600";
        }

        location @public {
            add_header Cache-Control "public, max-age=3600";
        }

        location @nextjs {
            # reverse proxy for next server
            proxy_pass http://localhost:8080; #Don't forget to update your port number
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }

        listen 80 default_server;
        listen [::]:80;
}
```
