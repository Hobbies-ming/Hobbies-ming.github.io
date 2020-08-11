---
title: 工作日の印象 006
tags: 技术 LINUX tar hostname vim
key: workday-006
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **hostname**

  ```shell
  ## 查看主机名
  $ hostname
  
  ## 设置主机名，会更新 /etc/hostname 文件
  $ sudo hostnamectl set-hostname newname
  
  ## 配置内网域名
  $ sudo vim /etc/hosts
  ---hosts---
  xxx
  xxx
  ip hostname.localdomain hostname
  ---
  ```
<!--more-->
* **tar 解压并重命名根目录**

  ```shell
  ## --strip-components n 去掉压缩包前n层目录
  $ mkdir test && tar -zxvf example.tar.gz -C ./test --strip-components 1
  ```

* **不解压情况下，查看压缩包目录结构**

  ```shell
  ## 1. use tar, -t test
  $ tar -tvf example.tar.gz
  
  ## 2. use vim, 不仅可以查看，还可以按ENTER键选择文件打开
  $ vim example.tar.gz
  
  ## 3. use less, 一样可以查看文件内容
  $ less example.tar.gz
  ```

* **vim 进入可视化模式**

  ```shell
  ## 进入vim 后 按 v 进入可视化模式
  ## 方向键选中文本
  ## 按 y 复制
  ## 按 p 粘贴
  ```