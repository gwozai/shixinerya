---
title: "Minio"
date: 2020-12-04T18:16:31+08:00
draft: false

---

# Minio

同阿里云的oss，七牛云的对象存储

用docker安装minio

```shell
docker run -p 9000:9000 --name minio \
-d --restart=always \
-e "MINIO_ACCESS_KEY=#自己的账号" \
-e "MINIO_SECRET_KEY=#自己的密码" \
-v /home/data:/data \
-v /home/config:/root/.minio \
minio/minio server /data
```





minio rclone的 config配置：

```shell
[minio]
type = s3
provider = Minio
env_auth = false
access_key_id = # 自己的账户名
secret_access_key = # 自己的密码
region = cn-east-1
endpoint = # 自己的ip地址
location_constraint = 
server_side_encryption =
```



想法：github action 可以运行docker容器，我在docker容器里面安装Minio

