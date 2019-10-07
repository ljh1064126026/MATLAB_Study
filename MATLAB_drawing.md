# MATLAB绘图
## MATLAB二维绘图
> 注意要先制定x ,y的**取值范围** 再代入函数中生成图像

### 离散绘图
* figure: create a figure window
* h=stem(y): 以x=1 ,2 ,3...作为横坐标，向量y作为纵坐标，建立离散点图像。点是空心点，并从点画一条线段连接到x轴，并返回一个handle
* set(ObjectName ,'PropertyName' ,'PropertyValue'): 设置对象相应属性的值
> 属性：如颜色、长度等
> 
> 可以通过handle查看stem的property

* h=stem(x ,y ,'option'): 'option'用于指定图像的属性（可以缺省'option')
> 'option'='filled': 离散点是实心点

* xlable('x'): 设置横坐标下方的注明文字
> ylable('y')

### 连续绘图
* h=plot(x ,y ,'option'): 和stem类似，但生成(x,y)之间直线连接的连续曲线图像 
> plot 

