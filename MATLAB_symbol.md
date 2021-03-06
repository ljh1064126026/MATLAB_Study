# MATLAB符号运算

## 符号运算入门
* `a=sym(b)`: 建立符号变量 赋值为b
* `syms a b c`: 建立多个符号变量
* `class(a)`: 返回变量数据类型

> 符号变量也可以存储多个符号变量复合而成的符号表达式

## 常用函数
* `collect(P ,var)`: 将符号表达式P根据var合并同指数阶项 并按照var的指数阶从大到小排序（合并同类项）
* `factor(P)`: 对P因式分解（P如果是数值 就分解质因数）
* `finverse(P ,var)`: 求P的反函数
* `compose(g ,u)`: 把函数u复合到函数g里
* `symvar(P)`: 输出符号表达式P中的符号自变量
* `subs(P ,oldvar ,newvar)`: 将符号表达式P中原来的变量oldvar替换成newvar
* `vpa(a ,n)`: 返回显示n位（总共）的a的数值解 类型仍是符号对象
* `expand(p)`: 将P展开（如 $P=(x+y)^{3}=x^3 + 3*x^2*y + 3*x*y^2 + y^3$）
* `simplify(P)`: 用多种恒等式对P进行综合化简
* `simple(P)`: 使用包括`simplify(P)`在内的化简方法对P进行化简

> simplify只是众多化简方法的一种 而simple调用了所有化简方法保证P的长度最短

* `[x1 ,x2]=numden(P)`: 通分P 将分子存储在x1中 分母存储在x2中 构成新的向量 x1,x2依旧是symbolic 且x1/x2可以得到通分后的P
* `pretty(P)`: 以书写方式显示P

## 数学运算
### 微分
* `limit(P ,var ,a)`: 求 $\lim_{va \to a}{P}$
* `limit(P ,var ,a ,'right' or 'left')`: 求左右极限
* `diff(P ,var ,n)`: P对var求n阶导数

### 积分
* `int(P ,var)`: 计算P对var的不定积分
* `int(P ,var ,a ,b)`: 计算 $\int_a^b{Pdx}$

> 符号矩阵是所有元素为符号变量的矩阵 可以和其他符号变量相互运算 操作方法和数值矩阵相同
> 上述运算也可以作用在符号矩阵（上的所有元素）

### 代数方程求解
> 各个等式和变量不是string 不需要单引号

* `[ans1 ,ans2 ,..., ansn]=solve(eq1 ,eq2 ,... ,eqn ,var1 ,var2 ,... ,varn)`: 计算由变量var1...varn构成的代数方程eq1...eqn构成的代数方程组，其中ans1...ansn分别是var1...varn的所有解
* `answer=solve(eq1 ,eq2 ,... ,eqn ,var1 ,var2 ,... ,varn)`: 将结果存储到结构体answer中（注意不能用ans）通过ans.vari访问各个变量的结果

### 微分方程求解
> 默认独立变量是t

```
>>> syms x(t) y(t) % Define a symbolic function 
>>> Dx=diff(x) % that is Dx=Dx(t)=x(t)
>>> Dy=diff(y)
>>> f1=Dx==y
>>> f2=Dy==-x
>>> ans1=dsolve(f1 ,f2) % dsolve(eq1 ,... ,eqn ,初始条件1 ,...,初始条件n ,var1 ,... ,varn)
>>> 
>>> [ans1.x,ans.y]
[ C5*cos(t) + C4*sin(t), C4*cos(t) - C5*sin(t)]
```
> 任意常数的个数=微分方程的个数-初始条件个数=自由度