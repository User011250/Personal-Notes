# Git笔记

## Github相关

GitHub是一个面向开源及私有软件项目的托管平台，因为只支持Git作为唯一的版本库格式进行托管，故名GitHub。

### 仓库（Repository）

仓库即项目，一个仓库代表一个软件项目。

### 关注（Watch）

关注项目，以便及时获取更新提醒。

### 收藏（Star）

收藏项目，以便于日后的查找和使用。

### 克隆（Fork）

将别人的项目克隆到自己的Github，之后的修改也不会影响别人原来的项目。

### 发起拉回请求（Pull Request）

在克隆项目或分支项目上进行修改后，向项目作者发起了拉回并合并修改后项目的请求，并等待审核。

### 问题卡片（Issue）

当发现代码BUG，但没有具体的可替换代码时，使用该功能进行讨论。

## Git相关

通过Git管理托管在Github上的项目代码。

### 安装Git

[Git官网下载](https://git-scm.com/)

### Git工作区域

- 工作区：添加、编辑、修改文件等动作。
- 暂存区：暂存已经修改的文件，最后统一提交到Git本地仓库中。
- Git本地仓库：最终确定的文件保存到本地仓库，成为一个新的版本。
- Git远程仓库：由Git本地仓库提交而来。

### Git基本命令

#### Github连接相关

- 设置用户名称：`git conifg --global user.name "username"`

- 设置电子邮箱：`git config --global user.email "xxxx@xxx.com"`

- 查看配置信息：`git config --global --list`

- 修改配置信息：`git config --global --edit` 

  > 在命令模式下，i进入编辑模式/Esc退出编辑模式/ZZ退出命令模式。

- SSH：`ssh-keygen -t rsa -C "邮箱地址"`

  >在用户的.ssh文件夹下`cat id_rsa.pub`获取密钥
  >
  >测试命令：`ssh -T git@github.com`

#### 本地仓库相关

- 创建仓库：`git init`

- 工作区->暂存区：`git add filename`

  >`git add  .`  文件的修改、新建
  >
  >`git add -u`  文件的修改、删除
  >
  >`git add -A`  文件的修改、删除和新建

- 暂存区->本地仓库： `git commit -m  "提交描述"`

- 删除暂存区和工作区文件：`git rm filename`

- 查看工作区和暂存区状态：`git status`

- 查看项目历史：`git log` / `git reflog`

  > wq退出

- 版本退回：`git reset HEAD/版本号前几位 filename`

  >--soft  只有本地仓库
  >
  >--mixed  默认模式，包括本地仓库、暂存区
  >
  >--hard　包括本地仓库、暂存区、工作区
  >
  >HEAD表示当前版本
  >
  >HEAD^表示上个版本
  >
  >HEAD^^表示上上个版本
  >
  >HEAD~100表示上100个版本

- 暂存区覆盖工作区：`git checkout -- filename` 

  > 暂存区全部覆盖工作区：`git checkout .`

#### 远程仓库相关

- 本地仓库->远程仓库：`git push 远程库名 本地分支名:远程分支名 `

  >在本地master下,`git push -u origin master` 
  >
  >把本地的master分支和远程的master分支关联起来，简化命令。

- 克隆项目：`git clone 项目地址 保存路径/重命名`

- 添加远程库`git remote add 默认远程库名origin 项目地址`

  >`git remote -v`
  >
  >`git remote rm origin`
  >
  >`git remote rename oldname newname `

- 拉取并合并远程仓库：`git pull 远程库名 远程分支名:本地分支名`

- 拉取远程仓库或分支：`git fetch 远程库名 <远程分支名>`

- 合并远程分支:`git merge 远程库名/远程分支名`

#### 分支相关

- 查看本地分支 `git branch`

- 查看远程分支`git branch -r`

- 查看所有分支`git branch -a`

- 创建分支 `git branch branchname`

- 切换分支`git checkout branchname`

- 创建并切换分支`git checkout -b branchname`

- 合并分支：`git merge 远程库名/远程分支名 or 本地分支名`

- 删除分支：`git branch -d branchname`

- 创建远程分支：`git push origin 远程分支名`

  > 首先要在本地创建同名分支，之后push创建的远程分支。

- 删除远程分支：`git push origin :远程分支名`

  > 空白分支覆盖远程分支。

#### 标签相关

- 查看所有标签：`git tag`
- 创建标签：`git tag tagname`
- 指定标签信息：`git tag -a <tagname> -m "blablabla..."`
- 推送一个本地标签：`git push origin tagname`
- 推送全部未推送过的本地标签：`git push origin --tags`
- 删除一个本地标签：`git tag -d tagname`
- 删除一个远程标签：`git push origin :refs/tags/tagname`

## 学习参考

- [Git教程-廖雪峰官网](https://www.liaoxuefeng.com/wiki/896043488029600)
- [GitHub使用教程-黑马](https://www.bilibili.com/video/BV1st411r7Sj?from=search&seid=8068310402318887654&spm_id_from=333.337.0.0)
- [Git安装教程-掘金](https://juejin.cn/post/7039897402660093966)

- [学习Git-菜鸟教程](https://www.runoob.com/git/git-tutorial.html)

