openwrt
=======
tl-703n flash openwrt
#下载固件
http://downloads.openwrt.org/snapshots/trunk/ar71xx/ 
#下载这个目录内所有的文件，防止以后没有办法升级 修改/etc/opkg.conf 文件中的地址为：http://ip/packages
http://downloads.openwrt.org/snapshots/trunk/ar71xx/packages/

#使用HFS网络文件服务器也非常方便。使用putty登入后，首先把固件下载到/tmp文件夹下：
wget http://192.168.1.234:8080/openwrt-ar71xx-generic-tl-wr703n-v1-squashfs-sysupgrade.bin
#然后刷新即可,注意，这个过程中不能断电，不能拔掉网线
sysupgrade -n openwrt-ar71xx-generic-tl-wr703n-v1-squashfs-sysupgrade.bin

telnet 192.168.1.1 23  # telnet登陆
passwd root # 修改密码

#安装LUCI，支持中文界面
#使用putty登陆路由后，通过如下命令安装LUCI与中文包：
opkg update // 更新软件列表
opkg list-installed // 查看已安装软件
opkg install luci // 安装LUCI
opkg install luci-i18n-chinese // 支持中文
#即可完成LUCI的安装。
#输入以下命令开启支持web服务的uhttpd，并设置其为自启动：
/etc/init.d/uhttpd enable # 开机自启动
/etc/init.d/uhttpd start  # 启动uhttpd


#知识：
http://see.sl088.com/wiki/Openwrt_USB%E5%90%AF%E5%8A%A8
