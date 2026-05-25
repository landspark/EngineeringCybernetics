# 工程控制论（下册）

（第三版）

钱学森 宋健 著

## 正文（015）

### 第十五章 噪声过滤的设计原理

上一章讨论了在随机输入作用下控制系统的分析问题，这一章将讨论有随机输入作用时控制系统的综合问题。这里控制系统没有完全给定，可能是已给定了系统的结构形式，但是某些参数并没有确定；也可能是连系统的结构形式都没有给定。综合就是要根据已知的系统输入特性，系统的结构形式，对系统输出的要求等来设计控制系统使它具有优良的性能。一般是从准确度的观点来看系统的性能的。例如，要求设计一个随动系统，它的输出应很准确地复现输入中的有用信号，因为输入中除了有用信号外还夹杂着各种各样的噪声。又例如，要设计一个接收机，它能很准确地判断在强烈的噪声中有无微弱信号的存在，并能准确地估计信号的某些参数。这些系统的综合都是要把输入中的有用信号与噪声分离开来，使信号尽量少受噪声的影响，所以这里谈的综合问题通常可以化为噪声过滤的问题。

#### 15.1 噪声过滤的均方误差

我们先来讨论信号的复现问题。假定过滤器的输入观测值 $x(t)$ 是有用信号 $f(t)$ 和噪声 $n(t)$ 的叠加

$$
x (t) = f (t) + n (t) \tag {15.1-1}
$$

> 此处省略原书 **图 15.1-1**

过滤器的输出是 $y(t)$ ，如图 15.1-1 所示。有用信号和噪声可能是随机的，也可能是非随机的。有用信号的特性与噪声的特性总是有一定的差异，一般说来，有用信号 $f(t)$ 变化比较缓慢，噪声 $n(t)$ 变化比较剧烈。过滤器是这样一种系统：它能够更多地让有用信号通过而一定程度 地阻止噪声的通过，使得输出 $y(t)$ 较多地与输入中的有用信号 $f(t)$ 有关，与噪声 $n(t)$ 有尽量少的联系。过滤器的作用就是在一定程度上过滤掉噪声，正是由于有用信号和噪声的特性的差异，才使过滤器的作用在一定程度上能够实现。

对于最简单的信号复现问题要求输出 $y(t)$ 尽可能地复现输入中的有用信号 $f(t)$ ，这时理想的输出 $y_{1}(t)$ 就等于 $f(t)$ 。有时，在一般的信号复现问题中要求输出 $y(t)$ 能复现有用信号 $f(t)$ 的某种变换，例如 $f(t)$ 的一阶导数或高阶导数，在 $\sigma$ 时刻后 的 $f(t)$ 的值或它的导数的值等, 这时过滤器的理想输出 $y_{1}(t)$ 不等于 $f(t)$ 而是

$$
y _ {1} (t) = \int_ {- \infty} ^ {\infty} h _ {1} (t - u) f (u) d u = \int_ {- \infty} ^ {\infty} h _ {1} (\sigma) f (t - \sigma) d \sigma \tag {15.1-2}
$$

式中 $h_1(t)$ 是定义于 $(-\infty, \infty)$ 上的某一给定的绝对可积函数或为 $\delta$ 函数及其高阶导数。

假定过滤器已经给定，它是一个线性常系数系统，传递函数是 $F(s)$ , 脉冲响应函数是 $h(t)$ 。当然, 过滤器应该是一个稳定的系统, 即 $F(s)$ 的极点都在复数 s 的左半平面上, 故 $F(s)$ 与 $h(t)$ 之间可用傅里叶变换式联系起来

$$
h (t) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {i \omega t} F (i \omega) d \omega \tag {15.1-3}
$$

在一般情况下， $F(s)$ 是 s 的有理分式，且分子多项式幂次比分母多项式幂次低，那么当 t<0 时 $h(t)=0$ 。当输入作用 $x(t)$ 加至过滤器输入端后，过滤器的输出信号将是

$$
y (t) = \int_ {- \infty} ^ {t} x (u) h (t - u) d u
$$

这里假定输入作用是从 $t = -\infty$ 开始的。根据卷积公式的对称性，令 $t - u = \sigma$ 就有

$$
y (t) = \int_ {0} ^ {\infty} h (\sigma) x (t - \sigma) d \sigma \tag {15.1-4}
$$

既然过滤器已经给定，一般来讲它的输出 $y(t)$ 与理想的输出 $y_{1}(t)$ 是不同的。 $y(t)$ 与 $y_{1}(t)$ 之差就是误差 $e(t)$ , 根据方程(15.1-2)和(15.1-4)有

$$
e (t) = y _ {1} (t) - y (t) = \int_ {- \infty} ^ {\infty} \left\{f (t - \sigma) h _ {1} (\sigma) \right.
$$

$$
- \left[ f (t - \sigma) + n (t - \sigma) \right] h (\sigma) \} d \sigma \tag {15.1-5}
$$

误差的平方是

$$
\begin{array}{l} e ^ {2} (t) = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} \left\{f (t - \sigma) h _ {1} (\sigma) - [ f (t - \sigma) + n (t - \sigma) ] h (\sigma) \right\} \\ \times \left\{f (t - u) h _ {1} (u) - [ f (t - u) + n (t - u) ] h (u) \right\} d \sigma d u \tag {15.1-6} \\ \end{array}
$$

在许多信号复现的问题中噪声是随机函数，我们用 $N(t)$ 来表示；同时信号的特性我们也不能确切预知，只能知道它的统计特性，例如，随动系统的输入有用信号常常是无法确切预知的，我们在这里也假设它是随机的，用 $F(t)$ 表示。这时方程(15.1-2),(15.1-4),(15.1-5)和(15.1-6)中的积分都是随机积分，观测值，理想输出，实际输出和误差也都是随机函数，分别用 $X(t), Y_{1}(t), Y(t)$ 和 $E(t)$ 来表示。如果 $F(t), N(t)$ 的统计特性已知，则根据式(15.1-6)可以求出 $E^{2}(t)$ 的数学期望（系集平均值),它叫做均方误差。通常这个值是一个时间函数。

如果假设 $F(t)$ ， $N(t)$ 都是平稳随机过程，而且它们之间是平稳相关的，那么 $\overline{E^{2}}$ （本章用“—”表示数学期望）与时间 t 无关。如果 $F(t)$ 和 $N(t)$ 的数学期望都等于零，那么很明显，此时误差 $E(t)$ 的数学期望也为零。这时，均方误差 $\overline{E^{2}}$ 就是误差

$E(t)$ 的方差 $\sigma_{E}^{2}$ 。设 $F(t)$ ， $N(t)$ 是平稳相关的平稳实随机过程，因此它们的自相关函数 $r_{F}(\lambda)$ ， $r_{N}(\lambda)$ 都是偶函数，互相关函数则满足下列关系

$$
r _ {F N} (\lambda) = r _ {N F} (- \lambda) \tag {15.1-7}
$$

这时的均方误差为

$$
\begin{array}{l} \overline {{{E ^ {2}}}} = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} \left\{r _ {F} (\sigma - u) [ h _ {1} (\sigma) - h (\sigma) ] [ h _ {1} (u) - h (u) ] \right. \\ - r _ {F N} (\sigma - u) \left[ h _ {1} (\sigma) - h (\sigma) \right] h (u) - r _ {N F} (\sigma - u) h (\sigma) \left[ h _ {1} (u) - h (u) \right] \\ + r _ {N} (\sigma - u) h (\sigma) h (u) \} d \sigma d u \tag {15.1-8} \\ \end{array}
$$

现在来找均方误差和信号，噪声的功率谱密度的关系。在上一章中已谈到功率谱密度与相关函数的关系是

$$
\Phi (\omega) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} r (\lambda) e ^ {- i \omega \lambda} d \lambda \tag {15.1-9}
$$

可以看出实平稳随机过程的自功率谱密度 $\Phi_{F}(\omega)$ , $\Phi_{N}(\omega)$ 是偶函数, 平稳相关的互功率谱密度根据式(15.1-7)有

$$
\Phi_ {F N} (\omega) = \Phi_ {N F} (- \omega) \tag {15.1-10}
$$

相关函数可以表示为

$$
r (\lambda) = \frac {1}{2} \int_ {- \infty} ^ {\infty} \Phi (\omega) e ^ {i \omega \lambda} d \omega \tag {15.1-11}
$$

根据前面对 $h_1(t), h(t)$ 的假定可以得到 $h_1(t)$ 的傅里叶变换

$$
F _ {1} (i \omega) = \int_ {- \infty} ^ {\infty} h _ {1} (t) e ^ {- i \omega t} d t \tag {15.1-12}
$$

和过滤器的频率特性

$$
F (i \omega) = \int_ {- \infty} ^ {\infty} h (t) e ^ {- i \omega t} d t = \int_ {0} ^ {\infty} h (t) e ^ {- i \omega t} d t \tag {15.1-13}
$$

利用公式(15.1-11)，(15.1-12)和(15.1-13)可以将方程(15.1-8)化简，最后得到

$$
\begin{array}{l} \overline {{E ^ {2}}} = \sigma_ {E} ^ {2} \\ = \frac {1}{2} \int_ {- \infty} ^ {\infty} \left\{\Phi_ {F} (\omega) \left[ F _ {1} (i \omega) - F (i \omega) \right] \left[ F _ {1} (- i \omega) - F (- i \omega) \right] \right. \\ - \Phi_ {F N} (\omega) [ F _ {1} (i \omega) - F (i \omega) ] F (- i \omega) - \Phi_ {N F} (\omega) F (i \omega) [ F _ {1} (- i \omega) \\ \left. - F (i \omega) \right] + \Phi_ {N} (\omega) F (i \omega) F (- i \omega) \} d \omega \tag {15.1-14} \\ \end{array}
$$

式中大括号{}内的表示式就是误差的功率谱密度 $\Phi_{E}(\omega)$ 。根据第 14.5 节所述，被积函数的最后一项实际上就是噪声通过过滤器 $F(s)$ 后输出的功率谱密度，被积函数的第一项是由于过滤器的实际性能与理想性能差异而产生有用信号的误差功率谱密度。显然第一项和最后一项是 $\omega$ 的实函数。如果信号与噪声是平稳相关的，那么被积函数的第二项和第三项是 $\omega$ 的复函数，但由于满足等式(15.1-10)，此二项是复共轭的，相加以后仍为实数，此二项是由于有用信 号和噪声相关而引起的均方误差。当信号和噪声互不相关时，均方误差只由第一项和最后一项产生。如果 $F_{1}(i\omega)$ 是某一个真实的稳定系统的频率特性，那么当 $F(i\omega)=F_{1}(i\omega)$ 时，误差就只由噪声通过过滤器 $F(i\omega)$ 后输出的功率谱密度产生。一般来说， $F_{1}(i\omega)$ 的通频带较宽，也就是在较大的 $\omega$ 值以后 $F_{1}(i\omega)$ 才趋近于零，那么即使 $F(i\omega)=F_{1}(i\omega)$ ，信号本身不产生误差，但是总的均方误差仍较大。如果选用通频带很窄的过滤器，即 $F(i\omega)$ 在不大的 $\omega$ 值以后就很快地趋于零，那么由噪声产生的误差将是很小的，但由于过滤器实际性能和理想性能差异很大因而信号本身产生的均方误差较大，总的均方误差仍然较大。从这里可以看出，如果过滤器的设计准则是使均方误差最小，那么应该选择一个适当的过滤器，它的通频带既不太宽，又和理想特性差异不太大。我们将在下面几节中讨论这种过滤器的设计。

#### 15.2 待定系数的最优过滤器设计原理

如果信号和噪声的统计特性和理想传递函数 $F_{1}(s)$ 已经给定，那么式(15.1-14)的均方误差中只有过滤器的传递函数 $F(s)$ 是没有确定的。设计使均方误差最小的最优过滤器的一种方法就是先假定过滤器的传递函数 $F(s)$ 取某种合适的形式，但是含有某些待定的参数。于是均方误差就是这些待定参数的某个确定函数。最后再根据均方误差最小的要求来确定这些参数的最优值。最优过滤器的设计问题就化成一个求已知函数的极值问题。菲利普斯(Phillips)假设最优过滤器的传递函数 $F(s)$ 是 $s$ 的有理分式，解决了这种最优过滤器的设计问题[15]。这的确是很自然的一种选择方法。因为我们知道线性常系数系统的传递函数就是 $s$ 的有理分式。

由于平稳随机过程的功率谱密度 $\Phi (\omega)$ 常有 $\Phi (\omega) = \Psi (i\omega)\Psi (-i\omega)$ 的形式，其中 $\Psi (i\omega)$ 也是 $i\omega$ 的有理分式，它的极点和零点都在复平面 $\omega$ 的上半平面。既然 $F(s)$ 是稳定的， $F(i\omega)$ 的极点都在复平面 $\omega$ 的上半平面，根据式(15.1-14)，均方误差 $\overline{E^2}$ 总可表示为

$$
\overline {{{E ^ {2}}}} = \frac {1}{2} \int_ {- \infty} ^ {\infty} \frac {g _ {n} (\omega)}{h _ {n} (\omega) h _ {n} (- \omega)} d \omega \tag {15.2-1}
$$

其中 $h_n(\omega)$ 和 $g_{n}(\omega)$ 的系数或是实数或是纯虚数的多项式

$$
h _ {n} (\omega) = a _ {0} \omega^ {n} + a _ {1} \omega^ {n - 1} + \dots + a _ {n} \tag {15.2-2}
$$

$$
g _ {n} (\omega) = b _ {0} \omega^ {2 n - 2} + b _ {1} \omega^ {2 n - 4} + \dots + b _ {n - 1} \tag {15.2-3}
$$

而且 $h_{n}(\omega)$ 的零点全在复平面 $\omega$ 的上半平面。

我们令

$$
I _ {n} = \frac {1}{2 \pi i} \int_ {- \infty} ^ {\infty} \frac {g _ {n} (x)}{h _ {n} (x) h _ {n} (- x)} d x \tag {15.2-4}
$$

那么均方误差

$$
\overline {{E ^ {2}}} = \pi i I _ {n}
$$

$I_{n}$ 与各系数 $a_{i}, b_{i}$ 的关系可见表 15.2-1。因此，在这种假设下我们求出了均方误差 $\overline{E^{2}}$ 的表达式，它是某些待定参数的函数。这样，我们就可以利用求多变量函数的极值方法求出待定参数的最优值。

表 15.2-1 积分值 $I_{n}$ 与 $g_{n}(x)$ 和 $h_{n}(x)$ 式内诸系数的关系

$$
I _ {1} = \frac {b _ {0}}{2 a _ {0} 0 a _ {1}}
$$

$$
I _ {2} = \frac {- b _ {0} + \frac {a _ {0} b _ {1}}{a _ {2}}}{2 a _ {0} a _ {1}}
$$

$$
I _ {3} = \frac {- a _ {2} b _ {0} + a _ {0} b _ {1} - \frac {a _ {0} a _ {1} b _ {2}}{a _ {3}}}{2 a _ {0} (a _ {0} a _ {3} - a _ {1} a _ {2})}
$$

$$
I _ {4} = \frac {b _ {0} (- a _ {1} a _ {4} + a _ {2} a _ {3}) - a _ {0} a _ {3} b _ {1} + a _ {0} a _ {1} b _ {2} + \frac {a _ {0} b _ {3}}{a _ {4}} (a _ {0} a _ {3} - a _ {1} a _ {2})}{2 a _ {0} (a _ {0} a _ {3} ^ {2} + a _ {1} ^ {2} a _ {4} - a _ {1} a _ {2} a _ {3})}
$$

$$
I _ {5} = \frac {M _ {5}}{2 a _ {0} \Delta_ {5}}
$$

$$
M _ {5} = b _ {0} \left(- a _ {0} a _ {4} a _ {5} + a _ {1} a _ {4} ^ {2} + a _ {2} ^ {2} a _ {5} - a _ {2} a _ {3} a _ {4}\right) + a _ {0} b _ {1} \left(- a _ {2} a _ {5} + a _ {3} a _ {4}\right)
$$

$$
+ a _ {0} b _ {2} \left(a _ {0} a _ {5} - a _ {1} a _ {4}\right) + a _ {0} b _ {3} \left(- a _ {0} a _ {3} - a _ {1} a _ {2}\right)
$$

$$
+ \frac {a _ {0} b _ {4}}{a _ {5}} (- a _ {0} a _ {1} a _ {5} + a _ {0} a _ {3} ^ {2} + a _ {1} ^ {2} a _ {4} - a _ {1} a _ {2} a _ {3})
$$

$$
\Delta_ {5} = a _ {0} ^ {2} a _ {5} ^ {2} - 2 a _ {0} a _ {1} a _ {4} a _ {5} - a _ {0} a _ {2} a _ {3} a _ {5} + a _ {0} a _ {3} ^ {2} a _ {4} + a _ {1} ^ {2} a _ {4} ^ {2} + a _ {1} a _ {2} ^ {2} a _ {5} - a _ {1} a _ {2} a _ {3} a _ {4}
$$

#### 15.3 最优过滤问题

在上一节中，最小均方误差是在过滤器的传递函数 $F(s)$ 的形式已给定的情况下求出的，在一般情况下，它不是最小的均方误差。现在再来讨论传递函数形式未知并以均方误差最小为准则的最优过滤问题。

先从随机序列的纯预测这样一个具体例子开始。假定预测器的输入只有有用信号而没有噪声。有用信号是一个随机序列 $F[t_{k}]$ ，我们以后简记为 $F_{k}$ 。对每一个任意给定的时刻 $t_{k}$ ，我们要求根据信号在 $t_{k}$ 时刻以前有限个或无限个时刻的值 $F_{k-1}, F_{k-2}, \cdots, F_{k-n}, \cdots$ 来预测以后某个时刻，例如 $t_{k+l}$ 时刻的有用信号 $F_{k+l}, l \geqslant 0$ 。用此预测值作为预测器的输出 $Y_{k}$ ，也就是预测器在 $t_{k}$ 时刻的输出 $Y_{k}$ 是输入 $F_{k-1}, F_{k-2}, \cdots, F_{k-n}, \cdots$ 等的函数

$$
Y _ {k} = g \left(F _ {k - 1}, F _ {k - 2}, \dots , F _ {k - n}, \dots\right) \tag {15.3-1}
$$

g 叫做纯预测函数。预测器输出 $Y_{k}$ 与被预测值 $F_{k+1}$ 之差叫做预测误差

$$
E _ {k} = F _ {k + l} - Y _ {k} \tag {15.3-2}
$$

它也是个随机序列。如果选择这样的纯预测函数 $\stackrel{\circ}{g}$ 使预测的均方误差在任何时

刻 $t_k$ 都最小，即

$$
\overline {{(\stackrel {\circ} {E} _ {k}) ^ {2}}} = \overline {{(F _ {k + l} - \stackrel {\circ} {Y} _ {k}) ^ {2}}} = \min \overline {{\{(F _ {k + l} - Y _ {k}) ^ {2} \}}} \tag {15.3-3}
$$

则这个预测器叫做最优预测器，这时 $Y_{k}$ 叫做 $F_{k+1}$ 的最优预测, $\dot{g}$ 叫做最优预测函数。当给预测器输入随机序列 $F_{k}$ 的某一个现实 $f_{k}$ 时，它的输出序列 $Y_{k}$ 取值 $y_{k}$

$$
y _ {k} = g \left(f _ {k - 1}, f _ {k - 2}, \dots , f _ {k - n}, \dots\right)
$$

可以证明，由最优预测函数 $\dot{g}$ 确定的最优输出 $\dot{y}_{k}$ 是随机变量 $F_{k+l}$ 在 $F_{k-n}$ , $n=1,2,\cdots$ 取值 $f_{k-n}$ 条件下的条件数学期望，也就是

$$
\mathring {y} _ {k} = \mathring {g} \left(f _ {k - 1}, f _ {k - 2}, \dots\right) = \overline {{\left\{F _ {k + l} \mid F _ {k - n} = f _ {k - n} , n = 1 , 2 , \dots \right\}}} \tag {15.3-4}
$$

事实上，如果随机序列 $F_{k}$ 的联合概率密度存在，均方误差 $\overline{E_{k}^{2}}$ 可表示为

$$
\overline {{{E _ {k} ^ {2}}}} = \iint \dots \int \left(f _ {k + l} - y _ {k}\right) ^ {2} w \left(f _ {k + l}, f _ {k - 1}, f _ {k - 2}, \dots\right) d f _ {k + l} d f _ {k - 1} d f _ {k - 2} \dots \tag {15.3-5}
$$

根据贝叶斯定理，概率密度函数是

$$
w \left(f _ {k + l}, f _ {k - 1}, f _ {k - 2}, \dots\right) = w \left(f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots\right) w \left(f _ {k - 1}, f _ {k - 2}, \dots\right) \tag {15.3-6}
$$

因此

$$
\begin{array}{l} \overline {{{E _ {k} ^ {2}}}} = \int \dots \int \left\{\int \left(f _ {k + l} - y _ {k}\right) ^ {2} w \left(f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots\right) d f _ {k + l} \right\} \\ \times w \left(f _ {k - 1}, f _ {k - 2}, \dots\right) d f _ {k - 1} d f _ {k - 2} \dots \\ \end{array}
$$

现在考虑大括号内的积分, 因 $y_{k}$ 只是 $f_{k-1}, f_{k-2}, \cdots$ 的函数而与 $f_{k+l}$ 无关, 所以

$$
\begin{array}{l} \int \left(f _ {k + l} - y _ {k}\right) ^ {2} w \left(f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots\right) d f _ {k + l} \\ = y _ {k} ^ {2} - 2 y _ {k} \left[ F _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots \right] + \int f _ {k + l} ^ {2} w \left(f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots\right) d f _ {k + l} \\ = \left\{y _ {k} - \overline {{\left[ F _ {k + l} \mid f _ {k - 1} , f _ {k - 2} , \cdots \right]}} \right\} ^ {2} - \overline {{\left[ F _ {k + l} \mid f _ {k - 1} , f _ {k - 2} , \cdots \right]}} \} ^ {2} \\ + \int f _ {k + l} ^ {2} w (f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots) d f _ {k + l} \tag {15.3-7} \\ \end{array}
$$

要使均方误差 $\overline{E_{k}^{2}}$ 最小就要使式(15.3-7)这个正值取最小值。式(15.3-7)中只有第一项与 $y_{k}$ 有关，因此就得出式(15.3-4)。

如果随机序列 $F_{k}$ 是高斯分布的，那么 $F_{k+l}$ 的条件概率分布也是高斯型的。此时 $F_{k+l}$ 的条件数学期望同时又是它的众数（在此值条件概率密度函数取极大值），中值（概率密度函数的中心点）和平方均值，因此用它来作 $F_{k+l}$ 的最优预测是最为恰当的。如果随机序列 $F_{k}$ 不是高斯分布的，那么选择条件数学期望作为 $F_{k+l}$ 的最优预测就没有什么明显理由。

当随机序列 $F_{k}$ 是高斯分布时, 最优预测函数 $\dot{g}$ 一定是线性函数。因为概率

密度函数的形式为

$$
w \left(f _ {k + l}, f _ {k - 1}, f _ {k - 2}, \dots\right) = c \exp \left\{- \frac {1}{2} \sum_ {p, q} b _ {p q} f _ {p} f _ {q} \right\}, p, q = k + l, k - 1, k - 2, \dots
$$

其中 c 和 $b_{p,q}$ 都是常数。随机变量 $F_{k+l}$ 的条件概率密度函数的形式为

$$
w \left(f _ {k + l} \mid f _ {k - 1}, f _ {k - 2}, \dots\right) = c _ {1} \exp \left\{- \frac {1}{2} \left[ b _ {k + l, k + l} f _ {k + l} ^ {2} + 2 \sum_ {n} b _ {k + l, k - n} f _ {k + l} f _ {k - n} \right] \right\}
$$

$c_{1}$ 和 $b_{k+l,k-n}$ 是常数，它是一维高斯分布，条件数学期望与 $f_{k-n}, n=1,2,\cdots$ 呈线性关系，而最优预测就是 $F_{k+l}$ 的条件数学期望，所以 g 是线性函数。当随机序列不是高斯分布时，最优预测函数不一定是线性函数。在实际情况下，我们所遇到的随机函数常常是高斯分布或近于高斯分布的，因此通常只限于求最优线性预测。

能够完全实现准确预测的序列称为奇异序列，这时 $\overline{E_{k}^{2}}=0$ 。例如，由有限个具有互不相关的随机振幅与随机相位的简谐振动之和组成的平稳随机序列信号可以做到预测的均方误差等于零，即知道了序列在过去某些时刻上的值就能以等于 1 的概率去确定它在以后任一时刻上的值。但是一般说来，实际上常遇到的随机序列都不是奇异的，因此即使是最优预测也仍然有误差。

一般来说，最优预测函数 $\dot{g}$ 是与时间有关的。当随机序列是平稳的，而且预测器的输入是 $t_{k}$ 以前无限时刻开始的，那么最优预测函数 $\dot{g}$ 与时间无关。

现在来讨论随机序列的一般最优过滤问题。假定过滤器的输入是观测值 $X_{k}$ ，它是 m 维随机序列，由 n 维有用信号随机序列 $F_{k}$ 和 m 维噪声随机序列 $N_{k}$ 组成

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {N} _ {k} \tag {15.3-8}
$$

其中 $C_{k}$ 是 $m \times n$ 阶非随机矩阵，它是下标 k 的函数。过滤器的理想输出 $Y_{1k}$ 是 $F_{k}$ 本身或 $F_{k}$ 某个已知的线性函数。如果 $F_{k}$ 的统计特性已知，那么 $Y_{1k}$ 的统计特性也可知道。现在要根据 $t_{k}$ 时刻以前 N 个时刻的观测值 $X_{k-n}, n=1,2,\cdots,N$ ，来确定过滤器的输出 $Y_{k}$ （它和 $Y_{1k}$ 的维数相同）

$$
\mathbf {Y} _ {k} = G \left[ \mathbf {X} _ {k - 1}, \mathbf {X} _ {k - 2}, \dots , \mathbf {X} _ {k - N} \right] \tag {15.3-9}
$$

其中 N 是正整数, 可以趋于无穷大。过滤器 G 的输出误差 $E_{k}$ 是实际输出与理想输出之差

$$
\boldsymbol {E} _ {k} = \boldsymbol {Y} _ {1 k} - \boldsymbol {Y} _ {k} \tag {15.3-10}
$$

它也是一个 n 维随机序列。如果过滤器 G 使输出误差的均方值

$$
\overline {{\boldsymbol {E} _ {k} ^ {\tau} \boldsymbol {E} _ {k}}} = \overline {{(\boldsymbol {Y} _ {1 k} - \boldsymbol {Y} _ {k}) ^ {\tau} (\boldsymbol {Y} _ {1 k} - \boldsymbol {Y} _ {k})}} \tag {15.3-11}
$$

最小，那么这样的过滤器就叫做最优过滤器,G 叫最优过滤函数。当 m=n=1, 则 $F_{k}, N_{k}, X_{k}, Y_{1k}, Y_{k}$ 都是随机变量序列，如果又有 $C_{k}=1, N_{k}=0, Y_{1k}=F_{k+l}, l\geqslant0$ , 这就成为我们上面提到的随机信号 $F_{k}$ 的纯预测问题。如果 $N_{k}\neq0$ , 则是一般的预测问题。如果 $C_{k}=1, N_{k}\neq0, Y_{1k}=F_{k-l}, l\geqslant0$ , 则是随机信号的平滑问 题。当 m=n=1, $C_{k}=1$ 和 $Y_{1k}=F_{k}$ 时，就是纯过滤问题。在观测值中包含有随机噪声时，一般说来，即使最优的过滤器仍存在大于零的极限均方误差，这主要是因为噪声的功率谱密度和有用信号的功率谱密度有叠接的部分，而过滤器相当于一个对于不同频率有不同通过能力的滤波器。对于这部分叠接频率，分不清观测值中哪些属于有用信号，哪些属于噪声，所以不可能把噪声过滤掉而又同时使有用信号完全通过。因此就不可避免产生过滤的误差。如果随机噪声是白色噪声，它的功率谱密度是个常数，那么即便是最优过滤，输出的均方误差也不可能等于零。

在随机序列的一般最优过滤问题中，可以证明，在观测值已给定为 $X_{k}$ 时，最优过滤器的输出 $\mathbf{y}_k$ 是理想输出 $Y_{1k}$ 的条件数学期望。如果在要求过滤均方误差 $\overline{E_k^c E_k}$ 最小的同时，还要求过滤器必须是线性的，即 $G$ 必须是线性函数，那么实现这种要求的过滤器叫做最优线性过滤器， $\dot{G}$ 叫做最优线性过滤函数。通常我们要求的最优过滤器就是求最优线性过滤器，因为如果有用信号和噪声是高斯分布时，求得的最优线性过滤器是一切过滤器中最好的，不可能再有其他的过滤器使过滤的均方误差更小。

对于随机过程来说，一般的最优过滤问题的提法和随机序列的过滤问题相类似。这时过滤器的输入即观测值 $X(t)$ 是 m 维随机过程，它由 n 维有用信号随机过程 $F(t)$ 和 m 维噪声随机过程组合而成

$$
\boldsymbol {X} (t) = \boldsymbol {C} (t) \boldsymbol {F} (t) + \boldsymbol {N} (t) \tag {15.3-12}
$$

其中 $C(t)$ 是 $m \times n$ 阶非随机的函数矩阵。过滤器的理想输出 $Y_{1}(t)$ 是对有用信号 $F(t)$ 进行某种已知的线性运算的结果。过滤器的实际输出 $Y(t)$ (与 $Y_{1}(t)$ 维数相同) 是对输入 $X(t)$ 进行物理上能实现的运算的结果。过滤误差 $E(t)$ 就是理想输出 $Y_{1}(t)$ 与实际输出 $Y(t)$ 之差，它也是 n 维随机过程

$$
\boldsymbol {E} (t) = \boldsymbol {Y} _ {1} (t) - \boldsymbol {Y} (t) \tag {15.3-13}
$$

使均方误差 $\overline{E^{*}(t)E(t)}$ 最小的过滤器就是最优过滤器。和随机序列的情况一样，在观测值 $X(t)$ 是某一个现实 $x(t)$ 时，最优过滤器的输出 $\dot{\mathbf{y}}(t)$ 是理想输出 $Y_{1}(t)$ 的条件数学期望。当信号 $F(t)$ 和噪声 $N(t)$ 是联合高斯分布时，最优线性过滤器是一切过滤器中均方误差 $\overline{E^{*}(t)E(t)}$ 最小的。

如果 m=n=1，那么 $F(t)$ ， $N(t)$ ， $X(t)$ ， $Y_{1}(t)$ ， $Y(t)$ 都是纯量随机过程。此时 $Y_{1}(t)=F(t+\sigma)$ ，根据 $\sigma$ 分别为大于零，等于零或小于零，便可得到随机信号 $F(t)$ 的预测、过滤或平滑问题。

下面几节，我们就来讨论各种类型观测值时以均方误差最小为准则的一般最优过滤问题。

#### 15.4 平稳随机序列的最优线性过滤 $^{[32,36]}$

设计最优线性过滤器的一种有效方法是柯尔莫果洛夫(Колмогоров)理论和维纳(Wiener)理论。这两种理论的实质和结果是相同的，但是处理方法各有特点。由于柯尔莫果洛夫理论有很好的几何直观性，利用希尔伯特空间的几何原理使过滤问题十分清晰而严密，所以先介绍这一理论。我们在这里只讨论一维的实随机序列。

假设过滤器（以后也称为系统）的输入是观测随机序列

$$
X _ {k} = F _ {k} + N _ {k}, \quad k = \dots , - 2, - 1, 0, + 1, + 2, \dots \tag {15.4-1}
$$

其中有用信号 $F_{k}$ 和噪声 $N_{k}$ 是平稳相关的数学期望为零，方差有界的平稳随机序列，所有的相关函数都为已知。假定系统的理想输出 $Y_{1k}$ 是有用信号 $F_{1k}$ 的已知线性函数，它的数学期望也为零，方差也有界，它的相关函数以及它与输入的互相关函数也为已知。我们先假定系统的实际输出 $Y_{k}$ 是 $t_{k}$ 时刻以前 n 个时刻的输入的线性组合

$$
Y _ {k} = a _ {k - 1} X _ {k - 1} + a _ {k - 2} X _ {k - 2} + \dots + a _ {k - n} X _ {k - n} \tag {15.4-2}
$$

输出误差是

$$
E _ {k} = Y _ {1 k} - Y _ {k} \tag {15.4-3}
$$

最优线性过滤问题就是选择系数 $\stackrel{\circ}{a}_{k i}, i=1,2,\cdots,n$ ，使最优输出

$$
Y _ {k} = \stackrel {\circ} {a} _ {k 1} X _ {1} + \stackrel {\circ} {a} _ {k 2} X _ {2} + \dots + \stackrel {\circ} {a} _ {k n} X _ {n} \tag {15.4-4}
$$

保证均方误差 $\overline{E_{k}^{2}}$ 达到最小。

为此把随机序列 $X_{k}, k=\cdots,-1,0,+1,\cdots$ 看做是随机变量空间 $H_{1}$ 中的一个序列，每一个 $X_{k}$ 都是希尔伯特空间 $H_{1}$ 中的元。当 $a_{k,i}, i=1,2,\cdots,n$ 取各种不同值时，所有由式(15.4-2)确定的 $Y_{k}$ 在 $H_{1}$ 中构成一个子空间 $H_{X}$ 。 $H_{1}$ 是无穷维的，而 $H_{X}$ 却是有穷维的，其维数不超过 n。子空间 $H_{X}$ 中每个元都可以表示为式(15.4-2)的形式，如果 $X_{k-1}, X_{k-2}, \cdots, X_{k-n}$ 线性不相关，子空间 $H_{X}$ 是 n 维，那么系数 $a_{k1}, a_{k2}, \cdots, a_{kn}$ 是唯一的。既然理想输出 $Y_{1k}$ 是有用信号 $F_{1k}$ 的线性函数，可以认为它也是随机变量空间 $H_{1}$ 中的一个元。输出误差 $E_{k}$ 是 $H_{1}$ 中由 $Y_{1k}$ 到子空间 $H_{X}$ 中某个元的差向量，它的数学期望等于零，均方误差就是 $E_{k}$ 的范数的平方，因此，要均方误差最小，必需而且只须 $\dot{E}_{k}$ 是 $Y_{1k}$ 到子空间 $H_{X}$ 的垂线，最优输出 $\dot{Y}_{k}$ 是 $Y_{1k}$ 在子空间 $H_{X}$ 的直交投影，而 $\dot{E}_{k}$ 与 $H_{X}$ 直交。因此， $\dot{E}_{k}$ 与 $X_{k-1}, X_{k-2}, \cdots, X_{k-n}$ 的内积分别等于零。这样就可得到下列 n 个方程式

$$
\langle \stackrel {\circ} {E} _ {k}, X _ {k - i} \rangle = 0, \quad i = 1, 2, \dots , n \tag {15.4-5}
$$

展开后得到线性方程组

$$
\langle Y _ {1 k}, X _ {k - i} \rangle = \stackrel {\circ} {a} _ {k 1} \langle X _ {k - 1}, X _ {k - i} \rangle + \stackrel {\circ} {a} _ {k 2} \langle X _ {k - 2}, X _ {k - i} \rangle + \dots + \stackrel {\circ} {a} _ {k n} \langle X _ {k - n}, X _ {k - i} \rangle
$$

$$
i = 1, 2, \dots , n \tag {15.4-6}
$$

只要 $X_{k-1}, X_{k-2}, \cdots, X_{k-n}$ 线性不相关，就可得到 $\overset{\circ}{a}_{k-1}, \overset{\circ}{a}_{k-2}, \cdots, \overset{\circ}{a}_{kn}$ 的唯一解

$$
\stackrel {\circ} {a} _ {k 1} = \frac {\left| \begin{array}{c c c} \langle Y _ {1 k} , X _ {k - 1} \rangle , \langle X _ {k - 2} , X _ {k - 1} \rangle , \cdots , \langle X _ {k - n} , X _ {k - 1} \rangle \\ \langle Y _ {1 k} , X _ {k - 2} \rangle , \langle X _ {k - 2} , X _ {k - 2} \rangle , \cdots , \langle X _ {k - n} , X _ {k - 2} \rangle \\ \vdots & \vdots & \vdots \\ \langle Y _ {1 k} , X _ {k - n} \rangle , \langle X _ {k - 2} , X _ {k - n} \rangle , \cdots , \langle X _ {k - n} , X _ {k - n} \rangle \end{array} \right|}{\left| \begin{array}{c c c} \langle X _ {k - 1} , X _ {k - 1} \rangle , \langle X _ {k - 2} , X _ {k - 1} \rangle , \dots , \langle X _ {k - n} , X _ {k - 1} \rangle \\ \langle X _ {k - 1} , X _ {k - 2} \rangle , \langle X _ {k - 2} , X _ {k - 2} \rangle , \dots , \langle X _ {k - n} , X _ {k - 2} \rangle \\ \vdots & \vdots & \vdots \\ \langle X _ {k - 1} , X _ {k - n} \rangle , \langle X _ {k - 2} , X _ {k - n} \rangle , \dots , \langle X _ {k - n} , X _ {k - n} \rangle \end{array} \right|}
$$

如果把 $X_{k-1}, X_{k-2}, \cdots, X_{k-n}$ 看作是一个 n 维随机列向量 X 的诸分量

$$
\boldsymbol {X} ^ {\tau} = \left(X _ {k - 1}, X _ {k - 2}, \dots , X _ {k - n}\right)
$$

那么

$$
\stackrel {\circ} {a} _ {k i} = \sum_ {j = 1} ^ {n} \left\langle Y _ {1 k}, X _ {k - j} \right\rangle \frac {\left| \sum_ {x} ^ {2} \right| _ {i , j}}{\left| \sum_ {x} ^ {2} \right|}, \quad i = 1, 2, \dots , n \tag {15.4-7}
$$

其中 $|\Sigma_x^2|$ 是方差阵 $\Sigma_x^2$ 的行列式， $|\Sigma_x^2|_{i,j}$ 是方差阵 $\Sigma_x^2$ 的第 $i$ 行第 $j$ 列元素的代数余子式，因此最优输出是

$$
\stackrel {\circ} {Y} _ {k} = P \left(H _ {X}\right) Y _ {1 k} = \sum_ {i = 1} ^ {n} \left(\sum_ {j = 1} ^ {n} \left\langle Y _ {1 k}, X _ {k - j} \right\rangle \frac {\left| \Sigma_ {X} ^ {2} \right| _ {i , j}}{\left| \Sigma_ {X} ^ {2} \right|}\right) X _ {k i} = R _ {Y _ {1 k} X} \Sigma_ {X} ^ {- 2} X \tag {15.4-8}
$$

其中 $P(H_{X})$ 是向 $H_{X}$ 子空间的直交投影算子。由于 $Y_{1k}$ 和 $X_{k}$ 是平稳的，因此求得的系数 $\stackrel{\circ}{a}_{ki}, i=1,2,\cdots,n$ 和 $R_{Y_{1k}x}\Sigma x^{-2}$ 与 k 无关。用 $\stackrel{\circ}{Y}_{k}$ 去逼近 $Y_{k1}$ 所产生的最小的均方误差为

$$
\begin{array}{l} \overline {{E _ {k} ^ {2}}} = \overline {{(Y _ {1 k} - \stackrel {\circ} {a} _ {k 1} X _ {k - 1} - \stackrel {\circ} {a} _ {k 2} X _ {k - 2} - \cdots - \stackrel {\circ} {a} _ {k n} X _ {k - n}) ^ {2}}} \\ = r _ {Y 1} [ 0 ] - \sum_ {l = 1} ^ {n} \sum_ {m = 1} ^ {n} \stackrel {\circ} {a} _ {k l} \stackrel {\circ} {a} _ {k m} r _ {X} [ l - m ] \\ = \sigma_ {Y _ {1}} ^ {2} - \sum_ {l = 1} ^ {n} \sum_ {m = 1} ^ {n} \mathring {a} _ {l} \mathring {a} _ {m} r _ {X} [ l - m ] \\ = \sigma_ {E} ^ {2} \tag {15.4-9} \\ \end{array}
$$

它与 k 无关。当 $X_{k-1}, X_{k-2}, \cdots, X_{k-n}$ 线性相关时，子空间 $H_{X}$ 的维数小于 n，可以确定无穷多组最优系数 $\stackrel{\circ}{a}_{1}, \stackrel{\circ}{a}_{2}, \cdots, \stackrel{\circ}{a}_{n}$ ，但无论取哪一组最优系数，得到的输出都是最优的，且最小均方误差是同一个 $\sigma_{E}^{2}$ 值。

当理想输出 $Y_{1k}=F_{k-1}$ 时, 最小均方误差是

$$
\min \sigma_ {E} ^ {2} = \sigma_ {F} ^ {2} - \sum_ {l = 1} ^ {n} \sum_ {m = 1} ^ {n} a _ {l} a _ {m} r _ {X} [ l - m ] \tag {15.4-10}
$$

要噪声完全过滤掉，即 $\sigma_{E}^{2}=0$ ，必须使 $F_{k-1}$ 包含在子空间 $H_{X}$ 中，此时称噪声 $N_{k}$ 为有用信号 $F_{k}$ 的从属序列。在一般技术问题中从属序列不存在，所以最优过滤器的均方误差是不可能等于零的。当 $F_{k}$ 和 $N_{k}$ 都是高斯分布时，最优线性过滤器的 $\sigma_{E}^{2}$ 就是最小的均方误差，不可能再加以改善。

在上面的讨论中，系统的输出只与有限个时刻的观测值有关，故求得的最优系统称为有限记忆的。当 n 趋于无穷大，即输出与 $t_{k}$ 以前所有时刻的观测值有关时，则系统称为无限记忆的，这时系统输出是无限个输入值线性组合的均方极限

$$
Y _ {k} = a _ {1} X _ {k - 1} + a _ {2} X _ {k - 2} + \dots + a _ {n} X _ {k - n} + \dots = \sum_ {l = 1} ^ {\infty} a _ {l} X _ {k - l} \tag {15.4-11}
$$

上式内右边的无穷级数应均方收敛于左边的 $Y_{k}$ ，故 $Y_{k}$ 的方差应是有界的。当 $a_{1}, a_{2}, \cdots, a_{n}, \cdots$ 取各种不同的数值并使无穷级数式 (15.4-11) 均方收敛时，所有可能的 $Y_{k}$ 及其均方极限在数学期望为零，方差有界的随机变量空间 $H_{1}$ （希尔伯特空间）中构成一个子空间 $H_{X}$ ，它一般是无穷维的。同样，最优过滤器的设计问题，就是要找一组有无限个数的数列 $\stackrel{\circ}{a}_{1}, \stackrel{\circ}{a}_{2}, \cdots, \stackrel{\circ}{a}_{n}, \cdots$ ，它使得最优输出

$$
\stackrel {\circ} {Y} _ {k} = \stackrel {\circ} {a} _ {1} X _ {k - 1} + \stackrel {\circ} {a} _ {2} X _ {k - 2} + \dots + \stackrel {\circ} {a} _ {n} X _ {k - n} + \dots = \sum_ {l = 1} ^ {\infty} \stackrel {\circ} {a} _ {l} X _ {k - l} \tag {15.4-12}
$$

达到均方误差 $\overline{E_k^2}$ 最小。式(15.4-12)中右边无穷级数是均方收敛于 $Y_{k}$ 的。例如，当 $\mathring{a}_l$ 满足条件 $\sum_{l=1}^{\infty} |\mathring{a}_l| < \infty$ 时，式(15.4-12)的右端肯定是均方收敛的。

根据前述原理，这组 $\stackrel{\circ}{a}_{1},\stackrel{\circ}{a}_{2},\cdots,\stackrel{\circ}{a}_{n},\cdots$ 必须满足无限个线性联立方程

$$
r _ {Y _ {1} X} [ l ] - \sum_ {m = 1} ^ {\infty} \mathring {a} _ {m} r _ {X} [ l - m ] = 0, \quad l = 1, 2, \dots , n \tag {15.4-13}
$$

这时就难以利用互相关函数，自相关函数来求系数 $\dot{a}_{1}, \dot{a}_{2}, \cdots, \dot{a}_{n}, \cdots$ 了。

利用平稳随机序列相关函数与功率谱密度的关系

$$
r [ k ] = \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} \Phi (\omega) e ^ {i \omega k T} d \omega \tag {15.4-14}
$$

$$
\Phi (\omega) = \frac {T}{\pi} \sum_ {k = - \infty} ^ {\infty} r [ k ] e ^ {- i \omega k T} \tag {15.4-15}
$$

就可以把方程组(15.4-13)写成

$$
\int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} e ^ {i \omega l T} \left\{\Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} ^ {*} (i \omega) \Phi_ {X} (\omega) \right\} d \omega = 0, \quad l = 1, 2, \dots , n \tag {15.4-16}
$$

其中

$$
\stackrel {\circ} {F} ^ {*} (i \omega) = \sum_ {m = 1} ^ {\infty} \stackrel {\circ} {a _ {m}} e ^ {- i \omega m T} \tag {15.4-17}
$$

$F^{*}(i\omega)$ 就是过滤器在采样周期为 T 时的离散频率特性。由于要求系统应该是稳定的，因此式(15.4-17)的右边级数 $\sum_{m=1}^{\infty}\stackrel{\circ}{a}_{m}e^{-i\omega T}$ 应一致收敛。同时最优线性过滤器的离散频率特性 $\stackrel{\circ}{F}_{i\omega}^{*}(i\omega)$ 应满足方程(15.4-16)。

我们令

$$
G ^ {*} (i \omega) = \left[ \Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} ^ {*} (i \omega) \Phi_ {X} (\omega) \right] \tag {15.4-18}
$$

由于 $\Phi_{Y_{1}X}(\omega)$ , $\Phi_{X}(\omega)$ 和 $F^{*}(i\omega)$ 都是周期为 $2\pi/T$ 的 $\omega$ 的函数, 所以 $G^{*}(i\omega)$ 可以展为无穷傅里叶级数。根据方程(15.4-16)和傅里叶级数的正交性

$$
\int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} e ^ {i \omega l T} e ^ {- i \omega m T} d \omega = \left\{ \begin{array}{l l} 0, & l \neq m \\ \frac {2 \pi}{T}, & l = m \end{array} \right. \tag {15.4-19}
$$

我们可以得出结论： $G^{*}(i\omega)$ 只可以展成含非负幂次的傅里叶级数，即

$$
G ^ {*} (i \omega) = \sum_ {m = 0} ^ {\infty} c _ {m} e ^ {+ i \omega m T} \tag {15.4-20}
$$

由于过滤器是稳定的, $F^{*}(i\omega)$ 恒为有界，所以最优输出的方差为

$$
\sigma_ {Y} ^ {2} = \overline {{Y _ {k} ^ {2}}} = \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} | \stackrel {\circ} {F} ^ {*} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega <   \infty \tag {15.4-21}
$$

因此，最优线性过滤器的采样频率特性 $F^{*}(i\omega)$ 应满足下面两个条件:

(1) $\stackrel{\circ}{F}^{*}(i\omega) = \sum_{m=1}^{\infty} a_{m} e^{-i\omega m T}$ 。

(2) $G^{*}(i\omega) = \left[\Phi_{Y_1X}(\omega) - \mathring{F}^* (i\omega)\Phi_X(\omega)\right] = \sum_{m=0}^{\infty}c_me^{i\omega mT}$ 。

这时理想输出与实际输出之间的最小均方误差（也就是方差）为

$$
\sigma_ {\dot {E}} ^ {2} = \left\| Y _ {1 k} - \stackrel {\circ} {Y} _ {k} \right\| ^ {2} = \sigma_ {Y _ {1}} ^ {2} - \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} | \stackrel {\circ} {F} ^ {*} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega \tag {15.4-22}
$$

在通常的情况下，随机序列的功率谱密度 $\Phi_{Y_{1}X}(\omega)$ 和 $\Phi_{X}(\omega)$ 常可写成 $e^{i\omega T}$ 的有理函数。在引进复变数 $z=e^{i\omega T}$ 后， $\Phi_{X}(i\omega)$ 就是复变有理函数 $\widetilde{\Phi}_{X}(z)$ 在单位圆周 $z=e^{i\omega T}$ 上的值。这时

$$
\stackrel {\circ} {F} (z) = \sum_ {m = 1} ^ {\infty} \frac {a _ {m}}{z ^ {m}} \tag {15.4-23}
$$

$$
\tilde {G} (z) = \left[ \tilde {\Phi} _ {Y _ {1} X} (z) - \stackrel {\circ} {\tilde {F}} (z) \tilde {\Phi} _ {X} (z) \right] = \sum_ {m = 0} ^ {\infty} c _ {m} z ^ {m} \tag {15.4-24}
$$

由于决定 $F^{*}(i\omega)$ 的级数是一致收敛的，故式(15.4-23)在单位圆周 $e^{i\omega T}=z$ 上是收敛的。由式(15.4-23)还可以看出 $\tilde{F}(z)$ 当 $|z|$ 趋于无穷大时趋于零。同时 $G^{*}(i\omega)$ 也是一致收敛的，故式(15.4-24)在单位圆周 $e^{i\omega T}=z$ 上也是收敛的。最后我们得出在 $\tilde{\Phi}(z)$ 为复变数 z 的有理函数时最优线性过滤器的采样传递函数 $\tilde{F}(z)$ 应满足下面三个条件：

$(1')$ $F(z)$ 在 z 平面的单位圆上和单位圆外，即 $|z| \geqslant 1$ 时，无极点。

$(2')$ $F(\infty)=0$ 。

$(3') \quad G(z) = [\Phi_{Y_1X}(z) - F(z)\Phi_X(z)]$ 在 z 平面的单位圆上和单位圆内，即 $|z| \leqslant 1$ ，无极点。

根据这些最优条件，在很多情况下可以求出最优线性过滤器的解析表达式。

例 1. 假定在过滤器的输入作用中，有用信号与噪声都是数学期望为零的平稳随机序列，它们之间是互不相关的，它们的相关函数分别是

$$
r _ {F} [ k ] = c _ {1} e ^ {- \alpha | k T |}, \quad \alpha > 0
$$

$$
r _ {N} [ k ] = \left\{ \begin{array}{l l} c _ {2}, & k = 0 \\ 0, & k \neq 0 \end{array} \right.
$$

现在要求构造最优线性纯过滤器，即 $Y_{1k}=F_{k-1}$ 。我们先求相关函数 $r_{Y_{1}X}, r_{X}$ 和 $r_{Y_{1}}$ ，

$$
r _ {Y _ {1} X} [ k ] = r _ {Y _ {1} F} [ k ] = r _ {F} [ k - 1 ]
$$

$$
r _ {X} [ k ] = r _ {F} [ k ] + r _ {N} [ k ]
$$

$$
r _ {Y _ {1}} [ k ] = r _ {F} [ k ]
$$

然后再根据公式(15.4-15)求出所需的各种功率谱密度

$$
\Phi_ {F} (\omega) = \frac {c _ {1} T}{\pi} \frac {\left(1 - a ^ {2}\right)}{\left(e ^ {i \omega T} - a\right) \left(e ^ {- i \omega T} - a\right)}
$$

$$
\Phi_ {N} (\omega) = \frac {c _ {2} T}{\pi}
$$

$$
\Phi_ {X} (\omega) = \Phi_ {F} (\omega) + \Phi_ {N} (\omega) = \frac {c _ {3} T}{\pi} \frac {(e ^ {i \omega T} - b) (e ^ {- i \omega T} - b)}{(e ^ {i \omega T} - a) (e ^ {- i \omega T} - a)}
$$

$$
\Phi_ {Y _ {1} X} (\omega) = e ^ {- i \omega T} \Phi_ {F} (\omega)
$$

其中

$$
a = e ^ {- \alpha T}, \quad | a | <   1
$$

$$
b c _ {3} = a c _ {2}, \quad c _ {3} (1 - b ^ {2}) = (c _ {1} + c _ {2}) (1 - a ^ {2}), \quad | b | <   1, c _ {3} > 0
$$

作变换 $e^{i\omega T}=z$ 后, 得到

$$
\tilde {\Phi} _ {F} (z) = A \frac {z}{(z - a) (1 - z a)}, \quad A = \frac {c _ {1} T}{\pi} \left(1 - a ^ {2}\right)
$$

$$
\tilde {\Phi} _ {X} (z) = B \frac {(1 - z b) (z - b)}{(1 - z a) (z - a)}, \quad B = \frac {c _ {3} T}{\pi}
$$

$$
\tilde {\Phi} _ {Y _ {1} X} (z) = z ^ {- 1} \tilde {\Phi} _ {F} (z)
$$

这时

$$
\tilde {G} (z) = \tilde {\Phi} _ {Y _ {1} X} (z) - \stackrel {\circ} {\tilde {F}} (z) \tilde {\Phi} _ {X} (z) = \frac {A - \stackrel {\circ} {\tilde {F}} (z) B (1 - b z) (z - b)}{(1 - a z) (z - a)}, \quad | a | <   1
$$

由于要满足最优条件 $(1^{\prime})$ 和 $(3^{\prime})$ ，即 $\tilde{F} (z)$ 不能有模大于或等于 1 的极点， $\tilde{G}(z)$ 不能有模小于或等于 1 的极点，因此 $\tilde{F} (z)$ 的极点只有可能在 $b$ 点

$$
\stackrel {\circ} {F} (z) = \frac {\tilde {\omega} (z)}{z - b}
$$

其中 $\tilde{\omega}(z)$ 为 $z$ 的整函数，它在整个 $z$ 平面上无极点；同时 $G(z)$ 的分子在 $z = a$ 点上一定要等于零，即

$$
A - B (1 - b a) (a - b) \tilde {F} (a) = A - B (1 - b a) \tilde {\omega} (a) = 0
$$

由此得到

$$
\tilde {\omega} (a) = \frac {A}{B (1 - a b)}
$$

再根据最优条件 $(2')$ ， $F(\infty)=0$ ，所以 $\tilde{\omega}(z)$ 应是常数

$$
\tilde {\omega} (z) = \frac {A}{B (1 - a b)} = \text { const }
$$

这样就求出了

$$
\stackrel {\circ} {F} (z) = \frac {A}{B (z - b) (1 - a b)}
$$

它可以展开成 $z$ 的幂级数

$$
\stackrel {\circ} {F} (z) = \frac {A}{B (1 - a b)} \sum_ {m = 1} ^ {\infty} \frac {b ^ {m - 1}}{z ^ {m}}
$$

因此最优线性过滤器的采样频率特性为

$$
\stackrel {\circ} {F} ^ {*} (i \omega) = \frac {A}{B (1 - a b)} \cdot \frac {1}{(e ^ {i \omega T} - b)} = \frac {A}{B (1 - a b)} \sum_ {m = 1} ^ {\infty} b ^ {m - 1} e ^ {- i m \omega T}
$$

最优输出为

$$
\stackrel {\circ} {Y} _ {k} = \frac {A}{B (1 - a b)} \sum_ {m = 1} ^ {\infty} b ^ {m - 1} X _ {k - m}
$$

这时，最小的均方误差为

$$
\begin{array}{l} \sigma_ {E} ^ {2} = r _ {Y _ {1}} [ 0 ] - \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} | \stackrel {\circ} {F} ^ {*} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega \\ = r _ {F} [ 0 ] - \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} \frac {A ^ {2}}{B (1 - a b) ^ {2}} \frac {1}{\left| e ^ {i \omega T} - a \right| ^ {2}} d \omega \\ = c _ {1} \left[ 1 - \frac {A}{B (1 - a b) ^ {2}} \right] \\ \end{array}
$$

如果要求输出 $Y_{k}$ 是输入 $X_{k}, X_{k-1}, \cdots, X_{k-N}, \cdots$ 的函数，而理想的输出定为 $Y_{1k} = F_{k}$ ，那么就相当于把上述系统的输出提前一个采样周期，这时最优输出 $\stackrel{\circ}{Y}_{k}$ 为

$$
\stackrel {\circ} {Y} _ {k} = \frac {A}{B (1 - \alpha b)} \sum_ {m = 0} ^ {\infty} b ^ {m} X _ {k - m}
$$

最优线性过滤器的采样频率特性为

$$
\stackrel {\circ} {F} ^ {*} (i \omega) = \frac {A}{B (1 - a b)} \sum_ {m = 0} ^ {\infty} b ^ {m} e ^ {- i \omega m T} = \frac {A}{B (1 - a b)} \frac {e ^ {i \omega T}}{e ^ {i \omega T} - b}
$$

例 2. 假设已知观测随机序列 $X_{k}=F_{k}+N_{k}$ 在所有采样时刻的值，而且有用信号 $F_{k}$ 和噪声 $N_{k}$ 都是数学期望为零的平稳随机序列，它们之间是互不相关的。现在要寻求用观测序列在所有时刻取值的线性函数来估计有用信号产生的均方误差的最小值。于是，系统的理想输出为 $Y_{1k}=F_{k}$ ，实际输出 $Y_{k}$ 是所有 $X_{k}, k=\cdots,-2,-1,0,1,2,\cdots$ 的线性函数

$$
Y _ {k} = \sum_ {m = - \infty} ^ {\infty} a _ {m} X _ {k - m}
$$

同样，为了求出最小的均方误差必须先寻找函数

$$
\stackrel {\circ} {F} ^ {*} (i \omega) = \sum_ {m = - \infty} ^ {\infty} \stackrel {\circ} {a} _ {k} e ^ {- i \omega m T}
$$

并使

$$
\int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} e ^ {i \omega l T} \left\{\Phi_ {F X} (\omega) - \stackrel {\circ} {F} ^ {*} (i \omega) \Phi_ {X} (\omega) \right\} d \omega = 0, \quad l = \dots , - 2, - 1, 0, 1, 2, \dots
$$

这说明函数 $G^{*}(i\omega)=\Phi_{FX}(\omega)-F^{*}(i\omega)\Phi_{X}(\omega)$ 的所有傅里叶系数都等于零，因此

$$
G ^ {*} (i \omega) = \Phi_ {F X} (\omega) - \stackrel {\circ} {F} ^ {*} (i \omega) \Phi_ {X} (\omega) = 0
$$

这样就可求出

$$
\stackrel {\circ} {F} ^ {*} (i \omega) = \frac {\Phi_ {F X} (\omega)}{\Phi_ {X} (\omega)} = \frac {\Phi_ {F} (\omega)}{\Phi_ {X} (\omega)}
$$

因此最小的均方误差为

$$
\sigma_ {\hat {E}} ^ {2} = r _ {F} [ 0 ] - \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} | \stackrel {\circ} {F} ^ {*} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega
$$

$$
\begin{array}{l} = \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} \left[ \Phi_ {F} (\omega) - | \stackrel {\circ} {F} ^ {*} (i \omega) | ^ {2} \Phi_ {X} (\omega) \right] d \omega \\ = \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} \frac {\Phi_ {F} (\omega) \left[ \Phi_ {X} (\omega) - \Phi_ {F} (\omega) \right]}{\Phi_ {X} (\omega)} d \omega \\ \end{array}
$$

由于 $F_{k}$ 与 $N_{k}$ 互不相关， $\Phi_{X}(\omega)=\Phi_{F}(\omega)+\Phi_{N}(\omega)$ ，所以

$$
\sigma_ {E} ^ {2} = \frac {1}{2} \int_ {- \frac {\pi}{T}} ^ {\frac {\pi}{T}} \frac {\Phi_ {F} (\omega) \Phi_ {N} (\omega)}{\Phi_ {F} (\omega) + \Phi_ {N} (\omega)} d \omega
$$

由此可见，即使可以利用所有的输入值来过滤噪声：也只有在有用信号的功率谱密度与噪声的功率谱密度不互相覆盖，即 $\Phi_{F}(\omega) \cdot \Phi_{N}(\omega) \equiv 0$ 时才能把噪声完全过滤掉。

#### 15.5 平稳随机过程的最优线性过滤 $^{[29,36]}$

现在来讨论平稳随机过程的最优过滤问题，这时要求设计的系统将是线性常系数连续系统。假定观测值 $X(t)$ 是有用信号 $F(t)$ 和噪声 $N(t)$ 的叠加

$$
X (t) = F (t) + N (t) \tag {15.5-1}
$$

$F(t)$ 和 $N(t)$ 都是数学期望为零的平稳随机过程, 它们之间是平稳相关的, 它们的相关函数都已给定, 设系统的理想输出 $Y_{1}(t)$ 是输入有用信号 $F(t)$ 的已知线性变换

$$
Y _ {1} (t) = \int_ {- \infty} ^ {\infty} h _ {1} (\sigma) F (t - \sigma) d \sigma \tag {15.5-2}
$$

其中 $h_{1}(t)$ 是定义于 $(-∞,∞)$ 上的某一给定的绝对可积函数或是 δ 函数及其高阶导数，并且满足条件

$$
\int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} h _ {l} (\lambda) h _ {l} (\sigma) R _ {F} (\lambda - \sigma) d \lambda d \sigma <   \infty \tag {15.5-3}
$$

系统的输出 $Y(t)$ 是 t 时刻以前所有观测值 $X(t-\sigma), \sigma \geqslant 0$ 的线性变换

$$
Y (t) = \int_ {0} ^ {\infty} h (\sigma) X (t - \sigma) d \sigma \tag {15.5-4}
$$

$h(t)$ 就是系统的脉冲响应函数, 它应满足下列三个条件:

(1) 当 t<0 时 $h(t)=0$ 。

(2) $\int_{0}^{\infty}|h(t)|dt < \infty$ 或是 $\delta$ 函数及其高阶导数。

(3) $\int_{0}^{\infty}\int_{0}^{\infty}h(t)h(t')R_X(t - t')dtdt' < \infty$

这时系统显然是稳定的，传递函数

$$
F (s) = \int_ {0} ^ {\infty} h (t) e ^ {- s t} d t
$$

的极点全在左半 S 平面上。从等式(15.5-2)和(15.5-4)中可以看出 $Y(t)$ 与 $Y_{1}(t)$ 都是数学期望为零的平稳随机过程，它们都与 $X(t)$ 平稳相关。现在要在所有满足上述三个条件的线性系统 $h(t)$ 中寻找最优的线性系统 $\stackrel{\circ}{h}(t)$ 使得过滤后误差 $E(t)=Y_{1}(t)-Y(t)$ 的均方值（也就是方差）取最小值

$$
\overline {{\stackrel {\circ} {E} ^ {2} (t)}} = \overline {{\left[ Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right] ^ {2}}} = \min _ {h (t)} \overline {{\left[ Y _ {1} (t) - Y (t) \right] ^ {2}}} \tag {15.5-5}
$$

在第 15.1 节中已经给出了相应于脉冲响应函数 $h(t)$ 的均方误差 $\overline{E^{2}}$ 的表示式 (15.1-8)。我们用 $h(t)=\stackrel{\circ}{h}(t)+\varepsilon\eta(t)$ 表示对最优脉冲响应函数 $\stackrel{\circ}{h}(t)$ 的变分，其中 $\eta(t)$ 也是满足上述三个条件的任意函数， $\varepsilon$ 是任意小的数。把 $h(t)=\stackrel{\circ}{h}(t)+\varepsilon\eta(t)$ 代入方程 (15.1-8) 后，不难求出均方误差增量的主要部分为

$$
\begin{array}{l} \delta \overline {{{E ^ {2}}}} = \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} \varepsilon \eta (\sigma) \{- r _ {F} (\sigma - u) [ h _ {1} (u) - \stackrel {\circ} {h} (u) ] + r _ {F N} (\sigma - u) \stackrel {\circ} {h} (u) \\ - r _ {N F} (\sigma - u) \left[ h _ {1} (u) - \stackrel {\circ} {h} (u) \right] + r _ {N} (\sigma - u) \stackrel {\circ} {h} (u) \rbrace d \sigma d u \\ + \int_ {- \infty} ^ {\infty} \int_ {- \infty} ^ {\infty} \varepsilon \eta (u) \{- r _ {F} (\sigma - u) [ h _ {1} (\sigma) - \stackrel {\circ} {h} (\sigma) ] - r _ {F N} (\sigma - u) [ h _ {1} (\sigma) \\ \left. - \stackrel {\circ} {h} (\sigma) \right] + r _ {N F} (\sigma - u) \stackrel {\circ} {h} (\sigma) + r _ {N} (\sigma - u) \stackrel {\circ} {h} (\sigma) \rbrace d \sigma d u \tag {15.5-6} \\ \end{array}
$$

因为 $h(t)$ 是最优的, 所以对任意 $\eta(t), \delta \overline{E^{2}}$ 都必须等于零, 这个条件给出了 $h(t)$ 应满足的方程式

$$
\begin{array}{l} \int_ {- \infty} ^ {\infty} \left[ r _ {F} (\sigma - u) + r _ {F N} (\sigma - u) \right] h _ {1} (u) d u \\ = \int_ {- \infty} ^ {\infty} \left[ r _ {F} (\sigma - u) + r _ {F N} (\sigma - u) + r _ {N F} (\sigma - u) + r _ {N} (\sigma - u) \right] \stackrel {\circ} {h} (u) d u \\ \end{array}
$$

由于

$$
\boldsymbol {r} _ {F} + \boldsymbol {r} _ {F N} = \boldsymbol {r} _ {F X}
$$

和

$$
\boldsymbol {r} _ {F} + \boldsymbol {r} _ {F N} + \boldsymbol {r} _ {N F} + \boldsymbol {r} _ {N} = \boldsymbol {r} _ {X}
$$

所以 $h(t)$ 应满足等式

$$
\int_ {- \infty} ^ {\infty} r _ {F X} (\sigma - u) h _ {1} (u) d u = \int_ {- \infty} ^ {\infty} r _ {X} (\sigma - u) \stackrel {\circ} {h} (u) d u \tag {15.5-7}
$$

方程(15.5-7)的左边正好就是理想输出 $Y_{1}(t)$ 与观测值 $X(t)$ 的互相关函数，所以

$$
r _ {Y _ {1} X} (\sigma) = \int_ {0} ^ {\infty} r _ {X} (\sigma - u) \stackrel {\circ} {h} (u) d u \tag {15.5-8}
$$

这个方程就是维纳-何甫(Hopf)积分方程。

维纳-何甫方程具有明显的几何意义。随机过程 $X(t - \tau)$ 在 $\tau \geqslant 0$ 时的所有的值都是希尔伯特空间 $H_{1}$ 中的向量。在 $t$ 时刻所有可能的线性过滤器的输出 $Y(t)$

及其均方极限组成了 $H_{1}$ 中的子空间 $H_{x}$ ，它一般是无穷维的。理想输出 $Y_{1}(t)$ 也是希尔伯特空间 $H_{1}$ 中的一个向量。根据希尔伯特空间的几何原理可以得出结论：均方误差最小的最优线性过滤器的输出 $\dot{Y}(t)$ 是向量 $Y_{1}(t)$ 在子空间 $H_{x}$ 内的直交投影，差向量

$$
E (t) = Y _ {1} (t) - \stackrel {\circ} {Y} (t)
$$

就是向量 $Y_{1}(t)$ 到子空间 $H_{X}$ 的垂线。垂线应与子空间 $H_{X}$ 直交，即与子空间 $H_{X}$ 内每一个向量直交，因此 $\dot{Y}(t)$ 应满足方程

$$
\langle Y _ {1} (t) - Y (t), X (t - \sigma) \rangle = 0, \quad \sigma \geqslant 0
$$

根据内积的定义有

$$
r _ {Y _ {1} X} (\sigma) = r _ {Y X} ^ {\circ} (\sigma), \quad \sigma \geqslant 0
$$

再根据线性常系数系统输出与输入之间互相关函数的表示式，即可得到式(15.5-7)。

我们利用平稳随机过程相关函数的谱分解公式

$$
r (\sigma) = \frac {1}{2} \int_ {- \infty} ^ {\infty} e ^ {i \sigma \omega} \Phi (\omega) d \omega \tag {15.5-9}
$$

就可以把方程(15.5-8)写成

$$
\int_ {- \infty} ^ {\infty} e ^ {i \omega \sigma} \left\{\Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} (i \omega) \Phi_ {X} (\omega) \right\} d \omega = 0, \quad \sigma \geqslant 0 \tag {15.5-10}
$$

其中

$$
\stackrel {\circ} {F} (i \omega) = \int_ {0} ^ {\infty} \stackrel {\circ} {h} (t) e ^ {- i \omega t} d t
$$

这就是最优过滤器的频率特性，它应满足方程(15.5-10)。

再令

$$
G (i \omega) = \Phi_ {Y _ {1} X} (\omega) - F (i \omega) \Phi_ {X} (\omega) \tag {15.5-11}
$$

如果 $G(i\omega)$ 的极点都在复平面 $\omega$ 的下半平面, 而且在上半平面当 $|\omega|$ 沿某一射线趋于无限时它趋于零的速度不慢于 $1/\omega$ , 那么这时

$$
\int_ {- \infty} ^ {\infty} e ^ {i \sigma \omega} G (i \omega) d \omega = \oint e ^ {i \sigma \omega} G (i \omega) d \omega = 0, \quad \sigma \geqslant 0
$$

上式中闭路积分路线是复平面 $\omega$ 上实轴以及包含上半 $\omega$ 平面的一个封闭半圆（图 15.5-1），因为积分路线内不包含 $e^{i\omega\sigma}G(i\omega)$ 的极点，所以积分等于零。由于过滤器的三个限制条件，因此最优过滤器的频率特性 $F(i\omega)$ 的极点应在上半 $\omega$ 平面，并且积分

$$
\frac {1}{2} \int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega <   \infty
$$

> 此处省略原书 **图 15.5-1**

综上所述，要求的最优线性过滤器的频率特性 $F(i\omega)$ 应满足下面三个条件:

(1) $F(i\omega)$ 的极点都在上半 $\omega$ 平面（保证系统稳定)。

(2) $G(i\omega) = \Phi_{Y_1X}(\omega) - F(i\omega)\Phi_X(\omega)$ 的极点都在下半 $\omega$ 平面，在上半 $\omega$ 平面中，当 $|\omega| \to \infty$ 时，它的减小速度不小于 $1 / \omega$ （保证均方误差最小）。

(3) $\int_{-\infty}^{\infty}|\stackrel {\circ}{F}(i\omega)|^{2}\Phi_{X}(\omega)d\omega < \infty$ （保证输出的方差有界）。这时最小的均方误差是

$$
\sigma_ {\hat {E}} ^ {2} = r _ {Y _ {1}} (0) - \frac {1}{2} \int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega \tag {15.5-12}
$$

如果

$$
F _ {1} (i \omega) = \int_ {- \infty} ^ {\infty} h _ {1} (t) e ^ {- i \omega t} d t
$$

那么由式(15.5-2)可以得到

$$
\Phi_ {Y _ {1} X} (\omega) = F _ {1} (i \omega) \Phi_ {F X} (\omega) \tag {15.5-13}
$$

在很多情况下 $\Phi_{X}(\omega)$ 可分解为

$$
\Phi_ {X} (\omega) = \Psi (i \omega) \Psi (- i \omega) \tag {15.5-14}
$$

$\Psi(i\omega)$ 是零点和极点都在上半 $\omega$ 平面的函数，例如是 $i\omega$ 的有理函数。把方程(15.5-13)和(15.5-14)代入等式(15.5-11)后可以得到

$$
\begin{array}{l} G (i \omega) = F _ {1} (i \omega) \Phi_ {F X} (\omega) - F (i \omega) \Psi (i \omega) \Psi (- i \omega) \\ = \Psi (- i \omega) \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} - \stackrel {\circ} {F} (i \omega) \Psi (i \omega) \right] \tag {15.5-15} \\ \end{array}
$$

如果 $\frac{F_{1}(i\omega)\Phi_{FX}(\omega)}{\Psi(-i\omega)}$ 可以分成两部分之和

$$
\frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} = \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {+} + \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {-} \tag {15.5-16}
$$

[ ]+ 代表它的极点在上半 $\omega$ 平面，[ ]- 代表它的极点在下半 $\omega$ 平面的那部分。那么

$$
G (i \omega) = \Psi (- i \omega) \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {-} + \Psi (- i \omega) \left\{\left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {+} - \stackrel {\circ} {F} (i \omega) \Psi (i \omega) \right\}
$$

上式中第一项极点都在下半 $\omega$ 平面；第二项前面部分因子的极点都在下半 $\omega$ 平面，后面部分因子的极点都在上半 $\omega$ 平面。因此，第二项的极点在上半、下半 $\omega$ 平面都有，要满足最优条件(2)中前一部分必须使 $\{\}$ 内的算式等于零，也就是

$$
\stackrel {\circ} {F} (i \omega) = \frac {1}{\Psi (i \omega)} \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {+} \tag {15.5-17}
$$

可以看出由式(15.5-17)得出的 $F(i\omega)$ 是满足最优条件(1)的。方程(15.5-17)只是最优线性过滤器的必要条件，它还应满足最优条件(2)的后一部分和最优条件(3)。在实际的 $\Phi_{FX}(\omega),\Phi_X(\omega)$ 和 $F_{1}(i\omega)$ 稳定时这些最优条件总是可以满足的。想从函数 $F_{1}(i\omega)\Phi_{FX}(\omega) / \Psi (-i\omega)$ 中分出极点在上半 $\omega$ 平面的那部分运算，也可以用解析式来表达。实际上 $\stackrel{\circ}{F}(i\omega)$ 可写成下列解析表达式

$$
\stackrel {\circ} {F} (i \omega) = \frac {1}{2 \pi \Psi (i \omega)} \int_ {0} ^ {\infty} e ^ {- i \omega t} d t \int_ {- \infty} ^ {\infty} \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} e ^ {i \omega t} d \omega \tag {15.5-18}
$$

用 $\omega$ 平面上的回路积分方法不难判断这个积分的正确性。至于在实际计算中到底采用方程(15.5-17)还是(15.5-18)要依据不同的具体情况来决定，有时还可以直接利用最优条件(1)，(2)，(3)。对于确定的 $h_1(t)$ 或 $F_{1}(i\omega)$ 和确定的各种功率谱密度 $\Phi_N, \Phi_F, \Phi_{FN}, \Phi_{NF}$ 来说，最优线性过滤器的特性就完全被确定了。

当噪声不存在时， $\Phi_N = \Phi_{FN} = \Phi_{NF} = 0, \Phi_{FX} = \Phi_F, \Phi_F(\omega) = \Psi(i\omega)\Psi(-i\omega)$ 。如果确定理想输出的函数 $h_1(t)$ 除了满足以上条件外并在 $t < 0$ 时 $h_1(t) = 0$ ，那么 $F_1(i\omega)$ 的极点都在上半 $\omega$ 平面。这时根据方程(15.5-17)就有 $\stackrel{\circ}{F}(i\omega) = F_1(i\omega), E(t) = 0$ ，这是可以事先想到的。如果 $F_1(i\omega)$ 的极点不全在上半 $\omega$ 平面，那么即使没有噪声实际的最优线性过滤器的频率特性 $\stackrel{\circ}{F}(i\omega)$ 也不可能等于 $F_1(i\omega)$ ，这时误差 $E(t)$ 不可能等于零，即总有均方误差存在。如果有噪声存在的话， $\stackrel{\circ}{F}(i\omega)$ 将不等于 $F_1(i\omega)$ ，即使最好的过滤器也不可能完全消除均方误差，换言之，过滤总是有限度的。

关于选取一个函数的极点在上半 $\omega$ 平面的那一部分运算, 我们可以作如下解释。假定 $F(i\omega)$ 在复平面 $\omega$ 的实轴上无极点, 且当 $|\omega|$ 沿平面上某一射线趋于无穷大时, $F(i\omega)$ 趋于零的速度不慢于 $1/\omega$ 。现在根据

$$
h (t) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} e ^ {i \omega t} F (i \omega) d \omega
$$

> 此处省略原书 **图 15.5-2**

来求 $h(t)$ 。由于 $F(i\omega)$ 有以上特性，所以可以把沿复平面 $\omega$ 实轴的积分化为沿闭路积分路线的积分。因为被积函数中有因子 $e^{i\omega t}$ ，对于正的 t 和负的 t 这两种情况，在复数 $\omega$ 平面上所取的积分路线也一定有所不同，正如图 15.5-2 所画的那样。假设 $F(i\omega)$ 只有在上半 $\omega$ 平面上的极点，那么对 t > 0 的情况，闭路积分路线包含了 $F(i\omega)$ 的极点，这时 $h(t)$ 不等于零；对 t < 0 的情况，闭路积分路线不包含 $F(i\omega)$ 的极点，这时 $h(t) = 0$ 。如果 $F(i\omega)$ 在下 半 $\omega$ 平面上也有极点，那么对 $t < 0$ 的情况，闭路积分路线包含了 $F(i\omega)$ 的某些极点，这时 $h(t)$ 不等于零。如果 $h(t)$ 是表示的系统的脉冲响应函数，那么 $F(i\omega)$ 在下半 $\omega$ 平面上有极点就意味着系统在冲量作用以前就有了反应，事实上任何实际物理系统都不可能发生这种情况。所以，从已知函数选取极点只有在上半 $\omega$ 平面的那一部分的运算，目的在于使得最优线性过滤器实际上能够实现。因为在这种情况中 $t < 0$ 时 $h(t) = 0$ 。在实际上能实现的传递函数这一概念的基础上，伯德和香农对方程(15.5-17)作了一个解释[8]。假定过滤器的输入 $X(t)$ 是白色噪声，功率谱密度 $\Phi_X(\omega) \equiv 1$ ，那么 $R_X(t - u) = \pi \delta(t - u)$ ，根据方程(15.5-7)就得出

$$
\stackrel {\circ} {h} (t) = \frac {1}{\pi} \int_ {- \infty} ^ {\infty} h _ {1} (u) r _ {F X} (t - u) d u = \frac {1}{\pi} r _ {Y _ {1} X} (t), \quad t > 0
$$

同时根据物理上能实现的概念就有

$$
\stackrel {\circ} {h} (t) = 0, \quad t <   0
$$

因此根据上面的解释，物理上能实现的最优线性过滤器的频率特性必然是

$$
F (i \omega) = \left[ \Phi_ {Y _ {1} X} (\omega) \right] _ {+} = \left[ F _ {1} (i \omega) \Phi_ {F X} (\omega) \right] _ {+} \tag {15.5-19}
$$

此处 $\left[\quad\right]_{+}$ 是原功率谱密度 $\Phi_{Y_{1}}x(\omega)$ 中极点在上半 $\omega$ 平面的分量。如果过滤器的输入不是白色噪声，而是某一可进行下列分解的函数 $X(t)$

$$
\Phi_ {X} (\omega) = \Psi (i \omega) \Psi (- i \omega) \tag {15.5-14}
$$

那么输入 $X(t)$ 通过一个传递函数为 $1 / \Psi (s)$ 的系统后输出 $Z(t)$ 是个白色噪声（见图 15.5-3），并且 $\Phi_{Z}(\omega) = 1$ 。输入是白色噪声 $Z(t)$ ，输出为 $Y(t)$ 的最优线性过滤器的频率特性根据式(15.5-19)应是 $[\Phi_{Y_1Z}(\omega)]_+ = [F_1(i\omega)\Phi_{FZ}(\omega)]_+$ 。那么输入是 $X(t)$ 输出为 $Y(t)$ 的最优线性过滤器应是上述两个环节的串联，它的频率特性应该是

$$
\stackrel {\circ} {F} (i \omega) = \frac {1}{\Psi (i \omega)} \left[ F _ {1} (i \omega) \Phi_ {F Z} (i \omega) \right] _ {+}
$$

> 此处省略原书 **图 15.5-3**

由于 $\Psi(i\omega)$ 的零极点都在上半 $\omega$ 平面, 所以 $F(i\omega)$ 的极点都在上半 $\omega$ 平面, 即过滤器是稳定的。又由于 $Z(t)$ 是输入 $X(t)$ 通过环节 $1/\Psi(i\omega)$ 后的输出, 所以

$$
\Phi_ {F Z} (\omega) = \Phi_ {F X} (\omega) \frac {1}{\Psi (- i \omega)} \tag {15.5-20}
$$

这样最优线性过滤器的频率特性的最终形式就是

$$
\stackrel {\circ} {F} (i \omega) = \frac {1}{\Psi (i \omega)} \left[ \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} \right] _ {+} \tag {15.5-17}
$$

上面的讨论还有另外一点需要说明。我们曾假设可以把 $\Phi_{X}(\omega)$ 进行如式 (15.5-14) 所示的分解, 但是对于 $\omega$ 的任意一个正值偶函数 $\Phi(\omega)$ 不见得总能分解成那种形式。如果要使 $\Phi(\omega)$ 能这样分解, $\Phi(\omega)$ 还必须满足维纳-派勒(Paley)准则 $^{[22]}$

$$
\int_ {- \infty} ^ {\infty} \frac {| \log \Phi (\omega) |}{1 + \omega^ {2}} d \omega <   \infty \tag {15.5-21}
$$

具体地说， $\Phi(\omega)$ 或者像在白色噪声的情况时那样，是个常数；或者当 $\omega \to \infty$ 时 $\Phi(\omega)$ 趋近于零，但趋于零的速度不能过快。如果 $\Phi(\omega)$ 像 $\omega^{-n}$ 那样的速度趋于零，不等式(15.5-21)将成立，但是如果它像 $e^{-|\omega|}$ 或者 $e^{-\omega^2}$ 那样快地趋于零就会使积分发散。后面两种类型的 $\Phi(\omega)$ 不能按式(15.5-14)进行分解。在实际工作中信号和噪声的功率谱密度通常是 $\omega^2$ 的有理分式，所以式(15.5-14)那样的分解是可能的。

#### 15.6 例子和应用

例 1. 假设信号和噪声为互不相关的平稳随机过程, 它们的功率谱密度相应为

$$
\Phi_ {F} (\omega) = \frac {1}{1 + \omega^ {4}}, \quad \Phi_ {N} (\omega) = n ^ {4}
$$

要求设计对信号起微分作用的最优线性过滤器，也就是给定的理想特性 $F_{1}(s)=s$ 。

首先我们求出输入作用的功率谱密度

$$
\Phi_ {X} (\omega) = \Phi_ {F} (\omega) + \Phi_ {N} (\omega) = \frac {(1 + n ^ {4}) + n ^ {4} \omega^ {4}}{1 + \omega^ {4}}
$$

这个函数显然可以按式(15.5-14)进行分解，即

$$
\Psi (i \omega) = \frac {- n ^ {2} \omega^ {2} + \sqrt {2} n ^ {4} \sqrt {1 + n ^ {4}} i \omega + \sqrt {1 + n ^ {4}}}{- \omega^ {2} + \sqrt {2} i \omega + 1}
$$

它的零点和极点都在上半 $\omega$ 平面。令 $i\omega=s$ ，那么得到

$$
\Psi (s) = \frac {n ^ {2} s ^ {2} + \sqrt {2} n ^ {4} \sqrt {1 + n ^ {4}} s + \sqrt {1 + n ^ {4}}}{s ^ {2} + \sqrt {2} s + 1}
$$

它的极点零点都在左半 S 平面。

于是

$$
\begin{array}{l} \frac {F _ {1} (i \omega) \Phi_ {F} (\omega)}{\Psi (- i \omega)} = \frac {F _ {1} (s) \Phi_ {F} (s / i)}{\Psi (- s)} \\ = \frac {s}{\left(s ^ {2} + \sqrt {2} s + 1\right) \left(n ^ {2} s ^ {2} - \sqrt {2} n ^ {4} \sqrt {1 + n ^ {4}} s + \sqrt {1 + n ^ {4}}\right)} \\ = \frac {a s + b}{s ^ {2} + \sqrt {2} s + 1} + \frac {c s + d}{n ^ {2} s ^ {2} - \sqrt {2} n ^ {4} \sqrt {1 + n ^ {4}} s + \sqrt {1 + n ^ {4}}} \\ \end{array}
$$

其中 a, b, c, d 都是常数。很明显，它的极点只在左半 S 平面（即上半 $\omega$ 平面）的部分是第一项，因此

$$
\left[ \frac {F _ {1} (i \omega) \Phi_ {F} (\omega)}{\Psi (- i \omega)} \right] _ {+} = \left[ \frac {F _ {1} (s) \Phi_ {F} (s / i)}{\Psi (- s)} \right] _ {+} = \frac {a s + b}{s ^ {2} + \sqrt {2} s + 1}
$$

把 $a, b$ 确定后我们得到

$$
\begin{array}{l} F (s) = \frac {1}{\Psi (s)} \left[ \frac {F _ {1} (s) \Phi_ {F} (s / i)}{\Psi (- s)} \right] _ {+} = \frac {1}{(n ^ {2} + \sqrt {1 + n ^ {4}}) (n + \sqrt [ 4 ]{1 + n ^ {4}})} \\ \times \frac {\left(^ {4} \sqrt {1 + n ^ {4}} - n\right) s - \sqrt {2} n}{n ^ {2} s ^ {2} + \sqrt {2} n ^ {4} \sqrt {1 + n ^ {4}} s + \sqrt {1 + n ^ {4}}} \\ \end{array}
$$

这就是最优线性过滤器的传递函数。当没有噪声时， $n\rightarrow0$ ， $F(s)$ 就随之趋于 s，这是当然的结果。

例 2. 假设噪声的强度非常高, 而信号比较微弱, 信号与噪声之间互不相关, 它们的功率谱密度分别是

$$
\Phi_ {N} (\omega) = 1, \quad \Phi_ {F} (\omega) = k \varphi (\omega)
$$

其中 k 是一个很小的量, $\varphi(\omega)$ 是 $\omega$ 的偶函数。假设 $K(s)$ 是函数 $\varphi(s/i)$ 的极点在左半 S 平面的部分, 也就是

$$
K (s) = \left[ \varphi \left(\frac {s}{i}\right) \right] _ {+} = \frac {1}{2 \pi} \int_ {0} ^ {\infty} e ^ {- s t} d t \int_ {- \infty} ^ {\infty} \varphi (\omega) e ^ {i \omega t} d \omega
$$

因为 $\varphi(\omega)$ 是 $\omega$ 的偶函数, 于是

$$
\varphi \left[ \frac {s}{i} \right] = K (s) + K (- s)
$$

并且

$$
\Phi_ {X} (\omega) = \Psi (i \omega) \Psi (- i \omega) = 1 + k \varphi (\omega) \cong [ 1 + k K (i \omega) ] [ 1 + k K (- i \omega) ].
$$

所以，假设 $F_{1}(s)$ 表示对信号所希望进行的作用，则最优线性过滤器的传递函数将是

$$
F (s) \cong \frac {k}{1 + k K (s)} \left[ \frac {F _ {1} (s) \varphi (s / i)}{1 + k K (- s)} \right] _ {+}
$$

这是对于数值小的 k 的二次近似式，一次近似式甚至于还要简单一些

$$
F (s) \cong k \left[ F _ {1} (s) \varphi \left(\frac {s}{i}\right) \right] _ {+}
$$

如果 $\varphi (\omega) = \frac{1}{1 + \omega^4}, F_1(s) = s$ ，则当 $k$ 很小时

$$
F (s) \cong - \frac {k}{2 \sqrt {2}} \frac {1}{s ^ {2} + \sqrt {2} s + 1}
$$

当 n 很大时, 再设 $k=1/n^{4}$ , 把此结果和例 1 的结果对照, 就可以验证例 1 的结果。所以在有强烈噪声干扰的情况下, 起微分作用的最优线性过滤器的传递函数改变得非常厉害, 和 $F_{1}(s)=s$ 完全没有相似之处。

例 3. 假设输入作用中信号和噪声是互不相关的平稳随机过程, 数学期望都等于零, 信号 $F(t)$ 是一个随机开关函数, 噪声 $N(t)$ 是白色噪声, 它们的功率谱密度分别是

$$
\Phi_ {F} (\omega) = \frac {1}{1 + \omega^ {2}}, \quad \Phi_ {N} (\omega) = n ^ {2}
$$

要求设计对信号进行预测的最优线性过滤器, 即过滤器的理想输出 $Y_{1}(t)=F(t+\alpha)$ , $\alpha>0$ , 这时 $F_{1}(s)=e^{\alpha s}$ 。首先求出输入作用 $X(t)$ 的功率谱密度

$$
\Phi_ {X} (\omega) = \Phi_ {F} (\omega) + \Phi_ {N} (\omega) = \frac {(1 + n ^ {2}) + n ^ {2} \omega^ {2}}{1 + \omega^ {2}}
$$

所以

$$
\Psi (i \omega) = \frac {\sqrt {1 + n ^ {2}} + n i \omega}{1 + i \omega}
$$

因此

$$
\frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} = \frac {e ^ {i \omega}}{(1 + i \omega) (\sqrt {1 + n ^ {2}} - n i \omega)}
$$

在这种情况下，需要利用方程(15.5-18)来计算 $F(s)$ 。首先，当 t>0 时

$$
\frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} e ^ {i \omega t} d \omega = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {e ^ {i \omega (t + a)}}{(1 + i \omega) (\sqrt {1 + n ^ {2}} - n i \omega)} d \omega
$$

$$
= \frac {e ^ {- (t + \alpha)}}{n + \sqrt {1 + n ^ {2}}}
$$

再根据式 $(15.5-18)$ ，得到

$$
\begin{array}{l} F (s) = \frac {1 + s}{\sqrt {1 + n ^ {2}} + n s} \int_ {0} ^ {\infty} e ^ {- s t} \frac {e ^ {- (t + \alpha)}}{n + \sqrt {1 + n ^ {2}}} d t \\ = \frac {(1 + s) e ^ {- a} \int_ {0} ^ {\infty} e ^ {- (s + 1) t} d t}{(n + \sqrt {1 + n ^ {2}}) (\sqrt {1 + n ^ {2}} + n s)} \\ = \frac {e ^ {- \alpha}}{(n + \sqrt {1 + n ^ {2}}) (\sqrt {1 + n ^ {2}} + n s)} \\ \end{array}
$$

也可以直接利用最优条件(1)，(2)，(3)来求最优线性预测过滤器的传递函数，把 $\Phi_{X}(\omega)$ 化为

$$
\Phi_ {X} (\omega) = \frac {n ^ {2} \left(\omega^ {2} + b ^ {2}\right)}{\left(\omega^ {2} + 1\right)} = \frac {n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}
$$

其中 $b=\sqrt{1+\frac{1}{n^{2}}}>0$ ，根据假设的条件

$$
\Phi_ {Y _ {1} X} (\omega) = F _ {1} (i \omega) \Phi_ {F} (\omega) = \frac {e ^ {i \omega \alpha}}{(\omega - i) (\omega + i)}
$$

可以求得

$$
G (i \omega) = \frac {e ^ {i \omega a} - F (i \omega) (\omega - i b) (\omega + i b) n ^ {2}}{(\omega - i) (\omega + i)}
$$

因为 $G(i\omega)$ 在上半 $\omega$ 平面不应有极点， $F(i\omega)$ 在下半 $\omega$ 平面不应有极点，所以 $F(i\omega)$ 的分母只能包含 $(\omega - ib)$ 的因子。 $F(i\omega)$ 又要满足最优条件(3)

$$
\int_ {- \infty} ^ {\infty} | F (i \omega) | ^ {2} \Phi_ {X} (\omega) <   \infty
$$

所以 $F(i\omega) = \frac{a}{\omega - ib}$ , 其中 $a$ 是常数。把它代入 $G(i\omega)$ 后得到

$$
G (i \omega) = \frac {e ^ {i \omega a} - a n ^ {2} (\omega + i b)}{(\omega - i) (\omega + i)}
$$

在上半 $\omega$ 平面，当 $|\omega|$ 沿某一射线趋于无穷大时， $e^{i\omega a}$ 趋于零， $G(i\omega)$ 趋于零的速度与 $1/\omega$ 相仿。由于 $G(i\omega)$ 不能有极点在上半 $\omega$ 平面，所以当 $\omega=i$ 时它的分子应等于零

$$
e ^ {- \alpha} - a (i + i b) n ^ {2} = 0
$$

所以

$$
a = \frac {e ^ {- a}}{i n ^ {2} (1 + b)}
$$

最后得到

$$
F (i \omega) = \frac {e ^ {- \alpha}}{i n ^ {2} (1 + b) (\omega - i b)} = \frac {e ^ {- \alpha}}{n ^ {2} (1 + b) (i \omega + b)}
$$

把 $b = \sqrt{1 + \frac{1}{n^2}}$ 代入，最后求得的最优线性预测过滤器的传递函数和前面的结果完全一样。

例 4. 除了 $\alpha<0$ 外, 其余条件与例 3 一样。求得的过滤器称为滞后过滤器。滞后过滤器的传递函数与预测过滤器差别很大。先用最优条件 (1), (2), (3) 来确定最优滞后过滤器的传递函数。这里 $G(i\omega)$ 的表示式和上例中相同, 只不过 $\alpha<0$ , 我们把它写为

$$
G (i \omega) = \frac {e ^ {- i \omega | a |} - F (i \omega) (\omega - i b) (\omega + i b) n ^ {2}}{(\omega - i) (\omega + i)}
$$

在上半 $\omega$ 平面，当 $|\omega|$ 沿某一射线趋于无穷大时， $e^{-i\omega |\alpha|}$ 趋于无穷大，如果 $F(i\omega)$ 仍采用 $\frac{a}{\omega - ib}$ 的形式就不能满足最优条件(2)，因此在 $F(i\omega)$ 中一定要有一项与 $e^{-i\omega |\alpha|}$ 抵消，所以

$$
F (i \omega) = \frac {e ^ {- i \omega | a |} - \gamma (\omega)}{n ^ {2} (\omega - i b) (\omega + i b)}
$$

其中 $\gamma(\omega)$ 是 $\omega$ 的多项式。这时

$$
G (i \omega) = \frac {\gamma (\omega)}{(\omega - i) (\omega + i)}
$$

根据最优条件(2)和最优条件(1)， $G(i\omega)$ 的极点只能在下半 $\omega$ 平面， $F(i\omega)$ 的极点只能在上半 $\omega$ 平面，而且在上半 $\omega$ 平面当 $|\omega|$ 沿某一射线趋于无穷大时 $G(i\omega)$ 趋于零的速度不慢于 $1/\omega$ ，所以 $\gamma(\omega)=c(\omega-i)$ ，c 是常数。当 $\omega=-ib$ 时， $F(i\omega)$ 的分母等于零，它的分子也应该等于零

$$
e ^ {- b | \alpha |} - c (- i b - i) = 0
$$

由此可以求出常数 $c$

$$
c = \frac {e ^ {- b | \alpha |}}{- i (1 + b)} = i \frac {e ^ {b \alpha}}{1 + b}
$$

最后求得最优滞后过滤器的频率特性为

$$
F (i \omega) = \frac {e ^ {i \omega \alpha} - i \frac {e ^ {b \alpha}}{1 + b} (\omega - i)}{n ^ {2} (\omega - i b) (\omega + i b)}
$$

传递函数是

$$
F (s) = \frac {s + 1}{(s + b) (s - b)} \cdot \frac {e ^ {b \alpha}}{n ^ {2} (1 + b)} - \frac {e ^ {s \alpha}}{n ^ {2} (s + b) (s - b)}
$$

它是稳定的, 只有 s = -b 是它的极点, 而 s = b 并不是它的极点。

同样，我们也可以利用公式(15.5-18)来求 $F(i\omega)$ 。由于 $\alpha<0$ , 所以在求

$$
\begin{array}{l} \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {F _ {1} (i \omega) \Phi_ {F X} (\omega)}{\Psi (- i \omega)} e ^ {i \omega t} d \omega = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {e ^ {i \omega (t + a)}}{(1 + i \omega) (\sqrt {1 + n ^ {2}} - n i \omega)} d \omega \\ = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {e ^ {i \omega (t + \alpha)}}{(1 + i \omega) (b - i \omega) n} d \omega \\ \end{array}
$$

时， $t > |\alpha|$ 和 $0 < t < |\alpha|$ 将得到两个不同的结果。在 $t > |\alpha|$ 时上述积分等于沿包围上半 $\omega$ 平面的闭曲线的闭路积分，而在 $0 < t < |\alpha|$ 时上述积分等于沿包围下半 $\omega$ 平面的闭曲线的积分，因此得到

$$
\begin{array}{l} \frac {e ^ {- (t + \alpha)}}{n (1 + b)}, \quad (t > | \alpha |) \\ \frac {e ^ {b (t + \alpha)}}{n (1 + b)}, \quad (0 <   t <   | \alpha |) \\ \end{array}
$$

最后得到

$$
\begin{array}{l} F (s) = \frac {1 + s}{n (s + b)} \left[ \int_ {0} ^ {\alpha} e ^ {- s t} \frac {e ^ {b (t + \alpha)}}{n (1 + b)} d t + \int_ {\alpha} ^ {\infty} e ^ {- s t} \frac {e ^ {- (t + \alpha)}}{n (1 + b)} d t \right] \\ = \frac {1 + s}{n ^ {2} (s + b) (1 + b)} \left[ \int_ {0} ^ {\alpha} e ^ {(b - s) t + b \alpha} d t + \int_ {\alpha} ^ {\infty} e ^ {- (s + 1) t - \alpha} d t \right] \\ = \frac {(1 + s) e ^ {+ b \alpha}}{n ^ {2} (s + b) (s - b) (1 + b)} - \frac {e ^ {s \alpha}}{n ^ {2} (s + b) (s - b)} \\ \end{array}
$$

这和前面的结果一样。上面求得的传递函数不能用简单的电阻电容元件组成的网络来实现。我们可以利用下面的近似式

$$
F _ {1} (s) = e ^ {\alpha s} \cong \left[ \frac {1 + (\alpha s / 2 \nu)}{1 - (\alpha s / 2 \nu)} \right] ^ {\nu}, \quad \alpha <   0, \quad \nu = \text {整数}
$$

来求近似的最优滞后过滤器， $\nu$ 越大，则越准确。

上面几个例子只是求出了最优过滤器的传递函数，尚未和闭路控制系统联系起来。下面介绍在闭路控制系统中最优过滤器的设计原理。

##### (1) 噪声作用下的反馈系统

假设反馈系统如图 15.6-1 所示， $F_{f}(s)$ 表示前向线路的传递函数， $F_{b}(s)$ 表示反馈线路的传递函数。系统的输入是信号 $F(t)$ 与噪声 $N(t)$ 之和 $X(t)$ ，它们都是平稳随机过程。假定理想输出 $Y_{1}(t)$ 是 $F_{1}(s)$ 对信号 $F(t)$ 作用的结果。现在要求在给定的 $F_{f}(s)$ ， $F_{1}(s)$ 和信号，噪声的特性的情况下求出使 $\left\|Y_{1}(t)-Y(t)\right\|^{2}$ 达最小值的 $F_{b}(s)$ 。正如图 15.6-1 所画的那样，等价的 $F(s)$ 是

$$
F (s) = \frac {F _ {f} (s)}{1 + F _ {f} (s) F _ {b} (s)} \tag {15.6-1}
$$

由最优线性过滤器的理论得知，最优线性过滤器的传递函数 $F(s)$ 可由方程 (15.5-17) 或 (15.5-18) 求得。知道了 $F(s)$ 以后，就可得到最优的反馈线路传递函数 $F_{b}(s)$

$$
F _ {b} (s) = \frac {1}{F (s)} - \frac {1}{F _ {f} (s)} \tag {15.6-2}
$$

##### (2) 本身产生噪声的反馈系统

> 此处省略原书 **图 15.6-1**

> 此处省略原书 **图 15.6-2**

前面，都是假设噪声来自于反馈控制系统外面，系统本身不产生噪声。然而在很多情况下，反馈控制系统的内部会产生噪声。例如像图 15.6-2 所表示的系统除了外来的噪声 $N(t)$ 以外，还会从测量输出的仪器那里产生内噪声 $M(t)$ 。这里仍用 $F_{f}(s)$ 表示前向线路的传递函数, $F_{b}(s)$ 表示反馈线路的传递函数, $F_{1}(s)$ 表示希望对信号所进行的作用。令 $F(s),N(s),M(s),Y(s)$ 和 $Y_{1}(s)$ 表示 $F(t),N(t),M(t),Y(t)$ 和 $Y_{1}(t)$ 的拉氏变换。于是有

$$
Y (s) = F _ {f} (s) \left\{F (s) + N (s) - F _ {b} (s) [ Y (s) + M (s) ] \right\}
$$

以及

$$
Y _ {1} (s) = F _ {1} (s) F (s)
$$

所以误差的拉氏变换就是

$$
\begin{array}{l} E (s) = Y _ {1} (s) - Y (s) = \frac {- F _ {f} (s)}{1 + F _ {f} (s) F _ {b} (s)} [ F (s) + N (s) ] \\ + \frac {F _ {f} (s) F _ {b} (s)}{1 + F _ {f} (s) F _ {b} (s)} M (s) + F _ {1} (s) F (s) \\ \end{array}
$$

令

$$
G (s) = \frac {F _ {f} (s) F _ {b} (s)}{1 + F _ {f} (s) F _ {b} (s)} \tag {15.6-3}
$$

就有

$$
1 - G (s) = \frac {1}{1 + F _ {f} (s) F _ {b} (s)}
$$

和

$$
\begin{array}{l} E (s) = [ 1 - G (s) ] \left[ F _ {1} (s) F (s) - F _ {f} (s) N (s) \right. \\ - F _ {f} (s) F (s) ] - G (s) \left[ - M (s) - F _ {1} (s) F (s) \right] \\ \end{array}
$$

> 此处省略原书 **图 15.6-3**

这个方程表明，现在的反馈控制系统的问题和图 15.6-3 的传递函数为 $G(s)$ 的过滤器的问题等价，相应的输入信号 $\tilde{F}(s)$ 和相应的噪声输入 $\tilde{N}(s)$ 是

$$
F (s) = \left\{F _ {1} (s) - F _ {f} (s) \right\} F (s) - F _ {f} (s) N (s) \tag {15.6-4}
$$

$$
N (s) = - M (s) - F _ {1} (s) F (s) \tag {15.6-5}
$$

理想的输出就是 $F(s)$ 。原来的问题是求最优的 $F_{b}(s)$ ，现在是求最优的 $G(s)$ ，这里相应的信号 $\tilde{F}(s)$ 和噪声 $\tilde{N}(s)$ 与未知量 $F_{b}(s)$ 无关。我们假设原来信号和噪声之间互不相关，因此只有功率谱密度 $\Phi_{F}, \Phi_{N}, \Phi_{M}$ 。利用方程(15.6-4)和(15.6-5)，在等价的过滤器问题中，各功率谱密度是

$$
\begin{array}{l} \Phi_ {F} ^ {\sim} \left[ \frac {s}{i} \right] = \left[ F _ {1} (s) - F _ {f} (s) \right] \left[ F _ {1} (- s) - F _ {f} (- s) \right] \Phi_ {F} \left[ \frac {s}{i} \right] \\ + F _ {f} (s) F _ {f} (- s) \Phi_ {N} \left[ \frac {s}{i} \right] \tag {15.6-6} \\ \end{array}
$$

$$
\Phi_ {F N} ^ {\sim \sim} \left[ \frac {s}{i} \right] = \left[ F _ {f} (s) - F _ {1} (s) \right] F _ {1} (- s) \Phi_ {F} \left[ \frac {s}{i} \right] \tag {15.6-7}
$$

$$
\Phi_ {N F} ^ {\sim \sim} \left[ \frac {s}{i} \right] = F _ {1} (s) \left[ F _ {f} (- s) - F _ {1} (- s) \right] \Phi_ {F} \left[ \frac {s}{i} \right] \tag {15.6-8}
$$

$$
\Phi_ {N} ^ {\sim} \left[ \frac {s}{i} \right] = \Phi_ {M} \left[ \frac {s}{i} \right] + F _ {1} (s) F _ {1} (- s) \Phi_ {F} \left[ \frac {s}{i} \right] \tag {15.6-9}
$$

由上面的公式可以看出，虽然原来的问题中信号和噪声互不相关，但是等价的过滤器问题中仍然有功率谱密度 $\Phi_{F\sim N}^{\sim\sim}$ 和 $\Phi_{N\sim F}^{\sim\sim}$ 。利用方程(15.6-6)—(15.6-9)被分解的函数就是

$$
\Phi_ {X} ^ {\sim} (\omega) = \Psi (i \omega) \Psi (- i \omega) = F _ {f} (i \omega) F _ {f} (- i \omega) \left\{\Phi_ {F} (\omega) + \Phi_ {N} (\omega) \right\} + \Phi_ {M} (\omega) \tag {15.6-10}
$$

根据方程(15.5-17)，最优的 $G(s)$ 是

$$
\stackrel {\circ} {G} (s) = \frac {1}{\Psi (s)} \left[ \frac {F _ {f} (s) F _ {f} (- s) \left\{\Phi_ {F} (s / i) + \Phi_ {N} (s / i) \right\} - F _ {1} (s) F _ {f} (s) \Phi_ {F} (s / i)}{\Psi (- s)} \right] _ {+} \tag {15.6-11}
$$

当 $G(s)$ 已知时, 方程(15.6-3)给出的最优反馈线路的传递函数如下

$$
\stackrel {\circ} {F} _ {b} (s) = \frac {1 / F _ {f} (s)}{\left[ 1 / \stackrel {\circ} {G} (s) \right] - 1} = \frac {\stackrel {\circ} {G} (s)}{F _ {f} (s) - \stackrel {\circ} {G} (s) F _ {f} (s)} \tag {15.6-12}
$$

##### (3) 饱和限制

> 此处省略原书 **图 15.6-4**

考虑图 15.6-4 所表示的反馈系统, 要求使得输出 $Y(t)$ 尽可能地和输入 $X(t)=F(t)$ 接近。放大器的传递函数是 $F_{a}(s)$ ，伺服马达的传递函数是 $F_{m}(s)$ 。如果设计的条件是适当地改变 $F_{a}(s)$ ，使得误差 $E(t)=Y(t)-F(t)$ 的均方值尽可能地小。这样在运转过程中加到马达里的控制功率就有可能达到非常高的数值。为了避免发生这种功率过高的情况，我们要求加到马达的功率的平均值必须不大于某一额定值。在这种情况下，均方误差是

$$
\overline {{{E}}} ^ {2} = \frac {1}{2} \int_ {- \infty} ^ {\infty} \left| \frac {F _ {a} (i \omega) F _ {m} (i \omega)}{1 + F _ {a} (i \omega) F _ {m} (i \omega)} - 1 \right| ^ {2} \Phi_ {F} (\omega) d \omega \tag {15.6-13}
$$

加到伺服马达的输入平均功率由加到伺服马达里的信号的均方值来表示，这个均方值应不大于额定值 $\sigma^{2}$ ,于是

$$
\sigma^ {2} \geqslant \frac {1}{2} \int_ {- \infty} ^ {\infty} \left| \frac {F _ {a} (i \omega)}{1 + F _ {a} (i \omega) F _ {m} (i \omega)} \right| ^ {2} \Phi_ {F} (\omega) d \omega \tag {15.6-14}
$$

我们利用拉格朗日乘子法。以方程(15.6-14)为约束条件求 $\overline{E^{2}}$ 的极小值问题；可以化为求

$$
\overline {{{E ^ {2}}}} + \lambda \frac {1}{2} \int_ {- \infty} ^ {\infty} \left| \frac {F _ {a} (i \omega)}{1 + F _ {a} (i \omega) F _ {m} (i \omega)} \right| ^ {2} \Phi_ {F} (\omega) d \omega \tag {15.6-15}
$$

的极小值问题, $\lambda$ 是拉格朗日乘子。待求极小的积分为

$$
\frac {1}{2} \int_ {- \infty} ^ {\infty} \left\{\mid F (i \omega) - 1 \mid^ {2} \Phi_ {F} (\omega) + \left| \frac {F (i \omega)}{F _ {m} (i \omega)} \right| ^ {2} \lambda \Phi_ {F} (\omega) \right\} d \omega \tag {15.6-16}
$$

其中

$$
F (i \omega) = \frac {F _ {a} (i \omega) F _ {m} (i \omega)}{1 + F _ {a} (i \omega) F _ {m} (i \omega)} \tag {15.6-17}
$$

这时这个问题可以与一个传递函数为 $F(s)$ 的最优过滤问题等价。对后者来说，理想传递函数 $F_{1}(s)=1$ ，输入信号是 $F(t)$ ，输入噪声的功率谱密度是

$$
\Phi_ {N} (\omega) = \frac {\lambda \Phi_ {F} (\omega)}{F _ {m} (i \omega) F _ {m} (- i \omega)}
$$

且 $F(t)$ 与 $N(t)$ 互不相关。这时被分解的函数是

$$
\Phi_ {\widetilde {X}} (\omega) = \Psi (i \omega) \Psi (- i \omega) = \left[ 1 + \frac {\lambda}{F _ {m} (i \omega) F _ {m} (- i \omega)} \right] \Phi_ {F} (\omega) \tag {15.6-18}
$$

根据方程(15.5-17)，最优过滤器的传递函数是

$$
\stackrel {\circ} {F} (s) = \frac {1}{\Psi (s)} \left[ \frac {\Phi_ {F} (s / i)}{\Psi (- s)} \right] _ {+} \tag {15.6-19}
$$

除了一个常数 $\lambda$ 外，方程(15.6-17)和(15.6-19)确定了最优放大器的传递函数 $\stackrel {\circ}{F}_{a}(s)$ 。可以得出均方误差 $\overline{E^2}$ 是 $\lambda$ 的递增函数，而伺服马达的输入平均功率是 $\lambda$ 的递减函数。因此令式(15.6-14)中的“≥”符号为“=”时，就可以求出 $\lambda$ 值，把它代入式(15.6-19)和(15.6-17)就可以求出所要求的最优的 $F_{a}(s)$ 来。

#### 15.7 有限记忆的最优线性过滤器 $^{[36]}$

在一类实际问题中，常要求所设计的过滤器的脉冲响应函数在有限时间以后等于零，也就是要求过滤器的输出 $Y(t)$ 只是 t 时刻以前有限时间区间内所有输入 $X(t-\sigma),0\leqslant\sigma\leqslant T$ 的线性变换

$$
Y (t) = \int_ {0} ^ {T} h (\sigma) X (t - \sigma) d \sigma \tag {15.7-1}
$$

这类过滤器称为有限记忆过滤器。当 $T \rightarrow \infty$ 时称为无限记忆过滤器。有限记忆的最优线性过滤器的设计问题的提法和第 15.5 节内无限记忆的最优线性过滤器的设计问题的提法相同，只不过输出 $Y(t)$ 应为

$$
Y (t) = \int_ {0} ^ {\infty} h _ {T} (\sigma) X (t - \sigma) d \sigma \tag {15.7-2}
$$

$hr(t)$ 是系统的脉冲响应函数，它除了应满足第 15.5 节中的三个条件外，还应满足。

(4) 当 t > T 时, $h_{T}(t) = 0$ 。

显然，这时系统的传递函数 $F_{T}(s) = \int_{0}^{\infty} h_{T}(t)e^{-st}dt$ 在整个 $s$ 平面上无极点。

前面已经谈到，数学期望为零的平稳随机过程 $X(t-\sigma)$ 在 $0 \leqslant \sigma \leqslant T$ 时的值域是希尔伯特空间 $H_{1}$ 中的无穷集合。在 t 时刻所有可能的有限记忆线性过滤器的输出 $Y(t)$ 及其均方极限组成了 $H_{1}$ 中的一个子空间 $H_{X,T}$ ，它一般是无限维的。理想输出 $Y_{1}(t)$ 也是 $H_{1}$ 中的一个向量。寻求最优有限记忆线性过滤器，就是要在子空间 $H_{X,T}$ 内寻找最优输出向量

$$
\stackrel {\circ} {Y} (t) = \int_ {0} ^ {\infty} \stackrel {\circ} {h} _ {T} (\sigma) X (t - \sigma) d \sigma
$$

使得最优输出误差 $E(t)=Y_{1}(t)-\dot{Y}(t)$ 的范数的平方取极小值

$$
\sigma_ {E} ^ {2} = \left\| Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right\| ^ {2} \min _ {h _ {T} (t)} \left\| Y _ {1} (t) - Y (t) \right\| ^ {2} \tag {15.7-3}
$$

类似前面的讨论，按空间的几何原理可以得出结论：最优输出 $Y(t)$ 是 $Y_{1}(t)$ 在子空 间 $H_{X,T}$ 上的直交投影，最优输出误差 $Y_{1}(t) - \dot{Y} (t)$ 是向量 $Y_{1}(t)$ 到子空间 $H_{X,T}$ 的垂线。垂线与子空间内任一向量直交，因此 $\dot{Y} (t)$ 满足方程

$$
\langle Y _ {1} (t) - \stackrel {\circ} {Y} (t), X (t - \sigma) \rangle = 0, \quad 0 \leqslant \sigma \leqslant T \tag {15.7-4}
$$

根据内积的定义有

$$
r _ {Y _ {1} X} (\sigma) = r _ {Y X} ^ {\circ} (\sigma), \quad 0 \leqslant \sigma \leqslant T \tag {15.7-5}
$$

利用平稳随机过程相关函数的谱分解公式可以把式(15.7-5)写成

$$
\int_ {- \infty} ^ {\infty} e ^ {i \sigma \omega} \left\{\Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} _ {T} (i \omega) \Phi_ {X} (\omega) \right\} d \omega = 0, \quad 0 \leqslant \sigma \leqslant T \tag {15.7-6}
$$

其中 $\stackrel{\circ}{F}_{T}(i\omega)=\int_{0}^{\infty}\stackrel{\circ}{h}_{T}(t)e^{-i\omega t}dt$ 就是最优有限记忆线性过滤器的频率特性。

我们令

$$
G _ {T} (i \omega) = \Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} _ {T} (i \omega) \Phi_ {X} (\omega) \tag {15.7-7}
$$

那么方程(15.7-6)可写为

$$
\int_ {- \infty} ^ {\infty} e ^ {i \sigma \omega} G _ {T} (i \omega) d \omega = 0, \quad 0 \leqslant \sigma \leqslant T \tag {15.7-8}
$$

此条件比第 15.5 节中相应的条件要弱一些。

现构造

$$
\boldsymbol {G} _ {T} (i \omega) = \boldsymbol {G} _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} \boldsymbol {G} _ {T} ^ {(2)} (\omega) \tag {15.7-9}
$$

使其满足式(15.7-8)，即

$$
\int_ {- \infty} ^ {\infty} e ^ {i \sigma \omega} G _ {T} ^ {(1)} (i \omega) d \omega + \int_ {- \infty} ^ {\infty} e ^ {- i (T - \sigma) \omega} G _ {T} ^ {(2)} (i \omega) d \omega = 0, \quad 0 \leqslant \sigma \leqslant T \tag {15.7-10}
$$

显然，如果 $G_{T}^{(1)}(i\omega)$ 在上半 $\omega$ 平面无极点，而且在上半 $\omega$ 平面上当 $|\omega|$ 沿某一射线趋于无穷大时 $G_{T}^{(1)}(i\omega)$ 趋于零的速度不慢于 $1 / \omega$ ，那么式(15.7-10)中等号左边的第一项就等于 $e^{i\sigma \omega}G_T^{(1)}(i\omega),0\leqslant \sigma \leqslant T$ 沿上半 $\omega$ 平面的闭路积分见图 15.7-1(a)，由于 $e^{i\sigma \omega}G_T^{(1)}(i\omega)$ 在上半 $\omega$ 平面内无极点，所以闭路积分等于零；如果 $G_{T}^{(2)}(i\omega)$ 在下半 $\omega$ 平面无极点，而且在下半 $\omega$ 平面当 $|\omega|$ 沿某一射线趋于无穷大时 $G_{T}^{(2)}(i\omega)$ 趋于零的速度不慢于 $1 / \omega$ ，那么式(15.7-10)中等号左边的第二项就等于 $e^{-i(T - \sigma)\omega}G_{T}^{(2)}(i\omega),0\leqslant \sigma \leqslant T$ 沿下半 $\omega$ 平面的闭路积分见图 15.7-1(b)，由于 $e^{-i(T - \sigma)\omega}G^{(2)}(i\omega)$ 在下半平面无极点，所以闭路积分也等于零。这时等式(15.7-10)才得以成立。由构造的 $G_{T}(i\omega)$ 式(15.7-9)可以解出 $\stackrel{\circ}{F}_{T}(i\omega)$

$$
\stackrel {\circ} {F} _ {T} (i \omega) = \frac {\Phi_ {Y _ {1} X} (\omega) - G _ {T} (i \omega)}{\Phi_ {X} (\omega)}
$$

> 此处省略原书 **图 15.7-1 (a) (b)**

可以看出此时 $F_{T}(i\omega)$ 也应包括两项

$$
\stackrel {\circ} {F} _ {T} (i \omega) = F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega) \tag {15.7-11}
$$

由于最优输出 $Y(t)$ 的方差应有界, 所以

$$
\int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} _ {T} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega <   \infty
$$

在构造的 $G_{T}(i\omega)$ 这种假设下, 最优的有限记忆线性过滤器的频率特性应满足下面三个条件:

(1) $F_{T}(i\omega)$ 在整个 $\omega$ 平面上无极点，并且

$$
\stackrel {\circ} {F} _ {T} (i \omega) = F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega)
$$

(2) $G_{T}(i\omega) = \Phi_{Y_{1}X}(\omega) - F_{T}(i\omega)\Phi_{X}(\omega)$ 可表示为

$$
G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} G _ {T} ^ {(2)} (i \omega)
$$

$G_{T}^{(1)}(i\omega)$ 和 $G_{T}^{(2)}(i\omega)$ 分别在上半和下半 $\omega$ 平面上无极点，并在相应的半平面上当 $|\omega|$ 沿某一射线趋于无穷大时，它们趋于零的速度不慢于 $1/\omega$ 。

$$
\int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} _ {T} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega <   \infty \tag {3}
$$

以上三个最优条件是寻找 $F_{T}(i\omega)$ 的充分条件，并不一定是必要的。但根据这三个条件一般总是可以求出 $F_{T}(i\omega)$ 来。现在我们根据上面所讲的最优条件(1)，(2)，(3)来求有限记忆的最优预测过滤器和滞后过滤器。假设输入信号和噪声的各个功率谱密度与第 15.6 节中例 3 和例 4 相同。

例 1. 有限记忆的最优预测过滤器。

根据第 15.6 节中例 3 所述, 输入的功率谱密度为

$$
\Phi_ {X} (\omega) = \frac {n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}, \quad b = \sqrt {1 + \frac {1}{n ^ {2}}}
$$

互功率谱密度为

$$
\Phi_ {Y _ {1} X} (\omega) = F _ {1} (i \omega) \Phi_ {F} (\omega) = \frac {e ^ {i \omega \alpha}}{(\omega - i) (\omega + i)}, \quad \alpha > 0
$$

根据上面所述，我们先求出 $G_{T}(i\omega)$ 的表示式

$$
\begin{array}{l} G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} G _ {T} ^ {(2)} (i \omega) \\ = \frac {e ^ {i \omega \sigma} - \left[ F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega) \right] n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)} \\ \end{array}
$$

由于在上半 $\omega$ 平面，当 $|\omega|$ 沿某一射线趋于无穷大时 $e^{i\omega \alpha},\alpha >0$ 趋于零，再根据最优条件(2)中 $G_{T}^{(1)}(i\omega)$ 和 $G_{T}^{(2)}(i\omega)$ 的渐近特性，所以只需令 $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 为 $\omega$ 的有理函数，而且分母的幂次比分子高一次就可以了，这样

$$
G _ {T} ^ {(1)} (i \omega) = \frac {e ^ {i \omega \alpha} - F _ {T} ^ {(1)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = - \frac {F _ {T} ^ {(2)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}
$$

如果 $F_{T}^{(1)}(i\omega)$ 的极点不是一 $ib$ 或 $ib$ ，那么它一定是 $G_{T}^{(1)}(i\omega)$ 的极点，如果 $F_{T}^{(2)}(i\omega)$ 的极点不是一 $ib$ 或 $ib$ ，那么它一定是 $G_{T}^{(2)}(i\omega)$ 的极点；根据最优条件(1)， $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 必须有相同的极点，否则 $F_{T}(i\omega)$ 就不可能在整个 $\omega$ 平面上无极点；再由最优条件(2) $G_{T}^{(1)}(i\omega)$ 的极点不能在上半 $\omega$ 平面， $G_{T}^{(2)}(i\omega)$ 的极点不能在下半 $\omega$ 平面；因此得出结论， $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 只可能有一 $ib$ 和 $ib$ 作为它的极点，并且

$$
F _ {T} ^ {(1)} (i \omega) = \frac {a _ {1} \omega + a _ {2}}{(\omega - i b) (\omega + i b)}
$$

$$
F _ {T} ^ {(2)} (i \omega) = \frac {c _ {1} \omega + c _ {2}}{(\omega - i b) (\omega + i b)}
$$

这时

$$
G _ {T} ^ {(1)} (i \omega) = \frac {e ^ {i \omega a} - \left(a _ {1} \omega + a _ {2}\right) n ^ {2}}{(\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {- (b _ {1} \omega + b _ {2})}{(\omega - i) (\omega + i)}
$$

根据最优条件(2)中 $G_{T}^{(1)}(i\omega)$ 和 $G_{T}^{(2)}(i\omega)$ 极点的分布情况， $G_{T}^{(1)}(i\omega)$ 的分子在 $\omega=i$ 时应等于零， $G_{T}^{(2)}(i\omega)$ 的分子在 $\omega=-i$ 时应等于零，所以有方程组

$$
\left\{ \begin{array}{l} e ^ {- a} - n ^ {2} \left(a _ {1} i + a _ {2}\right) = 0 \\ c _ {2} = c _ {1} i \end{array} \right.
$$

最优条件(1)

$$
F _ {T} (i \omega) = \frac {(a _ {1} \omega + a _ {2}) + e ^ {- i \omega T} (c _ {1} \omega + c _ {2})}{(\omega - i b) (\omega + i b)}
$$

在整个 $\omega$ 平面上无极点, 所以它的分子在 $\omega = ib$ 和 -ib 时应等于零, 于是有方程组

$$
\left\{ \begin{array}{l} a _ {1} b i + a _ {2} + e ^ {b T} (b c _ {1} i + c _ {2}) = 0 \\ - a _ {1} b i + a _ {2} + e ^ {- b T} (- b c _ {1} i + c _ {2}) = 0 \end{array} \right.
$$

由上述四个方程式可以解出 $a_{1}, a_{2}, c_{1}$ 和 $c_{2}$ 来，

$$
\begin{array}{l} a _ {1} = - i \frac {e ^ {- a} \left[ e ^ {- b T} (b - 1) + e ^ {b T} (b + 1) \right]}{n ^ {2} \left[ e ^ {- b T} (b - 1) ^ {2} + e ^ {b T} (b + 1) ^ {2} \right]} \\ a _ {2} = b \frac {e ^ {- \alpha} \left[ e ^ {- b T} (1 - b) + e ^ {b T} (1 + b) \right]}{n ^ {2} \left[ - e ^ {- b T} (b - 1) ^ {2} + e ^ {b T} (b + 1) ^ {2} \right]} \\ c _ {1} = i \frac {2 b e ^ {- \alpha}}{n ^ {2} \left[ - e ^ {- b T} (b - 1) ^ {2} + e ^ {b T} (b + 1) ^ {2} \right]} \\ c _ {2} = c _ {1} i = - \frac {2 b e ^ {- a}}{n ^ {2} \left[ - e ^ {- b T} (b - 1) ^ {2} + e ^ {b T} (b + 1) ^ {2} \right]} \\ \end{array}
$$

把 $a_{1}, a_{2}, c_{1}, c_{2}$ 代入 $F_{T}(i\omega)$ 中就可以得出最优的有限记忆线性过滤器。根据 $\stackrel{\circ}{F}_{T}(i\omega)$ 又可以求均方误差的最小值

$$
\sigma_ {E} ^ {2} = \sigma_ {Y _ {1}} ^ {2} - \frac {1}{2} \int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} _ {T} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega
$$

可以看出当 $T \rightarrow \infty$ 时, 由于 b > 0, 因此

$$
a _ {1} \rightarrow - i \frac {e ^ {- a}}{n ^ {2} (1 + b)}, \quad a _ {2} \rightarrow \frac {b e ^ {- a}}{n ^ {2} (1 + b)}, \quad c _ {1} \rightarrow 0, \quad c _ {2} \rightarrow 0
$$

所以

$$
\stackrel {\circ} {F} _ {T} (i \omega) \rightarrow \frac {a _ {1} \omega + a _ {2}}{(\omega - i b) (\omega + i b)} = \frac {e ^ {- \alpha}}{n ^ {2} (i \omega + b) (1 + b)}
$$

结果和第 15.6 节例 3 相同。

例 2. 现在来求有限记忆的最优滞后过滤器, 也就是例 1 中 $\alpha < 0$ 的情况。

这时求得的 $G_{T}(i\omega)$ 的表示式为

$$
\begin{array}{l} G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + G _ {T} ^ {(2)} (i \omega) e ^ {- i \omega T} \\ = \frac {e ^ {- i \omega | \alpha |} - \left[ F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega) \right] n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)} \\ \end{array}
$$

如果 $\alpha<-T$ ，令 $\alpha=(-T)+(-\sigma),\sigma>0$ ，可将上式化为

$$
\begin{array}{l} G _ {T} ^ {(1)} (i \omega) + G _ {T} ^ {(2)} (i \omega) = \frac {- F _ {T} ^ {(1)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)} \\ + e ^ {- i \omega T} \left[ \frac {e ^ {- i \omega \sigma} - F _ {T} ^ {(2)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)} \right] \\ \end{array}
$$

由于在下半 $\omega$ 平面，当 $|\omega|$ 沿某一射线趋于无穷大时， $e^{-i\omega\sigma}$ 趋于零，因此仍可令

$F_{T}^{(1)}(i\omega), F_{T}^{(2)}(i\omega)$ 为 $\omega$ 的有理函数，并且

$$
G _ {T} ^ {(1)} (i \omega) = \frac {- F _ {T} ^ {(1)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {e ^ {- i \omega \sigma} - F _ {T} ^ {(2)} (i \omega) n ^ {2} (\omega - i b) (\omega + i b)}{(\omega - i) (\omega + i)}
$$

我们仍按例 1 中所用的方法求出最优的 $F_{T}(i\omega)$ 。显然，本例中求得的 $F_{T}^{(2)}(i\omega)$ 是例 1 中求得的 $F_{T}^{(1)}(i\omega)$ 的共轭复值，本例中求得的 $F_{T}^{(1)}(i\omega)$ 是例 1 中求得的 $F_{T}^{(2)}(i\omega)$ 的共轭复值，此外还应用 $\sigma = |\alpha +T|$ 代替例 1 结果中的 $\alpha$ 。于是我们就得到 $\alpha < - T$ 时最优滞后过滤器的频率特性为

$$
F _ {T} (i \omega) = e ^ {- i T \omega} \tilde {F} _ {T} ^ {*} (i \omega)
$$

其中 $F_{T}(i\omega)$ 是 $\tilde{\alpha}=|\alpha+T|$ 时最优的有限记忆预测过滤器的频率特性， $F_{T}^{*}(i\omega)$ 是 $\tilde{F}_{T}(i\omega)$ 的共轭复值。

如果 $0 > \alpha > -T$ ，那么情况就有所变化。在 $G_{T}(i\omega)$ 表示式中的 $e^{-i\omega |\alpha |}$ 项，当 $|\omega|$ 沿上半 $\omega$ 平面某一射线趋于无穷大时它也趋于无穷大；如果把它归并至 $G_T^{(2)}(i\omega)$ 中去，再提出一项 $e^{-i\omega T}$ 后，它就成为 $e^{-i\omega |\alpha | + i\omega T}$ ，当 $|\omega|$ 沿下半 $\omega$ 平面某一射线趋于无穷大时， $e^{i\omega (T - |\alpha |)}$ 仍趋于无穷大。所以 $F_T^{(1)}(i\omega)$ 不能是 $\omega$ 的有理函数，它应包含可以抵消 $e^{-i\omega |\alpha |}$ 项的某一项。我们令

$$
F _ {T} ^ {(1)} (i \omega) = \frac {e ^ {- i \omega | a |} + \gamma^ {(1)} (\omega)}{n ^ {2} (\omega - i b) (\omega + i b)}
$$

$$
F _ {T} ^ {(2)} (i \omega) = \frac {\gamma^ {(2)} (\omega)}{n ^ {2} (\omega - i b) (\omega + i b)}
$$

这时

$$
G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} G _ {T} ^ {(2)} (i \omega) = \frac {- \gamma^ {(1)} (\omega) + e ^ {- i \omega T} \gamma^ {(2)} (\omega)}{(\omega - i) (\omega + i)}
$$

根据最优条件(2)中 $G_{T}^{(1)}(i\omega)$ 和 $G_{T}^{(2)}(i\omega)$ 的渐近特性, 可以令 $\gamma^{(1)}(\omega)\gamma^{(2)}(\omega)$ 为 $\omega$ 的有理函数, 而且它们的分子幂次与分母幂次相比应不高于一次, 这时

$$
G _ {T} ^ {(1)} (i \omega) = \frac {- \gamma^ {(1)} (\omega)}{(\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {- \gamma^ {(2)} (\omega)}{(\omega - i) (\omega + i)}
$$

根据最优条件(2)， $G_{T}^{(1)}(i\omega)$ 在上半 $\omega$ 平面无极点， $G_{T}^{(2)}(i\omega)$ 在下半 $\omega$ 平面无极点；再根据最优条件(1)， $F_{T}(i\omega)$ 在整个 $\omega$ 平面上无极点，因此 $r^{(1)}(\omega)$ 和 $\gamma^{(2)}(\omega)$ 只能有相同的极点；所以 $\gamma^{(1)}(\omega)$ 和 $\gamma^{(2)}(\omega)$ 是 $\omega$ 的多项式，并且

$$
\gamma^ {(1)} (\omega) = a (\omega - i)
$$

$$
\gamma^ {(2)} (\omega) = c (\omega + i)
$$

于是

$$
F _ {T} (i \omega) = \frac {e ^ {- i \omega | \alpha |} + a (\omega - i) + e ^ {- i \omega T} c (\omega + i)}{n ^ {2} (\omega - i b) (\omega + i b)}
$$

由于 $F_{T}(i\omega)$ 在整个 $\omega$ 平面上无极点, 所以它的分子在 $\omega = ib$ 和 -ib 时应等于零, 这样得到方程组

$$
\left\{ \begin{array}{l} a i (b - 1) + e ^ {b T} c i (b + 1) + e ^ {b | a |} = 0 \\ - a i (b + 1) + e ^ {- b T} c i (1 - b) + e ^ {- b | a |} = 0 \end{array} \right.
$$

解方程组，得到

$$
a = i \frac {e ^ {- b T + b | a |} (1 - b) - e ^ {b T - b | a |} (1 + b)}{e ^ {- b T} (1 - b) ^ {2} + e ^ {b T} (1 + b) ^ {2}}
$$

$$
c = i \frac {e ^ {- b | \alpha |} (b - 1) + e ^ {b | \alpha |} (b + 1)}{e ^ {- b T} (1 - b) ^ {2} + e ^ {b T} (1 + b) ^ {2}}
$$

把它代入 $F_{T}(i\omega)$ 就可以求出有限记忆最优滞后过滤器的频率特点。当 $T \to \infty$ 时，由于 b > 0，所以

$$
a \rightarrow i \frac {e ^ {- b | \alpha |}}{1 + b}, \quad c \rightarrow 0
$$

所以

$$
F _ {T} (i \omega) \rightarrow \frac {(1 + i \omega) e ^ {- b | a |}}{n ^ {2} (i \omega - b) (i \omega + b) (1 + b)} - \frac {e ^ {- i \omega | a |}}{n ^ {2} (i \omega + b) (i \omega - b)}
$$

结果和第 15.6 节例 4 相同。

#### 15.8 输入信号数学期望不等于零时的有限记忆最优过滤器

在前面的讨论中，我们曾认为输入信号和噪声都是数学期望等于零的平稳随机过程。但在实际中却常有这种情况，即输入信号的数学期望是个随时间变化的函数，它的相关函数 $r_{F}(t,t-\sigma)$ 只和 $\sigma$ 值有关；或者输入信号纯粹是个确定的时间函数。严格地讲，这种输入信号已经不是平稳随机过程了，但由于它的相关函数的特性，它与平稳随机过程的差别仅是表面上的。我们可以把这种信号看作为一个确定的时间函数与一个数学期望为零的平稳随机过程之和。在某一段有限时间内一个连续的时间函数常可以用有限次幂的 t 的多项式来逼近，因此可以认为在某一段有限时间内这个确定的时间函数就是有限次幂的 t 的多项式。在本节我们将把前几节所用过的方法进行推广来解决现在的这一类问题 $^{[36]}$ 。

假设过滤器的输入是个均方连续的随机过程，是由信号和噪声叠加而组成的。有用信号有两个分量，一个是数学期望为零的平稳随机过程 $F(t)$ ,另一个是已知其函数形式的时间函数 $g(t)$ ,在一段有限时间区间内, $g(t)$ 可表示为

$$
g (t) = \sum_ {k = 0} ^ {l} g _ {k} t ^ {k}, \quad t \in [ a, b ] \tag {15.8-1}
$$

其中 $g_{k}, k=0,1,2,\cdots,l$ 为 $l+1$ 个未知常数。噪声 $N(t)$ 是数学期望为零的平稳随机过程，它与 $F(t)$ 平稳相关。因此输入是

$$
X (t) = N (t) + F (t) + g (t) \tag {15.8-2}
$$

设 t 是区间 $[a, b]$ 内某一个任意的固定时刻。过滤器在 t 时刻的理想输出 $Y_{1}(t)$ 是 $[a, b]$ 区间内输入有用信号的线性变换

$$
Y _ {1} (t) = \int_ {t - b} ^ {t - a} h _ {1} (\sigma) [ g (t - \sigma) + F (t - \sigma) ] d \sigma \tag {15.8-3}
$$

其中 $h_{1}(\sigma)$ 是在 $[t-b, t-a]$ 上给定的某个绝对可积函数或是 $\delta$ 函数及其高阶导数，并且

$$
\int_ {t - b} ^ {t - a} \int_ {t - b} ^ {t - a} h _ {1} (\sigma_ {1}) h _ {1} (\sigma_ {2}) r _ {F} (\sigma_ {1} - \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} <   \infty
$$

过滤器的实际输出 $Y(t)$ 是 t 时刻以前某段有限时间区间内输入的线性变换

$$
Y (t) = \int_ {t - b} ^ {t - a} h _ {T} (\sigma) X (t - \sigma) d \sigma = \int_ {0} ^ {T} h _ {T} (\sigma) X (t - \sigma) d \sigma \tag {15.8-4}
$$

并且 $[t - T, t] \subset [a, b], h_r(t)$ 就是有限记忆线性过滤器的脉冲响应函数，它满足如下条件：

(1) 当 t<0 和 t>T 时， $h_{T}(t)=0$ 。

(2) $\int_{t - b}^{t - a}|h_r(\sigma)|d\sigma < \infty$ 或是 $\delta$ 函数及其高阶导数。

(3) $\int_{t - b}^{t - a}\int_{t - b}^{t - a}h_T(\sigma_1)h_T(\sigma_2)r_X(\sigma_1 - \sigma_2)d\sigma_1d\sigma_2 <   \infty$

这样，有限记忆线性过滤器的传递函数 $F_{T}(s) = \int_{0}^{\infty} h_{T}(t)e^{-st}dt$ 在整个 $S$ 平面上无极点。现在要在满足这些条件的过滤器 $h_{T}(t)$ 中寻找一个最优的 $\stackrel{\circ}{h}_{T}(t)$ ，使其相应的输出 $\stackrel{\circ}{Y}(t)$ 满足“无偏”条件 $Y_{1}(t) - \stackrel{\circ}{Y}(t) = 0$ ，和均方误差最小

$$
\overline {{\left[ Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right] ^ {2}}} = \min _ {h _ {T} (t)} \overline {{\left[ Y _ {1} (t) - Y (t) \right] ^ {2}}}
$$

根据等式(15.8-3)和(15.8-4)，所有满足“无偏”条件的过滤器 $h_{T}(t)$ 应满足

$$
\int_ {0} ^ {T} h _ {T} (\sigma) g (t - \sigma) d \sigma = \int_ {t - b} ^ {t - a} h _ {1} (\sigma) g (t - \sigma) d \sigma \tag {15.8-5}
$$

由于 $g(t)$ 是未知系数的 l 次幂多项式, 故条件(15.8-5)就等于条件组

$$
\int_ {0} ^ {T} h _ {T} (\sigma) \sigma^ {k} d \sigma = \int_ {t - b} ^ {t - a} h _ {1} (\sigma) \sigma^ {k} d \sigma , \quad k = 0, 1, 2, \dots , l \tag {15.8-6}
$$

最优的 $h_{T}(t)$ 必须在满足条件组(15.8-6)的 $h_{T}(\sigma)$ 中去找。

数学期望等于零的平稳随机过程 $X(t-\sigma)-\overline{X(t-\sigma)}$ 在 $0 \leqslant \sigma \leqslant T$ 时的所有值 都是希尔伯特空间 $H_{1}$ 中的向量。所有满足条件(1)，(2)，(3)的过滤器 $hr(t)$ 的输出 $Y(t)-\overline{Y(t)}$ 及其均方极限组成了 $H$ 中的子空间 $H_{X,r}$ ，它一般是无限维的，而所有同时满足条件(1)，(2)，(3)和式(15.8-6)中 $l+1$ 个条件的过滤器 $hr(t)$ 的输出 $Y(t)-\overline{Y(t)}$ 及其均方极限组成了子空间 $H_{X,r}$ 中的一个超平面 $Q_{X}$ ，它的维数比 $H_{X,r}$ 的维数少 $l+1$ 。 $Y_{1}(t)-\overline{Y_{1}(t)}$ 是数学期望为零方差有界的随机变量，它也是希尔伯特空间 $H$ 中的一个向量。 $Y_{1}(t)-Y(t)$ 就是希尔伯特空间 $H$ 中向量 $Y_{1}(t)-\overline{Y_{1}(t)}$ 与超平面 $Q_{X}$ 上某一个向量 $Y(t)-\overline{Y(t)}$ 的差向量。最优过滤问题就是要在超平面 $Q_{X}$ 上寻找向量 $\dot{Y}(t)-\overline{\dot{Y}(t)}$ ，使差向量 $Y_{1}(t)-\dot{Y}(t)$ 的范数平方最小。根据希尔伯特空间的几何原理，要使差向量的范数平方最小，那么 $\dot{Y}(t)-\overline{\dot{Y}(t)}$ 应是 $Y_{1}(t)-\overline{Y_{1}(t)}$ 在超平面 $Q_{X}$ 上的直交投影， $Y_{1}(t)-\dot{Y}(t)$ 是向量 $Y_{1}(t)-\overline{Y_{1}(t)}$ 到超平面 $Q_{X}$ 的垂线。由原点到超平面的任意两个向量之差向量位于超平面上，所以 $Y(t)-\dot{Y}(t)$ 位于超平面 $Q_{X}$ 上，它与垂线 $Y_{1}(t)-\dot{Y}(t)$ 直交，

$$
\langle Y _ {1} (t) - \stackrel {\circ} {Y} (t), Y (t) - \stackrel {\circ} {Y} (t) \rangle = 0 \tag {15.8-7}
$$

由式(15.8-5)知， $\overline{Y_{1}(t)}=\overline{Y(t)}=\overset{\circ}{Y}(t)$ ，因此可把式(15.8-7)展成

$$
\int_ {0} ^ {T} h _ {T} (\sigma) \left[ r _ {Y _ {1} X} (\sigma) - r _ {Y ^ {\prime} X} ^ {*} (\sigma) \right] d \sigma = r _ {Y _ {1} Y ^ {\prime}} (0) - r _ {Y ^ {\prime}} (0) \tag {15.8-8}
$$

等式右边是个待定的常数, 等式左边的 $r_{Y_{1}\hat{x}}(\sigma) - r_{\hat{y}X}(\sigma)$ 是与 $h_{T}(\sigma)$ 有关的量。其中 $h_{T}(\sigma)$ 是满足条件 (1), (2), (3) 以及条件式 (15.8-6) 的任意函数, 等式 (15.8-6) 的右边都是些确定的常数。显然, 如果

$$
r _ {Y _ {1} X} (\sigma) - r _ {Y X} ^ {*} (\sigma) = - \sum_ {k = 0} ^ {l} c _ {k} \sigma^ {k}, \quad 0 \leqslant \sigma \leqslant T \tag {15.8-9}
$$

其中 $c_{k}$ 为待定常数，那么在适当地选取 $c_{k}$ 值后总可以同时满足式(15.8-8)和(15.8-6)。而且， $\dot{Y}(t)-\overline{\dot{Y}(t)}$ 位于超平面 $Q_{X}$ 上，因此应满足等式

$$
\int_ {0} ^ {T} \stackrel {\circ} {h} _ {T} (\sigma) \sigma^ {k} d \sigma = \int_ {t - b} ^ {t - a} h _ {1} (\sigma) \sigma^ {k} d \sigma , \quad k = 0, 1, 2, \dots , l \tag {15.8-10}
$$

由此可以证明，同时满足等式(15.8-8)和条件(15.8-6)，(15.8-10)的 $r_{Y_1X}(\sigma) - r_{YX}^{\circ}(\sigma)$ 必然有式(15.8-9)的形式。

由于假定了输入 $X(t)$ 是均方连续的，所以只要在 $0 < \sigma < T$ 内满足等式(15.8-9)则在 $0 \leqslant \sigma \leqslant T$ 区间内也满足，这时

$$
r _ {Y _ {1} X} (\sigma) - r _ {Y X} ^ {\circ} (\sigma) + \sum_ {k = 0} ^ {l} c _ {k} \sigma^ {k} = 0, \quad 0 <   \sigma <   T \tag {15.8-11}
$$

利用相关函数和功率谱密度的关系可得到

$$
\frac {1}{2} \int_ {- \infty} ^ {\infty} e ^ {i \omega \sigma} \left[ \Phi_ {Y _ {1} X} (\omega) - \stackrel {\circ} {F} _ {T} (i \omega) \Phi_ {X} (\omega) \right] d \omega + \sum_ {k = 0} ^ {l} c _ {k} \sigma^ {k} = 0, \quad 0 <   \sigma <   T \tag {15.8-12}
$$

其中 $\stackrel{\circ}{F}_{T}(i\omega)=\int_{0}^{T}\stackrel{\circ}{h}_{T}(t)e^{-i\omega t}dt$ 是最优有限记忆过滤器的频率特性。当 $0<\sigma<T$ 时我们可以把 $t^{k}$ 写成

$$
t ^ {k} = \int_ {- \infty} ^ {\infty} e ^ {i \omega t} f _ {k} (\omega) d \omega , \quad k = 0, 1, \dots , l \tag {15.8-13}
$$

其中

$$
f _ {k} (\omega) = \frac {1}{2 \pi} \int_ {0} ^ {T} t ^ {k} e ^ {- i \omega t} d t, \quad k = 0, 1, \dots , l \tag {15.8-14}
$$

把方程(15.8-13)代入(15.8-12)后就得到

$$
\int_ {- \infty} ^ {\infty} e ^ {i \omega \sigma} \left[ \Phi_ {Y _ {1} X} (\omega) - F _ {T} (i \omega) \Phi_ {X} (\omega) + \sum_ {k = 0} ^ {l} 2 c _ {k} f _ {k} (\omega) \right] d \omega = 0, \quad 0 <   \sigma <   T \tag {15.8-15}
$$

这样就可以用类似于上一节的方法得出最优的 $F_{T}(i\omega)$ 应满足的条件：

(1) $F_{T}(i\omega)$ 在整个 $\omega$ 平面上无极点，并且

$$
\stackrel {\circ} {F} _ {T} (i \omega) = F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega)
$$

(2) $G_{T}(i\omega) = \Phi_{Y_{1}X}(\omega) - \mathring{F}_{T}(i\omega)\Phi_{X}(i\omega) + \sum_{k=0}^{l}c_{k}f_{k}(\omega)$ 可以表示为

$$
G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} G _ {T} ^ {(2)} (i \omega)
$$

$G_{T}^{(1)}(i\omega)$ 和 $G_{T}^{(2)}(i\omega)$ 分别在上半和下半 $\omega$ 平面上无极点，并在相应半平面上当 $|\omega|$ 沿某一射线趋于无穷大时它们都一致趋于零 ①。

(3) $\int_{-\infty}^{\infty}|\stackrel {\circ}{F}_T(i\omega)|^2\Phi_X(\omega)d\omega < \infty$

(4) $\int_{0}^{T} h_{T}(t) t^{k} dt = \int_{t - a}^{t - b} h_{1}(t) t^{k} dt$ ，即 $\left[\frac{d^{k}}{ds^{k}} F_{T}(s)\right]_{s=0} = \left[\frac{d^{k}}{ds^{k}} F_{1}(s)\right]_{s=0}$ ， $k = 0, 1, \cdots, l$

最优过滤器的均方误差为

$$
\begin{array}{l} \sigma_ {\dot {E}} ^ {2} = \left\| Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right\| ^ {2} \\ = r _ {Y _ {1}} (0) + \frac {1}{2} \int_ {- \infty} ^ {\infty} | \stackrel {\circ} {F} _ {T} (i \omega) | ^ {2} \Phi_ {X} (\omega) d \omega \\ - \int_ {- \infty} ^ {\infty} \stackrel {\circ} {F} _ {T} (- i \omega) \Phi_ {Y _ {1} X} (\omega) d \omega \tag {15.8-16} \\ \end{array}
$$

现在我们来举三个例子说明这种方法的应用。

例 1. 设输入端只有平稳随机有用信号 $F(t)$ ，它的数学期望是个常数，功率谱密度为 $\Phi_{F}(\omega)=\frac{1}{1+\omega^{2}}$ ，噪声 $N(t)\equiv0$ 。要求设计最优的有限记忆为 T 的线性预测过滤器。根据上面的最优条件，我们得到下列原始数据

$$
\Phi_ {X} (\omega) = \Phi_ {F} (\omega) = \frac {1}{1 + \omega^ {2}}, \quad F _ {1} (s) = e ^ {\alpha s}, \quad \alpha \geqslant 0
$$

$$
\Phi_ {Y _ {1} X} (\omega) = \frac {e ^ {i \omega \alpha}}{1 + \omega^ {2}}, f _ {0} (\omega) = \frac {1}{2 \pi i \omega} - e ^ {- i \omega T} \frac {1}{2 \pi i \omega}
$$

$$
f _ {1} (\omega) = \dots = f _ {l} (\omega) = 0
$$

于是我们就得到

$$
\begin{array}{l} G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + G _ {T} ^ {(2)} (i \omega) \\ = \frac {e ^ {i \omega \alpha} - \left[ F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega) \right]}{(\omega - i) (\omega + i)} + \frac {2 c _ {0}}{2 \pi i \omega} - \frac {2 c _ {0} e ^ {- i \omega T}}{2 \pi i \omega} \\ \end{array}
$$

由于在上半 $\omega$ 平面, 当 $|\omega|$ 沿某一射线趋于无穷大时 $e^{i\omega a}$ 一致趋于零或为常数, 所以可以令

$$
G _ {T} ^ {(1)} (i \omega) = \frac {\omega e ^ {i \omega \alpha} - \omega F _ {T} ^ {(1)} (i \omega)}{\omega (\omega - i) (\omega + i)} + \frac {c _ {0}}{i \pi \omega} = \frac {\omega e ^ {i \omega \alpha} - \omega F _ {T} ^ {(1)} (i \omega) + \frac {c _ {0}}{i \pi} (\omega - i) (\omega + i)}{\omega (\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {- \omega F _ {T} ^ {(2)} (i \omega)}{\omega (\omega - i) (\omega + i)} - \frac {c _ {0}}{i \pi \omega} = \frac {- \left[ \omega F _ {T} ^ {(2)} (i \omega) - \frac {c _ {0}}{i \pi} (\omega - i) (\omega + i) \right]}{\omega (\omega - i) (\omega + i)}
$$

根据最优条件(1)和(2)， $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 只可能有 $\omega=0$ 的极点，不可能再有其他极点。根据最优条件(3)可得出 $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 的形式为

$$
F _ {T} ^ {(1)} (i \omega) = \frac {a _ {1} \omega + a _ {0}}{\omega}, \quad F _ {T} ^ {(2)} (i \omega) = \frac {b _ {1} \omega + b _ {0}}{\omega}
$$

这时

$$
\stackrel {\circ} {F} _ {T} (i \omega) = \frac {a _ {1} \omega + a _ {0} + e ^ {- i \omega T} (b _ {1} \omega + b _ {0})}{\omega}
$$

$$
G _ {T} ^ {(1)} (i \omega) = \frac {\omega e ^ {i \omega a} - (a _ {1} \omega + a _ {0})}{\omega (\omega - i) (\omega + i)} + \frac {c _ {0}}{i \pi \omega}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {- (b _ {1} \omega + b _ {0})}{\omega (\omega - i) (\omega + i)} - \frac {c _ {0}}{i \pi \omega}
$$

根据最优条件(1)和(2)， $F_{T}(i\omega)$ 的分子在 $\omega=0$ 时应等于零， $G_{T}^{(1)}(i\omega)$ 的分子在 $\omega=i$ 和 $\omega=0$ 时应等于零， $G_{T}^{(2)}(i\omega)$ 的分子在 $\omega=-i$ 和 0 时应等于零，因此得到

$$
\left\{ \begin{array}{l} a _ {0} + b _ {0} = 0 \\ i e ^ {- a} - a _ {1} i - a _ {0} = 0 \\ - a _ {0} + \frac {c _ {0}}{i \pi} = 0 \\ - b _ {1} i + b _ {0} = 0 \\ - b _ {0} - \frac {c _ {0}}{i \pi} = 0 \end{array} \right.
$$

再由最优条件(4)， $\left[F_{T}(s)\right]_{s=0}=\left[F_{1}(s)\right]_{s=0}=1$ ，就得到

$$
a _ {1} + (- i T) b _ {0} + b _ {1} = 1
$$

现有五个未知数 $a_{0}, a_{1}, b_{0}, b_{1}$ 和 $c_{0}$ ，六个线性方程，其中有一个是不独立的，这样可以解出未知数：

$$
b _ {0} = \frac {1 - e ^ {- \alpha}}{2 + T} i, \quad b _ {1} = \frac {1 - e ^ {- \alpha}}{2 + T}
$$

$$
a _ {0} = - \frac {1 - e ^ {- a}}{2 + T} i, \quad a _ {1} = \frac {1 + e ^ {- a} (1 + T)}{2 + T} = e ^ {- a} + \frac {1 - e ^ {- a}}{2 + T}
$$

$$
c _ {0} = - \left(\frac {1 - e ^ {- \alpha}}{2 + T}\right) \pi
$$

最后得到最优的有限记忆线性过滤器的传递函数是

$$
\stackrel {\circ} {F} _ {T} (s) = e ^ {- \alpha} + \frac {1 - e ^ {- \alpha}}{2 + T} \left[ (1 + e ^ {- s T}) + \frac {1}{s} (1 - e ^ {- s T}) \right]
$$

最优脉冲响应函数就是

$$
\stackrel {\circ} {h} _ {T} (t) = \frac {1 - e ^ {- \alpha}}{2 + T} [ \delta (t) + 1 (t) - 1 (t - T) + \delta (t - T) ] + e ^ {- \alpha} \delta (t)
$$

其中 $1(t)$ 为单位阶跃函数， $1(t)=\left\{\begin{aligned}0,&t\leqslant0\\ 1,&t>0\end{aligned}\right.$ $h_{T}(t)$ 的图形见图 15.8-1。最优过滤器 $F_{T}(s)$ 的物理意义很明显，因为不存在噪声，当 $\alpha=0$ 时最优过滤器的输出 $Y(t)$ 就是输入信号 $X(t)$ 在 t 时刻的值，当 $a\neq0$ 时，最优过滤器的输出 $Y(t)$ 就是输入信号 $X(t)$ 在 t 时刻的值和在闭区间 $[t-T,t]$ 内输入信号 $X(t)$ 的等加权平均

> 此处省略原书 **图 15.8-1**

值之和。因为输入信号的数学期望是常数所以是等加权的，加权的系数 $\frac{1 - e^{-\alpha}}{2 + T}$ 是 $\alpha$ 的递增函数，也是有限记忆时间 $T$ 的递降函数，当 $T \gg 2$ 时加权系数几乎与 $T$ 成反比。加权系数的特性是由信号的统计特性决定的。

例 2. 假设输入端的有用信号中没有随机分量, 它只是时间 t 的线性函数 $g(t)=g_{0}+g_{1}t$ ，参数 $g_{0}$ 和 $g_{1}$ 是未知常数，噪声是数学期望为零的平稳随机过程，功率谱密度 $\Phi_{N}=\frac{1}{1+\omega^{2}}$ ，现要求设计最优的有限记忆为 T 的线性预测过滤器。同样，根据假设，我们得到下列原始数据

$$
\Phi_ {X} (\omega) = \Phi_ {N} (\omega) = \frac {1}{1 + \omega^ {2}}, \quad \Phi_ {F} (\omega) = \Phi_ {Y _ {1} X} (\omega) = 0
$$

$$
F _ {1} (s) = e ^ {\alpha s}, \quad \alpha \geqslant 0, \left[ \frac {d}{d s} F _ {1} (s) \right] _ {s = 0} = \alpha , \quad [ F _ {1} (s) ] _ {s = 0} = 1
$$

$$
f _ {0} (\omega) = \frac {1 - e ^ {- i \omega T}}{2 \pi i \omega}, \quad f _ {1} (\omega) = \frac {e ^ {- i \omega T} - 1}{2 \pi \omega^ {2}} - \frac {T e ^ {- i \omega T}}{2 \pi i \omega}
$$

因此我们就得到

$$
\begin{array}{l} G _ {T} (i \omega) = G _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} G _ {T} ^ {(2)} (i \omega) \\ = \frac {- \left[ F _ {T} ^ {(1)} (i \omega) + e ^ {- i \omega T} F _ {T} ^ {(2)} (i \omega) \right]}{(\omega - i) (\omega + i)} + c _ {0} \frac {1 - e ^ {- i \omega T}}{i \pi \omega} + c _ {1} \left[ \frac {e ^ {- i \omega T} - 1}{\pi \omega^ {2}} - \frac {T e ^ {- i \omega T}}{i \pi \omega} \right] \\ \end{array}
$$

令

$$
G _ {T} ^ {(1)} (i \omega) = - \frac {F _ {T} ^ {(1)} (i \omega) \omega^ {2}}{\omega^ {2} (\omega - i) (\omega + i)} + \frac {- c _ {1} - c _ {0} i \omega}{\pi \omega^ {2}}
$$

$$
G _ {T} ^ {(2)} (i \omega) = - \frac {F _ {T} ^ {(2)} (i \omega) \omega^ {2}}{\omega^ {2} (\omega - i) (\omega + i)} + \frac {c _ {1} + c _ {1} i \omega T + c _ {0} i \omega}{\pi \omega^ {2}}
$$

根据最优条件(1)和(2)中关于 $F_{T}(i\omega)$ 和 $G_{T}^{(1)}(i\omega)G_{T}^{(2)}(i\omega)$ 极点分布的规则， $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(1)}(i\omega)$ 只可能有相同的二重极点 $\omega=0$ ，除此以外不可能再有其他极点，再根据最优条件(3)可得出 $F_{T}^{(1)}(i\omega)$ 和 $F_{T}^{(2)}(i\omega)$ 的形式为

$$
F _ {T} ^ {(1)} (i \omega) = \frac {a _ {2} \omega^ {2} + a _ {1} \omega + a _ {0}}{\omega^ {2}}
$$

$$
F _ {T} ^ {(2)} (i \omega) = \frac {b _ {2} \omega^ {2} + b _ {1} \omega + b _ {0}}{\omega^ {2}}
$$

这时

$$
\stackrel {\circ} {F} _ {T} (i \omega) = \frac {(a _ {2} \omega^ {2} + a _ {1} \omega + a _ {0}) + e ^ {- i \omega T} (b _ {2} \omega^ {2} + b _ {1} \omega + b _ {0})}{\omega^ {2}}
$$

$$
G _ {T} ^ {(1)} (i \omega) = \frac {- \left(a _ {2} \omega^ {2} + a _ {1} \omega + a _ {0}\right) + \frac {1}{\pi} (- c _ {1} - c _ {0} i \omega) (\omega^ {2} + 1)}{\omega^ {2} (\omega - i) (\omega + i)}
$$

$$
G _ {T} ^ {(2)} (i \omega) = \frac {- \left(b _ {2} \omega^ {2} + b _ {1} \omega + b _ {0}\right) + \frac {1}{\pi} \left(c _ {1} + c _ {1} i \omega T + c _ {0} i \omega\right) \left(\omega^ {2} + 1\right)}{\omega^ {2} (\omega - i) (\omega + i)}
$$

根据最优条件(1)和(2)， $F_{T}(i\omega)$ 的分子及其导数在 $\omega=0$ 时应等于零， $G_{T}^{(1)}(i\omega)$ 的分子在 $\omega=i$ 和 $\omega=0$ 以及它的导数在 $\omega=0$ 时应等于零， $G_{T}^{(2)}(i\omega)$ 的分子在 $\omega=-i$ 和 $\omega=0$ 以及它的导数在 $\omega=0$ 时应等于零, 因此我们得到

$$
\left\{ \begin{array}{l} a _ {0} + b _ {0} = 0 \\ a _ {1} + (- i T) b _ {0} + b _ {1} = 0 \\ - (a _ {0} - a _ {2} + i a _ {1}) = 0 \\ - a _ {0} - \frac {c _ {1}}{\pi} = 0 \\ - a _ {1} - \frac {c _ {0}}{\pi} i = 0 \\ - (b _ {0} - b _ {2} - i b _ {1}) = 0 \\ - b _ {0} + \frac {c _ {1}}{\pi} = 0 \\ - b _ {1} + \frac {i c _ {1} T}{\pi} + \frac {i c _ {0}}{\pi} = 0 \end{array} \right.
$$

再由最优条件(4)， $F_{T}(i\omega)\big|_{\omega=0}=F_{1}(i\omega)\big|_{\omega=0}=1$

$$
\left. \frac {\partial}{\partial \omega} \stackrel {\circ} {F} _ {T} (i \omega) \right| _ {\omega = 0} = \left. \frac {\partial}{\partial \omega} F _ {1} (i \omega) \right| _ {\omega = 0} = i \alpha
$$

可知

$$
\left\{ \begin{array}{l} 2 a _ {2} - T ^ {2} b _ {0} - i T b _ {1} + 2 b _ {2} = 2 \\ - i b _ {0} T ^ {3} - T ^ {2} b _ {1} - 6 i T b _ {2} = 6 i \alpha \end{array} \right.
$$

这样就得到八个未知数 $a_0, a_1, a_2, b_0, b_1, b_2, c_0, c_1$ ，和十个方程式，其中两个方程式是不独立的，于是解出

$$
b _ {0} = \frac {- (T ^ {2} + 6 T + 3 \alpha T + 1 2 \alpha)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T} a _ {0} = \frac {T ^ {2} + 6 T + 3 \alpha T + 1 2 \alpha}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T}
$$

$$
b _ {1} = \frac {i (T ^ {3} + 6 T - 3 \alpha T ^ {2} - 6 \alpha T)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T} \quad a _ {1} = \frac {- i (2 T ^ {3} + 6 T ^ {2} + 6 T + 6 \alpha T)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T}
$$

$$
b _ {2} = \frac {T ^ {3} - \left(T ^ {2} + 3 \alpha T ^ {2} + 9 \alpha T + 1 2 T\right)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T} \quad a _ {2} = \frac {2 T ^ {3} + 7 T ^ {2} + 1 2 T + 9 \alpha T + 1 2 \alpha}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T}
$$

$$
c = \frac {\pi (2 T ^ {3} + 6 T ^ {2} + 6 T + 6 \alpha T)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T} \quad c _ {1} = - \frac {\pi (T ^ {2} + 6 T + 3 \alpha T + 1 2 \alpha)}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T}
$$

最优过滤器的传递函数就是

$$
\stackrel {\circ} {F} _ {T} (s) = a _ {2} + \frac {i a _ {1}}{s} + \frac {- a _ {0}}{s ^ {2}} + e ^ {- s T} \left[ b _ {2} + \frac {i b _ {1}}{s} + \frac {- b _ {0}}{s ^ {2}} \right]
$$

最优脉冲响应函数就是

$$
\begin{array}{l} h _ {T} (t) = a _ {2} \delta (t) + \left(i a _ {1} - a _ {0} t\right) \cdot 1 (t) + \left[ i b _ {1} - b _ {0} (t - T) \right] \cdot 1 (t - T) + b _ {2} \delta (t - T) \\ = \frac {T ^ {2} + 6 T + 3 \alpha T + 1 2 \alpha}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T} [ \delta (t) - \delta (t - T) ] + h _ {T} (t) \\ \end{array}
$$

其中

$$
h _ {T} (t) = \left\{ \begin{array}{l l} \frac {(2 T ^ {3} + 6 T ^ {2} + 6 T + 6 \alpha T) - (T ^ {2} + 6 T + 3 \alpha T + 1 2 \alpha) t}{T ^ {4} + 6 T ^ {3} + 9 T ^ {2} + 1 2 T}, & 0 \leqslant t \leqslant T \\ 0, \quad t <   0, t > T \end{array} \right.
$$

例 3. 假设平稳随机过程的数学期望是某个常数, 功率谱密度仍是 $\frac{1}{1 + \omega^{2}}$ , 那么怎样根据平稳过程在有限时间区间上测得的值来估计此过程的数学期望, 并使估计的均方误差最小? 我们把它化为类似于例 2 的问题。这时信号是某个未知常数; 把平稳过程与它的数学期望的差看作为噪声, 功率谱密度 $\Phi_{X}(\omega) = \Phi_{N}(\omega) = \frac{1}{1 + \omega^{2}}$ , 并且预测时间 $\alpha = 0$ 。根据这些条件可以求出

$$
a _ {0} = b _ {0} = 0, \quad a _ {1} = - b _ {1} = \frac {1}{i (2 + T)}, \quad a _ {2} = b _ {2} = \frac {1}{2 + T}
$$

因此，数学期望的估计应是

$$
\hat {m} _ {T} = \frac {1}{2 + T} \left[ X (t) + X (t - T) + \int_ {0} ^ {T} X (t - \tau) d \tau \right]
$$

这时估计的方差为

$$
\sigma_ {m _ {T}} ^ {2} = \frac {2 \pi}{2 + T}
$$

可以看出，当 T 趋于无穷大时估计的均方误差 $\sigma_{\hat{m}_{T}}^{2}$ 趋近于零， $\lim_{T\to\infty}\left[\sigma_{\hat{m}_{T}}^{2}T\right]=2\pi$ 。如果我们只用

$$
\mu_ {T} = \frac {1}{T} \int_ {0} ^ {T} X (t - \tau) d \tau
$$

来估计数学期望，即把有限区间内测得的值作简单平均，那么这种估计仍是无偏估计，但是估计的均方误差要比最优估计的大

$$
\sigma_ {\mu_ {T}} ^ {2} = \frac {2 \pi}{T ^ {2}} (e ^ {- T} - 1 + T) > \sigma_ {\widehat {m} _ {T}} ^ {2}
$$

可以看出当 $T \to \infty$ 时 $\lim_{T \to \infty} \frac{\sigma_{m_T}^2}{\sigma_{u_T}^2} = 1$ 。

假设有一个平稳随机过程，它的功率谱密度是 $\omega$ 的有理函数，现在要估计此平稳随机过程的数学期望，那么最优估计的均方误差 $\sigma_{m_{T}}^{2}$ 仍应满足下列极限关系

$$
\lim _ {T \rightarrow \infty} \left[ \sigma_ {\hat {m} _ {T}} ^ {2} T \right] = 2 \pi \Phi_ {X} (0)
$$

$$
\lim _ {T \to \infty} \frac {\sigma_ {m} ^ {2}}{\sigma_ {\mu T} ^ {2}} = 1
$$

#### 15.9 最优检测过滤器

在很多控制系统中，常常需要在随机噪声的干扰作用下把信号 $f(t)$ 探测出来。例如，信号检测系统就是要在随机噪声干扰作用下判断噪声中是否夹杂有信号或估计信号中的参数值。在这类控制系统中一般总是附有一个检测过滤器，它的作用就是加强通过过滤器后信号与噪声的强度比，然后使检测过程更加准确。例如，在脉冲制雷达中如果存在回波脉冲而且信号中不夹杂噪声，那么它的形状一般是固定的。当回波脉冲出现时信号达到它的最大强度。如果在信号中夹杂有随机噪声，回波脉冲在 $t_0$ 时刻出现，那么夹杂有噪声的信号在通过过滤器后在 $t_0$ 时刻应给出最小的信号变形，即过滤器输出的信号与噪声的强度比在 $t_0$ 时刻应最大。

假设过滤器的输入是夹杂有噪声的信号

$$
X (t) = f (t) + N (t) \tag {15.9-1}
$$

信号 $f(t)$ 是某个确定的时间函数，噪声 $N(t)$ 是数学期望为零的平稳随机过程，它的功率谱密度是 $\Phi_{N}(\omega)$ 。如果过滤器是线性的，它的输出是夹杂有噪声 $\tilde{N}(t)$ 的被变换了的信号 $\tilde{f}(t)$ ，其中 $\tilde{f}(t)$ 和 $\tilde{N}(t)$ 分别是信号 $\tilde{f}(t)$ 和噪声 $N(t)$ 单独作用于过滤器时的输出。显然，过滤器必须是稳定的，物理可实现的，而且输出的噪声应是方差有界的，即过滤器的脉冲响应函数 $h(t)$ 满足下列条件：

(1) 当 t<0 时, $h(t)=0$ 。

(2) $\int_{0}^{\infty}|h(t)|dt < \infty$ 。

(3) $\int_{0}^{\infty}\int_{0}^{\infty}h(t_1)h(t_2)r_N(t_1 - t_2)dt_1dt_2 <   \infty .$

最优检测过滤器应使得经过过滤作用后的信号 $f(t)$ 在 $t_{0}$ 时刻的值实际上和 $f(t_{0})$ 相同，即满足约束条件

$$
\tilde {f} (t _ {0}) = f (t _ {0}) = \text { const } \tag {15.9-2}
$$

同时输出的噪声的强度最小

$$
\overline {{\left[ \widetilde {N} (t) \right] ^ {2}}} = \min \tag {15.9-3}
$$

因此问题就可以化为在 $f(t), t_0$ 以及 $\Phi_N(\omega)$ 已给定的情况下，确定最优检测过滤器的传递函数 $\stackrel{\circ}{F}(s)$ 或脉冲响应函数 $\stackrel{\circ}{h}(t)$ ，使得与它相应的 $\stackrel{\sim}{f}(t)$ 和 $N(t)$ 满足

$$
\{\overbrace {\left[ N (t _ {0}) \right] ^ {2}} - 2 \lambda f (t _ {0}) \} = \min _ {h (t)} \{\overline {{\left[ N (t) \right] ^ {2}}} - 2 \lambda f (t _ {0}) \} \tag {15.9-4}
$$

其中 $\lambda$ 是拉格朗日乘子, 由约束条件式(15.9-2)确定。显然, 当条件式(15.9-2)和(15.9-3)满足时

$$
\widetilde {f} ^ {2} \left(t _ {0}\right) / \overline {{\left[ \widetilde {N} \left(t _ {0}\right) \right] ^ {2}}} = \max
$$

即在 $t_{0}$ 时刻信号与噪声的强度比最大。这一类问题可以化成第 15.8 节中已讨论过的问题来解决。下面叙述扎弟(Zadeh)和拉格基尼(Ragazzini)解决此问题的结果 $^{[31(2)]}$ 。

如果随机噪声 $N(t), -\infty < t < \infty$ 的功率谱密度 $\Phi_{N}(\omega)$ 能够分解成

$$
\Phi_ {N} (\omega) = \Psi (i \omega) \Psi (- i \omega) \tag {15.9-5}
$$

其中 $\Psi(i\omega)$ 的零点和极点都在上半 $\omega$ 平面上。我们引进成型滤波器 $1/\Psi(s)$ ，它的输出信号和噪声分别是 $f'(t)$ 和 $N'(t)$ （见图 15.9-1）。假设确定的信号 $f(t)$ ， $-\infty<t<\infty$ 的傅里叶变换是 $S(i\omega)$

$$
S (i \omega) = \int_ {- \infty} ^ {\infty} f (t) e ^ {- i \omega t} d t \tag {15.9-6}
$$

那么

$$
f ^ {\prime} (t) = \frac {1}{2 \pi} \int_ {- \infty} ^ {\infty} \frac {S (i \omega)}{\Psi (i \omega)} e ^ {i \omega t} d \omega \tag {15.9-7}
$$

> 此处省略原书 **图 15.9-1**

此时 $N'(t)$ 的功率谱密度 $\Phi_{N'}(\omega)=1$ ，它的相关函数

$$
r _ {N ^ {\prime}} (\sigma) = \pi \delta (\sigma) \tag {15.9-8}
$$

假定输入为 $f'(t)$ 和 $N'(t)$ 时最优检测过滤器的传递函数是 $\dot{F}'(s)$ ，脉冲响应函数是 $\dot{h}'(t)$ ，那么

$$
\stackrel {\circ} {F} (s) = \stackrel {\circ} {F} ^ {\prime} (s) \frac {1}{\Psi (s)} \tag {15.9-9}
$$

于是最优检测过滤器的输出 $\stackrel{\circ}{f}(t)+\stackrel{\circ}{N}(t)$ 可以写成

$$
\stackrel {\circ} {f} (t) = \int_ {0} ^ {\infty} \stackrel {\circ} {h} ^ {\prime} (\sigma) f ^ {\prime} (t - \sigma) d \sigma \tag {15.9-10}
$$

以及

$$
\stackrel {\circ} {N} (t) = \int_ {0} ^ {\infty} \stackrel {\circ} {h} ^ {\prime} (\sigma) N ^ {\prime} (t - \sigma) d \sigma \tag {15.9-11}
$$

输出噪声的均方值就是

$$
\overline {{\left[ \stackrel {\circ} {N} (t) \right] ^ {2}}} = \int_ {0} ^ {\infty} \int_ {0} ^ {\infty} \stackrel {\circ} {h} ^ {\prime} (\sigma_ {1}) \stackrel {\circ} {h} ^ {\prime} (\sigma_ {2}) r _ {N ^ {\prime}} (\sigma_ {1} - \sigma_ {2}) d \sigma_ {1} d \sigma_ {2}
$$

考虑到 $N'(t)$ 的相关函数的特性可以写出

$$
\overline {{\left[ \widetilde {N} (t) \right] ^ {2}}} = \pi \int_ {0} ^ {\infty} \left[ \stackrel {\circ} {h} ^ {\prime} (\tau) \right] ^ {2} d \tau \tag {15.9-12}
$$

利用方程(15.9-10)和(15.9-12)可以把方程(15.9-4)写成

$$
\begin{array}{l} \pi \int_ {0} ^ {\infty} \left[ \stackrel {\circ} {h} ^ {\prime} (t) \right] ^ {2} d t - 2 \lambda \int_ {0} ^ {\infty} \stackrel {\circ} {h} ^ {\prime} (t) f ^ {\prime} (t _ {0} - t) d t \\ = \min _ {h ^ {\prime} (t)} \left\{\pi \int_ {0} ^ {\infty} \left[ h ^ {\prime} (t) \right] ^ {2} d t - 2 \lambda \int_ {0} ^ {\infty} h ^ {\prime} (t) f ^ {\prime} (t _ {0} - t) d t \right\} \tag {15.9-13} \\ \end{array}
$$

方程(15.9-13)对任意确定的函数 $f'(t_{0}-t)$ 成立的必要和充分条件是

$$
\stackrel {\circ} {h} ^ {\prime} (t) = \frac {\lambda}{\pi} f ^ {\prime} (t _ {0} - t), \quad t \geqslant 0 \tag {15.9-14}
$$

自然，实际上可实现的系统当 t<0 时 $h'(t)\equiv0$ 。换句话说，对于任何 $t>0,F'(s)$ 对 $\delta(t)$ 的最优反应函数恒等于信号 $f'(t)$ 对 $t_{0}/2$ 的镜像（见图 15.9-2)。对于白色噪声的特殊情况，在早些时候这个结果就已经知道了，首先推导出这个结果的是诺斯(North) $^{[20]}$ 。

由方程(15.9-14)和(15.9-7)可得到

$$
\begin{array}{l} \stackrel {\circ} {F} ^ {\prime} (i \omega) = \int_ {0} ^ {\infty} \stackrel {\circ} {h} ^ {\prime} (t) e ^ {- i \omega t} d t = \frac {\lambda}{\pi} \int_ {0} ^ {\infty} f ^ {\prime} (t _ {0} - t) e ^ {- i \omega t} d t \\ = \frac {\lambda}{2 \pi^ {2}} \int_ {0} ^ {\infty} e ^ {- i \omega t} d t \int_ {- \infty} ^ {\infty} \frac {S (- i \omega)}{\Psi (- i \omega)} e ^ {i \omega (t - t _ {0})} d \omega \tag {15.9-15} \\ \end{array}
$$

> 此处省略原书 **图 15.9-2**

此结果与方程(15.5-18)的形式类似，所以

$$
\stackrel {\circ} {F} ^ {\prime} (s) = \frac {\lambda}{\pi} \left[ \frac {e ^ {- s t _ {0}} S (- s)}{\Psi (- s)} \right] _ {+} \tag {15.9-16}
$$

再根据方程(15.9-8)就得到输入为 $f(t)$ 和 $N(t)$ 时最优检测过滤器的传递函数

$$
\stackrel {\circ} {F} (s) = \frac {\lambda}{\pi \Psi (s)} \left[ \frac {e ^ {- s t _ {0}} S (- s)}{\Psi (- s)} \right] _ {+} \tag {15.9-17}
$$

其中 $\lambda$ 由约束条件(15.9-2)确定。 $[ ]_{+}$ 仍然表示只取极点在左半 S 平面的那一部分分量，也就是要使传递函数 $\dot{F}(s)$ 是稳定的，实际上可实现的。如果要求的最优检测过滤器是有限记忆的，那么根据第 15.8 节中的方法也不难求出最优的 $\dot{F}_{T}(s)$ 。对于白色噪声 $N(t)$ 的有限记忆最优检测过滤器的脉冲响应函数是

$$
\dot {h} _ {T} (t) = \left\{ \begin{array}{l l} \frac {\lambda}{\pi} f (t _ {0} - t), & t _ {0} \leqslant t \leqslant T \\ 0, & t <   0, t > T \end{array} \right. \tag {15.9-18}
$$

#### 15.10 非平稳随机过程的最优线性过滤

在有的工程系统中会遇到非平稳的随机过程，它的数学期望可以是零或某种时间函数，重要的是它的相关函数是两个变量的函数。对这种非平稳过程要求进行滤波。本节将介绍对非平稳过程最优过滤的设计方法。最优过滤器将在线性变系数系统中去寻找，最优的准则仍是真实过滤器的输出是无偏的，且它与理想输出之间的均方误差最小。

我们先从类似于第 15.5 节的简单情况开始。假定系统的输入 $X(t)$ 是有用信号 $F(t)$ 和噪声的叠加

$$
X (t) = F (t) + N (t) \tag {15.10-1}
$$

它们都是数学期望为零方差有界的非平稳随机过程。设过滤器的理想输出 $Y_{1}(t)$ 是信号 $F(t), -\infty < t < \infty$ 的已知线性变换

$$
Y _ {1} (t) = \int_ {- \infty} ^ {\infty} h _ {1} (t, \sigma) F (\sigma) d \sigma \tag {15.10-2}
$$

其中 $h_{1}(t,\tau)$ 对任意 $t,(0\leqslant t<\infty)$ 是在 $-\infty<\sigma<\infty$ 上绝对可积的函数或是 $\delta$ 函数及其高阶导数。设输入作用是从 t=0 开始作用于过滤器的，它的输出 $Y(t)$ 为

$$
Y (t) = \int_ {0} ^ {t} h (t, \sigma) X (\sigma) d \sigma , \quad 0 \leqslant t <   \infty \tag {15.10-3}
$$

其中 $h(t,\sigma)$ 是过滤器的脉冲响应函数, 它满足下列三个条件:

(1) 当 $\sigma < t$ 时, $h(t, \sigma) = 0$ 。

(2) 对任何 $0 \leqslant t < \infty, \int_{0}^{t} |h(t, \sigma)| d\sigma < \infty$ 。

(3) $\int_{0}^{t}\int_{0}^{t}h(t,\sigma_1)h(t,\sigma_2)r_X(\sigma_1 - \sigma_2)d\sigma_1d\sigma_2 <   \infty .$

这就是说，系统是物理上可以实现的，稳定的且输出是均方有界的。最优过滤问

题就是要在这一类系统中寻找最优的系统 $h(t,\sigma)$ ，使其相应的输出满足

$$
\left\| Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right\| ^ {2} = \min _ {h (t, \sigma)} \left\| Y _ {1} (t) - Y (t) \right\| ^ {2}, \quad 0 \leqslant t <   \infty \tag {15.10-4}
$$

同样，根据希尔伯特空间的几何原理，要满足条件式(15.10-4), $Y_{1}(t)-Y(t)$ 必须是 $Y_{1}(t)$ 到子空间 $H_{X}^{t}$ 的垂线, $H_{X}^{t}$ 是由所有可能的过滤器 $h(t,\sigma)$ 的输出及其均方极限组成的，因此垂线与子空间 $H_{X}^{t}$ 内任一向量直交

$$
\langle Y _ {1} (t) - \dot {Y} (t), X (u) \rangle = 0, \quad 0 \leqslant u \leqslant t \tag {15.10-5}
$$

根据数量积的定义我们得到

$$
r _ {Y _ {1} X} (t, u) = r _ {Y X} ^ {\circ} (t, u), \quad 0 \leqslant u \leqslant t \tag {15.10-6}
$$

再根据线性变系数系统输出输入的互相关函数和系统脉冲响应函数的关系，可以把方程(15.10-6)写为

$$
r _ {Y _ {1} X} (t, u) = \int_ {- \infty} ^ {t} h _ {1} (t, \sigma) r _ {F X} (\sigma , u) d u = \int_ {0} ^ {t} h (t, \sigma) r _ {X} (\sigma , u) d u, \quad 0 \leqslant u \leqslant t \tag {15.10-7}
$$

由于输入的各种统计特性（相关函数）和 $h_{1}(t,\sigma)$ 已给定, 故方程(15.10-7)的左边已给定, 右边积分号内 $r_{X}(\sigma,u)$ 也给定, 因此求解 $\dot{h}(t,\sigma)$ 即意味着求解伏尔得拉型积分方程(15.10-7)。这类方程要得到解析解, 在一般情况下是比较困难的, 只能用逐次逼近法或数值求解法。输入通过最优过滤器后最小的均方误差为 $\left\|Y_{1}(t)-\dot{Y}(t)\right\|^{2}$ , 把它展开后得到

$$
\sigma_ {E} ^ {2} (t) = \left\| Y _ {1} (t) - \overset {\circ} {Y} (t) \right\| ^ {2} = r _ {Y _ {1}} (t, t) - 2 r _ {Y _ {1}} \overset {\circ} {Y} (t, t) + r _ {Y} ^ {\circ} (t, t)
$$

因为

$$
r _ {Y _ {1} \stackrel {\circ} {Y}} (t, t) = \int_ {0} ^ {t} r _ {Y _ {1} X} (t, \sigma) \stackrel {\circ} {h} (t, \sigma) d \sigma
$$

$$
r _ {Y} ^ {\circ} (t, t) = \int_ {0} ^ {t} r _ {Y X} ^ {\circ} (t, \sigma) \stackrel {\circ} {h} (t, \sigma) d \sigma
$$

根据等式(15.10-6)就可以得到 $r_{Y_{1}\hat{Y}}(t,t)=r_{\hat{Y}}(t,t)$ ，所以最后得到

$$
\begin{array}{l} \sigma_ {E} ^ {2} = r _ {Y _ {1}} (t, t) - r _ {Y} ^ {\circ} (t, t) \\ = \overline {{\left[ Y _ {1} (t) \right] ^ {2}}} - \int_ {0} ^ {t} \int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma_ {1}) \stackrel {\circ} {h} (t, \sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \tag {15.10-8} \\ \end{array}
$$

假定系统的输入 $X(t)$ 包含三个部分，除了数学期望为零方差有界的非平稳随机有用信号 $F(t)$ 和噪声 $N(t)$ 外还有用非随机的时间函数 $g(t)$ 表示的有用信号, $g(t)$ 在有限时间区间 $[0, b]$ 内可以用 t 的有限次幂多项式表示

$$
g (t) = \sum_ {k = 0} ^ {l} g _ {k} t ^ {k}, \quad 0 \leqslant t \leqslant b \tag {15.10-9}
$$

其中 $g_{k}, k=0,1,\cdots,l$ 为未知常数。过滤器的理想输出 $Y_{1}(t)$ 是有用信号的已知线性变换

$$
Y _ {1} (t) = \int_ {0} ^ {b} h _ {1} (t, \sigma) [ g (\sigma) + F (\sigma) ] d \sigma , \quad 0 \leqslant t \leqslant b \tag {15.10-10}
$$

其中 $h_{1}(t,\sigma)$ 对任何 $0 \leqslant t \leqslant b$ 来说是在 $[0,b]$ 上给定的某个绝对可积函数或是 $\delta$ 函数及其高阶导数，并且

$$
\int_ {0} ^ {b} \int_ {0} ^ {b} h _ {1} (t, \sigma_ {1}) h _ {1} (t, \sigma_ {2}) r _ {F} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} <   \infty
$$

设输入作用 $X(t)$ 是从 t=0 的时刻开始作用于过滤器的, 它的输出 $Y(t)$ 为

$$
Y (t) = \int_ {0} ^ {b} h r (t, \sigma) X (\sigma) d \sigma , \quad 0 \leqslant t \leqslant b \tag {15.10-11}
$$

其中 $h_{T}(t,\sigma)$ 是过滤器的脉冲响应函数, 它满足下列三个条件:

(1) 当 $\sigma > t$ 或 $\sigma < t - T$ 时, $h_{T}(t, \sigma) = 0$ 。

(2) 对任何 $0 \leqslant t \leqslant b, \int_{0}^{t} |h_T(t, \sigma)| d\sigma < \infty$ 。

(3) $\int_{0}^{t}\int_{0}^{t}h_{T}(t,\sigma_{1})h_{T}(t,\sigma_{2})r_{X}(\sigma_{1},\sigma_{2})d\sigma_{1}d\sigma_{2}<\infty$ 。

最优过滤问题就是要在这一类系统中寻找最优的 $h_{T}(t,\sigma)$ ，使得其相应的输出 $\dot{Y}(t)$ 对任何 $t, T \leqslant t \leqslant b$ ，满足无偏条件

$$
\overline {{Y _ {1} (t) - \stackrel {\circ} {Y} (t)}} = 0
$$

和均方误差最小

$$
\overline {{\left[ Y _ {1} (t) - \stackrel {\circ} {Y} (t) \right] ^ {2}}} = \min _ {h _ {T} (t, \sigma)} \overline {{\left[ Y _ {1} (t) - Y (t) \right] ^ {2}}}
$$

根据等式(15.10-10)和(15.10-11)所有满足无偏条件的过滤器 $h_{T}(t,\sigma)$ 对任意固定的 $T \leqslant t \leqslant b$ 必须满足

$$
\int_ {t - T} ^ {t} h _ {T} (t, \sigma) g (\sigma) d \sigma = \int_ {0} ^ {b} h _ {1} (t, \sigma) g (\sigma) d \sigma \tag {15.10-12}
$$

由于 $g_{k}$ 是未知常数, 故条件式(15.10-12)就等于条件组

$$
\int_ {t - T} ^ {t} h _ {T} (t, \sigma) \sigma^ {k} d \sigma = \int_ {0} ^ {b} h _ {1} (t, \sigma) \sigma^ {k} d \sigma , \quad k = 0, 1, \dots , l \tag {15.10-13}
$$

最优的 $h_{T}(t,\sigma)$ 必须在满足式(15.10-13)的 $h_{T}(t,\sigma)$ 中去找。

同样，所有满足于条件(1)，(2)，(3)和条件组式(15.10-13)的过滤器 $h_T(t,\sigma)$ 的输出 $Y(t) - \overline{Y(t)}$ ， $T\leqslant t\leqslant b$ ，在随机变量的希尔伯特空间内组成了一个超平面 $Q_{X}$ ，最优的输出 $\dot{Y} (t)$ 使得向量 $(Y_{1}(t) - \dot{Y} (t))$ 是向量 $(Y_{1}(t) - \overline{Y_{1}(t)})$ 到超平面 $Q_{X}$ 的垂线，它与任何位于超平面上的线段直交

$$
\langle Y _ {1} (t) - \stackrel {\circ} {Y} (t), Y (t) - \stackrel {\circ} {Y} (t) \rangle = 0 \tag {15.10-14}
$$

根据数量积的定义，把式(15.10-14)展开后得到

$$
\int_ {t - T} ^ {t} h _ {T} (t, \sigma) \left[ r _ {Y _ {1} X} (t, \sigma) - r _ {Y X} ^ {*} (t, \sigma) \right] d \sigma = r _ {Y _ {1} Y} (t, t) - r _ {Y} ^ {*} (t, t) \tag {15.10-15}
$$

其中 $h_T(t, \sigma)$ 是满足条件(1)，(2)，(3)和式(15.10-13)的任意函数。等式(15.10-15)的右边是待定常数，左边的 $[r_{Y_1X}(t, \sigma) - r_{Y^X}(t, \sigma)]$ 与 $\dot{h}_T(t, \sigma)$ 有关。 $\dot{h}_T(t, \sigma)$ 也必须满足条件(1)，(2)，(3)和式(15.10-13)，而条件组式(15.10-13)的右边都是些确定的常数，所以得出

$$
r _ {Y _ {1} X} (t, \sigma) - r _ {Y ^ {\circ} X} (t, \sigma) = \sum_ {k = 0} ^ {l} c _ {k} (t) \sigma^ {k}, \quad t - T \leqslant \sigma \leqslant t \tag {15.10-16}
$$

其中 $c_{k}(t)$ 是待定的 $t$ 的函数。再利用输出输入互相关函数与脉冲响应函数的关系就可以得到

$$
\begin{array}{l} \int_ {t - T} ^ {t} \stackrel {\circ} {h} _ {T} (t, \sigma) r _ {X} (\sigma , u) d \sigma \\ = \int_ {0} ^ {b} h _ {1} (t, \sigma) r _ {F X} (\sigma , u) d \sigma + \sum_ {k = 0} ^ {l} c _ {k} (t) u ^ {k}, \quad t - T \leqslant u \leqslant t \tag {15.10-17} \\ \end{array}
$$

解联立积分方程(15.10-17)和(15.10-13)就可以求出最优脉冲响应函数 $h_{T}(t,\tau)$ 来。正如前面所说，要得出 $\dot{h}_{T}(t,\tau)$ 的解析表达式在一般情况下是不太可能的，只能求出它的近似解或数值解。

同样，由最优过滤器 $h_{T}(t,\tau)$ 所产生的最小均方偏差为

$$
\sigma_ {E} ^ {2} = r _ {Y _ {1}} (t, t) - 2 r _ {Y _ {1} Y} (t, t) + r _ {Y} (t, t)
$$

由于满足方程(15.10-16)，可以得出

$$
\begin{array}{l} r _ {Y 1 \stackrel {\circ} {Y}} (t, t) = r _ {Y} ^ {\circ} (t, t) + \sum_ {k = 0} ^ {l} c _ {k} (t) \int_ {t - T} ^ {t} \stackrel {\circ} {h} _ {T} (t, \sigma) \sigma^ {k} d \sigma \\ = r _ {Y} ^ {\circ} (t, t) + \sum_ {k = 0} ^ {l} c _ {k} (t) \int_ {0} ^ {b} h _ {1} (t, \sigma) \sigma^ {k} d \sigma \tag {15.10-18} \\ \end{array}
$$

于是，最后得到

$$
\begin{array}{l} \sigma_ {E} ^ {2} = r _ {Y _ {1}} (t, t) - r _ {Y} ^ {*} (t, t) - 2 \sum_ {k = 0} ^ {l} c _ {k} (t) \int_ {- \infty} ^ {t} h _ {1} (t, \sigma) \sigma^ {k} d \sigma \\ = r _ {Y _ {1}} (t, t) - \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {1}) h _ {T} (t, \sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \\ - 2 \sum_ {k = 0} ^ {l} c _ {k} (t) \int_ {0} ^ {b} h _ {1} (t, \sigma) \sigma^ {k} d \sigma \tag {15.10-19} \\ \end{array}
$$

现在我们来介绍一种最优过滤器的脉冲响应函数 $h_{T}(t,\sigma)$ 的近似计算方法 $^{[33]}$ ，利用这种方法可以很快地求出足够准确的 $\stackrel{\circ}{h}_{T}(t,\sigma)$ 来，而且这种 $\stackrel{\circ}{h}_{T}(t,\sigma)$ 是物理上可 以实现的。因为平稳随机过程是非平稳随机过程的一种特例，所以这种方法在求解平稳随机过程的最优过滤问题中也可以应用。

假定任意一个过滤器的脉冲响应函数是 $h_{T}(t,\sigma)$ ，由于它应是无偏的，所以它所造成的均方误差是

$$
\begin{array}{l} \sigma_ {E} ^ {2} (t) = \left\| Y _ {1} (t) - Y (t) \right\| ^ {2} = r _ {Y _ {1}} (t, t) - 2 r _ {Y _ {1} \mathring {Y}} (t, t) + r _ {Y} ^ {\circ} (t, t) \\ = r _ {Y _ {1}} (t, t) - 2 \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {2}) \int_ {0} ^ {b} h _ {1} (t, \sigma_ {1}) r _ {F X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \\ + \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {1}) h _ {T} (t, \sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2}, \quad T \leqslant t \leqslant b \tag {15.10-20} \\ \end{array}
$$

寻找最优的 $h_{T}(t,\sigma)$ 就是在满足条件组式(15.10-13)时，使 $\sigma_{E}^{2}(t)$ 取条件极小值。利用拉格朗日乘子法将条件极值问题化为绝对极值问题，为此我们作一个 $h_{T}(t,\sigma)$ 的二次泛函

$$
\begin{array}{l} J (h _ {T}) = \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {1}) h _ {T} (t, \sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \\ - 2 \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {2}) \int_ {0} ^ {t} h _ {1} (t, \sigma_ {1}) r _ {F X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \\ - 2 \sum_ {k = 0} ^ {l} \lambda_ {k} \int_ {t - T} ^ {t} h _ {T} (t, \sigma) \sigma^ {k} d \sigma , \quad T \leqslant t \leqslant b \tag {15.10-21} \\ \end{array}
$$

式中 $\lambda_{k}$ 是拉格朗日乘子。寻找使 $\sigma_{E}^{2}$ 取条件极小值的 $h_{T}(t,\sigma)$ 就是寻找使泛函 $J(h_{T})$ 取极小值的 $\dot{h}_{T}(t,\sigma)$ ，其中 $\lambda_{k}$ 由条件组式(15.10-13)确定。等式(15.10-21)可以写为

$$
\begin{array}{l} J (h _ {T}) = \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {1}) h _ {T} (t, \sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \\ - 2 \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {2}) \varphi (t, \sigma_ {2}) d \sigma_ {2}, \quad T \leqslant t \leqslant b \tag {15.10-22} \\ \end{array}
$$

其中

$$
\varphi (t, \sigma_ {2}) = \int_ {0} ^ {t} h _ {1} (t, \sigma_ {1}) r _ {F X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} - \sum_ {k = 0} ^ {l} \lambda_ {k} \sigma_ {2} ^ {k} \tag {15.10-23}
$$

$\varphi(t,\sigma_{2})$ 一般是在 $[t-T,t]$ 区间内对 $\sigma_{2}$ 的平方可积函数。因为 $h_{T}(t,\sigma_{1})$ 在一般的情况下可能包括 $\delta$ 函数及其高阶导数，所以我们要在广义函数类中来讨论二次泛函的极值问题。

在区间 $[t-T,t]$ 上定义的广义函数的线性空间内我们引入两个向量的内积为

$$
\langle \boldsymbol {x}, \boldsymbol {y} \rangle_ {A} = \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} x (\sigma_ {1}) y (\sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \tag {15.10-24}
$$

向量的范数平方为

$$
\| \boldsymbol {x} \| _ {A} ^ {2} = \langle \boldsymbol {x}, \boldsymbol {x} \rangle_ {A} = \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} x (\sigma_ {1}) x (\sigma_ {2}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} d \sigma_ {2} \tag {15.10-25}
$$

由于相关函数 $r_X(\sigma_1, \sigma_2)$ 的对称性和正定性，这样定义的内积满足希尔伯特空间内积公理。在这个函数线性空间内加上所有这个空间的函数序列的极限点就组成了一个希尔伯特空间，我们记为 $H_A$ 。显然 $H_A$ 是包括了一切对 $r_X(\sigma_1, \sigma_2)$ 平方可积函数组成的希尔伯特空间。一切在 $[t - T, t]$ 上平方可积的函数组成希尔伯特空间 $H$ ，在 $H$ 空间内两个向量的内积和范数平方分别为

$$
\langle \boldsymbol {x}, \boldsymbol {y} \rangle = \int_ {t - T} ^ {t} x (\sigma) y (\sigma) d \sigma \tag {15.10-26}
$$

$$
\| \boldsymbol {x} \| ^ {2} = \langle \boldsymbol {x}, \boldsymbol {x} \rangle = \int_ {t - T} ^ {t} x ^ {2} (\sigma) d \sigma \tag {15.10-27}
$$

显然所有属于空间 $H$ 的向量一定也是 $H_{A}$ 空间中的向量，反之则不然。等式(15.10-22)右边的后面一项是 $h_T(t, \sigma_2) \in H_A$ 的线性泛函，它是有界的，否则求 $J(h_T)$ 的极小值就没有意义了。根据泛函分析中的黎茨定理，总可以在 $H_A$ 中找到唯一的向量 $\varphi^*$ 使得

$$
\begin{array}{l} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {2}) \varphi (t, \sigma_ {2}) d \sigma_ {2} = \left\langle \boldsymbol {h} _ {T}, \varphi^ {*} \right\rangle_ {A} \\ = \int_ {t - T} ^ {t} \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {2}) \varphi^ {*} (t, \sigma_ {1}) r _ {X} (\sigma_ {1}, \sigma_ {2}) d \sigma_ {1} \\ T \leqslant t \leqslant b, \quad \boldsymbol {h} _ {T} \in H _ {A} \tag {15.10-28} \\ \end{array}
$$

这样二次泛函 $J(\boldsymbol{h}_{T})$ 就可以写为

$$
\begin{array}{l} J (\boldsymbol {h} _ {T}) = \left\langle \boldsymbol {h} _ {T}, \boldsymbol {h} _ {T} \right\rangle_ {A} - 2 \left\langle \boldsymbol {h} _ {T}, \varphi^ {*} \right\rangle_ {A} \\ = \left\langle \boldsymbol {h} _ {T} - \varphi^ {*}, \boldsymbol {h} _ {T} - \varphi^ {*} \right\rangle_ {A} - \left\langle \varphi^ {*}, \varphi^ {*} \right\rangle_ {A} \tag {15.10-29} \\ \end{array}
$$

由此得到当 $h_{T}=\varphi^{*}$ 时， $J(\boldsymbol{h}_{T})$ 最小

$$
\min _ {\boldsymbol {h} _ {T} \in H _ {A}} J (\boldsymbol {h} _ {T}) = - \left\langle \varphi^ {*}, \varphi^ {*} \right\rangle_ {A} = - \| \varphi^ {*} \| _ {A} ^ {2} \tag {15.10-30}
$$

要求得准确的 $\varphi^{*} \in H_{A}$ 是比较困难的。现在我们用在 $[t - T, t]$ 内平方可积的函数来逐次逼近 $\varphi^{*}$ 。式(15.10-22)也可表示为在 $H$ 空间内的二次泛函 $J(\pmb{h}_T)$ ， $\pmb{h}_T \in H$

$$
J (\boldsymbol {h} _ {T}) = \langle \boldsymbol {h} _ {T}, A \boldsymbol {h} _ {T} \rangle - 2 \langle \boldsymbol {h} _ {T}, \varphi \rangle , \quad \boldsymbol {h} _ {T}, \varphi \in H \tag {15.10-31}
$$

其中 $A$ 是线性算子

$$
A \boldsymbol {h} _ {T} = \int_ {t - T} ^ {t} h _ {T} (t, \sigma_ {1}) r _ {X} (\sigma_ {1}, \sigma_ {1}) d \sigma_ {2} \tag {15.10-32}
$$

由于相关函数 $r_{X}(\sigma_{1},\sigma_{2})$ 具有对称性和正定性, 所以 A 是对称算子

$$
\langle A x, x \rangle = \langle x, A x \rangle
$$

在开始时可取任意的 $h_{T_{0}} \in H$ 作为 $\varphi^{*}$ 的零次近似。我们可以求出二次泛函 $J(\boldsymbol{h}_{T})$ 在 $h_{T_{0}}$ 点的梯度向量 $z_{1}$ ，它应使 $d\left[J\left(\boldsymbol{h}_{T_{0}} + \varepsilon\boldsymbol{z}\right)\right]/d\varepsilon|_{\varepsilon=0}$ 达到最大值，其中 $z \in H$ 。

根据方程(15.10-31)我们得到（参看第 2.8 节)

$$
\begin{array}{l} J \left(\boldsymbol {h} _ {T _ {0}} + \varepsilon \boldsymbol {z}\right) = J \left(\boldsymbol {h} _ {T _ {0}}\right) + 2 \varepsilon \langle A \boldsymbol {h} _ {T _ {0}} - \varphi , \boldsymbol {z} \rangle + \varepsilon^ {2} \langle A \boldsymbol {z}, \boldsymbol {z} \rangle \\ \frac {d}{d \varepsilon} \left[ J \left(\boldsymbol {h} _ {T _ {0}} + \varepsilon \boldsymbol {z}\right) \right] | _ {\varepsilon = 0} = 2 \langle A \boldsymbol {h} _ {T _ {0}} - \varphi , \boldsymbol {z} \rangle \\ \end{array}
$$

显然梯度向量

$$
\mathbf {z} _ {1} = A \mathbf {h} _ {T _ {0}} - \varphi \tag {15.10-33}
$$

当 $h_{T}$ 点从 $h_{T_{0}}$ 点沿梯度向量 $z_{1}$ 变化时，在 $h_{T_{1}} = h_{T_{0}} + \varepsilon_{1} z_{1}$ 点二次泛函 $J(\boldsymbol{h}_{T})$ 将取极小值，由于

$$
\frac {d}{d \varepsilon_ {1}} \left[ J \left(\boldsymbol {h} _ {T _ {0}} + \varepsilon_ {1} \boldsymbol {z} _ {1}\right) \right] = 2 \langle A \boldsymbol {h} _ {T _ {0}} - \varphi , \boldsymbol {z} _ {1} \rangle + 2 \varepsilon_ {1} \langle A \boldsymbol {z} _ {1}, \boldsymbol {z} _ {1} \rangle
$$

所以

$$
\varepsilon_ {1} = - \frac {\left\langle \mathbf {z} _ {1} , A \mathbf {h} _ {r _ {0}} - \varphi \right\rangle}{\left\langle \mathbf {z} _ {1} , A \mathbf {z} _ {1} \right\rangle} = - \frac {\left\langle \mathbf {z} _ {1} , \mathbf {z} _ {1} \right\rangle}{\left\langle \mathbf {z} _ {1} , A \mathbf {z} _ {1} \right\rangle} \tag {15.10-34}
$$

因此以 $h_{T_{1}} = h_{T_{0}} + \varepsilon_{1} z_{1}$ 为一次近似时 $J(h_{T_{1}})$ 比 $J(h_{T_{0}})$ 有最大的减少。依次类推， $\varphi^{*}$ 的 n 次近似为

$$
\begin{array}{l} \boldsymbol {h} _ {T _ {n}} = \boldsymbol {h} _ {T _ {n - 1}} + \varepsilon_ {n} \boldsymbol {z} _ {n} \\ \mathbf {z} _ {n} = A \mathbf {h} _ {T _ {n - 1}} - \varphi \\ \varepsilon_ {n} = - \left\langle \mathbf {z} _ {n}, \mathbf {z} _ {n} \right\rangle / \left\langle \mathbf {z} _ {n}, A \mathbf {z} _ {n} \right\rangle \tag {15.10-35} \\ \end{array}
$$

把式(15.10-35)代入方程(15.10-31)可以得到

$$
J \left(\boldsymbol {h} _ {T _ {n - 1}}\right) - J \left(\boldsymbol {h} _ {T _ {n}}\right) = \frac {\left\langle \boldsymbol {z} _ {n} , \boldsymbol {z} _ {n} \right\rangle^ {2}}{\left\langle \boldsymbol {z} _ {n} , A \boldsymbol {z} _ {n} \right\rangle} \tag {15.10-36}
$$

由此可见 $\left\{J(\boldsymbol{h}_{T_{n}})\right\}$ 是单调递降序列，它有下界一 $\left\|\varphi^{*}\right\|_{A}$ ,所以序列 $\left\{J(\boldsymbol{h}_{T_{n}})\right\}$ 是收敛的

$$
J (\boldsymbol {h} _ {T _ {n - 1}}) - J (\boldsymbol {h} _ {T _ {n}}) \rightarrow 0, \quad n \rightarrow \infty
$$

并且可以证明 $\{\pmb{h}_{T_n}\}$ 在空间 $H_A$ 中收敛于 $\varphi^{*}$ 。如果 $\varphi^{*} \in H_{A}$ 但 $\varphi^{*} \overline{\in} H$ 时，序列 $\{\pmb{h}_{T_n}\}$ 在空间 $H$ 中是发散的。

类似地，我们可以按

$$
\pmb {h} _ {T _ {n}} = \pmb {h} _ {T _ {n - 1}} - \alpha \pmb {z} _ {n}, \quad \alpha \text {为某个正数}
$$

$$
\mathbf {z} _ {n} = A \mathbf {h} _ {T _ {n - 1}} - \varphi \tag {15.10-37}
$$

来求逐次渐近于 $\varphi^{*}$ 的函数序列。可以证明，当 $0 \leqslant \alpha \leqslant \frac{2}{\sup_{t} r_{X}(t, t)}$ 时逐次渐近的函数序列一定收敛于 $\varphi^{*}(t, \tau) = h_{T}(t, \tau)$ ，但是它的渐近速度要比按最速下降法式(15.10-35)求出的序列慢，在一般情况下两种序列的收敛情况相差不大。有时用最速下降法式(15.10-35)比较麻烦，所以也常常应用式(15.10-37)。

例如，过滤器的输入 $X(t)=g(t)+N(t)$ 。信号 $g(t)=g_{0}+g_{1}t$ ，其中 $g_{0}, g_{1}$ 为 未知常数。噪声 $N(t)$ 的数学期望为零，相关函数 $r_{N}(t_{1}, t_{2}) = e^{-20|t_{1} - t_{2}|}$ ，过滤器的理想输出 $Y_{1}(t) = g(t)$ ，现在要寻找最优的有限记忆 T = 1 的线性过滤器。我们用式(15.10-37)来求逐次渐近序列。令 $h_{T_{0}}(t, \tau) = 1, \alpha = 1/2$ ，那么求得 $\varphi^{*}$ 的二次近似就是

$$
\begin{array}{l} h _ {T _ {2}} (t, \sigma) = 4. 0 2 9 - 6. 0 8 8 (t - \sigma) + 0. 1 3 2 2 e ^ {- 2 0 (t - \sigma)} - 0. 0 4 5 4 e ^ {2 0 (t - \sigma - 1)} \\ - 0. 0 1 2 5 (t - \sigma) e ^ {- 2 0 (t - \sigma)} + 0. 0 1 2 5 (t - \sigma) e ^ {2 0 (t - \sigma - 1)}, \quad t - 1 \leqslant \sigma \leqslant t \\ \end{array}
$$

这个近似已经比较好，它所引起的均方误差只有 0.375,而最小的均方误差为 0.316。

#### 15.11 随机过程的卡尔曼滤波方法

在第 15.5 节中已经指出，平稳随机过程的最优线性过滤器是个线性常系数系统，它的脉冲响应函数 $h(t)$ 应满足维纳-何甫方程

$$
r _ {Y _ {1} X} (t) = \int_ {0} ^ {\infty} h (\sigma) r _ {X} (t - \sigma) d \sigma \tag {15.5-7}
$$

我们不直接由这个积分方程求解 $h(t)$ ，而是通过功率谱密度来求最优线性过滤器的传递函数 $F(s)$ 。对于非平稳随机过程，在上节也已指出最优线性过滤器的脉冲响应函数 $\dot{h}(t,\sigma)$ 应满足维纳-何甫方程

$$
r _ {Y _ {1} X} (t, u) = \int_ {0} ^ {t} h (t, \sigma) r _ {X} (\sigma , u) d \sigma \tag {15.10-7}
$$

它也需满足前几节所述的限制条件。 $h(t,\sigma)$ 是个线性变系数系统，无法用谱分解和传递函数的方法，而直接解积分方程(15.10-7)又比较困难，即使用最速下降法或梯度法来近似计算也很不方便。卡尔曼(Kalman)提出了一种递推式滤波器 $^{[17,18]}$ ，他不是从维纳-何甫方程出发，而是直接从信号模型出发，用递推的办法或求解微分方程的方法来求最优线性滤波器的结构和其中的参数——最优增益，最后得到一种动态跟踪系统。这种滤波方法的主要特点是适合用数字计算机进行运算，这对实时数据处理有很大的优点。随着数字计算机的普及，这种滤波方法得到了广泛的应用。下面为了说明卡尔曼滤波方法与维纳-何甫方程内在联系，我们将从维纳-何甫方程出发来求出卡尔曼滤波器的结构和最优参数的表达式。

假定 $F(t)$ 是待检测的有用信号, $N(t)$ 是混入的噪声, 送到滤波器作为输入的是观测值 $X(t)$ , 它满足下列观测方程

$$
X (t) = c (t) F (t) + N (t) \tag {15.11-1}
$$

式中 $c(t)$ 是某一已知变参数；待检测信号是下列微分方程（信号模型）的解

$$
\frac {d}{d t} F (t) = a (t) F (t) + b (t) W (t) \tag {15.11-2}
$$

式中 $a(t)$ , $b(t)$ 都是已知变参数; $W(t)$ 和 $N(t)$ 是数学期望为零的高斯白噪声, 它们只有在同一时刻的值才相关; t=0 时刻的信号 $F(0)$ 是个数学期望为零、方差已给定的随机变量, 它与 t>0 时的 $W(t)$ , $N(t)$ 都不相关; 因此

$$
\overline {{{W (t)}}} = 0, \quad \overline {{{N (t)}}} = 0, \quad r _ {W} (t, \sigma) = \sigma_ {W} ^ {2} (t) \delta (t - \sigma)
$$

$$
r _ {N} (t, \sigma) = \sigma_ {N} ^ {2} (t) \delta (t - \sigma), \quad r _ {W N} (t, \sigma) = r _ {W N} (t) \delta (t - \sigma)
$$

$$
r _ {W N} (t) = r _ {N W} (t), \quad \overline {{{F (0)}}} = 0, \quad r _ {F N} (0, t) = 0
$$

$$
r _ {F W} (0, t) = 0, \quad t > 0 \tag {15.11-3}
$$

从式(15.11-3)，(15.11-1)和(15.11-2)可知：

(1) 待检测信号 $F(t)$ 和观测值 $X(t)$ 的数学期望都等于零。

(2) $W(t)$ , $N(t)$ 与 t 时刻以前的信号 $F(\sigma)$ , 观测值 $X(\sigma)$ , $\sigma < t$ 都不相关, 即

$$
r _ {W F} (t, \sigma) = 0, \quad r _ {W X} (t, \sigma) = 0, \quad r _ {N F} (t, \sigma) = 0, \quad r _ {N X} (t, \sigma) = 0, \quad \sigma <   t \tag {15.11-4}
$$

我们将研究线性过滤问题，假定过滤器的理想输出 $Y_{1}(t)$ 就是被检测信号本身

$$
Y _ {1} (t) = F (t) \tag {15.11-5}
$$

线性过滤器输出 $Y(t)$ 与输入观测值 $X(t)$ 的关系是

$$
Y (t) = \int_ {0} ^ {t} h (t, \sigma) X (\sigma) d \sigma \tag {15.11-6}
$$

输出 $Y(t)$ 与理想输出 $Y_{1}(t)$ 之间的误差记为

$$
E (t) = Y _ {1} (t) - Y (t) = F (t) - Y (t) \tag {15.11-7}
$$

依上面所述，输出和误差的数学期望都等于零

$$
\overline {{{Y (t)}}} = 0, \quad \overline {{{E (t)}}} = 0 \tag {15.11-8}
$$

我们知道，为了使输出的均方误差 $\overline{E^{2}(t)}$ 最小，最优线性过滤器 $h(t,\sigma)$ 必须且只需满足维纳-何甫方程

$$
r _ {Y _ {1}, X} (t, u) = r _ {F X} (t, u) = \int_ {0} ^ {t} h (t, \sigma) r _ {X} (\sigma , u) d \sigma = r _ {Y X} ^ {\prime} (t, u), \quad 0 \leqslant u \leqslant t \tag {15.11-9}
$$

它在希尔伯特空间中的几何解释就是信号向量 $F(t)$ 与观测值向量的内积等于最优线性过滤器最优输出 $\dot{Y}(t)$ 与观测值向量 $X(u)$ 的内积，也就是说最优输出 $Y(t)$ 是信号 $F(t)$ 在所有观测值 $X(u), 0 \leqslant u \leqslant t$ 组成的线性子空间 $H_{x}$ 上的直交投影；均方误差最小的输出误差 $\dot{E}(t)$ 就是由信号 $F(t)$ 到子空间的垂线，它应与直交投影 $\dot{Y}(t)$ 正交

$$
r _ {E Y} ^ {\circ} (t, t) = r _ {F Y} ^ {\circ} (t, t) - r _ {Y} ^ {\circ} (t, t) = 0 \tag {15.11-10}
$$

首先，对积分方程(15.11-9)的两边，对 t 求偏导数，根据相关函数的定义，应用关系式(15.11-1)—(15.11-5)不难得到对 t 的偏导数为

$$
\begin{array}{l} \frac {\partial}{\partial t} r _ {Y _ {1} X} (t, u) = \frac {\partial}{\partial t} r _ {F X} (t, u) \\ = a (t) r _ {F X} (t, u) + b (t) r _ {W X} (t, u) = a (t) r _ {F X} (t, u) \tag {15.11-11} \\ \end{array}
$$

$$
\frac {\partial}{\partial t} \int_ {0} ^ {t} h (t, \sigma) r _ {X} (\sigma , u) d \sigma
$$

$$
= \int_ {0} ^ {t} \frac {\partial \stackrel {\circ} {h} (t , \sigma)}{\partial t} r _ {X} (\sigma , u) d \sigma + \stackrel {\circ} {h} (t, t) r _ {X} (t, u)
$$

$$
= \int_ {0} ^ {t} \frac {\partial h (t , \sigma)}{\partial t} r _ {X} (\sigma , u) d \sigma + \stackrel {\circ} {h} (t, t) [ c (t) r _ {F X} (t, u) + r _ {N X} (t, u) ]
$$

$$
= \int_ {0} ^ {t} \frac {\partial h (t , \sigma)}{\partial t} r _ {X} (\sigma , u) d \sigma + \stackrel {\circ} {h} (t, t) c (t) r _ {F X} (t, u) \tag {15.11-12}
$$

当然它们应该是相等的。再由维纳-何甫方程(15.11-9)有

$$
\int_ {0} ^ {t} \left[ a (t) \stackrel {\circ} {h} (t, \sigma) - \stackrel {\circ} {h} (t, t) c (t) \stackrel {\circ} {h} (t, \sigma) - \frac {\partial h (t , \sigma)}{\partial t} \right] r _ {X} (\sigma , u) d \sigma = 0, \quad 0 \leqslant u <   t
$$

因为 $r_{X}(\sigma,u)=c(\sigma)r_{F}(\sigma,u)c(u)+r_{N}(\sigma,u)$ ，它不等于零，所以 $h(t,\sigma)$ 要满足式 (15.11-9) 必须且只需

$$
a (t) \stackrel {\circ} {h} (t, \sigma) - \stackrel {\circ} {h} (t, t) c (t) \stackrel {\circ} {h} (t, \sigma) - \frac {\partial \stackrel {\circ} {h} (t , \sigma)}{\partial t} = 0, \quad 0 \leqslant \sigma \leqslant t \tag {15.11-13}
$$

同时，由式(15.11-6)和(15.11-13)可得到

$$
\begin{array}{l} \frac {d}{d t} \stackrel {\circ} {Y} (t) = \frac {d}{d t} \int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma) X (\sigma) d \sigma = \int_ {0} ^ {t} \frac {\partial h (t , \sigma)}{\partial t} X (\sigma) d \sigma + \stackrel {\circ} {h} (t, t) X (t) \\ = \int_ {0} ^ {t} [ a (t) \stackrel {\circ} {h} (t, \sigma) - \stackrel {\circ} {h} (t, t) c (t) \stackrel {\circ} {h} (t, \sigma) ] X (\sigma) d \sigma + \stackrel {\circ} {h} (t, t) X (t) \\ = a (t) \stackrel {\circ} {Y} (t) - \stackrel {\circ} {h} (t, t) c (t) \stackrel {\circ} {Y} (t) + \stackrel {\circ} {h} (t, t) X (t) \\ = a (t) Y (t) - h (t, t) [ X (t) - c (t) Y (t) ] \\ \end{array}
$$

记

$$
k (t) = h (t, t) \tag {15.11-14}
$$

为最优增益系数，那么最优线性滤波器的输出就是下列方程的解

$$
\frac {d}{d t} \mathring {Y} (t) = a (t) \mathring {Y} (t) + k (t) [ X (t) - c (t) \mathring {Y} (t) ] \tag {15.11-15}
$$

它的初始条件是

$$
\stackrel {\circ} {Y} (0) = 0 \tag {15.11-16}
$$

从上式可以看出，为了得到滤波器的最优输出 $Y(t)$ 必须确定最优增益系数。由式(15.11-2)可得

$$
F (t) = \varphi (t, 0) F (0) + \int_ {0} ^ {t} \varphi (t, \sigma) b (\sigma) W (\sigma) d \sigma \tag {15.11-17}
$$

其中 $\varphi(t,\sigma)$ 是式(15.11-2)的基本解, 它满足条件

$$
\frac {d \varphi (t , \sigma)}{d t} = a (t) \varphi (t, \sigma)
$$

$$
\varphi (t, \sigma) \varphi (\sigma , t) = \varphi (t, t) = 1 \tag {15.11-18}
$$

考虑在区间 $0 \leqslant u < t$ 中的维纳-何甫方程(15.11-9)，并令 u 趋于 t。由相关函数的性质可以推知

$$
\begin{array}{l} r _ {Y _ {1} X} (t, u) = r _ {F X} (t, u) = r _ {F} (t, u) c (u) + r _ {F N} (t, u) \\ = r _ {F} (t, u) c (u) + \varphi (t, 0) r _ {F N} (0, u) + \int_ {0} ^ {t} \varphi (t, \sigma) b (\sigma) r _ {W N} (\sigma , u) d \sigma \\ = r _ {F} (t, u) c (u) + \varphi (t, u) b (u) r _ {W N} (u) \\ \end{array}
$$

和

$$
\begin{array}{l} r _ {X} (\sigma , u) = r _ {X F} (\sigma , u) c (u) + r _ {X N} (\sigma , u) \\ = r _ {X F} (\sigma , u) c (u) + c (\sigma) r _ {F N} (\sigma , u) + r _ {N} (\sigma , u) \\ \end{array}
$$

同时有

$$
\begin{array}{l} \int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma) r _ {X} (\sigma , u) d \sigma = \int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma) r _ {X F} (\sigma , u) c (u) d \sigma + \int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma) c (\sigma) r _ {F N} (\sigma , u) d \sigma \\ + \int_ {0} ^ {t} h (t, \sigma) r _ {N} (\sigma , u) d \sigma \\ = r _ {Y F} ^ {\circ} (t, u) c (u) + \int_ {0} ^ {t} h (t, \sigma) c (\sigma) r _ {F N} (\sigma , u) d \sigma \\ + \stackrel {\circ} {h} (t, u) \sigma_ {N} ^ {2} (u) \\ \end{array}
$$

由式 $(15.11-9)$ ，有

$$
\begin{array}{l} h (t, u) = \left[ r _ {F} (t, u) c (t) - r _ {Y F} ^ {\circ} (t, u) c (u) + \varphi (t, u) b (u) r _ {W N} (u) \right. \\ - \int_ {0} ^ {t} h (t, \sigma) c (\sigma) r _ {F N} (\sigma , u) d \sigma ] \sigma_ {N} ^ {- 2} (u) \\ = \left[ r _ {E F} ^ {\circ} (t, u) c (u) + \varphi (t, u) b (u) r _ {W N} (u) \right. \\ - \int_ {0} ^ {t} h (t, \sigma) c (\sigma) r _ {F N} (\sigma , u) d \sigma ] \sigma_ {N} ^ {- 2} (u) \\ \end{array}
$$

注意到脉冲响应函数 $h(t,u)$ 对第一个变量是右连续的, 而对第二个变量是左连续的, 因此

$$
\stackrel {\circ} {h} (t, t) = \lim _ {u \uparrow t} \stackrel {\circ} {h} (t, u) = \left[ r _ {E F} ^ {\circ} (t, t) c (t) + b (t) r _ {W N} (t) \right] \sigma_ {N} ^ {- 2} (u)
$$

因为

$$
\begin{array}{l} r _ {F N} (\sigma , u) = \varphi (\sigma , 0) r _ {F N} (0, u) + \int_ {0} ^ {\sigma} \varphi (\sigma , \lambda) b (\lambda) r _ {W N} (\lambda , u) d \lambda \\ = \int_ {0} ^ {\sigma} b (\sigma , \lambda) b (\lambda) r _ {W N} (\lambda , u) d \lambda \\ \end{array}
$$

$\lambda$ 自 0 变化到 $\sigma, \sigma$ 又在 0 到 $t$ 之间变化，只有在 $\sigma > u$ 时 $r_{FN}(t, u)$ 才取有限值，在其余情况下都是 0。当 $u$ 从小于 $t$ 而趋于 $t$ 时， $r_F(\sigma, u)$ 仅在 $u = t$ 时不为零，其余均为零，因此当 $u$ 从小于 $t$ 而趋于 $t$ 时

$$
\int_ {0} ^ {t} \stackrel {\circ} {h} (t, \sigma) c (\sigma) r _ {F N} (\sigma , u) d \sigma
$$

趋于 0。再则，由于 $r_{\hat{E}F}(t,t)=r_{\hat{E}}(t,t)+r_{\hat{E}\hat{Y}}(t,t)$ ，垂线 $E(t)$ 与 $Y(t)$ 互为直交，所以 $r_{\hat{E}F}(t,t)=r_{\hat{E}}(t,t)$ 。最后我们得出最优增益系数的表达式为

$$
k (t) = \stackrel {\circ} {h} (t, t) = \left[ r _ {E} ^ {\circ} (t, t) c (t) + b (t) r _ {W N} (t) \right] \sigma_ {N} ^ {- 2} (t) \tag {15.11-19}
$$

将 $k(t)$ 代入式(15.11-15)就得到一个最优滤波器。经过最优线性过滤后的误差是

$$
E (t) = Y _ {1} (t) - Y (t) = F (t) - Y (t) \tag {15.11-20}
$$

显然它的数学期望为零。由信号模型式(15.11-2)和最优过滤器输出公式(15.11-15)可求得

$$
\begin{array}{l} \frac {d}{d t} \stackrel {\circ} {E} (t) = \frac {d}{d t} F (t) - \frac {d}{d t} \stackrel {\circ} {Y} (t) \\ = [ a (t) - k (t) c (t) ] \dot {E} (t) + b (t) W (t) - k (t) N (t) \tag {15.11-21} \\ \end{array}
$$

因为数学期望为零，所以最小方差就是最小均方误差 $\sigma_{\dot{E}}^{2}(t)=r_{\dot{E}}(t,t)=\overline{E^{2}(t)}$ 。它的导数是

$$
\begin{array}{l} \frac {d}{d t} \sigma_ {\overset {\circ} {E} (t)} ^ {2} = \frac {d}{d t} r _ {\overset {\circ} {E}} (t, t) = 2 r _ {\frac {d}{d t} \overset {\circ} {E} \overset {\circ} {E}} (t, t) \\ = 2 [ a (t) - k (t) c (t) ] r _ {E} ^ {\circ} (t, t) + 2 b (t) r _ {W E} ^ {\circ} (t) - 2 k (t) r _ {N E} ^ {\circ} (t, t) \\ \end{array}
$$

现在分别求 $r_{WE}(t,t)$ 和 $r_{NE}(t,t)$

$$
\begin{array}{l} r _ {W E} (t, t) = r _ {W F} (t, t) - r _ {W Y} (t, t) \\ = r _ {W F} (t, 0) \varphi (t, 0) + \int_ {0} ^ {t} r _ {W} (t, \sigma) b (\sigma) \varphi (t, \sigma) d \sigma - r _ {W Y} (t, 0) \varphi (t, 0) \\ - \int_ {0} ^ {t} r _ {W F} (t, \sigma) \varphi (t, \sigma) c (\sigma) k (\sigma) d \sigma - \int_ {0} ^ {t} r _ {W N} (t, \sigma) \varphi (t, \sigma) k (\sigma) d \sigma \\ \end{array}
$$

$$
+ \int_ {0} ^ {t} r _ {W Y} (t, \sigma) \varphi (t, \sigma) c (\sigma) k (\sigma) d \sigma
$$

$$
= \frac {1}{2} \sigma_ {W} ^ {2} (t) b (t) - \frac {1}{2} r _ {W N} (t) k (t)
$$

这是因为 $r_{WF}(t,\sigma)$ 和 $r_{W\hat{Y}}(t,\sigma)$ 只在 $\sigma=t$ 时才取不为 0 的有限值， $\sigma$ 为其他值时它们都等于零。类似可求得

$$
r _ {N E} (t, t) = r _ {N F} (t, t) - r _ {N Y} (t) = \frac {1}{2} r _ {N W} (t) b (t) - \frac {1}{2} \sigma_ {N} ^ {2} (t) k (t)
$$

这样最小均方误差满足下列方程

$$
\begin{array}{l} \frac {d}{d t} \sigma_ {\dot {E}} ^ {2} (t) = 2 [ a (t) - k (t) c (t) ] \sigma_ {\dot {E}} ^ {2} (t) + b ^ {2} (t) \sigma_ {W} ^ {2} (t) \\ - 2 b (t) r _ {W N} (t) k (t) + k ^ {2} (t) \sigma_ {N} ^ {2} (t) \tag {15.11-22} \\ \end{array}
$$

初始条件可根据式(15.11-6)和(15.11-20)得到

$$
\sigma_ {E} ^ {2} (0) = r _ {E} ^ {\circ} (0, 0) = r _ {F} (0, 0) \tag {15.11-23}
$$

对于非最优的线性过滤器，即增益系数不是由式(15.11-19)确定的而是另一个 $\widetilde{k}(t)$ ，那么式(15.11-15)输出 $Y(t)$ 的均方误差 $\overline{E^{2}(t)}=\sigma_{E}^{2}(t)$ 仍满足式(15.11-22)，但要用 $\widetilde{k}(t)$ 来代替最优的 $k(t)$ 。这样得到的均方误差就不是最小的，对任何 t 都有 $\sigma_{E}^{2}(t)\geqslant\sigma_{E}^{2}(t)$ 。

最优过滤器的输出 $Y(t)$ 与待检测信号 $F(t)$ 之间的最小均方误差 $\sigma_{E}^{2}(t)$ 的表达式可直接将式(15.11-19)代入(15.11-22)并加以整理后得到

$$
\begin{array}{l} \frac {d}{d t} \sigma_ {\dot {E}} ^ {2} (t) = 2 [ a (t) - b (t) r _ {W N} (t) \sigma_ {N} ^ {2} (t) c (t) ] \sigma_ {\dot {E}} ^ {2} (t) \\ - \sigma_ {E} ^ {4} (t) c ^ {2} (t) \sigma_ {N} ^ {- 2} (t) + b ^ {2} (t) \left[ \sigma_ {W} ^ {2} (t) - r _ {W N} ^ {2} \sigma_ {N} ^ {- 2} (t) \right] \tag {15.11-24} \\ \end{array}
$$

于是，用递推求解微分方程(15.11-15)，(15.11-19)和(15.11-22)的办法就可得到最优过滤器的输出 $Y(t)$ ，最优增益系数 $k(t)$ 和最小均方误差 $\sigma_{E}^{2}(t)$ ，这就是卡尔曼滤波方法。可以把这种滤波方法连同信号模型，观测方程画成如图 15.11-1 所示的方块图。

> 此处省略原书 **图 15.11-1**

上面我们假定观测值 $X(t)$ 的数学期望等于 0，实际上观测值中可能含有非随机的时间函数分量。例如，待检测的有用信号 $F(t)$ 满足下列方程式

$$
\frac {d}{d t} F (t) = a (t) F (t) + b (t) W (t) + g (t) \tag {15.11-25}
$$

而观测方程是

$$
X (t) = c (t) F (t) + N (t) + d (t) \tag {15.11-26}
$$

其中 $g(t)$ 和 $d(t)$ 都是给定的非随机时间函数， $W(t)$ 和 $N(t)$ 与以前的假设相同。此外，还假定信号初值 $F(0)$ 是个随机变量，数学期望为 $\overline{F(0)}$ ，方差为 $\sigma_{F}^{2}(0)=r_{F}(0,0)$ 。现在要构造一个最优的无偏线性过滤器，使输出的数学期望 $\overline{Y(t)}$ 等于信号的数学期望 $\overline{F(t)}$ ，而且输出的均方误差最小。这时，观测值 $X(t)$ 和信号 $F(t)$ 的数学期望都不等于零，它们分别满足于下列方程

$$
\frac {d}{d t} \overline {{F (t)}} = a (t) \overline {{F (t)}} + g (t) \tag {15.11-27}
$$

$$
\overline {{{X (t)}}} = c (t) \overline {{{F (t)}}} + d (t) \tag {15.11-28}
$$

但随机过程 $\left[F(t)-\overline{F(t)}\right]$ 和 $\left[X(t)-\overline{X(t)}\right]$ 的数学期望都等于零，它们分别满足于下列方程

$$
\frac {d}{d t} [ F (t) - \overline {{F (t)}} ] = a (t) [ F (t) - \overline {{F (t)}} ] + b (t) + W (t) \tag {15.11-29}
$$

$$
[ X (t) - \overline {{{X (t)}}} ] = c (t) [ F (t) - \overline {{{F (t)}}} ] + N (t) \tag {15.11-30}
$$

在这里只要将待检测信号改为 $\left[F(t)-\overline{F(t)}\right]$ ，观测值改为 $\left[X(t)-\overline{X(t)}\right]$ ，问题就又可归结为式(15.11-1)和(15.11-2)。引用前面的结果可立即得到最优无偏线性过滤器的输出应满足方程

$$
\frac {d}{d t} \stackrel {\circ} {Y} (t) = a (t) \stackrel {\circ} {Y} (t) + g (t) + k (t) [ X (t) - d (t) - c (t) \stackrel {\circ} {Y} (t) ] \tag {15.11-31}
$$

初始条件应是

$$
Y (0) = F (0) \tag {15.11-32}
$$

而最优过滤系数 $k(t)$ 和最小均方误差 $\sigma_{E}^{2}(t)$ 与数学期望无关，故仍满足于方程 (15.11-19) 和 (15.11-22)。

前面谈到的待检测信号和观测值都是一维的。上述讨论很容易推广到多维的情况。假设待检测信号 $F(t)$ 是 n 维向量随机过程，观测值是 m 维向量随机过程，它们分别满足方程式

$$
\frac {d}{d t} \boldsymbol {F} (t) = A (t) \boldsymbol {F} (t) + B (t) \boldsymbol {W} (t) + \boldsymbol {g} (t) \tag {15.11-33}
$$

$$
\boldsymbol {X} (t) = C (t) \boldsymbol {F} (t) + \boldsymbol {N} (t) + \boldsymbol {d} (t) \tag {15.11-34}
$$

其中 $g(t)$ 和 $d(t)$ 分别是 n 维和 m 维非随机向量函数， $A(t)$ ， $B(t)$ ， $C(t)$ 都是相应 阶数的非随机矩阵, $W(t)$ , $N(t)$ 分别是数学期望为零向量的 p 维和 m 维向量高斯白色随机过程，它们的相关矩阵是

$$
R _ {W} (t, \sigma) = \Sigma_ {W} ^ {2} (t) \delta (t - \sigma), \quad R _ {N} (t, \sigma) = \Sigma_ {N} ^ {2} (t) \delta (t - \sigma)
$$

$$
R _ {W N} (t, \sigma) = R _ {W N} (t) \delta (t - \sigma), \quad R _ {W N} (t) = R _ {N W} (t) ^ {\tau}
$$

设 t=0 时 $F(0)$ 是随机向量，它的数学期望是 $\overline{F(0)}$ ，方差阵为 $\Sigma_{F}^{2}(0)$ ， $F(0)$ 与 $W(t)$ ， $N(t)$ ，t>0 都是不相关的。现在的任务是要构造一个无偏的，均方误差为最小的最优线性过滤器。无偏要求就是最优输出 $\dot{Y}(t)$ 的数学期望与待检测信号的数学期望相等

$$
\overline {{\mathbf {Y} (t)}} = \overline {{\mathbf {F} (t)}} \tag {15.11-35}
$$

这时最优输出误差 $\dot{\boldsymbol{E}}(t)=\boldsymbol{F}(t)-\dot{\boldsymbol{Y}}(t)$ 的数学期望 $\dot{\boldsymbol{E}}(t)$ 是个零向量，而最小均方误差就是在希尔伯特空间 $H_{n}$ 中向量 $\dot{\boldsymbol{E}}(t)$ 的范数平方最小，也就是方差阵 $\Sigma_{\dot{\boldsymbol{E}}}^{2}(t)$ 或相关函数阵 $R_{\dot{\boldsymbol{E}}}(t,t)$ 的迹最小。经过类似的推导我们可以得到多维随机过程的最优过滤公式，即最优无偏线性过滤器的输出 $\dot{\boldsymbol{Y}}(t)$ 应满足方程

$$
\frac {d}{d t} \mathbf {\dot {Y}} (t) = A (t) \mathbf {\dot {Y}} (t) + \mathbf {g} (t) + K (t) [ \mathbf {X} (t) - \mathbf {d} (t) - C (t) \mathbf {\dot {Y}} (t) ] \tag {15.11-36}
$$

初始条件是

$$
\mathbf {\dot {Y}} (0) = \overline {{\boldsymbol {F} (0)}} \tag {15.11-37}
$$

其中 $K(t)$ 是最优增益矩阵, 它是 $n \times m$ 阶的且满足方程

$$
K (t) = \left[ \Sigma_ {E} ^ {2} (t) C ^ {\tau} (t) + B (t) R _ {W N} (t) \right] \Sigma_ {N} ^ {- 2} (t) \tag {15.11-38}
$$

$\sum_{E}^{2}(t)$ 是均方误差最小的方差阵，它是 $n \times n$ 阶的对称阵，并满足矩阵方程

$$
\begin{array}{l} \frac {d}{d t} \Sigma_ {\mathring {E}} ^ {2} (t) = [ A (t) - B (t) R _ {W N} (t) \Sigma_ {N} ^ {- 2} (t) C (t) ] \Sigma_ {\mathring {E}} ^ {2} (t) \\ + \sum_ {E} ^ {2} (t) \left[ A ^ {\tau} (t) - C ^ {\tau} (t) \Sigma_ {N} ^ {- 2} (t) R _ {W N} ^ {\tau} (t) B ^ {\tau} (t) \right] \\ - \sum_ {\mathring {E}} ^ {2} (t) C ^ {\tau} (t) \sum_ {N} ^ {- 2} (t) C (t) \sum_ {\mathring {E}} ^ {2} (t) \\ + B (t) \left[ \Sigma_ {W} ^ {2} (t) - R _ {W N} (t) \Sigma_ {N} ^ {- 2} (t) R _ {W N} ^ {\tau} (t) \right] B ^ {\tau} (t) \tag {15.11-39} \\ \end{array}
$$

和初始条件

$$
\Sigma_ {E} ^ {2} (0) = \Sigma_ {F} ^ {2} (0) \tag {15.11-40}
$$

当待检测信号和观测向量都是平稳随机过程，A, B, C 为与时间无关的常矩阵，设观测向量从 $t = -\infty$ 开始进入过滤器，这时 $K(t)$ 和 $\Sigma_{E}^{2}(t)$ 都趋于常矩阵，用卡尔曼滤波方法所得的结果与用维纳方法过滤的结果是一致的。我们用第 15.6 节中的例 3 来说明。根据所给的条件可得到待检测信号模型和观测方程分别是

$$
\frac {d}{d t} F (t) = - F (t) + W (t)
$$

$$
X (t) = F (t) + N (t)
$$

也就是说 $a(t)=-1, b(t)=1, c(t)=1; W(t)$ 和 $N(t)$ 是互不相关的两个数学期望为零的平稳白噪声。

$$
r _ {W} (t, \sigma) = \sigma_ {W} ^ {2} (t) \delta (t - \sigma), \quad \sigma_ {W} ^ {2} (t) = \pi , \quad r _ {N} (t, \sigma) = \sigma_ {N} ^ {2} (t) \delta (t - \sigma)
$$

$$
\sigma_ {N} ^ {2} (t) = \pi n ^ {2}, \quad r _ {W N} (t, \sigma) = 0
$$

根据最优过滤公式可得出

$$
\frac {d \stackrel {\circ} {Y} (t)}{d t} = - \stackrel {\circ} {Y} (t) + k (t) [ X (t) - \stackrel {\circ} {Y} (t) ]
$$

$$
k (t) = \sigma_ {E} ^ {2} (t) \sigma_ {N} ^ {- 2} (t) = \frac {1}{\pi n ^ {2}} \sigma_ {E} ^ {2} (t)
$$

和

$$
\frac {d}{d t} \sigma_ {\mathring {E}} ^ {2} (t) = - 2 \sigma_ {\mathring {E}} ^ {2} (t) - \frac {1}{\pi n ^ {2}} \sigma_ {\mathring {E}} ^ {4} (t) + \pi
$$

因为 $\sigma_{E}^{2}(t)$ 是个正值，整个过滤器是从 $t=-\infty$ 时开始工作的，因此 $\frac{d}{dt}\sigma_{E}^{2}(t)=0$ ， $\sigma_{E}^{2}(t)=\pi n(-n+\sqrt{1+n^{2}}), k(t)=\frac{1}{n}(\sqrt{1+n^{2}}-n)$ ，于是最优过滤器的传递函数就是

$$
\stackrel {\circ} {F} (s) = \frac {k}{s + (1 + k)} = \frac {\sqrt {1 + n ^ {2}} - n}{n s + \sqrt {1 + n ^ {2}}} = \frac {1}{(n + \sqrt {1 + n ^ {2}}) (\sqrt {1 + n ^ {2}} + n s)}
$$

这与第 15.6 节中例 3 的结果是一致的。

我们来看方程(15.11-39)，当待检测信号 $F(t)$ 是 n 维向量随机过程时，方差阵 $\Sigma_{E}^{2}(t)$ 有 $n \times n$ 个元素，由于它是对称的，因此实际上只有 $\frac{1}{2}n(n+1)$ 个未知函数。这是一个非线性微分方程，叫做黎卡提(Ricatti)方程。要解这个方程也比较困难。有一种解的方法是把它化为一组联立的线性微分方程

$$
\left\{ \begin{array}{l} \frac {d}{d t} V (t) = \left[ A (t) - B (t) R _ {W N} (t) \Sigma_ {N} ^ {- 2} (t) C (t) \right] V (t) \\ \quad + B (t) \left[ \Sigma_ {W} ^ {2} (t) - R _ {W N} (t) \Sigma_ {N} ^ {- 2} (t) R _ {W N} ^ {\tau} (t) \right] B ^ {\tau} (t) Z (t) \\ \frac {d}{d t} Z (t) = C ^ {\tau} (t) \Sigma_ {N} ^ {- 2} (t) C (t) V (t) \\ \quad - \left[ A ^ {\tau} (t) - C ^ {\tau} (t) \Sigma_ {N} ^ {- 2} (t) R _ {W N} ^ {\tau} (t) B ^ {\tau} (t) \right] Z (t) \end{array} \right. \tag {15.11-41}
$$

其中 $V(t)$ 和 $Z(t)$ 都是 $n \times n$ 阶方阵, 初始条件为

$$
V (0) = \Sigma_ {E} ^ {2} (0), \quad Z (0) = E
$$

在求出 $V(t)$ 和 $Z(t)$ 后, 如果 $Z(t)$ 的逆存在, 那么最小方差阵就是

$$
\Sigma_ {E} ^ {2} (t) = V (t) Z ^ {- 1} (t) \tag {15.11-42}
$$

当 $n$ 较大时解方程(15.11-41)也是比较麻烦的，要用到数值方法。对于从 $t = -\infty$ 开始的平稳随机过程来说，在 $t$ 时刻系统已达到稳态， $R_{E}(t,t)$ 的导数将等于零，因此式(15.11-39)成为一个代数黎卡提方程。近年来，随着计算技术的飞跃发展，大容量、高速度、高可靠性的数字计算机可以作为控制系统的一个组成部分参加工作。对任何连续的待测信号作数据处理时，总要用采样的方法把连续量变成离散的数列。对这种随机量序列利用卡尔曼方法可以得到随机序列线性过滤的递推公式，它特别便于在数字计算机上计算。下一节我们就来讨论随机序列线性过滤的递推方法。

#### 15.12 随机序列的最优递推线性过滤 $^{[5,17]}$

假设每一个时刻的观测量 $X_{k}^{c}=(X_{k_{1}},X_{k_{2}},\cdots,X_{km})$ 是一个数学期望为零的 m 维随机列向量，它可以看做是希尔伯特空间 $H_{m}$ 中的一个元， $H_{m}$ 是由 m 个随机变量空间 $H_{1}$ （无穷维希尔伯特空间）组成的积空间。k 个时刻的观测量 $X_{1},X_{2},\cdots,X_{k}$ 是 $H_{m}$ 空间中的 k 个元，也可以把它们看作为一个 km 维的随机列向量

$$
\mathcal {X} _ {k} ^ {\bar {r}} = \left(X _ {1} ^ {c}, X _ {2} ^ {c}, \dots , X _ {k} ^ {c}\right) = \left(X _ {1 1}, X _ {1 2}, \dots , X _ {1 m}; X _ {2 1}, \dots , X _ {2 m}; X _ {k 1}, \dots , X _ {k m}\right) \tag {15.12-1}
$$

$\mathcal{X}_{k}$ 是 $H_{km}$ 空间中的一个元， $H_{km}$ 是 km 个 $H_{1}$ 空间的积空间。在 $t_{k}$ 时间把这 k 个观测量 $X_{1}, X_{2}, \cdots, X_{k}$ ，即 $\mathcal{X}_{k}$ 输入给过滤器，这时过滤器的输出 $Y_{k}$ 是一个 n 维随机列向量，它的每个分量 $Y_{kj}$ 是输入观测量 $\mathcal{X}_{k}$ 的各分量 $X_{il}$ 的某种确定的线性组合，即

$$
Y _ {k j} = \sum_ {i = 1} ^ {k} \sum_ {l = 1} ^ {m} a _ {j, i l} X _ {i l}, \quad j = 1, 2, \dots , n
$$

因此输出 $Y_{k}$ 总可以写成下列表达式

$$
\mathbf {Y} _ {k} = A \mathfrak {X} _ {k} \tag {15.12-2}
$$

其中 $A=(a_{j,il}), j=1,2,\cdots,n, i=1,2,\cdots,k, l=1,2,\cdots,m$ 是一个 $n \times km$ 阶矩阵。显然，式(15.12-2)所表示的 $Y_{k}$ 的数学期望为零，可以把它看作为另一个空间 $H_{n}$ 中的一个元， $H_{n}$ 是由 n 个 $H_{1}$ 组成的积空间。矩阵 A 就是一个由 $H_{km}$ 到 $H_{n}$ 空间的线性算子。所有形如式(15.12-2)的过滤器的输出 $Y_{k}$ 在 $H_{n}$ 空间中构成了一个子空间 $H_{X_{k}}$ 它的维数不大于 nkm。过滤器在 $t_{k}$ 时间的理想输出 $Y_{1k}$ 也是个数学期望为零的 n 维随机列向量，它也是空间 $H_{n}$ 中的一个元。因此，过滤器在 $t_{k}$ 时间的输出误差是

$$
\boldsymbol {E} _ {k} = \boldsymbol {Y} _ {1 k} - \boldsymbol {Y} _ {k} \tag {15.12-3}
$$

它的数学期望也是零，它也是空间 $H_{n}$ 中的一个元。最优过滤器就是要输出的均方

误差最小，也就是要 $E_{k}$ 的范数平方最小，那么 $E_{k}$ 就必须与 $H_{n}$ 的子空间 $H_{X_{k}}$ 直交。

在 $H_{n}$ 中 $E_{k}$ 与子空间 $H_{X_{k}}$ 直交，因此 $E_{k}$ 必须和 $H_{X_{k}}$ 中的任何向量直交

$$
\langle \stackrel {\circ} {E} _ {k}, Y _ {k} \rangle = \sum_ {j = 1} ^ {n} \langle \stackrel {\circ} {E} _ {k j}, Y _ {k j} \rangle = 0
$$

根据式(15.12-2)，存在这样的 $Y_{k}$ ，它的第 j 个分量 $Y_{kj}$ 等于 $X_{k}$ 的某个分量 $X_{il}$ ，而 $Y_{k}$ 的其余分量都等于零，j 是 1 到 n 中的任意数，i 是 1 到 k 中的任意数，l 是 1 到 m 中的任意数。这样

$$
\langle \mathbf {E} _ {k}, \mathbf {Y} _ {k} \rangle = \langle E _ {k j}, X _ {i l} \rangle = 0, \quad j = 1, \dots , n, \quad i = 1, \dots , k, \quad l = 1, \dots , m
$$

这就是说在 $H_{1}$ 中两个随机变量 $E_{kj}$ 和 $X_{il}$ 必须直交，它们的相关系数 $r\hat{E}_{kj}X_{il} = 0$ 。 $H_{n}$ 中的随机向量 $\hat{E}_k$ 与 $H_{km}$ 中的随机向量 $\mathfrak{X}_k$ 的相关矩阵是由 $nkm$ 个相关系数 $r\hat{E}_{kj}X_{il}$ 组成的，因此它必须是零矩阵

$$
R _ {\mathring {E} _ {k}} \mathfrak {X} _ {k} = (r _ {\mathring {E} _ {k j}} ^ {X _ {i l}}) = O
$$

最优过滤器在 $t_{k}$ 时刻的输出 $Y_{k}=A\mathcal{X}_{k}$ 就是 $Y_{1k}$ 在子空间 $H_{X_{k}}$ 上的直交投影

$$
\mathbf {Y} _ {k} = P \left(H _ {\mathfrak {X} _ {k}}\right) \mathbf {Y} _ {1 k}
$$

其中 $P(H_{\mathfrak{X}_k})$ 是向子空间 $H_{\mathfrak{X}_k}$ 的直交投影算子。现在来求 $A$ ，根据式(15.12-2)和(15.12-3)可得到

$$
\stackrel {\circ} {E} _ {k} = Y _ {1 k} - \stackrel {\circ} {A} \mathcal {X} _ {k}
$$

对上述等式的两边分别求与 $\mathfrak{X}_k$ 的相关阵就有

$$
O = R _ {k} ^ {\prime} \mathcal {X} _ {k} = R _ {1 k} \mathcal {X} _ {k} - A \Sigma_ {k} ^ {2}
$$

和

$$
\stackrel {\circ} {A} = R _ {Y _ {1 k}} \mathfrak {X} _ {k} \Sigma_ {\mathfrak {X} _ {k}} ^ {- 2}
$$

于是最优过滤器的输出可表达为

$$
\mathbf {Y} _ {k} = P \left(H _ {\mathfrak {X} _ {k}}\right) \mathbf {Y} _ {1 k} = R _ {\mathbf {Y} _ {1 k}} \mathfrak {X} _ {k} \Sigma_ {\mathfrak {X} _ {k}} ^ {- 2} \mathfrak {X} _ {k} \tag {15.12-4}
$$

最优输出误差为

$$
\mathbf {E} _ {k} = \mathbf {Y} _ {1 k} - P (H _ {\mathfrak {X} _ {k}}) \mathbf {Y} _ {1 k} = \mathbf {Y} _ {1 k} - R _ {\mathbf {Y} _ {1 k} \mathfrak {X} _ {k}} \Sigma_ {\mathfrak {X} _ {k}} ^ {- 2} \mathfrak {X} _ {k} \tag {15.12-5}
$$

很容易验证，这样表达的直交投影算子 $P(H_{\mathfrak{X}_{k}})$ 的确是线性，自伴且幂等的。

同样，在观测量这个 m 维随机向量空间 $H_{m}$ 中也可以构成一个子空间 $S_{K_{k}}$ ， $S_{K_{k}}$ 中的任意元的每一个分量都是观测量 $X_{k}$ 的各分量的某种线性组合。一般来说，在 $H_{m}$ 中 $t_{k+1}$ 时刻的观测量 $X_{k+1}$ 与子空间 $S_{K_{k}}$ 不是直交的，但是

$$
\widetilde {\boldsymbol {X}} _ {k + 1} = \boldsymbol {X} _ {k + 1} - P (\mathfrak {X} _ {k}) \boldsymbol {X} _ {k + 1} = \boldsymbol {X} _ {k + 1} - R _ {x _ {k + 1}} \mathfrak {X} _ {k} \Sigma_ {\mathfrak {X} _ {k}} ^ {- 2} \mathfrak {X} _ {k} \tag {15.12-6}
$$

是与子空间 $\widetilde{\mathcal{X}}_k$ 直交的， $\widetilde{X}_{k+1}$ 就是在 $H_m$ 中 $X_{k+1}$ 到子空间 $\widetilde{\mathcal{X}}_k$ 的垂线，所以

$$
P (\widetilde {\mathfrak {X}} _ {k}) \widetilde {\boldsymbol {X}} _ {k + 1} = \mathbf {0} \tag {15.12-7}
$$

$X_{k+1}$ 的每个分量与 $X_{k}$ 的每个分量分别互相直交, 因此

$$
R _ {x _ {k + 1}} ^ {\sim} \mathfrak {X} _ {k} = O \tag {15.12-8}
$$

$t_{k+1}$ 时刻的过滤器输入是观测量 $\widetilde{\mathcal{X}}_{k+1} = (\widetilde{\mathcal{X}}_k, \mathbf{X}_{k+1})$ ，过滤器的输出 $Y_{k+1}$ 在空间 $H_n$ 中构成一个子空间 $H_{\widetilde{\mathcal{X}}_{k+1}}$ ， $H_{\widetilde{\mathcal{X}}_{k+1}}$ 中任意元的每一个分量分别是观测量 $\widetilde{\mathcal{X}}_k$ ， $X_{k+1}$ 的各分量的某种线性组合，由式(15.12-6)可知，它们也是 $\widetilde{\mathcal{X}}_k$ ， $X_{k+1}$ 各分量的某种线性组合。这样，子空间 $H_{\widetilde{\mathcal{X}}_{k+1}}$ 可以分解为两个互相直交的子空间 $H_{\widetilde{\mathcal{X}}_k}$ 和 $H_{\widetilde{x}_{k+1}}$ 的直交和。 $H_{\widetilde{\mathcal{X}}_{k+1}}$ ， $H_{\widetilde{\mathcal{X}}_k}$ 和 $H_{x_{k+1}}$ ，都是 $H_n$ 中的子空间， $H_{\widetilde{x}_{k+1}}$ 中的任意元的每个分量是 $X_{k+1}$ 各分量的某种线性组合。因此，直交投影算子有如下的关系

$$
P (H _ {\mathfrak {X} _ {k + 1}}) = P (H _ {\mathfrak {X} _ {k}}) + P (H _ {\widetilde {x} _ {k + 1}}) \tag {15.12-9}
$$

$X_{k+1}$ 是 $t_k$ 时刻新增加的观测量，但它的一部分 $P(\widetilde{X}_{k})X_{k+1}$ 是以前观测量 $X_0$ , $X_1, \cdots, X_k$ 中含有的信息，只有 $\widetilde{X}_{k+1}$ 才是 $t_{k+1}$ 时刻新增加的信息，所以称 $\widetilde{X}_{k+1}$ 为新息。新息序列 $\{\widetilde{X}_k\}$ 就是观测量序列 $\{X_k\}$ 经过直交化后得到的。

在下列随机序列线性过滤问题中，待检测信号 $F_{k}$ 是数学期望为零的 n 维随机列向量，它满足下列方程

$$
\boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {F} _ {k} + G _ {k} \boldsymbol {W} _ {k}, \quad k = 0, 1, 2, \dots \tag {15.12-10}
$$

观测量 $X_{k}$ 是数学期望为零的 m 维随机向量, 它满足方程

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {N} _ {k}, \quad k = 0, 1, 2, \dots \tag {15.12-11}
$$

其中 $W_{k}, N_{k}$ 分别是 p 维, m 维的白色高斯随机序列, 数学期望为零, 它们之间互不相关, 即

$$
\overline {{{\boldsymbol {W}}}} _ {k} = \mathbf {0}, \quad R w _ {k} w _ {j} = \Sigma_ {w _ {k}} ^ {2} \delta_ {k _ {j}}, \quad \delta_ {k _ {j}} = \left\{ \begin{array}{l l} 0, & k \neq j \\ 1, & k = j \end{array} \right.
$$

$$
\overline {{{{N}}}} _ {k} = \mathbf {0}, \quad R _ {N _ {k} N _ {j}} = \sum_ {N _ {k}} ^ {2} \delta_ {k j}, \quad R _ {W _ {k} N _ {j}} = 0
$$

$$
k = 0, 1, 2, \dots , \quad j = 0, 1, 2, \dots \tag {15.12-12}
$$

$\Phi_{k+1,k}, G_k, C_k$ 分别是相应阶的非随机矩阵。设 $t_0$ 时刻的信号初值 $F_0$ 的数学期望为零，方差是 $\Sigma_{F_0}^2$ ，它与 $W_k, N_k$ 都不相关

$$
\overline {{{\boldsymbol {F}}}} _ {0} = \mathbf {0}, \quad R _ {F _ {0} W _ {k}} = O, \quad R _ {F _ {0} N _ {k}} = O, \quad k = 0, 1, 2, \dots \tag {15.12-13}
$$

设过滤器的理想输出是待检测信号本身，即

$$
\mathbf {Y} _ {1 k} = \mathbf {F} _ {k}, \quad k = 0, 1, 2, \dots \tag {15.12-14}
$$

过滤器在 $t_{k}$ 时刻的输出 $Y_{k}$ 是输入的观测量 $X_{1}, X_{2}, \cdots, X_{k}$ 各分量的线性函数，现在要找一个输出均方误差最小的最优线性过滤器。

从方程(15.12-10)—(15.12-14)可以立即得出：待检测信号 $F_{k}$ 和观测量 $X_{k}$

与 $t_{k}$ 时刻以后的 $W_{j}, N_{j}$ 都不相关

$$
R _ {F _ {k} w _ {j}} = O, \quad j \geqslant k; \quad R _ {X _ {k} w _ {j}} = O; \quad j \geqslant k
$$

$$
R _ {X _ {k} N _ {j + 1}} = O, \quad j \geqslant k; \quad R _ {F _ {k} N _ {j}} = O
$$

$$
k = 0, 1, 2, \dots , \quad j = 0, 1, 2, \dots \tag {15.12-15}
$$

从前面已知，最优过滤器在 $t_{k}$ 时刻和 $t_{k+1}$ 时刻的输出分别是

$$
\mathbf {Y} _ {k} = P (H \mathfrak {X} _ {k}) \mathbf {F} _ {k} \tag {15.12-16}
$$

$$
\mathbf {Y} _ {k + 1} = P \left(H _ {\mathfrak {X} _ {k + 1}}\right) \mathbf {F} _ {k + 1} \tag {15.12-17}
$$

根据式(15.12-9)， $F_{k+1}$ 在子空间 $H_{X_{k+1}}$ 上的直交投影等于 $F_{k+1}$ 分别在子空间 $H_{X_{k}}$ 和 $H_{\widetilde{x}_{k+1}}$ 上直交投影之和（见图 15.12-1）。

$$
P \left(H _ {\mathfrak {X} ^ {k + 1}}\right) \mathring {\mathbf {Y}} _ {k + 1} = P \left(H _ {\mathfrak {X} ^ {k}}\right) \boldsymbol {F} _ {k + 1} + P \left(H _ {\widetilde {x} _ {k + 1}}\right) \boldsymbol {F} _ {k + 1} \tag {15.12-18}
$$

上式中第一项是 $F_{k+1}$ 在子空间 $Hx_{k}$ 上的直交投影，由式(15.12-10)，(15.12-15)和(15.12-16)就得到

$$
P (H _ {\mathfrak {X} _ {k}}) \boldsymbol {F} _ {k + 1} = P (H _ {\mathfrak {X} _ {k}}) (\Phi_ {k + 1, k} \boldsymbol {F} _ {k} + G _ {k} \boldsymbol {W} _ {k})
$$

$$
= \Phi_ {k + 1, k} P (H _ {\mathfrak {X} _ {k}}) F _ {k} + P (H _ {\mathfrak {X} _ {k}}) G _ {k} W _ {k} = \Phi_ {k + 1, k} Y _ {k} \tag {15.12-19}
$$

$F_{k+1}$ 到子空间 $H_{X_{k}}$ 的垂线记以 $F_{k+1}$ ，由式(15.12-3)，(15.12-10)和(15.12-19)可以得到

$$
\boldsymbol {F} _ {k + 1} = \boldsymbol {F} _ {k + 1} - P \left(H \mathfrak {X} _ {k}\right) \boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \left(\boldsymbol {F} _ {k} - \boldsymbol {Y} _ {k}\right) + G _ {k} \boldsymbol {W} _ {k} = \Phi_ {k + 1, k} \boldsymbol {E} _ {k} + G _ {k} W _ {k} \tag {15.12-20}
$$

> 此处省略原书 **图 15.12-1**

显然， $F_{k+1}$ 在子空间 $H_{x_{k+1}}^{\sim}$ 上的投影就等于 $F_{k+1}$ 在子空间 $H_{x_{k+1}}^{\sim}$ 上的投影

$$
P \left(H \tilde {x} _ {k + 1}\right) \widetilde {\boldsymbol {F}} _ {k + 1} = P \left(H \tilde {x} _ {k + 1}\right) \left[ \boldsymbol {F} _ {k + 1} - P \left(H \mathfrak {X} _ {k}\right) \boldsymbol {F} _ {k + 1} \right] = P \left(H \tilde {x} _ {k + 1}\right) \boldsymbol {F} _ {k + 1} \tag {15.12-21}
$$

由式(15.12-20)可得出 $F_{k+1}$ 的方差阵为

$$
\Sigma_ {\widetilde {F} _ {k + 1}} ^ {2} = \Phi_ {k + 1, k} \Sigma_ {\mathring {E} k} ^ {2} \Phi_ {k + 1, k} ^ {\tau} + G _ {k} \Sigma_ {W _ {k}} ^ {2} G _ {k} ^ {\tau} \tag {15.12-22}
$$

其中 $\Sigma_{E_{k}}^{2}$ 是 $t_{k}$ 时刻最优输出误差的方差阵。

由式(15.12-6)，(15.12-11)，(15.12-15)和(15.12-20)可以得到新息 $X_{k+1}$ 的表达式

$$
\begin{array}{l} \boldsymbol {X} _ {k + 1} = \boldsymbol {X} _ {k + 1} - P (\tilde {\mathcal {Y}} _ {k}) \boldsymbol {X} _ {k + 1} = \boldsymbol {X} _ {k + 1} - P (\tilde {\mathcal {Y}} _ {k}) C _ {k + 1} \boldsymbol {F} _ {k + 1} - P (\tilde {\mathcal {Y}} _ {k}) N _ {k + 1} \\ = \boldsymbol {X} _ {k + 1} - C _ {k + 1} P \left(H _ {\mathfrak {X} _ {k}}\right) \boldsymbol {F} _ {k + 1} = \boldsymbol {X} _ {k + 1} - C _ {k + 1} \Phi_ {k + 1, k} \boldsymbol {Y} _ {k} \tag {15.12-23} \\ \end{array}
$$

或

$$
\boldsymbol {X} _ {k + 1} = C _ {k + 1} \Phi_ {k + 1, k} \dot {\boldsymbol {E}} _ {k} + C _ {k + 1} G _ {k} \boldsymbol {W} _ {k} + \boldsymbol {N} _ {k + 1} = C _ {k + 1} \boldsymbol {F} _ {k + 1} + \boldsymbol {N} _ {k + 1} \tag {15.12-24}
$$

现在来计算式(15.12-18)中右边的第二个分量。根据式(15.12-4)中直交投影算子 $P(H_{\mathfrak{X}_k})$ 的表达形式可以得到

$$
P \left(H _ {x _ {k + 1}} ^ {\sim}\right) \boldsymbol {F} _ {k + 1} = P \left(H _ {x _ {k + 1}} ^ {\sim}\right) \widetilde {\boldsymbol {F}} _ {k + 1} = R _ {F _ {k + 1}, x _ {k + 1}} \Sigma_ {x _ {k + 1}} ^ {- 2} \widetilde {\boldsymbol {X}} _ {k + 1}
$$

根据式(15.12-20)，(15.12-15)和 $Y_{k}\in Hx_{k}$ ，所以得到

$$
R _ {F _ {k + 1}, N _ {k + 1}} ^ {\sim} = \Phi_ {k + 1, k} R _ {F _ {k}, N _ {k + 1}} - \Phi_ {k + 1, k} R _ {Y _ {k}, N _ {k + 1}} ^ {\circ} + G _ {k} R _ {W _ {k}, N _ {k + 1}} = O
$$

因此

$$
R _ {F _ {k + 1}, X _ {k + 1}} ^ {\sim} = \Sigma_ {F _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + R _ {F _ {k + 1}, N _ {k + 1}} ^ {\sim} = \Sigma_ {F _ {k + 1}} ^ {2} G _ {k + 1} ^ {\tau} \tag {15.12-25}
$$

$$
\begin{array}{l} \Sigma_ {\widetilde {X} _ {k + 1}} ^ {2} = C _ {k + 1} \Sigma_ {\widetilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + \Sigma_ {N _ {k + 1}} ^ {2} + C _ {k + 1} R _ {\widetilde {F} _ {k + 1}, N _ {k + 1}} + R _ {N _ {k + 1}, F _ {k + 1}} C _ {k + 1} ^ {\tau} \\ = C _ {k + 1} \Sigma_ {\widetilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + \Sigma_ {N _ {k + 1}} ^ {2} \tag {15.12-26} \\ \end{array}
$$

我们把 $R_{F_{k+1}} \widetilde{x}_{k+1} \Sigma_{\widetilde{x}_{k+1}}^{2}$ 叫做最优线性过滤的增益阵，记以 $K_{k+1}$ ，它是一个 $n \times m$ 阶矩阵

$$
K _ {k + 1} = R _ {F _ {k + 1}} \tilde {x} _ {k + 1} \Sigma_ {\tilde {X} _ {k + 1}} ^ {- 2} = \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} (C _ {k + 1} \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + \Sigma_ {N _ {k + 1}} ^ {2}) ^ {- 1} \tag {15.12-27}
$$

$K_{k+1}$ 的几何意义就是 $F_{k+1}$ （或 $\widetilde{F}_{k+1}$ ）在子空间 $H\widetilde{x}_{k+1}$ 上的直交投影的系数阵。于是， $t_{k+1}$ 时刻最优线性过滤的输出 $\mathring{Y}_{k+1}$ 就可以由 $t_{k}$ 时刻的输出 $\mathring{Y}_{k}$ 递推得到

$$
\mathbf {Y} _ {k + 1} = \Phi_ {k + 1, k} \mathbf {Y} _ {k} + K _ {k + 1} \left[ \mathbf {X} _ {k + 1} - C _ {k + 1} \Phi_ {k + 1, k} \mathbf {Y} _ {k} \right] \tag {15.12-28}
$$

如果取信号初值的数学期望 $\overline{F}_{0}$ 作为最优输出的初值 $Y_{0}$ ;那么 $Y_{k+1}$ 的数学期望和 $F_{k+1}$ 的数学期望同样都是零，所以是无偏的。

为了完成递推计算，还需要知道最优输出误差的方差阵 $\Sigma_{E_{k}}^{2}$ 的递推公式。由式(15.12-10)，(15.12-11)和(15.12-28)得到

$$
\begin{array}{l} \mathbf {\dot {E}} _ {k + 1} = \mathbf {F} _ {k + 1} - \mathbf {\dot {Y}} _ {k + 1} = (E - K _ {k + 1} C _ {k + 1}) [ \Phi_ {k + 1, k} \mathbf {\dot {E}} _ {k} + G _ {k} W _ {k} ] - K _ {k + 1} N _ {k + 1} \\ = \left(E - K _ {k + 1} C _ {k + 1}\right) F _ {k + 1} - K _ {k + 1} N _ {k + 1} \tag {15.12-29} \\ \end{array}
$$

因此

$$
\Sigma_ {\mathbf {E} _ {k + 1}} ^ {2} = \left(E - K _ {k + 1} C _ {k + 1}\right) \Sigma_ {\widetilde {\mathbf {F}} _ {k + 1}} ^ {2} \left(E - K _ {k + 1} C _ {k + 1}\right) ^ {\tau} + K _ {k + 1} \Sigma_ {\mathbf {N} _ {k + 1}} ^ {2} K _ {k + 1} ^ {\tau} (1 5. 1 2 - 3 0)
$$

其中 E 为单位矩阵，将 $F_{0}$ 的方差阵 $\Sigma_{F_{0}}^{2}$ 作为输出误差方差阵的初值 $\Sigma_{E_{0}}^{2}$ ，最小的均方误差就是方差阵 $\Sigma_{E_{k}}^{2}$ 的迹。

如果 $K_{k+1}$ 不取式(15.12-27)中计算出来的值，那么由式(15.12-28)得出的输出 $Y_{k}$ 就不是最优的，由式(15.12-30)得出的输出误差方差阵 $\Sigma_{E_{k}}^{2}$ 也不是最优的，故 $\mathrm{tr}(\Sigma_{E_{k}}^{2})\geqslant\mathrm{tr}(\Sigma_{E_{k}}^{2})$ 。

把上面叙述的递推计算公式综合起来可以建立如下的计算流程图。

> 此处省略原书 **图 15.12-2**

这样，在已给定的信号模型和观测量模型特性 $\Phi_{k+1,k}, G_{k}, C_{k}$ 和 $W_{k}, N_{k}$ 的统计特性 $\Sigma_{W_{k}}^{2}, \Sigma_{N_{k}}^{2}$ 的条件下，由初始条件 $Y_{0} \Sigma_{E_{0}}^{2}$ 和观测值的某个现实 $x_{k}, k=0,1,2,\cdots$ 就可以递推计算出最优线性过滤的增益阵 $K_{k}$ ，最优输出的某个现实 $y_{k}, k=0,1,2,\cdots$ 和最优输出误差的方差 $\Sigma_{E_{k}}^{2}$ 。如果只对输出误差的方差感兴趣，那可以不必计算增益阵和最优输出，这时 $\Sigma_{E_{k+1}}^{2}$ 也可以不必从 $K_{k+1}$ 算出。把式(15.12-27)代入式(15.12-30)就得到

$$
\Sigma_ {\tilde {E} _ {k + 1}} ^ {2} = \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} - \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} (C _ {k + 1} \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + \Sigma_ {N _ {k + 1}} ^ {2}) ^ {- 1} C _ {k + 1} \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} \tag {15.12-31}
$$

只用式(15.12-22)和式(15.12-31)就可直接递推算出最优输出误差的方差阵，同样，式(15.12-30)也可写成另一种形式

$$
\Sigma_ {\tilde {E} _ {k + 1}} ^ {2} = \left(E - K _ {k + 1} C _ {k + 1}\right) \Sigma_ {\tilde {F} _ {k + 1}} ^ {2} \tag {15.12-32}
$$

最优线性递推过滤器的结构可以用图 15.12-3 来表示, 它与信号模型有很密切的关系。

> 此处省略原书 **图 15.12-3**

正因为理想输出（即待检测信号）有它的规律性，根据前一时刻的值可以大概估计现时值，所以过滤器的实际输出也应遵循此规律。但是还知道与待测信号现时值有关系的观测值，这样可以根据现时的观测值对实际输出进行修正。而现时观测值中的一部分与以前的观测值有关，因此只需用现时观测值中的新息部分来修正实际输出。这相当于一个反馈控制系统，只要选择合适的增益阵就能使输出的均方误差最小。如果信号是白色的，无法根据前一时刻的值来估计现时值，那么过滤器只能根据现时观测值来估计现时信号值。如果在观测值中噪声 $N_{k}$ 占了很大比重，那么增益阵 $K_{k}$ 就“很小”,过滤器基本上根据信号的规律性由前一时刻的输出值来推算现时的输出值。

从这个最优递推线性过滤器出发，现在已有了许多推广，我们在这里只叙述几种情况，其他情况可以参看文献 $[21,25]$ 。

第一种情况：如果信号和观测量随机向量的数学期望不是零，或者含有非随机的分量，我们都可以把它归结为含有非随机的分量。这时信号和观测值可表示为

$$
\boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {F} _ {k} + \Psi_ {k} \boldsymbol {u} _ {k} + G _ {k} \boldsymbol {W} _ {k} \tag {15.12-33}
$$

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {d} _ {k} + \boldsymbol {N} _ {k} \tag {15.12-34}
$$

其中 $u_{k}, d_{k}$ 分别是 r 维，m 维非随机的向量序列， $\Psi_{k}$ 为 $n \times r$ 阶矩阵，信号初值 $F_{0}$ 的数学期望可能不是零，其他都和以前的假设一样。这时，信号和观测量的数学

期望都不等于零

$$
\overline {{{\boldsymbol {F}}}} _ {k + 1} = \Phi_ {k + 1, k} \overline {{{\boldsymbol {F}}}} _ {k} + \Psi_ {k} \boldsymbol {u} _ {k} \tag {15.12-35}
$$

$$
\overline {{{\boldsymbol {X}}}} _ {k} = \boldsymbol {C} _ {k} \overline {{{\boldsymbol {F}}}} _ {k} + \boldsymbol {d} _ {k} \tag {15.12-36}
$$

为了保证输出的无偏性，要求

$$
\overline {{{\boldsymbol {Y}}}} _ {k} = \overline {{{\boldsymbol {F}}}} _ {k} \tag {15.12-37}
$$

这时 $F_{k}-\overline{F}_{k}, X_{k}-\overline{X}_{k}$ 的数学期望都是零，它们满足于式(15.12-10)和(15.12-11)，我们可以得到 $\mathring{Y}_{k+1}-\overline{\mathring{Y}}_{k+1}$ 的最优输出，再考虑到式(15.12-35)—(15.12-37)就可以得出 $t_{k+1}$ 时刻的最优输出

$$
\mathbf {\dot {Y}} _ {k + 1} = \Phi_ {k + 1, k} \mathbf {\dot {Y}} _ {k} + \Psi_ {k} \mathbf {u} _ {k} + K _ {k + 1} \left(\mathbf {X} _ {k + 1} - \mathbf {d} _ {k + 1} - C _ {k + 1} \Phi_ {k + 1, k} \mathbf {\dot {Y}} _ {k} - C _ {k + 1} \Psi_ {k} \mathbf {u} _ {k}\right) \tag {15.12-38}
$$

初值是 $\dot{Y}_{0} = \overline{F}_{0}$ ，而 $\Sigma_{\widetilde{F}_{k+1}}^{2}, K_{k+1}, \Sigma_{\dot{E}_{k+1}}^{2}$ 的计算都和数学期望无关，所以式 (15.12-22)，(15.12-27) 和 (15.12-30) 仍有效。

第二种情况: 在信号和输入模型式(15.12-10)和(15.12-11)中, 信号 $F_{k}$ 和噪声 $N_{k}$ 相关。

(1) 如果

$$
R _ {W _ {k}, N _ {j + 1}} = R _ {W N _ {k}} \delta_ {k j} \tag {15.12-39}
$$

那么 $F_{k}$ 和 $N_{k}$ 只在同一时刻才相关。这时求 $Y_{k+1}$ 的式(15.12-27)和求 $\Sigma_{F_{k+1}}^{2}$ 的式(15.12-22)都不变，而求 $K_{k+1}$ 的式(15.12-27)就应改为

$$
\begin{array}{l} K _ {k + 1} = \left(\sum_ {\widetilde {F} _ {k + 1}} ^ {2} C _ {k + 1} ^ {\tau} + G _ {k} R _ {W N _ {k}}\right) \\ \times \left[ C _ {k + 1} \Sigma_ {\widetilde {F}} ^ {2} _ {k + 1} C _ {k + 1} ^ {\tau} + \Sigma_ {N _ {k + 1}} ^ {2} + C _ {k + 1} G _ {k} R _ {W N _ {k}} + R _ {W N _ {k}} ^ {\tau} G _ {k} ^ {\tau} C _ {k + 1} ^ {\tau} \right] ^ {- 1} \tag {15.12-40} \\ \end{array}
$$

求 $\Sigma_{E_{k+1}}^{2}$ 的式(15.12-30)应改为

$$
\begin{array}{l} \Sigma_ {E _ {k + 1}} ^ {2} = \left(E - K _ {k + 1} C _ {k + 1}\right) \Sigma_ {F _ {k + 1}} ^ {2} \left(E - K _ {k + 1} C _ {k + 1}\right) ^ {\tau} + K _ {k + 1} \Sigma_ {N _ {k + 1}} ^ {2} K _ {k + 1} \\ - \left(E - K _ {k + 1} C _ {k + 1}\right) G _ {k} R _ {W N _ {k}} K _ {k + 1} ^ {\tau} - K _ {k + 1} R _ {W N _ {k}} ^ {\tau} G _ {k} ^ {\tau} \left(I - K _ {k + 1} C _ {k + 1}\right) ^ {\tau} \tag {15.12-41} \\ \end{array}
$$

(2)如果

$$
R _ {W _ {k} N _ {j}} = R _ {W N _ {k}} \delta_ {k j} \tag {15.12-42}
$$

这时，求最优递推输出 $Y_{k+1}$ 的式(15.12-28)应改为

$$
\mathbf {Y} _ {k + 1} = P \left(H _ {\mathfrak {X} _ {k}}\right) \boldsymbol {F} _ {k + 1} + K _ {k + 1} \left[ \boldsymbol {X} _ {k + 1} - C _ {k + 1} P \left(H _ {\mathfrak {X} _ {k}}\right) \boldsymbol {F} _ {k + 1} \right] \tag {15.12-43}
$$

$$
P (H _ {\mathfrak {X} _ {k}}) \boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \stackrel {\circ} {\boldsymbol {Y}} _ {k} + (G _ {k} R _ {W N _ {k}} \Sigma_ {N _ {k}} ^ {- 2}) (\boldsymbol {X} _ {k} - C _ {k} \stackrel {\circ} {\boldsymbol {Y}} _ {k}) \tag {15.12-44}
$$

求 $\Sigma_{\widetilde{F}_{k+1}}^{2}$ 的式(15.12-22)应改为

$$
\begin{array}{l} \Sigma_ {\widetilde {F} k + 1} ^ {2} = \left(\Phi_ {k + 1, k} - G _ {k} R _ {W N _ {k}} \Sigma_ {N _ {k}} ^ {- 2}\right) \Sigma_ {\mathring {E} _ {k}} ^ {2} \left(\Phi_ {k + 1, k} - G _ {k} R _ {W N _ {k}} \Sigma_ {N _ {k}} ^ {- 2}\right) ^ {\tau} \\ + G _ {k} \Sigma_ {W _ {k}} ^ {2} G _ {k} ^ {\tau} - G _ {k} R _ {W N _ {k}} \Sigma_ {N _ {k}} ^ {- 2} R _ {W N _ {k}} ^ {\tau} G _ {k} ^ {\tau} \tag {15.12-45} \\ \end{array}
$$

而求 $K_{k + 1}$ 的式(15.12-27)和求 $\sum_{E_{k + 1}}^{2}$ 的式(15.12-30)都不变。

显然，在这两种情况中如果 $R_{WN_k} = 0$ ，即 $\pmb{W}_k$ 序列和 $\pmb{N}_k$ 序列根本不相关，那么最优线性递推公式就是式(15.12-22)，(15.12-27)，(15.12-28)和(15.12-30)。当 $t_{k + 1} - t_k\rightarrow 0$ 时，随机序列就趋于随机过程，这两种情况的过滤公式都趋于第 15.11 节中的式(15.11-15)，(15.11-19)和(15.11-22)。

第三种情况为有色噪声问题。如果信号模型式(15.12-10)中随机序列 $W_{k}$ 不是白色的，它有某种不均匀的谱密度，那么可以把它看成是白色随机序列 $V_{k}$ 作用于某一线性成型滤波器后的输出序列

$$
\boldsymbol {W} _ {k + 1} = \Xi_ {k + 1, k} \boldsymbol {W} _ {k} + \boldsymbol {V} _ {k} \tag {15.12-46}
$$

其中 $V_{k}$ 与 $N_{k}$ 是互不相关的随机序列。把式(15.12-46)与(15.12-10)结合起来，可以构成一个新的信号模型

$$
\left[ \begin{array}{c} \boldsymbol {F} _ {k + 1} \\ \boldsymbol {W} _ {k + 1} \end{array} \right] = \left[ \begin{array}{c c} \Phi_ {k + 1, k} & \boldsymbol {G} _ {k} \\ 0 & \Xi_ {k} \end{array} \right] \left[ \begin{array}{c} \boldsymbol {F} _ {k} \\ \boldsymbol {W} _ {k} \end{array} \right] + \left[ \begin{array}{c} 0 \\ \boldsymbol {E} \end{array} \right] \boldsymbol {V} _ {k} \tag {15.12-47}
$$

其中 E 是单位矩阵而观测模型为

$$
\boldsymbol {X} _ {k} = \left(\boldsymbol {C} _ {k}, 0\right) \binom {\boldsymbol {F} _ {k}} {\boldsymbol {W} _ {k}} + \boldsymbol {N} _ {k} \tag {15.12-48}
$$

这样就可以按照白随机序列的情况去进行过滤。这种方法的缺点是新信号的维数扩大了，增加了计算量，而我们要求的输出只和新信号中部分分量有关。

对于观测模型中的随机序列 $N_{k}$ 是有色噪声的情况，也可以用扩大信号维数的方法。但这种新的观测模型中没有新的白噪声，这在计算中可能会碰到不可逆矩阵的求逆问题，使计算难于继续进行。处理输入模型中有色随机噪声的问题还有一些方法 $^{[5]}$ ,我们在这里就不再一一列举了。

第四种情况为预测过滤问题。如果过滤器在 $t_{k}$ 时刻的理想输出不是 $t_{k}$ 时刻的信号 $F_{k}$ ，而是 $t_{k+1}$ 时刻的信号 $F_{k+l}, l>0$ ，而过滤器的输入仍是 $t_{k}$ 以及以前时刻的观测值 $X_{1}, X_{2}, \cdots, X_{k}$ ，这就是预测过滤问题。由于信号模型式(15.12-10)中的 $\Phi_{k+1,k}$ 有这样的性质

$$
\Phi_ {k j} \Phi_ {j l} = \Phi_ {k l} \tag {15.12-49}
$$

$$
\Phi_ {k, k} = E \tag {15.12-50}
$$

因此

$$
\begin{array}{l} \boldsymbol {F} _ {k + l} = \Phi_ {k + l, k} \boldsymbol {F} _ {k} + \Phi_ {k + l, k + 1} \boldsymbol {G} _ {k} \boldsymbol {W} _ {k} + \dots + \Phi_ {k + l, k + l - 1} \boldsymbol {G} _ {k + l - 2} \boldsymbol {W} _ {k + l - 2} \\ + \boldsymbol {G} _ {k + l - 1} \boldsymbol {W} _ {k + l - 1} \tag {15.12-51} \\ \end{array}
$$

最优预测过滤器在 $t_{k}$ 时刻的输出是

$$
\begin{array}{l} P (H _ {\mathfrak {X} _ {k}}) \mathbf {Y} _ {1 k} = P (H _ {\mathfrak {X} _ {k}}) \mathbf {F} _ {k + l} \\ = \Phi_ {k + 1, k} P (H _ {\mathfrak {X} _ {k}}) \boldsymbol {F} _ {k} + \Phi_ {k + l, k + 1} P (H _ {\mathfrak {X} _ {k}}) G _ {k} \boldsymbol {W} _ {k} + \dots \\ + P (H _ {\mathfrak {X} _ {k}}) G _ {k + l - 1} W _ {k + l - 1} \tag {15.12-52} \\ \end{array}
$$

由式(15.12-15)知， $W_{j}(j\geqslant k)$ 的各分量与 $X_{1},X_{2},\cdots,X_{k}$ 的各分量（即 $X_{k}$ 的各分量）互相直交，因此上式中 $P(HX_{k})G_{k}W_{k}=0,\cdots,P(HX_{k})G_{k+l-1}W_{k+l-1}=0$ ，最优输出是

$$
P (H _ {\mathfrak {X} _ {k}}) \boldsymbol {F} _ {k + l} = \Phi_ {k + l, k} P (H _ {\mathfrak {X} _ {k}}) \boldsymbol {F} _ {k} \tag {15.12-53}
$$

最优预测过滤器在 $t_{k}$ 时刻的输出误差是

$$
\boldsymbol {F} _ {k + 1} - P \left(H x _ {k}\right) \boldsymbol {F} _ {k + l} = \Phi_ {k + l, k} \boldsymbol {E} _ {k} + \Phi_ {k + l, k + 1} G _ {k} \boldsymbol {W} _ {k} + \dots + G _ {k + l - 1} \boldsymbol {W} _ {k + l - 1}
$$

它的方差阵是

$$
\begin{array}{l} \Sigma_ {\left(\boldsymbol {F} _ {k + l} - P \left(H _ {\mathfrak {X} _ {k}}\right) \boldsymbol {F} _ {k + l}\right)} ^ {2} = \Phi_ {k + l, k} \Sigma_ {\hat {\boldsymbol {E}} _ {k}} ^ {2} \Phi_ {k + l, k} ^ {\tau} + \Phi_ {k + l, k + 1} G _ {k} \Sigma_ {\boldsymbol {W} _ {k}} ^ {2} G _ {k} ^ {\tau} \Phi_ {k + l, k + 1} ^ {\tau} \\ + \Phi_ {k + l, k + l - 1} G _ {k + l - 2} \sum_ {w _ {k + l - 2}} ^ {2} G _ {k + l - 2} ^ {\tau} \Phi_ {k + l, k + l - 1} ^ {\tau} \\ + G _ {k + l - 1} \Sigma_ {W _ {k + l - 1}} ^ {2} G _ {k + l - 1} ^ {\tau} \tag {15.12-54} \\ \end{array}
$$

其中 $E_{k}$ 是最优线性过滤器在 $t_{k}$ 时刻的输出误差， $\Sigma_{E_{k}}^{2}$ 是最优线性过滤器输出误差的方差阵。

同样可以用这种基本方法去解决各种最优线性平滑问题。

#### 15.13 递推过滤的渐近特性和误差分析 $^{[5]}$

现在我们来对最优线性递推过滤作进一步的分析。已经知道，在作递推计算时，需要知道信号在初始时刻的统计特性（数学期望和方差)。如果我们不能确切知道这些统计特性，甚至完全不知道，那么在取初值时就会有一定的误差，甚至是随机地选取。最优输出，输出误差的方差阵和最优增益阵都是从选定的初值开始递推计算的，那么这对过滤有些什么影响？

过滤器的最优输出可以写为

$$
\mathbf {Y} _ {k + 1} = (E - K _ {k + 1} C _ {k + 1}) \Phi_ {k + 1, k} \mathbf {Y} _ {k} + K _ {k + 1} \mathbf {X} _ {k} \tag {15.13-1}
$$

当输入的一个现实 $x_{k}$ 时间序列加到已设计好的最优过滤器后, 就可以得到输出的一个现实 $y_{k+1}$ 的时间序列

$$
\mathbf {y} _ {k + 1} = \left(E - K _ {k + 1} C _ {k + 1}\right) \Phi_ {k + 1, k} \mathbf {y} _ {k} + K _ {k + 1} \mathbf {x} _ {k} \tag {15.13-2}
$$

这是一个变系数线性差分方程。我们知道：

（1）如果对任何非负的整数 $M$ ，矩阵 $\prod_{k = 0}^{M}(E - K_{k + 1}C_{k + 1})\Phi_{k + 1,k}$ 的范数 ① 都小

于某个常数，那么过滤器对初始值来说是稳定的，也就是只要过滤器的两个初值 $y_{0}$ 的差充分地小，那么由这两个初值开始计算的两个输出的差也是小的。

（2）如果 $\prod_{k=0}^{M}(E - K_{k+1}C_{k+1})\Phi_{k+1,k}$ 矩阵的范数在 $M$ 增长时趋于零，那么此过滤器对初值是渐近稳定的，也就是无论输出的初值 $\mathbf{y}_0$ 怎么取，只要 $k$ 充分大后输出 $\mathbf{y}_k$ 都趋于同一个解。

（3）如果对所有的非负整数 $M \geqslant L \geqslant 0$ ，矩阵 $\prod_{k=0}^{M} (E - K_{k+1} C_{k+1}) \Phi_{k+1, k}$ 的范数小于指数序列 $c_2 e^{-c_1 (M-L)}$ ， $c_1$ ， $c_2$ 都是大于零的常数，那么此过滤器是一致渐近稳定的，也就是除了对初值渐近稳定外，只要输入序列 $x_k$ 是有界的，那么输出序列 $y_k$ 也是有界的。在用数字机计算时，如果输入数据的字长是有界的，就总可以选定机器的字长使输出数据在任何时刻都不溢出。

为了说明什么样的信号和观测模型对应的最优线性递推过滤器是一致渐近稳定的，我们先介绍“一致完全能控制”和“一致完全能观测”这两个概念。假定信号和输入模型仍满足式(15.12-10)—(15.12-15)，如果存在某个正整数 $N$ ，使得能控矩阵 $C(k - N + 1,k)$ 是正定的，即

$$
C (k - N + 1, k) = \sum_ {i = k - N + 1} ^ {k} \Phi_ {k, i} G _ {i - 1} \Sigma_ {w _ {i - 1}} ^ {2} G _ {i - 1} ^ {\tau} \Phi_ {k, i} ^ {\tau} > 0 \tag {15.13-3}
$$

那么信号和观测模型式(15.12-10)和(15.12-11)叫做在 $t_k$ 时刻完全能控的。能控矩阵 $C(k-N+1,k)$ 与 $t_k$ 有关。如果存在正整数 $N$ ，使对所有的 $k \geqslant N$ ，矩阵 $C(k-N+1,k)$ 有一致的上下界

$$
\alpha_ {c} E \leqslant C (k - N + 1, k) \leqslant \beta_ {c} E, \quad \alpha_ {c} > 0, \quad \beta_ {c} > 0 \tag {15.13-4}
$$

其中 E 是单位矩阵，那么信号和观测模型式(15.12-10)和(15.12-11)叫做一致完全能控的。如果存在正整数 N,使得能观测矩阵 $O(k-N+1,k)$ 正定，即

$$
O (k - N + 1, k) = \sum_ {j = k - N + 1} ^ {k} \Phi_ {j, k} ^ {\tau} C _ {j} ^ {\tau} \Sigma_ {N j} ^ {- 2} C _ {j} \Phi_ {j k} > 0 \tag {15.13-5}
$$

那么信号和观测模型式(15.12-10)和(15.12-11)叫做在 $t_{k}$ 时刻完全能观测的。如果存在正整数 N，使对所有的 $k\geqslant N$ ，矩阵 $O(k-N+1,k)$ 有一致的上下界

$$
\alpha_ {0} E \leqslant O (k - N + 1, k) \leqslant \beta_ {0} E, \quad \alpha_ {0} > 0, \quad \beta_ {0} > 0 \tag {15.13-6}
$$

那么信号和观测模型式(15.12-10)和(15.12-11)叫做一致完全能观测的。

我们可以看出，当 $\Sigma_{w_{i-1}}^{2}, \Sigma_{N_{j}}^{2}$ 是单位矩阵 E 时，能控矩阵 C 和能观测矩阵 O 就相当于 $W_{k}=0, N_{k}=0$ ，并且 $F_{k}, X_{k}$ 是非随机序列 $f_{k}, x_{k}$ 时的线性离散系统的能控矩阵和能观测矩阵。这里的“能控”和“能观测”概念有它自己的物理意义。由信号模型式(15.12-10)可知，在 $t_{k}$ 时刻的信号可以表达为

$$
\boldsymbol {F} _ {k} = \Phi_ {k, k - N} \boldsymbol {F} _ {k - N} + \sum_ {i = k - N - 1} ^ {k} \Phi_ {k i} G _ {i - 1} \boldsymbol {W} _ {i - 1} \tag {15.13-7}
$$

因此 $F_{k}-\Phi_{k,k-N}F_{k-N}$ 的方差阵就是

$$
\sum_ {\left(\boldsymbol {F} _ {k} - \Phi_ {k, k - N} \boldsymbol {F} _ {k}\right)} ^ {2} = \sum_ {i = k - N - 1} ^ {k} \Phi_ {k, i} G _ {i - 1} \Sigma_ {\boldsymbol {w} _ {i - 1}} ^ {2} G _ {i - 1} ^ {\tau} \Phi_ {k, i} ^ {\tau} = C (k - N + 1, k)
$$

能控矩阵 $C(k-N+1,k)$ 的正定性说明在 $t_{k-N}$ 时刻信号是 $F_{k-N}, t_{k}$ 时刻信号是 $F_{k}$ 的概率是正的，是可能的。如果能观测矩阵 $O(k-N+1,k)$ 正定，那么它的逆存在，取 $F_{k}$ 的估计值 $Y_{k}$ 为

$$
\mathbf {Y} _ {k} = O ^ {- 1} (k - N + 1, k) \sum_ {j = k - N - 1} ^ {N} \Phi_ {j, k} ^ {\tau} C _ {j} \Sigma_ {N _ {j}} ^ {- 2} \mathbf {X} _ {j} \tag {15.13-8}
$$

我们就可以只用 N 个时刻的观测值 $X_{k-N+1}, \cdots, X_{k}$ 来估计 $F_{k}$ ，这样的估计是无偏的， $\overline{Y}_{k} = \overline{F}_{k} = 0$ ，但它一般不是最优的。

如果信号和观测模型是一致完全能控和一致完全能观测的，那么可以证明下列事实:

(1) 最优递推线性过滤的输出误差的方差阵当 $k \geqslant 2N$ 时有上下界

$$
\frac {\alpha_ {c}}{1 + n ^ {2} \beta_ {0} \beta_ {c}} E \leqslant \Sigma_ {E _ {k}} ^ {2} \leqslant \frac {1 + n ^ {2} \beta_ {0} \beta_ {c}}{\alpha c} E
$$

其中 n 是 $F_{k}$ 和 $Y_{k}$ 的维数。

(2) 最优递推线性过滤器式(15.13-2)是一致渐近稳定的, 即

$$
\left| \prod_ {k = L} ^ {M} \left(E - K _ {k + 1} C _ {k + 1}\right) \Phi_ {k + 1, k} \right| \leqslant c _ {2} e ^ {- c _ {1} (M - L)}, \quad M \geqslant L \geqslant 0, \quad c _ {2} > 0, \quad c _ {1} > 0
$$

（3）当过滤时间充分长后，最优输出 $Y_{k}$ 将不依赖于初值 $Y_{0}$ 的选取，最优输出误差的方差阵 $\Sigma_{E_{k}}^{2}$ 也不依赖于初始方差阵 $\Sigma_{E_{0}}^{2}$ 的选取。这里需要说明一下，一致完全能控和一致完全能观测是一致渐近稳定和误差方差阵有上下界的充分条件。如果不满足一致完全能控和一致完全能观测的某些条件，误差的方差阵仍可能有界或一致渐近稳定。

如果信号和输入模型是线性常系数的，白色噪声序列 $N_{k}$ 和 $W_{k}$ 是平稳的，那么经过充分长时刻后信号和输入都近于平稳随机序列。对这种情况，一致完全能控与完全能控是一样的，一致完全能观测与完全能观测是一样的。当 $\Sigma_{W}^{2}>0$ 和 $\Sigma_{N}^{2}>0$ 时，它们的充分必要条件分别是

$$
\sum_ {L = 0} ^ {N - 1} \Phi^ {L} G G ^ {\tau} (\Phi^ {L}) ^ {\tau} > 0 \tag {15.13-9}
$$

$$
\sum_ {L = 0} ^ {N - 1} \left(\Phi^ {L}\right) ^ {\tau} C ^ {\tau} C \Phi^ {L} > 0 \tag {15.13-10}
$$

它们都与 $\Sigma_{w}^{2}$ 和 $\Sigma_{v}^{2}$ 的具体值无关, 这与非随机的线性常系数离散系统的完全能控、完全能观测的性能类似。我们还可以证明: 对完全能控和完全能观测的线性常系数系统, 不管取怎样的初值, 当时间充分长后, 它的输出误差的方差阵趋于一个唯一确定 的矩阵，同时它的最优增益阵也趋于一个确定的矩阵，这时过滤达到稳态。

上面考虑初值对过滤结果的影响是假设信号和观测模型都是准确的。实际上，经常发生这样的情况：按理论上说，最优过滤器是稳定的，可以算出有界的最优输出值和输出的方差阵；但是当这种理论上计算出来的最优过滤器加上观测值后，实际上得到的滤波器输出和输出误差的方差阵与理论上相差很远，甚至输出误差的方差会趋于无穷大，这样的过滤器就根本失去了作用。这称作发散现象。滤波“发散”的主要原因有下列几个方面：（1）由于对物理问题了解不够或在简化数学模型时造成信号和观测模型不准确。（2）对信号和噪声的统计特性取得不合适。（3）由于在数字计算中，受有穷字长的限制，计算的近似而引起的，特别是方差项或均方项逐渐失去正定和对称性时使真实值和理论值的差别愈来愈大。下面我们就模型不准和统计特性不准来进行分析。

假设，真实的信号和观测模型是

$$
\boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {F} _ {k} + \boldsymbol {u} _ {k} + \boldsymbol {W} _ {k} \tag {15.13-11}
$$

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {d} _ {k} + \boldsymbol {N} _ {k} \tag {15.13-12}
$$

其中 $W_{k}, N_{k}$ 是互不相关的数学期望是零的白色随机序列，它们的方差阵分别是 $\Sigma_{w_{k}}^{2}, \Sigma_{N_{k}}^{2}; u_{k}, d_{k}$ 是非随机的时间序列；信号初值与 $W_{k}, N_{k}$ 都不相关。但是在我们计算时却采取另外的信号和观测模型

$$
\boldsymbol {F} _ {k + 1} ^ {*} = \Phi_ {k + 1, k} ^ {*} \boldsymbol {F} _ {k} ^ {*} + \boldsymbol {u} _ {k} ^ {*} + \boldsymbol {W} _ {k} ^ {*} \tag {15.13-13}
$$

$$
\boldsymbol {X} _ {k} = C _ {k} ^ {*} \boldsymbol {F} _ {k} ^ {*} + \boldsymbol {d} _ {k} ^ {*} + \boldsymbol {N} _ {k} ^ {*} \tag {15.13-14}
$$

其中符号的意义与上面相同但数值不同，加上右上角注“\*”以示区别。根据式(15.13-13)和(15.13-14)得到的最优线性递推公式为

$$
\mathbf {\dot {Y}} _ {k + 1} ^ {*} = \Phi_ {k + 1, k} ^ {*} \mathbf {\dot {Y}} _ {k} ^ {*} + \mathbf {\dot {u}} _ {k} ^ {*} + K _ {k + 1} ^ {*} \left(\mathbf {X} _ {k + 1} - \mathbf {\dot {d}} _ {k + 1} ^ {*} - C _ {k + 1} ^ {*} \Phi_ {k + 1, k} ^ {*} \mathbf {\dot {Y}} _ {k} ^ {*} - C _ {k + 1} ^ {*} \mathbf {\dot {u}} _ {k} ^ {*}\right) \tag {15.13-15}
$$

$$
\begin{array}{l} K _ {k + 1} ^ {*} = \left(\Phi_ {k + 1, k} ^ {*} \Sigma_ {\tilde {E} _ {k 0} ^ {*}} ^ {2} \Phi_ {k + 1, k} ^ {* \tau} + \Sigma_ {W _ {k} ^ {*}} ^ {2}\right) C _ {k + 1} ^ {* \tau} \left(C _ {k + 1} ^ {*} \Phi_ {k + 1, k} ^ {*} \Sigma_ {\tilde {E} _ {k 0} ^ {*}} ^ {2} \Phi_ {k + 1, k} ^ {\tau} C _ {k + 1} ^ {* \tau} \right. \\ + C _ {k + 1} ^ {*} \Sigma_ {W _ {k}} ^ {2} * C _ {k + 1} ^ {* \tau} + \Sigma_ {N _ {k}} ^ {2}) ^ {- 1} \tag {15.13-16} \\ \end{array}
$$

$$
\begin{array}{l} \Sigma_ {\boldsymbol {E} _ {k + 1} ^ {*}} ^ {2} = (E - K _ {k + 1} ^ {*} C _ {k + 1} ^ {*}) (\Phi_ {k + 1, k} ^ {*} \Sigma_ {\boldsymbol {E} _ {k 0} ^ {*}} ^ {2} \Phi_ {k + 1, k} ^ {* \tau} + \Sigma_ {\boldsymbol {W} _ {k} ^ {*}} ^ {2}) (E - K _ {k + 1} ^ {*} C _ {k + 1} ^ {*}) \\ + K _ {k + 1} ^ {*} \sum_ {N _ {k + 1} ^ {*}} ^ {2} K _ {k + 1} ^ {* \tau} \\ = \left(E - K _ {k + 1} ^ {*} C _ {k + 1} ^ {*}\right) \left(\Phi_ {k + 1, k} ^ {*} \Sigma_ {\hat {E} _ {k 0} ^ {*}} ^ {2} \Phi_ {k + 1, k} ^ {* \tau} + \Sigma_ {W _ {k} ^ {*}} ^ {2}\right) \tag {15.13-17} \\ \end{array}
$$

初值 $\mathbf{Y}_0^* = \overline{\mathbf{F}_0^*}$ ， $\Sigma_{\mathbf{E}_0^*}^2 = \Sigma_{\mathbf{F}_0}^2$ 。它的渐近特性已在前面分析过。因为 $\mathbf{Y}_k^*$ 是无偏的，因此 $\overline{\mathbf{E}_k^*} = 0$ ，方差阵 $\Sigma_{\mathbf{E}_k^*}^2$ 就是均方误差阵 $\overline{\mathbf{E}_k^* \mathbf{E}_k^{*\tau}}$ 。而现在真实的误差是

$$
\boldsymbol {E} _ {k} = \boldsymbol {F} _ {k} - \overset {\circ} {\boldsymbol {Y}} _ {k} ^ {*}
$$

$$
\begin{array}{l} = \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) \Phi_ {k, k - 1} ^ {*} E _ {k - 1} + \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) \Delta \Phi_ {k, k - 1} F _ {k - 1} - K _ {k} ^ {*} \Delta C _ {k} F _ {k} \\ + \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) \Delta \boldsymbol {u} _ {k - 1} + \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) \boldsymbol {W} _ {k - 1} - K _ {k} ^ {*} N _ {k} - K _ {k} ^ {*} \Delta \boldsymbol {d} _ {k} \tag {15.13-18} \\ \end{array}
$$

其中

$$
\Delta \Phi_ {k, k - 1} = \Phi_ {k, k - 1} - \Phi_ {k, k - 1} ^ {*}, \quad \Delta C _ {k} = C _ {k} - C _ {k} ^ {*}, \quad \Delta \boldsymbol {u} _ {k - 1} = \boldsymbol {u} _ {k - 1} - \boldsymbol {u} _ {k - 1} ^ {*}
$$

$$
\Delta \boldsymbol {d} _ {k - 1} = \boldsymbol {d} _ {k - 1} - \boldsymbol {d} _ {k - 1} ^ {*} \tag {15.13-19}
$$

它与式(15.13-11)一起组成递推关系式，初值 $E_{0}=F_{0}-\overline{F_{0}^{*}}$ 。 $E_{k}$ 的数学期望就往往不等于零了，那么均方误差阵是

$$
\begin{array}{l} \overline {{\boldsymbol {E} _ {k} \boldsymbol {E} _ {k} ^ {\tau}}} = (E - K _ {k} ^ {*} C _ {k} ^ {*}) [ \Phi_ {k, k - 1} ^ {*} \overline {{\boldsymbol {E} _ {k - 1} \boldsymbol {E} _ {k - 1} ^ {\tau}}} \Phi_ {k, k - 1} ^ {* \tau} + \Delta \Phi_ {k, k - 1} \overline {{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k - 1} ^ {\tau}}} \Delta \Phi_ {k, k - 1} ^ {\tau} \\ + \Delta \boldsymbol {u} _ {k - 1} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} + \Phi_ {k, k - 1} ^ {*} \overline {{\boldsymbol {E} _ {k - 1} \boldsymbol {F} _ {k - 1} ^ {\tau}}} \Delta \Phi_ {k, k - 1} ^ {\tau} \\ + \Delta \Phi_ {k, k - 1} \overline {{\boldsymbol {F} _ {k - 1} \boldsymbol {E} _ {k} ^ {\tau}}} \Phi_ {k, k - 1} ^ {* \tau} + \Phi_ {k, k - 1} ^ {*} \overline {{\boldsymbol {E}}} _ {k - 1} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Delta \boldsymbol {u} _ {k - 1} \overline {{\boldsymbol {E}}} _ {k - 1} ^ {\tau} \Phi_ {k, k - 1} ^ {* \tau} \\ \left. + \Delta \Phi_ {k, k - 1} \overline {{{F}}} _ {k - 1} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Delta \boldsymbol {u} _ {k - 1} \overline {{{F}}} _ {k - 1} ^ {\tau} \Delta \Phi_ {k, k - 1} ^ {\tau} \right] (E - K _ {k} ^ {*} C _ {k} ^ {*}) ^ {\tau} \\ + K _ {k} ^ {*} \left(\Delta C _ {k} \overline {{{\boldsymbol {F} _ {k} \boldsymbol {F} _ {k} ^ {\tau}}}} \Delta C _ {k} ^ {\tau} + \Sigma_ {N _ {k}} ^ {2} + \Delta \boldsymbol {d} _ {k} \Delta \boldsymbol {d} _ {k} ^ {\tau} + \Delta C _ {k} \overline {{{\boldsymbol {F}}}} _ {k} \Delta \boldsymbol {d} _ {k} ^ {\tau}\right) \\ + \Delta \boldsymbol {d} _ {k} \overline {{{\boldsymbol {F} _ {k} ^ {\tau}}}} \Delta C _ {k} ^ {\tau}) K _ {k} ^ {* \tau} - (E - K _ {k} ^ {*} C _ {k} ^ {*}) \left[ \Phi_ {k, k - 1} ^ {*} \overline {{{\boldsymbol {E} _ {k - 1}}}} \overline {{{\boldsymbol {F} _ {k} ^ {\tau}}}} \Delta C _ {k} ^ {\tau} \right. \\ + \Delta \Phi_ {k, k - 1} \overline {{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k} ^ {\tau}}} \Delta C _ {k} ^ {\tau} + \Delta \boldsymbol {u} _ {k - 1} \overline {{\boldsymbol {F} _ {k} ^ {\tau}}} \Delta C _ {k} ^ {\tau} + \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} \Delta C _ {k} ^ {\tau} + \Delta \Phi_ {k, k - 1} \overline {{\boldsymbol {F}}} _ {k - 1} \Delta \boldsymbol {d} _ {k} ^ {\tau} \\ \left. + \Phi_ {k, k - 1} ^ {*} \overline {{{E}}} _ {k - 1} \Delta d _ {k} ^ {\tau} \right] K _ {k} ^ {* \tau} - K _ {k} ^ {*} \left[ \Delta C _ {k} \overline {{{F _ {k} E}}} _ {k - 1} ^ {\tau} \Phi_ {k, k - 1} ^ {* \tau} + \Delta C _ {k} \overline {{{F _ {k} F}}} _ {k - 1} ^ {\tau} \Delta \Phi_ {k, k - 1} ^ {\tau} \right. \\ \left. + \Delta C _ {k} \overline {{\boldsymbol {F}}} _ {k} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Delta C _ {k} \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} + \Delta \boldsymbol {d} _ {k} \overline {{\boldsymbol {E}}} _ {k - 1} ^ {\tau} \Phi_ {k, k - 1} ^ {* \tau} + \Delta \boldsymbol {d} _ {k} \overline {{\boldsymbol {F}}} _ {k - 1} ^ {\tau} \Delta \Phi_ {k, k - 1} ^ {\tau} \right] \\ \times \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) ^ {\tau} \tag {15.13-20} \\ \end{array}
$$

其中

$$
\overline {{\boldsymbol {F} _ {k} \boldsymbol {F} _ {k} ^ {\tau}}} = \Phi_ {k, k - 1} \overline {{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k - 1} ^ {\tau}}} \Phi_ {k, k - 1} ^ {\tau} + \overline {{\boldsymbol {u} _ {k - 1} \boldsymbol {u} _ {k - 1} ^ {\tau}}} + \Sigma_ {\boldsymbol {W} _ {k - 1}} ^ {2} + \Phi_ {k, k - 1} \overline {{\boldsymbol {F}}} _ {k - 1} \boldsymbol {u} _ {k - 1} ^ {\tau}
$$

$$
+ \boldsymbol {u} _ {k - 1} \overline {{\boldsymbol {F} _ {k - 1} ^ {\tau}}} \Phi_ {k, k - 1} ^ {\tau} \tag {15.13-21}
$$

$$
\overline {{{\boldsymbol {E} _ {k - 1}}}} \overline {{{\boldsymbol {F} _ {k} ^ {\tau}}}} = \overline {{{\boldsymbol {E} _ {k - 1}}}} \overline {{{\boldsymbol {F} _ {k - 1} ^ {\tau}}}} \Phi_ {k, k - 1} ^ {\tau} + \overline {{{\boldsymbol {E} _ {k - 1}}}} \overline {{{\boldsymbol {u} _ {k - 1} ^ {\tau}}}} \tag {15.13-22}
$$

$$
\overline {{\boldsymbol {E} _ {k} \boldsymbol {F} _ {k} ^ {\tau}}} = (E - K _ {k} ^ {*} C _ {k} ^ {*}) [ \Phi_ {k, k - 1} ^ {*} \overline {{\boldsymbol {E} _ {k - 1} \boldsymbol {F} _ {k} ^ {\tau}}} + \Delta \Phi_ {k, k - 1} \overline {{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k} ^ {\tau}}} + \Delta \boldsymbol {u} _ {k - 1} \overline {{\boldsymbol {F} _ {k} ^ {\tau}}} + \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} ]
$$

$$
- K _ {k} ^ {*} \left[ \Delta C _ {k} \overline {{{F _ {k} F _ {k} ^ {\tau}}}} + \Delta d _ {k} \overline {{{F _ {k} ^ {\tau}}}} \right] \tag {15.13-23}
$$

$$
\overline {{{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k} ^ {\tau}}}} = \overline {{{\boldsymbol {F} _ {k - 1} \boldsymbol {F} _ {k - 1} ^ {\tau}}}} \Phi_ {k, k - 1} + \overline {{{\boldsymbol {F} _ {k - 1}}}} \boldsymbol {u} _ {k - 1} \tag {15.13-24}
$$

$$
\overline {{{\boldsymbol {E}}}} _ {k} = \left(E - K _ {k} ^ {*} C _ {k} ^ {*}\right) \left[ \Phi_ {k, k - 1} ^ {*} \overline {{{\boldsymbol {E}}}} _ {k - 1} + \Delta \Phi_ {k, k - 1} \overline {{{\boldsymbol {F}}}} _ {k - 1} + \Delta \boldsymbol {u} _ {k - 1} \right]
$$

$$
- K _ {k} ^ {*} \left[ \Delta C _ {k} \overline {{{\boldsymbol {F}}}} _ {k} + \Delta \boldsymbol {d} _ {k} \right] \tag {15.13-25}
$$

$$
\overline {{{\boldsymbol {F}}}} _ {k} = \Phi_ {k, k - 1} \overline {{{\boldsymbol {F}}}} _ {k - 1} + \boldsymbol {u} _ {k - 1} \tag {15.13-26}
$$

而初值

$$
\overline {{{\boldsymbol {E} _ {0} \boldsymbol {E} _ {0} ^ {\tau}}}} = \overline {{{(\boldsymbol {F} _ {0} - \boldsymbol {F} _ {0} ^ {*}) (\boldsymbol {F} _ {0} - \boldsymbol {F} _ {0} ^ {*}) ^ {\tau}}}} = \overline {{{\Delta \boldsymbol {F} _ {0}}}} \cdot \overline {{{\Delta \boldsymbol {F} _ {0} ^ {\tau}}}} \tag {15.13-27}
$$

$$
\overline {{{{\boldsymbol {F} _ {0}}}}} \overline {{{{\boldsymbol {F} _ {0} ^ {\tau}}}}} = \overline {{{{\boldsymbol {F} _ {0}}}}} \cdot \overline {{{{\boldsymbol {F} _ {0} ^ {\tau}}}}} + \Sigma_ {\boldsymbol {F} _ {0}} ^ {2} \tag {15.13-28}
$$

$$
\overline {{{\boldsymbol {E} _ {0} \boldsymbol {F} _ {0} ^ {\tau}}}} = \Sigma_ {\boldsymbol {F} _ {0}} ^ {2} + \overline {{{\Delta \boldsymbol {F} _ {0}}}} \cdot \overline {{{\boldsymbol {F} _ {0} ^ {\tau}}}} \tag {15.13-29}
$$

$$
\overline {{{\boldsymbol {E} _ {0}}}} = \overline {{{\Delta \boldsymbol {F} _ {0}}}} = \overline {{{\boldsymbol {F} _ {0}}}} - \overline {{{\boldsymbol {F} _ {0} ^ {*}}}} \tag {15.13-30}
$$

现在来讨论几种情况

(1) $\Phi_{k,k-1}, C_{k}, u_{k}, d_{k}$ 都准确无误差，只是 $\Sigma_{W_{k}}^{2}, \Sigma_{N_{k}}^{2}$ 和初值有误差。这时

$$
\boldsymbol {E} _ {k} = \left(E - K _ {k} ^ {*} C _ {k}\right) \Phi_ {k, k - 1} \boldsymbol {E} _ {k - 1} + \left(E - K _ {k} ^ {*} C _ {k}\right) \boldsymbol {W} _ {k - 1} - K _ {k} ^ {*} \boldsymbol {N} _ {k} \tag {15.13-31}
$$

$$
\overline {{{\boldsymbol {E} _ {k} \boldsymbol {E} _ {k} ^ {\tau}}}} = (E - K _ {k} ^ {*} C _ {k}) [ \Phi_ {k, k - 1} \overline {{{\boldsymbol {E} _ {k - 1} \boldsymbol {E} _ {k - 1} ^ {\tau}}}} \Phi_ {k, k - 1} ^ {\tau} + \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} ] (E - K _ {k} ^ {*} C _ {k}) ^ {\tau} + K _ {k} ^ {*} \Sigma_ {N _ {k}} ^ {2} K _ {k} ^ {*} \tag {15.13-32}
$$

把式（15.13-32）与（15.13-17）相比较，可得出结论：只要计算时模型式(15.13-13)和(15.13-14)的 $\Sigma_{\mathbf{w}_{k - 1}}^2,\Sigma_{N_k^*}^2$ 和初值 $\Sigma_{F_0}^2$ 分别大于或等于真实的 $\Sigma_{\mathbf{w}_{k - 1}}^2$ $\Sigma_{N_k}^2$ 和初值 $\overline{\mathbf{E}_0\mathbf{E}_0^\tau}$ ，那么对所有时刻 $t_k$ ，按模型式(15.13-13)和(15.13-14)计算出来的 $\Sigma_{\mathbf{E}_k^*}^2 = \overline{\mathbf{E}_k^*\mathbf{E}_k^{*\tau}}$ 永远大于或等于真实的均方误差阵 $\overline{\mathbf{E}_k\mathbf{E}_k^\tau}$ 。另外，如果模型式(15.13-13)和(15.13-14)是一致完全能控和一致完全能观测的，那么真实的均方误差阵是有界的，不发生发散现象。

（2） $\Phi_{k,k-1}$ 和 $C_{k}$ 都准确而 $u_{k-1}$ 和 $d_{k}$ 不准确，这是由于某些模型中含有不准确的参数或非线性系统线性化后引起的。这时

$$
\boldsymbol {E} _ {k} = \left(E - K _ {k} ^ {*} C _ {k}\right) \left[ \Phi_ {k, k - 1} \boldsymbol {E} _ {k - 1} + \Delta \boldsymbol {u} _ {k - 1} + \boldsymbol {W} _ {k - 1} \right] - K _ {k} ^ {*} \left(\boldsymbol {N} _ {k} + \Delta \boldsymbol {d} _ {k}\right) \tag {15.13-33}
$$

$$
\begin{array}{l} \overline {{{\boldsymbol {E} _ {k} \boldsymbol {E} _ {k} ^ {\tau}}}} = (E - K _ {k} ^ {*} C _ {k}) [ \Phi_ {k, k - 1} \overline {{{\boldsymbol {E} _ {k - 1} \boldsymbol {E} _ {k - 1} ^ {\tau}}}} \Phi_ {k, k - 1} ^ {\tau} + \Delta \boldsymbol {u} _ {k - 1} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Sigma_ {\boldsymbol {w} _ {k - 1}} ^ {2} \\ \left. + \Phi_ {k, k - 1} \overline {{{E _ {k - 1}}}} \Delta \boldsymbol {u} _ {k - 1} ^ {\tau} + \Delta \boldsymbol {u} _ {k - 1} \overline {{{E _ {k - 1} ^ {\tau}}}} \Phi_ {k, k - 1} ^ {\tau} \right] (E - K _ {k} ^ {*} C _ {k}) ^ {\tau} \\ + K _ {k} ^ {*} \left(\Sigma_ {N _ {k}} ^ {2} + \Delta \boldsymbol {d} _ {k - 1} \Delta \boldsymbol {d} _ {k - 1} ^ {\tau}\right) K _ {k} ^ {* \tau} - (E - K _ {k} ^ {*} C _ {k}) \left[ \Phi_ {k, k - 1} \overline {{{\boldsymbol {E}}}} _ {k - 1} \Delta \boldsymbol {d} _ {k} ^ {\tau} \right. \\ \left. + \Delta \boldsymbol {u} _ {k - 1} \Delta \boldsymbol {d} _ {k - 1} ^ {\tau} \right] K _ {k} ^ {* \tau} - K _ {k} ^ {*} \left[ \Delta \boldsymbol {d} _ {k} \overline {{\boldsymbol {E} _ {k - 1} ^ {\tau}}} \Phi_ {k, k - 1} ^ {\tau} + \Delta \boldsymbol {d} _ {k} \Delta \boldsymbol {u} _ {k - 1} \right] \\ \times \left(E - K _ {k} ^ {*} C _ {k}\right) ^ {\tau} \tag {15.13-34} \\ \end{array}
$$

$$
\overline {{{\boldsymbol {E} _ {k}}}} = \left(E - K _ {k} ^ {*} C _ {k}\right) \Phi_ {k, k - 1} \overline {{{\boldsymbol {E} _ {k - 1}}}} + \left(E - K _ {k} ^ {*} C _ {k}\right) \Delta \boldsymbol {u} _ {k - 1} - \boldsymbol {K} _ {k} ^ {*} \Delta \boldsymbol {d} _ {k} \tag {15.13-35}
$$

同样可以证明：如果信号和观测模型式(15.13-13)和(15.13-14)是一致完全能控和一致完全能观测的，且对所有的 $k,\Delta u_{k}$ 有一致的上界，真实的

$$
\Sigma_ {W _ {k}} ^ {2} \leqslant c _ {1} \Sigma_ {W _ {k} ^ {*}} ^ {2}, \quad \Sigma_ {N _ {k}} ^ {2} \leqslant c _ {2} \Sigma_ {N _ {k} ^ {*}} ^ {2}
$$

$c_{1}, c_{2}$ 是大于零的常数， $\Sigma_{N_{k}}^{2}$ 是正定的，那么真实的均方误差阵 $\overline{E_{k}E_{k}^{\tau}}$ 一定有一致的上界，也就是不出现“发散”现象。

这样，在设计最优线性递推过滤器时，对模型式(15.13-13)，(15.13-14)选取合适的 $\Sigma_{\pmb{w}_k^*}$ ， $\Sigma_{\pmb{x}_k^*}^2$ 有可能使模型具有一致完全能控和一致完全能观测的性能从而防止模型和统计特性不准确而引起的“发散”现象。

现在举一个简单的例子。假设真实的信号和观测模型是

$$
F _ {k} = F _ {k - 1} + u, \quad X _ {k} = F _ {k} + N _ {k}
$$

而在设计最优过滤器时，由于对参数 u 了解不准确，我们的模型取作

$$
F _ {k} ^ {*} = F _ {k - 1} ^ {*} + u ^ {*}, \quad X _ {k} = F _ {k} ^ {*} + N _ {k}
$$

其中 $N_{k}$ 是数学期望为零的平稳白色噪声 $\sigma_{N_{k}}^{2} = \sigma_{N}^{2}$ 。对于初值我们只知道数学期望为零，散布很大，于是我们取 $\mathbf{Y}_{0}^{*} = \overline{\mathbf{F}_{0}} = 0, \sigma_{\dot{E}_{0}^{*}}^{2} \rightarrow \infty$ 。根据最优过滤公式可以算出

$$
\sigma_ {\tilde {F} _ {k}} ^ {2} = \sigma_ {\tilde {E} _ {k - 1}} ^ {2}, \quad k _ {k} ^ {*} = \sigma_ {\tilde {F} _ {k} ^ {*}} ^ {2} / (\sigma_ {\tilde {F} _ {k} ^ {*}} ^ {2} + \sigma_ {N _ {k}} ^ {2})
$$

$$
\sigma_ {E _ {k} ^ {*}} ^ {2} = (1 - k _ {k} ^ {*}) \sigma_ {F _ {k}} ^ {2} (1 - k _ {k} ^ {*}) + k _ {k} ^ {*} \sigma_ {N} ^ {2} k _ {k} ^ {*} = \sigma_ {F _ {k} ^ {*}} ^ {2} \sigma_ {N} ^ {2} / (\sigma_ {F _ {k} ^ {*}} ^ {2} + \sigma_ {N} ^ {2})
$$

再根据初值 $\sigma_{E_0^*}^2\to \infty$ ，可得到 $k_{1}^{*} = 1,\sigma_{E_{1}}^{2} = \sigma_{N}^{2}$ ，依次递推就得到

$$
k _ {k} ^ {*} = \frac {1}{k}, \quad \sigma_ {E _ {k} ^ {*}} ^ {2} = \frac {1}{k} \sigma_ {N} ^ {2}
$$

最优输出为

$$
\begin{array}{l} \stackrel {\circ} {Y} _ {k} ^ {*} = \stackrel {\circ} {Y} _ {k - 1} ^ {*} + u ^ {*} + k _ {k} ^ {*} \left(X _ {k} - \stackrel {\circ} {Y} _ {k - 1} - u ^ {*}\right) \\ = \left(1 - \frac {1}{k}\right) \left(\stackrel {\circ} {Y} _ {k - 1} + u ^ {*}\right) + \frac {1}{k} X _ {k} \\ = \frac {k - 1}{2} u ^ {*} + \frac {1}{k} \sum_ {i = 1} ^ {k} X _ {k} \\ \overline {{{E _ {k} ^ {*}}}} = 0 \\ \end{array}
$$

在理论上计算出来的过滤器的输出均方误差 $\overline{(\mathring{E}_{k}^{*})^{2}}=\sigma_{\mathring{E}_{k}^{*}}^{2}=\frac{1}{k}\sigma_{N}^{2}$ 随 k 的增长趋于零。但是当我们把真实的观测值 $X_{k}=F_{k}+N_{k}$ 加到滤波器后，得到的输出则是

$$
Y _ {k} = \frac {k - 1}{2} u ^ {*} + \frac {1}{k} \sum_ {l = 1} ^ {k} \left(F _ {l} + N _ {l}\right) = F _ {0} + \frac {k - 1}{2} u ^ {*} + \frac {k + 1}{2} u + \frac {1}{k} \sum_ {l = 1} ^ {k} N _ {l}
$$

输出误差是

$$
E _ {k} = F _ {k} - Y _ {k} = \frac {k - 1}{2} \Delta u - \frac {1}{k} \sum_ {l = 1} ^ {k} N _ {l}
$$

其中 $\Delta u = u - u^{*}$ ，它的数学期望 $\overline{E}_{k} = \frac{k-1}{2}\Delta u$ ，不等于零，而且随着 k 的增长而增长。输出的均方误差是

$$
\overline {{{E _ {k} ^ {2}}}} = \frac {(k - 1) ^ {2}}{4} \Delta u ^ {2} + \frac {1}{k} \sigma_ {N} ^ {2}
$$

它随 k 的增长而更迅速地增长，这就出现了“发散”现象。

在这个例子中，因为过滤器的增益系数 $K_{k}$ 随 k 的增长迅速减小，于是，新的观测信息在过滤器中的作用迅速变弱，到后来，主要依靠信号的模型来决定输出，模型不准起了突出作用，引起“发散”。在此例中 $W_{k}$ 的方差阵 $\Sigma w_{k}^{2}$ 是零矩阵，如果选用正定阵 $\Sigma w_{k}^{2}$ ，那么可以改善“发散”的趋势，因模型不准确的影响会减弱些，但 不能改变“发散”的本质。因为此例中 $\Phi=1$ ，因此加了 $\Sigma w_{k}^{2}>0$ 的条件后仍不能得到一致完全能控和一致完全能观测的性能。当 $\Delta u=0$ 时，输出的均方误差尚可趋于稳定，但它不是那种以指数形式趋于稳定，而是以 1/k 的形式趋于稳定，已经处于稳定的边缘。当有 $\Delta u$ 常值误差后，输出误差的数学期望就不断地增大，所以均方误差就必然发散了。这个例子可以用加大新息的作用，或采用有限记忆的方法来克服“发散”现象。也可以把参数 u 看作系统信号中的待定参数，在进行最优过滤的同时对参数进行估计。现在来看一个更为一般的例子。假设信号和观测模型是

$$
\boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {F} _ {k} + \Psi_ {k} \boldsymbol {u} _ {k} + \Omega_ {k} \boldsymbol {a} _ {k} + G _ {k} \boldsymbol {W} _ {k} \tag {15.13-36}
$$

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {b} _ {k} + \boldsymbol {N} _ {k} \tag {15.13-37}
$$

其中， $a_{k}, b_{k}$ 为未知常参数，所以

$$
\boldsymbol {a} _ {k} = \boldsymbol {a} _ {k - 1} \tag {15.13-38}
$$

$$
\boldsymbol {b} _ {k} = \boldsymbol {b} _ {k - 1} \tag {15.13-39}
$$

把 $a_{k}, b_{k}$ 看做是新的信号的一部分, 构成新的信号和观测模型

$$
\left( \begin{array}{l} \boldsymbol {F} _ {k + 1} \\ \boldsymbol {a} _ {k + 1} \\ \boldsymbol {b} _ {k + 1} \end{array} \right) = \left( \begin{array}{c c c} \Phi_ {k + 1, k} & \Omega_ {k} & 0 \\ 0 & E & 0 \\ 0 & 0 & E \end{array} \right) \left( \begin{array}{l} \boldsymbol {a} _ {k} \\ \boldsymbol {b} _ {k} \end{array} \right) + \left( \begin{array}{l} \Psi_ {k} \\ 0 \\ 0 \end{array} \right) \boldsymbol {u} _ {k} + \left( \begin{array}{l} G _ {k} \\ 0 \\ 0 \end{array} \right) W _ {k} \tag {15.13-40}
$$

$$
\boldsymbol {X} _ {k} = \left(\boldsymbol {C} _ {k}, 0, E\right) \cdot \left( \begin{array}{l} \boldsymbol {F} _ {k} \\ \boldsymbol {a} _ {k} \\ \boldsymbol {b} _ {k} \end{array} \right) + \boldsymbol {N} _ {k} \tag {15.13-41}
$$

对新模型进行最优过滤时，就包含了对未知常参数的估计。在对新模型进行最优过滤就需要知道新信号初值 $(F_{0},a_{0},b_{0})$ 的数学期望和方差阵，但 $a_{0},b_{0}$ 的统计特性又是不知道的。只要最优过滤器是稳定的，那么 $a_{0},b_{0}$ 统计特性不准确对最优过滤器的输出影响是不大的，这种影响随着 k 的增大而趋于消失。利用扩大维数的方法还可以解决输入信号中含有非随机的且参数待定的函数问题。

对于 $W_{k}, N_{k}$ 的统计特性不准确的问题, 也可以采用自适应过滤的方法, 即在用输入 $X_{k}$ 进行过滤的同时, 设法对 $W_{k}, N_{k}$ 的统计特性进行估计或修正。这方面的情况读者可以参看文献 $^{[5]}$ 。

#### 15.14 线性二次高斯问题 $^{[21]}$

以前考虑最优控制问题时，系统中没有考虑随机作用的影响。这时系统的状态可以准确测量，使系统的某种性能指标达到极值的最优控制是系统状态的某种函数。本章前几节中考虑的最优过滤问题，虽然信号模型中也可能有非随机的控制输入，但它是已知的时间函数，与过滤器的输出毫无关系。实际上，经常碰到的 是这样的最优控制问题，系统中有不可忽略的随机作用的影响，这叫做最优随机控制问题。这时系统的状态是随机过程或随机序列，它不能直接测量到，只能根据与状态有关的输出来估计它。控制是根据系统的初值和系统在控制时刻的输出来决定，它应该是非随机的。性能指标应是某种统计特性。最优控制就是要寻找某种控制规律，使某项性能指标达到极值。

在各种最优随机控制问题中，线性二次高斯问题是最简单的一类，发展得较完善，且有广泛的应用。我们先较详细地讨论一下离散的（采样的）线性二次高斯问题，以后再简单地叙述连续的线性二次高斯问题，最后讨论它的应用。

在离散的线性二次高斯问题中，假设系统模型是

$$
\boldsymbol {F} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {F} _ {k} + \Psi_ {k} \boldsymbol {u} _ {k} + G _ {k} \boldsymbol {W} _ {k}, \quad k = 0, 1, 2, \dots , N \tag {15.14-1}
$$

$$
\boldsymbol {X} _ {k} = \boldsymbol {C} _ {k} \boldsymbol {F} _ {k} + \boldsymbol {N} _ {k}, \quad k = 0, 1, \dots , N \tag {15.14-2}
$$

其中系统的状态 $F_{k}$ 是 n 维随机向量序列；观测值 $X_{k}$ 是 m 维随机向量序列； $u_{k}$ 是 r 维控制序列，它是确定性的； $W_{k}, N_{k}$ 是互不相关的数学期望为零的 p 维，m 维白高斯随机序列，方差阵是 $\Sigma_{W_{k}}^{2}, \Sigma_{N_{k}}^{2}$ ；状态初值 $F_{0}$ 是高斯随机向量，其数学期望为 $\overline{F}_{0}$ ，方差阵是 $\Sigma_{F_{0}}^{2}; \Phi, \Psi, G, C$ 为相应阶数的矩阵。现在要寻找这样的最优控制序列 $u_{k}$ ，它是系统状态初值 $F_{0}$ 以及 $t_{k}$ 和以前时刻观测值 $\mathcal{X}_{k}^{\tau} = (X_{1}^{\tau}, X_{2}^{\tau}, \cdots, X_{k}^{\tau})$ 的某种确定函数，使得性能指标

$$
J = \overline {{{\frac {1}{2} \boldsymbol {F} _ {N} ^ {\tau} S \boldsymbol {F} _ {N} + \frac {1}{2} \sum_ {k = 0} ^ {N - 1} \left(\boldsymbol {F} _ {k} ^ {\tau} Q _ {k} \boldsymbol {F} _ {k} + \boldsymbol {u} _ {k} ^ {\tau} R _ {k} \boldsymbol {u} _ {k}\right)}}}
$$

达到极小，其中 S 和 $Q_{k}$ 是非负的对称矩阵, $R_{k}$ 是正定的对称矩阵。在这里, 应注意到:(1) 控制的时间是固定的, 从 $t_{0}$ 到 $t_{N}$ ; (2) 控制 $u_{k}$ 不受限制。为了要 J 达到最小, $u_{k}$ 必然不能很大, 所以不必加上限制;(3) 对系统状态的终值 $F_{k}$ 不加限制。同样因为要 J 达到最小, 终值不可能很大。

我们采用动态规划的方法解决此问题。先讨论无随机作用的线性二次最优控制问题，它是一个最优离散系统问题。这时 $W_{k}=N_{k}=0$ ，状态可直接测量，不必考虑式(15.14-2)，系统模型是

$$
\boldsymbol {f} _ {k + 1} = \Phi_ {k + 1, k} \boldsymbol {f} _ {k} + \Psi_ {k} \boldsymbol {u} _ {k} \tag {15.14-3}
$$

性能指标是

$$
J = \frac {1}{2} \boldsymbol {f} _ {N} ^ {\tau} S \boldsymbol {f} _ {N} + \frac {1}{2} \sum_ {k = 0} ^ {N - 1} (\boldsymbol {f} _ {k} ^ {\tau} Q _ {k} \boldsymbol {f} _ {k} + \boldsymbol {u} _ {k} ^ {\tau} R _ {k} \boldsymbol {u} _ {k}) \tag {15.14-4}
$$

要求 J 达到极小。

我们定义一个泛函序列 $v_{l}, l=0,1,\cdots,N-1$

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \min _ {\boldsymbol {u} _ {l + 1}} \dots \min _ {\boldsymbol {u} _ {N - 1}} \left[ \frac {1}{2} \boldsymbol {f} _ {N} ^ {\tau} S \boldsymbol {f} _ {N} + \frac {1}{2} \sum_ {k = l} ^ {N - 1} \left(\boldsymbol {f} _ {k} ^ {\tau} Q _ {k} \boldsymbol {f} _ {k} + \boldsymbol {u} _ {k} ^ {\tau} R _ {k} \boldsymbol {u} _ {k}\right) \right] \tag {15.14-5}
$$

当 l=N-1 时，

$$
v _ {N - 1} = \min _ {\boldsymbol {u} _ {N - 1}} \left[ \frac {1}{2} \boldsymbol {f} _ {N} ^ {\tau} S \boldsymbol {f} _ {N} + \frac {1}{2} \boldsymbol {f} _ {N - 1} ^ {\tau} Q _ {N - 1} \boldsymbol {f} _ {N - 1} + \frac {1}{2} \boldsymbol {u} _ {N - 1} ^ {\tau} R _ {N - 1} \boldsymbol {u} _ {N - 1} \right]
$$

把式(15.14-3)代入 $v_{N - 1}$ 后得到

$$
\begin{array}{l} v _ {N - 1} = \min _ {u _ {N - 1}} \frac {1}{2} \left[ f _ {N - 1} ^ {\tau} \left(\Phi_ {N, N - 1} ^ {\tau} S \Phi_ {N, N - 1} + Q _ {N - 1}\right) f _ {N - 1} \right. \\ + \boldsymbol {u} _ {N - 1} ^ {\tau} \left(\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}\right) \boldsymbol {u} _ {N - 1} \\ \left. + \boldsymbol {f} _ {N - 1} ^ {\tau} \Phi_ {N, N - 1} ^ {\tau} S \Psi_ {N - 1} \boldsymbol {u} _ {N - 1} + \boldsymbol {u} _ {N - 1} ^ {\tau} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \boldsymbol {f} _ {N - 1} \right] \\ \end{array}
$$

它是 $u_{k}$ 的二次三项式，由 S 的非负对称性和 $R_{N-1}$ 的正定对称性可知 $(\Psi_{N-1}^{x} S \Psi_{N-1} + R_{N-1})$ 是正定对称的，因此可以得到使上式达到极小的 $\mathring{u}_{N-1}$ 应是状态 $f_{N-1}$ 的线性函数：

$$
\mathbf {\dot {u}} _ {N - 1} = - \Lambda_ {N - 1} \boldsymbol {f} _ {N - 1} \tag {15.14-6}
$$

$$
\Lambda_ {N - 1} = (\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}) ^ {- 1} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \tag {15.14-7}
$$

把它代入 $v_{N-1}$ 后得到

$$
\boldsymbol {v} _ {N - 1} = \frac {1}{2} \boldsymbol {f} _ {N - 1} ^ {\mathrm{T}} P _ {N - 1} \boldsymbol {f} _ {N - 1} \tag {15.14-8}
$$

其中

$$
P _ {N - 1} = Q _ {N - 1} + \Phi_ {N, N - 1} ^ {\tau} [ S - S \Psi_ {N - 1} (\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}) ^ {- 1} \Psi_ {N - 1} ^ {\tau} S ] \Phi_ {N, N - 1} \tag {15.14-9}
$$

由 $Q_{N-1}$ 和 S 的非负对称性可知 $P_{N-1}$ 也是非负对称阵，现在来看 $v_{l}$ 与 $v_{l+1}$ 的关系，

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \min _ {\boldsymbol {u} _ {l + 1}} \dots \min _ {\boldsymbol {u} _ {N - 1}} \frac {1}{2} \left[ \boldsymbol {f} _ {N} ^ {T} S \boldsymbol {f} _ {N} + \sum_ {k = l + 1} ^ {N - 1} \left(\boldsymbol {f} _ {k} ^ {\tau} Q _ {k} \boldsymbol {f} _ {k} + \boldsymbol {u} _ {k} ^ {\tau} R _ {k} \boldsymbol {u} _ {k}\right) + \boldsymbol {f} _ {l} ^ {T} Q _ {l} \boldsymbol {f} _ {l} + \boldsymbol {u} _ {l} R _ {l} \boldsymbol {u} _ {l} \right]
$$

由系统模型式(15.14-3)知 $u_{l+1}, \cdots, u_{N}$ 对 $f_{l}$ 无影响, 因此

$$
\begin{array}{l} v _ {l} = \min _ {\boldsymbol {u} _ {l}} \left\{\min _ {\boldsymbol {u} _ {l + 1}} \dots \min _ {\boldsymbol {u} _ {N - 1}} \frac {1}{2} \left[ \boldsymbol {f} _ {N} ^ {\tau} S \boldsymbol {f} _ {N} + \sum_ {k = l + 1} ^ {N - 1} \left(\boldsymbol {f} _ {k} ^ {\tau} Q _ {k} \boldsymbol {f} _ {k} + \frac {1}{2} \boldsymbol {u} _ {k} ^ {\tau} R _ {k} \boldsymbol {u} _ {k}\right) \right] \right. \\ \left. + \frac {1}{2} \left(\boldsymbol {f} _ {l} ^ {\tau} Q _ {l} \boldsymbol {f} _ {l} + \boldsymbol {u} _ {l} ^ {\tau} R _ {l} \boldsymbol {u} _ {l}\right) \right\} \\ = \min _ {\boldsymbol {u} _ {l}} \left\{v _ {l + 1} + \frac {1}{2} \boldsymbol {f} _ {l} ^ {\tau} Q _ {l} \boldsymbol {f} _ {l} + \frac {1}{2} \boldsymbol {u} _ {l} ^ {\tau} R _ {l} \boldsymbol {u} _ {l} \right\} \\ \end{array}
$$

根据式(15.14-8)，可以设 $v_{l+1}=\frac{1}{2}f_{l+1}^{\tau}P_{l+1}f_{l+1}$ ，那么

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \frac {1}{2} \left[ \boldsymbol {f} _ {l + 1} ^ {\tau} P _ {l + 1} \boldsymbol {f} _ {l + 1} + \boldsymbol {f} _ {l} ^ {\tau} Q _ {l} \boldsymbol {f} _ {l} + \boldsymbol {u} _ {l} ^ {\tau} R _ {l} \boldsymbol {u} _ {l} \right]
$$

与 $t_{N-1}$ 时刻相类似, 可以得到

$$
\mathbf {\dot {u}} _ {l} = - \Lambda_ {l} \boldsymbol {f} _ {l} \tag {15.14-10}
$$

$$
\Lambda_ {l} = \left(\Psi_ {l} ^ {\tau} P _ {l + 1} \Psi_ {l} + R _ {l}\right) ^ {- 1} \Psi_ {l} ^ {\tau} P _ {l + 1} \Phi_ {l + 1, l} \tag {15.14-11}
$$

$$
v _ {l} = \frac {1}{2} \boldsymbol {f} _ {l} ^ {\tau} P _ {l} \boldsymbol {f} _ {l} \tag {15.14-12}
$$

$$
P _ {l} = Q _ {l} + \Phi_ {l + 1, l} ^ {\tau} \left[ P _ {l + 1} - P _ {l + 1} \Psi_ {l} \left(\Psi_ {l} ^ {\tau} P _ {l + 1} \Psi_ {l} + R _ {l}\right) ^ {- 1} \Psi_ {l} ^ {\tau} P _ {l + 1} \right] \Phi_ {l + 1, l} \tag {15.14-13}
$$

只要令 $P_{N}=S$ ，就可递推求出 $\Lambda_{l}$ 和 $P_{l}, l=N-1, N-2, \cdots, 0$ 。非随机的线性二次问题的最优控制规律就是 $\dot{u}=-\Lambda_{l}f_{l}, l=0,1,\cdots,N-1$ 。在这个最优控制规律作用下，所达到的最小性能指标就是

$$
\min J = v _ {0} = \frac {1}{2} f _ {0} ^ {\xi} P _ {0} f _ {0} \tag {15.14-14}
$$

现在来讨论考虑了随机作用的线性二次高斯问题。先定义一个泛函序列

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \min _ {\boldsymbol {u} _ {l - 1}} \dots \min _ {\boldsymbol {u} _ {N - 1}} \frac {1}{2} \overline {{\left[ \boldsymbol {F} _ {N} ^ {\xi} S \boldsymbol {F} _ {N} + \sum_ {k = l} ^ {N - 1} (\boldsymbol {F} _ {k} ^ {\xi} Q _ {k} \boldsymbol {F} _ {k} + \boldsymbol {u} _ {k} ^ {\xi} R _ {k} \boldsymbol {u} _ {k}) \right]}} \tag {15.14-15}
$$

当 l=N-1 时，

$$
v _ {N - 1} = \min _ {\boldsymbol {u} _ {N - 1}} \frac {1}{2} \overline {{\left[ \boldsymbol {F} _ {N} ^ {\tau} S \boldsymbol {F} _ {N} + \boldsymbol {F} _ {l - 1} ^ {\tau} Q _ {l - 1} \boldsymbol {F} _ {l - 1} + \boldsymbol {u} _ {l - 1} ^ {\tau} R _ {l - 1} \boldsymbol {u} _ {l - 1} \right]}}
$$

把式 $(15.14-1)$ 代入后得到

$$
\begin{array}{l} v _ {N - 1} = \min _ {u _ {N - 1}} \frac {1}{2} \left[ \overline {{{F _ {N - 1} ^ {\tau} \left(\Phi_ {N , N - 1} ^ {\tau} S \Phi_ {N , N - 1} + Q _ {N - 1}\right) F _ {N - 1}}}} \right. \\ + \boldsymbol {u} _ {N - 1} ^ {\tau} \left(\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}\right) \boldsymbol {u} _ {N - 1} + \overline {{{\boldsymbol {W} _ {N - 1} ^ {\tau} G _ {N - 1} ^ {\tau} G _ {N - 1} \boldsymbol {W} _ {N - 1}}}} \\ + \overline {{\boldsymbol {u} _ {N - 1} ^ {\tau} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N , N - 1} \boldsymbol {F} _ {N - 1}}} + \overline {{\boldsymbol {F} _ {N - 1} ^ {\tau} \Phi_ {N , N - 1} ^ {\tau} S \Psi_ {N - 1} \boldsymbol {u} _ {N - 1}}} \\ + \overline {{{\boldsymbol {F} _ {N - 1} ^ {\tau} \Phi_ {N , N - 1} ^ {\tau} S G _ {N - 1} \boldsymbol {W} _ {N - 1}}}} + \overline {{{\boldsymbol {W} _ {N - 1} ^ {\tau} \boldsymbol {G} _ {N - 1} ^ {\tau} S \Phi_ {N , N - 1} \boldsymbol {F} _ {N - 1}}}} \\ \left. + \overline {{\boldsymbol {u} _ {N - 1} ^ {\tau} \Psi_ {N - 1} ^ {\tau} S G _ {N - 1} \boldsymbol {W} _ {N - 1}}} + \overline {{\boldsymbol {W} _ {N - 1} ^ {\tau} G _ {N - 1} ^ {\tau} S \Psi_ {N - 1} \boldsymbol {u} _ {N - 1}}} \right] \\ \end{array}
$$

由于 $W_{N-1}$ 的数学期望是零向量, $W_{N-1}$ 与 $F_{N-1}$ 互不相关, 于是

$$
\begin{array}{l} v _ {N - 1} = \min _ {u _ {N - 1}} \frac {1}{2} \left[ \overline {{{\boldsymbol {F} _ {N - 1} ^ {\tau} \left(\Phi_ {N , N - 1} ^ {\tau} S \Phi_ {N , N - 1} + Q _ {N - 1}\right) \boldsymbol {F} _ {N - 1}}}} \right. \\ + \boldsymbol {u} _ {N - 1} ^ {\tau} \left(\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}\right) ^ {- 1} \boldsymbol {u} _ {N - 1} \\ \left. + \boldsymbol {W} _ {N - 1} ^ {\tau} \boldsymbol {G} _ {N - 1} ^ {\tau} \boldsymbol {G} _ {N - 1} \boldsymbol {W} _ {N - 1} + \boldsymbol {u} _ {N - 1} ^ {\tau} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \overline {{\boldsymbol {F} _ {N - 1}}} + \overline {{\boldsymbol {F} _ {N - 1} ^ {\tau}}} \Phi_ {N, N - 1} ^ {\tau} S \Psi_ {N - 1} \boldsymbol {u} _ {N - 1} \right] \\ \end{array}
$$

因为 $u_{N-1}$ 的选择不会影响 $F_{N-1}$ ，而且 $u_{N-1}$ 是初值 $F_{0}$ 以及 $t_{k}$ 和以前时刻的观测值

$$
\mathcal {X} _ {N - 1} ^ {\tau} = \left(X _ {0} ^ {\tau}, X _ {1} ^ {\tau}, \dots , X _ {N - 1} ^ {\tau}\right)
$$

的函数，所以要得到上述的极小值就相当于函数

$$
\begin{array}{l} \left[ \boldsymbol {u} _ {N - 1} ^ {\tau} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \left(\overline {{\boldsymbol {F} _ {N - 1}}} \mid \mathcal {X} _ {N - 1}\right) + \left(\overline {{\boldsymbol {F} _ {N - 1}}} \mid \mathcal {X} _ {N - 1}\right) \Phi_ {N, N - 1} ^ {\tau} S \Psi_ {N - 1} \boldsymbol {u} _ {N - 1} \right. \\ \left. + \boldsymbol {u} _ {N - 1} ^ {\tau} \left(\Psi_ {N - 1} S \Psi_ {N - 1} + R _ {N - 1}\right) \boldsymbol {u} _ {N - 1} \right] \\ \end{array}
$$

达到极小值，那么最优控制 $\dot{u}_{N-1}$ 应是

$$
\boldsymbol {u} _ {N - 1} = - \left(\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N - 1}\right) ^ {- 1} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \left(\overline {{\boldsymbol {F} _ {N - 1} \mid \mathcal {X} _ {N - 1}}}\right)
$$

$$
= - \Lambda_ {N - 1} \left(\overline {{\boldsymbol {F} _ {N - 1} \mid \mathfrak {X} _ {N - 1}}}\right)
$$

在第十四章和第 15.3 节中已经指出，在高斯分布的随机作用 $W_{k}, N_{k}, F_{0}$ 影响下，由系统线性模型式(15.14-1)和(15.14-2)得到的 $F_{k}, X_{k}$ 是联合高斯分布的。条件数学期望 $(\overline{F_{N-1}|\mathcal{X}_{N-1}})$ 就是使输出均方误差最小的最优过滤器的最优输出 $\mathring{Y}_{N-1}$ ，它是系统式(15.14-1)和(15.14-2)的输出 $\mathcal{X}_{N-1}$ （也是过滤器的输入）的线性函数，所以

$$
\mathring {\boldsymbol {u}} _ {N - 1} = - \Lambda_ {N - 1} \mathring {\boldsymbol {Y}} _ {N - 1} \tag {15.14-16}
$$

把式(15.14-16)代入 $v_{N - 1}$ ，考虑到最优过滤输出 $\mathbf{Y}_{N - 1} = \mathbf{F}_{N - 1} - \mathbf{E}_{N - 1}$ ，于是得到

$$
\boldsymbol {v} _ {N - 1} = \frac {1}{2} \overline {{\left[ \boldsymbol {F} _ {N - 1} ^ {\tau} \boldsymbol {P} _ {N - 1} \boldsymbol {F} _ {N - 1} \right]}} + \alpha_ {N - 1} \tag {15.14-17}
$$

其中 $P_{N - 1}$ 满足式(15.14-9)，而 $\alpha_{N - 1}$ 是

$$
\alpha_ {N - 1} = \frac {1}{2} \overline {{\left[ \stackrel {\circ} {\boldsymbol {E}} _ {N - 1} \Phi_ {N , N - 1} ^ {*} S \Psi_ {N - 1} \left(\Psi_ {N - 1} ^ {*} S \Psi_ {N - 1} + R _ {N - 1}\right) ^ {- 1} \Psi_ {N - 1} ^ {*} S \Phi_ {N , N - 1} \stackrel {\circ} {\boldsymbol {E}} _ {N - 1} \right.}}
$$

$$
\left. + \overline {{{\boldsymbol {W} _ {N - 1} ^ {\tau} \boldsymbol {G} _ {N - 1} ^ {\tau} \boldsymbol {G} _ {N - 1} ^ {\tau} \boldsymbol {W} _ {N - 1}}}} \right] \tag {15.14-18}
$$

当 P 是对称矩阵时, 下列等式成立

$$
\overline {{[ \boldsymbol {X} ^ {\tau} P \boldsymbol {X} ]}} = \overline {{\boldsymbol {X}}} ^ {\tau} P \overline {{\boldsymbol {X}}} + \operatorname{tr} [ P \Sigma_ {x} ^ {2} ] \tag {15.14-19}
$$

因 $E_{N-1}$ 和 $W_{N-1}$ 的数学期望都是零向量, 所以

$$
\begin{array}{l} \alpha_ {N - 1} = \frac {1}{2} \operatorname{tr} \left[ \Phi_ {N, N - 1} ^ {\tau} S \Psi_ {N - 1} \left(\Psi_ {N - 1} ^ {\tau} S \Psi_ {N - 1} + R _ {N}\right) ^ {- 1} \Psi_ {N - 1} ^ {\tau} S \Phi_ {N, N - 1} \Sigma_ {\tilde {E} _ {N - 1}} ^ {2} \right] \\ + \frac {1}{2} \operatorname{tr} \left[ G _ {N - 1} ^ {\tau} G _ {N - 1} \Sigma_ {W _ {N - 1}} ^ {2} \right] \\ \end{array}
$$

方差阵 $\Sigma_{E_{N-1}}^{2}$ 在最优过滤器的设计计算中可递推得出，它与控制向量 $u_{N-1}$ 无关，因此 $\alpha_{N-1}$ 与 $u_{N-1}$ 无关。现在再来求 $v_{l}$ 与 $v_{l+1}$ 的关系。由于 $u_{l+1}, u_{l+2}, \cdots, u_{N-1}$ 对 $F_{l}$ 无影响，所以可得到

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \left\{v _ {l + 1} + \overline {{{{\frac {1}{2} \boldsymbol {F} _ {l} ^ {\tau} Q _ {l} \boldsymbol {F} _ {l} + \frac {1}{2} \boldsymbol {u} _ {l} ^ {\tau} R _ {l} \boldsymbol {u} _ {l}}}}} \right\}
$$

根据式(15.14-17)可以设 $v_{l+1} = \frac{1}{2}\overline{\left[\boldsymbol{F}_{l+1}^{\ddagger}\boldsymbol{P}_{l+1}\boldsymbol{F}_{l+1}\right]} + \alpha_{l+1}, \alpha_{l+1}$ 与 $u_l$ 无关，那么

$$
v _ {l} = \min _ {\boldsymbol {u} _ {l}} \frac {1}{2} \overline {\left[ \boldsymbol {F} _ {l + 1} ^ {\tau} P _ {l + 1} \boldsymbol {F} _ {l + 1} + \boldsymbol {F} _ {l} ^ {\tau} Q \boldsymbol {F} _ {l} + \boldsymbol {u} _ {l} ^ {\tau} R _ {l} \boldsymbol {u} _ {l} \right] + \alpha_ {l + 1}}
$$

类似于 $t_{N-1}$ 时刻, 可以得到最优控制

$$
\mathbf {\dot {u}} = \frac {1}{2} = - \Lambda_ {l} \mathbf {\dot {Y}} _ {l} = - \left(\Psi_ {l} ^ {*} P _ {l + 1} \Psi_ {l} + R _ {l}\right) ^ {- 1} \Psi_ {l} ^ {*} P _ {l + 1} \Phi_ {l + 1, l} \mathbf {\dot {Y}} _ {l} \tag {15.14-20}
$$

把式(15.14-20)代入 $v_{l}$ 后得到

$$
v _ {l} = \frac {1}{2} \overline {{\left[ \boldsymbol {F} _ {l} ^ {\xi} \boldsymbol {P} _ {l} \boldsymbol {F} _ {l} \right]}} + \alpha_ {l} \tag {15.14-21}
$$

其中

$$
P _ {l} = Q _ {l} + \Phi_ {l + 1, l} ^ {\tau} \left[ P _ {l + 1} - P _ {l + 1} \Psi_ {l} \left(\Psi_ {l} ^ {\tau} P _ {l + 1} \Psi_ {l} + R _ {l}\right) ^ {- 1} \Psi_ {l} ^ {\tau} P _ {l + 1} \right] \Phi_ {l + 1, l} ^ {\tau} \tag {15.14-13}
$$

$$
\alpha = \alpha_ {l + 1} + \frac {1}{2} \operatorname{tr} \left[ \Phi_ {l + 1, l} ^ {\tilde {}} P _ {l + 1} \Psi_ {l} \left(\Psi_ {l} ^ {\tilde {}} P _ {l + 1} \Psi_ {l} + R _ {l}\right) ^ {- 1} \Psi_ {l} P _ {l + 1} \Phi_ {l + 1, l} \Sigma_ {\mathring {E} _ {l}} ^ {2} \right]
$$

$$
+ \frac {1}{2} \operatorname{tr} \left[ G _ {l} ^ {\tau} G _ {l} \Sigma_ {w l} ^ {2} \right] \tag {15.14-22}
$$

只要令 $P_{N}=S,\alpha_{N}=0$ ，就可以递推得到 $\Lambda_{l},P_{l},\alpha_{l}$ 和 $v_{l},l=N-1,\cdots,1,0$ 。性能指标 J 的极小值就是 $v_{0}$ 。这样就得到了采样线性二次高斯问题的全部解，即最优控制规律是

$$
\mathbf {\dot {u}} _ {k} = - \Lambda_ {k} \mathbf {Y} _ {k}, \quad k = 0, 1, \dots , N - 1 \tag {15.14-20}
$$

其中

$$
\Lambda_ {k} = \left[ \Psi_ {k} ^ {*} P _ {k + 1} \Psi_ {k} + R _ {k} \right] ^ {- 1} \Psi_ {k} P _ {k + 1} \Phi_ {k + 1, k}, \quad k = 0, 1, \dots , N - 1 \tag {15.14-23}
$$

$$
P _ {k} = Q _ {k} + \Phi_ {k + 1, k} ^ {\tau} \left[ P _ {k + 1} - P _ {k + 1} \Psi_ {k} \left(\Psi_ {k} ^ {\tau} P _ {k + 1} \Psi_ {k} + R _ {k}\right) ^ {- 1} \Psi_ {k} ^ {\tau} P _ {k + 1} \right] \Phi_ {k + 1, k} ^ {\tau}
$$

$$
k = 0, 1, \dots , N - 1 \tag {15.14-24}
$$

终端条件为 $P_{N}=S$

$$
\mathbf {\dot {Y}} _ {k} = \Phi_ {k, k - 1} \mathbf {\dot {Y}} _ {k - 1} + \Psi_ {k - 1} \mathbf {u} _ {k - 1} + K _ {k} \left(\mathbf {X} _ {k} - C _ {k} \Phi_ {k, k - 1} \mathbf {\dot {Y}} _ {k - 1} - C _ {k} \Psi_ {k - 1} \mathbf {u} _ {k - 1}\right) \tag {15.14-25}
$$

$$
K _ {k} = \Sigma_ {\widetilde {F} _ {k}} ^ {2} C _ {k} ^ {\tau} (C _ {k} \Sigma_ {F _ {k}} C _ {k} ^ {\tau} + \Sigma_ {N _ {k}} ^ {2}) ^ {- 1} \tag {15.14-26}
$$

$$
\Sigma_ {\tilde {F} _ {k}} ^ {2} = \Phi_ {k, k - 1} \Sigma_ {\tilde {E} _ {k - 1}} ^ {2} \Phi_ {k, k - 1} ^ {\tau} + G _ {k - 1} \Sigma_ {W _ {k - 1}} ^ {2} G _ {k - 1} ^ {\tau} \tag {15.14-27}
$$

$$
\Sigma_ {\tilde {E} _ {k}} ^ {2} = \Sigma_ {\tilde {F} _ {k}} ^ {2} - \Sigma_ {\tilde {F} _ {k}} ^ {2} C _ {k} ^ {\tau} (C _ {k} \Sigma_ {\tilde {F} _ {k}} C _ {k} ^ {\tau} + \Sigma_ {N _ {k}} ^ {2}) ^ {- 1} C _ {k} \Sigma_ {\tilde {F} _ {k}} ^ {2} \tag {15.14-28}
$$

初始条件为 $\dot{Y}_{0} = \overline{F_{0}}$ , $\Sigma_{\dot{E}_{0}}^{2} = \Sigma_{F_{0}}^{2}$ ，这样得到的性能指标的最小值为

$$
\begin{array}{l} \min J = \frac {1}{2} \overline {{\left[ \boldsymbol {F} _ {0} ^ {\mathrm{c}} P _ {0} \boldsymbol {F} _ {0} \right]}} + \alpha_ {0} = \frac {1}{2} \overline {{\boldsymbol {F} _ {0} ^ {\mathrm{c}}}} P _ {0} \overline {{\boldsymbol {F}}} _ {0} + \frac {1}{2} \operatorname{tr} \left[ P _ {0} \Sigma_ {\boldsymbol {F} _ {0}} ^ {2} \right] \\ + \frac {1}{2} \sum_ {k = 0} ^ {N - 1} \left[ \Phi_ {k + 1} ^ {\tau} P _ {k + 1} \Psi_ {k} \left(\Psi_ {k} ^ {\tau} P _ {k + 1} \Psi_ {k} + R _ {k}\right) ^ {- 1} \Psi_ {k} P _ {k + 1} \Phi_ {k + 1, k} \Sigma_ {E _ {k}} ^ {2} \right] \\ + \frac {1}{2} \sum_ {k = 0} ^ {N - 1} \left[ G _ {k} G _ {k} ^ {\tau} \Sigma_ {w _ {k}} ^ {2} \right] \tag {15.14-29} \\ \end{array}
$$

上式中第二项是由于初值的随机性引起的附加性能指标值，第四项是由于系统状态的随机性引起的附加性能指标值，第三项是由于状态估计不准确而引起的附加性能指标值。当所有的随机作用都不存在时,J 的最小值就是确定性线性二次问

题的最小性能指标值。

我们可以把结果用图 15.14-1 所示的方块图来表示。

> 此处省略原书 **图 15.14-1**

从上述结果可以看出，在线性二次高斯问题中可以把过滤问题和控制问题分离开来单独考虑。在考虑过滤问题时不需考虑控制是什么，只需把它看作一个确定性的输入就可以了。在考虑控制问题时不需考虑随机作用的影响，只需求出控制规律的最优反馈系数 $\Lambda_{k}$ 即可，然后，把它们两个串联起来，最优随机控制就用最优反馈系数乘以经过最优过滤后的输出而得到的，这就是所谓的“分离定理”。要注意，对于一般的最优随机控制问题，“分离定理”并不是都可以应用的。

对于连续的线性二次高斯问题，“分离定理”仍然成立。我们这里只叙述结果而不加证明。

假设系统的模型为

$$
\frac {d}{d t} \boldsymbol {F} (t) = A (t) \boldsymbol {F} (t) + B (t) \boldsymbol {W} (t) + \Psi (t) \boldsymbol {u} (t) \tag {15.14-30}
$$

$$
\boldsymbol {X} (t) = C (t) \boldsymbol {F} (t) + \boldsymbol {N} (t), \quad t _ {0} \leqslant t \leqslant t _ {N} \tag {15.14-31}
$$

其中系统的状态 $\boldsymbol{F}(t)$ 是 n 维向量随机过程，观测值 $\boldsymbol{X}(t)$ 是 m 维向量随机过程，r 维控制函数 $\boldsymbol{u}(t)$ 是非随机性的， $\boldsymbol{W}(t)$ 和 $\boldsymbol{N}(t)$ 是互不相关的数学期望为零的 p 维，m 维白色高斯随机过程，方差是 $\Sigma_{\boldsymbol{W}}^{2}(t), \Sigma_{\boldsymbol{N}}^{2}(t)$ ，状态初值 $\boldsymbol{F}(t_{0})$ 是随机向量，数学期望是 $\overline{\boldsymbol{F}_{0}}$ ，方差是 $\Sigma_{F_{0}}^{2}$ ，它与 $\boldsymbol{W}(t), \boldsymbol{N}(t)$ 都互不相关，A, B, $\Psi$ , C 为相应阶数的矩阵。要求寻找这样的最优控制函数 $\boldsymbol{u}(t)$ ，它是系统状态初值 $\boldsymbol{F}(t_{0})$ 和 t 时刻以前观测值 $\boldsymbol{X}(\sigma), t_{0} \leqslant \sigma \leqslant t$ 的某种确定函数，使得性能指标

$$
J = \overline {{{\frac {1}{2} \boldsymbol {F} (t _ {N}) ^ {\tau} S \boldsymbol {F} (t _ {N}) + \frac {1}{2} \int_ {t _ {0}} ^ {t _ {N}} [ \boldsymbol {F} (t) ^ {\tau} Q (t) \boldsymbol {F} (t) + \boldsymbol {u} ^ {\tau} (t) R (t) \boldsymbol {u} (t) ] d t}}} \tag {15.14-32}
$$

达到极小值。其中 S 和 $Q(t)$ 是非负的对称矩阵， $R(t)$ 是正定的对称矩阵。

可以证明，最优控制函数

$$
\mathbf {\dot {u}} (t) = - \Lambda (t) \mathbf {\dot {Y}} (t) \tag {15.14-33}
$$

其中最优反馈系数

$$
\Lambda (t) = R (t) \Psi^ {\tau} (t) P (t) \tag {15.14-34}
$$

矩阵 $P(t)$ 满足黎卡提方程

$$
\frac {d}{d t} P (t) = - A ^ {\tau} (t) P (t) - P (t) A (t) - Q (t) + P (t) \Psi (t) R ^ {- 1} (t) \Psi^ {\tau} (t) P (t) \tag {15.14-35}
$$

终端条件是

$$
P (t _ {N}) = S
$$

$Y(t)$ 是最优过滤器的输出，它由下式确定

$$
\frac {d}{d t} \mathbf {\dot {Y}} (t) = A (t) \mathbf {\dot {Y}} (t) + \Psi (t) \mathbf {u} (t) + K (t) [ \mathbf {X} (t) - C (t) \mathbf {\dot {Y}} (t) ] \tag {15.14-36}
$$

其中

$$
K (t) = \Sigma_ {E} ^ {2} (t) C ^ {\tau} (t) \Sigma_ {N} ^ {- 2} (t) \tag {15.14-37}
$$

$$
\frac {d}{d t} \Sigma_ {\dot {E}} ^ {2} (t) = A (t) \Sigma_ {\dot {E}} ^ {2} (t) + \Sigma_ {\dot {E}} ^ {2} (t) A ^ {\tau} (t) - \Sigma_ {\dot {E}} ^ {2} (t) C ^ {\tau} (t) \Sigma_ {N} ^ {- 2} (t) C (t) \Sigma_ {\dot {E}} ^ {2} (t) \tag {15.14-38}
$$

初始条件为

$$
\mathbf {\dot {Y}} (t _ {0}) = \overline {{\boldsymbol {F} (t _ {0})}}, \quad \Sigma_ {\mathbf {\dot {E}}} ^ {2} (t _ {0}) = \Sigma_ {\mathbf {F}} ^ {2} (t _ {0})
$$

此结果也可以用方块图表示（图 15.14-2)

> 此处省略原书 **图 15.14-2**

在最优控制式(15.14-33)的作用下，性能指标的最小值是

$$
\min J = \frac {1}{2} \overline {{{\boldsymbol {F} ^ {\epsilon} (t _ {0})}}} P (t _ {0}) \overline {{{\boldsymbol {F} (t _ {0})}}} + \frac {1}{2} \operatorname{tr} [ P (t _ {0}) \Sigma_ {\mathcal {F} _ {0}} ^ {2} ] + \operatorname{tr} \left\{\int_ {t _ {0}} ^ {t _ {N}} K (\sigma) \Sigma_ {N} ^ {2} (\sigma) K ^ {\tau} (\sigma) P (\sigma) d \sigma \right\}
$$

$$
+ \operatorname{tr} \left\{S \Sigma_ {\dot {E}} ^ {2} \left(t _ {N}\right) + \int_ {t _ {0}} ^ {t _ {f}} Q (\sigma) \Sigma_ {\dot {E}} ^ {2} (\sigma) d \sigma \right\} \tag {15.14-39}
$$

最后，我们来看线性二次高斯问题在控制系统设计中的作用 $^{[7]}$ 。在具体的集中参数控制系统中，受控对象（包括执行机构）的运动通常可用一个非线性变系数的常微分方程来描述

$$
\frac {d}{d t} \boldsymbol {f} (t) = \varphi (\boldsymbol {f} (t), \boldsymbol {u} (t), t), \boldsymbol {f} (t _ {0}) = \boldsymbol {f} _ {0} \tag {15.14-40}
$$

$f(t)$ 是系统的状态, $u(t)$ 是控制输入。受控对象的状态由测量装置经过某种变换而测得。测量装置的输出为

$$
\boldsymbol {x} (t) = \boldsymbol {g} (\boldsymbol {f} (t), t) \tag {15.14-41}
$$

如果测量装置有明显的动力学特性，那么也可以把它并入在受控对象的方程中。假设 $\varphi,g$ 都是连续的，并且对 f 和 u 都有足够次数的导数。当给定状态的初值和给定某个控制输入后，按式(15.14-40)和(15.14-41)就可准确地算出系统的状态 $f(t)$ 和观测值 $x(t)$ 。根据需要，可以确定符合某种需要的较好的控制输入 $u_{1}(t)$ 以及系统状态 $f_{1}(t)$ 和观测值 $x_{1}(t)$ 。例如在地地导弹的飞行控制系统中，可以根据某种性能指标确定一条从发射点到弹着点的理想弹道曲线 $f_{1}(t)$ 和实现此弹道曲线的理想的控制输入 $u_{1}(t)$ ,测量装置也可给出此弹道曲线的观测值 $x_{1}(t)$ 。这可以用极大值原理或动态规划等方法来完成。如果运动方程(15.14-41)是准确的，状态的初值是准确的，没有什么干扰因素，那么给了准确地控制输入 $u_{1}(t)$ 后，就可以准确地实现系统状态 $f_{1}(t)$ 。但是，这在实际上是不可能的，因为运动方程不可能完全准确（包括其中某些参数),初值 $f_{1}(t)$ 也不可能完全准确，还有各种干扰因素，因此再加上控制输入 $u_{1}(t)$ 后，不可能准确地实现最优的系统状态。那么，我们就要使实际的控制输入 $u(t)$ 稍加改变，使系统的状态 $f(t)$ 尽可能地接近于最优 $f_{1}(t)$ 。

定义状态的扰动量是

$$
\delta \boldsymbol {f} (t) = \boldsymbol {f} (t) - \boldsymbol {f} _ {1} (t) \tag {15.14-42}
$$

输出的扰动量是

$$
\delta \boldsymbol {x} (t) = \boldsymbol {x} (t) - \boldsymbol {x} _ {1} (t) \tag {15.14-43}
$$

控制输入的修正量是

$$
\delta \boldsymbol {u} (t) = \boldsymbol {u} (t) - \boldsymbol {u} _ {1} (t) \tag {15.14-44}
$$

我们可以加一个反馈控制，根据状态的扰动量 $\delta f$ 来确定控制输入的修正量，使以后的状态扰动量尽可能地小。把运动方程和输出方程(15.14-40),(15.14-41)在 $f_{1}(t),u_{1}(t)$ 附近展开成泰勒级数就可以得到

$$
\begin{array}{l} \frac {d}{d t} \delta \boldsymbol {f} (t) = \varphi (\boldsymbol {f} (t), \boldsymbol {u} (t), t) - \varphi (\boldsymbol {f} _ {1} (t), \boldsymbol {u} _ {1} (t), t) \\ = \left. \frac {\partial \varphi}{\partial \boldsymbol {f}} \right| _ {f _ {1} (t), \boldsymbol {u} _ {1} (t)} \delta \boldsymbol {f} (t) + \left. \frac {\partial \varphi}{\partial \boldsymbol {u}} \right| _ {f _ {1} (t), \boldsymbol {u} _ {1} (t)} \delta \boldsymbol {u} (t) + \boldsymbol {a} (\delta \boldsymbol {f} (t), \delta \boldsymbol {u} (t), t) \tag {15.14-45} \\ \end{array}
$$

$$
\begin{array}{l} \frac {d}{d t} \delta \boldsymbol {x} (t) = \boldsymbol {g} (\boldsymbol {f} (t), t) - \boldsymbol {g} (\boldsymbol {f} _ {1} (t), t) \\ = \left. \frac {\partial \boldsymbol {g}}{\partial \boldsymbol {f}} \right| _ {f _ {1} (t)} \delta \boldsymbol {f} (t) + \beta_ {0} (\delta \boldsymbol {f} (t), t) \tag {15.14-46} \\ \end{array}
$$

在忽略扰动的高次项后，就可以得到线性变系数方程

$$
\frac {d}{d t} \delta \boldsymbol {f} (t) = A (t) \delta \boldsymbol {f} (t) + B (t) \delta \boldsymbol {u} (t) \tag {15.14-47}
$$

$$
\delta \boldsymbol {x} (t) = C (t) \delta \boldsymbol {f} (t) \tag {15.14-48}
$$

其中

$$
A (t) = \left. \frac {\partial \varphi}{\partial \boldsymbol {f}} \right| _ {f _ {1} (t), \boldsymbol {u} _ {1} (t)}, \quad B (t) = \left. \frac {\partial \varphi}{\partial \boldsymbol {u}} \right| _ {f _ {1} (t), \boldsymbol {u} _ {1} (t)}, \quad C (t) = \left. \frac {\partial \boldsymbol {g}}{\partial \boldsymbol {f}} \right| _ {f _ {1} (t)} \tag {15.14-49}
$$

为了保证线性模型的有效性，必须使 $\delta\boldsymbol{f}(t)$ 和 $\delta\boldsymbol{u}(t)$ 都相当的小，因此在选择最优的 $\delta\boldsymbol{u}(t)$ 时使二次泛函性能指标

$$
J = \frac {1}{2} \delta \boldsymbol {f} (t _ {N}) ^ {\tau} S \delta \boldsymbol {f} (t _ {N}) + \frac {1}{2} \int_ {t _ {0}} ^ {t _ {N}} \delta \boldsymbol {f} (t) ^ {\tau} Q (t) \delta \boldsymbol {f} (t) + \delta \boldsymbol {u} (t) ^ {\tau} R (t) \delta \boldsymbol {u} (t) d t \tag {15.14-50}
$$

取最小值是很恰当的。这里 S 和 $Q(t)$ 是非负的对称阵， $R(t)$ 是正定的对称阵。这样就产生了一个非随机的线性二次问题。设计者可以选用适当的 S, $Q(t)$ , $R(t)$ ，使非随机的线性二次问题有合适的解。在实际物理问题中，受控对象和执行机构都受到各种随机干扰的影响，并且系统的状态并不是能够直接、全部测量到的，在测量过程中也受到随机干扰的影响，因此就需要考虑线性二次高斯问题，这时系统的状态 $F(t)$ 和观测值 $X(t)$ 都是向量随机过程。选择 $\delta u(t)$ 使性能指标

$$
J = \overline {{\frac {1}{2} \delta \boldsymbol {F} ^ {\tau} (t _ {N}) S \delta \boldsymbol {F} (t _ {N}) + \frac {1}{2} \int_ {t _ {0}} ^ {t _ {N}} \delta \boldsymbol {F} (t) ^ {\tau} Q (t) \delta \boldsymbol {F} (t) + \delta \boldsymbol {u} (t) ^ {\tau} R (t) \delta \boldsymbol {u} (t) d t}}
$$

达到极小，这与保证线性模型的有效性是一致的。线性二次高斯问题的结果已列在式(15.14-33)—(15.14-38)中。对于设计者来说，现在的问题就是选择合适的 $S,Q(t),R(t)$ 和 $\Sigma_{w}^{2}(t),\Sigma_{N}^{2}(t)$ ,使整个控制系统有较好的性能。

#### 15.15 从噪声中检测信号 $^{[14,24]}$

在很多控制系统中被测量、控制量或系统的状态都不可能直接得到，必须用某种被调制了的信号以各种物理过程的形式传送。我们把未调制时的原始量称为消息，用 $d(t)$ 表示，载负消息而用来传输消息的物理量称为信号，用 $f_{d}(t)$ 表示。如果消息和信号是随机函数，那么我们分别用 $D(t)$ 和 $F_{D}(t)$ 来表示。例如，在脉 冲制雷达的距离测量系统中，目标离雷达的斜距是消息，它是随时间连续变化的量，在调制后，视频信号是相位随距离变化的脉冲序列，射频信号是用视频信号调制的超高频正弦振荡（见图 15.15-1)。当然，在某些控制系统中消息和信号是完全相同的。在前面各节中已经比较详细地讨论了信号覆现的问题。在本节和下一节内将讨论信号的检测和信号参数估计的问题，在这些问题中最优过滤的设计往往不采用均方误差最小的准则，而采用其他准则。

> 此处省略原书 **图 15.15-1**

在一般控制系统的观测量中无论信号是否存在总是有随机噪声作用的。对于某些系统，例如雷达接收机，随机噪声作用较强，不能予以忽略。信号检测的目的就是要根据已知的信号噪声统计特性来辨识观测量中只有噪声呢还是有信号存在，所以通常称作“从噪声中检测信号”。

假设系统的观测值是信号和噪声的叠加

$$
X (t) = F _ {D} (t) + N (t) \tag {15.15-1}
$$

噪声 $N(t)$ 是数学期望为零的平稳随机过程，信号 $F_{D}(t)$ 也是随机函数，它是消息 $D$ 的真正载负者。假设在某一时间间隔中，消息 $D$ 只可能取两个值之一：0 或 1。如果消息 $D = 0$ 时 $F_{0}(t) = 0$ ；消息 $D = 1$ 时 $F_{1}(t) = f(t)$ ，那么称信号为“已知”的；如果消息 $D = 0$ 时 $F_{0}(t) = 0$ ，消息 $D = 1$ 时， $F_{1}(t)$ 是依赖于某个随机参数 $\Phi$ 的随机函数 $F_{1}(t) = F(t, \Phi)$ ，那么 $F(t)$ 称为是带有随机参数的信号。假设 $\Phi$ 与 $N(t)$ 的统计特性和信号 $F(t, \Phi)$ 或 $f(t)$ 的函数形式都已知，现在要根据在一段有限时间 间隔 $0 \leqslant t \leqslant T$ 内的观测值 $X(t)$ 的一个现实 $x(t)$ 来辨别消息 $D$ 取 0 还是取 1。通常是把 $X(t)$ 在 $0 \leqslant t \leqslant T$ 内所有可能的取值划分为两个部分 $Z_0$ 和 $Z_1$ ，如果 $x(t)$ 属于 $Z_0$ ，则认为消息 $D = 0$ ；如果 $x(t)$ 不属于 $Z_0$ 而属于 $Z_1$ ，那么就认为消息 $D = 1$ 。因为我们是根据一个观测值 $x(t), 0 \leqslant t \leqslant T$ 来辨别的，所以通常不可能绝对正确，总有出差错的可能。可能发生两种差错：第一种称为“虚警”，即 $D = 0$ 时而 $x(t)$ 属于 $Z_1$ ，误认为 $D = 1$ 。虚警概率即条件概率 $p\{x(t) \in Z_1 \mid D = 0\}$ ，简记为 $p_0(Z_1)$ ；第二种是“漏警”，即当 $D = 1$ 时，而 $x(t)$ 属于 $Z_0$ 误认为 $D = 0$ 。漏警概率即条件概率 $p\{x(t) \in Z_0 \mid D = 1\}$ ，简记为 $p_1(Z_0)$ 。另外还有两种正确的情况，它们的概率分别用 $p_0(Z_0)$ 和 $p_1(Z_1)$ 表示。显然

$$
p _ {0} \left(\mathbf {Z} _ {0}\right) + p _ {0} \left(\mathbf {Z} _ {1}\right) = 1, \quad p _ {1} \left(\mathbf {Z} _ {0}\right) + p _ {1} \left(\mathbf {Z} _ {1}\right) = 1 \tag {15.15-2}
$$

条件概率 $p_0(Z_1)$ 和 $p_1(Z_0)$ 分别是条件概率密度函数的积分

$$
p _ {0} \left(Z _ {1}\right) = \int_ {Z _ {1}} w (x \mid D = 0) d x \tag {15.15-3}
$$

$$
p _ {1} \left(Z _ {0}\right) = \int_ {Z _ {0}} w (x \mid D = 1) d x \tag {15.15-4}
$$

这里 w 是指多维条件概率密度函数。

我们可以按照不同的准则来划分 $Z_{0}$ 和 $Z_{1}$ ，在划分好以后可根据任意一次的观测值 $x(t), 0 \leqslant t \leqslant T$ ，去辨别有何种消息存在。为此可采用下列准则：

（1）发生差错的全概率最小：假定消息为 1 或 0 的先验概率分别是 $p(1)$ 和 $p(0)$ ，它们都是已知的，则发生差错的全概率为

$$
p = p (1) p _ {1} \left(\mathbf {Z} _ {0}\right) + p (0) p _ {0} \left(\mathbf {Z} _ {1}\right) \tag {15.15-5}
$$

（2）贝叶斯准则，即要使平均损耗最小：假定“虚警”和“漏警”相应的损耗值为 $R_{01}$ 和 $R_{10}$ ，两种正确的情况相应的损耗值为 $R_{00}$ 和 $R_{11}$ ，那么平均损耗 $\overline{R}$ 定义为

$$
\overline {{{R}}} = p (0) \left[ R _ {0 0} p _ {0} \left(Z _ {0}\right) + R _ {0 1} p _ {0} \left(Z _ {1}\right) \right] + p (1) \left[ R _ {1 1} p _ {1} \left(Z _ {1}\right) + R _ {1 0} p _ {1} \left(Z _ {0}\right) \right] \tag {15.15-6}
$$

（3）诺曼-皮尔生(Neyman-Person)准则：在虚警概率小于一定的水平的条件下使漏警概率最小。这就要求 $Z_{1}$ 满足下列条件

$$
p _ {0} \left(Z _ {1}\right) = \varepsilon , p _ {1} \left(Z _ {1}\right) \geqslant p _ {1} (Z) (\text {所有的} Z \text {应满足} p _ {0} (Z) = \varepsilon) \tag {15.15-7}
$$

（4）似然比准则：规定 $Z_{1}$ 由那些使 D=1 和 D=0 的条件概率密度函数之比不小于某个阈值 $\beta$ 的 $x(t), 0 \leqslant t \leqslant T$ 组成， $\beta$ 是大于或等于零的值。这种条件概率密度函数之比称为似然比，用符号 $l(x)$ 表示。那么似然比准则就是要求

$$
\text {当} l (x) = w (x \mid D = 1) / w (x \mid D = 0) \geqslant \beta \text {时}
$$

$$
x (t) \in Z _ {1}, \quad 0 \leqslant t \leqslant T, \quad \beta \geqslant 0 \tag {15.15-8}
$$

可以证明，只要选择恰当的 $\beta$ 值，第(1),(2),(3)种准则都可以化为似然比准则。

事实上，根据关系式(15.15-2),(15.15-3)和(15.15-4),式(15.15-5)可以化为

$$
p = p (1) - \int_ {z _ {1}} [ p (1) w (x \mid D = 1) - p (0) w (x \mid D = 0) ] d x \tag {15.15-9}
$$

为了使 p 达到最小, 必须使积分式最大, 即被积式当 $x(t) \in Z_{1}$ 时应该是非负的。于是发生差错的全概率最小的条件就化为不等式

$$
p (1) w (x \mid D = 1) - p (0) w (x \mid D = 0) \geqslant 0, \quad x (t) \in Z _ {1}
$$

进一步简化后又得到选择 $Z_{1}$ 的条件是

$$
l (x) = \frac {w (x \mid D = 1)}{w (x \mid D = 0)} \geqslant \frac {p (0)}{p (1)} \tag {15.15-10}
$$

若取 $\beta=\frac{p(0)}{p(1)}$ ，那么发生差错的全概率最小准则就等价于似然比准则。同样，若令

$$
\beta = \frac {p (0)}{p (1)} \cdot \frac {\left(R _ {0 1} - R _ {0 0}\right)}{\left(R _ {1 0} - R _ {1 1}\right)}
$$

> 此处省略原书 **图 15.15-2**

那么似然比准则就变成贝叶斯准则。在采用似然比准则时，取不同的 $\beta$ 值就可以得到不同的发生差错的概率 $p_0(Z_1)$ 和 $p_1(Z_0)$ 。我们以 $p_0(Z_1)$ 为横坐标，以 $p_1(Z_1) = 1 - p_1(Z_0)$ 为纵坐标就可以画出系统的工作特性（如图 15.15-2 所示）。显然当 $\beta = 0$ 时， $l(x) \geqslant \beta$ 对所有的 $x(t), 0 \leqslant t \leqslant T$ ，都能满足，因此 $p_0(Z_1) = 1, p_1(Z_1) = 1$ ；当 $\beta = \infty$ 时， $l(x) \geqslant \beta$ 对所有 $x(t), 0 \leqslant t \leqslant T$ ，都有 $p_0(Z_1) = 0, p_1(Z_1) = 0$ 。当 $\beta$ 在 0 到 $\infty$ 之间变化时， $0 \leqslant p_0(Z_1) \leqslant 1, 0 \leqslant p_1(Z_0) \leqslant 1$ 。可 以证明，系统的工作特性曲线是条单调的曲线，曲线上每一点的斜率就等于按似然比准则的相应于该点的 $p_{0}(Z_{1})$ 和 $p_{1}(Z_{1})$ 的阈值 $\beta$ 。如果给定了诺曼-皮尔生准则中的 $\varepsilon$ 值，那么由 $p_{0}(Z_{1})=\varepsilon$ 就可以在系统的工作特性曲线上寻到相应的 $\beta$ 值，因此诺曼-皮尔生准则也可以化成似然比准则。

在讨论信号检测问题时，常假定噪声 $N(t)$ 是个高斯分布的数学期望为零的白色噪声。如果噪声不是高斯分布的，那么解决信号检测问题就困难得多。幸好，实际上我们所遇到的随机噪声大多是高斯分布的。在讨论时，我们常以一个有限带宽的功率谱密度的平稳随机过程来近似白色噪声，如令

$$
\Phi_ {N} (\omega) = \left\{ \begin{array}{l l} N, & 0 \leqslant \omega \leqslant \omega_ {c} \\ 0, & \omega > \omega_ {c} \end{array} \right. \tag {15.15-11}
$$

由功率谱密度可以求出它的相关函数

$$
r _ {N} (\sigma) = \int_ {0} ^ {\infty} \Phi_ {N} (\omega) \cos \omega \sigma d \omega = N \int_ {0} ^ {\omega_ {c}} \cos \omega \sigma d \omega = \frac {N \sin \omega \sigma}{\sigma} \tag {15.15-12}
$$

功率谱密度 $\Phi_{N}(\omega)$ 和相关函数 $r_{N}(\sigma)$ 示于图 15.15-3 中。由图可以看出，在

$$
\sigma = h \frac {\pi}{\omega_ {c}}, \quad k = 1, 2, \dots
$$

> 此处省略原书 **图 15.15-3**

时 $r_{N}(\sigma)$ 等于零，如果 $\omega_{c}$ 足够大，使 $T \gg \pi / \omega_{c}$ 时， $r_{N}(\sigma)$ 可近似看为 $\delta$ 函数， $r_{N}(\sigma) \cong \pi N \delta(\sigma)$ ，就很近于白色噪声。如果噪声不是白色的，那么可以通过相应的转换，把它变成白色噪声来考虑。

现在来讨论几个从噪声中检测信号的例子。

例 1．假定信号是“已知”的，即 D=0 时， $F_{0}(t)=0, D=1$ 时 $F_{1}(t)=f(t)$ 是给定的确定函数， $N(t)$ 是高斯分布的白色噪声。现在要由观测到的一个现实 $x(t), 0 \leqslant t \leqslant T$ 来辨别 D=0 还是 D=1，要求根据似然比准则来确定 $Z_{1}$ 。

我们用有限带宽的平稳随机过程来近似白色噪声。先在区间 $0 \leqslant t \leqslant T$ 内取 n 个分点 $n = \frac{T\omega}{\pi}$ ，取 $t_k = k\Delta t = h\frac{T}{n}$ ，并令 $x(t_k) = x_k, f(t_k) = f_k$ 。这样我们就得到条件概率密度函数

$$
w \left(x _ {1}, \dots , x _ {n} \mid D = 0\right) = \left(2 \pi N \omega_ {c}\right) ^ {- \frac {n}{2}} \exp \left\{- \sum_ {k = 1} ^ {n} \frac {x _ {k} ^ {2}}{2 N \omega_ {c}} \right\}
$$

$$
w \left(x _ {1}, \dots , x _ {n} \mid D = 1\right) = \left(2 \pi N \omega_ {c}\right) ^ {- \frac {n}{2}} \exp \left\{- \sum_ {k = 1} ^ {n} \frac {\left(x _ {k} - f _ {k}\right) ^ {2}}{2 N \omega_ {c}} \right\}
$$

依定义似然比是

$$
l \left(x _ {1}, x _ {2}, \dots , x _ {n}\right) = \frac {w \left(x _ {1} , \cdots , x _ {n} \mid D = 1\right)}{w \left(x _ {1} , \cdots , x _ {n} \mid D = 0\right)} = \exp \left\{\sum_ {k = 1} ^ {n} \frac {2 f _ {k} x _ {k} - f _ {k} ^ {2}}{2 N \omega_ {c}} \right\}
$$

对指数的分子和分母都分别乘以 $\Delta t = T / n = \pi / \omega_{c}$ 后，又有

$$
l \left(x _ {1}, x _ {2}, \dots , x _ {n}\right) = \exp \left\{\sum_ {k = 1} ^ {n} \left(2 f _ {k} x _ {k} \Delta t - f _ {k} ^ {2} \Delta t\right) / 2 \pi N \right\}
$$

现令 $\omega_{\mathrm{c}} \rightarrow \infty$ ，即 $n \rightarrow \infty, \Delta t = \frac{T}{n} \rightarrow 0$ ，对上式取极限后便得到

$$
l (x) = \exp \left\{\frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t) d t - \frac {1}{2 \pi N} \int_ {0} ^ {T} f ^ {2} (t) d t \right\}
$$

按似然比准则 $Z_{1}$ 应这样选择, 使 $l(x) \geqslant \beta$ , 即

$$
\frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t) d t \geqslant \ln \beta + \frac {1}{2 \pi N} \int_ {0} ^ {T} f ^ {2} (t) d t, \quad x (t) \in Z _ {1}
$$

$\int_{0}^{T}f^{2}(t)dt$ 代表信号 $f(t),0\leqslant t\leqslant T$ 的载负功率 $E$ ，而 $2\pi N$ 代表单位赫兹上的噪声功率，一般把 $\frac{1}{2\pi N}\int_{0}^{T}f^{2}(t)dt$ 叫做信噪比，用 $q$ 来表示

$$
q = \frac {E}{2 \pi N} = \frac {1}{2 \pi N} \int_ {0} ^ {T} f ^ {2} (t) d t
$$

从第 15.9 节中我们知道，对信号 $f(t)$ 的有限记忆最优检测过滤器的脉冲响应函数为

$$
\stackrel {\circ} {h} _ {T} (t) = \left\{ \begin{array}{l l} \frac {\lambda}{\pi} f (T - t), & 0 \leqslant t \leqslant T \\ 0, & t <   0 \text {或} t > T \end{array} \right.
$$

如果取 $\lambda=1/N$ ，并在对 $f(t)$ 的最优检测过滤器的输入端加上系统的观测值 $x(t)$ ，那么在 T 时刻的输出为

$$
y (T) = \int_ {0} ^ {T} x (t) \stackrel {\circ} {h} _ {T} (T - t) d t = \frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t) d t
$$

这种信号检测系统的原理图见图 15.15-4, 它也可以用相关器的形式来实现 (图 15.15-5)。

> 此处省略原书 **图 15.15-4**

> 此处省略原书 **图 15.15-5**

当观测值 $X(t)$ 是随机函数时, 最优检测过滤器的输出 $Y(T)$ 也是随机变量:

$$
Y (T) = \frac {1}{\pi N} \int_ {0} ^ {T} X (t) f (t) d t
$$

当 D=0 时, $Y(T)$ 的数学期望为零, 当 D=1 时

$$
\overline {{{Y (T)}}} = \frac {1}{\pi N} \int_ {0} ^ {T} [ f (t) + N (t) ] f (t) d t = \frac {1}{\pi N} \int_ {0} ^ {T} f ^ {2} (t) d t = 2 q
$$

无论 D=0 还是 $D=1, Y(T)$ 的方差都等于

$$
\begin{array}{l} \sigma_ {Y (T)} ^ {2} = \frac {1}{(\pi N) ^ {2}} \int_ {0} ^ {T} \int_ {0} ^ {T} \overline {{{{N (t _ {1}) N (t _ {2})}}}} f (t _ {1}) f (t _ {2}) d t _ {1} d t _ {2} \\ = \frac {1}{\pi N} \int_ {0} ^ {T} \int_ {0} ^ {T} \delta (t _ {1} - t _ {2}) f (t _ {1}) f (t _ {2}) d t _ {1} d t _ {2} \\ = \frac {1}{\pi N} \int_ {0} ^ {T} f ^ {2} (t) d t \\ = \frac {E}{\pi N} \\ = 2 q \\ \end{array}
$$

因为 $Y(t)$ 是高斯分布的 $X(t)$ 的线性泛函, 所以它也是高斯分布的, 知道了它的数学期望和方差后, 它的分布就确定了。我们就可以算出相应于不同阈值 $\beta$ 的 $p_{0}(Z_{1})$ 和 $p_{1}(Z_{1})$

$$
p _ {0} \left(Z _ {1}\right) = \sqrt {\frac {1}{4 \pi q}} \int_ {\alpha} ^ {\infty} \exp \left[ - \frac {y ^ {2}}{4 q} \right] d y
$$

$$
p _ {1} \left(Z _ {1}\right) = \sqrt {\frac {1}{4 \pi q}} \int_ {\alpha} ^ {\infty} \exp \left[ - \frac {1}{4 q} (y - 2 q) ^ {2} \right] d y
$$

其中 $\alpha=\ln\beta+q$ 。对于不同的信噪比 q 又可以得到信号检测系统的不同工作特性（见图 15.15-6）。

> 此处省略原书 **图 15.15-6**

例 2．假定 D=1 时信号是带有随机相位的正弦振荡信号

$$
F (t, \Phi) = d (t) \cos (\omega t - \Phi)
$$

其中 $d(t)$ 是已知的时间函数， $\omega$ 为确定的频率， $\omega \gg 2\pi / T$ 而相位 $\Phi$ 是随机变量，它在 0 到 $2\pi$ 之间均匀分布

$$
w (\varphi) = \left\{ \begin{array}{l l} \frac {1}{2 \pi}, & 0 \leqslant \varphi \leqslant 2 \pi \\ 0, & \varphi <   0, \varphi > 2 \pi \end{array} \right.
$$

在 $\Phi$ 取某个确定的值 $\varphi$ 时， $F(t,\Phi)$ 取值为

$$
f (t, \varphi) = d (t) \cos (\omega t - \varphi) = d (t) \cos \omega t \cos \varphi + d (t) \sin \omega t \sin \varphi 。
$$

假定噪声仍与例 1 中相同。在 $\Phi$ 取确定的值 $\varphi$ 时

$$
\begin{array}{l} l (x, \varphi) = \exp \left\{\frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t, \varphi) d t - \frac {1}{2 \pi N} \int_ {0} ^ {T} f ^ {2} (t, \varphi) d t \right\} \\ = \exp \left\{\frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t, \varphi) d t - q \right\} \\ \end{array}
$$

其中

$$
\begin{array}{l} \frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t, \varphi) d t \\ = \frac {\cos \varphi}{\pi N} \int_ {0} ^ {T} x (t) d (t) \cos \omega t d t + \frac {\sin \varphi}{\pi N} \int_ {0} ^ {T} x (t) d (t) \sin \omega t \\ \end{array}
$$

令

$$
\int_ {0} ^ {T} x (t) d (t) \cos \omega t d t = M \cos \theta
$$

$$
\int_ {0} ^ {T} x (t) d (t) \sin \omega t d t = M \sin \theta
$$

则

$$
\frac {1}{\pi N} \int_ {0} ^ {T} x (t) f (t, \varphi) d t = \frac {M}{\pi N} \cos (\varphi - \theta)
$$

似然比

$$
l (x) = \int_ {- \infty} ^ {\infty} w (\varphi) l (x, \varphi) d \varphi
$$

因此

$$
l (x) = e ^ {- q} \int_ {0} ^ {2 \pi} \frac {1}{2 \pi} \exp \left[ \frac {M}{\pi N} \cos (\varphi - \theta) \right] d \varphi = e ^ {- q} \cdot I _ {0} \left(\frac {M}{\pi N}\right)
$$

$$
\ln l (x) = \ln \mathrm{I} _ {0} \left[ \frac {M}{\pi N} \right] - q
$$

其中 $I_{0}(u)=\frac{1}{2\pi}\int_{0}^{2\pi}e^{u\cos\varphi}d\varphi$ 是零阶贝塞尔函数，它是一个单调增加的函数。按似比准则要求 $l(x)\geqslant\beta$ ，就相当于 $M/\pi N$ 大于或等于某个与 $\beta$ 相应的数。

因为

$$
M = \sqrt {\left[ \int_ {0} ^ {T} x (t) d (t) \cos \omega t d t \right] ^ {2} + \left[ \int_ {0} ^ {T} x (t) d (t) \sin \omega t d t \right] ^ {2}}
$$

所以它可以按原理图 15.15-7 来计算 M, 其中 $\Omega$ 可以是任意的某个固定的较高频率, 但 M 与 $\Omega$ 无关, 图内的相关器就是我们前面讲到的按某个已知信号的最优检测过滤器, 例如相关器 1 就是脉冲响应函数为

$$
h _ {T} (t) = \left\{ \begin{array}{l l} d (T - t) \cos \omega (T - t), & 0 \leqslant t \leqslant T \\ 0, & t <   0, t > T \end{array} \right.
$$

的检测过滤器。

> 此处省略原书 **图 15.15-7**

根据例 1 中所谈到的情况, 当 D=0 时,

$$
\frac {M}{\pi N} \cos \theta = \frac {1}{\pi N} \int_ {0} ^ {T} x (t) d (t) \cos \omega t d t
$$

和

$$
\frac {M}{\pi N} \sin \theta = \frac {1}{\pi N} \int_ {0} ^ {T} x (t) d (t) \sin \omega t d t
$$

的数学期望都为零，方差是 $2q$ ，它们都是高斯分布的随机变量。由于 $\cos \omega t$ 与 $\sin \omega t$ 是正交的，因此 $\frac{M}{\pi N}\cos \theta$ 与 $\frac{M}{\pi N}\sin \theta$ 统计无关，因此 $\left[\frac{M}{\pi N}\right]^2$ 是二阶 $\chi^2$ 分布的随机变量。 $\frac{M}{\pi N}\sqrt{\frac{1}{2q}}$ 的方差等于 1，数学期望为零，所以

$$
p ^ {0} \left[ \frac {M}{\pi N} \sqrt {\frac {1}{2 q}} \geqslant \alpha \right] = \exp \left[ - \frac {\alpha^ {2}}{2} \right]
$$

如果取

$$
\beta = e ^ {- q} \mathrm{I} _ {0} (\sqrt {2 q} \alpha)
$$

那么

$$
p _ {0} \left(Z _ {1} (\beta)\right) = \exp \left[ - \frac {\alpha^ {2}}{2} \right]
$$

由于 $\beta$ 随 $\alpha$ 的增加而单调增加, 所以

$$
d p _ {0} \left(Z _ {1} (\beta)\right) = - \alpha \exp \left[ - \frac {\alpha^ {2}}{2} \right] d \alpha
$$

若根据系统的工作特性，按似然比准则来辨别消息 D,则

$$
d p _ {1} \left(Z _ {1} (\beta)\right) / d p _ {0} \left(Z _ {1} (\beta)\right) = \beta
$$

因此

$$
p _ {1} \left(Z _ {1} (\beta)\right) = \int_ {\beta} ^ {\infty} \beta d p _ {0} \left(Z _ {1} (\beta)\right) = e ^ {- q} \int_ {\alpha} ^ {\infty} - \alpha \exp \left[ - \frac {\alpha^ {2}}{2} \right] I _ {0} (\sqrt {2 q} \alpha) d \alpha
$$

这样我们就可以得到在不同的信杂比 q 时系统的工作特性曲线（图 15.15-8)。

> 此处省略原书 **图 15.15-8**

例 3. 假定信号 $f(t)$ 恒等于某个常数 m，噪声是数学期望为零，相关函数为 $R_{N}(\sigma)=e^{-\lambda^{2}|\sigma|}$ 的高斯分布的平稳随机过程。要求根据观测到的一个现实 $x(t),0\leqslant t\leqslant T$ ，来确定 D=0 还是 D=1。先在 $0\leqslant t\leqslant T$ 内取有限个观测值， $x_{k}=x(t_{k}),e^{-\lambda^{2}(t_{k+1}-t_{k})}=\rho_{k},k=0,1,2,\cdots,n$ 。我们可以得到条件概率密度函数为

$$
\begin{array}{l} w (x _ {0}, x _ {1}, \dots , x _ {n} \mid D = 0) = \frac {1}{(2 \pi) ^ {\frac {n + 1}{2}} \prod_ {k = 0} ^ {n - 1} (1 - \rho_ {k}) ^ {\frac {1}{2}}} \\ \times \exp \left\{- \frac {1}{2} x _ {0} ^ {2} - \frac {1}{2} \sum_ {k = 0} ^ {n - 1} \frac {\left[ x _ {k + 1} - \rho_ {k} x _ {k} \right] ^ {2}}{1 - \rho_ {k} ^ {2}} \right\} \\ \end{array}
$$

$$
\begin{array}{l} w \left(x _ {0}, x _ {1}, \dots , x _ {n} \mid D = 0\right) = \frac {1}{(2 \pi) ^ {\frac {n + 1}{2}} \prod_ {k = 0} ^ {n - 1} \left(1 - \rho_ {k}\right) ^ {\frac {1}{2}}} \exp \left[ - \frac {1}{2} \left(x _ {0} - m\right) ^ {2} \right. \\ - \frac {1}{2} \sum_ {k = 0} ^ {n - 1} \left. \frac {\left[ x _ {k + 1} - \rho_ {k} x _ {k} - m \left(1 - \rho_ {k}\right) \right] ^ {2}}{1 - \rho_ {k} ^ {2}} \right\} \\ \end{array}
$$

当 $n \to \infty$ 时， $\Delta_n = \max_h (t_{k+1} - t_k) \to 0$ ，不难得到

$$
l (x) = \exp \left\{\frac {m}{2} x (0) + \frac {m}{2} x (T) - \frac {m ^ {2}}{2} + \frac {m}{4} \lambda^ {2} \int_ {0} ^ {T} x (t) d t - \frac {m ^ {2}}{4} \lambda^ {2} T \right\}
$$

因此按似然比准则，当

$$
x (0) + x (T) + \lambda^ {2} \int_ {0} ^ {T} x (t) d t \geqslant K
$$

时认为 D=1，反之则认为 D=0，其中

$$
K = \frac {2}{m} \ln \beta + m + \frac {m}{2} \lambda^ {2} T
$$

当 K 趋于 $-\infty$ 时，虚警概率 $p_{0}(Z_{1})=1$ ，漏警概率 $p_{1}(Z_{0})=0$ ；而 K 趋于 $+\infty$ 时，虚警概率 $p_{0}(Z_{1})=0$ ，漏警概率 $p_{1}(Z_{0})=1$ ；当 K 在 $-\infty$ 到 $+\infty$ 之间取值时，虚警概率与漏警概率都在 0 到 1 之间。

上面我们讨论的都是根据一次的观测值辨别 D=0 或 D=1 的。当然还可以根据多次观测来作出辨别。这里我们不再作讨论，读者可以参看文献 $[14,24,25]$ 。

#### 15.16 信号参数的估计

现在来讨论从噪声中测定信号所携带的消息，也就是“估计信号的参数”。显然，上一节中讨论的在噪声中检测信号的问题只是一个特殊情况，在这种特殊情况中，消息 D(即参数）只取 0 和 1 两个值。例如，在脉冲制雷达中，目标离雷达天线的距离和回波脉冲与发射脉冲之间的时间间隔成正比，为了测量距离，我们必须去估计信号中时间间隔这个参数。又例如对活动目标来说，射频信号的载频的变化与在雷达天线方向目标速度的分量成正比，如果这个速度也是一个消息，那么我们就要估计信号中载频的变化这个参数。假设观测量是信号与噪声的叠加

$$
X (t) = F _ {D} (t) + N (t) \tag {15.16-1}
$$

信号 $F_{D}(t)$ 是消息 $D$ 的已知函数或是消息 $D$ 的带有随机参数 $\Phi$ 的函数 $F_{D}(t, \Phi)$ ; 消息 $D$ 可以是随机变量, 也可以是未知的非随机量。假定在 $X(t)$ 的一个现实中消息 $D$ 总是取某一个不变的值 $d$ ; 噪声 $N(t)$ 是数学期望为零的平稳随机过程。现在要求根据 $X(t)$ 的每一个现实 $x(t), 0 \leqslant t \leqslant T$ , 估计与此现实相应的消息值。消息 $D$ 的估计值 $\widehat{D}$ 应是输入 $X(t), 0 \leqslant t \leqslant T$ 的确定函数, 它与消息 $D$ 的取值 $d$

无关，

$$
\widehat {D} = D (X (t)), \quad 0 \leqslant t \leqslant T \tag {15.16-2}
$$

当 $X(t)$ 取不同的现实时， $\widehat{D}$ 也就取相应的不同的值。通常用 $w(x \mid d)$ 来表示信息 $D$ 取 $d$ 值时输入 $X(t)$ 的条件概率密度函数。当 $D$ 取 $d$ 值时估计 $\widehat{D}$ 的条件数学期望是

$$
\overline {{(\hat {D} \mid d)}} = \int_ {- \infty} ^ {\infty} \hat {d} (x) w (x \mid d) d x \tag {15.16-3}
$$

它显然是 d 的函数, 如果 $(\hat{D} \mid d) = d, \hat{D}$ 称为无偏估计。如果消息 D 可以在某个范围内连续地取值, 那么可以证明在 D 取 d 值时任何估计 $\hat{D}$ 都满足不等式

$$
\overline {{[ \hat {D} - d ] ^ {2}}} \geqslant \left[ \frac {\partial}{\partial d} \overline {{(\hat {D} \mid d)}} \right] ^ {2} / \left[ \frac {\partial}{\partial d} \ln w (x \mid d) \right] ^ {2} \tag {15.16-4}
$$

当 $\hat{D}$ 是无偏估计时，

$$
\hat {\sigma} _ {D} ^ {2} = \overline {{[ \hat {D} - d ] ^ {2}}} \geqslant 1 / \left[ \frac {\partial}{\partial d} \ln w (x \mid d) \right] ^ {2} \tag {15.16-5}
$$

当无偏估计 $\hat{D}$ 使式(15.16-5)中的左右两边相等时, 此估计 $\hat{D}$ 就称为有效估计。可以证明, 无偏有效估计是唯一的, 它的充分必要条件是

$$
\frac {\partial \ln w (x \mid d)}{\partial d} = k [ \hat {D} - \overline {{(\hat {D} \mid d)}} ] \tag {15.16-6}
$$

k 是任何不等于零的常数。显然，如果无偏有效估计存在的话，那么这个估计就是最好的。但是，在求有效估计时要计算 $\frac{\partial}{\partial d}\ln(x|d)$ 和 $\left[\frac{\partial}{\partial d}\ln(x|d)\right]^{2}$ ，这通常是比较困难的；另外，有效估计可能不存在，D 可能是未知非随机量或取离散值的随机变量，这时有效估计便失去了意义。所以通常不采用有效估计，而采用其他的估计方法。常用的有下列两种估计方法：

（1）最大事后概率密度函数法：事后概率密度就是已经得到了观测量 $X(t)$ 后再来反算消息 D 的概率密度，也就是当 $X(t)$ 取值 $x(t)$ 时的消息 D 的条件概率密度 $w(d|x(t))$ 。根据全概率公式有

$$
w (d \mid x (t)) = w (x \mid d) w (d) / w (x) \tag {15.16-7}
$$

其中 $w(d)$ 是消息 D 的先验概率密度函数。可选用使 $w(d|x(t))$ 取极大值的 d 作为估计，它是 $x(t)$ 的函数

$$
w (\hat {D} \mid x (t)) = \max _ {d} w (d \mid x (t)) \tag {15.16-8}
$$

这样就得到了 $\hat{D}$ 与 $X(t)$ 的关系, 在运用此种方法时, 消息 D 必须是随机变量, 而且需要知道它的先验概率 $w(d)$ 。如果 D 是连续取值的随机变量, 那么可以按照连续函数求极值的方法求出 $\hat{D}$ 来。

（2）最大似然法：现把消息 D 取 d 值时的观测量 $X(t)$ ， $0 \leqslant t \leqslant T$ 的条件概率密度函数称为似然函数。记为 $L(x(t); d)$

$$
L (x (t); d) = w (x \mid d) \tag {15.16-9}
$$

无论消息 D 是未知的非随机量或是随机变量时, 似然函数 $L(x(t); d)$ 都存在。最大似然法就是对于观测量的一个现实 $x(t)$ 来说, 选取使似然函数取极大值的 d 作为估计 $\hat{D}$ , 对于非随机量来说是 $\hat{d}$ , 因此 $\hat{D}$ 是 $x(t)$ 的函数

$$
\hat {D} (x (t)) = \max _ {d} L (x (t); d) = \max _ {d} w (x \mid d) \tag {15.16-10}
$$

当 $d$ 可以连续变化时

$$
\left. \frac {\partial}{\partial d} L (x (t), d) \right| _ {d = \widehat {D}} = \left. \frac {\partial}{\partial d} w (x \mid d) \right| _ {d = \widehat {D}} = 0 \tag {15.16-11}
$$

按最大似然法求估计时可以不需要知道消息 D 的先验统计特性, 这是它的优点之一。另外可以证明下列事实: 如果对消息 D 存在有效估计 $\hat{D}$ , 那么 $\hat{D}$ 一定是按最大似然法求出的唯一的估计; 如果观测现实 $x(t)$ 的时间趋于无穷, 则按最大似然法求得的估计渐近趋于无偏有效估计, 并且它的分布渐近趋于正态分布。

可以指出最大似然法和最大事后概率密度法二者之间的联系。由公式(15.16-7)可以看出，如果在 $w(x|d)$ 取最大值的 d 值附近的区域内消息 D 的先验概率密度 $w(d)$ 是均匀分布的，那么 $w(d|x)$ 和 $w(x|d)$ 取最大值时的 d 值是相同的。因此，在这种情况下，按这两种方法求出的估计是相同的。

正是由于以上这个特点，最大似然法在信号参数的估计问题中应用得很广泛。下面我们叙述几个按最大似然法估计消息的例子。

例 1. 假定信号 $f_{d}(t)$ 是由消息 d 调制而成

$$
f _ {d} (t) = (1 + m d) B (t)
$$

其中 m 是调制系数， $B(t)$ 是载波，它可能是频率较高的正弦波，也可能是等幅等宽的窄脉冲序列， $B(t)$ 和 m 都是已给定的，消息 d 是个未知的非随机量；噪声 $N(t)$ 是数学期望为零的高斯分布的白色噪声；功率谱密度 $\Phi_{N}(\omega)=N$ ；现在要求由观测 $X(t)=f_{d}(t)+N(t)$ 的一个现实 $x(t),0\leqslant t\leqslant T$ ，来估计消息 d 的值。

根据第 15.15 节中例 1 的讨论不难得到似然函数

$$
\begin{array}{l} L (x (t); d) = w (x (t) \mid d) \\ = K \exp \left\{- \int_ {0} ^ {T} [ x (t) - (1 + m d) B (t) ] ^ {2} d t / 2 \pi N \right\} \\ \end{array}
$$

其中常数 $K$ 可由条件 $\int w(x(t) |d) dx(t) = 1$ 来确定。如果按最大似然法求 $\hat{d}$ ，则

$$
\frac {\partial L (x (t) ; d)}{\partial d}
$$

在 d 等于 $\hat{d}$ 时应等于零，于是有

$$
\begin{array}{l} \widehat {d} = \left[ \int_ {0} ^ {T} x (t) B (t) d t / m \int_ {0} ^ {T} B ^ {2} (t) d t \right] - \frac {1}{m} \\ = \frac {1}{m E} \int_ {0} ^ {T} x (t) B (t) d t - \frac {1}{m} \\ \end{array}
$$

其中 E 是载波 $B(t)$ , $0 \leqslant t \leqslant T$ 载负的功率。只要用最优检测过滤器来得到

$$
\int_ {0} ^ {T} x (t) B (t) d t
$$

就可以得到要求的消息 d 的估计 $\hat{d}$ 。

例 2. 假定消息参数是由脉冲前沿距初始时刻的时间间隔 d 来表示的, 并假定它是未知的非随机量; 信号 $F_{d}(t)$ 是用高频正弦振荡调制的脉冲信号

$$
F _ {d} (t, \Phi) = a (t - d) \cos (\omega t + \Phi)
$$

其中 $\Phi$ 是随机参量，在 0 到 $2\pi$ 内均匀分布， $a(t-d)$ 是已知的脉冲信号

$$
a (t - d) = 0, \text {若} t <   d \text {和} t > d + \sigma
$$

$\sigma$ 为已知的脉冲持续时间， $\omega$ 为已知的高频正弦振荡的频率；噪声 $N(t)$ 仍与例 1 相同；现在要根据观测量 $X(t) = F_{d}(t,\Phi) + N(t)$ 的一个现实 $x(t),0\leqslant t\leqslant T$ ，来估计相应的 $d$ 值。同样，根据第 15.15 节中例 1 和例 2 的讨论不难得到在固定的 $\varphi$ 时的似然函数

$$
\begin{array}{l} L (x (t); d, \varphi) = K \exp \left\{- \frac {1}{2 \pi N} \int_ {0} ^ {T} [ x (t) - a (t - d) \cos (\omega t + \varphi) ] ^ {2} d t \right. \\ = K \exp \left\{- \frac {1}{2 \pi N} \int_ {0} ^ {T} x ^ {2} (t) d t \right\} \exp \left\{- \frac {E}{2 \pi N} \right\} \exp \{\eta (d, \varphi) \} \\ \end{array}
$$

其中

$$
E = \int_ {0} ^ {T} a ^ {2} (t - d) \cos^ {2} (\omega t + \varphi) d t
$$

是信号载负的能量，而

$$
\begin{array}{l} \eta (d, \varphi) = \frac {1}{\pi N} \int_ {d} ^ {d + \sigma} x (t) a (t - d) \cos (\omega t + \varphi) d t \\ = \frac {1}{\pi N} M (d) \cos (\varphi + \theta) \\ \end{array}
$$

式中

$$
M (d) = \sqrt {\left[ \int_ {d} ^ {d + \sigma} x (t) a (t - d) \cos \omega t d t \right] ^ {2} + \left[ \int_ {d} ^ {d + \sigma} x (t) a (t - d) \sin \omega t d t \right] ^ {2}}
$$

似然函数为

$$
L (x (t); d) = \int_ {0} ^ {2 \pi} \frac {1}{2 \pi} L (x (t); d, \varphi) d \varphi
$$

所以

$$
\begin{array}{l} L (x (t); d) = K _ {1} \exp \left\{- \frac {1}{2 \pi N} \int_ {0} ^ {T} x ^ {2} (t) d t \right\} \exp \left\{- \frac {E}{2 \pi N} \right\} \int_ {0} ^ {2 \pi} \exp \left\{\eta (d, \varphi) \right\} d \varphi \\ = K _ {1} \exp \left\{- \frac {1}{2 \pi N} \int_ {0} ^ {T} x ^ {2} (t) d t \right\} \exp \left\{- \frac {E}{2 \pi N} \right\} \cdot I _ {0} \left[ \frac {M (d)}{\pi N} \right] \\ \end{array}
$$

因为 $I_{0}(x)$ 是 x 的单调增加函数, 按最大似然法求得的估计应满足条件

$$
M (\hat {d}) = \max _ {d} M (d)
$$

$M(d)$ 是 $\eta(d, \varphi)$ 的包络线， $\eta(d, \varphi)$ 可以用最优检测过滤器得到，检测过滤器在 $d + \sigma$ 时刻得到最大值。因此将输入 $x(t)$ 通过最优检测过滤器后再通过无惯性检波器，使最后的输出达极大的时刻就是 $\hat{d} + \sigma$ 。

例 3. 假定信号就是消息, 它等于某个未知常数 d; 噪声是平稳随机高斯过程, 数学期望等于零, 相关函数为 $R_{N}(\sigma) = e^{-\lambda^{2}|\sigma|}$ 。现在要根据观测值 $X(t) = d + N(t)$ 的一个现实 $x(t), 0 \leqslant t \leqslant T$ , 来估计消息值 d。用与上节例 3 相同的方法可以求出似然函数

$$
L (x (t); d) = K \exp \left\{\frac {d}{2} \left[ x (0) + x (T) + \lambda^ {2} \int_ {0} ^ {T} x (t) d t \right] - \frac {d ^ {2}}{2} \left(1 + \frac {\lambda^ {2} T}{2}\right) \right\}
$$

K 是与 d 值无关的常数, 可由 $\int_{-\infty}^{\infty} L(x(t); d) dx(t) = 1$ 来决定。根据最大似然法, 估计 $\hat{d}$ 等于

$$
\hat {d} = \frac {1}{2 + \sigma^ {2} T} \left[ x (0) + x (T) + \lambda^ {2} \int_ {0} ^ {T} x (t) d t \right]
$$

可以看出， $d$ 的估计 $\hat{d}$ 与第 15.9 节中例 3 的结果一样。

如果信号中包含两个不同的消息 $D_{1}$ 和 $D_{2}$ ，那么可以按最大似然法求出消息 $D_{1}$ 和 $D_{2}$ 的联合估计 $(\widehat{D}_{1}, \widehat{D}_{2})$ 。这时似然函数 $L(x(t); d_{1}, d_{2})$ 就是当 $D_{1}$ 取 $d_{1}$ 值和 $D_{2}$ 取 $d_{2}$ 值时 $X(t), 0 \leqslant t \leqslant T$ 的条件概率密度函数 $w(x(t) | d_{1}, d_{2})$ 。在给定的观测现实 $x(t), 0 \leqslant t \leqslant T$ 时，消息 $d_{1}$ 和 $d_{2}$ 的联合估计 $(\widehat{D}_{1}, \widehat{D}_{2})$ 应是下列联立方程组的解

$$
\begin{array}{l} \frac {\partial L (x (t) ; d _ {1} , d _ {2})}{\partial d _ {1}} = 0 \\ \frac {\partial L (x (t) ; d _ {1} , d _ {2})}{\partial d _ {2}} = 0 \\ \end{array}
$$

同样，最大似然法可以推广到对任意 n 个消息的估计。在有多个消息存在时，只估计一个消息而不估计其他消息并不会提高此消息估计的准确程度。例如，在雷达的回波信号中估计距离和目标的径向速度，如果只估计距离而不去估计目标的径向速度就不能提高估计距离的准确性。

#### 15.17 一般的最优过滤问题

本章讨论了各种准则的最优过滤问题，如信号的最优复现，信号的最优检测和信号参数的最优估计等。究竟采用什么准则要由具体的工程问题的要求来确定。实际上可以把大部分已有的准则归结为一般的准则。

假定系统的观测量是有用信号 $F(t)$ 和噪声的叠加

$$
\boldsymbol {X} (t) = \boldsymbol {F} (t) + \boldsymbol {N} (t)
$$

在一般情况下，可以认为噪声是数学期望为零的平稳随机过程。有用信号 $F(t)$ 是时间 t 的随机函数，它也是消息和某些参数的确定函数，其中有些部分可能是随机的，也可能是未知的非随机量或非随机函数。通常信号 $F(t)$ 表示为

$$
\boldsymbol {F} (t) = \boldsymbol {f} (t, \boldsymbol {D} (t), \Phi (t)) \tag {15.17-1}
$$

$D(t)=(D_{1}(t),\cdots,D_{r}(t))$ 为消息， $\Phi(t)=(\Phi_{1}(t),\cdots,\Phi_{m}(t))$ 为参数。我们要求在系统的输出端得到某些消息或对这些消息进行某种运算后的结果的估计。理想输出可以表示为对信息进行某种已知运算的结果

$$
\mathbf {Y} _ {1} (t) = \mathbf {g} (\mathbf {D} (t)) \tag {15.17-2}
$$

系统的实际输出 $Y(t)$ 是对观测量 $X_{1}(t)$ 进行某种可实现的运算结果, 它可以表示成函数关系

$$
\boldsymbol {Y} (t) = \boldsymbol {h} \{X (t) \} \tag {15.17-3}
$$

实际上，系统的输出 $Y(t)$ 总是和理想输出 $Y_{1}(t)$ 有差别的，我们用损耗函数 $l(Y_{1},Y)$ 来度量这种差别，它是理想输出 $Y_{1}$ 和实际输出 Y 的某个确定的函数（泛函）或条件确定函数（泛函)。对于理想输出 $Y_{1}(t)$ 取某个值 $y_{1}(t)$ 时损耗函数的条件数学期望称为条件风险，它只依赖于 $Y_{1}(t)$ 的取值 $y_{1}(t)$ 和确定实际输出的运算 h。条件风险定义为

$$
r (\boldsymbol {h} \mid \mathbf {y} _ {1}) = \overline {{\left[ l \left(\mathbf {Y} _ {1} , \mathbf {Y}\right) \mid Y _ {1} = y _ {1} (t) \right]}} \tag {15.17-4}
$$

理想输出 $Y_{1}(t)$ 是随机函数时的条件风险 $r(\boldsymbol{h}|\boldsymbol{Y}_{1})$ 的数学期望称为平均风险, 它只依赖于运算 h

$$
r (\boldsymbol {h}) = \overline {{\left[ R \left(\boldsymbol {h} \mid \boldsymbol {Y} _ {1}\right) \right]}} = \overline {{\left[ l \left(\boldsymbol {Y} _ {1} , \boldsymbol {Y}\right) \right]}} \tag {15.17-5}
$$

实际上平均风险 $r(\boldsymbol{h})$ 就是损耗函数 $l(\mathbf{Y}_{1},\mathbf{Y})$ 的无条件数学期望。一般的最优过滤问题就是要选择运算 h 使得相应于某个损耗函数的平均风险取最小值，或者使在某种限制条件下相应于某个（条件损耗）函数的条件平均风险取最小值。几乎所有的统计准则都是这种一般准则的个别情况。下面我们就列举出相应于某些统计准则的损耗函数或条件损耗函数

(1) 均方误差最小准则: 这时取

$$
l (\mathbf {Y} _ {1}, \mathbf {Y}) = (\mathbf {Y} _ {1} - \mathbf {Y}) ^ {\tau} (\mathbf {Y} _ {1} - \mathbf {Y}) \tag {15.17-6}
$$

因此

$$
\min _ {h} r (\boldsymbol {h}) = \min _ {h} \overline {{(\boldsymbol {Y} _ {1} - \boldsymbol {Y}) ^ {\tau} (\boldsymbol {Y} _ {1} - \boldsymbol {Y})}}
$$

(2) 误差的范数不超过某个给定函数的概率最大准则: 这时取

$$
l \left(\mathbf {Y} _ {1}, \mathbf {Y}\right) = \left\{ \begin{array}{l l} 0, & | \mathbf {Y} _ {1} - \mathbf {Y} | \leqslant \varphi (t) \\ 1, & | \mathbf {Y} _ {1} - \mathbf {Y} | > \varphi (t) \end{array} \right. \tag {15.17-7}
$$

因此

$$
\min _ {h} r (\boldsymbol {h}) = \min _ {h} p \left\{\mid \boldsymbol {Y} _ {1} - \boldsymbol {Y} \mid > \varphi (t) \right\} = \max _ {h} p \left\{\mid \boldsymbol {Y} _ {1} - \boldsymbol {Y} \mid \leqslant \varphi (t) \right\}
$$

（3）信号检测时差错的全概率最小准则：假设 $Y_{1}$ 只取 0 和 1 两种值，如果根据实际观测而得的 $Y \geqslant \beta$ ，则认为信号是 1，如 $Y < \beta$ ，则认为信号为 0。这时取

$$
l (Y _ {1}, Y) = \left\{ \begin{array}{l l} 0, & \{Y _ {1} = 0, Y <   \beta \} \text {或} \{Y _ {1} = 0, Y \geqslant \beta \} \\ 1, & \{Y _ {1} = 0, Y \geqslant \beta \} \text {或} \{Y _ {1} = 1, Y <   \beta \} \end{array} \right. \tag {15.17-8}
$$

因此

$$
r (\boldsymbol {h}) = p \left\{Y _ {1} = 0, Y \geqslant \beta \right\} + p \left\{Y _ {1} = 1, Y <   \beta \right\} = p _ {0}
$$

$p_{0}$ 就是发生差错的全概率, $r(\boldsymbol{h})$ 取最小值也就是发生差错的最小全概率。

（4）诺曼-皮尔生准则：要求虚警概率不超过某个值时漏警概率最小。从第 15.15 节可知，当漏警概率最小时，虚警概率应该取它上限。因此诺曼-皮尔生准则就化为在虚警概率 $P\{Y \geqslant \beta | Y_1 = 0\} = \alpha$ 时，差错全概率 $p_0$ 最小的条件极值问题。这时取

$$
l (Y _ {1}, Y) = \left\{ \begin{array}{l l} 0, & \{Y _ {1} = 1, Y \geqslant \beta \} \text {或} \{Y _ {1} = 0, Y <   \beta \} \\ \lambda , & \{Y _ {1} = 0, Y \geqslant \beta \} \\ 1, & \{Y _ {1} = 1, Y <   \beta \} \end{array} \right. \tag {15.17-9}
$$

其中 $\lambda$ 是拉格朗日不定乘子。如果 $Y_{1} = 1$ 的先验概率是 $p, Y_{1} = 0$ 的先验概率是 $q = 1 - p$ ，那么

$$
\begin{array}{l} r (\boldsymbol {h}) = \overline {{\left[ l (Y _ {1} , Y) \right]}} = p \{Y _ {1} = 1, Y <   \beta \} + \lambda \cdot p \{Y _ {1} = 0, Y \geqslant \beta \} \\ = p \cdot p \{Y <   \beta \mid Y _ {1} = 1 \} + q \cdot p \{Y \geqslant \beta \mid Y _ {1} = 0 \} + (\lambda - 1) q \\ \bullet p \{Y \geqslant \beta \mid Y _ {1} = 0 \} \\ = p _ {0} + \lambda_ {1} p \{Y \geqslant \beta \mid Y _ {1} = 0 \} \\ \end{array}
$$

其中 $\lambda=(1-\lambda)q$ 也是不定乘子， $p_{0}$ 是发生差错的全概率。因此平均风险最小也就是在 $p\{Y\geqslant\beta|Y_{1}=0\}=0$ 条件下差错全概率最小。不定乘子 $\lambda$ 或 $\lambda_{1}$ 应在找到最小值后再从条件 $p\{Y\geqslant\beta|Y_{1}=0\}=\alpha$ 来确定。

（5）事后概率最大准则：它要求对观测量 $X(t)$ 的任意给定的现实 $x(t)$ ，条件概率密度 $w(y_{1} \mid x)$ 在 $y_{1} = y$ 时取最大值。这时只要令

$$
l (Y _ {1}, Y) = c - \delta (Y _ {1} - Y) \tag {15.17-10}
$$

即可，其中 c 为任意常数。这种损耗函数的平均风险为

$$
r (\boldsymbol {h}) = \overline {{\left[ l (Y _ {1} , Y) \right]}} = c - \iint \delta (y _ {1} - y) w (y _ {1}, y) d y _ {1} d y
$$

因为输出 y 是运算 h 对输入 $x(t)$ 作用的结果, 所以

$$
\begin{array}{l} r (\boldsymbol {h}) = c - \iint \delta (y _ {1} - \boldsymbol {h} \{x \}) w (y _ {1}, x) d y _ {1} d x \\ = c - \int w (x) d x \int \delta \left(y _ {1} - \boldsymbol {h} \{x \}\right) w \left(y _ {1} \mid x\right) d y _ {1} \\ = c - \int w (x) w (y \mid x) d x \\ \end{array}
$$

因为 $w(x) \geqslant 0$ ，所以当， $r(\boldsymbol{h})$ 取极小值时 $w(y|x)$ 取最大值，这意味着事后概率密度 $w(y_{1}|x)$ 在 $y_{1} = y$ 时取最大值。

（6）最大似然法：它要求对观测量 $X(t)$ 的一个现实 $x(t)$ ，条件概率密度 $w(x|y_1)$ 在 $y_1 = y$ 时取极大值。这时令

$$
l (Y _ {1}, Y) = c - \delta (Y _ {1}, Y) \tag {15.17-11}
$$

其中 $c$ 为任意常数。这种损耗函数的条件风险为

$$
\begin{array}{l} r (\boldsymbol {h} \mid y _ {1}) = \int l (y _ {1}, y) w (x \mid y _ {1}) d y _ {1} \\ = c - \int \delta \left(y _ {1} - y\right) w \left(x \mid y _ {1}\right) d y _ {1} \\ = c - w (x \mid y) \\ \end{array}
$$

当条件风险 $R(\boldsymbol{h} \mid y_{1})$ 取极小值时，输出 y 就满足最大似然法的条件。

对应于所有可能的损耗函数 $l(Y_{1}, Y)$ (它还可能包含某些待定参数) 的平均风险 $r(h)$ 最小的准则通常称为贝叶斯准则。显然，为了按贝叶斯准则确定最优过滤系统，必须知道信号和噪声的所有统计特性。而对某些个别的准则才可能只利用信号和噪声的局部统计特性。如果只知道相对于理想输出 $Y_{1}$ 的观测值 $X(t)$ 的条件概率特性，而 $Y_{1}$ 的概率特性不知道，那么最优过滤问题只能按最大似然法来设计或者按极小极大准则来设计。极小极大准则就是要保证系统在最坏可能的条件下最好地工作，即使所有可能的 $Y_{1}$ 的现实的条件风险值中最大者达极小值

$$
\min _ {\boldsymbol {h}} \max _ {\boldsymbol {y} _ {1}} r (\boldsymbol {h} \mid \boldsymbol {y} _ {1})
$$

这种准则对于某类系统的设计特别有用，例如，用导弹去攻击作机动飞行的敌机时，敌机总想作某种机动使导弹击中它的概率减小，这时导弹的控制系统应这样设计使得在敌机作最坏的机动时仍能使导弹尽可能准确地接近它。

一般来讲，在相同的条件下，按不同的准则设计出来的最优运算 h 或最优过滤器将不相同。但是在个别的情况下，也可能同一个过滤器对好几种准则都是最优的。这里特别要指出，按第 15.3 节到第 15.13 节的方法设计出来 的线性过滤器，如果随机信号和随机噪声是正态分布它不仅对均方误差最小的准则是最优的，而且对于以 $|Y_1 - Y|$ 为变量的任意非降损耗函数的平均风险最小准则来说，它也是最优的，并且对于事后概率密度最大的准则来说也是最优的。

#### 15.18 参考文献

[1] 江泽培, 1) 多维平稳过程的预测理论, 数学学报, 13(1963), 2.  
2) On the estimation of regression coefficient of a continuous parameter time series with a stationary residual., Теория Вероятн. и её Примен., 4(1959), 4.  
3) О линейной экстрополяции непрерывного однородного поля, Теория Вероятн. и её Примен., 2(1957), 1.

[2] 王传善, 弱干扰下连续远动信号的最佳接收, 自动化学报, 2(1964), 2.

[3] 安鸿志, 加权滤波方法, 数学的实践和认识, 1973, 4.

[4] 安鸿志, 严加安, 限定记忆滤波方法, 数学的实践和认识, 1973, 4.

[5] 中国科学院数学研究所概率组编, 离散时间系统滤波的数学方法, 国防工业出版社, 1975.

[6] 陈翰馥, 关于随机能观测性, 中国科学, 1976, 7.

[7] Athans, M., The role and use of the stochastic linear-quadraticness problem in control system design, IEEE Trans., AC-16(1971). Dec., 529–552.

[8] Bode, H. W., Shannon, C. E., A simplified derivation of linear least square smoothing and prediction theory, Proc. IRE, 38(1950), April 417–425.

[9] Bokesembom, A.S., Novik, D., Optimum controllers for linear closed-loop systems, NACA TN. 2939, 1953.

[10] Booton, R. C., An optimization theory for time-varying linear system with non-stationary statistical inputs, Proc. IRE, 40(1952), 977-981.

[11] Chang S. S. L., Synthesis of Optimum Control Systems, Mc-Graw Hill Book Co. Inc., 1961.

[12] Deustch, R., Estimation Theory, Prentice-Hall. Inc., Englewood Cliffs, N.J., 1968.

[13] Flanklin, G., Linear filtering of sampled-data, IRE Conv. Record, 1955. pt. 4, 119–128.

[14] Helstron, C. W., Statistical Theory of Signal Detection, Pergamon. New York, 1960. (信号检测的统计理论, 陈宗骘译, 上海科技出版社, 1965.)

[15] James, H. F., Nichols, N. B., Phillips, R. S., Theory of Seruomechanisms, Chap. 7, M. I. T. Radiation Laboratory Series, 25, McGraw-Hill Book Co. Inc., New York, 1947.

[16] Kailath, T., An innovations approach to least squares estimation IEEE Trans., AC-13 (1968), Dec., 646–660.

[17] Kalman. R. E., A new results to linear filtering and prediction problems, ASME Trans. Series D, 82(1960), 35–45.

[18] Kalman, R. E., Bucy, R. S., New results in Linear filtering and prediction theory, ASME Trans. Series D, 83(1961), 95–108.

[19] Laning, J. H., Battin, R. H., Random Processes in Automatic Control, McGraw-Hill Book Co., Inc., New-York, 1956. (自动控制中的随机过程, 涂其例译, 科学出版社, 1963.)

[20] Lawson, J. L., Uhlenbeck, G. E., Threshold Signals, MIT Radiation Laboratory Series Vol. 26. McGraw-Hill Book Co., Inc., New York, 1950.

[21] Meditch, J.S., Stochastic Optimal Linear Estimation and Control, McGraw-Hill Book Co., Inc., New York, 1969.

[22] Paley, R. E. A. C., Wiener, N., Fourier transforms in the complex domain, Amer. Math. Soc. Colleqium 19(1934), 17.

[23] Pelegrin, M.J., Calcul Statistique des Systèmes Asservis, Paris, 1953. (随动系统的统计计算, 涂其俐等译, 科学出版社, 1960.)

[24] Person, W. W., Birdsall, T. G., Fox. W. C., The theory of signal detectability, IRE Trans., PGIT-4(1954), 171–212.

[25] Sage, A. P., Melsa, J. L., Estimation Theory with Applications to Communications and Control. McGraw-Hill, 1971. (估计理论及其在通讯与控制中的应用, 田承骏、唐策善等译, 科学出版社, 1978.)

[26] Slepin, D., Estimation of signal parameter in the presence of noise. IRE Trans., PGIT-3 (1954), march, 68–69.

[27] Sorenson, H. W., On the behavior in Linear minimum variance estimation problems, IEEE Trans., AC-12(1967), Oct., 557–562.

[28] Turn, T. J., Zaborszky, J., A pratical nondiverging filter, AIAA J. 8 (1970), 6, 1127-1133.

[29] Wiener, N., The Extrapolation, Interpolation and Smoothing of Stationary Time Series with Engineering Applications, John Wiley & Sons, Inc., New York, 1949.

[30] Wonham, W. M. On the separation theorem of stochastic control, SIAM J. Control 6 (1968), 312-326.

[31] Zadeh, L. A., Ragazzini, J. R., 1) An extension of Wiener's theory of prediction, J. Appl. Phs., 21(1950), July, 645–655. 2) Optimum filters for the detection of signals in noise, Proc. IRE 40 (1952), Oct., 1223–1231.

[32] Колмогоров, А. Н., Интерполирование и экстраполирование стационарных случайных последовательностей, Изв АН СССР, отэеленце Мат., 5(1941). 3—14.

[33] Леонов, Ю. П., О приближенном метода синтеза оптимальных линейных систем для выделения полезного сигнал из шума, Aut, 20(1959), 8.

[34] Перов, В. П., Статистический Синтез Импульных Систем, Советском Радио, 1959.

[35] Пугачев, В. С., Теория Случайных Процессов и её Применение к Задачам Автоматического Управления, издание второе, Физматгиз, 1960. (随机过程理论及其在自动控制中的应用, 田欣为等译, 科学出版社, 1966.)

[36] Яглом, А. М., 1) Экстраполирование, интеполнрование и фильтрация стационарных случайных процессов с рациональной спектральной плотностью, Трулы Москвы. Матем. Общества, 4, 1955. (具有有理谱密度的平稳随机过程的外推, 内插和平滑, 数学进展, 2 (1956), 2.)   
2) Введение в теории стационарных случайных функций, Успехи Мат. Наук, 7(1952), 5.
   (平稳随机函数引论, 梁之舜译, 数学进展, 2(1956), 2.)
