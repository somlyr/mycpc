#### [官方文档](https://docs.vyos.io/en/equuleus/)

#### 配置用户
> 设置用户名/密码
```
configure
set system login user **username** authentication plaintext-password **password**
commit
save
exit
```
#### 配置接口地址
> net0连接公网，net1连接内网
```
set interface ethernet eth0 address 192.168.168.1/24
set interface ethernet eth1 address 10.100.100.1/24
commit
save
```
#### 配置默认网关
> 通过静态路由配置默认网关
```
configure
set protocols static route 0.0.0.0/0 next-hop 192.168.168.254 distance 1
commit
save
```
#### 配置DHCP服务
> 指定DHCP网关
```
set service dhcp-server shared-network-name mycpc-dhcp-net subnet 10.100.100.0/24 default-router 10.100.100.1
commit
save
```
> 指定DHCP DNS
```
set service dhcp-server shared-network-name mycpc-dhcp-net subnet 10.100.100.0/24 dns-server 10.100.100.1
commit
save
```
> 指定DHCP租期
```
set service dhcp-server shared-network-name mycpc-dhcp-net subnet 10.100.100.0/24 lease 3600
commit
save
```
> 指定DHCP地址池
```
set service dhcp-server shared-network-name mycpc-dhcp-net subnet subnet 10.100.100.0/24 range include start 10.100.100.10
set service dhcp-server shared-network-name mycpc-dhcp-net subnet subnet 10.100.100.0/24 range include stop 10.100.100.254
commit
save
```
### 配置DNS服务
> 配置系统DNS服务器地址
```
set system name-server 114.114.114.114
commit
save
```
> 配置DNS转发，可配置使用三种模式
* 使用系统DNS转发
```
set service dns forwarding system
commit
save
```
* 使用指定DNS转发
```
set service dns forwarding name-server 114.114.114.114
commit
save
```
* 当internet口为DHCP方式时，也可通过DHCP获取
```
set service dns forwarding dhcp eth0
commit
save
```
>配置DNS监听地址
```
set service dns forwarding listen-address 10.100.100.1
commit
save
```
>配置允许访问DNS服务的内网地址
```
set service dns forwarding allow-from 10.100.100.0/24
commit
save
```
#### 配置NAT
> 使用internet侧接口地址作为地址池
```
set nat source rule 1 desciption mycpc-nat-used-ifaddr
set nat source rule 1 outbound-interface eth0
set nat source rule 1 source address 10.100.100.0/24
set nat source rule 1 translation address masquerade
commit
save
```
