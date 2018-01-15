
# github  代码访问工具
***
# 创建方法：
1. 网上新建一个仓库，并添加一个 readme 文件，git clone 到本地修改提交
2. 网上新建一个控仓库，本地新建一个同名的仓库（文件夹），把自己做好的项目上传到网上
	- 将本地的文件夹变成 git 仓库  命令 git init
	- git add index.html 将某些文件添加到 git 的缓存区   （. 代表所有）  让git软件跟踪你的修改
	- git commit -m'版本信息' 将本次的修改做成一个版本  并提交版本信息
	（如果是第一次使用git commit 命令的话会弹出提示信息 请告诉我你是谁）
	- git push
		第一次推送的话
		没有推送目标。
	- 通过命令行指令 URL ，或用下面命令配置一个远程仓库

```
git remote add origin https://github.com/theonell/theonelm.git
```

	- 然后使用该远程仓库名执行推送

```
	git push -u origin master
```


# 添加公钥
- ssh-keygen 创建了一个钥匙，主目录下会生成 .ssh文件
- 内部会生成 两个文件，其中一个就是公钥（id_rsa.pub）

1. 分支命令
	- git branch --查看当前仓库的分支
	- * 说明 当前位于某个分支
	- -r 查看远程仓库的分支
	- git branch 分支名  创建新的分支
	- git branch gh-pages  内容默认和master一样
	- git checkout 分支名  切换分支
	- git checkout -b 分支名  创建新的分支并切换
2. 如果一个仓库（除了xxx.github.io之外）内有gh-pages分支
3. 可使用用户名.github.io/仓库名,访问gh-pages分之下的页面
