# rexgen_direct
Template-free prediction of organic reaction outcomes using graph convolutional neural networks

Described in [A graph-convolutional neural network model for the prediction of chemical reactivity](https://pubs.rsc.org/en/content/articlelanding/2019/sc/c8sc04228d)

# Dependencies
- Python (trained/tested using 2.7.6, visualization/deployment compatible with 3.6.1)
- Numpy (trained/tested using 1.12.0, visualization/deployment compatible with 1.14.0)
- Tensorflow (trained/tested using 1.3.0, visualization/deployment compatible with 1.6.0)
- RDKit (trained/tested using 2017.09.1, visualization/deployment compatible with 2017.09.3)
- Django (visualization compatible with 2.0.6)

_note: there may be some issues with relative imports when using Python 2 now; this should be easy to resolve by removing the periods preceding package names_

# Instructions 


### Looking at predictions from the test set
```cd``` into the ```website``` folder and start the Django app using ```python manage.py runserver```. Go to ```http://localhost:8000/visualize``` in a browser to use the interactive visualization tool

### Using the trained models
You can use the fully trained model to predict outcomes by following the example at the end of ```rexgen_direct/rank_diff_wln/directcandranker.py```

### Retraining the models
Look at the two text files in ```rexgen_direct/core_wln_global/notes.txt``` and ```rexgen_direct/rank_diff_wln/notes.txt``` for the exact commands used for training, validation, and testing. You will have to unarchive the data files after cloning this repo.


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)