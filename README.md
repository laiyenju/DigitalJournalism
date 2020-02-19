# 數位新聞工具手冊
**Road To Digital Journalism**
以下安裝設定以 Mac 電腦為主。

## 開始之前，先設定電腦

此篇是以 NPR 的新聞開發環境[所寫的內容](http://blog.apps.npr.org/2013/06/06/how-to-setup-a-developers-environment.html)為主，但原本 NPR 釋出的文件版本較舊，所以本文是依據原文件的架構，再去找補充資料，親自測驗後才更新的內容。
需要注意的是，[NPR 團隊](https://github.com/nprapps)用 Python 開發應用程式、架設網站，依照此文件設定的開發環境等同於 Python 的開發環境。


**步驟**
- 安裝 command line 工具
- 安裝 Homebrew
- 安裝 Python 3 (以及虛擬環境 virtualenv)
- 安裝 Node.js
- 設定 git 與 GitHub
- 安裝 Postgres 與 PostGIS
- 開發環境的其他設定
  - 以 iTerm2 取代內建的 Terminal
  - 安裝程式碼編輯器（Atom 或 SublimeText）
  
---

### 安裝 command line 工具

### 安裝 Homebrew
Homebrew 是專門管理安裝套件的軟體，能省下解決不同版本衝突的時間。

1. 安裝 Homebrew 管理套件

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

2. 檢查是否安裝成功

`brew doctor`

3. 若有警告訊息表示 Homebrew 版本過舊，輸入以下命令更新

`brew update`

### 安裝 Python 3 (以及虛擬環境 virtualenv)
1. 

### 安裝 Node.js

此部分是以 nvm 管理 Node.js，因為 Node.js 的版本管理問題常讓人傷腦筋，因此以 nvm 方便安裝與刪除各種版本的 Node.js。

1. 以命令列安裝 nvm

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash`

2. 以安裝好的 nvm 去安裝 Node.js（安裝 Node.js 同時也會自動安裝 npm）

`nvm install node`

3. 關閉 Terminal 再重新開啟，輸入 `nvm use node`

4. 再輸入以下指令，確認都出現版本號，代表安裝成功

- `node -v` 會顯示安裝的 Node.js 的版本號
- `npm -v` 會顯示安裝的 npm 的版本號

日後若要更新 Node.js，輸入 `nvm install node --reinstall-packages-from=node` 即可。

### 設定 git 與 GitHub

1. 建立一個名為 .gitconfig 檔案

`touch ~/.gitconfig`

2. 設定自己的名稱與信箱

- `git config --global user.name "YOUR NAME"` **YOUR NAME** 要改成自己的英文名字
- `git config --global user.email "xxx@mail.tw"`  **xxx@mail.tw** 要改成自己的信箱

3. 確認是否設定成功

輸入 `git config --list`，若顯示列表跟設定的相同（如下），表示成功

```
user.name=YOUR NAME
user.email=xxx@mail.tw
```

### 安裝 Postgres 與 PostGIS

### 開發環境的其他設定

### 安裝 iTerm2

1. 到[此頁面](https://www.iterm2.com/#/section/home)下載 iTerm2

2. 改用 zsh 讓頁面更易讀

`sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`


## 開源新聞工具
- [NPR Tools](http://blog.apps.npr.org/tools/)


## 參考文件
>
> - [How to Setup Your Mac to Develop News Applications Like We Do](http://blog.apps.npr.org/2013/06/06/how-to-setup-a-developers-environment.html) by NPR Visual Team 
> - [macOS Catalina 10.15: Setting up a Brand New Mac for Development](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/?ref=vincentapp.io)
> - [Connecting to GitHub with SSH](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
