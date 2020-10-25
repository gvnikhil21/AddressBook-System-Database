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
### Insert contacts to addressbook table
```
insert into addressbook values
('gv', 'nikhil', 'main road', 'jharsuguda', 'odisha', '768201', '1234567890', 'gvxyz@gmail.com'),
('kane', 'warner', 'ecil', 'hyderabad', 'telangana', '500062', '0123456789', 'kanexyz@gmail.com'),
('nikhil', 'gv', 'sector-1', 'rourkela', 'odisha', '769008', '9871234560', 'nikhilxyz@gmail.com'),
('jonny', 'holder', 'main road', 'bangalore', 'karnataka', '530068', '6549870123', 'holderxyz@gmail.com');
```
### Retrieve all contacts from addressbook
```
select * from addressbook;
```
### Edit existing contact person using name
```
update addressbook
set address='lalbagh' where first_name='jonny' and last_name='holder';
``` 
### Delete contact person using name
```
delete from addressbook
where first_name='jonny' and last_name='holder';
```