#### Windows虚机设置
* [最佳实践参考-just for win7](https://pve.proxmox.com/wiki/Windows_7_guest_best_practices)
* [Win10 安装Virtual IO驱动](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers)
* [Fedora VirtIO Driver 源站下载](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/)

> 主要准备活动
* 下载最新稳定版 For Win8-12[VirtIO Dirver virtio-win-0.1.196-1](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/virtio-win-0.1.196-1/virtio-win-0.1.196.iso)
* VM显示选择spice，同时显存设置128M(大一些)
* 选择VM创建ISO时，除windows ISO外，再额外创建一个CDROM驱动器并添加[windows virtio iso](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)
* 在VM安装过程中如出现无法发现Disk的情况，可能和所选的磁盘驱动待安装有关，可在安装界面中选择所需的VirtIO驱动安装解决

> VM安装成功后，可手工安装VirtIO驱动、QXL Agent
* Open the Windows Explorer and navigate to the CD-ROM drive.
* Simply execute (double-click on) **virtio-win-gt-x64**
* Follow its instructions.
* (Optional) use the **virtio-win-guest-tools** wizard to install the QEMU Guest Agent and the SPICE agent for an improved remote-viewer experience.
* Reboot VM

#### Window10虚机激活
> 启动regedit编辑注册表选项,添加SkipRearm选项
```
在HKEY_LOCAL_MACHINE下设置DWord键值:SkipRearm=0
```
> 通过KMS激活系统，以管理员身份运行CMD
```
win10专业版用户请依次输入：
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms kms.03k.org
slmgr /ato

win10企业版用户请依次输入：
slmgr /ipk NPPR9-FWDCX-D2C8J-H872K-2YT43
slmgr /skms kms.03k.org
slmgr /ato

win10家庭版用户依次输入：
slmgr /ipk TX9XD-98N7V-6WMQ6-BX7FG-H8Q99
slmgr /skms kms.03k.org
slmgr /ato
```
