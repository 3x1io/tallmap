# Environment Setup
this steps to make our framework development environment run perfectly and without any errors, thanks for Linux and Laravel Valet for suppport that

## Install BackBox Linux

we are like to use [BackBox](https://www.backbox.org/download/) Linux it's has a lot of tools and support our environment, so form the link we support download the ISO image and put it in USB using [Rufus](https://rufus.ie/en/) and than boot your computer into it

## Install dependencies packages
let's start by open our terminal and update the system to the last one, and after that install some packages

```bash
sudo apt-get update
```

```bash
sudo apt-get upgrade
```

after it finished reboot your computer and after that run this command

```bash
sudo apt-get install network-manager libnss3-tools jq xsel
```

## Install PHP & it's extensions
```bash
sudo apt install php8.0-fpm
```

```bash
sudo apt install php8.0-cli php8.0-common php8.0-curl php8.0-mbstring php8.0-opcache php8.0-readline php8.0-xml php8.0-zip php8.0-mysql php8.0-gd
```

## Install MySql Server

```bash
sudo apt-get -y install mysql-server
```

```bash
sudo mysql_secure_installation
```

use `0` for password and use any password something like `12345678`

after the installation finished, start mysql server

```bash
sudo mysql
```

and on the mysql server console use this command 

```bash
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '12345678';
```
```bash
mysql> FLUSH PRIVILEGES;
```
```bash
mysql> exit;
```

## Install Composer 

```bash
sudo apt install curl
```

```bash
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

## Install Valet Linux+

```bash
composer global require genesisweb/valet-linux-plus
```

no you need to export Valet use
```bash
PATH="$PATH:$HOME/.composer/vendor/bin"
```
Or use the following
```bash
PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

and now it will be easy to start install valet 

```bash
valet install
```

it will ask you for a password input `12345678`


## Install PHPmyadmin

the valet has been installed now, let's go and install phpmyadmin and link it with .test subdomain using valet
first of all create a folder for your sites on home directory ~

```bash
cd ~
mkdir Sites
cd Sites
```

now we are on the Sites path, let's park this directory to be the directory of our projects

```bash
valet park
```
now any project on this directory will be auto-linked with subdomain .test, let's download phpmyadmin from this [link](https://www.phpmyadmin.net/) and unzip the file inside the Sites directory and rename the folder to phpmyadmin, after that go inside the folder and use this command

```bash
cp config.sample.inc.php config.sample.php
nano config.sample.php
```
change the line to

```php
$cfg['blowfish_secret'] = 'YK07LhNSe50vrj,HwBfb.l3gpbv;u8b7',
```
now use CTRL + x and say Y
now we will use valet to link phpmyadmin and secure the link with SSL


```bash
valet link
valet secure
valet open
```

now you can see the phpmyadmin working and you can use root as user and the password you created to mysql to login


