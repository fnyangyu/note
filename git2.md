git clone git@github.com:Sunny-zz/1709.git

https://github.com/Sunny-zz/1709.git

github 分支   gh-pages         xxx.github.io/app1



master  主分支
index.html style.css公共
about.html   help.html
ls -a  查看隐藏文件   .git 说明本地文件夹是一个github仓库
git branch  --查看当前仓库的分支  *说明  当前位于某个分支   -r 查看远端的分支
git brandch  分支名    --创建新的分支     git branch gh-pages
            当创建新的分支的时候分支里面的内容默认和master分支一样
git checkout 分支名   --切换分支

git checkout -b [yourbranch]  创建新的分支并切换过去



如果一个仓库(除了 xxx.github.io 之外)内有 gh-pages 分支
可使用 用户名.github.io/仓库名  访问 gh-pages 分支下的页面


新建一个仓库  hello    输入网址  xxx.github.io/hello  看到index.html

1.创建仓库 hello  添加了readme.md
2.克隆到本地 git clone
3.新建分支 gh-pages 并切换  git
4.分支上新建 index.html  并上传    git add .   git commit -m'11'   git push
5.访问  git用户名.github.io/hello



github 代码托管工具
本地  网上
1.网上有仓库并且仓库内有内容  仓库克隆到本地   git clone 地址(http ssh)
git add .     git commit -m'xx'     git push      git  pull
2.把本地的项目上传到网上的空仓库
git init     git add .     git commit -m'xx'     git push

ssh-keygen   主目录下会生成 .ssh 文件 内部会生成 两个文件 其中一个就是公钥  id_rsa.pub


分支


1.git用户名.github.io 这个仓库 下的 index.html 能直接访问
用户名.github.io
2.如果一个仓库(除了 xxx.github.io 之外)内有 gh-pages 分支下的 index.html能直接访问
用户名.github.io/仓库名

node   npm
apm install emmet atom编辑器安装插件    atom package manger
nvm  node  version  manger   使用nvm可以安装任何版本的node
nvm ls-remote  查看nvm可以安装那些node版本
nvm use stable
npm 是node的包管理工具  node  packge  manger
新建一个文件夹npm-demo
npm init
npm i jquery --save
npm unninstall jquery
npm i xx --save-dev 安装工具包
压缩js html css   新的js语法自动编译为es5语法

.gitignore 文件  git上传时 写在该文件被忽略上传


将本地仓库删除   克隆网上的仓库到本地  将node_modules删除
再上传 此时网上就没有了 node_modules
然后本地 npm i  node_modules 就会出现
此时 新建  .gitignore
再上传  此时本地的node_modules 就会上传不上去了
