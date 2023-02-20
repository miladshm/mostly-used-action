# Installation

[Download](https://www.mongodb.com/try/download/community) and install Community edition

```bash
sudo chown -R mongodb:mongodb /var/lib/mongodb;
sudo chown mongodb:mongodb /tmp/mongodb-27017.sock;
sudo rm -rf /tmp/mongodb-27017.sock;

sudo systemctl enable mongod;
sudo service mongod start;
sudo service mongod status;
```
