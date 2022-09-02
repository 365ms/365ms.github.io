---
title: 博客搭建
date: 2022-03-26 11:36:09
tags:
---

## 第一步
	访问Nodejs.org
	下载Nodejs.pkg

## 第二步
	打开terminal
	开启管理员模式 
		sudo su
	利用淘宝镜像源下载 cnpm 
		npm install -g cnpm --registry=https://registry.npm.taobao.org
	利用cnpm 全局安装 hexo 
		cnpm install -g hexo
<!--more-->
## 第三步
	cd /usr/jdm/
	创建Blog文件夹
		mkdir Blog
	生成博客网站
		sudo hexo init
	启动
		hexo s
## 第四步
	生成文章
		hexo n “（title）”
	目前路径在/source/_posts  回退到Blog根目录
		cd .../...
	先清理
		hexo clean
	再生成
		hexo g
## 第五步
	博客部署在Github上
		登陆Github 创建新的仓库
			Repository name 严格设置为 Github昵称.github.io 

	打开terminal
	开启管理员模式 
		sudo su
	利用cnmp安装 Github部署插件
		cnmp install --save hexo-deployer-git
	配置hexo 部署内容
		在Blog文件夹 打开 _config.yml
			找到# Deployment 开始配置
				type: git
				repo: (仓库地址) 在Github 新建的仓库界面 
				branch: master
	回到terminal 开始部署
		hexo d
		依次输入 Github的昵称 
				新建仓库的token 
	（token在哪？ 参考:https://blog.csdn.net/weixin_41010198/article/details/119698015）
## 第六步
	访问网站
		使用Repository name 访问








	
