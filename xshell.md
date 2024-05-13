### xshell在工作中的应用

- ##### 命令行快速TELNET

```
telnet x.x.x.x
admin
greenway
```

- ##### 命令行快速SSH/SFTP

```
ssh/sftp x.x.x.x
root
paaword
```

- ##### 命令行  SCP传文件

  [查看配置](https://version-1301999062.cos.ap-beijing.myqcloud.com/xshell%20%20%20scp%E4%BC%A0%E6%96%87%E4%BB%B6.pdf)

```
scp C:\Users\yeshp.GW\Desktop\FTP\Loader.elf root@192.168.40.111:/flash/sys ## 40网段。## 路径 属性
```

```
(sudo) chmod 777/644/... /flash/sys/文件名 ## 我，组，其他；权限-rwx-4 2 1， 4 2 1， 4 2 1
```

- ##### 命令行快速FTP

```
FTP X.X.X.X      ##windows ipv4地址
```

- ##### 命令行快速SERIAL

```
serial -b 9600 com4  
```

- ##### 命令行快速CMD/Powershell

```
cmd/realcmd
或者
powershell
```

- ##### 记录日志

```
选定内容-右键-到文本编辑器，保存。
```

- ##### CMD_快速改IPV4地址

```
cmd

netsh interface ip set address name="GW" source=static addr=192.168.76.100   mask=255.255.255.0
exit
```

- ##### CMD_快速恢复联网状态

```
CMD

netsh interface ip set address name="GW" source=dhcp             ## name与网卡名字需对应
EXIT 
```

- ##### JS_快速改IPV4地址

```js
Sub Main
	xsh.Screen.Synchronous = true
	xsh.Screen.Send(chr(8) + "cmd" + "\n")
	xsh.Screen.WaitForString("C:\Users\yeshp.GW\Documents\NetSarang Computer\7\Xshell\Sessions>")
	xsh.Screen.Send("netsh interface ip set address name=\"GW\" source=static addr=192.168.76.100 mask=255.255.255.0" + "\n")
	xsh.Screen.WaitForString("C:\Users\yeshp.GW\Documents\NetSarang Computer\7\Xshell\Sessions>")
	xsh.Screen.Send("exit" + "\n")
End Sub
```

- ##### 高亮字符串

  [查看配置](https://version-1301999062.cos.ap-beijing.myqcloud.com/xshell%20%20%20%E9%AB%98%E4%BA%AE%E5%AD%97%E7%AC%A6.pdf)

```
(\b(localhost|([1-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-4])\.[0-9]+\.[0-9]+\.[0-9]+|null|none)\b)
```

```
[^A-Za-z_&-]( fail| down |AIS|LCK|OCI|BDI|SSF|LOFLOM|AU_LOP|TU_AIS|LOS|LOF|AU_AIS|  No  |PLM|RDI|RS_LOF|HP_PLM|HP_RDI)
```

```
[^A-Za-z_&-](760b.fpga|760c.fpga|760e.fpga|fpga_code.bin|760s.fpga)
```

```
[^A-Za-z_&-](\PT Tx: 0x21 Rx: 0x21 Exp: 0x21 )
```

```
[^A-Za-z_&-]( 0x21|0x31|02h|03h|GWTT MSTP @2005|tx: 0x21|exp: 0x21|rx: 0x21|Tx power: |Rx power: )
```

```
[^A-Za-z_&-](kong| V02R19C17B013|v1.0b1|v1.1b2|v1.2b1|v2.0b1|B020|V1.1b1|v1.4b1|v1.2b3|v2.2b2|v1.0b2|nms.fpga|sw.fpga|app_code.bin|sysfile_ini.bin)
```

- ##### 主题Ubuntu

&emsp;&emsp;[点击下载](https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/ubuntu.xcs)

- ##### .EXE

&emsp;&emsp;[点击下载_0142](https://version-1301999062.cos.ap-beijing.myqcloud.com/Xshell-7.0.0142p.exe)