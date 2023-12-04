##### 文本居中

```
<div  align='center' >实习总结报告</div>
```

##### 图片居中

```
<div align="center"> <img src="图片地址" width = 500 height = 300 /> </div>
<div align="center"> <img src="图片地址" width="70%" /> </div>
```

```
<div align="center"> <img src="图片地址" style="zoom: 65%;" /> </div>
```

```
<div align="center"> <img src="图片地址"/> </div>
```

##### 左对齐/右对齐

```
<p align="left"><img src="图片链接"</p>          ## 图
```

```
<p align="right"> PQSQ </p>                     ## 字
```

```
img src="https://gitbook-pic-1301999062.cos.ap-beijing.myqcloud.com/3tKxU8V2WhRXzdI.png" alt="image.png" style="zoom:70%;" align="right"/>
```

##### 字体颜色/尺寸/类型

```
<font color="white" size=7 face="黑体"> 白7黑体字 </font>
```

**加粗语法**

```
<stong>  加粗文本  </strong>
<b> 加粗文本 </b>
```

##### 插入视频

```
<video controls="controls" width="100%">
  <source src="../courseResources/mp4.mp4" type="video/mp4">
</video>
```

**视频居中**

```
<center> 视频   </center>
```

##### 插入pdf

```
<embed src="../courseResources/pdf.pdf"  width="500" height="375" />
```

##### 插入ppt

```
<embed src="../courseResources/pptTest.pdf"  width="100%" height="500px" />
```

**缩进**

```
&emsp;&ensp;     ##俩空格、一个空格
```

**标题居中**

```
<h2 style="text-align:center">我是二级居中的标题<h2>
```

**换行**

```
<br>
```

**页内跳转**

```
[跳转标题二](#jump)                                     ## 跳转语法
<span id="jump"></span>标题二                        ## 添加锚点
```

**上标、下标**

```
sub  ##下标
sup  ##上标
<sub>下标内容</sub>
```

**添加脚注**

```
内容[^1]
[^1]: 脚注内容
```

**公式katex语法**

```
\frac   ##除法
^   ## 次方
<center>$$"gon"$$</center> 
```

**文字底色**

```
<mark>  文字  </mark>
```

**背景色**

```
<table><tr><td bgcolor=“D1EEEE”>   文字   </td></tr>
```

**隐藏某行内容**

```
<p hidden>这个段落应该被隐藏。</p>
```

**文字底色插件**

```
{
    "plugins": ["emphasize"]
}
```

```
This text is {% em %}highlighted !{% endem %}

This text is {% em %}highlighted with **markdown**!{% endem %}

This text is {% em type="green" %}highlighted in green!{% endem %}

This text is {% em type="red" %}highlighted in red!{% endem %}

This text is {% em color="#ff0000" %}highlighted with a custom color!{% endem %}
```

**引用个性style格式**

```
默认：callout
个性化：flat
```

**插入视频**

```
<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="https://1301999062.vod-qcloud.com/bd28f392vodtranscq1301999062/5262199b3270835011374725705/coverBySnapshot/coverBySnapshot_10_0.jpg" data-setup='{"aspectRatio":"16:9"}'>
  <source src="https://1301999062.vod-qcloud.com/bd28f392vodtranscq1301999062/5262199b3270835011374725705/v.f80000.mp4" type='video/mp4' >
    </video>
```

**选择题**

```python
{%mcq ans="o4"%}
{%title%} 卧薪尝胆说的哪位历史人物?
{%o1%} 夫差
{%o2%} 范蠡
{%o3%} 管仲
{%o4%} 勾践
{%endmcq%}
```
