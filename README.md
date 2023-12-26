
**DOCKER** <br />
<br /> kiem tra version docker -v
<br /> Trong docker cos container(may ao) => mooix container co image (ung dung), volumn giong nhu o cung roi
<br /><br />  moi container se co 2 port:    port public:port private
<br /><br />
<br /><br /> Tao container: docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=1234 -p 3306:3306 mysql:latest
<br /><br />
<br /><br />
<br /><br /><br /> thao tac lenh co ban CONTAINER
<br /><br /> xem danh sach container dang chay: docker ps 
<br /><br /> xem danh sach TAT CA container dang chay va khong chay: docker ps -a
<br /><br /> chay container: co 2 cach: docker start [name container] // hoac docker start [4 ky tu dau tien cua chuoi ID]
<br /><br /> dung container: tuong tu: docker stop [name container] // hoac docker stop [4 ky tu dau tien cua chuoi ID]
<br /><br /> restart: docker restart
<br /><br /><br /> delete conatiner: docker delete [name container] // hoac docker delete [4 ky tu dau tien cua chuoi ID] (docker -f delete [name container] de bat buoc xoa)
<br /><br /> tao container : docker run -d -p 80:80 docker/getting-started
<br /><br />
<br /><br />
<br /><br /><br /><br /><br /> thao tac lenh co ban IMAGE
<br /><br />xem danh dach image: docker images
<br /><br /><br /> xoa image: docker rmi [name image]// [4 ky tu dau tien cua chuoi ID] =< phai xoa container dang su dung image thi moi xoa image duoc
<br /><br /> duplicate image: docker tag [name image]:[tag] [new name]:[new tag]( vi du: docker tag mysql:latest mysql_copy:v1)
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br /> cac buoc day image len hub docker
<br /><br /> b1: phai doi ten sao cho trung: docker tag [name image]:[tag] [new name]:[new tag]
<br /><br /> b2: push: docker push chris27101991/test001:tagname (luu y phai dang nhap)
<br /><br /> Muon lay image cua nguoi khac: docker pull chris27101991/test001:tagname
<br /><br /> Login docer desktop bang 2 cach:
<br /><br /> c1: co the lam bang chuojt nhu binh thuong
<br /><br /><br /> c2: docker login => sau do nhap du lieu vao (user name thi vao hub docker copy; password thi vao my account => security=>access token
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br /> CACH LAY DATA KHONG CAN THONG QUA TABLE PLUS
<br /><br /> b1: vao may ao: docker exec -it [ten may ao/ conatiner] / hoac[4 ky tu dau cua ID] bash
<br /><br /> => day dang la terminal cua may ao - khong con la cua may minh nua
<br /><br /> b2: dang nhap vao table plus : mysql -u root -p
<br /><br /> b3: nhap password
<br /><br /> => luc nay dang la terminal cua mysql
<br /><br /><br /> show database: show databases;
<br /><br /> chon database: USE youtube_app;
<br /><br /> show table: show tables;
<br /><br /> SELECT * from video;
<br /><br />
<br /><br /> =====> de thoat ra: exit; (2 lan) de tro ve may minh
<br /><br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br /> DONG GOI SOURCE CODE => IMAGE
<br /><br />-----------------------HTML TRHUAN---------
<br /><br /> B1: tao file Dockerfile => cap ngaoi cung.
<br /><br /> dong goi html va react: 
<br /><br /> b1: cai dat ung dung tran mang: FROM nginx
  <br /><br /> WORKDIR /usr/share/nginx/html  =>> khai bao 1 duong dan duoc lap di lap lai 
<br /><br /><br /> b2: copy het tat ca nhung source minh dang co VAO may ao : COPY . .
<br /><br /> B2: MO TERMINAL NGAY chua dockerfile
<br /><br />  lenh dong goi => tao image:  docker build . -t [tem image] (vi du: docker build . -t img-html)
<br /><br /> B3: cho no chay de tao container: docker run -d -p 3030:80 --name [dat ten cho container] [image vua tao]. vi du: docker run -d -p 3030:80 --name cons-html img-html (port trong luoon luon 80 vi phai tuan thu nginx)
<br /><br /> ====> vao locahost:3030 la ra ket qua
<br /><br /><br />
<br /><br /><br /><br />-----------------------REACT---------
<br /><br /> ====> neu react thi:
<br /><br /> b1: chay: npm run build
<br /><br /> b2: dau file Dockerfile vao trong build va ghi hoan toan tuong tu
<br /><br /> b3: docker build ./build -t [tem image]
<br /><br /><br />
<br /><br /> TONG HOP CAC BUOC
<br /><br /> b1: npm run build
<br /><br /> b2: Dockerfile trong build
<br /><br /> b3: FROM nginx
<br /><br /> b4: WORKDIR /usr/share/nginx/html
<br /><br /> b5: COPY . .
<br /><br /> b6: cd build
<br /><br /> b7: docker build . -t img-youtube
<br /><br /> b8: docker run -d -p 3333:80 --name cons-youtube img-youtube
<br /><br />
<br /><br /><br />
<br /><br /><br /><br />-----------------------BACK END---------
<br /><br /><br />-------SEQUELIZE
<br /><br /> FROM node:16
<br /><br />WORKDIR usr/share/node37_BE
<br /><br />COPY package.json .
<br /><br />RUN npm i (RUN yarn install)
<br /><br />COPY . .
<br /><br /> CMD ["npm","start"]  (CMD ["yarn","start"])
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br />-------PRISMA
<br /><br /> FROM node:16
<br /><br />WORKDIR usr/share/node37_BE
<br /><br />COPY package.json .
<br /><br />RUN npm i (RUN yarn install)
<br /><br />COPY prisma ./prisma
<br /><br />RUN npx prisma generate
<br /><br />
<br /><br />
<br /><br />COPY . .
<br /><br /> CMD ["npm","start"]  (CMD ["yarn","start"])
<br /><br />
<br /><br /><br /> luu y can phai tao file .dockerignore => node_modules
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
**Luong di:** module > controller > service<br />

**module:** dung de ket noi controller va service
**controller:**  dinh nghia API khac voi Express(dinh ghia cac chuc nang, nghiep vu...) === **Router** cua express<br />
**service:**  dinh nghia cac chuc nang, nghiep vu...<br />

**Lệnh tạo module nhanh:**  nest g module [tên module] <br />
**Lệnh tạo controller nhanh:**  nest g controller [tên module] --no-spec <br />
**Lệnh tạo service nhanh:**  nest g service [tên module] <br />
<br />
<br />

=>>>>>>**Lệnh tạo nhanh ca 3 file:**  nest g resource [tên module] --no-spec <br />

 <br /> DTO(data transfer object): giup khia bao nhung cai type it hoac nhieu hon type ban dau
  <br /> DTO: giup khia bao nhung cai type it hoac nhieu hon type ban dau
  <br />  <br />  <br />  <br />  <br />

=>>>>>>**Su dung bien moi truong:**  npm i @nestjs/config <br />
<br /> them vao moudule thang cha lon nhat: app.module.ts ====>>> 
ConfigModule.forRoot({ <br />
      isGlobal: true, <br />
    }), <br />
 <br /> gan vao controller cua cai muon xai
  <br /> su dung: this.configService.get('ten bien')

<br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br />
**LAY DU LIEU TU DATABASE**<br />
<br /> su dung cac ORM: sequlize / prisma
<br />
<br />
**PRISMA:**<br />
<br /> npm i prisma @prisma/client
<br /> npx prisma init
<br /> vao .env su thong tin dnag nhap: chuoi ket noi (DATABASE_URL="mysql://root:1234@localhost:3306/youtube_app?schema=public") va file schema ("mysql")
<br /> npx prisma db pull
<br /> npx prisma generate

<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />



<br /><br />UPLOAD PHOTO
<br /><br /> npm i @types/multer
<br />
<br />
<br /><br /> tu controller cua thang nao can dung middleware thi: <br />
 up 1 tam :single<br />
@UseInterceptors(<br />
    FileInterceptor('avatar', {<br />
      storage: diskStorage({<br />
        destination: process.cwd() + '/public/img',<br />
        filename: (req, file, callback) =><br />
          callback(null, new Date().getTime() + '_' + file.originalname),<br />
      }),<br />
    }),<br />
  )<br />
  @Post('/upload')<br />
  uploadPhoto(@UploadedFile() file: Express.Multer.File) {<br />
    return this.userService.uploadPhoto(file);<br />
  }<br />
<br /><br />
<br /><br />
 up nhieu tam :multiple<br />
@UseInterceptors(<br />
    FilesInterceptor('avatar', 3 ,{<br /> 
      storage: diskStorage({<br />
        destination: process.cwd() + '/public/img',<br />
        filename: (req, file, callback) =><br />
          callback(null, new Date().getTime() + '_' + file.originalname),<br />
      }),<br />
    }),<br />
  )<br />
  @Post('/upload')<br />
  uploadPhoto(@UploadedFiles() file: Express.Multer.File[]) {<br />
    return this.userService.uploadPhoto(file);<br />
  }<br />
<br />{FilesInterceptor =>>> co "s"} va them tham so thu 2 la so tam hinh cho phep;@UploadedFiles() =>> co "s" va Express.Multer.File[] =>> co []<br /> 
<br /><br />


<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
**SWAGGER:**  <br />
<br /><br />  yarn add @nestjs/swagger swagger-ui-express HOAC  npm i @nestjs/swagger swagger-ui-express
<br /><br /> qua main.ts
<br /><br /> const config = new DocumentBuilder().setTitle('Node 37 - version 0.0.1').build();<br />
  const document = SwaggerModule.createDocument(app, config);<br />
  SwaggerModule.setup('/swagger', app, document);<br />
  <br />
 Gom nhom API lai thi vao controller cho no decorater <br />
@ApiTags('User')<br />
@Controller('user')<br />
<br />
<br />
<br />
<br />
**TOKEN BANG NESTJS:**  <br />
npm i @nestjs/config @nestjs/passport passport passport-local @nestjs/jwt passport-jwt @types/passport-jwt  <br />








<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />




<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
**Step 3: Push code into remote :**  <br />
  git add -A <br />
  git commit -m "content" <br />
  git push -u origin main (1st push - compare with when *remote haven't had the branch*  ) <br />
  git push (from 2nd push) <br />
<br />
<br />


**BRANCH** <br />
<br />
**LIST BRANCH:** git branch<br />
**LIST BRANCH FROM ROMOTE:** git branch -r<br />
**CREATE NEW BRANCH only:** git branch login <br />
**BEFORE SWITCHING ANOTHER BRANCH - WE SHOULD SYNC**: git fetch <br />
**SWITCH BRANCH only:** git checkout login <br />
**CREATE NEW BRANCH from current branch and SWITCH to the new branch:** git checkout -b login <br />
**DELETE BRANCH:** git branch -D login <br />

**MERGE LOGIN TO MAIN - update MAIN with the code of LOGIN**<br />
**Step 1: at LOGIN branch, we must commit:** git add -A && git commit -m ""<br />
**Step 2: switch to MAIN branch - the branch we need to have new code:** git checkout main<br />
**Step 3: at LOGIN branch, merge the code:** git merge login<br />
**Step 4: push into remote - MAIN branch** git add -A && git commit -m  && git push<br />


<br />
<br />
**CLONE** <br />
<br />
**Step 1: clone git from remote - crate "child folder" inside the folder at terminal:** git clone https://github.com/quangsiDev/demo_git -> repo is "child folder" so we must be cd into "child folder"<br />
**Step 1.1: clone git from remote - put "all file" inside the folder at terminal:** git clone https://github.com/quangsiDev/demo_git .<br />
**Step 2: create new branch and code in the new one :** git checkout -b new<br />
--> if whne we code in new and fail -> come to main -> clone code again -> careate new branch -> code in the new one again


<br />
<br />
**PULL** <br />
<br />
**Step 1: get latest code :** git pull<br />

<br />
<br />
**RESTORE THE OLD CODE** <br />
<br />
**undo the lastest code campare with the last commit :** git stash<br />
**undo the old code from old commit:** <br />
    **S1:find the id of the old version and Copy** git log <br/>
    **S2:get the old code** git checkout id<br/>
    now it will automatically create new history branch, so from here we can checkout to new branch and code or code in this branch, it depend

<br />
<br />
**NOTE** <br />
<br />
**REMOVE ORIGIN:** git remote remove origin<br />
**REVIEW COMMIT HISTORY:** git log<br />
**COMPARE CLONE & PULL** <br />
git clone<br />
Lệnh này sẽ sao chép toàn bộ dữ liệu và thiết lập trên remote repository, tức là
nó sẽ tự động tạo một local repository trên máy tính của bạn sau khi chạy lệnh.
Lệnh này *chỉ nên sử dụng khi bạn cần tạo mới một dự án Git* trên máy tính.<br />
• git pull<br />
Lệnh này sẽ chỉ *lấy những dữ liệu có sự thay đổi từ remote repository* đem về
cập nhật cho local repository<br />

**Git pull is rejected: ! [rejected]        main -> main (non-fast-forward)** <br />
-> using: git pull --rebase
<br/>
<br/>

<br/>

<br/>

<br/>

<br/>

-----------------------------------
<br/>
**CSS TEXT LIMITED LINE: 
 style={{
        overflow: "hidden",
        textOverflow: "ellipsis",
        display: "-webkit-box",
        lineClamp: 2,
        WebkitLineClamp: 2,
        WebkitBoxOrient: "vertical",
    }}
