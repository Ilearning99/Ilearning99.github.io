# 基本变换

基本变换主要是缩放变换、平移变换、旋转变换，计算机图形学都是针对现实世界空间中的点，因此对应点只在2D平面或3D空间。

## 齐次坐标




## 缩放变换

缩放变换是对应坐标乘以相应的缩放系数。

2D缩放矩阵：

$$\left[
\begin{matrix}
    s_x & 0 & 0 \\
    0 & s_y & 0 \\
    0 & 0 & 1
\end{matrix}
\right]$$

3D缩放矩阵：

$$\left[
\begin{matrix}
    s_x & 0 & 0 & 0 \\
    0 & s_y & 0 & 0 \\
    0 & 0 & s_z & 0 \\
    0 & 0 & 0 & 1
\end{matrix}
\right]$$

## 平移变换

平移变换是相应坐标加上相应的偏移量。

2D平移矩阵：

$$\left[
\begin{matrix}
    1 & 0 & a_x \\
    0 & 1 & a_y \\
    0 & 0 & 1
\end{matrix}
\right]
$$

3D平移矩阵：

$$\left[
\begin{matrix}
    1 & 0 & 0 & a_x \\
    0 & 1 & 0 & a_y \\
    0 & 0 & 1 & a_z \\
    0 & 0 & 0 & 1
\end{matrix}
\right]
$$

## 旋转变换

旋转一般情况是相对于一个过原点的轴，逆时针旋转$\theta$角。

### 2D旋转
- 相当于围绕一个过原点的穿出纸面的$z$轴旋转
- 借助极坐标和直角坐标的关系进行推导

原始坐标点：

$$
\left[
\begin{matrix}
x\\ y\\ 1
\end{matrix}
\right]
=
\left[
\begin{matrix}
l \cdot cos\alpha \\ l\cdot sin\alpha \\ 1
\end{matrix}
\right]
$$


旋转$\theta$角之后的坐标点：

$$
\left[\begin{matrix}x'\\ y'\\ 1\end{matrix}\right]
=
\left[\begin{matrix}l\cdot cos(\alpha+\theta) \\ l\cdot sin(\alpha+\theta) \\ 1\end{matrix}\right]
＝
\left[\begin{matrix}l\cdot (cos\alpha cos\theta - sin\alpha sin\theta) \\ l\cdot (sin\alpha cos\theta + cos\alpha sin\theta) \\ 1\end{matrix}\right]
=
\left[
\begin{matrix}
    cos\theta & -sin\theta & 0 \\
    sin\theta & cos\theta & 0  \\
    0   &  0  & 1  
\end{matrix} 
\right]
\left[\begin{matrix} l\cdot cos\alpha \\ l\cdot sin\alpha \\ 1 \end{matrix}\right]
$$

2D旋转矩阵：

$$
R(\theta) =
\left[
\begin{matrix}
    cos\theta & -sin\theta & 0 \\
    sin\theta & cos\theta & 0  \\
    0   &  0  & 1  
\end{matrix} 
\right]
$$

### 3D旋转

一般地，例如，任意$\vec{b}$对3D空间的$\vec{a}$轴（单位向量），逆时针旋转$\theta$角。

#### 平行于$\vec{a}$轴部分：

这一部分在旋转过程中不受影响。

$$\vec{b_{\parallel}}=\vec{a}(\vec{a}^T\vec{b})=(\vec{a}\vec{a}^T)\vec{b}$$

#### 垂直于$\vec{a}$轴部分：

找到$\vec{b}$垂直于$\vec{a}$的分量：

$$\vec{b_{\perp}}=(I-\vec{a}\vec{a}^T)\vec{b}$$

##### 建立辅助坐标系

将$\vec{a}$看做z轴方向，$\vec{a}$与$\vec{b}$构成的平面看做z轴与x轴构成的平面，$b_{\perp}$看做x轴方向，得到坐标系：

$$
\begin{aligned}
\vec{z} &= \vec{a} \\
\vec{y} &= \frac{\vec{a} \times \vec{b}}{|\vec{a} \times \vec{b}|} = \frac{\vec{a} \times \vec{b}}{|\vec{a}||\vec{b}|cos\angle_{\vec{a},\vec{b}}} = \frac{\vec{a} \times \vec{b}}{|\vec{a}||\vec{b_{\perp}}|}  = \frac{A^*\vec{b}}{|\vec{b_{\perp}}|} \\
\vec{x} &= \vec{b_{\perp}}
\end{aligned}
$$

##### 垂直部分绕$\vec{a}$旋转$\theta$角之后:

$$
\vec{b_{\perp}} \cdot cos\theta + |\vec{b_{\perp}}| \cdot sin\theta \cdot \vec{y} = (I-\vec{a}\vec{a}^T)\vec{b} \cdot cos\theta + A^* \vec{b} \cdot sin\theta = ((I-\vec{a}\vec{a}^T)\cdot cos\theta + A^* \cdot sin\theta) \cdot \vec{b}
$$

#### 旋转之后的向量表示

$$
(\vec{a}\vec{a}^T)\vec{b} + ((I-\vec{a}\vec{a}^T)\cdot cos\theta + A^* \cdot sin\theta) \cdot \vec{b} = (I \cdot cos\theta + \vec{a}\vec{a}^T \cdot (1 - cos\theta) + + A^* \cdot sin\theta) \cdot \vec{b} = R(\vec{a}, \theta) \cdot vec{b}
$$

围绕$\vec{a}$旋转$\theta$角的旋转矩阵：

$$
R(\vec{a}, \theta) = I \cdot cos\theta + \vec{a}\vec{a}^T \cdot (1 - cos\theta) + + A^* \cdot sin\theta
$$

#### 旋转之后的坐标表示

$$
R(\vec{a}, \theta) = cos\theta 
\left[
\begin{matrix}
    1 & 0 & 0 \\
    0 & 1 & 0  \\
    0 & 0 & 1  
\end{matrix} 
\right] + (1 - cos\theta)
\left[
\begin{matrix}
    x^2 & xy & xz \\
    xy & y^2 & yz  \\
    xz & yz & z^2  
\end{matrix}
\right]
+ sin\theta \left[
\begin{matrix}
    0 & -z & y \\
    z & 0 & -x  \\
    -y & x & 0  
\end{matrix} 
\right]
$$

#### 3D样例

按照$\vec{z}$轴旋转：

$$\vec{z}=\left[\begin{matrix}0\\0\\1\end{matrix}\right]$$

$$
\begin{aligned}
R(\vec{z},\theta)&=
cos\theta 
\left[
\begin{matrix}
    1 & 0 & 0 \\
    0 & 1 & 0  \\
    0 & 0 & 1  
\end{matrix} 
\right] + (1 - cos\theta)
\left[
\begin{matrix}
    0 & 0 & 0 \\
    0 & 0 & 0  \\
    0 & 0 & 1  
\end{matrix}
\right]
+ sin\theta \left[
\begin{matrix}
    0 & -1 & 0 \\
    1 &  0 & 0  \\
    0 &  0 & 0  
\end{matrix} 
\right]\\
&=
\left[
\begin{matrix}
    cos\theta & -sin\theta & 0 \\
    sin\theta &  cos\theta & 0 \\
            0 &          0 & 1
\end{matrix}
\right]
\end{aligned}
$$


按照$\vec{x}$轴旋转：

$$\vec{x}=\left[\begin{matrix}1\\0\\0\end{matrix}\right]$$

$$
\begin{aligned}
R(\vec{x},\theta)&=
cos\theta 
\left[
\begin{matrix}
    1 & 0 & 0 \\
    0 & 1 & 0  \\
    0 & 0 & 1  
\end{matrix} 
\right] + (1 - cos\theta)
\left[
\begin{matrix}
    1 & 0 & 0 \\
    0 & 0 & 0  \\
    0 & 0 & 0  
\end{matrix}
\right]
+ sin\theta \left[
\begin{matrix}
    0 &  0 & 0 \\
    0 &  0 & -1  \\
    0 &  1 & 0  
\end{matrix} 
\right]\\
&=
\left[
\begin{matrix}
            1 &          0 &          0 \\
            0 &  cos\theta & -sin\theta \\
            0 &  sin\theta &  cos\theta
\end{matrix}
\right]
\end{aligned}
$$

### 旋转的性质
- 旋转的可加性 $R(\theta+\alpha)=R(\theta)+R(\alpha)$
- 每一行表示的向量能构成一组标准正交基
    - 旋转矩阵构成正交矩阵 $I=R^TR$
    - 旋转矩阵可以看作新的坐标系
- 可以看作坐标系在顺时针旋转对应角度

如下，给对应点旋转后，新的点相当于是在新坐标系下的坐标：

$$z'=Rz=
\left[
\begin{matrix}
    u^T \\ v^T \\ w^T
\end{matrix}
\right]z =
\left[
\begin{matrix}
    u^Tz \\ v^Tz \\ w^Tz
\end{matrix}
\right]
$$







