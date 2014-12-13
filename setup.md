# HackCentral Server Commands

## Update packages
```shell
apt-get -y update
```

## Install packages
```shell
apt-get -y install curl git-core python-software-properties postfix telnet
apt-get -y update
```

## Install NGINX
```shell
add-apt-repository ppa:nginx/stable
apt-get -y update
apt-get -y install nginx
service nginx start
```

## Install PostgreSQL
```shell
add-apt-repository ppa:pitti/postgresql
apt-get -y update
apt-get -y install postgresql libpq-dev
```

## Setup Database
```shell
sudo -u postgres psql
\password #enter new root PG password
createuser <user> with password ‘<password>’; #change <user> and <password>
create database <database_name> with owner <user>; #change <database_name> and <user>
\q
```

## Create Database
```shell
sudo -u postgres psql postgres
CREATE DATABASE hackcentral_production OWNER hc;
\q #close out of postgresql session
```

## Install Node.js
```shell
add-apt-repository ppa:chris-lea/node.js
apt-get -y update
apt-get -y install nodejs
```

## Create Deploy User
```shell
adduser deployer
adduser deployer sudo
su - deployer
cd ~
```

## Install Ruby 2.1.3 via Rbenv
```shell
curl -L https://raw.github.com/fesplugas/rbenv-installer/master/bin/rbenv-installer | bash
nano ~/.bashrc
```
## .bashrc (add the following code)
```shell
export RBENV_ROOT="${HOME}/.rbenv"

if [ -d "${RBENV_ROOT}" ]; then
 	 export PATH="${RBENV_ROOT}/bin:${PATH}"
  	eval "$(rbenv init -)"
fi
```

## Continuing to install Ruby 2.1.3 via Rbenv
```shell
rbenv bootstrap-ubuntu-12-04
rbenv install 2.1.3
rbenv global 2.1.3
ruby -v
```

## Install Bundler and Rails
```shell
sudo gem install bundler rails --no-ri --no-rdoc
rbenv rehash
```

## Make GitHub a known host
```shell
ssh@github.com
```

## Get rid of default configuration
```shell
sudo rm /etc/nginx/sites-enabled/default
sudo rm /etc/nginx/sites-enabled/default && sudo service nginx restart
```

## Restart NGINX and Unicorn
```shell
sudo service nginx restart
sudo update-rc.d unicorn_hackcentral defaults
sudo service nginx restart && sudo service unicorn_hackcentral restart

```
