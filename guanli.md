### OSPF

OSPF是IETF组织开发的一个基于链路状态的内部网关协议，广泛应用于接入网和城域网中。目前针对IPv4协议使用OSPF Version 2。在OSPF出现前，网络上广泛使用RIP（Routing Information Protocol）作为内部网关协议。由于RIP是基于距离矢量算法的路由协议，存在着收敛慢、路由环路、可扩展性差等问题，所以逐渐被OSPF取代

采用最短路径SPF（Shortest Path First）算法。通过链路状态通告LSA（Link State Advertisement）描述网络拓扑，依据网络拓扑生成一棵最短路径树SPT（Shortest Path Tree），计算出到网络中所有目的地的最短路径，进行路由信息的交换。收敛速度快，小于1s。应用于规模适中的网络中，最多可支持几百台ME设备。例如，中小型企业网络。

### 系统文件

设备软件主要包括linux程序和app文件。设备上电后，先运行linux程序，初始化硬件并显示设备的硬件参数，然后运行app文件；app文件一方面提供对硬件的驱动和适配功能，另一方面实现了业务特性。linux程序与app文件是设备启动、运行的必备软件，为整个设备提供支撑、管理、业务等功能。

设备提供app、sdn、fpga、全量flash文件四种文件包：

![Static Badge](https://img.shields.io/badge/APP-purple),设备OTP5600主要的运行程序文件，一般情况下升级该文件，文件大小11M左右；

![Static Badge](https://img.shields.io/badge/SDN-purple),运行netconf管理协议的yang文件，主要负责设备对接上层的netconf控制器；

![Static Badge](https://img.shields.io/badge/fpga-purple),硬件的驱动文件，和app相匹配运行，最新为V2.22版本；

![Static Badge](https://img.shields.io/badge/FLASH-purple),设备整个全量升级包，包括所有的文件，可以烧录到闪存直接升级，目前分两种，一种是32M的全量升级包，一种是37M的全量升级包，根据主控板卡的硬件差异进行选择烧录升级;

上载SDN文件，~~下载略~~

```
OTP5600-II(config)#upload ftp file /mnt/flash/gwd/sdn/wholePack.bin 132.234.25.21 123 123 dci-sdn.bin
```

上载FPGA文件，~~下载略~~

```
 upload ftp file /mnt/flash/gwd/otp5600.fpga 132.234.25.22 123 123 otp5600.fpga
```

上载FLASH文件，<u>下载不支持</u>

```
 upload ftp flash 132.234.25.22 123 123 flash.bin gpn
```

### 网元开通配置

> Ver_B039网管方式改动！

**5500**

```
interface loopback 1
ip address 132.234.25.22/32
exit
```

```
vlan 10
ip address unnumberd loopback 1
add port 9/1 untagged
exit
```

```
router ospf
  network 132.234.25.22/32 area 0
  default-information originate always			
exit
```

```
vlan 10
ip ospf network point-to-point
exit
```

**5600**

```
interface loopback 1
ip address 132.234.25.26/32
exit
```

```
vlan 10
ip address unnumberd loopback 1
add port 9/1 untagged
exit
```

```
router ospf
  network 132.234.25.23/32 area 0		
exit
```

```
vlan 10
ip ospf network point-to-point
exit
```

```
interface och 1/1
set frequency 191.4
```

### 升级

<strong>网关网元</strong>

目前网管方式需要先串口登录设备，释放9/1-2口到默认VLAN1，然后telnet方式升级。

<strong>非网关网元</strong>

B039以上版本已经支持远程升级，telnet到非网关网元直接download下载文件即可。

### OSPF路由不通排查

OTP5600-GEJD板卡（光放板卡）和OTP5600-WRDY（WSS板卡）目前硬件带OSC模块，根据型号不同，分别带不同数量的千兆OSC模块和百兆OSC模块，具体信息参考市场发布的产品配置表。

<strong>排查OSC模块是否工作正常</strong>


```
interface wdm_osc <slot/1>
show sfp
```

> 说明：OSC模块发光`2dBm`，收光`-30dBm`左右

<strong>查看OSC模块互通协商是否UP</strong>


```
   show port-link
```

> 说明:OSC模块一般是两个互通使用，目前千兆对千兆，百兆对通百兆，默认起来是强制协商；两个OSC模块正常都能协商起来，如果没协商起来，<u>auto enable</u>开启自动协商。
>

<strong>查看OSPF配置信息是否正确</strong>


```
   show running-config ospf 
```

<strong>查看OSPF邻居信息是否正确</strong>


```
   show ip ospf neighbor
```

### FreeSSHd软件使用

- 软件上传工单，需要可登录下载。

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/2023-09-22_153810.png" style="zoom:50%;" />  

图为软件界面，需要设置的项为Users、SSH、Authentication、SFTP四项。

- Users：添加用户名和密码

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/2023-09-22_154252.png" style="zoom:53%;" /> 

- SSH：设置监听ip和端口

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/2023-09-22_154622.png" style="zoom:50%;" /> 

- Authentication：设置密匙key方式，按图设置

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/2023-09-22_160031.png" style="zoom:50%;" />  

- SFTP:    date文件存放路径

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/2023-09-22_155807.png" style="zoom:50%;" /> 

最后点击“`Click here to start it`” 启动server服务器。报错一般是电脑系统服务项开启了，关闭即可。

### NAT管理-升级手册

- 网关网元可直接升级；

  ```
  download ftp app x.x.x.x 76 213546 file_name
  ```

- 针对非网关网元的升级，需要将网关网元当作ftp-server来升级：

1.配置网关网元ftp-server的用户名、密码

```
config ftpserver createuser root
config ftpserver createpassword public

config节点下：show running ftpserver    ##查询配置信息
```

2.升级非网关网元

```
download  ftp file /tmp/OTP5600_V04R20C09B006.bin 192.168.51.166(PCip) 123 123 OTP5600_V04R20C09B006.bin   ## 先将文件下载到网关网元指定目录/tmp下
```

```
download ftp app 133.68.70.219(loopback1 ip) root public OTP5600_V04R20C09B006.bin gpn
```

注意：当/tmp目录下长期未重启设备导致内存占用过多，可进入网关网元shell节点下先查看文件system "ls -l /tmp"，再使用命令删除文件：system "rm /tmp/文件名"



### 电信NAT管理

##### 1. 原理

如果运营商只提供一个IP地址，而每台网元都需要至少一个IP地址进行管理，为了解决地址不足的问题，网关网元就需要启动NAT功能，网关网元配置一个公网IP地址、一个私有IP地址，非网关网元配置私网IP地址

在进行NAT转换时，“内部非网关网元的私网IP +端口号”同“网关网元公网IP +端口号”是一对一静态绑定的，多个私网IP可以映射为同一个公网IP地址的不同的端口号，所以一个公网IP可以被多个私网IP地址使用。

##### 2. 方式

- 开启NAT功能，并添加私网IP映射。

  <font color=red>私网IP+端口号830映射到公网IP+20000到20199端口</font>

```
config netagent
config netagentmgt_ip public 132.234.25.22                          ## 网关网元-公ip
config netagentmgt_ip private 192.168.7.10                          ## 网管网元-私ip
config netagentmgt innerip 192.168.7.11 port 20000 mapport 830      ## 非网关网元私ip
config netagentmgt innerip 192.168.7.12 port 20001 mapport 830      
config netagentmgt innerip 192.168.7.13 port 20002 mapport 830
config netagentmgt innerip 192.168.7.14 port 20003 mapport 830
config netagentmgt innerip 192.168.7.15 port 20004 mapport 830
config netagentmgt innerip 192.168.7.16 port 20005 mapport 830
config netagentmgt innerip 192.168.7.17 port 20006 mapport 830
config netagentmgt innerip 192.168.7.18 port 20007 mapport 830
config netagentmgt innerip 192.168.7.19 port 20008 mapport 830
config netagentmgt innerip 192.168.7.20 port 20009 mapport 830
config netagentmgt enable
exit
```

##### 3. 配置默认路由

```
ip route  132.252.0.0/16   132.234.25.1     ##  目标路由：服务器ip；下一跳路由：网关ip
```

##### 4. 查看配置是否生效

```
show running-config netagent
save
```

##### 5. 如果配置错误，需要

```
erase config-file
eboot
```

