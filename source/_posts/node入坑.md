---
title: node入坑
date: 2020-03-25 11:25:59
tags:
---
方式1：
```
childProcess = exec('adb logcat | grep "sqsdk"');
 childProcess.stdout.on("data", (data) => {
            console.log(`${data}`);
        });
```
 到达了maxbuffer便不会输出
 
 <!--more-->
 
 方式2：
 执行脚本文件：不支持多个平台
 
 方式3：
 执行spawn子进程，发现会多出来很多日志
子进程需要关闭父进程来关闭掉


```$xslt
let result = str.search(/sqsdk/);
正则匹配到的位置：1032

03-25 11:51:20.793  8773  8820 V IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>getRecentlyServerData serverData:[recentlyTcpServerProfile = [ sIP=123.125.102.86, sPort=443, pIP=null, pPort=0, protocol=tcp, type=recently ],timeStamp = 0],apnKey:02:00:00:00:00:00
03-25 11:51:20.793  8773  8820 D IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>start getCurrentApn 
03-25 11:51:20.793  1344  1744 E WifiService: enforceCanAccessScanResults: hiding ssid and bssidUID 10368 has no location permission
03-25 11:51:20.793  8773  8820 D IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>end getCurrentApn key = 02:00:00:00:00:00
03-25 11:51:20.793  8773  8820 I IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>load 20002_apnisps_for_channel_session
03-25 11:51:20.795  8773  8820 V IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>get current apn optimum server list, apnKey is 02:00:00:00:00:00, ispKey isother
03-25 11:51:20.795  8773  8773 D sqsdk-SqTrackActionManager: sq trackAction event:SqTrackAction{event='open_game', name='打开游戏'}
03-25 11:51:20.795  8773  8820 V IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>get optimum server list, key is other
03-25 11:51:20.795  8773  8820 I IIpInfoManager(MiLinkSDK)(misdk): SessionManagerForSimpleChannel_=>load 20002_optservers_for_channel_session
```

### 获取当前component的实例


代码示例

```
//main.js
window._vue = new Vue({
  router, render: h => h(App)
}).$mount("#app");

//component组件
mounted() {
      let _this = this;
      getRecentFiles(function(tmpFiles) {
        console.log("tmpFiles:"+tmpFiles);
        //原始数据被reverse
        _this.recentFiles = { ...tmpFiles.reverse() };
        console.log("最近文件1", _this.recentFiles);

        console.log("tmpFiles:"+tmpFiles);
        window._vue.recentFiles = { ...tmpFiles.reverse() };
        console.log("最近文件1", window._vue.recentFiles);
        if (window._vue.recentFiles == _this.recentFiles){
          console.log("相同");
        }else {
          console.log("不同");
        }
      });
      console.log("mounted");
    }
    
```
原始数据：
```
"{\"path\":\"/Users/kuyuzhiqi/Downloads/1587029980r9pGVrpMjB_out/2020_04_16_17_58_28/report.html\",\"time\":\"2020-04-16 19:03:02\"}"
```
```
"{\"path\":\"/Users/kuyuzhiqi/Desktop/appdetection/mwmb/report.html\",\"time\":\"2020-04-16 19:04:01\"}"
```

运行结果：


