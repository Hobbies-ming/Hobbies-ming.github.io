---
title: 工作日の印象 001
tags: 技术 SSL mount LINUX
key: workday-001
author: MING
---

* Linux 安装 Pip 及 Python 包时，出现 **SSL: CERTIFICATE_VERIFY_FAILED**, certificate expired 错误（SSL 证书具有加密和服务器身份验证的作用，相当于服务器的身份证ID）

  ```shell
  ## use --no-check-certific option to SKIP
  ## then "python get-pip.py", it'll download and install pip
  ## maybe it's still wrong because of the SSL certificate. So let's install offline
  $ wget --no-check-certific https://bootstrap.pypa.io/get-pip.py
  
  ## use pip to install package, add below options to SKIP
  $ pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org $package_name
  
  ## another permanent fix
  $ mkdir ~/.pip && vim ~/.pip/pip.conf
  ---pip.conf---
  [global]
  trusted-host = pypi.python.org
                 pypi.org
                 files.pythonhosted.org
  ---pip.conf---
  ```

* **Linux 挂载命令 mount** 

  ```shell
  ## mount windows share dir to linux
  ## -t denotes type of file system, e.g., ext3/tmpfs
  ## cifs - common internet file system
  $ sudo mount -t cifs //ip/path-to-dir ~/linux-dir -o username=$user,noexec
  ```

  * **ERROR: mount: cannot mount read-only**

    ```shell
    ## 2020/8/3
    ## you need to install the cifs-utils package
    sudo apt install cifs-utils
    ```

  * **ERROR: mount error(2): No such file or directory**

    ```shell
    ## try to install package keyutils
    ## maybe cifs cannot find the keyutils
    sudo apt install keyutils
    ```

  * **ERROR: mount error(13): Permission denied**

    ```shell
    ## use option "sec=ntlm" to set security mode which decides password encryption
    sudo mount -t cifs //ip/path-to-dir ~/linux-dir -o sec=ntlm,username=$user,noexec
    ```