# 工程控制论（上册）

（第三版）

钱学森 宋健 著

## 正文（005）

### 第五章 线性控制系统参数设计

上一章的主要内容是分析问题，即给定了系统的运动方程式后，用解析方法去评价它的各种动态和稳态性能，那里基本上没有涉及系统的设计方法。设计问题（或称之为综合问题）的含义是当受控对象的运动方程给定时，按预定的动态或其他品质指标要求，求出控制装置的运算形式或控制规律。这一章内我们将自简至繁地介绍线性系统的设计方法。这里将主要研究线性常系数微分方程式所描述的受控系统的设计。并且假定控制规律也是线性的。设运动方程式为

$$
a _ {n} \frac {d ^ {n} x}{d t ^ {n}} + a _ {n - 1} \frac {d ^ {n - 1} x}{d t ^ {n - 1}} + \dots + a _ {1} \frac {d x}{d t} + a _ {0} x = b u \tag {5.0-1}
$$

式中 x 为受控量, u 为对象的控制量。在必要时, 我们也将式(5.0-1)写成一阶向量方程式

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u} \tag {5.0-2}
$$

向量 $\boldsymbol{x}=(x_{1},\cdots,x_{n}); x_{i}=\frac{d^{i-1}x}{dt^{i-1}}$ ; 矩阵 A 的元素与式(5.0-1)诸系数的关系前章内已讨论过。式(5.0-2)的控制向量 u 可能只含一个分量, 如式(5.0-1)那样, 此时矩阵 B 只含一列元素, 因此可看成是一个常向量。当给定输入作用 $\boldsymbol{g}(t)$ 后, 式(5.0-2)可写成对误差 $\varepsilon(t)$ 的微分方程式

$$
\frac {d \varepsilon}{d t} = A \varepsilon - B u + \left[ \frac {d g}{d t} - A g \right] \tag {5.0-3}
$$

控制系统的设计任务是找出控制规律

$$
\boldsymbol {u} (\varepsilon) = C \varepsilon
$$

或者

$$
u _ {i} \left(\varepsilon_ {1}, \dots , \varepsilon_ {n}\right) = \sum_ {\alpha = 1} ^ {n} c _ {i \alpha} \varepsilon_ {\alpha}, \quad i = 1, 2, \dots , r \tag {5.0-4}
$$

使方程式(5.0-3)自任何初始条件开始运动均能使误差 $\varepsilon(t)$ 趋于零。方程式(5.0-1)的待求控制规律的形式是

$$
u \left(\varepsilon_ {1}, \dots , \varepsilon_ {n}\right) = \sum_ {\alpha = 1} ^ {n} c _ {\alpha} \varepsilon_ {\alpha}
$$

$c_{a}$ 称为反馈系数, 其中某些系数可能为零, 而 $\varepsilon_{a}=\frac{d^{\alpha-1}\varepsilon}{dt^{\alpha-1}}$ 。当输入作用属于固有类时（见前章), 式(5.0-3)与(5.0-2)重合。如果系统的任务是稳定零解, 则上面各

式内的误差 $\varepsilon_{i}$ 均将换为系统的坐标 $x_{i}$ 。

具有式(5.0-4)形式控制规律的控制系统我们称之为线性反馈控制系统，因为控制量是误差的线性函数。下面我们将介绍几种设计控制装置的方法，即根据各种不同的要求确定线性控制规律中的诸系数 $c_i$ 。

应该指出，线性控制规律并不是对一切品质指标都能成为最好的形式，对特定的某些品质指标这种规律确实很不错，正确选择系数，能使系统达到最理想的程度。但是，一般讲来，最好的控制装置并不是线性的。关于非线性控制装置的设计我们将在以后详细讨论。由于线性系统设计容易，装置简单，设备不复杂，所以目前采用的很多，在这里详细介绍几种设计方法是有现实意义的。

#### 5.1 稳定区域

在线性控制系统的设计中，首先关心的是如何保证系统的稳定性，即学会正确选择控制规律式(5.0-4)中的反馈系数以保证系统稳定。因为常系数系统的运动稳定性与输入作用无关，故只研究式(5.0-3) $g(t)\equiv0$ 的情况就够了。

现在研究系统式(5.0-1)。设控制装置的运算规律是

$$
b u = - b \left(h _ {1} x _ {1} + \dots + h _ {n} x _ {n}\right) = - c _ {1} x _ {1} - \dots - c _ {n} x _ {n} \tag {5.1-1}
$$

代入式 $(5.0-1)$ 后有

$$
a _ {n} \frac {d ^ {n} x}{d t ^ {n}} + \left(a _ {n - 1} + c _ {n}\right) \frac {d ^ {n - 1} x}{d t ^ {n - 1}} + \left(a _ {n - 2} + c _ {n - 1}\right) \frac {d ^ {n - 2} x}{d t ^ {n - 2}} + \dots + \left(a _ {0} + c _ {1}\right) x = 0 \tag {5.1-2}
$$

显然，欲使式(5.1-2)稳定，必须正确地确定诸反馈系数 $c_{i}$ ，使特征方程

$$
a _ {n} s ^ {n} + \left(a _ {n - 1} + c _ {n}\right) s ^ {n - 1} + \dots + \left(a _ {0} + c _ {1}\right) = 0 \tag {5.1-3}
$$

的一切根均有负实部。

当一组 $c_{i}$ 已给定后，方程式(5.1-3)的根也唯一地被确定，若令 $c_{i}$ 连续变化，则这些根也随之连续变化，因为代数方程式的根是其系数的连续函数。现将 $(c_{1}, c_{2}, \cdots, c_{n})$ 看成是 n 维空间 $R_{n}$ 中的点，于是 $R_{n}$ 中每一个点 c 对应一组根。在 $R_{n}$ 内的一切使式(5.1-3)的所有 n 个根均有负实部的点的集合记为 $D(n)$ ，在很多情况下后者构成一个区域，称之为线性系统的稳定区域。如果能用简便的办法找出这个区域 $D(n)$ ，那么线性系统的设计便得到初步解决。继之，可以设想， $R_{n}$ 内共有 $n+1$ 个不同类型的区域 $D(0), D(1), \cdots, D(n)$ ，在 $D(m)$ 中的所有点 c 使式(5.1-3)有 m 个具有负实部的根，在 $D(0)$ 内的点使一切根均有正实部，如此等等。如何找到 $D(n)$ 就是我们的任务。

上一章介绍过的艾文思方法解决了这个问题的一部分，即当可变的参数只有一个（系统的放大系数）时，用它可以求出足以保证系统稳定的放大系数的变化 范围。但是，当可变参数大于一个时，艾文思方法就难以使用了。本节所介绍的稳定区域的方法首先在文献[24]内曾详细的阐述过。

我们先从一维参数空间开始讨论。假定式(5.1-3)内除一个参数以外，例如 $c_{i}=c$ ,其他都为零。这时式(5.1-3)可改写成

$$
P (s) + c Q (s) = 0 \tag {5.1-4}
$$

或者

$$
c = - \frac {P (s)}{Q (s)}
$$

将 $s=i\omega$ 代入上式后, 再将等式右端分成实部和虚部

$$
c = U (\omega) + i V (\omega) \tag {5.1-5}
$$

为了讨论方便，我们暂且令参数 $c$ 可取复值，即它可取值于一个复平面内（图 5.1-1）。不难看出，如果多项式 $Q(s)$ 在 $S$ 平面之虚轴上及其附近没有零点，那么式(5.1-5)是将 $S$ 平面内之虚轴保角映射至 $c$ 平面。当 $s$ 沿虚轴历遍 $(-i\infty, i\infty)$ 时，在 $c$ 平面上出现一条连续曲线 $c(i\omega)$ 。由于 $U(\omega)$ 是自变量的偶函数， $V(\omega)$ 是奇函数，故曲线 $c(i\omega)$ 对实轴对称，故只需画出 $\omega$ 自 0 至 $+\infty$ 的一半就够了，另外一半可用镜面反射的方法画出（图 5.1-1)。显然，当参数 $c$ 取值于这条曲线上任何点时，特征方程式(5.1-4)至少有一对纯虚根。例如曲线 $c(i\omega)$ 上的点 $\eta$ 满足方程式

$$
P (i \omega_ {0}) + \eta Q (i \omega_ {0}) = 0
$$

如果式(5.1-4)是第一类保角变换（即保持曲线走向的保角变换),那么 S 平面上虚轴附近之左半平面将变至 c 平面上之曲线 $c(i\omega)$ 之左旁，图 5.1-1 内有斜线标出之部分便是。顺便提一句，变换式(5.1-4)是否是第一类，在作图时立刻可以觉察出来。

> 此处省略原书 **图 5.1-1**

相应地选择式(5.1-4)内之 c 值, 可以使 S 平面上的任何点, 例如 $s_{1}$ 点, 成为特征方程式的根。要使图 5.1-1 内之 $s_{1}$ 点成为特征方程式的根, 只需令

$$
c = - \frac {P (s _ {1})}{Q (s _ {1})}
$$

即可。设在 $S$ 平面内有一通过 $i\omega_0$ 点的曲线段 $s_1 s_2$ ，它的对应的影像在 $C$ 平面上是 $c_1 c_2$ ，后者通过 $\eta$ 点。由于保角变换的特性，若 $s_2$ 位于虚轴之右边，与其相应的点 $c_2$ 必也位于曲线 $C(i\omega)$ 的右边。由此可以断言，在图 5.1-1 中的 $C$ 平面上，区域 Ⅱ 内之任何 $c$ 值确定的具有负实部根的个数比区域 I 多一个。同理，区域 Ⅲ 内的点所确定的负实部根的个数又比区域 Ⅱ 多一个。这样，如果区域 I 属于 $D(m)$ ，那么 Ⅱ 区属于 $D(m + 1)$ ，Ⅲ 区则属于 $D(m + 2)$ 。在绝大多数情况下，根据特征方程式的阶数，曲线 $C(i\omega)$ 一旦画出，马上可以判定各个 $D(m)$ 的位置。例如，设方程式(5.1-4)为三阶代数方程，图 5.1-1 内之曲线是相应的虚轴变换的象。从图中马上可以看出区域 Ⅲ 属于 $D(3)$ ，区域 Ⅱ 属于 $D(2)$ ，区域 I 则属于 $D(1)$ 。因此，区域 Ⅲ 是系统对参数 $c$ 的稳定区域，这里任何点 $c$ 所确定的特征方程的一切根均具有负实部。在讨论中曾经假定 $c$ 可以取复值，实际上它只能取实数值。于是，参数 $c$ 只能取值于 Ⅲ 区内之实轴线段 $ab$ 上，端点 $a$ 和 $b$ 不包括在内，因为当 $c = a$ 或 $c = b$ 时特征方程有一对纯虚根，系统位于稳定的边缘。

这种用区域划分的方法去确定保证系统稳定的参数取值范围，对选定系统放大系数或其他关键参数是很方便的，因为能求出该参数可能取值的全体。如果某参数已经选定，这种方法也提供一种检验系统稳定性的手段。例如，可以求出已确定的该参数值离临界值差多远，从而判断系统稳定性对参数变化的敏感程度等。这种方法还可以推广到多参数稳定域选择问题。但是如果待选定的参数超过两个，这种方法实际上便很难应用，对两个参数的情况，用作图法仍然能得到较好的效果。对这种情况的稳定域划分可参看本章所列参考文献[24]。

#### 5.2 对数频率法

在前章内我们曾详细讨论了利用对数频率法（伯德法）去分析系统稳定性的原理。在分析理论的基础上，对数频率法也可以用以设计（综合）线性控制系统。设受控对象的频率特性是

$$
W (i \omega) = \frac {X (i \omega)}{U (i \omega)} = K \frac {\left(P _ {1} e ^ {i \varphi_ {1}}\right) \left(P _ {2} e ^ {i \varphi_ {2}}\right) \cdots \left(P _ {m} e ^ {i \varphi_ {m}}\right)}{\left(Q _ {1} e ^ {i \theta_ {1}}\right) \left(Q _ {2} e ^ {i \theta_ {2}}\right) \cdots \left(Q _ {n} e ^ {i \theta_ {n}}\right)} \tag {5.2-1}
$$

式中 $P_{i}, Q_{j}$ 均为实变数 $\omega$ 的函数。上式取对数为

$$
2 0 \log W (i \omega) = 2 0 \log | W (i \omega) | + i (2 0 \log e) \left[ \sum_ {j = 1} ^ {m} \varphi_ {j} - \sum_ {j = 1} ^ {n} \theta_ {j} \right]
$$

上式右端之第一项是对数幅频特性，第二项是对数相频特性，将它们分别画于图 5.2-1 中。相频特性将直接画出 $\theta=\sum_{j=1}^{m}\varphi_{j}(\omega)-\sum_{j=1}^{n}\theta_{j}(\omega)$ 。如果对数频率特性满

足伯德稳定条件，即相稳定裕度 $\theta_{0}$ 和幅稳定裕度 $M_{0}$ 为足够大时，那么可直接采用控制规律 u = -x，即用简单的反馈（这种反馈常称为“硬反馈”）得到的控制系统一定是稳定的。但是，一般讲来，这种简单的反馈并不能保证反馈系统稳定和具有良好的动态性能。设受控对象的对数频率特性如图 5.2-1 所示，对于这个受控对象利用简单的反馈是行不通的，因为当 $20\log|W|=0$ 时相角小于 $-\pi$ ，为了使控制系统能正常工作，必须借助于更复杂的控制规律。

> 此处省略原书 **图 5.2-1**

设采用控制规律

$$
u = - (c _ {1} s + 1) x \tag {5.2-2}
$$

令 $u_{1} = -x$ ，有 $u = (c_{1}s + 1)w_{1}$ 。于是，新的传递函数是

$$
W _ {1} (i \omega) = \frac {X (i \omega)}{U _ {1} (i \omega)} = (c _ {1} i \omega + 1) W (i \omega) \tag {5.2-3}
$$

我们知道，环节 $(ic_{1}\omega+1)$ 的对数幅频特性是

$$
2 0 \log \sqrt {c _ {1} ^ {2} \omega^ {2} + 1} = 1 0 \log (c _ {1} ^ {2} \omega^ {2} + 1)
$$

它在 $\omega_{1}=\frac{1}{c_{1}}$ 点以前以零分贝为渐近线，在 $\omega_{1}=\frac{1}{c_{1}}$ 以后则以 20 分贝/旬频程的斜率上升。它的相特性是在 $\omega\ll\omega_{1}$ 时以 0 为其渐近线，当 $\omega=\omega_{1}$ 时 $\theta=\frac{\pi}{4}$ ，而 $\omega\to\infty$ 时， $\theta\rightarrow\frac{\pi}{2}$ 。将 $(ic_{1}\omega+1)$ 的对数幅频特性与 $20\log|W(i\omega)|$ 相加，再将前者和后者的相频特性 $\theta$ 相加，便得到新的对数频率特性，如图 5.2-1 虚线所示之 $20\log|W_{1}|$ 和 $\theta_{1}(\omega)$ 。采用了控制规律式(5.2-2)后，可以看到，利用 $u_{1}=-x$ 的 简单反馈（即 $u=-(c_{1}s+1)x$ )，反馈控制系统已获得足够的相稳定裕度 $\theta_{0}$ 和幅稳定裕度 $M_{0}$ 。用这种方法设计出的控制系统的结构如图 5.2-2 所示。

> 此处省略原书 **图 5.2-2**

当采用控制规律式(5.2-2)控制系统依然不能获得良好的稳定性能时，可采用更为复杂的规律，例如

$$
u = - \left(c _ {1} s ^ {2} + c _ {2} s + 1\right) x \tag {5.2-4}
$$

或者

$$
u = - \left(c _ {1} s ^ {3} + c _ {2} s ^ {2} + c _ {3} s + 1\right) x \tag {5.2-5}
$$

等。如果式(5.2-4)或(5.2-5)之右端可分解为一次单因子之乘积，每一个因子又具有式(5.2-2)的形式，那么对这类控制系统的作图方法与前述无异。只需在 $20\log|W|$ 的对数幅频特性和相频特性上加上诸单因子的对数幅频特性和相频特性后，算出相稳定裕度和幅稳定裕度即可。

如果对控制系统的动态特性要求已经给定，例如对过渡过程的时间和过渡过程的超调量已经提出要求，也可以根据经验公式和近似计算方法做出需要的开路系统的理想对数频率特性图，然后再取理想频率特性和受控对象频率特性的差作为控制装置的频率特性，以此选择式(5.2-4)或(5.2-5)内的系数 $c_{i}$ ，使其尽量接近需要的形式。至于如何估计对数频率特性与反馈系统动态性能之间的关系，什么样的对数频率特性才是理想的，这些问题至今没有确切的答案。在文献[27]中曾做了近似估计，并提出了一些经验性的计算方法，感兴趣的读者可以参阅。

#### 5.3 复合控制系统与稳态补偿

至今我们研究过的各类系统都是按误差进行控制的系统，也就是说，控制量仅仅是系统误差坐标的线性函数，而与输入作用 $g(t)$ 无关。这样做的根据是系统的稳定性与输入作用无关，而仅与系统的坐标反馈方式有关，而且当输入作用属于固有类时（参看第四章，第 4.8 节），系统对输入作用 $g(t)$ 的跟踪精度也与控制装置无关。但是，当输入作用不属于固有类时，系统必然不能准确地跟踪输入作用。误差 $\varepsilon(t)$ 将与输入 $g(t)$ 有关，其关系式是式(4.8-14)。除输入作用外，在受控对象上还可能有外扰作用 $f(t)^{[4]}$ ，后者的作用点常与输入作用 $g(t)$ 的作用点不 同。现写出图 5.3-1 所示系统的运动方程式：

> 此处省略原书 **图 5.3-1**

$$
\begin{array}{l} T \frac {d ^ {2} x}{d t ^ {2}} + \frac {d x}{d t} = y + f (t) \\ \frac {d y}{d t} = u \\ \varepsilon = g (t) - x (t) \tag {5.3-1} \\ \end{array}
$$

令 $x = x_{1}\frac{dx}{dt} = x_{2},y = x_{3}$ ，代入上式后得到一个一阶方程组：

$$
\begin{array}{l} \frac {d x _ {1}}{d t} = x _ {2} \\ \frac {d x _ {2}}{d t} = - \frac {1}{T} x _ {2} + \frac {1}{T} x _ {3} + \frac {1}{T} f (t) \\ \frac {d x _ {3}}{d t} = u \\ \varepsilon = g (t) - x _ {1} \\ \end{array}
$$

再令 $\varepsilon_1 = g(t) - x_1(t),\varepsilon_2 = \frac{dg}{dt} -\frac{dx_1}{dt},\varepsilon_3 = x_3$ ，代入上式，有

$$
\begin{array}{l} \frac {d \varepsilon_ {1}}{d t} = \varepsilon_ {2} \\ \frac {d \varepsilon_ {2}}{d t} = - \frac {1}{T} \varepsilon_ {2} - \frac {1}{T} \varepsilon_ {3} + h (t) - \frac {1}{T} f (t) \tag {5.3-2} \\ \frac {d \varepsilon_ {3}}{d t} = u \\ \end{array}
$$

式中 $h(t)=\frac{d^{2}g}{dt^{2}}+\frac{1}{T}\frac{dg}{dt}$ 。从上列方程式的形式看，如果控制规律 u 只是误差 $\varepsilon_{1}$ ， $\varepsilon_{2}$ ， $\varepsilon_{3}$ 的线性组合，那么，一般讲来， $\varepsilon(t)$ 将是 $\left[h(t)-\frac{1}{T}f(t)\right]$ 的函数。当 $h-\frac{1}{T}f$ 为常数且系统在 t 趋于很大时， $\varepsilon_{1}$ ， $\varepsilon_{2}$ ， $\varepsilon_{3}$ 也趋于某一稳态误差。

这种由外部作用引起的误差能否消除呢？答复是明显的，当外扰和输入作用可以测量时，一般讲可以用外扰补偿方法去消除动态和稳态误差，即在控制装置中引入外扰的相应坐标，使控制规律含有 $g(t)$ 和 $f(t)$ 及其导数，使 $h(t)$ 和 $f(t)$ 对系统的误差不发生影响[21,22]。现在就来研究在外扰可以完全测量时如何设计控制装置，使前者得到补偿。

设系统只有一个控制量 u。对于误差坐标的运动方程式设为

$$
\frac {d \varepsilon}{d t} = A \varepsilon + \boldsymbol {b} u + \boldsymbol {f} (t) \tag {5.3-3}
$$

式中 $\varepsilon=(\varepsilon_{1},\varepsilon_{2},\cdots,\varepsilon_{n}),\boldsymbol{b}=(b_{1},b_{2},\cdots,b_{n}),\boldsymbol{f}(t)=(f_{1}(t),\cdots,f_{n}(t))$ 。向量 b 的各分量均为常数，其中一部分可以为零，向量 $f(t)$ 的某些分量也可能为零。

用外扰补偿的第一个方法是将 u 分为两部分 $u = u_{1} + u_{2}$ ，令

$$
u _ {1} = \sum_ {\alpha = 1} ^ {n} c _ {\alpha} \varepsilon_ {\alpha} \tag {5.3-4}
$$

使方程式

$$
\frac {d \varepsilon}{d t} = A \varepsilon + b \left[ \sum_ {\alpha = 1} ^ {n} c _ {\alpha} \varepsilon_ {\alpha} \right] = (A + B) \varepsilon \tag {5.3-5}
$$

式中

$$
B = \left( \begin{array}{c c c c} b _ {1} c _ {1} & b _ {1} c _ {2} & \dots & b _ {1} c _ {n} \\ b _ {2} c _ {1} & b _ {2} c _ {2} & \dots & b _ {2} c _ {n} \\ \vdots & \vdots & & \vdots \\ b _ {n} c _ {1} & b _ {n} c _ {2} & \dots & b _ {n} c _ {n} \end{array} \right)
$$

稳定并具有良好的过渡过程。而控制量的第二部分满足恒等式（如果这是可能的话)

$$
\boldsymbol {b} u _ {2} + \boldsymbol {f} (t) \equiv \mathbf {0} \tag {5.3-6}
$$

即

$$
w = - \frac {1}{b _ {i}} f _ {i} (t), \quad i = 1, 2, \dots , n
$$

但是，一般说来，式(5.3-6)是不可能成立的。不难看出，欲使式(5.3-6)有解，必须要求

$$
\frac {f _ {1} (t)}{b _ {1}} = \frac {f _ {2} (t)}{b _ {2}} = \dots = \frac {f _ {n} (t)}{b _ {n}}
$$

而当 $b_{i}=0$ 时 $f_{i}(t)$ 必须恒为零。这种情况只有在外扰的作用点与控制量的作用点相同时才可能有解。如果 $g(t)$ 属于固有作用类，而 $f(t)$ 与 u 作用在同一个点上，这时自然有完全补偿公式 $w_{2}=-f(t)$ 。

当 $f(t)$ 的作用点与控制量的作用点不同时，式(5.3-6)不可能有解。例如前面讨论过的系统式(5.3-2)和(5.3-6)要求 $h(t)-f(t)=0$ 和 $w=0$ 。当前者不为零时，式(5.3-6)无解。

设 x 为受控对象的主要受控量, $f(t)$ 的作用点可以是任意的, $g(t)$ 为任意足够光滑的函数。这类系统的运动方程总可化成式(5.3-3)的形式。当对误差的控制规律式(5.3-4)已经选定时, 方程式(5.3-3)的解可写成

$$
\varepsilon (t) = e ^ {D t} \varepsilon_ {0} + \int_ {0} ^ {t} e ^ {D (t - \tau)} (\boldsymbol {b u} _ {2} + \boldsymbol {f} (\tau)) d \tau \tag {5.3-7}
$$

上式内方阵 $D = A + B$ 。把向量等式内的第一个坐标 $\varepsilon_{1}(t)$ 分出

$$
\varepsilon_ {1} (t) = \sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t) \varepsilon_ {0 \alpha} + \int_ {0} ^ {t} \sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t - \tau) \left(b _ {\alpha} u _ {2} + f _ {\alpha} (\tau)\right) d \tau \tag {5.3-8}
$$

上式右端第一项为系统的自由运动，因为 $\varphi_{\alpha}(t)$ 为矩阵函数 $e^{Dt}=(\varphi_{\alpha\beta}(t))$ 的第一行元素，若系统式(5.3-5)稳定，则 $\lim_{\tau\to\infty}\varphi_{\alpha\beta}(t)=0$ 。为了完全补偿外扰作用 $f_{\alpha}(t)$ ，必须对任何 t 使下列等式成立

$$
\int_ {0} ^ {t} \left(\sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t - \tau) b _ {\alpha}\right) u _ {2} (\tau) d \tau \equiv - \int_ {0} ^ {t} \sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t - \tau) f _ {\alpha} (\tau) d \tau \tag {5.3-9}
$$

等式之右端为已知函数，故上式为一积分方程

$$
\int_ {0} ^ {t} K (t - \tau) u _ {2} (\tau) d \tau = v (t) \tag {5.3-10}
$$

式中

$$
K (t - \tau) = \sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t - \tau) b _ {\alpha}, \quad v (t) = - \int_ {0} ^ {t} \sum_ {\alpha = 1} ^ {n} \varphi_ {1 \alpha} (t - \tau) f _ {\alpha} (\tau) d \tau
$$

可以用任何一种方法解积分方程式(5.3-10)，例如逐步逼近法等。这样即可求出补偿函数 $w_{2}(t)=I(f_{1}(t),\cdots,f_{n}(t))$ ，后者将完全补偿掉外扰和输入函数的作用，而使系统的稳态误差为零。

如果用拉氏变换方法解积分方程(5.3-9)，利用卷积公式可直接找出 $u_{2}(t)$ 与 $f_{\alpha}(t), \alpha=1,2,\cdots,n$ ，的关系式。对式(5.3-9)两端作拉氏变换后有

$$
- \Phi_ {u} (s) U _ {2} (s) = \sum_ {\alpha = 1} ^ {n} \Phi_ {f \alpha} (s) F _ {\alpha} (s) \tag {5.3-11}
$$

或者

$$
\begin{array}{l} U _ {2} (s) = \frac {- \sum_ {\alpha = 1} ^ {n} \Phi_ {f \alpha} (s) F _ {\alpha} (s)}{\Phi_ {u} (s)} \\ = - \sum_ {\alpha = 1} ^ {n} \frac {\Phi_ {f \alpha} (s)}{\Phi_ {u} (s)} F _ {\alpha} (s) \tag {$5.3-11^{\prime$}} \\ \end{array}
$$

不难看出，上式内 $\Phi_{u}(s)$ 正是受控对象对误差 $\varepsilon$ 的传递函数， $\Phi_{fa}(s)$ 是自加入外扰点至误差 $\varepsilon$ 点的传递函数。根据式(5.3-11')可以确定对外扰和输入作用的补偿规律。假定设计好的系统为图 5.3-2 所示。由输入 $g(t)$ 所引起的动态误差是

> 此处省略原书 **图 5.3-2**

$$
E _ {g} (s) = \frac {1}{1 + W _ {k} (s) W _ {1} (s) W _ {2} (s)} G (s) \tag {5.3-12}
$$

由 $u_{2}$ 作用引起的误差为

$$
E _ {u _ {2}} (s) = \frac {- W _ {1} (s) W _ {2} (s)}{1 + W _ {1} (s) W _ {2} (s) W _ {k} (s)} U _ {2} (s)
$$

按式 $(5.3-11)$ 有补偿公式

$$
U _ {2} (s) = \frac {1}{W _ {1} (s) W _ {2} (s)} G (s) \tag {5.3-13}
$$

外扰作用 $f(t)$ 引起的误差是

$$
E _ {f} (s) = - \frac {W _ {2} (s)}{1 + W _ {k} (s) W _ {1} (s) W _ {2} (s)} F (s) \tag {5.3-14}
$$

根据式 $(5.3-11')$ 有完全补偿公式

$$
U _ {2} (s) = - \frac {1}{W _ {1} (s)} F (s) \tag {5.3-15}
$$

这样，我们便得到对输入作用 $g(t)$ 和对外扰作用 $f(t)$ 的全补偿公式(5.3-13)和(5.3-15)。加上补偿装置后，控制系统的方块图将如图 5.3-3 所示。在这种控制系统内控制量 u 不仅是误差的函数，也是输入作用和外扰作用的函数。这种系统常称为复合控制系统。

> 此处省略原书 **图 5.3-3**

从理论上看，动态补偿问题已完全由式(5.3-9)或(5.3-11')所解决。但是，应该指出，要想得到这种全补偿系统在实际工作中是有困难的。这种困难主要来自两个方面：其一是测量困难，并不是所有的外扰都能准确地瞬时测量出来。例如飞行器上所受的阵风干扰，在实际上就几乎不可能直接测量出来。当然，这时补偿公式(5.3-11)就不能应用了。第二个困难是补偿装置的实现方法，因为式(5.3-13)和式(5.3-15)都要求实现较为复杂的控制规律。其中包括对外扰作用和输入作用的高阶导数，而后者是不易得到的。因为即便外扰和输入作用的瞬时值可以测出，由于实际量中总含有噪声，欲得到它们的高阶导数是异常困难的。尽管如此，复合系统的应用还是十分广泛。当完全补偿不可能做到时，常不得不满足于部分的或局部的补偿。究竟补偿精度能做到何种程度，由实际工程问题中 上述两种困难的克服程度而定，也与输入作用 $g(t)$ 和外扰作用 $f(t)$ 的变化规律有关。例如当 $f(t)$ 为常量或为缓变函数时，补偿通常比较简单。关于各种补偿方法的研究，还可参考文献 $[16,21,22,25,26]$ 。

#### 5.4 控制装置参数选择

前面几节内讨论过的线性系统设计方法的出发点是保证系统的稳定性，使动态误差与稳态误差完全消除或者减小到一定程度。但是，有时对控制系统的品质要求不限于此，还可能有其他类型的指标。例如，在控制系统中的能量消耗，温度控制中的温差等都常作为对控制系统的指标要求。对于伺服系统的过渡过程也有时要求均方误差小，例如图 5.4-1 内所示的过渡过程，如果要求 $\varepsilon(t)$ 迅速趋于零，那么在 $t_1$ 足够大时，指标

$$
J = \int_ {0} ^ {t _ {1}} \varepsilon^ {2} (t) d t \tag {5.4-1}
$$

在一定程度上体现了过渡过程的快速性和平滑性。本节内我们将研究具有式(5.4-1)型质量指标的线性系统设计方法。

因为在本章内所讨论的对象只限于线性控制系统，所以这里只研究线性控制规律的选择方法。事前做下列互相并不独立的假定：设输入作用 $g(t)$ 属于系统的固有作用类，因此系统无静差；其次设系统渐近稳定，即任何初始误差 $\varepsilon_{1}$ 都将随时间的增大而趋于零，而衰减速度为指数规律。设用 x 表示系统的误差，系统的运动方程式为

> 此处省略原书 **图 5.4-1**

$$
a _ {n} \frac {d ^ {n} x}{d t ^ {n}} + a _ {n - 1} \frac {d ^ {n - 1} x}{d t ^ {n - 1}} + \dots + a _ {0} x = 0 \tag {5.4-2}
$$

或者写成一般的形式

$$
\frac {d \boldsymbol {x}}{d t} = D \boldsymbol {x}, \quad D = A + B C \tag {5.4-3}
$$

式中 A, B 分别为受控对象方程

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u}
$$

的 $n \times n$ 和 $n \times m$ 阶矩阵, C 为待求矩阵, 它决定控制装置中的控制规律。

因为系统式(5.4-3)或(5.4-2)为稳定，所以矩阵 D 的一切特征根有负实部。严格说来线性系统的一切过渡过程只有 $t \to \infty$ 时才会完全结束，因为函数 $e^{-\alpha t}, \alpha >$

0, 只有在 $t \to \infty$ 时才为零。由于这两个原因, 式(5.4-1)内之积分上限可换为无穷大, 此时积分依然收敛, 为了作更一般的讨论, 我们设积分指标为对一非负二次型的积分

$$
J = \int_ {0} ^ {\infty} \sum_ {\alpha , \beta = 1} ^ {n} g _ {\alpha \beta} x _ {\alpha} x _ {\beta} d t = \int_ {0} ^ {\infty} (\boldsymbol {x}, G \boldsymbol {x}) d t \tag {5.4-4}
$$

式中 $x_{\alpha}$ 为向量 x 的分量，G 为非负方阵，其元素为 $g_{ij}$ ，而且 $g_{ij} = g_{ji}$ ，即 G 为对称矩阵。

由于式(5.4-3)是一个线性齐次方程组，当系统的初始误差 $x_{0}$ 给定时，系统的运动规律 $x(t)$ 就已完全被确定，因此，实际上积分指标式(5.4-4)是初始条件 $x_{0}$ 的连续函数。让我们首先求出这个函数关系 $^{[9]}$ 。令 F 为某一正定对称矩阵，用它构成二次型

$$
h (t) = (\boldsymbol {x} (t), F \boldsymbol {x} (t))
$$

对 $h(t)$ 微分后有

$$
\begin{array}{l} \frac {d h (t)}{d t} = \left(D \boldsymbol {x} (t), F \boldsymbol {x} (t)\right) + \left(\boldsymbol {x} (t), F D \boldsymbol {x} (t)\right) \\ = (\boldsymbol {x} (t), (D ^ {\tau} F + F D) \boldsymbol {x} (t)) \\ \end{array}
$$

式内 $D^{\tau}$ 为 D 的转置矩阵。令

$$
D ^ {\tau} F + F D = G \tag {5.4-5}
$$

那么有

$$
\int_ {0} ^ {\infty} \frac {d h (t)}{d t} d t = (\boldsymbol {x} (t), F \boldsymbol {x} (t)) \mid_ {0} ^ {\infty} = \int_ {0} ^ {\infty} (\boldsymbol {x}, G \boldsymbol {x}) d t
$$

于是

$$
- (\pmb {x} _ {0}, F \pmb {x} _ {0}) = \int_ {0} ^ {\infty} (\pmb {x}, G \pmb {x}) d t \tag {5.4-6}
$$

由此可知，若矩阵 F 求出后，系统质量指标式(5.4-4),就可直接写为初始误差 $x_{0}$ 的函数

$$
J = - \left(\boldsymbol {x} _ {0}, F \boldsymbol {x} _ {0}\right) = - \sum_ {\alpha , \beta = 1} ^ {n} f _ {\alpha \beta} x _ {\alpha 0} x _ {\beta 0} \tag {5.4-7}
$$

求矩阵 $F$ 有两种方法，第一种方法是直接求解矩阵方程(5.4-5)，此时得到 $n^2$ 个线性代数方程式构成的方程组。可以证明，这个方程组必然有唯一解。这个方法虽然可用，但终嫌过烦。第二个求解方法是利用矩阵函数的特性。将式(5.4-5)之两端左右分别乘以矩阵函数 $e^{D^{\tau}t}$ 和 $e^{Dt}$ 得

$$
e ^ {D ^ {\tau} t} G e ^ {D t} = e ^ {D ^ {\tau} t} D ^ {\tau} F e ^ {D t} + e ^ {D ^ {\tau} t} F D e ^ {D t}
$$

显然此等式之右端是 $e^{D^{\tau}_{t}}Fe^{D_{t}}$ 对 t 的导数，因为 $e^{D_{t}}D=De^{D_{t}}$ 。再对前式积分

$$
\int_ {0} ^ {\infty} \frac {d}{d t} (e ^ {D ^ {\tau} t} F e ^ {D t}) d t = \int_ {0} ^ {\infty} e ^ {D ^ {\tau} t} G e ^ {D t} d t
$$

左端取积分后有

$$
\int_ {0} ^ {\infty} \frac {d}{d t} (e ^ {D ^ {\tau_ {t}}} F e ^ {D t}) d t = e ^ {D ^ {\tau_ {t}}} F e ^ {D t} \mid_ {0} ^ {\infty} = - F
$$

因此，可求出

$$
F = - \int_ {0} ^ {\infty} e ^ {D \tau_ {t}} G e ^ {D t} d t \tag {5.4-8}
$$

上式之所以成立是由于

$$
\lim _ {t \rightarrow \infty} e ^ {D t} = \lim _ {t \rightarrow \infty} e ^ {D ^ {\tau} t} = 0
$$

右端 0 为零矩阵。

现举单摆振动阻尼问题为例来说明矩阵 F 的求解方法。设控制系统的误差运动方程为

$$
\frac {d ^ {2} x}{d t ^ {2}} + x = u \tag {5.4-9}
$$

设控制规律为 $u = -c \frac{dx}{dt}$ ，则反馈系统方程式为

$$
\frac {d ^ {2} x}{d t ^ {2}} + c \frac {d x}{d t} + x = 0 \tag {5.4-10}
$$

令 $x = x_{1},\frac{dx}{dt} = x_{2}$ ，上式可改写成方程组

$$
\frac {d x _ {1}}{d t} = x _ {2}
$$

$$
\frac {d x _ {2}}{d t} = - x _ {1} - c x _ {2} \tag {5.4-11}
$$

我们知道, 当 c>0 时系统式(5.4-10)总为渐近稳定。设过渡过程质量指标为

$$
J = \int_ {0} ^ {\infty} (x _ {1} ^ {2} + x _ {2} ^ {2}) d t = \int_ {0} ^ {\infty} (\boldsymbol {x}, \boldsymbol {G} \boldsymbol {x}) d t \tag {5.4-12}
$$

式中

$$
G = \left( \begin{array}{c c} 1 & 0 \\ 0 & 1 \end{array} \right)
$$

因为

$$
D = \left( \begin{array}{c c} 0 & 1 \\ - 1 - c \end{array} \right), e ^ {D t} = \left( \begin{array}{c c} \frac {- \lambda_ {2}}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {1} t} + \frac {\lambda_ {1}}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {2} t} & \frac {1}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {1} t} - \frac {1}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {2} t} \\ \frac {- 1}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {1} t} + \frac {1}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {2} t} & \frac {\lambda_ {1}}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {1} t} - \frac {\lambda_ {2}}{\lambda_ {1} - \lambda_ {2}} e ^ {\lambda_ {2} t} \end{array} \right) \tag {5.4-13}
$$

式中 $\lambda_1, \lambda_2$ 是代数方程式

$$
\lambda^ {2} + c \lambda + 1 = 0
$$

的两个根。容易计算

$$
e ^ {D \tau_ {t}} G e ^ {D t} = \beta^ {2} \left( \begin{array}{c c} (1 + \lambda_ {2} ^ {2}) e ^ {2 \lambda_ {1} t} - 4 e ^ {\left(\lambda_ {1} + \lambda_ {2}\right) t} & - (\lambda_ {1} + \lambda_ {2}) e ^ {2 \lambda_ {1} t} - (\lambda_ {1} + \lambda_ {2}) e ^ {2 \lambda_ {2} t} \\ + (1 + \lambda_ {1} ^ {2}) e ^ {2 \lambda_ {2} t} & + 2 (\lambda_ {1} + \lambda_ {2}) e ^ {\left(\lambda_ {1} + \lambda_ {2}\right) t} \\ - (\lambda_ {1} + \lambda_ {2}) e ^ {2 \lambda_ {1} t} - (\lambda_ {1} + \lambda_ {2}) e ^ {2 \lambda_ {2} t} & (1 + \lambda_ {1} ^ {2}) e ^ {2 \lambda_ {1} t} + (1 + \lambda_ {2} ^ {2}) e ^ {2 \lambda_ {2} t} \\ + 2 (\lambda_ {1} + \lambda_ {2}) e ^ {\left(\lambda_ {1} + \lambda_ {2}\right) t} & - 4 e ^ {\left(\lambda_ {1} + \lambda_ {2}\right) t} \end{array} \right) \tag {5.4-14}
$$

式中 $\beta=\frac{1}{\lambda_{1}-\lambda_{2}}$ 。

注意到, 只要 c>0, 公式(5.4-8)右端积分总是收敛的, 故我们可以对式(5.4-14)作下列积分运算

$$
\int_ {0} ^ {\infty} e ^ {D \tau_ {t}} G e ^ {D t} d t = \beta^ {2} \left( \begin{array}{c c} \frac {c ^ {4} - 2 c ^ {2} - 8}{2 c} & \frac {c ^ {2} - 4}{2} \\ \frac {c ^ {2} - 4}{2} & \frac {c ^ {2} - 4}{c} \end{array} \right) \tag {5.4-15}
$$

因为 $\lambda_{1}$ 和 $\lambda_{2}$ 是方程式 $\lambda^{2} + c\lambda + 1 = 0$ 的两个根，容易算出上式右端矩阵四个元素的值为

$$
- F = \int_ {0} ^ {\infty} e ^ {D \tau_ {t}} G e ^ {D t} d t = \left[ \begin{array}{c c} \frac {c ^ {2} + 2}{2 c} & \frac {1}{2} \\ \frac {1}{2} & \frac {1}{c} \end{array} \right] \tag {5.4-16}
$$

设式(5.4-10)表示的单摆运动的初始条件是任意的： $x_{1}(0)=x_{10}, x_{2}(0)=x_{20}$ ，则全部过渡过程的积分质量指标式(5.4-12)可直接求出。依式(5.4-7)有

$$
J = - \left(\boldsymbol {x} _ {0}, F \boldsymbol {x} _ {0}\right) = \frac {c ^ {2} + 2}{2 c} x _ {1 0} ^ {2} + x _ {1 0} x _ {2 0} + \frac {1}{c} x _ {2 0} ^ {2} \tag {5.4-17}
$$

今假定单摆的初始速度为 0，即 $x_{20}=0$ ，而初始振幅 $x_{10}$ 异于 0。由式(5.4-17)可知，此时二次积分指标的值为

$$
J = \frac {c ^ {2} + 2}{2 c} x _ {1 0} ^ {2} \tag {5.4-18}
$$

容易检查, 函数 $\frac{c^{2}+2}{2c}$ 当 $c=\sqrt{2}$ 时有极小值。所以, 对一切初始速度为 0 的运动, 欲使 J 达极小值的最优阻尼是取 $c=\sqrt{2}$ 。

前面我们用矩阵函数的方法求出了均方误差的表达式。实际上表达式(5.4-7)也可以用拉氏变换的方法求出，即直接从工程上常用的传递函数的表达式求出函数 $J(\pmb{x}_0)$ ，有时这种方法可能更方便些。为此只要找出矩阵 $F$ 与传递函数的关系就够了。下面我们试建立这种新的关系式[11]。首先对受控对象的误差方程式

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u} \tag {5.4-19}
$$

进行拉氏变换

$$
s \boldsymbol {X} (s) - \boldsymbol {x} _ {0} = A \boldsymbol {X} (s) + B \boldsymbol {U} (s)
$$

式中 $X(s)$ 表示向量 $x(t)$ 的拉氏变换, $U(s)$ 为控制向量 $u(t)$ 的象函数, 二者依然是向量函数, 解上述方程后

$$
\boldsymbol {X} (s) = (s E - A) ^ {- 1} B \boldsymbol {U} (s) + (s E - A) ^ {- 1} \boldsymbol {x} _ {0} \tag {5.4-20}
$$

式中 E 为单位矩阵，而矩阵 $(sE-A)^{-1}$ 称为受控系统的传递函数。现令控制规律为 $\boldsymbol{u}(t)=C\boldsymbol{x}(t)$ ，或 $\boldsymbol{U}(s)=C\boldsymbol{X}(s)$ 。代入式(5.4-20)并化简后得到 $\boldsymbol{x}(t)$ 的象函数

$$
\boldsymbol {X} (s) = (s E - (A + B C)) ^ {- 1} \boldsymbol {x} _ {0} \tag {5.4-21}
$$

现在可以直接解算式(5.4-4)了。引入矩阵记号

$$
K (s) = (s E - (A + B C)) ^ {- 1} \tag {5.4-22}
$$

可以证明式(5.4-7)的正定矩阵 $F$ 可由下式求出

$$
F = - \frac {1}{2 \pi i} \int_ {- i ^ {\infty}} ^ {i ^ {\infty}} K ^ {\tau} (s) G K (- s) d s \tag {5.4-23}
$$

式中 $K^{\tau}(s)$ 为 $K(s)$ 的转置矩阵。将 $\boldsymbol{x}(t)=\frac{1}{2\pi i}\int_{-i^{\infty}}^{+i^{\infty}}\boldsymbol{X}(s)e^{st}ds$ 代入式(5.4-4)之右端后再作下列变换得

$$
\begin{array}{l} J = \int_ {0} ^ {\infty} \left[ \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} X (s) e ^ {s t} d s, G x (t) \right] d t \\ = \frac {1}{2 \pi i} \int_ {- i \infty} ^ {i \infty} \left[ X (s), G \int_ {0} ^ {\infty} x (t) e ^ {s t} d t \right] d s \\ = \frac {1}{2 \pi i} \int_ {- i ^ {\infty}} ^ {+ i ^ {\infty}} (\boldsymbol {X} (s), G \boldsymbol {X} (- s)) d s \tag {5.4-24} \\ \end{array}
$$

对 $\boldsymbol{x}(t)$ 的拉氏反变换之积分线路可以取虚轴 $(-i^{\infty}, +i^{\infty})$ ，这是因为 $\boldsymbol{x}(t)$ 渐近趋于零， $\boldsymbol{X}(s)$ 的一切奇点均位于左半平面。而式 (5.4-24) 内之积分号可以互换是由于两个积分都绝对收敛。将式 (5.4-21) 代入式 (5.4-24) 得

$$
\begin{array}{l} J = \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} (K (s) x _ {0}, G K (- s) x _ {0}) d s \\ = \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} \left(\boldsymbol {x} _ {0}, K ^ {\tau} (s) G K (- s) \boldsymbol {x} _ {0}\right) d s \\ = \left[ \boldsymbol {x} _ {0}, \frac {1}{2 \pi i} \int_ {- i \infty} ^ {i \infty} K ^ {\tau} (s) G K (- s) d s \boldsymbol {x} _ {0} \right] \\ \end{array}
$$

将上式与式 $(5.4-6)$ 比较即得到式 $(5.4-23)$ 。当 G 为单位矩阵时

$$
J = \int_ {0} ^ {\infty} (x _ {1} ^ {2} (t) + \dots + x _ {n} ^ {2} (t)) d t = - (x _ {0}, F x _ {0})
$$

$$
F = - \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} K ^ {\tau} (s) K (- s) d s \tag {5.4-25}
$$

设误差运动方程式是式(5.4-2)，而

$$
J = \int_ {0} ^ {\infty} x ^ {2} (t) d t
$$

根据前述可推知

$$
J = \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} \frac {N _ {0} (s) N _ {0} (- s)}{D (s) D (- s)} d s = \frac {1}{2 \pi i} \int_ {- i \infty} ^ {+ i \infty} \left| \frac {N _ {0} (s)}{D (s)} \right| ^ {2} d s \tag {5.4-26}
$$

其中

$$
\begin{array}{l} D (s) = a _ {n} s ^ {n} + a _ {n - 1} s ^ {n - 1} + \dots + a _ {1} s + a _ {0} \\ N _ {0} (s) = a _ {n} x _ {0} s ^ {n - 1} + \left(a _ {n} x _ {0} ^ {(1)} + a _ {n - 1} x _ {0}\right) s ^ {n - 2} + \dots \\ + \left(a _ {n} x _ {0} ^ {(n - 1)} + a _ {n - 1} x _ {0} ^ {(n - 2)} + \dots + a _ {1} x _ {0}\right) \\ \end{array}
$$

这里

$$
x _ {0} ^ {(i)} = \frac {d ^ {i} x}{d t ^ {i}} \mid_ {t = 0}, \quad \text {若} x _ {0} ^ {(i)} = 0, \quad i = 1, 2, \dots , n - 1
$$

则

$$
N _ {0} (s) = \left(a _ {n} s ^ {n - 1} + a _ {n - 1} s ^ {n - 2} + \dots + a _ {1}\right) x _ {0}
$$

前面分析的单摆阻尼问题例中，只含有一个待选参数 $c$ 。事实上本节所讨论的方法同样可以应用到多参数选择的情况。如果考虑 $n$ 阶系统，初始偏差限定为只有一个误差坐标不为零，其他 $n - 1$ 个坐标初值均为 0，那么由式(5.4-7)确定的 $J$ 的系数，将是反馈矩阵 $C[$ 见式(5.4-3)]的每一元素的解析函数：

$$
J = f (c _ {i j}) x _ {1 0} ^ {2}
$$

容易用计算机去求最好的矩阵元素 $c_{ij}$ ，使系数函数 f 即 J 取极小值。如果系统的初始条件是任意的，J 就是系统初始状态的二次型，一般来讲，J 的极小（即最好的反馈矩阵）还依赖初始条件，所以不能求出一个固定的常量矩阵，使 J 对任何初始条件均为极小，这时就只能满足于对某些具有代表性的初始条件的参数选择。

#### 5.5 极点配置问题

在第四章讨论系统稳定性时，我们已经看到线性常系数系统的稳定性，完全取决于系统传递函数的极点在复平面上的分布。实际上，不仅系统稳定性取决于极点分布，系统的其他特性和品质指标，在很大程度上都由极点在左半平面上的位置所决定。以二阶振荡系统为例，如果它有一对互为共轭的复根，即两个极点相对实轴对称，那么系统阻尼的大小，取决于极点负实部的大小，而振荡频率的高低则决定于虚部的大小。因此，为了增大系统阻尼，我们可以使这对极点离虚轴远一些；要想减小振荡频率，可以使极点离实轴近一些。这样，我们就可以根据系 统设计指标要求，有目的地配置系统的极点分布。回想一下我们讲过的根轨迹法，也是一种极点配置，不过它只把极点配置在左半平面使系统渐近稳定就行了。当系统的指标要求不仅是渐近稳定，而且还对系统的过渡过程有进一步要求（如超调量，振荡次数，过渡时间，通频带等),这时极点配置只在左半平面还不够，还必须更精确的配置。于是，就出现了这样的问题，就是闭路系统的极点是否可以通过反馈规律的选择而任意配置?在什么条件下可以这样配置?关于这个问题的答案是，只要系统是完全能控的，那么它的极点就可以用状态线性反馈而任意配置。这一节我们将简单地讨论这个问题 $^{[8,19]}$ 。

设单输入单输出线性系统为

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + \boldsymbol {b u}
$$

$$
y = \boldsymbol {c} ^ {\tau} \boldsymbol {x} \tag {5.5-1}
$$

其中 A 是 $n \times n$ 阶常矩阵, b, c 是 $n \times 1$ 阶矩阵。x 是系统状态变量, y 是输出量, u 是控制。

所谓极点配置，就是指经过状态（或输出）的线性反馈, $u=k^{x}$ ,k 是 $n\times1$ 阶矩阵，使闭环系统

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + \boldsymbol {b k} ^ {\tau} \boldsymbol {x} = (A + \boldsymbol {b R} ^ {\tau}) \boldsymbol {x}
$$

的极点 $(A+bk^{\tau}$ 的本征值）可以取任意指定的值。

应该指出，现实的物理系统都是实系数的，因此，某个极点若是复数，那么它的共轭复数也一定是极点。所以复数极点一定成对出现。当任意配置极点时，其中若有复数，则一定包含一对互为共轭的复数。

下面我们来证明，如果系统式(5.5-1)是完全能控的，即矩阵 $(b,Ab,A^{2}b,\cdots,A^{n-1}b)$ 的秩为 n(见第 4.11 节),那么任意一组数 $s_{1},s_{2},\cdots,s_{n}$ ,必存在一个矩阵 k,使 $A+bk^{\tau}$ 的本征值为 $s_{1},s_{2},\cdots,s_{n}$ 。这就是说，通过状态反馈可以使闭环系统的极点任意配置。

为了证明简单，首先对系统式(5.5-1)进行坐标变换。

设有一非奇异 $n \times n$ 阶矩阵 T，使 x = Tx，经过变换后，式(5.5-1)可以变成

$$
\dot {\boldsymbol {x}} = T A T ^ {- 1} \boldsymbol {x} + T \boldsymbol {b} u
$$

$$
y = \boldsymbol {c} ^ {\tau} T ^ {- 1} \boldsymbol {x} \tag {5.5-2}
$$

系统式(5.5-1)和(5.5-2)是等价的（确切说是代数等价)，它们有相同的传递函数阵，有相同的脉冲响应阵，如令 $A_0 = TAT^{-1}$ ，则有 $e^{A_0t} = Te^{At}T^{-1}$ 。系统的一些动态特性不因坐标变换而改变。这样，就有可能使我们找到一个适当的非奇异矩阵 $T$ ，把系统式(5.5-1)化成式(5.5-2)，从而使式(5.5-2)变得更方便于我们的讨论。

下面我们先选出非奇异矩阵 T。

令

$$
\begin{array}{l} Q = (\boldsymbol {b}, A \boldsymbol {b}, A ^ {2} \boldsymbol {b}, \dots , A ^ {n - 1} \boldsymbol {b}) \\ A _ {c} = \left( \begin{array}{c c c c c c} & 0 & 1 & 0 & \dots & 0 \\ & & & 1 & & \\ & & & & \ddots & \\ & & & & & 1 \\ - \alpha_ {0} & - \alpha_ {1} & & \dots & - \alpha_ {n - 1} \end{array} \right) \\ \end{array}
$$

$$
L = \left( \begin{array}{c c c c c} \alpha_ {1} & \alpha_ {2} & \dots & \alpha_ {n - 1} & 1 \\ \alpha_ {2} & & & & \\ \vdots & & \ddots & & \\ \alpha_ {n - 1} & & & 0 & \\ 1 & & & & \end{array} \right) \tag {5.5-3}
$$

则 Q, L 都是非奇异矩阵, 它们的逆矩阵都存在。

设

$$
T = (Q L) ^ {- 1} \tag {5.5-4}
$$

我们看一下，它能将式(5.5-1)变成什么形式。

$$
T ^ {- 1} = Q L = \left(\boldsymbol {D} _ {1}, \boldsymbol {D} _ {2}, \dots , \boldsymbol {D} _ {n}\right)
$$

容易验证

$$
\begin{array}{l} \boldsymbol {D} _ {i} = \sum_ {j = 0} ^ {n - i - 1} \alpha_ {i + j} A ^ {j} \boldsymbol {b} + A ^ {n - i} \boldsymbol {b}, \quad i = 1, 2, \dots , n - 1 \\ \boldsymbol {D} _ {n} = \boldsymbol {b} \\ \end{array}
$$

所以有

$$
A D _ {i} = D _ {i - 1} - \alpha_ {i - 1} D _ {n}, \quad i = 2, 3, \dots , n
$$

而

$$
\begin{array}{l} \boldsymbol {A} \boldsymbol {D} _ {1} = A (\alpha_ {1} \boldsymbol {b} + \alpha_ {2} A \boldsymbol {b} + \dots + \alpha_ {n - 1} A ^ {n - 2} \boldsymbol {b} + A ^ {n - 1} \boldsymbol {b}) \\ = \left(\alpha_ {1} A \boldsymbol {b} + \alpha_ {2} A ^ {2} \boldsymbol {b} + \dots + \alpha_ {n - 1} A ^ {n - 1} \boldsymbol {b} + A ^ {n} \boldsymbol {b}\right) \\ = - \alpha_ {0} E b \\ = - \alpha_ {0} D _ {n} \\ \end{array}
$$

其中 $E$ 是单位矩阵。这里利用了线性代数中的凯莱-哈密顿(Cayley-Hamilton)定理。于是，我们又可以推出

$$
\begin{array}{l} A T ^ {- 1} = A \left(\boldsymbol {D} _ {1}, \boldsymbol {D} _ {2}, \dots , \boldsymbol {D} _ {n}\right) \\ = \left(A D _ {1}, A D _ {2}, \dots , A D _ {n}\right) \\ = \left(- \alpha_ {0} D _ {n}, D _ {1} - \alpha_ {1} D _ {n}, \dots , D _ {n - 1} - \alpha_ {n - 1} D _ {n}\right) \\ \end{array}
$$

$$
\begin{array}{l} = \left(\boldsymbol {D} _ {1}, \boldsymbol {D} _ {2}, \dots , \boldsymbol {D} _ {n}\right) \left( \begin{array}{c c c c c} 0 & 1 & 0 & \dots & 0 \\ & 0 & & \ddots & 0 \\ & & & & 1 \\ - \alpha_ {0} & - \alpha_ {1} & \dots & - \alpha_ {n - 1} \end{array} \right) \\ = T ^ {- 1} A _ {c} \\ \end{array}
$$

最后得到

$$
T A T ^ {- 1} = A _ {c} \tag {5.5-5}
$$

通过简单运算，容易验证

$$
T \boldsymbol {b} = L ^ {- 1} Q ^ {- 1} \boldsymbol {b} = \left[ \begin{array}{c c c} & 0 & \\ & 0 & \\ & \vdots & \\ & 0 & \\ & 1 & \end{array} \right] \tag {5.5-6}
$$

如记

$$
\boldsymbol {c} ^ {\tau} = \boldsymbol {c} ^ {\tau} T ^ {- 1} = \boldsymbol {c} ^ {\tau} Q L = (a _ {0}, c _ {1}, \dots , c _ {n - 1}) \tag {5.5-7}
$$

那么，系统式(5.5-1)经过非奇异变换 T 变成了如下的形式

$$
\frac {d \boldsymbol {x}}{d t} = A _ {c} \boldsymbol {x} + \left( \begin{array}{c c c} & 0 \\ & 0 \\ & \vdots \\ & 0 \\ & 1 \end{array} \right) u
$$

$$
\mathbf {y} = \boldsymbol {c} ^ {\tau} \mathbf {x} \tag {5.5-8}
$$

其中 $A_{c}$ 如式(5.5-3)。(这种形式，有的书上叫做可控标准形)。

由上所述，我们可以看出，对任意单输入单输出系统，只要完全能控，由矩阵 Q 出发，总可以把系统变成式(5.5-8)的形式，因此，我们不妨假定系统式(5.5-1)已经是式(5.5-8)的形式，否则我们可以用上述办法化成这种形式。现在我们对具有式(5.5-8)形式的系统

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + \boldsymbol {b u}
$$

$$
y = \boldsymbol {c} ^ {\tau} \boldsymbol {x} \tag {5.5-9}
$$

其中

$$
A = \left( \begin{array}{c c c c c} 0 & 1 & 0 & \dots & 0 \\ & & & \ddots & \\ & & & & 1 \\ - \alpha_ {0} & - \alpha_ {0} & \dots & & - \alpha_ {n - 1} \end{array} \right), \quad \boldsymbol {b} = \left( \begin{array}{c c c c c} & 0 & \\ & 0 & \\ & \vdots & \\ & 0 & \\ & 1 & \end{array} \right), \quad \boldsymbol {c} \left( \begin{array}{c c c c c} & c _ {0} & \\ & c _ {1} & \\ & \vdots & \\ & c _ {n - 1} \end{array} \right)
$$

来证明当它完全能控时，可以任意配置极点。

事实上，经过状态反馈 $\boldsymbol{k}^{\tau}=(k_{0},k_{1},\cdots,k_{n-1})$ 后的闭环系统矩阵为

$$
A + \boldsymbol {b} \boldsymbol {k} ^ {\tau} = \left( \begin{array}{c c c c c} 0 & 1 & 0 & \dots & 0 \\ & & & & 0 \\ & 0 & & \ddots & \\ & & & & 1 \\ - \left(\alpha_ {0} - k _ {0}\right) & - \left(\alpha_ {1} - k _ {1}\right) \dots - \left(\alpha_ {n - 1} - k _ {n - 1}\right) \end{array} \right) \tag {5.5-10}
$$

而传递函数为

$$
G (s) = \frac {c _ {n - 1} s ^ {n - 1} + c _ {n - 2} s ^ {n - 2} + \cdots + c _ {0}}{s ^ {n} + \left(\alpha_ {n - 1} - k _ {n - 1}\right) s ^ {n - 1} + \cdots + \left(\alpha_ {0} - k _ {0}\right)} \tag {5.5-11}
$$

由此可以明显看出，因为一个代数方程的根是诸系数的解析函数，当任意指定 n 个极点 $s_{1}, s_{2}, \cdots, s_{n}$ 时，总可以找到一组数 $k_{0}, k_{1}, \cdots, k_{n-1}$ 用 $\boldsymbol{k}^{\tau} = (k_{0}, k_{1}, \cdots, k_{n-1})$ 作反馈，而使 $s_{1}, s_{2}, \cdots, s_{n}$ 为传递函数 $G(s)$ 的极点。这样我们就证明了前面的结论。

这个事实反过来也是正确的，即是说如果系统式(5.5-1)通过状态反馈可以任意配置极点时，那么系统一定是完全能控的。

通过上述证明，我们还可以看到，在任意配置极点时，并不改变传递函数的零点分布。这是因为零点的位置只取决于 $\boldsymbol{c}^{\tau}=(c_{0},c_{1},\cdots,c_{n-1})$ 。在配置极点时，传递函数的分子并不变化。

还可以证明，系统经过状态反馈仍保持能控性，就是说如果系统式(5.5-1)是完全能控的，经过状态反馈后，系统仍是完全能控的。但状态反馈不一定能保持可观测性。若用观测量（输出）反馈，即 $u = Hy$ 时，则既保持能控性也保持能观测性。一个完全能控完全能观测的系统，它的传递函数不可能产生零点和极点完全相消的问题。由此我们可以推出，用观测量 $y$ 作反馈不能任意配置极点。否则配置的极点和零点相同，产生零极相消的问题就破坏了系统的能控性和能观测性，这和输出反馈保持能控性和能观测性是矛盾的。所以通过观测量反馈一般是不能任意配置极点的。

在实际情况中，有些状态变量是量测不到的，因此状态反馈也常不易实现，为了克服这个困难，近些年来提出用观测器来达到这个目的，有关这方面的内容，可参考有关文献 $^{[19]}$ 。

以上事实不仅对单输入单输出的系统是对的，对多输入多输出系统也是正确的。下面我们不加证明，只把结论列出来。

设多输入多输出线性常系数系统

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u}
$$

$$
\mathbf {y} = C \mathbf {x} \tag {5.5-12}
$$

其中 $A, B, C$ 分别是 $n \times n, n \times r, m \times n$ 阶矩阵。 $x, y, u$ 分别是 $n, m, r$ 维向量，代表系统的状态，输出和控制。

如果系统式(5.5-12)是完全能控的，那么一定可以找到状态反馈矩阵 $K(r \times n$ 阶),使 u = Kx, 可以任意配置 $A + BK$ 的本征值。也就是说，对任意 n 个数 $s_{1}, s_{2}, \cdots, s_{n}$ , 可以找到 K, 使

$$
\det (s I - A - B K) = \prod_ {i = 1} ^ {n} (s - s _ {i}) \tag {5.5-13}
$$

反之，如果系统式(5.5-12)通过状态反馈可以任意配置极点时，那么系统一定是完全能控的。由此看出，一个系统的完全能控性和它可以任意配置极点这一事实是等价的。

#### 5.6 参考文献

[1] 蔡金涛, 契贝舍夫式工作参数滤波器的原理和计算, 科学出版社, 1962.

[2] 陈辉堂, 随动系统, 人民教育出版社, 1961.

[3] 王新民, 在连续控制系统中应用时滞元件滤波器作为校正装置的几个必要条件, 自动化学报, 2(1964), 1, 1-6.

[4] 张芷香, 扰动控制原理在镇定高频淬火装置直流电源电压中的应用, 自动化学报, 2(1964), 3.

[5]吕应祥，绝对不变性与不变性到 $\varepsilon$ 自适应控制系统，自动化学报，2(1964)，4.

[6] 叶正明, 线性复合自动控制系统的图解综合法, 自动化学报, 2(1964), 2.

[7] 何国伟、王文贤，从所需校正网络相频或幅频曲线计算传递函数的方法，自动化学报，2(1964)，1.

[8] 黄琳、郑应平、张迪，李雅普诺夫第二方法与最优控制器分析设计问题，自动化学报，2(1964)，4.

[9] Bellman, R., Notes, on matrix theory-X: A problem in Control, Quarterly of Applied Math., 14(1957), 4.

[10] Bliss. G. A., Lectures on the Calculus of Variations, University of Chicago Press. Chicago. Illinois, 1946.

[11] Chaug, S. S. L., Synthesis of Optimal Control Systems, McGraw-Hill. New York, 1961.

[12] Chestnut, H., Mayer. R. W., Servomechanism and Regulating System Design, Wiley, 1959.

[13] Kalman, R. E., Control system analysis and design via the second method of Lyapunov. ASME Paper 59-NAC-2, 59-NAC-3. 1959.

[14] Newton. G. C., Gould, L. A., & Kaiser, J. F., Analytical Design of Linear Feedback Controls, John Wiley & Sons, Inc., New York, 1957.

[15] Reswick. J. B., Disturbance-response feedback a new control concept, Trans. ASME, 78 (1956), 153.

[16] Truxal, J. G., Automatic Feedback Control System Synthesis, McGraw-Hill, New York, 1955.

[17] Tou.J.T., Modern Control Theory, McGraw-Hill. 1964.

[18] Westcott, J. H., Synthesis of optimum feedback systems satisfying a power limitation. Frequency Response Symposium. Dec., 1953. ASME Paper 53-A-17.

[19] Wonham. W. M., On pole assignment in multi-input controllable linear systems, IEEE Trans. on Automatic Control, AC-12. 1967.

[20] Айзерман, М. А., Увеличение значения коэффициентов усиления одноконтурной системы. Автоматика и Телемеханика, 1951, 2.

[21] Ивахненко А.Г., О способах устранения установившейся ошибки системы автоматического регулирования, Доклаэы АН СССР, 87(1953), 6.

[22] Кулебакин. В. С., О поведении непрерывно возмущаемых автоматизированных линейных систем, Доклаэы АН СССР, 60(1948), 2.

[23] Летов, А. М., Аналитическое конструирование регуляторов, Автоматика и Телемеханика, 21(1960), 4, 5, 6.

[24] Неймарк, Ю. Н., Об определении значений параметров, при которых система устойчива, Автоматика и Телемеханика, 9(1948), 3.

[25] Петров, Б. Н., О реализуемости условии инвариантности, Теория инвариантности и её применение в автоматических устройствах, Труды Совещания, АН УССР, ОТН, 1959.

[26] Розоноэр, Л. И., Вариадионный подход в проблеме инвариантности систем автоматического управления, Автоматика и Телемеханика, 24(1963). 6, 7.

[27] Солодовнчов, В. В., Основы автоматического регулирования, Машгиз, Москва, 1954. (自动调正原理, 王众托译, 水利电力出版社, 1958 年.)
