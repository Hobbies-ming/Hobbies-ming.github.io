---
title: 工作日の印象 007
tags: 技术 LINUX mount sshfs samba
key: workday-007
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* 如果两台 LINUX 主机无法进行 NFS 挂载，在服务端安装 Samba 模拟windows，客户端即可通过 cifs 挂载目标位置

* 一个更加简单的方法是使用 sshfs，只要两台机器支持ssh连接即可
  <!--more-->

  ```shell
  ## sshfs 原理是基于SFTP进行远程连接并访问
  $ sshfs user@host:share/ host_share/
  
  ## 查看
  $ mount
  $ df -hT
  
  ## 解挂
  $ umount host_share/
  
  ## dd 测试挂载资源的访问速度，按指定大小的块从输入文件拷贝到输出文件
  $ dd if=host_share/bigfile of=/dev/null bs=1M
  ```

* 修改linux 用户密码

  ```shell
  ## passwd 修改 user用户的密码
  $ passwd user
  ```

  