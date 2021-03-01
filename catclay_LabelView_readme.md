#LabelView
 
android上用于显示标签云的组件
  

功能： 
1、设置标签 
2、设置每个标签的配色方案 
3、设置每个标签的x/y速度 
4、设置标签云是否滚动(默认滚动) 
5、设置标签云的item点击事件 
 

具体使用方法： 

1、在xml中配置： 
&lt;org.loader.labelview.LabelView 
            xmlns:label="http://schemas.android.com/apk/res/org.loader.labelview" 
	        android:layout_marginTop="20dp" 
	        android:id="@+id/lv" 
	        android:layout_below="@id/et_input" 
	        android:layout_width="wrap_content" 
	        android:layout_height="wrap_content" 
	        label:is_static="false" 
	        android:background="@android:color/white"/>
            
在Activity中配置： 

    @Override
    protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		
		mEditText = (EditText) findViewById(R.id.et_input);
		mLabelView = (LabelView) findViewById(R.id.lv);
		
		mLabelView.setLabels(new String[] {"蛋疼","loader","Android", "Google", "馒头", "大米", "服务"});
		mLabelView.setColorSchema(new int[] {Color.DKGRAY, Color.CYAN, Color.GREEN, Color.LTGRAY, Color.MAGENTA, Color.RED});
		mLabelView.setSpeeds(new int[][] {{1,2},{1,1},{2,1},{2,3}});
		mLabelView.setOnItemClickListener(new OnItemClickListener() {
			@Override
			public void onItemClick(int index, String label) {
				Toast.makeText(MainActivity.this, "index : " + index + ",label : " + label, Toast.LENGTH_SHORT).show();
				mEditText.setText(label);
			}
		});
	}
    
效果展示（动态图有失真现象，所以直接截图了）： 
![image](http://git.oschina.net/qibin/LabelView/raw/master/images/1.png)
![image](http://git.oschina.net/qibin/LabelView/raw/master/images/2.png)

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)