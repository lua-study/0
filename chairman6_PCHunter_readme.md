# ArkProtect
### Platform in Win7 x86/x64 
## A Windows kernel watch tool which can protect PC somehow 
#### Maybe some bugs exist, please test it in Virtual Machine

## process module:

1. Enumerate processes.

2. Enumerate process's loaded modules.

3. Enumerate process's running threads.

4. Enumerate process's openning handles.

5. Enumerate process's openning windows.

6. Enumerate process's userspace memory.

7. Terminate a process (by force).

## driver module:

1. Enumerate current loaded drivers.

2. Unload target driver.

## kernel module:

1. Enumerate system callbacks.

2. Enumerate filter drivers.

3. Enumerate timer object (IOTimer/ DpcTimer).

## kernel hook:

1. Now, just support ssdthookcheck & sssdthook check, it will support inline hook check in the future.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)