# IOI

This is an implementation of [One Time of Interaction May Not Be Enough: Go Deep with an Interaction-over-Interaction Network for Response Selection in Dialogues, ACL 2019].


## Requirements
* Ubuntu 16.04
* Tensorflow 1.4.0
* Python 3.5


## Usage
Dowload ubuntu corpus and preprocess the data, run

```bash
# download ubuntu corpus and the pre-trained word2vec file 
sh download.sh

# preprocess the data
python data_utils_record.py
```

All hyper parameters are stored in config.py. To train, run

```bash
python main.py --log_root=logs_ubuntu --batch_size=20
```

To evaluate the model, run
```bash
python evaluate.py --log_root=logs_ubuntu --batch_size=20
```


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)