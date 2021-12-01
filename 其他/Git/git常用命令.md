1、自报家门：你的名字和Email地址：
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
2、创建Git仓库：git init
3、把文件添加到仓库：git add file1.txt file2.txt
4、把文件提交到仓库：git commit -m "备注"
5、掌握仓库当前的状态:git status
6、查看difference，显示的格式正是Unix通用的diff格式： git diff readme.txt 
7、显示从最近到最远的提交日志：git log（简化```$ git log --pretty=oneline```）
8、回退版本
```
$ git reset --hard HEAD^（上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100）
$ git reset --hard 1094a（版本号没必要写全，前几位就可以了）
```
9、记录你的每一次命令：git reflog
10、丢弃工作区的修改：git checkout -- file
11、添加到了暂存区时，想丢弃修改
```
$  git reset HEAD <file>
$ git checkout -- file
或
$ git reset --hard 1094a（版本号没必要写全，前几位就可以了）
```
12、从版本库中删除该文件
```
$ git rm test.txt
$ git commit -m "remove test.txt"
```
13、关联Github远程仓库（注意：配置SSH Key公钥）
```
$ git remote add origin git@github.com:michaelliao/learngit.git
```
14、第一次推送master分支的所有内容：git push -u origin master
15、推送最新修改：git push origin master
16、从远程库克隆一个本地库：git clone git@github.com:michaelliao/gitskills.git
17、查看分支：git branch
18、创建分支：git branch <name>
19、切换分支：git checkout <name>
20、创建+切换分支：git checkout -b <name>
21、合并某分支到当前分支（默认为Fast forward模式，丢掉分支信息）：git merge <name>
22、合并某分支到当前分支（禁用Fast forward）：git merge --no-ff -m "merge with no-ff" <name>
23、删除分支：git branch -d <name>
24、查看分支合并图：git log --graph（简化$ git log --graph --pretty=oneline --abbrev-commit）
25、储藏工作空间：git stash
26、查看储藏空间内容：git stash list
27、恢复储藏空间：git stash apply
28、恢复指定储藏空间：git stash apply stash@{0}
29、删除储藏空间：git stash drop
30恢复+删除储藏空间：git stash pop
31、强制删除没有被合并的某一分支：git branch -D <name>
32、向远程仓库推送：git push origin <branch-name>
33、从远程仓库拉取：git pull
34、在本地创建和远程分支对应的分支：git checkout -b branch-name origin/branch-name
35、创建本地分支和远程分支的链接关系：git branch --set-upstream-to <branch-name> origin/<branch-name>
36、查看远程库信息：git remote -v
37、把分叉的提交历史“整理”成一条直线：git rebase

