# chapter7_Kronecker乘积

>定义:$A=(a_{ij})_{m\times n}$和$B=(b_{ij})_{p\times q}$的kronecker乘积为$A \otimes B = (a_{ij}B)_{m \times n}$, 其中矩阵A中的每一个元素乘以矩阵B构成了Kronecker乘积的一个子块.

Kronecker乘积有$A \otimes B \in \mathbb{C}^{mp \times nq}$, 并且可以应用与任意形状的两个矩阵.

## 性质

1. $k(A\otimes B) = (kA)\otimes B = A\otimes (kB)$, 其中k为标量(scalar)

2. $(A_1 + A_1)\otimes B = A_1 \otimes B + A_2 \otimes B$, 反之亦然成立

3. $(A \otimes B)^H = A^H \otimes B^H$, 对转置T依然成立(正序法则)

4. $(A \otimes B)\otimes C = A \otimes (B \otimes C)$

5. $(A \otimes B)(C \otimes D) = AC \otimes BD$

6. $(A \otimes B)^{-1} = A^{-1} \otimes B^{-1}$

7. $(A \otimes B)^+ = A^+ \otimes B^+$

8. 如果矩阵$A_{m\times m}$,$B_{n \times n}$都是Unitary矩阵, 则$A \otimes B$也为酉矩阵.

9. 如果矩阵$A_{m\times m}$,$B_{n \times n}$都是上(下)三角矩阵, 则$A \otimes B$也为上(下)矩阵.

10. $rank(A \otimes B) = rank(A)rank(B)$

11. 如果矩阵A,B都是方阵, $A \otimes B$相似于$B \otimes A$, 因为有$A = P_0^{-1}J_0P_0$和$B = P_1^{-1}J_1P_1$
$$
(P_0 \otimes P_1)(J_0 \otimes J_1)(P_0 \otimes P_1)^{-1} = (P_0^{-1}J_0P_0) \otimes (P_1^{-1}J_1P_1)
$$

12. $A\otimes B$的特征值, 即$A \otimes B = (P_0 \otimes P_1)(J_0 \otimes J_1)(P_0 \otimes P_1)^{-1}$中$J_0 \otimes J_1$的全体特征值为$\lambda_i \mu_j$

13. $A \otimes I_n + I_m \otimes B^T$的全体特征值为$\lambda_i + \mu_i$, 则$A \otimes I_n + I_m \otimes B^T$可逆的充要条件是$\lambda_i + \mu_i \neq 0$

14. $det(A\otimes B) = (detA)^n(detB)^m$, 参考第12条可以进行证明

15. 有$Ax = \lambda x, By = \mu y$, 则有$(A \otimes B)(x \otimes y) = (\lambda \mu)(x \otimes y)$

## 矩阵拉直操作(flatten)与直积的关系

**矩阵拉直操作的性质**

* 满足线性运算
* $\overrightarrow{AXB} = (A\otimes B^T)\overrightarrow X$

## 应用

### 求解Lyapunov方程

$$
\eqalign{
    A\in C^{m\times m} &, B\in C^{n\times n}\\
    AX+XB &= F\\
    &\Updownarrow\\
    AXI_m + I_nXB &= F\\
    &\Updownarrow\\
    (A\otimes I_m+I_n \otimes B^T)\overrightarrow X &= \overrightarrow F
}
$$

### 求解一般线性矩阵方程

### 求解线性非齐次矩阵ODE
