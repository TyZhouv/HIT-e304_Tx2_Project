# Git OverView
[Git Tuturial Link 1（官方文档）](https://docs.github.com/cn/get-started)    
[Git Tuturial Link 2（Git特性）](https://www.liaoxuefeng.com/wiki/896043488029600)   
[Git Func and Command Overview（Cmd 较全）](https://blog.csdn.net/huwh_/article/details/78505565)  
[MarkDown Edit Helper](https://www.runoob.com/markdown/md-image.html)
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
><img src="http://assets.processon.com/chart_image/622a04ad1efad407e98862df.png" width = "1800" height = "400" alt="远程和本地仓库示意图" align=center />  


# 1 Git 本地仓库(Local)与远程仓库(Remote)
![Git Remote Index WorkSpace](https://img-blog.csdn.net/20171111113251312?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast) 


>Remote : 表示服务器或 e304-Gitlab  
>Repository : 表示本地的 Git 仓库  
>Index ：表示暂存区  
>workspace : 表示具体项目文件的工作空间  

|操作|Git 命令 <img width=200>|Note|
|----|----|----|
|创建Git仓库|git init|初始为Git仓库，会在根目录建立一个.git文件夹，进行针对文件修改及不同分支的记录|
|添加文件到暂存区|git add /img<br>git add xxx.txt|add的文件只会被存放到暂存区|
|提交文件|git commit /img -m "xx"<br>git commit xx.py -m "xx"<br>git commit  -m "xxx"|提交给Git仓库|
|撤销尚未提交的修改|git checkout head a.txt b.txt<br>git checkout head *.py*<br>git checkout head||
|查看仓库状态|git status<br>|查看当前仓库有哪些文件增添、修改了还没有被同步;<br>查看当前暂存区是否还有没有未commitd的文件;|
|查看提交日志|git log<br>gitk<br>gitk c_branch<br>gitk --all|git log : 查看提交的日志<br>gitk ：查看指定分支的日志|
|上传本地仓库至Git服务器|git push|默认是上传到origin master分支<br>|
|忽略文件||在根目录建立一个.gitignore文件，把要忽略的文件直接写入.gitignore中，然后add此文件到版本库并提交|
|从服务器clone Git项目|git clone &lt;url&gt;|Download .zip :<br>单纯获得了一个工程文件，不支持pull或者push<br>git clone &lt;url &gt;:<br>git clone会先在当前文件夹建立仓库，再去复制工程，支持git pull或push。<br>如果你想往开源项目上添砖加瓦，使用git clone会好一些。<br>clone会自动关联远程的分支。|
|关联远程仓库|git remote add origin &lt;url&gt; ||
|从服务器拉取项目更新|git pull|clone是将一个库复制到你的本地，是一个本地从无到有的过程<br>pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库<br>git pull相当于是从远程获取最新版本并merge（合并）到本地<br>git pull = git fetch + git merge|
|...|||
# 2 Git 版本切换
Git每次Commit都是一个版本，可以查看各版本之间的差异，并且切换到任意不同版本。
|操作|Git 命令 <img width=300>|Note|
|----|----|----|
|查看版本号|git log --pretty=oneline  |--pretty=oneline表示只显示版本号和commit的注释<br>不要此参数会显示详情|
|项目版本回退及切换|1.git checkout &lt;commit&gt;<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;<br>3.git reset --hard &lt;commit&gt; <br>|1.git checkout &lt;commit&gt; 命令把整个git仓库文件回退到 commit 参数指定的版本<br>2.git checkout [&lt;commit&gt;] [--] &lt;filepath&gt;命令只回退 filepath 文件到 commit 参数指定的版本<br>不影响其他文件<br>**3.git reset --hard &lt;commit&gt; 命令把git的HEAD指针指向到 commit 对应的版本，<br>本地文件内容也会被回退，之后的版本会消失！ 不可逆！！！**|
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

# 4.e304-Gitlab使用示例
## 4.1 创建本地项目为Git仓库，并上传至e304-Gitlab
4.1.1 注册帐号
> *（1）输入e304-Gitlab的网址，注册帐号并等待管理员批准*  
> *（2）登陆账号，Menu -> Project -> Create new Project -> 复制Clone &lt;http url&gt;*  
> 
><img src="https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/http.png?raw=true" width = "800" height = "600" alt="远程和本地仓库示意图" align=center /> 
> *（3）在Repository中将 main branch 从 main 更换为 master*  
> 
> ![branch](https://github.com/TyZhouv/HIT-e304_Tx2_Project/blob/master/img/maintomaster.png?raw=true)


4.1.2 创建本地项目为Git仓库并上传至e304-Gitlab  

**Ubuntu Cmd Flow：**   
>$ git init  
>*#在本地项目文件夹根目录内使用 git init 初始化本地Git仓库*   
>*#会生成一个.git隐藏文件夹针对文件修改和分支管理的记录* 

```python
output： 
已初始化空的 Git 仓库于 /home/sluca_tian/aaty_workspace/e304_Git/e304 Tx2_Project/.git/    
```
>$ git add Git_Tuturial.md img/ readme.md Study/  *#将本地文件夹中的文件加入到暂存区*  


>$ git commit -m "Init my tx2 project to e304-GitServer"  *#提交到Git仓库生成一个版本*  

```python
output:
[master （根提交） 5eef553] Init my tx2 project to e304-GitServer
 30 files changed, 621 insertions(+)
 create mode 100644 Git_Tuturial.md
 create mode 100644 Study/Jeston_Hello AI World/Coding Your Own Object Detection Program.md
 create mode 100644 Study/Jeston_Hello AI World/Collecting my own Detection Datasets.md
 create mode 100644 Study/Jeston_Hello AI World/Hello AI World_CodeFLow.md
...
```
>$ git remote add origin  &lt;http url&gt   *#关联远程 的仓库*  
>$ git push --set-upstream origin master  *#提交到远程仓库的master分支上，并关联此分支*

```python
output：
Username for 'http://192.168.35.165': Tianyuan.zhou
Password for 'http://Tianyuan.zhou@192.168.35.165': 
对象计数中: 38, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (35/35), 完成.
写入对象中: 100% (38/38), 1.41 MiB | 2.28 MiB/s, 完成.
Total 38 (delta 1), reused 0 (delta 0)
remote: 
remote: To create a merge request for master, visit:
remote:   http://192.168.35.165/Tianyuan.Zhou/e304-tx2_project/-/merge_requests/new?merge_request%5Bsource_branch%5D=master
remote: 
To http://192.168.35.165/Tianyuan.Zhou/e304-tx2_project.git
 * [new branch]      master -> master
分支 'master' 设置为跟踪来自 'origin' 的远程分支 'master'。
```
## 4.2 从e304拉取服务器Git项目
>note：如果是已经clone，只是需要拉取远端的更新，用git pull即可）  

>$  git pull origin master *#远端主机默认origin，master表示分支名*

```python
output：
Username for 'http://192.168.35.165': tianyuan.zhou
Password for 'http://tianyuan.zhou@192.168.35.165': 
来自 http://192.168.35.165/Tianyuan.Zhou/e304-tx2_project
 * branch            master     -> FETCH_HEAD
已经是最新的。

```
## 4.3 在本地进行Git项目更新并提交到服务器
>同4.1 在本地修改、增减文件后add、commit加入本地Git 仓库 ，再使用 git push 上传到e304-Git服务器


## 4.4 查看本地Git仓库和远程Git仓库的差异（远程Git仓库可能由于他人的提交更新）
*查看本地仓库与远程仓库的差异*  

**Ubuntu Cmd Flow：**   
>$ git diff origin/master

*-- stat命令的功能是统计哪些文件发生了改变，有多少行产生了改动，并不会给出改动的具体内容。*
```python
output:
diff --git a/add-delbranch-file.txt b/add-delbranch-file.txt
new file mode 100644
index 0000000..e69de29
diff --git a/modifiedtxt.txt b/modifiedtxt.txt
deleted file mode 100644
index 19d6416..0000000
```

## 4.5 Git项目版本切换
Git每次Commit都是一个版本，可以查看各版本之间的差异，并且切换到任意不同版本。

*要实现的功能：*   

**Ubuntu Cmd Flow：**   

>$ ls

```python
output:
Git_Tuturial.md  img  modifiedtxt.txt  readme.md  Study
```
>$ touch modifiedtxt.txt *#在master分支下创建了一个modifiedtxt.txt*
>$ git add modifiedtxt.txt
>$ git commit -m "add a test modified txtfile"
>$ git log --pretty=oneline  *#查看所有的提交日志*
```python
output:
3f5864ce8074e3f94597fd867d23fa32f766ea17 (HEAD -> master) add a test modified txtfile
5eef553c62faa7fe26c71e551384fad2ae312090 (origin/master) Init my tx2 project to e304-GitServer
```
>git reset --hard 5eef553 *#版本回退到没有modifiedtxt.txt的版本*  

*#只需要写日志前几个hash码即可，git tag可以替代hash码，注意此命令会使之后版本消失，可以学习使用 git revert*

```python
output:
HEAD 现在位于 5eef553 Init my tx2 project to e304-GitServer
```
>$ ls

```python
output:
Git_Tuturial.md  img  readme.md  Study
#可见已经恢复到没有modifiedtxt.txt文件的版本
```
>$ git log

```python
commit 5eef553c62faa7fe26c71e551384fad2ae312090 (HEAD -> master, origin/master)
Author: tianyuan.zhou@mediatek.com <970199674@qq.com>
Date:   Fri Mar 11 15:40:23 2022 +0800

    Init my tx2 project to e304-GitServer
#可见提交此版本之后的日志被清除
```

## 4.6 Git分支管理（创建分支、分支比较、分支合并）

*要实现的功能：创建另一个分支deletettxt删除modifiedtxt.txt，切换到原分支本地文件夹中modifiedtxt.txt出现。*  

**Ubuntu Cmd Flow：**    

*创建分支*  
>$ touch modifiedtxt.txt *#在master分支下建立了一个txt文件*
>$ ls  

```python
output:
Git_Tuturial.md  img  modifiedtxt.txt  readme.md  Study
```
>$ git checkout -b deletetxt  *#创建deletetxt分支，-b切换至此分支*

```python
output:
切换到一个新分支 'deletetxt'
```
>$ rm modifiedtxt.txt  *#删除deletetxt分支下的txt文件*
>$ ls  

```python
output:
Git_Tuturial.md  img  readme.md  Study
```
>$ git status  

```python
output:
位于分支 deletetxt
尚未暂存以备提交的变更：
  （使用 "git add/rm <文件>..." 更新要提交的内容）
  （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

	删除：     modifiedtxt.txt

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
```
>git add modifiedtxt.txt  
>git commit -m "del modifiedtxt"  

*分支比较*  
>git diff master  *#deletetxt分支与master分支比较*

```python
output:
diff --git a/modifiedtxt.txt b/modifiedtxt.txt
deleted file mode 100644
index 19d6416..0000000
...
```
>$ git checkout master  *#切换到master分支*

```python
output:
切换到分支 'master'
您的分支与上游分支 'origin/master' 一致。  
```
>$ ls  

```python
output:
Git_Tuturial.md  img  modifiedtxt.txt  readme.md  Study
#可见master分支下是有这个文件的
```

*分支合并*
>$ git checkout deletetxt  *#切换到deletetxt分支*
>$ touch merge.txt  
>$ git add merge.txt  
>$ git commit -m "add merge.txt"  *#在deletetxt分支新增merge.txt文件*
>$ ls    

```python
output:
Git_Tuturial.md  img  merge.txt  readme.md  Study
```
>$ git checkout master  *#切换到master分支*
>ls

```python
output:  
 Git_Tuturial.md  img  readme.md  Study 
#可见master分支下是没有merge.txt文件的
```
>$ git merge deletetxt *#将deletetxt分支与master分支 merge*

```python
output:
更新 ab14d24..0a0e340
Fast-forward
 merge.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 merge.txt

```
>$ ls 

```python
output:
Git_Tuturial.md  img  merge.txt  readme.md  Study
#master分支下有了delectetxt分支下编辑的merge.txt文件
```
# 5 Git命令（较全）思维导图
![Git命令（较全）思维导图](https://img-blog.csdn.net/20171111113313194?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHV3aF8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)   
	
	
	
