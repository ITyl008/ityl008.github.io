[toc]
---
title: edgeexp
date: 2024-07-08 14:29:56
tags:
---

# edge浏览器扩展 🥢
## 去除广告 🔪
![step1](pg2/5a27cda252b1cc0d022e6d51.png)
👣如何去除 [HTMLcheat](https://htmlcheatsheet.com/) 当中的ad呢？
---
- **老师教的方法是在控制台下,并要求放在浏览器扩展中** 
	
	![step1](pg2/adsandcont.jpg)

- **后面自己摸索编写js**
	``` js
		// 在父类masonryPanel下找到广告栏 reklamocska, 在判断rekla。
		//因为每个栏都有minimizepanel,但是有reklamocska的才是我们需要的


		document.querySelectorAll('.masonryPanel').forEach(ad => {
		  const re = ad.querySelector('.reklamocska');
		  //re就是在masonryPanel下找到reklamocska,如果找到就关闭masonrypanel的minimizePanel
		  //这样一个逻辑
		  if (re){
			const mi= ad.querySelector('.minimizePanel');
			mi.click();
		  }
		});
	```
![step2](pg2/6011d59d2a08e9000490abbe.png)

2. 🎫制作扩展参考微软官网 [创建扩展教程](https://learn.microsoft.com/zh-cn/microsoft-edge/extensions-chromium/getting-started/part1-simple-extension?tabs=v3)
	-
	- 新建一个manifast.js 添加如下内容
		``` json
		{
		    "name": "NASA picture of the day viewer",
		    "version": "0.0.0.1",
		    "manifest_version": 3,
		    "description": "An extension to display the NASA picture of the day.",
		    "icons": {
		        "16": "icons/nasapod16x16.png",
		        "32": "icons/nasapod32x32.png",
		        "48": "icons/nasapod48x48.png",
		        "128": "icons/nasapod128x128.png"
		    },
		    "action": {
		        "default_popup": "popup/popup.html"
		    }
		}
		```
	- 新建一个html
	![htmljiegou](pg2/jt247851.png)
**贴出代码**
		``` html
		<html lang="en">
			<head>
				<meta charset="UTF-8" />
				<title>NASA picture of the day</title>
			</head>
			<body>
				<div>
					<img src="/images/stars.jpeg" alt="Display the stars image" />
				</div>
			</body>
		</html>
		```
	- 目录结构如下 
		``` shell
		└── part1
		    ├── manifest.json
		    ├── icons
		    │   ├── nasapod16x16.png
		    │   ├── nasapod32x32.png
		    │   ├── nasapod48x48.png
		    │   └── nasapod128x128.png
		    ├── images
		    │   └── stars.jpeg
		    └── popup
		        └── popup.html
		```
		图片如下

		![mljiegou](pg2/jt24785.png)
		
	- 进入 edge 输入 `edge://extensions/`

		![edgekuoz](pg2/jt247852.png)
		
	**下一步添加扩展文件夹**
	
	![edgeanzhuangjietu](pg2/jt247853.png)
	
	**下一步查看和使用**
	
	![edgeanzhuangjietu](pg2/jt247854.png)