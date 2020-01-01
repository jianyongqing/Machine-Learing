<h1 align="center">Pandas</h1>

> pandas是基于NumPy的一种工具，该工具是为了解决数据分析任务而创建的。pandas纳入了大量库和一些标准的数据模型，提供了高效地操作大型数据集所需的工具。pandas提供了大量能使我们快速便捷地处理数据的函数和方法。

> Pandas的官方网站是： http://pandas.pydata.org/
	
    # 导入相关库
    import numpy as np
    import pandas as pd

# 一、pandas数据结构

> pandas常用的数据结构有两种：Series 和 DataFrame.

## 1.1 Series

> Series是一个带有名称和索引的一维数组，既然是数组，肯定要说到的就是数组中的元素类型，在 Series中包含的数据类型可以是整数、浮点、字符串、Python对象等.

## 1.2 DataFrame

> DataFrame是一个带有索引的二维数据结构，每列可以有自己的名字，并且可以有不同的数据类型. 你可以把它想象成一个 excel 表格或者数据库中的一张表，DataFrame是最常用的Pandas对象.


# 二、pandas基本功能 

# 三、pandas数据处理

-------------------------------------------------------------------------------------------------------------------------------------------

# 代码笔记

```python
import numpy as np
import pandas as pd 

# user_info = pd.read_csv("../data/user_info.csv")

# pandas数据结构
class Pandas_demo:
    def __init__(self):
        pass

    def series_demo(self):
        # 构建索引
        name = pd.Index(["Tom", "Bob", "Mary", "James"], name="name")
        # 构建 Series
        user_age = pd.Series(data=[18, 30, 25, 40], index=name, name="user_age_info")
        print(user_age)
        print(user_age['Tom'])
        print(user_age[:3]) # 获取前三个元素
        print(user_age[user_age > 30]) # 获取年龄大于30的元素
        print(user_age[[3, 1]]) # 获取第4个和第二个元素

    def dataframe_demo(self):
        index = pd.Index(data=["Tom", "Bob", "Mary", "James"], name="name")
        data = {
            "age": [18, 30, 25, 40],
            "city": ["BeiJing", "ShangHai", "GuangZhou", "ShenZhen"],
            "sex": ["male", "male", "female", "male"]
        }
        user_info = pd.DataFrame(data=data, index=index)

        # 访问行
        print(user_info.loc['Tom'])
        print(user_info.iloc[0])
        print(user_info.iloc[1:3])

        # 访问列
        print(user_info['age']) # 获取所有用户的年龄
        print(user_info[['age','city']]) # 同时获取年龄和城市,可以变换列的顺序
        
        # 新增/删除列
        user_info['sex'] = 'male' # 新增列(所以性别都一样)
        user_info.pop('sex') # 删除'sex'列

        user_info['sex'] = ['male','male', 'female', 'male'] # 新增列(用户的性别不一致)
        print(user_info)

        A = user_info.assign(age_add_one = user_info['age'] + 1) # 想要保证原有的DataFrame不改变的话，我们可以通过assign方法来创建新的一列。
        print(A)

# pandas基本功能
class Pandas_demo2:
    def __init__(self):
        pass
    
    #  以DataFrame为例
    def basic_function(self):
        index = pd.Index(data=["Tom", "Bob", "Mary", "James"], name="name")
        data = {
            "age": [18, 30, 25, 40],
            "city": ["BeiJing", "ShangHai", "GuangZhou", "ShenZhen"],
            "sex": ["male", "male", "female", "male"]
        }
        user_info = pd.DataFrame(data=data, index=index)
    
        print(user_info.info()) # 了解数据的整体情况，可以使用info方法来查看
        print(user_info.head(2)) # 数据量巨大时,可以通过head方法查看头部的n条数据和tail方法查看尾部的n条数据
        print(user_info.tail(2))
        print(user_info.shape) # 通过 .shape 获取数据的形状
        print(user_info.T) # 通过 .T 获取数据的转置
        print(user_info.values) # 通过 .values来获取它包含的原有数据,获取后的数据类型其实是一个ndarray

        # 描述与统计 数据的简单统计指标（最大值、最小值、平均值、中位数等）
        print(user_info.age.max()) # 查看年龄的最大值
        print(user_info.describe()) # 想要一次性获取多个统计指标，只需调用 describe 方法即可.
        print(user_info.describe(include=["object"])) # 如果想要查看非数字类型的列的统计指标，可以设置 include=["object"] 来获得.
        print(user_info.sex.value_counts()) # 统计下某列中每个值出现的次数
        print(user_info.age.idxmax()) # 获取某列最大值对应的索引

        # 离散化
        age_demo = pd.cut(user_info.age,3) # 年龄分成3个区间段
        print(age_demo)
        age_demo2 = pd.cut(user_info.age,[1,18,30,50])
        print(age_demo2)
        age_demo3 = pd.cut(user_info.age,[1,18,30,50],labels=['childhood','youth','middle'])
        print(age_demo3)

        # 排序功能
        sort_age = user_info.sort_values(by='age') # 按照年龄排序
        print(sort_age)

        # 函数应用
        A = user_info.age.map(lambda x: "yes" if x >= 30 else "no")
        print(A)
        
        city_map = {
            "BeiJing": "north",
            "ShangHai": "south",
            "GuangZhou": "south",
            "ShenZhen": "south"
        }
        B = user_info.city.map(city_map)
        print(B)

        # 修改列/索引名称
        C = user_info.rename(columns={"age": "Age", "city": "City", "sex": "Sex"})
        print(C)
        D = user_info.rename(index={"Tom": "tom", "Bob": "bob"})
        print(D)

# 数据处理
class Pandas_demo3:
    def __init__(self):
        pass

    # 缺失值处理
    def data_processing(self):
        index = pd.Index(data=["Tom", "Bob", "Mary", "James", "Andy", "Alice"], name="name")
        data = {
            "age": [18, 30, np.nan, 40, np.nan, 30],
            "city": ["BeiJing", "ShangHai", "GuangZhou", "ShenZhen", np.nan, " "],
            "sex": [None, "male", "female", "male", np.nan, "unknown"],
            "birth": ["2000-02-10", "1988-10-17", None, "1978-08-08", np.nan, "1988-10-17"]
        }
        user_info = pd.DataFrame(data=data, index=index)       
        print(user_info)
        print(user_info.isnull()) # 通过isnull()或notnull()方法判断是否为缺失值
        print(user_info[user_info.age.notnull()]) # 过滤掉用户年龄为空的用户

        # 丢弃缺失值 使用dropna方法可以丢弃缺失值
        '''
        axis 参数用于控制行或列，跟其他不一样的是，axis=0 （默认）表示操作行，axis=1 表示操作列。

        how 参数可选的值为 any（默认） 或者 all。any 表示一行/列有任意元素为空时即丢弃，all 一行/列所有值都为空时才丢弃。

        subset 参数表示删除时只考虑的索引或列名。

        thresh参数的类型为整数，它的作用是，比如 thresh=3，会在一行/列中至少有 3 个非空值时将其保留。
        '''
        print(user_info.dropna(axis=0, how="any")) # 一行数据只要有一个字段存在空值即删除
        print(user_info.dropna(axis=0, how="all")) # 一行数据所有字段都为空值才删除
        print(user_info.dropna(axis=0, how="any", subset=["city", "sex"])) # # 一行数据中只要city或sex 存在空值即删除

        # 填充缺失值 使用fillna方法可以丢弃缺失值
        print(user_info.age.fillna(0)) # 标量填充有缺失的年龄都填充为 0
        print(user_info.age.fillna(method="ffill")) # method="bfill" 使用前一个或后一个有效值来填充

        # 替换缺失值
        print(user_info.age.replace(40, np.nan))
        print(user_info.age.replace({40: np.nan})) # 映射字典
        print(user_info.replace({"age": 40, "birth": pd.Timestamp("1978-08-08")}, np.nan)) # 定每列要替换的值
        print(user_info.sex.replace("unknown", np.nan)) # 将特定字符串进行替换
        print(user_info.city.replace(r'\s+', np.nan, regex=True)) # 除了可以替换特定的值之外，还可以使用正则表达式来替换，如：将空白字符串替换成空值
    
if __name__ == "__main__":
    a = Pandas_demo()
    # a.series_demo()
    # a.dataframe_demo()

    b = Pandas_demo2()
    # b.basic_function()

    c = Pandas_demo3()
    c.data_processing()    
```
