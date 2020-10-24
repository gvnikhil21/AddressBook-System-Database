# AddressBook-System-Database

### Create addressbook_service database
```
create database addressbook_service;
```
### Switch to addressbook_service database
```
use addressbook_service;
```
### Create Addressbook Table
```
create table addressbook(
first_name          varchar(20) not null,
last_name           varchar(20) not null,
address             varchar(50) not null,
city		    varchar(20) not null,
state               varchar(20) not null,
zip                 int(6) not null,
phone_number        varchar(10) not null,
email_id	    varchar(30) not null,
primary key         (first_name,last_name)
);
```