# MATLAB基础操作
## 数据类型操作函数

### 数值范围强制转换
* `init8; uint8; ...; int64; uint64`
* `single(); double()`

### 取整
> MATLAB的浮点数类型只有 `single` 和 `double`

* `round(single_num)`: 向最接近single_num的integer取整
* `fix(single_num)`: 向0方向取整
* `floor(num)`: 取底
* `ceil(num)`: 取顶

### 复数
> 创建复数可以直接创建 `如 3+4i(或j)`

* `complex(a ,b)`: 创建复数=`3+4i`
* `real(z) imag(z) conj(z)`: 分别返回复数的 实部 虚部 共轭复数

### 数值类型显示格式
> `format short`默认5位显示（不是小数点后五位，是总共五位）

* `format short/long e`: 5位/15位带指数显示
* `format bank`: 小数点后2位
* `format rat`: 分数（近似）显示

### 矩阵/数组/向量基本运算
* `'`共轭转置  `.'`转置不共轭
* 其余所有运算符前面加`.`如`.*`都是对应元素运算

### 向量/数组生成方式
* `a=[a ,b ,c] or [a;b;c]`: `,`用于单行内分割 `;`用于多行间分割
* `a=[start:step:end]`
* `a=linspace(1 ,3 ,3)`: 生成从1～3 3个元素的**等差数列**
* `a=logspace(0 ,log10(32) ,6)`: 生成从$10^{0}$ ~ $10^{log_{10}^{32}}=32$ 有6个元素的**等比数列**

### 向量运算
* `dot(a ,b)`: 向量ab做点积运算
* `cross(a ,b)`: 向量ab做叉积运算

### 矩阵操作
* `A(a:b,c:d)`: a行到b行，c列到d列
* `A(a:b,:)`: a行到b行所有列的元素
* `A(a:b)`: 第a个元素到第b个元素（列优先）
* `A(a,b)`: 元素(a,b)
* `A(a)`: 第a个元素（列优先）
* `A(:)=B`: A的全元素访问 要求A已经被事先创建 两者形状不必相同 只要数量相等即可 赋值后维持A的形状
* `B=A(a:b,c:d)`: 抽取A的子矩阵快赋值给B
* `C=[A;B] or C=[A,B]`: 矩阵拼接
* `zeros(m ,n) ones(m ,n) rand(m ,n) randn(m ,n) eye(m ,n)`: 生成m*n阶全0 全1矩阵 在0～1之间均匀分布的随机矩阵 满足正态分布的随机矩阵 单位矩阵
* `diag(V,k)`: 创建对角元素为向量V 其他元素为0的对角矩阵(k=0)
> 当k>0时 向量向对角线上方偏k个位置

* `diag(A,k)`: 提取矩阵A的主对角线上的元素构成一个向量（k=0）
* `magic(m)`: 构成m阶魔方矩阵

> 对于方阵可以eye(m)  

* `cat(n ,A ,B ,C)`: 沿n维方向拼接矩阵（1：列，2：行）
* `repmat(A ,a1 ,a2 ,...,an)`: A沿1维（列方向）有a1个，沿2维（行方向）有a2个，沿3维（页方向）有a3个...
* `repmat(A ,a)`: A沿1维 2维方向都有a个
* `reshape(A ,a ,b)`: 将矩阵A重置为元素相同、数量相等 形状为a*b的矩阵
* `det(A)`: 求矩阵对应行列式的值
* `inv(A)`: 矩阵求逆（不可逆矩阵会报错）
* `A/B A\B`: A*inv(B) inv(A)\*B
* `rank(A)`: 求A的秩
* `[x ,lamda]=eig(A) or [x ,lamda]=eigs(A)`: 求A的特征向量和特征值
* `size(A)`: 输出矩阵第1，2，3...n维分别构成的向量的维数 将这些维数构成一个向量
* `length(A)=max(size(A))`

## 文件操作
* `load file_name.mat`: 命令加载数据文件
