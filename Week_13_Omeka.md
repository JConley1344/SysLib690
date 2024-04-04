# Week 13- Omeka

## Preinstallation Steps
I ran `sudo apt update` and needed to update 40 packages on my virtual machine. 
I then ran `sudo atp upgrade` to install all 40 packages. 
I then needed to step away from my machine, so I used `reboot now` to make sure all updates took.

When I came back to the virtual machine, all packages were up to date. 

I started with doing the prerequist command lines from the systems librarian book. I ran `sudo apt install imagemagick` then ran the line `sudo a2enmod rewrite`. I was then promted to `systemctl restart apache2`, so I ran the line `
sudo systemctl restart apache2` to restart apache2.  Everything was in place to start installation, downloading, and configuring of Omeka. 

## Create Database & User

I created a new database called omeka and a new user and password for that database. I made sure to get the commandline correct by transcripbing the code into notepad first to copy and paste. This allowed me to be error free in the execution of these commands. 

`create user 'omeka'@'localhost' identified by 'XXXXXXX';`
`create database omeka;`
`grant all privileges on omeka.* to 'omeka'@'localhost';`
`show databases;`
`\q` to leave mysql.

`exit` to leave the root

## Installation

`cd var/www/html`
`sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`
messed up and did `sudo app install unzip` and had to figure out why the command was not found. 
`sudo apt install unzip`

Omeka zip file installed.

## Download & Extract





## Config

## Finishing Installation 
