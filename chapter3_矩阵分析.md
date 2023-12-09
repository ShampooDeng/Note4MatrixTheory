# chapter3_矩阵分析

参考资料: [matrix-function](https://www.statlect.com/matrix-algebra/matrix-function)

~~常见的单变量函数, 通常以一个标量作为输入, 并输出一个标量, 因此可以称这类函数为**标量函数**.~~
~~将标量函数的的输入和输出推广到**方阵**, 函数接受一个方阵, 输出一个同样尺寸的方阵, 称这类函数为**矩阵函数**.~~

TODO

## 矩阵序列

数列收敛的充要条件
$$
\lim_{k \to \infty} A^{(k)} = A \iff \lim_{k \to \infty} ||A^{(k)}-A||=0
$$

数列收敛的性质
* $\lim_{k\to \infty}(\alpha A^{k} + \beta B^{k}) = \alpha A + \beta B$
* $\lim_{k\to\infty}A^{k}B^{k} = AB$
* $\lim_{k\to\infty}(A^{(k)})^{-1}=A^{-1}$, 前提是$A^{(k)},A$均可逆

**收敛矩阵**
>对于**方阵**$A$, 若有$\lim_{k\to\infty}A^k=O$, 则$A$为**收敛矩阵**,
>其充要条件为
$$
谱半径\rho(A) \lt 1
$$

已知矩阵的任意范数有$\rho(A) \leq ||A||$, 则
$$
||A|| < 1 \quad \Rightarrow \rho(A) < 1
$$

## 矩阵级数(series)

>A series is an infinite ordered set of terms combined together by the addition operator. 

>矩阵级数为$C^{m\times n}$中的矩阵序列$\{A^{(k)}\}$的无穷和, 记作$\sum^{+\infty}_{k=0}A^{(k)}$.

为了研究矩阵级数的敛散性, 我们研究该级数的前N项和, 记作$S^{(N)}=\sum^{N}_{k=0}A^{(k)}$.
如果矩阵级数**收敛**, 则有$\lim_{N\to\infty}S^{(N)}=S$, 即
$$
\sum^{\infty}_{k=0}A^{(k)} = S
$$

矩阵级数$A^{(k)}=(a_{ij}^{(k)})_{m\times n}$的收敛, 可以理解为其$m\times n$个元素$a_{ij}^{(k)}$**数项级数收敛**.

### 矩阵级数收敛条件和性质

**绝对收敛**, $\left|a_{ij}^{(k)}\right|$均收敛, 则矩阵级数$A^{(k)}$绝对收敛.
其**充要条件**为$\sum_{k=0}^{+\infty}||A^{(k)}||$收敛.

---

**矩阵级数收敛的5条性质**

* 矩阵级数的和
* 矩阵级数的数乘
* 绝对收敛的矩阵级数, 必收敛
* 矩阵级数$A^{(k)}$(绝对)收敛, $\sum_{k=0}^{+\infty}PA^{(k)}Q = P\sum_{k=0}^{+\infty}A^{(k)}Q$
* 矩阵级数A和B收敛, 则他们**按项相乘**的矩阵级数也收敛, 为AB

### 矩阵幂级数

>对于**方阵**$A\in C^{n\times n}$, $a_k\in C$, 矩阵幂级数为$\sum_{k=0}^{+\infty}a_k A^k$

我们研究矩阵幂级数的方式大多可以**类比幂级数**, 
例如利用**收敛半径和谱半径比较**, 判断矩阵幂级数的敛散性
再比如, 利用和幂级数类似的**错位相减的方式, 对矩阵幂级数进行求和**

## 矩阵函数(matrix function)

>矩阵函数的类型貌似有很多种, 需要做进一步调查和研究. 
>这里似乎集中讨论的是进行$C_{n\times n}\to C_{n\times n}$映射的函数$f$.

函数可以展开成幂级数的形式, 有$f(z)=\sum_{k=0}^{+\infty}a_k z^k$.
所以类似的我们有$f(A)=\sum_{k=0}^{+\infty}a_k A^k$.

**矩阵函数的幂级数展开形式**, 可以直接有其对应一般函数的幂级数展开形式得到, 只需要将将$z \to A$即可.

常用的的幂级数展开式:

* $e^A$
* $\sin(A)$
* $\cos(A)$

### 矩阵函数的函数值计算

给定矩阵$A$和函数表达式$f(A)$, 我们往往需要求解出矩阵函数的矩阵表达形式(该幂级数的极限), 因为这样计算更加的直接高效.
(矩阵函数本质上也是幂级数, 展开后涉及到无穷项和, 不便于计算)

常用方法如下:

* [Hamilto-Cayley定理](https://www.statlect.com/matrix-algebra/Cayley-Hamilton-theorem)
* Jordan型
* 待定系数(利用**最小多项式**, 来降低$f(A)$展开式的次数, 简化计算), 但是次数过高时计算复杂

>⚠️: 通常涉及到两种矩阵函数$f(A)$和$f(At)$, 其中$f(A)$是$f(At) \\\ s.t. \\\ t=1$的特殊情况.
另外, 处理矩阵多项式$P(A)$的时候, 我们通常研究$P(\lambda)$来间接研究$P(A)$.

### 常用矩阵函数的性质

主要讨论了$e^A,\sin A, \cos B$的计算性质.

**三角函数的奇偶性**
* $\sin(-A)=\sin(A)$
* $\cos(-B)=-\cos(B)$

**欧拉公式**
* $e^{iA} = \cos A + i\sin A$

**三角函数倍角公式**
* $\cos 2A = \cos^2 A - \sin^2 A$
* $\sin 2A = 2\cos A \sin A$

**指数型矩阵函数的trace和inverse**
* $\rm{det}\\\ e^A = e^{trA}$
* $(e^A)^{-1} = e^{-A}$
*note: 由于行列式不为0, 所以e^A始终可逆*

**f(A+B)与f(A),f(B)的关系**, 注意:要求$AB=BA$
* $e^{A+B} = e^Ae^B$
* $\sin(A+B) = \sin A\cos B + \cos A\sin B$
* $\cos(A+B) = \cos A\cos B - \sin A\sin B$

## 矩阵积分&微分

>函数矩阵: 函数矩阵$A(t)$中每一个元素都是一个关于$t$的数量函数$f(t)$.
>与函数类似, 我们可以针对函数矩阵定义**微分**和**积分**.

 对于**求导**函数矩阵满足:

* 加法法则
* 数乘法则
* 乘法法则
* 链式法则
* 对$A^{-1}(t)A(t)=I$求导有, $\frac{\rm{d}}{\rm{d}t}A^{-1}(t) = -A^{-1}(t)(\frac{\rm{d}}{\rm{d}t}A(t))A^{-1}(t)$

常见**带自变量**$t$的矩阵函数$e^At,\sin At, \cos At$, 也可以表示为函数矩阵的形式, 并且满足:

* $\frac{\rm{d}}{\rm{d}t}e^{At} = Ae^{At} = e^{At}A$
* $\frac{\rm{d}}{\rm{d}t}sinAt = AcosAt = (cosAt)A$
* $\frac{\rm{d}}{\rm{d}t}cosAt = -AsinAt = -(sinAt)A$

注: 对于这几个常见的由矩阵幂级数所表示的函数矩阵, 写成幂级数的表达形式后求导有
$$
\frac{\rm{d}}{\rm{d}t}e^{At} = \frac{\rm{d}}{\rm{d}t} \sum^{+\infty}_{k=0} \frac{t^k}{k!}A^k = 
A^k \frac{\rm{d}}{\rm{d}t} \sum^{+\infty}_{k=0} \frac{t^k}{k!} =  Ae^{At} = e^{At}A
$$

对于**积分**, 函数矩阵有:

* 加法法则
* 数乘法则
* $\int^{a}_{b} A(t)B \rm{d}t = \left(\int^{a}_{b} A(t) \rm{d}t \right) B$$, $\int^{a}_{b} AB(t)$同理
* $\frac{\rm{d}}{\rm{d}t} \left(\int^{t}_{a}A(\tau)\rm{d}\tau \right) = A(t)$
* $\int^{a}_{b}A'(t)\rm{d}t = A(a) - A(b)$

---

>数量函数对**矩阵变量**进行**求导**, 其结果为函数矩阵.
>结果为一个由数据函数对矩阵变量中每一个元素求导所得数值函数, 所构成的函数.

---

>矩阵值函数: TODO

## 矩阵分析的应用

Welcome to matrix analysis!

### 求解一阶线性非齐次ODE

$$
\frac{dx(t)}{dt} -Ax(t) = f(t)
$$

其中A为矩阵, x(t),f(t)为向量, 对于上述方程有如下**通解**：

$$
\eqalignno{
\alpha &= e^{\int^{t}_{t_0}-Adt} = e^{A(t-t_0)} &(1)\cr
\beta &= \int^{t}_{t_0}\alpha f(t)dt &(2)\cr
x &= \frac{1}{\alpha}(\beta+C) = e^{At}\int^{t}_{t_0}e^{-At} f(t)dt + e^{At}C &(3) \\
x(0) &= O + e^{O}C = C &(4)
}
$$

注：式(3)中$e^{At}C$即微分方程的**特解**，可以**直接通过初值条件**求解

### 求解Lyapunov方程

似乎不考察

### 最小二乘问题

>最小二乘问题的本质是**求解矛盾方程组**
>将高维空间中的向量$x^*$投影到低维空降中, 使$||Ax^*-b||_2$最小, 则认为$x^*$为该矛盾方程的解向量.

>带约束条件的最小二乘问题, 可以使用Lagrange数乘法构造, 能量方程$||Ax-b||_2 +u^T(Bx-d)$

* 能量方程对$x$求导, 求得能量方程取得极小值时$x$所满足的条件.

**详见第六章**
