# Week 14
## Koha

### Firewall and 8080
I went ahead and set up the VPN and Firewall for my new instance on Google Cloud
```
Click on the hamburger ☰ icon at the top left.
Click on VPN Network
Click on Firewall
At the top of the page, choose Create a firewall rule (do not choose Create a firewall policy)
Add name: koha
Add description: open port 8080
Next to Targets, click on All instances in the network
In the Source IPv4 ranges, add 0.0.0.0/0
Click on Specified protocols and ports
Click on TCP
Add 8080 in the Ports box
Click on Create
```
# Installing Koha

After updating and cleaning my new VM Instance I went about setting up Koha. 
I started with `sudo apt install gnupg2` and then `sudo reboot now` the server.

I logged in as the root user `sudo su`.

## Added Koha repository
`echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list`

Then added the digital signature
`wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -`

## Install Koha

I updated the Koha repository, `apt update`.

Viewed the Koha package information `apt show koha-common`.

Finally installed koha, `apt install koha-common`.

## Congfigured Koha

Used `nano` to configure files `nano /etc/koha/koha-sites.conf`.

Changed the **`INTRAPORT="80"`** to **`INTRAPORT="8080"`**

Installed `mysql`, `apt install mysql-server`, and set the root password.

Enabled URL rewriting and CGI functionality `a2enmod rewrite a2enmod cgi`.

Restarted apache2, `systemctl restart apache2`.

Created a database for Koha and then told apache2 ports to listen to 8080.
This is where I had an issue. I first removed the ***Listen80*** from the file and replaced it with ***Listen8080***. However I needed both lines of code or the patron facing ILS did not work.
So I went back in and added ***Listen 80*** back in so that I had both codes and it worked perfectly.

Then I had to enable, deflate and relode apache2. 
```
a2dissite 000-default
a2enmod deflate
a2ensite bibliolib
systemctl reload apache2
systemctl restart apache2
```

## Koha Web Installer

I found the username and password `nano /etc/koha/sites/bibliolib/koha-conf.xml` to get into configuring the staff end of the Koha ILS.

I then created a superuser/staff user once the installation and configuration of the site was created.
Here I created a couple of users and added a few books.

![Screenshot 2024-04-12 105240](https://github.com/JConley1344/SysLib690/assets/157387139/d7f2ab76-e425-4277-80af-e6adca4e4c78)


![Screenshot 2024-04-12 101930](https://github.com/JConley1344/SysLib690/assets/157387139/3b312282-d628-41b1-ae5e-804ff5cd7aac)

Patron Iinterface
![Screenshot 2024-04-12 102018](https://github.com/JConley1344/SysLib690/assets/157387139/809bed34-fb1a-4849-a25f-9aa13ad517f8)


I found that documentation is very important.
