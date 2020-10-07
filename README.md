# tensorflow-learning
## Install
1. ``` install anaconda```
2. ```conda create -n env_tensorflow pip python=3.7```
3. ```conda activate env_tensorflow```
4. ```pip install --upgrade tensorflow```
5. install Microsoft Visual C++ Redistributable for Visual Studio 2019 from https://visualstudio.microsoft.com/zh-hans/downloads/
6. install cuda 10.1 from https://developer.nvidia.com/cuda-toolkit-archive
7. install jupyter notebook ``` conda install nb_conda```

## error
#### keras.utils.plot_model(): 
1. should install graphviz and pydot first
2. ``` pip install pydot```
3. downloading graphviz from https://graphviz.gitlab.io/
4. setup graphviz
5. add "C:\programfile\graphviz\bin" to PATH of User
6. add "C:\programfile\graphviz\bin\dot.exe" to PATH of System
7. ```conda install graphviz```
8. ```conda install pydotplus```

#### keras.datasets.mnist.load():
通常因为国内无法加载数据，那么我们可以先下载数据，然后根据tensorflow提供的源码自己写一个load_data函数
1. download mnist dataset from https://storage.googleapis.com/tensorflow/tf-keras-datasets/mnist.npz. 该网址可从keras.datasets.mnist.load()的源码中获取
2. load_data函数，用来读取下载的数据
```python
def load_data(path):
  with np.load(path, allow_pickle=True) as f:
    x_train, y_train = f['x_train'], f['y_train']
    x_test, y_test = f['x_test'], f['y_test']

    return (x_train, y_train), (x_test, y_test)
```

## tensorflow
- logits: in tensorflow, means that unnormalized "probability", often as output of dense layer and input of softmax layer
