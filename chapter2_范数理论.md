# chapter2_范数理论

## 向量范数

[vector-norm](https://www.statlect.com/matrix-algebra/vector-norm)

$S$为向量空间，向量空间$S$上的范数运算是一个将向量$s$映射$\mathbb R^+$上，其中$s \in S$，记作$||s||$。

### 向量范数三公理

任何向量范数满足以下三条公理：

* $||s|| \geq 0$，有且仅当$s=\mathbf 0$时$||s||=0$
* $||\lambda s|| = |\lambda| \ ||s||$
* $||x+y|| \leq ||x|| + ||y||$

### 二范数

**属于二范数的性质**

* $||s||_2 = \sqrt {(s,s)}$，向量二范数与向量内积的关系
* $||a+b||_2 = ||a||_2 + ||b||_2$，这里$a,b$正交, 毕达哥拉斯定理
* $(a,b) \leq \sqrt {(a,a)(b,b)}$，Cauchy-Schwarz Inequality
* $||Ux||_2 = ||x||_2$, 酉不变性

### p范数

$$
||x||_p = \left(\sum_{k=1}^{n}|\xi_k|^p \right)^{\frac 1 p}
$$

### Holder Inequality

TODO

### 由已知向量范数构造新向量范数

$$
||x||_b = ||Ax||_a
$$

### 向量范数等价性

如果向量范数$||\cdot||_a$和$||\cdot||_b$等价，则有
$$
\alpha ||x||_b \leq ||x||_a \leq \beta ||x||_b
$$
### 常见范数

**向量一范数**

$$
||x||_1 = \sum_{k=1}^{n}|\xi_k|
$$

**向量二范数**

$$
||x||_2 = \sqrt{\sum_{k=1}^{n}|\xi_k|^2}
$$

**向量$\infty$范数**

$$
||x||_{\infty} = max|\xi_k|
$$

**椭圆范数/加权范数**

$$||x||_A = \sqrt{x^H A x}$$

## 矩阵范数

**以下矩阵范数若未说明，均指方阵范数**

### 矩阵范数四公理

任何矩阵范数满足以下四条公理：

* $||A|| \geq 0$，有且仅当$A=\mathbf 0$时$||A||=0$
* $||\lambda A|| = |\lambda| \ ||A||$
* $||A+B|| \leq ||A|| + ||B||$
* $||AB|| \leq ||A|| \ ||B||$
* $| \ ||A|| - ||B|| \ | \leq ||A|| - ||B||$

### 与向量范数相容性
矩阵范数$||\cdot||_m$和向量范数$||\cdot||_v$相容，则对于任意$A$和$x$，都有
$$
||Ax||_v \leq ||A||_m ||x||_v
$$

### 从属范数

由**向量范数**导出的矩阵范数，或从属于**向量范数**的矩阵范数，有
$$
||A|| = max \frac{||Ax||_v}{||x||_v} (x \neq \mathbf 0)
$$

### 常见矩阵范数

* m1范数, 矩阵元素模的和
* m2范数(F范数), 矩阵元素模的平方的和, $\sqrt{tr(A^HA)}$
* m$\infty$范数, 矩阵列数乘以矩阵中最大的元素

**从属范数**(由向量范数导出的矩阵范数)

* 矩阵1范数, 矩阵最大的列和(列各元素模的和)
* 矩阵2范数, $A^HA$最大的特征值, 谱范数
* 矩阵无穷范数, 矩阵最大的行和(每行各元素模的和)

**对于长方阵**

* G范数(几何平均范数)$\sqrt{mn}$版本的矩阵m无穷范数

## 矩阵谱半径

>定义：${\lambda_1, \lambda_2, \dots, \lambda_n}$是$A \in \mathbb{C}^{n \times n}$的n个特征值
$$
\rho (A) = max_j{|\lambda_j|}
$$

### 谱半径的性质

* $\rho(A^k) = (\rho(A))^k$
* $\rho(AA^H) = \rho(A^HA) = ||A||^2_2$
* $\rho(A) = ||A||_2$如果A是正规矩阵(normal matrix)

### 普半径与矩阵范数的关系

$A \in \mathbb{C}^{n \times n}$，则$\forall || \ \cdot \ || \in \mathbb{C}^{n \times n}$，有(可以考虑通过矩阵范数与向量范数的相容性进行证明)
$$
\rho (A) \leq ||A||
$$

设$A \in \mathbb{C}^{n \times n}$，$\forall \varepsilon > 0$，$\exists || \ \cdot \ || \in \mathbb{C}^{n \times n}$，有
$$
||A||_m \leq \rho(A)+\varepsilon
$$

## 矩阵条件数

>定义矩阵的条件数为，$A \in \mathbb{C}^{n \times n}$，$|| \ \cdot \ || \in \mathbb{C}^{n \times n}$，有
$$
cond(A) = ||A|| \ ||A^{-1}||
$$

背景：矩阵条件数反映的是方程组$Ax = b$中解$x$的误差对矩阵误差$\delta A$和$\delta b$的敏感程度。条件数越大，方程组对误差的放大程度越大，即病态（bad condition）。

TODO

## Tips