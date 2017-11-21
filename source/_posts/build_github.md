---
 layout: post
 title: "我的博客情缘-hexo搭建博客"
 date: 2017-7-27 11:40
 comments: true
 tags: 
    - hexo
 categories: "博客"
---

# 搭建一个属于自己的博客基本上分一下几个步骤
> * 环境搭建
> * 安装配置Hexo
> * 创建github仓库
> * 配置SSH keys
> * 配置主题
> * 关联github仓库
> * 创建和发布文章


## 第一步：环境搭建
### 安装Git

git官网(http://git-scm.com)
Windows: 直接下载和安装

### 安装Node.js

进入官网(https://nodejs.org/en/)
下载安装包，直接点击安装就可以了

## 第二步：安装配置Hexo
git和node.js安装成功后就可以使用npm安装hexo了
进入git或cmd执行以下命令 
> npm install -g hexo-cli

然后在你喜欢的目录下创建一个文件夹 hexo
cd 到 hexo文件夹右键单击Git Bash Here执行，
>hexo init
这个过程可能需要几分钟

初始化hexo，完成后执行
>npm install

安装依赖模块
执行完上述操作之后 xxx文件夹下面是这种结构
![image](/images/hexo/init-floder.png)

## 第三步：创建github仓库
在本地仓库首页点击右上角的加号，创建一个新的仓库
![image](/images/hexo/add-rep.png)

注意仓库名称的问题

## 第四步：配置SSH keys
github和本地代码做推送和拉取时，需要用到ssh的密钥对进行数据加解密，由于github上新建的项目没有添加密钥，所以本地仓库连接不到远程仓库。
### 首先需要检查你电脑上现有的ssh key：
>cd ~/.ssh

如果提示：No such file or directory 说明你没有ssh keys

### 生成新的ssh keys：
> ssh-keygen -t rsa -C "youremail@youremail.com"

邮箱地址改为你的邮箱地址 C必须为大写 回车后出现
![image](/images/hexo/ssh.png)

再次回车后系统会要你输入密码：
> Enter passphrase (empty for no passphrase):<输入加密串>
> Enter same passphrase again:<再次输入加密串>

这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入。这个设置是防止别人往你的项目里提交内容。

最后看到这样的界面，就成功设置ssh key了：
![image](/images/hexo/ssh-set-ok.png)

### 将ssh key 添加到github上
打开本地 C:\Users下的 .ssh 文件夹，找到id_rsa.pub文件，复制文件内容
登录github个人主页，打开Setting
![image](/images/hexo/set-ssh.png)

![image](/images/hexo/add-ssh.png)

完成SSH的配置


## 第五步：配置主题
进入hexo下的themes文件夹下，右键Git Bash
> git clone https://github.com/litten/hexo-theme-yilia.git

等待文件下载完成之后就可以在 themes问价夹下看到一个新的文件夹，你可以给这个问价夹改名为yilia
![image](/images/hexo/update-theme.png)
此时打开 hexo根目录下的 _config.yml文件，将theme改为 yilia ，这里的名称和themes文件夹下的名称应该相同，否则会报 no layout index.html的错误

修改完成之后再次运行
> hexo server

就可以看到修改主题后的效果了
![image](/images/hexo/new-theme.png)

## 关联github仓库
打开hexo根目录下的 _config.yml文件，修改
repository ：你的仓库地址
> deploy:
>  type: git
>  repository: https://github.com/XXX/XXX.github.io.git
>  branch: master

这样就将github个人仓库和hexo关联上了，接下来你需要执行
> hexo clean

清除以前生成的文件

> hexo generate

重新生成新的文件

> hexo deploy 

本地博客发布到github上，如果发布时候出现错误 ERROR Deployer not found: git

> 请执行 npm install hexo-deployer-git --save



## 第六步：创建和发表文章
想要发布新的文章，首先需要创建。cd到hexo文件夹下

> 执行 hexo new "文章标题"

你可以在hexo->source->_post目录下看到你新创建的那个文章,接下来你可以使用任意一款可以编辑markdown的工具写文章了，写好之后执行
> hexo g  
> hexo d

## 附录
>* hexo new "postName" #新建文章
>* hexo new page "pageName" #新建页面
>* hexo clean #清除之前生成的静态页面
>* hexo generate #生成静态页面至public目录
>* hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
>* hexo deploy #将.deploy目录部署到GitHub
>* hexo help  # 查看帮助
>* hexo version  #查看Hexo的版本

>* hexo n == hexo new
>* hexo g == hexo generate
>* hexo s == hexo server
>* hexo d == hexo deploy