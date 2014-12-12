# HackCentral Server Commands

## Create Deploy User
```shell
  sudo adduser deploy
  sudo adduser deploy sudo
  su deploy
```

## Update packages
```shell
  sudo apt-get update && sudo apt-get upgrade
```

## Install Ruby 2.1.3 via RVM
```shell
  curl -L https://get.rvm.io | bash -s stable
  source ~/.rvm/scripts/rvm
  echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc
  rvm install 2.1.3
  rvm use 2.1.3 --default
```

## Install Bundler and Rails
```shell
  echo "gem: --no-ri --no-rdoc" > ~/.gemrc
  sudo gem install bundler rails --no-ri --no-rdoc
```

## Install NodeJS
```shell
  sudo apt-get install nodejs
```

## Install PostgreSQL
```shell
  sudo apt-get install postgresql postgresql-contrib libpq-dev
```

## Create Database User
```shell
  sudo su - postgres
  createuser hc --pwprompt #enter password you want for this user
```

## Create Database
```shell
  sudo -u postgres psql postgres
  CREATE DATABASE hackcentral_production OWNER hc;
  \q #close out of postgresql session
```

## Install Git
```shell
  sudo apt-get install git
```

## Install NGINX and Unicorn
```shell
  sudo apt-get install nginx
  cd ~
  gem install unicorn --no-ri --no-rdoc
```

## Setup NGINX
```shell
  sudo rm /etc/nginx/sites-available/default
  sudo nano /etc/nginx/sites-available/default #Copy and paste the content from here: https://github.com/hackcentral/server-stuff/blob/master/default
```
## Making Unicorn work if server restarts
```shell
  sudo chmod +x config/unicorn_init.sh
  sudo ln -s /var/www/hackcentral/config/unicorn_init.sh /etc/init.d/unicorn
```

## Restart NGINX
```shell
  sudo service nginx restart
```
