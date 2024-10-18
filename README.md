# laravel-wsl-setup

## Ubuntu package list ->
```bash
sudo apt-get update
```

## PHP ->
```bash
sudo add-apt-repository ppa:ondrej/php
```
```bash
sudo apt install php php-fpm php-mysql php-mbstring php-xml php-bcmath php-intl php-curl php-zip
```
```bash
sudo service php-fpm start
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

## Create laravel app ->
```bash
composer create-project laravel/laravel example-app
```

## SQLite intall ->
Make sure that this repository of PHP is added - it is not required to repeat this step
```bash
sudo add-apt-repository ppa:ondrej/php
```
```bash
sudo yum install php-sqlite3
```


## Laravel project start ->
```bash
php artisan serve
```

## Laravel DB:migration ->
```bash
php artisan migrate
```


