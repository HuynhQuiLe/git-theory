# git-theory
**USUALLY USE** <br />
<br />
**Step 1: create repo local:** git innit<br />

**Step 2: link repo-local with repo-remote:**  git remote add origin https://github.com/HuynhQuiLe/samar.git

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
**CREATE NEW BRANCH only:** git branch login <br />
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
**NOTE** <br />
<br />
**REMOVE ORIGIN:** git remove origin<br />
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
