---

title: 工作日の印象 009
tags: 技术 GIT diff PYTHON argparse
key: workday-009
excerpt_type: html
excerpt_separator: <!--more-->
author: MING
---

* **git diff**

  ```shell
  ## 比较同一文件两个版本的差异
  ## br_a 是源分支， br_b 是目标分支
  ## 差异按小节组织，以@@开头如@@-4,6 +4,7@@
  ## --- 开头行表示源文件特有，+++ 开头行表示目标文件特有
  $ git diff br_a br_b src/example.py
  ```
<!--more-->
* **Git 使用 commit ID 查找某次提交详情的两种方法**

  ```shell
  ## 本地操作, commit-id 是 SHA-1 hash值，如 80879bb6790b99ebe634cb70df60e0b1137b7160
  ## 一般使用hash前七位就可以搜索了
  ## git show 展示该次提交的详细信息和修改内容
  $ git show commit-id
  
  ## github/gitlab 【在线查看】某次提交，页面只能切分支和tag
  ## 进入repo，在网址后面追加 /commit/commit-id ，可以看到这一版的修改
  # 例如link: github.com/user/repo/commit/commit-id
  # 【看这个版本下的所有文件】：github.com/user/repo/tree/commit-id
```
  
* **Python argparse 模块**

  ```
  ## 支持位置参数和选项参数
  > import argparse
  > parser= argparse.ArgumentParser(description='process some integers')
  > parser.add_argument('param_name', type=str, help='first pos param')
  > parser.add_argument('param2_name', type=str, help='second pos param')
  > parser.add_argument('--param3_name', type=int, help='a optional param') ## 可读性更好，位置自由
  
  ## usage
  > python test.py -h  ## show all helps
  > python test.py abc def param3_name 123
  
  ## resolve
  > args= parser.parse_args() ## 解析sys.argv
  > args.param_name  ## 'abc' 
  > args.param2_name  ## 'def'
  > args.param3_name  ## 123
  ```

  