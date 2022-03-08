# Git OverView
[Git Tuturial Link](https://www.runoob.com/markdown/md-link.html)  

Git : Distributed version control system  
Feature :  Aim to modified details  
Support : Version Control  
Git 指针与分支流概述下述功能
# Git支持的项目管理操作
|操作|Git 命令|Note|
|----|----|----|
|创建Git仓库|git init||
|提交文件|git add xxx<br>git commit xxx|
|查看仓库状态、日志|git status<br>git log|
|上传本地仓库至Git服务器|git push||
|从服务器clone Git项目|git clone||
|项目版本回退及切换|||
|查看不同版本之间的差异||
|分支创建|
|分支切换|
|分支合并|
|解决冲突|
|标签创建与修改|

# Git 使用示例
## 1 创建、上传本地项目仓库
**Ubuntu Cmd Flow ：**  
示例：
项目文件夹名字为 HIT e304_Tx2_Project
```C++
文件树一级结构为：  
├── HIT_PROJ  
├── readme.md  
└── Study  
```

>1. cd HIT e304_Tx2_Project  


>2. git init  


git init 即用来创建Git仓库，会在项目文件夹下新建一个.git文件夹，记录文件的修改信息
>3. git status
```C++
nvidia@nvidia-tian:~/HIT e304_Tx2_Project$ git status
位于分支 master
您的分支与上游分支 'origin/master' 一致。

未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）

	HIT_PROJ/

提交为空，但是存在尚未跟踪的文件（使用 "git add" 建立跟踪）
  
提交为空，但是存在尚未跟踪的文件（使用 "git add" 建立跟踪）
```

>4. git add HIT_PROJ/

可以用Tab补全

>5. git status
pic

>6. git commit -m "add HIT_PROJ"
```C
nvidia@nvidia-tian:~/HIT e304_Tx2_Project$ git commit -m "Init projrct git Commit add files"
[master 0a273eb] Init projrct git Commit add files
 81 files changed, 5466 insertions(+)
 create mode 100644 "HIT_PROJ/ty_workspace/Mnist_Demo/mnisi_cpu_ws/D:\\python\\minist/MNIST/processed/test.pt"
 create mode 100644 "HIT_PROJ/ty_workspace/Mnist_Demo....
```

>7. git status
```python
nvidia@nvidia-tian:~/HIT e304_Tx2_Project$ git status
位于分支 master
您的分支领先 'origin/master' 共 1 个提交。
  （使用 "git push" 来发布您的本地提交）

无文件要提交，干净的工作区

```
## 2 git diff查看修改内容
## 3 版本回退
