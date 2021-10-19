---
title: "场景一：一体机初始化"
description: 本小节主要介绍青立方® 超融合易捷版 场景一：一体机初始化。 
keywords: 青立方® 超融合易捷版，场景一：一体机初始化
weight: 15
collapsible: false
draft: false
---



CloudeCube Express 一体机出厂时已预装超融合操作系统，并已经设置 ETH0 的 IP 地址为 `100.100.100.100/24`。

## 确定 ETH0 物理位置

以通过服务器基本信息配置界面 **Boot setting** 区域上检验，点击左侧 **网卡检查**，使网卡 ETH0 对应网口上的 LED 不断地闪烁，从而确定其物理位置。

![Boot setting](../../../_images/boot_setting.png)

![网卡检查](../../../_images/check_eth0.png)

## 步骤 1：配置服务器基本信息

1. 配置 PC（笔记本电脑）与待安装机器环境同网段 IP 地址。
   
   若使用的是 Windows 10 系统，其中 IP 地址填写诸如 100.100.100.101 等，在 100.100.100.100/24 子网内的地址。子网掩码填写 255.255.255.0，其他可不必填写。

   <img src="../../../_images/ipv4.png" alt="配置网络环境" style="zoom:50%;" />

2. 使用网线直连服务器的 ETH0 网卡口。
   
   在您的电脑用浏览器打开 http://100.100.100.100:9998/bootsetting/ 访问 **Boot Setting** 配置网络的界面，根据实际环境信息来配置服务器管理网络。
   
3. 在勾选网卡并检测网卡。
   
   ![检查网卡](../../../_images/check_net.png)

4. 填写配置信息。

    若安装多台超融合机器时，需要**分别登录每台机器以配置网络**。

    **主机名**：主机名必须采用这样的格式规范：`ZONE_ID r 机柜位置 n 机器位置`。例如pek3r02n02。

    **IP 地**址：自定义物理节点的管理 IP 地址，例如本示例的 3 台物理主机的管理 IP 地址设置为 172.16.76.3 - 172.16.76.5。

    **子网掩码**：设置服务器所在网段的子网掩码，例如 255.255.255.0。

    **网关**：填写服务器所在网段的网关 IP 地址，例如 172.16.76.1。

    <img src="../../../_images/net_info.png" alt="配置网络信息" style="zoom:50%;" />

5. 开启 Bond 和 VLAN，并设置启动节点。

    **开启 Bond**：如果您的管理 IP 是配置给做了 Bond 的两张网卡的两个网口（一张网卡选一个网口），此时需要勾选此项，在左边勾选两张对应网卡，未手动设置Bond的网卡会被自动配置 。

    **开启 VLAN**：如果您的管理 IP 对应在物理交换机上配置了 VLAN ，无论是分配给了网卡的一个网口（未开启 Bond），还是分配给做了 Bond 的两张网卡的两个网口（开启了 Bond），此时需开启 VLAN 并填入 VLAN ID (从交换机获取)，根据实际情况在左侧勾选目标网口或者构建 Bond 的两个网口；(若 Bond 或 VLAN 都不设置，可自行选择其中一张网卡配置 IP 地址)。

    **启动节点**：多台机器只需要选择其中任意一台勾选设置为启动节点，并填写一个额外的与该服务器同网段的空闲 IP 地址，作为 Web Installer 的登录入口。

   ![配置网络信息](../../../_images/net_info_2.png)

6. 确认填写无误可以点击**设置**，刷新浏览器后如果该配置页面不再显示，说明配置成功。

   ![检查网络信息](../../../_images/check_network.png)

## 步骤 2：访问 Web Installer

1. 在浏览器中输入启动节点的 IP http://IP:9998/ ，访问登录界面。

2. 输入用户名和密码。

   默认登录用户名密码为 admin/zhu88jie。

以 http://192.168.0.2:9998/ 为示例说明。

![登录界面](../../../_images/login.png)