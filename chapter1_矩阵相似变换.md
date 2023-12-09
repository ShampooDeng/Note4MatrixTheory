# chapter1_矩阵相似变换

## 特征值与特征向量

* [eigenvalues-and-eigenvectors](https://www.statlect.com/matrix-algebra/eigenvalues-and-eigenvectors)
* [characteristic-polynomial](https://www.statlect.com/matrix-algebra/characteristic-polynomial)
* [properties-of-eigenvalues-and-eigenvectors](https://www.statlect.com/matrix-algebra/properties-of-eigenvalues-and-eigenvectors)
* [linear-independence-of-eigenvectors](https://www.statlect.com/matrix-algebra/linear-independence-of-eigenvectors)

## Jordan标准型

* [Jordan-form](https://www.statlect.com/matrix-algebra/Jordan-form)
* [generalized-eigenvector](https://www.statlect.com/matrix-algebra/generalized-eigenvector)
* [similar-matrix](https://www.statlect.com/matrix-algebra/similar-matrix)

### 代数重数与几何重数

代数重数$r$表示特征值的重数，即特征多项式（characteristic polynomial）中有根的重数。
几何重数$s$表示Jordan块的特征值所对应特征向量的数目，也等于Jordan块的数目。
**一个特征向量对应一个Jordan块**

代数重数$r$和几何重数$s$满足
$$
1 \leq s \leq r
$$

### 求解Jordan标准型

* 求解特征向量->由特征向量和Jordan块的**数量关系**求解
* 初等变化法
* 行列式因子法

>任何方阵相似与相似于Jordan标准型。
$$
A = PJP^{-1}
$$

所以可以认为对角矩阵是Jordan标准型的一种**特殊形式**。
因此可以效仿求解矩阵特征向量的方式，求解Jordan标准型。
注意，当特征值的重数**超过3**，就难以通过Jordan块的数目判断Jordan块的阶数。

---

另一种推荐的方法为**行列式因子法**。
定义**k阶行列式因子$D_k(\lambda)$**为$(\lambda I - A ) \in \mathbb{R}^{m \times n}$的全部k阶子式的**最大公因式**。

由行列式因子定义**不变因子$d_k(\lambda)$**，有
$$
D_k(\lambda) = d_k(\lambda) d_{k-1}(\lambda) \dots d_1(\lambda)
$$

定义**初等因子**为$(\lambda - \lambda_n)^n$，每个初等因子对应一个Jordan块的对角值和其阶数，有
$$
d_k(\lambda) = (\lambda - \lambda_n)^n \dots (\lambda - \lambda_m)^m
$$

## 矩阵多项式

* [matrix-polynomial](https://www.statlect.com/matrix-algebra/matrix-polynomial)
* [Cayley-Hamilton-theorem](https://www.statlect.com/matrix-algebra/Cayley-Hamilton-theorem)
* [minimal-polynomial](https://www.statlect.com/matrix-algebra/minimal-polynomial)
* [Schur-decomposition](https://www.statlect.com/matrix-algebra/Schur-decomposition)

将多项式$p(x) = a_1 x + a_2 x^2 \dots + a_n x^n$由$\mathbb{C}$推广到$\mathbb{C}^{n \times n}$，
则**定义**矩阵多项式**为$p(A) = a_1 A + a_2 A^2 \dots + a_n A^n$。

*注意*：这里$A$为方阵

### Hamilton Cayley定理

对于$A \in \mathbb{C}^{n \times n}$，特征多项式$\psi(x) = \text{det}(A - \lambda I)$，则有
$$
\psi(A) = (A - \lambda_1 I)(A - \lambda_2 I)\dots(A - \lambda_n I) = \mathbf{O}
$$

### 最小多项式

定义**零化多项式**为$f(\lambda)$使$f(A) = \mathbb{O}$，其中$A \in \mathbb{C}^{n \times n}$。
显然$A$的特征多项式$\psi(\lambda)g(\lambda)$，为零化多项式。

定义$A$的**最小多项式**$m_A(\lambda)$为所有零化多项式中次数最小矩阵多项式，可以整除$A$任意零化多项式。

**求解最小多项式**，可以通过$A_{n\times n}$的第$n$阶和第$n-1$行列式因子计算，即
$$
m_A(\lambda) = \frac{\psi(\lambda)}{D_{n-1}(\lambda)} = \frac{D_n(\lambda)}{D_{n-1}(\lambda)}
$$

**相似矩阵具有相同的零化多项式**

## 向量内积

[inner-product](https://www.statlect.com/matrix-algebra/inner-product)

定义向量**内积**为
$$
(x,y) = y^Hx 或者\left<x,y\right>
$$

**Cauchy-Schwarz不等式**
$$
(x,y) \leq \sqrt{(x,x)(y,y)}
$$

**向量内积与向量2范数**
$$
||x||_2 = \sqrt{(x,x)}
$$

## 将矩阵推广至复数域

* [conjugate-transpose-and-hermitian-matrix](https://www.statlect.com/matrix-algebra/conjugate-transpose)
* [unitary-matrix](https://www.statlect.com/matrix-algebra/unitary-matrix)
* [normal-matrix](https://www.statlect.com/matrix-algebra/normal-matrix)

### 酉矩阵（Unitary matrix）

>正交矩阵为方阵，其列分量**两两线性无关**并且**长度（向量2范数）为1**
>满足$A^TA = AA^T = I$

>共轭转置为在转置的基础上，对矩阵每个元素取共轭，记作$A^H$

将矩阵$A$由$\mathbb{R}^{n \times n}$推广到$\mathbb{C}^{n \times n}$，则有
$$
A^HA = AA^H = I
$$

### 酉相似下的标准型(schur定理)

>任何方阵A都酉相似于上三角矩阵T
$$
A = UTU^H 
$$

### Hermite矩阵

$$
A^H = A
$$

### 正规矩阵（Normal matrix)

$$
A^HA = AA^H
$$

正规矩阵包括以下矩阵：

|   实矩阵   |    复矩阵     |
| :--------: | :-----------: |
|  正交矩阵  |    酉矩阵     |
|  对称矩阵  |  Hermite矩阵  |
| 反对称矩阵 | 反Hermite矩阵 |
|  对角矩阵  |    $\dots$    |

>矩阵$A$有且仅当$A$为正规矩阵时，能够酉对角化$D = U^H A U$

>如果$A$为实对称矩阵，则有$D = P^T A P$，其中为$D$实对角矩阵，$P$为正交矩阵

**酉不变性**，$A = U^H B U$(即$B$酉相似于$A$)，如果$A$为正规矩阵，则$B$为正规矩阵

## 正定矩阵

* [positive-definite-matrix](https://www.statlect.com/matrix-algebra/positive-definite-matrix)

>对于实矩阵有正定矩阵，对于复矩阵有Hermite正定矩阵的概念

### 二次型（quadratic form）

有二次多项式$f(x_1,x_2,\dots,x_n) = \sum{\alpha x_i^2} + \sum_{i \neq j}{\beta x_i x_j}$，则可以写成 $f(x) = x^T A x$ ，其中$A$不唯一。

>任何二次型$x^T A x$都可以由**唯一**的对称矩阵$B$表示
$$
f(x) = x^T A x = x^T B x
$$

### 正定 & 半正定 & 负定

对于任意$x$有$x^TAx \geq 0$，其中$A \in \mathbb{C}^{n \times n}$，则$A$为Hermite正定矩阵。
（如果$A \in \mathbb{R}^{n \times n}$，则$A$为正定矩阵）
等价于

* $A$的特征值均为正实数
* $A = P^H \sqrt D \sqrt D P = L^H L$

类似的有**Hermite半正定矩阵**，等价条件有

* $A$的特征值全为非负实数
* $A = P^H \sqrt D \sqrt D P = L^H L$

**Hermite负定矩阵**
TODO

### 判定Hermite正定矩阵

$A$为正定矩阵的**充分必要条件**是$A$的K阶顺序主子式全为正。
*注意*：K阶顺序主子式全非负，不能导出$A$为半正定矩阵。

## 矩阵对角化

* $A = PJP^{-1}$
* $A = UDU^H$
