
## 學習計劃


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

