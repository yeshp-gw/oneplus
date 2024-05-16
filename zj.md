###### 关于出差地市的一些总结

[直达广州](#guangzhou)

[直达郑州](#zz)

[直达南通](#nt)

[直达泰州](#tz)

### 三门峡

[三门峡，这是地方冬天可以观赏美丽的天鹅，本次出差无缘。](https://baike.baidu.com/item/三门峡市天鹅湖城市湿地公园/9988908)


格林波分设备三门峡放置于`新大楼（5楼）`和`六峰路局（3楼）`，业务类型`point to point`，现场配置为两光一电，4块PDSD，组网如下：

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/6bf52mi7AJedrjn.png" alt="image.png" style="zoom: 200%;" />

<center> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/WdPacbUeEpCAhLJ.png" style="zoom: 65%;" /> </center>

总结： 此次出差作为接触波分的第一站，问题全靠常识，这点还得记功劳于多年的读书上。这次出差算是仅仅认识了波分设备，理论知识几乎为0，还有就是一些现场操作问题，可忽略！

### 鹤壁

鹤壁，全国文明城市排名前五的城市，是一座宜居城市，环境优美。

鹤壁组网同三门峡，设备放置于`新大楼（5楼）`和`大梁庄（2楼）`业务模式`point to point`，现场5块PDSD。

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/VQuYoqPKfIjlh4B.png" alt="image.png" style="zoom:58%;" />

总结：  此次出差是接触波分设备的第二站，相同的组网已经完全没有难度。这次调测光路仅掌握了show  mode命令，因为当时一路光调不通，经排查为mode 设置错误。

​          期间，还去周口开通U设备

### 洛阳

洛阳，全国唯一非省会城市开通地铁的城市，千朝古都，汉服文化盛行，地铁基本都能看到。

洛阳是波分设备的第三站，组网方式不同于三门峡、鹤壁，是一个环网结构，设备放置于西工、洛南、和谷水，配置4光3电、4光4电。谷水机房远离市区并且安全级别较高，进入机房需要人打申请。组网如下：

<center> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/56Dz3ecgmiAO7GZ.png"style="zoom: 57%;" /> </center>    

<center> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/p6IGctdeRKCJhBQ.png"style="zoom: 58%;" /> </center>

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202311011437129.png" style="zoom:95%;" />

  ![](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/55.jpg)

<center><img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/WdPacbUeEpCAhLJ.png" style="zoom: 67%;" /></center> 

总结：接触波分设备的第三站，这次是波分知识和人际关系的爆破点，波分知识增长不少，人际关系开始紧张。

串波、环网、标签、上ODF架等，都是全新的知识。但是基本的命令还是涉及的不够多。大局了解的比较多。

了解最多的还是上ODF架的一些东西，打印标签的一些格式：`机柜号+框+槽位+板卡名称+接口名称-TX/RX  电框`，

`框+槽位+板卡名称+接口名称-TX/RX  光框`，没有一定的东西，好坏参半不必太当真。

### 庆阳

庆阳，莫酸奶真的好喝，人口排名居甘肃省前列。

接触波分设备测试的头一回，坐标庆阳电信，负责人李小娟，简单的点对点10GE业务测试，测试项目主要是传输设备的稳定性和设备性能，顺带测了op倒换和损耗。

<center><img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%BA%86%E9%98%B3.jpg" style="zoom: 35%;" /> </center>


<div align='center' ><font size=3>现场图</font></div>

<center><video id="my-video" class="video-js" controls preload="auto" width="35%"
poster="http://1301999062.vod-qcloud.com/bd28f392vodtranscq1301999062/d269f43e3270835012416384556/coverBySnapshot_10_0.jpg" data-setup='{"aspectRatio":"16:9"}'>
    <source src="http://1301999062.vod-qcloud.com/e63f05eavodcq1301999062/d269f43e3270835012416384556/OhbhjiFevoIA.mp4" type='video/mp4' >
    </video></center>

<p hidden>https://youtube.com/shorts/_nw_C2xk4dk## </p>


总结：  就学会了一个上网管(B039版本网管方式变了) 、倒换阈值的设置、延迟时间设置、打环命令、计算光路提升了下，学会了写路由等。其他再补充。

### <span id="guangzhou"></span>广州

<div align="center"> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202311011447386.jpg" style="zoom: 10%;" /> </div>

##### 试点系统图

![](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%B9%BF%E5%B7%9E.png)

##### 试点连纤图

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%B9%BF%E5%B7%9E%E8%AF%95%E7%82%B9.png" style="zoom:80%;" />

##### 现场图

<div align="center"> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202311021005797.png" style="zoom: 85%;" /> </div>

##### 仪器

| <font color="red">光功率计</font> | <font color="red">58仪表100G</font> | <font color="red">光谱分析仪</font> |  <font color="red">光衰减器</font>  |
| :-------------------------------: | :---------------------------------: | :---------------------------------: | :---------------------------------: |
|           **尾纤20根**            |           **光衰3dBmx2**            |     ~~**理线架、标签32个**、~~      | <font color="red">**分光器**</font> |

##### 发货清单

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E8%AE%BE%E5%A4%87%E6%B8%85%E5%8D%95.png" style="zoom:95%;" />

##### 模块发光指标

![](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%8F%91%E5%85%89%E6%8C%87%E6%A0%87.png)

&emsp;<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202310131352466.png" style="zoom: 56%;" />

##### 调波波

0dBm---->-6dBm---->7dBm---->4dBm(入纤光功率)-------------6dBm（OLP）----->3dBm(出纤光功率)----->-3dBm

##### 测试项目

- 背靠背OSNR容限

  要求：最少两波以上才能测量OSNR，一测极限业务不丢包情况下的值，二测关闭CFP模块关闭激光器下的光谱仪读书，三测20db下次的值，三个数值录入表格得出OSNR值。

![](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202310130900931.png)

光可调衰减器B：光缆损耗，3dB/10KM

光可调衰减器A：设置大于噪声源

ASE：设置一个值（可用OA代替，需要设置`set los_status N`  出光-6左右，经过PA放大可以达到10dBm左右）

光谱仪：记录S+N值、N值等，最后通过公式计算得出OSNR值，查看preFEC

业务分析仪：打流，模拟业务

- 异厂家解耦

  要求：A厂家的电和B厂家的光互通。

  难点：合分波器波长不一致，按照规范没问题。

- 谱宽测试

  直接拿光谱仪扫，谱宽的定义：波峰处向下3dB和20dB处的值。

- 修改三大运行商模型

  ```
  config#  netconf_datastore              ## 查看模型
  config#  netconf_datastore  cmcc        ## 设置模型
  ```

  

总结：计划赶不上变化，OSNR准备最充分，反而各种阻碍，其他没准备的，测的不能说特别顺利，但也算的上顺利，正所谓<u>“有心栽花花不开，无心插柳柳成荫”</u> ,气人不!

看来，做事要准备，也仅仅是准备大概率发生的，必然的；不必然的事，随机应变是上策，总之，事的背后是人，保持好与人平和的态度，协调人，问题终会解决！！

知识这块，关于“中心波长”相关的知识需要补习，这方面测试被问到了，不清楚这块内容是不是该售后了解的内容，不妨学来试试，至少以后类似这种事多一分从容与自信。

测试对版本相对关注，所以，有些情况下，需要干一些见不得人的“脏事”。比如，从测试开始到测试结束，私底下换了三个版本。这对测试官来说，绝对不允许，但是在我这确实这么干了！西吧

总之，事的背后是人，人稳当当的，这事八九成就成了，没啥问题的。

### <span id="zz"></span>郑州

- ##### U设备上线

<img src="https://version-1301999062.cos.ap-beijing.myqcloud.com/202311170925504.png" style="zoom:50%;" />

&emsp;需求：修改用户名、密码

```
user login-password admin
##输入新密码
user enable-password admin
##输入新密码
```

- ##### A设备上线

  需求：8GE挂远端上线配置、远端基本配置、用户名密码修改

```
netconf_datastore cucc           
netconf_yang version set 3
netconf enable
env set NETCONF=CUCC
                               ##GPN7600上线远端需要做的配置，切记关闭DHCP功能。##
dhcpr enable
dhcpr serverip add x.x.x.x          ##DHCP服务器ip地址
dhcpr gcc relay enable
dhcpr add relayif vlanAuto4000
 
vlan 4000                            ##如果下挂A6，需要配置以下内容
add port 1/1 tag                     ## 挂远端的口加入到vlan
ip address unnumberd loopback 10
exit

interf ethe 1/1                      ##挂远端的口
managevlan 4000
exit                             注意：U设备禁止开启DHCPC，否则会篡改对端U设备IP
```

```
grosadvdebug
download ftp sdn 10.10.10.130 admin admin otncucc0726V2.bin          ##A6设备配置
exit

lldp txmode netconf
vlanmode dot
vlan 4000
add port 1/9 tag
ip address unnumberd loopback 10
exit
dhcpc vlan 4000 4000
dhcpc enable                         
ofagent enable
```

```
管控配置DHCP relay地址，为该U设备的环回地址，地址池28位掩码共计16个可用IP
例如：U设备 loopback10 地址为3.57.3.129，掩码28位
     则： DHCP relay地址为3.57.3.129，地址池地址为3.57.3.130-3.57.3.143
```

- 透传业务
  - NE1

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/NE1.gif"/>

- NE2

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/NE2.gif"/>

- ##### EOO

  - NE1

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/NE1.gif"/>

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/8ge.gif"/>

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/8ge.gif"/>

[管控测试文档|点击下载](https://version-1301999062.cos.ap-beijing.myqcloud.com/%E4%B8%AD%E5%9B%BD%E8%81%94%E9%80%9AOTN-CPE%E8%AE%BE%E5%A4%87%E7%AE%A1%E6%8E%A7%E6%8E%A5%E5%8F%A3_%E7%8E%B0%E7%BD%91%E8%AF%95%E7%82%B9%E6%B5%8B%E8%AF%95%E6%96%B9%E6%A1%88_GW.pdf)

## <span id="nt"></span>南通

南通，家纺四件套出名，有山姆商店，经济实力相当强，苏F牌照。

作为2024年第一波，今年的工作主打一个合适就行，端正下交流态度，自身也要断舍离。

##### 组网方式

<center><img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%8D%97%E9%80%9A%E7%94%B5%E4%BF%A1DCI-BOX%E4%B8%89%E7%82%B9%E7%8E%AF.png" style="zoom:50%;" /></center>

<center><img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E4%BC%81%E4%B8%9A%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_17066621541415.png"/></center>

南通电信DCI-BOX三点环；（<u>长桥</u>、易家桥、苏通产业园）主备路由。

##### 网管方式

直连网管；  长桥3楼设备，4楼网管机，中间经过交换机。

##### 设备型号

|  设备型号  |   数量    |
| :--------: | :-------: |
| OTP5600-II | <u>13</u> |

##### 位置

`易家桥` &emsp;[江苏省南通市崇川区工农路129号](https://map.qq.com/?type=marker&isopeninfowin=1&markertype=1&pointx=120.883071&pointy=32.008432999999997&name=%E5%B7%A5%E5%86%9C%E8%B7%AF129%E5%8F%B7&addr=%E6%B1%9F%E8%8B%8F%E7%9C%81%E5%8D%97%E9%80%9A%E5%B8%82%E5%B4%87%E5%B7%9D%E5%8C%BA%E5%B7%A5%E5%86%9C%E8%B7%AF129%E5%8F%B7&zoomLevel=18)

`长桥`&emsp;[江苏省南通市崇川区环城西路21号](https://map.qq.com/?type=marker&isopeninfowin=1&markertype=1&pointx=120.864896&pointy=32.013057000000003&name=%E7%8E%AF%E5%9F%8E%E8%A5%BF%E8%B7%AF21%E5%8F%B7&addr=%E6%B1%9F%E8%8B%8F%E7%9C%81%E5%8D%97%E9%80%9A%E5%B8%82%E5%B4%87%E5%B7%9D%E5%8C%BA%E7%8E%AF%E5%9F%8E%E8%A5%BF%E8%B7%AF21%E5%8F%B7&zoomLevel=19)

`苏通产业园`&emsp;[江苏省南通市崇川区江达路](https://map.qq.com/?type=marker&isopeninfowin=1&markertype=1&pointx=120.982778&pointy=31.823122999999999&name=%E6%B1%9F%E8%BE%BE%E8%B7%AF&addr=%E6%B1%9F%E8%8B%8F%E7%9C%81%E5%8D%97%E9%80%9A%E5%B8%82%E5%B4%87%E5%B7%9D%E5%8C%BA%E6%B1%9F%E8%BE%BE%E8%B7%AF&zoomLevel=18)，南通电信云计算中心；

##### 各站点配置

本期DCI-BOX建设工程图纸|[点击预览](https://version-1301999062.cos.ap-beijing.myqcloud.com/%E5%9B%BE%E7%BA%B824.1.17--2023%E5%B9%B4%E5%8D%97%E9%80%9A%E7%94%B5%E4%BF%A1DCI-BOX%E5%BB%BA%E8%AE%BE%E5%B7%A5%E7%A8%8B.pdf)

配置预览：

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%8D%97%E9%80%9ADCI-BOX%E9%85%8D%E7%BD%AE%E6%B8%85%E5%8D%95.jpg"/>

波道规划：<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E5%8D%97%E9%80%9A%E6%B3%A2%E9%81%93%E8%A7%84%E5%88%92" style="zoom: 25%;" />

清单明细|[点击下载](https://version-1301999062.cos.ap-beijing.myqcloud.com/2023.11.15-%E6%A0%BC%E6%9E%97%E5%A8%81%E5%B0%94-%E5%8D%97%E9%80%9A%E7%94%B5%E4%BF%A1DCI%E9%85%8D%E7%BD%AE%E6%B8%85%E5%8D%95%EF%BC%8813%E6%B3%A2%EF%BC%89.xlsx)

内网穿透|[点击查看](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202405151015895.png)

## <span id="tz"></span>泰州

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/%E6%B3%B0%E5%B7%9E1"/>

| 序号 | 网元名称                        | 网元号 | 设备类型 | 网元IP地址     | 掩码 | 网元地址                                          |
| ---- | ------------------------------- | ------ | -------- | -------------- | :--- | ------------------------------------------------- |
| 22   | 网管服务器                      | 2001   | 戴尔     | 132.240.139.66 | 32位 | 泰州市海陵区凤凰东路88号5楼                       |
| 1    | 1001-江苏泰州海陵区新区局-光层1 | 1001   | OLS20    | 133.234.25.1   | 32位 | 泰州市海陵区凤凰东路88号                          |
| 2    | 1002-江苏泰州海陵区新区局-光层2 | 1002   | OLS20    | 133.234.25.2   | 32位 | 泰州市海陵区凤凰东路88号                          |
| 3    | 1003-江苏泰州海陵区新区局-电层1 | 1003   | OTE20    | 133.234.25.3   | 32位 | 泰州市海陵区凤凰东路88号                          |
| 4    | 1004-江苏泰州海陵区海陵局-光层1 | 1004   | OLS20    | 133.234.25.4   | 32位 | 泰州市海陵区城北街道青年桥通信市场3楼             |
| 5    | 1005-江苏泰州海陵区海陵局-光层2 | 1005   | OLS20    | 133.234.25.5   | 32位 | 泰州市海陵区城北街道青年桥通信市场                |
| 6    | 1006-江苏泰州海陵区海陵局-电层1 | 1006   | OTE20    | 133.234.25.6   | 32位 | 泰州市海陵区城北街道青年桥通信市场                |
| 7    | 1007-江苏泰州姜堰区里华局-光层1 | 1007   | OLS20    | 133.234.25.7   | 32位 | 泰州市姜堰区里华邮政支局3楼                       |
| 8    | 1008-江苏泰州姜堰区里华局-光层2 | 1008   | OLS20    | 133.234.25.8   | 32位 | 泰州市姜堰区里华邮政支局3楼                       |
| 9    | 1009-江苏泰州姜堰区里华局-电层1 | 1009   | OTE20    | 133.234.25.9   | 32位 | 泰州市姜堰区里华邮政支局3楼                       |
| 10   | 1010-江苏泰州姜堰区城东局-光层1 | 1010   | OLS20    | 133.234.25.10  | 32位 | 泰州市姜堰区东大街23号4楼                         |
| 11   | 1011-江苏泰州姜堰区城东局-光层2 | 1011   | OLS20    | 133.234.25.11  | 32位 | 泰州市姜堰区东大街23号4楼                         |
| 12   | 1012-江苏泰州姜堰区城东局-电层1 | 1012   | OTE20    | 133.234.25.12  | 32位 | 泰州市姜堰区东大街23号4楼                         |
| 13   | 1013-江苏泰州姜堰区南郊局-光层1 | 1013   | OLS20    | 133.234.25.13  | 32位 | 泰州市姜堰区长江西路69号3楼                       |
| 14   | 1014-江苏泰州姜堰区南郊局-光层2 | 1014   | OLS20    | 133.234.25.14  | 32位 | 泰州市姜堰区长江西路69号                          |
| 15   | 1015-江苏泰州姜堰区南郊局-电层1 | 1015   | OTE20    | 133.234.25.15  | 32位 | 泰州市姜堰区长江西路69号                          |
| 16   | 1016-江苏泰州姜堰区大伦局-光层1 | 1016   | OLS20    | 133.234.25.16  | 32位 | 泰州市姜堰区中国电信（大伦营业厅）2楼             |
| 17   | 1017-江苏泰州姜堰区大伦局-光层2 | 1017   | OLS20    | 133.234.25.17  | 32位 | 泰州市姜堰区中国电信（大伦营业厅）                |
| 18   | 1018-江苏泰州姜堰区大伦局-电层1 | 1018   | OTE20    | 133.234.25.18  | 32位 | 泰州市姜堰区中国电信（大伦营业厅）                |
| 19   | 1019-江苏泰州姜堰区娄庄局-光层1 | 1019   | OLS20    | 133.234.25.19  | 32位 | 泰州市姜堰区中国电信（泰州姜堰娄庄网盈合作店）2楼 |
| 20   | 1020-江苏泰州姜堰区娄庄局-光层2 | 1020   | OLS20    | 133.234.25.20  | 32位 | 泰州市姜堰区中国电信（泰州姜堰娄庄网盈合作店）    |
| 21   | 1021-江苏泰州姜堰区娄庄局-电层1 | 1021   | OTE20    | 133.234.25.21  | 32位 | 泰州市姜堰区中国电信（泰州姜堰娄庄网盈合作店）    |

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202405150954490.png" style="zoom: 200%;" />
