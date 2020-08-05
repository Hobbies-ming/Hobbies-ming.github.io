---
title: 工作日の印象 004
tags: 技术 SSH screen LINUX
key: workday-004
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* Arch 远程板子重启后，会重新更新自己的 SSH 公钥，再次 ssh login 时会出现 **RSA Host key 验证失败** 的问题。这里提供两种解决方法：

  ```shell
  ## 1. 删除本地key, 使其重新更新 .ssh/known_hosts 文件
  $ ssh-key -R $host-ip
  $ ssh $user@$host
  
  ## 2. 关闭严格模式进行登录
  $ ssh -o StrictHostKeyChecking=no $user@$host
  ```
<!--more-->
* **screen 命令**

  ```shell
  ## screen 可以在登录界面开多个虚拟终端，并自由切换，不会中断任务的执行。
  ## 建议耗时任务使用 screen 运行，防止中断且不占用主界面
  ## 创建并进入一个视窗
  $ screen
  
  ## 后台运行并离开这个视窗，回到原界面
  $ 按下 ctrl+a+d
  
  ## 列出所有视窗
  $ screen -ls
  
  ## 重新进入被分离的视窗
  $ screen -x $screen-id
  
  ## 删除视窗
  $ screen -X -S $screen-id
  
  ## 自动擦除失效的视窗
  $ screen -wipe
  ```

  