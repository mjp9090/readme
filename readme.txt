git config --global user.name "Your Name"			配置姓名			
git config --global user.email "email@example.com"	配置邮箱		
git init											把这个目录初始化为仓库
ls -ah 												查看隐藏文件
git status											查看当前状态
git add												向缓存区中添加文件
	git add build.gradle				提交文件
	git add app							提交目录
	git add .							提交所有文件
git commit -m "First commit"			参数-m后面输入的是本次提交的说明，可以输入任意内容
git diff								查看更改前后的差别
git diff HEAD -- readme.txt				查看工作区和版本库里面最新版本的区别
git log									查看本仓库的提交日志(commit右侧的是指向这个提交的哈希值)
git log --pretty=short					只显示提交信息的第一行
git reset --hard HEAD					在Git中，用HEAD表示当前版本
	HEAD^								上一个版本
	HEAD^^								上两个版本
	HEAD~100							上100个版本
git reset --hard 3628164				根据commit id找回最新版本
git reflog								记录每一次命令
git checkout -- readme.txt				丢弃在工作区的修改（命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令）
git reset HEAD readme.txt				把暂存区的文件修改撤销掉（unstage），重新放回工作区
git reset HEAD 							把暂存区的所有文件修改撤销掉（unstage），重新放回工作区
git rm test.txt							从版本库中删除该文件
git commit -m "remove test.txt"				提交删除
git checkout -- test.txt				用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
git log build.gradle					显示指定目录、文件的日志
$git log -p build.gradle				显示文件的改动，可查看文件的提交日志和提交前后的差别
		
ssh-keygen -t rsa -C "youremail@example.com"		创建SSH Key
git remote add origin git@github.com:mjp9090/BroadcastTest.git		本地库和远程库关联
git push -u origin master				把本地库的所有内容推送到远程库上
git push origin master					提交远程库
git clone git@github.com:mjp9090/BroadcastTest.git	克隆一个本地库。还可以用git clone https://github.com/michaelliao/gitskills.git这样的地址
git fetch origin branch					从远程库下载文件
		
git checkout -b dev					命令加上-b参数表示创建并切换，相当于以下两条命令git branch dev；git checkout dev
git branch dev						创建分支
git branch						查看当前分支
git checkout master					切换回master分支
git merge dev						把dev分支的工作成果合并到master分支上
git branch -d dev					删除dev分支
git branch -r -D origin/BranchName			删除本地的远程分支
git push origin -d BranchName				远程删除git服务器上的分支
git log --graph --pretty=oneline --abbrev-commit	用带参数的git log也可以看到分支的合并情况
git merge --no-ff -m "merge with no-ff" dev		合并分之禁用fast forward.合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并
		
git stash						把当前工作现场“储藏”起来
git stash list						查看储藏的工作现场
git stash apply						恢复后，stash内容并不删除
git stash pop						恢复的同时把stash内容也删了
git stash apply stash@{0}				可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash
git branch -D feature-vulcan				Git友情提醒，feature-vulcan分支还没有被合并，如果删除，将丢失掉修改，如果要强行删除，需要使用命令git branch -D feature-vulcan
git remote						查看远程库的信息
git remote -v						查看远程库的详细信息
		
git tag v1.0						创建标签
git tag							查看所有标签
git log --pretty=oneline --abbrev-commit		找到历史提交的commit id
git tag v0.9 6224937					要对add merge这次提交打标签，它对应的commit id是6224937
git show v0.9						查看标签信息
git tag -a v0.1 -m "version 0.1 released" 3628164			创建带有说明的标签，用-a指定标签名，-m指定说明文字
git tag -s v0.2 -m "signed version 0.2 released" fec145a		签名采用PGP签名，因此，必须首先安装gpg（GnuPG），如果没有找到gpg，或者没有gpg密钥对，就会报错，如果报错，请参考GnuPG帮助文档配置Key
git tag -d v0.1						如果标签打错了，也可以删除
git push origin v1.0					推送某个标签到远程
git push origin --tags					一次性推送全部尚未推送到远程的本地标签
git push origin :refs/tags/v0.9				如果标签已经推送到远程，先从本地删除，然后，从远程删除
		
git config --global color.ui true			让Git显示颜色，会让命令输出看起来更醒目
.gitignore						要忽略的文件名填进去，Git就会自动忽略这些文件。
