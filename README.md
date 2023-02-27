


![store](https://user-images.githubusercontent.com/122470877/221504493-c6647a2d-4be4-44cc-8857-abec7ef2e0c7.png)

#DDL

create database store;

 create table countries(
    code int (10)primary key ,
    name varchar(20) unique ,
    continent_name varchar(20) not null

);

 create table users(
    id int (10)primary key ,
    full_name varchar(20),
    email varchar(20) unique ,
    gender char(1) check ( gender='m'or gender='f' ),
    date_of_birth varchar(15),
    created_at datetime ,
    country_code int (10),
    foreign key (country_code) references countries (code)


);

    create table orders(
    id int (10)primary key ,
    user_id int (10),
    status varchar(6) check ( status='start' or status='finish' ),
    created_at datetime,
    foreign key (user_id) references users (id)

    );

 create table order_products(
    order_id int (10),
    product_id int(10),
    quantity int default 0,
    foreign key (order_id) references orders (id),
    foreign key (product_id) references products (id)

);

 create table products(
    id int (10) primary key,
    name varchar(10) not null ,
    price int(10) default 0,
    status varchar(10) check ( status='valid' or status='expired' ),
    created_at datetime
    );
    alter table products add column created_at timestamp default now();
    alter table orders add column created_at timestamp default now();
    alter table users add column created_at timestamp default now();

#DML

    insert into countries values (010,'Riadh','Asia');
    insert into users values (200,'samah Abdullah','samah@gmail.com','f','2000/3/4',now(),010);
    insert into orders values (1,200,'start',now());
    insert into order_products values (1,19,4);
    insert into products values (19,'laptop',5000,'expired',now());

    update countries set continent_name='Africa' where code=010;
    delete from products where id=19;

  select * from countries;
  select * from products;
  select * from users;
  select * from orders;
