---
title: "在 macOS Sonoma 上停用 caps indicator (大寫 標誌/提示)"
date: 2024-12-03T22:19:43+08:00
draft: false # Set 'false' to publish
tableOfContents: false # Enable/disable Table of Contents
description: ''
categories:
  - tech
tags:
  - mac
---

升級到 macOS 14 後，打字框多出了一個完全沒用的大寫藍色游標

找了一下發現 apple 官方論壇有人討論同一件事：

ref. https://discussions.apple.com/thread/255159504

參考下述解法可解決問題：


Found a solution. In Terminal:


```bash
sudo mkdir -p /Library/Preferences/FeatureFlags/Domain
sudo /usr/libexec/PlistBuddy -c "Add 'redesigned_text_cursor:Enabled' bool false" /Library/Preferences/FeatureFlags/Domain/UIKit.plist
```

Then reboot. After reboot - problem solved.