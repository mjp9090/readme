工作区（Working Directory）
就是你在电脑里能看到的目录

版本库（Repository）
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区
git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。


配置
git config --list									配置文件
git config --list --global							查看全局配置文件
git config --global user.name "Your Name"			配置姓名			
git config --global user.email "email@example.com"	配置邮箱
git config --global alias.st status					配置命令简称		
git init											把这个目录初始化为仓库
.gitignore											要忽略的文件名填进去，Git在提交时就会自动忽略这些文件。

提交文件
git add												向缓存区中添加文件
	git add build.gradle								提交文件
	git add app											提交目录
	git add .											提交所有文件
	
提交文件	
git commit -m "message"						参数-m后面输入的是本次提交的说明，可以输入任意内容

message的命名规则type(scope):subject
type常用类型：
feat：		新功能
fix：		修复BUG
style:		格式
refactor:	代码重构
chore:		项目构建

scope：		模块

subject：	描述信息

使用CZ需要先安装npm
git clone --recursive git://github.com/isaacs/npm.git


npm install -g commitizen

commitizen init cz-conventional-changelog--save-exact

npm init


分支管理
本地分支（指向提交对象的一个可变指针）
git branch dev										创建分支
git branch											查看当前分支
git checkout master									切换到master分支
git checkout -b dev									命令加上-b参数表示创建并切换，相当于以下两条命令git branch dev；git checkout dev
git merge dev										把dev分支合并到master分支上
合并时遇到冲突(CONFLICT)，手工解决冲突后在进行merge
git branch -d dev									删除dev分支

远程分支（指向远程仓库中文件的指针，实际开发中每一个本地分支都应该存在一个与远程分支的对应关系）
git branch -r -D origin/BranchName					删除本地的远程分支



 

git log --graph --pretty=oneline --abbrev-commit	用带参数的git log也可以看到分支的合并情况
git merge --no-ff -m "merge with no-ff" dev			合并分之禁用fast forward.合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并

远程库
ssh-keygen -t rsa -C "youremail@example.com"						创建SSH Key
git remote add origin git@github.com:mjp9090/readme.git				本地库和远程库关联
git clone git@github.com:mjp9090/readme.git							从远程库将代码下载到本地。还可以用git clone https://github.com/michaelliao/gitskills.git这样的地址
git clone -b dev git@github.com:mjp9090/readme.git					从远程库克隆特定分支
git fetch origin master												将远程库修改的代码同步到本地。
git diff origin/master											    查看远程库修改的内容
git merge origin/master												把origin/master分支合并到主分支
git pull origin master												从远程库获取最新代码并且合并到本地，相当于合并执行fetch merge两个命令
git push -u origin master											由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
git push origin master												提交远程库		
git remote															查看远程库的信息
git remote -v														查看远程库的详细信息
git push origin -d BranchName										删除远程git服务器上的分支

隐藏工作现场
git stash											把当前工作现场“储藏”起来
git stash list										查看储藏的工作现场
git stash apply										恢复后，stash内容并不删除
git stash pop										恢复的同时把stash内容也删了
git stash apply stash@{0}							可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash
git branch -D feature-vulcan						Git友情提醒，feature-vulcan分支还没有被合并，如果删除，将丢失掉修改，如果要强行删除，需要使用命令git branch -D feature-vulcan

标签
git tag -a v0.1 -m "version 0.1 released" //3628164	创建带有说明的标签，用-a指定标签名，-m指定说明文字
git push origin --tags								一次性推送全部尚未推送到远程的本地标签
git tag												查看所有标签
git tag -l 标签										查看特定标签
git log --pretty=oneline --abbrev-commit			找到历史提交的commit id
git tag -a v0.9 6224937 -m "version 0.9 released"	要对add merge这次提交打标签，它对应的commit id是6224937
git show v0.9										查看标签信息
git tag -s v0.2 -m "signed version 0.2 released" fec145a		签名采用PGP签名，因此，必须首先安装gpg（GnuPG），如果没有找到gpg，或者没有gpg密钥对，就会报错，如果报错，请参考GnuPG帮助文档配置Key
git tag -d v0.1										如果标签打错了，也可以删除
git push origin v1.0								推送某个标签到远程
git push origin :refs/tags/v0.9						如果标签已经推送到远程，先从本地删除，然后，从远程删除

还原
git reset --hard HEAD								在Git中，用HEAD表示当前版本
	HEAD^												上一个版本
	HEAD^^												上两个版本
	HEAD~100											上100个版本
git reset --hard 3628164							根据commit id找回最新版本
git reset HEAD readme.txt							把暂存区的文件修改撤销掉（unstage），重新放回工作区
git reset HEAD 										把暂存区的所有文件修改撤销掉（unstage），重新放回工作区

删除d
git rm test.txt										从版本库中删除该文件

git checkout -- readme.txt							用版本库里的版本替换工作区的版本（命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令）

查看
ls -ah 												查看隐藏文件
git status											查看当前状态
git diff											查看没有添加至暂存区的修改
dit diff --staged									查看添加至暂存区的修改
git diff HEAD -- readme.txt							查看工作区和版本库里面最新版本的区别
git log												查看本仓库的提交日志(commit右侧的是指向这个提交的哈希值)
git log --pretty=oneline | grep 文件名				只显示提交信息的第一行
git reflog											记录每一次命令
git log build.gradle								显示指定目录、文件的日志
git log -p build.gradle								显示文件的改动，可查看文件的提交日志和提交前后的差别


显示		
git config --global color.ui true					让Git显示颜色，会让命令输出看起来更醒目

