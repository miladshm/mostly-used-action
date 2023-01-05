# Install PHP 8.1 on Fedora 37

Step 1. Before proceeding, update your Fedora operating system to make sure all existing packages are up to date. Use this command to update the server packages:
```bash
sudo dnf upgrade
sudo dnf update
```
Step 2. Add PHP Repository.

To install PHP on Fedora, you need to set up the REMI repository. Now import the Remi PHP repository using the following command below:
```bash
sudo dnf install http://rpms.remirepo.net/fedora/remi-release-37.rpm
```
Now, verify the installation:
```bash
dnf repolist | grep remi
```
Output:
```bash
\[root@idroot.us ~\]$ dnf repolist | grep remi
remi Remi's RPM repository - Fedora 37 - x86_64
remi-modular Remi's Modular repository -   Fedora   37   - x86_64
```
Step 3. Installing PHP 8 on Fedora 37.

By default, the PHP package come in the default repository of Fedora 37. Now run the following command below to install the PHP 8.1 packages to your Fedora system:
```bash
sudo dnf module enable php:remi-8.1 
sudo dnf install php php-common php-cli
```
In addition, if you would like to install the most commonly used extensions for PHP 8.1, use the following command:
```bash
sudo dnf install php-cli php-fpm php-curl php-mysqlnd php-gd php-opcache php-zip php-intl php-common php-bcmath php-imagick php-xmlrpc php-json php-readline php-memcached php-redis php-mbstring php-apcu php-xml php-dom php-redis php-memcached php-memcache
```
After installing PHP, use the below command to check its version:
```bash
php -v
```
Output:
```
PHP 8.1.13   (cli)   (built:   Nov   28   2022   11:36:13)   (NTS gcc x86_64)   Copyright   (c)   The PHP Group   Zend   Engine v4.1.13,   Copyright   (c)   Zend   Technologies   with   Zend   OPcache v8.1.13,   Copyright   (c),   by   Zend   Technologies
```

# Diffrent versions of PHP
Different applications may require various versions of PHP. In this post, we are going to install multiple versions of PHP on Fedora. In my particular case, I'm using Fedora 35.  

We will also show how to set the default version of PHP to be used on the Fedora system as when required. We will be installing PHP 7.4 and PHP 8 on a single Fedora system.  

Currently, the supported stable version of PHP in the Fedora software repositories is the PHP 8.0. You can confirm this by running the `dnf` command below.
```bash
    sudo dnf info php-fpm
```
The output should be similar with below:

![Latest php version in Fedora](https://r00t4bl3.com/uploads/attachment-screenshot-from-2021-12-28-15-15-21-e8777ca9eba2e4bfebd85f0e062e15a9.png)

## PHP 7.4 Installation

Next, we'll install an older PHP version, version 7.4. Unfortunately, Official Fedora software repository only provide PHP 8. We must add another repository to be able to install older PHP version. This repository is called Remi repository.

To add Remi repository to our Fedora 37 system:
```bash
    sudo dnf -y install https://rpms.remirepo.net/fedora/remi-release-37.rpm
```
![Add remi repo](https://r00t4bl3.com/uploads/attachment-screenshot-from-2021-12-28-15-35-45-66201257e9817f0707abe5d547f0481a.png)

Some common dependencies are available in Remi repository, which need to be enabled:
```bash
    sudo dnf config-manager --set-enabled remi
```
![Enable remi repo](https://r00t4bl3.com/uploads/attachment-screenshot-from-2021-12-28-15-39-52-c718b8e202fb22332471300d1c65fa90.png)

Now it's time to install PHP 7.4.
```bash
    sudo dnf install php74-php-cli php74-php-fpm php74-php-gd php74-php-curl php74-php-mysqlnd php74-php-zip php74-php-xml php74-php-mbstring php74-php-bcmath
```

When the installation process finished, let's verify our installation by typing this command:
```bash
    php -v
```
It should respond with something like this:  

    PHP 8.0.14 (cli) (built: Dec 16 2021 03:01:07) ( NTS gcc x86_64 )

For PHP 7.4, verify installation by using this command:  
```bash
    php74 -v
```
It should respond with something like this:  

    PHP 7.4.27 (cli) (built: Dec 14 2021 17:17:06) ( NTS )

## PHP 8.0 Installation
```bash
    sudo dnf install php80-php-cli php80-php-fpm php80-php-gd php80-php-curl php80-php-mysqlnd php80-php-zip php80-php-xml php80-php-mbstring php80-php-bcmath
```

When the installation process finished, let's verify our installation by typing this command:
```bash
    php -v
```
It should respond with something like this:  

    PHP 8.0.14 (cli) (built: Dec 16 2021 03:01:07) ( NTS gcc x86_64 )

For PHP 7.4, verify installation by using this command:  
```bash
    php80 -v
```
It should respond with something like this:  

    PHP 8.0.13 (cli) (built: Dec 14 2021 17:17:06) ( NTS )
## PHP 8.1 Installation
```bash
    sudo dnf install php81-php-cli php81-php-fpm php81-php-gd php81-php-curl php81-php-mysqlnd php81-php-zip php81-php-xml php81-php-mbstring php81-php-bcmath
```

When the installation process finished, let's verify our installation by typing this command:
```bash
    php -v
```
It should respond with something like this:  

    PHP 8.0.14 (cli) (built: Dec 16 2021 03:01:07) ( NTS gcc x86_64 )

For PHP 7.4, verify installation by using this command:  
```bash
    php81 -v
```
It should respond with something like this:  

    PHP 8.0.13 (cli) (built: Dec 14 2021 17:17:06) ( NTS )
## Updating default PHP version
### PHP 7.4
```bash
    sudo update-alternatives --set php /usr/bin/php74
```
### PHP 8.0
```bash
    sudo update-alternatives --set php /usr/bin/php80
```
### PHP 8.1
```bash
    sudo update-alternatives --set php /usr/bin/php81
```