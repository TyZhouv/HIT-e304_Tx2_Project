# Git OverView
[Git Tuturial Link 1](https://docs.github.com/cn/get-started)    
[Git Tuturial Link 2](https://pdai.tech/md/devops/tool/tool-git.html)   
[Git Func and Command Overview](https://blog.csdn.net/huwh_/article/details/78505565)  
[Git命令（较全）思维导图](https://img-blog.csdn.net/20171111113313194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)   

**Git：分布式版本管理和控制系统**  
特性：
>1. 版本管理和控制
>2. 多人协作开发
>3. 支持所有文本编辑文件的版本控制(C、C++、Matlab、Python..)

# 1 Git 本地仓库(Local)与远程仓库(Remote)
![Git Remote Index WorkSpace](https://img-blog.csdn.net/20171111113251312?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  
|操作|Git 命令 <img width=300>|Note|
|----|----|----|
|创建Git仓库|git init|初始为Git仓库，会在根目录建立一个.git文件夹，进行针对文件修改及不同分支的记录|
|提交文件|git add /img<br>git add xxx.txt|add的文件只会被存放到暂存区|
|提交文件|git commit /img -m "x"<br>git commit x.py -m "xx"<br>git commit  -m "xxx"|提交给Git仓库|
|撤销尚未提交的修改|git checkout head a.txt b.txt<br>git checkout head *.py*<br>git checkout head||
|查看仓库状态、日志|git status<br>git log<br>gitk<br>gitk c_branch<br>gitk --all|git status :<br>查看当前仓库有哪些文件增添、修改了还没有被同步;<br>查看当前暂存区是否还有没有未commitd的文件;<br>git log : <br>查看提交的日志<br>gitk 查看指定分支的日志|
|关联远程仓库|git remote add origin &lt;url&gt; |exp:<br>git remote add origin https://github.com/xxxxxx|
|上传本地仓库至Git服务器|git push|默认是上传到origin master分支<br>|
|忽略文件||在根目录建立一个.gitignore文件，把要忽略的文件直接写入.gitignore中，然后add此文件到版本库并提交|
|从服务器clone Git项目|git clone|Download .zip :<br>单纯获得了一个工程文件，不支持pull或者push<br>git clone &lt;url &gt;:<br>git clone会先在当前文件夹建立仓库，再去复制工程，支持git pull或push。<br>如果你想往开源项目上添砖加瓦，使用git clone会好一些。<br>clone会自动关联远程的分支。|
|从Remote拉取项目更新|git pull|clone是将一个库复制到你的本地，是一个本地从无到有的过程<br>pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库<br>git pull相当于是从远程获取最新版本并merge（合并）到本地<br>git pull = git fetch + git merge|
# 2 Git 版本切换
Git每次Commit都是一个版本，可以查看各版本之间的差异，并且切换到任意不同版本。
>要实现的功能：新建了一个version_back.txt：This is Version1 , add后commit到仓库，形成版本。  
>现在需要版本回退到没有这个txt文件的版本  

**Ubuntu Cmd Flow：  **   

>git log --pretty=oneline  
  
![git log]()
>git reset --hard 5eb8  
  
![backimg]()
  
|操作|Git 命令 <img width=300>|Note|
|----|----|----|
|查看版本号|git log --pretty=oneline  |--pretty=oneline表示只显示版本号和commit的注释<br>不要此参数会显示详情|
|项目版本回退及切换|1.git checkout &lt;commit&gt;<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;<br>3.git reset --hard &lt;commit&gt; <br>|1.git checkout &lt;commit&gt; 命令把整个git仓库文件回退到 commit 参数指定的版本<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;命令只回退 filepath 文件到 commit 参数指定的版本<br>不影响其他文件<br>3.git reset --hard &lt;commit&gt; 命令把git的HEAD指针指向到 commit 对应的版本，<br>本地文件内容也会被回退，之后的版本会消失！ 不可逆！！！|
|更新之前某个版本内的文件|git revert &lt;commit&gt;|这种方式不会把版本往前回退，而是覆盖之前的版本内容。<br>你只需要让别人更新一下代码就可以了|
|...|||

# 3 Git 分支管理（多人协作、不同模组同时开发）

Git 指针与分支流概述下述功能
|操作|Git 命令 <img width=300>|Note|
|----|----|----|
|查看所有分支和当前分支|git branch -a|当前分支前有星号|	
|分支创建|git checkout -b &lt;new-branch-name&gt;|= <br>git branch version2<br> git checkout version2|
|分支切换|git checkout &lt;branch name&gt;|把分支从默认的master切换到version2：<br>git checkout version2|
|分支合并|git merge &lt;branch-name&gt;|通过git checkout 切换到A分支，如果要合并A、B分支不同的内容：<br>git checkout A<br>git merge B|
|解决冲突git mergetoll||用可视化工具显示多个用户之间出现冲突的内容，可以修改后再合并|
|标签创建|git tag 1.0<br>git tag  aaa 1.1|可以通过标签检出、创建分支|
|显示标签列表|git tag||
|...|||

# 4 创建本地项目为Git仓库，并上传至e304服务器

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

>8.

```
	
# 5 git diff查看本地仓库与远程仓库的差异
>查看本地仓库与远程仓库的差异
Ubuntu Cmd Flow：   
```python
  git fetch origin
  git diff --stat master origin/master
  #git diff -- stat命令的功能是统计哪些文件发生了改变，有多少行产生了改动，并不会给出改动的具体内容。
```
output:  
![gitdiff]()



	
	
	
