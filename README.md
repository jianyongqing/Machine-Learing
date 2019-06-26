# Machine Learning


| 走进机器学习的世界 | 机器学习常用工具 | 建模与问题解决流程 | 数据预处理 | 特征工程 | 机器学习算法 | 深度学习 | 自然语言处理 | 计算机视觉 | 
| :--------: | :---------: | :---------: | :---------: | :---------: | :---------:| :---------: | :-------: | :-------:|
| [:fire:](#fire-走进机器学习的世界) | [:memo:](#memo-机器学习常用工具) |[:watermelon:](#watermelon-建模与问题解决流程) | [:art:](#art-数据预处理) |[:pencil2:](#pencil2-特征工程)|  [:floppy_disk:](#floppy_disk-机器学习算法)| [:computer:](#computer-深度学习)| [:cloud:](#cloud-自然语言处理)| [:bulb:](#bulb-计算机视觉)|

<p align="center">
<a>
  <img src="https://github.com/jianyongqing/Machine-Learing/blob/master/res/imgs/%E4%BA%92%E8%81%94%E7%BD%91%E5%AF%B9%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E7%9A%84%E6%8F%8F%E8%BF%B0.jpg"/>
 </a>
</p>

## :fire: 走进机器学习的世界

- [走进机器学习的世界](https://github.com/jianyongqing/Machine-Learing/blob/master/Notes/%E8%B5%B0%E8%BF%9B%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E7%9A%84%E4%B8%96%E7%95%8C/%E8%B5%B0%E8%BF%9B%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E7%9A%84%E4%B8%96%E7%95%8C.md)

## :memo: 机器学习常用工具

- Numpy

  - [Numpy基本操作](https://github.com/jianyongqing/Machine-Learing/blob/master/Notes/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/Numpy%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C.md)

- Pandas

  - [Pandas基本操作](https://github.com/jianyongqing/Machine-Learing/blob/master/Notes/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/Pandas%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C.md)

- Matplotlib

  - [Matplotlib基本操作](https://github.com/jianyongqing/Machine-Learing/blob/master/Notes/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7/Matplotlib%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C.md)

- scikit-learn

----------------------------------------------------------------------------------------------------------------------------------------

## :watermelon: 建模与问题解决流程

    1. 数据预处理
    
    2. 特征工程
    
    3. 模型选择与评估
    
    4. 寻找最佳超参数：交叉验证
    
    5. 模型分析与模型融合

## :art: 数据预处理

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


