# Windows WSL Laravel Development Enviroment Setup
This guide is for installing latest PHP version from ppa:ondrej/php
If you would like to install different version of PHP it is required to mention the version for all the packages.
This guide is just for quick development WSL setup for learning and testing.

[WSL Install](#wsl-install--)  
[PHP Install](#php--)  
[Install Composer](#install-composer--)  
[Install laravel globaly](#install-laravel-globaly--)  
[SQLite intall](#sqlite-intall--)  
[Create laravel app](#create-laravel-app)  
[Install Node.js and npm](#install-nodejs-and-npm)  
[git-new-env-setup](#git-new-env-setup)  
[How to Fully remove WSL](#how-to-fully-remove-wsl-with-all-files-and-config--)  

## WSL Install ->
Let's install Windows WSL using PowerShell.
```bash
wsl --install
```
```
After this go to microsoft Store and install one of Ubuntu-** distros
After this you can click Open and setup Ubuntu with username and password.
```

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


## Install Composer ->
```bash
sudo apt install php-cli unzip
```
Download Composer installer
```bash
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
Chech Composer authentic HASH
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```
Verify if HASH is Authentic
```bash
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
If you get "Installer verified" proceed to install
```bash
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

## Install laravel globaly ->
Install Laravel Installer Globally: Run the following command to install the Laravel installer globally using Composer:
```bash
composer global require laravel/installer
```

Run the following command to find the exact directory:
By looking into the output you will know what export PATH
```bash
composer global config home
```

Add Composer's Bin Directory to PATH: After installation, make sure the Laravel installer is in your system's PATH. Add the following line to your shell configuration file (e.g., ~/.bashrc, ~/.zshrc, or ~/.profile):
```bash
export PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

Then reload the shell configuration:
```bash
source ~/.bashrc
```
Verify Laravel Installer
```bash
laravel --version
```
Create a New Project using laravel command
```bash
laravel new project --dev
```

## SQLite intall ->
Make sure that ppa:ondrej/php repository of PHP is added in the first steps
```bash
sudo apt install php-sqlite3
```
Sqlite Browser to edit SQLITE databases
```bash
sudo apt-get install sqlitebrowser
```
To start using it enter
```bash
sqlitebrowser
```

## Create laravel app
```bash
composer create-project laravel/laravel example-app
```
```bash
php artisan serve
```

## IF YOU HAVE EXISTING PROJECT
Go into project directory
```bash
cd example-app
```
Install all dependencies
```bash
composer install
```
Create .env file
```bash
cp .env.example .env
```
Generate APP_KEY
```bash
php artisan key:generate
```
Start the server
```bash
php artisan serve
```

# Install Node.js and npm
Update your package index
```bash
sudo apt update
```
Install NodeSource's setup script:
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
Install Node.js and npm:
```bash
sudo apt install -y nodejs
```
Verify installation
```bash
node -v
```
```bash
npm -v
```
After that you can instal Project required dependencies
```bash
npm install
```
Build Assets with Vite
For development it start Autoreload server:  
And then you can use 'php artisan serve' on seperate CMD window to start working
```bash
npm run dev
```
For production aswell you can use it in development it will prebuild assets  
But you would need to restart every time change is made (without need for keeping 'npm run dev' in seperate CMD window.
```bash
npm run build
```

# git-new-env-setup

Set up your Git identity
```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "your.email@example.com"
```

Check if an SSH key already exists on your WSL (but probably not new setup)
```bash
sudo ls ~/.ssh
```

If no key exists, generate one:
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

Copy the public key
```bash
cat ~/.ssh/id_ed25519.pub
```

Add the public key to your GitHub account:
Go to your GitHub account settings.
Navigate to SSH and GPG keys.
Click New SSH Key, paste the key, and save.

Clone your repository using SSH
```bash
git clone git@github.com:name/example.git
```

Make Changes and Push

Edit any file
```bash
nano /example/README.md
```
Add all to git
```bash
git add .
```
Add commit comment
```bash
git commit -m "Initial setup"
```
Push to main branch
```bash
git push origin main
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



