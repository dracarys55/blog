---
title: 當你有一天受夠了 Egret wing。
description: 那就奔向 vs code + google chrome 的懷抱吧
date: '2024/03/07'
categories: []
keywords: []
slug: ''
---

**_那就奔向 vs code + google chrome 的懷抱吧_**

  

let vsc = vs code;

let wing = egret wing;

### 前言 :

**基於白鷺官方自己所言，整個 wing 的架構其實都是基於 vsc 為基礎的(就是山寨**

**而因為vsc 迭代太快，導致白鷺團隊開發速度跟不上 vsc 的腳步，索性直接放棄 wing ….**

**那我們也只好聽官方的話，乖乖使用 vsc 進行開發吧。**

### 工具棧 :

vsc + egret EUI editor + egret inspector

### 獲得的新能力 :

[1.](http://1.hot)即時 hot reload 功能 (即修改過TS 不用再重新編譯)。

2.因為使用 chrome 而非 wing 裡面類似閹割過的chrome的預設瀏覽器 ，所以可以得到一切 chrome 最新最強的功能。

3.因為使用原生 vsc ，他們各種強大的掛件就不需要多說了，一切都是你的XD 。

4.egret inspector 可以給予在移動端觀看exml布局的功能。

5.egret EUI editor 提供更強大的exml 編輯能力。

### vsc 推薦下載掛件 :

與白鷺相關 -

<aside> 💡 名稱: Egret Coder 識別碼: egretengine.coder 描述: Egret support for Visual Studio Code 版本: 0.1.233 發行者: 白鹭 VS Marketplace 連結: [https://marketplace.visualstudio.com/items?itemName=egretengine.coder](https://marketplace.visualstudio.com/items?itemName=egretengine.coder)

</aside>

非白鷺相關 -

[Vscode 熱門套件](https://www.casper.tw/development/2020/12/13/vscode-extension/)

### 前置作業:

*   確認已有 Egret Coder extension 並全域啟用
*   確認 launch.json 包含以下配置
*   已按照以下網址的 — 直接使用部分在 google extension 安裝 EgretInspector

  

*   [https://github.com/jsl6/egret-inspector-install#直接使用](https://github.com/jsl6/egret-inspector-install#%E7%9B%B4%E6%8E%A5%E4%BD%BF%E7%94%A8)
*     
    
*   確認 launch.json 包含以下配置 (點右方標籤可以 toggle
*     
    

  

*   `{ "type": "chrome", "request": "launch", "name": "Launch Chrome against localhost", "url": "<http://192.168.0.122:3000/index.html>", "webRoot": "${workspaceFolder}", }, { "type": "Egret", "request": "launch", "name": "Egret Debugger", "url": "<http://localhost>:${command:WebsitePort}", "webRoot": "${workspaceFolder}", "sourceMaps": true, "userDataDir": "${tmpdir}" }, { "type": "Egret", "request": "launch", "name": "Egret WebpackDevServer Debugger", "url": "<http://localhost:3000>", "webRoot": "${workspaceFolder}", "preLaunchTask": "egret: build" }`

  

  

*     
    
*     
    
*   已按照以下網址的 — 直接使用部分在 google extension 安裝 EgretInspector
*     
    
*   [https://github.com/jsl6/egret-inspector-install#直接使用](https://github.com/jsl6/egret-inspector-install#%E7%9B%B4%E6%8E%A5%E4%BD%BF%E7%94%A8)
*     
    
*     
    
*   已安裝個別的 EgretInspector 與 eui-editor 的
*     
    
*   那個..官網就有了，去找一下吧。
*     
    

### 開始運行:

在開啟專案資料夾之後，按下F5 就會看到以下畫面

請注意左下角有個 egret debugger 的部分，那是選擇如何運行你的白鷺，

如選擇 egret debugger 那就是一般的運行(不包含hot reload功能

如選擇 Launch Chrome against [localhost](http://localhost) 那之後加入

egret run -a 就會有 hot reload 功能了

我們先按下 ctrl + \` 開始終端機 輸入: egret run -a

等看到以下字樣時

即可以按下 F5 並且選擇 Launch Chrome against [localhost](http://localhost) 後

就可以得到一個有 hot reload 功能的白鷺遊戲了。

PS : 如要查看 EXML 可按下 F12 最後一個即是 egret 按下去就可以

看到熟悉的exml檢視器了，阿如果沒看到，請再三確認你有安裝好 google \\

chrome extension了，在前置作業部分第三點。