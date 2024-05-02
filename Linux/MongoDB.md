# Installation

[Download](https://www.mongodb.com/try/download/community) and install Community edition

## OR add Mongodb Repository

```bash
sudo nano /etc/yum.repos.d/mongodb-org-6.0.repo
```

```
[mongodb-org-6.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/6.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-6.0.asc
```

install it with dnf

```bash
sudo dnf install mongodb-org
```

#Configuration
```bash
sudo chown -R mongod:mongod /var/lib/mongo;
sudo chown mongod:mongod /tmp/mongodb-27017.sock;
sudo rm -rf /tmp/mongodb-27017.sock;

sudo systemctl enable mongod;
sudo service mongod start;
sudo service mongod status;
```
