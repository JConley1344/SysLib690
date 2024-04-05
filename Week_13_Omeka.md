# Week 13- Omeka

## Prerequisites

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

I felt very confident at this point in the process. However, that soon changed.

## Installation
I got back into `cd var/www/html`.

I then used `wget` to download the zip file to my server. That looked like this `sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`.
I did mess up and used `sudo app install unzip` and had to figure out why the command was not found. Once I realized that I had used 'app' intstead of 'apt' I on track again.
(`sudo apt install unzip`)

Here is where an issue started. I was unable get the zip file to unzip. I kept getting the `checkdir error`. I of course tried to fix the issue on my own and ended getting confused as I looked for solutions online. 

![Screenshot 2024-04-04 214259](https://github.com/JConley1344/SysLib690/assets/157387139/87022937-6fe5-49c2-bfd4-736bc52538e1)

***(Do not scoure the internet for answers when you are not 100% on what you are looking for- results 3/10, do not recommend)***

Posted about the error on **Element**.

Used `sudo unzip omeka-3.1.2.zip` and it worked perfectly. 

**Omeka file installed!!**

## Download & Extract
I then checked the files using `ls -l`.

I moved the omeka-3.1.2 file to omeka using `sudo mv /var/www/html/omeka-3.1.2 /var/www/html/omeka`.

I then went into *omeka* using `cd /var/www/html/omeka`, looked for the file `db.ini` and used `nano` to edit it.

**OMEKA Installation Success!!!**

![Screenshot 2024-04-05 143644](https://github.com/JConley1344/SysLib690/assets/157387139/f67f61de-e2c8-49d8-9a70-323b50829d9c)


## Omeka

![Screenshot 2024-04-05 143722](https://github.com/JConley1344/SysLib690/assets/157387139/963cd726-1416-467a-a3b3-81f4d0e662d3)

I added a couple of books to just see how it would look on the public facing side. I have only ever used Omeka once in 602. However, after looking through it I was thinking that maybe what I created for my practicum in Fall 2023. I used the program *LiveBinder*. I believe *Omeka* might be a better option. I am debating on trying it out. 

![Screenshot 2024-04-05 174621](https://github.com/JConley1344/SysLib690/assets/157387139/a43184a4-71ab-484c-a431-224de24acd99)


### Personal Notes
