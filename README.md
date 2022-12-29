# SpringBoot-CRUD-On-AWS-Elastic-BeanStalk

This repository is an extension of https://github.com/sangamsahai/Spring-Boot-Mysql-CRUD-App

The above repository has the code for a basic SpringBoot CRUD app which was tested on local machine.
In this repo, we deploy the same app on AWS Elatic Beanstalk. 

Steps - 
1) Create an environment in Elastic Beanstalk choosing Java as the platform.
<img width="1728" alt="Screen Shot 2022-12-28 at 8 46 31 PM" src="https://user-images.githubusercontent.com/10198686/209905595-c4ea3c30-7d67-46ec-91f8-1dc4b8dfa1a2.png">

2) Create a mysql DB instance inside that environment
<img width="1728" alt="Screen Shot 2022-12-28 at 8 58 40 PM" src="https://user-images.githubusercontent.com/10198686/209905658-30f69a27-50a5-4dd1-9c3b-98e38e29055b.png">
Run the folling DDL in the new created DB - 

```
 create database store_database;

 use store_database;
 
 create table if not exists product_inventory
 (id bigint not null primary key auto_increment,
 product_name varchar(32) not null,
 color varchar(11),
 price int
 );
```

3) Make the folliwng changes in the Java code
- in the properties file, use the new DB endpoint and new DB useranme and password
- comment out the tests
- make the health check API at the root level

4) Build the java code to create the jar

5) Upload and Deploy the jar in BeanStalk
<img width="1728" alt="Screen Shot 2022-12-28 at 9 17 56 PM" src="https://user-images.githubusercontent.com/10198686/209905760-5054faca-4cdf-493c-a2ae-acf9fcc7cd5a.png">
<img width="1728" alt="Screen Shot 2022-12-28 at 9 20 46 PM" src="https://user-images.githubusercontent.com/10198686/209905787-42f59ca2-5bcd-4182-b395-dd4985567bcf.png">


6) Test the API on postman.<img width="1728" alt="Screen Shot 2022-12-28 at 9 19 52 PM" src="https://user-images.githubusercontent.com/10198686/209905837-8891b32e-e3d0-4525-9c43-f0cda658f981.png">
<img width="1728" alt="Screen Shot 2022-12-28 at 9 20 12 PM" src="https://user-images.githubusercontent.com/10198686/209905845-62d063bf-d69b-4669-b2f4-64d2f369fc18.png">
<img width="1728" alt="Screen Shot 2022-12-28 at 9 20 22 PM" src="https://user-images.githubusercontent.com/10198686/209905853-c356647f-1d0c-40dd-8207-0d80e01d948b.png">
