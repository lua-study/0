EN|[CN](README_cn.md)

# Face Detection  

Developers can deploy the application on the Atlas 200 DK to collect camera data in real time and predict facial information in the video.

## Prerequisites  

Before using an open source application, ensure that:

-   Mind Studio  has been installed.
-   The Atlas 200 DK developer board has been connected to  Mind Studio, the cross compiler has been installed, the SD card has been prepared, and basic information has been configured.

## Software Preparation  

Before running the application, obtain the source code package and configure the environment as follows.

1.    Obtain the source code package.

    Download all the code in the sample-facedetection repository at  [https://gitee.com/Atlas200DK/sample-facedetection](https://gitee.com/Atlas200DK/sample-facedetection)  to any directory on Ubuntu Server where  Mind Studio  is located as the  Mind Studio  installation user, for example,  $HOME/sample-facedetection/.

2.    Obtain the source network model required by the application.

    Obtain the source network model and its weight file used in the application by referring to  [Table 1](#en-us_topic_0182554577_table144841813177), and save them to any directory on the Ubuntu server where  Mind Studio  is located (for example,  **$HOME/ascend/models/facedetection**).

    **Table  1**  Models used for face detection

      
             Model Name 
     
          Model Description 
     
          Model Download Path 
     
     
     
            face_detection 
     
          Network model for face detection. 
         It is a network model converted from ResNet10-SSD300 model based on Caffe. 
     
          Download the source network model file and its weight file by referring to      README.md  in  https://gitee.com/HuaweiAscend/models/tree/master/computer_vision/object_detect/face_detection . 
     
     
     
     

3.  Convert the source network model to a Da Vinci model.
    1.  Choose  **Tool \> Convert Model**  from the main menu of  Mind Studio. The  **Convert Model**  page is displayed.
    2.  On the  **Convert Model**  page, set  **Model File**  and  **Weight File**  to the model file and weight file downloaded in  [2](#en-us_topic_0182554577_li1365682471610), respectively.

        See  [Figure 1](#en-us_topic_0182554577_fig1954118512311).

        -   Set  **Model Name**  to the model name in  [Table 1](#en-us_topic_0182554577_table144841813177):  **face\_detection**.
        -   Retain default values for other parameters.

        **Figure  1**  face\_detection model conversion configuration    
        ![](doc/source/img/face_detection-model-conversion-configuration.jpg "face_detection-model-conversion-configuration")

    3.  Click  **OK**  to start model conversion.

        During the conversion, the following error will be reported.

        **Figure  2**  Model conversion error    
        ![](doc/source/img/model-conversion-error.jpg "model-conversion-error")

        Select  **SSDDetectionOutput**  from the  **Suggestion**  drop-down list box at the  **DetectionOutput**  layer and click  **Retry**.

        After successful conversion, a .om model file is generated in the  **$HOME/tools/che/model-zoo/my-model/face\_detection** directory.

        See the following figure.

        **Figure  3**  Successful model conversion    
        ![](doc/source/img/successful-model-conversion.jpg "successful-model-conversion")

4.  Upload the converted .om model file to the  **sample-facedetection/script**  directory in the source code path in  [1](#en-us_topic_0182554577_li953280133816).
5.  Log in to Ubuntu Server where  Mind Studio  is located as the  Mind Studio  installation user and set the environment variable  **DDK\_HOME**.

    **vim \~/.bashrc**

    Run the following commands to add the environment variables  **DDK\_HOME**  and  **LD\_LIBRARY\_PATH**  to the last line:

    **export DDK\_HOME=$HOME/tools/che/ddk/ddk**

    **export LD\_LIBRARY\_PATH=$DDK\_HOME/uihost/lib**

    >![](doc/source/img/icon-note.gif) **NOTE:**    
    >-   If the environment variables have been added, skip this step.  

    Enter  **:wq!**  to save and exit.

    Run the following command for the environment variable to take effect:

    **source \~/.bashrc**


## Deployment  

1.  Access the root directory where the face detection application code is located as the  Mind Studio  installation user, for example,  **$HOME/sample-facedetection**.
2.  Run the deployment script to prepare the project environment, including compiling and deploying the ascenddk public library and configuring Presenter Server. The Presenter Server is used to receive the data sent by the application and display the result through the browser.

    **bash deploy.sh** _host\_ip_ _model\_mode_

    -   _host\_ip_: For the Atlas 200 DK developer board, this parameter indicates the IP address of the developer board.
    -   _model\_mode_  indicates the deployment mode of the model file. The default setting is  **internet**.
        -   **local**: If the Ubuntu system where  Mind Studio  is located is not connected to the network, use the local mode. In this case, download the dependent common code library to the  **sample-facedetection/script**  directory by referring to  [Downloading Dependent Code Library](#en-us_topic_0182554577_section4995103618210).
        -   **internet**: Indicates the online deployment mode. If the Ubuntu system where  Mind Studio  is located is connected to the network, use the Internet mode. In this case, download the dependent code library online.


    Example command:

    **bash deploy.sh 192.168.1.2 internet**

    When the message  **Please choose one to show the presenter in browser\(default: 127.0.0.1\):**  is displayed, enter the IP address used for accessing the Presenter Server service in the browser. Generally, the IP address is the IP address for accessing the  Mind Studio  service.

    Select the IP address used by the browser to access the Presenter Server service in  **Current environment valid ip list**, as shown in  [Figure 4](#en-us_topic_0182554577_fig184321447181017).

    **Figure  4**  Project deployment    
    ![](doc/source/img/project-deployment.png "project-deployment")

3.    Start Presenter Server.

    Run the following command to start the Presenter Server program of the face detection application in the background:

    **python3 presenterserver/presenter\_server.py --app face\_detection &**

    >![](doc/source/img/icon-note.gif) **NOTE:**   
    >**presenter\_server.py**  is located in the  **presenterserver**  in the current directory. You can run the  **python3 presenter\_server.py -h**  or  **python3 presenter\_server.py --help**  command in this directory to view the usage method of  **presenter\_server.py**.  

    [Figure 5](#en-us_topic_0182554577_fig69531305324)  shows that the presenter\_server service is started successfully.

    **Figure  5**  Starting the Presenter Server process    
    ![](doc/source/img/starting-the-presenter-server-process.png "starting-the-presenter-server-process")

    Use the URL shown in the preceding figure to log in to Presenter Server \(only the Chrome browser is supported\). The IP address is that entered in  [Figure 6](#en-us_topic_0182554577_fig64391558352)  and the default port number is  **7007**. The following figure indicates that Presenter Server is started successfully.

    **Figure  6**  Home page    
    ![](doc/source/img/home-page.png "home-page")

    The following figure shows the IP address used by the Presenter Server and  Mind Studio  to communicate with the Atlas 200 DK.

    **Figure  7**  Example IP Address    
    ![](doc/source/img/example-ip-address.png "example-ip-address")

    Where:

    -   The IP address of the Atlas 200 DK developer board is 192.168.1.2 \(connected in USB mode\).
    -   The IP address used by the Presenter Server to communicate with the Atlas 200 DK is in the same network segment as the IP address of the Atlas 200 DK on the UI Host server. For example: 192.168.1.223.
    -   The following is an example of accessing the IP address of the Presenter Server using a browser: 10.10.0.1, because the Presenter Server and  Mind Studio  are deployed on the same server, the IP address is also the IP address for accessing the  Mind Studio  through the browser.


## Running  

1.  Run the face detection application.

    Run the following command in the  **sample-facedetection**  directory to start the face detection application:

    **bash run\_facedetectionapp.sh** _host\_ip_ _presenter\_view\_app\_name camera\_channel\_name_  &

    -   _host\_ip_: For the Atlas 200 DK developer board, this parameter indicates the IP address of the developer board.
    -   _presenter\_view\_app\_name_: Indicates  **View Name**  displayed on the Presenter Server page, which is user-defined. The value of this parameter must be unique on the Presenter Server page, which contains only case-senstive leters, digits, and underscores(_). The number of characters should be 3-20.
    -   _camera\_channel\_name_: Indicates the channel to which a camera belongs. The value can be  **Channel-1**  or  **Channel-2**. For details, see  **View the Channel to Which a Camera Belongs**  in  [Atlas 200 DK User Guide](https://ascend.huawei.com/documentation).

    Example command:

    **bash run\_facedetectionapp.sh 192.168.1.2 video Channel-1 &**

2.  Use the URL that is displayed when you start the Presenter Server service to log in to the Presenter Server website. For details, see  [3](#en-us_topic_0182554577_li499911453439).

    Wait for Presenter Agent to transmit data to the server. Click  **Refresh**. When there is data, the icon in the  **Status**  column for the corresponding channel changes to green, as shown in  [Figure 8](#en-us_topic_0182554577_fig113691556202312).

    **Figure  8**  Presenter Server page    
    ![](doc/source/img/presenter-server-page.png "presenter-server-page")

    >![](doc/source/img/icon-note.gif) **NOTE:**   
    >-   The Presenter Server of the face detection application supports a maximum of 10 channels at the same time \(each  _presenter\_view\_app\_name_  parameter corresponds to a channel\).  
    >-   Due to hardware limitations, the maximum frame rate supported by each channel is 20fps, a lower frame rate is automatically used when the network bandwidth is low.  

3.  Click  **image**  or  **video**  in the  **View Name**  column and view the result. The confidence of the detected face is marked.

## Follow-up Operations  

-   **Stopping the Face Detection Application**

    The face detection application is running continually after being executed. To stop it, perform the following operation:

    Run the following command in the **$HOME/sample-facedetection** directory as the  Mind Studio  installation user:

    **bash stop\_facedetectionapp.sh** _host\_ip_

    _host\_ip_: For the Atlas 200 DK developer board, this parameter indicates the IP address of the developer board. For the Atlas 300 PCIe card, this parameter indicates the IP address of the PCIe card host.

    Example command:

    **bash stop\_facedetectionapp.sh 192.168.1.2**

-   **Stopping the Presenter Server Service**

    The Presenter Server service is always in the running state after being started. To stop the Presenter Server service of the face detection application, perform the following operations:

    Run the following command to check the process of the Presenter Server service corresponding to the face detection application as the  Mind Studio  installation user:

    **ps -ef | grep presenter | grep face\_detection**

    ```
    ascend@ascend-HP-ProDesk-600-G4-PCI-MT:~/sample-facedetection$ ps -ef | grep presenter | grep face_detection 
    ascend    7701  1615  0 14:21 pts/8    00:00:00 python3 presenterserver/presenter_server.py --app face_detection
    ```

    In the preceding information,  _7701_  indicates the process ID of the Presenter Server service corresponding to the face detection application.

    To stop the service, run the following command:

    **kill -9** _7701_


## Downloading Dependent Code Library  

Download the dependent software libraries to the  **sample-facedetection/script**  directory.

**Table  2**  Download the dependent software library

  
         Module Name 
 
      Module Description 
 
      Download Address 
 
 
 
        EZDVPP 
 
      Encapsulates the DVPP interface and provides image and video processing capabilities, such as color gamut conversion and image / video conversion 
 
       https://gitee.com/Atlas200DK/sdk-ezdvpp  
     After the download, keep the folder name       ezdvpp  . 
 
 
       Presenter Agent 
 
       API for interacting with the Presenter Server . 
 
       https://gitee.com/Atlas200DK/sdk-presenter/tree/master  
     Obtain the presenteragent folder in this path, after the download, keep the folder name       presenteragent  . 
 
 
       tornado (5.1.0) 
     protobuf (3.5.1) 
     numpy (1.14.2) 
 
      Python libraries that Presenter Server depends on. 
 
      You can search for related packages on the Python official website  https://pypi.org/  for installation. If you run the pip3 install command to download the file online, you can run the following command to specify the version to be downloaded:      pip3 install tornado==5.1.0 -i      Installation source of the specified library  --trusted-host      Host name of the installation sourc e  
 
 
 
 



 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)