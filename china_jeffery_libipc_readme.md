#libipc
* 使用Windows命令管道实现进程间通信，目前仅支持windows平台
* 提供纯C接口，支持多语言调用
* 支持多实例，线程安全
* 占用系统资源低，支持高并发
* 这不是一个玩具

#使用方法
##服务端
    #include "stdafx.h"
	#pragma comment(lib, "../../Debug/libipc_d.lib")

	#include "../../src/libipc.h"

	DWORD WINAPI ListenCallback(H_IPC ipc, LPVOID pvMsg, DWORD dwMsgSize, BOOL bNeedAnswer, LPVOID pvAnswer, DWORD dwAnswerMaxSize) {
	    char szMsg[1024] = {0};
	    memcpy(szMsg, pvMsg, dwMsgSize);
	
	    printf("Recv: %s\n", szMsg);
	
	    DWORD dwAnswerSize = 0;
	
	    if(bNeedAnswer) {
	        if(pvAnswer) {
	            char szRsp[] = "Hi, I'm server.";
	            int iRspLen  = strlen(szRsp);
	
	            if(0 == memcpy_s(pvAnswer, dwAnswerMaxSize, szRsp, iRspLen))
	                dwAnswerSize = iRspLen;
	        }
	    }
	
	    return dwAnswerSize;
	}


	int _tmain(int argc, _TCHAR *argv[]) {
	    H_IPC h = IPC_Init();
	    IPC_SetMaxConcurrent(h, 255);
	    BOOL bRet = IPC_Create(h, TEXT("TEST"), ListenCallback);
	
	
	    getchar();
	
	    IPC_Release(h);
	
	    getchar();
	    return 0;
	}


##客户端
    #include "stdafx.h"
	#include  
	#pragma comment(lib, "../../Debug/libipc_d.lib")


	#include "../../src/libipc.h"

	unsigned __stdcall ThreadProc(void *param) {
	    unsigned long flag = 1;
	
	    while(1) {
	        char szMsg[20] = "I am a client.";
	        char szRsp[21] = {0};
	        DWORD dwRspSize = 20;
	        LONG dwRet = 0;
	
	        dwRet = IPC_SendMessage(TEXT("TEST"), szMsg, strlen(szMsg), szRsp, dwRspSize, 10000);
	
	        if(dwRet   %s\n", flag++, szMsg, szRsp);
	        }
	
	        Sleep(1);
	    }
	
	    return 1;
	}


	unsigned __stdcall Test4ThreadProc(void *param) {
	    unsigned long flag = 1;
	
	    while(1) {
	        char szMsg[50] = "I am a client from Test4ThreadProc.";
	        char szRsp[21] = {0};
	        DWORD dwRspSize = 20;
	        LONG dwRet = 0;
	
	        dwRet = IPC_SendMessage(TEXT("TEST"), szMsg, strlen(szMsg), szRsp, dwRspSize, 20000);
	
	        if(dwRet   %s\n", flag++, szMsg, szRsp);
	        }
	
	        Sleep(1);
	    }
	
	    return 1;
	}
	
	unsigned __stdcall Test4ThreadProc2(void *param) {
	    unsigned long flag = 1;
	
	    while(1) {
	        char szMsg[50] = "I am a client from Test4ThreadProc2.";
	        char szRsp[21] = {0};
	        DWORD dwRspSize = 20;
	        LONG dwRet = 0;
	
	        dwRet = IPC_SendMessage(TEXT("TEST"), szMsg, strlen(szMsg), szRsp, dwRspSize, 20000);
	
	        if(dwRet   %s\n", flag++, szMsg, szRsp);
	        }
	
	        Sleep(1);
	    }
	
	    return 1;
	}
	
	unsigned __stdcall Test4ThreadProc3(void *param) {
	    unsigned long flag = 1;
	
	    while(1) {
	        char szMsg[50] = "I am a client from Test4ThreadProc3.";
	        char szRsp[21] = {0};
	        DWORD dwRspSize = 20;
	
	        BOOL bRet = IPC_PostMessage(TEXT("TEST"), szMsg, strlen(szMsg));
	
	        if(!bRet) {
	            printf("Post Error.\n");
	        }
	        else {
	            printf("[%d] Post %s\n", flag++, szMsg);
	        }
	
	        Sleep(1);
	    }
	
	    return 1;
	}
	
	void Test1() {
	    _beginthreadex(NULL, 0, ThreadProc, NULL, 0, NULL);
	}
	
	void Test2() {
	    char szMsg[20] = "I am a client.";
	    char szRsp[21] = {0};
	    DWORD dwRspSize = 20;
	    DWORD dwRet = 0;
	
	    dwRet = IPC_SendMessage(TEXT("TEST"), szMsg, strlen(szMsg), szRsp, dwRspSize, 60000);
	
	    if(dwRet   %s\n", szMsg, szRsp);
	    }
	}
	
	void Test3() {
	    char szMsg[50] = "[test3] I am a client.";
	    DWORD dwRet = 0;
	
	    dwRet = IPC_PostMessage(TEXT("TEST"), szMsg, strlen(szMsg));
	
	    if(dwRet <= 0) {
	        printf("Send Error: %d\n", dwRet);
	    }
	}
	
	void Test4() {
	    _beginthreadex(NULL, 0, Test4ThreadProc, NULL, 0, NULL);
	    _beginthreadex(NULL, 0, Test4ThreadProc2, NULL, 0, NULL);
	    _beginthreadex(NULL, 0, Test4ThreadProc3, NULL, 0, NULL);
	}
	
	int _tmain(int argc, _TCHAR *argv[]) {
	    Test4();
	
	    getchar();
	    return 0;
	}
	


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)