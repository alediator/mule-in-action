Mule JDBC Transport Demos
---------------------------------

The examples use an embedded Apache Derby database and ActiveMQ instance.
You'll need to edit the global properties and dataSource as appropriate to use
your own servers.  A MySQL schema is in src/main/sql.

You'll also need to edit the IMAP host properties using the global-properties for
each example to point to a valid IMAP server (the unit tests use a mock IMAP
server.)

Start the examples with the script that is relevant for your OS.

# Simple command line create and import schema
/jdbc$ mysqladmin -u root -p create monitoring
jdbc$ mysql -u root -p monitoring
[...]
mysql> create user miatest;
mysql> GRANT ALL ON monitoring.* TO 'miatest'@'localhost';
[...]
/jdbc$ mysql -u miatest -p monitoring < src/main/sql/monitoring.sql

# Simple drop user and database
jdbc$ mysql -u root -p monitoring
[...]
mysql> drop user miatest;
[...]
/jdbc$ mysqladmin drop monitoring -u root -p
