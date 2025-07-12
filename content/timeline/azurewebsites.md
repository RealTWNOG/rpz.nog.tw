---
author:
  name: "tdc"
date: 2025-07-12T13:00:35+08:00
linktitle: "Azurewebsites"
type:
- post
- posts
title: "Azurewebsites RPZ"
eventname: Azurewebsites 被刑事局回報涉毒網站遭到 DNS 汚染
eventlocation: 📍 刑事局
weight: 20
---

## 經過

微軟雲端服務底下的 Azurewebsites.net 根網域，在 7 月 10 日下午突然遭到刑事局以涉毒為由，由 TWNIC 台網中心以 DNS RPZ（Response Policy Zone）封鎖將近 2 個小時，導致根網域下的 Azure Web App 等服務受到影響。

事後刑事局調查原因，坦承為其內部文書轉檔疏失，將要封鎖的涉毒網站網址名稱的子網域誤刪，留下 Azurewebsites.net 根網域，導致 TWNIC 封鎖整個根網域。

新聞來源：[刑事局封鎖涉毒網址轉檔作業出包，Azurewebsites.net根網域遭封鎖近2小時，連TWNIC公文系統都被封](https://www.ithome.com.tw/news/170025)

而後續刑事局承認內部出錯，於 7 月 10 日下午 5 點 22 分接獲 TWNIC 台網中心通知後，請求 TWNIC 解除封鎖，在下午 6 點 11 分左右恢復正常服務。

這邊整理一下，大意上是指：  
1️⃣ 刑事局內部文書作業轉檔過程中誤刪子網域  
2️⃣ 只留下 Azurewebsites.net 根網域送交 RPZ 清單  
3️⃣ TWNIC 依公文執行封鎖整個根網域  
4️⃣ TWNIC 自家的公文系統也架在 azurewebsites.net 網域底下，發現後主動通知刑事局

## 事件

刑事局在執行涉毒網站封鎖作業時，在 2025 年 7 月 10 日下午 4 點 44 分，發文通報 TWNIC 進行 DNS RPZ 封鎖。下午 4 點多，Azurewebsites.net 根網域遭到封鎖，導致該根網域底下所有服務都無法正常使用，連接根網域畫面即顯示因違反毒品危害防治條例而遭到封鎖。

在封鎖期間，不少用戶發現在根域名底下的服務無法正常連上，包括 7-ELEVEN 的數位禮券，也有企業發現 Azure Web App 的測試機、架在上面的 UAT 網站連不上。

正常來說 azurewebsites 是沒有 A 紀錄的
![](/images/azurewebsites/photo_2025-07-10_17-28-46.jpg)

## 分析

刑事局毒品查緝中心坦言，這次事件發生的原因，為其內部文書作業轉檔過程中出錯。有網友分析，這次事件凸顯了幾個問題：

問題發生在刑事局到 TWNIC 的部分
當作業人員原本是要刪除 https://
卻不小心將前面的子網域也一併刪除
只剩下 Azurewebsites.net 根網域
導致 TWNIC 封鎖整個根網域
這次事件還有個小插曲
TWNIC 自家的公文系統也架在被封鎖的根網域底下
因此在執行封鎖後自己的公文系統也無法使用
必須透過電子郵件接收解除封鎖的公文

## 結論

這次事件很明顯的有幾個問題。

* **作業流程問題**：刑事局內部文書轉檔作業缺乏查核機制，導致誤刪子網域的錯誤未被及時發現，同時 TWNIC 應該新增一個自動檢查機制，若該網域在全球使用廣泛，則應該在經過一次人工檢查後再進行封鎖。
* **影響評估不足**：封鎖根網域的影響範圍過大，連 TWNIC 自己的系統都受到影響。
* **除錯機制缺乏**：缺少白名單機制來預防重要根網域被誤封，同時也沒有 RPZ 的申訴管道。

