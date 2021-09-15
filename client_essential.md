#### Spice client
* linux下通过API获取访问配置，使用oVirt Remote-viewer登录guest桌面
> 通过API接口获取spice.vv，有访问时效，通过脚本连接配置获取及remote-viewer执行，可解决时效问题
```
# ./spice_example_client.sh
```

* 客户端访问窗口resize问题
> 确定在guest VM中spice-vdagent已正确安装并运行，确认guest中video memory配置是否足够支撑当前的窗口分辨率及尺寸；修改video memory配置需要重启VM；

* 开源项目参考(virt-viewer wrapper)
  * [c4pve tools](https://www.cv4pve-tools.com/)    *[C#]*
  * [spice quickconnect](https://github.com/Elbandi/proxmox-spice-quickconnect)    *[Golang]*
  * [cnovirt](https://github.com/cnovirt/opencc-ovirt-pro-win)    *[NodeJS]*
  * [remote-desktop-client source](https://github.com/iiordanov/remote-desktop-clients)
  * [remote-desktop-client opaque apk](https://napkforpc.com/apk/com.undatech.opaque/)

#### windows下virt-viewer 10.0客户端spice无声音问题
> * 下载vv 7/9/10版本
>   * 下载[virt-viewer 7](https://virt-manager.org/download/sources/virt-viewer/virt-viewer-x64-7.0.msi)
>   * 下载[virt-viewer 9](https://releases.pagure.org/virt-viewer/virt-viewer-x64-9.0-1.1.msi)
>   * 下载[virt-viewer 10](https://virt-manager.org/download/)
> * 解压缩 vv 7/9 msi获取3个文件
>
```
VirtViewer v7.0-256\lib\gstreamer-1.0\libgstdirectsoundsink.dll
VirtViewer v9.0-257\lib\gstreamer-1.0\libgstcoreelements.dll
VirtViewer v9.0-257\lib\gstreamer-1.0\libgstcoretracers.dll
```
> * 安装vv10，并用vv7/9中的3个文件替换vv10中对应文件

#### PVE API
* 通过PVE Rest API定制客户端(+virtviewer)
  * [PVE API wiki](https://pve.proxmox.com/wiki/Proxmox_VE_API)
  * [PVE API online](https://pve.proxmox.com/pve-docs/api-viewer/#/nodes/{node}/qemu/{vmid}/spiceproxy)

#### USB Redirect
* 使用Windows客户端上的USB设备
> 如果需要把 Windows 客户端系统上的 USB 设备重定向到虚拟机上，则需要在 Windows 客户端上安装 usbdk。您需要确定所使用的 usbdk 版本与客户端系统的系统相匹配。例如，64 位版的 usbdk 必须安装在 64 位的 Windows 系统上。
>
> FYI：*确定Spice虚机的USB支持选项被设置为Native*
