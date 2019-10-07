# MATLAB绘图
## MATLAB二维绘图
> 注意要先制定x ,y的**取值范围**，即先准备数据， 再代入函数中生成图像

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
* title(''): 设置图名
* legend(''): 设置图例
* text(x ,y ,''): 在(x,y)处显示文字
* axis([x\_st ,x\_en ,y\_st ,y\_en]): 设置显示的x轴 y轴的范围

### 连续绘图
* h=plot(x ,y ,'option'): 和stem类似，但生成(x,y)之间直线连接的连续曲线图像 
> plot(x ,y ,'b-'): 显示曲线为蓝色(blue)，曲线形状是实线
> 
> 颜色的标识用英文单词的第一个字母
> 颜色的形状分别有：':'虚线（点线），'--'粗虚线，'-'实线，'-.'虚线点线结合

* h.PropertyName=PropertyValue: 用handle设置图像的属性
* figure(number): 设置第number图形窗口
* subplot(a ,b ,c): 指定当前操作的是被分为a行b列的a*b个子图的第c个子图
> 若a b发生改变 原先的figure会被覆盖
> c是行优先 矩阵的index访问是列优先

* grid on: 开启网格显示




