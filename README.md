# 將Vue專案部署至Github Pages

1. 在gitHub上創建一個新的專案![](https://i.imgur.com/LhXpgpP.png)

![](https://i.imgur.com/wTc7PYf.png)

2. 在本地端create 一個vue專案 (與剛剛在gitHub上創建的同名)

4. 在本地專案資料夾根目錄新增一個 vue.config.js 
    ```
    // vue.config.js
    module.exports = {
    publicPath: process.env.NODE_ENV === "production" ? "/專案名稱/" : "/",
    };
    ```
    
5. 在根目錄新增 deploy.sh
    ###### 這是要部署在gitHub page上的部署腳本
    ###### 參考 vue cli 部署指南  [https://cli.vuejs.org/zh/guide/deployment.html#github-pages](https://)
    ```
    # 當發生錯誤時終止腳本運行
    set -e
    # 打包
    yarn build
    # 移動至到打包後的dist目錄 
    cd dist
    # 因為dist資料夾預設是被ignore的，因此在進入dist資料夾後初始化git
    git init 
    git add .
    git commit -m 'deploy'
    # 將dist資料夾中的內容推送至遠端的gh-pages分支中，並強制無條件將舊有的內容取代成目前的內容（指令 git push -f)
    git push -f https://github.com/rayyyyyyyyyyyyyyyyyyyy/專案名稱.git master:gh-pages
    cd -
    ```
 
5. 將本地端專案上傳gitHub
    ###### 參考 gitHub init
    ```
    git init
    git add .
    git commit -m "註解文字"
    git branch -M main or master
    git remote add origin https://github.com/Rayyyyyyyyyyyyyyyyyyyy/專案名稱.git
    git push -u origin main
    ```

6. 運行腳本 
    ```
    sh ./deploy.sh
    ```
    

