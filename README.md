# laravel-wsl-setup
This guide is for installing latest PHP version from ppa:ondrej/php
If you would like to install different version of PHP it is required to mention the version for all the packages.
This guide is just for quick development WSL setup for learning and testing. Next i will have to learn to use Docker.

## WSL Install ->
```bash
wsl --install
```
```
After this go to microsoft Store and install one of Ubuntu-** distros
```
```
After this you can click Open and setup Ubuntu with username and password.
```

## Ubuntu package list ->
```bash
sudo apt-get update
```
I think its always nice to upgrade aswell (not required)
```bash
sudo apt-get upgrade
```

## PHP ->
```bash
sudo add-apt-repository ppa:ondrej/php
```
```bash
sudo apt install php php-fpm php-mysql php-mbstring php-xml php-bcmath php-intl php-curl php-zip
```
```bash
php -v
```


## Install Composer ->
```bash
sudo apt install php-cli unzip
```
```bash
cd ~
```
```bash
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```
```bash
echo $HASH
```
```bash
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
```bash
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

## SQLite intall ->
Make sure that ppa:ondrej/php repository of PHP is added in the first steps
```bash
sudo apt install php-sqlite3
```


## Create laravel app ->
```bash
mkdir code $$ cd code
```
```bash
composer create-project laravel/laravel example-app
```
```bash
cd example-app
```
```bash
php artisan serve
```


## How to Fully remove WSL with all files and config ->
Open CMD or PowerShell prompt
```bash
wsl -l
```
```bash
wsl --unregister Ubuntu-**
```
```
After doing previous steps you have to manually delete Ubuntu app
Uninstall Ubuntu-** from Windows Search (App Store installed)
```
