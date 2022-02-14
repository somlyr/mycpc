#### [编译环境](https://github.com/albfan/miraclecast/wiki/Building)
----

#### 演示环境准备
* 从系统的Network Manage中摘除实验所需的无线端口(wlan0)
> 
**方法1:**
```
nmcli device set wlan0 managed no
```
**方法2:**
```
sudo systemctl stop NetworkManage.service
```
> 
* 停止系统已启用的wpa服务
```
sudo systemctl stop wpa_supplicant.service
```
> 
* 检查系统服务，原系统的wpa服务已停止
```
sudo ps -aux|grep wpa
```
----

#### 启动miracast sink服务
>
* 启动miracle-wifid
```
sudo miracle-wifid -i wlan0 --log-level trace
```

> 
* 启动miracle-sinkctl
```
sudo miracle-sinkctl --log-level trace

miracle-sink# run 3
```

#### 使用手机的miracast投屏
*不同手机的投屏软件命名不同，例如：小米:投屏，三星:smartview，使用方法大致相同*
* **步骤1**: 启动软件，会自动搜索miracast sink端
* **步骤2**: 点击连接搜索到的sink端

