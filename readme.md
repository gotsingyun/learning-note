# Git使用教程

@(示例笔记本)[git]

[原文参考](https://blog.csdn.net/mango9126/article/details/68946439) 
**git是什么**： 分布式版本控制系统；

-----
[TOC]

## git安装

 >   [点击官网下载](https://www.git-scm.com/download/)(我是在三方软件管家下载的)默认安装即可，安装完成后在安装路径下查询 ‘git ->  git bash即可’；或者在任意目录下右键，查看是否有'Git Bash Here'。 

###设置用户名等信息
   有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。
```git
$ git config --global user.name "tsingyun_go"
$ git config --global user.email "tsingyun_go@163.com"
```

##git基础语法

|语法          |简述     |备注   |
|:--          |:--     |:--   |
|git init     | 将当前文件夹纳入git管理       |      |
|git add readme.txt|在当前目录添加文件文件到（.git中）暂存区||
|git commit -m "reademe 提交" |将文件提交至本地git仓库| -m ''是注释|
|git status| 查看状态||
|git diff redeme.txt|修改后可查看修改内容||
|git log|查看修改记录||
|git reset --hard HEAD^|(强制)回退到上一版本| HEAD^^:上上个版本；HEAD^100 上100个版本|
|git reflog |查看所有记录，包含回退的版本|
|git reset --hard xxx(版本号)|强制回退到某一版本|
|git checkout --readme.txt|撤销还未commit的修改内容，即工作区做的修改全部撤销，但是不影响暂存区||
|git checkout reademe.txt|对比上面缺少'--'后会创建新分支||
|git rm b.txt|删除commit后的文件||
|git checkout --b.txt|恢复删除的文件||
|git remote add origin "github上的仓库地址"|把本地仓库内容添加至远程github仓库|
|git push -u origin master|把本地仓库分支master内容推送至远程仓库|本地的master分支和远程的master分支关联起来， 在以后的推送或者拉取时就可以简化命令|
|git clone "github上的仓库地址"|克隆一个本地库|
|git checkout -b dev|创建并切换分支||
|git branch|查看当前分支|会列出所有的分支，当前分支前面会添加一个星号|
|git merge dev|在当前分支上合并dev分支内容||
|git branch -d dev |删除dev分支||


###远程仓库
注册github账号，因为本地git仓库与github仓库之间传输是通过SSH加密的，故需如下配置：
####1、创建SSH Key,
  在用户目录下查找.ssh目录下的id_rsa （非对称加密算法的密文）与id_rsa.pub （明文）文件，若无,输入如下命令，若有则跳过
```cmd
ssh-keygen -t rsa -C "your email"
```
###2、添加密文
   在github上点击登录头像打开 'settings ->  Developer settings  ->  Personal access tokens -> Generate new token '，
添加你的id_rsa.pub （明文）


