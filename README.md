# git-guide
git - 简易指南

1、从git官网：https://git-scm.com/downloads 下载软件，安装

2、创建检出仓库新仓库：在电脑某盘，创建新文件夹，到文件夹目录打开git，执行git init命令创建新的git仓库

3、检出仓库：执行如下命令以创建一个本地仓库的克隆版本：git clone /path/to/repository 

如果是远端服务器上的仓库，你的命令会是这个样子：git clone username@host:/path/to/repository

工作流原理：

你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 工作目录，它持有实际文件；第二个是 缓存区（Index），它像个缓存区域，临时保存你的改动；最后是 HEAD，指向你最近一次提交后的结果。

4、添加与提交

你可以计划改动（把它们添加到缓存区），使用如下命令：

git add <filename>

git add *

这是 git 基本工作流程的第一步；使用如下命令以实际提交改动：

git commit -m "代码提交信息"

现在，你的改动已经提交到了 HEAD，但是还没到你的远端仓库。

推送改动

你的改动现在已经在本地仓库的 HEAD 中了。执行如下命令以将这些改动提交到远端仓库：

git push origin master

可以把 master 换成你想要推送的任何分支。 

PS：在此处遇到问题查询了下资料：Please make sure you have the correct access rights and the repository exists.然后谷歌了一下，原来是ssh key有问题

-1、首先我得重新在git设置一下身份的名字和邮箱（因为当初都忘了设置啥了，因为遇到坑了）进入到需要提交的文件夹底下（因为直接打开git Bash，在没有路径的情况下，根本没！法！改！刚使用git时遇到的坑。。。）

git config --global user.name "yourname"

git config --global user.email“your@email.com"

注：yourname是你要设置的名字，your@email是你要设置的邮箱。

-2、删除.ssh文件夹（直接搜索该文件夹）下的known_hosts(手动删除即可，不需要git）

-3、git输入命令

$ ssh-keygen -t rsa -C "your@email.com"（请填你设置的邮箱地址）

接着出现：

Generating public/private rsa key pair.

Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):

请直接按下回车

然后系统会自动在.ssh文件夹下生成两个文件，id_rsa和id_rsa.pub，用记事本打开id_rsa.pub

将全部的内容复制

-4、打开https://github.com/，登陆你的账户，进入设置

进入ssh设置

在key中将刚刚复制的粘贴进去

点击add ssh key

-5、在git中输入命令：

ssh -T git@github.com

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：

git remote add origin <server>

如此你就能够将你的改动推送到所添加的服务器上去了。
