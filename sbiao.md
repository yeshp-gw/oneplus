### 差旅统计

{% chart %}

{
    "data": {
         x: 'x',
        columns: [
                      ['x',1,2,3,4,5,6,7,8,9,10,11,12],
                      ['天数', 0, 0, 5, 15, 4, 30,25,0,11,11,13,6],
                      ['开销', 0,  0, 2000, 5500, 2000, 10000,9000,0,3000,3000,4000,2800]
           ], 
        axes: {
                    开销: 'y2'
        },
        types: {
                 开销: 'bar' // ADD
        },
        labels: true,
        type:'spline'
    },
    axis: {
                y: {
                            label: { // ADD
                                           text: '天数',
                                           position: 'outer-middle'
                            }
                },
                y2: {
                               show: true,
                               label: { // ADD
                                            text: '开销(单位：元)',
                                            position: 'outer-middle'  // 标签页位置
                       }
                },
                x: {
                                type: 'category',                           
                                tick: {
                                            rotate: 0,   // x轴数字的倾斜度，-70：向左倾斜70°
                                            multiline: false
                                },
                                    height: 0   // 标签与x轴的距离差
                }
          },title:{text:'8888'}
}

{% endchart %}

<center>2023差旅统计</center>

{% chart %}

{
    "data": {
         x: 'x',
        columns: [
                      ['x',1,2,3,4,5,6,7,8,9,10,11,12],
                      ['天数', 12, 8,31 , 23, 0, 0,0,0,0,0,0,0],
                      ['开销', 4380,  2900, 12000, 8500, 1000, 1000,1000,1000,1000,1000,1000,1000]
           ], 
        axes: {
                    开销: 'y2'
        },
        types: {
                 开销: 'bar' // ADD
        },
        labels: true,
        type:'spline'
    },
    axis: {
                y: {
                            label: { // ADD
                                           text: '天数',
                                           position: 'outer-middle'
                            }
                },
                y2: {
                               show: true,
                               label: { // ADD
                                            text: '开销(单位：元)',
                                            position: 'outer-middle'  // 标签页位置
                       }
                },
                x: {
                                type: 'category',                           
                                tick: {
                                            rotate: 0,   // x轴数字的倾斜度，-70：向左倾斜70°
                                            multiline: false
                                },
                                    height: 0   // 标签与x轴的距离差
                }
          },title:{text:'8888'}
}

{% endchart %}



<center>2024差旅统计</center>



<div id="chart"></div>
<script>
  var chart = c3.generate({
  bindto: '#chart',
  data: {
        x: 'x',
        columns: [
            ['x',"1月","2月","3月","4月","5月","6月","7月","8月","9月","10月","11月","12月"],
            ['啤酒',100,115,120,130,135,140,190,260,300,252,200,180,120],
            ['汽水',90,105,110,112,115,180,290,360,420,352,200,110,100],
            ['白酒',510,450,330,300,280,280,290,380,450,452,460,466,520]
         ],
         type: 'spline',
         labels: true
    },
    legend: {
       position: 'bottom'
    },
    axis: {
        x: {
            type: 'category',
            tick: {
                rotate: -70,
                multiline: false
            },
                    height: 70
         }
     },
     title:{
         text: "饮料销售走抛图"
      },
 });

