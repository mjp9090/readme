git config --global user.name "Your Name"			��������			
git config --global user.email "email@example.com"	��������		
git init											�����Ŀ¼��ʼ��Ϊ�ֿ�
ls -ah 												�鿴�����ļ�
git status											�鿴��ǰ״̬
git add												�򻺴���������ļ�
	git add build.gradle				�ύ�ļ�
	git add app							�ύĿ¼
	git add .							�ύ�����ļ�
git commit -m "First commit"			����-m����������Ǳ����ύ��˵��������������������
git diff								�鿴����ǰ��Ĳ��
git diff HEAD -- readme.txt				�鿴�������Ͱ汾���������°汾������
git log									�鿴���ֿ���ύ��־(commit�Ҳ����ָ������ύ�Ĺ�ϣֵ)
git log --pretty=short					ֻ��ʾ�ύ��Ϣ�ĵ�һ��
git reset --hard HEAD					��Git�У���HEAD��ʾ��ǰ�汾
	HEAD^								��һ���汾
	HEAD^^								�������汾
	HEAD~100							��100���汾
git reset --hard 3628164				����commit id�һ����°汾
git reflog								��¼ÿһ������
git checkout -- readme.txt				�����ڹ��������޸ģ������е�--����Ҫ��û��--���ͱ���ˡ��л�����һ����֧�������
git reset HEAD readme.txt				���ݴ������ļ��޸ĳ�������unstage�������·Żع�����
git reset HEAD 							���ݴ����������ļ��޸ĳ�������unstage�������·Żع�����
git rm test.txt							�Ӱ汾����ɾ�����ļ�
git commit -m "remove test.txt"				�ύɾ��
git checkout -- test.txt				�ð汾����İ汾�滻�������İ汾�����۹��������޸Ļ���ɾ���������ԡ�һ����ԭ����
git log build.gradle					��ʾָ��Ŀ¼���ļ�����־
$git log -p build.gradle				��ʾ�ļ��ĸĶ����ɲ鿴�ļ����ύ��־���ύǰ��Ĳ��
		
ssh-keygen -t rsa -C "youremail@example.com"		����SSH Key
git remote add origin git@github.com:mjp9090/BroadcastTest.git		���ؿ��Զ�̿����
git push -u origin master				�ѱ��ؿ�������������͵�Զ�̿���
git push origin master					�ύԶ�̿�
git clone git@github.com:mjp9090/BroadcastTest.git	��¡һ�����ؿ⡣��������git clone https://github.com/michaelliao/gitskills.git�����ĵ�ַ
git fetch origin branch					��Զ�̿������ļ�
		
git checkout -b dev					�������-b������ʾ�������л����൱��������������git branch dev��git checkout dev
git branch dev						������֧
git branch						�鿴��ǰ��֧
git checkout master					�л���master��֧
git merge dev						��dev��֧�Ĺ����ɹ��ϲ���master��֧��
git branch -d dev					ɾ��dev��֧
git branch -r -D origin/BranchName			ɾ�����ص�Զ�̷�֧
git push origin -d BranchName				Զ��ɾ��git�������ϵķ�֧
git log --graph --pretty=oneline --abbrev-commit	�ô�������git logҲ���Կ�����֧�ĺϲ����
git merge --no-ff -m "merge with no-ff" dev		�ϲ���֮����fast forward.�ϲ���֧ʱ������--no-ff�����Ϳ�������ͨģʽ�ϲ����ϲ������ʷ�з�֧���ܿ��������������ϲ�����fast forward�ϲ��Ϳ����������������ϲ�
		
git stash						�ѵ�ǰ�����ֳ������ء�����
git stash list						�鿴���صĹ����ֳ�
git stash apply						�ָ���stash���ݲ���ɾ��
git stash pop						�ָ���ͬʱ��stash����Ҳɾ��
git stash apply stash@{0}				���Զ��stash���ָ���ʱ������git stash list�鿴��Ȼ��ָ�ָ����stash
git branch -D feature-vulcan				Git�������ѣ�feature-vulcan��֧��û�б��ϲ������ɾ��������ʧ���޸ģ����Ҫǿ��ɾ������Ҫʹ������git branch -D feature-vulcan
git remote						�鿴Զ�̿����Ϣ
git remote -v						�鿴Զ�̿����ϸ��Ϣ
		
git tag v1.0						������ǩ
git tag							�鿴���б�ǩ
git log --pretty=oneline --abbrev-commit		�ҵ���ʷ�ύ��commit id
git tag v0.9 6224937					Ҫ��add merge����ύ���ǩ������Ӧ��commit id��6224937
git show v0.9						�鿴��ǩ��Ϣ
git tag -a v0.1 -m "version 0.1 released" 3628164			��������˵���ı�ǩ����-aָ����ǩ����-mָ��˵������
git tag -s v0.2 -m "signed version 0.2 released" fec145a		ǩ������PGPǩ������ˣ��������Ȱ�װgpg��GnuPG�������û���ҵ�gpg������û��gpg��Կ�ԣ��ͻᱨ�����������ο�GnuPG�����ĵ�����Key
git tag -d v0.1						�����ǩ����ˣ�Ҳ����ɾ��
git push origin v1.0					����ĳ����ǩ��Զ��
git push origin --tags					һ��������ȫ����δ���͵�Զ�̵ı��ر�ǩ
git push origin :refs/tags/v0.9				�����ǩ�Ѿ����͵�Զ�̣��ȴӱ���ɾ����Ȼ�󣬴�Զ��ɾ��
		
git config --global color.ui true			��Git��ʾ��ɫ�����������������������Ŀ
.gitignore						Ҫ���Ե��ļ������ȥ��Git�ͻ��Զ�������Щ�ļ���
