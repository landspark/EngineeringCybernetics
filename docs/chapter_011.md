# 工程控制论（上册）

（第三版）

钱学森 宋健 著

## 正文（011）

### 第十一章 有时滞的线性系统

在这一章里，我们将要在常系数线性系统里再引进一种新的因素，这就是时滞。所谓时滞 $\tau$ 的意义是：系统的各个变数之间的关系不能够用这些变数在同一时刻 t 的值的关系来表示，相反地，这个关系牵涉到某些变数在时刻 t 的值，同时也牵涉到某些变数在时刻 $t-\tau$ 的值。那些在时刻 $t-\tau$ 取数值的变数与那些在时刻 t 取数值的变数比较，在时间上的滞后（时滞）就是 $\tau$ 。如输气管道中压力波的传 播过程是时滞环节的一个例子，因为压力波在管道中是以有限速度传播的，管道始端的压力波要经过时间 $\tau$ 才传到管道末端。此外，还存在某些高阶系统，它们很难用一般的简单的微分方程来描述，有时就在系统方程中引进时滞量 $\tau$ ，把它作为时滞系统来近似研究，以达到化简的目的。例如，对单位阶跃函数的反应如图 11.0-1 所示的系统，有时可以认为它是一个时滞环节与惯性环节的串联。时滞 $\tau$ 与第 3.1 节所讲的一阶线性系统的时间常数是完全不同的。时滞系统（有时滞作用的系统）的运动状态是用常系数的微分差分方程描述的，这当然比以前所讨论过的只用微分方程描述的系统要复杂得多。曾有很多人研究过有时滞的系统，譬如说：卡兰德尔（Callander），哈尔垂（Hartree），波特尔（Porter）[7]以及米诺尔斯基（Minorsky）[11]，崔泊金（Цыпкин）[25]等，秦元勋等曾对此类系统作过 综合性研究 $^{[1]}$ 。但是，我们要讨论的问题的范围是更狭小的。我们只希望知道：如果反馈控制系统有一个固有的时滞 $\tau$ ，那么，应该怎样分析这个系统的运动状态？我们特别希望把第 4.3 节的乃氏方法加以修改，使这个方法也能应用到时滞系统上来。

> 此处省略原书 **图 11.0-1**

以下我们在研究一般理论的同时，还要通过时滞系统的一个特例的处理来说明这种理论。这个特例就是利用反馈控制的方法使火箭发动机中的燃烧过程稳定。很多学者研究过火箭发动机中燃烧过程的不稳定现象，但是下面关于燃烧时滞现象的分析是根据的克洛科(Crocco)的研究结果 $^{[8]}$ 。这个观点虽然已经证明不能用在所谓“高频振荡”,但对火箭发动机的所谓“低频率振荡”却是适用的，我们 为了使计算简单起见，假设只用一种液体燃料 $^{[15]}$ 。

#### 11.1 燃烧中的时滞

液体燃料从射入燃烧室加热到即将燃烧的临界状态，需要一段时间（这就是燃烧的时滞），然后就迅速地燃烧而变为热燃气。假设 $\dot{m}_b(t)$ 是时刻 $t$ 时由于燃烧而产生的热燃气的质量速率（所谓“质量速率”就是按照质量来计算的时间变化率）。 $\dot{m}_i(t)$ 是在时刻 $t$ 时喷入燃料的质量速率。 $\tau (t)$ 是在时刻 $t$ 开始燃烧的那些燃料的时滞。所以，在从 $t$ 到 $t + dt$ 这一段时间间隔内燃烧的燃料是在从 $t - \tau$ 到 $t - \tau +d(t - \tau)$ 这一段时间间隔内喷射进来的。因此

$$
\dot {m} _ {b} (t) d t = \dot {m} _ {i} (t - \tau) d (t - \tau) \tag {11.1-1}
$$

产生出来的热燃气，有一部分被用来充加在燃烧室中，从而提高燃烧室中的压力 $p(t)$ ，另外一部分通过喷口被喷射出去。如果燃烧室中可能发生的振荡的频率相当低，因此，就可以把燃烧室内的压力看做是均匀的，而且，作为第一次的近似[15]，我们也可以把流过喷口的气流看做是似稳的（所谓“似稳”的意思就是：在任何一段不太长的时间间隔内都可以看做是平稳的）。所以，经过喷口的喷气的质量速率与火箭发动机中的热燃气的密度成正比。但是，对于“单一燃料”（也就是只用一种燃料）的火箭发动机来说，热燃气的温度几乎与燃烧压力无关，而热燃气的密度只与压力成正比，所以，如果 $\overline{m}$ 是流过整个系统的稳态质量速率； $\overline{M}_{g}$ 是发动机中的热燃气的平均质量； $\overline{p}$ 是燃烧室中的压力的稳态平均值。如果把尚未燃烧的液体燃料在燃烧室中所占据的容积忽略不计，我们就有

$$
\dot {m} _ {b} d t = \overline {{\dot {m}}} \frac {p}{p} d t + d \left[ \overline {{M}} _ {g} \frac {p}{p} \right] \tag {11.1-2}
$$

现在，对于燃烧室压力与燃料喷入速率，我们分别引进两个无量纲变数 $\psi$ 和 $\eta$ , 它们的定义是

$$
\psi = \frac {p - \overline {{p}}}{\overline {{p}}}, \quad \eta = \frac {\dot {m} _ {i} - \overline {{\dot {m}}}}{\overline {{\dot {m}}}} \tag {11.1-3}
$$

所以 $\psi$ 和 $\eta$ 就是压力和喷入速率对于稳态平均值的相对偏差。利用式(11.1-3)，并且把 $\dot{m}_{b}$ 从方程(11.1-1)和方程(11.1-2)消去，就得到

$$
\frac {\overline {{M}} _ {g}}{\dot {m}} \frac {d \psi}{d t} + \psi + 1 = \left(1 - \frac {d \tau}{d t}\right) [ \eta (t - \tau) + 1 ] \tag {11.1-4}
$$

为了计算 $\frac{d\tau}{dt}$ ，就必须引进克洛科的压力与时滞相关的概念。假定液体燃料达到燃烧临界状态的质量速率是 $f(p)$ ，那么，时滞 $\tau$ 就由下列公式确定

$$
\int_ {t - \tau} ^ {t} f (p) d t = \text { const } \tag {11.1-5}
$$

可以把常数看做是为了把单位质量的喷入的冷燃料变到即将燃烧的状态所必须加进去的热量。 $f(p)$ 的物理意义就是：从热燃气到喷入的液体燃料的传热速率。把方程(11.1-5)对 t 微分就得

$$
[ f (p) ] _ {t} - [ f (p) ] _ {t - \tau} \left(1 - \frac {d \tau}{d t}\right) = 0 \tag {*}
$$

现在我们就可以明确地引进离开均匀稳定状态的微小扰动的概念。假设压力 p 与稳态值 $\overline{p}$ 之间的偏差相当小。那么 $f(p)$ 在时刻 t 的值以及 $f(p)$ 在时刻 $t-\tau$ 的值都可以用 $\overline{p}$ 附近的泰勒级数表示。如果不考虑级数中二次和二次以上的方幂，则有

$$
[ f (p) ] _ {t} = f (\overline {{p}}) + \overline {{p}} \left[ \frac {d f}{d p} \right] _ {p = \overline {{p}}} \psi (t)
$$

和

$$
[ f (p) ] _ {t - \tau} = f (\bar {p}) + \bar {p} \left[ \frac {d f}{d p} \right] _ {p = \bar {p}} \psi (t - \tau) \quad (* *)
$$

以上方程中的 $\tau$ 是相当于平均压力 $\overline{p}$ 的时滞，所以是一个常数。把（ $*\ast$ )的两个关系式相除，再利用（ $*$ )的关系就得出下列近似公式

$$
1 - \frac {d \tau}{d t} = 1 + \left[ \frac {d \log f}{d \log p} \right] _ {p = - p} [ \psi (t) - \psi (t - \tau) ] \tag {11.1-6}
$$

把方程(11.1-4)和(11.1-6)合并起来，并且略去二次项，就得出下列方程

$$
\frac {d \varphi}{d z} + \varphi = u (z - \delta) + n [ \varphi (z) - \varphi (z - \delta) ] \tag {11.1-7}
$$

在这个方程里

$$
n = \left(\frac {d \log f}{d \log p}\right) _ {p = \overline {{p}}} \tag {11.1-8}
$$

$$
\theta_ {g} = \frac {\overline {{M}} _ {g}}{\dot {\overline {{m}}}}, \quad z = \frac {t}{\theta_ {g}}, \quad \delta = \frac {\tau}{\theta_ {g}} \tag {11.1-9}
$$

而

$$
\varphi (z) = \varphi \left[ \frac {t}{\theta_ {g}} \right] = \psi (t)
$$

$$
\mu (z - \delta) = \mu \left[ \frac {1}{\theta_ {\mathrm{g}}} (t - \tau) \right] = \eta (t - \tau)
$$

$\theta_{g}$ 是发动机内的燃气的质量的平均值与流过发动机的燃气的平均质量速率的比值，因此它也就是热燃气从被燃烧产生到经过喷口喷射出去的平均时间，所以 $\theta_{g}$ 就称为“燃气通过时间”。在以下的计算中，我们就用这个基本的时间常数作为测量时间的单位。z 是无量纲的时间变数。 $\delta$ 是燃烧的无量纲的时滞常数。

如果 n 是一个与 $\overline{p}$ 无关的常数, 那么 $f(p)$ 就与 $p^{n}$ 成正比。这就是克洛科所假设的 $f(p)$ 的形状。现在, 我们把问题提得稍微普遍一些: $f(p)$ 是任意的; n 是由 方程(11.1-8)计算的；因而也就是 $\overline{p}$ 的函数。如果把 $f(p)$ 看作是从热燃气到雾状的液体燃料的传热速率，那么，关于传热的物理定律指出,n 的值在 1/2 与 1 之间。

这样，我们就建立了描述燃烧室中压力变化规律的方程(11.1-7)。

#### 11.2 时滞系统的运动规律

在上一节，我们推导了火箭发动机燃烧室中压力变化的运动方程(11.1-7),这是一个一阶常系数微分差分方程。现在采用常用的符号 t 代替时间变量 z,用 $\tau$ 代替时滞量 $\delta$ ,于是方程(11.1-7)可改写为

$$
\frac {d \varphi}{d t} = (n - 1) \varphi (t) - n \varphi (t - \tau) + \mu (t - \tau)
$$

由此可见，压力变化的趋势（方程左端）不仅依赖于当时的压力 $\varphi(t)$ ，而且明显地依赖于过去的历史状况 $\varphi(t-\tau)$ 和 $\mu(t-\tau),\tau>0$ 。这样，与微分方程就有一个根本的差别，为了求解方程式(11.1-7)初值不能只给在初始瞬时 $t=t_{0}$ ，而必须给在一个区间上，例如给定

$$
\varphi (t) = \psi (t), \quad t _ {0} - \tau \leqslant t \leqslant t _ {0}
$$

一般来讲，时滞系统的运动都可以用一阶微分差分方程组来描述，如果将时间坐标原点向右移动 $t_{0}-\tau$ ,那么初始条件就给在区间 $0 \leqslant t \leqslant \tau$ 上。本节内我们先一般地讨论具有一个常时滞量 $\tau$ 的线性常系数系统，看看它们具有何种特性。假定有任一个具有时滞因素的线性系统，其运动方程为

$$
\frac {d y _ {i}}{d t} = \sum_ {j = 1} ^ {n} a _ {i j} y _ {j} (t) + \sum_ {j = 1} ^ {n} b _ {i j} y _ {j} (t - \tau) + u _ {i} (t), \quad t > \tau
$$

$$
y _ {i} (t) = \varphi_ {i} (t), \quad 0 \leqslant t \leqslant \tau
$$

$$
i = 1, 2, \dots , n
$$

写成向量和矩阵的形式即为

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} (t) + B \mathbf {y} (t - \tau) + \mathbf {u} (t), \quad t > \tau \tag {11.2-1}
$$

$$
\mathbf {y} (t) = \varphi (t), \quad 0 \leqslant t \leqslant \tau \tag {11.2-2}
$$

其中 $\mathbf{y}(t)$ , $\varphi(t)$ 和 $\mathbf{u}(t)$ 为 n 维向量函数, A 和 B 为 $n \times n$ 矩阵, $\mathbf{u}(t)$ 称为驱动函数, $\varphi(t)$ 称为初始函数, 它定义在初始区间 $[0, \tau]$ 上。当然, 对于变时滞的情形, 即 $\tau$ 是 t 的函数 $\tau(t)$ 时, 方程

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} (t) + B \mathbf {y} (t - \tau (t)) + \mathbf {u} (t)
$$

的初始区间由初始时刻 $t_{0}$ 及 $t_{0}$ 处的延迟时间 $\tau(t_{0})$ 而定。初始函数给定在初始区间 $E_{t_{0}}$ 上，例如

$$
\mathbf {y} (t) = \varphi (t), \quad t \in E _ {t _ {0}}
$$

$E_{t_{0}}$ 是由 $t=t_{0}$ 及 $t_{0}+\tau(t_{0})$ 的点组成。

这一节里我们将讨论满足方程(11.2-1)和初始条件式(11.2-2)的解的存在性及解的形式问题。为了便于叙述，我们先定义几个基本概念。首先必须指出，初始条件式(11.2-2)，即函数 $\varphi(t)$ 实际上不可能是任意的。既然它代表系统的初始状态， $\varphi(t)(0 \leqslant t \leqslant \tau)$ 必然为“足够好”的一条曲线。由于 $\varphi(t)$ 的性质对系统在 $\tau$ 以后的运动有很大影响，下面我们将指出 $\varphi(t)$ 与 $y(t)$ 之间的某些简单关系。

如果函数 $f(t)$ 在开区间 $t_1 < t < t_2$ 上有 $K$ 阶连续导数，则称函数 $f(t)$ 是 $C^k(t_1, t_2)$ 类的，记为 $f(t) \in C^k(t_1, t_2)$ 。在方程(11.2-1)和(11.2-2)中如果 $\pmb{u}(t)$ 是 $C^0(0, \infty)$ 类函数， $\varphi(t)$ 是 $C^0[0, \tau]$ 类函数，那么在 $t \geqslant 0$ 上存在唯一的连续函数 $\mathbf{y}(t)$ ，它满足初始条件式(11.2-2)且在 $t > \tau$ 时满足方程(11.2-1)。如果 $\pmb{u}(t)$ 属于 $C^1(0, \infty)$ 类和 $C^2(2\tau, \infty)$ 类，那么解 $\mathbf{y}(t)$ 就是 $C^1(\tau, \infty)$ 类的函数。如果初始函数 $\varphi(t)$ 是 $C^1[0, \tau]$ 类函数，而且在 $t = \tau$ 时有

$$
\frac {d \varphi (\tau)}{d \tau} = A \varphi (\tau) + B \varphi (0) + \boldsymbol {u} (\tau) \tag {11.2-3}
$$

那么解的一阶导数 $\dot{\mathbf{y}}(t)$ 在 $\tau$ 处连续，即 $\mathbf{y}(t)$ 是 $C^{1}[0,\infty)$ 类的函数 $^{[1]}$ 。

这样，无论对哪一类初始条件，和对增长速度不快于某一指数幂的 $\boldsymbol{u}(t)$ ,我们就可以利用拉氏变换的方法对方程(11.2-1)求解。

利用分部积分可以得到

$$
\int_ {\tau} ^ {\infty} \mathbf {y} (t - \tau) e ^ {- s t} d t = e ^ {- \tau s} \int_ {0} ^ {\infty} \mathbf {y} (t) e ^ {- s t} d t \tag {11.2-4}
$$

和

$$
\int_ {\tau} ^ {\infty} \dot {\mathbf {y}} (t) e ^ {- s t} d t = - \varphi (\tau) e ^ {- \tau s} + s \int_ {0} ^ {\infty} \mathbf {y} (t) e ^ {- s t} d t - s \int_ {0} ^ {\tau} \varphi (t) e ^ {- s t} d t \tag {11.2-5}
$$

将方程(11.2-1)乘以 $e^{-st}$ ，并从 $\tau$ 到 $\infty$ 对 t 积分，将式(11.2-4)和(11.2-5)代入就得到

$$
D (s) \int_ {0} ^ {\infty} \mathbf {y} (t) e ^ {- s t} d t = \mathbf {p} (s) + \mathbf {q} (s) \tag {11.2-6}
$$

其中

$$
D (s) = s E - A - B e ^ {- \tau s} \tag {11.2-7}
$$

$$
\boldsymbol {p} (s) = e ^ {- \tau s} \varphi (\tau) + (s E - A) \int_ {0} ^ {\tau} \varphi (t) e ^ {- s t} d t \tag {11.2-8}
$$

$$
\boldsymbol {q} (s) = \int_ {\tau} ^ {\infty} \boldsymbol {u} (t) e ^ {- s t} d t \tag {11.2-9}
$$

若 $D(s)$ 的逆矩阵存在, 则

$$
\int_ {0} ^ {\infty} \mathbf {y} (t) e ^ {- s t} d t = D ^ {- 1} (s) [ \mathbf {p} (s) + \mathbf {q} (s) ] \tag {11.2-10}
$$

行列式 $\det D(s)$ 称为方程 (11.2-1) 的特征函数, 方程 $\det D(s)=0$ 称为特征方程, 特征方程的根称为特征根。

特征方程是一个超越代数方程，在复 S 平面上一般有无穷多个根，记为 $s_{k}$ ( $k=1,2,\cdots$ )，而特征方程在任意半平面 $\mathrm{Re}s > \sigma$ ( $\sigma$ 是任意实数)，内只有有限个根。这只要在该半平面内以原点为中心的充分大的圆内部分利用特征函数的解析性质，在圆外部分利用儒歇 (Rouchi) 定理 $^{[19]}$ 就可看出。因此总可以找到这样的常数 c，使

$$
\mathrm{Re} s _ {k} <   c, \quad k = 1, 2, \dots \tag {11.2-11}
$$

因而就可以通过对式(11.2-10)的拉氏反变换得到解 $y(t)$

$$
\mathbf {y} (t) = \frac {1}{2 \pi i} \int_ {(C)} e ^ {s t} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] d s, \quad t > 0 \tag {11.2-12}
$$

这里，积分路径 $(C)$ 满足式(11.2-11)。这就是满足初始条件式(11.2-2)，方程(11.2-1)的解的一般形式。

式(11.2-12)可以展开为级数形式。以原点为中心作一系列圆围道 $C_{1}$ ， $C_{2}$ ，…， $C_{l}$ ， $C_{l+1}$ ，…，使

(1) $C_{l} \subset C_{l+1}, (l=1,2,\cdots)$ 。

(2) $C_{l}$ 上没有特征根。

(3) 在 $C_{l}$ 与 $C_{l+1}$ 之间只有有限个特征根。

圆 $C_{l}$ 上位于 $\operatorname{Re}s > c$ 的部分记为 $C_{l}^{+}$ ，圆 $C_{l}$ 上位于 $\operatorname{Re}s < c$ 的部分记为 $C_{l}^{-}$ ，那么

$$
\begin{array}{l} \int_ {c _ {l}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s = \int_ {c _ {l} ^ {+}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s \\ + \int_ {c _ {l} ^ {-}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s \tag {11.2-13} \\ \end{array}
$$

可以证明，当 t 足够大时

$$
\lim _ {t \rightarrow \infty} \int_ {c _ {l} ^ {-}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s = 0 ^ {[ 1 ]}, \quad t > n \tau \tag {11.2-14}
$$

又根据留数定理有

$$
\frac {1}{2 \pi i} \int_ {c _ {l}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s = \sum_ {s _ {k} \in C _ {l}} \operatorname{Re} _ {s _ {k}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} \tag {11.2-15}
$$

和

$$
\lim _ {t \rightarrow \infty} \int_ {c _ {l} ^ {+}} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s = \int_ {(C)} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s \tag {11.2-16}
$$

因而

$$
\frac {1}{2 \pi i} \int_ {(C)} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t} d s = \lim _ {l \rightarrow \infty} \sum_ {s _ {k} \in C _ {l}} \operatorname{Re} _ {s _ {k}} D ^ {- 1} (s) [ \boldsymbol {p} _ {0} (s) + \boldsymbol {q} (s) ] e ^ {s t}
$$

利用式(11.2-12)即得

$$
\mathbf {y} (t) = \lim _ {l \rightarrow \infty} \sum_ {s _ {k} \in C _ {l}} \operatorname{Res} D ^ {- 1} (s) [ \boldsymbol {p} (s) + \boldsymbol {q} (s) ] e ^ {s t}, \quad t > n \tau \tag {11.2-17}
$$

而 $D^{-1}(s)[\pmb {p}(s) + \pmb {q}(s)]e^{st}$ 在 $s_k$ 的留数具有

$$
\boldsymbol {e} ^ {s _ {k} t} \boldsymbol {p} _ {k} (t)
$$

的形式，其中 $s_{k}$ 为特征根, $\boldsymbol{p}_{k}(t)$ 为多项式向量，其幂次小于 $s_{k}$ 的重数。因此 $\boldsymbol{y}(t)$ 可表示为

$$
\mathbf {y} (t) = \lim _ {l \rightarrow \infty} \sum_ {s _ {k} \in C _ {l}} e ^ {s} k ^ {t} \boldsymbol {p} _ {k} (t), \quad t > n \tau \tag {11.2-18}
$$

它在任何有限闭区间

$$
t _ {0} \leqslant t \leqslant t _ {0} ^ {\prime}, \quad t _ {0} > n \tau \tag {11.2-19}
$$

上一致收敛。如果所有特征根都具有负实部，即

$$
\operatorname{Re} s _ {k} <   C <   0 \tag {11.2-20}
$$

那么，极限式(11.2-18)在区间

$$
t _ {0} \leqslant t <   \infty , \quad t _ {0} > n \tau \tag {11.2-21}
$$

上一致收敛。式(11.2-18)可进一步表示为

$$
\mathbf {y} (t) = \sum_ {k = 1} ^ {\infty} e ^ {s} k ^ {t} \mathbf {p} _ {k} (t) \tag {11.2-22}
$$

此级数的收敛性总可得到保证。

#### 11.3 时滞系统的运动稳定性

这一节我们将一般地讨论常系数常时滞系统的稳定性问题，这对我们讨论具体问题时在方法和概念上会有所帮助。现研究齐次方程组

$$
\frac {d x (t)}{d t} = A \boldsymbol {x} (t) + B \boldsymbol {x} (t - \tau), \quad t > t _ {0} + \tau
$$

$$
\boldsymbol {x} (t) = \varphi (t), \quad t _ {0} \leqslant t \leqslant t _ {0} + \tau \tag {11.3-1}
$$

这里仍然沿用李雅普诺夫稳定性定义作为研究系统稳定性的依据。由初始函数 $\varphi(t)$ 所决定的一个特定运动（未受扰运动) $x_0(t)$ 的稳定性定义可以这样叙述：若对任何正数 $\varepsilon > o$ ，总存在一个正数 $\delta$ ，当初始函数变为 $\psi(t)$ 并在区间 $t_0 \leqslant t \leqslant t_0 + \tau$ 内满足（按欧氏空间的向量范数）

$$
\| \boldsymbol {\psi} (t) - \varphi (t) \| <   \delta \tag {11.3-2}
$$

时，方程(11.3-1)相应的解 $\boldsymbol{x}_{1}(t)$ (受扰运动）在 $t \geqslant t_{0}$ 上都有

$$
\left\| \mathbf {x} _ {1} (t) - \mathbf {x} _ {0} (t) \right\| <   \varepsilon \tag {11.3-3}
$$

则称方程(11.3-1)的这一特定未受扰运动 $x_{0}(t)$ 是稳定的。反之，若对某个 $\varepsilon>0$ ，找不到这样的 $\delta>0$ ，则称未受扰运动 $x_{0}(t)$ 为不稳定。特别是，当运动 $x_{0}(t)$ 稳定，且

$$
\lim _ {t \rightarrow \infty} \boldsymbol {x} _ {1} (t) = \boldsymbol {x} _ {0} (t) \tag {11.3-4}
$$

时，则称 $\boldsymbol{x}_{0}(t)$ 为渐近稳定。

稳定的几何意义可由图 11.3-1 说明。图中粗实线表示由初始函数 $\varphi(t)$ 所决定的特定未受扰运动 $x_0(t)$ 。对于任意给定半径为 $\varepsilon$ ，球心随 $x_0(t)$ 迁移的 $\varepsilon$ 球体，可以在 $\varphi(t)$ 附近指定一个以 $\delta$ 为半径， $\varphi(t)$ 为球心的 $\delta$ 球体，使得在 $t_0$ 到 $t_0 + \tau$ 时间内以 $\varphi(t)$ 为球心的 $\delta$ 球体内的任何一条曲线作为初始轨迹的运动，在任何 $t \geqslant t_0$ 时刻都走不出 $x_0(t)$ 的 $\varepsilon$ 球体的范围时，则称运动 $x_0(t)$ 是稳定的。如果对 $x_0(t)$ 的某一个 $\varepsilon$ 球体，在 $\varphi(t)$ 附近找不到这样的 $\delta$ 球体，则称运动 $x_0(t)$ 不稳定。在 $x_0(t)$ 稳定的情况下，如果随着时间 $t$ 的增长， $x_1(t)$ 无限趋近于 $x_0(t)$ ，则称运动 $x_0(t)$ 为渐近稳定。

> 此处省略原书 **图 11.3-1**

与线性微分方程类似，线性微分差分方程也有这样的特点：要么全体解都稳定，要么全体解都不稳定。因为方程(11.3-1)由任何初始函数 $\varphi(t), t_{0} \leqslant t \leqslant t_{0} + \tau$ , 所决定的一个特定解 $x_{0}(t)$ , 通过下列变换

$$
\mathbf {y} (t) = \mathbf {x} _ {1} (t) - \mathbf {x} _ {0} (t) \tag {11.3-5}
$$

$y(t)$ 仍然满足方程组(11.3-1)，因而任一特定解 $x_{0}(t)$ 的稳定性问题就化为同一方程组的零解—— $y(t)=0$ 的稳定性问题。这样，若零解稳定，则全体解都稳定。反之，若零解不稳定，则全体解都不稳定。因而也就有系统稳定性的问题。下面我们只研究零解的稳定性。

这里还要特别指出运动稳定性与初始区间 $[t_0, t_0 + \tau]$ 的关系。对于线性常系数常时滞微分差分方程(11.3-1)来说，与线性常系数微分方程类似，稳定性与初始区间 $[t_0, t_0 + \tau]$ 无关。因为发生在任何区间 $[t_0, t_0 + \tau] (t \geqslant 0)$ 上的扰动 $\psi(t)$ 经过

变换

$$
\lambda = t - t _ {0}
$$

后就可变为在区间 $[0, \tau]$ 上的扰动

$$
\boldsymbol {\psi} (\lambda + t _ {0}) = \boldsymbol {f} (\lambda)
$$

所以，若对初始区间 $[0, \tau]$ 上的扰动，运动 $x_0(t)$ 是稳定的，那么，对任何初始区间 $[t_0, t_0 + \tau], t \geqslant 0$ 上的扰动，运动也都稳定。然而，对于变时滞系统则不然，若运动对初始区间 $E_{t_0}$ 上的扰动稳定，而对初始区间 $E_{t_1}(t_1 > t_0)$ 的扰动未必稳定。这样，稳定性定义就需要加强，只有对任何初始区间 $E_{t_1}(t_1 > t_0)$ 都能找到相应的 $\delta(\varepsilon)$ ，满足条件式(11.3-3)，才称它是稳定的。反之，只要对某个初始区间 $E_{t_1}(t_1 > t_0)$ ，找不到 $\delta(\varepsilon)$ ，满足条件式(11.3-3)，就称运动不稳定。

现在我们再来讨论线性常系数常时滞系统

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} (t) + B \mathbf {y} (t - \tau) + \mathbf {u} (t), \quad t > \tau \tag {11.3-6}
$$

满足初始条件

$$
\mathbf {y} (t) = \varphi (t), \quad 0 \leqslant t \leqslant \tau \tag {11.3-7}
$$

的运动稳定的条件。这里，我们所关心的仍然是渐近稳定问题。与通常无时滞的线性系统类似，系统渐近稳定的充分必要条件是特征方程 $\det D(s)=0$ 的全部根都具有负实部。这一条件的必要性是显然的，因为只要有一个根具有正实部，例如 $Re_{sk}=\sigma_{k}>0$ ，那么，由展开式(11.2-22)可以看到， $y(t)$ 中包含有 $p_{k}(t)e^{\sigma_{k}t}$ 项。显然，不论初始偏差如何小，随着 t 之增长， $\|y(t)\|$ 总将无限增大，即

$$
\lim _ {t \rightarrow \infty} \| \mathbf {y} (t) \| = \infty
$$

所以解是不稳定的，当然也就不渐近稳定。这个准则的充分性，我们可以这样来说明，如果初始函数 $\varphi(t)$ 是定义在区间 $0 \leqslant t \leqslant \tau$ 上的 $C^{1}$ 类函数，设

$$
m = \max _ {0 \leqslant t \leqslant \tau} \| \varphi (t) \|
$$

那么可以证明

$$
\| \mathbf {y} (t) - \lim _ {l \rightarrow \infty} \sum e ^ {s _ {k} t} \boldsymbol {p} _ {k} (t) \| <   c _ {0} m e ^ {c t [ 1 ]}, \quad t > \tau \tag {11.3-8}
$$

这里 $c_0$ 为某正常数， $e^{s_k t} \pmb{p}_k(t)$ 是 $D^{-1}(s) \pmb{p}(s)$ 在特征根 $s_k$ 处的留数， $\pmb{p}_k(t)$ 是 $t$ 的多项式、其幂次小于 $s_k$ 的重数， $c$ 为任意实数，求和是对 $C_l$ 圆与半平面 $\operatorname{Res} > c$ 交集内的所有特征根进行的。如果所有特征根均具有负实部，那么可以选 $c < 0$ ，使所有特征根都位于半平面 $\operatorname{Res} < c < 0$ 内，这样式(11.3-8)就成为

$$
\| \mathbf {y} (t) \| <   c _ {0} m e ^ {c t}, \quad t > \tau \tag {11.3-9}
$$

因为 $c < 0$ ，所以

$$
\| \mathbf {y} (t) \| <   c _ {0} m, \quad t > \tau
$$

对于任意给定的 $\varepsilon$ ，只要选择 m 满足

$$
m = \frac {\varepsilon}{c _ {0}}
$$

那么 $y(t)$ 就满足

$$
\| \mathbf {y} (t) \| <   c _ {0} \frac {\varepsilon}{c _ {0}} = \varepsilon , t > \tau
$$

在有限时间 $0 \leqslant t \leqslant \tau$ 内， $\parallel y(t) \parallel$ 是有界的，而且选择适当的 m 可使

$$
\| \mathbf {y} (t) \| <   \varepsilon , \quad 0 \leqslant t \leqslant \tau
$$

因而总能找到这样的 $m$ ，在 $t \geqslant 0$ 内都满足

$$
\left\| \mathbf {y} (t) \right\| <   \varepsilon
$$

所以系统是稳定的。再利用式(11.3-9)便得到

$$
\lim _ {t \rightarrow \infty} \| \mathbf {y} (t) \| = \lim _ {t \rightarrow \infty} o m e ^ {c t} = 0 \tag {11.3-10}
$$

因而系统是渐近稳定的。

关于第 11.2 和第 11.3 节的详细论述，读者可参阅文献[4],那里还讨论了更为一般的时滞系统。

#### 11.4 萨奇(Satche)图

现在我们就以第 11.1 节的燃烧过程为例，分析它的稳定性。克洛科把燃料喷入速率是常数时的燃烧不稳定性称为固有不稳定性。如果喷入速率是一个与燃烧室压力 p 无关的常数，那么, $\mu\equiv0$ 。因此，根据方程(11.1-7),稳定性问题就由下列齐次方程限定:

$$
\frac {d \varphi}{d z} + (1 - n) \varphi (z) + n \varphi (z - \delta) = 0 \tag {11.4-1}
$$

也可以用前节内讨论过的拉氏变换的方法来处理方程(11.4-1)，作法和以前各章中处理没有时滞的方程的方法相同。事实上，安索夫(Ansoff)也用过这个方法 $^{[3]}$ 。然而，在目前的燃烧的稳定性问题里，基本方程没有驱动项，所以，可以用一个比较直接的解法，这个解法就是解线性微分差分方程的古典方法，作法是这样的：设

$$
\varphi (z) \cong e ^ {s z}
$$

于是得到特征方程

$$
s + (1 - n) + n e ^ {- \delta s} = 0 \tag {11.4-2}
$$

这是一个 s 的超越方程。燃烧的稳定性的条件就是: 方程(11.4-1)的根 s 的实数部分是负数。

也可以应用拉氏变换方法从方程(11.4-1)得出方程(11.4-2)来。假定 $\varphi(z)$ 的拉氏变换是 $\Phi(s)$ ，对方程(11.4-1)进行拉氏变换，就得到

$$
s \Phi (s) - \varphi (0) + (1 - n) \Phi (s) + n e ^ {- s \delta} \left[ \Phi (s) + \int_ {- \delta} ^ {0} \varphi \left(z ^ {\prime}\right) e ^ {- s z ^ {\prime}} d z ^ {\prime} \right] = 0
$$

如果 $\varphi(z)$ 的初始条件是所谓的零初始条件, 也就是说: $z \leqslant 0$ 时 $\varphi(z) = 0$ , 那么就有

$$
[ s + (1 - n) + n e ^ {- \delta s} ] \Phi (s) = 0
$$

于是，我们就得到方程(11.4-2)。这里的 $s$ 和以前各章中的变数 $s$ 具有相同的“意义”。这两者之间的唯一区别，就是这里的 $s$ 已经通过式(11.1-9)的 $\theta_{g}$ 的变换成为无量纲的量了。也可以看到这样一个有趣的事实：如果方程(11.4-1)是一个在方程右端有驱动项的非齐次方程，那么，对这个方程施行拉氏变换法以后，所得到的方程仍然是非齐次的。如果把 $\varphi(z)$ 看做是系统在单位阶跃函数作用下的输出，系统的传递函数就会是

$$
F (s) = \frac {1}{s + (1 - n) + n e ^ {- s \delta}}
$$

这个 $F(s)$ 又是一个超越的传递函数的例子。

克洛科把方程(11.4-2)的实数部分和虚数部分分离开来得到两个方程，根据这两个方程他解出了方程的复数根 s。然而，如果只对系统是否稳定的问题感兴趣，那么，根据第 11.3 节关于稳定条件的结论我们仍然可以成功地利用第 4.3 节的柯西定理。设

$$
G (s) = e ^ {- \delta s} - \left[ - \frac {1 - n}{n} - \frac {s}{n} \right] \tag {11.4-3}
$$

于是，系统的稳定性问题就归结为 $G(s)$ 在复 $S$ 平面的右半部有没有零点的问题。当 $s$ 在一条包围右半平面的闭合曲线上转动一周时，我们只要把变数 $G(s)$ 的相应的变化情况加以考察，就能够回答系统是否稳定的问题。如果向量 $G(s)$ 旋转的总圈数是某一个数，按照柯西定理这个数就是 $G(s)$ 在右半 $S$ 平面上的零点个数与极点个数的差。既然，在全 $S$ 平面上 $G(s)$ 显然没有极点，所以， $G(s)$ 旋转的总圈数就是零点的个数。因此，如果系统是稳定的，那么，当 $s$ 在上述的闭合曲线上转动一周时， $G(s)$ 旋转的总圈数一定是零。所以，可以用描画乃氏图的办法来回答稳定性的问题。

但是，对方程(11.4-3)所表示的 $G(s)$ 直接应用上述的方法是很不方便的，因为时滞项 $e^{-\delta s}$ 的存在，这个表示式是比较复杂的。对于这样一些有时滞的系统，萨奇(Satche)提出了一个富有创造性的巧妙的处理方法[14]：不直接处理 $G(s)$ 本身，而把它分成两部分

$$
G (s) = g _ {1} (s) - g _ {2} (s) \tag {11.4-4}
$$

其中

$$
g _ {1} (s) = e ^ {- \delta s}
$$

$$
g _ {2} (s) = - \frac {1 - n}{n} - \frac {s}{n} \tag {11.4-5}
$$

> 此处省略原书 **图 11.4-1**

这样一来，向量 $G(s)$ 就是一个顶点在 $g_{1}(s)$ 而起点在 $g_{2}(s)$ 的向量了。如果 $s$ 在虚轴上变动， $g_{1}(s)$ 的图线就是一个单位圆。如果 $s$ 在大的半圆周上， $g_{1}(s)$ 就在单位圆的内部。当 $s$ 在虚轴上变动的时候， $g_{2}(s)$ 就是一条与虚轴平行的直线（图 11.4-1）。当 $s$ 在大的半圆周上变动时， $g_{2}(s)$ 就在左方描画成一个大的半圆周，这个半圆周与 $s$ 所在的那个半圆周恰好组成一个圆周。只要稍微考虑一下，就可以想到：如果希望对于任何时滞 $\delta$ 的值， $G(s)$ 旋转的总圈数都是零，那么， $g_{2}(s)$ 图线就必须完全在 $g_{1}(s)$ 图线的外面。这也就是 说，对于本质上稳定的系统，即绝对稳定系统 $^{①}$ 来说，必须有

$$
\frac {1 - n}{n} > 1 \quad \text {或者} \quad \frac {1}{2} > n > 0 \tag {11.4-6}
$$

现在，很容易看出把 $G(s)$ 分解为 $g_{1}(s)$ 和 $g_{2}(s)$ 两部分的做法可以使得相当的两条图线都比原来的 $G(s)$ 图线简单得多。 $g_{1}(s)$ 的图线与 $g_{2}(s)$ 的图线组成的图线就称为萨奇图。

如果 $n > \frac{1}{2}$ , $g_{1}(s)$ 的图线就与 $g_{2}(s)$ 的图线相交, 因而就有一部分 $g_{2}(s)$ 点在图 11.4-2 的单位圆的内部, 但是, 只要相当于这些 $g_{2}(s)$ 的 $g_{1}(s)$ 点都在 $g_{2}(s)$ 点的右方, $G(s)$ 图线就不绕原点转, 系统仍然是稳定的。如果对于同一个 $s = i\omega^{*}$ , $g_{2}(s)$ 与 $g_{1}(s)$ 重合, 则 $G(s)$ 图线就通过原点, 系统处于临界稳定状态。这时, 必须满足条件

$$
\mid g _ {2} (i \omega^ {*}) \mid = 1
$$

$$
\arg g _ {1} \left(i \omega^ {*}\right) = \arg g _ {2} \left(i \omega^ {*}\right)
$$

再从式(11.4-5)就可求出临界稳定状态下的 $\omega^{*}$ 和 $\delta^{*}$

$$
\omega^ {*} = \sqrt {2 n - 1} \tag {11.4-7}
$$

> 此处省略原书 **图 11.4-2**

$$
\delta^ {*} = \frac {\cos^ {- 1} \left[ - \frac {1 - n}{n} \right]}{\sqrt {2 n - 1}} = \frac {1}{\sqrt {2 n - 1}} \left[ \pi - \cos^ {- 1} \left(\frac {1 - n}{n}\right) \right] \tag {11.4-8}
$$

所以当 $\delta=\delta^{*}$ 时， $\varphi(z)$ 有一个频率是 $\omega^{*}$ 的振荡解。因而 $\delta^{*}$ 是无量纲的临界时滞，而 $\omega^{*}$ 是无量纲的临界频率。当 $\delta<\delta^{*}$ ，也就是说当

$$
\cos (\delta \sqrt {2 n - 1}) > - \frac {1 - n}{n}
$$

时，系统就是稳定的。

#### 11.5 有反馈伺服机构的火箭发动机的系统动力学性质

现在我们来考虑图 11.5-1 所画的火箭发动机系统, 这个系统包含三部分: 火箭发动机, 供应燃料的馈送机构（燃料泵和附属的传导装置）及反馈伺服机构。为了近似地表示出实在的导管的弹性效应, 我们可以假想在刚硬的导管的中点（燃料泵与燃料喷嘴之间）有一个附有弹簧活塞的容器, 在喷嘴附近还有另外一个由伺服机构控制的容器。传感器（测量仪器）测量了燃烧室的压力, 测量的结果经过一个放大器而成为伺服机构的输入信号。如果设计者已经把燃料的馈送机构和火箭发动机本身的设计完全确定, 不允许再加以更改, 现在的问题就是: 是否可以设计一个使整个系统稳定的合适的放大器? 因为关于燃烧的时滞还没有确切的知识, 所以, 在进行实际设计的时候, 我们就必须设法使系统无条件地稳定, 也就是说, 对于任何的时滞 $\delta$ 的值系统都是稳定的。

> 此处省略原书 **图 11.5-1**

假定 $\dot{m}_{0}$ 是流出燃料泵的燃料的瞬时质量速率； $p_{0}$ 是燃料泵的出口处的瞬时压力，燃料流动的平均速率一定是 $\overline{\dot{m}}$ 。平均压力是 $\overline{p}_{0}$ 。燃料泵的特性可以用下列方程表示

$$
\frac {p _ {0} - \overline {{p}} _ {0}}{\overline {{p}} _ {0}} = - \alpha \frac {\dot {m} _ {0} - \overline {{\dot {m}}}}{\dot {m}} \tag {11.5-1}
$$

如果质量的流动的变化的时间速率比弹性波在液体中的传播速度小，但是比燃料泵的转速的缓慢的时间变化率大，那么，相当于常数转速的情况，燃料泵的压力-体积曲线在稳态工作点的斜率就是 $\alpha$ （这里所说的“体积”就是流出燃料泵的燃料按照体积计算的速率）。对于普通的离心泵来说， $\alpha$ 差不多等于 1。对于传输泵（输出的流量几乎是不变的泵）来说， $\alpha$ 非常大。对于等压泵或者简单的增压装置来说， $\alpha$ 等于零。

假设 $\dot{m}_{1}$ 是喷嘴与弹簧容器口之间的燃料流动的瞬时质量速率； $\chi$ 是容器的弹簧常数， $p_{1}$ 是作用在容器上的瞬时压力。于是就有

$$
\dot {m} _ {0} - \dot {m} _ {1} = \rho \chi \frac {d p _ {1}}{d t} \tag {11.5-2}
$$

这里的 $\rho$ 是燃料的密度, 它是一个常数。

在以下的计算里，由于摩擦力而在导管上引起的压力降落是忽略不计的。因此，压力差 $p_{0}-p_{1}$ 只是由流动的加速度引起的，也就是说

$$
p _ {0} - p _ {1} = \frac {l}{2 A} \frac {d \dot {m} _ {0}}{d t} \tag {11.5-3}
$$

这里的常数 A 是导管的横截面的面积; 常数 l 是导管的总长度。与此类似, 如果 $p_{2}$ 是控制容器上的瞬时压力, 也就有

$$
p _ {1} - p _ {2} = \frac {l}{2 A} \frac {d \dot {m} _ {1}}{d t} \tag {11.5-4}
$$

如果控制容器中所容纳的质量是 C, 那么

$$
\dot {m} _ {1} - \dot {m} _ {i} = \frac {d C}{d t} \tag {11.5-5}
$$

因为控制容器与燃料喷嘴非常接近，所以，在燃料从控制容器流到燃料喷嘴的过程中，由于质量而引起的惯性效应是可以忽略的。因此

$$
p ^ {2} - p = \frac {1}{2} \frac {\dot {m} _ {i} ^ {2}}{\rho A _ {i} ^ {2}} \tag {11.5-6}
$$

其中的 $A_{i}$ 是燃料喷嘴的有效开口面积。因为在稳定状态下压力 $\overline{p}_{0}$ 与 $\overline{p}$ 的差 $\Delta\overline{p}$ 是

$$
\overline {{p}} _ {0} - \overline {{p}} = \Delta \overline {{p}} = \frac {1}{2} \frac {\overline {{\dot {m}}} ^ {2}}{\rho A _ {i} ^ {2}} \tag {11.5-7}
$$

所以在计算中可以把 $A_{i}$ 消去。方程(11.5-1)和(11.5-7)就描述了燃料馈送系统的动力学性质。直接利用消去某些变数的计算方法，就得出 $m_{i}, p$ ，与 C 之间的关系式。为了把这个关系写成无量纲的形式，我们引进下列几个参数

$$
P = \frac {\overline {{p}}}{2 \Delta \overline {{p}}}, \quad E = \frac {2 \Delta \overline {{p}}}{\overline {{m}} \theta_ {g}} \rho \chi , \quad J = \frac {l \overline {{\dot {m}}}}{2 \Delta \overline {{p}} A \theta_ {g}} \tag {11.5-8}
$$

以及

$$
\kappa = \frac {C}{\overline {{\dot {m}}} \theta_ {\mathrm{g}}} \tag {11.5-9}
$$

这里的 $\theta_{g}$ 就是方程(11.1-9)所给的燃气通过时间。这样一来，联系 $\varphi, \mu$ 与 $\kappa$ 的无量纲方程就是

$$
\begin{array}{l} P \left\{1 + \alpha E \left(P + \frac {1}{2}\right) \frac {d}{d z} + \frac {1}{2} J E \frac {d ^ {2}}{d z ^ {2}} \right\} \varphi + \left\{\left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \right. \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] \frac {d}{d z} + \left[ \frac {1}{2} \alpha J E \left(P + \frac {1}{2}\right) + \frac {1}{2} J E \right] \frac {d ^ {2}}{d z ^ {2}} + \frac {1}{4} J ^ {2} E \left. \frac {d ^ {3}}{d z ^ {3}} \right\} \mu \\ + \left\{\alpha \left(P + \frac {1}{2}\right) \frac {d}{d z} + J \frac {d ^ {2}}{d z ^ {2}} + \frac {1}{2} \alpha J E \left(P + \frac {1}{2}\right) \frac {d ^ {3}}{d z ^ {3}} + \frac {1}{4} J ^ {2} E \frac {d ^ {4}}{d z ^ {4}} \right\} \kappa = 0 \tag {11.5-10} \\ \end{array}
$$

这里的 z 就是方程(11.1-9)所定义的无量纲时间变数。

伺服控制的动力学性质是由下列各种因素的综合所确定的：测量压力的仪器的特性，放大器的反应性能以及伺服机构的特性。伺服控制的总的动力学性质是由下列算子方程表示的

$$
F \left(\frac {d}{d z}\right) \varphi = \kappa \tag {11.5-11}
$$

这里的 F 是两个多项式的比值，而且分母的次数高于分子的次数。

方程(11.1-7)，(11.5-10)和(11.5-11)是三个变数 $\varphi,\mu,\kappa$ 的三个方程。既然，它们都是常系数的方程，这些变数的适当的形式就是

$$
\varphi = a e ^ {s z}, \quad \mu = b e ^ {s z}, \quad \kappa = c e ^ {s z} \tag {11.5-12}
$$

把方程(11.5-12)代入方程(11.1-7)，(11.5-10)和(11.5-11)，就得到 a, b, c 的三个齐次方程。所以我们有

$$
\begin{array}{l} a [ s + (1 - n) + n e ^ {- \delta s} ] - b e ^ {- \delta s} = 0 \\ P \left\{1 + \alpha E \left(P + \frac {1}{2}\right) s + \frac {1}{2} J E s ^ {2} \right\} a + \left\{\left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \right. \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] s + \left[ \frac {1}{2} \alpha J E \left(P + \frac {1}{2}\right) + \frac {1}{2} J E \right] s ^ {2} + \frac {1}{4} J ^ {2} E s ^ {3} \Bigg \} b \\ + s \left\{\alpha \left(P + \frac {1}{2}\right) + J s + \frac {1}{2} \alpha J F \left(P + \frac {1}{2}\right) s ^ {2} + \frac {1}{4} J ^ {2} E s ^ {3} \right\} c = 0 \\ F (s) a - c = 0 \\ \end{array}
$$

为了使 a, b, c 三个数不全是零, 它们的系数所组成的行列式就必须等于零。系数行列式除以 n 后, 就有

$$
\begin{array}{l} E (s) = \left[ \frac {s}{n} + \frac {1 - n}{n} \right] \left\{\frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] s ^ {2} \right. \\ \left. + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \right\} \\ + e ^ {- \delta s} \left\{\frac {1}{4} J ^ {2} E s ^ {2} + \left[ \frac {1}{2} J E \left(1 + \alpha \left(P + \frac {1}{2}\right)\right) + \frac {1}{2 n} J E P \right] s ^ {2} \right. \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) + J + \frac {\alpha E P}{n} \left(P + \frac {1}{2}\right) \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) + \frac {P}{n} \right] \\ + \frac {s F (s)}{n} \left[ \frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} \alpha J E \left(P + \frac {1}{2}\right) s ^ {2} \right. \\ \left. + J _ {s} + \alpha \left[ P + \frac {1}{2} \right] \right\} \\ = 0 \tag {11.5-13} \\ \end{array}
$$

为简单起见，我们写成下列形式

$$
E (s) = L _ {0} (s) + H (s) e ^ {- \delta s} \tag {$11.5-13^{\prime$}}
$$

其中

$$
\begin{array}{l} L _ {0} (s) = \left[ \frac {s}{n} + \frac {1 - n}{n} \right] \left\{\frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] s ^ {2} \right. \\ \left. + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \right\} \\ H (s) = \frac {1}{4} J ^ {2} E s ^ {3} + \left\{\frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] + \frac {1}{2 n} J E P \right\} s ^ {2} + \left[ \alpha E \left(P + \frac {1}{2}\right) \right. \\ + J + \frac {\alpha E P}{n} \left[ P + \frac {1}{2}\right) ] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) + \frac {P}{n} \right] + \frac {s F (s)}{n} \left[ \frac {1}{4} J ^ {2} E s ^ {3} \right. \\ + \frac {1}{2} \alpha J E \left[ P + \frac {1}{2} \right] s ^ {2} + J s + \alpha \left[ P + \frac {1}{2} \right] \Bigg ] \tag {11.5-14} \\ \end{array}
$$

式(11.5-13)就是用来确定指数 s 的特征方程。于是 $F(s)$ 就被认为是反馈部分的总传递函数。整个系统的稳定性问题就决定于方程(11.5-13)是否有实部为正的根。

#### 11.6 没有反馈伺服机构时的不稳定性

如果没有反馈伺服机构，那么，只要在方程(11.5-13)中使 $F(s)=0$ , 就得出系统的特征方程。和通常的情况一样, 我们假设方程(11.5-13)中与 $e^{-\delta s}$ 相乘的部分 $H(s)$ 在右半 S 平面没有零点。因此, 就可以用 $H(s)$ 除方程(11.5-13)而不会使除得的商数在右半 S 平面上有极点。这样一来, 就又得到了描绘萨奇图所需要的表示式

$$
G (s) = \frac {E (s)}{H (s)} = g _ {1} (s) - g _ {2} (s)
$$

$$
g _ {1} (s) = e ^ {- \delta s}
$$

所以 $g_{1}(s)$ 的图线仍是一个“单位圆”，然而 $g_{2}(s)$ 就复杂得多了

$$
\begin{array}{l} g _ {2} (s) = - \left[ \frac {s}{n} + \frac {1 - n}{n} \right] \\ \times \left\{\frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] s ^ {2} + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] s \right. \\ + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \} \div \left\{\frac {1}{4} J ^ {2} E s ^ {3} - \frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) + \frac {P}{n} \right] s ^ {2} \right. \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) \left(1 + \frac {P}{n}\right) + J \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) + \frac {P}{n} \right] \Bigg \} \tag {11.6-1} \\ \end{array}
$$

如果 s 是纯虚数, $s = i\omega$ , 那么, $g_{2}(s)$ 的图线在 x 轴上的“截距”的坐标就是方程 (11.6-1) 在 s = 0 时的值。也就是

$$
g _ {2} (0) = - \frac {1 - n}{n} \frac {1 + \alpha \left[ P + \frac {1}{2} \right]}{1 + \alpha \left[ P + \frac {1}{2} \right] + (P / n)} \tag {11.6-2}
$$

因为 $n, \alpha$ 和 $P$ 这三个参数都是正数，所以现在的 $g_{2}(0)$ 的绝对值小于方程(11.4-5)所给的 $g_{2}(0)$ 的绝对值，我们已经知道那个 $g_{2}(0)$ 的值是与系统的无条件稳定性有关系的。现在我们就看到，由于有了燃料馈送系统，结果就使得萨奇图的 $g_{2}(s)$ 图线更接近于 $g_{1}(s)$ 的单位圆图线。譬如说，如果不考虑馈送系统，那么，当 $n = \frac{1}{2}$ 时， $g_{2}(s)$ 图线就刚好与相当于发动机本身的单位圆图线相切。但是，如果把馈送系统也考虑进去， $g_{2}(s)$ 图线就与单位圆相交了，而且，当时滞 $\delta$ 超过某一个有限的数值时，系统就失去稳定性。因此，馈送系统的影响是不利于系统的稳定的。从方程(11.6-1)可得出对于 $s$ 的大的虚数值的渐近表示式(11.6-3)，考虑了这个表示式就会使我们更加确信上述的事实

$$
g _ {2} (i \omega) \cong - \left[ \frac {i \omega}{n} + \left(\frac {1 - n}{n} - \frac {2 P}{J n ^ {2}}\right) + \dots \right], | \omega | \gg 1 \tag {11.6-3}
$$

因此，对于 $s$ 的大虚数值来说， $g_{2}(s)$ 渐近地趋近于一条平行于虚轴的直线，这条直线在虚轴的左方，与虚轴的距离是

$$
\frac {1 - n}{n} - \frac {2 P}{J n ^ {2}}
$$

所以，还是可以看到，馈送系统的作用是使 $g_{2}(s)$ 图线更接近单位圆。

这样就很明显，如果参数 n 差不多等于 1/2,或者大于 1/2,就不可能把系统设计成无条件稳定的，因为在没有反馈伺服机构的情况下, $g_{1}(s)$ 图线与 $g_{2}(s)$ 图线总是相交的。

#### 11.7 有反馈伺服机构时系统的稳定性

如果方程(11.5-13)中 $H(s)$ 在右半 S 平面没有零点或极点, 那么从 $g_{1}(s)$ 和 $g_{2}(s)$ 的萨奇图就可以判断方程(11.5-13)在右半 S 平面有没有零点。

这时

$$
\begin{array}{l} g _ {1} (s) = e ^ {- \delta s} \\ g _ {2} (s) = - \left[ \frac {s}{n} + \frac {1 - n}{n} \right] \left\{\frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] s ^ {2} \right. \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) + J \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] \Bigg \} / H (s) \tag {11.7-1} \\ \end{array}
$$

这里的 $H(s)$ 就如式(11.5-14)所示。

当 s 在图 11.4-1 所画的路线上转动时， $g_{1}(s)$ 的图线仍然是一个单位圆。因此，如果相应的 $g_{2}(s)$ 图线完全在单位圆的外面，方程 (11.5-13) 就不会在右半 S 平面上有根。换句话说，如果在设计伺服控制部分的传递函数 $F(s)$ 的时候，使 $g_{2}(s)$ 图线完全在单位圆的外面（图 11.7-1），那么，对于任何的时滞值，系统都是稳定的。

> 此处省略原书 **图 11.7-1**

作为一个例子，我们取

$$
n = \frac {1}{2}, \quad P = \frac {3}{2}
$$

$$
J = 4
$$

$$
E = \frac {1}{4}
$$

$$
\alpha = 1
$$

$\alpha$ 的数值相当于燃料泵是一个离心泵的情形。如果没有伺服控制， $g_{2}(s)$ 就是

$$
g _ {2} (s) = - \frac {1}{2} \frac {(2 s + 1) (2 s ^ {3} + 3 s ^ {2} + 9 s + 6)}{s ^ {3} + 3 s ^ {2} + 6 s + 6}
$$

主要的兴趣在于 s 取纯虚数 $i\omega(\omega$ 是实数) 时的 $g_{2}(s)$ 的变化情况。因而

$$
\begin{array}{l} g _ {2} (i \omega) = - \frac {1}{2} \frac {(6 - 2 1 \omega^ {2} + 4 \omega^ {4}) (6 - 3 \omega^ {2}) + \omega^ {2} (2 1 - 8 \omega^ {2}) (6 - \omega^ {2})}{(6 - 3 \omega^ {2}) ^ {2} + \omega^ {2} (6 - \omega^ {2}) ^ {2}} \\ - \frac {1}{2} i \omega \frac {\left(2 1 - 8 \omega^ {2}\right) \left(6 - 3 \omega^ {2}\right) - \left(6 - 2 1 \omega^ {2} + 4 \omega^ {4}\right) \left(6 - \omega^ {2}\right)}{\left(6 - 3 \omega^ {2}\right) ^ {2} + \omega^ {2} \left(6 - \omega^ {2}\right) ^ {2}} \\ \end{array}
$$

图 11.7-2 中画出了这条图线的 $\omega > 0$ 的部分。可以明显地看到，如果时滞的值足够大，系统就会不稳定。从另一方面来看，如果考虑了伺服控制，而且假设 $g^{2}(s)$ 能够相应地变为

$$
g _ {2} (s) = - 2 \frac {(s + 2) (s + 3)}{(s + 6)}
$$

那么，正如图 11.7-2 所画的那样，新的 $g_{2}(s)$ 图线就完全在 $g_{1}(s)$ 的单位圆图线的外面，因而，现在的系统就是无条件稳定的。根据方程(11.6-1)和(11.7-1)直接加以计算，就知道反馈部分的传递函数 $F(s)$ 应当是

$$
F (s) = - 4. 8 7 5 \frac {(s + 1 . 0 5 2 8) \left(s ^ {2} + 0 . 7 1 6 4 s + 2 . 6 3 0 4\right)}{s (s + 2) (s + 3) (s + 0 . 5 3 3 2) \left(s ^ {2} + 0 . 4 6 6 8 s + 3 . 7 5 1 1\right)}
$$

所以，反馈部分具有第 3.3 节讨论过的积分线路的那种特性。如果测量燃烧室压力的传感器的反应性能和带动控制容器的伺服机构的特性都已经给定了，那么，我们就可能设计出一个放大器，使得总的传递函数接近于上面提到的传递函数 $F(s)$ ，用这个伺服控制系统就可以使燃烧过程得到稳定。

作为第二个例子，我们取

$$
n = \frac {1}{2}, \quad P = \frac {3}{2}, \quad J = 4, \quad E = \frac {1}{4}, \quad \alpha = 0
$$

因为 $\alpha=0$ ，所以燃料泵的出口压力 $p_{0}$ 是一个常数，即使燃料流出的速率发生变化的时候 $p_{0}$ 也不会变动。这就相当于简单的增压装置的情形。如果没有反馈伺服机构，则

$$
g _ {2} (s) = - \frac {1}{2} \frac {(2 s + 1) (2 s ^ {3} + s ^ {2} + 8 s + 2)}{s ^ {3} + 2 s ^ {2} + 4 s + 4}
$$

当 $s$ 是纯虚数时

$$
\begin{array}{l} g _ {2} (i \omega) = - \frac {1}{2} \frac {(4 - 2 \omega^ {2}) (2 - 1 7 \omega^ {2} + 4 \omega^ {4}) + \omega^ {2} (4 - \omega) ^ {2} (1 2 - 4 \omega^ {2})}{(4 - 2 \omega^ {2}) ^ {2} + \omega^ {2} (4 - \omega^ {2}) ^ {2}} \\ - \frac {1}{2} i \omega \frac {\left(4 - 2 \omega^ {2}\right) \left(1 2 - 4 \omega^ {2}\right) - \left(4 - \omega^ {2}\right) \left(2 - 1 7 \omega^ {2} + 4 \omega^ {4}\right)}{\left(4 - 2 \omega^ {2}\right) ^ {2} + \omega^ {2} \left(4 - \omega^ {2}\right) ^ {2}} \\ \end{array}
$$

这条 $g_{2}$ 的图线被画在图 11.7-3 上。很明显，如果没有伺服控制，而且时滞 $\delta$ 的值也足够大，燃烧就会是不稳定的。事实上，这个系统的稳定性能还不如前一个例子的系统好：也就是说，对于比较小的时滞值这个系统就会变为不稳定的。 $g_{2}$ 图线在 $\omega = 2$ 点附近的部分是特别有趣的。在 $\omega = 2$ 附近 $g_{2}$ 图线与 $g_{1}$ 的单位圆图线非常接近，如果时滞 $\delta$ 的值又能使得在 $\omega \simeq 2$ 时， $g_{1}(i\omega)$ 与 $g_{2}(i\omega)$ 也相当接近 $g_{1}(i\omega) \simeq g_{2}(i\omega)$ ，那么，在 $\omega \simeq 2$ 处就会发生一个几乎不衰减的振荡。这个临界的 $\delta$ 值显然小于那个由 $g_{2}$ 与单位圆在 $\omega \simeq 0.65$ 的实在的交点所确定的时滞 $\delta$ 的临界值。

> 此处省略原书 **图 11.7-2**

> 此处省略原书 **图 11.7-3**

为了实现无条件的稳定性，必须把 $g_{2}$ 图线移出单位圆，譬如说，如果希望把 $g_{2}$ 也变为与第一个例子中的那个图线完全相同的“稳定”的图线

$$
g _ {2} (s) = - 2 \frac {(s + 2) (s + 3)}{s + 6}
$$

计算的结果表明：传递函数 $F(s)$ 就必须是

$$
F (s) = - 4. 8 7 5 \frac {(s + 0 . 8 1 2 6) \left(s ^ {2} - 0 . 0 4 3 3 7 s + 2 . 6 5 0 6\right)}{s ^ {2} (s + 2) (s + 3) \left(s ^ {2} + 4\right)}
$$

所以，反馈部分必须具有二重积分线路那样的特性。而且，传递函数在 $\mp 2i$ 有两 个纯虚数的极点。因为我们在原有的系统中忽略了导管的摩擦阻尼的作用，所以在这里才对放大器发生了这个不现实的要求。在任何一个实际的系统中，导管的摩擦阻尼作用必然会把所需要的传递函数 $F(s)$ 中的这两个纯虚数极点消除掉，并且把它们变为两个复共轭的极点。

必须强调指出，利用反馈伺服机构来稳定燃烧过程的做法的优点就是：由于反馈伺服机构的可变化性很大，对于任何的时滞 $\delta$ 或 $\tau$ 的值，我们都可以使系统无条件地稳定。既然我们没有关于时滞的准确的数据，所以，这个实现无条件稳定性的可能性对于工程实际来说确实是十分重要的。不但如此，如果要求在参数 $n$ 发生任何的变化的情况下系统都是稳定的，我们也可以用以上这种伺服稳定的方法进行设计。由于物理学的理由， $n$ 可以取 $1/2$ 与 1 之间的一个值。我们来处理最坏的可能性 $n \cong 1$ ，并且在这种情形下进行设计，使系统是无条件稳定的。这样设计出来的系统对于所有可能的 $n$ 的值，当然都是稳定的。因此，即使不知道系统的确切的参数值，我们也还能保证反馈伺服机构的稳定作用。

#### 11.8 利用萨奇图判断时滞系统稳定性的一般准则

在以前的伺服稳定作用的讨论中，我们都假定方程(11.7-1)的多项式 $H(s)$ 在右半 S 平面上没有零点和极点。然而，事实并不一定是这样的。所以，首先我们应该研究 $H(s)$ 在右半 S 平面的零点和极点的个数。

我们把方程(11.5-14)简写为

$$
H (s) = H _ {0} (s) + F (s) I (s) = 1 + L (s)
$$

其中

$$
\begin{array}{l} H _ {0} (s) = \frac {1}{4} J ^ {2} E s ^ {3} + \left\{\frac {1}{2} J E \left[ 1 + \alpha \left(P + \frac {1}{2}\right) \right] + \frac {1}{2 n} J E P \right\} s ^ {2} \\ + \left[ \alpha E \left(P + \frac {1}{2}\right) + J + \frac {\alpha E P}{n} \left(P + \frac {1}{2}\right) \right] s + \left[ 1 + \alpha \left(P + \frac {1}{2}\right) + \frac {P}{n} \right] \\ I (s) = \frac {s}{n} \left[ \frac {1}{4} J ^ {2} E s ^ {3} + \frac {1}{2} \alpha J E \left(P + \frac {1}{2}\right) s ^ {2} + J E + \alpha \left(P + \frac {1}{2}\right) \right] \\ \end{array}
$$

假定 $H(s)$ 在右半 $S$ 平面有 $r$ 个零点和 $q$ 个极点，由 $H(s)$ 的表达式可以看到，它的 $q$ 个极点一定都是 $F(s)$ 的极点，于是 $E(s)$ 在右半 $S$ 平面上也就有 $q$ 个极点。另一方面，为了得到 $g_{1}(s)$ 和 $g_{2}(s)$ ，就要用 $H(s)$ 去除方程(11.5-13)中的 $E(s)$ 。这样做的结果就在右半 $S$ 平面引进了 $q$ 个零点和 $r$ 个极点。因此，如果要求 $E(s)$ 在右半 $S$ 平面上没有零点， $G(s)$ 就要围绕原点顺时针方向转 $-q + (q - r) = -r$ 圈，也就要求 $g_{2}(s)$ 围绕单位圆 $g_{1}(s)$ 以顺时针方向旋转 $-r$ 圈。于是，就需要确定 $H(s)$ 在右半 $S$ 平面上的零点数 $r$ 。因此只要画 $H(s)$ 的分子多项式 $H_{1}(s)$ 的乃氏图就 够了。当 s 沿着图 11.4-1 的曲线转动一周时， $H_{1}(s)$ 围绕原点顺时针方向转的圈数就是 $H(s)$ 在右半 S 平面的零点数。所以，为了解决一般情况下的稳定性问题，萨奇图和乃氏图都是要用到的（图 11.8-1）。

> 此处省略原书 **图 11.8-1 （实线表示正的 $\omega$ ，虚线表示负的 $\omega$ ）**

显然，这里所讲的把萨奇图和乃氏图结合起来的稳定性准则，对于任意一个同类的时滞系统都是适用的。这一类系统的稳定性判据可以化为这样一个问题，即确定特征方程

$$
E (s) = 0
$$

是否有大于零的实数部分的根。这里的 $E(s)$ 包含有 $e^{-\tau s}$ 因数的项。正像前面讨论过的那样，用 $E(s)$ 里的 $e^{-\tau s}$ 的系数 $H(s)$ 去除 $E(s)$ 便得到

$$
\frac {E (s)}{H (s)} = G (s) = g _ {1} (s) - g _ {2} (s)
$$

其中

$$
g _ {1} (s) = e ^ {- \tau s}
$$

当 s 在图 11.4-1 所画的右半圆的路线上转动时， $g_{1}(s)$ 和 $g_{2}(s)$ 的图线就构成了萨奇图， $g_{1}(s)$ 的图线是单位圆。用 $H(s)$ 除 $E(s)$ 可能在萨奇图中引进若干个正实数部分的零点。为了判明这个情况，我们必须画出 $H(s)$ 分子的乃氏图。然后，根据 $G(s)$ 围绕原点沿顺时针方向转的圈数就可以确定 $E(s)=0$ 在右半 S 平面上的根的个数。

函数 $g_{2}(s)$ 里包含有反馈部分的传递函数, 反馈部分中的放大器是可以由设计者自由处理的。由于系统的其他部分的原因, $g_{2}(s)$ 里也可能包含有 s 的超越函 数。因为，反馈部分的放大器的传递函数通常都是两个多项式的比值，所以很难把来源于超越函数的损害稳定性的不良影响完全补偿掉。可是，在萨奇图中 $g_{2}(s)$ 图线上最危险的部分就是最接近 $g_{1}(s)$ 的单位圆图线的那一部分。然而，接近单位圆的 $g_{2}(s)$ 点通常都是相应于小的 s 值，所以在 $g_{2}(s)$ 的危险的部分上超越函数可以展开为 s 的泰勒级数。我们可以只取级数的少数几项作为超越函数的近似值[25]，并且根据这个近似的结果来设计反馈部分的放大器。这样一来系统在危险部分的损害稳定性的不良影响就可以被放大器补偿掉。不言而喻，最后还必须根据放大器的设计特性用已有的稳定性准则校验系统的性能。以上所讲的方法是马伯尔(Marble)和柯克司(Cox)所提出的。如果想知道详细的论述，读者可以去参阅原著[12]。

#### 11.9 频率法的稳定性准则

这一节我们力图把乃氏法更直接地应用到时滞系统中来，希望利用无时滞的开环频率特性来判断有时滞的闭环系统的稳定性问题。这种方法是建立在图 11.9-1(c)结构图的基础上的。由第三章关于传递函数的知识可以知道，任何一个时滞系统，不论时滞环节位于系统的主回路（图 11.9-1a)还是位于反馈线上（图 11.9-1b)，它们的闭环传递函数的分母（特征方程）是相同的。例如图 11.9-1(a)的闭环传递函数为

$$
\phi^ {*} (s) = \frac {F _ {0} (s) e ^ {- \tau s}}{1 + F _ {0} (s) e ^ {- \tau s}} = \frac {N _ {0} (s) e ^ {- \tau s}}{D _ {0} (s) + N _ {0} (s) e ^ {- \tau s}}
$$

> 此处省略原书 **图 11.9-1**

其中 $F_{0}(s)=F_{1}(s)F_{2}(s)$ 是无时滞开环传递函数， $N_{0}(s)$ ， $D_{0}(s)$ 分别为 $F_{0}(s)$ 的分子多项式和分母多项式。而图 11.12(b) 的闭环传递函数是

$$
\phi^ {*} (s) F _ {s} ^ {*} = \frac {F _ {1} (s)}{1 + F _ {0} (s) e ^ {- \tau s}} = \frac {N _ {1} (s) D _ {2} (s)}{D _ {0} (s) + N _ {0} (s) e ^ {- \tau s}}
$$

$$
F _ {0} (s) = F _ {1} (s) F _ {2} (s)
$$

可见图 11.9-1(a) 和图 11.9-1(b) 的闭环特征方程相同, 因而两者的稳定性是等价的。这样, 我们就可以从结构图 11.9-1(c) 出发来考虑有时滞的闭环系统的稳定性。

第 4.3 节所介绍的无时滞系统的稳定判据准则是利用开环传递函数的倒数 $\frac{1}{F_{0}(s)}$ 来判别的。当然，也可以利用传递函数 $F(s)$ 本身的图线来判断。由于大部分实际系统传递函数分母的阶数大于分子的阶数，仅在个别情况下两者相等。因此，当 s 绕图 4.3-1 的曲线旋转时， $F_{0}(s)$ 图线的主要部分由频率特性 $F_{0}(i\omega)$ 所决定。由于 $F_{0}(-i\omega)=\overline{F_{0}}(i\omega)^{\textcircled{1}}$ ，故可以直接利用开环频率特性 $F_{0}(i\omega),0\leqslant\omega<\infty$ ，来判断闭环的稳定性。如果开环的传递函数在右半平面无极点，那么闭环稳定的充要条件是开环频率特性在复平面上不包围 $(-1,i0)$ 点。

从时滞系统的典型结构图（图 11.9-1c)可以看出，有时滞的开环频率特性 $F_{0}^{*}(i\omega)$ 可以由无时滞的开环频率特性 $F_{0}(i\omega)$ 求得。因为

$$
F _ {0} ^ {*} (i \omega) = F _ {0} (i \omega) e ^ {- i \tau \omega}
$$

即对任何固定的自变数 $\omega$ ，向量 $F_{0}^{*}(i\omega)$ 可由 $F_{0}(i\omega)$ 顺时针方向转以 $\tau\omega$ 角而得到。因此，可以直接利用无时滞的开环频率特性来判断有时滞的闭环系统的稳定性。

首先我们讨论无时滞的开环系统稳定或中性稳定时，时滞系统的稳定情况。此时与无时滞的系统类似，闭环时滞系统稳定的充要条件是开环时滞系统频率特性在 $0 \leqslant \omega < \infty$ 段内不包围 $(-1, i0)$ 点。

我们来考察特性 $1 + F_{0}^{*}(i\omega)$ ， $F_{0}^{*}(i\omega)$ 是开环时滞系统的频率特性，而 $N_{0}(i\omega)$ 和 $D_{0}(i\omega)$ 分别是开环无时滞系统频率特性的分子与分母，于是

$$
1 + F _ {0} ^ {*} (i \omega) = 1 + \frac {N _ {0} (i \omega)}{D _ {0} (i \omega)} e ^ {- i \tau \omega} = \frac {D _ {0} (i \omega) + N _ {0} (i \omega) e ^ {- i \tau \omega}}{D _ {0} (i \omega)}
$$

其中分母是无时滞开环系统的特征方程，分子是有时滞闭环系统的特征方程。若要求有时滞的闭环系统稳定，那么当 $\omega$ 由 0 变至 $+\infty$ 时，开环时滞系统频率特性 $F_0^* (i\omega)$ 应该不包围 $(-1,i0)$ 点。如果 $F_0^* (i\omega)$ 不包围 $(-1,i0)$ 点而通过该点，那么系统就处于临界稳定状态。临界时滞时间 $\tau_{k}$ 和临界频率 $\omega_{k}$ 应该由下列两式决定

$$
\left| F _ {0} \left(i \omega_ {k}\right) \right| = 1
$$

$$
\arg \left[ F _ {0} (i \omega_ {k}) \right] - \tau_ {k} \omega_ {k} = - \pi \pm 2 \pi q, \quad q = 0, 1, \dots \tag {11.9-1}
$$

从上述讨论似乎可以得出结论：一切具有时滞的元件都会使系统的稳定性变坏。实际上并非完全如此。有时，利用具有时滞的元件还可以改善闭路系统的稳定性。例如，设有一个闭路系统当没有时滞元件时不稳定，如具有图 11.9-2 那种频率特性的系统，显然它的闭路系统是不稳定的，因为频率特性包围了 $(-1,i0)$ 点。此时如果在系统中的主回路或反馈回路内增加一个时滞元件，使频率特性曲线顺时针旋转一个角度，当时滞 $\tau$ 选择恰当时，可以使原来包围 $(-1,i0)$ 点的频率特性曲线转到此点的外部，于是增加了时滞元件的闭路系统就一变而为稳定系统了。在工程实际问题中，就有人利用时滞元件的这种性能去改善系统的稳定性，试验的结果也是很成功的。

> 此处省略原书 **图 11.9-2**

关于时滞系统的线性综合方法，即控制装置的设计，也可以用频率特性去进行。比较成功的方法可参看文献[22]。

#### 11.10 参考文献

[1] 秦元勋、刘泳清、王联，带有时滞的动力系统的运动稳定性，科学出版社，1963.

[2] 赵民义, 复变函数论, 高等教育出版社, 1960.

[3] Ansoff. H. I., Stability of linear oscillating systems with constant time lag, J. Appl. Mechanics (ASME), 16(1949), 158–164.

[4] Bellman, R., Cooke, K. L., Differential-Difference Equations, Academic Press, New York, 1963.

[5] Balestrino, A., Celetano, G., Stabilization by Digital Controllers of Multivariable Linear Systems with time-lays, Proc. of 7th IFAC Congress. Helsinki, 1978.

[6] Bhat, K. P. M., Koivo, H. N., Modal characterization of controllability and observability for time delay systems, IEEE Trans. on AC, AC-21(1976), 2.232–233.

[7] CaHander, A., Hartree, D., Porter, A., Trans. Roy. Soc., London (A), (1935), 415–444.

[8] Crocco, L., Jour. Amer. Rocket Soc., 21(1951), 163–178.

[9] Goldenberg, A., Davison. E. J., The Robust Control of a Servomechanism Problem with Time Delay. Proc. of 7th IFAC Congress, Helsinki, 1978.

[10] Jakubczyk, B., Olbrot, A. W., Dynamic Feedback Stabilization of Linear Time-lag Systems. Proc. of 7th IFAC Congress, Helsinki, 1978.

[11] Minorsky, J. N., Self-Excited oscillations in dynamical systems Possessiny retarded actions J. Appl. Mechanics (ASME), 9(1942), 67–71.

[12] Marble, F. E., Cox, D. W., Jour. Amer. Rocket Soci. 23(1953), 75–81.

[13] Pandolfi, L., Stabilization of neutral functional differential equations. J. of optimization Theory and Appl., 20(1976), 2, 191-204.

[14] Satche, M., J. Appl. Mechanics, (ASME), 16(1949), 419-420.

[15] Tsien H.S.(钱学森),J.Amer.Rocket Soci.22(1952),139-143.

[16] Wonham, W. M., Linear Multivariable Control, Springer-Verlay, New York, 1974.

[17] Вулгаков В. В., Колебание, Москва, 1954.

[18] Лаврентьев М. А., Шабат В. В., Методы Теории Функций Комплексного Переменного, Москва, 1958.

[19] Попов Е. П., Динамика Систем Автоматического Регулирования, Гл. 7, Государетвенное издательство технико-теоретической литеражуры, Москва, 1954.

[20] Понтрятин Л.С., О нулях некоторых элементарных трансдендентных функций, изв. АН.
СССР, Серия матем., 6(1942), 115–134.

[21] Уланов Г. К., Анализ устойчивости систем автоматического регулирования с запаздыванием, в книге основы теории автоматического регулирования, под ред. Солодовникова, В. В. Гл. 13, Машигиз, 1954.

[22] Фанъ Чун-вуй(范崇惠), Анапиз качества и синтез автоматического регулирования с запаздыванием, Автамамика и Телемеханика, 19(1958), 3.

[23] Фельдбаум А. А., Электрические системы автоматического регулирования, Государственное издательство оборонный промышленности, Москва, 1957. (电的自动调节系统, 章燕申, 金兰, 石定机等译, 国防工业出版社, 1961.)

[24] Харатишвили Г. А., Принцип Максимума в теории оптимальных процессов с запаздыванием, Доклалы АН СССР, 136(1961), 39—42.

[25] Цыпкин Я. 3., Устойчивость систем с запаздывающей обратной связью, Автаматика и Телемеханика, 7(1946), 2—3.
