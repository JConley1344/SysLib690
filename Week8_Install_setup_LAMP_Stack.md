# Week8
## Apache Web Server

I used `sudo apt update` and `sudo apt upgrade` to conduct the 19 upgrades needed. I used `sudo reboot` to reboot due to a kernel update being required. 

Following along with the vdieo I used the codes `apt search apache2 | head` to idenity the specific package name. Then went ahead and installed apache2 using the command `sup apt install apache2`.
I checked to make sure apache2 2 was enabled and running (using `systemctl status apache2`. 

I had connection issues again. (Still no reason why it is happening.) Once back I checked the status of apache2 again to make sure everything was still running. It was

Both `w3m 127.0.01` anbd `w3m localhost` work to bring up the defult page. My defult page looked a bit different, the `It Works` banner is different, but otherwise it looked the same as the w3m addresses. 

![Ubuntu Apache2](https://github.com/JConley1344/SysLib690/assets/157387139/722888b4-3cb1-4527-92b6-71f64eb1af4d)

To finish up the installation and set up of the Apache2 server. I used the codes 
```
cd /var/www/html/
sudo mv index.html index.html.original
sudo nano index.html
```
Then moved index.html to `index.html.origninal`. 

I do not know HTML so I typed to practice formating for **HTML**. 
```
<html>
<head>
<title>My first web page using Apache2</title>
</head>
<body>

<h1>Welcome</h1>

<p>Welcome to my web site.
I created this site using the Apache2 HTTP server.</p>

</body>
</html>
```

### Observations on HTLM Formating
1. It starts and ends with **<html>**
2. Different sections start and end with the what they are desinated *ie:* <head> for heading and <body> for the body of text. 
3. `</p>` is for paragraph, which is used in microsoft word the same way.


## PHP

## MySQL
