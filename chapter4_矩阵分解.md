# chapter4_矩阵分解

[QR-decomposition](https://www.statlect.com/matrix-algebra/QR-decomposition)
[row-echelon-form](https://www.statlect.com/matrix-algebra/row-echelon-form)

## 三角分解

TODO：矩阵论暂时不知道考不考？等复习数值分析的时候在对这个部分的内容进行补充。

## QR分解

>对于$K\times L$的矩阵$A$, 如果$A$中的**列向量两两线性无关**, 则A可以被分解为
>其中$Q$为列向量正交的$K\times L$长方阵, $R$为$L\times L$的上三角矩阵
$$
A = QR
$$

>QR分解唯一.

从上述定义来看, 如果$A$为$n\times n$的方阵, 那个$Q$为列向量正交的$n\times n$矩阵(**酉矩阵**), $R$依旧为**上三角矩阵**.

下面将介绍求解QR分解的两种方法1.Householder变换2.Givens变换

### Householder变换求解QR分解


>Householder矩阵H为(其中$u^Hu=1$, 即u为单位向量)
$$
H = I - 2uu^H
$$

>对于任意向量$x\in C^n$都存在Householder矩阵, 满足
$$
\eqalignno{
&z^Hz = 1 &(1)\\
&|\alpha| = ||x||_2 &(2)\\
&u = \frac{x-\alpha z}{||x - \alpha z||_2} &(3)\\
&H = I - 2uu^H &(4)\\
&Hx = \alpha z &(5)\\
}
$$

Householder矩阵具有一下性质

1. Hermite矩阵
2. 酉矩阵
3. $H^2 = I$
4. $H^{-1} = H$
5. $det(H)=-1$
6. $\pmatrix{I_r & O \cr O & H}$是$r+n$阶的Householder矩阵(**重要**)

**使用Householder变换进行QR分解的步骤(以$3\times 3$矩阵为例)**

$$
H_n\dots H_2H_1A = R
$$

* 构造Householder矩阵是第一列的变为$e_1$
* 截取分块矩阵$\left(\begin{array}{c|c} 1 &* \\ \hline 0 &A \end{array}\right)$, 中的$A_{2\times 2}$
* 对A构造$2\times 2$Householder矩阵
* 将$2\times 2$Householder矩阵增维为$3\times 3$Householder矩阵
* 重复上述步骤直到最后一列
* $Q=H_{1}H_{2}$, R为上三角矩阵

⚠️: 这里Householder矩阵的作用是通过初等反射变换将向量$x$与$e_1$对齐. 计算Householder矩阵的过程就是计算反射变换反射平面法向量$u$的过程.

### Givens变换求解QR分解

>Givens矩阵是广义的旋转矩阵, 其二维特例是旋转矩阵:
$\pmatrix{cos\theta &sin\theta \\ -sin\theta &cos\theta}$

将二维的旋转矩阵推广到$C^{n\times n}$上, 就得到了**Givens**矩阵(其中$c,s$分别位于p行p列和q行q列的四个交点处):
$$
T_{pq} = \pmatrix{1 \\ &\overline c &&&\overline s \\&&1 \\ &&&\ddots \\ &-s &&&c \\ &&&&&1 \\ &&&&&&1}
$$

>Givens矩阵是酉矩阵(旋转变换是正交变换)
>Givens变换能够将向量的$a_p \geq 0, \\\ a_q = 0$, 其他分量保持不变

**构造Givens变换的步骤**

* 任意向量$x = (\xi_1, \xi_2,\xi_3,\dots ,\xi_n)$
* $c = \frac{\xi_p}{\sqrt{|\xi_p|^2+|\xi_q|^2}}$, $s = \frac{\xi_q}{\sqrt{|\xi_p|^2+|\xi_q|^2}}$
* $T_{pq}$

**使用Givens变换将向量$x$与$e_1$对齐**
$$
T_{1n}\dots T_{14}T_{13}T_{12}x = e_1
$$

**使用Givens变换进行QR分解步骤（以$3\times 3$矩阵为例)**

* 依次施加Givens变换将第i列向量的第j个分量变为0, 保持第i个分量为非零
* 检查对角线元素$a_{ii}$为向量$(a_{ii+1}\dots a_{in})^T$的二范数(长度)
* 重复上述步骤直到最后一列
* $Q=T_{12}^T\dots T_{1n}^TT_{23}^T\dots T_{2n}^T$, R为上三角矩阵

$$
T_{2n}\dots T_{23}T_{1n}\dots T_{12}A = 
\left(\begin{array}{cc|cc}
||a||_2 &* &* &\dots &*\\
0 &||b||_2 &* &\dots &*\\
\hline
\mathbf{0} &\mathbf{0} &\mathbf{c_3} &\dots & \mathbf{c_n} 
\end{array}\right)
$$

⚠️: 这里的Givens变化本质上是顺时针旋转矩阵, 通过计算向量$x$的所有分量$x_i$与$e_1$的夹角, 依次将这些分量通过顺势针旋转变换与$e_1
$对齐.

## 满秩分解

>将**非零**矩阵分解为一个**行满秩**矩阵和一个**列满秩**矩阵的乘积.
>定义: 形状为$m\times n$且$rankA \neq 0$的矩阵A, 存在行满秩矩阵和列满秩矩阵$F_{m\times r}, G_{r\times n}$, 有
$$
A = FG
$$

>Hermite标准型, 本质上就是[行最简形](https://www.statlect.com/matrix-algebra/row-echelon-form). 在下文中用$H$来表示

**满秩分解推导如下**

$$
\eqalignno{
    A \buildrel 行变换 \over \longrightarrow SA &= H \\
     \buildrel 列置换 \over \longrightarrow SAP &= \pmatrix{I_r &K \\ O &O}\\
     \buildrel 列变换,消去k \over \longrightarrow SAT &= \pmatrix{I_r &O \\ O &O}\\
}
$$

基于上述推导, 满秩分解可以写为下式

$$
A = S^{-1}\pmatrix{I &O \\ O &O}T^{-1} = \underbrace{S^{-1}\pmatrix{I_r \\ O}}_{F}\underbrace{\pmatrix{I_r & O}T^{-1}}_G
$$

所以**满秩分解的求解**可以被描述为：

* 将矩阵A变换为Hermite标准型
* 以H中的含有$e_i$的列数作为索引，取出A中的列，作为F
* 取出H的前r个非零行，作为G（r为矩阵A的rank）

>⚠️: 满秩分解并不唯一, 上述方法仅仅是构造满秩分解的一种方法