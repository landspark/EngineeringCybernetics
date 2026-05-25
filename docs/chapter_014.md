# 工程控制论（下册）

（第三版）

钱学森 宋健 著

## 正文（014）

### 第十四章 随机输入作用下的控制系统

在以前各章里，系统的输入是确切知道的时间函数。但是在很多控制系统中，输入信号并不是确切知道的，只能用某些统计特性加以描述。例如，由于空气的湍流在飞机的机翼结构内引起的运动和应力就属于这一类问题。在这个例子中，可以把随时间变化的气流状态看做是系统的输入，它是一个随机函数，只能知道它的统计特性。机翼的应力是系统的输出，它也是一个随机函数，也只能知道它的统计特性。随机输入的另一个例子就是控制信号中的噪声。在本章里，我们讨论随机输入作用下控制系统的分析，而在下一章则将讨论设计问题。

#### 14.1 随机变量和随机向量

随机量是通过概率来描述的，概率论是讨论和处理随机量的理论基础。所以我们首先回忆一下几个基本定义。在讨论有关概率的问题时，最重要的概念就是概率三要素:

（1）基本事件空间 $\Omega:\Omega$ 是一个集合，它包含有限个或无限个元素 $\omega,\omega$ 叫做基本事件。

例如，如果认为实数轴上所有点都是基本事件，则基本事件空间 $\Omega$ 就是整个实数轴, $\Omega$ 内包含了无限个而且是不可数的基本事件 $\omega$ 。

（2）事件体 $\mathcal{F}$ 。在 $\Omega$ 内规定某些子集合，每一个子集合称为事件。所有这些规定好的子集合的全体叫做事件体 $\mathcal{F}$ 。 $\mathcal{F}$ 要满足下面几个要求：

a）基本事件空间 $\Omega$ 也是一个事件，用集合的符号表示即 $\Omega\in\mathcal{F};b)$ 如果可数个事件都属于事件体 F，那么它们的并也属于事件体 F，即若 $A_{n}\in\mathcal{F}, n=1,2,\cdots$ ，则 $\bigcup_{n=1}^{\infty}A_{n}\in\mathcal{F};c)$ 如果事件 A 属于事件体 F，那么它的逆事件也属于事件体 F。

例如，在实数轴上存在从某个整数 $\omega_{1}$ 开始到另一个整数 $\omega_{2}, \omega_{2} > \omega_{1}$ 为止的半开区间 $[\omega_{1}, \omega_{2})$ ，这种半开区间的并我们称之为事件，如 $A_{1} = [0, 5)$ ， $A_{2} = [-2, -1) \cup [0, 5)$ ，…。因此事件体 F 就是所有这种半开区间的并的全体。显然，F 是满足 a)，b），c) 三个要求的。

（3）概率 $P$ 。对于 $\mathcal{F}$ 中每一个事件 $A$ 存在一个实数 $p\{A\}$ ，我们称它为事件 $A$ 的概率，它应满足下面三个要求：a) $P$ 的取值在 0 到 1 之间，即对 $A \in \mathcal{F}, 0 \leqslant p\{A\} \leqslant 1; b)$ 基本事件空间 $\Omega$ 的概率等于 1，即 $p\{\Omega\} = 1; c)$ 两两不相交的事件的 联合概率等于这些事件的概率的和，即若 $A_{n} \in F, n = 1, 2, \cdots$ ，而且 $A_{i} \cap A_{i} = \varnothing^{①}$ ， $i \neq j, i, j = 1, 2, \cdots$ ，则 $p\left\{\bigcup_{n=1}^{\infty} A_{n}\right\} = \sum_{n=1}^{\infty} p\{A_{n}\} \leqslant 1$ ，右端级数总是收敛的，且其极限小于等于 1。

例如，对上面规定的事件我们规定事件 $A=\left[\omega_{1},\omega_{2}\right)$ 的概率是

$$
p \{A \} = \frac {1}{\sqrt {2 \pi}} \int_ {\omega_ {1}} ^ {\omega_ {2}} e ^ {- \omega^ {2}} d \omega
$$

显然这样规定的概率是满足上面三个要求的。

即使基本事件空间 $\Omega$ 是一样的，根据不同问题的不同需要可以有不同的事件体 $\mathcal{F}$ 和不同的概率 $P$ 。即使 $\Omega$ 和 $\mathcal{F}$ 都一样，由于客观实践的规律不同可以有不同的概率函数测度 $p$ ，于是 $\mathcal{F}$ 中的每一个事件有它不同的出现概率。因此三要素 $\{\Omega, \mathcal{F}, P\}$ 应该看为统一的整体，后者常称之为概率场或概率空间。

今后在研究某一个概率问题时，应该以同一个概率场（三要素）出发。同一个问题中不允许出现两个不同的概率场。例如，进行两个随机变量同时参加的运算中，它们应该定义在相同的概率场上。

从概率场（三要素）出发我们可以给出随机变量的严格定义。假定 $X(\omega)$ 是定义在基本事件空间 $\Omega$ 上的单值实函数，后者的取值范围是整个实数轴，且对任意一个实数 $x$ ，一切满足于不等式 $X(\omega) < x$ 的 $\omega$ 的集合是事件体 $\mathcal{F}$ 中的事件，即 $\{\omega: X(\omega) < x\} \in \mathcal{F}$ ，那么我们称 $X(\omega)$ 为实随机变量，函数 $W(x) = p\{X(\omega) < x\}$ 称为随机变量 $X$ 的概率分布函数。显然， $W(x)$ 是一个单调非降的左连续函数，它只取正值，并且 $W(-\infty) = 0, W(+\infty) = 1$ 。 $W(x)$ 对 $x$ 的导数（如果存在的话） $w(x) = \frac{d}{dx} W(x)$ ，称为随机变量 $X$ 的概率密度函数。如果我们引进 $\delta$ 函数，那么概率密度函数 $w(x)$ 对常见的随机变量都是存在的。例如，随机变量 $X$ 取值 $x_k$ 的概率为 $p_k$ ，那么 $W(x)$ 在 $x_k$ 点有一个数值为 $p_k$ 的跳跃， $w(x)$ 含有一个 $p_k \delta(x - x_k)$ 的分量。由 $W(x)$ 的非降性可知 $w(x)$ 恒取非负的值。当一个随机变量的概率分布函数或概率密度函数为已知时，就认为此随机变量已给定。由此可知，只有概率场 $\{\Omega, \mathcal{F}, P\}$ 和函数 $X(\omega)$ 二者联合起来才决定一个随机变量。

随机变量 X 的主要数值特性定义如下：

X 的数学期望（本章用符号“—”表示数学期望)

$$
\overline {{{X}}} = \int_ {- \infty} ^ {\infty} x w (x) d x \tag {14.1-1}
$$

X 的函数 $f(X)$ 的数学期望

$$
\overline {{f (X)}} = \int_ {- \infty} ^ {\infty} f (x) w (x) d x \tag {14.1-2}
$$

$X$ 的方差

$$
\sigma_ {X} ^ {2} = \overline {{[ X - \overline {{X}} ] ^ {2}}} = \int_ {- \infty} ^ {\infty} (x - \overline {{X}}) ^ {2} w (x) d x \tag {14.1-3}
$$

由方差的定义可知 $\delta_{X}^{2}\geqslant0$ ，当随机变量恒取常值时 $\sigma_{X}^{2}$ 等于零。

现在来考虑建立在同一个概率场 $\{\Omega, \mathcal{F}, P\}$ 上的两个随机变量 $X$ 与 $Y$ 。单个随机变量 $X$ 的概率密度函数是 $w_X(x)$ ，单个随机变量 $Y$ 的概率密度函数是 $w_Y(y)$ 。事件 $A = \{\omega: X(\omega) < x, Y(\omega) < y\}$ 是同时满足 $X(\omega) < x, Y(\omega) < y$ 的 $\omega$ 组成的集合，它的概率 $p\{A\} = p\{X < x, Y < y\} = W(x, y)$ 称为两个随机变量 $X$ 和 $Y$ 的联合概率分布函数。 $w(x, y) = \frac{\partial^2}{\partial x \partial y} W(x, y)$ 称为 $X$ 和 $Y$ 的联合概率密度函数。如果随机变量 $X$ 取值 $x$ 的概率不为零，事件 $B = \{\omega: X(\omega) = x, Y(\omega) < y\}$ 的概率记为 $p\{B\}$ ，那么

$$
W _ {Y \mid X} (y \mid x) = \frac {p \{B \}}{p \{X = x \}} \tag {14.1-4}
$$

称为 X 取 x 值时随机变量 Y 的条件概率分布函数。如果 X 在实轴上连续取值，那么 X 取某一点值的概率等于零，这时

$$
\begin{array}{l} W _ {Y \mid X} (y \mid x) = \lim _ {h \rightarrow 0} P \{Y <   y \mid x \leqslant X <   x + h \} \\ = \lim _ {h \rightarrow 0} \frac {P \{Y <   y , x \leqslant X <   x + h \}}{P \{x \leqslant X <   x + h \}} \tag {14.1-5} \\ \end{array}
$$

$w_{Y|X}(y|x)=\frac{\partial}{\partial y}W_{Y|X}(y|x)$ 称为条件概率密度函数。显然，下面等式成立

$$
w (x, y) = w _ {X} (x) w _ {Y \mid X} (y \mid x) = w _ {Y} (y) w _ {X \mid Y} (x \mid y) \tag {14.1-6}
$$

如果 $w(x,y)=w_{X}(x)w_{Y}(y)$ ，即 $w_{Y|X}(y|x)=w_{Y}(y)$ ， $w_{X|Y}(x|y)=w_{X}(x)$ ，那么称 X 和 Y 是互相独立的。在一般情况下则是 $w_{Y|X}(y|x)<w_{Y}(y)$ ， $w_{X|Y}(x|y)<w_{X}(x)$ ，所以 $w(x,y)<w_{X}(x)w_{Y}(y)$ 。单个随机变量的概率密度函数可以由联合概率密度函数求得

$$
w _ {X} (x) = \int_ {- \infty} ^ {\infty} w (x, y) d y, \quad w _ {Y} (y) = \int_ {- \infty} ^ {\infty} w (x, y) d x \tag {14.1-7}
$$

两个随机变量的乘积 XY 也是随机变量, 它的数学期望是

$$
\overline {{{X Y}}} = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} x y w (x, y) d x d y \tag {14.1-8}
$$

我们把

$$
r _ {X Y} = \overline {{[ X - \overline {{X}} ] [ Y - \overline {{Y}} ]}} \tag {14.1-9}
$$

称为 X 与 Y 的相关系数, 显然有 $r_{XY} = r_{YX}$ 。

$$
\rho_ {X Y} = \frac {1}{\sigma_ {X} \sigma_ {Y}} r _ {X Y} \tag {14.1-10}
$$

称为 $X$ 与 $Y$ 的比相关系数。由于对任意的 $a, b, \left[ a \frac{X}{\sigma_X} + b \frac{Y}{\sigma_Y} \right]$ 这个随机变量的方差总是大于或等于零的，所以显然有 $|\rho_{XY}| \leqslant 1$ 。如果 $\rho_{XY} = \pm 1$ ，那么 $X$ 和 $Y$ 有完全相互依赖的关系。如果 $\rho_{XY} = 0$ ，即 $r_{XY} = 0$ ，则称随机变量 $X$ 与 $Y$ 是互不相关的。如果 $X$ 与 $Y$ 互相独立，那么 $X$ 与 $Y$ 一定是互不相关的；但是如果 $X$ 与 $Y$ 互不相关，那么它们不一定互相独立。类似地

$$
\overline {{(Y \mid X = x)}} = \int_ {- \infty} ^ {\infty} y w _ {Y \mid X} (y \mid x) d y \tag {14.1-11}
$$

称为 X 取 x 值时 Y 的条件数学期望。如果 X 与 Y 互相独立，则 $\overline{(Y \mid X = x)} = \overline{Y}$ 。

如果随机变量 X 可以写为 $X = Y + iZ$ ，其中 Y 和 Z 是定义在同一个概率场上的实随机变量，那么 X 称为定义在这个概率场上的复随机变量。X 的复共轭随机变量是 $X^{*} = Y - iZ$ 。本章用“\*”号表示复共轭值。对于复随机变量，数学期望是个复数

$$
\overline {{X}} = \overline {{Y}} + i \overline {{Z}} \tag {14.1-12}
$$

方差却是正实数

$$
\sigma_ {X} ^ {2} = \overline {{[ X - \overline {{X}} ] [ X - \overline {{X}} ] ^ {*}}} = \overline {{[ X - \overline {{X}} ] ^ {2}}} = \sigma_ {Y} ^ {2} + \sigma_ {Z} ^ {2} \tag {14.1-13}
$$

两个复随机变量 X 与 W 的相关系数定义为

$$
r _ {X W} = \overline {{[ X - \overline {{X}} ] [ W - \overline {{W}} ] ^ {*}}} \tag {14.1-14}
$$

显然有 $r_{XW} = r_{WX}^{*}, |r_{XW}| \leqslant \sigma_X \sigma_W$ 。

现在来讨论随机变量序列的极限。在普通数列的极限问题中，如果数列 $\{x_{n}\}, n=1,2,\cdots$ 满足 $\lim_{n\to\infty}|a-x_{n}|=0,a$ 为某一常数，则 $a=\lim_{n\to\infty}x_{n},a$ 称为数列 $\{x_{n}\}$ 的极限。在随机问题中随机变量序列 $\{X_{n}\},n=1,2,\cdots$ 不能按一般方法取极限，随机变量模的平方的数学期望是一个数，可对这种数列取极限。假定对一个随机变量序列 $\{X_{n}\}$ 存在一个随机变量 X，使 $\lim_{n\to\infty}\overline{|X-X_{n}|^{2}}=0$ ，那么 X 就称为随机变量序列 $\{X_{n}\}$ 的均方极限，用 $X=1.i.m.X_{n}$ 来表示，以便区别于一般的极限。今后在随机的极限问题中，如求导数或求积分的运算中常采用均方极限。

如果 $g(X)$ 是实随机变量 $X$ 的一个非负函数那么

$$
\overline {{{{g (X)}}}} = \int_ {- \infty} ^ {\infty} g (x) w (x) d x \geqslant K \int_ {g (x) \geqslant K} w (x) d x
$$

后面一个积分是在所有满足 $g(x) \geqslant K$ 的部分上进行的, 这个积分正好就是 $p\{g(X) \geqslant K\}$ 。所以

$$
p \{g (X) \geqslant K \} \leqslant \frac {1}{K} \overline {{g (X)}} \tag {14.1-15}
$$

称为切比雪夫(Че́бышев)不等式。现在取 $g(X)=(X-\overline{X})^{2}$ ，那么 $\overline{g(X)}=\sigma_{X}^{2}$ ，设

$K=k^{2}\sigma_{X}^{2}$ ，就可以得到必耐梅-切比雪夫(Bienayme-Чебышев)不等式

$$
p \left\{\mid X - \overline {{{X}}} \mid > k \sigma_ {X} \right\} = p \left\{\mid X - \overline {{{X}}} \mid^ {2} \geqslant k ^ {2} \sigma_ {X} ^ {2} \right\} \leqslant \frac {1}{k ^ {2}} \tag {14.1-16}
$$

如果数学期望为零的随机变量序列 $\{X_{n}\}$ 均方收敛于 $X$ （数学期望也为零），即 $X = 1.\mathrm{i.m.}X_{n}$ ，那么任意给定小的 $\varepsilon >0$ 由不等式(14.1-16)就可以得到

$p\{|X - X_n|\geqslant \varepsilon \} \leqslant \frac{1}{\varepsilon^2}\sigma_{(X - X_n)}^2$ 。再由均方收敛的定义，由 $\sigma_{(X - X_n)}^2 = \overline{|X - X_n|^2}\rightarrow 0$ 则可得出 $\lim_{n\to \infty}p\{|X - X_n|\geqslant \varepsilon \} = 0$ 。这就是说，如果序列 $\{X_{n}\}$ 均方收敛于 $X$ ，那么 $X$ 也是序列 $\{X_{n}\}$ 在概率上的极限，或 $\{X_{n}\}$ 依概率收敛于 $X$ 。

这种序列极限的一个十分重要的例子是所谓的中心极限定理。在很多实际问题中，一个随机变量往往是由许多相互独立的随机因素的影响而引起的，每一个因素在总的影响中所起的作用基本上是均匀地大小。我们可以把这种随机变量看做是许多个相互独立的随机变量的和，每一个随机变量的方差远小于总的随机变量的方差。那么不管每一个随机变量的概率分布函数如何，它们之和的极限随机变量的概率分布将是高斯分布（也称正态分布）

$$
w (x) = \frac {1}{\sqrt {2 \pi} \sigma_ {X}} \exp \left\{- \frac {(x - \overline {{{X}}}) ^ {2}}{2 \sigma_ {X} {} ^ {2}} \right\} \tag {14.1-17}
$$

这就是中心极限定理 $^{[1]}$ 。

我们现在来讨论随机向量。由建立在同一个概率场上的 n 个随机变量 $X_{1}$ ， $X_{2}$ ， $\cdots$ ， $X_{n}$ 组成了一个 n 维随机向量

$$
\boldsymbol {X} ^ {\tau} = \left(X _ {1}, X _ {2}, \dots , X _ {n}\right) \tag {14.1-18}
$$

对 $\Omega$ 中给定的元 $\omega, X(\omega)$ 是一个 n 维列向量 $\boldsymbol{x}^{\tau} = (x_{1}, x_{2}, \cdots, x_{n})$ 。随机向量 X 的概率分布（或密度）函数就是 n 个随机变量 $X_{1}, X_{2}, \cdots, X_{n}$ 的联合概率分布（或密度）函数。它有如下特性

$$
\int_ {- \infty} ^ {\infty} \dots \int_ {- \infty} ^ {\infty} w x (\boldsymbol {x}) d x _ {2} \dots d x _ {n} = w _ {X _ {1}} (x _ {1}) \tag {14.1-19}
$$

$$
\int_ {- \infty} ^ {\infty} \dots \int_ {- \infty} ^ {\infty} w _ {X} (\boldsymbol {x}) d x _ {3} \dots d x _ {n} = w _ {X _ {1} X _ {2}} (x _ {1}, x _ {2}) \tag {14.1-20}
$$

于是可以推得随机向量 X 的数学期望 $\overline{X}$ 是一个 n 维列向量, 它的每个分量就是随机向量每个分量的数学期望

$$
\overline {{{X}}} ^ {\tau} = (\overline {{{X}}} _ {1}, \overline {{{X}}} _ {2}, \dots , \overline {{{X}}} _ {n}) \tag {14.1-21}
$$

X 的方差是一个 $n \times n$ 阶方阵, 记为

$$
\Sigma_ {X} ^ {2} = \overline {{[ X - \overline {{X}} ] [ \{X - \overline {{X}} \} ^ {*} ] ^ {\tau}}} = \left( \begin{array}{c c c} \sigma_ {X _ {1}} ^ {2} & r _ {X _ {1} X _ {2}} \dots r _ {X _ {1} X _ {n}} \\ r _ {X _ {2} X _ {1}} & \sigma_ {X _ {2}} ^ {2} \dots r _ {X _ {2} X _ {n}} \\ \vdots & \vdots & \vdots \\ r _ {X _ {n} X _ {1}} & r _ {X _ {n} X _ {2}} \dots \sigma_ {X _ {n}} ^ {2} \end{array} \right) \tag {14.1-22}
$$

上角注“τ”是矩阵转置符号。当 X 为实随机向量时，X 的方差阵是对称正定阵。如果 X 各分量两两不相关，那么方差阵是对角阵，对角线上的元是它各分量的方差 $\sigma_{X_{i}}^{2}$ 。两个随机向量（不一定是相同维数的）X, Y 的联合概率分布（或密度）函数是它们各分量 $X_{1}, X_{2}, \cdots, X_{n}, Y_{1}, Y_{2}, \cdots, Y_{m}$ 的联合概率分布（或密度）函数，且

$$
\int_ {- \infty} ^ {\infty} \dots \int_ {- \infty} ^ {\infty} w _ {X Y} (\boldsymbol {x}, \boldsymbol {y}) d x _ {2} \dots d x _ {n} d y _ {1} d y _ {3} \dots d y _ {m} = w _ {X _ {1} Y _ {2}} (x _ {1}, y _ {2}) \tag {14.1-23}
$$

因此, n 维随机向量 X 与 m 维随机向量 Y 的相关系数是 $n \times m$ 阶矩阵, 它的每一个元素是 X 的某个分量与 Y 的某个分量的相关系数

$$
R _ {X Y} = \overline {{[ \boldsymbol {X} - \overline {{{\boldsymbol {X}}}} ] [ \{\boldsymbol {Y} - \overline {{{\boldsymbol {Y}}}} \} ^ {*} ] ^ {\tau}}} = \left( \begin{array}{c c c} r _ {X _ {1} Y _ {1}} & r _ {X _ {1} Y _ {2}} \dots r _ {X _ {1} Y _ {m}} \\ r _ {X _ {2} Y _ {1}} & r _ {X _ {2} Y _ {2}} \dots r _ {X _ {2} Y _ {m}} \\ \vdots & \vdots & \vdots \\ r _ {X _ {n} Y _ {1}} & r _ {X _ {2} Y _ {2}} \dots r _ {X _ {n} Y _ {m}} \end{array} \right) \tag {14.1-24}
$$

随机向量的条件概率分布，条件数学期望，均方极限等都和随机变量相类似，这里就不再叙述了。我们仅提一下，具有高斯分布的 n 维随机向量 X 的概率密度函数是

$$
\begin{array}{l} w (\boldsymbol {x}) = w \left(x _ {1}, x _ {2}, \dots , x _ {n}\right) \\ = \frac {1}{(2 \pi) ^ {\frac {n}{2}} \left| \Sigma_ {\mathbf {x}} ^ {2} \right| ^ {\frac {1}{2}}} \exp \left[ - \frac {1}{2 \left| \Sigma_ {\mathbf {x}} ^ {2} \right|} \sum_ {i = 1} ^ {n} \sum_ {j = 1} ^ {n} \left| \Sigma_ {\mathbf {x}} ^ {2} \right| _ {i j} \left(x _ {i} - \bar {x} _ {i}\right) \left(x _ {j} - \bar {x} _ {j}\right) ^ {*} \right] \tag {14.1-25} \\ \end{array}
$$

其中 $|\Sigma_{\mathbf{x}}^{2}|$ 是方差阵 $\Sigma_{\mathbf{x}}^{2}$ 的行列式， $|\Sigma_{\mathbf{x}}^{2}|_{ij}$ 是方差阵 $\Sigma_{\mathbf{x}}^{2}$ 的元素 $r_{X_i X_j}$ 的代数余子式。

#### 14.2 随机变量和随机向量的几何概念

任何一个数学期望不等于零的随机变量可以看作为一个不为零的数和一个数学期望为零的随机变量之和。不失一般性，下面我们只讨论数学期望为零的、方差有界的随机变量。假定 $X$ 与 $Y$ 是同一个概率场上的两个实随机变量， $X$ 取值 $x$ 的概率密度函数为 $w_{X}(x), Y$ 取值 $y$ 的概率密度函数为 $w_{Y}(y)$ ，那么两个随机变量的线性组合 $Z = aX + bY$ ，其中 $a, b$ 为任意实常数，也是同一概率场上的实随机变量，它们的值域都可看作为整个实数轴 $R$ 。 $Z$ 的概率分布函数是

$$
W _ {z} (z) = \int_ {- \infty} ^ {\infty} d y \int_ {- \infty} ^ {\frac {z - b y}{a}} w (x, y) d x \tag {14.2-1}
$$

如果 X 与 Y 互相独立，那么

$$
w _ {Z} (z) = \int_ {- \infty} ^ {\infty} \frac {1}{| a |} w _ {X} \left[ \frac {z - b y}{a} \right] w _ {Y} (y) d y \tag {14.2-2}
$$

Z 的数学期望仍等于零, $\overline{Z}=a\overline{X}+b\overline{Y}=0$ ; 它的方差是

$$
\sigma_ {Z} ^ {2} = \overline {{(a X + b Y) ^ {2}}} = a ^ {2} \sigma_ {X} ^ {2} + b ^ {2} \sigma_ {Y} ^ {2} + 2 a b \sigma_ {X} \sigma_ {Y} \rho_ {X Y}
$$

由于 $\sigma_{X}^{2}, \sigma_{Y}^{2}$ 都有界， $|\rho_{XY}| \leqslant 1$ ，所以 $\sigma_{Z}^{2}$ 仍然有界。由此得到，一切建立在同一概率场上的取值于实轴的实随机变量（数学期望为零、方差有界）构成一个线性空间，而每一个这样的实随机变量都是此线性空间中的元（向量）。

在此空间中引进内积

$$
\langle X, Y \rangle = r _ {X Y} = \overline {{{{X Y}}}} = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} x y w (x, y) d x d y \tag {14.2-3}
$$

很容易证明，这种用相关系数定义的内积满足条件:(1) $\langle X,Y\rangle=\langle Y,X\rangle$ 。

(2) $\langle a_{1}X_{1} + a_{2}X_{2},Y\rangle = a_{1}\langle X_{1},Y\rangle +a_{2}\langle X_{2},Y\rangle$ ，其中 $a_1,a_2$ 是实常数。

(3) $\langle X,X\rangle\geqslant0$ ,当且仅当 X=0 时才等于零。

根据此内积的定义，此空间的元的范数 $\parallel X \parallel$ 为

$$
\| X \| ^ {2} = \langle X, X \rangle = \int_ {- \infty} ^ {\infty} x ^ {2} w _ {X} (x) d x = \sigma_ {X} ^ {2} \geqslant 0 \tag {14.2-4}
$$

同样，可以证明:

(4) $\|aX\| = |a| \cdot \|X\|$ ，其中 a 是实常数。

(5) $|\langle X, Y \rangle| \leqslant \|X\| \cdot \|Y\|$ , 这就是施瓦尔茨-布涅柯夫斯基(Schwarz-Bunjakovskii)不等式, 即第 14.1 节中已说过的

$$
\mid r _ {X Y} \mid \leqslant \sigma_ {X} \sigma_ {Y}
$$

(6) $\| X + Y \| \leqslant \| X \| + \| Y \|$ , 这就是三角形不等式, 这是因为

$$
\begin{array}{c} \parallel X + Y \parallel^ {2} = \parallel X \parallel^ {2} + \parallel Y \parallel^ {2} + 2 \langle X, Y \rangle \leqslant \parallel X \parallel^ {2} + \parallel Y \parallel^ {2} + 2 | \langle X, Y \rangle | \leqslant \\ \parallel X \parallel^ {2} + \parallel Y \parallel^ {2} + 2 \parallel X \parallel \cdot \parallel Y \parallel = (\parallel X \parallel + \parallel Y \parallel) ^ {2} \end{array}
$$

只有在 $Y=\lambda X, \lambda$ 为正实数时才取等号。

于是，这个线性空间是个内积空间。我们可以把 $\|X-Y\|$ 看作为两个随机变量 X 和 Y 的距离。在这空间中，如果 $\langle X,Y\rangle=0$ , 则称此两个随机变量直交。在空间内任一随机变量序列的均方极限如存在，那么它仍是数学期望为零、方差有界的实随机变量。我们把所有这些极限点和线性空间联合起来就是一个完备空间。这样，建立在同一概率场的这种随机变量及极限点构成了一个希尔伯特空间（完备的内积空间） $H_{1}$ 。每一个这样的随机变量是希尔伯特空间 $H_{1}$ 中的一个元（向量）。像一般函数空间一样, $H_{1}$ 是无穷维的。

如果 X, Y 是复随机变量, 以上论断仍然有效, 即一切数学期望为零、方差有界的复随机变量也构成一个希尔伯特空间 $H_{1}$ 。不过内积的定义应改为

$$
\langle X, Y \rangle = r _ {X Y} = \overline {{{{X Y ^ {*}}}}} \tag {14.2-5}
$$

它是一个复数。上述条件(1)应改为 $\langle X,Y\rangle=\langle Y,X\rangle^{*}$ ，(2)和(4)中的系数均为复数。范数 $\|X\|$ 应改为

$$
\| X \| ^ {2} = \langle X, X \rangle = \int | x | ^ {2} w (x) d x = \sigma_ {X} ^ {2} \geqslant 0 \tag {14.2-6}
$$

假定在空间 $H_{1}$ 中任意给定两个元 X 和 Y, 那么元 Y 总可以表示成为两个互相直交的分量的和

$$
Y = Y _ {X} + Y \tag {14.2-7}
$$

其中 Y 与 X 直交， $\langle Y, X \rangle = 0$ ; $Y_{X}$ 是 Y 在 X 上的直交投影，我们以后记以 $P(X)Y$ ，它等于某个常数乘以 X

$$
Y _ {X} = P (X) Y = a X \tag {14.2-8}
$$

我们来求 $Y$ 与 $X$ 的内积

$$
\langle Y, X \rangle = \langle P (X) Y, X \rangle + \langle Y, X \rangle = a \langle X, X \rangle
$$

如果 $\langle X,X\rangle\neq0$ ,就可以得到常数 a

$$
a = \langle Y, X \rangle \cdot \langle X, X \rangle^ {- 1} = r _ {Y X} \sigma_ {X} ^ {- 2} \tag {14.2-9}
$$

Y 的两个互相直交的分量分别是

$$
P (X) Y = r _ {Y X} \sigma_ {X} ^ {- 2} X
$$

和

$$
Y = Y - P (X) Y = Y - r _ {Y X} \sigma_ {X} ^ {- 2} X
$$

数学期望为零的 n 维随机向量就是由 n 个数学期望为零的随机变量组成的。如果这些随机变量的方差有界，那么 n 维随机向量的方差阵的每个元素都有界。由于每一个数学期望为零、方差有界的随机变量可以看作为 $H_{1}$ 空间中的一个元，因此 n 维数学期望为零的随机向量可以看作为 n 个 $H_{1}$ 空间的积空间 $H_{n}$ 中的一个元。在 $H_{n}$ 中两个 n 维随机向量 X 和 Y 的内积定义为

$$
\langle \boldsymbol {X}, \boldsymbol {Y} \rangle = \sum_ {i = 1} ^ {n} \left\langle X _ {i}, Y _ {i} \right\rangle = \sum_ {i = 1} ^ {n} r _ {X _ {i} Y _ {i}} = \operatorname{tr} R x y = \overline {{{\boldsymbol {Y} ^ {\tau} \boldsymbol {X}}}} \tag {14.2-10}
$$

其中 tr 是方阵诸对角线元素之和, 叫做迹。显然, 由此内积定义的范数为

$$
\| \boldsymbol {X} \| = \langle \boldsymbol {X}, \boldsymbol {X} \rangle = \sum_ {i = 1} ^ {n} \sigma_ {\chi_ {i}} ^ {2} = \operatorname{tr} (\Sigma_ {\chi} ^ {2}) \tag {14.2-11}
$$

它满足前面所述的性质(1)—(6)。

在 $H_{n}$ 中如果 $\langle X,Y\rangle=0$ ，就称 X 与 Y 直交。要注意，如果两个 n 维随机向量 X,Y 的相关矩阵是零矩阵，那么 X 与 Y 一定直交；反之，如果 X 与 Y 直交，那么相关矩阵不一定是零矩阵，即 X 的任意分量 $X_{i}$ 与 Y 的任意分量 $Y_{j}$ 不一定是直交的。这与 $H_{1}$ 中的情况不同。

假定在 $H_{n}$ 中任意给定两个元 $\mathbf{X}$ 和 $\mathbf{Y}$ , 那么 $\mathbf{Y}$ 总可以表示为两个相互直交的元的和

$$
\mathbf {Y} = \mathbf {Y} _ {X} + \mathbf {Y} \tag {14.2-12}
$$

其中 Y 与 X 直交, $Y_{x}$ 是 Y 在 X 上的直交投影

$$
\mathbf {Y} _ {X} = P (\mathbf {X}) \mathbf {Y} = a \mathbf {X} \tag {14.2-13}
$$

如果 $\operatorname{tr}(\Sigma_X^2) \neq 0$ ，那么可求出常数 $a$

$$
a = \langle Y, X \rangle \cdot \langle X, X \rangle^ {- 1} = \langle Y, X \rangle \mathrm{tr} ^ {- 1} (\Sigma_ {X} ^ {2}) = \frac {\sum_ {i = 1} ^ {n} r _ {Y _ {i} X _ {i}}}{\sum_ {i = 1} ^ {n} \sigma_ {X _ {i}} ^ {2}} \tag {14.2-14}
$$

根据希尔伯特空间 $H_{n}$ 的几何特性, Y 到 X 方向的最短距离就是 Y 的范数。

用希尔伯特空间的方法讨论随机向量，使得一些问题在几何意义上变得十分清晰、简单。必要时我们就用希尔伯特空间的一些定理来处理随机变量和随机向量。在下一章，我们将用它来解决预测、过滤等问题。

#### 14.3 随机函数

随机函数 $Y(\omega,t)$ 是以 t 为参变量的一簇随机变量。对于每一个固定的 $t=t_{k}$ ， $Y(\omega,t_{k})$ 是定义在给定概率场 $\{\Omega,\mathcal{F},P\}$ 上的一个随机变量。今后在一般情况下我们将省略 $\omega$ 只写为 $Y(t)$ 。如果 t 只取某些离散值，如 $t_{0},t_{1},t_{2},\cdots$ ，则 $Y(t)$ 称为随机序列，简记为 $Y_{k},k=0,1,2,\cdots$ 。如果 t 在某个时间区间内连续取值，则 $Y(t)$ 称为随机过程。如果 $\omega$ 是基本事件空间 $\Omega$ 中的一个确定的元，那么 $Y(\omega,t)$ 就是一个非随机的数量函数。对每一个给定的 $\omega$ 就相应地有一个确定的数量函数 $y(\omega,t)$ ，简记为 $y(t)$ ，它称为随机函数 $Y(t)$ 的一个现实。

n 个随机函数 $Y_{1}(t)$ , $Y_{2}(t)$ , $\cdots$ , $Y_{n}(t)$ 组成一个 n 维的向量随机函数 $\mathbf{Y}(t)$ 。它是以 t 为参变量的一簇随机向量，对每一个固定的 $t_{k}$ , $\mathbf{Y}(t_{k})$ 是一个随机向量。对每一个给定的 $\omega\mathbf{Y}(t)$ 就对应一个非随机的向量函数 $\mathbf{y}(t)$ , $\mathbf{y}(t)$ 就称为向量随机函数 $\mathbf{Y}(t)$ 的一个现实。根据 t 的取值情况又可分为向量随机序列 $Y_{k}$ , $k=0,1,2,\cdots$ 和向量随机过程。随机函数我们可以看作为一维的向量随机函数。

假定 t 在时间轴上某一个集合 T 内取值。对于任意的 $t \in T, Y(t)$ 的分布函数 $W_{1}(y,t) = p\{Y_{1}(t) < y_{1}, \cdots, Y_{n}(t) < y_{n}\}$ 称为向量随机函数的第一概率分布函数，它是 t 和 $y_{1}, y_{2}, \cdots, y_{n}$ 的函数，它也就是 $Y(t)$ 这个随机向量的概率分布函数。同样，可以定义次数更高的概率分布函数。第二概率分布函数 $W_{2}(y_{1}, t_{1}; y_{2}, t_{2})$ 就是两个随机向量 $Y(t_{1})$ 和 $Y(t_{2})$ 的联合概率分布函数。如果对 T 内任意 n 个 t, n 是任意的正整数， $Y(t)$ 的第 n 次概率分布函数已确定的话，则认为向量随机函数 $Y(t)$ 已给定。同样，也可以定义各次概率密度函数。概率分布函数和概率密度函数之间的关系为

$$
W _ {m} \left(\mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}, \dots ; \mathbf {y} _ {m}, t _ {m}\right) = \underbrace {\int_ {- \infty} ^ {y _ {1}} \cdots \int_ {- \infty} ^ {y _ {m}}} _ {m \text {个}} w _ {n} \left(\mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}, \dots ; \mathbf {y} _ {m}, t _ {m}\right) d \mathbf {y} _ {1} d \mathbf {y} _ {2} \dots d \mathbf {y} _ {m} \tag {14.3-1}
$$

其中每一个积分都是重积分，重数是向量随机函数的维数。根据概率的基本性

质， $W_{m}$ 和 $w_{m}$ 满足下列条件：

（1） $W_{m}$ 对每个 $y_{1}, y_{2}, \cdots, y_{m}$ 的分量都是单调非降左连续的， $0 \leqslant W_{n} \leqslant 1$ 。 $w_{m}$ 恒取非负值。

（2）对各对变量 $y_{i}, t_{i}, i=1,2,\cdots,m,\cdots,W_{m}$ 与 $w_{m}$ 都是对称的，例如

$$
W _ {2} \left(\mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}\right) = W _ {2} \left(\mathbf {y} _ {2}, t _ {2}; \mathbf {y} _ {1}, t _ {1}\right)
$$

$$
w _ {3} \left(\mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}; \mathbf {y} _ {3}, t _ {3}\right) = w _ {3} \left(\mathbf {y} _ {3}, t _ {3}; \mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}\right) = w _ {3} \left(\mathbf {y} _ {2}, t _ {2}; \mathbf {y} _ {3}, t _ {3}; \mathbf {y} _ {1}, t _ {1}\right)
$$

（3）由次数较高的概率密度函数可以导出次数较低的概率密度函数，例如，设 k<n,则

$$
\begin{array}{l} w _ {k} \left(\mathbf {y} _ {1}, t _ {1}; \dots ; \mathbf {y} _ {k}, t _ {k}\right) = \int_ {- \infty} ^ {\infty} \dots \int_ {- \infty} ^ {\infty} w _ {m} \left(\mathbf {y} _ {1}, t _ {1}; \dots ; \mathbf {y} _ {k}, t _ {k}; \mathbf {y} _ {k + 1}, t _ {k + 1}; \dots ; \mathbf {y} _ {m}, t _ {m}\right) \\ \times d \mathbf {y} _ {k + 1} \dots d \mathbf {y} _ {m} \tag {14.3-2} \\ \end{array}
$$

并且有 $\int_{-\infty}^{\infty} w_1(\mathbf{y}_1, t_1) d\mathbf{y}_1 = 1$ 。

(4) $W_{m}(\mathbf{y}_{1},t_{1};\dots ; - \infty ,t_{k};\dots ;\mathbf{y}_{m},t_{m}) = 0,\quad 1\leqslant k\leqslant m$

$$
W _ {m} \left(\infty , t _ {1}; \dots ; \infty , t _ {k}; \dots ; \infty , t _ {m}\right) = 1
$$

这里，在 $t_{k}$ 时 $y_{k}$ 为 $-\infty$ 或 $+\infty$ 是指它的每个分量都取值 $-\infty$ 或 $+\infty$ 。

可以看出随机函数的概率分布（密度）函数都是和参变量 t 有关的, m 次分布（密度）函数就和 m 个时间有关。因此, 由各次概率密度函数确定的一些统计特性也和时间有关; 由第一概率密度函数确定的统计特性是一个时间的函数, 由第二概率密度函数确定的统计特性是两个时间的函数。

由第一概率密度函数确定的统计特性主要有：

数学期望（或系集平均值）是个非随机的列向量函数

$$
\overline {{{\boldsymbol {Y} (t)}}} = \int_ {- \infty} ^ {\infty} \boldsymbol {y} w _ {1} (\boldsymbol {y}, t) d \boldsymbol {y} \tag {14.3-3}
$$

它的每个分量是向量随机函数每个分量的数学期望

$$
\overline {{{\boldsymbol {Y} (t) ^ {\tau}}}} = (\overline {{{Y _ {1} (t)}}}, \overline {{{Y _ {2} (t)}}}, \dots , \overline {{{Y _ {n} (t)}}}) \tag {14.3-4}
$$

它们都是时间的函数。

方差阵

$$
\begin{array}{l} \Sigma_ {Y} ^ {2} (t) = \overline {{[ Y (t) - \overline {{Y (t)}} ] [ \{Y (t) - \overline {{Y (t)}} \} ^ {*} ] ^ {\tau}}} \\ = \langle \mathbf {Y} (t) - \overline {{{\mathbf {Y} (t)}}}, \mathbf {Y} (t) - \overline {{{\mathbf {Y} (t)}}} \rangle \tag {14.3-5} \\ \end{array}
$$

是非随机的方阵，它也是时间的函数，对每个固定的 t 它是非负阵。对于一维随机函数来说，方差是非负的时间函数。

由第二概率密度函数确定的统计特性主要有：

$Y(t)$ 的自相关函数阵是两个时间变量的函数

$$
R _ {Y} \left(t _ {1}, t _ {2}\right) = \overline {{\left[ Y (t _ {1}) - \overline {{Y (t _ {1})}} \right] \left[ \left\{Y (t _ {2}) - \overline {{Y (t _ {2})}} \right\} ^ {*} \right] ^ {\tau}}}
$$

$$
= \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} \left[ \mathbf {y} _ {1} - \overline {{\mathbf {Y} (t _ {1})}} \right] \left[ \left\{\mathbf {y} _ {2} - \overline {{\mathbf {Y} (t _ {2})}} \right\} ^ {*} \right] ^ {\tau} w _ {2} \left(\mathbf {y} _ {1}, t _ {1}; \mathbf {y} _ {2}, t _ {2}\right) d \mathbf {y} _ {1} d \mathbf {y} _ {2} \tag {14.3-6}
$$

它代表向量随机函数 $Y(t)$ 在 $t_{1}$ 和 $t_{2}$ 两个时刻的值的线性相关程度。如果 $Y(t_{1})$ 与 $Y(t_{2})$ 互不相关，那么 $R_{Y}(t_{1}, t_{2}) = 0$ 。当 $t_{1} = t_{2} = t$ 时 $R_{Y}(t_{1}, t_{2}) = R_{Y}(t) = \sum_{Y}^{2}(t)$ 。显然 $R_{Y}(t_{1}, t_{2}) = (R_{Y}^{*}(t_{2}, t_{1}))^{\tau}$ 。

建立在同一个概率场上的两个向量随机过程 $X(t)$ 和 $Y(t)$ 的互相关函数阵也是两个时间变量的函数

$$
\begin{array}{l} R _ {X Y} \left(t _ {1}, t _ {2}\right) = \overline {{\left[ X \left(t _ {1}\right) - \overline {{X \left(t _ {1}\right)}} \right] \left[ \left\{Y \left(t _ {2}\right) - \overline {{Y \left(t _ {2}\right)}} \right\} ^ {*} \right] ^ {\tau}}} \\ = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} [ \boldsymbol {x} - \overline {{{\boldsymbol {X} (t _ {1})}}} ] [ \{\boldsymbol {y} - \overline {{{\boldsymbol {Y} (t _ {2})}}} \} ^ {*} ] ^ {\tau} w _ {2} (\boldsymbol {x}, t _ {1}; \boldsymbol {y}, t _ {2}) d \boldsymbol {x} d \boldsymbol {y} \tag {14.3-7} \\ \end{array}
$$

其中 $w_{2}(x,t_{1};y,t_{2})$ 是联合第二概率密度函数。显然， $R_{XY}(t_{1},t_{2})=\left[R_{YX}^{*}(t_{2},t_{1})\right]^{\tau}$ 。

假定 $\mathbf{Y}(t)$ 是一个在时间区间 T 上定义的向量随机过程。对于 T 内任意一点 $t_{0}$ ，如果属于 T 的变量 t 自任何方向无限趋于 $t_{0}$ 时， $\mathbf{Y}(t)$ 的每一个分量都有 $1.i.m.Y_{i}(t)=Y_{i}(t_{0}), i=1,2,\cdots,n$ 成立，那么称 $Y_{i}(t)$ 和 $\mathbf{Y}(t)$ 在 $t_{0}$ 点是均方连续的，简称连续。如果随机过程 $\mathbf{Y}(t)$ 对 T 内每一点都连续，那么称 $\mathbf{Y}(t)$ 在 T 上连续。容易检验，如果随机过程是连续的，那么它的数学期望 $\overline{\mathbf{Y}(t)}$ 和自相关函数阵 $R_{Y}(t_{1},t_{2})$ 的每个分量也是连续的；相反，如果随机过程的数学期望和自相关函数阵的每个分量都连续，那么随机过程也连续。

可以对随机过程 $Y(t)$ 进行各种运算。如果随机过程 $X(t)$ 是几个不同维数的向量随机过程 $Y_{k}(t), k=1,2,\cdots,r$ 的线性叠加

$$
\boldsymbol {X} (t) = \sum_ {k = 1} ^ {r} C _ {k} (t) \boldsymbol {Y} _ {k} (t) \tag {14.3-8}
$$

其中 $C_{k}(t)$ 是相应阶数的矩阵, 是 t 的函数, 那么 $X(t)$ 的数学期望为

$$
\overline {{{\boldsymbol {X} (t)}}} = \sum_ {k = 1} ^ {r} C _ {k} (t) \overline {{{\boldsymbol {Y} _ {k} (t)}}} \tag {14.3-9}
$$

自相关函数阵为

$$
R _ {X} (t _ {1}, t _ {2}) = \sum_ {k = 1} ^ {r} \sum_ {l = 1} ^ {r} C _ {k} (t _ {1}) R _ {Y _ {k} Y _ {l}} (t _ {1}, t _ {2}) C _ {l} (t _ {2}) ^ {*} \tag {14.3-10}
$$

其中 $C_{l}(t_{2})^{*}$ 是 $C_{l}(t_{2})$ 的复共轭矩阵。

现在我们来定义随机过程的导数和积分。随机过程 $\left[Y(t+\Delta t)-Y(t)\right]/\Delta t$ 当 $\Delta t$ 趋于零时的均方极限，如果存在的话，称为随机过程 $Y(t)$ 的导数

$$
\dot {\mathbf {Y}} (t) = \frac {d}{d t} \mathbf {Y} (t) = \operatorname * {l i m.} _ {\Delta t \rightarrow 0} \frac {Y (t + \Delta t) - Y (t)}{\Delta t} \tag {14.3-11}
$$

向量随机过程的导数也是一个向量随机过程，导数的每个分量是原过程相应分量

的导数

$$
\dot {\mathbf {Y}} ^ {\tau} (t) = \frac {d}{d t} \mathbf {Y} ^ {\tau} (t) = \left[ \frac {d}{d t} Y _ {1} (t), \frac {d}{d t} Y _ {2} (t), \dots , \frac {d}{d t} Y _ {n} (t) \right] \tag {14.3-12}
$$

根据导数和数学期望的定义可以知道，求数学期望和求导数这两个运算是可以交换的。所以随机过程的导数的数学期望等于数学期望的导数

$$
\overline {{\frac {d}{d t} \mathbf {Y} (t)}} = \frac {d}{d t} \overline {{\mathbf {Y} (t)}} \tag {14.3-13}
$$

随机过程导数的相关函数阵等于过程的相关函数阵对两个时间变量的联合二阶偏导数

$$
R _ {Y} (t _ {1}, t _ {2}) = \frac {\partial^ {2}}{\partial t _ {1} \partial t _ {2}} R _ {Y} (t _ {1}, t _ {2}) \tag {14.3-14}
$$

并不是所有随机过程都有导数存在，导数存在的充分必要条件是随机过程的相关函数阵对两个变量的联合二阶偏导数存在。

假定 $Y(t)$ 是一个随机过程, $g(s, t)$ 是一确定的两个变量的函数, 如果

$$
X (s) = \int_ {a} ^ {b} g (s, t) Y (t) d t \tag {14.3-15}
$$

存在，那么称 $X(s)$ 为 $Y(t)$ 的积分变换, $g(s,t)$ 称为核函数。公式(14.3-15)理解为当最大的 $\Delta t_{k}$ 趋于零时黎曼(Rieman)和 $\sum_{k} g(s,t_{k})Y(t_{k})\Delta t_{k}$ 的均方极限, 其中 $\Delta t_{k}$ 是区间 $[a,b]$ 任意划分成的无数小区间中的一个, $t_{k}$ 是小区间 $\Delta t_{k}$ 中的任意一个点。并不是所有随机过程对核函数的积分都存在, 积分存在的充分必要条件是双重积分

$$
\int_ {a} ^ {b} \int_ {a} ^ {b} g (s _ {1}, t _ {1}) g ^ {*} (s _ {2}, t _ {2}) R _ {Y} (t _ {1}, t _ {2}) d t _ {1} d t _ {2}
$$

存在并且有界，其中 $g^{*}(s,t)$ 是 $g(s,t)$ 的共轭复函数。一般情况下只需要用到它的充分条件就够了，即 $g(s,t)$ 均方可积

$$
\int_ {a} ^ {b} | g (s, t) | ^ {2} d t <   \infty
$$

向量随机过程的积分也是向量随机过程，积分的每个分量等于原过程相应分量的积分

$$
\int_ {a} ^ {b} g (s, t) \mathbf {Y} (t) d t = \left[ \begin{array}{c} \int_ {a} ^ {b} g (s, t) Y _ {1} (t) d t \\ \vdots \\ \int_ {a} ^ {b} g (s, t) Y _ {n} (t) d t \end{array} \right] \tag {14.3-16}
$$

同样，积分变换存在时，数学期望和积分这两种运算可以互相交换。随机过程积分 $X(s)$ 的数学期望为

$$
\overline {{{\boldsymbol {X} (s)}}} = \int_ {a} ^ {b} g (s, t) \overline {{{\boldsymbol {Y} (t)}}} d t \tag {14.3-17}
$$

$X(s)$ 的相关函数是

$$
R _ {X} (s _ {1}, s _ {2}) = \int_ {a} ^ {b} \int_ {a} ^ {b} g (s _ {1}, t _ {1}) R _ {Y} (t _ {1}, t _ {2}) g ^ {*} (s _ {2}, t _ {2}) d t _ {1} d t _ {2} \tag {14.3-18}
$$

今后我们经常会遇到一类特殊的随机过程或随机序列。对任意正整数 m，它的第 m 次概率密度函数 $w_{n}(y_{1}, t_{1}; y_{2}, t_{2}; \cdots; y_{m}, t_{m})$ 如式(14.1-22)形式的话，就叫做高斯随机过程或高斯随机序列。如是一维高斯过程（或序列），对任意正整数 m，m 个随机变量 $Y(t_{1}), Y(t_{2}), \cdots, Y(t_{m})$ 组成的 m 维随机向量是高斯分布的，如是 n 维高斯过程（或序列），m 个随机向量 $Y(t_{1}), Y(t_{2}), \cdots, Y(t_{m})$ 组成的 mn 维随机向量将是高斯分布的。对于高斯过程（或序列）来说，只要知道它的数学期望和相关矩阵，那么它的分布就完全确定了。如果高斯过程在 $t_{1}, t_{2}, \cdots, t_{m}$ 上取值的随机向量是互不相关的，那么它们也是互相独立的。

#### 14.4 平稳随机函数

在实际的工程问题中常碰到这样一类随机过程 $Y(t)$ : 当所有的时间沿时间轴同时移动一个位置时它的各次概率密度函数都保持不变, 也就是对任意的 $y_{1}, y_{1}, \cdots, y_{m}$ 和 $t_{1}, t_{2}, \cdots, t_{n}, m$ 为任意的正整数, 和任意的 $\lambda$ , 下列等式永远成立

$$
w _ {m} \left(\mathbf {y} _ {1}, t _ {1}; \dots ; \mathbf {y} _ {n}, t _ {n}\right) = w _ {m} \left(\mathbf {y} _ {1}, t _ {1} + \lambda ; \dots ; \mathbf {y} _ {n}, t _ {n} + \lambda\right) \tag {14.4-1}
$$

我们称这种随机过程 $Y(t)$ 为窄平稳过程。在分析控制系统在随机干扰下的准确度及与此有关的随机函数的性质时，往往只用到数学期望和相关函数阵，也就是只以第一、第二概率密度函数为基础。设随机过程 $Y(t)$ 的数学期望恒为常值，它的相关函数 $R_{Y}(t_{1}, t_{2})$ 只与 $\lambda = t_{1} - t_{2}$ 有关，而且方差阵 $\Sigma_{Y}$ 为有界（它的每个元素有界），那么我们称它为宽平稳过程。显然，如果窄平稳过程的方差阵为有界，那么它一定也是宽平稳过程。今后，我们只讨论宽平稳过程。同样，具有类似性质的随机序列称为宽平稳序列。

根据平稳随机函数的定义我们就可以得到它的相关函数 $R_{Y}(\lambda)$ 的性质：

(1) $R_{Y}(0)=\langle Y(t),Y(t)\rangle=\Sigma_{Y}^{2}$ (14.4-2)

$\lambda$ 等于零时的相关函数阵就是方差阵，它是不随时间变化的常方阵，而且是非负的。当平稳随机过程是一维时

$$
r _ {Y} (0) = \langle Y (t), Y (t) \rangle = \sigma_ {Y} ^ {2} \geqslant 0 \tag {14.4-3}
$$

(2) $R_{Y}(\lambda) = \langle \mathbf{Y}(t + \lambda),\mathbf{Y}(t)\rangle = \{\langle \mathbf{Y}(t),\mathbf{Y}(t + \lambda)\rangle^{*}\}^{\tau} = \{\left[R_{Y}(-\lambda)\right]^{*}\}^{\tau}$ (14.4-4)

如是一维实平稳随机过程 $Y(t)$ ，则

$$
r _ {Y} (\lambda) = r _ {Y} (- \lambda) \tag {14.4-5}
$$

(3) 对一维平稳随机过程来说

$$
\mid r _ {Y} (\lambda) \mid \leqslant r _ {Y} (0) \tag {14.4-6}
$$

这是因为 $|r_Y(\lambda)| = |\langle Y(t + \lambda), Y(t) \rangle| \leqslant \|Y(t + \lambda)\| \cdot \|Y(t)\| = \sigma_Y^2 = r_Y(0)$ 。

读者容易验证，平稳随机过程 $Y(t)$ 在所有的 t 上连续的充分必要条件是它的相关函数阵 $R_{Y}(\lambda)$ 的各元素在 $\lambda=0$ 点连续。对一维随机过程来说，根据第 14.3 节中随机过程导数的定义可推得数学期望为零的可微实平稳随机过程 $Y(t)$ 的自相关函数, $r_{Y}(\lambda)$ 的导数在 $\lambda=0$ 点的值为零，即

$$
\left[ \frac {d}{d \tau} r _ {Y} (\lambda) \right] _ {\lambda = 0} = 0 \tag {14.4-7}
$$

也就是平稳随机过程和它的导数在同一时刻的值是互不相关的。这是因为

$$
r _ {Y} (\lambda) = \overline {{Y (t) Y (t - \lambda)}} = \overline {{Y (t + \lambda) Y (t)}}
$$

它们对 $\lambda$ 的导数在 $\lambda=0$ 点的值是

$$
\left[ \frac {d}{d \lambda} r _ {Y} (\lambda) \right] _ {\lambda = 0} = - \overline {{Y (t) \left[ \frac {d}{d t} Y (t) \right]}} = \overline {{\left[ \frac {d}{d t} Y (t) \right] Y (t)}}
$$

此式只有等于零才可能成立，所以等式(14.4-7)是正确的。根据同样方法对于足够光滑的平稳过程 $Y(t)$ 可以得到

$$
\left[ \frac {d}{d \lambda} r _ {Y} (\lambda) \right] _ {\lambda = 0} = \left[ \frac {d ^ {3}}{d \lambda^ {3}} r _ {Y} (\lambda) \right] _ {\lambda = 0} = \left[ \frac {d ^ {5}}{d \lambda^ {5}} r _ {Y} (\lambda) \right] _ {\lambda = 0} = \dots = 0
$$

$$
\left[ \frac {d ^ {2}}{d \lambda^ {2}} r _ {Y} (\lambda) \right] _ {\lambda = 0} = - \sigma_ {\frac {d Y}{d t}} ^ {2}
$$

$$
\left[ \frac {d ^ {4}}{d \lambda^ {4}} r _ {Y} (\lambda) \right] _ {\lambda = 0} = \sigma_ {\frac {d ^ {2} Y}{d t ^ {2}}} ^ {2}, \dots \tag {14.4-8}
$$

于是，无限次可微的平稳随机过程 $Y(t)$ 的自相关函数可以展开为泰勒级数

$$
r _ {Y} (\lambda) = r _ {Y} (0) + \frac {\lambda^ {2}}{2 !} \frac {d ^ {2}}{d \lambda^ {2}} r _ {Y} (0) + \frac {\lambda^ {4}}{4 !} \frac {d ^ {4}}{d \lambda^ {4}} r _ {Y} (0) + \dots \tag {14.4-9}
$$

从式 $(14.4-9)$ 也可以导出式 $(14.4-5)$ 。

如果在同一概率场上的两个平稳向量随机函数 $X(t)$ 和 $Y(t)$ 的互相关函数阵 $R_{XY}(t_1,t_2)$ 只和 $\lambda = t_1 - t_2$ 有关，那么称 $X(t)$ 和 $Y(t)$ 是平稳相关的。向量随机函数 $X(t)$ 是平稳的必须且只需它的每个分量 $X_{i}(t)$ 是平稳的和各分量之间是平稳相关的。对平稳相关的 $X(t)$ 和 $Y(t)$ 的互相关函数阵来说

$$
R _ {X Y} (\lambda) = \left[ R _ {Y X} ^ {*} (- \lambda) \right] ^ {\tau} \tag {14.4-10}
$$

根据实验所得的数据来确定平稳随机过程的相关函数和数学期望时，如果采用系集平均的方法，就要同时对同一个系统进行大量的重复观测，这种做法在实际上是有困难的，或者要付出高昂的代价。因为平稳随机过程的数学期望和相关函数与实验观测计时的起点无关，我们要问是否可以用平稳随机过程的一个现实 $y(\omega,t)$ 来确定它的数学期望和相关函数呢?可以证明，对于连续平稳的一维实随机过程 $Y(t)$ 等式

$$
\overline {{Y}} = 1. \underset {T \rightarrow \infty} {\mathrm{i.m.}} \cdot \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t \tag {14.4-11}
$$

成立的充分必要条件是

$$
1. \underset {T \rightarrow \infty} {\mathrm{i.m.}} \frac {1}{2 T} \int_ {- T} ^ {T} r _ {Y} (\lambda) d \tau = 0 \tag {14.4-12}
$$

这是因为

$$
\begin{array}{l} \left| \left| \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t - \overline {{Y}} \right| \right| ^ {2} = \left| \left| \frac {1}{2 T} \int_ {- T} ^ {T} [ Y (t) - \overline {{Y}} ] d t \right| \right| ^ {2} \\ = \frac {1}{4 T ^ {2}} \left\langle \int_ {- T} ^ {T} [ Y (t) - Y ] d t, \int_ {- T} ^ {T} [ Y (t) - \overline {{{Y}}} ] d t \right\rangle \\ = \frac {1}{4 T ^ {2}} \int_ {- T} ^ {T} \int_ {- T} ^ {T} r _ {Y} (t _ {1}, t _ {2}) d t _ {1} d t _ {2} \\ \end{array}
$$

由于 $r_{Y}(t_{1}, t_{2}) = r_{Y}(t_{1} - t_{2})$ ，令 $\lambda = t_{1} - t_{2}$ ，在作变换后

$$
\left| \left| \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t - \bar {Y} \right| \right| ^ {2} = \frac {1}{2 T} \int_ {- 2 T} ^ {2 T} \left(1 - \frac {| \lambda |}{T}\right) r _ {Y} (\lambda) d \lambda
$$

由于等式(14.4-12)成立，因此 $\left\|\frac{1}{2T}\int_{-T}^{T}Y(t)dt-\overline{Y}\right\|^{2}$ 当 T 趋于无穷大时趋于零，因此上述论断是正确的。同样，如果 $\left[Y(t+\lambda)Y(t)\right]$ 对固定的 $\lambda$ 也是平稳过程，它的相关函数记为 $b_{\lambda}(u)$ ,那么等式

$$
\begin{array}{l} r (\lambda) = 1. \underset {T \rightarrow \infty} {\mathrm{i.m.}} \frac {1}{2 T} \int_ {- T} ^ {T} [ Y (t + \lambda) - \bar {Y} ] [ Y (t) - \bar {Y} ] d t \\ = 1. \underset {T \rightarrow \infty} {\mathrm{i.m.}} \frac {1}{2 T} \int_ {- T} ^ {T} Y (t + \lambda) Y (t) d t - \overline {{{Y}}} ^ {2} \tag {14.4-13} \\ \end{array}
$$

成立的充分必要条件是

$$
\lim _ {T \rightarrow \infty} \frac {1}{2 T} \int_ {- T} ^ {T} b _ {\lambda} (u) d u = 0 \tag {14.4-14}
$$

这就是各态历经定理。

对某一特定的随机过程当 $r(\lambda)$ 衰减得足够快时, 这些充分必要条件是满足的。根据等式(14.4-11), 再由切比雪夫不等式可知, 对于任意小量 $\varepsilon$ , 概率

$$
p \left\{\left| \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t - \bar {Y} \right| \geqslant \varepsilon \right\}
$$

当 T 趋于无穷大时趋于零。这是因为

$$
p \left\{\left| \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t - \bar {Y} \right| \geqslant \varepsilon \right\} \leqslant \frac {1}{\varepsilon^ {2}} \left\| \frac {1}{2 T} \int_ {- T} ^ {T} Y (t) d t - \bar {Y} \right\|
$$

而后者则在给定的 $\varepsilon$ 和 $T \rightarrow \infty$ 时趋于零，所以上述论断是正确的。同样，当 T 趋于无穷大时

$$
p \left\{\left| \frac {1}{2 T} \int_ {- T} ^ {T} (Y (t + \tau) - \bar {Y}) (Y (t) - \bar {Y}) d t - r _ {Y} (\lambda) \right| \geqslant \varepsilon \right\}\rightarrow 0
$$

在实际问题中，根据上述各态历经定理，当 T 足够大时，可以认为下列两式成立的概率接近于 1

$$
\overline {{{Y}}} \cong \frac {1}{2 T} \int_ {- T} ^ {T} y (\omega , t) d t \tag {14.4-15}
$$

$$
r _ {Y} (\tau) \cong \frac {1}{2 T} \int_ {- T} ^ {T} y (\omega , t + \lambda) y (\omega , t) d t - \overline {{{Y}}} ^ {2} \tag {14.4-16}
$$

请读者注意：上列两式在使用时并不一定完全可靠。因为实际测量时 T 不能趋于无穷大，故上式成立的概率小于 1。其次，即使是概率为零的事件也是可能发生的，所以公式(14.4-15)和(14.4-16)对某些特定的测试结果可能有不成立的危险性，因此，在使用这些公式时要小心。采用公式(14.4-15)和(14.4-16)来计算数学期望和相关函数时，仍然需要多观测几个相同的系统，或者对每一个随机函数多观测几次，然后按系集取平均值，这样可以提高结论的可靠性。

现在来讨论平稳随机函数的一些具体例子。

例 1. 假定 $\{Y_{k}\}$ 是一个具有相同概率分布的互不相关的复值平稳随机序列。 $k=\cdots,-2,-1,0,1,2,\cdots$ ，它的数学期望 $\overline{Y}$ 等于零，相关函数为

$$
r _ {Y} [ \lambda ] = \left\langle Y _ {k + \lambda}, Y _ {k} \right\rangle = \overline {{{Y _ {k + \lambda} Y _ {k} ^ {*}}}} = \left\{ \begin{array}{l l} 0, & \lambda \neq 0 \\ 1, & \lambda = 0 \end{array} \right.
$$

设序列 $\{X_{k}\}$ 是 $\{Y_{k}\}$ 的滑动和，即

$$
X _ {k} = \sum_ {i = 0} ^ {n} a _ {i} Y _ {k - i}, \quad k = \dots , - 2, - 1, 0, 1, 2, \dots
$$

不难检查，对任意 $k,\overline{X}_{k}=0,X$ 的相关函数是

$$
r_{X}[\lambda ] = \overline{X_{k + \lambda}X_{k}^{*}} = \sum_{\substack{0\leqslant i\leqslant n\\ 0\leqslant \lambda -i\leqslant n}}a_{i}a_{\lambda -i}^{*}
$$

由此可见，序列 $\{X_{k}\}$ 也是平稳序列。如果 $n\to \infty$ ， $\sum_{i = 0}^{\infty}|a_i|^2 < \infty$ ，则对任何 $n,X_{k}$ 均为平稳序列。

根据第 14.2 节中所讲的随机变量的几何概念, 此例中平稳序列 $\{Y_{k}\}$ 是在希尔伯特空间 H 中互相直交, 范数等于 1 的单位向量序列, 对某固定的 k, $X_{k}$ 是随机变量希尔伯特空间中某一个 n 维子空间中的一个元素, 在各种可能的 $a_{i}$ 值时的所有 $X_{k}$ 及其均方极限组成了这个 n 维子空间。

例 2. 假定随机过程 $Y(t)=Ye^{i\omega t}$ ，Y 是数学期望为零的复随机变量，那么不难检查 $Y(t)$ 是平稳的。数学期望和自相关函数分别是

$$
\overline {{Y (t)}} = \overline {{Y}} e ^ {i \omega t} = 0
$$

$$
r _ {Y} (\lambda) = \langle Y, Y \rangle e ^ {i \omega (t + \lambda)} e ^ {- i \omega t} = \sigma_ {Y} ^ {2} e ^ {i \omega \lambda}
$$

如果复随机过程 $Y(t)$ 是

$$
Y (t) = Y _ {1} e ^ {i \omega_ {1} t} + Y _ {2} e ^ {i \omega_ {2} t} + \dots + Y _ {n} e ^ {i \omega_ {n} t} = \sum_ {k = 1} ^ {n} Y _ {k} e ^ {i \omega_ {k} t}
$$

其中 $Y_{k}, k=1,2,\cdots,n$ ，是数学期望为零的互不相关的复随机变量， $\omega_{k}, k=1,2,\cdots,n$ 互不相等，那么立刻可以证明 $Y(t)$ 也是平稳的。它的数学期望仍等于零，它的相关函数

$$
r _ {Y} (\lambda) = \sigma_ {Y _ {1}} ^ {2} e ^ {i \omega_ {1} \lambda} + \sigma_ {Y _ {2}} ^ {2} e ^ {i \omega_ {2} \lambda} + \dots + \sigma_ {Y _ {n}} ^ {2} e ^ {i \omega_ {n} \lambda} = \sum_ {k = 1} ^ {n} \sigma_ {Y _ {k}} ^ {2} e ^ {i \omega_ {k} \lambda}
$$

当 $n \to \infty$ ，要级数 $r_Y(\lambda)$ 收敛，必须使 $\sum_{k=1}^{\infty} \overline{|Y_k|^2} = \sum_{k=1}^{\infty} \sigma_{Y_k}^2 < \infty$ ，这时 $\sum_{k=1}^{\infty} Y_k e^{i\omega_k t}$ 也收敛于 $Y(t), Y(t)$ 的数学期望为零，自相关函数为

$$
r _ {Y} (\lambda) = \sum_ {k = 1} ^ {\infty} \sigma_ {Y _ {k}} ^ {2} e ^ {i \omega_ {k} \lambda}
$$

这种平稳随机过程称为具有纯离散谱点的过程, $\omega_{1},\omega_{2},\cdots$ 的总体称为平稳过程的点谱系。

例 3. 假定实随机过程是

$$
Y (t) = X \cos \omega t + Z \sin \omega t
$$

其中 X 和 Z 都是数学期望为零的实随机变量, 如果 $\sigma_{X}^{2} = \sigma_{Z}^{2} = b$ , 而且 $\langle X, Z \rangle = 0$ , 则 $Y(t)$ 是平稳的, 这时相关函数

$$
r _ {Y} (\lambda) = b \cos \omega \lambda
$$

同样的，设实随机过程是

$$
Y (t) = \sum_ {k = 1} ^ {n} \left(X _ {k} \cos \omega t + Z _ {k} \sin \omega t\right)
$$

其中 $X_{k}, Z_{k}, k=1,2,\cdots,n$ ，都是数学期望为零的实随机变量，如果要 $Y(t)$ 是平稳的，则必须有

$$
\langle X _ {i}, Z _ {j} \rangle = 0, \quad i, j = 1, 2, \dots , n
$$

$$
\langle X _ {i}, X _ {j} \rangle = \langle Z _ {i}, Z _ {j} \rangle = \left\{ \begin{array}{l l} 0, & i \neq j \\ b _ {i}, & i = j \end{array} , \quad i, j = 1, 2, \dots , n \right.
$$

这时 $Y(t)$ 的相关函数为

$$
r _ {Y} (\lambda) = \sum_ {k = 1} ^ {n} b _ {k} \cos \omega_ {k} \lambda
$$

当 $n \to \infty$ 时，若 $\sum_{k=1}^{\infty} b_k < \infty$ ，则 $\sum_{k=1}^{\infty} b_k \cos \omega_k \lambda$ 收敛，且级数

$$
\sum_ {k = 1} ^ {\infty} \left(X _ {k} \cos \omega_ {k} t + Z _ {k} \sin \omega_ {k} t\right)
$$

也均方收敛于 $Y(t)$ ，后者的相关函数为

$$
r _ {Y} (\lambda) = \sum_ {k = 1} ^ {\infty} b _ {k} \cos \omega_ {k} \lambda
$$

#### 14.5 平稳随机函数的谱分解

首先让我们回忆一下普通函数的谱分解。设有一普通函数 $f(t)$ ，它定义于区间 $[- \theta, \theta]$ 上。从数学分析中我们知道，如果 $f(t)$ 在此区间内平方可积，那么它可以展成傅里叶级数

$$
f (t) = \sum_ {k = - \infty} ^ {\infty} a _ {k} e ^ {i \omega_ {k} t}, \quad - \theta \leqslant t \leqslant \theta \tag {14.5-1}
$$

其中 $\omega_{k}=k\pi/\theta,k=0,\pm1,\pm2,\cdots$ 。 $a_{k}$ 称为傅里叶系数，它由下式决定

$$
a _ {k} = \frac {1}{2 \theta} \int_ {- \theta} ^ {\theta} f (t) e ^ {- i \omega_ {k} t} a t, \quad k = 0, \pm 1, \pm 2, \dots \tag {14.5-2}
$$

式(14.5-1)右边的级数是周期函数，周期为 $2\theta$ ,它只在 $[- \theta, \theta]$ 区间上均方收敛于 $f(t)$ ,即

$$
\lim _ {n \rightarrow \infty} \int_ {- 0} ^ {0} | f (t) - \sum_ {k = - n} ^ {n} a _ {k} e ^ {i \omega_ {k} t} | ^ {2} d t = 0 \tag {14.5-3}
$$

在 $[-\theta,\theta]$ 区间外级数与 $f(t)$ 可能截然不同或毫无意义。如果把 $f(t)$ 看作为函数空间( $L_{2}$ 空间）的向量，并用 $\|f(t)\|$ 表示此向量的范数，那么就有派雪伐尔(Parseval)等式

$$
\| f (t) \| = \int_ {- \theta} ^ {\theta} | f (t) | ^ {2} d t = 2 \theta \sum_ {k = - \infty} ^ {\infty} | a _ {k} | ^ {2} \tag {14.5-4}
$$

这意味着下列三角函数序列

$$
\frac {1}{\sqrt {2 \theta}}, \frac {1}{\sqrt {2 \theta}} e ^ {i \frac {\pi}{\theta} t}, \frac {1}{\sqrt {2 \theta}} e ^ {i \frac {2 \pi}{\theta} t}, \dots
$$

构成函数空间的规范直交基底，它们的范数等于 1,并互相正交

$$
\frac {1}{2 \theta} \int_ {- \theta} ^ {\theta} e ^ {i \frac {k \pi}{\theta} t} e ^ {- i \frac {l \pi}{\theta} t} d t = \left\{ \begin{array}{l l} 0, & k \neq l \\ 1, & k = l \end{array} \right. \tag {14.5-5}
$$

如果将 $|a_k|$ 画在图内，便得到函数 $f(t)$ 的谱密度图，如图 14.5-1(a)。在图 14.5-1(b)中竖轴画出的是 $|a_k|^2$ ，这就是函数 $f(t)$ 的功率谱密度图，此时 $|a_k|^2$ 表示谐波 $\vec{e}^{i\omega_k t}$ 所载负的信号功率。因此式(14.5-1)可称为函数 $f(t)$ 的谱分解。

> 此处省略原书 **图 14.5-1 (a) (b)**

如果 $f(t)$ 给定在全部实轴 $(-∞,∞)$ 上，那么我们知道，若 $f(t)$ 平方可积，则它可展成傅里叶积分

$$
f (t) = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} s (\omega) d \omega \tag {14.5-6}
$$

等式右边积分均方收敛于 $f(t)$ ，即

$$
\lim _ {a \rightarrow \infty} \int_ {- \infty} ^ {\infty} \left| f (t) - \int_ {- a} ^ {a} e ^ {i \omega t} s (\omega) d \omega \right| ^ {2} d t = 0 \tag {14.5-7}
$$

$s(\omega)$ 称为谱密度函数，把它与频率特性 $F(i\omega)$ 比较可以看出, $F(i\omega)$ 是 $s(\omega)$ 的 $2\pi$ 倍。这时

$$
s (\omega) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} f (t) e ^ {- i \omega t} d t \tag {14.5-8}
$$

和前面一样，等式(14.5-8)的右边均方收敛于 $s(\omega)$ , 即

$$
\lim _ {a \rightarrow \infty} \int_ {- \infty} ^ {\infty} \left| s (\omega) - \frac {1}{2 \pi} \int_ {- a} ^ {a} e ^ {- i \omega t} f (t) d t \right| ^ {2} d \omega = 0 \tag {14.5-9}
$$

对函数空间( $L_{2}$ 空间）中向量 $f(t)$ 的范数有下列“功率”等式

$$
\int_ {- \infty} ^ {\infty} | f (t) | ^ {2} d t = 2 \pi \int_ {- \infty} ^ {\infty} | s (\omega) | ^ {2} d \omega \tag {14.5-10}
$$

我们把 $s(\omega)$ 的积分

$$
S (\omega) = \int_ {- \infty} ^ {\omega} s (\omega) d \omega \tag {14.5-11}
$$

称为 $f(t)$ 的谱函数。

由于这种分解在技术上用处很大，例如可以根据谱密度函数来判断信号的变化速度，并估计各种频率的谐波通过线性系统所发生的变化。自然会产生这样的问题：一个随机函数能否进行谱分解?如果能够找到谱函数的话，那么人们可以从某种意义上判断这个随机函数主要集中于高频谐波部分或是低频谐波部分。幸运的是，答案是肯定的。平稳随机函数和普通函数有类似的特性，可以分解成谐波，即可以进行谱分解。平稳随机函数的谱分解给控制系统的分析和综合提供了一个十分清晰和严整的全套理论和处理方法。在没有开始讨论以前我们先把结论写出。设 $Y_{n}, n=0, \pm1, \pm2, \cdots$ 是一个数学期望为零的平稳随机序列，而且方差有界，那么它可以分解成傅里叶-司蒂吉斯(Stieltjes)积分

$$
Y _ {n} = \int_ {- \pi} ^ {\pi} e ^ {i \omega n} d Z (\omega) \tag {14.5-12}
$$

式中 $Z(\omega)$ 为某一个随机谱函数, 它的特性以后再仔细研究。

若平稳随机过程 $Y(t)$ 定义在全部时间轴 $(-∞,∞)$ 上，而且数学期望为零，方差有界，则它可以按谱函数进行分解

$$
Y (t) = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} d Z (\omega) \tag {14.5-13}
$$

式中 $Z(\omega)$ 为随机谱函数。谱展式(14.5-12)与(14.5-13)的右端随机积分都是在均方意义上收敛于 $Y_{n}$ 或 $Y(t)$ 的。

我们先来研究随机序列的谱分解。设 $\{Y_{n}\}$ 是某一个数学期望为零，方差有界的平稳随机序列，根据第 14.2 节的讨论，对于每一个固定的 n 可以把 $Y_{n}$ 看成为希尔伯特空间 H 内的一个向量，而当 n 变化时 $Y_{n}$ 构成一个向量序列 $\cdots,Y_{-1},Y_{0},Y_{1},\cdots$ 。由于该序列的平稳性可知两个向量的内积 $\langle Y_{n},Y_{n-k}\rangle=r_{Y}[k]$ 只与 k 有关而不依赖于 n。如果用 U 表示移位算子

$$
U Y _ {n} = Y _ {n + 1} \tag {14.5-14}
$$

那么有

$$
\langle U Y _ {n}, U Y _ {n - k} \rangle = \left\langle Y _ {n + 1}, Y _ {n + 1 - k} \right\rangle = r _ {Y} [ k ] = \left\langle Y _ {n}, Y _ {n - k} \right\rangle \tag {14.5-15}
$$

同样

$$
\langle U Y _ {n}, U Y _ {n - k} \rangle = \langle Y _ {n}, U ^ {*} U Y _ {n - k} \rangle \tag {14.5-16}
$$

式中 $U^{*}$ 是 U 的伴随算子。由式(14.5-15)和(14.5-16)可知

$$
U ^ {*} U = I \tag {14.5-17}
$$

I 是希尔伯特空间 H 中的单位算子。

上式告诉我们 $U^{*}=U^{-1}$ 。对于每一个平稳随机序列都存在一个保范算子 U 使

$$
Y _ {n} = U ^ {n} Y _ {0} \tag {14.5-18}
$$

而且这个保范算子 U 可以扩充作用至希尔伯特空间的子空间 $H_{Y}$ ，即由随机序列 $\{Y_{n}\}$ 组成的线性闭子空间。由泛函分析得知，在希尔伯特空间 $H_{Y}$ 中的保范算子（酉算子）可以展成 $^{[5]}$

$$
U = \int_ {- \pi} ^ {\pi} e ^ {i \omega} d E _ {\omega} \tag {14.5-19}
$$

上式内 $E_{\omega}$ 为由某一个自伴算子 A 派生的投影算子，下角注 $\omega$ 表示投影算子将整个子空间 $H_{Y}$ 的所有向量投影到自伴算子 A 在区间 $(- \pi, \omega]$ 的一切谱点所确定的特征子空间 $H_{\omega}$ 中去。若 $Y_{0}$ 表示任一数学期望为零，方差有界的随机变量，那么它属于希氏空间 $H_{Y}$ ，向量 $E_{\omega} Y_{0}$ 便属于子空间 $H_{\omega}$ 。投影算子有下列特性：

(1) $E_{\omega}E_{\omega} = E_{\omega}$

(2) 若 $\omega_{1} \leqslant \omega_{2}$ , 则 $\| E_{\omega_1} Y_0 \| \leqslant \| E_{\omega_2} Y_0 \|$ 。

(3) $\| E_{-\pi}Y_0\| = 0,\| E_\pi Y_0\| = \| Y_0\| = \sigma_Y$

（4）由于相应于两个互不相交区间内诸谱点对应的特征子空间内的向量互相正交，若令 $E_{\Delta \omega} = E_{\omega +\Delta \omega} - E_{\omega}$ ，而 $\Delta \omega_{1}$ 与 $\Delta \omega_{2}$ 互不相交，则必有

$$
\left\| \boldsymbol {E} _ {\Delta \omega_ {1}} \boldsymbol {E} _ {\Delta \omega_ {2}} \boldsymbol {Y} _ {0} \right\| = 0
$$

利用投影算子的特性, 当 $\Delta\omega=\Delta\omega$ 时有

$$
\parallel E _ {\Delta \omega_ {1}} E _ {\Delta \omega_ {2}} Y _ {0} \parallel = \parallel E _ {\Delta \omega_ {1}} Y _ {0} \parallel
$$

根据 $E_{\omega}$ 的上述特性, 等式(14.5-19)也可以改写为

$$
U = \int_ {- \pi} ^ {\pi} e ^ {i \omega} E _ {d \omega} \tag {14.5-20}
$$

进一步不难推得，算子 U 的整数次方幂可展成

$$
U ^ {n} = \int_ {- \pi} ^ {\pi} e ^ {i \omega n} d E _ {\omega} \tag {14.5-21}
$$

等式(14.5-19)和(14.5-21)的实际意义是，对任意两个建立在同一概率场上的数学期望为零，方差有界的随机变量，下列关系式总成立

$$
\langle U X, Y \rangle = \int_ {- \pi} ^ {\pi} e ^ {i \omega} d \langle E _ {\omega} X, Y \rangle
$$

$$
\langle U ^ {n} X, Y \rangle = \int_ {- \pi} ^ {\pi} e ^ {i \omega n} d \langle E _ {\omega} X, Y \rangle , \quad n = 0, \pm 1, \pm 2, \dots
$$

利用式(14.5-21)立即可得到平稳随机序列的谱展式

$$
Y _ {n} = U ^ {n} Y _ {0} = \int_ {- \pi} ^ {\pi} e ^ {i n \omega} d E _ {\omega} Y _ {0} = \int_ {- \pi} ^ {\pi} e ^ {i n \omega} d Z (\omega)
$$

式中 $Z(\omega)=E_{\omega}Y_{0}$ 是随机函数。由投影算子特性可推出随机谱函数的特性：

(1) $\overline{Z(\omega)}=0$ ,这是由于 $\overline{Y}_{0}=0$ 。

(2) $\| Z(-\pi)\| = 0,\| Z(\pi)\| = \| Y_0\| = \sigma_Y$

（3）设 $Z(\Delta\omega_{1})=Z(\omega_{1}+\Delta\omega_{1})-Z(\omega_{1})$ ，区间 $(\omega_{1},\omega_{1}+\Delta\omega_{1}]$ 与 $(\omega_{2},\omega_{2}+\Delta\omega_{2}]$ 互不相交，则有

$$
\overline {{{Z (\Delta \omega_ {1}) Z ^ {*} (\Delta \omega_ {2})}}} = \langle Z (\Delta \omega_ {1}), Z (\Delta \omega_ {2}) \rangle = 0
$$

这是因为

$$
\langle Z (\Delta \omega_ {1}), Z (\Delta \omega_ {2}) \rangle = \langle E _ {\Delta \omega_ {1}} Y _ {0}, E _ {\Delta \omega_ {2}} Y _ {0} \rangle = \langle Y _ {0}, E _ {\Delta \omega_ {1}} ^ {*} E _ {\Delta \omega_ {2}} Y _ {0} \rangle = 0
$$

式中 $E_{\Delta\omega_{1}}^{*}$ 是 $E_{\Delta\omega_{1}}$ 的伴随算子，由于 $E_{\Delta\omega_{1}}$ 是由自伴算子派生出来的投影算子，所以 $E_{\Delta\omega_{1}}$ 也是自伴的， $E_{\Delta\omega_{1}}^{*}=E_{\Delta\omega_{1}}$ 。再由 $E_{\omega}$ 的特性(4)可推知上式成立。

平稳随机序列的相关函数为

$$
r _ {Y} [ k ] = \left\langle Y _ {n + k}, Y _ {n} \right\rangle = \left\langle U ^ {n + k} Y _ {0}, U ^ {n} Y _ {0} \right\rangle
$$

根据序列的谱展式可得到

$$
r _ {Y} [ k ] = \int_ {- \pi} ^ {\pi} e ^ {i \omega k} d \langle E _ {\omega} Y _ {0}, Y _ {0} \rangle = \int_ {- \pi} ^ {\pi} e ^ {i k \omega} d F _ {Y} (\omega) \tag {14.5-22}
$$

上式内 $F_{Y}(\omega)=\langle E_{\omega}Y_{0},Y_{0}\rangle$ 称为平稳随机序列的谱函数（它是非随机的)，它是非降有界函数，因为

$$
\langle E _ {\omega} Y _ {0}, Y _ {0} \rangle = \langle E _ {\omega} Y _ {0}, E _ {\omega} Y _ {0} \rangle = \| E _ {\omega} Y _ {0} \| ^ {2} = \| Z (\omega) \| ^ {2}
$$

所以

$$
F (- \pi) = 0, \quad F (\pi) = \| Y _ {0} \| ^ {2} = \sigma_ {Y} ^ {2}
$$

当 $F(\omega)$ 为可微函数时， $dF(\omega) / d\omega = f(\omega)$ 称为平稳随机序列的谱密度。于是式

(14.5-22)可写为

$$
r _ {Y} [ k ] = \int_ {- \pi} ^ {\pi} e ^ {i k \omega} f _ {Y} (\omega) d \omega \tag {14.5-23}
$$

当 $F(\omega)$ 为不可微时，因为 $F(\omega)$ 是有界变差函数，引进 $\delta$ 函数，使式(14.5-23)依然有效。类似地两个平稳相关的平稳随机序列的相关函数也可有

$$
r _ {Y X} [ k ] = \int_ {- \pi} ^ {\pi} e ^ {i k \omega} d F _ {Y X} (\omega) = \int_ {- \pi} ^ {\pi} e ^ {i k \omega} f _ {Y X} (\omega) d \omega
$$

式中 $F_{YX}(\omega)=\langle E_{\omega}Y_{0},X_{0}\rangle=\langle E_{\omega}Y_{0},E_{\omega}X_{0}\rangle$ 。因此我们无论对自相关函数或互相关函数都可写为

$$
r [ k ] = \int_ {- \pi} ^ {\pi} e ^ {i k \omega} f (\omega) d \omega , \quad k = 0, \pm 1, \pm 2, \dots \tag {14.5-24}
$$

如果注意式(14.5-24)的结构便可发现，它与第十章中的离散拉氏反变换公式相类似。读者不难证明

$$
f (\omega) = \frac {1}{2 \pi} \sum_ {k = - \infty} ^ {\infty} r [ k ] e ^ {- i \omega k} \tag {14.5-25}
$$

这样我们就得到了 $r[k]$ 与 $f(\omega)$ 的直接相互转换关系。

对于实过程来说， $r_{Y}[k]$ 是个偶函数，因此 $f(\omega)$ 也是偶函数。为了计算方便我们设

$$
\Phi (\omega) = 2 f (\omega), \quad \omega \geqslant 0 \tag {14.5-26}
$$

展成傅里叶级数后有

$$
\Phi (\omega) = \frac {r [ 0 ]}{\pi} + \frac {2}{\pi} \sum_ {k = 0} ^ {\infty} r [ k ] \cos k \omega \tag {14.5-27}
$$

$$
r [ k ] = \int_ {0} ^ {\pi} \cos \omega k \Phi (\omega) d \omega \tag {14.5-28}
$$

我们再来研究谱展式(14.5-13)。连续的平稳随机过程 $Y(t)$ 是一个参变量为 $t$ 的随机变量簇 $\{Y(t)\}, -\infty < t < \infty$ 。由 $\{Y(t)\}$ 组成的线性闭包，即 $\{Y(t)\}$ 中向量的线性组合及其均方极限的集合，组成希氏空间中的一个子空间 $H_{Y}$ 。我们定义算子 $U(t)$

$$
U (t) Y (\lambda) = Y (t + \lambda) \tag {14.5-29}
$$

很明显算子具有如下性质

$$
U (t + s) = U (t) U (s) = U (s) U (t) \tag {14.5-30}
$$

由于过程是平稳的，所以对于 $\{Y(t)\}$ 中任何 $Y(t_{1})$ 和 $Y(t_{2})$ 和任意的 $\lambda$ ,有

$$
\begin{array}{l} \langle U (\lambda) Y (t _ {1}), U (\lambda) Y (t _ {2}) \rangle = \langle Y (t _ {1} + \lambda), Y (t _ {2} + \lambda) \rangle = r _ {Y} (t _ {1} - t _ {2}) \\ = \langle Y (t _ {1}), Y (t _ {2}) \rangle \tag {14.5-31} \\ \end{array}
$$

所以算子 $U(t)$ 是保范算子（酉算子)，而且 $U^{*}(t)=U^{-1}(t)$ 。可以把保范算子 $U(t)$ 扩充作用至整个子空间 $H_{Y}$ 。可以证明， $\{U(t)\},-\infty<t<\infty$ 是保范算子的单参

数连续群，它有唯一的谱分解式

$$
U (t) = \int_ {- \infty} ^ {\infty} e ^ {i t \omega} d E _ {\omega} \tag {14.5-32}
$$

式内 $E_{\omega}$ 是由某一个自伴算子 A 派生的投影算子，下角注 $\omega$ 表示投影算子将整个子空间 $H_{Y}$ 的向量投影到自伴算子 A 在区间 $(-∞, ω]$ 的一切谱点所确定的特征子空间 $H_{\omega}$ 中去。这样

$$
Y (t) = U (t) Y (0) = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} d E _ {\omega} Y (0) = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} d Z (\omega)
$$

式中 $Z(\omega)$ 为随机谱函数, 它具有前述的相同性质, 差别仅在于此处它定义于 $(-∞,∞)$ 上, 所以它的特性(2)应改为

$$
\| Z (- \infty) \| = 0, \quad \| Z (\infty) \| = \| Y (0) \| = \sigma_ {Y} ^ {2}
$$

根据平稳随机过程的谱分解公式(14.5-13)和投影算子的特性，可以求出相关函数的谱分解公式

$$
\begin{array}{l} r _ {Y} (t - s) = \langle Y (t), Y (s) \rangle = \langle U ^ {t} Y (0), U ^ {s} Y (0) \rangle \\ = \int_ {- \infty} ^ {\infty} e ^ {i (t - s) \omega} d \langle E _ {\omega} Y (0), Y (0) \rangle \\ = \int_ {- \infty} ^ {\infty} e ^ {i (t - s) \omega} d F _ {Y} (\omega) \tag {14.5-33} \\ \end{array}
$$

上式内 $F_{Y}(\omega)=\langle E_{\omega}Y(0),Y(0)\rangle$ 称为随机函数的谱函数，注意， $F_{Y}(\omega)$ 已是非随机的了。由投影算子 $E_{\omega}$ 的特性知道

$$
F _ {Y} (\omega) = \left\langle E _ {\omega} Y (0), Y (0) \right\rangle = \left\langle E _ {\omega} Y (0), E _ {\omega} Y (0) \right\rangle = \| Z (\omega) \| ^ {2}
$$

因此 $F_{Y}(\omega)$ 是非降有界函数, 而且

$$
F _ {Y} (- \infty) = 0, \quad F _ {Y} (\infty) = \| Z (\infty) \| ^ {2} = \sigma_ {Y} ^ {2}
$$

当 $F(\omega)$ 为可微函数时， $f(\omega)=\frac{d}{d\omega}F(\omega)$ 称为谱密度。这时

$$
r _ {Y} (\lambda) = \int_ {- \infty} ^ {\infty} e ^ {i \omega \lambda} f _ {Y} (\omega) d \omega \tag {14.5-34}
$$

如果 $F(\omega)$ 不可微, 当引进 $\sigma$ 函数后式 (14.5-34) 仍然有效。对两个平稳相关的平稳随机过程的互相关函数也有类似的谱分解公式。总的来说, 对平稳随机过程的相关函数, 谱分解公式为

$$
r (\lambda) = \int_ {- \infty} ^ {\infty} e ^ {i \omega \lambda} f (\omega) d \omega \tag {14.5-35}
$$

并且我们可以得到

$$
f (\omega) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {- i \omega \lambda} r (\lambda) d \lambda \tag {14.5-36}
$$

这是因为

$$
\frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {- i \omega \lambda} r (\lambda) d \lambda = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {- i \omega \lambda} d \lambda \int_ {- \infty} ^ {\infty} e ^ {i \sigma \lambda} f (\sigma) d \sigma
$$

$$
\begin{array}{l} = \int_ {- \infty} ^ {\infty} f (\sigma) d \sigma \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {i \lambda (\sigma - \omega)} d \lambda \\ = \int_ {- \infty} ^ {\infty} f (\sigma) \delta (\sigma - \omega) d \sigma = f (\omega) \\ \end{array}
$$

如果 $r(\lambda)$ 在 $-\infty$ 到 $+\infty$ 上绝对可积，那么 $f(\omega)$ 是存在的。如果 $r(\lambda)$ 在 $-\infty$ 到 $+\infty$ 上不是绝对可积的，那么在引进 $\delta$ 函数后 $f(\omega)$ 还是存在的。

当平稳随机过程 $Y(t)$ 是实过程时, 相关函数是偶函数, 这时谱密度 $f(\omega)$ 也是偶函数, 因此只需要研究 $\omega \geqslant 0$ 时的值就可以了。为了计算方便, 我们引进

$$
\Phi (\omega) = 2 f (\omega), \quad \omega \geqslant 0 \tag {14.5-37}
$$

这时有

$$
r (\lambda) = \int_ {0} ^ {\infty} \cos \omega \lambda \Phi (\omega) d \omega , \quad \lambda \geqslant 0 \tag {14.5-38}
$$

$$
\Phi (\omega) = \frac {2}{\pi} \int_ {0} ^ {\infty} \cos \omega \lambda r (\lambda) d \lambda , \quad \omega \geqslant 0 \tag {14.5-39}
$$

方程(14.5-38)和(14.5-39)称为维纳-辛钦(Wiener-Xinchin)关系。如果随机过程的范数的平方代表它所载负的功率

$$
\| Y (t) \| ^ {2} = r _ {Y} (0) = \int_ {0} ^ {\infty} \Phi (\omega) d \omega \tag {14.5-40}
$$

那么 $\Phi(\omega)$ 就代表 $Y(t)$ 在不同频率上所载负的功率密度, 所以常称为功率谱密度。

如果 $F(\omega)$ 有第一类断续，则在谱密度 $f(\omega)$ 里可以包含用 $\delta$ 函数所表示的冲量。当平稳随机过程中包含有角频率为 $\omega_{k}$ 的随机振幅的周期振动分量时，在相关函数 $r(\lambda)$ 里一定包含一个频率为 $\omega_{k}$ 的周期振动分量。根据 $\delta$ 函数的性质

$$
\frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {i \lambda t} d t = \delta (\lambda)
$$

谱密度 $f(\omega)$ 中将包含一个 $(F(\omega_{k+0}) - F(\omega_{k-0}))\delta(\omega - \omega_k)$ 的分量。

现在我们来讨论两个由相关函数计算功率谱密度的实例。

例 1. 如果相关函数是以高斯曲线给定的

$$
r (\lambda) = r (0) e ^ {- \alpha^ {2} \lambda^ {2}}
$$

相应的功率谱密度就是

$$
\Phi (\omega) = \frac {2}{\pi} r (0) \int_ {0} ^ {\infty} \cos \omega \lambda e ^ {- \alpha^ {2} \lambda^ {2}} d \lambda = \Phi (0) e ^ {- (\omega^ {2} / 4 \alpha^ {2})}
$$

其中

$$
\Phi (0) = \frac {1}{\alpha \sqrt {\pi}} r (0)
$$

有趣的事实是: 当保持 $\Phi(0)$ 不变时, 令 $\alpha\rightarrow\infty$ , 这时对于所有有限的 $\lambda$ 来说, 相关函数都趋于零。同时, $r(0)$ 以一种使 $r(\lambda)$ 变为 $\delta$ 函数的方式趋于 $\infty$ 。这也就是说, 不 同时刻的 $Y(t)$ 值是毫不相关的。所以这个随机过程是所有随机过程中“最杂乱无章”的一个。这时，功率谱密度是一个与频率无关的常数，这个最杂乱的随机过程称为白色噪声。常常用白色噪声来描述物理系统中自然发生的随机变化。

严格地说，白色噪声不是宽平稳过程，因为它的方差为无界

$$
\sigma^ {2} = r (0) = \int_ {0} ^ {\infty} \Phi (\omega) d \omega = \int_ {0} ^ {\infty} \Phi (0) d \omega = \infty
$$

但是从真实的物理系统中永远取不出纯粹的白色噪声，因为真实物理系统总有有限的通频带，白色噪声通过此系统后功率谱密度在足够大的频率段以外就趋于零，并且 $\int_0^\infty \Phi (\omega)d\omega$ 有限。 $\int_0^\infty \Phi (\omega)d\omega <  \infty$ 是指信号总的负载功率有限。如果用仪器去测量白色噪声的统计特性，由于仪器总有有限的通频带，所以得到的结果也不是纯粹的白色噪声。其实，白色噪声是一个广义的平稳随机过程[12]，它是中间运算的一个工具，而不代表真正物理量的统计特性。它通常总是以通过某个通频带有限的系统而得到的平稳过程来表示的。如果平稳随机过程的功率谱密度在足够大的一段频率范围内近似于常数，那么可以把它看作为白色噪声。这里所指的“足够大”是与被研究系统的通频带相比较而言。

> 此处省略原书 **图 14.5-2**

例 2. 对于流体的匀速运动中的微小各向同性湍流, 冯·卡门 (Von Kármán) 和霍瓦尔斯 (Howarth) 曾经证明 $^{[15]}$ : 基本的二阶相关函数就是 $r_{1}(\lambda)$ 和 $r_{2}(\lambda)$ , $r_{1}(\lambda)$ 是在同一空间点上平行于平均流动方向的扰动速度分量对于时间间隔 $\lambda$ 的相关函数, $r_{2}(\lambda)$ 是与平均流动方向垂直的扰动速度分量的相应的相关函数 (图 14.5-2)。如果 v 是平均速度, l 是湍流的特性长度, 那么这两个相关函数就可以近 似地表示为

$$
\begin{array}{l} r _ {1} (\lambda) = r _ {1} (0) e ^ {- \lambda v / l}, \quad \lambda \geqslant 0 \\ r _ {2} (\lambda) = r _ {2} (0) e ^ {- \lambda v / l} \left[ 1 - \frac {1}{2} \frac {\lambda v}{l} \right], \quad \lambda \geqslant 0 \\ \end{array}
$$

根据方程(14.5-39)，平行于平均流动方向的扰动速度分量的功率谱密度 $\Phi_{1}(\omega)$ 和垂直于这个方向的扰动速度分量的功率谱密度 $\Phi_{2}(\omega)$ 就是

$$
\begin{array}{l} \Phi_ {1} (\omega) = \Phi_ {1} (0) \frac {1}{1 + (\omega l / v) ^ {2}}, \quad \omega \geqslant 0 \\ \Phi_ {2} (\omega) = \Phi_ {2} (0) \frac {1 + 3 (\omega l / v) ^ {2}}{\left[ 1 + (\omega l / v) ^ {2} \right] ^ {2}}, \quad \omega \geqslant 0 \\ \end{array}
$$

这里的 $\Phi_{1}(0)$ 和 $\Phi_{2}(0)$ 是相应的功率谱密度在 $\omega=0$ 处的值。 $\Phi_{1}(0)$ ， $\Phi_{2}(0)$ 与

$r_{1}(0)$ , $r_{2}(0)$ 的关系是

$$
\Phi_ {1} (0) = \frac {2}{\pi} \frac {l}{v} r _ {1} (0)
$$

$$
\Phi_ {2} (0) = \frac {1}{\pi} \frac {l}{v} r _ {2} (0)
$$

上面所说的是平稳的一维随机函数的谱分解。平稳的向量随机函数是由好几个一维随机函数所组成的，不过要注意，除了各分量本身是平稳随机函数外各分量之间还是平稳相关的。它的功率谱密度与相关函数阵相对应，也是一个矩阵。

#### 14.6 功率谱密度的直接计算

根据相关函数来计算功率谱密度的做法不是绝对必须的。有时候也可以根据随机函数 $Y(t)$ 本身的已知性质把功率谱密度直接计算出来。

我们先来讨论一维平稳随机序列功率谱密度的直接计算。假定 $\{Y_{n}\}$ 是数学期望为零，方差有界的平稳随机序列，那么有限的滑动和

$$
A _ {N} (\omega) = \sum_ {k = - N} ^ {N} Y _ {k} e ^ {- i \omega k} \tag {14.6-1}
$$

也是数学期望为零，方差有界的随机函数, $\omega$ 是参变量。 $A_{N}(\omega)$ 的范数平方是

$$
\left\| A _ {N} (\omega) \right\| ^ {2} = \sum_ {k = - N} ^ {N} \sum_ {l = - N} ^ {N} \overline {{{Y _ {k} Y _ {l} ^ {*}}}} e ^ {- i \omega k} e ^ {i \omega l}
$$

$$
= \sum_ {k = - N} ^ {N} \sum_ {l = - N} ^ {N} r _ {Y} [ k - l ] e ^ {- i \omega (k - l)}
$$

在引进 k-l=n 后，n 就取自 -2N 到 2N 的整数值。对同一个 n，相同的项就有 $2N+1-|n|$ 个。所以有

$$
\left\| A _ {N} (\omega) \right\| ^ {2} = \sum_ {n = - 2 N} ^ {2 N} (2 N + 1 - | n |) r _ {Y} [ n ] e ^ {- i \omega n} \tag {14.6-2}
$$

因此

$$
\lim _ {n \rightarrow \infty} \frac {1}{\pi (2 N + 1)} \| A _ {N} (\omega) \| ^ {2} = \lim _ {N \rightarrow \infty} \frac {1}{\pi} \sum_ {n = - 2 N} ^ {2 N} \left[ 1 - \frac {| n |}{2 N + 1} \right] r _ {Y} [ n ] e ^ {- i \omega n}
$$

$$
= \frac {1}{\pi} \sum_ {n = - \infty} ^ {\infty} r _ {Y} (n) e ^ {- i \omega n} = \Phi_ {Y} (\omega)
$$

这样就可以按下列公式直接求功率谱密度

$$
\Phi_ {Y} (\omega) = \lim _ {N \rightarrow \infty} \frac {1}{\pi (2 N + 1)} \| A _ {N} (\omega) \| ^ {2} \tag {14.6-3}
$$

假定 $Y(t)$ 是一数学期望为零, 方差有界的平稳随机过程, 那么它的积分

$$
A _ {\theta} (\omega) = \int_ {- \theta} ^ {\theta} Y (t) e ^ {- i \omega t} d t \tag {14.6-4}
$$

也是数学期望为零方差有界的随机函数, $\omega$ 为参变量。 $A_{\theta}(\omega)$ 的范数平方为

$$
\begin{array}{l} \left\| A _ {\theta} (\omega) \right\| ^ {2} = \int_ {- 0} ^ {0} \int_ {- \theta} ^ {\theta} \overline {{{Y (t) Y ^ {*} \left(t ^ {\prime}\right)}}} e ^ {- i \omega t} e ^ {i \omega t ^ {\prime}} d t d t ^ {\prime} \\ = \int_ {- 0} ^ {\theta} \int_ {- \theta} ^ {\theta} r _ {Y} (t - t ^ {\prime}) e ^ {- i \omega (t - t ^ {\prime})} d t d t ^ {\prime} \\ \end{array}
$$

在变量置换 $\lambda=t-t'$ 后可简化为

$$
\left\| A _ {\theta} (\omega) \right\| ^ {2} = 2 \theta \int_ {- 2 \theta} ^ {2 \theta} \left(1 - \frac {| \lambda |}{2 \theta}\right) r _ {Y} (\lambda) e ^ {- i \omega \lambda} d \lambda \tag {14.6-5}
$$

因此

$$
\begin{array}{l} \lim _ {\theta \rightarrow \infty} \frac {1}{2 \pi \theta} \| A _ {\theta} (\omega) \| ^ {2} = \lim _ {\theta \rightarrow \infty} \frac {1}{\pi} \int_ {- 2 \theta} ^ {2 \theta} \left[ \right. 1 - \frac {| \lambda |}{2 \theta}\left. \right) r _ {Y} (\lambda) e ^ {- i \omega \lambda} d \lambda \\ = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} r _ {Y} (\lambda) e ^ {- i \omega \lambda} d \lambda = \Phi_ {Y} (\omega) \\ \end{array}
$$

这样就可以按下列公式直接求功率谱密度

$$
\Phi_ {Y} (\omega) = \lim _ {\theta \rightarrow \infty} \frac {1}{2 \pi \theta} \| A _ {\theta} (\omega) \| ^ {2} \tag {14.6-6}
$$

我们现在来讨论几个直接计算平稳随机过程的功率谱密度的例子。

例 1. 平稳随机过程 $Y(t)$ 是一系列形状相同的脉冲，脉冲的频率是一个常数，脉冲的高度是一个数学期望为零，方差有界的随机变量，并具有一定的概率密度分布函数。此外，还假定这一系列的脉冲高度是互不相关的。如果脉冲是矩形的，那么这一系列脉冲就像图 14.6-1 所画的那样。如果一个高度为 1 的脉冲表示式是 $\eta(t)$ ，那么

> 此处省略原书 **图 14.6-1**

其中 T 是两个相邻脉冲之间的时间间隔， $X_{k}$ 是第 k 个脉冲的幅度。设 $\theta = NT$ ，那么

$$
\begin{array}{l} A _ {0} (\omega) = \int_ {- N T} ^ {N T} Y (t) e ^ {- i \omega t} d t = \int_ {- N T} ^ {N T} \sum_ {k} X _ {k} \eta (t - k T) e ^ {- i \omega t} d t \\ = \sum_ {k = - N} ^ {N} X _ {k} e ^ {- i \omega k T} \int_ {- \infty} ^ {\infty} \eta (\xi) e ^ {- i \omega \xi} d \xi \\ \end{array}
$$

$$
= \alpha (\omega) \sum_ {k = - N} ^ {N} X _ {k} e ^ {- i \omega k T}
$$

式中

$$
\alpha (\omega) = \int_ {- \infty} ^ {\infty} \eta (\xi) e ^ {- i \omega \xi} d \xi
$$

如果脉冲是宽度为 $2\varepsilon$ 高度为 1 的矩形脉冲, 则

$$
\alpha (\omega) = \int_ {- \varepsilon} ^ {\varepsilon} e ^ {- i \omega \xi} d \xi = \frac {2 \sin \omega \varepsilon}{\omega}
$$

根据方程(14.6-6)，功率谱密度就是

$$
\begin{array}{l} \Phi (\omega) = \frac {1}{\pi T} | \alpha (\omega) | ^ {2} \lim _ {N \rightarrow \infty} \frac {1}{2 N} \left[ \sum_ {k = - N} ^ {N} \sum_ {l = - N} ^ {N} \overline {{{X _ {k} X _ {l}}}} e ^ {- i \omega (k - l) T} \right] \\ = \frac {1}{\pi T} | \alpha (\omega) | ^ {2} \lim _ {N \rightarrow \infty} \frac {1}{2 N} \left[ \sum_ {k = - N} ^ {N} \sum_ {l = - N} ^ {N} r _ {X} [ k - l ] e ^ {- i \omega (k - l) T} \right] \\ \end{array}
$$

因为这一系列脉冲的高度是互不相关的，所以除了 k=l 外 $r_{X}[k-l]$ 都等于零，当 k=l 时 $r_{X}[k-l]=\sigma_{X}^{2}$ ,所以

$$
\lim _ {N \rightarrow \infty} \frac {1}{2 N} \left[ \sum_ {k = - N} ^ {N} \sum_ {l = - N} ^ {N} r _ {X} [ k - l ] e ^ {- i \omega (k - l) T} \right] = \sigma_ {X} ^ {2}
$$

最后就得到

$$
\Phi (\omega) = \frac {\sigma_ {X} ^ {2}}{\pi T} | \alpha (\omega) | ^ {2}
$$

例 2. 我们来考虑图 14.6-2 所表示的平稳随机过程 $Y(t)$ 。这个过程在时间间隔 T 中的值或是 +1 或是 -1。这里的 T 不是常数，而是一个随机变量。T 的概率密度函数 $w(T)$ 是已知的。不言而喻， $T \geqslant 0$ 。还要假定这一系列时间间隔 T 是互不相关的。我们用 $T_{k} (k=1,2,3,\cdots)$ 来表示第 k 个时间间隔。假设时间间隔的数学期望是 $\overline{T}$

$$
\overline {{{T}}} = \int_ {0} ^ {\infty} T w (T) d T
$$

我们令 $2\theta = N \overline{T}$ ，这样

> 此处省略原书 **图 14.6-2**

$$
A _ {0} (\omega) = \int_ {0} ^ {N T} Y (t) e ^ {- i \omega t} d t = \frac {1}{i \omega} \sum_ {k = 1} ^ {N} (- 1) ^ {k} \left(e ^ {- i \omega t _ {k}} - e ^ {- i \omega t _ {k - 1}}\right)
$$

这里的 $t_{k}$ 表示第 k 个时间间隔的终点。以上的表示式又可以改写为

$$
A _ {0} (\omega) = \left[ \frac {2}{i \omega} \sum_ {k = 1} ^ {N} (- 1) ^ {k} e ^ {- i \omega t _ {k}} \right] - \frac {1}{i \omega} (- 1) ^ {N} e ^ {- i \omega t _ {N}} + \frac {1}{i \omega}
$$

根据方程 $(14.6-6)$ ，再进行一定化简后得到

$$
\Phi (\omega) = \frac {4}{\pi \overline {{T}} \omega^ {2}} \lim _ {N \rightarrow \infty} \frac {1}{N} \sum_ {k = 1} ^ {N} \sum_ {k ^ {\prime} = 1} ^ {N} (- 1) ^ {k + k ^ {\prime}} \overline {{{e ^ {- i \omega (t _ {k} - t _ {k ^ {\prime}})}}}}
$$

我们先考虑 $k > k'$ 的情况，譬如说 $k = k' + m$ ,这时就有

$$
e ^ {- i \omega (t _ {k} - t _ {k} ^ {\prime})} = e ^ {- i \omega T _ {k ^ {\prime} + 1}} e ^ {- i \omega T _ {k ^ {\prime} + 2}} \dots e ^ {- i \omega T _ {k ^ {\prime} + m}}
$$

既然这一系列时间间隔是互不相关的，因此 $T_{k'+1}, T_{k'+2}, \cdots, T_{k'+m}$ 的联合概率密度函数就等于它们各自概率密度函数之积。如果引进 $e^{-iT\omega}$ 的数学期望

$$
\overline {{{e ^ {- i T \omega}}}} = \chi (\omega) = \phi (\omega) + i \psi (\omega) = \int_ {0} ^ {\infty} e ^ {- i \omega T} w (T) d T
$$

$\chi(\omega)$ 是复函数，实部为 $\phi(\omega)$ ,虚部为 $\psi(\omega)$ , $\chi(\omega)$ 又称为 T 的特征函数，那么

$$
\overline {{e ^ {- i \omega (t _ {k} - t _ {k ^ {\prime}})}}} = [ \chi (\omega) ] ^ {m}
$$

在求 $\Phi(\omega)$ 的双重和式中，像 $e^{-i\omega(t_{k}-t_{k^{\prime}})}$ 这样的乘积的个数有 N-m 个，而每一个这样的乘积的符号都是 $(-1)^{m}$ ，所以求极限后就有来源于这些乘积的一项

$$
\lim _ {N \rightarrow \infty} \frac {N - m}{N} [ - \chi (\omega) ] ^ {m}
$$

m 可以是从 1 到 $\infty$ 的所有正整数, 而且从 $\chi(\omega)$ 的定义可知 $|\chi(\omega)| \leqslant 1$ , 因此这样一些项的总和为

$$
\sum_ {m = 1} ^ {\infty} \lim _ {N \rightarrow \infty} \frac {N - m}{N} [ - \chi (\omega) ] ^ {m} = \frac {- \chi (\omega)}{1 + \chi (\omega)} - \lim _ {N \rightarrow \infty} \frac {\chi (\omega)}{N [ 1 + \chi (\omega) ] ^ {2}} = - \frac {\chi (\omega)}{1 + \chi (\omega)}
$$

不难看出，来源于 $k^{\prime}>k$ 的那些项的总和与来源于 $k>k^{\prime}$ 的各项总和刚好是复共轭的。此外，来源于 $k=k^{\prime}$ 各项的总和刚好等于 1。所以最后得出

$$
\Phi (\omega) = \frac {4}{\pi \overline {{T}} \omega^ {2}} \left\{1 - \operatorname{Re} \left[ \frac {\chi (\omega)}{1 + \chi (\omega)} \right] \right\}
$$

这里的 Re[] 就是取[] 里的实数部分。如果 $\chi(\omega)$ 的实数部分和虚数部分分别是 $\phi(\omega)$ 和 $\psi(\omega)$ ，那么

$$
\Phi (\omega) = \frac {4}{\pi \overline {{T}} \omega^ {2}} \frac {1 - \phi^ {2} (\omega) - \psi^ {2} (\omega)}{\left[ 1 + \phi^ {2} (\omega) \right] + \psi^ {2} (\omega)}
$$

如果概率密度函数 $w(T)$ 是泊松(Poisson)分布函数

$$
w (T) = \left\{ \begin{array}{l l} \frac {1}{T} e ^ {- T / T}, & T \geqslant 0 \\ 0, & T <   0 \end{array} \right.
$$

对此特殊分布来说，这样的一个振幅是 1 的随机开关函数的功率谱密度就是

$$
\Phi (\omega) = \frac {\overline {{T}}}{\pi} \frac {1}{1 + (\omega \overline {{T}} / 2) ^ {2}}
$$

因为这个随机过程没有任何有规则的周期性，所以功率谱密度是连续而光滑的。

#### 14.7 随机函数离开平均值大偏差的概率及超过一个固定值的频率

如果随机函数是一个结构中的应力，那么只知道这个应力的平均值是很不够的，因为结构的破坏与应力本身的大小有关系。为了安全起见，我们就需要知道应力超过结构材料的容许工作应力的概率，也就是随机函数 $Y(t)$ 的函数值 Y 的大小超过常数值 K 的概率 $p\{|Y|\geqslant K\}$ , 如果第一概率密度函数 $w_{1}(y)$ 是已知的，那么这个问题的答案就很简单

$$
p \{| Y | \geqslant K \} = \int_ {- \infty} ^ {- K} w _ {1} (y) d y + \int_ {K} ^ {\infty} w _ {1} (y) d y \tag {14.7-1}
$$

但是，在不少工程问题中并不知道概率密度函数，而只知道数学期望 $\overline{Y}$ 和方差 $\sigma_{Y}^{2}$ 。就是在这种情况下，对于离开平均值（即数学期望）的大偏差的概率，我们还是可以给出一个一般的估计的。这个估计就是必耐梅-切比雪夫不等式

$$
p \left\{\mid Y - \bar {Y} \mid \geqslant k \sigma \right\} = p \left\{\left(Y - \bar {Y}\right) ^ {2} \geqslant k ^ {2} \sigma^ {2} \right\} \leqslant \frac {1}{k ^ {2}} \tag {14.1-16}
$$

对于最实际的应用来说，必耐梅-切比雪夫不等式所给的估计还嫌太宽，也就是说，这个不等式所给的上限常常是过高的。如果 $w_{1}(y)$ 只有一个极大值，我们就可以给出一个比较精确的估计。这时 $w_{1}(y)$ 的极大值所在的点 $y_{0}$ 称为众数。这样的分布密度函数称为单众数密度函数（或单峰密度函数)。对于单众数密度函数的情形，大偏差概率的估计是高斯首先作出的。为了证明高斯的不等式，我们来考虑图 14.7-1 所画的函数 $w_{1}(x)$ , $w_{1}(x)$ 在 x>0 的区域内是单调减小的。可以把 $w_{1}(x)$ 看做是许多矩形函数的和, 这些矩形函数都是这样的: 在 $0 \leqslant x \leqslant x_{0}$ 间隔内等于一个常数, 在 $x > x_{0}$ 区域内等于零。我们先来考虑矩形函数 $v(x)$

> 此处省略原书 **图 14.7-1**

如果 $0 \leqslant x \leqslant x_0$ ， $v(x) = 1$

如果 $x > x_{0}$ ， $v(x) = 0$

对于任意一个 $K > x_{0}$

$$
K ^ {2} \int_ {K} ^ {\infty} v (x) d x = 0
$$

但是，如果 $0 < K \leqslant x_{0}$

$$
K ^ {2} \int_ {K} ^ {\infty} v (x) d x = K ^ {2} \left(x _ {0} - K\right)
$$

不难证明，对于这个范围内的 K 来说 $K^{2}(x_{0}-K)$ 的极大值是 $\frac{4}{27}x_{0}^{3}$ 。所以下列关系式对所有 K 值都是成立的

$$
K ^ {2} \int_ {K} ^ {\infty} v (x) d x \leqslant \frac {4}{9} \int_ {0} ^ {\infty} x ^ {2} v (x) d x
$$

用叠加的方法就可以得出

$$
K ^ {2} \int_ {K} ^ {\infty} w _ {1} (x) d x \leqslant \frac {4}{9} \int_ {0} ^ {\infty} x ^ {2} w _ {1} (x) d x
$$

现在，来考虑一个横坐标是 $x=y-y_{0}$ 的单众数密度函数 $w_{1}(x)$ 。这里的 $y_{0}$ 是众数。这时

$$
K ^ {2} \int_ {K} ^ {\infty} w _ {1} (x) d x \leqslant \frac {4}{9} \int_ {0} ^ {\infty} x ^ {2} w _ {1} (x) d x
$$

而且

$$
K ^ {2} \int_ {- \infty} ^ {K} w _ {1} (x) d x \leqslant \frac {4}{9} \int_ {- \infty} ^ {0} x ^ {2} w _ {1} (x) d x
$$

把这两个不等式加起来，就得到

$$
K ^ {2} p \{\mid Y - y _ {0} \mid \geqslant K \} \leqslant \frac {4}{9} v ^ {2}
$$

这里的 v 是离开众数的偏差的平均值

$$
v ^ {2} = \overline {{{(Y - y _ {0}) ^ {2}}}} = \int_ {- \infty} ^ {\infty} (y - y _ {0}) ^ {2} w _ {1} (y) d y \tag {14.7-2}
$$

设 $K = k\nu$ ，我们就得到高斯不等式

$$
p \left\{\mid Y - y _ {0} \mid \geqslant k v \right\} \leqslant \frac {4}{9 k ^ {2}} \tag {14.7-3}
$$

如果密度函数 $w_{1}(y)$ 对于 $y = y_0$ 是对称的，即 $w_{1}(y_{0} + x) = w_{1}(y_{0} - x)$ ，那么就有 $y_0 = \overline{Y}, v = \sigma_Y$ 。因而方程(14.7-3)就化为

$$
p \{| Y - \overline {{Y}} | \geqslant k \sigma_ {Y} \} \leqslant \frac {4}{9 k ^ {2}} \tag {14.7-4}
$$

所以方程(14.7-4)所表示的概率估计比方程(14.1-16)的估计更精确。

在很多情况下，我们可以认为 $w_{1}(y)$ 是高斯分布概率密度函数（至少也可以近似地这样假设)。这时，利用误差函数 $f(x)=\frac{2}{\sqrt{\pi}}\int_{0}^{x}e^{-t^{2}}dt$ 的渐近展开式，不难直接算出

$$
p \left\{\mid Y - \overline {{{Y}}} \mid \geqslant k \sigma_ {Y} \right\} \cong \frac {\sigma^ {- \frac {1}{2} h ^ {2}}}{k \sqrt {2 \pi}}, \quad k \gg 1 \tag {14.7-5}
$$

这个概率的数值很小。例如在 k=3 时，这个概率只有 0.003。可是，如果利用方程(14.1-16)只能知道这个概率比 0.1111 小。即使用方程(14.7-4)来估计，也只知道这个概率小于 0.0493。这三种估计结果所以有这样悬殊的差别，当然是因为这些估计方法所依据的资料在确切程度上有很大差别的缘故。所根据的假设越一般化，所能得出的估计结果就越不精确。

如果所考虑的平稳随机函数是结构中的应力，并且假设需要根据应力超过某一个固定值（也就是材料的疲劳应力）的重复次数来进行设计，那么就必须知道随机函数在单位时间内超过固定值 $y = \xi$ 的可能次数。这个次数显然是随机函数在单位时间内经过 $\xi$ 值的可能次数的一半。用 $N_0(\xi)$ 表示上述的经过 $\xi$ 值的次数。这个数最先是由瑞斯(Rice)计算出来的[18]，下面我们介绍他的计算方法。

设 $Y(t)$ 是可微的随机过程， $w(y, \dot{y}) dy dy$ 是在同一时刻随机函数 $Y(t)$ 的值在 $y$ 和 $dy$ 之间，而它对时间导数 $\dot{Y}(t)$ 的值在 $\dot{y}$ 和 $\dot{y} + dy$ 之间的联合概率。这个概率也可以解释为在单位时间内 $Y(t)$ 和 $\dot{Y}(t)$ 同时在上述范围内的时间比率。但是，随机函数经过 $dy$ 所需的时间是 $dy / |\dot{y}|$ 。所以，所需要的经过 $\xi$ 和 $\dot{y}$ 的可能次数就等于 $w_2(\xi, \dot{y}) dy dy$ 被 $dy / |\dot{y}|$ 除得的商 $|\dot{y}| w_2(\xi, \dot{y}) dy$ 。因此，对所有的 $\dot{y}$ 值积分就可以得到次数 $N_0(\xi)$

$$
N _ {0} (\xi) = \int_ {- \infty} ^ {\infty} | \dot {y} | w _ {2} (\xi , \dot {y}) d \dot {y} \tag {14.7-6}
$$

但是方程(14.4-7)表明，只要平稳随机函数是可微的, $Y(t)$ 和 $\dot{Y}(t)$ 就是互不相关的。如果 $Y(t)$ 和 $\dot{Y}(t)$ 的联合分布是高斯分布，那么 $Y(t)$ 和 $\dot{Y}(t)$ 还是互相独立的, $Y(t)$ 和 $\dot{Y}(t)$ 独自的分布也是高斯分布，于是

$$
w _ {2} (y, \dot {y}) = w _ {1} (y) w _ {1} (\dot {y})
$$

方程(14.7-6)就可以写成

$$
N _ {0} (\xi) = w _ {1} (\xi) \int_ {- \infty} ^ {\infty} | \dot {y} | w _ {1} (\dot {y}) d \dot {y} \tag {14.7-7}
$$

如果 $w_{1}(\dot{y})$ 是对称的，即 $w_{1}(\dot{y}) = w_{1}(-\dot{y})$ ，则

$$
N _ {0} (\xi) = 2 w _ {1} (\xi) \int_ {0} ^ {\infty} \dot {y} w _ {1} (\dot {y}) d \dot {y} \tag {14.7-8}
$$

设 $\dot{Y}$ 的数学期望为零, 方差为 $\sigma_{Y}^{2}$ , Y 的数学期望为 $\overline{Y}$ , 方差为 $\sigma_{Y}^{2}$ , 按照方程 (14.1-17) 和 (14.7-8) 就有

$$
N _ {0} (\xi) = \frac {2 w _ {1} (\xi)}{\sigma_ {\dot {Y}} \sqrt {2 \pi}} \int_ {0} ^ {\infty} \dot {y} \exp \left[ - \frac {\dot {y} ^ {2}}{2 \sigma_ {\dot {Y}} ^ {2}} \right] d \dot {y} = \frac {2 \sigma_ {\dot {Y}} w _ {1} (\xi)}{\sqrt {2 \pi}} \tag {14.7-9}
$$

利用方程(14.4-8)和(14.5-38)，可以由 $Y(t)$ 的功率谱密度算出方差

$$
\sigma_ {Y} ^ {2} = \int_ {0} ^ {\infty} w ^ {2} \Phi_ {Y} (\omega) d \omega \tag {14.7-10}
$$

再根据方程(14.1-17)，(14.5-40)，(14.7-9)和(14.7-10)就得出

$$
\begin{array}{l} N _ {0} (\xi) = \frac {1}{\pi} \frac {\sigma_ {Y}}{\sigma_ {Y}} \exp \left[ - \frac {1}{2} \frac {(\xi - \bar {Y}) ^ {2}}{\sigma_ {Y} ^ {2}} \right] \\ = \frac {1}{\pi} \left[ \frac {\int_ {0} ^ {\infty} \omega^ {2} \Phi_ {Y} (\omega) d \omega}{\int_ {0} ^ {\infty} \Phi_ {Y} (\omega) d \omega} \right] ^ {\frac {1}{2}} \exp \left[ - \frac {1}{2} \frac {(\xi - \overline {{{Y}}}) ^ {2}}{\sigma_ {Y} ^ {2}} \right] \tag {14.7-11} \\ \end{array}
$$

这就是瑞斯给出的公式。 $N_{0}(\xi)/2$ 就是 $Y(t)$ 超过 $\xi$ 值的频率。

#### 14.8 随机函数的线性变换

在第 14.3 节中已经讨论了三种特定的对随机函数的变换。它们都是线性变换，并得到了随机函数的数学期望和相关函数的变换规律。可以看出，这几种线性变换和求数学期望的运算是可以互相交换作用次序的。假定随机函数 $Y(s)$ 是对随机函数 $X(t)$ 进行变换后的结果

$$
Y (s) = A _ {t} X (t) \tag {14.8-1}
$$

Y 和 X 可以有相同的自变量（即 s=t)或不同的自变量（即 $s \neq t$ )。例如控制系统的输出就是对输入进行变换的结果。如果这种变换满足下列两个条件, 就称为线性变换, 我们用 $L_{t}$ 表示线性变换, 它满足:

(1) $L_{t}[X_{1}(t) + X_{2}(t)] = L_{t}X_{1}(t) + L_{t}X_{2}(t)$ 。 (14.8-2)

(2) $L_{t}[cX(t)] = cL_{t}X(t)$ 。 (14.8-3)

其中 $c$ 为任意常数。线性控制系统的输出就是对输入进行线性变换的结果。在控制系统中我们常用到的基本线性变换有：

(1) $L_{t}X(t)=P(d/dt)X(t)$ ，其中 $P(d/dt)$ 是微分算子 d/dt 的多项式。

(2) $L_{t}X(t)=P(U)X(t)$ ，其中 $P(U)$ 是移位算子 U 的多项式。

(3) $L_{t}X(t) = \int_{a}^{b}g(s,t)X(t)dt$ ，其中 $g(s,t)$ 是核函数。

(4) $L_{t}X(t) = \sum_{i = 0}^{\infty}g_{i}(s)X_{i}(t)$ ，其中 $g_{i}(s),i = 0,1,2,\dots$ 是加权函数。

(5) $L_{t}\pmb {X}(t) = \pmb{c}^{\tau}\pmb {X}(t) = \sum_{i = 1}^{n}c_{i}X_{i}(t)$

其中 X 是向量随机函数。 $X_{i}(t)$ 是它的分量；c 是某个常数向量； $c_{i}$ 是它的分量。这些基本线性变换的积也是线性变换。可以证明，对于这些类型的线性变换，只要它们变换后的结果是存在的，那么线性变换和求数学期望这两种运算是 可以交换作用次序的，因此，随机函数的数学期望和相关函数的变换规律是

$$
\overline {{Y (s)}} = \overline {{L _ {t} X (t)}} = L _ {t} \overline {{X (t)}} \tag {14.8-4}
$$

$$
r _ {Y} \left(s _ {1}, s _ {2}\right) = \overline {{{Y \left(s _ {1}\right) Y \left(s _ {2}\right) ^ {*}}}} = \overline {{{L _ {t _ {1}} L _ {t _ {2}} ^ {*} X \left(t _ {1}\right) X \left(t _ {2}\right) ^ {*}}}}
$$

$$
= L _ {t _ {1}} L _ {t _ {2}} ^ {*} \overline {{{X (t _ {1}) X (t _ {2}) ^ {*}}}} = L _ {t _ {1}} L _ {t _ {2}} ^ {*} r _ {X} (t _ {1}, t _ {2}) \tag {14.8-5}
$$

$$
r _ {Y X} \left(s _ {1}, t _ {2}\right) = \overline {{{Y (s _ {1}) X (t _ {2}) ^ {*}}}} = \overline {{{L _ {t _ {1}} X (t _ {1}) X (t _ {2}) ^ {*}}}}
$$

$$
= L _ {t _ {1}} \overline {{X (t _ {1}) X (t _ {2}) ^ {*}}} = L _ {t _ {1}} r _ {X} (t _ {1}, t _ {2}) \tag {14.8-6}
$$

这里 $L_{t}^{*}$ 表示 $L_{t}$ 的共轭线性变换。如果线性变换是实的，那么 $L_{t}^{*}=L_{t}$ 。

如果随机函数 $X(t)$ 是高斯分布的，那么可以证明，通过线性变换后得到的 $Y(s)=L_{t}X(t)$ 也是高斯分布的 $^{[26]}$ 。如果 $Y(s)$ 是 $X(t)$ 的线性变换

$$
Y (s) = \int_ {a} ^ {b} g (s, t) X (t) d t
$$

即使 $X(t)$ 不是高斯分布的，但如果 $X(t_{1})$ 和 $X(t_{2})$ 不相关的最大区间 $\left|t_{1} - t_{2}\right|$ 比 $|b - a|$ 小得多，那么 $Y(s)$ 也是近于高斯分布的。不相关的最大区间 $\left|t_1 - t_2\right|$ 小也就意味着 $X(t)$ 的相关函数很快地衰减为零，因此 $X(t)$ 的功率谱密度相应地就比较宽。 $\mid b - a\mid$ 区间大也就意味着 $g(s,t)$ 实际不为零的时间长，线性变换的系统的惯性较大。因此当一个不是高斯分布的功率谱密度较宽的随机过程 $X(t)$ 通过一个惯性较大（即通带较窄）的线性系统后，输出 $Y(s)$ 就近于高斯分布的。

假定 $X(t)$ 是可微的平稳随机过程, 它的谱分解式为

$$
X (t) = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} d Z (\omega) \tag {14.5-13}
$$

相关函数的谱分解式为

$$
r _ {X} (\lambda) = \int_ {- \infty} ^ {\infty} e ^ {i \omega \lambda} f _ {X} (\omega) d \omega \tag {14.5-35}
$$

那么可以证明它的导数 $Y(t)=\frac{d}{dt}X(t)$ 的谱分解式为

$$
Y (t) = \int_ {- \infty} ^ {\infty} (i \omega) e ^ {i \omega t} d Z (\omega) \tag {14.8-7}
$$

$Y(t)$ 的自相关函数的谱分解式为

$$
r _ {Y} (\lambda) = \int_ {- \infty} ^ {\infty} | i \omega | ^ {2} e ^ {i \omega \lambda} f _ {X} (\omega) d \omega = \int_ {- \infty} ^ {\infty} \omega^ {2} e ^ {i \omega \lambda} f _ {X} (\omega) d \omega \tag {14.8-8}
$$

而 $Y(t)$ 的自谱密度为

$$
f _ {Y} (\omega) = \omega^ {2} f _ {X} (\omega) \tag {14.8-9}
$$

同样， $Y(t)$ 与 $X(t)$ 的互谱密度为

$$
f _ {Y X} (\omega) = (i \omega) f _ {X} (\omega) \tag {14.8-10}
$$

把此结果更推广一步。如果

$$
Y (t) = P \left[ \frac {d}{d t} \right] X (t) \tag {14.8-11}
$$

$P(d/dt)$ 是微分算子 d/dt 的多项式, 只要 $Y(t)$ 存在, 那么 $Y(t)$ 的谱分解式就为

$$
Y (t) = \int_ {- \infty} ^ {\infty} P (i \omega) e ^ {i \omega t} d Z (\omega) \tag {14.8-12}
$$

$Y(t)$ 的自谱密度为

$$
f _ {Y} (\omega) = \left| P (i \omega) \right| ^ {2} f _ {X} (\omega) \tag {14.8-13}
$$

$Y(t)$ 与 $X(t)$ 的互谱密度

$$
f _ {Y X} (\omega) = P (i \omega) f _ {X} (\omega) \tag {14.8-14}
$$

如果平稳随机序列 $\{X_{n}\}$ 和它的相关函数 $r_X[n]$ 的谱分解式分别是

$$
X _ {n} = \int_ {- \pi} ^ {\pi} e ^ {i \omega n} d Z (\omega) \tag {14.5-12}
$$

$$
r _ {X} [ n ] = \int_ {- \pi} ^ {\pi} e ^ {i \omega n} f _ {X} (\omega) d \omega \tag {14.5-24}
$$

随机序列 $\{Y_{n}\}$ 是 $\{X_{n}\}$ 的线性变换

$$
Y _ {n} = P (U) X _ {n} \tag {14.8-15}
$$

其中 $P(U)$ 是移位算子 U 的多项式, 那么 $Y_{n}$ 的谱分解是

$$
Y _ {n} = \int_ {- \pi} ^ {\pi} P (e ^ {i \omega}) e ^ {i \omega n} d Z (\omega) \tag {14.8-16}
$$

自谱密度与 $Y_{n}$ ， $X_{n}$ 的互谱密度分别为

$$
f _ {Y} (\omega) = \left| P \left(e ^ {i \omega}\right) \right| ^ {2} f _ {X} (\omega) \tag {14.8-17}
$$

$$
f _ {Y X} (\omega) = P \left(e ^ {i \omega}\right) f _ {X} (\omega) \tag {14.8-18}
$$

#### 14.9 线性常系数系统对于平稳随机输入的反应

现在我们开始来讨论这一章的第二部分，也就是各类控制系统在随机作用下系统的分析问题。我们先从简单的问题开始。如果对一个线性常系数控制系统加上一个平稳随机输入，那么我们希望知道的是输出的数学期望，相关函数或方差，可能还需要估计离开平均值的大偏差的概率以及超过某个固定值的频率等。对于很多的工程问题来说，关于输出量的这些统计特性的知识已经足够了。

假设平稳随机输入 $X(t)$ 的数学期望为 $\overline{X}$ ，相关函数是 $r_{X}(\lambda)$ ，功率谱密度是 $\Phi_{X}(\omega)$ 。再设线性常系数系统只有一个输入和一个输出。表示输出和输入之间的特性关系是传递函数 $F(s)$ 和脉冲响应函数 $h(t)$ 。我们讨论的系统假定都是稳定的，因此 $F(s)$ 的所有极点都在左半 S 平面，即所有极点的实部都是负数。依脉冲响应函数的定义， $h(t)$ 当 t<0 时等于零。对于一个从 $t=-\infty$ 就开始作用的输入作用来说，输出量

$$
y (t) = \int_ {0} ^ {\infty} h (u) x (t - u) d u \tag {14.9-1}
$$

输出量 $y(t)$ 是输入量的线性变换。当输入是平稳随机过程 $X(t)$ 时，输出量 $Y(t)$ 是个随机过程

$$
Y (t) = \int_ {0} ^ {\infty} h (u) X (t - u) d u \tag {14.9-2}
$$

利用随机函数线性变换的特性就能算出输出量的数学期望和相关函数分别是

$$
\overline {{{Y}}} (t) = \overline {{{X}}} \int_ {0} ^ {\infty} h (u) d u = \text { const } \tag {14.9-3}
$$

$$
r _ {Y} (t + \lambda , t) = \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} r _ {X} (\lambda + u - u ^ {\prime}) h (u) h (u ^ {\prime}) d u d u ^ {\prime} = r _ {Y} (\lambda) \tag {14.9-4}
$$

由于 $\overline{Y(t)}$ 是常数, $r_{Y}(t+\lambda,t)$ 只与 $\lambda$ 有关，所以 $Y(t)$ 也是平稳的。同时输出与输入之间的互相关函数为

$$
r _ {Y X} (t + \lambda , t) = \int_ {0} ^ {\infty} r _ {X} (\lambda - u) h (u) d u = r _ {Y X} (\lambda) \tag {14.9-5}
$$

所以输出与输入是平稳相关的。根据相关函数与功率谱密度之间的关系式(14.5-36)和(14.5-37)我们就得到

$$
\begin{array}{l} \Phi_ {Y} (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} r _ {Y} (\lambda) e ^ {- i \omega \pi} d \lambda \\ = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} r _ {X} (\lambda - u + u ^ {\prime}) e ^ {- i \omega (\pi - u + u ^ {\prime})} h (u ^ {\prime}) e ^ {i \omega u ^ {\prime}} h (u) e ^ {- i \omega u} d u d u ^ {\prime} d \lambda \\ \Phi_ {Y X} (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} r _ {Y X} (\lambda) e ^ {- i \omega \lambda} d \lambda \\ = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} \int_ {0} ^ {\infty} r _ {X} (\lambda - u) e ^ {- i \omega (\lambda - u)} h (u) e ^ {- i \omega u} d u d \lambda \\ \end{array}
$$

$$
\begin{array}{l} \Phi_ {Y X} (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} r _ {Y X} (\lambda) e ^ {- i \omega \lambda} d \lambda \\ = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} \int_ {0} ^ {\infty} r _ {X} (\lambda - u) e ^ {- i \omega (\lambda - u)} h (u) e ^ {- i \omega u} d u d \lambda \\ \end{array}
$$

再根据传递函数与脉冲过渡函数之间的关系

$$
F (i \omega) = \int_ {0} ^ {\infty} h (u) e ^ {- i \omega u} d u
$$

就得到

$$
\Phi_ {Y} (\omega) = \Phi_ {X} (\omega) F (i \omega) F (- i \omega) = | F (i \omega) | ^ {2} \Phi_ {X} (\omega) \tag {14.9-6}
$$

$$
\Phi_ {Y X} (\omega) = \Phi_ {X} (\omega) F (i \omega) \tag {14.9-7}
$$

在这里我们用到了 $F(i\omega)$ 是 $F(-i\omega)$ 的复共轭数的事实。根据方程(14.9-6)就可以由输入的功率谱密度和线性常系数系统的频率特性算出输出的功率谱密度。甚至于当频率特性只是用曲线或数字表格来表示的情况下， $\Phi_{Y}(\omega)$ 也还是不难计算出来的。从这里我们也可以看到，在线性常系数系统中传递函数和频率特性的概念是很有用的。根据等式(14.9-3)可以由输入的数学期望求出输出的数学期望。可以看出式(14.9-3)中的积分 $\int_0^\infty h(u)du$ 实际上就是传递函数 $F(s)$ 在 $s = 0$ 时的值，也就是稳态放大系数 $K$ ，所以

$$
\overline {{{Y}}} = F (0) \overline {{{X}}} = K X \tag {14.9-8}
$$

在一般的情况下，传递函数 $F(s)$ 是 s 的有理分式，而且分子的幂次比分母的幂次低，因此当 $\omega\to\infty$ 时， $F(i\omega)\to0$ 。这样，当 $\omega\to\infty$ 时输出功率谱密度 $\Phi_{Y}(\omega)$ 比输入功率谱密度 $\Phi_{X}(\omega)$ 更快地趋于零。这一事实对白色噪声的输入量仍然有效。它表明随机输出高频分量的强度比随机输入高频分量的强度要小得多。所以一般线性常系数系统有一种使输出比输入更“光滑”的“过滤”作用。

假定线性常系数控制系统有几个输入（或控制量）和几个输出量（或受控量)，则系统的特性可以用向量形式的微分方程来描述

$$
\frac {d}{d t} \mathbf {y} = A \mathbf {y} + B \mathbf {x} \tag {14.9-9}
$$

式中 x 是 m 维向量, 表示系统的输入作用; y 是 n 维向量, 表示系统的状态; 它的某几个分量可能是输出量; A 是 $n \times n$ 阶常方阵, B 是 $n \times m$ 阶矩阵; n 是系统的阶数。假定系统是稳定的, 那么方阵 A 的所有特征值都有负实部。对于从 $t = -\infty$ 就开始作用的输入量来说, 输出量

$$
\mathbf {y} (t) = \int_ {- \infty} ^ {t} \Phi (t - \sigma) B \mathbf {x} (\sigma) d \sigma \tag {14.9-10}
$$

输出量也是输入量的线性变换，其中 $\Phi(t-\sigma)=e^{A(t-\sigma)}$ , 它是方程(14.9-9)的齐次方程的基本解矩阵。 $\Phi(t-\sigma)B$ 是 $n\times m$ 阶矩阵, 它代表输入和系统状态之间的关系, 相当于脉冲响应函数的性质。当输入是 m 个平稳随机过程时, 还假定任意两个之间又是平稳相关的, 那么就相当于输入一个 m 维平稳随机向量函数 $X(t)$ , 这时输出是向量函数 $Y(t)$

$$
\mathbf {Y} (t) = \int_ {- \infty} ^ {t} e ^ {A (t - \sigma)} B \mathbf {X} (\sigma) d \sigma = \int_ {0} ^ {\infty} e ^ {A u} B \mathbf {X} (t - u) d u \tag {14.9-11}
$$

利用随机函数线性变换的特性不难算出 $Y(t)$ 的数学期望和自相关矩阵分别是

$$
\overline {{{\boldsymbol {Y} (t)}}} = \int_ {0} ^ {\infty} e ^ {A u} B d u \overline {{{\boldsymbol {X}}}} \tag {14.9-12}
$$

$$
R _ {Y} (t + \lambda , t) = \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} e ^ {A u _ {1}} B R _ {X} (\lambda - u _ {1} + u _ {2}) B ^ {\tau} e ^ {A ^ {\tau} u _ {2}} d u _ {1} d u _ {2}
$$

$$
= R _ {Y} (\lambda) = \left[ \begin{array}{c c c} r _ {Y _ {1} Y _ {1}} (\lambda) & r _ {Y _ {1} Y _ {2}} (\lambda) \dots r _ {Y _ {1} Y _ {n}} (\lambda) \\ \vdots & \vdots & \vdots \\ r _ {Y _ {n} Y _ {1}} (\lambda) & r _ {Y _ {n} Y _ {2}} (\lambda) \dots r _ {Y _ {n} Y _ {n}} (\lambda) \end{array} \right] \tag {14.9-13}
$$

所以 $Y(t)$ 也是平稳的随机向量函数。同样，输出与输入之间也是平稳相关的，互相关矩阵为

$$
\begin{array}{l} R _ {Y X} (t + \lambda , t) = \int_ {0} ^ {\infty} e ^ {A u} B R _ {X} (\lambda - u) d u \\ = R _ {Y X} (\lambda) = \left[ \begin{array}{c c c} r _ {Y _ {1} X _ {1}} (\lambda) & r _ {Y _ {1} X _ {2}} (\lambda) \dots r _ {Y _ {1} X _ {m}} (\lambda) \\ \vdots & \vdots & \vdots \\ r _ {Y _ {n} X _ {1}} (\lambda) & r _ {Y _ {n} X _ {2}} (\lambda) \dots r _ {Y _ {n} X _ {m}} (\lambda) \end{array} \right] \tag {14.9-14} \\ \end{array}
$$

自相关矩阵 $R_{Y}(\lambda)$ 是 $n \times n$ 阶的，它的元素表示系统状态的自相关函数或互相关函数。互相关矩阵 $R_{YX}(\lambda)$ 是 $n \times m$ 阶的，它的元素是系统的某个状态与某个输入的互相关函数。如果 m 个输入作用互不相关，则 $R_{X}(\lambda)$ 是对角矩阵

$$
R _ {X} (\lambda) = \left[ \begin{array}{c c c c} r _ {X _ {1}} (\lambda) & 0 & \dots & 0 \\ 0 & r _ {X _ {2}} (\lambda) & \dots & 0 \\ \vdots & \vdots & & \vdots \\ 0 & 0 & \dots & r _ {X _ {m}} (\lambda) \end{array} \right]
$$

这时

$$
R _ {Y} (\lambda) = \sum_ {k = 1} ^ {m} \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} e ^ {A u _ {1}} \boldsymbol {b} _ {k} r _ {X _ {k}} (\lambda - u _ {1} + u _ {2}) \boldsymbol {b} _ {k} ^ {\tau} e ^ {A ^ {\tau} u _ {2}} d u _ {1} d u _ {2} \tag {14.9-15}
$$

其中 $b_{k}$ 是矩阵 B 的第 k 列向量， $b_{k}^{\tau}$ 是 $b_{k}$ 的转置。方程(14.9-15)表明，只有输入作用各分量互不相关时，系统状态的相关矩阵才等于输入作用各分量单独作用时的状态相关矩阵之和。

如果我们把

$$
\Phi_ {Y} (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} R _ {Y} (\lambda) e ^ {- i \omega \lambda} d \lambda \tag {14.9-16}
$$

$$
\Phi_ {Y X} (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} R _ {Y X} (\lambda) e ^ {- i \omega \lambda} d \lambda \tag {14.9-17}
$$

称为自功率谱密度矩阵和互功率谱密度矩阵，它们的元素为自功率谱密度和互功率谱密度，那么读者不难证明类似于方程(14.9-6)和(14.9-7)的公式

$$
\Phi_ {Y} (\omega) = \boldsymbol {F} (i \omega) \Phi_ {X} (\omega) \boldsymbol {F} ^ {\tau} (- i \omega) \tag {14.9-18}
$$

$$
\Phi_ {Y X} (\omega) = \boldsymbol {F} (i \omega) \Phi_ {X} (\omega) \tag {14.9-19}
$$

式中 $F(s)$ 是系统的传递函数矩阵

$$
\boldsymbol {F} (s) = \int_ {0} ^ {\infty} e ^ {A t} B e ^ {- s t} d t
$$

$F^{r}(s)$ 是 $F(s)$ 的转置矩阵。同样，与方程(14.9-8)相类似有

$$
\overline {{{\boldsymbol {Y}}}} = \boldsymbol {F} (0) \overline {{{\boldsymbol {X}}}} \tag {14.9-20}
$$

当系统阶数很高时，用上述方法计算输出的功率谱密度和相关函数就比较麻烦。现在我们来介绍兰宁和白亭(Laning, Battin)所提出的模拟计算方法 $^{[14]}$ ，当系统是以实物给出时这种方法也完全可以应用。我们来看一个输入和一个输出的系统。根据方程(14.9-4)，输出量的相关函数为

$$
r _ {Y} (\lambda) = \int_ {0} ^ {\infty} h (u ^ {\prime}) d u ^ {\prime} \int_ {0} ^ {\infty} h (u) r _ {x} (\lambda - u + u ^ {\prime}) d u
$$

作变量置换 $t = \lambda + u'$ ，有

$$
r _ {Y} (\lambda) = \int_ {\lambda} ^ {\infty} h (t - \lambda) d t \int_ {0} ^ {\infty} h (u) r _ {X} (t - u) d u
$$

考虑到互相关函数的公式有

$$
r _ {Y X} (t) = \int_ {0} ^ {\infty} h (u) r _ {X} (t - u) d u \tag {14.9-21}
$$

$$
r _ {Y} (\lambda) = \int_ {\lambda} ^ {\infty} h (t - \lambda) r _ {Y X} (t) d t = \int_ {- \infty} ^ {\infty} h (t - \lambda) r _ {Y X} (t) d t \tag {14.9-22}
$$

后一等式的成立是因为当 t<0 时 $h(t)=0$ 。这样，模拟的方框图就如图 14.9-1 所示。模拟的原理如下：

(1) 在 t=0 时开始将输入相关函数 $r_{X}(t)$ 输入第一个系统 $F(s)$ 。

（2）在 $t=\lambda$ 时再将单位脉冲输入第二个系统，它的传递函数也是 $F(s)$ ，或者可以把单位脉冲输入等效为系统 $F(s)$ 的相应的初始条件。

（3）将(1)和(2)得到的结果送入乘法器，相乘，再把乘积送入积分器进行积分，当 $t\to\infty$ （实际上只要第(1)和(2)项输出近于零后）时，积分器的输出就趋于 $r_{Y}(\lambda)$ 。当 $\lambda=0$ 时得到的结果就是方差 $\sigma_{r}^{2}$ 。

> 此处省略原书 **图 14.9-1**

现在我们引进成型滤波器 $^{[14]}$ 的概念，利用这个概念可以使模拟或者分析计算方便很多。在实际工程问题中我们常碰到的平稳随机过程的功率谱密度是 $\omega$ 的有理分式，并常可写成下列形式

$$
\Phi (\omega) = \frac {Q (\omega)}{P (\omega)} = \frac {A (i \omega) A (- i \omega)}{B (i \omega) B (- i \omega)} = \Psi (i \omega) \Psi (- i \omega) \tag {14.9-23}
$$

其中 $\Psi(i\omega)$ 的所有零点和极点，即 $A(i\omega)$ 和 $B(i\omega)$ 的零点，都在上半 $\omega$ 平面，也就是这些点的虚部都大于零； $A(s)$ 和 $B(s)$ 都是 s 的多项式， $A(s)$ 的幂次小于 $B(s)$ 的幂次。把白色噪声自 $t=-\infty$ 开始就加入至某一线性常系数系统，它输出的功率谱密度可以按方程式 (14.9-23) 求出。如果某一系统当输入为功率谱密度恒等于 1 的白色噪声时，它的输出功率谱密度等于 $\Phi_{X}(\omega)$ ，我们称此系统为成型滤波器。显然，它的传递函数等于 $\Psi(s)=A(s)/B(s)$ 。按照上面的假定，它是稳定的，所以有可能用电阻电容等元件简单地构成。

可以把成型滤波器 $\Psi(s)$ 与系统 $F(s)$ 串联起来看作一个新的线性常系数系统 $F_{1}(s)$

$$
F _ {1} (s) = \Psi (s) F (s) \tag {14.9-24}
$$

如果原系统 $F(s)$ 是稳定的，那么新系统 $F_{1}(s)$ 也是稳定的。新系统的脉冲响应函数为

$$
h _ {1} (t) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} F _ {1} (i \omega) e ^ {i \omega t} d \omega = \int_ {0} ^ {\infty} f (\sigma) \psi (t - \sigma) d \sigma \tag {14.9-25}
$$

其中

$$
\psi (t) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \Psi (i \omega) e ^ {i \omega t} d \omega
$$

如果在系统 $F_{1}(s)$ 的输入端加上一个功率谱密度等于 1，即相关函数为 $\pi\delta(\lambda)$ 的随机过程，那么 $F_{1}(s)$ 输出的功率谱密度仍为 $\Phi_{Y}(\omega)$ 。这时

$$
\begin{array}{l} r _ {Y} (\lambda) = \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} \pi \delta (\lambda - u + u ^ {\prime}) h _ {1} (u) h _ {1} (u ^ {\prime}) d u d u ^ {\prime} \\ = \pi \int_ {0} ^ {\infty} h _ {1} (u) h _ {1} (\lambda + u) d u \tag {14.9-26} \\ \end{array}
$$

输出的方差为

$$
\sigma_ {Y} ^ {2} = r _ {Y} (0) = \pi \int_ {0} ^ {\infty} h _ {1} ^ {2} (u) d u \tag {14.9-27}
$$

由方程(14.9-27)可以看出, $\sigma_{y}^{2}$ 可以用模拟计算方法简单地求出，其模拟计算的方块图可以表示成图 14.9-2 的形式。其中单位脉冲 $\delta(t)$ 的输入可以化为等效的初始条件。

> 此处省略原书 **图 14.9-2**

现在我们来讨论平稳随机输入作用下线性常系数系统分析的几个例子。

（1）考虑第四章曾讨论过的二阶线性常系数系统。设系统的运动方程是

$$
m \frac {d ^ {2} y}{d t ^ {2}} + c \frac {d y}{d t} + k y = x (t)
$$

不难检验，系统的传递函数 $F(s)$ 是

$$
F (s) = \frac {1}{m s ^ {2} + c s + k} = \frac {1}{k} \frac {1}{\left(s ^ {2} / \omega_ {0} ^ {2}\right) + 2 \zeta (s / \omega) + 1}
$$

这里的 $\omega$ 是指没有阻尼时的自然频率, $\zeta$ 是实际阻尼与临界阻尼的比值

$$
\omega_ {0} ^ {2} = \frac {k}{m}, \quad \zeta = \frac {c / m}{2 \omega_ {0}}
$$

于是可求出

$$
\left| F (i \omega) \right| ^ {2} = F (i \omega) F (- i \omega) = \frac {1}{k ^ {2} \left\{\left[ (\omega / \omega) ^ {2} - 1 \right] ^ {2} + 4 \zeta^ {2} (\omega / \omega) ^ {2} \right\}}
$$

如果平稳随机输入的数学期望是 $\overline{X}$ ，功率谱密度是 $\Phi_{X}(\omega)$ ，那么输出的数学期望和功率谱密度就分别是

$$
\overline {{{Y}}} = F (0) \overline {{{X}}} = \frac {1}{k} \overline {{{X}}}
$$

$$
\Phi_ {Y} (\omega) = \frac {\Phi_ {X} (\omega)}{k ^ {2} \left\{\left[ (\omega / \omega_ {0}) ^ {2} - 1 \right] ^ {2} + 4 \zeta^ {2} (\omega / \omega_ {0}) ^ {2} \right\}}
$$

如果我们希望知道输出的方差，那么有

$$
\sigma_ {Y} ^ {2} = \int_ {0} ^ {\infty} \Phi_ {Y} (\omega) d \omega = \frac {1}{k ^ {2}} \int_ {0} ^ {\infty} \frac {\Phi_ {X} (\omega)}{\left[ (\omega / \omega) ^ {2} - 1 \right] ^ {2} + 4 \zeta^ {2} (\omega / \omega) ^ {2}} d \omega
$$

如果 $\zeta$ 很小，则被积函数的分母在 $\omega = \omega_0$ 处几乎等于零。因此，如果 $\Phi_X(\omega)$ 是一个变化缓慢的函数，就有

$$
\sigma_ {Y} ^ {2} \cong \frac {\omega_ {0} \Phi_ {X} (\omega_ {0})}{k ^ {2}} \int_ {0} ^ {\infty} \frac {d x}{(x ^ {2} - 1) ^ {2} + 4 \zeta^ {2} x ^ {2}} = \frac {1}{k ^ {2}} \omega_ {0} \Phi_ {X} (\omega) \frac {\pi}{4 \zeta} = \frac {\pi}{2 m c} \frac {\Phi_ {X} (\omega_ {0})}{\omega_ {0} ^ {2}}
$$

这个等式表明，如果阻尼系数 c 趋于零，输出的方差就趋于无穷大。当 c 等于零时，传递函数 $F(s)$ 有一对纯虚数极点 $i\omega_{0}$ 。一般来说，只要线性系统的传递函数有实部大于或等于零的极点，就会发生输出方差是无限大的现象。因此，如果要求线性系统在随机输入作用下具有符合需要的运转状态，那么传递函数 $F(s)$ 的所有极点必须都要有负实部。这就是本节开始时我们对系统所加的限制。这种要求与在普通非随机的输入作用下对系统的要求是相同的。一般来说，可以用进一步改变系统的传递函数的方法来改变输出的其他性能。例如，我们完全可以设想在某一个合用的频率 $\omega_{0}^{*}$ 处，函数 $\Phi_{X}(\omega)/\omega_{0}^{2}$ 取极小值，就像图 14.9-3 所画的那样。那么，输出的随机振幅的大小就可以减小到几乎是最低的限度。其实，这是容易做到的，只要在系统上加一个传递函数是常数 $\alpha$ 的反馈线路就可以了（参看图 14.9-4)。这样一来，系统的运动方程就变为

$$
m \frac {d ^ {2} y}{d t ^ {2}} + c \frac {d y}{d t} + k y = x - \alpha y
$$

或者

$$
m \frac {d ^ {2} y}{d t ^ {2}} + c \frac {d y}{d t} + (k + \alpha) y = x
$$

系统的自然频率变为 $\sqrt{\frac{k+\alpha}{m}}$ 。所以只要适当地选择 $\alpha$ 的值，就可以使系统的自然频率等于 $\omega_{0}^{*}$

$$
\left(\omega_ {0} ^ {*}\right) ^ {2} = \frac {k + \alpha}{m}
$$

> 此处省略原书 **图 14.9-3**

> 此处省略原书 **图 14.9-4**

如果既要使输出的方差最小，又要使输出的数学期望不变，那么反馈线路的传递函数应该选择得使系统稳态放大系数不变，因此这时反馈线路应是微分环节。具体参数的选择问题，我们将在下一章里讨论。

（2）作为第二个例子，我们考虑一个弦长是 c 的薄平板状的机翼，这个机翼以一个常速度 V 在空气的湍流中运动。设 x 轴在弦的方向上，z 轴在机翼的跨度方向上，y 轴与跨度方向和弦都垂直。假设湍流的扰动速度分量 u, v, w 与 V 相比较都是很小的。由于这些湍流扰动速度的存在，机翼就有一个随时间变化的明显的冲角 $\alpha$ ，因而也就在机翼上产生了随时间变化的升力。只要扰动速度相当小，变化着的冲角 $\alpha$ 就由下列公式给出

$$
\alpha = \frac {v}{V}
$$

这时，可以把冲角 $\alpha=\alpha(t)$ 看做是系统驱动函数。系统的“反应”（输出）就是机翼上变化着的升力，或者，把升力系数 $C_{t}$ 看做是系统的反应。这是李普曼（Liepmann）研究过的一个问题 $^{[15]}$ 。

为了求出升力系数的平均平方值 $\overline{C_{l}^{2}(t)}$ ，首先必须确定机翼的一个传递函数。这个工作已经在第 12.2 节里做过了。其实，如果 v 是输入，升力系数 $C_{l}$ 是输出，那么，频率特性 $F(i\omega)$ 就是由方程(12.2-19)到(12.2-22)的各个方程所表示的。

虽然，实质上湍流扰动是三维的，也就是说,u,v,w 都是 x,y,z,t 的函数。可是，对于第一次近似的分析来说，只考虑 v 以及 v 与 x,t 的关系似乎就很够了。所以，在湍流中我们只来考虑下列形状的扰动速度或冲角

$$
\alpha (x, t) = \frac {v (x , t)}{V}
$$

假定，在数量级是 c/V 的时间里，湍流的特性没有显著的变化，冲角就只与 $t-(x/V)$ 有关，第 12.2 节所给的西尔思的结果也就可以应用。在分析湍流的时候，常常采用这一个假设。这个假设实质上也就是要求下面的条件成立：一个流体质点的流速的时间变化率小于一个固定的空间点处的流速的时间变化率。根据这个假

设，就有

$$
\overline {{{C _ {l} ^ {2}}}} = 4 \pi^ {2} \int_ {0} ^ {\infty} \Phi (\omega) | \varphi (k) | ^ {2} d \omega
$$

其中的 $\Phi(\omega)$ 是 v/V 的功率谱。

按照第 14.4 节的例 2

$$
\Phi (\omega) = \frac {\overline {{v}} ^ {2}}{V ^ {2}} \frac {L}{\pi V} \frac {1 + 3 (L ^ {2} \omega^ {2} / V ^ {2})}{[ 1 + (L ^ {2} \omega^ {2} / V ^ {2}) ] ^ {2}}
$$

此外，李普曼还发现 $|\varphi (k)|^2$ 可以近似地表示为

$$
\mid \varphi (k) \mid^ {2} \approx \frac {1}{1 + 2 \pi k}
$$

所以

$$
\begin{array}{l} \overline {{{C _ {l} ^ {2}}}} = 4 \pi^ {2} \frac {\overline {{{v}}} ^ {2}}{V ^ {2}} \int_ {0} ^ {\infty} \frac {1 + 3 u ^ {2}}{\left(1 + u ^ {2}\right) ^ {2}} \frac {1}{1 + \eta u} d u \\ = 4 \pi^ {2} \frac {\overline {{v ^ {2}}}}{V ^ {2}} \left[ \frac {4 \eta - \pi}{2 \pi (\eta^ {2} + 1)} + \frac {\eta^ {2} + 3}{2 \pi (\eta^ {2} + 1) ^ {2}} (\eta \log \eta^ {2} + \pi) \right] \\ \end{array}
$$

其中

$$
\eta = \frac {\pi c}{L}
$$

升力系数的平均平方值与参数 $\eta$ 之间的关系如图 14.9-5 所示。

> 此处省略原书 **图 14.9-5**

很显然，如果 $c/L \rightarrow 0$ , 这就是弦长比湍流的尺度小得很多的情形。这时

$$
\overline {{{C _ {l} ^ {2}}}} \rightarrow 4 \pi^ {2} \frac {\overline {{{v}}} ^ {2}}{V ^ {2}} = 4 \pi^ {2} \overline {{{\alpha}}} ^ {2}
$$

在似稳状态中，机翼的升力系数与冲角的关系曲线的斜率就是 $2\pi$ 。相反地，如果 $c / L$ 非常大，这就是机翼的弦长比湍流的尺度大得很多的情形，这时 $\overline{C_l^2}$ 几乎等于零。这也就是说：各个局部的扰动总起来说都互相抵消掉了，所以，总的升力是零。其实这个结果是可以想象到的。

（3）间歇输入的问题：关于空气动力学的扰流抖振问题有一个极为重要的现象，这就是尾流中的间歇现象。所谓间歇现象是这样的：一个尾流的边缘的运动尺度很大，以至于边缘附近的一个点有时候处于尾流的内部，有时候又在尾流的外面。如果一个尾翼与一个失速或者部分失速的机翼的尾流的边缘很接近，这种间歇现象对于尾翼上的升力就会发生很重要的影响。对于这种作用可以作这样一个粗略的理解：可以把尾部的流动看作是一个均匀洗流的区域，这个洗流是有时存在有时消失的，洗流作用的时间是一系列不规则的时间间隔。这样一个流动对于间歇地失速的机翼的尾流中的情况来说，或许就是一个好的模型。在这种情况下，尾翼上的流动状态就是时而这样时而那样的，从一种状态变到另一种状态（从有洗流的状态变到没有洗流的状态，或者反过来）的时间间隔的长度 $T$ 就是一个随机函数，假定 $T$ 的概率分布函数是泊松分布函数，那么按照第 14.6 节中例 2 的结果，稍微修改一下就可以得出 $T$ 的功率谱密度。这里的平均偏差不是 1 而是角度平均值 $\sqrt{v^2} / V$ ；驱动函数（洗流）起作用的时间间隔的平均值也就是 $T$ 的平均值 $\overline{T}$ 。所以功率谱密度就是

$$
\Phi (\omega) = \frac {\overline {{v ^ {2}}}}{V ^ {2}} \frac {\overline {{T}}}{\pi} \frac {1}{1 + (\omega \overline {{T}} / 2) ^ {2}}
$$

于是升力系数的平均平方值的近似值就是

$$
\begin{array}{l} \overline {{{C _ {l} ^ {2}}}} = \frac {\overline {{{v}}} ^ {2}}{V ^ {2}} \frac {\overline {{{T}}}}{\pi} 4 \pi^ {2} \int_ {0} ^ {\infty} \frac {d \omega}{[ 1 + (\omega \overline {{{T}}} / 2) ^ {2} ] [ 1 + \pi (\omega c / V) ]} \\ = 4 \pi^ {2} \frac {\overline {{{v ^ {2}}}}}{V ^ {2}} \frac {2}{\pi} \frac {\eta \log \eta + \frac {\pi}{2}}{1 + \eta^ {2}} \left[ \eta = \frac {2 \pi c}{V T} \right] \\ \end{array}
$$

$\overline{C}_{l}^{2}$ 与 $\eta$ 的这个关系画在图 14.9-6 上。 $\eta\rightarrow0$ 和 $n\rightarrow\infty$ 时的极限值当然是与上面研究过的那种情形相等的。

> 此处省略原书 **图 14.9-6**

#### 14.10 线性变系数系统对非平稳随机输入的反应

在上节中谈到：对于一个线性常系数系统，如果在 $t=-\infty$ 开始加上一个平稳随机输入，那么它的输出也是一个平稳随机过程。但是，输入常常是在某一个时刻才开始加入的，譬如在 t=0 的时刻才开始加入，这时系统的输出将是怎样的呢?我们将要看到，虽然输入是平稳随机过程，但系统的输出，一般讲来，是个非平稳的随机过程。事实上系统的输出是

$$
Y (t) = \int_ {0} ^ {t} h (t - \sigma) X (\sigma) d \sigma \tag {14.10-1}
$$

这里积分上限为 t 是由于 $\sigma > t$ 时 $h(t - \sigma) = 0$ ，积分下限为零是由于输入 $X(t)$ 在 t = 0 时才开始加入。在作变量置换 $u = t - \sigma$ 后得到

$$
Y (t) = \int_ {0} ^ {t} h (u) X (t - u) d u \tag {14.10-2}
$$

可以看出输出量仍是输入量的线性变换。方程(14.10-2)与(14.9-2)不同之处就是积分上限是 t 而不是 $\infty$ 。输出随机过程的数学期望和相关函数分别是

$$
\overline {{{Y}}} (t) = \overline {{{X}}} \int_ {0} ^ {t} h (u) d u \tag {14.10-3}
$$

$$
r _ {Y} (t + \lambda , t) = \int_ {0} ^ {t + \lambda} d u \int_ {0} ^ {t} h (u) h (u ^ {\prime}) r _ {X} (\lambda - u + u ^ {\prime}) d u ^ {\prime} \tag {14.10-4}
$$

可以看出随机过程 $Y(t)$ 是非平稳的。只有 t 足够大， $\int_{0}^{t} h(u) du \rightarrow \int_{0}^{\infty} h(u) du$ 时， $Y(t)$ 才是近于平稳的。

现在来看更一般的情况。假定已给定的系统是一个线性变系数系统，它只有一个输入和一个输出。代表系统输出和输入之间的特性关系的是脉冲响应函数 $h(t,\sigma)$ ，它是两个变量 t 和 $\sigma$ 的函数，它就是在 $\sigma$ 时刻系统输入端加以单位脉冲函数 $\delta(t-\sigma)$ 时系统输出端在 t 时刻的反应。显然 $t<\sigma$ 时 $h(t,\sigma)=0$ 。如果在 t=0 时刻开始在此系统输入端加上一个非平稳随机过程 $X(t)$ ，那么系统的输出也是非平稳的

$$
Y (t) = \int_ {0} ^ {t} h (t, \sigma) X (\sigma) d \sigma \tag {14.10-5}
$$

同样根据随机过程线性变换的原理得出输出 $Y(t)$ 的数学期望和相关函数分别为

$$
\overline {{{Y (t)}}} = \int_ {0} ^ {t} h (t, \sigma) \overline {{{X (\sigma)}}} d \sigma \tag {14.10-6}
$$

$$
r _ {Y} (t + \lambda , t) = \int_ {0} ^ {t + \lambda} d u _ {1} \int_ {0} ^ {t} h (t + \lambda , u _ {1}) h (t, u _ {2}) r _ {X} (u _ {1}, u _ {2}) d u _ {1} d u _ {2} \tag {14.10-7}
$$

输出与输入的互相关函数为

$$
r _ {Y X} (t + \lambda , t) = \int_ {0} ^ {t + \lambda} h (t + \lambda , \sigma) r _ {X} (\sigma , t) d \sigma \tag {14.10-8}
$$

如果输入是一个数学期望等于零的白色噪声，它的相关函数是 $r_{X}(t_{1}, t_{2}) = \delta(t_{1} - t_{2})$ , 那么输出随机过程的自相关函数就为

$$
\begin{array}{l} r _ {Y} (t + \lambda , t) = \int_ {0} ^ {t + \lambda} d u _ {1} \int_ {0} ^ {t} h (t + \lambda , u _ {1}) h (t, u _ {2}) \delta (u _ {1} - u _ {2}) d u _ {2} \\ = \left\{ \begin{array}{l l} \int_ {0} ^ {t} h (t + \lambda , u _ {2}) h (t, u _ {2}) d u _ {2}, & \lambda > 0 \\ \int_ {0} ^ {t + \lambda} h (t + \lambda , u _ {1}) h (t, u _ {1}) d u _ {1}, & \lambda <   0 \end{array} \right. \tag {14.10-9} \\ \end{array}
$$

这时输出与输入的互相关函数将是

$$
\begin{array}{l} r _ {Y X} (t + \lambda , t) = \int_ {0} ^ {t + \lambda} h (t + \lambda , \sigma) \delta (\sigma - t) d \sigma \\ = \left\{ \begin{array}{l l} h (t + \lambda , t), & \lambda > 0 \\ \frac {1}{2} h (t, t), & \lambda = 0 \\ 0, & \lambda <   0 \end{array} \right. \tag {14.10-10} \\ \end{array}
$$

要知道输出随机过程的统计特性必须要知道以第二个变量 $\sigma$ 为自变量的脉冲响应函数 $h(t,\sigma)$ ，也就是在不同的时刻 $\sigma,\sigma<t$ ，输入一个单位脉冲函数 $\delta(t-\sigma)$ 时系统在 t 时刻的输出反应。这一点在一般情况下难以做到。下面我们介绍一种用第十三章所讲的伴随函数和格林公式来解决这类问题的方法。

为了更一般起见我们用向量形式来表示线性变系数系统的状态。假定 $n$ 阶线性变系数系统的运动规律是

$$
\frac {d}{d t} \mathbf {y} = A (t) \mathbf {y} + B (t) \mathbf {x} \tag {14.10-11}
$$

其中 m 维向量 x 是系统的输入作用, n 维向量 y 表示系统的状态, 它的某几个分量是输出量, $A(t)$ 是 $n \times n$ 阶函数方阵, $B(t)$ 是 $n \times m$ 阶函数矩阵, 它们的元素都是变量 t 的函数。系统式(14.10-11)的伴随方程是

$$
\frac {d}{d t} \boldsymbol {\psi} = - A ^ {\tau} (t) \boldsymbol {\psi} \tag {14.10-12}
$$

其中 $A^{\tau}(t)$ 是 $A(t)$ 的转置矩阵， $\psi$ 也是 n 维向量，称为伴随函数。根据格林公式有

$$
\left(\mathbf {y} \left(t _ {2}\right), \boldsymbol {\psi} \left(t _ {2}\right)\right) = \left(\mathbf {y} \left(t _ {1}\right), \boldsymbol {\psi} \left(t _ {1}\right)\right) + \int_ {t _ {1}} ^ {t _ {2}} (B (t) \mathbf {x} (t), \boldsymbol {\psi} (t)) d t \tag {14.10-13}
$$

其中 $(\boldsymbol{y},\boldsymbol{\psi})$ 表示两个向量的数量积, $\boldsymbol{\psi}(t)$ 是伴随方程(14.10-12)在某种初始或终端条件下的解。

假定从 t=0 开始给系统输入一个非平稳的向量随机函数 $X(t)$ ，那么系统的状态 $Y(t)$ 就是一个非平稳的向量随机函数。下面我们分几种情况讨论。

（1）系统状态的初值 t=0 时， $Y(t)=0$ ，输出量是 $Y(t)$ 的某个分量 $Y_{i}(t)$ 。这时只需令伴随方程(14.10-12)的终端条件为

$$
\psi_ {j} (t = T) = \left\{ \begin{array}{l l} 0, & j \neq i \\ 1, & j = i \end{array} \right.
$$

把求出的伴随函数 $\psi(t)$ 代入式(14.10-13)中就得到

$$
Y _ {i} (t = T) = \int_ {0} ^ {T} (B (t) X (t), \boldsymbol {\psi} (t)) d t \tag {14.10-14}
$$

$Y_{i}$ 仍是输入 $X(t)$ 的线性变换。根据随机函数线性变换的原理， $Y_{i}(t)$ 的数学期望和相关函数分别是

$$
\overline {{{Y _ {i} (T)}}} = \int_ {0} ^ {T} (B (t) \overline {{{X (t)}}}, \boldsymbol {\psi} (t)) d t \tag {14.10-15}
$$

$$
r _ {Y i} (T + \lambda , T) = \int_ {0} ^ {T + \lambda} d u _ {1} \int_ {0} ^ {T} \boldsymbol {\psi} _ {1} ^ {\tau} (u _ {1}) B (u _ {1}) R x (u _ {1}, u _ {2}) B ^ {\tau} (u _ {2}) \boldsymbol {\psi} _ {2} (u _ {2}) d u _ {2} \tag {14.10-16}
$$

在式(14.10-16)中 $\psi_{1}(u)$ 是终端条件为

$$
\psi_ {j} (t = T + \lambda) = \left\{ \begin{array}{l l} 0, & j \neq i \\ 1, & j = i \end{array} \right.
$$

时的伴随方程的解, $\psi_{2}(u)$ 是终端条件为

$$
\psi_ {j} (t = T) = \left\{ \begin{array}{l l} 0, & j \neq i \\ 1, & j = i \end{array} \right.
$$

时伴随方程的解；向量或矩阵上的右上角注“ $\tau$ ”仍表示转置；Rx 是输入随机向量函数的自相关矩阵。如果输入是互不相关的数学期望等于零的白色噪声

$$
R _ {X} (t, \sigma) = \left[ \begin{array}{c c c c} \sigma_ {x _ {1}} ^ {2} & 0 & \dots & 0 \\ 0 & \sigma_ {x _ {2}} ^ {2} & \dots & 0 \\ \vdots & \vdots & & \vdots \\ 0 & 0 & \dots & \sigma_ {x _ {m}} ^ {2} \end{array} \right] \delta (t - \sigma) \tag {14.10-17}
$$

那么输出的数学期望 $\overline{Y_i(T)} = 0$ ，相关函数为

$$
r _ {Y i} (T + \lambda , T) = \left\{ \begin{array}{l l} \int_ {0} ^ {T} \sum_ {k = 1} ^ {m} \sigma_ {x _ {k}} ^ {2} \left[ \boldsymbol {\psi} _ {1} ^ {\tau} (u) \boldsymbol {b} _ {k} (u) \boldsymbol {b} _ {k} ^ {\tau} (u) \boldsymbol {\psi} _ {2} (u) \right] d u, & \tau \geqslant 0 \\ \int_ {0} ^ {T + \tau} \sum_ {k = 1} ^ {m} \sigma_ {x _ {k}} ^ {2} \left[ \boldsymbol {\psi} _ {1} ^ {\tau} (u) \boldsymbol {b} _ {k} (u) \boldsymbol {b} _ {k} ^ {\tau} (u) \boldsymbol {\psi} _ {2} (u) \right] d u, & \tau <   0 \end{array} \right. \tag {14.10-18}
$$

其中 $\boldsymbol{b}_{k}(t)$ 是长方矩阵 $B(t)$ 的第 k 列向量。

(2) 系统状态的初值 t=0 时 $Y(t)=0$ ，设输出量为

$$
(\mathbf {Y} (t), \mathbf {c c c c}) = \sum_ {i = 1} ^ {n} c _ {i} (t) Y _ {i} (t)
$$

$\pmb{c}(t)$ 是某个确定的向量函数。那么它的输出 $(Y(T),\pmb {c}(T))$ 仍用 $\int_0^T (B(t)\pmb {X}(t),$ $\psi(t)dt$ 表示, 不同的是 $\psi(t)$ 是伴随方程 (14.10-12) 在终端条件 $\psi(t=T)=c(t=T)$ 时的解。它的数学期望和相关函数的求法和 (1) 相仿。

（3）系统状态的初值不为零，它是一个随机向量 $Y(t=0)=Y_{0}$ ，系统无外作用。如果由终端条件

$$
\psi_ {j} (t = T) = \left\{ \begin{array}{l l} 0, & j \neq i \\ 1, & j = i \end{array} \right.
$$

解出伴随函数在 t=0 时的值 $\psi(0)$ ，那我们就可以得到系统状态分量 $Y_{i}(t)$ 在 t=T 时刻的值

$$
Y _ {i} (T) = \left(\mathbf {Y} _ {0}, \boldsymbol {\psi} (0)\right) = \boldsymbol {\psi} ^ {\tau} (0) \mathbf {Y} _ {0} \tag {14.10-19}
$$

还可以得到系统状态分量 $Y_{i}(T)$ 的数学期望和相关函数，

$$
\overline {{{Y _ {i} (T)}}} = \boldsymbol {\psi} ^ {\tau} (0) \overline {{{\mathbf {Y}}}} _ {0} \tag {14.10-20}
$$

$$
r _ {Y i} (T + \lambda , T) = \boldsymbol {\psi} _ {1} ^ {\tau} (0) \Sigma_ {Y _ {0}} \boldsymbol {\psi} _ {2} (0) \tag {14.10-21}
$$

在式(14.10-21)中 $\psi_{1}$ 和 $\psi_{2}$ 所表示的仍与(1)中的相同。

（4）系统状态的初值不为零，是一个随机向量，在 t=0 时开始加入一个随机输入 $X(t)$ ，它与初始状态不相关。这样可以按照它们分别作用时得到的结果相加，这里也就不再赘述了。

按照上面的方法可以方便地求出输出在某个固定时刻的统计特性。如果要求的是以 t 为自变量的输出的统计特性，那么上面的方法仍然合适。下面我们来介绍一种由邓肯(Duncan) $^{[9]}$ 首先提出的方法。

假定变系数线性系统的运动规律是

$$
\frac {d \mathbf {y}}{d t} = A (t) \mathbf {y} + B (t) \mathbf {x} \tag {14.10-11}
$$

在 t=0 时 $y(0)=0$ 。假定从 t=0 开始给系统输入一个 m 维向量的随机函数 $X(t)$ ，它的各个分量都是数学期望为零的白色噪声，各个分量之间互不相关

$$
R _ {X} (t, \sigma) = \left[ \begin{array}{c c c c} \sigma_ {x _ {1}} ^ {2} & 0 & \dots & 0 \\ 0 & \sigma_ {x _ {2}} ^ {2} & \dots & 0 \\ \vdots & \vdots & & \vdots \\ 0 & 0 & \dots & \sigma_ {x _ {m}} ^ {2} \end{array} \right] \delta (t - \sigma) \tag {14.10-17}
$$

这时，系统的状态或输出是

$$
\boldsymbol {Y} (t) = \int_ {0} ^ {T} \Phi (t, \sigma) B (\sigma) \boldsymbol {X} (\sigma) d \sigma
$$

其中 $\Phi(t,\sigma)=e^{\int_{\sigma}^{t}A(u)du}$ 是齐次方程 $\frac{d}{dt}\mathbf{y}=A(t)\mathbf{y}$ 的基本解矩阵， $\Phi(t,t)=E,E$ 是单位矩阵。显然 $\overline{\mathbf{Y}(t)}=\mathbf{0}$ 。在 t 时刻输出 $\mathbf{Y}(t)$ 与输入 $\mathbf{X}(t)$ 的互相关矩阵为

$$
R _ {Y X} (t, t) = \overline {{{\boldsymbol {Y} (t) \boldsymbol {X} ^ {\tau} (t)}}}
$$

$$
= \int_ {0} ^ {t} \Phi (t, \sigma) B (\sigma) \overline {{{\boldsymbol {X} (\sigma) \boldsymbol {X} ^ {\tau} (t)}}} d \sigma
$$

$$
= \int_ {0} ^ {t} \Phi (t, \sigma) B (\sigma) R _ {X} (\sigma , t) d \sigma
$$

$$
= \frac {1}{2} B (t) \Sigma_ {x} \tag {14.10-22}
$$

其中

$$
\Sigma_ {X} = \left[ \begin{array}{c c c c} \sigma_ {x _ {1}} ^ {2} & 0 & \dots & 0 \\ 0 & \sigma_ {x _ {2}} ^ {2} & \dots & 0 \\ \vdots & \vdots & & \vdots \\ 0 & 0 & \dots & \sigma_ {x _ {n}} ^ {2} \end{array} \right] \tag {14.10-23}
$$

矩阵 $[Y(t)Y^{\tau}(t)]$ 的导数为

$$
\frac {d}{d t} [ \mathbf {Y} (t) \mathbf {Y} ^ {\tau} (t) ] = [ A (t) \mathbf {Y} (t) + B (t) \mathbf {X} (t) ] \mathbf {Y} ^ {\tau} (t) + \mathbf {Y} (t) [ \mathbf {Y} ^ {\tau} (t) A ^ {\tau} (t) + \mathbf {X} ^ {\tau} (t) B ^ {\tau} (t) ]
$$

$$
= A (t) \mathbf {Y} (t) \mathbf {Y} ^ {\tau} (t) + B (t) \mathbf {X} (t) \mathbf {Y} ^ {\tau} (t) + \mathbf {Y} (t) \mathbf {Y} ^ {\tau} (t) A ^ {\tau} (t)
$$

$$
+ \boldsymbol {Y} (t) \boldsymbol {X} ^ {\tau} (t) \boldsymbol {B} ^ {\tau} (t)
$$

在两边取数学期望后，再把式(14.10-22)代入就可得到

$$
\frac {d}{d t} R _ {Y} (t, t) = A (t) R _ {Y} (t, t) + R _ {Y} (t, t) A ^ {\tau} (t) + B (t) \Sigma_ {X} B ^ {\tau} (t) \tag {14.10-24}
$$

这样就得到了自相关矩阵 $R_{Y}(t,t)$ 满足的微分方程。因为 $R_{Y}(t,t)$ 是对称矩阵，所以将方程(14.10-24)展开后得到的是 $\frac{n\times(n+1)}{2}$ 个线性变系数微分方程的方程组。解此微分方程组就可以得到输出 $Y_{i}(t)$ 的方差 $\sigma_{Y_{i}}^{2}(t)$ 和其他一些统计特性。

现在再来看一个例子。所给定的系统是

$$
T \frac {d y}{d t} + y = x, \quad y (0) = 0
$$

在 t=0 开始给系统加入一个数学期望为零的平稳随机过程 $X(t)$ ，它的相关函数为 $r_{X}(\lambda)=ae^{-c|\lambda|}$ 。根据式(14.5-36)得出输入的功率谱密度为

$$
\Phi_ {X} (\omega) = \frac {2 a c}{\pi (c + j \omega) (c - j \omega)}
$$

所以成型滤波器的传递函数为 $\sqrt{\frac{2ac}{\pi}} \cdot \frac{1}{c+s}$ 。如果 $N(t)$ 是一个数学期望为零的白色噪声 $r_{N}(t, \sigma) = \pi \delta (t - \sigma)$ ，那么 $X(t)$ 和 $N(t)$ 满足下列微分方程

$$
\frac {d X}{d t} + c X = \sqrt {\frac {2 a c}{\pi}} N (t)
$$

我们以 Y 和 X 作为向量 $Y(t)$ 的两个分量, 输入作用为 $N(t)$ , 因此

$$
\frac {d \mathbf {Y}}{d t} = A (t) \mathbf {Y} + \boldsymbol {b} (t) N (t)
$$

其中

$$
A (t) = \left[ \begin{array}{c c} - \frac {1}{T} & \frac {1}{T} \\ 0, & - c \end{array} \right], \quad \boldsymbol {b} (t) = \left[ \begin{array}{c} 0 \\ \sqrt {\frac {2 a c}{\pi}} \end{array} \right], \quad \boldsymbol {Y} (t) = \left[ \begin{array}{c} Y (t) \\ X (t) \end{array} \right]
$$

将方程(14.10-24)展开后就得到:

$$
\frac {d}{d t} r _ {Y} (t, t) = - \frac {2}{T} r _ {Y} (t, t) + \frac {2}{T} r _ {Y X} (t, t)
$$

$$
\frac {d}{d t} r _ {Y X} (t, t) = - \left[ \frac {1}{T} + c \right] r _ {Y X} (t, t) + \frac {1}{T} r _ {X} (t, t)
$$

$$
\frac {d}{d t} r _ {X} (t, t) = - 2 c r _ {X} (t, t) + 2 a c
$$

相应的初始条件为 $r_{Y}(0,0) = 0, r_{YX}(0,0) = 0, r_{X}(0,0) = a$ 。于是

$$
\overline {{{Y ^ {2} (t)}}} = r _ {Y} (t) = a \left[ \frac {1}{1 + c T} + \frac {1}{1 - c T} e ^ {- 2 t / T} - \frac {2}{1 - c ^ {2} T ^ {2}} e ^ {- (1 + c T) t / T} \right]
$$

在前面的讨论中我们看到，如果系统的输入是白色噪声，那么分析计算的公式就比较简单，在计算输出的相关函数时只要求单重积分就可以了。但是，系统的输入 $X(t)$ 往往不是白色噪声，而在某些情况下是非平稳过程，我们只知它的相关矩阵 $Rx(t_{1}, t_{2})$ 。根据在线性常系数系统中引进的成型滤波器的概念，我们也可以设想 $X(t)$ 是某一个线性变系数系统在输入为白色噪声时的输出，这个系统就是成型滤波器。现在我们就设法根据相关矩阵 $Rx(t_{1}, t_{2})$ 来求成型滤波器的方程 $^{[20]}$ 。我们先假定成型滤波器的方程已给定

$$
\frac {d}{d t} \boldsymbol {x} = D (t) \boldsymbol {x} + \boldsymbol {f} (t) n (t) \tag {14.10-25}
$$

其中 $D(t)$ 和 $f(t)$ 为待求的函数矩阵和函数向量，滤波器的输入 $N(t)$ 是数学期望等于零的白色噪声 $r_{N}(t_{1}, t_{2}) = \delta(t_{1} - t_{2})$ ，输出为非平稳随机过程 $X(t)$ ，输入 $N(t)$ 是自 $t = t_{0}$ 时刻开始加入的， $X(t_{0}) = 0$ 。那么我们可以得到

$$
\boldsymbol {X} (t) = \int_ {t _ {0}} ^ {t} \Phi (t, u) \boldsymbol {f} (u) N (u) d u
$$

其中 $\Phi(t,u)$ 是方程(14.10-25)的齐次方程的基本解矩阵

$$
\frac {d}{d t} \Phi (t, u) = D (t) \Phi (t, u)
$$

当 $n(t)$ 是单位脉冲函数 $\delta(t-\sigma)$ 时，我们记输出为 $\boldsymbol{h}(t,\sigma)$ 。显然， $\boldsymbol{h}(t,\sigma)$ 代表系统的脉冲响应函数

$$
\boldsymbol {h} (t, \sigma) = \int_ {t _ {0}} ^ {t} \Phi (t, u) \boldsymbol {f} (u) \delta (u - \sigma) d u
$$

$$
= \left\{ \begin{array}{l} \Phi (t, \sigma) f (\sigma), \quad t > \sigma > t _ {0} \\ \frac {1}{2} f (\sigma), \quad t = \sigma \\ \mathbf {0}, \quad \sigma > t > t _ {0} \end{array} \right. \tag {14.10-26}
$$

输出的自相关矩阵 $R_{x}(t_{1}, t_{2})$ 为

$$
R _ {X} \left(t _ {1}, t _ {2}\right) = \overline {{{\boldsymbol {X} \left(t _ {1}\right) \boldsymbol {X} ^ {\tau} \left(t _ {2}\right)}}} = \int_ {t _ {0}} ^ {t _ {1}} d u _ {1} \int_ {t _ {0}} ^ {t _ {2}} \Phi \left(t _ {1}, u _ {1}\right) \boldsymbol {f} \left(u _ {1}\right) \delta \left(u _ {1} - u _ {2}\right) \boldsymbol {f} ^ {\tau} \left(u _ {2}\right) \Phi^ {\tau} \left(t _ {2}, u _ {2}\right) d u _ {2}
$$

$$
= \left\{ \begin{array}{l l} \int_ {t _ {0}} ^ {t _ {1}} \boldsymbol {h} (t _ {1}, \sigma) \boldsymbol {h} ^ {\tau} (t _ {2}, \sigma) d \sigma , & t _ {1} \leqslant t _ {2} \\ \int_ {t _ {0}} ^ {t _ {2}} \boldsymbol {h} (t _ {1}, \sigma) \boldsymbol {h} ^ {\tau} (t _ {2}, \sigma) d \sigma , & t _ {1} \geqslant t _ {2} \end{array} \right. \tag {14.10-27}
$$

自相关矩阵 $R_{x}(t_{1}, t_{2})$ 具有如下特性：

(1) 当 $t_{1} > t_{2} > t_{0}$ 时 $\left|\frac{d}{dt_{1}}R_{X}(t_{1}, t_{2}) = D(t_{1})R_{X}(t_{1}, t_{2})\right|$ (14.10-28)

当 $t_2 > t_1 > t_0$ 时 $\frac{d}{dt_2} Rx(t_1, t_2) = Rx(t_1, t_2)D^{\tau}(t_2)$ (14.10-29)

(2) 当 $t_{2} > t_{1} > t_{0}$ 时

$$
\frac {d}{d t _ {1}} R _ {X} \left(t _ {1}, t _ {2}\right) = D \left(t _ {1}\right) R _ {X} \left(t _ {1}, t _ {2}\right) + \boldsymbol {f} \left(t _ {1}\right) \boldsymbol {h} ^ {\tau} \left(t _ {2}, t _ {1}\right) \tag {14.10-30}
$$

当 $t_1 > t_2 > t_0$ 时

$$
\frac {d}{d t _ {2}} R _ {X} \left(t _ {1}, t _ {2}\right) = R _ {X} \left(t _ {1}, t _ {2}\right) D ^ {\tau} \left(t _ {2}\right) + \boldsymbol {h} \left(t _ {1}, t _ {2}\right) \boldsymbol {f} ^ {\tau} \left(t _ {2}\right) \tag {14.10-31}
$$

（3）自相关矩阵 $R_{x}(t_{1}, t_{2})$ 总可以分解为单自变量矩阵的乘积

$$
R _ {X} \left(t _ {1}, t _ {2}\right) = \left\{ \begin{array}{l l} H \left(t _ {1}, t _ {0}\right) \Phi^ {\tau} \left(t _ {2}, t _ {0}\right), & t _ {1} <   t _ {2} \\ \Phi \left(t _ {1}, t _ {0}\right) H ^ {\tau} \left(t _ {2}, t _ {0}\right), & t _ {1} > t _ {2} \end{array} \right. \tag {14.10-32}
$$

实际上，当 $t_1 < t_2$ 时，

$$
R _ {X} \left(t _ {1}, t _ {2}\right) = \int_ {t _ {0}} ^ {t _ {1}} \boldsymbol {h} \left(t _ {1}, \sigma\right) \boldsymbol {f} ^ {\tau} (\sigma) \Phi^ {\tau} \left(t _ {2}, \sigma\right) d \sigma = \int_ {t _ {0}} ^ {t _ {1}} \boldsymbol {h} \left(t _ {1}, \sigma\right) \boldsymbol {f} ^ {\tau} (\sigma) \Psi \left(\sigma , t _ {0}\right) \Phi^ {\tau} \left(t _ {2}, t _ {0}\right) d \sigma
$$

其中 $\Psi(\sigma,t_{0})=\Phi^{-1}(\sigma,t_{0})$ 。如果令

$$
H (t _ {1}, t _ {0}) = \int_ {t _ {0}} ^ {t _ {1}} \boldsymbol {h} (t _ {1}, \sigma) \boldsymbol {f} ^ {\varepsilon} (\sigma) \Psi (\sigma , t _ {0}) d \sigma \tag {14.10-33}
$$

其中 $\Psi(\sigma,t_{0})=\Phi^{*}(t_{0},\sigma)$ ，就可得到式(14.10-32)的上半等式。同样也可以得到式(14.10-33)的下半等式。可以看出，矩阵 $H(t_{1},t_{0})$ 满足下面的微分方程

$$
\frac {d}{d t _ {1}} H \left(t _ {1}, t _ {0}\right) = D \left(t _ {1}\right) H \left(t _ {1}, t _ {0}\right) + f \left(t _ {1}\right) f ^ {\tau} \left(t _ {1}\right) \Psi \left(t _ {1}, t _ {0}\right) \tag {14.10-34}
$$

根据自相关矩阵的以上特性，我们就可以由自相关矩阵 $R_{x}(t_{1}, t_{2})$ 求出待求的

函数矩阵 $D(t)$ 和函数向量 $f(t)$ 。

在求出 $D(t)$ 和 $f(t)$ 后，就可以把成型滤波器式(14.10-25)和原来的系统式(14.10-11)，合并成一个新的线性变系数系统。在 $t = t_{0}$ 开始在新的系统上加上一个数学期望为零的白色噪声 $N(t), R_{N}(\tau) = \delta(\tau)$ 。新系统的输出中的一部分分量就组成了 $Y(t)$ 。根据前面的分析我们可以求出输出 $Y(t)$ 的统计特性。

在通常情况下, $X(t)$ 不是向量随机函数，而是一般的随机过程,

$$
r _ {X} \left(t _ {1}, t _ {2}\right) = \left\{ \begin{array}{l l} h \left(t _ {1}, t _ {0}\right) \cdot \varphi \left(t _ {2}, t _ {0}\right), & t _ {2} > t _ {1} > t _ {0} \\ \varphi \left(t _ {1}, t _ {0}\right) \cdot h \left(t _ {2}, t _ {0}\right), & t _ {1} > t _ {2} > t _ {0} \end{array} \right.
$$

这时，很容易求出成型滤波器的 $d(t)$ 和 $f(t)$ 。例如，非平稳随机过程 $X(t), t > 0$ 的相关函数为

$$
r _ {X} \left(t _ {1}, t _ {2}\right) = \left\{ \begin{array}{l l} 3 t _ {1} / t _ {2} ^ {2}, & t _ {2} > t _ {1} > 0 \\ 3 t _ {2} / t _ {1} ^ {2}, & t _ {1} > t _ {2} > 0 \end{array} \right.
$$

这时 $t_0 = 0, h(t, t_0) = 3t, \varphi(t, t_0) = 1/t^2, \psi(t, t_0) = t^2$ 。

因此

$$
d (t) = \frac {d}{d t} \left[ \frac {3 t _ {2}}{t ^ {2}} \right] / \frac {3 t _ {2}}{t ^ {2}} = - \frac {2}{t}
$$

$$
f ^ {2} (t) = \left[ \frac {d}{d t} (3 t) - \left(- \frac {2}{t}\right) 3 t \right] \frac {1}{t ^ {2}} = \frac {9}{t ^ {2}}
$$

$$
f (t) = \frac {3}{t}
$$

所以，成型滤波器的方程为

$$
\frac {d x}{d t} = - \frac {2}{t} x + \frac {3}{t} n (t), \quad t > t _ {0} = 0
$$

即

$$
t \frac {d x}{d t} + 2 x = 3 n (t), \quad t > t _ {0} = 0
$$

#### 14.11 在随机输入作用下非线性系统的分析

在实际系统中总是存在着各种非线性的因素，最常见的就是饱和现象和非灵敏区现象。在某些特定条件下，有可能把非线性系统近似看作线性系统来分析，但是在很多情况下这种近似是不允许的。例如，我们来看一个飞机上自动驾驶仪的舵机系统，它的作用是根据输入到舵机系统的信号大小，按比例地产生舵偏角，使飞机拐弯飞行。舵机系统的作用原理方框图见图 14.11-1。如果控制信号 x 中没有随机分量，那么在最大舵偏角的范围内，舵偏角是正比于控制信号的。如果在控制信号中还夹杂了随机干扰，那么舵偏角也是作随机摆动的。在随机干扰比 较小时，舵偏角的平均值还是正比于控制信号的平均值的大小；当随机干扰比较剧烈时，在同样的控制信号的平均值下舵偏角的平均值会剧烈变小，就是舵系统“失效”了。“失效”的原因是在于舵机系统的放大器有饱和现象。因此即使控制信号中的平均分量使放大器工作在线性段，但是随机干扰剧烈时会使整个舵机系统的性能受到放大器饱和的影响。放大器放大系数选择得越大，则这种“失效”的可能性也越大。在这一节中我们将介绍一种能够包括上述这类问题的分析方法，即在随机输入作用下非线性闭路控制系统的近似分析方法。

> 此处省略原书 **图 14.11-1**

先讨论无惯性非线性环节在随机输入时的输出特性。无惯性非线性环节的输出是输入的非线性函数

$$
y = f (x) \tag {14.11-1}
$$

当加入随机输入时，在任何时刻 $t_{k}$ ，输出的随机变量 $Y(t_{k})$ 只与输入随机变量 $X(t_{k})$ 有关

$$
Y (t _ {k}) = f [ X (t _ {k}) ] \tag {14.11-2}
$$

$t_{k}$ 在这里只是作为参数引入的。如果已经知道随机输入的概率分布特性，那么我们就可以求得随机输出的数学期望，自相关函数，方差及输出输入之间的互相关函数

$$
\overline {{{Y (t)}}} = \int_ {- \infty} ^ {\infty} f (x) w _ {1} (x, t) d x \tag {14.11-3}
$$

$$
\begin{array}{l} r _ {Y} \left(t _ {1}, t _ {2}\right) = \overline {{{Y (t _ {1}) Y (t _ {2})}}} - \overline {{{Y (t _ {1})}}} \cdot \overline {{{Y (t _ {2})}}} \\ = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} f (x _ {1}) f (x _ {2}) w _ {2} (x _ {1}, t _ {1}; x _ {2}, t _ {2}) d x _ {1} d x _ {2} \\ - \int_ {- \infty} ^ {\infty} f (x _ {1}) w _ {1} (x _ {1}, t _ {1}) d x _ {1} \cdot \int_ {- \infty} ^ {\infty} f (x _ {2}) w _ {1} (x _ {2}, t _ {2}) d x _ {2} \tag {14.11-4} \\ \end{array}
$$

$$
\sigma_ {Y} ^ {2} (t) = \int_ {- \infty} ^ {\infty} [ f (x) ] ^ {2} w _ {1} (x, t) d x - \left[ \int_ {- \infty} ^ {\infty} f (x) w _ {1} (x, t) d x \right] ^ {2} \tag {14.11-5}
$$

$$
\begin{array}{l} r _ {Y X} \left(t _ {1}, t _ {2}\right) = \overline {{{{Y (t _ {1}) X (t _ {2})}}}} - \overline {{{{Y (t _ {1})}}}} \cdot \overline {{{{X (t _ {2})}}}} \\ = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} x _ {2} (t _ {2}) f (x _ {1}) w _ {2} (x _ {1}, t _ {1}; x _ {2}, t _ {2}) d x _ {1} d x _ {2} \\ \end{array}
$$

$$
- \int_ {- \infty} ^ {\infty} f (x _ {1}) w _ {1} (x _ {1}, t _ {1}) d x _ {1} \cdot \int_ {- \infty} ^ {\infty} x _ {2} (t _ {2}) w _ {1} (x _ {2}, t _ {2}) d x _ {2} \tag {14.11-6}
$$

假设随机输入 $X(t)$ 是高斯过程，那么它的第一，第二概率密度函数分别是

$$
w _ {1} (x, t) = \frac {1}{\sqrt {2 \pi} \sigma_ {X} (t)} \exp \left\{- \frac {1}{2} \left[ \frac {x (t) - \overline {{{X (t)}}}}{\sigma_ {X} (t)} \right] ^ {2} \right\} \tag {14.11-7}
$$

$$
\begin{array}{l} w _ {2} \left(x _ {1}, t _ {1}; x _ {2}, t _ {2}\right) = \frac {1}{2 \pi \sigma_ {X} \left(t _ {1}\right) \sigma_ {X} \left(t _ {2}\right) \sqrt {1 - \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)}}} \\ \times \exp \left\{- \frac {1}{2 \left(1 - \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)} ^ {2}\right)} \left[ \left(\frac {x \left(t _ {1}\right) - \overline {{X \left(t _ {1}\right)}}}{\sigma_ {X} \left(t _ {1}\right)}\right) ^ {2} \right. \right. \\ + \left[ \frac {x \left(t _ {2}\right) - \overline {{X \left(t _ {2}\right)}}}{\sigma_ {X} \left(t _ {2}\right)} \right] ^ {2} - 2 \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)} \\ \left. \times \frac {\left(x \left(t _ {1}\right) - \overline {{X \left(t _ {1}\right)}}\right) \left(x \left(t _ {2}\right) - \overline {{X \left(t _ {2}\right)}}\right)}{\sigma_ {X} \left(t _ {1}\right) \sigma_ {X} \left(t _ {2}\right)} \right] \Bigg \} \tag {14.11-8} \\ \end{array}
$$

其中 $\rho_{X(t_{1})X(t_{2})}$ 是随机变量 $X(t_{1})$ 和 $X(t_{2})$ 的比相关系数。为了使计算简化，常将第二概率密度函数按照切比雪夫-埃尔米特(Чебыщев-Hermite)多项式展开为无穷级数

$$
w _ {2} \left(x _ {1}, t _ {1}; x _ {2}, t _ {2}\right) = \frac {1}{2 \pi \sigma_ {X \left(t _ {1}\right)} \sigma_ {X \left(t _ {2}\right)}} \exp \left\{- \frac {1}{2} \left[ \frac {x (t _ {1}) - \overline {{x (t _ {1})}}}{\sigma_ {X} (t _ {1})} \right] ^ {2} - \frac {1}{2} \left[ \frac {x (t _ {2}) - \overline {{x (t _ {2})}}}{\sigma_ {X} (t _ {2})} \right] ^ {2} \right\}
$$

$$
\times \sum_ {n = 0} ^ {\infty} \frac {1}{n !} \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)} ^ {n} H _ {n} \left[ \frac {x \left(t _ {1}\right) - \overline {{x \left(t _ {1}\right)}}}{\sigma_ {X} \left(t _ {1}\right)} \right] \cdot H _ {n} \left[ \frac {x \left(t _ {2}\right) - \overline {{x \left(t _ {2}\right)}}}{\sigma_ {X} \left(t _ {2}\right)} \right] \tag {14.11-9}
$$

其中 $H_{n}(\zeta)$ 为切比雪夫-埃尔米特多项式, 它可以从递推公式中得到

$$
H _ {n + 1} (\zeta) = \zeta H _ {n} (\zeta) - n H _ {n - 1} (\zeta)
$$

$$
H _ {0} (\zeta) = 1, \quad H _ {1} (\zeta) = \zeta \tag {14.11-10}
$$

多项式 $H_{n}(\zeta), n=0,1,2,\cdots$ 在 $-\infty<\zeta<\infty$ 上对权函数 $e^{-\frac{\zeta^{2}}{2}}$ 是正交的

$$
\int_ {- \infty} ^ {\infty} H _ {n} (\zeta) H _ {m} (\zeta) e ^ {- \frac {\zeta^ {2}}{2}} d \zeta = \left\{ \begin{array}{c} 0, \quad m \neq n \\ \sqrt {2 \pi} n!, \quad m = n \end{array} \right. \tag {14.11-11}
$$

这样，高斯过程 $X(t)$ 经过无惯性非线性环节后输出的统计特性就是

$$
\overline {{{Y (t)}}} = \overline {{{f [ X (t) ]}}} = a _ {0} (t) = a _ {0} (\overline {{{X (t)}}}, \sigma_ {X} (t)) \tag {14.11-12}
$$

$$
r _ {Y} \left(t _ {1}, t _ {2}\right) = \sum_ {n = 1} ^ {\infty} \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)} ^ {n} a _ {n} \left(t _ {1}\right) a _ {n} \left(t _ {2}\right)
$$

$$
= \sum_ {n = 1} ^ {\infty} \rho_ {X (t _ {1}) X (t _ {2})} ^ {n} a _ {n} (\overline {{{{X (t _ {1})}}}}, \sigma_ {X} (t _ {1})) a _ {n} (\overline {{{{X (t _ {2})}}}}, \sigma_ {X} (t _ {2})) \tag {14.11-13}
$$

$$
\sigma_ {Y} ^ {2} (t) = \sum_ {n = 0} ^ {\infty} a _ {n} ^ {2} (\overline {{{X (t)}}}, \sigma_ {X} (t)) \tag {14.11-14}
$$

$$
\begin{array}{l} r _ {Y X} \left(t _ {1}, t _ {2}\right) = \sum_ {n = 1} ^ {\infty} \rho_ {X \left(t _ {1}\right) X \left(t _ {2}\right)} ^ {n} a _ {n} (t) b _ {n} (t) \\ = \sum_ {n = 1} ^ {\infty} \rho_ {X (t _ {1}) X (t _ {2})} ^ {n} a _ {n} (\overline {{{X (t _ {1})}}} \sigma_ {X} (t _ {1})) b _ {n} (\overline {{{X (t _ {2})}}}, \sigma_ {X} (t _ {2})) \tag {14.11-15} \\ \end{array}
$$

其中

$$
a _ {n} (t) = a _ {n} (\overline {{{X (t)}}}, \sigma_ {X} (t)) = \frac {1}{\sqrt {n !}} \overline {{{f [ X (t) ] H _ {n} \left[ \frac {X (t) - \overline {{{X (t)}}}}{\sigma_ {X} (t)} \right]}}}, \quad n = 0, 1, 2, \dots \tag {14.11-16}
$$

$$
b _ {n} (t) = \frac {1}{\sqrt {n !}} \overline {{{X (t) H _ {n} \left[ \frac {X (t) - \overline {{{X (t)}}}}{\sigma_ {X} (t)} \right]}}}, \quad n = 1, 2, \dots \tag {14.11-17}
$$

利用公式(14.11-10)中的 $H_{0}(\zeta)=1, H_{1}(\zeta)=\zeta$ 和正交性式(14.11-11)可以最后得到

$$
r _ {Y X} (t _ {1}, t _ {2}) = \frac {1}{\sigma_ {X} (t _ {1})} a _ {1} \overline {{(X (t _ {1})}}, \sigma_ {X} (t _ {1})) r _ {X} (t _ {1}, t _ {2}) \tag {14.11-18}
$$

如果 $X(t)$ 是平稳高斯过程，那么公式(14.11-12)—(14.11-17)和(14.11-18)将分别为

$$
\overline {{{Y}}} = \overline {{{f (X)}}} = a _ {0} (\overline {{{X}}}, \sigma_ {X}) \tag {14.11-19}
$$

$$
r _ {Y} (\lambda) = \sum_ {n = 1} ^ {\infty} \rho_ {X} ^ {n} (\lambda) a _ {n} ^ {2} (\overline {{{X}}}, \sigma_ {X}) \tag {14.11-20}
$$

$$
\sigma_ {Y} ^ {2} = \sum_ {n = 1} ^ {\infty} a _ {n} ^ {2} (\overline {{{X}}}, \sigma_ {X}) \tag {14.11-21}
$$

$$
a _ {n} (\overline {{{X}}}, \sigma_ {X}) = \frac {1}{\sqrt {n !}} f (X) H _ {n} \left[ \frac {X - \overline {{{X}}}}{\sigma_ {X}} \right], \quad n = 1, 2, \dots \tag {14.11-22}
$$

$$
r _ {Y X} (\lambda) = \frac {1}{\sigma_ {X}} a _ {1} r _ {X} (\lambda) \tag {14.11-23}
$$

> 此处省略原书 **图 14.11-2**

其中 $\rho_{X}(\lambda)$ 就是 $\rho_{X(t + \lambda)X(t)}$ 。级数 $r_Y(\lambda)$ 具有明显的物理意义，与它第一项相应的输出的那一个分量，其相关函数的形式与输入的相关函数是一致的，其余分量表示由于非线性引起的畸变。这些畸变通常不是很显著的，首先是因为级数的系数以 $1 / n!$ 的速度递减，其次是由于相关函数本身当 $\lambda >0$ 时， $|\rho_X(\lambda)| < 1$ ，所以 $\rho_X^n (\lambda)$ 随着 $\lambda$ 的增加也急剧减小。主要的畸变也只可能在 $\lambda$ 值较小时发生。

假设, 非线性环节是理想的继电器（图 14.11-2), 它的输出输入关系是

$$
Y = f (X) = \left\{ \begin{array}{l l} l, & x <   0 \\ - l, & x > 0 \end{array} \right.
$$

如果输入的平稳随机过程 $X(t)$ 的数学期望 $\overline{X(t)} = 0$ ，比相关函数 $\rho_X(\lambda) = e^{-|\lambda|}$ ，方差 $\sigma_X^2 = 1$ ，那么输出的自相关函数为

$$
r _ {Y} (\lambda) = \sum_ {n = 1} ^ {\infty} \rho_ {X} ^ {n} (\lambda) a _ {n} ^ {2} = \frac {2 t ^ {2}}{\pi} \sin^ {- 1} \rho_ {X} (\lambda)
$$

$r_{Y}(\lambda)$ 的第一项是 $\rho_{X}(\lambda)a_{1}^{2}$ ，它们的关系见图 14.11-3。当 $|\lambda| \geqslant 0.65$ 时，用 $r_{Y}(\lambda)$ 的第一项 $\rho_{X}(\lambda)a_{1}^{2}$ 来代替 $r_{Y}(\lambda)$ 的误差将不超过 5%。

> 此处省略原书 **图 14.11-3**

对于一些常用到的典型非线性环节，根据公式(14.11-12)和(14.11-16)可以算出系数 $a_{0}, a_{1}, a_{2}$ 等来。对于理想继电器环节（图 14.11-2)来说,

$$
\frac {a _ {0}}{l} = 2 \Phi (\overline {{{X}}} / \sigma_ {X})
$$

$$
\frac {a _ {1}}{l} = \sqrt {\frac {2}{\pi}} e ^ {- \frac {1}{2} (\overline {{X}} / \sigma_ {X}) ^ {2}}
$$

$$
\frac {a _ {2}}{l} = - (\overline {{{X}}} / \sqrt {2} \sigma_ {X}) \frac {a _ {1}}{l}
$$

$$
\frac {a _ {3}}{l} = \frac {1}{\sqrt {6}} \left[ \left(\overline {{{X}}} / \sigma_ {X}\right) ^ {2} - 1 \right] \frac {a _ {1}}{l}
$$

......

其中 $\Phi(X)=\frac{1}{\sqrt{2\pi}}\int_{0}^{X}e^{-\frac{1}{2}t^{2}}dt,\frac{a_{n}}{l}$ 与 $\frac{\overline{X}}{\sigma_{X}}$ 的关系曲线, $n=0,1,2,3,\cdots$ 可见图 14.11-4。对于有限幅特性的线性放大环节（图 14.11-5)，它的输出输入关系是

$$
Y = f (X) = \left\{ \begin{array}{l l} l, & X \geqslant \Delta \\ \frac {l}{\Delta} X, & - \Delta \leqslant X \leqslant \Delta \\ - l, & X \leqslant - \Delta \end{array} \right.
$$

> 此处省略原书 **图 14.11-4**

> 此处省略原书 **图 14.11-5**

系数 $a_0, a_1, a_2, a_3$ 分别为

$$
a = \left\{ \begin{array}{l} (1 + m _ {1}) \Phi \left\{\frac {1 + m _ {1}}{\sigma_ {1}} \right\} - (1 - m _ {1}) \Phi \left\{\frac {1 - m _ {1}}{\sigma_ {1}} \right\} + \frac {\sigma_ {1}}{\sqrt {2 \pi}} \left[ e ^ {- \frac {1}{2} \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) ^ {2}} - e ^ {- \frac {1}{2} \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) ^ {2}} \right] \end{array} \right\}
$$

$$
a _ {1} = l \sigma_ {1} \left[ \Phi \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) + \Phi \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) \right]
$$

$$
a _ {2} = \frac {l \sigma_ {1}}{2 \sqrt {\pi}} \left[ e ^ {- \frac {1}{2} \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) ^ {2}} - e ^ {- \frac {1}{2} \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) ^ {2}} \right]
$$

$$
a _ {3} = - \frac {l}{2 \sqrt {3} \pi} \left[ (1 + m _ {1}) e ^ {- \frac {1}{2} \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) ^ {2}} + (1 - m _ {1}) e ^ {- \frac {1}{2} \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) ^ {2}} \right]
$$

其中 $m_{1} = \overline{X}/\Delta, \sigma_{1} = \sigma_{X}/\Delta, \Phi(x) = \frac{1}{\sqrt{2\pi}}\int_{0}^{x} e^{-\frac{1}{2}t^{2}} dt, \frac{a_{0}}{l}, \frac{\Delta}{l} \cdot \frac{a_{1}}{\sigma_{X}}$ 与 $m_{1}, \sigma_{1}$ 的关系曲线示于图 14.11-6 中。

> 此处省略原书 **图 14.11-6**

知道了无惯性非线性环节在随机输入时的输出特性，就很容易求出开路非线性系统在高斯随机过程的输入作用下的输出特性。在一般情况下，开路非线性系统可以表示为由三个环节串联组成，中间是无惯性非线性环节，前后都是线性惯性环节（图 14.11-7)它们的关系式是

$$
U (t) = \int_ {- \infty} ^ {t} h _ {1} (t, \sigma) X (\sigma) d \sigma
$$

$$
V (t) = f (U (t))
$$

$$
Y (t) = \int_ {- \infty} ^ {t} h _ {2} (t, \sigma) V (\sigma) d \sigma \tag {14.11-24}
$$

> 此处省略原书 **图 14.11-7**

要求得输出 $Y(t)$ 的统计特性, 就需要知道非线性环节输出 $V(t)$ 的统计特性。如果只知道非线性环节输入 $U(t)$ 的数学期望和相关函数是不够的, 必须知道 $U(t)$ 的分布, 才能求出 $V(t)$ 的统计特性。假设开路非线性系统的输入 $X(t)$ 是高斯过程, 那么高斯过程经过任何线性变换后仍是高斯过程, $U(t)$ 也是高斯过程。知道了系统输入 $X(t)$ 的数学期望和相关函数就可以算出系统输出 $Y(t)$ 的数学期望和相关函数。如果线性环节是常系数的, 而且 $X(t)$ 是从 $t = -\infty$ 时输入的平稳过程, 那么在计算中有关随机过程线性变换的部分, 可以考虑利用输出输入之间功率谱密度的关系与相关函数和功率谱密度的关系, 以便使计算简单些。

对于非线性系统来说，开路系统的计算方法不能搬用到闭路系统中去。对于线性系统，我们可以根据开路系统的传递函数或特性求出闭路系统的传递函数或 特性，它与输入的大小无关。对于非线性系统，没有传递函数的概念，系统的特性与输入作用的大小有关，闭路内每个环节的输入及特性都与它的输出有关。即使整个闭路非线性系统的输入是一个高斯过程，但在闭路内的非线性环节的输入，严格说来还不是高斯过程，它的分布规律与很多因素有关，一般来说，比较难于准确确定。不能确定非线性环节输入的分布规律，就不能准确地确定它的输出的统计特性。现在我们来介绍一种工程近似方法——统计线性化方法。这一方法是由波顿(Booton)首先提出的 $^{[7]}$ 。统计线性化方法在实用上比较方便，在满足一定的条件下，它具有足够的准确度，但是也很难确定它在一般情况下的准确程度。

统计线性化的实质就是按照一定的准则用线性放大环节来代替非线性环节，然后按线性系统的方法来分析。我们假设非线性环节的输入是高斯分布的，这样就可以求出非线性环节输出的数学期望、相关函数与输入的数学期望、相关函数的关系。设非线性环节的输出输入特性是

$$
Y = f (X) \tag {14.11-25}
$$

近似的线性环节的输出输入特性为

$$
Y _ {1} = k _ {0} \overline {{{X}}} + k _ {1} (X - \overline {{{X}}}) \tag {14.11-26}
$$

这里对输入的平均分量和随机分量采用了不同的放大系数 $k_{0}$ 和 $k_{1}$ 。 $k_{0}$ 和 $k_{1}$ 的值根据不同的准则来确定，它是与非线性环节的输入有关系的。有一种线性化的准则是使近似偏差 $Y_{1}-Y$ 的平方的数学期望最小，即

$$
\overline {{E ^ {2}}} = \overline {{[ Y _ {1} - Y ] ^ {2}}} = \overline {{[ k _ {0} \overline {{X}} + k _ {1} (X - \overline {{X}}) - Y ] ^ {2}}} = \min \tag {14.11-27}
$$

把式(14.11-27)的右端展开后得到

$$
\overline {{{E ^ {2}}}} = \left[ k _ {0} \overline {{{X}}} - \overline {{{Y}}} \right] ^ {2} + k _ {1} ^ {2} \sigma_ {X} ^ {2} + \sigma_ {Y} ^ {2} - 2 k _ {1} r _ {Y X} (t, t)
$$

要使 $\overline{E^{2}}$ 最小，则令

$$
\frac {\partial \overline {{{E}}} _ {2}}{\partial k _ {0}} = 0, \quad \frac {\partial \overline {{{E}}} _ {2}}{\partial k _ {1}} = 0
$$

这样就得到使 $\overline{E^2}$ 最小时的 $k_0$ 和 $k_{1}$

$$
k _ {0} = \overline {{Y}} / \overline {{X}} \tag {14.11-28}
$$

$$
k _ {1} = r _ {Y X} / \sigma_ {X} ^ {2} \tag {14.11-29}
$$

根据公式(14.11-19)和(14.11-23)就得到

$$
k _ {0} = a _ {0} / \overline {{{X}}} \tag {14.11-30}
$$

$$
k _ {1} = a _ {1} / \sigma_ {X} \tag {14.11-31}
$$

$k_{0}$ 和 $k_{1}$ 都是输入 $X(t)$ 的数学期望 $\overline{X}$ 和方差 $\sigma_{X}$ 的函数。如果非线性特性 $f(X)$ 不是奇对称的，即

$$
f (- X) \neq - f (X)
$$

那么即使输入的数学期望 $\overline{X}$ 等于零, 输出的数学期望 $\overline{Y}$ 也不等于零。这时, 若在

近似的线性环节的输出输入特性式(14.11-26)中用 $\overline{Y}$ 来代替 $k_{0}\overline{X}$ ，则

$$
Y _ {1} = \overline {{{Y}}} + k _ {1} (X - \overline {{{X}}}) \tag {14.11-32}
$$

$$
\overline {{{Y}}} = a _ {0} \tag {14.11-33}
$$

$$
k _ {1} = a _ {1} / \sigma_ {X} \tag {14.11-34}
$$

自然，也可以按照其他准则来确定 $k_{0}$ 和 $k_{1}^{[24]}$ 。

在统计线性化后，闭路非线性系统就成为了闭路线性系统，但是它还有两个待定参数，我们可以把非线性环节的 $a_0, a_1$ 与 $\overline{X}, \sigma_X$ 的关系和线性系统统计分析的方法联系在一起来求出等效的放大系数 $k_0$ 和 $k_1$ 以及非线性闭路系统的近似统计特性。

下面我们用一个极简单的控制系统来作为例子说明如何应用统计线性化方法。假设此控制系统的结构图是图 14.11-8，它所包含的非线性环节是带有限幅特性的放大器。在 $t = -\infty$ 时就开始给系统加上一个已知的平稳随机过程 $X(t)$ ，现在来求此控制系统的输出特性。根据统计线性化的假设，非线性环节的等效放大系数是 $k_{0}$ 和 $k_{1}$ 利用线性系统的分析方法，我们得出输出量 $Y$ 和非线性环节的输入量的数学期望和方差分别是

$$
\overline {{{Y}}} = \frac {k _ {0} K _ {1}}{1 + k _ {0} K _ {1} K _ {2}} \overline {{{X}}}
$$

$$
\overline {{{U}}} = \frac {1}{1 + k _ {0} K _ {1} K _ {2}} \overline {{{X}}}
$$

$$
\sigma_ {Y} ^ {2} = \frac {1}{2} \int_ {- \infty} ^ {\infty} \left| \frac {k _ {1} K _ {1}}{1 + k _ {1} K _ {1} K _ {2} + T j \omega} \right| ^ {2} \Phi_ {X} (\omega) d \omega
$$

$$
\sigma_ {U} ^ {2} = \frac {1}{2} \int_ {- \infty} ^ {\infty} \left| \frac {1 + T j \omega}{1 + k _ {1} K _ {1} K _ {2} + T j \omega} \right| ^ {2} \Phi_ {X} (\omega) d \omega
$$

其中 $\Phi_{X}(\omega)$ 是输入 $X(t)$ 的功率谱密度。

> 此处省略原书 **图 14.11-8**

假设输入随机过程的相关函数为 $r_X(\lambda) = \sigma_X^2 e^{-\alpha |\lambda |}$ ，那么 $\Phi_X(\omega) = \frac{2\alpha\sigma_X^2}{\pi} \cdot \frac{1}{\alpha^2 + \omega^2}$ ，经过一定的运算后可得

$$
\sigma_ {Y} ^ {2} = \frac {\left(k _ {1} K _ {1}\right) ^ {2}}{\left(1 + k _ {1} K _ {1} K _ {2}\right) \left(1 + k _ {1} K _ {1} K _ {2} + \alpha T\right)} \sigma_ {X} ^ {2}
$$

$$
\sigma_ {U} ^ {2} = \frac {1 + \alpha T (1 + k _ {1} K _ {1} K _ {2})}{(1 + k _ {1} K _ {1} K _ {2}) (1 + k _ {1} K _ {1} K _ {2} + \alpha T)} \sigma_ {X} ^ {2}
$$

再根据限幅特性和非线性环节输入是高斯过程的假设，我们可以得到等效放大系数 $k_{0}, k_{1}$ 和非线性环节输入量 U 的统计特性的关系:

$$
k _ {0} = \frac {l}{\Delta} \frac {\sigma_ {1}}{m} \left[ \left(\frac {1 + m}{\sigma_ {1}}\right) \Phi \left(\frac {1 + m}{\sigma_ {1}}\right) - \left(\frac {1 - m}{\sigma_ {1}}\right) \Phi \left(\frac {1 - m}{\sigma_ {1}}\right) + \dot {\Phi} \left(\frac {1 + m}{\sigma_ {1}}\right) - \dot {\Phi} \left(\frac {1 - m}{\sigma_ {1}}\right) \right]
$$

$$
k _ {1} = \frac {l}{\Delta} \left[ \Phi \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) + \Phi \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) \right]
$$

其中

$$
m _ {1} = \frac {\overline {{U}}}{\Delta}, \quad \sigma_ {1} = \frac {\sigma_ {U}}{\Delta}
$$

$$
\Phi (u) = \frac {1}{\sqrt {2 \pi}} \int_ {0} ^ {u} e ^ {- \frac {t ^ {2}}{2}} d t
$$

$$
\dot {\Phi} (u) = \frac {1}{\sqrt {2 \pi}} e ^ {- \frac {u ^ {2}}{2}}
$$

由此我们可以建立联立方程式：

$$
\begin{array}{l} k _ {0} = \frac {l}{\Delta} \frac {\sigma_ {1}}{m _ {1}} \left[ \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) \Phi \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) - \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) \Phi \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) \right. \\ + \dot {\Phi} \left[ \frac {1 + m}{\sigma_ {1}} \right] - \dot {\Phi} \left[ \frac {1 - m}{\sigma_ {1}} \right] \\ \end{array}
$$

$$
k _ {1} = \frac {l}{\Delta} \left[ \Phi \left(\frac {1 + m _ {1}}{\sigma_ {1}}\right) + \Phi \left(\frac {1 - m _ {1}}{\sigma_ {1}}\right) \right]
$$

$$
\sigma_ {1} = \frac {l}{\Delta} \cdot \frac {\sigma_ {X}}{l} \sqrt {\frac {1 + \alpha T \left(1 + k _ {1} K _ {1} K _ {2}\right)}{\left(1 + k _ {1} K _ {1} K _ {2}\right) \left(1 + k _ {1} K _ {1} K _ {2} + \alpha T\right)}}
$$

$$
m _ {1} = \frac {l}{\Delta} \cdot \frac {\overline {{{X}}}}{l} \cdot \frac {1}{1 + K _ {1} K _ {2} k _ {0}}
$$

解上面联立方程式就可以求出等效放大系数 $k_{0}$ 与 $k_{1}$ ，再根据 $k_{0}$ 和 $k_{1}$ 可以求出输出的 $\overline{Y}$ 和 $\sigma_{Y}$ 。假设 $\alpha T = 0.1, l / \Delta = 1, K_{1}K_{2} = 1, K_{1} = 2, \overline{X} / l = 0.8$ ，那么 $k_{0}, k_{1}, \overline{Y} / \overline{X}$ 与 $\sigma_{X} / l$ 的关系见图 14.11-9。从图中可以看出，当输入中的平均分量固定不变时，输入中随机分量愈大，输出的平均分量就愈小。如果把非线性环节的线性段的放大系数 $l / \Delta$ 增大，那么反而使这种“失效”现象更厉害。例如，在 $\alpha T = 0.1, K_{1}K_{2} = 1, \overline{X} / l = 0.8$ 的条件下，当 $l / \Delta = 1$ 时， $\sigma_{X} / l = 1.0$ 时的 $\overline{Y} / \overline{X}$ 等于 $\sigma_{X} / l = 0$ 时的 0.94 倍；而当 $l / \Delta = 2$ 时， $\sigma_{X} / l = 1.0$ 时的 $\overline{Y} / \overline{X}$ 等于 $\sigma_{X} / l = 0$ 时的 0.84 倍。如果在 $l / \Delta$ 增大时，闭合回路中的放大系数 $K_{1}K_{2}\frac{l}{\Delta}$ 不变，那么这种“失效”现象更为急剧。在 $\alpha T = 0.1$

$K_{1}K_{2}\frac{l}{\Delta}=1,\overline{X}/l=0.8$ 的条件下，当 $l/\Delta=2$ 时， $\sigma_{X}/l=1.0$ 时的 $\overline{Y}/\overline{X}$ 等于 $\sigma_{X}/l=0$ 时的 0.64 倍。

> 此处省略原书 **图 14.11-9**

统计线性化方法在原则上也可以推广到变系数非线性系统和非平稳随机输入的情况。这时，等效放大系数就不是待定常数，而是与输入的相关函数、数学期望有关的待定时间函数了。

#### 14.12 离散系统对随机输入的反应

前几节讨论的都是连续系统对随机输入的反应。在很多离散控制系统中，它的输入也含有严重的随机干扰。例如，脉冲雷达的距离跟踪系统和角跟踪系统都是离散控制系统，它的输入作用是从目标反射回来的脉冲回波，除了真正代表目标位置的信号外，还夹杂了很多随机噪声和干扰。下面我们就来分析一下最简单的离散系统——线性常系数离散系统对随机输入的反应。

在第十章我们已经谈到，如果离散系统内的连续部分是线性常系数系统的，采样元件是脉冲线性调幅元件（它的输出是宽度相同、相位相同的矩形脉冲，每一个采样周期的脉冲幅度与采样时刻脉冲元件输入值成正比关系),那么此离散系统也是线性常系数的。线性常系数离散系统的运动规律是用线性常系数差分方程组来描述的，在一般情况下它是

$$
\mathbf {y} _ {n + 1 + \epsilon} = D \mathbf {y} _ {n + \epsilon} + B _ {1} \mathbf {x} _ {n} + B _ {2} \mathbf {x} _ {n + 1} \tag {14.12-1}
$$

其中 $y_{n+\varepsilon}$ 是 $y(t)$ 在 $t=(n+\varepsilon)T$ 时刻的值， $x_{n}$ 是 $x(t)$ 在 t=nT 时刻的值。 $\varepsilon T$ 表示状态取值延迟于采样时刻的时间， $1>\varepsilon\geqslant0$ ，如果 $\varepsilon=0$ ，就表示在采样时刻取值。设 x 是 m 维向量，代表系统的输入。y 是 n 维向量，代表系统的状态，它的某几个 分量是系统的输出。D 是 $n \times n$ 阶常方阵，如果它的特征值都在复平面上的单位圆内，则此采样系统是稳定的。 $B_{1}$ 和 $B_{2}$ 都是 $n \times m$ 阶常矩阵，它们都随 $\varepsilon$ 不同而不同。假设输入作用在 $t = -\infty$ 时就加入到系统里去了，而且系统又是稳定的，那么在 $nT + \varepsilon T$ 时刻系统的状态就为

$$
\mathbf {y} _ {n + \epsilon} = \sum_ {k = 0} ^ {\infty} D ^ {k} B _ {1} \mathbf {x} _ {n - 1 - k} + \sum_ {k = 0} ^ {\infty} D ^ {k} B _ {2} \mathbf {x} _ {n - k} \tag {14.12-2}
$$

我们令

$$
H _ {e} ^ {*} [ k T ] = \left\{ \begin{array}{l l} 0, & k <   0 \\ B _ {2}, & k = 0 \\ D ^ {k} B _ {2} + D ^ {k - 1} B _ {1}, & k = 1, 2, \dots \end{array} \right. \tag {14.12-3}
$$

那么等式(14.12-2)就成为

$$
\mathbf {y} _ {n + \varepsilon} = \sum_ {k = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ k T ] \mathbf {x} _ {n - k} \tag {14.12-4}
$$

显然， $H_{\epsilon}^{*}[kT]$ 是 $n\times m$ 阶函数矩阵，它相当于离散系统的脉冲过渡函数。可以看出 $y_{n+\epsilon}$ 是输入作用 $x_{n}$ 的线性变换。

如果输入作用是平稳随机序列 $\{\mathbf{X}_n\}$ 那么系统的状态 $\{\mathbf{Y}_{n + \varepsilon}\}$ 也是随机序列，其中

$$
\mathbf {Y} _ {n + \epsilon} = \sum_ {k = 0} ^ {\infty} H _ {\epsilon} ^ {*} [ k T ] \mathbf {X} _ {n - k} \tag {14.12-5}
$$

根据随机函数线性变换的特性我们可以算出 $Y_{n + \varepsilon}$ 的数学期望和自相关函数矩阵：

$$
\overline {{{\mathbf {Y} _ {n + \varepsilon}}}} = \left[ \sum_ {k = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ k T ] \right] \overline {{{\mathbf {X} _ {n}}}} \tag {14.12-6}
$$

$$
\begin{array}{l} R _ {Y} [ n + k + \varepsilon , n + \varepsilon ] = \left\langle Y _ {n + k + \varepsilon}, Y _ {n + \varepsilon} \right\rangle \\ = \sum_ {l = 0} ^ {\infty} \sum_ {m = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ l T ] R x [ k - l + m ] (H _ {\varepsilon} ^ {*} [ m T ]) ^ {\tau} \\ = R _ {Y} [ k ] \tag {14.12-7} \\ \end{array}
$$

$\overline{Y_{n+\varepsilon}}$ 是与 n 无关的常矩阵（当 $\varepsilon$ 不同时, 它是不同的), $R_{\nu}[n+k+\varepsilon,n+\varepsilon]$ 只与 k 有关, 所以 $\{Y_{n+\varepsilon}\}$ 是平稳随机序列。系统的状态与输入之间的互相关函数矩阵是

$$
\begin{array}{l} R _ {Y X} [ n + k + \varepsilon , n ] = \left\langle Y _ {n + k + \varepsilon}, X _ {n} \right\rangle \\ = \sum_ {l = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ l T ] R _ {X} [ k - l ] = R _ {Y X} [ k ] \tag {14.12-8} \\ \end{array}
$$

所以它们是平稳相关的。

根据相关函数和功率谱密度的关系式(14.5-25)和(14.5-26)可得到

$$
\Phi_ {Y \varepsilon} (\omega) = \frac {1}{\pi} \sum_ {k = - \infty} ^ {\infty} R _ {Y} [ k ] e ^ {- i \omega k T}
$$

$$
\begin{array}{l} = \frac {1}{\pi} \sum_ {l = 0} ^ {\infty} \sum_ {k = - \infty} ^ {\infty} \sum_ {m = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ l T ] e ^ {- i \omega l T} R _ {x} [ k - l + m ] e ^ {- i \omega (k - l + m) T} \left(H _ {\varepsilon} ^ {*} [ m T ]\right) ^ {\tau} e ^ {i \omega m T} \\ = \boldsymbol {F} _ {\varepsilon} ^ {*} (i \omega) \Phi_ {X} (\omega) \left[ \boldsymbol {F} _ {\varepsilon} ^ {*} (i \omega) \right] ^ {\tau} \tag {14.12-9} \\ \end{array}
$$

$$
\Phi_ {Y X \varepsilon} (\omega) = \frac {1}{\pi} \sum_ {k = - \infty} ^ {\infty} R _ {Y} [ k ] e ^ {- i \omega k T}
$$

$$
= \frac {1}{\pi} \sum_ {l = 0} ^ {\infty} \sum_ {k = - \infty} ^ {\infty} H _ {\varepsilon} ^ {*} [ l T ] e ^ {- i \omega l T} R _ {X} [ k - l ] e ^ {- i \omega (k - l) T}
$$

$$
= \boldsymbol {F} _ {\varepsilon} ^ {*} (i \omega) \Phi_ {X} (\omega) \tag {14.12-10}
$$

其中

$$
\boldsymbol {F} _ {\varepsilon} ^ {*} (i \omega) = \sum_ {l = 0} ^ {\infty} H _ {\varepsilon} ^ {*} [ l T ] e ^ {- i \omega l T} \tag {14.12-11}
$$

就是离散系统式(14.12-1)的离散频率特性矩阵。同样，等式(14.12-6)可以改写为

$$
\overline {{{\mathbf {Y} _ {n + \varepsilon}}}} = \boldsymbol {F} _ {\varepsilon} ^ {*} (0) \overline {{{\boldsymbol {X} _ {n}}}} \tag {14.12-12}
$$

假设离散控制系统只有一个输出 y 和一个输入 x，它的运动规律是用线性常系数高阶差分方程来表示的

$$
a _ {0} y _ {n + l} + a _ {1} y _ {n + l - 1} + \dots + a _ {l} y _ {n} = b _ {0} x _ {n + m} + b _ {1} x _ {n + m - 1} + \dots + b _ {m} x _ {n}, \quad m \leqslant l \tag {14.12-13}
$$

假设系统是稳定的，并在 $t=-\infty$ 时就开始给系统加入一个平稳的随机系列，那么系统的输出输入关系就是

$$
a _ {0} Y _ {n + l} + a _ {1} Y _ {n + l - 1} + \dots + a _ {l} Y _ {n} = b _ {0} X _ {n + m} + b _ {1} X _ {n + m - 1} + \dots + b _ {m} X _ {n}, \quad m \leqslant l \tag {14.12-14}
$$

根据前面所述，我们已经知道输出 $\{Y_{n}\}$ 也是平稳随机序列。根据第 14.8 节的随机函数线性变换的特性式(14.8-17),我们求方程(14.12-14)两边的功率谱密度，就可以得到

$$
\left| a _ {0} e ^ {i \omega l} + a _ {1} e ^ {i \omega (l - 1)} + \dots + a _ {l} \right| ^ {2} \Phi_ {Y} (\omega) = \left| b _ {0} e ^ {i \omega m} + b _ {1} e ^ {i \omega (m - 1)} + \dots + b _ {m} \right| ^ {2} \Phi_ {X} (\omega)
$$

于是，输出与输入功率谱密度之间的关系是

$$
\Phi_ {Y} (\omega) = \left| \frac {b _ {0} e ^ {i \omega m} + b _ {1} e ^ {i \omega (m - 1)} + \cdots + b _ {m}}{a _ {0} e ^ {i \omega l} + a _ {1} e ^ {i \omega (l - 1)} + \cdots + a _ {l}} \right| ^ {2} \Phi_ {X} (\omega) \tag {14.12-15}
$$

由此可得离散系统式(14.12-13)的 $\varepsilon$ 为零的离散频率特性

$$
F _ {\varepsilon = 0} ^ {*} (i \omega) = \frac {b _ {0} e ^ {i \omega m} + b _ {1} e ^ {i \omega (m - 1)} + \cdots + b _ {m}}{a _ {0} e ^ {i \omega l} + a _ {1} e ^ {i \omega (l - 1)} + \cdots + a _ {l}} \tag {14.12-16}
$$

这正好与我们以前的概念相符合。

线性变系数离散系统和非线性离散系统对随机输入的反应的分析方法与连续系统的分析方法相类似，我们在这里就不再赘述了。

#### 14.13 平稳输入时控制系统的设计举例

在第 14.9 节里, 我们曾讨论了二阶系统对于随机输入的反应, 在那里的讨论中已经说明了用反馈控制来改进系统性能的可能性。但是, 在那个例子里反馈机构是相当原始的, 因为进行反馈控制作用所需要的力的数量级与输入驱动函数的数量级相同。在一个更实际的设计中, 我们可以把反馈机构设计得更巧妙一些, 使得反馈作用所需要的力减少很多。例如, 可以用反馈伺服机构带动可以转动的附加翼片, 从而控制湍流中的机翼的运动。转动翼片所需要的力与机翼运动所引起的空气动力效应（升力、阻力、转矩等）相比较, 可以小得很多。我们可以把这个控制系统的方框图想象为图 14.13-1 的情形。输入的随机函数 X 是扰动气流。输出 Y 就是机翼的位移。第一个传递函数 $F_{1}(s)$ 表示扰动气流和这个气流所引起的升力之间的关系。升力与转矩变化的结果, 就使得机翼产生垂直方向的运动和旋转运动。这些由于空气动力的原因所产生的外力与机翼运动之间的关系是由结构的传递函数 $F_{2}(s)$ 所描述的。机翼的运动又要产生两种作用。机翼的运动通过第二个空气动力学的传递函数 $F_{3}(s)$ 又产生空气动力。这是第一个反馈线路, 然而, 这个反馈线路不是设计者所能任意改动的。设计者能够处理的是第二个反馈线路。机翼的运动可以用来控制襟翼的运动, 假设这一部分的传递函数是 $F_{4}(s)$ 。襟翼的运动通过传递函数 $F_{5}(s)$ 又产生空气动力。所以输入与输出之间的关系就是

> 此处省略原书 **图 14.13-1**

$$
\mathbf {Y} (s) = F _ {2} (s) \left[ F _ {1} (s) \mathbf {X} (s) + F _ {3} \mathbf {Y} (s) + F _ {5} (s) F _ {4} (s) \mathbf {Y} (s) \right]
$$

或者

$$
\frac {\mathbf {Y} (s)}{\mathbf {X} (s)} = F _ {s} (s) = \frac {F _ {1} (s) F _ {2} (s)}{1 - F _ {2} (s) \left[ F _ {3} (s) + F _ {5} (s) F _ {4} (s) \right]} \tag {14.13-1}
$$

所以，改动伺服机构的传递函数 $F_{4}(s)$ 就可以使系统的总传递函数得到改善。

如果 $\Phi_{X}(\omega)$ 是输入 X 的功率谱密度, $\Phi_{Y}(\omega)$ 是输出 Y 的功率谱密度, 那么按照方程(14.8-13)

$$
\Phi_ {Y} (\omega) = \Phi_ {X} (\omega) F _ {s} (i \omega) F _ {s} (- i \omega) \tag {14.13-2}
$$

这里的 $F_{s}(s)$ 是由方程(14.13-1)给定的。完全可以想到，如果希望飞机里的乘客得到最大的安适，我们就必须使加速度 $\frac{d^{2}}{dt^{2}}Y(t)$ 尽可能地小，这也就意味着 $\left[\frac{d^{2}}{dt^{2}}Y(t)\right]^{2}$ 取极小值。因为

$$
\overline {{{X ^ {2} (t)}}} = \sigma_ {X} ^ {2} (t) + [ \overline {{{X (t)}}} ] ^ {2}
$$

所以在相同的方差下，数学期望 $\left[\frac{d^2}{dt^2} Y(t)\right]$ 等于零可使 $\left[\frac{d^2}{dt^2} Y(t)\right]^2$ 取极小。因此要求 $\left[\frac{d^2}{dt^2} Y(t)\right]^2$ 取极小也意味着要求 $\overline{\frac{d^2}{dt^2}Y(t)}$ 等于零，同时还要 $\frac{d^2}{dt^2} Y(t)$ 的方差 $\sigma_{\ddot{Y}}^{2}$ 取极小。根据方差与功率谱密度的关系和导数的功率谱的表示式就可得出

$$
\sigma_ {Y} ^ {2} = \int_ {0} ^ {\infty} \omega^ {4} \left| \frac {F _ {1} (i \omega) F _ {2} (i \omega)}{1 - F _ {2} (i \omega) \left[ F _ {3} (i \omega) + F _ {5} (i \omega) F _ {4} (i \omega) \right]} \right| ^ {2} \Phi_ {X} (\omega) d \omega \tag {14.13-3}
$$

因为 $F_{1}(s), F_{2}(s), F_{3}(s)$ 和 $F_{5}(s)$ 都已经固定下来了，不能加以改变，所以我们只能用改变传递函数 $F_{4}(s)$ 的方法使 $\sigma_{Y}^{2}$ 达到极小值。可以采用下列做法：先作出一个传递函数 $F_{4}(s)$ ，但暂时先不确定其中的参数数值；根据式(14.13-3)就可以把 $\sigma_{Y}^{2}$ 计算出来，结果中包含 $F_{4}(s)$ 的未定参数；再用普通求极小值的方法确定使 $\sigma_{Y}^{2}$ 取极小的参数。这样确定的 $F_{4}(s)$ 就是使乘客最舒适的伺服机构的传递函数。必须指出，在此方法中， $F_{4}(s)$ 的基本形式还是由设计者根据某些实际情况和经验相当随意地选定的，只是某些参数尚未确定而已。所以上面得到的极小值并不一定是真正能够达到的极小值。因为，如果把 $F_{4}(s)$ 的基本形式加以改变，还是用同样的计算方法就可能得出一个更好的结果。所以，如果希望得到更好的结果，还必须研究 $F_{4}(s)$ 应是哪一种形式的函数问题，这一个问题可以用最优化的方法解决。在下一章中我们还要讨论。对于特定的输入条件，设计目的不一样时，所得到的 $F_{4}(s)$ 的形式即使是同一个形式，但参数也可能不同，甚至相差甚远。某些参数对这个设计目的来说是比较好的，但对另一个设计目的来说，可能是极不好的。这就是下一章要讨论的控制系统在随机输入下的综合问题。

#### 14.14 参考文献

[1] 复旦大学数学系编, 概率论与数理统计（第二版), 上海科技出版社, 1961.

[2] 王寿仁, 关于广义随机过程的一个注记, 科学记录, 新辑 2(1958), 1.15-18.

[3] 郑绍濂, 多维平稳随机过程的谱分解, 复旦大学学报, 2(1960).

[4] 冯康, 广义函数论, 数学进展, 1(1955), 3.

[5] 关肇直, 泛函分析讲义, 高等教育出版社, 1958.

[6] Bendat, J. S., Principles and Application of Random Noise Theory, John Wiley & Sons. Inc., New York, 1958.

[7] Booton, R. C., Nonlinear control system with random inputs IRE Trans., CT-1(1954), 1.

[8] Cranér, H., Mathematical Methods of Statistics, Princeton University Press, Princeton, New Jersey, 1946. (统计学的数学方法, 魏宗舒等译, 上海科技出版社, 1966.)

[9] Duncan, D. B., Response of time-dependent systems to random inputs. J. Appl. Phys., 24 (1953), May, 609–611.

[10] Grenader, U., Rosenblatt, M., Statistical Analysis of Stationary Time Series, John Wiley & Sons, Inc., 1957. (平稳时间序列的统计分析, 郑绍濂等译, 上海科技出版社, 1962.)

[11] James, H. F., Nichols, N. B., & Phillips, R. S., Theory of Servomechanisms, Chap. 7, MIT Radiation Laboratory Series Vol. 25, McGraw-Hill Company, Inc., New York, 1947.

[12] Karhunun, K., Über lineare methoden in der wahrscheinlichkeitsrechnung, Ann. Acad. Sci. Fennical A.I. Math-Phy., 37, 1947, 1—79.

[13] Von Kárman, Howarth. On the statistical theory of isotropic turbulence, Proc. Roy. Soc. (A), 164(1938), 192.

[14] Laning, J. H., Battin, R. H., Random Processes in Automatic Control, McGraw-Hill Book Co., Ins., New York. 1956. (自动控制中的随机过程, 涂其例译, 科学出版社, 1963.)

[15] Liepmann, H. W., On the application of statistical concepts to the buffeting problem, J. Aeronaut. Science, 19(1952), 793—801.

[16] Papoulis, A., Probability, Random Variables and Stochastic Processes, McGraw-Hill Book Co., New York, 1965.

[17] Pelegrin, M.J., Calcul Statistique des Systèmes Asservis, Paris, 1953. (随动系统的统计计算, 涂其例译, 科学出版社, 1960.)

[18] Rice, S. O., Mathematical analysis of random noise, Bell system Tech. J., 23(1944), July, 282–332, 24(1945), Jan., 46–156.

[19] Vowels. R. E., The application of statistical methods to servomechanisms, Australian J. Appl. Science, 4(1953), 469–488.

[20] Батков, А. М., Обобщение метода формирующих фильтров на Нестационарные процессы, AuT, 20(1959), 8.

[21] Бернштейн, С. Н., Распространение предельной теоремы теории вероятностей на суммы зависимых случайных величин, Успехи Mat. Наук, вып. 10(1944), 55—114.

[22] Гельфонд, И. М. Обощенные случайные процессы, ДАН СССР, 100(1955), 5, 852—856.

[23] Доступов, Б. Г. Приближенное определение вероятностых характеристик выходных координат нелинейных систем Автоматического ретулирования, AuT, 18(1957), 11.

[24] Казаков, И. Е., Приближенный вероятностный анализ точность работы существенно нелинейных автоматических систем, AuT, 17(1956), 5.

[25] Колмогоров, А. Н., 1) Аналитические методы в теории вероятностей, Успеху Mat. Наук,

Вып, v (1938), 5–41.2) Стационарные последовательности в Гильбертовом прострасте, БЮЛЛ. МТУ, 2(1941), 6, 1–40.

[26] Пугачев, В.С., Теория Случайных Процессов и её Применение к Задачам Автоматического Управления, Издание Второе, Физматгиз, 1960. (随机过程理论及其在自动控制中的应用, 田欣为等译, 科学出版社, 1966.)

[27] Пупков, К. А., Метод исследования точность существенно помощи эквивалентной передаточной функций, AuT, 21, (1960), 2.

[28] Яглом А.М., Введение в теории стационарных случайных функций, Уснехи Мат. Наук, 7 (1952), 5. (平衡随机函数引论, 梁之舜译, 数学进展, 2(1952), 1.)
