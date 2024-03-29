# Week 11 Cataloging Modules (4.5)

What an interesting week. This week I felt like I finally have a pretty good drip on what was going on.
That said I started by watching the video and then reading through again the instructions. 

## Creating the HTML Page
I logged into my virtual machine. I first ran `sudo apt update`. I had 11 updates. I ran `sudo apt upgrade` to update my machine.

I then created the new directory **cataloging** using the code `sudo mkdir cataloging` in `cd /var/www/html/`.
I then created the file `index.html` in **cataloging**.

The file `index.html` contained the following code:
```
<!DOCTYPE html>
<html>
<head>
    <title>Enter Records</title>
</head>
<body>
    <h1>OPAC Library Administration</h1>

    <p>This is the library administration page for entering records into the OPAC.</p>
    <p>Please do not use this page unless you are an authorized cataloger.</p>

    <form action="insert.php" method="post">
        <label for="author">Author:</label>
        <input type="text" name="author" id="author" required><br><br>

        <label for="title">Book Title:</label>
        <input type="text" name="title" id="title" required><br><br>

        <label for="publisher">Publisher:</label>
        <input type="text" name="publisher" id="publisher" required><br><br>

        <label for="copyright">Copyright:</label>
        <input type="date" id="copyright" name="copyright">

        <input type="submit" value="Submit">
    </form>
</body>
</html>
```

## Creating the PHP Cataloging Page
Inside the cataloging directory I created the file **insert.php** using `sudo nano insert.php`. I used the following code to create the file.

```
<?php

// Load MySQL credentials
require_once '../login.php';

// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");

// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");

// Prepare and bind SQL statement
$stmt = $conn->prepare("INSERT INTO books (author, title, publisher, copyright) VALUES (?, ?, ?, ?)");
$stmt->bind_param("ssss", $author, $title, $publisher, $copyright);

// Set parameters and execute statement
$author = $_POST["author"];
$title = $_POST["title"];
$publisher = $_POST["publisher"];
$copyright = $_POST["copyright"];

if ($stmt->execute() === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $stmt->error;
}

// Close statement and connection
$stmt->close();
$conn->close();

echo "<p>Return to the cataloging page: <a href='http://35.232.255.82/cataloging/'>http://35.232.255.82/cataloging/</a></p>";
?>
```

## Security 
I created the login and password for the cataloging page. I kept *libcat* at the username for the login. 

I also use the code provided to create the **`.htaccess`** file.

```
AuthType Basic
AuthName "Authorization Required"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
```

I then double checked the configuration of the ***apache2*** files and got the okay. I restarted appache2 and then checked the status to make sure that apache2 had restarted. ***Success***

### Security Update: 3/19/2024

I found that after I entered my password in it did not prompt me to do so again the rest of the day. This worried me. So I chose not to submit my learnings to the board. 

**Celebration!!** This morning it asked for my secutiry login and password when navigating to the cataloging page. I have not figured out why it did not ask each time yesterday I opened and closed the cataloging page. I did not save the password for autofill. 

![690 week 11_6](https://github.com/JConley1344/SysLib690/assets/157387139/153ac792-9d87-422b-a2ad-fbea2c7123a5)

## Cataloging
I added an additional 19 titles to the OPAC today. All children's books from my son's personal collection. ***(See picture)*** 
![20240318_141330](https://github.com/JConley1344/SysLib690/assets/157387139/8530d5fc-85c3-4dab-a5cc-8a22125a2cd2)

I entered 5 in from the cataloging page, just to practice what you did in the video and make sure that mine was working. It worked perfectly. I then added the additional 14 from the virtual machine in `SQL`. I also searched and confirmed publishing dates for all 19 titles. I used sticky notes to have the dates ready for input. ***(See Picture)***

![20240318_141402](https://github.com/JConley1344/SysLib690/assets/157387139/1ca051cf-6755-451a-9e6a-ea3aff33b842)

I reviewed the code from two weeks ago because I did not remember how to get to opacdb.
I used `mysql -u opacuser -p` to get into MySQL. I then `use opacdb;` to start inserting titles.

I entered titles in sets of 2, because last time that worked best. I also did all my typing in *Notepad* then copy and pasted the code into the virtual machine.

Here is what my coding looked like to be entered into MySQL. 

```
insert into books (author, title, publisher, copyright) values
('David LaRochelle', 'See the Ghost', 'Candlewick Press', '2023-07-25'),
('David LaRochelle', 'See the Dog', 'Candlewick Press', '2021-09-14');

insert into books (author, title, publisher, copyright) values
('David LaRochelle', 'See the Cat', 'Candlewick Press', '2021-03-30'),
('Angela DiTerlizzi', 'The Magical Yet', 'Hachette Book Group', '2020-04-21');

insert into books (author, title, publisher, copyright) values
('Jory John', 'The Couch Potato', 'Harper Collins Publishing', '2020-11-03'),
('Jory John', 'The Smart Cookie', 'Harper Collins Publishing', '2021-11-02');

insert into books (author, title, publisher, copyright) values
('Jory John', 'The Sour Grape', 'Harper Collins Publishing', '2022-11-01'),
('Jory John', 'The Cool Bean', 'Harper Collins Publishing', '2019-12-03');

insert into books (author, title, publisher, copyright) values
('Jory John', 'As Cool As It Gets', 'Harper Collins Publishing', '2022-09-13'),
('Anna Llenas', 'The Color Monster A Story About Emotions', 'Little, Brown and Company', '2018-04-19');

insert into books (author, title, publisher, copyright) values
('Kira Willey', 'Breathe Like a Bear 30 Mindful Moments for Kids to Feel Calm and Focused Anytime, Anywhere', 'Rodale Kids', '2017-12-05'),
('Kira Willey', 'Breathe Like a Bear First Day of School Worries', 'Rodale Kids', '2023-06-27');

insert into books (author, title, publisher, copyright) values
('Clare Helen Welsh', 'Sunny Side Up', 'Kane Miller EDC Publishing', '2023-05-11'),
('Amy June Bates', 'The Big Umbrella', 'Simon & Shuster Publishing', '2018-02-06');
```
I then ran the code `select * from books;` to verify that all titles were in the OPAC. I now have 37 total. 

### Visuals From This Week 11 Assignments
**Updated OPAC (image 1)**

![690 week 11_1](https://github.com/JConley1344/SysLib690/assets/157387139/0a9c2c3a-caf5-43f0-8783-8e69f84700af)

**Updated OPAC (image 2)**

![690 week 11_3](https://github.com/JConley1344/SysLib690/assets/157387139/aa711c7c-14ed-46e2-89a6-fc44be0275c8)

**Upadted OPAC from SQL**

![690 week 11_7](https://github.com/JConley1344/SysLib690/assets/157387139/b5a0ab1b-0ed5-4e91-81eb-68ce72b580c7)

**PHP Cataloging Page (after password entered)**

![690 week 11](https://github.com/JConley1344/SysLib690/assets/157387139/1db3a336-1369-4e2f-8f9e-086c9a520382)

**OPAC Search Landing Page**

![690 week 11_4](https://github.com/JConley1344/SysLib690/assets/157387139/125e826a-6354-43b7-a312-47e3cdfc2356)

**OPAC Search Results *Please note that 5 titles returned out of 7 due to date restrictions*.**

![690 week 11_5](https://github.com/JConley1344/SysLib690/assets/157387139/68e5bc50-f387-4ad4-a2e3-c3aeda3ed3f5)




