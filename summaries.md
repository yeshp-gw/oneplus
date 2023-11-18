### 差旅统计

<script src="https://cdn.staticfile.org/Chart.js/3.9.1/chart.js"></script>
</head>
<body>

<canvas id="myChart" width="400" height="200"></canvas>
<script>
const ctx = document.getElementById('myChart');
const labels = ['1月份', '2月份', '3月份','4月份', '5月份', '6月份', '7月份','8月份','9月份','10月份','11月份','12月份'];  // 设置 X 轴上对应的标签
const data = {
  labels: labels,
  datasets: [{
    label: '2023年出差统计',
    data: [0,0,5,15,4,30,25,0,11,11,0,0],
    fill: false,
    borderColor: 'rgb(0, 128, 0)', // 设置线的颜色
	backgroundColor: ['rgba(179, 0, 33, 0.5)'],// 设置点的填充色
	pointStyle: 'circle',     //设置点类型为圆点
    pointRadius: 5,    //设置圆点半径
    pointHoverRadius: 10, //设置鼠标移动上去后圆点半径
    tension: 0.1
  }]
};
const config = {
  type: 'line', // 设置图表类型
  data: data,
  options: {
    responsive: true,  // 设置图表为响应式
    interaction: {  // 设置每个点的交互
      intersect: false,
    },
    scales: {  // 设置 X 轴与 Y 轴
      x: {
        display: true,
        title: {
          display: true,
          text: '月份'
        }
      },
      y: {
        display: true,
        title: {
          display: true,
          text: '天数'
        }
      }
    }
  }
};
const myChart = new Chart(ctx, config);
</script>
