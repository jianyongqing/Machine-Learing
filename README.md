# Machine Learning


| 走进机器学习的世界 | 机器学习常用工具 | 建模与问题解决流程 | 数据预处理 | 特征工程 | 机器学习算法 | 深度学习 | 自然语言处理 | 计算机视觉 | 
| :--------: | :---------: | :---------: | :---------: | :---------: | :---------:| :---------: | :-------: | :-------:|
| [:fire:](#fire-走进机器学习的世界) | [:memo:](#memo-机器学习常用工具) |[:watermelon:](#watermelon-建模与问题解决流程) | [:art:](#art-数据预处理) |[:pencil2:](#pencil2-特征工程)|  [:floppy_disk:](#floppy_disk-机器学习算法)| [:computer:](#computer-深度学习)| [:cloud:](#cloud-自然语言处理)| [:bulb:](#bulb-计算机视觉)|

[https://github.com/jianyongqing/Machine-Learing/blob/master/res/imgs/ML-all%20around%20us.png]

## :fire: 走进机器学习的世界

> 机器学习已广泛应用于数据挖掘、计算机视觉、自然语言处理、生物特征识别、搜索引擎、医学诊断、检测信用卡欺诈、证券市场分析、DNA序列测序、语音和手写识别、战略游戏和机器人等领域。

### 1.1 机器学习算法分类

1. Group by Learn Style

> 广义而言，有三种机器学习算法

- 监督学习

基本上，在监督机器学习中，输入数据被称为训练数据，并且具有已知的标签或结果，例如垃圾邮件/非垃圾邮件或股票价格。在此，通过训练过程中准备模型。此外，还需要做出预测。并且在这些预测错误时予以纠正。训练过程一直持续到模型达到所需水平。
<br><br>示例问题：分类和回归。
<br>示例算法：逻辑回归和反向传播神经网络。

- 无监督学习

在无监督机器学习中，输入数据未标记且没有已知结果。我们必须通过推导输入数据中存在的结构来准备模型。这可能是提取一般规则，但是我们可以通过数学过程来减少冗余。
<br><br>示例问题：聚类，降维和关联规则学习。<br>示例算法：Apriori算法和k-Means。

- 强度学习

该算法训练机器做出具体的决策。它是这样工作的：机器暴露在一个能让它通过反复试错来训练自己的环境中。该机器利用过去的经验进行学习，并尝试透彻地了解并利用这些知识来做出精确的业务决策。强化学习的例子有：马尔科夫决策过程。

NO2.Group by Similarity

![](https://github.com/jianyongqing/Machine-Learing/blob/master/res/imgs/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E7%AE%97%E6%B3%95%E5%88%86%E7%B1%BB.png)

## :memo: 机器学习常用工具

- [Numpy](http://www.numpy.org/) 

- [Pandas](http://pandas.pydata.org/) 

- [Matplotlib](https://matplotlib.org/)

- [scikit-learn](https://www.sklearn.org/)

----------------------------------------------------------------------------------------------------------------------------------------

## :watermelon: 建模与问题解决流程

1. 数据预处理
2. 特征工程
3. 模型选择与评估
4. 寻找最佳超参数：交叉验证
5. 模型分析与模型融合

## :art: 数据预处理

![](https://i.imgur.com/WjljTuC.jpg)

1. 导入需要的库
```Python
import numpy as np
import pandas as pd
```
2. 导入数据集
```python
dataset = pd.read_csv('数据预处理_Data.csv')//读取csv文件
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

## :pencil2: 特征工程

----------

# :floppy_disk: 机器学习算法

- 线性回归

- 逻辑回归

- 决策树

- SVM(支持向量机)

- 朴素贝叶斯

- kNN(k-近邻算法)

- K-Means(K均值算法)

- 随机森林

- 降维算法

- Gradient Boosting算法(梯度提升算法)

  - GBM

  - XGBoost

  - LightGBM

  - CatBoost

----------------------------------------------------------------------------------------------------------------------------------------

## :computer: 深度学习

## :cloud: 自然语言处理

## :bulb: 计算机视觉 


