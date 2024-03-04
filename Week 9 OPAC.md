#Week 9 OPAC

After last week's chaotic start I was a bit skiddish to start this week. I am very extremely cauious after watching all my hard work go down in flames. 

![coder-everything-is-fine-meme](https://github.com/JConley1344/SysLib690/assets/157387139/058c3053-001e-47b4-9aa1-e7d9238d2734)

## HTML Page
In `cd /var/ww/html/ I created the file` **mylibrary.html**. I then added the code to create the basic seach box.

```
<html>
<head>
<title>MySQL Server Example</title>
</head>
<body>

<h1>A Basic OPAC</h1>

<p>In the form below,
<b>optionally</b> enter text in the search field.
You can search by author, title, or publisher.
Capitalization is not necessary.
It's okay to enter partial information,
like part of an author's, title's, or publisher's name.</p>

<p>The date fields are <b>required</b>.
You can use the date fields to limit results.
I added some extra records,
which you can view to know what you can query:</p>

<p><a href="http://35.232.255.82/opac.php">http://35.232.255.82/opac.php</a></p>

<p>This is very much a toy,
stripped down
<a href="https://en.wikipedia.org/wiki/Online_public_access_catalog">OPAC</a>.
The records are basic.
Not only do they not conform to
<a href="https://www.loc.gov/marc/">MARC</a>,
but they don't even conform to something
as simple as
<a href="https://www.dublincore.org/">Dublin Core</a>.

<p>I also don't provide options
to select different fields,
like author, title, or publisher fields.
Instead the search field below searches
all the fields
(author, title, publisher)
in our <b>books</b> table.</p>

<p>The key idea is to get a sense
of how an OPAC works, though.</p>

<h2>My Basic Library OPAC</h2>
<form method="post" action="search.php">
    <label for="search">Search:</label>
    <input type="text" name="search" id="search">
    <br>
    <label for="start_date">Start Date:</label>
    <input type="date" name="start_date" id="start_date">
    <br>
    <label for="end_date">End Date:</label>
    <input type="date" name="end_date" id="end_date">
    <br>
    <input type="submit" value="Search">
</form>


</body>
</html>
```

## PHP Search Form
I chose to stick with the `nano` editor instead of vim like the video, mostly because it is the only one I have really used. I did test out other editors
during section *3.2* but found I understand and like `nano`. I proceeded to use the code for provided for **search.php**. I chose to copy and paste, to avoid major issues in typing. 

```
<?php
// Load MySQL credentials
require_once 'login.php';

// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");

// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");

// Check if search query was submitted
if (isset($_POST['search'])) {
    // Sanitize user input to prevent SQL injection attacks
    $search = mysqli_real_escape_string($conn, $_POST['search']);

    // Get the start and end dates for the date range
    $start_date = mysqli_real_escape_string($conn, $_POST['start_date']);
    $end_date = mysqli_real_escape_string($conn, $_POST['end_date']);

    // Build the MySQL query with a WHERE
    // clause that includes the date range filter
    $query = "SELECT * FROM books WHERE
        (author LIKE '%$search%' OR
        title LIKE '%$search%' OR
        publisher LIKE '%$search%') AND
        copyright BETWEEN '$start_date' AND '$end_date'";

    // Execute the query
    $result = mysqli_query($conn, $query);

    // Check if any results were returned
    if (mysqli_num_rows($result) > 0) {
        // Loop through the results and output them
        while ($row = mysqli_fetch_assoc($result)) {
            echo "ID: " . $row["id"] . "<br>";
            echo "Author: " . $row["author"] . "<br>";
            echo "Title: " . $row["title"] . "<br>";
            echo "Publisher: " . $row["publisher"] . "<br>";
            echo "Copyright: " . $row["copyright"] . "<br><br>";
        }
    } else {
        echo "No results found.";
    }

    // Free up memory by closing the MySQL result set
    mysqli_free_result($result);
}

// Close the MySQL connection
mysqli_close($conn);

echo "<p>Return to search page: <a href='http://35.232.255.82/mylibrary.html'>http://35.232.255.82/mylibrary.html</a></p>";

?>
```



