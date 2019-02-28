# Samba的安装与配置

**版本信息**

| 版本号 | 日期       | 作者   | 描述 |
| ------ | ---------- | ------ | ---- |
| v1.0   | 2018-07-08 | kshell |      |

**目录**

[TOC]

## 一：环境

| 项目     | 版本号                         |
| -------- | ------------------------------ |
| 操作系统 | Linux Mint 18.3 Sylvia 64 位   |
| 内核版本 | Linux 4.13.0-43-generic x86_64 |

## 二：Samba的安装

### 1：安装软件包

```
sudo apt install samba
```

### 2：检查版本

```
sudo smbstatus
```

或者

```
sudo smbd --version
```

### 3：版本输出信息

```
Samba version 4.3.11-Ubuntu
```

### 4：检查服务运行状态

```
sudo service smbd status
sudo service nmbd status
```

| 服务 | 协议端口       | 服务描述                                          |
| ---- | -------------- | ------------------------------------------------- |
| smbd | tcp139和tcp445 | 管理samba服务器上的共享目录                       |
| nmbd | udp137和udp138 | 进行netbios名解析，使客户端能浏览服务器的共享资源 |

## 三：Samba的配置

### 1：配置文件

| 配置文件 | 文件路径            |
| -------- | ------------------- |
| smb.conf | /etc/samba/smb.conf |

### 2：配置共享

```
[down]
    comment = downloads
    path = /home/kshell/downloads
    read only = yes 
    guest ok =  no 
    valid users = kshell
```

### 3：配置描述

| 描述           | 配置                          |
| -------------- | ----------------------------- |
| 共享名称       | [down]                        |
| 共享描述       | comment = downloads           |
| 共享目录       | path = /home/kshell/downloads |
| 只读共享       | read only = yes               |
| 不允许匿名访问  | guest ok =  no                |
| 可访问的用户   | valid users = kshell,weihua   |

配置共享或修改配置后需要重启smbd服务才能生效

```
sudo service smbd restart
```

### 4：配置Samba用户

- Samba需要配置自己的用户用于访问共享，该用户不是系统用户
- 曾经以为就是系统用户，结果折腾来折腾去就是访问不了
- 使用sudo smbpasswd -a username 增加用户并设置密码就可以访问共享了

```
sudo smbpasswd -a kshell
```

## 四：客户端访问Samba

- Android设备上安装ES文件浏览器
- 局域网->新建->填入Samba服务器ip、用户名和密码即可
<meta http-equiv="refresh" content="1">