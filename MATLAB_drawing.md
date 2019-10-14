# MATLAB绘图
> 大多数绘图函数都有handle设置property,大多数颜色、线条等property都可以被设置  
> 见教材p213~p214 相关色彩、点型、线型   
> 点型只能用于plot stem设置   
> 每次生成新图都要用handle接受 方便后期修改  
> `ezplot()`如何设置数据点型?  
> 如何删除曲线?  
## MATLAB二维绘图
> 注意要先制定x ,y的**取值范围**，即先准备数据， 再代入函数中生成图像

* hold on: 保持原图不被新图覆盖
> hold off  
* plot()是用离散的点逼近连续的点 ezplot()是更加精确的连续图形 故前者需要提前定义好x向量 后者用syms即可

### 二维绘图步骤
1. 准备数据（x,y）的取值范围
2. 指定图像窗口(figure(3))和子图位置(subolot(1 ,2 ,1))
3. 绘制图形
4. 添加属性修饰等

### 离散绘图
* figure: create a figure window
* h=stem(y): 以x=1 ,2 ,3...作为横坐标，向量y作为纵坐标，建立离散点图像。点是空心点，并从点画一条线段连接到x轴，并返回一个handle
> h=stem(x ,y): x,y都是向量  
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
```
h_stem=stem(x ,sin(x)+cos(x) ,'ro')%红色+空心圆点
h_plot_sin=plot(x ,sin(x) ,'b--')%蓝色+虚线
h_plot_cos=plot(x ,cos(x) ,'k-')%黑色+实线

legend([h_stem ,h_plot_sin ,h_plot_cos] ,'sin(x)+cos(x)' ,'sin(x)' ,'cos(x)')
%通过handle分别设置三个图像的图例
```
* text(x ,y ,''): 在(x,y)处显示文字
* axis([x\_st ,x\_en ,y\_st ,y\_en]): 设置显示的x轴 y轴的范围

### 连续绘图
* h=plot(x ,y ,'option'): 和stem类似，但生成(x,y)之间直线连接的连续曲线图像 
> plot(x ,y ,'b-'): 显示曲线为蓝色(blue)，曲线形状是实线
> 
> 颜色的标识用英文单词的第一个字母  
> 颜色的形状分别有：':'虚线（点线），'--'粗虚线，'-'实线，'-.'虚线点线结合  
> h=plot(x1 ,y1 ,'opt1' ,x1 ,y2 ,'opt2' ...): 绘制多个曲线  
> 

* h.PropertyName=PropertyValue: 用handle设置图像的属性
* figure(number): 设置第number图形窗口
* subplot(a ,b ,c): 指定当前操作的是被分为a行b列的a*b个子图的第c个子图
> 若a b发生改变 原先的figure会被覆盖  
> c是行优先 矩阵的index访问是列优先

* grid on: 开启网格显示

#### 方程式绘图
> ezlot()无需提前设置方程式中x y的范围 

* ezplot(方程式 ,[x\_st ,x\_en ,y\_st ,y\_en]) %标准方程式，方程式可以是`x^2-y==0`或`x^2==y（可以省略==y）`等
* ezplot(x的参数方程, y的参数方程, [tmin ,tmax]) %参数方程
> 可以省略范围声明 MATLAB会默认范围  
> 横纵坐标的显示范围一般都用向量表示

#### 图像填色
* patch(x\_vector ,y\_vector ,[r ,g ,b]):x\_vector and y\_vector一一对应作为多边形的顶点 从而围成一个多边形 填充该多边形 r:red ,g:green ,b:blue
> patch(x\_vector ,y\_vector ,'r')  
> 顶点需要按顺序从头连接到尾  
* 


