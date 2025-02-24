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
- in visual studio code,open terminal and execuate `npm install` and waiting it
    -在執行 `npm install`時 可能會拋出error 這是因為PowerShell在預設情況下，會阻止未經授權的script執行，這樣才可以保護系統免於執行潛在的危險程式。
    -所以可以以選 以**系統管理員開啟powershell** 然後**設定允許未經認證之script執行** `Set-ExecutionPolicy Remotesigned-Scope CurrentUser`(Scope範圍) 
    -等到裝好後 執行`npm run start:dev`(在開發環境中啟動應用程式)
