# Git

### 配置

​	**name**

​		git config --global user.name "jensen"

​	**email**

​		git config --global user.email "le1ton@outlook.com"

### 使用git

​	git status 

​		-- 查看当前仓库状态

​	git init

​		-- 初始化仓库

​	刚刚添加到项目中的文件处于未跟踪状态

​		未跟踪  ---> 暂存

​			git add <filename> 将文件切换到暂存的状态

​			git add * 将所有已修改（未跟踪）的文件暂存

​			![image-20230311140607919](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20230311140607919.png) 

​		暂存  ---> 未修改

​			git commit -m "xxx" 将暂存的文件存储到仓库中

​			git commit -a -m "xxx" 吉他就·提交所有已修改的文件（未跟踪的文件不会提交） 

​		未修改  ---> 修改

​			修改代码后，文件会变为修改状态

### 常用命令

1. 重置文件

```bash
git restore <filename> #恢复文件
git restore --staged <filename> #取消暂存状态
```

2. 删除文件

```bash
git rm <filename> #删除文件
git rm <filename> -f #强制删除文件
```

3. 移动文件

```bash
git mv from to #移动文件 重命名文件
```

### 分支

git在存储文件时，每次代码提交都会创建一个与之对应的节点，git就是通过一个一个的节点来记录代码的状态的。节点会构成一个树状结构，树状结构就意味着这个数会存在分支，默认情况下仓库只有一个分支，命名为master，在使用git时，可以创建多个分支，分支与分支之间相互独立，在一个分支上修改代码不会影响到其他的分支。

1. 查看分支

```bash
git branch # 查看当前分支
git branch <branch name> # 创建新的分支
git branch -d <branch name> # 删除分支
git switch <branch name> # 切换分支
git switch -c <branch name> # 创建并切换分支

```

在开发中，都是在自己的分支上编写代码，代码编写完成后，再将自己的分支合并到主分支中

### 变基（rebase）

在开发中，除了通过merge来合并分支外，还可以通过变基来完成分支的合并。

我们通过merge合并分支时，在提交记录中会将所有的分支创建和分支合并过程全部都显示出来，这样当项目比较复杂，开发过程比较波折时，我们必须要反复地创建、合并、删除分支。这样但是这样一来将会使得我们的代码的提交记录变得极为混乱

**原理**（变基时发生了什么）：

	1. 当我们发起变基时，git会首先找到两条分支的最近的共同祖先
	1. 对比当前分支相对于祖先的历史提交，并且将他们提取出来存储到一个临时文件中
	1. 将当前部分指向目标的基底
	1. 以当前基底开始，重新执行历史操作

变基和merge对于合并分支来说最终的结果是一样的！但是变基会使得代码的提交记录更整洁清晰！注意！大部分情况下合并和变基是可以互换的，但是如果分支已经提交给了远程仓库，那么这是尽量不要使用变基

### 远程仓库（remote）

目前我们对于git所有的操作都是在本地进行的。但是在开发中显然不能这样，这时我们就需要一个远程的git仓库，远程的git仓库和本地的本质没有什么区别，不同点在于远程的仓库可以被多人同时访问使用，方便我们协同开发，在实际工作中，git服务器通常由公司搭建内部使用，或是购买一些公共的私有git服务器。我们学习阶段，直接使用一些开放的公共git仓库。目前常用的库有两个：GitHub和Gitee（码云）

将本地库上传到github：

```bash
git remote add origin https://github.com/Le1ton/git-demo.git 
	# git remote add <remote name> <url>
	
git branch -M main
	# 修改分支的名字为main
	
git push -u origin main
	# git push 将代码上传到服务器上
```

将本地库上传到gitee：

```bash
git remote add origin https://gitee.com/uleiton/git-demo.git
git push -u origin "master"
```

### 远程库的操作的命令

```bash
git remote # 列出当前的管理的远程库
git remote add <远程库名> <url> # 关联远程仓库
git remote remove <远程库名> # 删除远程库
git push -u <远程库名> <分支名> # 向远程仓库推送代码，并和当前分支关联
git push <远程库> <本地分支>:<远程分支>
git clone <url> # 从远程库下载代码

git push # 如果本地库的版本低于远程库，push默认是推不上去的
git fetch 
	# 要想推送成功，必须先确保本地库和远程库的版本一致,fetch它会从远程仓库下载所有代码，但它不会将代码和当前分支自动合并
	# 使用fetch拉取代码后，必须要手动对代码进行合并
git pull # 从服务器中拉取代码并自动合并
```

**注意！**推送代码之前，一定要先从远程库中拉去最新的代码

### tag 标签

- 当头指针没有指向某个分支的头部时，这种状态我们称为分离头指针（HEAD detached），在分离头指针的状态下也可以操作代码，但是这些操作不会出现在任何的分支上，所以注意不要在分离头指针的状态下操作仓库
- 如果非得要回到后边的节点对代码进行操作，则可以选中**创建分支**后再操作

```bash
git switch -c test 1dd381e 
git switch -c <分支名><提交ID>
```

- 可以为提交记录设置标签，设置标签以后，可以通过标签快速地识别出不同的开发节点

```bash
git tag
git tag 版本
git tag 版本 提交ID
git push 远程仓库 标签名
git push 远程仓库 --tags
git tag -d 标签名 # 删除标签
git push 远程仓库 --delete 标签名 # 删除远程标签
```

### gitignore

- 默认情况下，git会监视项目中所有内容，但是有些内容比如node_modules目录中的内容，我们不希望它被git所管理，我们可以在项目目录中添加一个 .gitignore 文件，来设置那些需要git忽略的文件。

### GitHub的静态页面

- 在GitHub中，可以将自己的静态页面直接部署到GitHub中，它会给我们提供一个地址使得我们的页面变成一个真的的网站，可以供用户访问
- 要求：
  - 静态页面的分支必须叫做：gh-pages
  - 如果希望页面可以通过xxx.github.io访问，则需要将库的名字配置为xxx.github.io

### docusaurus

- facebook推出的开源的静态的内容管理系统，通过它可以快速的部署一个静态网站
- 使用：
  - 网址：
    -  https://docusaurus.io/
  - 安装
    - npx create-docusaurus@latest my-website classic
  - 启动项目
    - npm start 或 yarn start
  - 构建项目
    - npm run build 或 yarn build
  - 配置项目
    - docusaurus.config.js 项目的配置文件
  - 添加页面
    - 在docusaurus中，页面分为三种：1. page	2. blog	3. doc
  - 注意事项
    * deploymentBranch 来指定分支！
      *  deploymentBranch: "gh-pages"
    * 还需要配置一个环境变量：GIT_USER: GitHub的用户名
    * navBar















