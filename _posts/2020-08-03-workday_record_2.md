---
title: 工作日の印象 002
tags: 技术 apt Ubuntu源 tar cp LINUX
key: workday-002
author: MING
---

* **sudo apt update 时报错：E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)**

  ```shell
  ## check who is using 'apt'
  ## -i ignores uppercase/lowercase
  ps aux | grep -i apt
  
  ## you find apt.systemd.daily update, 这是一个后台自动运行的系统更新的守护进程
  sudo kill $pid
  
  ## check again by "ps aux | grep -i apt", if not, force to kill it
  sudo kill -9 pid
  ```

* **Ubuntu16.04 更换清华源**

  ```shell
  ## 备份源列表
  cp /etc/apt/sources.list /etc/apt/sources.list.bak
  
  ## 使用清华源覆盖或者置顶（推荐覆盖如果有其他源的报错）
  ## https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/
  sudo vim /etc/apt/sources.list
  ---
  # 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
  
  # 预发布软件源，不建议启用
  # deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-proposed main restricted universe multiverse
  ---
  
  ## update index
  sudo apt update
  ```

* **Linux 压缩命令 tar**

  ```
  ## f - 指定档案名，置后
  tar -zcvf /path/to/target-tar /source
  ```

* **Linux 复制命令 cp**

  ```shell
  ## -v, verbose, 打印拷贝文件过程
  cp -v a b
  
  ## -r 递归复制目录到目标位置下,若目标不存在则类似复制为目标
  cp -r dir1 dir2
  ```

  