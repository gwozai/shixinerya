+++

title="windows的一些脚本"
tags=["定时任务","邮箱"]
categories=["定时任务","邮箱"]
date="2020-12-05T09:17:57+08:00"
toc=true

+++



# window的一些脚本



## 校园网开机认证太麻烦，我用脚本使认证开机自启。

```powershell
::查看可用网络
netsh wlan show networks
::断开WiFi连接
netsh wlan disconnect
::连接WiFi ZBXS-GiWiFi
netsh wlan connect ssid=ZBXS-GiWiFi name=ZBXS-GiWiFi
```

## 可以使用命令行进行邮件推送

使用软件blat [ 蓝奏云下载 ](https://myfileforever.lanzous.com/io6Cuj2bpob) 

官方网址[happy mailing : Blat online](https://www.blat.net/)

```powershell
:: 进入到blat的目录下 \blat\blat3222\full
blat -install smtp.qq.com xxxxxxx@qq.com 3 25  
::blat支持SMTP服务要到qq邮箱申请
blat body.txt -to xxxxxxxx@qq.com -u "xxxxxxxxx@qq.com" -pw "xxxxxxxxxx" -subject "嗨!HELLO from blat " -charset Gb2312 # body.txt 是要发送的内容 -to 发送给谁 -u 用户名 -pw 用户名的密码 -charset 使用中文编码
```

![image-20201205094236007](http://kodohub.yiye.show/img/image-20201205094236007.png)



参考连接[用blat邮件发送](https://my.oschina.net/SamXIAO/blog/1790383)



## 一些命令

```powershell
::打印时间
echo %date% %time%
```

设置关机

shutdown 

- -r 重启

- -s 关机

- -t 时间 

  ```powershell
  shutdown -t 1000
  ```

  

- -a 关机命令取消

  ```powershell
  shutdown -a
  ```

  