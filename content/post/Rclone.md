---
title: "Rclone"
date: 2020-12-03T11:53:25+08:00
draft: false

---

# Rclone 的使用


网盘同步工具Rclone的使用,rclone是一个非常强大的网盘同步工具。可以用命令行进行操作。

详细使用

　　操作命令

- rclone 命令的语法格式：

　　　　Syntax: [options] subcommand &lt;parameters&gt; &lt;parameters...&gt;

- 常用的 rclone 命令有：

　　　　rclone config - 以控制会话的形式添加rclone的配置，配置保存在.rclone.conf文件中。
　　　　rclone copy - 将文件从源复制到目的地址，跳过已复制完成的。
　　　　rclone sync - 将源数据同步到目的地址，只更新目的地址的数据。
　　　　rclone move - 将源数据移动到目的地址。
　　　　rclone delete - 删除指定路径下的文件内容。
　　　　rclone purge - 清空指定路径下所有文件数据。
　　　　rclone mkdir - 创建一个新目录。
　　　　rclone rmdir - 删除空目录。
　　　　rclone check - 检查源和目的地址数据是否匹配。
　　　　rclone ls - 列出指定路径下所有的文件以及文件大小和路径。
　　　　rclone lsd - 列出指定路径下所有的目录/容器/桶。
　　　　rclone lsl - 列出指定路径下所有文件以及修改时间、文件大小和路径。
　　　　rclone md5sum - 为指定路径下的所有文件产生一个md5sum文件。
　　　　rclone sha1sum - 为指定路径下的所有文件产生一个sha1sum文件。
　　　　rclone size - 获取指定路径下，文件内容的总大小。.
　　　　rclone version - 查看当前版本。
　　　　rclone cleanup - 清空remote。
　　　　rclone dedupe - 交互式查找重复文件，进行删除/重命名操作。

### rclone config

- 开启一个交互式的配置会话。命令格式如下：

　　　　rclone config

### rclone copy

- 将文件从源复制到目的地址，跳过已复制完成的。命令格式如下：

　　　　rclone copy source:sourcepath dest:destpsth

- 说明：
  rclone copy 复制总是指定路径下的数据；而不是当前目录。
  –no-traverse 标志用于控制是否列出目的地址目录。

### rclone sync

　　rclone sync source:path dest:path

- 说明：
  同步数据时，可能会删除目的地址的数据；建议先使用–dry-run 标志来检查要复制、删除的数据。
  同步数据出错时，不会删除任何目的地址的数据。
  rclone sync 同步的始终是 path 目录下的数据，而不是 path 目录。（空目录将不会被同步）

### rclone move

　　rclone move source:path dest:path

- 说明：
  同步数据时，可能会删除目的地址的数据；建议先使用–dry-run 标志来检查要复制、删除的数据。

### rclone purge

- 清空 path 目录和数据。命令格式如下：

　　rclone purge remote:path

- 说明：
  此命令，include/exclude 过滤器失效。
  删除 path 目录下部分数据，请使用 rclone delete 命令

### rclone mkdir

- 创建 path 目录。命令格式如下：

　　rclone mkdir remote:path

### rclone rmdir

- 删除一个空目录。命令格式如下：

　　rclone rmdir remote:path

- 说明：
  不能删除非空的目录，删除非空目录请使用 rclone purge。

### rclone check

- 检查源和目标地址文件是否匹配。命令格式如下：

　　rclone check source:path dest:path

- 说明：
  –size-only 标志用于指定，只比较大小，不比较 MD5SUMs。

### rclone ls

- 列出指定 path 下，所有的文件以及文件大小和路径。命令格式如下：

　　rclone ls remote:path

### rclone lsd

- 列出指定 path 下，所有目录、容器、桶。命令格式如下：

　　　　rclone lsd remote:path

### rclone delete

- 删除指定目录的内容。命令格式如下：

　　rclone delete remote:path

- 说明：
  不同于 rclone purge，rclone delete 可使用 include/exclude 过滤器选择删除文件内容。

#### 一些例子：

- 删除文件大小大于 100M 的文件

　　# 先检查哪些文件将被删除
　　rclone --min-size 100M lsl remote:path # 使用rclone lsl 列出大于100M的文件
　　rclone --dry-run --min-size 100M delete remote:path # 使用--dry-run 检查将要被删除的文件

　　# 使用 rclone delete 进行文件删除
　　rclone --min-size 100M delete remote:path

### rclone size

- 获取指定 path 下所有数据文件的总大小。命令格式如下：

　　rclone size remote:path