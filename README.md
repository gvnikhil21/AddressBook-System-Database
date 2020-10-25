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
### Retrieve contact by city or state
```
select * from addressbook
where city='hyderabad' or state='odisha';
```
### Count contacts in addressbook by city and state
#### Count contacts by city
```
select city, count(city) as 'no. of contacts' from addressbook
group by city;
```
#### Count contacts by state
```
select state, count(state) as 'no. of contacts' from addressbook
group by state;
``` 
### Retrieve entries sorted by person's name for a given city
```
select * from addressbook 
where city='hyderabad' 
order by concat(first_name,' ',last_name);
```
### Identify each addressbook with name and type
#### Alter addressbook to add addressbook_name
```
alter table addressbook
add addressbook_name varchar(10) first;
```
#### Alter addressbok to add addressbook_type
```
alter table addressbook
add addressbook_type varchar(10) after addressbook_name;
```
#### Update values for addressbook_name and addressbook_type columns
```
update addressbook set 
addressbook_name='bookOne' where first_name in ('gv','jonny','kane','nikhil');

update addressbook 
set  addressbook_type=
case first_name
when 'gv' then 'personal'
when 'jonny' then 'office'
when 'nikhil' then 'personal'
when 'kane' then 'office'
end;
```
#### Retrieve contact by addressbook name or type
```
select * from addressbook where addressbook_name='bookOne';
select * from addressbook where addressbook_type='personal';
```
### Get count of contacts by addressbook type
```
select addressbook_type, count(addressbook_type) as 'no. of contacts' from addressbook
group by addressbook_type;
```
### Add person to both family and friend addressbook type
#### Change primary key to first_name + last_name + addressbook_type
```
alter table addressbook drop primary key;
alter table addressbook add primary key (addressbook_type, first_name,last_name);
```
#### Add contact to friend and family
```
insert into addressbook 
values
('bookTwo','friend','gv', 'nikhil', 'main road', 'jharsuguda', 'odisha', '768201', '1234567890', 'gvxyz@gmail.com'),
('bookTwo','family','gv', 'nikhil', 'main road', 'jharsuguda', 'odisha', '768201', '1234567890', 'gvxyz@gmail.com');
```