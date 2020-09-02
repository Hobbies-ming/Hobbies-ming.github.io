---
title: 工作日の印象 011
tags: 技术 LINUX GIT reset
key: workday-011
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **git reset 回退到以前版本**

  ```shell
  ## 版本库和源码回退到某个版本
  $ git reset --hard commit-id
  
  ## 仅版本库回退，源码不变
  $ git reset --soft commit-id
  
  ## 回退到上一次提交; 回退到前n次提交
  $ git reset --hard HEAD^
  $ git reset --hard HEAD~2
  ```
<!--more-->
* **Linux 脚本传参数**

  ```shell
  ## 位置参数，从1开始，0是脚本名
  ## read 读用户输入
  ---bash---
  #!/bin/bash
  var=$1
  echo 'The var value is ${var}'
  
  echo 'Input a number: '
  read num
  echo $num
  ```

  