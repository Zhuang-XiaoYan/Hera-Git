# 一、第一次PR相关命令

## 1.1 首先fork公司和开源代码仓库

git fork https://github.com/zhuangxiaoyan512/data.git（主仓库的URL）

## 1.2 在将你的个人远端仓库的clone到你的本地

git clone git@github.com:2462612540/data.git(个人仓库URL)

## 1.3 进入到项目中，在有.git文件的目录下 连接到远端仓库地址

git remote add upstream https://github.com/zhuangxiaoyan512/data.git（主仓库的URL）

## 1.4 禁止向远端主仓库进行的代码提交

git remote set-url --push upstream no_push

## 1.5 查看本地关联的代码库

git remote -v

## 1.6 checkout你的开发分支

git checkout vxrail-cr

## 1.7 在vxrail-cr分支上建立自己的分支的

git checkout -b topic/jiale_xiong/data/vxp568

## 1.8 查看的当时分支是否你自己的分支

git branch

## 1.9 然后在进行的你开发

update code

## 1.10 查看那些文件修改了

git status

## 1.11 提交好修改的文件大本地仓库

git add filename1 filename2

## 1.12 提交comit 信息（这个是作为代码提交的检查的 符合你们公司的开发规范）

git commit --amend (git commit -m "公司的规范")

## 1.13 推送到本地同时提交PR

git push -f origin topic/jiale_xiong/data/vxp568(本地分支):vxrail-cr（个人远端分支）

# 二、主仓库修后PR提交命令

## 2.1 拉取远端主仓库

git fetch upstream

## 2.2 进行合并操作(可以使用rebase 和merege两种操作)

此时你在topic/jiale_xiong/data/vxp568下将需要rebase或者是merege的分支

git rebase vxrail-cr(本地的分支) 就是将vxrail-cr（已经是最新的）合并到你当下分支（topic/jiale_xiong/data/vxp568）

## 2.3 这个时候就会出现有conflict问题

update code

## 2.4 查看有哪些文件有冲突

git diff

## 2.5 解决好冲突

update code

## 2.6 重新提交刚刚解决冲突的文件

git add filename1 filename2

## 2.7 提交commit 信息 记得这几是需要需改符合你公司的要求或者是开源社区的要求

git commit --amend

## 2.8 推送到本地同时提交PR

git push -f origin topic/jiale_xiong/data/vxp568(本地分支):vxrail-cr（个人远端分支）