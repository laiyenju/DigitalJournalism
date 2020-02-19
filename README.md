# 數位新聞起步手冊 Road To Digital Journalism

因為參考的 NPR 使用 Mac，而我自己也使用 Mac，所以下列內容就以 Mac 的設定為主，等待有緣分的 Windows 使用者添加囉。


## 如何使用此手冊?

- 「起步」手冊，是希望能協助大家用安全、快速、方便的方式，快速建立好適合打造數位新聞內容/產品的電腦。
- 因此這裡的文件會依照安裝步驟，手把手帶著大家一步一步安裝。
- 由於不想在剛起步的階段，就讓大家承受資訊過載之苦（同時我也正在學習中，也不一定能將原理都說明清楚），所以只會簡單說明每個步驟的原因。若想要知道各個工具或安裝套件的詳細用途，請查看此文件的 [Wiki](https://github.com/laiyenju/DigitalJournalism/wiki)，我會盡可能地描述清楚。

---

此文件是以[美國公共廣播電台 NPR](https://www.npr.org/) 的新聞開發環境[所寫的內容](http://blog.apps.npr.org/2013/06/06/how-to-setup-a-developers-environment.html)為主，但原本 NPR 釋出的文件版本較舊，所以是依據原文件的架構，再去找補充資料，親自測驗後才更新的內容。

需要注意的是，[NPR 團隊](https://github.com/nprapps)用 Python 開發應用程式、架設網站，依照此文件設定的開發環境等同於 Python 的開發環境。

---

### 安裝步驟
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

### 01 安裝 command line 工具

在 Terminal 輸入 `xcode-select --install` 後按下 Enter 鍵，（需要等較久時間）就能完成安裝。

若上述指令碼無法成功安裝（看到 Terminal 出現錯誤訊息，請到 [Apple 開發者網站](http://developer.apple.com/downloads/index.action)下載 Xcode 最新版本）

**注意：絕對不要從 App Store 下載 Xcode**

### 02 安裝 Homebrew

Homebrew 是專門管理安裝套件的軟體，讓人能有效率地安裝開發用套件。

首先，開啟 Terminal（終端機），並依序輸入以下指令

1.  `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  
     輸入後，按下 Enter 鍵，（需要等待一小段時間）就能安裝 Homebrew

2. 檢查 Homebrew 是否有安裝成功

    在 Terminal 輸入 `brew doctor` 後，按下 Enter 鍵。
    
    若顯示 `Your system is ready to brew.` 表示安裝成功。

3. 若不幸出現警告訊息（通常會長這樣 `Warning:....`）表示有東西要更新或額外設定，這時請耐心讀系統提供的訊息，依照指示完成任務。
    
    > 補充：在 Terminal 內輸入`brew update` 就能更新 Homebrew。

### 03 安裝 Python3 (以及虛擬環境 virtualenv)

Mac 以內建 Python 2.7，但 Python 已宣佈日後不再支援 2.7 版本，所以建議都升級到 Python 3.x。

所以這裡會使用 Homebrew 安裝 Python3（也就是 Python 3.x 版本），以及搭配 Python 配置開發環境會用到的 virtualenv。

1. 在 Terminal 內輸入 `brew install python3`，按下 Enter 鍵，安裝 Python3
2. 在 Terminal 內輸入 `pip3 install virtualenv`，按下 Enter 鍵，安裝虛擬環境 virtualenv

> 補充：virtualenv的使用方式，可以參考我之前記下的[虛擬環境操作手冊](https://clockwork.substack.com/p/51e)

### 04 安裝 Node.js

這裡會帶大家用 nvm 管理 Node.js，因為 Node.js 的版本管理問題常讓人傷腦筋，因此以 nvm 方便安裝與刪除各種版本的 Node.js。

1. 在 Terminal 中輸入 `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash`
  
    按下 Enter 鍵後，就能安裝 nvm

2. 在 Terminal 中輸入 `nvm install node`

    按下 Enter 鍵，就能以 nvm 去安裝 Node.js（安裝 Node.js 同時也會自動安裝 npm）    

3. 關閉 Terminal 再重新開啟，輸入 `nvm use node`

4. 再輸入以下指令，確認都出現版本號，代表安裝成功

    - `node -v` 會顯示安裝的 Node.js 的版本號（會出現 v13.9.x）
    - `npm -v` 會顯示安裝的 npm 的版本號（會出現 6.13.x）

> 補充：日後若要更新 Node.js，輸入 `nvm install node --reinstall-packages-from=node` 即可。

### 05 設定 git 與 GitHub

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

### 06 安裝 Postgres 與 PostGIS

這兩者在做數據新聞時（地圖、視覺化等）就會用到，到 [Postgres.app 網站](https://postgresapp.com/) 下載即可。

### 07 開發環境的其他設定

### 08 安裝 iTerm2 取代內建的 Terminal

這不是必要步驟，若仍想使用 Terminal，就可以跳過。

1. 到[此頁面](https://www.iterm2.com/#/section/home)下載 iTerm2

2. 改用 zsh 讓頁面更易讀

    `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

### 09 安裝程式碼編輯器

推薦免費、使用社群活躍，且很多人都在使用的兩種程式碼編輯器給大家參考，

- [Atom](https://atom.io/) 由 GitHub 開發的。
- [Sublime Text](https://www.sublimetext.com/)，我自己也在用。


## 開源新聞工具
- [NPR Tools](http://blog.apps.npr.org/tools/)


## 參考文件
>
> - [How to Setup Your Mac to Develop News Applications Like We Do](http://blog.apps.npr.org/2013/06/06/how-to-setup-a-developers-environment.html) by NPR Visual Team 
> - [macOS Catalina 10.15: Setting up a Brand New Mac for Development](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/?ref=vincentapp.io)
> - [Connecting to GitHub with SSH](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)


###### tags: `tutorials` `journalism`
