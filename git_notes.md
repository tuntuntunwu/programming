# Git Note


## git基本操作

<https://www.runoob.com/manual/git-guide/>
<https://www.runoob.com/git/git-workspace-index-repo.html>

git clone git@github.com:Owner/Repositoryname.git：  
git支持多种协议，默认git@使用ssh，也可使用https等。使用https速度会慢且每次push都需输入口令，但对某些只开放了http端口的机子，只能使用https。  
git clone \<source repository> \<destination repository>：  
复制本地仓库。\<source repository>：想克隆的本地仓库路径，\<destination repository>：想克隆去另一个地方的路径。例如git clone d:/git e:/git11 是将d:/git的仓库（即包含隐藏文件.git的目录）克隆到 e:/git11 目录下。  
注意：1、\<destination repository>目录必须没有在文件系统上创建，或创建了但里面为空，不然会克隆不成功。2、与从远程拉取仓库不同，路径的最后不用写.git来表明这是一个仓库。

git版本表示：  
HEAD指向最近一次提交的版本，HEAD^则指向HEAD的上一提交版本，HEAD^^（也可以写作HEAD^2）则表示上上个提交版本，依次类推，更简洁的表示方式为HEAD^n或HEAD~n。更为通用的版本表示形式是它们的ID，每个提交版本都有唯一的40位SHA1值对应，使用它们表示版本时只需写出能唯一确定一个版本的前几位SHA1值即可。

git diff：  
git diff：查看工作区与暂存区的不同。  
git diff –cached [\<commit>]：查看暂存区与指定提交版本的不同，版本可缺省（为HEAD）。  
git diff \<commit>：查看工作区与指定提交版本的不同。  
git diff \<commit>..\<commit>：查看2个指定提交版本的不同，其中任一可缺省（为HEAD）。  
git diff \<commit>...\<commit>：查看2个不同分支指定提交版本的不同，其中任一可缺省（为HEAD），该命令相当于git diff $(git-merge-base A B) B。

git checkout -- \<file>：  
与git reset不同，reset是替换整个目录树，多余的文件将被删除。而checkout只是替换指定的文件，对多余的文件保留不做任何处理。

git reflog：  
这个命令可以查看所有的已提交版本ID而不管是否已经reset过（reset的版本 之后的已提交版本ID都不再显示在git log中）。使用这个命令来获取版本ID对重置版本的git reset命令很有帮助。

git rm \<file>：  
把文件从工作区和暂存区中删除。使用—cached只会从暂存区中删除。使用–rf \<directory>删除指定目录下的所有文件和子目录。

git mv \<source> \<destination>：  
在工作区和暂存区中进行移动或重命名。若\<destination>不为一个目录名，则执行重命名。如果为一个目录名，则执行移动。

git checkout -b \<branchname>：  
创建新分支并立即切换到该分支下。  
git checkout \<branchname>：  
分支切换的过程是：1、对工作区和暂存区未提交的修改（自然包括其文件）不做处理统统保留，依然维持其未提交状态。2、HEAD指向当前切换到的分支的最后一次提交版本，并且根据这个版本对工作区和暂存区中那些未进行修改的文件进行替换、删除。

git merge \<branchname>：  
如果分支能合并，则直接合并，出现以下2种情况则不能直接合并，需手动修改再合并：（假设被合并的分支为feature，要合并进的分支为master）1、master中未提交的修改与feature中的并入版本有冲突。2、master中先版本与feature中的并入版本有冲突。

git rebase:  
此命令可以一键将本地未push的分叉提交历史整理成直线。  
<https://www.jianshu.com/p/4a8f4af4e803>  
<https://git-scm.com/docs/git-rebase#_description>

git销毁仓库：  
直接删除目录下.git目录即可。


## git远程操作

git remote add origin git@github.com:Owner/Repositoryname.git  
git remote –v:  
设置此仓库所要链接到的远程仓库。origin指代了 具有以上URL的远程仓库对象。

git branch --set-upstream-to=origin/\<branchname> \<branchname>：  
建立本地分支与远程仓库分支的关联（一般用相同名字），push、fetch、pull操作中有用。

git push –u origin \<branchname>：  
push一次只推送一个本地分支\<branchname>，推送到远程仓库的同名分支，缺省时为master。-u表示建立这一本地分支与同名的远程仓库分支的关联。

git fetch origin \<branchname>：  
当参数全部缺省时，如果此分支设置了与一个远程仓库分支的关联，则拉取那个远程仓库分支的内容，如果不存在关联，则拉取整个origin（所有的远程仓库分支，用origin/\<branchname>表示）。当参数只有origin时，拉取整个origin。参数齐全时拉取远程仓库的\<branchname>。fetch只是拉取内容，要使用拉取的内容，需进行分支合并，git merge origin/\<branchname>。

git pull origin \<branchname>：  
和fetch用法一样，不过pull是直接执行了fetch+merge。

git remote rm origin：  
取消此仓库与远程仓库的链接
