#WordPress vulnerable

This is a modified version of WordPress 3, to allow for easy SQL injection. This was created as an educational project. Do not use in production.

There is at least an easy injection in the comment field, allowing change of comment parameters and a more difficult one in the login form allowing login bypass.

#Installation

##Using the provided example database

Edit wp-config.php and fill the following fields with your MySQL data:

    DB_NAME, DB_USER, DB_PASSWORD, DB_HOST

In addition for the provided example database to work set the options WP_SITEURL and WP_HOME to the full address of the website.

Afterwards load the provided db.sql into your database and remove it from your htdocs directory.

Navigate to the website and you should be able to log in using the username "admin" with the password "admin123".

##Setting up a new wordpress site

Remove wp-config.php and create your own configuration following the WordPress installation instructions.

For the second task set "Comment must be manually approved" under Settings -> Discussion in the admin area.

# Tasks

There are two SQL injection tasks, the first one is an easy one, the second one is more difficult.

## First task

The provided wordpress installation has configured, that all comments need to be approved by an administrator. Your target is to post a comment without admin approval, which is publically visable, by setting the approval flag with an SQL injection.

Visit the first blog entry on the website and find the comment field. Enter some text containing an apostrophe ' and watch what happens. Use your SQL knowledge to get your comment approved.

## Second task

As you don't only want to post comments but, as you are really evil, you also want to change everything else on the website the second task is to get access to the administrator area. Navigate to the login form using the link on the bottom left side.

As some help this is how wordpress validates your inputs:

1. Get all rows from the user table where the username matches your input.
2. Exit if no row matches
3. Check what hash function is used in the password hash found in the matching row(ie plain md5 hash)
4. Hash the entered password using that same hash function
5. If the hash equals the password in the database record log the user in using the user ID found in the database

All of this information could of course be found out by any programmer by reading the available source code.
