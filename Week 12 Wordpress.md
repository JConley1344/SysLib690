# Week 12 WordPress
## Updating Virtual Machine

Sometimes I wonder if I am not rebooting my virtual machine correctly because I swear there are updates every time I log on. 
After 28 updates, and 25 minutes, I was up and moving with this week's command line.
![loading-40834_1280](https://github.com/JConley1344/SysLib690/assets/157387139/2ebe1b6f-1893-4552-9767-fdac8b809f76)

## Download & Extract
I made sure I was in the/var/www/html directory with the `cd /var/www/html` command line.

I then downloaded the latest version of WordPress using `sudo wget https://wordpress.org/latest.tar.gz`.

And extracted the package using `sudo tar -xzvf latest.tar.gz`.

## Creating a Database and User
I switched to the root Linux user and logged in to MySQL using,
`sudo su
mysql -u root`.

I used the command lines below to create the WordPress database and a user. In place of the 'XXXXXXXX,' I created my own password for login purposes.

```
create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';
create database wordpress;
grant all privileges on wordpress.* to 'wordpress'@'localhost';
show databases;
\q
```

## Configuring
Once the WordPress database was created I changed to the WordPress directory `cd /var/www/html/wordpress`.

I then copied and renamed the configuration file to edit. `sudo cp wp-config-sample.php wp-config.php`

I used `nano` to edit and update the configuration file. `sudo nano wp-config.php` Here I updated the database name, database user, and database password. 
I then added `define('FS_METHOD','direct');` to the command line to disable **FTP uploads**. 

## Changing Ownership

I used the command line `sudo chown -R www-data:www-data /var/www/html/wordpress' to change ownership from nogroup. 

![wordpress 690_1](https://github.com/JConley1344/SysLib690/assets/157387139/1ed7992a-a7cc-44a3-8c52-510100ac2dba)

## WordPress Designing 

I finished the installation of the user interface of WordPress.
![wordpress 690](https://github.com/JConley1344/SysLib690/assets/157387139/285770c8-830d-4db3-8149-37954706514e)

![wordpress 690_2](https://github.com/JConley1344/SysLib690/assets/157387139/6318f318-8ee8-45d5-af79-6cb72ef79a37)

Then I got lost for hours looking at different possible designs for the website.

My current WordPress site:
http://35.232.255.82/wordpress/
