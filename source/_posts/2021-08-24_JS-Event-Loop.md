---
title: 前端 JS 熱門面試考題解析（一） — Event Loop 是什麼？
description: 如何 Javascript 是一個人，那應該會是個單純的男孩子。
date: '2021-08-24T12:11:14.736Z'
categories: []
thumbnail: ./../images/1____IgEi8FRlR9scHfR5O__1ZA.png
keywords: []
slug: >-
  /@jackliu-61470/%E5%89%8D%E7%AB%AF-js-%E7%86%B1%E9%96%80%E9%9D%A2%E8%A9%A6%E8%80%83%E9%A1%8C%E8%A7%A3%E6%9E%90-%E4%B8%80-event-loop-%E6%98%AF%E4%BB%80%E9%BA%BC-be367e7fa7be
---

前端 JS 熱門面試考題解析（一） — Event Loop 是什麼？

> ### **如果 Javascript 是一個人，那應該會是個可愛單純的男孩子。**

<!-- ![](C:\Users\s6263\OneDrive\桌面\medium\posts\md_1709892859090\img\1____IgEi8FRlR9scHfR5O__1ZA.png) -->

為什麼這麼說呢？

我們都知道 Javascript 是單執行緒語言，目的是避免 [ConcurrencyIssue](https://stackoverflow.com/questions/461896/what-is-the-most-frequent-concurrency-issue-youve-encountered-in-java)

所帶來的混淆性與不確定性，而單執行緒是什麼意思呢？

就是一次只能做一件事，那問題來了，如果大家日常聽到這個人，一次只能做一件事，不能分心，第一反應是如何呢？
<br/>

**恩…他是不是有點笨？**

<br/>
沒錯當我一開始聽到也是這樣想的，cpu都越多越好了，還有人在單核戰到底的喔，有點特別，不過，單執行緒還是有其優勢的，第一是確定性，你通常都可以確定程式會如何跑，流程是如何，第二是速度快，畢竟一次只需要做一件事嘛。

好的說完背景人設

以下我們開始看圖說故事，來暸解一下 這個單純的男孩子是怎麼度過他的一天的 XD
<br/>

> ### Event Loop 解說

![](./../images/call_heap.gif)
<br/>

**Call Stack & Heap :** 也就是核心的 JS 任務列，所有程式碼依序執行，都會依序進入 Call Stack 一一執行，除了非同步請求。

**Web APIs：**瀏覽器給你的一群 API 大哥們，有各式各樣的功能，（當你解決不了就叫大哥們）其中一項就是幫你處理非同步請求，那些需要時間，沒辦法馬上解決的問題。

**Callback Queue：** 最簡單的理解就是 Web APIs 幫你處理完的結果就會放在這，結果可能包含成功或失敗，那何時會顯示結果出來呢？ 這就要呼叫我們的 Event Loop 了。

**Event Loop：**可以把它想成一個管家，幫你管理 Callback Queue的任務何時可以出來。

總不可能，程式跑到一半，欸剛剛結果來囉，然後就幫你隨便放在程式碼某個片段裡面吧，那下次回傳所需的時間秒數不同，結果又出現在不同的地方？？

所以 Event Loop 會幫你查看 Call Stack ，確定程式都跑完了 ，他就會依序幫你把 Callback Queue 裡面的任務推上去。

<br/>

以上，是最簡單最淺顯易懂的解釋了，希望可以達到老嫗能解的程度～

其他更多範例或更多的教學可以參考網路其他文章。
<br/>

這邊我想提到一個大家可能比較常忽略的地方，但是剛好在面試有被問到，做了研究之後覺得挺有趣的跟大家分享。

假如有兩個非同步請求，例如兩個 setTimeout 好了，各需要執行五秒的時間，請問跑完整段程式碼是五秒嗎，還是兩個的總和，十秒呢？

這問題牽扯到 setTimeout 是同時執行還是一行一行執行，問得更深一點就是 setTimeout 在 Web APIs 裏面執行，是在瀏覽器引擎執行的，那核心問題來了

> ### **_瀏覽器引擎是多執行緒還是單執行緒？_**

到這裡，答案可能並非剛入行的我能想到的，畢竟你我都只是剛碰 js 這門程式語言的小白而已，瀏覽器引擎呢，絕大多數都是多執行緒，也就意味著，兩個 setTimeout 也只會**執行五秒**而已，大家可以在 [codepen](https://codepen.io/ebemdmwf-the-scripter/pen/YzQKLPX) 上玩玩，理解一下 js 引擎與瀏覽器引擎之間的差異 。

祝福各位面試時遇到這題時，可以完整回答出來，對你有幫助的話可以讓我知道

畢竟發現自己的學習筆記也可以幫助到他人，其實是很快樂的 ～