---
title: "Aria2"
date: 2020-12-04T18:55:34+08:00
draft: false
---

# aria2

环境：centos7

## aria2的安装



一键脚本：// 因为网络原因，如果没有安装好的话多试几次，

```shell
wget -N git.io/aria2.sh && chmod +x aria2.sh && ./aria2.sh
```







![image-20201204185720358](https://gitee.com/yiyehub/CND/raw/main/note/image-20201204185720358.png)

选择 1 进行安装



## 配置自动上传脚本

[Aria2 一键安装管理脚本 增强版](https://p3terx.com/go/aHR0cHM6Ly9naXRodWIuY29tL1AzVEVSWC9hcmlhMi5zaA==) 整合了 [Aria2 完美配置](https://p3terx.com/go/aHR0cHM6Ly9naXRodWIuY29tL1AzVEVSWC9hcmlhMl9wZXJmZWN0X2NvbmZpZw==) ，安装后会附带一些附加功能脚本功能脚本，RCLONE 自动上传脚本就是其中之一。由于默认不启用，所以需要手动启用。

> **TIPS:** 本项目的上传脚本使用更稳定快速的原生命令上传方式，而非处在测试阶段的挂载方式，这点和一般的脚本不同。

- 输入`nano /root/.aria2c/aria2.conf`打开 Aria2 配置文件进行修改。或使用[Aria2 一键安装管理脚本 增强版](https://p3terx.com/go/aHR0cHM6Ly9naXRodWIuY29tL1AzVEVSWC9hcmlhMi5zaA==)中的手动修改选项打开配置文件进行修改。找到“下载完成后执行的命令”，把`clean.sh`替换为`upload.sh`。

```none
# 下载完成后执行的命令
on-download-complete=/root/.aria2c/upload.sh
```

> ![image-20201204191754284](https://gitee.com/yiyehub/CND/raw/main/note/image-20201204191754284.png)

- 输入`nano /root/.aria2c/script.conf`打开附加功能脚本配置文件进行修改，有中文注释，按照自己的实际情况进行修改，第一次使用只建议修改网盘名称。

```none
# 网盘名称(RCLONE 配置时填写的 name)
drive-name=OneDrive
```

- 重启 Aria2 。脚本选项重启或者执行以下命令：

```none
service aria2 restart
```

## 检查是否配置成功

执行 `upload.sh` 脚本，提示 `success` 即配置成功。

```none
/root/.aria2c/upload.sh
```

## 使用方法

当进行完以上所有操作，现在下载文件就会自动上传至相应的网盘。

Aria2 是命令行后端软件，需要配合前端 GUI 才能有更好的使用体验，对于从来没有接触过的萌新，建议去看《[Aria2 前端面板 AriaNg 使用教程](https://p3terx.com/archives/aria2-frontend-ariang-tutorial.html)》来了解相关基础知识。

原文链接：

[Aria2 + Rclone 实现 OneDrive、Google Drive 等网盘离线下载 - P3TERX ZONE](https://p3terx.com/archives/offline-download-of-onedrive-gdrive.html)

