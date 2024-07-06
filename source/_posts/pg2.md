---
title: 建立hexo所遇到的坑
date: now
---
## 本人因为兴趣所以搭建了一个网站，也用来记录自己成长的过程。
## 下面开始总结过程
入门视频：[CodeSheep](https://www.bilibili.com/video/BV1Yb411a7ty?from=search&seid=2930915894768396428)	
下载所需的必备软件：
## **node.js** [点击跳转到下载](https://nodejs.org/dist/v14.16.1/)
## **git-bash**  [点击跳转到下载](https://npm.taobao.org/mirrors/git-for-windows/v2.31.1.windows.1/)
	那现在ok了，我们进入下载好的git 使用bash（看个人还可以用git-cmd） 
1.使用npm -v && node -v 出现 ![图片](pg2/1.jpg)
2.使用npm 将镜像源指向淘宝： 

	```
	npm install -g cnpm --registry=https://registry.npm.taobao.org
```
等待安装。。。

3.cnpm -v ’查看cnpm
4.全局安装hexo博客框架： 
```
	cnpm install -g hexo-cli 
```
hexo -v 验证
5.****建立空文件夹用来存储以后写的博客****
```
	mkdir blog
```
或者自己创建一个文件夹并进入其中

6.hexo 初始化 
```
	hexo init
```
等待安装。。。
可以查看文件夹里面会生成一些hexo的文件夹。
```
	hexo s ’本地打开hexo服务 浏览器输入localhost：4000 看到hexo标题时即成功。
```
以后都可以用hexo s 来预览

```
	hexo n “filename” ‘引号里面就是文件名，系统会自动地创建你所指定地filename.md
```
输入LL 查看文件或者进入 source\ _posts文件夹，使用编辑软件进入编辑。
_注意开头格式-前六行就写这些，下面一行开始写内容支持markdown语法_
```
	---
	title： 本篇博客的名称
	date：yyyy-mm-dd hh：MM：ss ；这里不能写错
	tags：
	---
```
可以查看文件夹中是否有建立 【你所指定地filename.md】
下面首先使用 `hexo clean` 清除， `hexo g` 生成，就可重新启动 `hexo s`
	会发现刚刚写的会在第一篇开头。
	
# 部署 _github/gitee_
## Github
1.登录 [Github](https://github.com/login?return_to=%2Fjoin%3Fref_cta%3DSign%2Bup%26ref_loc%3Dheader%2Blogged%2Bout%26ref_page%3D%252F%26source%3Dheader-home) 如果没有账号就 [注册](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)
	好了之后我们进入主页点击右上角加号选择 **New repository** 
注意： 
	Repository name要和左边的一样，如你的用户名使hsw12那么repository name就是 hsw12.github.io(Youusename.github.io)格式不能错
	Description (optional) 描述随便
	输入以上ok 选择-**creat repository**
	
	进入命令行 此时需要安装git插件：命令行目录要在\blog下，就是你安装hexo的目录
键入 `cnpm install --save hexo-deployer-git`  -稍等安装
	进入_config.yml文件，最下方修改
```
#deploy:
  type: git 	'注意每行“：”后都要有一个空格且repo，branch是自己写'
  repo: https://github.com/hsw12/hsw12.github.io ’指定刚刚建立的github仓库 
  branch: master ‘指定 branch

	
```
那 github仓库地址在哪呢？ 在 github界面点击头像 _your repository_ - 下方有 Youusename.github.io 格式的库点进去选择code 那里有https复制粘贴
	还要再一部就是保存你的github用户名，邮箱，用来确认你是谁。
```
	 git config --global user.name "Your Name" 如 hsw12那your name就要写 hsw12注意不要删除双引号
	 git config --global user.email "email@example.com" qq邮箱都可
	 再次输入可以查看系统保存
	 git config --global user.name
	 git config --global user.email
```

那么ok 输入 hexo三步部署。
```
	hexo clean ’清除
	hexo generate ‘生成
	hexo deploy  ’部署
	如果最后显示 INFO  Deploy done: git 说明部署成功
	可能还要输入github用户名和邮箱或密码，视情况。
```
这时候刷新github repository 会发现有文件夹了和文件了。那就说明对了。浏览器可以使用*.gihub.io访问了。
# 问题 1
1) 显示不是 deploy done ？ 有一个error: GE007: Your push would publish a private email address.信息那就是你的github邮箱**没有公开** 
[解决](https://blog.csdn.net/qq_34359927/article/details/83860031)
# 问题2 
2） Repository not found 你在 _config.yml 下输入的repo: 库源错误，如果是github 就要.https://github.com/yourusername/yourusername.gihub.io 
如果是gitee 就要 输入： https://gitee.com/yourusername/yourusername.git
# 问题3
输入 `hexo clean `显示失败，那么就要在/blog目录下找到 public 如果是空文件夹就要删除，如果不是那么就要先复制一份到别的地方去在删除原来的。

--------------------------------------------------
# gitee 部署
 结合着看 **先看** (https://gitee.com/help/articles/4136#article-header0)

# 主题的更换
 在/blog目录下
` git clone https://github.com/litten/hexo-theme-yilia.git（.git也要输入） themes/yilia(yilia是自建的) `  如果没成功就多输几次。会发现/blog/theme目录下会出现yilia目录。
进入去/blog目录下的_config.yml文件里。找到 **#Extensions** 下在 _theme：_ 注意加一个空格输入 yilia
```
	再输入
	hexo clean
	hexo g
	hexo s
```
在浏览器中输入发现内容改变了。