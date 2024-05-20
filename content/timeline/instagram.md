---
author:
  name: "tdc"
date: 2024-03-22
linktitle: "Instagram "
type:
- post
- posts
title: "Instagram RPZ"
eventname: Instagram 被回報為賭博詐騙網站遭到 DNS 汙染
eventlocation: 📍 不明
weight: 20
image: https://i.sudo.host/i/RJXnanQV.webp
---

## 經過

有網友在 ptt 上[發文](https://www.ptt.cc/bbs/Gossiping/M.1711087306.A.8C9.html)表示，使用中華電信的 DNS 伺服器，發現 Instagram 被回報為賭博詐騙網站，並且被 DNS 汙染，用電腦打開 Instagram 會跳出警告視窗，網頁會轉跳到刑事警察局警告頁面。

![https://i.sudo.host/i/bmRACXRP.webp](https://i.sudo.host/i/bmRACXRP.webp)
(圖源：ptt)

![https://i.sudo.host/i/RJXnanQV.webp](https://i.sudo.host/i/RJXnanQV.webp)
  
(圖源：ptt)


## 事件

此次影響範圍不明，但根據網友發文時間推斷 `2024 年 03 月 22 日 14:01:44` 發生異常直到 `2024 年 03 月 22 日 14:37` 恢復，期間為期大約 40 分鐘，並且有網友在留言中表示，使用中華電信的 DNS 伺服器，Instagram 仍然被回報為賭博詐騙網站。

![https://i.sudo.host/i/JdctL7XL.webp](https://i.sudo.host/i/JdctL7XL.webp)


## 分析

此次意外封鎖完全沒有相關單位發出聲明，也沒有相關新聞報導，且 TWNIC 上的 RPZ 紀錄也沒有相關資訊，僅能推斷人為操作不當，意外將正常網頁加入 RPZ 清單。


可能原因：
- 人為錯誤：操作人員可能誤將 Instagram 網址或相關 IP 加入 RPZ 清單。
- 其他原因：可能存在其他未知的技術或人為因素。

影響範圍：
- 根據目前所擁有的資訊，主要影響使用中華電信 DNS 伺服器的用戶。
- 其他 DNS 伺服器「可能」不受影響。
- 影響時間約 40 分鐘。


## 結論

盼望相關單位應調查事件原因，並公開說明，避免出現類似事件再次發生，甚至能擁有一個完全公開透明的報告。