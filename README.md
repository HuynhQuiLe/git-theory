# git-theory
**NestJS** <br />
<br />
**Luong di:** module > controller > service<br />

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










**controller:**  dinh nghia API khac voi Express(dinh ghia cac chuc nang, nghiep vu...) === **Router** cua express<br />
**service:**  dinh nghia cac chuc nang, nghiep vu...<br />

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
