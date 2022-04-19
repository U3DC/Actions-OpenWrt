
## 说明

> 本项目旨在使用Github的Actions功能实现OpenWrt的云编译，根本上解决本地编译的网络、环境配置问题。
> 同时大家也能通过配置来增、减插件，打造属于自己的OpenWrt固件，拒绝各种广告固件。
> 项目基于Lean的LEDE进行编译。
---

1. 自动化用的是P3TERX项目，项目地址：https://github.com/kenzok8/openwrt-packages

  编译的OpenWrt源项目是Lean的LEDE，项目地址：https://github.com/coolsnowwolf/lede

2. 云编译项目主要需修改俩个地方：
* diy-part1.sh里面添加feeds源，可以使用 https://github.com/kenzok8/openwrt-packages
* 另一个是.config文件，可以本地自己通过make menuconfig来保存生成或者直接用别人的。

3. Windows环境下可以简单使用WSL（Windows Subsystem for Linux）来搭建Ubuntu环境（建议20版本以上），此环境的作用主要是用来配置config文件，然后将文件上传到github。

4. 默认登陆IP 192.168.1.1 密码 password

----
## 附录：本地编译常见问题
* fatal: unable to access 'https://github.com/coolsnowwolf/lede/': gnutls_handshake() failed: The TLS connection was non-properly terminated.

解决方式：

> git config --global http.sslVerify "false"

---------------------------

* error: RPC failed; curl 18 transfer closed with outstanding read data remaining

解决方案：

> git config --global http.postBuffer 524288000

-------------------------------
	
* Can't exec "make": No such file or directory at ./scripts/feeds line 22.

解决方案：

> sudo apt-get install build-essential subversion libncurses5-dev zlib1g-dev sudo apt-get install gawk gcc-multilib flex git-core gettext libssl-dev  

--------------------------------

* Build dependency: Please install 'unzip'

解决方案：

> sudo apt install unzip

------------------------

* fatal: unable to access 'https://git.openwrt.org/feed/telephony.git/': server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none

解决方案：

> export GIT_SSL_NO_VERIFY=1

或者 

> sudo apt-get update
> sudo apt-get install ca-certificates

-----------------

* <stdin>:1:10: fatal error: libelf.h: No such file or directory

解决方案：
  
> sudo apt-get install libelf-dev

--------------------

* fatal error: gelf.h: No such file or directory
  
解决方案：

> sudo apt-get install libelf-dev
