# SQL-assignment
1.To create the tables
CREATE DATABASE AssignmentDatabase
drop database AssignmentDatabase

USE AssignmentDatabase
CREATE TABLE Pack_grades
(
	grade_id INT IDENTITY NOT NULL PRIMARY KEY,
	grade_name VARCHAR(50),
	min_price INT ,
	mix_price INT
)

USE AssignmentDatabase
CREATE TABLE packages
(
	pack_id INT IDENTITY NOT NULL PRIMARY KEY,
	speed INT ,
	strt_date DATE,
	monthly_payement INT,
	sector_id INT REFERENCES sectors(sector_id)
)

USE AssignmentDatabase
CREATE TABLE sectors
(
	sector_id INT IDENTITY NOT NULL PRIMARY KEY,
	sector_name varchar(50)
)

-------------------------------------------------------------------------

2.To create the Customers table and assign the priamary key

USE AssignmentDatabase
CREATE TABLE customers
(
	cust_id INT IDENTITY NOT NULL PRIMARY KEY,
	first_name varchar(15),
	last_name varchar(15),
	DOB DATE,
	DOJ DATE,
	city varchar(15),
	street varchar(15),
	stateofcustomer varchar(15),
	main_phone_num BIGINT ,
	sec_phone_num BIGINT,
	fax INT ,
	monthly_discount INT,
	pack_id INT REFERENCES packages(pack_id)
)

----------------------------------------------------------------
3.To insert the values into the Tables and display the table values

INSERT INTO Pack_grades
VALUES	('A',10000,15000),
  	('B',7000,10000),
  	('C',4000,7000),
  	('D',1000,4000),
	('E',200,900)

USE AssignmentDatabase
INSERT INTO sectors
VALUES  ('private'),
 	('business'),
  	('telecom'),
  	('govt'),
  	('IT')

INSERT INTO  packages 
  VALUES  
  (50,'2005/02/02',17000,1),
  (70,'2006/05/03',15000,2),
  (40,'2006/04/04',18000,3),
  (70,'2008/08/12',21000,4),
  (70,'2007/03/07',30000,5);

SELECT * FROM packages

  
Display all values in the customers table

SELECT * FROM customers

----------------------------------------------------------------------------------
4.TO display the internet speed,monthly payement,internet package number
SELECT speed as InternetSpeed ,pack_id as InternetPackageNumber,monthly_payement FROM packages

-------------------------------------------------------------------------------------
5.SELECT cust_id ,first_name,last_name,main_phone_num,sec_phone_num,pack_id FROM customers
-------------------------------------------------------------------------------------------
6.SELECT first_name,last_name,DOJ,monthly_discount,(monthly_discount+(monthly_discount*0.2)) as discountafteranadditionof20percent,(monthly_discount-(monthly_discount*0.2)) as discountafterreductionof20percent FROM customers
----------------------------------------------------------------------
7.SELECT pack_id AS packagenumber, speed, strt_date as datewhenthepackagebecameavailable,monthly_payement,monthly_payement*12 as Yearly_Payement from packages
------------------------------------------------------------------------
8.SELECT CONCAT(first_name,' ',last_name) as FULL_NAME,CONCAT(main_phone_num , ' ' , sec_phone_num) as CONTACT_DETAILS from customers
---------------------------------------------------------------------------
9.SELECT DISTINCT city FROM customers
----------------------------------------------------------------------------
10.SELECT DISTINCT stateofcustomer FROM customers
----------------------------------------------------------------------------
11.SELECT DISTINCT city,stateofcustomer FROM customers
----------------------------------------------------------------------------
12.SELECT concat(last_name,'  ' ,stateofcustomer) as CUSTOMER_AND_STATE from customers
----------------------------------------------------------------------------
13.SELECT first_name as FN,last_name as LN ,monthly_discount as DC,CONCAT(city ,' ' ,street) as FULL_ADDRESS from customers
----------------------------------------------------------------------------
14.SELECT DISTINCT monthly_discount FROM customers
----------------------------------------------------------------------------
15.SELECT DISTINCT pack_id FROM customers
----------------------------------------------------------------------------
16.SELECT first_name,last_name,pack_id from customers
where last_name = 'KING'
----------------------------------------------------------------------------
17.select * from packages
where speed = 5
----------------------------------------------------------------------------
18.
select first_name, last_name, pack_id ,monthly_discount from customers
where monthly_discount < 30
---------------------------------------------------------------------------
19.
select first_name, last_name, pack_id ,monthly_discount from customers
where DOJ < '2007/1/1'
---------------------
20.select * from customers
where pack_id = 2 OR pack_id=  1 OR pack_id =2+1
---------------------------------------------------------------------------
21.SELECT cust_id,first_name,last_name,city,stateofcustomer,pack_id FROM customers
WHERE pack_id != 27 AND pack_id !=  10 AND  pack_id != 3
-----------------------------------------------------------------------------
22.SELECT last_name, main_phone_num, monthly_discount,pack_id FROM customers
WHERE cust_id = 703 OR cust_id =314 OR cust_id =503
---------------------------------------------------------------------------
23.SELECT first_name,monthly_discount FROM customers
WHERE first_name  like '%e'
----------------------------------------------------------------------------
24.SELECT last_name,monthly_discount FROM customers
WHERE last_name  like '_d%'
-----------------------------------------------------------------------------
25.SELECT * FROM customers
WHERE first_name LIKE '%I%' OR first_name LIKE '%L%' OR first_name LIKE '%h%'
ORDER BY monthly_discount DESC
------------------------------------------------------------------------------
26.SELECT * FROM customers
WHERE last_name NOT LIKE '%a%'
ORDER BY pack_id 
------------------------------------------------------------------------------
27.SELECT * FROM customers
WHERE pack_id IS NULL
-------------------------------------------------------------------------------
28.SELECT CONCAT(first_name,last_name)  AS FULL_NAME FROM customers
WHERE monthly_discount NOT BETWEEN 20 AND 30
ORDER BY FULL_NAME
------------------------------------------------------------------------------
29.SELECT CONCAT(first_name, ' ' ,last_name)  AS FULL_NAME ,CONCAT(main_phone_num,' ' ,street) AS CONTACT_DETAILS ,monthly_discount AS DC FROM customers
WHERE monthly_discount  BETWEEN 11 AND 27
--------------------------------------------------------------------------------
30.SELECT * FROM customers
WHERE (city = 'NEWYORK' AND monthly_discount BETWEEN 20 AND 30) OR ((pack_id !=8 AND pack_id !=19 AND pack_id !=30) AND DOJ < '2007/1/1' ) 
------------------------------------------------------------------------------------
31.SELECT last_name,pack_id,DOB FROM customers
WHERE DOJ BETWEEN '2007/12/12' AND '2010/04/17'
-------------------------------------------------------------------------------------
32.SELECT pack_id,strt_date,speed FROM packages
WHERE strt_date < '2007/1/1'
------------------------------------------------------------------------------------
33.SELECT pack_id,strt_date, sector_id FROM packages
WHERE sector_id = 1
------------------------------------------------------------------------------------
34.SELECT pack_id,speed, sector_id FROM packages
WHERE speed = 50 OR speed = 100
------------------------------------------------------------------------------------
35.select last_name ,monthly_discount from customers
where stateofcustomer = 'orlando'
------------------------------------------------------------------------------------
36.select last_name,pack_id from customers
where pack_id = 9 OR pack_id = 18
OR
select last_name,pack_id from customers
where pack_id in(9,18)
------------------------------------------------------------------------------------
37.select first_name,main_phone_num,sec_phone_num from customers
where sec_phone_num IS NULL
------------------------------------------------------------------------------------
38.select first_name,monthly_discount ,pack_id from customers
where monthly_discount IS NULL
------------------------------------------------------------------------------------
39.select cust_id,lower(first_name),upper(last_name) from customers
where cust_id between 8 and 10
---------------------------------------------------------------------------------------
40.
a)select first_name,last_name ,CONCAT(LEFT(first_name,1),LEFT(last_name,3),'@myemail.com') as email from customers
b)select first_name,last_name ,CONCAT(LEFT(first_name,1),RIGHT(last_name,3),'@myemail.com') as email from customers
----------------------------------------------------------------------------------------
41.select last_name ,len(last_name) as lengthoflast_name from customers
where len(last_name)>9
------------------------------------------------------------------------------------------
42.
a)select first_name,last_name,main_phone_num,REPLACE(main_phone_num , '519' ,'$$$') as newphonenumber from customers
where main_phone_num like '%519%'
b)select first_name,last_name,main_phone_num,REPLACE(main_phone_num , '519' ,'$$$') as newphonenumber from customers
where main_phone_num like '519%'
----------------------------------------------------------------------------------------------
43.
select  first_name,last_name,monthly_discount, monthly_discount+(monthly_discount*0.197) as monthlyiscountafteradditionof19, 
			ROUND(monthly_discount+(monthly_discount*0.197),2) as Ronudedmonthly_discount,
			FLOOR(monthly_discount+(monthly_discount*0.197)) as florredmonthly_discount,
			CEILING(monthly_discount+(monthly_discount*0.197)) as ceiledmonthly_discount
from customers
--------------------------------------------------------------------------------------------------
44.select first_name,DOJ,dateadd(dd,-10,DOJ) AS DOJMINUS10DAYS,dateadd(dd,+10,DOJ) AS DOJPLUS10DAYS,dateDiff(dd,DOJ,DOB)AS DIFFERENCEINDAYS from customers
------------------------------------------------------------------------------------------------
45.SELECT first_name,DOB,DATEDIFF(yy,DOB,GETDATE()) as Age FROM customers
---------------------------------------------------------------------------------------------------
46.select * from customers
where DOB = GETDATE()
-----------------------------------------------------------------------------------------------------
47.select first_name,DOJ,DATEDIFF(yy,DOJ,getdate()) as Experience from customers
where DATEDIFF(yy,DOJ,getdate()) >5
----------------------------------------------------------------------------------------------------
48.select concat(first_name,cast(DOJ as varchar)),concat(last_name,cast(monthly_discount as int)) from customers
----------------------------------------------------------------------------------------------------------------------
49.select last_name,CONCAT(UPPER(stateofcustomer),' ' ,cust_id) , concat(convert(varchar(11),DOJ,106),'  ',CONVERT(varchar(11),DOB,106)) from customers
where last_name LIKE '[S|k]%'
OR
select last_name,CONCAT(UPPER(stateofcustomer),' ' ,cust_id) , concat(convert(varchar(11),DOJ,106),'  ',CONVERT(varchar(11),DOB,106)) from customers
where  substring(last_name,1,1)in('S','k')
--------------------------------------------------------------------------------------------------------------------------
50
a)
select first_name,last_name,DOB,main_phone_num,sec_phone_num,ISNULL(main_phone_num,'N/A') as newmainphonenumber,ISNULL(sec_phone_num,'N/A') as newsecphonenum from customers
where pack_id = 4 OR main_phone_num IS NULL OR sec_phone_num IS NULL
OR
select first_name,last_name,DOB,main_phone_num,sec_phone_num,COALESCE(main_phone_num,'N/A') as newmainphonenumber,COALESCE(sec_phone_num,'N/A') as newsecphonenum from customers
where pack_id = 4 OR main_phone_num IS NULL OR sec_phone_num IS NULL

b)select first_name,last_name,DOB,main_phone_num,sec_phone_num from customers
where YEAR(DOB) = '1974'
-------------------------------------------------------------------------------------------------------------------------------
51.
SELECT first_name,last_name,monthly_discount,
	CASE
		WHEN monthly_discount BETWEEN 0 AND 10 THEN 'A'
		WHEN monthly_discount BETWEEN 11 AND 20 THEN 'B'
		WHEN monthly_discount BETWEEN 21 AND 30 THEN 'C'
		ELSE 'D'
	END 'Grades' 
FROM customers
--------------------------------------------------------------------------------------------------------------------
52.select min(last_name) as Lowestlastname from customers
--------------------------------------------------------------------------------------------------------
53.select AVG(monthly_payement) as Avgofmonthlypayement from packages group by monthly_payement
-------------------------------------------------------------------------------------------------
54.select max(last_name) as Lowestlastname from customers
------------------------------------------------------------------------------------------------
55.select count(pack_id)as numberofpackages from packages
----------------------------------------------------------------------------------
56.select count(*) as numberofrecords from customers
-------------------------------------------------------------------------------------
57.select count(distinct(stateofcustomer)) as Distinctstates from customers
------------------------------------------------------------------------------------
58.select count(distinct(speed)) as Distinctspeeds from packages
------------------------------------------------------------------------------------
59.select count(fax)from customers
where fax IS NOT NULL
-----------------------------------------------------------------------------------
60.select count(fax) from customers
where fax IS NULL
----------------------------------------------------------------------------------------------------
61.select max(monthly_discount) as highestmonthlydiscount, min(monthly_discount) as lowestmonthlydiscount ,avg(monthly_discount) from customers
------------------------------------------------------------------------------------------------------
62.select stateofcustomer,count(cust_id)as cutomersofstate from customers
group by stateofcustomer
----------------------------------------------------------------------------------------------------
63.select speed,avg(monthly_payement)  as Avgofmonthly_payement from packages
group by speed
-------------------------------------------------------------------------------------------------
64.select stateofcustomer,count(distinct(city)) from customers
group by stateofcustomer
------------------------------------------------------------------------------------------------
65.select sector_id,max(monthly_payement) from packages
group by sector_id
-----------------------------------------------------------------------------------------------------
66.
a)select pack_id,avg(monthly_discount) from customers
group by pack_id
b)select pack_id,avg(monthly_discount) from customers
where pack_id = 2 or pack_id = 3
group by pack_id
-----------------------------------------------------------------------------------------------------
67.select max(monthly_payement),min(monthly_payement),avg(monthly_payement) from packages
group by speed
----------------------------------------------------------------------------------------------------
68.
a)select pack_id,count(cust_id) from customers
group by pack_id
b)select pack_id,count(cust_id) from customers
where monthly_discount > 20
group by pack_id
c)select pack_id,count(cust_id) from customers
group by pack_id
having count(cust_id) >=100
--------------------------------------------------------------------------------------------------
69.Select  stateofcustomer,city, count(cust_id) as NumberofCusteomers from customers
group by stateofcustomer,city
-------------------------------------------------------------------------------------------------
70.
a)select city,avg(monthly_discount) as Avgmonthly_discount from customers
group by city
b)select city,avg(monthly_discount) as Avgmonthly_discount from customers
where monthly_discount > 20
group by city
------------------------------------------------------------------------------------------------
71.
a)select stateofcustomer,min(monthly_discount) from customers group by stateofcustomer
b)select stateofcustomer,min(monthly_discount) from customers 
group by stateofcustomer
having min(monthly_discount) > 10
----------------------------------------------------------------------------------------------
72.select speed , count(pack_id) from packages
group by speed
having count(pack_id ) > 8
---------------------------------------------------------------------------------------------
73.
a)
select  first_name,last_name,c.pack_id ,speed from customers as c,packages as p
where c.pack_id = p.pack_id
b)select  first_name,last_name,c.pack_id ,speed from customers as c,packages as p
where c.pack_id = p.pack_id and p.pack_id in(2,4)
order by last_name
-------------------------------------------------------------------------------------------------
74.
a)select pack_id,speed,monthly_payement,sector_name from packages as p,sectors as s
where p.sector_id = s.sector_id
b)
select Concat(first_name,'  ',last_name)as Customername,p.pack_id,speed,monthly_payement,sector_name from packages as p INNER JOIN sectors as s
ON p.sector_id = s.sector_id 
INNER JOIN customers as c
ON c.pack_id = p.pack_id  
c)
select Concat(first_name,'  ',last_name)as Customername,p.pack_id,speed,monthly_payement,sector_name from packages as p INNER JOIN sectors as s
ON p.sector_id = s.sector_id AND sector_name = 'business'
INNER JOIN customers as c
ON c.pack_id = p.pack_id  
----------------------------------------------------------------------------------------------------------------
75.select Concat(first_name,'  ',last_name)as Customername,p.pack_id,speed,monthly_payement,sector_name from packages as p INNER JOIN sectors as s
ON p.sector_id = s.sector_id AND sector_name = 'private'
INNER JOIN customers as c
ON c.pack_id = p.pack_id and year(DOJ) = '2007'
-------------------------------------------------------------------------------------------------------------------
76.select pack_id,speed,monthly_payement,grade_name from packages as p ,Pack_grades as pg
 where p.pack_id  = pg.grade_id
-----------------------------------------------------------------------------------------------------------------
77.
a) select first_name,last_name ,monthly_payement,speed from customers as c INNER JOIN packages  as p
 ON p.pack_id  = c.pack_id
b) select first_name,last_name,speed,monthly_payement from customers as c LEFT OUTER JOIN packages as p
ON c.pack_id = p.pack_id
c) select first_name,last_name,speed,monthly_payement from customers as c RIGHT OUTER JOIN packages as p
ON c.pack_id = p.pack_id OR c.cust_id = NULL
d)select first_name,last_name,speed,monthly_payement from customers as c FULL OUTER JOIN packages as p
ON c.pack_id = p.pack_id 
------------------------------------------------------------------------------------------------------------------
78.select c1.first_name, c1.last_name  from customers as c1 JOIN customers as c2
on c1.cust_id = c2.cust_id and c1.first_name = 'Amado' and c1.last_name = 'Taylor'
--------------------------------------------------------------------------------------------------------------------
79.select first_name,last_name,monthly_discount from customers
where monthly_discount< 
(
select monthly_discount from customers
where cust_id = 103
)
------------------------------------------------------------------------------------------------------------------
80.
select pack_id,speed  from packages 
where speed = 
(
select speed from packages where pack_id  = 10
)
---------------------------------------------------------------------------------------------------------------
81.select  first_name,last_name ,city,stateofcustomer  from customers
where stateofcustomer = 
(
select stateofcustomer from customers
where cust_id=170
)
----------------------------------------------------------------------------------------------------------------
82.select pack_id,speed,sector_id from packages where sector_id=(select sector_id from packages where pack_id=10);
--------------------------------------------------------------------------------------------------------------
83.select firstname,lastname,join_date from customers where join_date > (select join_date from customers where cus_id=540);
---------------------------------------------------------------------------------------------------------------
84.select first_name,last_name,DOJ from customers where year(DOJ) =(select year(DOJ)from customers where cus_id=372) 
 and month(DOJ)= (select MONTH(DOJ) from customers where cust_id =372);
*----------------------------------------------------------------------------------------------------------------
85. select first_name,last_name,city,stateofcustomer,c.pack_id from customers as c,packages as p where c.pack_id=p.pack_id and speed=5;
------------------------------------------------------------------------------------------------------------------------
86. select pack_id,speed,strt_date from packages where year(strt_date) IN (select year(strt_date) from customers where pack_id=7);
If the inner query returns more than one value then we need to use the IN 
----------------------------------------------------------------------------------------------------------------------------
88. select first_name ,last_name, monthly_discount   from customers as c,packages as p
 where p.pack_id = c.pack_id AND monthly_payement > (select avg(monthly_payement) from packages )
--------------------------------------------------------------------------------------------------------------------------
89. select first_name,city,stateofcustomer,DOB,monthly_discount from customers
where DOB=(select DOB from customers where cust_id=179) and monthly_discount >
(select monthly_discount from customers where cust_id=107);
----------------------------------------------------------------------------------------------------------------------
90select * from packages where speed =
(select speed from packages where pack_id=30) and monthly_payement >
(select monthly_payement from packages where pack_id=7)
 -----------------------------------------------------------------------------------------------------------------------
91.
 select pack_id,speed,monthly_payement from packages where monthly_payement >
(select max(monthly_payement) from packages where speed='50'); 
-------------------------------------------------------------------------------------------------------------------------
92. select pack_id,speed,monthly_payement from packages where monthly_payement >
(select min(monthly_payement) from packages where speed='50'); 
--------------------------------------------------------------------------------------------------------------------------
93. select pack_id,speed,monthly_payement from packages where monthly_payement <
(select min(monthly_payement) from packages where speed='50');
--------------------------------------------------------------------------------------------------------------------------
94.
select first_name,monthly_discount,pack_id from customers where monthly_discount < 
(select avg(monthly_discount) from customers) and pack_id =(select pack_id from customers where first_name='Kelvin');​ 
