---
title: "使用Hexo遇到的奇怪事情"
layout: page
Date: 2016-05-28


---
## 使用hexo中遇到的各种奇怪的事情

- 在主页下添加静态html页面

	最方便的方法就是把网页或有网页的文件夹放在 `theme/theme-name/source` 下。然后hexo g,hexo d 就好了。  
  
  参见hexo上的问题 [#820](https://github.com/hexojs/hexo/issues/820#issuecomment-54732767)  
  
- 在搜索问题解决方案的时候找到一个[Hexo常见问题解决方案](https://xuanwo.org/2014/08/14/hexo-usual-problem/#%E8%87%AA%E6%9C%89%E5%9F%9F%E5%90%8D%E4%BA%8C%E7%BA%A7%E7%9B%AE%E5%BD%95%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AE)  
 收集了不少hexo上出现的问题和解决方案。
 
- 重新找到了一个比较全的简明[Github Pages与Hexo教程](http://www.jianshu.com/p/05289a4bc8b2)  

- hexo command not found
	可以看问题[#206]（https://github.com/hexojs/hexo/issues/206） 
	出现问题的原因是没有指定node的版本
	用下面命令解决

```bash

	nvm ls #查看nvm的所有版本和当前使用的版本  
	nvm use 0.0.0 #使用nvm某个版本  
	nvm alias default 0.0.0 #将nvm的默认版本指定为某个版本  
	
```

- 最诡异的是这个问题
	在compile的时候出错了，可以参考问题[#224](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak/issues/224)，最后要把hexo的版本降回版本3.1.1才解决掉，浪费了好多时间orz
	


