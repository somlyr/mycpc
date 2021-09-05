#### Spice client
* linux下通过API获取访问配置，使用oVirt Remote-viewer登录guest桌面
> 通过API接口获取spice.vv，有访问时效，通过脚本连接配置获取及remote-viewer执行，可解决时效问题
```
# ./spice_example_client.sh
```

* 客户端访问窗口resize问题
> 确定在guest VM中spice-vdagent已正确安装并运行，确认guest中video memory配置是否足够支撑当前的窗口分辨率及尺寸；修改video memory配置需要重启VM；

#### [c4pve tools](https://www.cv4pve-tools.com/)
