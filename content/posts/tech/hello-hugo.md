---
title: "Hello Hugo"
date: 2024-04-07T22:19:07+08:00
draft: false # Set 'false' to publish
tableOfContents: false # Enable/disable Table of Contents
description: ''
categories:
  - tech
tags:
  - hugo
---

## 楔子

日子渾渾噩噩，回想不起兩個月前在做啥， medium 一看上一篇文章還停在 2019 年，心理發慌

## 前言

換到新 BU 之後事情多且雜，很難確切記得忙過哪些事情。

2023 年開始在 notion 內留下 blog 文章，但遲遲找不到 ok 的平台搬家

這次的搬家的主要目標是要貫徹研究所時期堅持的原則：文章用 .md + git 存，方便轉換平台。

次要目標是希望盡量降低寫作成本，避免一想到更新 blog 有多麻煩就開始犯懶

## 實驗過程

### Hexo

本來的首選是 hexo，畢竟靠 JavaScript 吃了快十年的飯，用 Hexo 應該最有回家的感覺

在 Hexo 上 survey 了五六種 theme，並實際裝來跑看看

可惜實際一測發現 hexo 的開發有點鬆散，很容易遇到前後不相容的問題

找不到一個夠強的大腿抱，只能忍痛放棄。

### Hugo

令人殘念的是 Hugo 也沒好到哪邊去，但稍微測過幾個 theme 之後，相容度比 Hexo 稍好。

自己動手修改 template 的難度貌似比 hexo 低一點

就先把 blog 丟在這。

### Vitepress

<https://vitepress.dev/>

還很新

Vitepress 前陣子剛結束為時一兩年(?) 的 beta，推出 1.0 穩定版

目前還沒有適合 Blog 的 theme

但只要有合適的 theme，功能不要差太多

**Vitepress 會是我往後搬家的首選**

### Notion

Notion 匯出筆記的功能很猛，如果有某個資料夾筆記直接跟 git 連動的功能的話，Notion 應該會是我的首選

可惜暫時還沒找到堪用的解決方案

### medium

上一個 blog 的內容放在 medium，如果能跟 git 連動的話會是僅次於 Notion 的首選

可惜目前別說 git 了，連搬家的功能都還不太行

再加上付費牆越來越誇張，我遲早會把所有的 blog 撤離 medium 這個不尊重閱讀體驗的平台。

### logdown

上上一個 blog 的內容放在 logdown

當初就覺得 logdown 韭菜味很濃，在上面更新了兩三篇文就果斷停更。

事實證明我的直覺是對的，網站兩三年後直接停更 （域名到還是活著）

可惜了一個好網站

時至 2024 今日，似乎還是沒有足以統治市場的 blog 平台

如果換個組織經營並加上夠好的搬家功能的話，也許我就不用 survey 其他平台摟。

## 筆記

### theme

挑了一個相對順眼的 theme [Lowkey](https://themes.gohugo.io/themes/lowkey-hugo-theme/)

clone 下來裝之後馬上撞到了 bug，2024/03 的時候發了 PR 給作者，目前 (2024/04) 暫時沒被合併

### 改 code

截至目前為止 (2024/04/07)，官網上的 Lowkey 是有 bug 的

必須自行 patch 掉

（其實也就是某個變數名稱 rename 後忘記改，[可以參考此 PR](https://github.com/nixentric/Lowkey-Hugo-Theme/pull/30)）

再來想要改大頭像或是微調 theme 的話，都必須對 git submodules 下手才行

建議 fork 一份 Lowkey 到自己的 namespace 下再做後續修改

另外 fork 後，記得修改 `.gitmodules` 的設定，把 git repo 指向自己的 namespace

### deploy

deploy 到 github pages 的部分十年前就測過了，還不錯，可惜 github 近年來速度有越來越慢的趨勢...

一開始是打算 deploy 到自己的 VPS 上

但轉念一想，應該來試試看 [cloudflare 的 pages 服務](https://pages.cloudflare.com/)

做 CDN 起家的公司提供的 hosting 服務聽起來就很猛

實際上**整個開發體驗遠比想像中的還要棒**

config 填一填連 yaml 都不用準備就幫你 deploy 好了，還自動串接 github webhook

唯一有點疑慮的地方是，文件上有寫說 free account 每個月只有 500 次的 build

(由於有串接 githob webhook，等於 git 只能改 500 次，第 501 次開始就不會動摟)

但我在 dashboard 上並沒有看到相關的使用次數統計

也許 cloudflares 也發現 500/month 掐的有點緊，正在調整中吧 ...

### cheatsheet

- 啟動 dev server: `hugo server`
- 啟動 dev server, 包含草稿: `hugo server -D`
- 建立新文章: `hugo new content posts/tech/hello-hugo.md`
- 建置: `hugo`
- cloudflare 建置指令: `npm install; hugo`

## 時間花費

這次 blog 建置過程，經過約三個週末（週末固定禮拜天研究，每個禮拜約花五小時）

其中兩個週末在評估 hexo / hugo / notion 等平台

最後一個週末在實際建置＋更新內容＋發佈到 cloudflare 上

## Hugo / theme Lowkey 已知問題

- Lowkey 的時間格式是 dd/mm/yyyy
  - 可以靠改 code 解決
- Lowkey 預設的 avatar 是 80x80，超糊
  - 可以靠改 code 解決
- Lowkey 不支援 archives 頁面
- Lowkey 不遵守 hugo.toml 內的設定值，且安裝步驟會要求你用它提供的範例檔覆蓋掉自己的網站，這 code 用起來心理不太踏實，可能要有隨時下去修改的覺悟
- 幫 Lowkey 修的簡單 bug，過了兩個禮拜作者還沒 merge，也沒有任何回應
- Lowkey 的 disqus 功能可能被作者改壞了，或根本沒有實作此功能
  - 我的網站出不來，還在研究中
- Hugo 不支援 vuepress / hackmd 的 markdown plugin，目前最痛的是不能用 info / warning block 的語法
- Hugo/Hexo 都有的問題： 每個 theme 實作的功能不一樣，使用 theme 前需謹慎評估該 theme 有沒有實作你需要的功能

列一列之後發現問題好像比我想像的還多，十分勸退 QQ

如果對樣式沒有特別的要求的話，建議還是優先使用 github 上 star 多的 hugo theme

我正好是 Lowkey 這個 project 的第 100 個讚

也就是我 survey theme 的當下，他只有十位數的讚

## 寫在最後

{{< alert info "心得" >}}
為什麼想找一個可以貼貼廢文的平台能夠這麼難...
{{< /alert >}}