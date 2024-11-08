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
