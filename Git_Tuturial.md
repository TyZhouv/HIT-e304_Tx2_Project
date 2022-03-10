# Git OverView
[Git Tuturial Link 1（官方文档）](https://docs.github.com/cn/get-started)    
[Git Tuturial Link 2（Git特性）](https://www.liaoxuefeng.com/wiki/896043488029600)   
[Git Func and Command Overview（Cmd 较全）](https://blog.csdn.net/huwh_/article/details/78505565)  

**Git：分布式版本管理和控制系统**

*记录文件修改的版本控制系统要解决什么问题？*
>1.怕丢失旧版本文件多处保留副本  
>![flex](https://www.liaoxuefeng.com/files/attachments/918921393733152/0)  
>2.不知道每个副本各修改了什么内容  
>3.多人合作一个项目时，要核对每个人的修改，是否会对其他人造成影响  
>4.多人同时进行同一项目开发较麻烦

**Git：分布式 版本管理和分支管理系统** 
特性：
>1. 版本管理和控制：所有文件都被Git管理起来，每个文件的修改、删除，Git都能跟踪，任何时刻都可以追踪、还原历史。
>2. 多人协作开发：强大的分支管理系统支持分支合并、差异对比
>3. 支持所有文本编辑文件的版本控制(C、C++、Matlab、Python..)
><img src="http://assets.processon.com/chart_image/622a04ad1efad407e98862df.png" width = "1800" height = "400" alt="图片名称" align=center />  
>
 


# 1 Git 本地仓库(Local)与远程仓库(Remote)
![Git Remote Index WorkSpace](https://img-blog.csdn.net/20171111113251312?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast) 

|操作|Git 命令 <img width=200>|Note|
|----|----|----|
|创建Git仓库|git init|初始为Git仓库，会在根目录建立一个.git文件夹，进行针对文件修改及不同分支的记录|
|添加文件到暂存区|git add /img<br>git add xxx.txt|add的文件只会被存放到暂存区|
|提交文件|git commit /img -m "xx"<br>git commit xx.py -m "xx"<br>git commit  -m "xxx"|提交给Git仓库|
|撤销尚未提交的修改|git checkout head a.txt b.txt<br>git checkout head *.py*<br>git checkout head||
|查看仓库状态|git status<br>|查看当前仓库有哪些文件增添、修改了还没有被同步;<br>查看当前暂存区是否还有没有未commitd的文件;|
|查看提交日志|git log<br>gitk<br>gitk c_branch<br>gitk --all|git log : 查看提交的日志<br>gitk ：查看指定分支的日志|
|关联远程仓库|git remote add origin &lt;url&gt; ||
|上传本地仓库至Git服务器|git push|默认是上传到origin master分支<br>|
|忽略文件||在根目录建立一个.gitignore文件，把要忽略的文件直接写入.gitignore中，然后add此文件到版本库并提交|
|从服务器clone Git项目|git clone &lt;url&gt;|Download .zip :<br>单纯获得了一个工程文件，不支持pull或者push<br>git clone &lt;url &gt;:<br>git clone会先在当前文件夹建立仓库，再去复制工程，支持git pull或push。<br>如果你想往开源项目上添砖加瓦，使用git clone会好一些。<br>clone会自动关联远程的分支。|
|从服务器拉取项目更新|git pull|clone是将一个库复制到你的本地，是一个本地从无到有的过程<br>pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库<br>git pull相当于是从远程获取最新版本并merge（合并）到本地<br>git pull = git fetch + git merge|
|...|||
# 2 Git 版本切换
Git每次Commit都是一个版本，可以查看各版本之间的差异，并且切换到任意不同版本。
|操作|Git 命令 <img width=300>|Note|
|----|----|----|
|查看版本号|git log --pretty=oneline  |--pretty=oneline表示只显示版本号和commit的注释<br>不要此参数会显示详情|
|项目版本回退及切换|1.git checkout &lt;commit&gt;<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;<br>3.git reset --hard &lt;commit&gt; <br>|1.git checkout &lt;commit&gt; 命令把整个git仓库文件回退到 commit 参数指定的版本<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;命令只回退 filepath 文件到 commit 参数指定的版本<br>不影响其他文件<br>3.git reset --hard &lt;commit&gt; 命令把git的HEAD指针指向到 commit 对应的版本，<br>本地文件内容也会被回退，之后的版本会消失！ 不可逆！！！|
|更新之前某个版本内的文件|git revert &lt;commit&gt;|这种方式不会把版本往前回退，而是覆盖之前的版本内容。<br>只需要让别人更新一下代码就可以了|
|...|||

# 3 Git 分支管理（多人协作、不同模组同时开发）

|操作|Git 命令 <img width=200>|Note|
|----|----|----|
|查看所有分支和当前分支|git branch -a|当前分支前有星号|	
|分支创建|git checkout -b &lt;new-branch-name&gt;|= <br>git branch version2<br> git checkout version2|
|分支切换|git checkout &lt;branch name&gt;|把分支从默认的master切换到version2：<br>git checkout version2|
|分支合并|git merge &lt;branch-name&gt;|通过git checkout 切换到A分支，如果要合并A、B分支不同的内容：<br>git checkout A<br>git merge B|
|解决冲突git mergetoll||用可视化工具显示多个用户之间出现冲突的内容，可以修改后再合并|
|标签创建|git tag 1.0<br>git tag  aaa 1.1|可以通过标签检出、创建分支|
|显示标签列表|git tag||
|...|||
# 4.使用示例
## 4.1 创建本地项目为Git仓库，并上传至e304服务器



## 4.2 从e304克隆Git项目
>note：如果是已经clone，只是需要拉取远端的更新，用git pull即可）


## 4.3 查看本地Git仓库和远程Git仓库的差异（远程Git仓库可能由于他人的提交更新）
**查看本地仓库与远程仓库的差异**
Ubuntu Cmd Flow：   
>git fetch origin
>git diff --stat master origin/master

*-- stat命令的功能是统计哪些文件发生了改变，有多少行产生了改动，并不会给出改动的具体内容。*
output:  
![gitdiff](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/diffimg.png?raw=true)

## 4.4 在本地进行Git项目更新并提交到服务器
## 4.5 Git项目版本切换
Git每次Commit都是一个版本，可以查看各版本之间的差异，并且切换到任意不同版本。
>要实现的功能：
>新建了一个version_back.txt, add后commit到仓库，形成版本。  
>现在需要回退到没有这个txt文件的版本  

**Ubuntu Cmd Flow：**   

>git log --pretty=oneline  


![git log](https://raw.githubusercontent.com/TyZhouv/HIT-e304_Tx2_Project/master/img/gitlog.png)
>git reset --hard 5eb8  


![backimg](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/backimg.png?raw=true)

# 4.6 Git分支管理（创建分支、分支比较、分支合并）
>创建并切换到刚创建的分支
>git checkout version2 -b

![创建并切换到刚创建的分支](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/new%20branch.png?raw=true)
>查看所有分支及当前处于的分支
>git branch -a

![查看当前分支](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/branch%20list.png?raw=true)
>在刚创建的分支 version2 中添加了 version2.txt 和一张图片，并与 master分支比较差异

![分支比较](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/diff_master_version.png?raw=true)
>git checkout master

切换到master分支会发现，本地文件夹中version2.txt的文件消失了

>git merge version2

![merge](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/merge.png?raw=true)
合并master、version2分支，此时会发现处于master分支也有了version2.txt文件


**Git命令（较全）思维导图**
![Git命令（较全）思维导图](https://img-blog.csdn.net/20171111113313194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)   
	
	
	
