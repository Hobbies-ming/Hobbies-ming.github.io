---
title: 工作日の印象 008
tags: 技术 numpy make hexdump
key: workday-008
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **array.tofile() / np.fromfile()**

  ```python
  ## 将数组数据以二进制写入文件，不适合object类型数据，没有数组元信息如形状、元素类型
  > a= np.ndarray((3,4),dtype=float32)
  > a.tofile('test.bin')
  > b= np.fromfile('test.bin', dtype=float32) ## 读到一个一维数组里
  > b= b.reshape((3,4)) ## 还原原数据
  ```
<!--more-->
* **np.save() / np.load()**

  ```python
  ## np 专有的二进制格式，保存为后缀名.npy文件中
  ## 支持object类型数据如字典、列表
  > np.save('test.npy', a)
  > c= np.load('test.npy') ## 不需要reshape
  ```

* **make / cmake**

  ```shell
  ## 对于单个源文件，用 gcc 编译即可
  ## 对于多个源文件的项目，make 按照 makefile 文件指定的命令去编译链接
  ## 手写 makefile 比较麻烦，所以 cmake 可以生成 makefile 文件
  ## 最终手写更为简单的 cmakelists.txt 文件
  ```

* **hexdump**

  ```shell
  ## 十六进制格式查看二进制文件
  $ hexdump -C test.npy
  ```

  