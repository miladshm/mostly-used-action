# PostgreSQL

## Server

### Installation

The installation and initialization of the postgresql server is a little bit different in comparison to other packages and other Linux distros. This document aims to summarize basic installation steps relevant to recent Fedora Linux releases.

```bash
    sudo dnf install postgresql-server postgresql-contrib
```

#### Run by default

The postgresql server is not running and disabled by default. To set it to start at boot, run:

```bash
    sudo systemctl enable postgresql
```

#### Populating initial DB

The database needs to be populated with initial data after installation. The database initialization could be done using following command. It creates the configuration files postgresql.conf and pg_hba.conf

```bash
    sudo postgresql-setup --initdb --unit postgresql
```

#### Start server manually

To start the postgresql server manually, run:

```bash
    sudo systemctl start postgresql
```

####

## phpPgAdmin

### Installation

The installation of the postgresql GUI web-server is a little bit different in comparison to older Fedora because the package is out of the repo.

1. We assume you have php installed on your server and Working.
2. Download the latest from GitHub repo:

<https://github.com/phppgadmin/phppgadmin/releases>

```bash
    sudo tar xf phpPgAdmin-x.y.z.tar.bz2 -C /var/www/phpPgadmin
```

In order to make phpPgAdmin navigable, we create a configuration file for the web service (Apache in this case):

```bash
    sudo nano /etc/httpd/conf.d/phpPgAdmin.conf
```

The content will be an alias that will point to the installation path of the application:

```
    Alias /phppgadmin /var/www/phpPgAdmin
```

Save the file and Reload the Web Service:

```bash
    sudo systemctl reload httpd
```

phpPgAdmin requires the presence in Fedora 31 of certain PHP extensions, mainly the one that allows the connection with the database service, which we will install from the system repositories:

```bash
    sudo dnf install -y php-pgsql
```
