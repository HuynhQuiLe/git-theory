# BACK-END-THEORY
**USUALLY USE** <br />
<br />
**Tải MYSQL BẰNG CÂU LỆNH TERMINAL:** docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=1234 -d -p 3306:3306 mysql <br />


**5 THONGN TIN KHI CAI DAT VAO MAY, BAT BUOC PHIA NHO** <br />
1. **HOST**: localhost ||127.0.0.1 <br/>
2. **username**: root (quyen cao nhat) <br/>
3. **password**: 1234 <br/>
4. **port**: 3306 (neu cai roi thi 3307) <br/>
5. update sau <br/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
#lenh SQL
# QUY TAC 
# - khong khoang cach, ky tu dac biet, khong viet hoa, khong chu so dau tien 
# - dat ten bang quy tac snake key. vidu: nguoi_dung, 

#TAO DATABASE MOI
# . viet hoa mau xanh duong la LENH SQL
CREATE DATABASE db_node37;
#chay database bang cach:
#1/ to khoi
#2/ nhan run current 
#3/ nhan reset 

#CHON DATA BASE DE THAO TAC 
USE db_node37;

#lenh tao table 
#users: user_id, user_name, email, age
CREATE TABLE users(
	user_id INT, 
	user_name VARCHAR(255), 
	email VARCHAR(255), 
	age INT(250)
);

#xoa table, database
DROP DATABASE db_node37;
DROP TABLE users;

DROP DATABASE IF EXISTS db_node37;

#CHINH SUA TABLE
#1/them cot
ALTER TABLE users
ADD COLUMN birth_day DATETIME;

ALTER TABLE users
ADD COLUMN user_status BOOLEAN;


#2/ xoa cot
ALTER TABLE users
DROP COLUMN birth_day;

#3/ chinh sua cot
ALTER TABLE users
MODIFY COLUMN birth_day DATE;




#CRUD delete --- DUNG CHO ROWS
#1/Create => them data
INSERT INTO users(user_id, user_name, email, age, birth_day, user_status) VALUES 
				 (1, 'Chris Le', 'chris@gnail.com', 27, '1996-10-25', 0),
				 (2, 'Nam Le', 'nam@gnail.com', 56, '1923-10-05', 1),
				 (3, 'David', 'david@gnail.com', 17, '2003-07-25', 0);



#2/Read
SELECT *
FROM users #=> 2 daong dau laf lay tat ca
WHERE user_id = 3 #=>chi lay 1 thang
ORDER BY user_id #=> sap xep theo email, age .... =>TU BE TOI LON
ORDER BY user_id DESC #=> sap xep theo email, age .... =>TU LON TOI BE




#3/Update => thay doi toan bo
UPDATE users SET age=1, email='abc'; #=> update toan bo
UPDATE users SET age=1, email='abc' WHERE user_id = 1; #where giong if - nhung chi co 1 dau = CHI UPDATE 1 THANG DUY NHAT




#4/Delete => thay doi toan bo
DELETE FROM users; #=> xoa taon bo
DELETE FROM users WHERE user_id = 1; #=>xoa 1 thang duy nhat => khong duoc dung khi di lam =>SU DUNG UPDATE DE AN NO DI


####CACH XOA BANG CACH UPDATE
UPDATE users SET user_status = 1 WHERE user_id = 3

SELECT *
FROM users
WHERE user_status = 1
# =< no chi hien nhung thang active ra thoi


#WHERE ma co dau = laf so sanh tuyet doi, co the dung LIKE: WHERE user_status LIKE 1 => = va LIKE la giong nhau - so sanh tuyet doi
#neu muon so sanh, lay trong chuoi do, chi can ton lai ky tu nay la lay ra thi dung: WHERE user_name LIKE '%abc%'
SELECT *
FROM users
WHERE user_name = 'abc'
WHERE user_name LIKE 'abc'
WHERE user_name LIKE '%abc%' #=>chuc nang tiem kiem
WHERE user_name LIKE 'abc%' #=>tiem kiem nhung thang nao bat dau bang tu khoa 'abc'
WHERE user_name LIKE '%abc' #=>tiem kiem nhung thang nao ket thuc bang tu khoa 'abc'


SELECT * #=> lay het tat ca column

SELECT user_name, user_status, email #=> chi lay nhung thang duoc liet ke ra


GROUP BY
HAVING






