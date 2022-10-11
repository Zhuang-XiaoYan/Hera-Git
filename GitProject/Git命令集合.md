# Git命令集合

Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。
Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。
Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# git-config

```bash
1. 配置命令:
git config --global user.name "xxx"
git config --global user.email xxxxxxxxxx@163.com
git config --global http.postBuffer 2M # 最大上传文件的大小
git config --global color.ui true

2. 查看配置:
git config --list
cat ~/.gitconfig # 查看配置文件

3. 直接修改配置文件
vim ~/.gitconfig
[user]
        email = 19805159366@163.com
        name = SEUZTh
[https]
[http]
        postBuffer = 2M
4. 删除配置
git config unset --global user.name
```

# git-init
```bash
1. 初始化
git init
git init newrepo
2. 查看生成的.git目录
cd .git
ls
```

# git-commit
```bash
1. 显示工作目录和暂存区的状态
git status

2. 提交目录下所有文件
git add .

3. 提交指定文件
git add xxx.格式

4. 添加说明
git commit -m '说明'

5. 查看历史提交
git log
```

# git-diff
```bash
1. 查看修改前后的区别
git-diff

2. 添加到暂存区
git add .

3. 查看状态
git status

4. 查看暂存区和Reportory的区别
git diff --staged

5. 将暂存区的内容提交
git commit -m '说明'

6. 查看提交历史
git log
```
# git-rename
```shell
1. 查看状态
git status

2. 告诉git,删除了某文件
git rm xxx.格式

3. 添加重命名后的文件
git add xxx.格式

4. 查看状态
git status

5. 提交
git commit -m '把xxx重命名为xxx'
```

# git-mv
```shell
1. 重命名文件
git mv 旧文件.格式 新文件.格式

2. 查看状态
git -status

3. 提交
git commit -m '把某某重命名为某某某'

4. 移动文件或目录
git不会跟踪空白目录,新建目录后,查看状态时不会提示有新文件夹.
git mv xxx.格式 新文件夹/
git mv 旧文件夹 新文件夹/

5. 提交
git commit -m '把什么移动到了什么目录下'
```

# git-rm
```shell
1. 删除文件
git rm xxx.格式

2. 查看状态
git status

3. 提交
git commit -m '删除了某某某文件'
```

# git-head
```shell
1. 删除文件
git rm xxx.格式

2. 恢复文件
git checkout HEAD -- xxx.格式 # HEAD代表最近的一次提交，--表示当前分支

3. 提交删除后恢复文件
git checkout HEAD^ -- xxx.格式 # ^表示上一次提交，两个^^上上次
```

# git-revert
```shell
1. 查看历史提交
git log --oneline

2. 恢复某次提交
git revert id号
```

# git-reset
```shell
1. soft
git log --oneline
git reset --soft id号 # 将指针指向id这次提交

2. hard
git reset --mixed id号

3. mixed
git reset --hard id1
git reset --hard id2
```

# git-branch
```shell
1. 查看项目所有的分支
git branch

2. 创建新分支
git branch xxx

3. 切换分支
git checkout xxx

4. 查看当前分支
git branch

```

# git-checkout
```shell
1. 查看提交历史显示是哪个分支上的
git log --oneline --decorate

2. 切换到主分支
git checkout master

3. 查看所有分支的历史提交
git log --oneline --decorate --all

```

# git-branch-diff
```shell
1. 查看两个分支的区别
git diff master..某某某

2. 查看两个分支的同一文件的区别
git diff master..某分支 某文件

```

# git-fast-forward
```shell
1. 合并某分支到master
git merge 某分支
# 这是一个Fast-forward，不会是一个新的提交，查看历史提交，会显示最后一次是在分支上进行的提交。
git diff master..某分值
```
    
# git-merge
```shell
1. 切换分支
git checkout 某分支
git branch # 查看当前分支

2. 快捷提交
git commit -am '说明'
git log --oneline # 查看历史提交

3. master和某分支均已修改的情况下合并
git log --oneline --decorate --all -19 --graph # 查看10条，所有分支的历史提交
git branch # 查看当前所在分支
git merge 某分支

# 输入合并提交的描述（可保持默认）
git log --oneline --decorate --all -19 --graph # 查看10条，所有分支的历史提交
```

# git-conflict
```shell
1. 合并分支时出现冲突
```

# rm-branch
```shell
1. 给分支重命名
git merge master

2. 删除分支
git branch -m 已经存在的分支 新名字
git branch -d 某分支
```

# stash
```shell
1. 保存工作进度
git status
git stash save '修改了某某文件'
git status # 目录是干净的

2. 查看保存的工作进度的列表
git stash list

3. 对比工作进度和现在目录的区别
git stash show -p stash@{代号} # 代号使用git stash list查看

4. 恢复工作进度
git stash apply stash@{代号}

5. 删除工作进度
git stash drop stash@{0}

6. 恢复工作进度时直接删除工作进度
git stash pop stash@{代号}

```

# log
```shell
1. 查看历史
git log

2. 显示简单的日志列表
git log --oneline
git log --oneline -行数
git log --oneline --author="作者"

3. 显示指定内容的提交
git log --oneline --grep='内容'

4. 显示指定日期的提交
git log --oneline --before='2021-08-03' # 2021.08.03之前的提交
git log --oneline --before='1 week' # 1周之前的提交
git log --oneline --before='3 days' # 3天之前的提交

5. 图形效果
git log --oneline --graph

6. 查看log详细使用手册
git help log

```

# alias
```shell
1. 给常用命令添加别名
git config --global alias.co checkout

2. 给命令行命令设置别名
vi ~/.bashrc
alias gco='git checkout'
source ~/.bashrc

```

# ignore / gitignore
```shell
1. 在项目根目录下指定需要忽略的文件
git config --global core.excludesfile ~/.gitignore_global
vi ~/.gitignore_global

ls -la #查看以.开头的文件
vi .gitignore
*.log
git add.
git commit -m '添加了 .gitignore 文件'
```
# origin
```shell
git remote add origin 远程代码库地址

git remote

git remote -v

git remote rm 远程名
```
# push
```shell
git push -u origin master
git branch -a # 查看本地所有分支
git branch -r # 查看远程分支
git push -u origin 某分支
```
# clone
```shell
git clone https://xxxx.git 目标目录
cd 目标目录
git checkout master # 切换到主分支
# 修改文件……
git commit -am '修改了某文件' # 提交
git push origin master # 把提交推送到远程
```
# fetch
```shell
git fetch
git status
git merge origin/master
git status
```
# fork
```shell
git clone https://xxx.git 目标目录
git config user.name '李四'
git config user.email '某某@163.com'
vi README.md
git add .
git commit -m '添加了README.md 文件'
git push origin master # 输入李四的用户名和密码
```
# pull-request
```shell
git fetch

git push origin master
```
# git 分支从 master 改为 main
```shell
git branch -M main
```
# Git 配置 socks5 代理
```shell
git config --global http.proxy 'socks5://127.0.0.1:port'
git config --global https.proxy 'socks5://127.0.0.1:port'
```
# 第一次 push 代码的步骤
```shell
git init
git add .
git commit -m '说明'
git remote add origin https://xxx.git
git push -u origin main
```
# 克隆的项目子模块作为新项目文件跟踪
```shell
git rm --cached folder # 其中 folder 为子文件夹。
git add folder
```
    










 





