
## 學習計劃

- [x] 配置環境 (2天)
- [x] Dart入門
- [x] 閱讀[教學](https://ithelp.ithome.com.tw/users/20119550/ironman/2221) (30天)
    - [x] Flutter hello world
    - [x] Flutter basic widgets
        - [ ] 延伸：[Flutter Widget of the Week](https://www.youtube.com/watch?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) on Youtube
    - [x] Flutter packages
    - [ ] App 開頭動畫
    - [ ] Firebase與Bloc Design Pattern 
    - [ ] Flutter Bloc 套件介紹 (1) Events、States和Transitions 
    - [ ] Flutter Bloc 套件介紹 (２) BlocBuilder、BlocProvider和BlocListener 
    - [ ] 實作Authentication Bloc 
    - [ ] 實作Login Bloc、Firebase Authentication 
    - [ ] 使用SharedPreference記下帳號、接上TMDb API 
    - [ ] 實作Movie Bloc 
    - [ ] Flutter測試框架以及Mockito Package使用範例介紹 
    - [ ] 如何用Mockito測試Bloc 
    - [ ] 測試Movie API和Movie Bloc 
    - [ ] 美化首頁(1) 滑動吧！電影卡片 
    - [ ] 美化首頁(2) 增加Drawer和標題文字動畫 
    - [ ] 實作Youtube Bloc、Youtube API 
    - [ ] 設計電影細節頁面、播放Youtube影片 
    - [ ] 使用Firestore快速建造簡易留言區 
    - [ ] 上傳圖片到Firebase Storage 
    - [ ] 在留言取得並顯示使用者的照片 
    - [ ] 使用FCM發送通知給使用者 
    - [ ] Profile Mode檢測App效能 
    - [ ] 輸出Release APK 
- [ ] 自己製作一個一起看影片的APP (14天)
    - [ ] 前端：用戶界面部分
    - [ ] 後端：串流服務

### 學習資料
- 第 11 屆 iThome 鐵人賽 [Flutter---Google推出的跨平台框架，Android、iOS一起搞定 系列](https://ithelp.ithome.com.tw/users/20119550/ironman/2221)
- [Flutter Widget of the Week](https://www.youtube.com/watch?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) on Youtube
<!-- ============================================================ -->

## 碰到的困難

### adb device: no permission


在輸入`adb devices`命令之後出現了如下output
```
> adb devices
List of devices attached
<device id>        no permission
```

#### 解決辦法

在Android USB有以下幾種連接模式
- data transfer
- usb network sharing
- midi
- ptp
- charging only / no data transfer

經過測試，只有ptp模式下才可以連接（結果顯示爲unauthorized或device）  
嗯，靈異現象（機魂不悅.jpg）


### The SDK directory is not writable 

在Android模擬的時候報了以下錯誤
```
The SDK directory is not writable (/opt/android-sdk)
```

由於`/opt`裡的大多是root權限，普通的User權限當然無法做修改，當然也無法更新檔案

#### 解決辦法

更改資料夾權限
```bash
> sudo chown -R $(whoami) /opt/android-sdk
```

