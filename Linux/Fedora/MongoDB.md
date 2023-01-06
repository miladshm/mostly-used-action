# Installation

[Download](https://www.mongodb.com/try/download/community) and install Community edition

```bash
sudo chown -R mongod:mongod /var/lib/mongo;
sudo chown mongod:mongod /tmp/mongodb-27017.sock;
sudo rm -rf /tmp/mongodb-27017.sock;

sudo systemctl enable mongod;
sudo service mongod start;
sudo service mongod status;
```
