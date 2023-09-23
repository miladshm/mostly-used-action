````nginx
upstream backend {
  server localhost:8080;
}

upstream websocket {
  server localhost:8081;
}

server {
  listen 80;
  server_name api.ex.com
  location / {
    # add_header 'Access-Control-Allow-Origin' '*';
    proxy_pass http://backend;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    client_max_body_size 10g;
  }

  location /socket.io {
    # add_header 'Access-Control-Allow-Origin' '*';
    proxy_pass http://websocket;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    client_max_body_size 10g;
  }

  location /robots.txt {
    return 200 'User-agent: *\nDisallow: /';
  }
}
````
