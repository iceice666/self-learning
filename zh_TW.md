
# ResourcePack Server

> 在線版本在這裡！https://github.com/iceice666/self-learning/blob/resourcepack-server/zh_TW.md  
> 你也可以掃描這個QR碼  
> ![](qrcode_zh.png)

一個允許你在自己的伺服器上托管資源包的模組。  
（截至 2024/02/16，此模組已被下載了 355 次。）  

## 動機

在遊戲《Minecraft》中，資源包可以用來修改遊戲的紋理、聲音、音樂、語言文件、結尾字幕、螢幕效果和字體。  
它提供了一種簡單的方式來自定義遊戲的外觀並引入新功能。  
許多伺服器利用資源包來提升玩家的遊戲體驗。  
然而，原版《Minecraft》伺服器不支持原生地托管資源包。  
相反，通常你必須將資源包托管在第三方網站上，
對於玩家和伺服器管理員來說可能很不方便，
特別是對於經常更新資源包的開發人員來說。  
這個模組的目標是通過讓你可以直接在自己的伺服器上托管資源包來解決這個問題。

## 計劃與進度

### 第一部分：模組開發前的準備工作

- [x] 學習如何為《Minecraft》創建模組
    - [x] 熟練掌握 Java 和 Kotlin
        - [x] Java 和 Kotlin 的基本語法
        - [x] 理解如何在 Kotlin 中使用 Java 反射
    - [x] 熟悉使用 Fabric API 開發模組
    - [x] 學習如何使用 Fabric 網絡功能來發送和接收封包
    - [x] 理解如何使用 Fabric 命令來引入新的命令到遊戲中
    - [x] 學習如何使用 Fabric mixins 來修改遊戲的行為
        - [x] 學習如何使用 IntelliJ IDEA 來反編譯遊戲的源代碼

### 第二部分：模組開發

- [x] 開發配置管理器來處理資源包伺服器的配置  
      （這需要使用 Java 反射）
- [x] 確定服務器如何向客戶端發送資源包下載請求
- [x] 開發資源包伺服器管理器
    - [x] 實現啟動和停止資源包伺服器的功能
    - [x] 啟用更改資源包的功能
    - [x] 計算資源包的 SHA1 雜湊值
    - [x] 向客戶端發送請求

## 解決的問題

### [Server not prompting client to download](https://github.com/iceice666/resourcepack-server/issues/3) 

#### 問題描述

在更新資源包後，sha1 值未更新。

#### [解決方案](https://github.com/iceice666/resourcepack-server/pull/4/commits/91e0ff98ac171994bc61f9500f04c04ce6767dfc)  

注入的類的建構函數僅在服務器啟動時被調用一次。  
因此，當我們更新資源包時，SHA1 值不會被更新。  
解決方案是注入到負責發送**資源包下載請求**的類中。  
這樣，每次服務器發送資源包下載請求時，
將會發送正確的 SHA1 值給客戶端。

## 我學到的東西

這個模組託管在Github上，所以當有些人遇到問題或Bug時會在Github的issue回報。
在和他們的互動中，若他們提供訊息不完整，這個時候就需要猜或一步步引導他們把情況完整的說出來。
有時還會遇到整整半個月都等不到回覆。
這時候就會覺得“好累，我要不要乾脆不理他們算了”，
但是解決問題，看到issue被closed頓時感到如釋重負。

## 參考資料和資源

- [Minecraft Wiki - 資源包](https://minecraft.gamepedia.com/Resource_pack)
- https://fabricmc.net/wiki/start
- https://fabricmc.net/wiki/tutorial:networking
- https://fabricmc.net/wiki/tutorial:commands
- https://www.runoob.com/kotlin/kotlin-tutorial.html
- https://www.runoob.com/kotlin/kotlin-basic-types.html
- https://www.runoob.com/kotlin/kotlin-extensions.html
- https://www.runoob.com/kotlin/kotlin-extend.html
- https://www.runoob.com/kotlin/kotlin-data-sealed-classes.html
- https://www.runoob.com/kotlin/kotlin
