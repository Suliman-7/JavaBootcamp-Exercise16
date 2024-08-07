

create database store ;

create table countraies (
    code int primary key ,
    name varchar(20) unique ,
    continent_name varchar(20) not null
);

insert into countraies values(966 , 'Saudi Arabia' , 'Asia');
insert into countraies values(987 , 'Belgium' , 'Europe');
insert into countraies values(789 , 'Egypt' , 'Africa');

update countraies set name='England' where code='987';


create table users (
    id int primary key ,
    full_name varchar(20) ,
    email varchar(20) unique ,
    gender char(1) check ( gender='m' or gender='f' ) ,
    date_of_birth varchar(15) ,
    created_at datetime ,
    country_code int ,
    foreign key (country_code) references countraies(code)
);

insert into users values (1,'mohammed ahmed','moha@email.com','m','2000/01/01','2010/06/10',966);

insert into users values (2,'yasser khalid','yas@email.com','m','2001/10/07','2010/10/11',789);

insert into users values (3,'maha abdullah','maha@email.com','f','2005/12/26','2015/01/30',987);



create table orders (
    id int primary key ,
    user_id int ,
    foreign key (user_id) references users(id),
    status varchar(6) check ( status='start' or status='finish' ),
    created_at datetime
);

insert into orders values (4,1,'start','2022/09/03');
insert into orders values (5,2,'finish','2023/11/10');
insert into orders values (6,3,'finish','2023/04/12');


create table order_products (
    order_id int ,
    foreign key (order_id) references orders(id),
    product_id int ,
    foreign key (product_id) references products(id),
    quantity int default 0
);

insert into order_products values (4,7,20);
insert into order_products values (5,8,100);
insert into order_products values (6,9,30);




create table products(
    id int primary key ,
    name varchar(10) not null ,
    price int default 0 ,
    status varchar(10) check ( status='valid' or status='expired' ) ,
    created_at datetime
);

insert into products values (7,'watch',2000,'valid','2024/07/07');
insert into products values (8,'machine',2000,'valid','2020/01/07');
insert into products values (9,'coffee',2000,'expired','2017/01/04');

delete from products where id=7;



select * from countraies ;

select * from users ;

select * from orders ;

select * from products ;

select * from order_products ;

