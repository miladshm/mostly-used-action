# Running NodeJs app as systemd service

```systemd
[Unit]
Description=blinkit
Documentation=https://github.com/robb-j/blinkit/
After=network.target

[Service]
Type=simple
User=node
ExecStart=/usr/bin/node /path/to/project/src/index.js
WorkingDirectory=/usr/src/blinkit
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
