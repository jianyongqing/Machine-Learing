### 一、机器学习简介 ###

- 机器学习应用领域

<table><tr><td>&emsp;&emsp;机器学习已广泛应用于数据挖掘、计算机视觉、自然语言处理、生物特征识别、搜索引擎、医学诊断、检测信用卡欺诈、证券市场分析、DNA序列测序、语音和手写识别、战略游戏和机器人等领域。</table></tr></td>

![](https://i.imgur.com/gzVGzU5.png)

- 机器学习算法分类

![](https://i.imgur.com/CLWcIy9.jpg)

NO1.Group by Learn Style

1. 监督学习

![](https://i.imgur.com/kbfgESu.jpg)

<table><tr><td>
&emsp;&emsp;基本上，在监督机器学习中，输入数据被称为训练数据，并且具有已知的标签或结果，例如垃圾邮件/非垃圾邮件或股票价格。在此，通过训练过程中准备模型。此外，还需要做出预测。并且在这些预测错误时予以纠正。训练过程一直持续到模型达到所需水平。
<br><br>示例问题：分类和回归。<br>示例算法：逻辑回归和反向传播神经网络。
</table></tr></td>

2. 无监督学习

![](https://i.imgur.com/z94FZPJ.jpg)

<table><tr><td>
在无监督机器学习中，输入数据未标记且没有已知结果。我们必须通过推导输入数据中存在的结构来准备模型。这可能是提取一般规则，但是我们可以通过数学过程来减少冗余。
<br><br>示例问题：聚类，降维和关联规则学习。<br>示例算法：Apriori算法和k-Means。
</table></tr></td>

3. 半监督学习

![](https://i.imgur.com/M3p4g9H.jpg)

<table><tr><td>
输入数据是标记和未标记示例的混合。存在期望的预测问题，但该模型必须学习组织数据以及进行预测的结构。
<br><br>示例问题：分类和回归。<br>示例算法：其他灵活方法的扩展。
</table></tr></td>

NO2.Group by Similarity

![](https://i.imgur.com/ECP4c4c.png)

### 二、建模与问题解决流程 ###

1. 数据预处理
2. 特征工程
3. 模型选择与评估
4. 寻找最佳超参数：交叉验证
5. 模型分析与模型融合


### 三、机器学习常用工具 ###

- numpy
> http://www.numpy.org/
- pandas
> http://pandas.pydata.org/
- matplotlib
> https://matplotlib.org/
- scikit-learn
> https://www.sklearn.org/

### 四、数据预处理 ###

1. 导入需要的库
```Python
import numpy as np
import pandas as pd
```
2. 导入数据集
```python
dataset = pd.read_csv('Data.csv')//读取csv文件
X = dataset.iloc[ : , :-1].values//.iloc[行，列]
Y = dataset.iloc[ : , 3].values  // : 全部行 or 列；[a]第a行 or 列
                                 // [a,b,c]第 a,b,c 行 or 列
```
3. 处理丢失数据
```python
from sklearn.preprocessing import Imputer
imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0)
imputer = imputer.fit(X[ : , 1:3])
X[ : , 1:3] = imputer.transform(X[ : , 1:3])
```
4. 解析分类数据
```python
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder_X = LabelEncoder()
X[ : , 0] = labelencoder_X.fit_transform(X[ : , 0])
```
5. 拆分数据集为测试集和训练集
```python
onehotencoder = OneHotEncoder(categorical_features = [0])
X = onehotencoder.fit_transform(X).toarray()
labelencoder_Y = LabelEncoder()
Y =  labelencoder_Y.fit_transform(Y)
```
6. 特征缩放
```python
from sklearn.preprocessing import StandardScaler
sc_X = StandardScaler()
X_train = sc_X.fit_transform(X_train)
X_test = sc_X.transform(X_test)
```

### 五、特征工程 ###

----------

### 五、常用机器学习算法 ###

- 朴素贝叶斯分类器

- K-means：聚类算法

- K邻近算法

- 支持向量机

- Apriori算法

- 线性回归

- 决策树

- 随机森林

- Logistic回归

- 降低维度算法

- Gradient Boost和Adaboost算法



