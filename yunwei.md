# DCI运维相关

波分排故实质是光经过光学器件后的质量优劣性，所以排查涉及光收、损耗、色散等各种影响光的因素和参数。

OTN光层影响因素：非线性（功率过高）、衰耗、OSNR信噪比。

功率控制原理：光功足够强的前提下，不引起非线性效应。

### 光器件衰耗

| **AWG** |         TX≤6dB         |          RX64dB          |
| :-----: | :--------------------: | :----------------------: |
| **OLP** | **TX≤4dB**(分光器衰减) | **RX≤1.5dB**(光开关衰减) |



### 单波最佳入纤光功率<font face="仿宋" size=2>(工程经验值)</font>

|   400G-16QAM   |    3dBm    |
| :------------: | :--------: |
| **200G-16QAM** |  **1dBm**  |
| **200G-QPSK**  | **2.5dBm** |

### 调测<font face="仿宋" size=2>（仅记录多波光功率调测）</font>

<div align="center"><img src="https://s2.loli.net/2023/09/21/JlYmkqAoH6LQBrs.png"  style="zoom:85%;" /></div>

顾名思义，合波光功率就是单波功率相加得到的总功率，但整个链路光功单位为dBm，不能相加，故有如下计算功率：

<center>$$dBm=10\lg^\frac{Power}{1mW}$$</center>

<center>$$mW=10\lg^\frac{dBm}{10}$$</center>



单波：1--->2 ：0dBm-5<font color=red>dB</font>=-5dBm   

&emsp;2--->3：-5dBm-2<font color=red>dB</font>=-7dBm 

&emsp;3--->4：-7dBm+10<font color=red>dB</font>(增益补偿10dB)=3dBm

&emsp;4--->5：3dBm-12<font color=red>dB</font>(线路损耗)=-9dBm

&emsp;5--->6：-9dBm+12<font color=red>dB</font>(端放补偿)=3dBm

&emsp;6--->7： 3dBm-5<font color=red>dB</font>=-2dBm   <font color=white>----</font> 故，cfp收-2dBm

推广到多波：

<center>$${\text{多波}}={\text{单波}}+10\lg^n(n{\text{为波道数目}})$$</center>

### OLP保护板<font face="仿宋" size=3>（暂不支持双端倒换）</font>

> <font face="仿宋" >双向倒换需要使用APS信令通道进行协议报文交互，APS 信令通道可以使用ODUk开销中的APS/PCC字段来实现，也可以使用光监控通道，通过IP数据包的方式来实现。</font>

倒换方式：绝对倒换、相对倒换

返回方式：返回式、非返回式

等待恢复时间WTR：防止抖动引起的频繁倒换，业务切回工作信道之前需要保证一个延迟的考察时间

切换延时：主路倒换到备路

回切延时：备用回切到主用前需要等待的一个时间

自动模式延迟：从手动切换到自动时，自动模式功能生效的延时时间

```
am pri_switch_threshold 5 -18.00          ##主用光功率门限值
am sec_switch_threshold 5 -18.00          ##备用光功率门限值
```

### 一些常用命令汇总

```
interface och  <slot/1>                  ## 进入CFP模块
set frequency 191.4                      ##  CFP模块频率设置
set  powerconfig -2.00                   ## 设置CFP模块发光
set channel spacing [100GHz|50GHz]       ## 设置步长/频率
set line loopback none/inner/outer       ## 设置线路测环回                               
```

```
ntwk-type [16qam|8qam|qpsk]              ## 设置线路测码型转换
mode [otuc1|otuc2|otuc4]                 ## 配置线路测业务模式
interface ethernet <slot/1>              ## 进入客户侧端口
mode [10ge_lan|10ge_wan|stm64|otu2|100g|100g-nonfec|otu4]    ## 配置10ge业务模式
loopback mode none/inner/outer           ## 配置客户侧环回
```

- 进入备用主控命令

```
grosadvdebug
swtich 11
grosadvdebug
slave-enable
enable    
```

















# OTN运维相关

### 改制

###### ***`EOPC126`改制为`EOSC126`**

```
GPN7600(config)#grosadvdebug
GPN7600(DEBUG_H)> board-eeprom 13
  date      Specify manufacture date 
  ext-info  Extended Information 
  sn        Specify board serial number 
  type      Specify board type 
  version   Specify board hardware version 
  <cr>      Just press enter to execute command!

GPN7600(DEBUG_H)> board-eeprom 13 type eosc126   
reboot 13    //复位对应槽位生效
```

**`8AT2`改制为** **`X`**

```
ext-info2针对8AT2板卡         type针对8ge板卡
```

```linux
grosadvdebug
> board-eeprom <slot> ext-info2 mode=<date>           board-eeprom <slot> type  <name>
**mode=0,   8AT2**      //加载760b.fpga//                **eos-8ge, <name>=8ge-32 ** 
**mode=1,   4XT2**
**mode=2,   4GT1**
**mode=3,   8AST2** 
**mode=4,   2XT2** 
**mode=5,   2GT1** 
**mode=6，  T10X**
**mode=8,   8AT2SDH**    //16个vp_SDH//
**mode=27,  8AT2-B**     //8AT2-B板卡因为缺少芯片，不能改制为8AT2板卡// //8AT2加载760b.fpga// //V2//
V3版本：
**mode=20， OODX(8AT2/8AT2-B)**
**mode=6，  T10X**
```



### 更改

***更改`NEID`和系统`MAC`***

```
grosadvdebug 
>show netid 
>config netid 0x[16进制的数据] 
>config sysmac 0000.1111.2222           **一般不随便更改设备MAC地址** 
reboot重启生
```

***更改设备`Loopback10`地址***

```linux
插入8at2设备会有一个Loopback10的环回地址，133网段

第一种方法：
GPN7600(config)# interface  loopback 10
GPN7600(config)#ip address xxx.xxx.xxx.xxx/24
第二种方法：
GPN7600(config)# dcn ip xxx.xxx.xxx.xxx/24        // 掩码按照规划 //
```

> 优选第二种方式，原因可能影响ospf  id号。



### 启、闭

***启、闭U/D口物理状态***

```
GPN7600(config)#int eth 17/<1-2>                
GPN7600(if-eth17/3)#shutdown                ## 关闭端口
GPN7600(if-eth17/3)#undo shutdown           ## 开启端口 

GPN7600(if-eth17/3)#int eth 17/<3-10>       ## <3-10>对应E1/1-8
GPN7600(if-eth17/3)#shutdown
GPN7600(if-eth17/3)#undo shutdown
```

***启、闭8GE物理口状态***

```
GPN7600(config)#int eth 1/1 
GPN7600(if-eth1/1)#shutdown                       ## 进入端口，shutdown
或者
GPN7600(config-msap)#ioctl eth disable 1/1        ## msap节点下，关闭。任选其一！
```

***启、闭激光器状态***

```linux
端口下port laser off/on                             ## shutdown仅关闭端口，未关闭激光器
```

### 主登录备

***设备底层，主用主控登陆备用主控方法***

```
config# grosadvdebug                           进入debug节点 
debug > switch 2                               进入2槽的备用主控 
slot2 > grosadvdebug                              
debug> slave-config enable                     启用cofig节点 
debug> exit 
slot2> enable 
slot2(config)#
```

### ***团体字   `查询` `更改`***

```
GPN7600(config)# show snmp community-string        //## 查询团体字
  Read-only Community String is :[public] 
  Read-write Community String is :[private]
------------------------------------------------------------------------------
config snmp community readonly gwtt@123       //这个是读团体    //##修改团体字 
config snmp community readwrite gwtt@123      //这个是写团体
```

> **修改snmp需对应修改‘网管’和‘底层’两处，否则上载不生效**

### V2升级脚本

```
GPN7600升级步骤

第一步：保存
GPN7600(config)#save

第二步：备份
upload ftp config 192.168.9.99 gwglwe2022 GWadmin@123  config.txt                                 
upload ftp file /flash/sys/db.bin 192.168.9.99 gwglwe2022 GWadmin@123  db.bin                     
upload ftp file /flash/sys/slotconfig.bin 192.168.9.99 76 213546 slotconfig.bin      

第三步：删除主用主控文件，释放空间
GPN7600(config)#dosfs
GPN7600(host:)#cd /flash/sys
GPN7600(/flash/sys)#rm app_code_backup.bin
GPN7600(/flash/sys)#rm app_code.bin
GPN7600(/flash/sys)#ll 					//L是小写字母，查询剩余空间，R13B240SP15或者SP16要求大于15M 方可以升级！

第四步：删除备用主控文件，释放空间			//没有备用主控，请忽略此步骤
GPN7600(config)#grosadvdebug
GPN7600(DEBUG_H)>switch 18
Slot18>grosadvdebug
Slot18(DEBUG_H)> slave-config en
Slot18(DEBUG_H)> slave-config enable
Slot18(DEBUG_H)> exit
Slot18>enable
Slot18(config)#dosfs
Slot18(host:)#cd /flash/sys
Slot18(/flash/sys)#rm app_code_backup.bin
Slot18(/flash/sys)#rm app_code.bin
Slot18(/flash/sys)#ll
删除完成以后，使用 exit 命令多退出几次就到原始config节点了，然后继续下一步。

第五步：下载版本，开始升级

download ftp app 192.168.11.12 gwglwe2022 GWadmin@123 GPN7600_V02R19C17B013.bin gpn                          
download ftp file /yaffs/sys/760s.fpga 192.168.11.12 gwglwe2022 GWadmin@123  otn_a_760s_20201102.fpga                8AT2板卡 

download ftp file /yaffs/sys/760b.fpga 192.168.11.12 gwglwe2022 GWadmin@123  otn_a_760b_20211129.fpga                8AT2板卡


reboot   

download ftp file /yaffs/sys/760c.fpga 192.168.11.12 gwglwe2022 GWadmin@123 otn_a_760c_20200414.fpga                2XT2板卡

download ftp file /yaffs/sys/760e.fpga 192.168.11.12 gwglwe2022 GWadmin@123  otn_a_760e_20200922.fpga               T10X板卡


下载FPGA大包
download ftp fpga 192.168.11.12 gwglwe2022 GWadmin@123  fpga_code_1058_SP15.bin other                        

下载NMS文件
download ftp fpga 192.168.11.12 root passw  GPN7600-NMS-V1_FPGA_v1.1.14.fpga master             

下载SW文件
download ftp fpga 192.168.11.12 gwglwe2022 GWadmin@123  GPN7600_SW_A_PTN_oam_v0323_20190411.fpga sw              

下载SYSfile文件
download ftp sysfile 192.168.11.12 gwglwe2022 GWadmin@123 sysfile_gwd_V02R02B043_GPN7600_OTN_V2R3.bin        

第六步：重启设备
GPN7600(config)#reboot

第七步：检查是否下载成功

GPN7600(config)#show version				//检查APP版本是否下载陈工
ProductOS Version V02R18C02B020 (Build on 13:27:19 Aug 30 2018)

GPN7600(config)#grosadvdebug
GPN7600(DEBUG_H)>show fpga				//检查FPGA版本
  fpga_code.bin: 1.0.5.4				//大版本
    sp version: SP7					//小版本


电路平面升级，没有特别注意事项，基本操作升级即可！
```

### boot升级

1. GPN7600(config)# reboot              ##重启
2. ctrl＋c                          ## 进入boot>界面

```
showip          ## 显示ip地址 
showmac         ## 显示MAC地址 
setip           ## 设置ip
**********************************
注：U口和D口此时是无效的，也无法使用*
********************************** 	
```

```
setdownflag 3   ## 设备下载APP文件的类型 
download "tiger",192.168.33.100,"11","22","GPN7600_V02R19C17B013.bin"      ## 必须为tiger，其他文件名不行 
download "tiger",192.168.33.100,"11","22","GPN7600_SW_A_PTN_oam_v0323_20190411.fpga"
```

> [!note]
>
> IP地址为自己电脑的IP地址，123 和123 是用户名密码,
>
> V1R13B240SP15.bin 则是自己需要下载的相应文件名称 。

```
GPN7600(config)#download ftp boot 192.168.30.7 test 111111 bootrom405-3.0.2.bin all   ## 实际未同步到SW 
GPN7600(config)#sync-file bootrom all             ## 手动同步boot文件到备用NMS板卡和SW板卡
```

> [!note]
>
> 注意：目前软件版本同步到SW的boot文件实际未同步，需要手动将该boot文件重新同步到sw板卡。下载boot文件到NMS板卡，系统不会自动将boot文件同步到备用NMS及SW板卡，需要使用命令完成同步。

### V3升级脚本

- ##### app

```
download ftp app 10.10.10.172 111 111 GPN7600_V03R21C01B073SP01.bin gpn
```

- ##### NMS

```
download ftp fpga 10.10.10.172 111 111 GPN7600-NMS-V1_FPGA_v1.1.15.fpga master
```

- ##### Other

```
download ftp fpga 10.10.10.172 111 111 fpga_code_1058_SP16.bin other
```

- ##### UXC

```
download ftp file /yaffs/sys/uxc_a.fpga 10.10.10.172 111 111 UXC-20220403.fpga 
download ftp file /yaffs/sys/7610.fpga 10.10.10.172 111 111 OTN_CM_7610-20220323.fpga 
download ftp file /yaffs/sys/7616.fpga 10.10.10.172 111 111 OTN_CM_7616-20211217.fpga 
download ftp file /yaffs/sys/7616c.fpga 10.10.10.172 111 111 OTN_CM_7616C_20211201.fpga
```

- ##### sysfile

```
download ftp sysfile 10.10.10.172 111 111 sysfile_gwd_V02R02B044_GPN7600_V3R1_7U.bin
```

### MySQL数据库

[![Static Badge](https://img.shields.io/badge/MySQL%E6%95%B0%E6%8D%AE%E5%BA%93-html%E6%9F%A5%E7%9C%8B-blue)](https://version-1301999062.cos.ap-beijing.myqcloud.com/MySQL%E6%95%B0%E6%8D%AE%E5%BA%93.html)

### Win 开启FTP

[![Static Badge](https://img.shields.io/badge/Win%20%E5%BC%80%E5%90%AFFTP-html%E6%9F%A5%E7%9C%8B-blue)](https://version-1301999062.cos.ap-beijing.myqcloud.com/Win%E5%BC%80%E5%90%AFFTP.html)

<img src="https://version-1301999062.cos.ap-beijing.myqcloud.com/ftp.png"/>
