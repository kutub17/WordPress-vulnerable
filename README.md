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
