---
title: linux命令
date: 2019-12-18 14:29:30
tags:
- 工具
- linux
- ssh
- vscode
categories: others
typora-root-url: linux命令
---

# 文件操作

- **复制文件夹**

  ```python
  cp -r /source_direction /target_direction
  ```

- **解压`.gz`文件**

  ```python
  tar -zxvf filename.tar.gz
  # tar是打包，不压缩
  # gz是用gzip把打包成.tar的文件压缩
  ```

- **拆包`.tar`文件**

  ```
tar -xvf filename.tar
  ```
  
- **打包成`.tar`文件**

  ```
tar -cvf tar-file-name.tar original-file-name
  ```
  
  

- **解压`.zip`文件**

  解压到当前文件夹

  ```
  unzip filename.zip
  ```

- **批量复制文件**

  ```python
  cp -r /fold/. /target_dir
  ```

- **删除文件夹**

  ```
  rm -rf filedir
  ```

  

# 服务器操作

- **使用`srun`提交任务排队**

  ```python
  srun -t 300 -w node02 --gres=gpu:1 python filename.py
  ```

- **使用`sbatch`提交排队任务**

  创建文件`submit_jobs.sh`: 注意这个文件不能从txt文件改格式新建为sh，否则会出现unix格式问题，如果出现问题可以将之前的sh文件复制过来用！

  ```python
  #!/bin/bash
  #SBATCH -J jingge # job name
  #SBATCH -p defq # partition name (should always be defq)
  #SBATCH -N 1 # number of computing node (should always be 1)
  #SBATCH --ntasks=1 # maximum number of parallel tasks (processes)
  #SBATCH --gres=gpu:1 # number of gpus allocated on each node
  #SBATCH -t 105:00 # maximum running time in hh:mm:ss format
  python filename.py
  ```

   Make the script executable by 激活任务

  ```
  chmod a+x submit_jobs.sh
  ```

   submit the job with `sbatch`  提交任务

  ```
  sbatch submit_jobs.sh #据说不用激活，直接提交就可以
  ```

   取消任务

  ``` 
  scancel your_jobID
  ```

  （实时）跟踪任务，输出到屏幕（如果运行结束后再tail，只会打屏最后结尾的地方）

  ```python
  tail -f slurm-your_jobID.out # out文件可以直接查看
  ```

- 服务器后台运行程序

  ```
  tmux
  ```

- 服务器后台运行保存log文件（不适用于srun提交程序时）

  ```
  nohup python -u filename.py > filename.log 2>&1 &
  ```

  

# tmux使用

- 列出所有session

  ```python
  tmux ls
  ```

- 创建一个新的session
  ```
  tmux new -s <name-of-my-session>
  ```
  
- 进入名为try的session

  ```
  tmux attach -t try
  ```
  
- 关闭session回到原来的界面

  ```python
  tmux kill-session -t session_name/index
  #or:
  tmux kill-session
  #or
  ctrl+d
  #or
  exit
  ```

- 从原始界面回进上一次tmux会话

  ```python
  tmux a
  ```

- 从原始界面回进指定tmux会话

    ```python
    tmux a -t foo # 恢复名称为 foo 的会话，会话默认名称为数字
    ```

# 日志

-  **记录日志又打屏**

   nohup command > myout.file 2>&1 &

   tailf myout.file

 2>&1 >output.log 

# VSCode快捷键

- F1或 `Ctrl+Shift+P` 打开命令面板

# 配置相关

- 换源

  ```python
  pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  # pip换源，加快下载速度
  ```

- 安装tensorboard可视化

  ```python
  pip install tensorboardX
  pip install tensorboard
  pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  # pip换源，加快下载速度
  pip install tensorflow
  ```

# 版本匹配问题

- tensorboard

  ```\
  tensorflow 1.14.0 + pytorch1.1.0+python 3.7.3+tensorboard 2.0.2?？？？？？
  ```

  

