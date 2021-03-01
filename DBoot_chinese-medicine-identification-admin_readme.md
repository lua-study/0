 
 中药图片拍照识别系统-后端 
 
 
  
  
  
  
  
  
 

## 说明
当前项目是中药识别APP的后端工程，提供纯数据接口；移动端请移步[中药图片拍照识别系统-移动APP端](https://gitee.com/xiaohaoo/chinese-medicine-identification)。

## 项目介绍
**本项目包含五个模块：**

- **admin：**[服务器端](./admin)
- **medicine-collection：**[爬虫工程](./medicine-collection)，用于爬取中药数据      
- **image-cnn-model：**[卷积神经网络工程](./image-cnn-model)   
- **util：**[抽离的项目公用工具类](./util) 
- **datasets：**[数据集](./datasets)

## 项目预览
- 项目运行展示
   
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     

- [视频演示](https://www.bilibili.com/video/BV14T4y157rM)
- [APP下载地址](https://gitee.com/xiaohaoo/chinese-medicine-identification/releases)

## 主要目录结构

```
├─admin
│  └─src
│     ├─main
│     │  ├─java
│     │  │  └─com
│     │  │      └─xiaohao
│     │  │          └─admin
│     │  │              ├─bean
│     │  │              ├─config
│     │  │              ├─controller
│     │  │              ├─dao
│     │  │              └─service
│     │  └─resources
│     │      ├─static
│     │      └─templates
│     └─test
│         └─java
│             └─com
│                 └─xiaohao
│                     └─admin
├─image-cnn-model
│  ├─resources
│  │  ├─keras-model
│  │  ├─model_info
│  │  └─train-log
│  └─src
│     ├─analyse
│     ├─train
│     └─preprocess
├─medicine-collection
│  └─src
│     ├─main
│     │  ├─java
│     │  │  └─xiaohao
│     │  │      ├─datacleaning
│     │  │      └─datacollection
│     │  └─resources
│     │      ├─images
│     │      └─static
│     └─test
│         └─java
│             ├─com
│             └─org
└─util
   └─src
      ├─main
      │  ├─java
      │  │  └─com
      │  │      └─xiaohao
      │  │          ├─bai
      │  │          ├─cnnmodel
      │  │          ├─file
      │  │          ├─img
      │  │          └─mongo
      │  └─resources
      └─test
          └─java
              └─com
                  └─xiaohao
```
## 技术详情
1. **admin服务器端工程**

    Maven构建
    
    SpringBoot框架,一键启动与部署
    
    >:exclamation: :exclamation:提示：[application-demo.yml](./admin/src/main/resources/application-demo.yml)文件仅作为配置示例文件，
    运行时需要重命名为application.yml并自定义配置必要信息。
        
    缓存：MongoDB
    
    全文检索：Elasticsearch + IK分词器
    
    MySQL
    
    基于Java的Deeplearning4j深度学习框架探索
    
2. **medicine-collection爬虫工程**
    
    爬虫主要用来爬取**训练集**以及**中药的详细信息**，主要包含：中药名称、中药形态、图片、
    别名、英文名、配伍药方、功效与作用、临床应用、产地分布、药用部位、
    性味归经、药理研究、主要成分、使用禁忌、采收加工、药材性状等信息。
    
    爬虫框架：WebMagic（[参考代码](./medicine-collection/src/main/java/xiaohao/datacollection/MedicineCountPageProcessor.java)）
    
    数据持久化：MongoDB
    
    数据结构（简略展示）
    
    - 中药一级分类信息
    
    ![](./medicine-collection/src/main/resources/images/中药分类信息.jpg)
    
    - 中药详细信息
    
    ![](./medicine-collection/src/main/resources/images/中药详细信息.jpg)

3. **image-cnn-model卷积神经网络工程**

    Language: Python
    
    使用TensorFlow 深度学习框架，使用Keras会大幅缩减代码量
    
    训练机器：华为Atlas 200 AI开发板（或本地计算机）
    
    [数据集](./datasets)
    
    常用的**卷积网络模型**及在ImageNet上的准确率
    
    |模型|大小|Top-1准确率|Top-5准确率|参数数量|深度|
    |:---:|:---:|:---:|:---:|:---:|:---:|
    |Xception|88 MB|0.790|0.945|22,910,480|126|
    |VGG16|528 MB|0.713|0.901|138,357,544|23|
    |VGG19|549 MB|0.713|0.900|143,667,240|26|
    |ResNet50|98 MB|0.749|0.921|25,636,712|168|
    |ResNet101|171 MB|0.764|0.928|44,707,176|-|
    |ResNet152|232 MB|0.766|0.931|60,419,944|-|
    |ResNet50V2|98 MB|0.760|0.930|25,613,800|-|
    |ResNet101V2|171 MB|0.772|0.938|44,675,560|-|
    |ResNet152V2|232 MB|0.780|0.942|60,380,648|-|
    |ResNeXt50|96 MB|0.777|0.938|25,097,128|-|
    |ResNeXt101|170 MB|0.787|0.943|44,315,560|-|
    |InceptionV3|92 MB|0.779|0.937|23,851,784|159|
    |InceptionResNetV2|215 MB|0.803|0.953|55,873,736|572|
    |MobileNet|16 MB|0.704|0.895|4,253,864|88|
    |MobileNetV2|14 MB|0.713|0.901|3,538,984|88|
    |DenseNet121|33 MB|	0.750|0.923|8,062,504|121|
    |DenseNet169|57 MB|	0.762|0.932|14,307,880|169|
    |DenseNet201|80 MB|0.773|0.936|20,242,984|201|
    |NASNetMobile|23 MB|0.744|0.919|5,326,716|-|
    |NASNetLarge|343 MB|0.825|0.960|88,949,818|-|
    
    由于硬件条件限制，综合考虑模型的准确率、大小以及复杂度等因素，采用了**Xception模型**，
    该模型是134层（包含激活层，批标准化层等）拓扑深度的卷积网络模型。
       
    **Xception函数定义：**
    
    ```python
    def Xception(include_top=True,
        weights='imagenet',
        input_tensor=None,
        input_shape=None,
        pooling=None,
        classes=1000,
        **kwargs)
    
    # 参数
    # include_top：是否保留顶层的全连接网络
    # weights：None代表随机初始化，即不加载预训练权重。'imagenet’代表加载预训练权重
    # input_tensor：可填入Keras tensor作为模型的图像输入tensor
    # input_shape：可选，仅当include_top=False有效，应为长为3的tuple，指明输入图片的shape，图片的宽高必须大于71，如(150,150,3)
    # pooling：当include_top=False时，该参数指定了池化方式。None代表不池化，最后一个卷积层的输出为4D张量。‘avg’代表全局平均池化，‘max’代表全局最大值池化。
    # classes：可选，图片分类的类别数，仅当include_top=True并且不加载预训练权重时可用
    ```
   
    **构建代码**
    
    [基于Xception的模型微调,详细请参考代码](image-cnn-model/src)
      
    1. 设置Xception参数
    
        迁移学习参数权重加载：[xception_weights_tf_dim_ordering_tf_kernels_notop.h5](./image-cnn-model/resources/keras-model/xception_weights_tf_dim_ordering_tf_kernels_notop.h5)
    
        ```python
        # 设置输入图像的宽高以及通道数
        img_size = (299, 299, 3)
        
        base_model = keras.applications.xception.Xception(include_top=False,
                                                        weights='..\\resources\\keras-model\\xception_weights_tf_dim_ordering_tf_kernels_notop.h5',
                                                        input_shape=img_size,
                                                        pooling='avg')
        
        # 全连接层，使用softmax激活函数计算概率值，分类大小是628
        model = keras.layers.Dense(628, activation='softmax', name='predictions')(base_model.output)
        model = keras.Model(base_model.input, model)
        
        # 锁定卷积层
        for layer in base_model.layers:
          layer.trainable = False
        ```
    
    2. 全连接层训练(v1.0)
    
        ```python
        from base_model import model
       
        # 设置训练集图片大小以及目录参数
        img_size = (299, 299)
        dataset_dir = '..\\datasets\\dataset'
        img_save_to_dir = 'resources\\image-traing\\'
        log_dir = 'resources\\train-log'
        
        model_dir = 'resources\\keras-model\\'
       
        # 使用数据增强
        train_datagen = keras.preprocessing.image.ImageDataGenerator(
            rescale=1. / 255,
            shear_range=0.2,
            width_shift_range=0.4,
            height_shift_range=0.4,
            rotation_range=90,
            zoom_range=0.7,
            horizontal_flip=True,
            vertical_flip=True,
            preprocessing_function=keras.applications.xception.preprocess_input)
        
        test_datagen = keras.preprocessing.image.ImageDataGenerator(
            preprocessing_function=keras.applications.xception.preprocess_input)
        
        train_generator = train_datagen.flow_from_directory(
            dataset_dir,
            save_to_dir=img_save_to_dir,
            target_size=img_size,
            class_mode='categorical')
        
        validation_generator = test_datagen.flow_from_directory(
            dataset_dir,
            save_to_dir=img_save_to_dir,
            target_size=img_size,
            class_mode='categorical')
        
        # 早停法以及动态学习率设置
        early_stop = EarlyStopping(monitor='val_loss', patience=13)
        reduce_lr = ReduceLROnPlateau(monitor='val_loss', patience=7, mode='auto', factor=0.2)
        tensorboard = keras.callbacks.tensorboard_v2.TensorBoard(log_dir=log_dir)
        
        for layer in model.layers:
            layer.trainable = False
       
        # 模型编译
        model.compile(optimizer='rmsprop', loss='categorical_crossentropy', metrics=['accuracy'])
        
        history = model.fit_generator(train_generator,
                                      steps_per_epoch=train_generator.samples // train_generator.batch_size,
                                      epochs=100,
                                      validation_data=validation_generator,
                                      validation_steps=validation_generator.samples // validation_generator.batch_size,
                                      callbacks=[early_stop, reduce_lr, tensorboard])
        # 模型导出
        model.save(model_dir + 'chinese_medicine_model_v1.0.h5')
        ```
    
    3. 对于顶部的6层卷积层，我们使用数据集对权重参数进行微调
       ```python
        # 加载模型
        model=keras.models.load_model('resources\\keras-model\\chinese_medicine_model_v2.0.h5')
        
        for layer in model.layers:
           layer.trainable = False
        for layer in model.layers[126:132]:
           layer.trainable = True
       
        history = model.fit_generator(train_generator,
                                      steps_per_epoch=train_generator.samples // train_generator.batch_size,
                                      epochs=100,
                                      validation_data=validation_generator,
                                      validation_steps=validation_generator.samples // validation_generator.batch_size,
                                      callbacks=[early_stop, reduce_lr, tensorboard])
        model.save(model_dir + 'chinese_medicine_model_v2.0.h5')

       ```
    4. 在后端项目中，我们使用Deeplearn4j调用训练好的模型
        
        ```java
        public class CnnModelUtil {
        
            private static ComputationGraph CNN_MODEL = null;
        
            /**
             * 中药名字的编码
             */
            private static final Map  MEDICINE_NAME_MAP = new HashMap<>();
        
            /**
             * 定义cnn model的文件夹路径
             */
            private static final String DATA_DIR = System.getProperty("os.name")
                    .toLowerCase().contains("windows") ? "D:\\data\\model\\"
                    : "./data/model/";
        
            /**
             * 定义中药编码表的文件名
             */
            private static final String MEDICINE_LABLE_FILE_NAME = "medicine_name-lable.txt";
        
            /**
             * 定义模型的文件名
             */
            private static final String CNN_MODEL_FILE_NAME = "chinese_medicine_model.h5";
        
        
            /**
             * 图片的加载器
             */
            private static final NativeImageLoader IMAGE_LOADER = new NativeImageLoader(299, 299, 3);
        
        
            /**
             * 初始化
             */
            static {
                try {
                    CNN_MODEL = KerasModelImport.importKerasModelAndWeights(DATA_DIR + CNN_MODEL_FILE_NAME);
        
                    Files.readAllLines(Paths.get(DATA_DIR, MEDICINE_LABLE_FILE_NAME)).forEach(v -> {
                        String[] split = v.split(",");
                        MEDICINE_NAME_MAP.put(Integer.valueOf(split[1]), split[0]);
                    });
                } catch (IOException | InvalidKerasConfigurationException | UnsupportedKerasConfigurationException e) {
                    e.printStackTrace();
                }
            }
        
            /**
             * 对图像进行预测
             * 对预测的概率值进行排序处理
             * 返回值是概率值前10的中药的名字
             * @param file
             * @return
             * @throws IOException
             */
            public static Map  medicineNamePredict(File file) throws IOException {
                INDArray image = IMAGE_LOADER.asMatrix(file).divi(127.5).subi(1);
                INDArray output = CNN_MODEL.outputSingle(image);
                Map  resultMap = new HashMap<>();
                float[] floats = output.toFloatVector();
                for (int i = 0; i  > resultList = new LinkedList<>(resultMap.entrySet());
                resultList.sort(Map.Entry.comparingByValue(Comparator.reverseOrder()));
                Map  medicinePredict = new LinkedHashMap<>();
                resultList.stream().limit(10).forEach(v -> {
                    medicinePredict.put(MEDICINE_NAME_MAP.get(v.getKey()), v.getValue());
                });
                return medicinePredict;
            }
        }
       ```     
     
    **模型概览**
    
    [模型详细参数](./image-cnn-model/resources/model_info/model_summary.txt)
    
    [模型详细结构](./image-cnn-model/resources/model_info/model.png)
    
    **训练过程正确率以及损失函数可视化展示**
    
    ![正确率](./image-cnn-model/resources/model_info/正确率.png)
    ![损失函数](./image-cnn-model/resources/model_info/损失函数.png)
      
4. **数据集**
    - [数据集1：](./datasets/dataset2)包含约200张图片，像素：600*536
    - [数据集2：](./datasets/dataset2)包含约417张图片，像素：640*426
    - [数据集3：](./datasets/dataset3)包含约628张图片，像素：250*200
    - [中药名字编码表](datasets/medicine_name-lable.txt)
    
5. **util公用工具类**

- 关于[MongoDbUtil](util/src/main/java/com/xiaohao/mongo)说明

    >:exclamation: :exclamation:提示：[mongodb-demo.properties](./util/src/main/resources/mongodb/mongodb-demo.properties)
    >文件仅作为配置示例文件，运行时需要重命名为mongodb.properties并自定义配置必要信息。
## 依赖环境说明

|依赖|版本|
|:---:|:---:|
|JDK|8+|
|Python|3.6|
|Maven|3.0+|
|TensorFlow|2.0|
|mongoDB|4.2.2|
|mongo-java-driver|3.12|
|MySQL|8.0+|
|Spring Boot|2.2.2|
|Elasticsearch|7.4.2|
|IK分词器|7.4.2|
|deeplearning4j|1.0.0-beta6|
|nd4j-native-platform|1.0.0-beta6|
    
## 开源软件使用须知
- **允许用于个人学习;**
- **开源版不适合商用;**
- **禁止将本项目的代码和资源进行任何形式的出售，产生的一切任何后果责任由侵权者自负;**
- **[LICENSE](LICENSE)**


## 交流、反馈与参与贡献
- 如需关注项目最新动态，请Watch、Star项目，同时也是对项目最好的支持
- 欢迎参与技术讨论、二次开发等咨询、问题和建议！
- QQ：993021993
- 微信：

  ![WECHAT][WECHAT]

#### 喜欢的朋友请star一下，让我更有信心的去维护，谢谢！^_^

[WECHAT]:data:image/png;base64,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/vKL448/nrbddtuau8FIq+oNYOk4+eSTQy9gRx11VOj0YzDRmjwjW4ooEriddtpp2gRxt99+exTFB8KRRx6prctjjz1WLUYmGkTivSAJ784++2xtVY477jjt/XfccUfNvSMjI96sWbNCJ987//zzfXcL2rv55puHfqbpc9lll/mqA7By5UptOfPmzQv13iW22morbfm6JIsYE/J7y7Kqf2MMtRuYK7p6Y25FgWl9RsfKGoROWRcCSorozsXuoFTNr1YESTIJiU7HGAMu9WbRSHQ3JVmcTugo4zroYBqgM9E76GAaoKUTfTI0xlIsbEVYpinCyuSnrXOMMTHMkCEIxoRWO6oEKb9VWvrJCjedDKtDq+dKSw8uH//4x1tq7tDh73//e+hIrW222YbOPffcmutPPvmk0LzyABQ8A9r466+/vvpvqkxaJJlUJzXOitdcc00N5RHIKEDgoMZdI+EfNMaybOkLD8046qLi85//PO28886+2omUTNCAq9xs8OkHfbMKaNdB4awCue6uvvrqar/Iun/zm98MdfYG/vSnP9EPf/jDGj/6D3/4w4IGOipwSwfyzoHau16EYlTQxR20BFFo9Exa98n6QIMai8U827brat1feeUVL5PJ1NTzwAMP1LbzBz/4gbZNV155pfb+JUuWaO/XYdWqVdXvUXepBf7oRz+qvf+MM87Qlr106dKae1Wtuyx78eLF2rIffvhhbdnnnXee9v7DDz9ce//9998/ob+BNWvWeD09PTX37rbbbtqyv/nNb9atCy8b2GuvvWruxTvGu1bBte7yw8dMuz94769KrXuztLjNfiRlcT1iCD/I5XLVu3g5UnTn1MikiO48cMRE67xmzZqaslUnInm/zCJjojlWRX0/mn5ZBuqqo2pGYgcdBgcHJ9RbliOPS5wxlRhRY5hdUdJgWwpNtwwZjgo6NttmqMiDfFS681YeVVoqurf7jMXFr6gIHPggVemL1Zdjirs23cPv5eYfvlio5akhm1FRD/PnmGiaTEQOnHjCVJ9mSSn5gtrKPHS6+rWCBET3XFL48VuBUBOds5ZOFZgoi/n1ZncY+Ts+sImxoKhKtCAKLbW+ctLIMtSym8k7p4Nu8prqbXomlxBM98vysaDplJomRWcjCmr1XepCcU3530xjpF3gzzPNoagIM5oW3dVd6tWEqOrLV+Mo8VqhPgrS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zi/a7jCDztp5551rztdwGPjHP/4RunyYgeACqwK51/wSEKIuujLgdKFLJhkEOFpA0aema8ICpfPGaiUgFuJdqIB5TvcuIHLq+sUEv6m66gHeaLq6wDNSh+222863YwvGA8aFCpyh0QcqoKTT1QUurdKcyYHcgCpzDEylrYxSM8KLAKeddppXUc80/CQSCW90dLTmoa+88orvMup9fvOb32gbtP3229f8bt68ed74+LjvDrjiiisaPt+yrOrff//7332X/dxzz2nLaOVniy220Nblzjvv1D73zDPPbHqwuK4r/rtmzRqvp6cn0nbx/nr44Yd91+nFF1/UlnHsscdq7z/77LO1z//Vr37VdL9I3H777dqyMbeiwKSI7jpNYlhNuYRJXIyCR7uVlMQmcbmVMFk9TEeXVvtjR4Eg/Wi6N+iRo5UJPKPCpEx0HqcrEdW5pZXnn1aWHbXN1i8a2dRfbQhSd1OfB23/q2EB7GjdO+hgGiDURJcrH9wz/QJikU40akQk4BcmRYxOAwrlWtT5tJsFd4pp147K4/M5dIolMrxnv5IIjyJs5pjm10deF7pqAmde5X0etH4mumc/kM81WYuiskY1fbjg3luHHnqo7wkDP2oQOKq+3tB0gqpXfZng+0bwhjr4d9llF+HWqAJsLZKQkf/muOOOq/EwQ12+//3v1zjIYACgTe0Envmxj32src+E5YPnu5N9Bh2Kri6HHHKItpzbbrutYay2LBuuu5/85Cd96Uzwm//+97905513+roX5V966aVCC+4H0Lno2omFTtcvOIvr7oemX60LJvq1115b1QPIcQ5abpBxoCw+B0BQoiv7wAMP9NWWhmhWoVcqlTzHccSnGeB3sgypkdXhwQcf1GojL7zwQu39Bx98sPb+wcFB7f26ezfbbDPtvZdccklLtO712t9KoO91bdh1110DPXXfffcNpCUPgqVLl4rf2LbtxWIxbXm4ju/xCVKP/v5+bU1uvfVW7f3nnntuoLqb6pPP58X3fA60GqFEd4vR4HIFW70P7pVBA2osufwvypIrPsRLHaQYqYYv8nBEbq+U5XCxCs4LMvEBr4/fVM9RAu2VdcOu16gfw3wkIPlIaYZH+kkSBN0zdJApqVEWj1iTH84uAzsy3+XqfUjJj15PfJf3Y6eUban3oQodtwSPpORWIR3zq58+wfVFixZV+0W2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

    


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)