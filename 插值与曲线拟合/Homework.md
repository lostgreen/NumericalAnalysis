# Homework

## T1

已知数据表如下，试不用开方的方法而用抛物插值计算115的算术平方根的近似值，并估计计算结果的截断误差。

| x    | 100 | 121 | 144 |
|------|-----|-----|-----|
| y    | 10  | 11  | 12  |

根据抛物插值基函数的形式

\[
l_0(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)}
\]

\[
l_1(x) = \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)}
\]

\[
l_2(x) = \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)}
\]

抛物插值问题的解为

\[
P(x) = y_0 l_0(x) + y_1 l_1(x) + y_2 l_2(x)
\]

代入 \( l_0(x), l_1(x), l_2(x) \) 得：

\[
P(x) = y_0 \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)} + y_1 \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)} + y_2 \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)}
\]

\[
P(115) = 10.722755505364201 \approx 10.7228
\]

截断误差 \( R_2(x) \) 为：

\[
R_2(x) = \frac{f^{(3)}(\xi)}{3!} (x - x_0)(x - x_1)(x - x_2) \quad \xi \in (x_0, x_2)
\]

由于 \( f(x) = \sqrt x \)，我们有：

\[
f^{(3)}(x) = \frac{3}{8 \sqrt{x^5}}
\]

在区间 \([100, 144]\) 上，\( |f^{(3)}(x)| \) 的最大值为 \( 3.75 * 10 ^{-6}\)。

因此，误差的绝对值不超过：

\[
|R_2(115)| \leq \frac{3.75 * 10 ^{-6}}{6} |(115 - 100)(115 - 121)(115 - 144)| \approx 1.63 \times 10^{-3}
\]

## T2

已知 \( x_i (i=0,1,2,\cdots n) \) 两两互异的插值节点，\( l_i(x) (i=0,1,2,\cdots n) \) 为对应的插值基函数，试证明：
\[
\sum_{i=0}^n x_i^k l_i(x) = x^k \quad (k=0,1,2,\cdots n)
\]

构造\( f(x) = x ^ k \)
考虑k次插值公式
\( f(x) = R_k(x) + P(x) 
 = R_k(x) + \sum_{i=0}^{n}y_il_i(x) \)
根据插值节点\(f(x_i) = P(x_i)\)的性质
可以得出\(f(x) = R_k(x) + \sum_{i=0}^{n}x_i^kl_i(x)\)
又\( R_k(x) = \frac{f^{k+1}(x)}{(k+1)!} \prod_{i=0}^n(x - x_i) , f^{(1+k)}(x) = 0\)
于是我们得到\( R_k(x) = 0\)，化简原式子得到
\( f(x) = x^k = \sum_{i=0}^{n}x_i^kl_i(x)\)

## T3

已知函数表如下，求对应的Newton插值多项式。

| \( x \) | 0 | 1 | 4 | 3 | 6 |
|---------|---|---|---|---|---|
| \( y \) | 0 | -7 | 8 | 5 | 14 |

解：
牛顿插值公式：
$$
N_4(x)=C_0+C_1(x-x_0)+C_2(x-x_0)(x-x_1)+C_3(x-x_0)(x-x_1)(x-x_2)+C_4(x-x_0)(x-x_1)(x-x_2)(x-x_3)
$$
代入插值条件，得线性方程组
$$
\begin{equation}
\left\{
    \begin{aligned}
        C_0&=0\\
        C_0+C_1&=-7\\
        C_0+4C_1+12C_2&=8\\
        C_0+3C_1+6C_2-6C_3&=5\\
        C_0+6C_1+30C_2+60C_3+180C_4&=14
    \end{aligned}
\nonumber
\right.   
\end{equation}
$$
解得
$$
\begin{equation}
\left\{
    \begin{aligned}
        C_0&=0\\
        C_1&=-7\\
        C_2&=3\\
        C_3&=-\frac{4}{3}\\
        C_4&=\frac{23}{90}
    \end{aligned}
\nonumber
\right.   
\end{equation}
$$
将系数代入插值公式，得
$$
\begin{equation}
    \begin{aligned}
        N_4(x)&=-7x+3x(x-1)-\frac{4}{3}x(x-1)(x-4)+\frac{23}{90}x(x-1)(x-3)(x-4)\\
        &=\frac{23}{90}x^4 - \frac{152}{45}x^3 + \frac{1307}{90}x^2 - \frac{92}{5}x
    \end{aligned}
\nonumber
\end{equation}
$$

## T4

怎样选步长，才能使分段线性插值函数与 \( \sin x \) 的误差不超过 \( \frac{1}{2} \times 10^{-4} \)。

解：
根据分段线性插值误差公式
$$
|f(x) - S(x)| \le |\frac{1}{8}Mh^2|
$$ $$
f''(x) = -\sin x
$$
推导出
$$
\frac{1}{8}h^2 \le \frac{1}{2} \times 10^{-4}
$$$$
h \le 2 \times 10 ^ {-2}
$$
因此步长小于等于$2 \times 10 ^ {-2}$

## T5

5、求满足下列条件的三次Hermite插值多项式。

| \( x \) | 1 | 2 |
|---------|---|---|
| \( y \) | 2 | 3 |
| \( y' \) | 1 | -1 |

根据Hermite插值公式容易知道
$$
\alpha_0(x)=(1 - 2\frac{x - x_0}{x_0 - x_1})(\frac{x-x_1}{x_0-x_1})^2=(2x-1)(x-2)^2
$$$$
\alpha_1(x)=(1 - 2\frac{x - x_1}{x_1 - x_0})(\frac{x-x_0}{x_1-x_0})^2=(-2x+5)(x-1)^2
$$$$
\beta_0(x)=(x-x_0)(\frac{x-x_1}{x_0-x_1})^2=(x-1)(x-2)^2
$$$$
\beta_1(x)=(x-x_1)(\frac{x-x_0}{x_1-x_0})^2=(x-2)(x-1)^2
$$$$
H_3(x)=\alpha_0y_0 + \alpha_1y_1 + \beta_0y_0' + \beta_1y_1'
$$$$
H_3(x)=-2x^3+8x^2-9x+5
$$

## T6

已知函数 y=f(x)在区间 [1,3]四阶可导,对应的数据表如下。求满足下列条件的插值多项式及余项。（思考如何证明余项：此问不需作答）
| \( x \) | 1 | 2 | 3 |
|---------|---|---|---|
| \( y \) | 2 | 4 | 12|
| \( y' \)|  |  3 |   |

设插值公式$$
H_3(x)=\alpha_0(x)y_0+\alpha_1(x)y_1+\alpha_2(x)y_2+\beta_1(x)y_1'
$$
根据插值条件，得出基函数的形式为：$$
\alpha_0(x) = a(x - x_1)^2(x-x_2)
$$$$
\alpha_1(x) = (bx+c)(x-x_0)(x-x_2)
$$$$
\alpha_2(x) = d(x-x_0)(x-x_1)^2
$$$$
\beta_1(x) = e(x-x_0)(x-x_1)(x-x_2)
$$
带入插值条件得到方程组
$$
\begin{equation}
\left\{
    \begin{aligned}
        -2a&=1\\
        2b+c&=-1\\
        -b&=0\\
        2d&=1\\
        -e&=1
    \end{aligned}
\right.
\nonumber
\end{equation}
$$解得
$$
\begin{equation}
\left\{
    \begin{aligned}
        a&=-\frac{1}{2}\\
        b&=0\\
        c&=-1\\
        d&=\frac{1}{2}\\
        e&=-1
    \end{aligned}
\right.
\nonumber
\end{equation}
$$
所以，插值公式为：
$$
\begin{equation}
    \begin{aligned}
        H_3(x)&=-(x-2)^2(x-3)-4(x-1)(x-3)+6(x-1)(x-2)^2-3(x-1)(x-2)(x-3)\\
        &=2x^3-9x^2+15x-6
    \end{aligned}
\nonumber
\end{equation}
$$
插值余项为
$$
R(x)=\frac{f^{(4)}(\xi_x)}{4!}(x-1)(x-2)^2(x-3)\qquad(1<\xi_x<3)
$$

## T7

已知实验数据如下表，试用最小二乘法求拟合直线$y=g(x)=a_1x+a_0$

| **x** | **0** | **1** | **2** | **3** | **5** |
|-------|-------|-------|-------|-------|-------|
| y     | 1.1   | 1.9   | 3.1   | 3.9   | 4.9   |

课外思考：假如经验说明拟合模型为二次式$y=g(x)=ax+bx^2$，那又如何确定模型参数呢？）

正规方程组
$$
\begin{equation}
\left\{
    \begin{aligned}
        5a+11b&=14.9\\
        11a+39b&=44.3
    \end{aligned}
\right.
\nonumber
\end{equation}
$$
解得
$$
\begin{equation}
\left\{
    \begin{aligned}
        a&=1.268\\
        b&=0.778
    \end{aligned}
\right.
\nonumber
\end{equation}
$$
所以，拟合直线是
$$
y=0.778x+1.268
$$

课外思考：
这时有：
$$
\frac{g(x)}{x}=a+bx
$$
所以，将 $\{(x_0, \frac{y_0}{x_0})...(x_i, \frac{y_i}{x_i})...(x_n, \frac{y_n}{x_n})\}(x_i\neq0)$进行线性拟合即可得出 $a, b$ 的系数。
