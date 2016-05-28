---
title: "如何把simiki部署到GithubPage"
layout: page
date: 2016-05-28 15:11:34
---

- 目标：

	把simiki生成的wiki页面部署到miniminyi.com/wiki上  

- 问题：

	miniminyi.com上的网页是用hexo生成的，hexo的拓展性不是特别好，不能直接把simiki生成的wiki文件夹直接放到miniminyi.github.io的文件夹下

- 方法：

	1. 	把静态网页放在hexo中的theme/theme_name/source文件夹下  
		hexo g 之后，放在source下的文件会出现在博客的主目录下  

		**缺点**：

		每次用simiki生成页面后，都要复制到hexo里，再执行 hexo g和push，太麻烦  
		

	2. 
		- 参考[simiki部署](http://simiki.org/zh-docs/deploy.html)  ,按照不绑定域名的方法：
		- 先在github中新建一个repository，命名为wiki，在wiki的output目录下，git初始化，创建 `gh-pages`分支：
		
		```
			cd output
			git init
			git checkout -b gh-pages
			git add .
			git commit -m 'comment'
			git remote add origin git@github.com: <username>/wiki.git
			git push -u origin gh-pages
		```
		- 回到上层目录，创建`.gitignore`文件：
		
		```
			cd ../
			echo '*.pyc\noutput' > .gitignore
		```

		- 创建master分支:
		
		```
			git init
			# 将要绑定的域名+/wiki写到站点根目录下的CNAME文件中
			echo "<yourdomain.com>/wiki" > CNAME
			git add .
			git commit -m 'your comment'
			# 以下步骤会在Github上创建一个空项目后提示
			git remote add origin git@github.com:<username>/<projectname>.git
			git push -u origin master
		```

		- 修改simiki中的_config.yml文件
			设置_config.yml中的root配置项:
			`root: /<projectname>`

		- 按照这个方法做完之后，每次把md文件加入content文件夹后，只需要返回上层文件夹，`simiki g`和`simiki p`，然后进入output文件夹，`git add .`和`git commit -m "comment"`和`git push -u origin gh-pages`
		- 如果除了修改md文件，还修改了主题或config之类，则需要回到mywiki文件夹，`git push -u origin master`

