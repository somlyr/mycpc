#### xrdp使用说明
* ubuntu下使用
> 安装xrdp
```
sudo apt-get install xrdp
```
> 调整xrdp启动设置，在/etc/xrdp/startwm.sh文件中增加如下设置
```
unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
```
