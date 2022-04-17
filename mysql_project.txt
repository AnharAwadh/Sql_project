create database store;

create table countries(
    codee int primary key ,
   namee varchar(20) unique ,
    countinet_name varchar(20) not null
);
#crate table users
create table users(
   id int primary key ,
    full_name varchar(20),
  emaile  varchar(20) unique ,
  gender char(1) check(gender='F' or gender='M'),
  date_of_brith varchar(15),
  created_at  TIMESTAMP DEFAULT now(),#Add default datetime to created_at column
  country_code int ,
    foreign key (country_code) references  countries (codee)

);

#create table orders
create table orders(
    id int primary key ,
    user_id int ,
stuaus varchar(6) check(stuaus='start' or stuaus='finsh'),
     created_at datetime,
     foreign key (user_id) references users (id)
);



create table products(
    id int primary key ,
  namee  varchar(10) not null ,
  price int default 0,
  statuse varchar(10) check(statuse='valid' or statuse='expired'),
  created_at TIMESTAMP DEFAULT now() #Add default datetime to created_at column 
);

create table order_products(
    order_id int,
    prodect_id int ,
  quantity int default 0 ,
  primary key (order_id,prodect_id),
   foreign key (order_id) references orders(id),
foreign key (prodect_id) references products(id)
);
#add data to all tables
insert  into countries values (1,'Anhar','Asa');
insert  into users values(1,'Anhar Awadh','anhar@gmail.com','F','1996-06-06','2020-09-06 10:55:22',1);
insert  into orders values(1,1,'start','2020-10-08 12:45:22');
insert  into products values(1,'Ahamed',30,'expired','2021-11-08 11:35:33');
insert  into products values(2,'Ali',20,'expired','2021-12-05 10:55:33');
insert  into order_products values(1,1,3);
update countries set namee= 'Aisha' where codee =1;#Update row name from countries table.
delete from products where id='2'; #Delete row from products table

