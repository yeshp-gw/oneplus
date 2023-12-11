### 差旅统计

{% chart %}

{
    "data": {
        "columns": [
                      ["天数",0, 0, 0, 5, 15, 4, 30,25,0,11,11,13,0],
                      ["开销",0, 0,  0, 2000, 6000, 2000, 10000,9000,0,3000,3000,4000,0]
           ],
 axes: {
                开销: 'y2'
               },
        types: {
                 开销: 'bar' // ADD
               }
     },
    "axis": {
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
                       position: 'outer-middle'
                                  }
                       }
                 }
}

{% endchart %}

