# tensorflow-learning
### Install
1. ``` install anaconda```
2. ```conda create -n env_tensorflow pip python=3.7```
3. ```conda activate env_tensorflow```
4. ```pip install --upgrade tensorflow```
5. install Microsoft Visual C++ Redistributable for Visual Studio 2019 from https://visualstudio.microsoft.com/zh-hans/downloads/
6. install cuda 10.1 from https://developer.nvidia.com/cuda-toolkit-archive
7. install jupyter notebook ``` conda install nb_conda```

### error
#### keras.utils.plot_model(): 
1. should install graphviz and pydot first
2. ``` pip install pydot```
3. downloading graphviz from https://graphviz.gitlab.io/
4. setup graphviz
5. add "C:\programfile\graphviz\bin" to PATH of User
6. add "C:\programfile\graphviz\bin\dot.exe" to PATH of System
7. ```conda install graphviz```
8. ```conda install pydotplus```
