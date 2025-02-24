# melody-eats-backend
Design an application step by step

-  download Node.js 
    -  下載`.msi`檔案並執行 一直按next 記得選主動加入`Add to PATH` 就不用手動添加環境變數
    -  run `node -v`或者`npm -v`確認已安裝成功
    -  open powersheell 執行`npm install -g @nestjs/cli`
       - `npm` node package manager
       - `-g` global 代表該封包會安裝到到系統 而不是僅存在於專案內

-  genearate an application
    -`nest g application` 會問你這個專案要叫什麼 我取名為 melody-eats-backend

-  open this project in visual studio code
    -`cd melody-eats-backend`
    -`code .` (中間一定要空一格 常常忘 很白痴)
-  啟動server `npm start`
 
-  in visual studio code,open terminal and execuate `npm install` and waiting it
    -在執行 `npm install`時 可能會拋出error 這是因為PowerShell在預設情況下，會阻止未經授權的script執行，這樣才可以保護系統免於執行潛在的危險程式。
    -所以可以以選 以**系統管理員開啟powershell** 然後**設定允許未經認證之script執行** `Set-ExecutionPolicy Remotesigned-Scope CurrentUser`(Scope範圍) 
    -等到裝好後 執行`npm run start:dev`(在開發環境中啟動應用程式)

-  create a repository in github to record the new process (只專注於我們想要的開發的項目)
    -在terminal中輸入`git init` initialize
    -這時visual studio code會跳出warnings 提示目前repository有大量未提交的變更 這些變更通常來自於node.js內建的模組 `node_modules` 我們不需要commit它們到github上
     所以下載擴充軟體 `gitignore` 將這些模組加入gitignore 以避免git花不必要地時間去追蹤這些檔案
    -點左下角 `manage`->`Command Palettes`->`gitignore`->我們目前用什麼語言開發 就把該語言相關模組都加入gitignore中
    -此時refresh 會發現目前要被追蹤的file減少到可接受大小
  
  ![image](https://github.com/user-attachments/assets/ee645b52-9d7f-4a8e-b6f5-e4b0401d7ef6)
- 修改原本預設的 `ReadMe.md` 這個文件 然後commit到github上 `git add .`->`git commit`
    - 將本地 Git倉庫連接到GitHub上創建的遠端倉庫。how to do? first, copy在GitHub上創建的倉庫URL（如 https://github.com/ladyotter-inwater(github用戶名)/melody-eats-bacxkend(倉庫名).git）輸入`git remote add origin `
    - 此時`origin`就會指向遠端的倉庫(即成功連接上github) 此時 就可以將文件`push`上去
    - 使用 `git remote remove origin` 來移除遠端倉庫 `origin`
    - 使用 `git remote -v` 再次確認 `origin` 是否已經移除 刪除成功就會空 不顯示任何東西
-`push` code to the github
    -連接到remote repository時 會顯示**要授權** 此時可以設定SSH(這樣就不用每次都要輸入PAT)
      1. 生成SSH private key `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
        `-t rsa` 表示使用RSA演算法生成密鑰
        `-b 4096` 指定密鑰長度為4096位
        `-C "your_email@example.com"` 為密鑰添加註解 通常是標記綁定github的那個email
      2. 設定private key儲存的route 因為預設是在C:\Users\黃馨... 但因為路徑中有中文 所以等夏會報錯 故要自訂儲存路徑 我是存在 `C:/Users/melody/.ssh` 下 `.ssh`這個資料夾要自己創建
      3. 查看public key ->這是要add到github的 輸入`cat C:/Users/melody/.ssh/id_rsa.pub`時 terminal就會顯示public key的內容 它會以`ssh-rsa`開頭 copy & paste to this place
      4. `settings`->`SSH and GPG keys`->`new SSH key`
      5. 測試SSH連線有沒有成功 `ssh -T git@github.com` 如果設置完成 會顯示Hi <your-username>! You've successfully authenticated, but GitHub does not provide shell access.
      6. 變更github repository的URL `git remote set-url origin git@github.com:ladyotter-inwater/melody-eats-backend.git`
      7. and it's ok you can push your project onto github
      8. `git push -u origin master` 預設是main 但我都放在master
-  API reference ApolloServer
    - 網址 : https://www.apollographql.com/docs/apollo-server/api/apollo-server
    - `option`有兩個參數是一定要設定 `typedefs` & `resolvers`
-  跳出Error `GraphQLError: Query root type must be provided.`
     ![image](https://github.com/user-attachments/assets/a47b07f0-2d3a-4b25-a4a9-cdb46a109179) [image](https://github.com/user-attachments/assets/78266ca7-0365-41a3-94a5-5fb438694c30)
    -how to fix it?
-  各種修bug
    - 換行符號設定 : 在Window下開發是CRLF 在Linux則是LF
    - Eslite是用來檢查程式語法的tool Prettier則是自動整理程式碼的tool
    - 使用快捷鍵格式化format程式碼 `ctrl+alt+f`

