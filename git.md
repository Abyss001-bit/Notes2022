# 2021 git study

## git安装
    windows安装：一路确认即可

## git 配置github仓库


### 认证主机与仓库(配置个人的用户名称和电子邮件地址)
```
此处使用global 即配置文件只适用于该用户，而 system 对系统中所有用户都普遍适用
git config --global user.name "Abyss001-bit"
git config --global user.email "mortytr001@126.com"
```
### 设置文本编辑器 Emacs
```
git config --global core.editor emacs
```
### 设置文本编辑器 vimdiff
```
git config --global merge.tool vimdiff
```
### 查看配置信息
```
git config --list
```
### 修改环境变量
```
git config usre.name
itanrong
```

## git 工作流程

    克隆 Git 资源作为工作目录。------git clone XXX
    在克隆的资源上添加或修改文件。  -----修改
    如果其他人修改了，你可以更新资源。-----add
    在提交前查看修改。 ------查看修改
    提交修改。--------commit
    在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。 ----reset and commiet

### git 工作区、暂存区和版本库

    工作区：电脑上看到的目录
    版本库：工作区由一个隐藏目录 .git ,这个不算工作区，而是版本库，版本库中有索引、分支、对象库三部分
    暂存区：一般在 .git 目录下的 index 文件（.git/index）中，也叫索引，即版本库的索引


    工作区 add 使得 暂存区目录更新，工作区修改写入对象库中的一个新对象中，新对象id被记录在暂存区的文件索引中。

    commit 使得暂存区的目录树写入版本库（对象库）中，对应暂存区目录树的分支做出更新。

    git reset HEAD : 暂存区的目录树被重写，被分支指向的目录树代替，即回退了，工作区不受影响，此操作在add后commit前。

    git rm --cached <file> : 会直接从暂存区删除文件，工作区不做改变，也是add后commit前。

    git checkout . 或者 git checkout -- <file> :  用暂存区的全部或指定文件替换工作区的文件。会清除工作区中未添加到暂存区中的改动。

    git checkout HEAD . 或者 git checkout HEAD <file> : 用HEAD指向的分支全部或部分文件替代暂存区和工作目录中的文件。会清除全部未提交的修改。

* 由此可知，在 commit之前一定要确保修改完成了 


### git 创建仓库

```
git config --global user.name "Abyss001-bit"
git config --global user.email "mortytr001@126.com"
```

本地创建仓库链接远程：

```
echo "# 2021" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/Abyss001-bit/2021.git
git push -u origin master
```

* 不知道为什么我的github 第一次push 容易失败


远程clone 推送项目：
```
克隆仓库：
git clone https://github.com/Abyss001-bit/2021.git
修改提交推送
```
## git基本操作
```
git init

git add .
git status
git diff   ---比较文件的不同，即暂存区和工作区的差异。
git commit -m "XXX"

git log

git remote   ---远程仓库操作
git fetch    ---从远程获取代码库
git pull     ---下载远程代码并合并
git push     ---上传远程代码并合并
```

## git分支管理
```
创建分支：
git branch (branchname)

列出分支：
git branch -a

切换分支：
git checkout (branchname)

创建新分支并切换到该分支下：
git checkout -b (branchname)

合并分支：
git merge 
合并分支遇到冲突需要手动修改，用git add告诉文件冲突已经解决

删除分支：
git branch -d (branchname)
```


## git查看提交历史
```
git log
git log --graph   拓扑图版
git log --oneline 简洁行版
git log --reverse 逆向显示日志
git log --author=Linus --oneline -5  指定用户Linus提交的5行日志

git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges 
看 Git 项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）
```

## git查看指定文件的修改记录
```
git blame <file>
```

## git标签
```
git tag -a v1.0  
之后会自动让我写些注释

或者
指定标签信息：
git tag -a <tagname> -m "XXX标签"
PGP签名标签:
git tag -s <tagname> -m "XXX标签"

追加标签：
git tag -a v0.9 id

查看所有标签：
git tag
```
## git版本回退
```
HEAD 是当前版本，HEAD^ 是上一个版本
git reset --hard HEAD^    

回退到指定版本
git reset --hard id

记录每一次命令
git reflog
```

## github仓库
https://www.runoob.com/git/git-remote-repo.html


## gitee仓库
https://www.runoob.com/git/git-gitee.html

## git服务器搭建
https://www.runoob.com/git/git-server.html
