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

## keras
#### model
- tf.keras.Model(inputs,outputs,name), 函数式API
- class Mymodel(tf.keras.Model), 子类model, 子类model需要实现__init__构造函数和前向传播call. 其中training可以控制模型在training和testing阶段拥有不同的策略。
```python
class Mymodel(tf.keras.Model):
	def __init__(self):
		super(Mymodel,self).__init__()
		self.dense1 = tf.keras.layers.Dense(4, activation = tf.nn.relu)
		self.dense2 = tf.keras.layers.Dense(5, activation = tf.nn.softmax)
		self.dropout = tf.keras.layers.Dropout(0.5)
	def call(self, inputs, training=False):
		x = self.dense1(inputs)
		if training:
			x = self.dropout(x)
		return self.dense2(x)
```
注[^super(Mymodel.self)].

[^super(Mymodel.self)]:当子类重写父类构造函数时，如果想要调用父类构造函数时，必须显式调用。

- model.compile(...): 定义模型的config，例如losses，metrics等。
- model.fit(): train the model
- model.predict(): use the model to do prediction
- model.evaluate():
