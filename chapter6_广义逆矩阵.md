# chapte6_广义逆矩阵

>广义逆矩阵部分或全部满足4个Penrose方程, 将满足不同方程的广义逆矩阵可以记作如A{1}, A{2,3}, A{1,2,3}, A{1234}(+加号逆)
>其中$A \in C^{m \times n}$, $X \in C^{n \times m}$

$$
AXA = A
$$
$$
XAX=X
$$
$$
(AX)^H = AX
$$
$$
(XA)^H = XA
$$

注: 广义逆矩阵的条件没有逆矩阵严格, 并且适用于**任意形状**矩阵

## 研究{1}逆

通过初等变换讲矩阵$A$变换为**Hermite标准型**, 有

$$
SAP = \pmatrix{I_r & K \cr O & O} \qquad (K\in C^{r\times (n-r)})
$$

由此, 可以计算出A的**部分**1逆

$$
X = P\pmatrix{I_r & O \cr O & L}_{n\times m}S \qquad 部分A\{1\}逆
$$

注: $X\in A\{1\}$, 如果$rank(x)=rank(A)$, 则$X\in A\{1,2\}$

$$
X = P\pmatrix{I_r & O \cr O & O}S \qquad A\{1,2\}逆
$$

如果需要求出矩阵$A$的全体{1}逆, 则需要将矩阵$A$变换为**等价标准型**, 有

$$
SAT = \pmatrix{I_r & O \cr O & O}
$$

则矩阵$A$的**全体**{1}逆有

$$
X = T\pmatrix{I_r & L_{12} \cr L_{21} & L_{22}}S \quad 全体A\{1\}逆
$$

### {1}逆的性质

* $A \in C^{m\times n}$, $A^{(1)}\in C^{n\times m}$
* $rankA^{(1)} \geq rankA$
* $rank AA^{(1)} = r \leq m$
* $rank A^{(1)}A = r \leq n$
* A行满秩, $AA^{(1)}=I_m$
* A列满秩, $A^{(1)}A=I_n$
* 更多内容参考教材

## 由{1}逆构造其他广义逆矩阵

>如果$A\in C_{m\times n}$, $X\in A\{1\}$, 则$X\in A\{1,2\}$的充要条件是${\rm rank}(X)={\rm rank}(A)$

>如果对$A\in C_{m\times n}$, 有$(A^HA)^{(1)}$, $(AA^H)^{(1)}$, 则
$$
\eqalign{
Y &= (A^HA)^{(1)}A^H \in A^{\{1,2,3\}} \cr
Z &= A^H(AA^H)^{(1)} \in A^{\{1,2,4\}}
}
$$

>对于矩阵$A$**唯一**的$A^+$有
$$
A^+ = A^{(1,3)}AA^{(1,4)}
$$

## 研究Moore Penrose逆$A^+$

>加号逆$A^+$满足四个Penrose方程, 并且唯一

### 求解$A^+$

>可以使用SVD方式求解$A^+$ , 也可以使用矩阵的满秩分解$A=FG$, 对$A^+$进行求解. 

>任意矩阵$A\in{C^{m\times n}}$存在
$$
S_{m\times m}A_{m\times n}T_{n\times n} = (I_r, \mathbf{0})^T_{m \times r}(I_r,\mathbf{0})_{r \times n}
$$
>
>其中$S, T$都是满秩矩阵(S代表行变换, T代表置换矩阵和列变换矩阵的乘积), 所以存在A的满秩分解,
$$
A = S^{-1} \pmatrix{I_r \cr \mathbf{0}} (I_r,\mathbf{0}) T^{-1}=F_{m\times r}G_{r\times n}
$$

由$A = FG$, 可以得到A的加号逆$A^+$, 有

$$
F^+ = (F^HF)^{-1}F^H
$$
$$
G^+ = G^H(GG^H)^{-1}
$$
$$
A^+ = G^+F^+
$$

>**关于如何记忆公式:**
可以观察到无论是$F^+$还是$G^+$的表达是第一个和最后一个矩阵都是共轭转置的, 区别在于$F^+$是头两个矩阵的求逆, 而$G^+$是后两个矩阵求逆;
同时已知$A\in C^{m\times n}$和$A\in C^{n\times m}$, 所以需要把$A=FG$给反过来保证$A^+$的形状, 所以就有$A^+ = G^+F^+$

特殊情况下, A为行满秩矩阵$rank(A)=m$, (满秩分解过程中不需要做行变换), 有

$$
F=I,\\ G=A,\\ A^+=A^H(AA^H)^{-1}
$$

A为列满秩矩阵$rank(A)=n$, (满秩分解中不需要做列变换和列置换), 有

$$
F=A,\\ G=I,\\ A^+=(A^HA)^{-1}A^H
$$

### Moore Penrose逆的性质

* $(A^+)^+ = A$
* $rankA^+ = rankA$
* $(A^H)^{+} = (A^+)^H$
* $rank AA^{+} = r \leq m$
* $rank A^{+}A = r \leq n$
* A行满秩, $AA^{+}=I_m$
* A列满秩, $A^{+}A=I_n$
* $(A^HA)^+ = A^+(A^H)^+$, 倒序法则
* $A^+ = (A^HA)^+A^H = A^H(AA^H)^+$
* 更多内容参考教材

## 求解矩阵方程和线性方程组

### 矩阵方程$AXB=D$

方程$AXB=D$(其中$A\in C^{m\times n},\\ B\in C^{p\times q},\\ D\in C^{m\times q}$ )有解的**充分必要**条件是

$$
AA^{(1)}DB^{(1)}B = D
$$
其通解为

$$
X=A^{(1)}DB^{(1)}+Y-A^{(1)}AYBB^{(1)},\\其中Y\in C^{m\times q}任意
$$

### 线性方程组$Ax=b$

线性方程组$Ax=b$可以认为是特殊的矩阵方程组$AXB=D$, 当$B=I_{1\times1},\\ D=b\in C^{m\times1}$.
另外, $A^+$可以被认为是特殊的$A^{(1)}$, 所以这里$A^+$和$A^{(1)}$满足同一套公示.

有线性方程组$Ax=b$($A\in C^{m\times n},\\ b\in C^{m\times1},\\ x\in C^{n\times1}$), 则方程组**有解**的**充分必要**条件是(即A为行满秩矩阵)
$$
AA^+b=b
$$
其通解为

$$
x = A^+b + (I-A^+A)y,\\ y\in C^{n\times1}
$$

注意: 方程组有解(A为行满秩)的情况下, 当A为列满秩矩阵$I=A^+A$方程仅有唯一解. (即$A^{-1}$存在, 并且$A^+=A^{-1}$)

>在实际问题中, 常需要求解出方程全体解中**唯一**的**极小范数解**, 即$||x_0||_2 = min_{Ax=b}||x||_2$, 为$x_0 = A^+b$

---

>当方程组无解时, 即$AA^+b \neq b$时(即方程为矛盾方程组或超定方程组), 常需要求出方程组的最小二乘解, 即$min(||A\tilde{x}-b||_2)$.

矛盾方程组$Ax=b$, 其最小二乘解为
$$
\tilde{x} = A^+b + (I-A^+A)y,\\ y\in C^{n\times1}
$$

注意: A如果满足列满秩(实际问题中大多数情况下满足), 则矛盾方程组的二乘解仅有一个.
而矛盾方程组**唯一**的极小范数最小二乘解, 即$min||\tilde{x}||_2, \text{subject to }min(||A\tilde{x}-b||_2)$, 为
$$
\tilde{x} = A^+b
$$

---

从一个全新的角度看最小二乘问题, 矛盾方程组$Ax=b$的解$\tilde{x}$, 本质上是另一个方程组$Ax = AA^+b$的解.
可以理解为将高维向量b投影到矩阵A所展开的线性空间中, 然后求解线性方程组.
当然由于$A^+$往往**不易计算**, 所以上述方程的等价方程, 又称**法方程组**, 为

$$
A^HAx=A^Hb
$$