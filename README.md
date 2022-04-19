
## 说明

使用Github的Actions功能来实现Openwrt的云编译。可以根本上解决网络、环境配置问题。

1.此项目Fork的是P3TERX项目，项目地址：https://github.com/kenzok8/openwrt-packages

2.需要修改俩个地方：
* diy-part1.sh里面添加feeds源，可以使用 https://github.com/kenzok8/small-package
* 另一个是.config文件，可以本地自己通过make menuconfig来保存生成或者直接用别人的。

3.windows环境下可以简单使用WSL（Windows Subsystem for Linux）来搭建Ubuntu环境。
