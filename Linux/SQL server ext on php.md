````shell

sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
sudo dnf install yum-utils
sudo dnf module reset php
sudo dnf module install php:remi-8.1
sudo dnf check-update
# Note: The php-pdo package is required only for the PDO_SQLSRV driver
sudo dnf install php-pdo php-pear php-devel

sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install -y msodbcsql18
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install -y mssql-tools18

# optional: for unixODBC development headers
sudo dnf install unixODBC-devel unixODBC

sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit

sudo dnf install php-sqlsrv

````

