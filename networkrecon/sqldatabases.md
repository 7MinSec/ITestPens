# SQL Databases

## SQLite Recon: Basics
This exercise involved doing some sqlite recon against a .db file.  I used [this site](https://www.sqlitetutorial.net/sqlite-commands/) as a basic primer for sqlite3, then issued the `sqlite3` command at the terminal.  To glean further information about the database, I used the following commands:

````
.open database.db
.databases (to check open databases)
.tables (to list tables)
select * from TABLE_NAME (to retrieve data/flags)
````
