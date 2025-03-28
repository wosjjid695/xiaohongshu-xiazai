# 在CloudCone存储VPS上快速部署飞牛NAS系统的完整指南

## 前言
飞牛NAS作为一款新兴的国产NAS系统，凭借其简洁易用的界面和丰富的功能，正受到越来越多用户的关注。本文将详细介绍如何在CloudCone存储型VPS上通过DD方式快速安装飞牛NAS系统。

## 准备工作
- **运行环境**：Debian 12系统
- **必备信息**：安装前请记录VPS的以下网络信息：
  - IP地址
  - 子网掩码
  - 默认网关

👉 [【点击查看】2025年最新CloudCone优惠码及特价云服务器方案汇总](https://bit.ly/Cloudcone)

## 安装步骤

### 1. 一键DD安装
在SSH终端执行以下命令：

bash
wget --no-check-certificate -qO InstallNET.sh 'https://raw.githubusercontent.com/leitbogioro/Tools/master/Linux_reinstall/InstallNET.sh' && chmod a+x InstallNET.sh
./InstallNET.sh --image 'https://r2.yx.lu/fnos.vhd.gz'

### 2. 系统重启
安装完成后，执行`reboot`命令重启VPS。重启后系统需要10-15分钟完成安装。

> 提示：可通过VNC查看安装进度，但DD脚本显示可能不准确。

### 3. 首次登录
安装完成后，使用以下默认凭据登录：
- 用户名：mjj
- 密码：mjj@123

## 网络配置

### 1. 切换root权限
bash
sudo su
# 输入mjj用户密码

### 2. 配置网络
执行`nmtui`命令进入网络配置界面：
1. 选择"Edit a connection"
2. 选择有线连接(wired)
3. 配置以下参数：
   - Addresses：IP地址/子网掩码（如142.171.62.11/24）
   - Gateway：默认网关（如142.171.62.1）
   - DNS Servers：8.8.8.8

### 3. 激活网络
配置完成后：
1. 返回主菜单
2. 选择"Activate a connection"
3. 激活修改后的网络配置

## 存储空间配置

### 1. 常见问题解决
首次创建存储空间时可能会遇到GPT PMBR大小不符的问题，解决方法：

bash
fdisk -l  # 查看硬盘信息
parted -l  # 修复GPT表

### 2. 创建存储空间
1. 删除默认的5G空闲空间
2. 重新创建存储空间

## 系统功能概览
飞牛NAS提供以下实用功能：
- **文件管理**：支持多种文件格式的上传下载
- **多媒体中心**：内置影音播放器、下载工具
- **备份工具**：完善的数据备份方案
- **应用中心**：丰富的扩展应用

> 注意：使用BT/PT功能需谨慎，可能涉及版权问题导致VPS被封。

## 结语
通过本教程，您已成功在CloudCone存储VPS上部署了飞牛NAS系统。这款国产NAS系统功能全面，操作简便，是个人和小型企业搭建私有云的理想选择。