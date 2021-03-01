#ZqxChart
![折线图,柱状图](http://git.oschina.net/uploads/images/2016/0630/141247_00df7a2e_372342.gif "折线图,柱状图")
![饼状图](http://git.oschina.net/uploads/images/2016/0630/141029_c9b91675_372342.gif "饼状图")
maven：
------
     
         com.zqx.chart 
         chart 
         0.2 
         pom 
     


gradle：
-------
    compile 'com.zqx.chart:chart:0.2'

使用方法：
==========
  1.折线图
  --------
      //通过代码设置：
      LineChart lineChart = (LineChart) findViewById(R.id.linechart);
      LineChartData lineChartData = LineChartData.builder()
              .setXdata(xdata)//x轴数据
              .setYdata(ydata)//y轴数据
              .setYpCount(7)//y轴刻度数量
              .setCoordinatesColor(getResources().getColor(android.R.color.holo_orange_dark))
              //.setXXX()
              .setAnimType(Anim.ANIM_ALPHA)//动画效果，目前仅支持两种
              .build();
      lineChart.setChartData(lineChartData);
      //通过xml设置：
       
       
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:orientation="vertical">
      
               
            
       
      // res/下新建 attrs.xml
       
       
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
                
                
           
       
  2.柱状图
  --------
      //通过代码设置
      Histogram histogramChart = (Histogram) findViewById(R.id.histogramchart);
      HistogramData histogramData = HistogramData.builder()
              .setXdata(xdata)
              .setYdata(ydata)
              .setYpCount(7)
              .setAnimType(Anim.ANIM_ALPHA)
              .build();
      histogramChart.setChartData(histogramData);
      #通过xml设置
       
       
       
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
           
       
      //也可以通过代码和 arrays.xml 设置每个x坐标对应柱状图的颜色,代码可以通过新建一个color 数组并调用
          setColors(xxx);
      //arrays.xml color 个数与数据个数对应
         
         
             @android:color/darker_gray 
             @android:color/holo_red_dark 
             @android:color/holo_green_dark 
             @android:color/holo_orange_dark 
             @color/histogram_test 
             @android:color/holo_blue_dark 
             @color/colorAccent 
         
  3.饼状图
  --------
        饼状图动画效果目前只支持alpha
        code:
            PieChart pieChart = (PieChart) findViewById(R.id.piechart);
            int[] colors = new int[]{Color.RED,Color.BLACK,Color.BLUE,Color.GREEN,Color.GRAY,
                    Color.YELLOW,Color.LTGRAY,Color.CYAN,Color.MAGENTA};
            PieChartData pieChartData = PieChartData.builder()
                    .setDatas(datas)
                    //.setColors(colors)
                    .setTextColor(Color.RED)
                    //.setTextSize(36)
                    //.setSeparationDegree(3)
                    .setPieItemClickListener(new OnPieItemClickListener() {
                        @Override
                        public void onPieItemClick(int position) {
                            Toast.makeText(MainActivity.this,"click->"+position,Toast.LENGTH_SHORT).show();
                        }
                    }).build();
            pieChart.setChartData(pieChartData);
        xml:
             
         
         
           @color/colorPrimary 
           @android:color/darker_gray 
           @android:color/holo_red_dark 
           @android:color/holo_green_dark 
           @android:color/holo_orange_dark 
           @android:color/white 
           @android:color/holo_blue_dark 
           @color/colorAccent 
           @android:color/black 
         
        饼状图自定义属性
         
             
             
             
             
             
             
             
             
                  
                  
                  
             
         
  
待完成
======
折线图和柱状图的多组数据显示。

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)