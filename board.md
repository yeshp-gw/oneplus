# 板卡

- #### DMD-8GE

[![Static Badge](https://img.shields.io/badge/DMD_8GE%E6%9D%BF%E5%8D%A1%E5%BC%80%E9%80%9A%E6%8C%87%E5%AF%BC%E4%B9%A6-V1.1-blue)](https://version-1301999062.cos.ap-beijing.myqcloud.com/DMD-8GE%E6%9D%BF%E5%8D%A1%E5%BC%80%E9%80%9A%E6%8C%87%E5%AF%BC%E4%B9%A6%EF%BC%88V1.1%EF%BC%89.pdf)

<!--sec data-title="8GE底层配置命令" data-id="section0" data-show=true ces-->

**8GE底层配置_板卡业务模式**

```
GPN7600(config)# config interface vcg agg-mode <slot> local        //板卡内汇聚//
GPN7600(config)# config interface vcg agg-mode <slot> switch       //设备级汇聚//
```

**8GE底层配置_端口双模**

```
port模式：
GPN7600(config)# int msap-eth <slot/port>         
GPN7600(config)# config l1mux port                  //配置端口模式：port/vlan/none/mpls//
GPN7600(config)# exit
GPN7600(config)# int vcg <slot/port>
GPN7600(config)# config l1mux port <1-8>                //配置vcg要绑定的端口//
GPN7600(config)#exit
vlan模式：
GPN7600(config)# int msap-eth <slot/port>
GPN7600(config)# config l1mux vlan 
GPN7600(config)# exit
GPN7600(config)# int vcg <slot/port>
GPN7600(config)# config l1mux port <1-8>              //绑定端口//
GPN7600(config)# config l1mux vlan <1-4094>           //配置vlan<1-4094>
GPN7600(config)# exit

GPN7600(config)# config msap
GPN7600(config)# ioctl vcg info <slot/port>              //查看配置是否生效//

GPN7600(config)# int vcg <slot/port>
GPN7600(config)# config vlan-action <tx/rx> mode <nochange|add|modify|delete>    //配置vcg动作//
GPN7600(config)# config vlan-action <tx/rx> vlanid <1-4094>      //配置发送或者接收方向的vlan id//
```

**8GE底层配置_端口up/down**

```
GPN7600(config)#int eth 1/1  
GPN7600(if-eth1/1)#shutdown                       ## 进入端口，shutdown 
或者 
GPN7600(config-msap)#ioctl eth disable 1/1        ## msap节点下，关闭。任选其一！
```

<!--endsec-->

[![Static Badge](https://img.shields.io/badge/EOSC_8GE%E7%AB%AF%E5%8F%A3%E4%BF%9D%E6%8A%A4%E9%85%8D%E7%BD%AE%E6%8C%87%E5%AF%BC%E4%B9%A6-V1.1-blue)](https://version-1301999062.cos.ap-beijing.myqcloud.com/EOSC8GE%E7%AB%AF%E5%8F%A3%E4%BF%9D%E6%8A%A4%E9%85%8D%E7%BD%AE%E6%8C%87%E5%AF%BC%E4%B9%A6.doc)

> [!note]
>
> 新版本8ge默认NOOP模式，修改VLAN模式时软件设置了防误操作机制，需对应VCG先配置“未绑定”，然后修改配置VLAN。

- #### OTN-8AT2

<img src="https://version-1301999062.cos.ap-beijing.myqcloud.com/202311161503294.png" style="zoom:50%;" />

<center><font size="5">板卡结构</font></center>

详细内容参考文档说明▾

[![Static Badge](https://img.shields.io/badge/OTN%E6%A6%82%E8%BF%B0%E4%B8%8EOTN%E6%9D%BF%E5%8D%A1%E4%BB%8B%E7%BB%8D-V1.1%E4%B8%8B%E8%BD%BD-blue)](https://version-1301999062.cos.ap-beijing.myqcloud.com/OTN%E6%A6%82%E8%BF%B0%E4%B8%8EOTN%E6%9D%BF%E5%8D%A1%E4%BB%8B%E7%BB%8D.pptx)





