# libserv

#### 介绍
跨平台串口通信库

#### Linux用例
```C++
//需要绑定的包校验函数
bool check_function(std::vector  package){
    return true;
}

//需要绑定的消息处理回调
int test_function(void *arg, std::vector  message){
    if (message.size()   package){
    return true;
}

//需要绑定的消息处理回调
int test_function(void *arg, std::vector  message){
    if (message.size() < 11)return 0;
    char *temp_char = new char[message.size()];
    for (int i = 0; i < message.size() - 1; i++) {
        temp_char[i] = message[i];
    }
    std::cout<<"Recive<-"<<clock()<<"  "<<temp_char<<std::endl;
}
int main(int argc,char **argv){
    //打开设备COM9
    Serial serial(9,9600);
    //绑定回调函数
    serial.BindCall(test_function);
    //绑定包校验函数
	serial.BindPackageCheck(check_function);
	//启动接收信息监听
	serial.Run();
	int counter = 12;
	while (true) {
		Sleep(300);
		char buffer[5] = { 0xff,0xaa,0x03,0x03,0x00 };
		serial.AnsySend(buffer, 5);
	}
}
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)