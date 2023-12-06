## UMS_设备上线、业务配置；业务迁移至UMS

### <center>设备上线</center>

以联通UMS为例，设备纳管需要三个地址：接口地址、loopback 10、dhcpr_ip（全省唯一）

> [!Note]
>
> 接口地址上4A平台；loopback10地址上UMS（默认），也可以是接口地址；dhcpr_ip配置需满足U设备下挂其他U设备

- OTN-CPE设备上线(联通为例)

  - SDN文件符合要求

  ```
  GPN7600(config)# download ftp sdn x.x.x.x  user  password  文件名.bin  # OTN设备
  GPN710D(DEBUG_H)# download ftp sdn x.x.x.x  user  password  文件名.bin  # 远端
  ```

  [<img alt="Static Badge" src="https://img.shields.io/badge/SDN-CUCC_20230227.bin-purple">](https://version-1301999062.cos.ap-beijing.myqcloud.com/otncucc20230227.bin) [<img alt="Static Badge" src="https://img.shields.io/badge/NMS_APP-GPN7600_179.bin-purple">](https://version-1301999062.cos.ap-beijing.myqcloud.com/GPN7600_179.bin) [<img alt="Static Badge" src="https://img.shields.io/badge/NMU_APP-GPN7600_179.bin-purple">](https://version-1301999062.cos.ap-beijing.myqcloud.com/GPN7600_179NMU.bin) [<img alt="Static Badge" src="https://img.shields.io/badge/FPGA-1058_SP25_vlan_1030.bin-purple">](https://version-1301999062.cos.ap-beijing.myqcloud.com/fpga_code_1058_SP25_vlan_1030.bin) 

  - 配置如下命令

  ```
  netconf_datastore cucc
  netconf_yang version set 3
  netconf enable
  env set NETCONF=CUCC    
  ```

  > [!Note]
  >
  > ```
  > 移动管控需额外配置：netconf cmcc callhome enable  
  > ```

  - dhcpr配置

    ```
    dhcpr enable
    dhcpr serverip add x.x.x.x         ## serverip需要联通提供！
    dhcpr gcc relay enable
    ```

  - dhcpc配置

    ```
    dhcpc gcc enable
    dhcpc enable
    ```

  - 资源管理-->设备信息管理-->网元信息管理，点击“增加”。

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061008861.png"/>

  - 查看SDN文件是否下载

    ```
    show ver
    ```

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/show%20ver.png" style="zoom: 67%;" />

    ```
    environment show
    ```

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061144514.png" style="zoom:50%;" />

  - 检查830端口是否打开

    ```
    show running-config sdn
    ```

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061145831.png" style="zoom: 50%;" />

  - 查看ofcd进程

    ```
    show task
    ```

  - 查看dhcpr配置是否正确

    ```
    show running-config dhcpr
    ```

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061147122.png" style="zoom:50%;" />

  - 查看dhcpc配置是否正确

    ```
    show running-config dhcpc                ## 谨慎操作，操作不当会篡改对端信息导致托管
    ```

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061150803.png" style="zoom:50%;" />

  - 此时，查看U设备是否连接到UMS

    ```
    show ssh-peer information
    ```

    ![](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061154659.png)

- A6设备上线

  <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061247071.png" style="zoom:50%;" />

  根据场景需求，A6设备上线分为两种：

  - 远端603G（包括变种710D等型号）

    - U设备配置

    ```
    netconf_datastore cucc                   ## config节点下
    netconf_yang version set 3
    netconf enable
    env set NETCONF=CUCC
    ```

    ```
    dhcpr enable
    dhcpr serverip add x.x.x.x               ## 管控服务器地址，找联通要。
    dhcpr gcc relay enable
    dhcpr add relayif vlanAuto4000           ## 下挂A6时配置的vlan4000，根据现场情况配置更改
    ```

    - A设备配置（603G）

    ```
    vlan 4000
    add port 1/1 tag
    ip address unnumberd loopback 10
    exit
    ```

    ```
    interf ethe 1/1
    managevlan 4000
    exit
    ```

  - GPN800(小800)

    - U设备配置

    ```
    config otn
    interface any 14/7              ## 根据现场情况配置
    config porttype otu1
    exit
    ```

    ```
    interface gcc 14/9
    config gcc-channel peerport 1 1 1 101 client
    ```

    - A设备配置

    ```
    interface gcc 1/1
    config gcc-channel peerport 1 14 1 7 client
    ```

  - 管控平台需要添加DHCP relay

    DHCP Relay地址为U设备环回地址，地址池范围为掩码可用ip范围。

    <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061312641.png"  />

- 查看A设备是否上线成功。
- 调试开关（谨慎操作）

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;底层打开XML日志命令

```
grosadvdebug                                   
sdn debug level verbose
sdn debug module adapter enable
sdn print debug here enable
```

&emsp;&nbsp;&nbsp;&nbsp;关闭XML日志命令

```
sdn debug module all disable
```

------

### <center>业务配置</center>

[参考郑州测试内容，里面有详细业务下发步骤](https://version-1301999062.cos.ap-beijing.myqcloud.com/%E4%B8%AD%E5%9B%BD%E8%81%94%E9%80%9AOTN-CPE%E8%AE%BE%E5%A4%87%E7%AE%A1%E6%8E%A7%E6%8E%A5%E5%8F%A3_%E7%8E%B0%E7%BD%91%E8%AF%95%E7%82%B9%E6%B5%8B%E8%AF%95%E6%96%B9%E6%A1%88_GW.pdf) 

### <center>业务迁移至UMS</center>

配置好业务之后，网管操作如下：

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061422021.png" style="zoom:67%;" /> <img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061424335.png" style="zoom:67%;" /> 

```
show running-config ctp         ## 一定要有数据，没数据说明没迁移成功
```

<img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/202312061424950.png" style="zoom:67%;" />管控刷新后应该会有东西。