---
title: 工作日の印象 010
tags: 技术 LINUX GIT commit clone source export
key: workday-010
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **git commit**

  ```shell
  ## -a 只能将已跟踪的文件修改/删除提交到暂存区，没跟踪的会使用失败
  $ git commit -a -m 'info'
  $ git commit -am 'info'
  
  ## 一般
  $ git status
  $ git add .
  $ git commit -m 'info'
  
  ## 长评，进入vim
  $ git commit
  
  ## 长评，多行
  $ git commit -m '
  $ > foo
  $ > bar'
  ```
<!--more-->
* **git clone - SSL error**

  ```shell
  ## https 下载时，取消 SSL 验证
  $ git config --global http.sslVerify false
  ```

* **export & source**

  ```shell
  ## export 是将本地变量设为环境变量，也就是当前脚本结束，父脚本也可以使用
  ## source 是 bash 的内置命令，等同于点命令 .
  ## source 读取脚本内容到当前环境执行，变量会留存
  $ source run.sh
  $ . run.sh
  
  ## 这两种方式等同，需要脚本有执行权限
  ## 会创建子shell并执行命令，继承父环境的变量，但自己的变量不会带回父环境除非export
  $ chmod +x run.sh
  $ sh run.sh
  $ ./run.sh
  ```