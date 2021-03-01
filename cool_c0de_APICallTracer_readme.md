# ApiCallTracer
A Tool for instrumentation of Android apps. We instrument the apps to record which API method gets executed along with the class and function name it was called in.

Several tools exist which log API methods but does not log the class name and function name they were called in. The logs collected in this format helps in static analysis using SecFlowDroid*. SecFlowDroid* deploys a hybrid approach utilizing both dyanamic analysis followed by static analysis techniques. The ApiSeqLogger is a part of SecFlowDroid+ which takes care of dyanamic analysis part.
For getting the list of sensitive APIs to instrument APK with refer Pscout, SuSi or axplorer.
## Prerequisite
1. Unix-like OS
2. Apktool
3. Python-2.7
4. Keytool and Jarsigner command should work
5. Adb command should work
## Usage
Create your signature using keytool for signing Android apps after instrumenting it.  
```keytool -genkey -v -keystore my-releasekey.keystore -alias alias_name -keyalg RSA -validity 10000```  
From the main directory run instrument.sh script on your terminal.  
```./instrument.sh   ```  

After instrumenting apk this script also signs the APK. It will prompt for your password to sign the APK.   
The instrumented APK is present in ` /dist/` folder.
For automated exploration of apps setup DroidBot. Script to run DroidBot and start Android Emulator is present in `Scripts folder`.  
Install the app on device or emulator and run the app.  
Use following command to log:  
  ```
  adb logcat -c  
  adb logcat -s Prashant  
```
  
To perform static analysis using SecFlowDroid* we need to edit log using the editLog.py(removes time and first two lines which is not part of log).  

```python edit_log.py  ```  

For SecFlowDroid visit https://github.com/asifazamali/secflowdroid






 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)