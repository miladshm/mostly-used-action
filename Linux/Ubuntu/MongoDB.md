# Installation and running MongoDB, properly

## Import the public key

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.pub | \
sudo gpg -o /usr/share/keyrings/mongodb-server-6.0.gpg
```
## Add repo

```bash
echo "deb [ arch=amd64,arm64 signed=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

## Install

```bash
sudo apt-get update
sudo apt-get install -y mongodb-org
```

## Run

```bash
sudo chown -R mongodb:mongodb /var/lib/mongodb;
sudo chown mongodb:mongodb /tmp/mongodb-27017.sock;
sudo rm -rf /tmp/mongodb-27017.sock;

sudo systemctl enable mongod;
sudo service mongod start;
sudo service mongod status;
```
