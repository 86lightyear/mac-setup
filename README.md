## Mac-setup 🍇
[![Build Status](https://api.travis-ci.com/jsycdut/mac-setup.svg?branch=master)](https://travis-ci.com/jsycdut/mac-setup)

目前项目正在改动中，大家不要使用啊（逃


## TODO

1. 更新软件包为用户手动选择
2. 安装的时候去除复杂的内容输出，疯狂输出真的看着不舒服
3. 网络环境不再打算配置SS代理，而是改用国内的源以提升速度

## Introduction 🙉
🐼 If you are a non-chinese speaker, please check out the en-branch of this project

这是一个为你的Mac自动安装软件的Bash脚本，让你抽出时间喝咖啡而不是把时间花费在下载和安装你需要的软件。

## NOTICE
这里有一个非常重要的前提，那就是网络配置以及系统版本，一定要配置好终端代理，因为国内的homebrew网络环境很差，所以科学上网，尤其是为终端配置代理是特别需要的，推荐shadowsocks，这里在本仓库下的resources文件夹下放置了ShadowsocksX-NG 1.8.2，应该先利用这个来配置好科学上网（需要相关的shadowsocks账号，这个如果没有自建服务器，可以使用我的[安装脚本](https://github.com/jsycdut/shadowsocks-install-scripts)自己搭建shadowsocks服务端，或者去网上自己找一找免费账号，分享这个的也很多，如果没法配置好代理，建议还是不要用这个安装脚本了，因为真的会很龟速），然后在终端执行`export ALL_PROXY=socks5://127.0.0.1:1086`，（一般ShadowsocksX-NG 1.8.2的socks5代理地址就是socks5://127.0.0.1:1086，这个要根据实际的情况来，或者可以安装shadowsocks-libev配置好之后进行代理设置），网络环境是很重要的，要不然很可能脚本使用过程就是龟速甚至无法安装成功。

另外，关于图形化的APP，比如iterm2，一般最新的版本需要Mac OS X 10.12，这其实都还好，因为homebrew会自动处理相关依赖，当系统版本不满足的时候，就不会对该条目进行安装。

除此之外，在安装某些图形化APP的时候，可能需要用户输入密码才能进行，比如wireshark，如果想要完全自动安装，可能需要修改一下安装脚本，将wireshark剔除出去。

最后，在排除了网络的缓慢因素之外，对命令行工具的安装，homebrew是采用编译源码安装的方式进行的，所以会有点慢，因为操作步骤比较繁杂，需要耐心等待，比如真的去喝杯咖啡什么的。

## Why 🙈
每一次我的Mac使用了半年左右，我就会重新安装一遍系统，因为有些东西累积的太多了，需要清理一下，一般我都是备份文件之后，就直接重新在线安装OS X，但是面对干干净净的系统，我总是需要花上小半天的时间来配置我需要的工作环境，比如安装一下vim，配置一下vimrc，去下载jetbrains公司的IDE用于开发，安装一下MySQL这种常见的数据库等，一开始觉得配置挺有意思，还很有成就感，但是做了两次之后就再也不想这么干了，因为新鲜感早已过去，剩下的只是消耗时间的重复，所以我写了这么个脚本来自动安装一些常用的软件。

## How 🙊
1. 克隆本仓库到您的电脑

2. 进入仓库目录，要执行安装，只需要执行`./install.sh`即可。如果提示此脚本没有运行权限，请执行`chmod u+x install.sh`

## 软件清单 🐕
软件清单分两个，`brew_cask_app_list`为GUI软件包，`brew_cli_app_list`为CLI软件包，这二者都是数组。

## 如何添加自定义的软件包 🔥
这很简单，只需要改写`install_app_for_mac.sh`里面的`brew_cask_app_list`和`brew_cli_app_list`这两个数组即可，你可以删除里面你不想要的软件包，你也可以在对应的数组里面加入你想要的软件包，注意分清GUI和CLI即可。

目前已经列入安装清单的软件包如下

| 名称 | 类别 | 介绍 |
| :--: | :--: | :--: |
| IINA |  GUI | 视频播放 |
|alfred|  GUI | spotlight的替代品|
|iterm2|  GUI | 优秀的Mac终端工具|
| QQ   |  GUI | 腾讯QQ|
| typora|  GUI | markdown编辑预览工具|
| sogouinput | GUI | 搜狗输入法|
|google-chrome| GUI |谷歌浏览器|
|firefox| GUI|火狐浏览器|
|wireshark| GUI |网络抓包工具|
|etcher| GUI | U盘烧录工具|
|telegram-desktop|GUI|聊天工具Telegram|
|intellij-idea|GUI|jetbrains, Java IDE|
|pycharm|GUI|jetbrains，Python IDE|
|clion|GUI|jetbrains, C && C++  IDE|
|datagraip|GUI|jetbrains, Database IDE|
|webstorm|GUI|jetbrains, Web front end IDE|
|mysql|CLI|MySQL数据库|
|wget|GLI|网络下载器|
|aria2|CLI|网络下载器|
|tree|CLI|图形化显示目录内容|


## 使用效果 🐈
> 安装homebrew，`./install_app_for_mac.sh`

![](https://raw.githubusercontent.com/jsycdut/photos/master/mac-setup/install-homebrew.png)
![](https://raw.githubusercontent.com/jsycdut/photos/master/mac-setup/install-app.png)

## Travis CI✨
我在仓库里面加入了Travis的支持，就目前Travis的报告来看，这个脚本是大体成功的，为什么是大体呢，因为可以在报告里面看到Intellij IDEA和Wireshark两个显示error，具体失败原因是下载镜像失败，这可能和网络问题有关，但是其他的软件包都正常安装了，至于失败的俩嘛，就手动安装吧。祝大家使用愉快！


