---
layout: default
parent: New System Setup
title: Software Setup
nav_order: 1
---

# Software Setup

## ❶ Homebrew Setup

1. To install Homebrew, execute the following in terminal: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

## ❷ Install nodeJS 16.18 and NPM

1. Run `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash` in terminal.  Follow the commands at the end of the install to make `nvm` usable
2. Run `nvm install 16.18.1` to install nodeJS and `npm`

## ❸ Install PHP version 8.1
1. Run `brew install shivammathur/php/php@8.1` in terminal
2. Run `brew link php@8.1` in terminal
3. Update path variable in .zshrc (or .bashrc, change filename below as needed):
    - `echo 'export PATH="/opt/homwbrew/opt/php@8.1/bin:$PATH"' >> ~/.zshrc`
    - `echo 'export PATH="/opt/homwbrew/opt/php@8.1/sbin:$PATH"' >> ~/.zshrc`
    - `source ~/.zshrc`
4. Check the version: run `php -v` in terminal

## ❹ Install Yarn
1. Run `npm install --global yarn` in terminal

## ❺ Composer Setup
1. Run `curl -sS https://getcomposer.org/installer | php` in the terminal
2. Install composer in a path-accessible folder:
    - `mkdir -p /usr/local/bin`
    - `mv composer.phar /usr/local/bin/composer`
    - `chmod +x /usr/local/bin/composer`

----
Next Step: [SSH Service Setup](/docs/new-system-setup/ssh-service-setup)
{: .fs-5 }