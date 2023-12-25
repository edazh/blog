---
title: WSL-Ubuntu配置国内镜像源
date: 2023-12-26 00:33
tags: ['前端', 'wsl', 'linux', 'ubuntu']
categories: 开发手札
---

## apt-get 和 pip 国内源更换

1. 输入：`sudo -s` 切换为 `root` 超级管理员；
2. 查看 `linux` 版本：`lsb_release -a`
3. 执行命令：`vim /etc/apt/sources.list`
4. 使用命令：`%d` 清空所有内容；
5. 清华数据源地址：[https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/](https://yq.aliyun.com/go/articleRenderRedirect?url=https%3A%2F%2Fmirrors.tuna.tsinghua.edu.cn%2Fhelp%2Fubuntu%2F)  选择相应的版本复制内容，点击`i`键进入编辑文本模式，粘贴内容到 vim 编辑窗体，点击`ESC`键进入编辑模式，输入`:wq`保存离开；
6. 更新源：`sudo apt-get update`
7. 更新软件：`sudo apt-get upgrade`

## pip3 的安装与升级

```bash
# 安装pip3
sudo apt-get install python3-pip

# 升级pip3
sudo pip3 install --upgrade pip

# 查看pip版本
pip -V
```

## pip 源更换

1. 根目录创建.pip 文件：`mkdir ~/.pip`
2. 创建文件 pip.conf：`vim .pip/pip.conf`
3. 点击`i`键，进入编辑模式，复制信息：

```
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
trusted-host = pypi.tuna.tsinghua.edu.cn
```

这个更换的是清华的源，清华的源 5 分钟同步官网一次，建议使用。

- 清华大学  [https://pypi.tuna.tsinghua.edu.cn/simple/](https://yq.aliyun.com/go/articleRenderRedirect?url=https%3A%2F%2Fpypi.tuna.tsinghua.edu.cn%2Fsimple%2F)
- 阿里云  [http://mirrors.aliyun.com/pypi/simple/](http://mirrors.aliyun.com/pypi/simple/)
- 中国科技大学  [https://pypi.mirrors.ustc.edu.cn/simple/](https://yq.aliyun.com/go/articleRenderRedirect?url=https%3A%2F%2Fpypi.mirrors.ustc.edu.cn%2Fsimple%2F)
- 豆瓣(douban) [http://pypi.douban.com/simple/](https://yq.aliyun.com/go/articleRenderRedirect?url=http%3A%2F%2Fpypi.douban.com%2Fsimple%2F)
- 中国科学技术大学  [http://pypi.mirrors.ustc.edu.cn/simple/](https://yq.aliyun.com/go/articleRenderRedirect?url=http%3A%2F%2Fpypi.mirrors.ustc.edu.cn%2Fsimple%2F)

按下`ESC`切换到命令行模式，输入`:wq`保存离开。

来自 <[https://yq.aliyun.com/articles/629867?spm=a2c4e.11155472.0.0.45c05de2Uez9bt](https://yq.aliyun.com/articles/629867?spm=a2c4e.11155472.0.0.45c05de2Uez9bt)>

---

## 配置 SSH 服务

1.最好首先更新软件源，然后卸载重装一遍 ssh 服务，这里不是很确定是不是自带 ssh 服务有没有问题

sudo apt-get remove openssh-server sudo apt-get install openssh-server

2.编辑 sshd_config 文件，修改几处配置才能正常使用用户名/密码的方式连接

```bash
sudo vi /etc/ssh/sshd_config

Port 22 #默认即可，如果有端口占用可以自己修改
PasswordAuthentication yes # 允许用户名密码方式登录
```

3.修改完之后重启`ssh`服务

```bash
sudo service ssh restart
```
