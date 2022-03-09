# Git OverView
[Git Tuturial Link 1](https://pdai.tech/md/devops/tool/tool-git.html)    
[Git Tuturial Link 2](https://pdai.tech/md/devops/tool/tool-git.html)   
[Git Tuturial Link 3](https://pdai.tech/md/devops/tool/tool-git.html)   
[Git Func and Command Overview](https://blog.csdn.net/huwh_/article/details/78505565)

Git：分布式版本管理和控制系统
特性：
>1. 版本管理和控制
>2. 多人协作开发


Git 指针与分支流概述下述功能
# Git 管理思维导图 
![Git Remote Index WorkSpace](https://img-blog.csdn.net/20171111113251312?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  

# Git支持的项目管理操作
|操作|Git 命令|Note|
|----|----|----|
|创建Git仓库|git init||
|提交文件|git add xxx<br>git commit xxx|
|查看仓库状态、日志|git status<br>git log|
|关联远程仓库|git remote add <name> <url>|exp:<br>git remote add origin https://github.com/xxxxxx|
|上传本地仓库至Git服务器|git push||
|从服务器clone Git项目|git clone||
|项目版本回退及切换|||
|查看不同版本之间的差异|||
|查看所有分支和当前分支|git branch -a|当前分支前有*号|	
|分支创建|git branch -b <new-branch-name>|如果仅创建不切换则去掉参数 -b<br>exp:git branch aaa|
|分支切换|git checkout <branch name>|把分支从默认的master切换到aaa：<br>git checkout aaa|
|分支合并|git merge <branch-name>|通过git checkout 切换到A分支，如果要合并A、B分支不同的内容：<br>git checkout A<git merge B>|
|解决冲突|||
|标签创建与修改|||

![Git命令思维导图](https://img-blog.csdn.net/20171111113313194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
# Git 使用示例 （上传本地项目、查看版本之间的差异、版本回退）
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
