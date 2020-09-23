---
title: 工作日の印象 011
tags: 技术 LINUX GIT reset
key: workday-011
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **git reset 回退或穿越**

  ```shell
  ## 版本库和源码回退到某个版本
  ## 清空暂存区并刷写工作区
  $ git reset --hard commit-id
  
  ## 仅版本库回退，源码不变
  ## 被撤销版本的修改退回到暂存区（原暂存区的内容仍保留不受影响）
  $ git reset --soft commit-id
  
  ## 暂存区和被撤销版本的修改全部退回到工作区，适合回退后删除文件
  $ git reset --mix commit-id
  
  ## 回退到上一次提交; 回退到前n次提交
  $ git reset --hard HEAD^
  $ git reset --hard HEAD~2
  
  ## 撤销远程库的问题提交，修改后重新提交
  $ git reset --soft commit-id
  ## sync with locate
  $ git push --force
  ## do some fixes
  $ git commit -am ‘xxx'
  $ git push
  
  ## 查看所有的操作记录，包括被撤销的提交
  $ git reflog
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

  