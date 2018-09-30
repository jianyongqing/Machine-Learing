## python数据分析之matplotlib ##

![](https://i.imgur.com/PFe6cHr.png)

   参考连接：https://matplotlib.org/   画廊：（https://matplotlib.org/gallery.html）
            

Matplotlib 是 Python 的一个绘图库。它包含了大量的工具，你可以使用这些工具创建各种图形，包括简单的散点图，正弦曲线，甚至是三维图形
    
    #导入相关库
    import matplotlib.pyplot as plt
    import numpy as np


### 一、画一个简单的图形 ###
	>> x = np.linspace(0, 2 * np.pi, 50)
	>> y = np.sin(x)
	>> plt.plot(x, y)
	>> plt.show()
	
![](https://i.imgur.com/AkBLK2X.png)


### 二、在一张图纸里绘制多个图形 ###
有时候，可能需要在一个图纸里绘制多个图形，这里我们同时绘制了 (x, y), (x, y * 2)两个图形。
	
    >>	plt.plot(x, y)
	>>	plt.plot(x, y * 2)
	>>	plt.show()

![](https://i.imgur.com/8YI0J7G.jpg)

绘制出图形之后，我们可以自己调整更多的样式，比如颜色、点、线

	>>	plt.plot(x, y, 'y*-')
	>>	plt.plot(x, y * 2, 'm--')
	>>	plt.show()

![](https://i.imgur.com/7NRHhtM.png)	

可以看到，设置样式时，就是增加了一个字符串参数，比如 'y*-' ，其中 y 表示黄色，* 表示 星标的点，- 表示实线。


### 三、更多设置 ###
- 设置figure
 
matplotlib的figure就是一个单独的figure小窗口，小窗口里面还可以有更多的图片。当然，你可以认为Matplotlib绘制的图形都在一个默认的 figure 中，你可以自己创建 figure，好处就是可以控制更多的参数，常见的就是控制图形的大小，如下：
    
    
    >>  plt.figure(figsize=(6, 3))
	>>  plt.plot(x, y)
	>>  plt.plot(x, y * 2)
	>>  plt.show()
	     
   
- 设置标题

直接通过 plt.title 即可设置图形标题
    
    >>  plt.title("sin(x) & 2sin(x)")

![](https://i.imgur.com/yQDqDyQ.jpg)


- 设置坐标轴

通过 xlim 和 ylim 来设限定轴的范围，通过 xlabel 和 ylabel 来设置轴的名称。此外，我们也可以通过 xticks 和 yticks 来设置轴的刻度。	

    >>  plt.plot(x, y) plt.plot(x, y * 2) 
	>>  plt.xlim((0, np.pi + 1)) 
	>>  plt.ylim((-3, 3)) #通过xlim和ylim来限定轴的范围 
	>>  plt.xlabel('X')  
	>>  plt.ylabel('Y') #通过xlabel和ylabel来设置轴的名称
	>>  plt.show()      #此外，也可以通过xticks和yticks来设置轴的刻度

![](https://i.imgur.com/11cKMol.jpg)    


- 设置label和legend

设置 label 和 legend 的目的就是为了区分出每个数据对应的图形名称。
    
    >>  plt.plot(x, y, label="sin(x)")
	>>  plt.plot(x, y * 2, label="2sin(x)") #对两条线绘制图例
	>>  plt.legend(loc='best') #控制图例的位置，best表示自动分配最佳位置
	>>  plt.show()

 ![](https://i.imgur.com/lItaXlC.jpg)   


- 添加注释
    
有时候我们需要对特定的点进行标注，我们可以使用 plt.annotate 函数来实现，也可以使用 plt.text 函数来添加注释。     
   
    >>  plt.scatter(x0, y0, s=50) # 画出标注点 
    >>  plt.annotate(......) # 略 
    >>  plt.text(0.5, -0.25, "sin(np.pi) = 0", fontdict={'size': 16, 'color': 'r'})


### 四、使用子图 ###


### 五、常见的图形 ###
- 散点图
- 柱状图
- 等高线图
- Image图片
- 3D数据


### 六、其他操作 ###

- 中文乱码问题

默认情况下，Matplotlib 中文会乱码。

	>>	x = ['小明', '小红', '小白', '小东']  #注意列表中元素非数字无法简单构造成数组
	>>	y = [80, 76, 90, 92]
	>>	plt.plot(x, y)
	>>	plt.show()

![](https://i.imgur.com/yw72tqv.png)

其实只需要配置下后台字体即可。
		
	>>	plt.rcParams['font.sans-serif']=['SimHei'] #用来正常显示中文标签
	>>	plt.rcParams['axes.unicode_minus']=False #用来正常显示负号

![](https://i.imgur.com/OwShong.png)
