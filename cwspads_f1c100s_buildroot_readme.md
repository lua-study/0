# Buildroot f1c100s一键编译

### 编译flash
- make licheepi_nano-flash_defconfig
- make

### 编译ramdisk
- make licheepi_nano-ram_defconfig
- make

### 烧写flash
- sudo ./up-flash.sh

### 在内存中运行
- sudo ./up-ram.sh

### nes模拟器编译与采蘑菇运行
- cd board/f1c100s/apps/infones/linux
- make
- 把InfoNES和Super_mario_brothers.nes复制到"output/target/root"
- 在回到f1c10s_buildroot目录下 make
- sudo ./up-flash.sh 或 sudo ./up-ram.sh
- 运行嵌入式linux系统,登陆后在/root目录下运行
- ./InfoNES Super_mario_brothers.nes

### 修改核心添加RGB与BGR切换功能（画PCB时方便走线）
- output/build/linux-5.2.11/arch/arm/boot/dts/suniv-f1c100s.dtsi
- RGB

be0: display-backend@1e60000 {

	compatible = "allwinner,suniv-f1c100s-display-backend";
	
	reg =  ;
	
	reg-names = "be";
	
	interrupts =  ;
	
	clocks =  ,  ,
	
		  ;
		 
	clock-names = "ahb", "mod",
	
		      "ram";
		      
	resets =  ;
	
	reset-names = "be";
	
	assigned-clocks =  ;
	
	assigned-clock-rates =  ;
	
    rgb-channel-swap =  ; /* 或者删除这句为RGB格式 */
    
- BGR

be0: display-backend@1e60000 {

	compatible = "allwinner,suniv-f1c100s-display-backend";
	
	reg =  ;
	
	reg-names = "be";
	
	interrupts =  ;
	
	clocks =  ,  ,
	
		  ;
		 
	clock-names = "ahb", "mod",
	
		      "ram";
		      
	resets =  ;
	
	reset-names = "be";
	
	assigned-clocks =  ;
	
	assigned-clock-rates =  ;
	
    rgb-channel-swap =  ; /* 设置为1为BGR格式 */


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)