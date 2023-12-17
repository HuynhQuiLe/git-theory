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
<br/>
<br/>



#THONG TIN CO BAN BE <br/>
<br/>
// LY THUYET <br/>
app.get("/demo/:id1/:email1", (req, res) => { <br/>
  // C1: LAY TU URL <br/>
  //   - query string: domain/demo?id=123&email=demo@gmail.com <br/>
  const { id, email } = req.query; <br/>
<br/>
  //   - query param: domain/demo/123/demo@gmail.com => phai dinh nghia param o dong 7 <br/>
  const { id1, email1 } = req.params; <br/>
<br/>
  //C2: LAY TU JSON <br/>
  let { name, age, role } = req.body; <br/>
<br/>
  //   res.send("Hello"); <br/>
  res.status(200).json({ name, age, role }); <br/>
}); <br/>
<br/>
app.listen(PORT, (req, res) => { <br/>
  console.log(`Server is running on  PORT ${PORT}`); <br/>
});<br/>
<br/>
// KET NOI VOI CSDL  bang cach truyen thong<br/>
<br/>
const mysql2 = require("mysql2");<br/>
<br/>
const connect = mysql2.createConnection({ <br/>
  host: "localhost",<br/>
  user: "root",<br/>
  password: "1234",<br/>
  port: 3306,<br/>
  database: "youtube_app",<br/>
});<br/>

app.get("/get-video", (req, res) => {<br/>
<br/>
  // su dung cach truyen thong<br/>
  try {<br/>
    connect.query("SELECT * FROM video", (err, result) => {<br/>
      //cau lenh lay duoc bang do ra<br/>
      res.status(200).json(result);<br/>
    });<br/>
  } catch (error) {<br/>
    res<br/>
      .status(400)<br/>
      .json({ message: "Đã có lỗi xảy ra, không tìm thấy tài nguyên." });<br/>
  }<br/>
}, );<br/>


<br/>
<br/>
<br/>
<br/>

DATABASE FIRST <br/>

yarn add sequelize-auto <br/>

<br/>
run: yarn sequelize-auto -h <host> -d <database> -u <user> -x [password] -p [port] --dialect [dialect] -o [/path/to/models] -l es6 <br/>
=>>>> yarn sequelize-auto -h localhost -d youtube_app -u root -x 1234 -p 3306 --dialect mysql -o src/models -l es6 (es6 la co reuired, cin neu muoon viet theo moudle thi es6 => esm)
<br/> moi lan thay doi database - them cot hoac table  => chay lai dong nay
<br/>

  let data = await model.video.findAll(); //thay the cho SELECT * FROM video 
<br/>
neu muon co WHERE thi: <br/>
let data = await model.video.findAll({ <br/>
	where: {<br/>
 		video_id: 2
 		}<br/>
}); <br/>

<br/>
de su dung LIKE %% thi:
<br/> import {Sequelize} from 'sequelize'
<br/> let Op = Sequelize.Op
<br/> let data = await model.video.findAll({ <br/>
	where: {<br/>
 		video_id: 2, <br/>
   		video_name: { <br/>
     			[Op.like]: '%code%' <br/>
		}<br/>
 		}<br/>
}); <br/>

neu muon lay 1 so cot nhat dinh thoi: SELECT video_id, video_name FROM video <br/>
<br/>let data = await model.video.findAll({ <br/>
	where: {<br/>
 		video_id: 2
 		}<br/>
	
 attributes: ["video_id", "video_name"] <br/>
 },
 
 ); <br/>
<br/>
khi lien ket data cau 2 hoac nhieu table thi co the dung  include: ["user", "type"], **user duoc lay trong init-models, giong 100% as
<br/> hoac co the dung include:[model.user, model.video_type] => phai xoa as trong init-models
<br/>
<br/>
<br/>
<br/>
BCRYPT

<br/>1. cho phep ma hoa
<br/><br/> bcrypt.hashSync(pass_word, 10),
<br/>2. cho phep so anh du lieu tho vs du lieu ma hoa
<br/> (bcrypt.compareSync(pass_word, emailExist.pass_word) => tham so 1 la du lieu tho, tham so 2 la du lieu da ma hoa
<br/><br/>
<br/>
JWT
<br/><br/> 1. ma hoa du lieu
<br/> 2. kiem tra token hop le
<br/><br/> 3. giai token
<br/>
<br/> luoon luoon co 3 pahn de tao ra token, mooix cai ngan cach bang dau cham (.)
<br/> 1. HEADER: chua giai thuat, han su dung... (cau hinh)
<br/> 2. PAYLOAD: DATA
<br/>3. SIGNATURE: khoa bi mat
<br/>
<br/>
<br/>1. ma hoa du lieu<br/>
createToken: (data) => {<br/>
    let token = jwt.sign({ data }, "BIMAT", { algorithm: "HS256" });<br/> => TS1: PAYLOAD; TS 2: SIGNATURE; TS3: HEADER
    return token;<br/>
  },<br/>

  <br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/><br/> UPLOAD HINH ANH
<br/> c1: luu tran sOurce BE
<br/>c2: luu tran sOurce ben thu 3
<br/>c3: luu truc tiep tren column cua table
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/> **PRISMA CHUC NANG SERACH**:

let user = await this.prisma.users.findMany({<br/>
      where: {<br/>
        full_name: {<br/>
          contains: full_name,<br/>
        },<br/>
      },<br/>
    });<br/>



><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
