---
title: 工作日の印象 003
tags: 技术 nfs Ubuntu mount LINUX
key: workday-003
author: MING
---

## 在两台 Linux 主机之间共享文件夹

1. **安装 NFS (Network File System)** 

   ```shell
   ## server end , the dir shared
   sudo apt-get install nfs-kernel-server
   
   ## client end
   sudo apt-get install nfs-common
   ```

2. **服务主机配置 NFS exports 文件**

   ```shell
   sudo vim /etc/exports
   ---
   /path/to/share $client_ip(rw,sync,no_subtree_check,no_root_squash)
   ## e.g., /home/root/share 203.0.113.*(rw,sync,no_subtree_check,no_root_squash)
   ---
   ```

3. **服务主机启动 NFS 服务**

   ```shell
   ## check status
   service nfs-server status
   
   ## start nfs
   service nfs-server start
   
   ## restart nfs
   service nfs-server restart
   ```

4. **客户端挂载共享文件夹**

   ```shell
   ## check the export list on server can be seen on client or not
   showmount -e $server_ip
   
   ## mount
   sudo mount -t nfs $server_ip:/path/to/share /home/root/share
   
   ## check mount
   mount -t nfs
   ```

   