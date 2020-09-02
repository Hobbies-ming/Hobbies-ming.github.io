---
title: 工作日の印象 005
tags: 技术 LINUX GIT unzip find locate checkout fetch
key: workday-005
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **unzip 指定解压路径**

  ```shell
  $ unzip example.zip -d /target/path/
  ```

* **locate 命令**

  ```shell
  ## locate 查询系统预建的文件索引数据库（ubuntu 在/var/lib/mlocate.db）
  ## 查询速度快，但可能不一定和当前文件系统同步
  $ locate filename
  
  ## 使用正则表达式
  $ locate -r 're'
  
  ## 忽略大小写
  $ locate -i filename
  
  ## 手动更新数据库，会遍历整个文件系统，非常费时
  $ updatedb
  ```
<!--more-->
* **find 命令**

  ```shell
  ## find 在指定目录下查找文件
  ## 当前目录下查找所有jpg图片
  $ find . -name "*.jpg"
  
  ## 将被拒绝访问的目录清理
  $ find . -name "*.jpg" 2>/dev/null
  
  ## 忽略大小写
  $ find . -iname "*.gif"
  
  ## 正则表达式，必须匹配一个路径而不是文件名，所以前面加 .*/
  $ find . -regex ".*/[a-z|-]*\.d"
  ```

* **git checkout**

  ```shell
  ## 用于切换分支，撤回工作区下的修改
  ## 查看所有分支和当前分支(-v 可以看到最近一次提交)
  $ git branch -a
  $ git branch -v
  
  ## 基于当前分支创建新的本地分支，再切换分支（实际是移动HEAD指针）
  ## checkout分支会刷新工作区,如果工作区修改过，修改的文件不会刷新
  $ git branch dev
  $ git checkout dev
  
  ## 强制覆盖工作区
  $ git checkout -f dev
  
  ## 创建并切换到新分支，上面的命令合并
  $ git checkout -b dev
  
  ## 创建后推送到远程分支，没有会自动创建对应远程分支
  $ git push origin dev:dev
  $ git push origin dev
  
  ## 用版本库或者缓存区刷新（检出）工作区，会优先使用缓存区
  ## 如果之前add过，则需要使用 reset 命令
  $ git checkout .
  
  ## 撤回某一文件的修改
  $ git checkout -- filename
  ```

* **git fetch && git pull**

  ```shell
  ## fetch 去取回远程主机的所有分支更新到本地远程分支
  $ git fetch
  
  ## 检出远程分支或tag
  $ git checkout br-or-tag
  
  ## 将远程分支的最新更新合并到当前对应分支,确保工作区clean
  $ git merge br
  
  ## clean 工作区(删除未跟踪的文件/目录), -n 选项打印会被删除的文件，-f force，-d 选项同时删除文件夹
  $ git clean -n
  $ git clean -f
  $ git clean -fd
  $ git clean -fd -n
  
  ## git pull 先fetch再merge，但仍有区别，建议不要用
  $ git pull
  ```

  