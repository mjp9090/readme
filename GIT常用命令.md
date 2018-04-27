<H1> aaa </H1>
GIT常用命令
==========
名词解释
-------

- 工作区（Working Directory）：就是你在电脑里能看到的目录

- 版本库（Repository）：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库

- 暂存区（Stage）：Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区

----------

### 配置

- 查看配置文件:```git config --list```								
- 查看全局配置文件: ```git config --list --global```					
- 配置姓名: ```git config --global user.name "Your Name"```						
- 配置邮箱:```git config --global user.email "email@example.com"```	
- 配置命令简称:```git config --global alias.st status```						
- 把这个目录初始化为仓库:```git init```											

###### .gitignore文件作用：要忽略的文件名填进去，Git在提交时就会自动忽略这些文件。

----------

### 提交文件
- 向暂存区中添加文件:
												
		提交单个文件： git add build.gradle
		提交目录：git add app											
		提交所有文件:git add .
								
- 将暂存区文件提交版本库： ```git commit -m "message"```
- 参数-m后面输入的是本次提交的说明，可以输入任意内容

- message的命名规则:type(scope):subject
				
		常用类型:type(1. 新功能:feat; 2. 修复BUG:fix; 3. 格式:style; 4. 代码重构:refactor; 5. 项目构建:chore)
		模块:scope 
		描述信息：subject

git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。

~~使用CZ需要先安装npm(此处未测试成功)~~

~~git clone --recursive git://github.com/isaacs/npm.git~~

~~npm install -g commitizen~~

~~commitizen init cz-conventional-changelog--save-exact~~

~~npm init~~

----------

### 分支管理

#### 本地分支（指向提交对象的一个可变指针）
- 创建分支:```git branch dev```										
- 查看当前分支:```git branch```											
- 切换到master分支:```git checkout master```									
- 命令加上-b参数表示创建并切换，```git checkout -b dev```
 - 相当于以下两条命令:	```git branch dev；git checkout dev```
- 把dev分支合并到master分支上:```git merge dev```	合并时遇到冲突(CONFLICT)，手工解决冲突后在进行merge 	
- 删除dev分支:```git branch -d dev```									

#### 远程分支（指向远程仓库中文件的指针，实际开发中每一个本地分支都应该存在一个与远程分支的对应关系）
- 删除本地的远程分支:```git branch -r -D origin/BranchName	```				
- 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并:```git merge --no-ff -m "merge with no-ff" dev```而fast forward合并就看不出来曾经做过合并	
- 用带参数的git log也可以看到分支的合并情况:```git log --graph --pretty=oneline --abbrev-commit```	

----------

### 远程库
- 创建SSH Key:```ssh-keygen -t rsa -C "youremail@example.com"```						
- 本地库和远程库关联:```git remote add origin git@github.com:mjp9090/readme.git```				
- 从远程库将代码下载到本地:```git clone git@github.com:mjp9090/readme.git```还可以用git clone https://github.com/michaelliao/gitskills.git这样的地址
- 从远程库克隆特定分支:```git clone -b dev git@github.com:mjp9090/readme.git```					
- 将远程库修改的代码同步到本地:```git fetch origin master```												
- 查看远程库修改的内容:```git diff origin/master```											    
- 从远程库获取最新代码并且合并到本地，相当于合并执行fetch merge两个命令:```git pull origin master```												
- 第一次推送master分支:```git push -u origin master```由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
- 提交远程库:```git push origin master```														
- 查看远程库的信息:```git remote```															
- 查看远程库的详细信息:```git remote -v```														
- 删除远程git服务器上的分支:```git push origin -d BranchName```										

----------

### 隐藏工作现场
- 把当前工作现场“储藏”起来:```git stash```											
- 查看储藏的工作现场:```git stash list```										
- 恢复后，stash内容并不删除:```git stash apply```										
- 恢复的同时把stash内容也删了:```git stash pop```										
- 可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash:```git stash apply stash@{0}```						
- 分支还没有被合并,强行删除:```git branch -D feature-vulcan```	

----------

### 标签
- 创建带有说明的标签，用-a指定标签名，-m指定说明文字:```git tag -a v0.1 -m "version 0.1 released" //3628164```	
- 推送全部尚未推送到远程的本地标签:```git push origin --tags```								
- 查看所有标签:```git tag```												
- 查看特定标签:```git tag -l 标签名```										
- 找到历史提交的commit id：```git log --pretty=oneline --abbrev-commit	```		
- 对特定的commit id补打标签：```git tag -a v0.9 6224937 -m "version 0.9 released"```	
- 查看标签信息:```git show v0.9```										
- 如果标签打错了，也可以删除:```git tag -d v0.1	```									
- 推送某个标签到远程:```git push origin v1.0```								
- 如果标签已经推送到远程，先从本地删除，然后，从远程删除:```git push origin :refs/tags/v0.9```						

----------

### 还原
- 还原，HEAD表示当前版本：```git reset --hard HEAD```									
- 根据commit id还原最新版本：```git reset --hard 3628164```							
- 把暂存区的文件修改撤销掉（unstage），重新放回工作区:```git reset HEAD readme.txt```							
- 把暂存区的所有文件修改撤销掉（unstage），重新放回工作区:```git reset HEAD``` 								 
- 用版本库里的版本替换工作区的版本:```git checkout -- readme.txt```（命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令）	

----------

### 删除
- 从版本库中删除该文件:```git rm test.txt```										

----------

### 查看
- 查看隐藏文件:```ls -ah``` 												
- 查看当前状态:```git status```											
- 查看没有添加至暂存区的修改:```git diff```											
- 查看添加至暂存区的修改:```dit diff --staged```									
- 查看工作区和版本库里面最新版本的区别:```git diff HEAD -- readme.txt```							
- 查看本仓库的提交日志(commit右侧的是指向这个提交的哈希值):```git log```											
- 只显示提交信息的第一行:```git log --pretty=oneline | grep 文件名```				
- 记录每一次命令:```git reflog```											
- 显示指定目录、文件的日志:```git log build.gradle```								
- 显示文件的改动，可查看文件的提交日志和提交前后的差别:```git log -p build.gradle```								

----------

### 显示		
- 让Git显示颜色，会让命令输出看起来更醒目:```git config --global color.ui true```		