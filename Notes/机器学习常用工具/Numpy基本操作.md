<h1 align="center">Numpy</h1>

> 简单来说，Numpy 是 Python 的一个科学计算包，包含了多维数组以及多维数组的操作。Numpy 的核心是 ndarray(n-dimension-array) 对象，这个对象封装了同质数据类型的n维数组。

> Numpy的官方网站是： http://www.numpy.org/

    # 导入相关库
    import numpy as np

# 一、N维数组 ndarray

     [[0, 1, 2],
      [3, 4, 5]]

## 1.1 构建ndarray

```python
import numpy as np

# 创建列向量
a = np.array([0, 1, 2, 3]) # 1-D(列向量),4 row x 1 col
print(a)

# 创建矩阵
b = np.array([[0, 1, 2], [3, 4, 5]]) # 2-D,2 row x 3 col
print(b)
```

## 1.2 nddaray基本属性

## 1.3 常用数组

# 二、基本操作

# 三、索引,切片和迭代

----------------------------------------------------------------------------------------------------------------------------------------

# 代码笔记

```python
import numpy as np 

class Ndnaray:
    def __init__(self):
        pass

    # 1.1 创建ndarray
    def create_ndarray(self):
        # 创建列向量
        a = np.array([1,2,4])
        print(a)

        # 创建矩阵
        b = np.array([[0,1,2],[3,4,5]])
        print(b)
    
    # 1.2 ndarray基本属性    
    def ndarray_attributive(self):
        a = np.array([[0,1,2],[3,4,5]])
        print(a.shape) # 数组的尺寸,shape将为(n,m)
        print(a.size) # 数组中元素的总个数
        print(a.dtype) # 数组元素的数据类型
        print(a.T) # 数组的转置

        b = np.array([1,2,3],dtype='f')
        print(b.dtype)

    # 1.3 常用数组
    def simple_ndarray(self):
        # 生成0-5数组
        a = np.arange(5)
        print(a)

        # 生成开始为1,结束为5,步长为2的数组
        b = np.arange(1,6,2)
        print(b)

        # 生成单位矩阵
        c = np.eye(3)
        print(c)

        # 生成对角矩阵
        d = np.diag(np.array([1,2,3]))
        print(d)

        # 生成随机矩阵
        e = np.random.rand(2,3) # uniform in [0,1]
        print(e)
    
    # 2. 基本操作
    def basic_operation(self):
        # Numpyz中数组上的算术运算符使用元素级别!!!
        a = np.array([20,30,40,50])
        b = np.arange(4)
        print(a-b)
        print(b**2)
        print(a < 35)

        # 乘法运算符*的运算在NumPy数组中也是元素级别的. 如果想要执行矩阵乘积，可以使用dot函数.
        c = np.array([[1,1], [0,1]])
        d = np.array([[2,0], [3,4]])
        print(c*d) # 元素乘积（elementwise product）
        print(c.dot(d)) # 矩阵相乘（matrix product）

    # 3. 索引,切片和迭代
    def indexing_slcing_iterating(self):
        # 1-D数组的索引
        x = np.arange(10)
        print(x[2]) # >>> 2
        print(x[-2]) # >>> 8
        
        # 2-D数组的索引
        y = np.array([[2,4,6],[1,2,3]])
        print(y[1,2]) # 索引位于2 row x 3 col的数据元素
        y[1,2] = 8
        print(y)

        # 切片
        z = np.array([[ 0,  1,  2,  3],[10, 11, 12, 13],[20, 21, 22, 23],[30, 31, 32, 33],[40, 41, 42, 43]])
        print(z[0:2,1])
        print(z[0:5:2,1])

if __name__ == "__main__":       
    mad = Ndnaray()
    # mad.create_ndarray()
    # mad.simple_ndarray()
    # mad.ndarray_attributive()
    # mad.basic_operation()
    mad.indexing_slcing_iterating()
```








