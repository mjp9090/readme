��������Working Directory��
�������ڵ������ܿ�����Ŀ¼

�汾�⣨Repository��
��������һ������Ŀ¼.git��������㹤����������Git�İ汾��

Git�İ汾������˺ܶණ������������Ҫ�ľ��ǳ�Ϊstage�����߽�index�����ݴ���
git add����ʵ���Ͼ��ǰ�Ҫ�ύ�������޸ķŵ��ݴ�����Stage����Ȼ��ִ��git commit�Ϳ���һ���԰��ݴ����������޸��ύ����֧��


����
git config --list									�����ļ�
git config --list --global							�鿴ȫ�������ļ�
git config --global user.name "Your Name"			��������			
git config --global user.email "email@example.com"	��������
git config --global alias.st status					����������		
git init											�����Ŀ¼��ʼ��Ϊ�ֿ�
.gitignore											Ҫ���Ե��ļ������ȥ��Git���ύʱ�ͻ��Զ�������Щ�ļ���

�ύ�ļ�
git add												�򻺴���������ļ�
	git add build.gradle								�ύ�ļ�
	git add app											�ύĿ¼
	git add .											�ύ�����ļ�
	
�ύ�ļ�	
git commit -m "message"						����-m����������Ǳ����ύ��˵��������������������

message����������type(scope):subject
type�������ͣ�
feat��		�¹���
fix��		�޸�BUG
style:		��ʽ
refactor:	�����ع�
chore:		��Ŀ����

scope��		ģ��

subject��	������Ϣ

ʹ��CZ��Ҫ�Ȱ�װnpm
git clone --recursive git://github.com/isaacs/npm.git


npm install -g commitizen

commitizen init cz-conventional-changelog--save-exact

npm init


��֧����
���ط�֧��ָ���ύ�����һ���ɱ�ָ�룩
git branch dev										������֧
git branch											�鿴��ǰ��֧
git checkout master									�л���master��֧
git checkout -b dev									�������-b������ʾ�������л����൱��������������git branch dev��git checkout dev
git merge dev										��dev��֧�ϲ���master��֧��
�ϲ�ʱ������ͻ(CONFLICT)���ֹ������ͻ���ڽ���merge
git branch -d dev									ɾ��dev��֧

Զ�̷�֧��ָ��Զ�ֿ̲����ļ���ָ�룬ʵ�ʿ�����ÿһ�����ط�֧��Ӧ�ô���һ����Զ�̷�֧�Ķ�Ӧ��ϵ��
git branch -r -D origin/BranchName					ɾ�����ص�Զ�̷�֧



 

git log --graph --pretty=oneline --abbrev-commit	�ô�������git logҲ���Կ�����֧�ĺϲ����
git merge --no-ff -m "merge with no-ff" dev			�ϲ���֮����fast forward.�ϲ���֧ʱ������--no-ff�����Ϳ�������ͨģʽ�ϲ����ϲ������ʷ�з�֧���ܿ��������������ϲ�����fast forward�ϲ��Ϳ����������������ϲ�

Զ�̿�
ssh-keygen -t rsa -C "youremail@example.com"						����SSH Key
git remote add origin git@github.com:mjp9090/readme.git				���ؿ��Զ�̿����
git clone git@github.com:mjp9090/readme.git							��Զ�̿⽫�������ص����ء���������git clone https://github.com/michaelliao/gitskills.git�����ĵ�ַ
git clone -b dev git@github.com:mjp9090/readme.git					��Զ�̿��¡�ض���֧
git fetch origin master												��Զ�̿��޸ĵĴ���ͬ�������ء�
git diff origin/master											    �鿴Զ�̿��޸ĵ�����
git merge origin/master												��origin/master��֧�ϲ�������֧
git pull origin master												��Զ�̿��ȡ���´��벢�Һϲ������أ��൱�ںϲ�ִ��fetch merge��������
git push -u origin master											����Զ�̿��ǿյģ����ǵ�һ������master��֧ʱ��������-u������Git������ѱ��ص�master��֧�������͵�Զ���µ�master��֧������ѱ��ص�master��֧��Զ�̵�master��֧�������������Ժ�����ͻ�����ȡʱ�Ϳ��Լ����
git push origin master												�ύԶ�̿�		
git remote															�鿴Զ�̿����Ϣ
git remote -v														�鿴Զ�̿����ϸ��Ϣ
git push origin -d BranchName										ɾ��Զ��git�������ϵķ�֧

���ع����ֳ�
git stash											�ѵ�ǰ�����ֳ������ء�����
git stash list										�鿴���صĹ����ֳ�
git stash apply										�ָ���stash���ݲ���ɾ��
git stash pop										�ָ���ͬʱ��stash����Ҳɾ��
git stash apply stash@{0}							���Զ��stash���ָ���ʱ������git stash list�鿴��Ȼ��ָ�ָ����stash
git branch -D feature-vulcan						Git�������ѣ�feature-vulcan��֧��û�б��ϲ������ɾ��������ʧ���޸ģ����Ҫǿ��ɾ������Ҫʹ������git branch -D feature-vulcan

��ǩ
git tag -a v0.1 -m "version 0.1 released" //3628164	��������˵���ı�ǩ����-aָ����ǩ����-mָ��˵������
git push origin --tags								һ��������ȫ����δ���͵�Զ�̵ı��ر�ǩ
git tag												�鿴���б�ǩ
git tag -l ��ǩ										�鿴�ض���ǩ
git log --pretty=oneline --abbrev-commit			�ҵ���ʷ�ύ��commit id
git tag -a v0.9 6224937 -m "version 0.9 released"	Ҫ��add merge����ύ���ǩ������Ӧ��commit id��6224937
git show v0.9										�鿴��ǩ��Ϣ
git tag -s v0.2 -m "signed version 0.2 released" fec145a		ǩ������PGPǩ������ˣ��������Ȱ�װgpg��GnuPG�������û���ҵ�gpg������û��gpg��Կ�ԣ��ͻᱨ�����������ο�GnuPG�����ĵ�����Key
git tag -d v0.1										�����ǩ����ˣ�Ҳ����ɾ��
git push origin v1.0								����ĳ����ǩ��Զ��
git push origin :refs/tags/v0.9						�����ǩ�Ѿ����͵�Զ�̣��ȴӱ���ɾ����Ȼ�󣬴�Զ��ɾ��

��ԭ
git reset --hard HEAD								��Git�У���HEAD��ʾ��ǰ�汾
	HEAD^												��һ���汾
	HEAD^^												�������汾
	HEAD~100											��100���汾
git reset --hard 3628164							����commit id�һ����°汾
git reset HEAD readme.txt							���ݴ������ļ��޸ĳ�������unstage�������·Żع�����
git reset HEAD 										���ݴ����������ļ��޸ĳ�������unstage�������·Żع�����

ɾ��d
git rm test.txt										�Ӱ汾����ɾ�����ļ�

git checkout -- readme.txt							�ð汾����İ汾�滻�������İ汾�������е�--����Ҫ��û��--���ͱ���ˡ��л�����һ����֧�������

�鿴
ls -ah 												�鿴�����ļ�
git status											�鿴��ǰ״̬
git diff											�鿴û��������ݴ������޸�
dit diff --staged									�鿴������ݴ������޸�
git diff HEAD -- readme.txt							�鿴�������Ͱ汾���������°汾������
git log												�鿴���ֿ���ύ��־(commit�Ҳ����ָ������ύ�Ĺ�ϣֵ)
git log --pretty=oneline | grep �ļ���				ֻ��ʾ�ύ��Ϣ�ĵ�һ��
git reflog											��¼ÿһ������
git log build.gradle								��ʾָ��Ŀ¼���ļ�����־
git log -p build.gradle								��ʾ�ļ��ĸĶ����ɲ鿴�ļ����ύ��־���ύǰ��Ĳ��


��ʾ		
git config --global color.ui true					��Git��ʾ��ɫ�����������������������Ŀ

