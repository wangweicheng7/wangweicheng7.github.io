# Git 启蒙

> Git 是一个分布式的版本控制和源代码管理系统，强调速度。 Git 最初由Linus Torvalds设计和开发为Linux内核开发管理代码。 Git是GNU通用公共许可证版本2的条款下分发的免费软件。

## 配置

* 配置用户账户信息
	
	```
	git config --global user.name "陌上一梦觅琴音" // 设置用户名
	git config --global user.email "moshangyimeng@gmail.com" // 设置用户邮箱	
	```
	
* SSH 密钥

	获得SSH密钥
	
	```
	cd ~/.ssh	// 查看是否已有密钥，如果没有键入
	ssh-keygen -t -C "你的邮箱"	// 生成密钥，一路回车
	```
	这时你的 `~/.ssh`目录下会有两个文件 `id_rsa`&`id_rsa.pub`，登录你的git仓库，将`id_rsa.pub`里面的内容粘贴到你的 SSH密钥
	
	测试密钥是否可用
	
	```
	ssh -T git@*** // 你的仓库地址
	```

## 仓库

* 本地已存在 `Git` 仓库或文件夹
	
	```	
	cd <仓库目录>
	git init  // 初始化仓库
	git remote add origin git@github.com:PW****.git // 关联到远程仓库
	git add .	// 添加所有文件
	git commit	// 提交修改
	git push -u origin master	// 提交到远程仓库master分支，初次提交要 -u
	```

* 本地还没有仓库
	
	```
	git clone gogs@github.com:PW****.git	// 将远程仓库代码克隆岛本地
	cd <仓库目录>
	/* 这样就将远程仓库信息克隆岛本地了，你可以在当前目录下修改文件，并比较 */
	```
* 多仓库操作
	
	同时推送你的更改到多个远程仓库，你可以使用
	
	```
	git remote set-url --add origin git@*****.git // 远程仓库的地址
	```
	或者进入.git目录下，修改config文件
	
	```
	[remote "origin"]
		url = git@github.com:PW***.git
		fetch = +refs/heads/*:refs/remotes/origin/*
		url = git@****.git	// 在这里添加你的远程仓库地址，有多少加多少
	```
	
	
## 分支管理
* 查看远程仓库分支   
	
	```
	git branch -a		// 查看远程所有仓库
	```
	
* 拉取远程分支
	
	```
	git fetch branch-1 // 假设有branch-1分支
	git checkout -b|-B <branch-1> // 如果远程存在branch-1，拉取到本地，如果没有，本地创建branch-1分支
	git checkout branch-1 // 切换到branch-1分支
	```	
* 添加到暂存区
	
	```
	git add .	// 添加所有修改
	git add README.md	// 添加README.md文件的修改
	```
* 提交暂存区
	
	```
	git commit // 提交更改，
	git commit -m "更改的信息" // 提交更改，并添加更改的信息
	```
* 将本地提交推送到远程
	
	```
	git push origin master	// 推送到主分支
	git push origin branch-1 // 推送到branch-1分支
	```
* 删除分支
	
	```
	git branch -d branch-1
	git branch -D branch-1	// 强行删除
	git push origin :branch-1	// 本地删除推送到远程，需要将本地分支删除
	git push --delete origin branch-1	// 删除远程分支
	```
	
## 标签管理
	
* 打标签操作要在`commit`操作之后进行，e.g
	
	```
	git add .
	git commit -m "release 1.0.0"
	git tag -a 1.0.0 -m "release 1.0.0"
	```
	
* 查看所有标签
	
	```
	git tag
	```
* 创建新标签
	
	```	
	git tag 1.0.0	 [-m]	// 创建标签，-m "release"，添加标签注释
	git tag 1.0.0	 6f4937e		// 为历史的提交打标签,6f4937e是你提交的节点hash值
	```
* 显示标签信息
	
	```
	git show 1.0.0	// 查看标签信息
	```
* 删除标签
	
	```
	git tag -d 1.0.0	// 从本地删除标签
	git push origin :refs/tags/1.0.0	// 删除远程标签
	```
* 推送标签
	
	```
	git push origin 1.0.0	// 将1.0.0推送到远程
	git push origin --tags	// 一次推送所有标签
	```
	
	
	
	
	
	
	
	
	
	
	
	
	
	
