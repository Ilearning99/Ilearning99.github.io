# 计算机图形学基础
这是学堂在线课程Foundations of Computer Graphics课程中ppt和作业的相关笔记

## 数学基础
计算机图形学的数学基础是矩阵与向量运算，因为计算机图形学主要涉及到物体表面点的平移和旋转，空间中的点可以作为向量，平移和旋转可以看作对对应矩阵和向量的乘积。

### 向量基本运算
向量运算主要包括相加、点乘、叉乘

- 叉乘

1. 定义：

$$\vec{a} \times \vec{b} = 
\left[
\begin{matrix}
   \vec{i} & \vec{j} & \vec{k} \\
   x_a & y_a & z_a \\
   x_b & y_b & z_b
\end{matrix}
\right] = (y_a z_b - z_a y_b) \vec{i} + (z_a x_b - x_a z_b) \vec{j} + (x_a y_b - y_a x_b) \vec{k}
$$

2. 性质：
    - 长度：$|\vec{a}||\vec{b}|sin\phi$，其中$\phi$是$\vec{a}$和$\vec{b}$之间的夹角
    - 方向：与$\vec{a}$和$\vec{b}$垂直，满足右手系的关系

3. 用处：用作构造直角坐标系

例如，通过向量$\vec{a}$和$\vec{b}$，构造直角坐标系$\vec{u},\vec{v},\vec{w}$

将$\vec{u}$与$\vec{a}$的方向相关，$\vec{v}$与$\vec{b}$的方向相关，得到

$$
\begin{aligned}
\vec{u} &= \frac{\vec{a}}{|\vec{a}|} \\
\vec{w} &= \frac{\vec{a} \times \vec{b}}{|\vec{a} \times \vec{b}|} \\
\vec{v} &= \vec{w} \times \vec{u}
\end{aligned}
$$

4. 矩阵表示：

矩阵表示更便于叉乘与其他变换操作相统一

$$
\vec{a} \times \vec{b} = 
\left[
\begin{matrix}
    0 & -z_a & y_a \\
    z_a & 0 & -x_a \\
    -y_a & x_a & 0
\end{matrix}
\right]
\left[ 
\begin{matrix}
x_b \\ y_b \\ z_b
\end{matrix} 
\right] = A^* \vec{b}
$$

5. 疑问：由于现阶段知识的缺陷，我有以下疑问：
    - 叉乘运算目前看只存在于3维空间，不像点乘是存在于任意维空间，因此这个概念看上去不完整，没有拓展到高维
    - 叉乘的定义是通过行列式运算定义的，这里像一个巧合，那么，是先有行列式运算，发现了相应的性质然后再定义了叉乘，还是需要定义有对应性质的叉乘，然后用到了行列式呢？
