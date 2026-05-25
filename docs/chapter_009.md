# 工程控制论（上册）

（第三版）

钱学森 宋健 著

## 正文（009）

### 第九章 满足指定积分指标的控制系统设计

在前面几章里，我们主要从分析的观点去讨论控制系统的设计问题。那就是首先假定了系统的结构，然后找出系统具有什么样的性能。

在上面一章里，我们第一次引入了一种不同的、更为直接的观点：我们首先指定某些性能，然后寻求能够给出所要求的性能的控制系统。本章内，我们将把这一原理用到任意的系统上去。在这种控制系统中，被满足的性能准则是用被控制量的积分表示的，因此可以得到一个非常普遍的用微分方程来表示的系统的性能。一般说来，这是一个非线性的微分方程。按这种原理设计成功的控制系统通常就是一个非线性系统。

#### 9.1 基本概念

实际上，第八章内曾研究过的最速控制系统，就是属于具有最短过渡时间的系统，而最短过渡时间可以用积分公式表达出来。下面我们将讨论一个更为一般的问题：系统质量指标是具有更为普遍的积分形式。设受控对象的运动规律为下列一阶常微分方程组所描述

$$
\frac {d x _ {1}}{d t} = f _ {1} \left(x _ {1}, x _ {2}, \dots , x _ {n}, u _ {1}, u _ {2}, \dots , u _ {r}\right)
$$

$$
\frac {d x _ {2}}{d t} = f _ {2} \left(x _ {1}, x _ {2}, \dots , x _ {n}, u _ {1}, u _ {2}, \dots , u _ {r}\right)
$$

$$
\dots
$$

$$
\frac {d x _ {n}}{d t} = f _ {n} \left(x _ {1}, x _ {2}, \dots , x _ {n}, u _ {1}, u _ {2}, \dots , u _ {r}\right) \tag {9.1-1}
$$

式中 $x_{i}, i=1,2,\cdots,n$ ，为受控对象的状态坐标分量， $u_{1}, u_{2}, \cdots, u_{r}$ 为控制量。上式也可以写成向量方程式，令 $\boldsymbol{x}=(x_{1}, x_{2}, \cdots, x_{n}), \boldsymbol{u}=(u_{1}, u_{2}, \cdots, u_{r})$ ，则有

$$
\frac {d \boldsymbol {x}}{d t} = \boldsymbol {f} (\boldsymbol {x}, \boldsymbol {u}) \tag {9.1-1a}
$$

式中 $f=(f_{1},f_{2},\cdots,f_{n})$ 。

受控运动的性能指标，我们用积分

$$
\boldsymbol {J} = \int_ {0} ^ {t _ {1}} f _ {0} (\boldsymbol {x}, \boldsymbol {u}) d t \tag {9.1-2}
$$

来表示，右边积分上限 $t_{1}$ 是评价运动优劣的时间区间，即仅在 $[0, t_{1}]$ 时间间隔内 评价系统的运动。显然，当 $f_{0} \equiv 1$ 时，我们便得到 $J = t_{1}$ ，此时运动到达终端所需的时间就是评价受控运动优劣的指标。这一问题我们已在前一章内详细地讨论过了。设 $x_{0} = (x_{10}, x_{20}, \cdots, x_{n0})$ 是受控对象(9.1-1)的初始状态。控制的目的是使受控对象由此点出发到达某一特定状态 $x_{1}$ 或某一状态集合 D（状态空间内某一特定区域）。

如果式(9.1-2)表示控制过程中某种物理量的耗损，如能量或燃料消耗等，则希望选择控制 $\boldsymbol{u}(t)$ 使

$$
J = \int_ {0} ^ {t _ {1}} f _ {0} (\boldsymbol {x} (t), \boldsymbol {u} (t)) d t = \min, \quad \boldsymbol {x} (0) = \boldsymbol {x} _ {0} \tag {9.1-3}
$$

有时又希望使 $J=\max$ ，这时只需将函数 $f_{0}$ 变号后，便可归结为条件式(9.1-3)。

设 $x_{0}$ 是受控对象的初始状态, 控制的目的是使受控对象到达某一状态集合 D (区域)。自 $x_{0}$ 到达 D 且满足条件式(9.1-3)的控制函数称为最优控制。不难想象, 这里可能有四种情况:

（1）自 $x_{0}$ 点用任何控制 $u(t)$ 都不可能到达区域 D，此时不存在任何能到达目的地的控制函数，当然也无最优控制可言。

（2）自 $x_{0}$ 点只有一个控制 $u(t)$ 使受控对象的状态到达 D。此时，到达终端状态的控制只有一个，它所对应的式(9.1-3)的 J 也唯一地被确定，对于这种情况最优控制也是没有意义的。

（3）自 $x_{0}$ 引至 D 的控制函数有多个（有穷多个或无穷多个)。如果这种控制为有穷多个，那么其中使 J 取最小值的控制便是要求的最优控制，若这些控制所对应的 J 相等，则可认为其中任何一个控制都是最优的。如果自 $x_{0}$ 引到 D 的控制函数有无穷多个，其中有一个或数个控制使 J 取最小值，此时我们说最优控制函数存在，控制设计的任务就是找出这个最优控制来。

（4）自 $x_{0}$ 点引到 D 的控制有无穷多个，但其中没有一个能使 J 取极小。此时最优控制依然是不存在的。

上述四种情况中的第四种；初看起来很奇怪。其实这种情况是常见的。试看下面的例子。设在水平面上有一质量为 $m$ 的物体，在 $t = 0$ 时处于静止状态。现用一个力 $F$ ，将物体推至 $\pmb{x}_{1}$ 点（图 9.1-1）。忽略空气阻力和摩擦力，物体运动方程式为

$$
\frac {d ^ {2} x}{d t ^ {2}} = \frac {F (t)}{m}, \quad F (t) \geqslant 0
$$

> 此处省略原书 **图 9.1-1**

要求找到一种控制力 $F(t)$ ，使物体到过 $x_{1}$ 点，且消耗能量为最小。显然，这种控制力（函数）有无穷多个。但是，消耗能量最小的控制力却不存在。实际上，能量耗损由下式表示

$$
J = \int_ {0} ^ {x _ {1}} F (t) d x = \int_ {0} ^ {t _ {1}} F (t) v (t) d t = \frac {1}{2} m [ v (t _ {1}) ] ^ {2}
$$

式中 $\frac{dx(t)}{dt} = v(t), t_1$ 是物体到达 $x_1$ 点的时刻， $F(t) \geqslant 0$ 。为使耗能减少，需减小 $v(t_1)$ ，当 $v(t_1) \to 0$ 时，耗能 $J \to 0$ 。当 $J = 0$ 时， $v(t_1) = 0$ ，此时 $F(t) \equiv 0$ ，而这种控制又不能使物体到达 $x_1$ 点。由此看到，使物体到达 $x_i$ 点的控制力有无穷多个，其中却没有最优控制。对任何使 $v(t_1)$ 足够小的 $F_1(t)$ ，还可找到“更小的” $F_2(t)$ ，使 $v(t_1)$ 更小，在极限的情况下， $J = 0$ ，而 $F(t) \equiv 0$ 不属于可准控制范围，所以，在这种情况下，最优控制并不存在。

由这样一个简单例子就可以看到，并不是所有的情况下，最优控制都存在。因此，在进行控制设计时，首先重要的是搞清楚最优控制是否存在。否则，寻求最优控制的努力可能是徒劳的。

另一个值得提及的概念是关于对控制量取值的限制。有时，若控制量 $u(t)$ 的取值不受限制，即它的取值范围可以是整个 r 维空间，这时最优控制也常常没有意义。还以上述例子来说明这点。设图 9.1-1 内所示之力 $F(t)$ 不受限制，要求找出一个最优控制使物体自零点到达 $x_{1}$ 点费时最短。显然， $F(t)$ 在起始时刻的取值越大，物体的运动速度也越大，如果对 $F(t)$ 取值没限制，当 $F(t)$ 的取值趋于无穷大时，物体到达 $x_{1}$ 点的时间将趋于无穷小，这在实际上是没有意义的。

由此可见，做最优控制器的设计时，首先要关心的问题是最优控制的存在性。即首先弄清欲达到的终点状态实际上是否能够到达，对控制量有哪些限制条件，以及在这种限制条件下最好的控制函数是否存在等。这些问题往往只能从技术问题的物理概念中寻求解答。在一般情况下，最优控制的存在性难以用数学方法加以证明。对存在性问题有了肯定的答案以后，就可以开始最优控制的设计。

当最优控制找到以后，在某些闭路系统中，设计控制装置时还要考虑到控制系统在终点状态是否稳定。若闭路系统不能保证终点状态稳定，那么有时它就不能作为实际装置加以实现。稳定性的要求是一种特殊的准则，在过渡过程里，主要控制系统的设计，常不考虑这一特殊准则。这种情况像上一章一样，因为系统满足了那些指定条件后，整个系统已经具有了合适的性能。设计完毕后，如果系统在终点状态上是稳定的，自然就无须采取特殊措施。也有另外一种可能，即满足最优条件的控制装置，不能保证闭路系统的稳定性，此时必须在系统里另加一 个稳定装置，后者只在过渡过程完毕后才发生作用，因此它不会影响控制系统已经设计好了的运转性能。例如，对一个二阶系统，用 y 表示输出, $y_{s}$ 表示必须保持的终点状态，稳定装置应保证使系统在 $y=y_{s},\dot{y}=0$ 的状态上稳定。对于三阶系统，稳定装置应保证下列状态稳定

$$
y = y _ {s}, \quad \dot {y} = 0, \quad \ddot {y} = 0
$$

当这样的一个装置加到控制系统以后，控制系统有两种运行方式，这也就是一个多方式控制系统。在过渡过程期间，主要控制系统按照指定的性能运行。过渡过程终止时，再换到第二个系统进行控制，这时候将保证系统最后处于稳定状态，避免系统离开希望到达的运转点。

除了对控制量常常存在一些客观限制条件以外，还可能存在某些对受控量的限制。这种限制条件也可以写成积分形式.如要求最优控制满足附加条件

$$
J _ {i} = \int_ {0} ^ {t _ {1}} g _ {i} (\boldsymbol {x}, \boldsymbol {u}) d t \leqslant \lambda_ {i}, \quad i = 1, 2, \dots , m
$$

式中 $g_{i}$ 是 $x=(x_{1},x_{2},\cdots,x_{n})$ 和 $u=(u_{1},u_{2},\cdots,u_{r})$ 的 $n+r$ 元连续或连续可微函数。下节内将用实例加以说明。

#### 9.2 几个实例

先让我们回忆一下古典变分法中的一个例子，即所谓贝努利(Bernoulli)捷线 问题。设欲使一物体依重力沿某曲线自 0 点下滑至 P 点。需求出一条曲线，物体沿此曲线下滑时将以最短时间到达 P 点。设任取一光滑的曲线 $y(x)$ ，重力加速度为 g。若忽略摩擦力后，初始为静止的物体滑至 $y(x)$ 点时的速度为 $\sqrt{2gy}$ 。物体滑过弧元 $ds=\sqrt{1+(\dot{y}(x))^{2}}dx$ 所需的时间为

> 此处省略原书 **图 9.2-1**

$$
d t = \frac {\sqrt {1 + (\dot {y} (x)) ^ {2}} d x}{\sqrt {2 g y}}
$$

于是，当曲线 $y(x)$ 已给定时，物体自 0 点滑至 P 点 所需的时间为

$$
J = \int_ {0} ^ {x _ {1}} \frac {\sqrt {1 + (\dot {y}) ^ {2}}}{\sqrt {2 g y}} d x \tag {9.2-1}
$$

现需找出一条“最好的”曲线 $\dot{y}(x)$ ，使时间 J 为最小。从控制理论的观点，上述捷线问题可以改为下列等价问题：设有一“受控对象”，其运动方程式为

$$
\frac {d y}{d x} = u, \quad y (0) = 0, \quad y (x _ {1}) = y _ {1} \tag {9.2-2}
$$

性能指标为

$$
J = \int_ {0} ^ {x _ {1}} \frac {\sqrt {1 + u ^ {2}}}{\sqrt {2 g y}} d x \tag {9.2-3}
$$

我们看到，选择一条捷线等价于求出一个最优“控制函数” $\dot{u}(x)=\frac{dy(x)}{dx}$ 和相应的满足条件式(9.2-2)的“系统运动”。这一问题的解早在 1696 年为瑞士数学家贝努利和牛顿等人得到，因而开创了一门称为“变分法”的数学分支。以后我们将会看到，古典变分法对最优控制系统的设计是极为有用的。但是，对一些比较复杂的问题，古典变分法中的一些定理和计算方法不能完全满足控制系统设计的要求。为此必须对古典变分法的理论加以扩充。

为了说明最优控制系统的命题方法，让我们再看一个实例：关于喷气发动机工作过程的控制问题 $^{[8]}$ 。喷气发动机的主要运转状态是它的运转速率 $N(t)$ ,它是受控对象的受控量。当 $N(t)$ 的变化规律被确定后，其他的工作特征，例如发动机的推力也就被决定了。在发动机运转时对它的限制条件是关于超速，超温，压缩机的浪涌，燃烧室的熄灭等。令 $N_{s}$ 表示指定的速度。T 表示加到轮机里的温度,P 表示压缩机出口处的压力，于是可以用下述积分表示发动机的性能准则:

$\int_{0}^{t_{1}}f_{1}(N-N_{s})dt,$ 控制速度

$\int_{0}^{t_{1}}f_{2}(N)dt,$ 超速

$\int_{0}^{t_{1}}f_{3}(T)dt,$ 温度容许的上限和下限

$\int_{0}^{t_{1}}f_{4}[P-g(N)]dt,$ 压缩机浪涌

$\int_{0}^{t_{1}}f_{5}[P-h(N)]dt,$ 熄灭

以及

$$
\int_ {0} ^ {t _ {1}} d t, \quad \text { 升起的时间 } \tag {9.2-4}
$$

这些被积函数的性质如图 9.2-2 所示, 量 $P - g(N)$ 是压缩机出口处的压力超出安全压力而发生浪涌的总量, $g(N)$ 表示对于浪涌以下的安全值, 是每一个发动机速度所对应的压缩机出口处压力。燃烧室熄灭的情况可以用同样方式处理。升起的时间是系统从一个主要运行状态过渡到另一状态总共需要的时间。

这里和第 6.6 节谈到过的喷气发动机的情形相似，线性化以后发动机的特性

可以表示如下

$$
T = a N + a \tau \dot {N}
$$

$$
P = b N + c \dot {T} \tag {9.2-5}
$$

> 此处省略原书 **图 9.2-2**

其中 $\tau$ 是发动机的时间常数。将这些关系式代到方程(9.2-4)的积分里，我们看到它们全都有下面的形式

$$
\int_ {0} ^ {t _ {1}} f (N, \dot {N}) d t
$$

其中 f 是 N 和 $\dot{N}$ 的连续函数，N 是时间 t 的连续函数。关于这个问题，在第 9.5 节内还要讨论。

#### 9.3 古典变分法的应用

古典变分法给控制系统设计提供的理论和方法大体分为两类。一类是不考虑受控对象的运动方程式，即在整个运动过程中受控对象本身的特性并不重要，重要的是运动规律的全局。例如，求探空火箭的最优弹道问题 $^{[17]}$ ，要求找出一条 理想弹道，在相同的燃料消耗条件下，使火箭达到的高度最大。由于这种弹道很长，而弹体上控制系统的动作速度相对于这条最优弹道来说是足够大的，因而在考虑最优弹道的选择时，可把弹体看成是其重心（质点）的运动，而忽略刚体运动及弹上控制设备的运动规律。另一类问题是当积分指标的计算时间间隔与控制系统的动作速度为同一数量级时，受控对象本身的运动规律必须考虑在内，甚至成为决定性的因素。

第一类问题可叙述如下: 设 $x=(x_{1}, x_{2}, \cdots, x_{n})$ 为控制系统的 n 个状态坐标。对控制系统的要求是找出连接两个给定点 $x_{0}$ 和 $x_{1}$ ，的连续光滑的曲线，使受控对象沿此曲线运动时积分

$$
J = \int_ {0} ^ {t _ {1}} f _ {0} (t, x _ {1}, x _ {2}, \dots , x _ {n}; \dot {x} _ {1}, \dot {x} _ {2}, \dots , \dot {x} _ {n}) d t \tag {9.3-1}
$$

取极小值。上式内 $\dot{x}_{i}=\frac{dx_{i}}{dt}, i=1,2,\cdots,n$ 。如果引进向量符号，式(9.3-1)可改写成

$$
\boldsymbol {J} = \int_ {0} ^ {t _ {1}} f _ {0} (\boldsymbol {t}, \boldsymbol {x}, \boldsymbol {u}) d t \tag {9.3-2}
$$

$$
\frac {d \boldsymbol {x}}{d t} = \boldsymbol {u}, \quad \boldsymbol {u} = (u _ {1}, u _ {2}, \dots , u _ {n}) \tag {9.3-3}
$$

式中 u 为曲线 $x(t)$ 的切线向量，要求找出函数 $u(t)$ ，使 $x(t)$ 由固定点 $x_{0}$ 引到 $x_{1}$ ，且使式(9.3-2)取极小值。这类问题的提法也可以改为端点不固定的情况，即端点 $x_{0}$ 和 $x_{1}$ 满足一些附加条件

$$
g _ {i} \left(\boldsymbol {x} _ {0}, \boldsymbol {x} _ {1}\right) = 0, \quad i = 1, 2, \dots , l \tag {9.3-4}
$$

在满足这些条件的点中，找出最好的初始点和终点。

第二类问题与上述问题的不同点在于受控对象的运动方程式比式(9.3-3)更复杂，即除式(9.3-2)和式(9.3-4)外，运动 $x(t)$ 必须满足条件式(9.1-1)

$$
\frac {d \boldsymbol {x} (t)}{d t} = \boldsymbol {f} (t, \boldsymbol {x}, \boldsymbol {u})
$$

为了掌握古典变分法处理这类问题的主要思想，下面先对第一类问题当 n=1 时，略加讨论。设控制指标为

$$
J = \int_ {0} ^ {t _ {1}} F (\mathbf {y}, \dot {\mathbf {y}}) d t = \min \tag {9.3-5}
$$

其中 $y(t)$ 为受控对象的一个唯一输出坐标； $\dot{y} = \frac{dy}{dt}$ ， $F$ 是 $y$ 和 $\dot{y}$ 的连续可微函数，设受控对象的初始状态为 $y_0 = y(t_0)$ ，而受控对象的终点状态是不固定的，且积分上界 $t_1$ 也是不固定的。若将 $y(t)$ 看成是一个一阶系统的输出

$$
\frac {d y}{d t} = \dot {y} = u \tag {9.3-6}
$$

则指标式 $(9.3-5)$ 也可改写为

$$
J = \int_ {0} ^ {t _ {1}} F (y, u) d t = \min \tag {$9.3-5^{\prime$}}
$$

如果我们认为 $y(t)$ 是一个最优解，那就是说 $y(t)$ 是所有可能得到的输出里的某个输出，它满足方程(9.3-5)表示的条件。我们考虑 $y(t)$ 附近的一些解 $y(t)+\varepsilon\delta y(t)$ 。其中 $\delta y(t)$ 是一个任意的函数， $\varepsilon$ 是一个数值很小的参数。如果 $y(t)$ 满足方程(9.3-5)表示的条件，那么 J 应在 $\varepsilon=0$ 处达极小值，即

$$
\left[ \frac {d}{d \varepsilon} \int_ {0} ^ {t _ {1} + \varepsilon \delta t _ {1}} F (y + \varepsilon \delta y, \dot {y} + \varepsilon \delta \dot {y}) d t \right] _ {\varepsilon = 0} = 0
$$

或

$$
\int_ {0} ^ {t _ {1}} \frac {\partial F}{\partial y} \delta y d t + \int_ {0} ^ {t _ {1}} \frac {\partial F}{\partial \dot {y}} \dot {\delta y} d t + F (t _ {1}) \delta t _ {1} = 0 \tag {9.3-7}
$$

变分 $\delta t_{1}$ 出现的原因在于: 方程(9.3-5)里那个积分的上限并非固定, 而是在图 9.3-1 表示的曲线 $y = f(t)$ 上变动。这就是前面讨论过的从一个主要变量运行状态过渡到另外一个状态的边界条件。用部分积分法, 方程(9.3-7)变成

$$
\int_ {0} ^ {t _ {1}} \left[ \frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) \right] \delta y d t + \left[ \frac {\partial F}{\partial \dot {y}} \right] _ {t _ {1}} \delta y (t _ {1}) - \left[ \frac {\partial F}{\partial \dot {y}} \right] _ {0} \delta y (0) + F (t _ {1}) \delta t _ {1} = 0
$$

> 此处省略原书 **图 9.3-1**

由于终端满足的条件，很容易计算出 $\delta y(t_{1})$ 和 $\delta t_{1}$ 之间的关系，即

$$
\dot {y} (t _ {1}) + \delta y (t _ {1}) = \dot {f} (t _ {1}) \delta t _ {1}
$$

然后把 $\delta y(t_{1})$ 消掉, 因为 $\delta t$ 是任意的, 我们得到

$$
\int_ {0} ^ {t _ {1}} \left[ \frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) \right] \delta y d t = 0 \tag {9.3-8}
$$

以及

$$
\delta t _ {1} \left\{F (t _ {1}) + \left[ \frac {\partial F}{\partial \dot {y}} \right] _ {t _ {1}} [ \dot {f} (t _ {1}) - \dot {y} (t _ {1}) ] \right\} - \left[ \frac {\partial F}{\partial \dot {y}} \right] _ {0} \delta y (0) = 0 \tag {9.3-9}
$$

如果在方程(9.3-5)中，时间间隔 t 被考虑为系统从一个主要运行状态过渡到另一个状态的时间；在这种情况下，系统变数 y 从一个固定值变化到另一个固定值。那么曲线 $y=f(t)$ 必须是一条直线，这条直线的方程是 $f(t)=\text{const}$ ,因此可认为

$$
\delta y (0) = 0
$$

$$
\dot {f} (t _ {1}) = 0 \tag {9.3-10}
$$

于是方程(9.3-8)和方程(9.3-9)变成

$$
\frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) \tag {9.3-11}
$$

以及

$$
\text {如果} \left[ \frac {\partial F}{\partial \dot {y}} \right] \text {是有限数,} F (t _ {1}) = \dot {y} (t _ {1}) \left[ \frac {\partial F}{\partial \dot {y}} \right] _ {t _ {1}} \tag {9.3-12}
$$

因为 $\delta y(0) = 0$ ，当 $t = 0$ 时，并不一定要求方程(9.3-11)成立，唯一的条件是： $t = 0$ 时 $(\partial F / \partial \dot{y})_0$ 是有限数，而且 $y$ 连续变化。一个新的过渡过程开始时， $\dot{y}, F, (\partial F / \partial y)$ 和 $(\partial F / \partial \dot{y})$ 可以不连续。因为方程(9.3-11)的缘故，在其他点 $(0 < t \leqslant t_1)$ ， $\partial F / \partial \dot{y}$ 将是连续的。

方程(9.3-11)表示满足方程(9.3-5)那个条件的变量 $y(t)$ 的微分方程.通常把方程(9.3-11)叫做变分问题的尤拉-拉格朗日(Euler-Lagrange)方程。这里所考虑的问题中，函数 $F$ 不明显地包含时间变数 $t$ 。于是我们可以立刻得到方程(9.3-11)的一个第一积分。方程(9.3-11)的第一积分中，满足边界条件方程(9.3-12)的第一积分具有下述形式

$$
F (y, \dot {y}) = \dot {y} \frac {\partial F}{\partial \dot {y}} \tag {9.3-13}
$$

把这个方程对时间 t 微分, 我们得到

$$
\frac {\partial F}{\partial y} \dot {y} + \ddot {y} \frac {\partial F}{\partial \dot {y}} = \ddot {y} \frac {\partial F}{\partial \dot {y}} + \dot {y} \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right)
$$

既然在那些 $y, \partial F / \partial \dot{y}$ , 等连续的地方, 下面公式成立

$$
\ddot {y} \left[ \frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) \right] = 0
$$

那么，或者 $\dot{y}=0$ , 或者满足方程(9.3-11)。但是通常在过渡过程中 $\dot{y}$ 不会等于零 (也即无论在任何时间间隔内不恒等于零), 于是由方程(9.3-11)和方程(9.3-12)所描述的 $y(t)$ 的两个必须满足的条件, 可以用单独一个方程(9.3-13)代替。

这样，我们称方程式(9.3-11)为最优控制所应满足的必要条件。引进式(9.3-6)内的符号，这个必要条件又可以写为

$$
\frac {\partial F}{\partial y} - \frac {d}{d t} \frac {\partial F}{\partial u} = 0
$$

$$
\frac {d y}{d t} = u
$$

$$
F (y (t _ {1}), u (t _ {1})) - u (t _ {1}) \left[ \frac {\partial F}{\partial u} \right] _ {t _ {1}} = 0 \tag {9.3-14}
$$

由上列三个方程式可求出两个未知函数 $u(t)$ ， $y(t)$ 和一个未知量 $t_{1}$ 。这三个条件中的前两个实际上与终端条件固定与否无关，只有第三个条件才是由 $t_{1}$ 变分而得到的。因而前两个条件具有普遍性。

再来研究一个普遍的情况。设受控对象的输出坐标不是一个，而是 n 个。此时指标泛函式(9.3-5)将变为

$$
J = \int_ {0} ^ {t _ {1}} F (y _ {1}, y _ {2}, y _ {3}, \dots , y _ {n}; \dot {y} _ {1}, \dots , \dot {y} _ {n}) d t \tag {9.3-15}
$$

或者写成

$$
J = \int_ {0} ^ {t _ {1}} F (y _ {1}, y _ {2}, \dots , y _ {n}; u _ {1}, u _ {2}, \dots , u _ {n}) d t
$$

$$
\frac {d y _ {i}}{d t} = u _ {i}, \quad i = 1, 2, \dots , n \tag {9.3-16}
$$

重复前述讨论，无论初始条件和终端条件是否已经给定，都可以得到相应于式(9.3-14)中的前两个必要条件

$$
\frac {\partial F}{\partial y _ {i}} - \frac {d}{d t} \frac {\partial F}{\partial u _ {i}} = 0, \quad i = 1, 2, \dots , n
$$

$$
\frac {d y _ {i}}{d t} = u _ {i}, \quad i = 1, 2, \dots , n \tag {9.3-17}
$$

如果初始条件和终端条件已经给定，那么这两组方程式中含有 2n 个未知函数 $y_{1}(t),\cdots,y_{n}(t);u_{1}(t),\cdots,u_{n}(t)$ 。如果初始条件和终点条件是不固定的，则与式(9.3-17)同时还会出现两个附加条件，有如条件式(9.3-9)或(9.3-12)那样。

下面再来研究一类更为复杂一些的泛函指标

$$
J = \int_ {0} ^ {t _ {1}} F (y, \dot {y}, \ddot {y}; z, \dot {z}, \ddot {z}) d t = \min \tag {9.3-18}
$$

式中 y 和 z 是受控对象的两个主要输出坐标。如果引进新的符号 $y = y_{1}, \dot{y} = y_{1}$ ， $\ddot{y} = u_{1}; z = y_{3}, \dot{z} = y_{4}, \ddot{z} = u_{2}$ ，则式(9.3-18)可写成

$$
J = \int_ {0} ^ {t _ {1}} F (y _ {1}, y _ {2}, y _ {3}, y _ {4}; u _ {1}, u _ {2}) d t \tag {9.3-19}
$$

$$
\frac {d y _ {1}}{d t} = y _ {2}
$$

$$
\frac {d y ^ {2}}{d t} = u _ {1}
$$

$$
\frac {d y _ {3}}{d t} = y _ {4}
$$

$$
\frac {d y ^ {4}}{d t} = u ^ {2} \tag {9.3-20}
$$

由此看到，这相当于由两个二阶方程描述的受控对象, $u_{1}$ 和 $u_{2}$ 是两个独立的控制量。

设受控对象在 t=0 时刻的状态为固定，而终点时刻 $t_{1}$ 是待求的，但终点状态 是给定的。再设 $y(t)$ 和 $z(t)$ 是两个最优的受控运动，它们都具有二次连续导数。令 $y(t)$ 和 $z(t)$ 分别获得微小增量（变分) $\varepsilon \delta y(t)$ 和 $\varepsilon \delta z(t)$ ，其中 $\delta y(t)$ 和 $\delta z(t)$ 为二阶连续可微的固定函数， $\varepsilon$ 为任意小的常数。于是 $y(t)$ 和 $z(t)$ 使式(9.3-18)或式(9.3-19)取极值，即当 $\varepsilon = 0$ 时有

$$
\frac {d}{d \varepsilon} \int_ {0} ^ {t _ {1} + \varepsilon \delta t _ {1}} F (y + \varepsilon \delta y, \dot {y} + \varepsilon \delta \dot {y}, \ddot {y} + \varepsilon \delta \ddot {y}, z + \varepsilon \delta z, \dot {z} + \varepsilon \delta \dot {z}, \ddot {z} + \varepsilon \delta \ddot {z}) d t = 0 \tag {9.3-21}
$$

方程(9.3-18)中积分的时间间隔由一个固定时刻 $(t=0)$ 开始，可是不是在某个固定时刻终止，而是终止在曲线 $y=f_{1}(t)$ ， $\dot{y}=f_{2}(t)$ ， $z=g_{1}(t)$ ，以及 $\dot{z}=g_{2}(t)$ 上。 $\delta y$ 和 $\delta z$ 是任意的函数，自然是时间的互相无关的函数。

我们把方程(9.3-21)的微分运算写出来

$$
\int_ {0} ^ {t _ {1}} \left[ \frac {\partial F}{\partial y} \delta y + \frac {\partial F}{\partial \dot {y}} \dot {\delta y} + \frac {\partial F}{\partial \ddot {y}} \ddot {\delta y} + \frac {\partial F}{\partial z} \delta z + \frac {\partial F}{\partial \dot {z}} \dot {\delta z} + \frac {\partial F}{\partial \ddot {z}} \ddot {\delta z} \right] d t + F (t _ {1}) \delta t _ {1} = 0
$$

经过部分积分以后，我们得到

$$
\begin{array}{l} \int_ {0} ^ {t _ {1}} \left[ \frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) + \frac {d ^ {2}}{d t ^ {2}} \left(\frac {\partial F}{\partial \ddot {y}}\right) \right] \delta y d t + \int_ {0} ^ {t _ {1}} \left[ \frac {\partial F}{\partial z} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {z}}\right) + \frac {d ^ {2}}{d t ^ {2}} \left(\frac {\partial F}{\partial \ddot {z}}\right) \right] \delta z d t \\ + \left[ \frac {\partial F}{\partial \dot {y}} \delta y + \frac {\partial F}{\partial \ddot {y}} \dot {\delta y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {y}}\right) \delta y \right] _ {0} ^ {t _ {1}} + F (t _ {1}) \delta t _ {1} \\ + \left[ \frac {\partial F}{\partial \dot {z}} \delta z + \frac {\partial F}{\partial \ddot {z}} \dot {\delta z} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {z}}\right) \delta z \right] _ {0} ^ {t _ {1}} = 0 \tag {9.3-22} \\ \end{array}
$$

和前面的讨论相类似，积分中被积函数以及边界条件必须分别等于零。从给出的终端条件，我们得到

$$
\begin{array}{l} \delta y (t _ {1}) = \left[ \dot {f} _ {1} (t _ {1}) - \dot {y} (t _ {1}) \right] \delta t _ {1} \\ \dot {\delta y} (t _ {1}) = \left[ \dot {f} _ {2} (t _ {1}) - \ddot {y} (t _ {1}) \right] \delta t _ {1} \\ \delta z (t _ {1}) = \left[ \dot {g} _ {1} (t _ {1}) - \dot {z} (t _ {1}) \right] \delta t _ {1} \\ \dot {\delta z} (t _ {1}) = \left[ \dot {g} _ {2} (t _ {1}) - \ddot {z} (t _ {1}) \right] \delta t _ {1} \tag {9.3-23} \\ \end{array}
$$

从方程(9.3-22)得到的三个条件可以写成两个联立的尤拉-拉格朗日方程

$$
\begin{array}{l} \frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) + \frac {d ^ {2}}{d t ^ {2}} \left(\frac {\partial F}{\partial \ddot {y}}\right) = 0 \\ \frac {\partial F}{\partial z} - \frac {d}{d t} \left[ \frac {\partial F}{\partial \dot {z}} \right] + \frac {d ^ {2}}{d t ^ {2}} \left[ \frac {\partial F}{\partial \ddot {z}} \right] = 0 \tag {9.3-24} \\ \end{array}
$$

以及

$$
\left\{\left[ F - \dot {y} \frac {\partial F}{\partial \dot {y}} + \dot {y} \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {y}}\right) - \ddot {y} \frac {\partial F}{\partial \ddot {y}} - \dot {z} \frac {\partial F}{\partial \dot {z}} + \dot {z} \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {z}}\right) - \ddot {z} \frac {\partial F}{\partial \ddot {z}} \right] _ {t = t _ {1}} \right.
$$

$$
\begin{array}{l} + \dot {f} _ {1} (t _ {1}) \left[ \frac {\partial F}{\partial \dot {y}} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {y}}\right) \right] _ {t = t _ {1}} + \dot {f} _ {2} (t _ {1}) \left(\frac {\partial F}{\partial \ddot {y}}\right) _ {t = t _ {1}} + \dot {g} _ {1} (t _ {1}) \left[ \frac {\partial F}{\partial \dot {z}} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {z}}\right) \right] _ {t = t _ {1}} \\ + \dot {g} ^ {2} (t _ {1}) \left[ \frac {\partial F}{\partial \ddot {z}} \right] _ {t = t _ {1}} \Bigg \} \delta t _ {1} + \delta y (0) \left[ \frac {\partial F}{\partial \dot {y}} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {y}}\right) \right] _ {t = 0} + \dot {\delta y} (0) \left[ \frac {\partial F}{\partial \ddot {y}} \right] _ {t = 0} \\ + \delta z (0) \left[ \frac {\partial F}{\partial \dot {z}} - \frac {d}{d t} \left(\frac {\partial F}{\partial \ddot {z}}\right) \right] _ {t = 0} + \dot {\delta z} (0) \left[ \frac {\partial F}{\partial \ddot {z}} \right] _ {t = 0} = 0 \tag {9.3-25} \\ \end{array}
$$

方程(9.3-24)表示两个微分方程的系统，这个系统满足方程(9.3-18)原来给出的准则。这种问题的物理解答必须满足方程(9.3-18),除此以外还要满足方程(9.3-25)的那些边界条件。但是，因为 F 不明显地包含变数 t,这一系列的条件可以加以修改：如果把方程(9.3-24)中第一个方程乘以 $\dot{y}$ ,第二个方程乘以 $\dot{z}$ ,然后加起来，就得到一个全微分，它的积分就是

$$
F - \dot {y} \frac {\partial F}{\partial \dot {y}} + \dot {y} \frac {d}{d t} \left[ \frac {\partial F}{\partial \ddot {y}} \right] - \ddot {y} \frac {\partial F}{\partial \ddot {y}} - \dot {z} \frac {\partial F}{\partial \dot {z}} + \dot {z} \frac {d}{d t} \left[ \frac {\partial F}{\partial \ddot {z}} \right] - \ddot {z} \frac {\partial F}{\partial \ddot {z}} = C \tag {9.3-26}
$$

因为 $F$ 是 $\dot{y}$ 和 $\ddot{y}$ 的一个函数， $\partial F / \partial \dot{y}$ 和 $\partial F / \partial \ddot{y}$ 未必会等于零， $\partial F / \partial \ddot{y}$ 也不一定是时间的常数函数，于是 $\frac{\partial F}{\partial y} - \frac{d}{dt}\left[\frac{\partial F}{\partial \ddot{y}}\right]$ 不一定等于零。由于初始条件和终点状态是给定的，所以在式(9.3-25)中可取

$$
\delta y (0) = \dot {\delta y} (0) = \dot {f} _ {1} (t _ {1}) = \dot {f} _ {2} (t _ {1}) = 0
$$

变量 $z$ 也有类似的情形。于是得到一系列边界条件如下

$$
\delta y (0) = 0, \quad \dot {f} _ {1} \left(t _ {1}\right) = 0
$$

$$
\delta \dot {y} (0) = 0, \quad \dot {f} _ {2} \left(t _ {1}\right) = 0
$$

$$
\delta z (0) = 0, \quad \dot {g} _ {1} \left(t _ {1}\right) = 0
$$

$$
\dot {\delta z} (0) = 0, \quad \dot {g} _ {2} (t _ {1}) = 0 \tag {9.3-27}
$$

这些边界条件也是与变量 $y, \dot{y}, z$ 和 $\dot{z}$ 的起始值和终止值对应的条件，但是过渡过程的时间间隔 $t_1$ 可以变化。由方程(9.3-27)的边界条件，方程(9.3-25)指出方程(9.3-26)右端的那个常数 $C$ 必须等于零。方程(9.3-18)的最后解答如下

$$
F - \dot {y} \frac {\partial F}{\partial \dot {y}} + \dot {y} \frac {d}{d t} \left[ \frac {\partial F}{\partial \ddot {y}} \right] - \ddot {y} \frac {\partial F}{\partial \ddot {y}} - \dot {z} \frac {\partial F}{\partial \dot {z}} + \dot {z} \frac {d}{d t} \left[ \frac {\partial F}{\partial \ddot {z}} \right] - \ddot {z} \frac {\partial F}{\partial \ddot {z}} = 0 \tag {9.3-28}
$$

并且满足下面两个方程中的一个

$$
\frac {\partial F}{\partial y} - \frac {d}{d t} \left(\frac {\partial F}{\partial \dot {y}}\right) + \frac {d ^ {2}}{d t ^ {2}} \left(\frac {\partial F}{\partial \ddot {y}}\right) = 0
$$

$$
\frac {\partial F}{\partial z} - \frac {d}{d t} \left[ \frac {\partial F}{\partial \dot {z}} \right] + \frac {d ^ {2}}{d t ^ {2}} \left[ \frac {\partial F}{\partial \ddot {z}} \right] = 0 \tag {9.3-29}
$$

方程(9.3-28)和(9.3-29)表示一个系统的两个变量 y 和 z 的微分方程, 它们是控制方程, 也是设计计算机所用的方程。

边界条件式(9.3-27)确定系统由一个主要运行状态过渡到另一状态的过渡过程的初始和终点条件。这样，如果方程式(9.3-27)所表示的条件都成立，系统便由一组固定的 $y,\dot{y},z,\dot{z}$ 过渡到另一组固定的 $y,\dot{y},z,\dot{z}$ 。方程(9.3-28)是一个三阶微分方程。方程(9.3-29)是一个四阶微分方程。于是除了 $y,\dot{y},z$ 和 $\dot{z}$ 的四个初始值而外，还可以假设一组与最后的 $y$ 相应的三个值 $\dot{y},z$ 和 $\dot{z}$ ，那就是，当 $y=y_{s}$ 时； $\dot{y}=0,z=z_{s}$ ，以及 $\dot{z}=0$ 。还必须在系统里加入一个稳定装置，使得在终止点，满足

$$
\ddot {y} = 0 \text {以及} \ddot {z} = 0
$$

我们看到，虽然上述情况比前面讨论过的一阶系统更为复杂，但是完全可以用同样的办法处理。

从此例中我们又看到，决定最优控制的两个条件中，式(9.3-29)是一个普遍的必要条件，它与初始状态和终点状态无关，条件式(9.3-28)是由终点时刻 $t_{1}$ 的不固定得到的。若引进式(9.3-19)和式(9.3-20)内曾用过的符号，则可将上述三个条件改写为

$$
\frac {\partial F}{\partial y _ {1}} - \frac {d}{d t} \frac {\partial F}{\partial y _ {2}} + \frac {d ^ {2}}{d t ^ {2}} \frac {\partial F}{\partial u _ {1}} = 0
$$

$$
\frac {\partial F}{\partial y _ {3}} - \frac {d}{d t} \frac {\partial F}{\partial y _ {4}} + \frac {d ^ {2}}{d t ^ {2}} \frac {\partial F}{\partial u _ {2}} = 0 \tag {9.3-30}
$$

$$
F - y _ {2} \frac {\partial F}{\partial y _ {2}} + y _ {2} \frac {d}{d t} \frac {\partial F}{\partial u _ {1}} - u _ {1} \frac {\partial F}{\partial u _ {1}} - y _ {4} \frac {\partial F}{\partial y _ {4}} + y _ {4} \frac {d}{d t} \frac {\partial F}{\partial u _ {2}} - u _ {2} \frac {\partial F}{\partial u _ {2}} = 0 \tag {9.3-31}
$$

$$
\frac {d y _ {1}}{d t} = y _ {2}
$$

$$
\frac {d y ^ {2}}{d t} = u _ {1}
$$

$$
\frac {d y _ {3}}{d t} = y _ {4}
$$

$$
\frac {d y _ {4}}{d t} = u ^ {2} \tag {9.3-32}
$$

这里共有七个方程式，含有六个未知函数和一个未知数： $y_{1}(t)$ ， $y_{2}(t)$ ， $y_{3}(t)$ ， $y_{4}(t)$ ， $u_{1}(t)$ ， $u_{2}(t)$ 和 $t_{1}$ 。对方程组(9.3-30)和(9.3-32)积分后将出现八个积分常数，后者将由四个初始状态和四个终点状态决定，它们是 $y_{1}(0)$ ， $y_{2}(0)$ ， $y_{3}(0)$ ， $y_{4}(0)$ ； $y_{1}(t_{1})$ ， $y_{2}(t_{1})$ ， $y_{3}(t_{1})$ ， $y_{4}(t_{1})$ 。方程式(9.3-31)就变为一个代数等式，由它可解出 $t_{1}$ 。

在讨论了几种类型的系统之后，我们再来回顾一下这些问题的解中包括的一些重要假设。在推导尤拉-拉格朗日必要条件时，我们只是做了形式上的推导，却故意没有提到两点重要的假设。首先，在推导时，我们先假定最优控制函数 $u(t)$ 是存在的。得到的结果是，如果它们存在的话，必满足尤拉-拉格朗日方程及相应的决定 t 的条件。在实际问题中，任意给定泛函指标式(9.3-5),(9.3-15)或(9.3-19)后是否一定存在最优控制函数呢?从上述讨论中是得不到答案的，而且像第一节那种不存在最优控制的情况是完全可能发生的。遗憾的是，关于存在性至今没有普遍的行之有效的判别准则，对这一问题的研究在数学上是一个困难的问题。

其次，在推导过程中，我们对 $y(t)$ 的增量 $\delta y(t)$ 未做任何限制，只说它是任意固定的足够光滑的函数。这意味着对控制量 $u(t)$ 的取值不做任何限制，如果最优控制存在的话，那么欲满足条件式(9.3-14)或(9.3-30)， $u(t)$ 可以在实轴上的任何处取值。这种情况有时在技术问题中是可以允许的，有时却是不能允许的。当 $u(t)$ 受限制时，例如，在实际问题中如果要求 $|u(t)| \leqslant M$ ，则尤拉-拉格朗日方程就未必有解。当然，如果求出的最优控制函数满足限制条件的话，事情就简单了。否则，前述古典变分法所提供的方法就将无能为力了。此时必须建立新的理论，以适应这种实际要求。这将在以后详细讨论。

#### 9.4 决定最优控制的标准方程组

前节内我们讨论了古典变分法中的几种特殊情况。那里受控对象的运动方程式实际上是多个一阶或二阶环节的联合。前面曾提到过另外一种普遍性问题，即系统的受控运动方程式已给定，须求出满足给定积分指标的最优控制函数。为了清楚起见，我们再将问题的数学内容叙述如下。设受控对象的运动由下列方程组所描述

$$
\frac {d x _ {i}}{d t} = f _ {i} \left(x _ {1}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}\right), \quad i = 1, 2, \dots , n, \quad r \leqslant n \tag {9.4-1}
$$

受控运动的质量指标是

$$
J = \int_ {0} ^ {t _ {1}} f _ {0} (x _ {1}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}) d t \tag {9.4-2}
$$

式中， $f_{0}, f_{i}$ 均为诸自变量的连续可微函数，而且不明显依赖于 t；积分上限 $t_{1}$ 为受控对象由某一初始状态到达指定的终点状态所需时间。

设 $\boldsymbol{x}_{0}=(x_{10},x_{20},\cdots,x_{n0})$ 为受控对象的初始状态， $\boldsymbol{x}_{1}=(x_{11},x_{21},\cdots,x_{n1})$ 为终点状态。须求出一个向量控制函数 $\boldsymbol{\dot{u}}(t)=(\dot{u}_{1}(t),\cdots,\dot{u}_{r}(t))$ ，使受控对象自 $x_{0}$ 点到达 $x_{1}$ 点，且使沿 $\dot{\boldsymbol{x}}(t)$ 和 $\dot{\boldsymbol{u}}(t)$ 的积分 J 取极小值，即

$$
J (\mathring {\boldsymbol {u}} (t)) = \int_ {0} ^ {t _ {1}} f _ {0} (\mathring {\boldsymbol {x}} (t), \mathring {\boldsymbol {u}} (t)) d t = \min \tag {9.4-3}
$$

必须指出该问题的几个特点：

（1）受控对象的两个端点都假设为固定的。所谓最优控制 $\mathring{u}(t)$ 是指一切将 $x_{0}$ 引至 $x_{1}$ 的控制函数中，使其在式(9.4-3)意义上是最好的。

(2) 在 t=0 时刻, 受控对象自 $x_{0}$ 出发, 到达 $x_{1}$ 的时刻 $t_{1}$ 并不固定。

（3）假设 $\boldsymbol{u}(t)$ 的每个分量 $u_{i}(t)$ 均为 t 的分段连续函数。每一个 $u_{i}(t)$ 在每一时刻 t 的取值不受限制，只要有界即可，在任意有限时间内，只有有限个第一类间断点。

在上述的假设条件下，我们来讨论最优控制所应满足的条件。下面的证明方法不同于古典变分法中常采用的变分方法，而采用文献[22]中的思想，用更为直观的几何证明。这种几何方法还将在下节内应用，那里将讨论 $\boldsymbol{u}(t)$ 受限制的情况下最优控制应满足的必要条件。

研究方程组(9.4-1)的同时，引进新坐标 $x_{0}=J$ , 并按式(9.4-2)写出关于 $x_{0}(t)$ 的微分方程式

$$
\frac {d x _ {0}}{d t} = f _ {0} (x _ {1}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}) \tag {9.4-4}
$$

将式(9.4-1)和(9.4-4)合并后就得到一个由 $n+1$ 个方程式组成的方程组。用 x 表示 $n+1$ 维向量 $(x_{0}, x_{1}, \cdots, x_{n})$ ，式(9.4-1)和(9.4-4)可联合写成一个向量方程式

$$
\frac {d \bar {\boldsymbol {x}}}{d t} = \bar {\boldsymbol {f}} (\bar {\boldsymbol {x}}, \boldsymbol {u}), \quad \bar {\boldsymbol {x}} (0) = \bar {\boldsymbol {x}} _ {0} = (0, x _ {1 0}, \dots , x _ {n 0}) \tag {9.4-5}
$$

式中 $\bar{\boldsymbol{x}}=(x_{0},x_{1},\cdots,x_{n});\bar{\boldsymbol{f}}=(f_{0},f_{1},\cdots,f_{n})$ 。最优控制 $\hat{\boldsymbol{u}}(t)$ 所对应的最优运动 $\hat{\boldsymbol{x}}(t)$ 和 $J(t)=x_{0}(t)$ 可以合并为 $\hat{x}$ ，并看成是 $n+1$ 维空间的一条曲线。这条曲线自 $\bar{x}_{0}$ 点出发，在 $t=t_{1}$ 时到达 $\bar{x}_{1}$ 点，并使 $x_{0}(t_{1})$ 取最小值（图 9.4-1）。

应用几何概念，求最优控制的问题可以转述成如下问题。对方程式(9.4-5)须求出一个控制函数 $\hat{\boldsymbol{u}}(t)$ ，使系统自 $\bar{x}_{0}$ 点出发，在某一时刻 $t=t_{1}$ ，到达平行于 $x_{0}$ 轴且通过 $(0,x_{1})$ 点的直线 L 上。使交点 $\bar{x}_{1}$ 的第一个分量 $x_{0}$ 达极小值。

为了寻求最优控制函数的特点，现将 $\mathring{\boldsymbol{u}}(t)$ 做某些微小的变化。取一个异于 $\mathring{\boldsymbol{u}}(t)$ 的控制函数

$$
\boldsymbol {u} (t) = \left\{ \begin{array}{l l} \dot {\boldsymbol {u}} (t) + \delta \boldsymbol {u}, & s - \varepsilon \delta t \leqslant t \leqslant s <   t _ {1} \\ \dot {\boldsymbol {u}} (t), & 0 \leqslant t <   s - \varepsilon \delta t, \quad s <   t \leqslant t _ {1} \end{array} \right. \tag {9.4-6}
$$

> 此处省略原书 **图 9.4-1**

上式内 $\varepsilon$ 为一足够小的正数， $\delta t$ 为任意正常数，s 为小于 $t_{1}$ 的任意固定时刻， $\delta u$ 为 任意 r 维常向量。我们看到，新的 $\boldsymbol{u}(t)$ 除在小区间 $[s-\varepsilon\delta t, s]$ 上有了变化外，在其余时刻均与 $\dot{\boldsymbol{u}}(t)$ 的取值相同。因此，受控系统式 (9.4-5) 在 $s-\varepsilon\delta t$ 时刻以前的运动依然是最优的，只在 $s-\varepsilon\delta t$ 时刻开始偏离最优运动轨线。当 $\varepsilon$ 足够小时，在这一小区间内系统运动的偏离量可用下列公式算出

$$
\begin{array}{l} \int_ {s - \epsilon \delta t} ^ {s} \left[ \bar {\boldsymbol {f}} (\bar {\boldsymbol {x}} (t), \mathring {\boldsymbol {u}} (t) + \delta \boldsymbol {u}) - \bar {\boldsymbol {f}} (\mathring {\boldsymbol {x}} (t), \mathring {\boldsymbol {u}} (t)) \right] d t \\ = \int_ {s - \varepsilon \delta t} ^ {s} \left(\sum_ {\alpha = 1} ^ {r} \frac {\partial \bar {\boldsymbol {f}}}{\partial u _ {\alpha}} \delta u _ {\alpha}\right) d t + \bar {O} _ {1} (\varepsilon , \delta \boldsymbol {u}) \\ = \varepsilon \delta t \left[ \sum_ {\alpha = 1} ^ {r} \frac {\partial \bar {\boldsymbol {f}} (\stackrel {\circ} {\boldsymbol {x}} (s) , \stackrel {\circ} {\boldsymbol {u}} (s))}{\partial u _ {\alpha}} \delta u _ {\alpha} \right] + \bar {O} (\varepsilon , \delta \boldsymbol {u}) \tag {9.4-7} \\ \end{array}
$$

上式右端之第一项由于用 $\bar{x}$ 代换了 $\bar{x}(s)$ 所产生的误差对 $\varepsilon$ 来说将是高阶无穷小，并于 $\bar{O} (\varepsilon ,\delta \pmb {u})$ 内。不难证明，当 $\varepsilon \rightarrow 0$ 时， $\lim \frac{\bar{O} (\varepsilon,\delta\pmb{u})}{\varepsilon}$ 为零向量；当 $\| \delta \pmb {u}\| \to 0$ 时 $\frac{\bar{O} (\varepsilon,\delta\pmb{u})}{\|\delta\pmb{u}\|}\rightarrow \mathbf{0}$ 。

最优运动轨线在 s 时刻已经发生了偏差。在 s 以后，控制函数没有改变。令

$$
\delta t \left(\boldsymbol {f} \left(\stackrel {\circ} {\boldsymbol {x}} (s), \stackrel {\circ} {\boldsymbol {u}} + \delta \boldsymbol {u}\right) - \bar {\boldsymbol {f}} \left(\stackrel {\circ} {\boldsymbol {x}} (s), \stackrel {\circ} {\boldsymbol {u}} (s)\right)\right) = \bar {\boldsymbol {y}} (s) \tag {9.4-8}
$$

在 $s$ 时刻的轨线偏离是 $\varepsilon \overline{\mathbf{y}}(s)$ 。从微分方程的理论中我们知道，由于小的初始偏差引起的轨道偏差主要部分可用线性化的办法算出，即在 $s \leqslant t \leqslant t_1$ 区间内 $\delta \overline{\mathbf{x}}(t) = \overline{\varepsilon \mathbf{y}}(t)$ 可由下列线性化方程组求出

$$
\frac {d \mathbf {y} _ {i} (t)}{d t} = \sum_ {\alpha = 1} ^ {n} \frac {\partial f _ {i}}{\partial x _ {\alpha}} y _ {\alpha}, \quad i = 0, 1, \dots , n, \quad s \leqslant t \leqslant t _ {1} \tag {9.4-9}
$$

或写成向量方程式

$$
\frac {d \bar {\mathbf {y}}}{d t} = A (t) \bar {\mathbf {y}} \tag {9.4-10}
$$

此处

$$
A (t) = \left( \begin{array}{c c c c} \frac {\partial f _ {0}}{\partial x _ {0}} & \frac {\partial f _ {0}}{\partial x _ {1}} & \dots & \frac {\partial f _ {0}}{\partial x _ {n}} \\ \vdots & \vdots & & \vdots \\ \frac {\partial f _ {n}}{\partial x _ {0}} & \frac {\partial f _ {n}}{\partial x _ {1}} & \dots & \frac {\partial f _ {n}}{\partial x _ {n}} \end{array} \right)
$$

其中各系数是沿最优轨线求出的，即

$$
\frac {\partial f _ {i}}{\partial x _ {\alpha}} = \frac {\partial f _ {i} (\stackrel {\circ} {\boldsymbol {x}} (t) , \stackrel {\circ} {\boldsymbol {u}} (t))}{\partial x _ {\alpha}}
$$

故它们均为已知的时间 t 的函数。

式(9.4-9)或(9.4-10)是一个线性方程组。设 $\Phi(t, s)$ 是它的基本解矩阵。那么，它的解将是

$$
\bar {\mathbf {y}} (t) = \Phi (t, s) \bar {\mathbf {y}} (s), \quad s \leqslant t \leqslant t _ {1} \tag {9.4-11}
$$

现在研究在 $t=t_{1}$ 时刻轨道偏离的情况。显然当 $t=t_{1}$ 时有

$$
\delta \bar {\boldsymbol {x}} (t _ {1}) = \varepsilon \bar {\boldsymbol {y}} (t _ {1}) = \varepsilon \Phi (t _ {1}, s) \bar {\boldsymbol {y}} (s) \tag {9.4-12}
$$

再根据式(9.4-7)和 $\bar{y}(s)$ 的定义，我们有

$$
\mathbf {y} (s) = \delta t B (s) \delta \mathbf {u} \tag {9.4-13}
$$

上式中 $B(s)$ 为 $n \times r$ 阶长方阵，

$$
B (s) = \left[ \begin{array}{c c c c} \frac {\partial f _ {0}}{\partial u _ {1}} & \frac {\partial f _ {0}}{\partial u _ {2}} & \dots & \frac {\partial f _ {0}}{\partial u _ {r}} \\ \vdots & \vdots & & \vdots \\ \frac {\partial f _ {n}}{\partial u _ {1}} & \frac {\partial f _ {n}}{\partial u _ {2}} & \dots & \frac {\partial f _ {n}}{\partial u _ {r}} \end{array} \right] \tag {9.4-14}
$$

其中每个元素都是在最优轨线的 s 时刻算出的, 即

$$
\frac {\partial f _ {i}}{\partial u _ {j}} = \frac {\partial f _ {i} (\stackrel {\circ} {\boldsymbol {x}} (t) , \stackrel {\circ} {\boldsymbol {u}} (t))}{\partial u _ {j}}
$$

按式(9.4-13)和(9.4-12)，若 $\varepsilon$ 为足够小的正数， $s$ 为固定时刻，于是每一个特定的 $\delta u$ 便对应一个 $\bar{y}(s)$ ，进而有一个 $\delta \bar{x}(t_1)$ 。当常向量 $\delta u$ 在 $r$ 维空间零点周围变化时， $\bar{y}(s)$ 和 $\delta \bar{x}(t_1)$ 也将在 $\bar{x}_1$ 点周围改变其方向及大小。一切可能的 $\{\delta u\}$ 按式(9.4-12)和(9.4-13)构成的所有 $\{\delta \bar{x}(t_1)\}$ 将是一个线性子空间 $K$ （把 $\bar{x}_1$ 看成它们的坐标原点）。子空间 $K$ 的维数将不大于 $r$ 。由于 $\bar{x}$ 是最优运动，通过点 $\bar{x}_1$ 而平行于 $x_0$ 轴的直线 $L$ 不可能包含于子空间 $K$ 内。否则按式(9.4-6)的方法将 $\dot{u}(t)$ 加以改变，受控系统式(9.4-5)有可能在 $t_1$ 时刻到达直线 $L$ 上比 $x_0(J)$ 取值更小的点，而这与 $\dot{u}(t)$ 为最优控制的假定相矛盾，故是不可能的。由此可知，当 $r = n$ 时， $K$ 的维数不可能大于 $n - 1$ ，否则直线 $L$ 将包含于其内。

既然 K 的维数不大于 r（当 r=n 时不大于 n-1），则存在一个通过 $\bar{x}_{1}$ 点的 n-1 维超平面 P，它能将 K 和以 $\bar{x}_{1}$ 为始点的向量 $z=(-1,0,\cdots,0)$ 完全隔开。取 $\bar{\psi}_{1}$ 为 P 的与向量 z 位于同侧的法向量，称之为 P 的外法向量，此时不等式

$$
\left(\delta \bar {\boldsymbol {x}} \left(t _ {1}\right), \bar {\boldsymbol {\psi}} _ {1}\right) \leqslant 0 \tag {9.4-15}
$$

对任何 $\bar{y}(s)$ 均成立。考虑到 $\varepsilon>0, \delta t>0$ ，根据式(9.4-8)，上式可写为

$$
\left(\Phi \left(t _ {1}, s\right) \bar {\mathbf {y}} (s), \bar {\boldsymbol {\psi}} _ {1}\right) \leqslant 0
$$

其中 $\bar{\psi}_{1}=(\psi_{01},\psi_{11},\psi_{21},\cdots,\psi_{n1})$ 为非零向量，且 $\psi_{01}\leqslant0$ 。由于内积的特性有

$$
\left(\Phi \left(t _ {1}, s\right) \bar {\mathbf {y}} (s), \bar {\boldsymbol {\psi}} _ {1}\right) = \left(\bar {\mathbf {y}} (s), \Phi^ {\mathrm{r}} \left(t _ {1}, s\right) \bar {\boldsymbol {\psi}} _ {1}\right) \tag {9.4-16}
$$

再研究线性化方程组(9.4-9)的共轭方程组

$$
\frac {d \psi_ {0}}{d t} = - \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha}}{\partial x _ {0}} \psi_ {\alpha}
$$

...

$$
\frac {d \psi_ {n}}{d t} = - \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha}}{\partial x _ {n}} \psi_ {\alpha} \tag {9.4-17}
$$

或者写成向量的方程式

$$
\frac {d \bar {\psi}}{d t} = - A ^ {\tau} (t) \bar {\psi} \tag {9.4-18}
$$

令 $F(t,s)$ 是式(9.4-18)的基本解矩阵， $F(\tau,\tau)=E$ 。不难证明， $F(t,s)=(\Phi^{\tau}(t,s))^{-1}$ 这个关系式总成立。这是因为

$$
\frac {d \Phi^ {- 1} \Phi}{d t} = \frac {d \Phi^ {- 1}}{d t} \Phi + \Phi^ {- 1} \frac {d \Phi}{d t} = 0
$$

故

$$
\frac {d \Phi^ {- 1}}{d t} = - \Phi^ {- 1} A (t) \Phi \Phi^ {- 1} = - \Phi^ {- 1} A (t)
$$

将上式两端转置后有

$$
\frac {d (\Phi^ {\tau}) ^ {- 1}}{d t} = - A ^ {\tau} (t) (\Phi^ {\tau}) ^ {- 1} \tag {9.4-19}
$$

这就证明了 $(\Phi^{r}(t,s))^{-1}$ 是式(9.4-18)的基本解矩阵。令 $\bar{\psi}(t)$ 是式(9.4-18)的一个特解，且

$$
\bar {\boldsymbol {\psi}} (t _ {1}) = \bar {\boldsymbol {\psi}} _ {1} \tag {9.4-20}
$$

此处 $\psi_{1}$ 是前述之外法向量。于是

$$
\bar {\boldsymbol {\psi}} _ {1} = \left(\Phi^ {\tau} (t _ {1}, s)\right) ^ {- 1} \bar {\boldsymbol {\psi}} (s)
$$

将上式代入式(9.4-16)后便有

$$
(\bar {\mathbf {y}} (s), \Phi^ {\tau} (t _ {1}, s) (\Phi^ {\tau} (t _ {1}, s)) ^ {- 1} \bar {\boldsymbol {\psi}} _ {1} (s)) = (\bar {\mathbf {y}} (s), \bar {\boldsymbol {\psi}} (s)) \leqslant 0
$$

再由式(9.4-8)将 $\bar{\mathbf{y}}(s)$ 之值代入上式，便得到最后不等式

$$
\bar {f} (\stackrel {\circ} {x} (s), \stackrel {\circ} {u} (s) + \delta u) - (\bar {f} (\stackrel {\circ} {x} (s), \stackrel {\circ} {u} (s)), \bar {\psi} (s)) \leqslant 0
$$

或者

$$
\bar {f} (\stackrel {\circ} {x} (s), \stackrel {\circ} {u} (s), \bar {\psi} (s)) \geqslant (\bar {f} (\stackrel {\circ} {x} (s), \stackrel {\circ} {u} + \delta u), \bar {\psi} (s)) \tag {9.4-21}
$$

记函数

$$
H (\bar {\boldsymbol {x}}, \bar {\boldsymbol {\psi}}, \boldsymbol {u}) = \sum_ {\alpha = 0} ^ {n} f _ {\alpha} \psi_ {\alpha} \tag {9.4-22}
$$

不难直接检查此函数 H 与方程组(9.4-5)及(9.4-18)的关系是

$$
\frac {\partial H}{\partial \psi_ {i}} = \frac {d x _ {i}}{d t}, \quad i = 0, 1, \dots , n
$$

$$
\frac {\partial H}{\partial x _ {i}} = - \frac {d \psi_ {i}}{d t}, \quad i = 0, 1, \dots , n \tag {9.4-23}
$$

函数 H 与分析力学中的哈密顿函数的结构形式很类似，故常称为哈密顿函数。通过函数 H 可知条件式(9.4-21)等价于下列等式:

$$
H (\stackrel {\circ} {x} (s), \bar {\psi} (s), \stackrel {\circ} {u} (s)) = \operatorname{ext} H (\stackrel {\circ} {x}, \bar {\varphi} (s), \stackrel {\circ} {u} (s) + \delta u) \tag {9.4-24}
$$

这就是说，在受控系统的最优运动轨线上，在 s 时刻对任意足够小的 $\delta u$ ，最优控制 $\mathring{u}(s)$ 使 H 取极值。但是，由于 s 是任意的， $0 < s < t_{1}$ ，故条件式（9.4-24）对最优轨线上除两个端点外的一切点均成立。若函数 $f_{i}(x,u)$ 对 u 的每个分量 $u_{i}$ 是连续可微函数，则式（9.4-24）还可以写成

$$
\frac {\partial}{\partial u _ {i}} H (\stackrel {\circ} {\boldsymbol {x}} (t), \bar {\boldsymbol {\psi}} (t), \boldsymbol {u}) = 0
$$

$$
i = 1, 2, \dots , r, \quad 0 <   t \leqslant t _ {1} \tag {9.4-25}
$$

上述讨论中，我们均假定系统到达终点的时间 $t_{1}$ 已经给定，因此在推导上述条件时，对 $t_{1}$ 未做变化。实际上由于到达端点的时间也可以变化，由变化 $t_{1}$ 还可以求出另外一个最优控制必须满足的必要条件。现设到达终点的时间不是 $t_{1}$ 而是 $t_{1} + \Delta t_{1}, \Delta t_{1}$ 是任意足够小的正数或负数。在区间 $[0, t_{1} + \Delta t_{1}]$ 定义控制函数为

$$
\boldsymbol {u} (t) = \left[ \begin{array}{l l} \mathring {\boldsymbol {u}} (t), & 0 \leqslant t \leqslant t _ {1} \\ \mathring {\boldsymbol {u}} (t _ {1}), & t _ {1} \leqslant t \leqslant t _ {1} + \Delta t _ {1} \end{array} \right. \tag {9.4-26}
$$

由于终端时刻的变化而产生的增量 $\delta\bar{x}(t_{1})$ 同样应满足条件式(9.4-15)，即

$$
\left(\boldsymbol {f} \left(\stackrel {\circ} {\boldsymbol {x}} \left(t _ {1}\right), \stackrel {\circ} {\boldsymbol {u}} \left(t _ {1}\right)\right) \Delta t _ {1}, \bar {\boldsymbol {\psi}} _ {1}\right) \leqslant 0
$$

由于 $\Delta t_{1}$ 是任意的，其符号可正可负，故上式只有在左端为零时才能成立。因此，可以断言在 $t_{1}$ 时刻有

$$
H \left(\stackrel {\circ} {x} \left(t _ {1}\right), \bar {\psi} \left(t _ {1}\right), \stackrel {\circ} {u} \left(t _ {1}\right) = \left(\bar {f} \left(\stackrel {\circ} {x} \left(t _ {1}\right), \stackrel {\circ} {u} \left(t _ {1}\right)\right), \bar {\psi} \left(t _ {1}\right)\right) = 0 \quad (9. 4 - 2 7) \right.
$$

但是，根据关系式(9.4-22)可以算出当 $\mathbf{\dot{u}}(t)$ 为固定时

$$
\begin{array}{l} \frac {d H}{d t} = \left[ \frac {d \bar {\boldsymbol {f}}}{d t}, \bar {\boldsymbol {\psi}} \right] + \left[ \bar {\boldsymbol {f}}, \frac {d \bar {\boldsymbol {\psi}}}{d t} \right] \\ = \left[ A (t) \frac {d \stackrel {\circ} {\boldsymbol {x}}}{d t}, \bar {\boldsymbol {\psi}} \right] + (\bar {\boldsymbol {f}}, - A ^ {\tau} (t) \bar {\boldsymbol {\psi}}) \\ = (\bar {\boldsymbol {f}}, A ^ {\tau} (t) \bar {\boldsymbol {\psi}}) - (\bar {\boldsymbol {f}}, A ^ {\tau} (t) \bar {\boldsymbol {\psi}}) \\ \equiv 0 \\ \end{array}
$$

此处 $A(t)$ 为式(9.4-10)中的方阵。故沿最优运动轨线，哈密顿函数恒为常数

$$
H \left(\stackrel {\circ} {x} \left(t _ {1}\right), \bar {\psi} \left(t _ {1}\right), \stackrel {\circ} {u} \left(t _ {1}\right)\right) = \text { const }, \quad 0 \leqslant t \leqslant t _ {1}
$$

由式(9.4-27)知 $H(t_{1})=0$ ，所以又有

$$
H \left(\stackrel {\circ} {x} \left(t _ {1}\right), \stackrel {\circ} {\psi} \left(t _ {1}\right), \stackrel {\circ} {u}\right) \equiv 0, \quad 0 \leqslant t \leqslant t _ {1} \tag {$9.4-27^{\prime$}}
$$

这样我们就得到了一套完整的最优控制应该满足的必要条件。现将这些条件集中写出

$$
\frac {d x _ {i}}{d t} = f _ {i} (\mathring {\boldsymbol {x}} (t), \mathring {\boldsymbol {u}} (t)), \quad i = 0, 1, \dots , n
$$

$$
\boldsymbol {x} (0) = \left(0, x _ {1 0}, x _ {2 0}, \dots , x _ {n 0}\right)
$$

$$
\boldsymbol {x} \left(t _ {1}\right) = \left(x _ {1 1}, x _ {2 1}, \dots , x _ {n 1}\right)
$$

$$
\frac {d \psi_ {i}}{d t} = - \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha}}{\partial x _ {i}} \psi_ {\alpha}, \quad i = 0, 1, \dots , n
$$

$$
\frac {\partial H}{\partial u _ {i}} = 0, \quad i = 1, 2, \dots , r
$$

$$
H \equiv 0 \tag {9.4-28}
$$

总之，如果控制量 $\boldsymbol{u}(t)$ 的取值不受限制，自 $x_{0}$ 点至 $x_{1}$ 点的最优控制 $\mathring{\boldsymbol{u}}(t)$ 存在，那么必存在一组非零函数 $\psi_{0}(t),\cdots,\psi_{n}(t)$ ,后者是式(9.4-28)中第二组方程式的解，使哈密顿函数 H 在每一时刻对变量 u 取极值，而且沿最优运动轨线 H 恒等于零。

现分析一下必要条件式(9.4-28)的结构。首先，由于各 $f_{i}$ 中不含 $x_{0}$ ，故

$$
\frac {d \psi_ {0}}{d t} = 0, \quad \psi_ {0} = \text { const }, \quad \psi_ {0} \leqslant 0
$$

这里的第三个条件是由于一切 $\delta\bar{x}(t_{1})$ 所构成的子空间 K 不包含向量 $z=(-1,0,\cdots,0)$ 。其次，式(9.4-28)内共含有 $2n+r+2$ 个未知函数和一个未知数 $t_{1}$ ，即共有 $2n+r+3$ 个未知因素，而恰恰有 $2n+r+3$ 个方程式，若最优控制存在的话，可以由式(9.4-28)求出。式(9.4-28)内包括了 $2n+2$ 个微分方程式，其他 $r+1$ 个方程式是代数方程。为了解两组微分方程式必须有 $2n+2$ 个边界条件。实际上我们只有 $2n+1$ 个边界条件，因为 $x_{0}(t)$ 的终点值（最优值）是未知的。看起来，似乎还缺少一个条件。事实上，由于对 $\bar{\psi}$ 的方程组是线性齐次的，初始条件只能准确到某一常数公因子，故对它的求解只需要有 n 个初始条件就够了。此外，还有一个初始条件应由式(9.4-27') 在 t=0 时确定，所以实际上只需有 2n 个初始条件就能求出两组微分方程的解。剩下的一个边界条件恰好留给 $t_{1}$ 。因此，式(9.4-28)中不仅方程式的个数是足够的，而且边界条件也恰恰满足需要。正由于这个理由，我们说式(9.4-28)给出了求最优控制所必需的完整条件。因此，我们称式(9.4-28)为决定最优控制的标准方程组。

但是，还应该注意到，如果式(9.4-28)只有一个孤立的解，它连接 $x_{0}$ 和 $x_{1}$ ，那么它就是唯一的最优运动和最优控制。如果满足式(9.4-28)的控制和运动不止一个，而有很多个，则在这些运动中仍有必要加以选择。这就是说，条件式 (9.4-28)仅仅是最优控制和最优运动的必要条件。满足式(9.4-28)的控制函数不能保证都是最优的。还有一种情况可能是不存在式(9.4-28)能够使受控系统自 $x_{0}$ 点出发到达 $x_{1}$ 点的解，此时最优控制将不存在。如果满足式(9.4-28)的解有很多个，每一个都使 $x_{0}=J=\min$ ，这时最优控制将不唯一，在设计实际系统时可任选其中的一个加以实现。

#### 9.5 附加限制时的最优控制和喷气发动机控制设计

在实际问题中，除预先给定控制过程的积分指标外，还可能提出某些关于受控对象输出坐标的限制条件。例如第 9.2 节中喷气发动机的工作过程中，常要求对发动机温度进行限制。这种限制也往往是以积分形式给定的，例如要求控制过程满足条件

$$
J _ {1} = \int_ {0} ^ {t _ {1}} g (\boldsymbol {x}, \boldsymbol {u}) d t \leqslant l \tag {9.5-1}
$$

其中 l 为某一给定常数。这样必须在使受控对象式(9.4-1)自状态 $x_{0}$ 引至 $x_{1}$ ，且满足条件(9.5-1)的一切控制中寻求使式(9.4-2)达极小值的控制函数——条件最优控制函数 $u(t)$ 。

如果设计控制系统时先不考虑式(9.5-1)的限制条件，而直接解方程组(9.4-28)，这样求出的 $u(t)$ 和 $x(t)$ ，必须再代入(9.5-1)，检查该条件是否被满足。自然，这时有两种可能：由式(9.4-28)求出的最优控制满足条件式(9.5-1)，此时限制条件式(9.5-1)不改变前述的设计结果；另一种可能是由式(9.4-28)求出的最优控制不满足条件式(9.5-1)，此时就不能按原来的计算进行设计了，而要寻求满足式(9.5-1)的新的条件最优控制。上述两种情况中，对设计者有意义的是第二种，因此，当由式(9.4-28)求出的最优控制不满足式(9.5-1)时，我们有理由在式(9.5-1)内取等号，即将式(9.5-1)改写成条件

$$
J _ {1} = \int_ {0} ^ {t _ {1}} g (\boldsymbol {x}, \boldsymbol {u}) d t = l \tag {9.5-2}
$$

用类似前节的方法可以证明 $^{[22]}$ 如果 $\mathring{\boldsymbol{u}}(t)$ 和 $\mathring{\boldsymbol{x}}(t)$ 是满足条件式(9.5-2)的自 $x_{0}$ 点引至 $x_{1}$ 点的最优控制，如果它们不是 $J_{1}$ 的极值函数，则必存在一个常数 $\lambda$ ，使 $\mathring{\boldsymbol{u}}(t)$ 和 $\mathring{\boldsymbol{x}}(t)$ 成为满足下列积分泛函指标的最优控制

$$
J _ {0} = \int_ {0} ^ {t _ {1}} \left[ f _ {0} (\boldsymbol {x}, \boldsymbol {u}) + \lambda g (\boldsymbol {x}, \boldsymbol {u}) \right] d t = \min \tag {9.5-3}
$$

以新的积分指标式(9.5-3)代替原积分式(9.4-2)后，依然可以利用标准方程组(9.4-28)求出条件最优控制。此时又多了一个未知常数 $\lambda$ 。但是，为了求 $\lambda$ 我们却又多了一个条件式(9.5-2)。于是，如果条件最优控制函数存在的话，由式 (9.4-28), (9.5-2), (9.5-3)有希望将它求出。

作为例子，我们继续研究第 9.2 节中曾经介绍过的喷气发动机的过程控制问题，并对发动机输入至轮机的工作物体的温度加以限制。根据式(9.2-4)和(9.2-5),当控制速度时，若只把旋转速度误差看做是最重要的因素，控制准则就变成

$$
\int_ {0} ^ {t _ {1}} f (N - N _ {s}) d t = \min \tag {9.5-4}
$$

于是，由方程(9.3-13)的控制条件可以简单地给出等式

$$
f _ {1} (N - N _ {s}) = 0
$$

由于 $f_{1}$ 的性质, 我们有 $N = N_{s}$ 。这个结果表示: 在发动机的性能没有受到其他限制条件的情况下, 这种速度控制将保持速度误差恒等于零, 然而只有允许温度无限升高, 才可能实际达到上述要求。这个结果和前面的方程 (9.3-13) 前后不一致, 在那个方程里, N 并不是一个时间的不连续的函数。这个例子是一般问题的一种显然情形。但是这个结果指出必须附带有另外的准则才能给出实际上有意义的系统。

设 T 表示发动机工作温度的瞬时值，根据式(9.2-4)内的温度限制表达式，对温度的限制条件可写成

$$
J _ {1} = \int_ {0} ^ {t _ {1}} f _ {3} (T (t)) d t \tag {9.5-5}
$$

现在假设在速度控制问题中把条件式(9.5-4)和(9.5-5)合并考虑。根据本节内前面的讨论，可以写成一个类似式(9.5-3)的积分指标

$$
J _ {0} = \int_ {0} ^ {t _ {1}} \left[ f _ {1} (N - N _ {s}) + \lambda f _ {3} (T) \right] d t = \min \tag {9.5-6}
$$

所以 $F = f_{1}(N - N_{s}) + \lambda f_{3}(T)$ 。由于利用了方程(9.2-5)，方程(9.3-13)变成

$$
f _ {1} (N - N _ {s}) + \lambda f _ {3} (T) = \lambda a \tau \dot {N} \dot {f} _ {3} (T) \tag {9.5-7}
$$

这是过渡过程的控制方程。当过渡过程终止时，理想的稳定装置发生作用，所以就有

$$
N = N _ {s}
$$

$$
\dot {N} = 0 \tag {9.5-8}
$$

方程(9.5-7)和(9.5-8)描写出整个控制系统的性质。我们可以设想，有一架计算机安装在系统里，它由测量机构获得有关 $N$ 和 $T$ 的资料，贮藏有 $\lambda, a$ 和 $\tau$ 的资料，以及燃料速度和 $N, T$ 之间的联系，然后根据方程(9.5-7)，产生适当的燃料喷射率的信号。当 $N$ 即将到达 $N_{s}$ 时，稳定机构参与作用，所以过渡过程终止时方程(9.5-8)自然满足，一般说来，控制方程(9.5-7)是非线性方程，计算机不可能是线性元件，不像简单的电阻电容线路那样。

作为一个例子，考虑下述情况，当 $T > L_{2}$ 时, $f_{3}(T) = (T - L_{2})^{n}$ , 当 $T < L_{1}$ 时, $f_{3}(T)=(L_{1}-T)^{n}$ 。通常，次数 n 必须大于 1，因为如果 n<1，T 可以是无限大，这样即使积分

$$
\int_ {0} ^ {t _ {1}} f _ {3} (T) d t
$$

是有限的，将使 N 不连续，这不符合实际情况。在讨论中，令 n=2，并且令 $f_{1}(N-N_{s})=(N-N_{s})^{2}$ 。所以我们又以对于给定值所发生的平均平方误差作为误差的量度，于是方程(9.5-7)变成

$$
\frac {(N - N _ {s}) ^ {2}}{\lambda} + (L - a N) ^ {2} = a ^ {2} \tau^ {2} \dot {N} ^ {2} \tag {9.5-9}
$$

在这个式子里：对加速度的情形，即当 $N < N_{s}$ 时

$$
\dot {N} > 0, L = L _ {2}
$$

对减速度的情形，即当 $N > N_{s}$ 时有

$$
\dot {N} <   0, L = L _ {1}
$$

此时，控制系统的方块图可用图 9.5-1 表示如下。

> 此处省略原书 **图 9.5-1**

$N_{e}$ 是真正的发动机速度, 假定我们考虑减速度的情况, $N > N_{s}$ 。在过渡过程中, $N_{e} - N_{s}$ 是正的, 所以计算机和发动机伺服系统之间的开关闭合, 计算机发出信号。计算机根据方程(9.5-9)产生信号 $a\tau \dot{N}$ 。在图 9.5-1 中用一个直角三角形边长的关系描写信号之间的联系。发动机伺服控制系统要设计得使发动机尽可能服从计算机所发出的信号 $a\tau \dot{N}$ 。这只要利用图中所表示的放大系数很高的线路就可以达到目的。当速度误差的值变得非常小的时候, 计算机就停止发出信号, 于是系统的稳定装置将保证系统保持指定速度 $N_{s}$ , 而处于稳定状态, 于是系统满足方程(9.5-8)的条件。

控制系统里有一个可调整的参数 $\lambda$ 。对于任意一个给定的 $\lambda$ 和得到的超温积分来说，这个系统将会使速率误差平方的积分取极小值。 $\lambda$ 的值确定超温积分的 值式(9.5-6)，我们考虑 $aN_{s} = L$ 这一特殊情况，那就是，与温度的限制相适应的加速度或减速度是服从方程(9.2-5)的。有兴趣地注意到，在这个特殊例子里，根据方程(9.5-9)的控制条件，当 $N = N_{s}$ 时， $\dot{N} = 0$ ，所以并不需要一个额外的稳定装置，图(9.5-1)中控制系统里的开关也就可去掉。在这一特殊情况下，方程(9.5-9)变成线性的，可以写成

$$
E (L - \alpha N) = a \tau \dot {N} \tag {9.5-10}
$$

其中

$$
E = \left[ 1 + \frac {1}{a ^ {2} \lambda} \right] ^ {\frac {1}{2}} \tag {9.5-11}
$$

现在那些积分可以很容易的计算出来，例如，温度积分是

$$
\begin{array}{l} \int_ {0} ^ {t _ {1}} (T - L) ^ {2} d t = \int_ {0} ^ {t _ {1}} (a N - L + a \tau \dot {N}) ^ {2} d t \\ = (E - 1) ^ {2} \int_ {0} ^ {t _ {1}} (L - a N) ^ {2} d t \\ = a ^ {2} (E - 1) ^ {2} \int_ {0} ^ {t _ {1}} \left(N _ {s} - N\right) ^ {2} d t \\ = a ^ {2} (E - 1) ^ {2} \int_ {N _ {0}} ^ {N _ {s}} \left(N _ {s} - N\right) ^ {2} \frac {d N}{\dot {N}} \\ = a ^ {3} \tau (E - 1) ^ {2} \int_ {N _ {0}} ^ {N _ {s}} \frac {(N _ {s} - N) ^ {2} d N}{E a (N _ {s} - N)} \\ = a ^ {2} \tau \frac {(E - 1) ^ {2}}{E} \frac {1}{2} \left(N _ {s} - N _ {0}\right) ^ {2} \\ = \frac {\tau}{2} \frac {(E - 1) ^ {2}}{E} (L - a N _ {0}) ^ {2} \\ \end{array}
$$

于是得到

$$
\frac {1}{\tau} \int_ {0} ^ {t _ {1}} \frac {(T - L) ^ {2}}{(L - a N _ {0}) ^ {2}} d t = \frac {(E - 1) ^ {2}}{2 E} \tag {9.5-12}
$$

其中 $N_{0}$ 是过渡过程开始时的发动机速度。同样，速度积分是

$$
\frac {a ^ {2}}{\tau} \int_ {0} ^ {t _ {1}} \left(\frac {N - N _ {s}}{L - a N _ {0}}\right) ^ {2} d t = \frac {1}{2 E} \tag {9.5-13}
$$

假设 $T_{max}$ 是最高温度，于是

$$
\frac {T _ {\mathrm{max}} - L}{L - a N _ {0}} = E - 1 \tag {9.5-14}
$$

从方程(9.5-10)我们有

$$
E a (N _ {s} - N) = a \tau \frac {d N}{d t}
$$

在过渡过程中，控制系统的特性时间用 $\tau^{*}$ 表示

$$
\tau^ {*} = \frac {\tau}{E} \tag {9.5-15}
$$

这些方程的左端已经化成无量纲的形式了。最高温度 $T_{max}$ 是过渡过程开始时的温度。

当 $E = 1(\lambda = \infty)$ 时，这时候温度不超出，这与我们前面的叙述相符：当 $\lambda \to \infty$ 时，表示超温的积分等于零。速率积分等于 0.5，并且 $\tau^{*} = \tau$ 。如果 $E$ 增大（或者 $\lambda$ 减小），温度积分和最高温度增大，而速度积分和时间常数减小。可以取 $\sqrt{2}$ 为 $E$ 的一个折中值，或者 $a^2\lambda = 1$ 。只要把 $E$ 或者 $\lambda$ 的值给定，控制计算机的程序也就确定了，于是可以进行控制系统的设计工作。

对于方程(9.5-9)的普遍情形，积分值计算起来非常麻烦，但是可以采用同样的步骤设计控制系统。勃克森包姆和胡德给出方程(9.5-10)真正的解答，那就是求出 t 的函数 $N^{[8]}$ ,但是我们在这里对于控制系统的设计并不着重在求得这种解。控制系统的全部资料由方程(9.5-10)本身给出，因为这个方程已经告诉我们应该如何构造控制计算机。如果根据那些条件做出计算机，于是就能保证得到希望的性能。N 对于时间的具体变化情况倒并不重要。因此我们的设计方法与其说是根据假设的方程的解去进行设计。倒不如说是“设计”非线性方程本身。

#### 9.6 控制量受限制时的最优控制设计

前面数节内所讨论的最优控制问题都基于一个重要假定: 控制函数 $\boldsymbol{u}(t)$ 的取值范围事先不受任何限制。按方程组 (9.4-28) 求出的最优控制函数 $\dot{\boldsymbol{u}}(t)=(\dot{\boldsymbol{u}}_{0}(t),\cdots,\dot{\boldsymbol{u}}_{r}(t))$ 可以在 r 维空间的任何地方取值。我们曾经指出过, 控制量 u 的取值在绝大多数情况下总是受限制的。控制量的变化只能在预先确定的范围内取值。而古典变分法的理论中其主要方法的证明和主要结论实质上都没有充分地, 或完全没有考虑这种限制条件。为了确切地反映这一基本事实, 古典变分法的理论和方法就难于直接采用。这里需要有另外一种研究方法, 以使古典变分法的应用范围得以改进, 使之更适合于实际控制问题的基本特点。

值得指出的是，这种附加的控制系统特有的限制条件，无论在实际技术问题中或在理论上都使得最优问题与古典变分法内所研究的问题具有本质上的不同。例如在古典变分法的意义上并不存在最优解的时候，考虑了限制条件后，最优解就不仅存在，而且还具有重要的实际意义。举例来说，在 x,y 平面上有一条光滑曲线 $y=f(x)$ ,如果此曲线在全平面内确实有极小值存在，那么用求极值的古典方法可以求出极值及其对应的横坐标 $x_{0}$ 。但是，当 x 的取值范围受限制时，如 $a\leqslant x\leqslant b$ ,该函数 $f(x)$ 在此区间内可能没有极值，而最小值却总是存在的。此时古典方法就完全无能为力了。本章初我们曾讨论过的物体运动一例中，按古典变 分法的提法（即图 9.1-1 中 $F(t)$ 不受限制的情况）最速控制是不存在的，但当作用力 $F(t)$ 的取值受限制时，如 $0<a\leqslant F(t)\leqslant b$ ,最优控制就存在了。这一点读者不难从简单的物理概念中推知。

总之，本节内我们将介绍控制量受限制时的最优控制的设计问题。设受控对象的运动方程依然为式(9.4-1)，性能指标为式(9.4-2)型的积分泛函。控制量 $\pmb{u}$ 的取值范围假定为 $r$ 维空间的某一点集 $U$ ，后者可能是一个区域，例如由下列不等式组所确定

$$
g _ {i} \left(u _ {1}, u _ {2}, \dots , u _ {n}\right) \leqslant 0, \quad i = 1, 2, \dots , m \tag {9.6-1}
$$

也可能是一个正方体，由下列条件决定

$$
\mid u _ {i} \mid \leqslant M, \quad i = 1, 2, \dots , r \tag {9.6-2}
$$

或者只包含几个孤立点和线。例如，若控制器是由数个双极继电器组成的，那么控制量的每个分量 $u_{i}$ 只可能取值 $\pm M$ ，此时点集 $U$ 只含有 $2^{r}$ 个孤立点。当 $r = 1$ 时，控制量只能取两个值：+M 或 -M，M 为某一给定的正数。

在这种特定条件下讨论的最优控制问题是由庞特里亚金(Понтрягин)及其学生们完成的 $^{[22]}$ 。这里仅限于叙述他们的基本方法和此方法的几何意义。最后我们将指出这种方法与前述古典变分法之间的联系。

如果控制函数 $\boldsymbol{u}(t)$ 在任何时刻均取值于 U，而且它的每一分量 $u_{i}(t), i=1,2,\cdots,r$ ，都是逐段连续的函数，在任何有限时间内只可能有有限个第一类断续点，则称这类 $\boldsymbol{u}(t)$ 为可准控制 $^{①}$ 。控制量的取值域 U 是 r 维空间的任意点集，它也可以是全空间，此时问题将与古典变分法的命题一致。以后我们将假定控制量的值域 U 已被给定。

与前节类似，对受控对象式(9.4-1)引进一个新的坐标 $x_{0}, x_{0}(t) = J(t)$ , 则

$$
\frac {d x _ {0}}{d t} = f _ {0} \left(x _ {1}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}\right)
$$

于是式(9.4-1)和(9.4-2)可联合成为一个包含 $n+1$ 个一阶方程式的方程组，将它写成向量形式

$$
\frac {d \bar {\boldsymbol {x}}}{d t} = \bar {\boldsymbol {f}} (\bar {\boldsymbol {x}}, \boldsymbol {u}), \bar {\boldsymbol {x}} (0) = (0, \boldsymbol {x} _ {0}) \tag {9.6-3}
$$

式中 $f=(f_{0},f_{1},\cdots,f_{n}),\bar{x}=(x_{0},x_{1},\cdots,x_{n})$ 。设受控对象的终点条件 $x_{1}=(x_{11},x_{21},\cdots,x_{n1})$ 已经给定。所谓最优控制是指在一切可准控制中寻求使受控对象自 $x_{0}$ 到达 $x_{1}$ 并使 $x_{0}$ 达极小值的控制函数。这一问题的几何意义如图 9.4-1 所示。这与前节内的古典问题的提法不同点在于，这里的控制函数必须在可准函数的范

围内选取，故 $\boldsymbol{u}(t)$ 的取值不能是任意的。

为了叙述最优控制所应满足的（必要）条件，与前节的讨论类似，引进一组 $n+1$ 维向量函数 $\bar{\psi}(t)=(\psi_{0}(t),\psi_{1}(t),\cdots,\psi_{n}(t))$ ,假定它们是下列方程组的解

$$
\frac {d \psi_ {i}}{d t} = - \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha}}{\partial x _ {i}} \psi_ {\alpha}, \quad i = 0, 1, 2, \dots , n \tag {9.6-4}
$$

类似地构造哈密顿函数 H

$$
H (\bar {\boldsymbol {x}}, \bar {\boldsymbol {\psi}}, \boldsymbol {u}) = (\bar {\boldsymbol {\psi}}, \bar {\boldsymbol {f}} (\bar {\boldsymbol {x}}, \boldsymbol {u})) = \sum_ {\alpha = 0} ^ {n} \psi_ {\alpha} f _ {\alpha} (\bar {\boldsymbol {x}}, \boldsymbol {u}) \tag {9.6-5}
$$

上式内用 $(\bar{x},\bar{y})$ 表示两个 $n + 1$ 维向量的数量积。于是，式(9.6-3)和(9.6-4)可以通过函数 $H$ 写成哈密顿方程组

$$
\frac {d x _ {i}}{d t} = \frac {\partial H}{\partial \psi_ {i}}, \quad i = 0, 1, 2, \dots , n \tag {9.6-6}
$$

$$
\frac {d \psi_ {i}}{d t} = - \frac {\partial H}{\partial x _ {i}}, \quad i = 0, 1, 2, \dots , n \tag {9.6-7}
$$

如果 $\boldsymbol{u}(t)$ 已经给定，则 $\boldsymbol{x}(t)$ 可从式(9.6-3)中求出，于是式(9.6-4)的诸系数就成为已知的时间函数了， $\bar{\psi}(t)$ 将是这个线性方程组的解。

文献[22]证明了下列事实：设 $\dot{\boldsymbol{u}}(t)$ 和 $\dot{\bar{x}}$ 分别是式(9.6-3)的最优控制和最优运动, $t_{1}$ 是最优运动自 $\bar{x}_{0}$ 点到达 $\bar{x}_{1}$ 点的时间, 则 $\dot{\boldsymbol{u}}(t)$ 必满足下列条件: 即存在式(9.6-4)的非零解 $\dot{\bar{\psi}}(t)$ , 使下列两个条件成立:

(1) 哈密顿函数 H 沿最优运动轨迹 $\overline{\boldsymbol{x}}(t)$ 在任何时刻对 u 取极大值, 即

$$
H (\stackrel {\circ} {x} (t), \stackrel {\circ} {\psi} (t), \stackrel {\circ} {u} (t)) = \max _ {u \in U} (\stackrel {\circ} {\psi} (t), \bar {f} (\stackrel {\circ} {x}, u)), \quad 0 \leqslant t \leqslant t _ {1} \tag {9.6-8}
$$

(2) 沿最优运动的轨线上 $\psi_{0}(t)=\mathrm{const}\leqslant0$ , 且

$$
H \left(\stackrel {\circ} {x} (t), \stackrel {\circ} {\psi} (t), \stackrel {\circ} {u} (t)\right) \equiv 0, \quad 0 \leqslant t \leqslant t _ {1} \tag {9.6-9}
$$

这就是著名的关于最优控制的极大值原理。

表面上看来，上述两个条件与前节的古典问题的必要条件式(9.4-28)颇为类似，差别仅在于式(9.4-24)是“极值条件”，式(9.6-8)则是“条件最大值”。换言之，式(9.4-24)中 $H$ 在一切 $\delta u$ 中取极值。而式(9.6-8)中 $H$ 在 $u \in U$ 中取最大值。这一点绝不仅是字面上的差别，而反映了一种深刻的质的变化。

关于极大值原理的详细证明读者可参阅专著 $^{[22]}$ 。这里我们仅指出它与前节的讨论中有本质性差别的地方。前节内我们证明极值条件式(9.4-24)时，利用了一个基本事实，即由于 $\delta u$ 的各种变化所引起的最优轨线构成一个线性子空间 K。后者的线性是由于最优控制的变化 $\delta u$ 所引起的最优轨线的末端变化 $\bar{\delta x}(t_{1})$ 对 $\delta u$ 是线性关系。由于对 $\delta u$ 无任何限制，故 $\bar{\delta x}(t_{1})$ 构成一个线性集合。而在 $\delta u$ 受限制的情况 下，如果最优控制函数 $\dot{\boldsymbol{u}}(t)$ 的取值完全位于 U 的内部，则前节内所述之证明方法在这里依然可以采用，此时条件式 (9.6-8) 和 (9.4-24) 将完全重合。但是，当最优控制 $\dot{\boldsymbol{u}}(t)$ 的取值位于 U 的边界时，前述的证明方法就完全无效了，因为此时 $\delta\boldsymbol{u}$ 不能任意取值，否则 $\dot{\boldsymbol{u}}(t)+\delta\boldsymbol{u}$ 可能超出 U 的限制范围，变成为不可准许的控制函数了。文献 [22] 的作者们利用一种独特型的变分方法构造了一种关于 $\dot{\boldsymbol{u}}(t)$ 的变分集合，并证明了由于这种特殊的变分所造成的最优轨线的末端偏离 $\delta\bar{x}(t_{1})$ 的全体构成的集合是一个凸锥体 K，而不是一个线性子空间。以 $\bar{x}_{1}$ 为始点的向量 $z=(-1,0,\cdots,0)$ 必然处于此凸锥体的外部。这样，就可以建立一个超平面，使向量 z 与凸锥体 K 位于此超平面的两侧， $\bar{\psi}_{1}$ 是此超平面的外法向量，即它与 K 不在超平面的同侧。除此而外的其他证明过程与前节所述的基本思想是相同的。

以后我们还将利用极大值原理去解决一类具体问题。

#### 9.7 末端不固定时的最优控制

前面几节讨论的问题都是关于受控对象自某一给定初始状态到达另外一个固定的端点状态的最优控制所应满足的必要条件。我们曾经指出，无论控制量 $\boldsymbol{u}(t)$ 的取值是否受到限制，在最优控制确实存在的情况下，只要方程(9.4-28)和(9.6-8)给出足够的方程式个数，就可以求出最优运动的一切未知变量和未知常量。

在实际技术问题中常有另外一种情况，就是运动的端点并不完全固定，而仅需满足某些较为“不严”的限制条件。例如，对受控对象的终点状态只有局部限制：某几个坐标分量的状态为给定，而另一种分坐标则是任意的。用多维空间的几何术语来讲，终点状态不是相空间内的某一个固定点，而是一个维数小于 $n$ 的超曲面，终点状态，即受控运动的轨线端点，应该位于此超曲面上。此时前面得到的最优控制所应满足的条件就不能充分决定最优控制函数了，因为这超曲面上的点有无穷多个，究竟这些点中那一个点从损耗最小的意义上来看是系统理想的终端状态呢？甚之，系统的初始点状态也可能是不固定的，而仅要求位于某一超曲面上。总之，这类问题可以叙述如下。在 $n$ 维相空间内给定两个维数不大于 $n - 1$ 维的超曲面 $S_{1}$ 和 $S_{2}$ ，它们互不相交。要求找出 $S_{1}$ 和 $S_{2}$ 上的某些点 $\pmb{x_0} \in S_1$ 和 $\pmb{x_1} \in S_2$ ，使自 $\pmb{x_0}$ 至 $\pmb{x_1}$ 点的最优控制就是自超曲面 $S_{1}$ 至超曲面 $S_{2}$ 的最优控制。这里实际上包含了三个问题：求出 $S_{1}$ 上的点 $\pmb{x_0}$ ，使自该点到达 $S_{2}$ 的最优控制比自 $S_{1}$ 上任何其他点到达 $S_{2}$ 的最优控制还要好。也就是在很多最优控制中求更优者；其次要求出自此“理想点”到达 $S_{2}$ 的最优控制函数；最后还须求出 $S_{2}$ 上的理想端点的位置。

设受控对象的运动方程依然是式(9.4-1)

$$
\frac {d x _ {i}}{d t} = f _ {i} \left(x _ {1}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}\right), \quad i = 1, 2, \dots , n
$$

受控运动的质量指标是式(9.4-2)

$$
x _ {0} = J = \int_ {0} ^ {t _ {1}} f _ {0} (x _ {1}, x _ {2}, \dots , x _ {n}; u _ {1}, \dots , u _ {r}) d t
$$

系统的初始状态位于初始超曲面 $S_{1}$ 上, 后者由方程式

$$
h (x _ {1}, \dots , x _ {n}) = 0 \tag {9.7-1}
$$

所确定。系统的终点状态应在超曲面 $S_{2}$ 上，它由方程式

$$
q (x _ {1}, \dots , x _ {n}) = 0 \tag {9.7-2}
$$

决定。欲求自 $S_{1}$ 至 $S_{2}$ 的最优控制最直观的方法是先任意选择 $\pmb{x_0} \in S_1$ 和 $\pmb{x_1} \in S_2$ ，求出自 $\pmb{x_0}$ 至 $\pmb{x_1}$ 的最优控制，然后再找出最好的始点和终点。这样便得到一个三重最优问题，可写成

$$
x _ {0} = J = \min _ {\boldsymbol {x} _ {1} \in S _ {2}} \min _ {\boldsymbol {x} _ {0} \in S _ {1}} \min _ {\boldsymbol {u} \in U} \int_ {0} ^ {t _ {1}} f (\boldsymbol {x} (t), \boldsymbol {u} (t)) d t
$$

显然，这种方法在实际上几乎是毫无用处的。为了求出最好的 $\dot{\pmb{x}}_0$ 和 $\dot{\pmb{x}}_1$ ，需要找出一些附加条件，用来寻找最理想的始点和端点。

在未开始讨论这些附加条件以前，先指出下列明显事实：如果理想的端点 $\dot{\pmb{x}}_0$ 和 $\dot{\pmb{x}}_1$ 已经找到，那么最优控制问题就变为前面已经详细讨论过的自固定点至固定点的最优控制问题。在受控量不受限制时最优控制函数必须满足条件式(9.4-28)，而在控制量受限制时则应满足条件式(9.6-8)。因此，前节内得到的结果依然适用于本节初提出的问题。

为了讨论简单，我们假定决定超曲面 $S_{1}$ 和 $S_{2}$ 的方程式(9.7-1)和(9.7-2)中的函数 $h(\boldsymbol{x}), q(\boldsymbol{x})$ 为连续可微函数，即它们所确定的超曲面是光滑的。在其上的每一点都有一次偏导数存在，且梯度向量

$$
\operatorname{grad} h (\boldsymbol {x}) = \left[ \frac {\partial h}{\partial x _ {1}}, \frac {\partial h}{\partial x _ {2}}, \dots , \frac {\partial h}{\partial x _ {n}} \right] \neq \mathbf {0}
$$

$$
\operatorname{grad} q (\boldsymbol {x}) = \left[ \frac {\partial q}{\partial x _ {1}}, \frac {\partial q}{\partial x _ {2}}, \dots , \frac {\partial q}{\partial x _ {n}} \right] \neq \mathbf {0}
$$

换言之，梯度向量处处不为零向量，即曲面上没有奇点。此外还假定超曲面 $S_{1}$ 和 $S_{2}$ 都是 n-1 维的。关于维数的假定并不是完全必要的，只是为了讨论方便而已。

先讨论控制量不受限制的情况。现假定 $S_{1}$ 上的 $\dot{\pmb{x}}_0$ 已经找到，来研究 $S_{2}$ 上的理想端点 $\dot{\pmb{x}}_1$ 应该满足什么条件。从第 9.5 节中我们已经知道，如果 $\dot{\pmb{u}}(t)$ 是自 $\dot{\pmb{x}}_0$ 点到达 $\dot{\pmb{x}}_1$ 点的最优控制，在最优运动的中间任一时刻 $\tau ,0\leqslant \tau < t_1$ ，对最优控制函数 $\dot{\pmb{u}} (t)$ 做一系列的微小变化 $\{\delta \pmb {u}\}$ ，在最优轨线终点 $\dot{\pmb{x}}_1(t_1)$ 所产生的偏离 $\{\delta \pmb {x}(t_1)\}$ 的全体构成一个线性子空间 $K$ ，它的维数不超过 $r$ 。在 $n + 1$ 维空间内通过 $\dot{\pmb{x}}_1$ 点所做的平行于 $x_0$ 轴的直线 $\mathcal{L}$ 图 9.4-1)绝不会包含在子空间 $K$ 的内部。 $n$ 维相空间内超曲面 $S_{2}$ 在 $n + 1$ 维相空间内变成一个柱面 $S_2^{\prime}$ 直线 $\mathcal{L}$ 是此 柱面的一条基线，从几何结构上可以推知，若过 $\vec{x}_{1}$ 点做此柱面的切平面 P,它的方程式应该是

$$
\sum_ {i = 0} ^ {n} \frac {\partial q}{\partial x _ {i}} (\stackrel {\circ} {x} _ {i 1} - x _ {i}) = (\operatorname{grad} q (\stackrel {\circ} {\bar {x}}), \stackrel {\circ} {\bar {x}} - \bar {\bar {x}}) = 0 \tag {9.7-3}
$$

式中

$$
\operatorname{grad} q (\stackrel {\circ} {x}) = \left[ 0, \frac {\partial q}{\partial x _ {1}}, \dots , \frac {\partial q}{\partial x _ {n}} \right] \Bigg | _ {x = \stackrel {\circ} {x} _ {1}}
$$

是切平面 $P$ 的法向量。由于 $\vec{x}_1$ 是自 $S_1'$ 到达 $S_2'$ 的最优端点，故切平面以 $\vec{x}_1$ 为中心的邻域不可能包含于子空间 $K$ 的内部，否则将存在一种式(9.4-6)形的控制，使轨线端点的第一个坐标小于 $\dot{x}_{01}$ ，这与最优的假定相矛盾。于是，过 $P$ 上垂直于 $x_0$ 轴的直线可做一个超平面 $P'$ ，使 $\mathcal{L}$ 的下半部与 $K$ 完全隔开。因而 $P'$ 的法向量必然是 $\{\psi, \mathrm{grad}q(\bar{x})\}$ 。重复前面的讨论，可以得到如下结论：决定最优控制的向量函数 $\vec{\psi}(t)$ 在轨线末端应与 $P'$ 垂直。换言之， $\vec{\psi}(t)$ 在末端的方向应有下列形式

$$
\dot {\bar {\psi}} (t _ {1}) = \left[ \psi_ {0}, \frac {\partial q}{\partial x _ {1}}, \dots , \frac {\partial q}{\partial x _ {n}} \right] \Bigg | _ {x = \hat {x} _ {1}} \tag {9.7-4}
$$

此式就是古典变分法中的横截条件。

由于受控对象的运动方程式(9.4-1)之右端不明显包含时间变量 t，用逆运动的方法，对最优轨线的始点也可以得到同样的结果，即在 t=0 时， $\hat{\psi}(0)$ 应具有下面形式

$$
\dot {\bar {\psi}} (0) = \left[ \psi_ {0}, \frac {\partial h}{\partial x _ {1}}, \dots , \frac {\partial h}{\partial x _ {n}} \right] \Bigg | _ {x = \hat {x} _ {0}} \tag {9.7-5}
$$

这样一来，决定最优控制的标准方程组(9.4-28)将变成下列新的形式

$$
\frac {d x _ {i}}{d t} = f _ {i} (\mathring {\boldsymbol {x}} (t), \mathring {\boldsymbol {u}} (t)), \quad i = 0, 1, 2, \dots , n
$$

$$
\stackrel {\circ} {\boldsymbol {x}} (0) \in S _ {1}, \quad \stackrel {\circ} {\boldsymbol {x}} _ {1} \in S _ {2}
$$

$$
\frac {d \psi_ {i}}{d t} = - \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha}}{\partial x _ {i}} \psi_ {\alpha}, \quad i = 0, 1, 2, \dots , n
$$

$$
\dot {\bar {\psi}} (0) = \left[ \psi_ {0}, \frac {\partial h}{\partial x _ {1}}, \dots , \frac {\partial h}{\partial x _ {n}} \right] \Bigg | _ {x = \dot {x} _ {0}}
$$

$$
\stackrel {\circ} {\boldsymbol {\psi}} (t _ {1}) = \left[ \psi_ {0}, \frac {\partial q}{\partial x _ {1}}, \dots , \frac {\partial q}{\partial x _ {n}} \right] \Bigg | _ {x = \stackrel {\circ} {x} _ {1}}
$$

$$
H (\stackrel {\circ} {x} (t), \stackrel {\circ} {\psi} (t), \dot {u} (t)) = \operatorname{ext} (\stackrel {\circ} {\psi} (t), \bar {f} (\stackrel {\circ} {x}, u)) \equiv 0
$$

$$
\frac {\partial H}{\partial u _ {i}} = 0, \quad i = 1, 2, \dots , r \tag {9.7-6}
$$

读者不难看出，标准方程组(9.7-6)提供了足够的条件解 $2n+2$ 个一阶常微分方程式。于是最优控制函数及最优轨线的两个端点，如果它们存在的话，就可以从方程组(9.7-6)中求出。

上面讨论的依然是受控量不受限制的情况. 如果 u 的取值受某种限制, 则式 $(9.7-6)$ 中的最后一个条件将改为

$$
H (\stackrel {\circ} {x}, \stackrel {\circ} {\psi} (t), \stackrel {\circ} {u} (t)) = \max _ {u \in U} (\stackrel {\circ} {\psi} (t), f (\stackrel {\circ} {x} (t), u)) \equiv 0 \tag {9.7-7}
$$

这与端点完全固定的情况是一样的。对后一种情况更严格的数学证明这里不再详述，读者可参看文献[22]。此外，前面假定的 $S_{1}$ 和 $S_{2}$ 均为 $n - 1$ 维超曲面也不是必要的。当它们的维数小于 $n - 1$ 时，限制条件式(9.7-1)和(9.7-2)中，将包含数个方程式。例如，假定 $S_{2}$ 由 $m$ 个等式所确定

$$
q _ {i} (\boldsymbol {x}) = 0, \quad i = 1, 2, \dots , m \tag {9.7-8}
$$

同时满足这 m 个方程式的一切点构成一个 n-m 维超曲面 $S_{2}$ ，此时下列向量

$$
\operatorname{grad} q _ {1} (\boldsymbol {x}), \operatorname{grad} q _ {2} (\boldsymbol {x}), \dots , \operatorname{grad} q _ {m} (\boldsymbol {x}) \tag {9.7-9}
$$

对于 $S_{2}$ 上的一切点，都是线性无关的，也就是说下列 $n \times m$ 阶方阵

$$
\left[ \begin{array}{c c c c} \frac {\partial q _ {1} (\boldsymbol {x})}{\partial x _ {1}} & \frac {\partial q _ {2} (\boldsymbol {x})}{\partial x _ {1}} & \dots & \frac {\partial q _ {m} (\boldsymbol {x})}{\partial x _ {1}} \\ \frac {\partial q _ {1} (\boldsymbol {x})}{\partial x _ {2}} & \frac {\partial q _ {2} (\boldsymbol {x})}{\partial x _ {2}} & \dots & \frac {\partial q _ {m} (\boldsymbol {x})}{\partial x _ {2}} \\ \vdots & \vdots & & \vdots \\ \frac {\partial q _ {1} (\boldsymbol {x})}{\partial x _ {n}} & \frac {\partial q _ {2} (\boldsymbol {x})}{\partial x _ {n}} & \dots & \frac {\partial q _ {m} (\boldsymbol {x})}{\partial x _ {n}} \end{array} \right] \tag {9.7-10}
$$

对一切 $x \in S_{2}$ 均有最大秩 m。

式(9.7-8)中的每一个等式决定一个 $n - 1$ 维超曲面，它的每一点上的切平面 $P_{i}$ 的法向量是 $\mathrm{grad}q_i(x)$ 。在任意点 $x\in S_2$ 上所作的 $m$ 个切平面

$$
(\operatorname{grad} q _ {i} (\boldsymbol {x}), \boldsymbol {x} - \boldsymbol {y}) = \sum_ {\alpha = 1} ^ {n} \frac {\partial q _ {i}}{\partial x _ {\alpha}} (x _ {\alpha} - y _ {\alpha}) = 0, \quad i = 1, 2, \dots , m \tag {9.7-11}
$$

的交，称为 $S_{2}$ 在 x 点的切平面 P, 它的维数也是 n-m。不难理解, P 的法向量可由式(9.7-9)诸向量的线性组合表示, 即

$$
\boldsymbol {n} (\boldsymbol {x}) = \sum_ {\alpha = 1} ^ {m} \mu_ {\alpha} \operatorname{grad} q _ {\alpha} (\boldsymbol {x}) \tag {9.7-12}
$$

在这种情况下，式(9.7-6)中确定 $\bar{\psi}$ 的边界条件的关系式将改为

$$
\bar {\boldsymbol {\psi}} (0) = \left(\psi_ {0}, n _ {1} (\boldsymbol {x}), \dots , n _ {n} (\boldsymbol {x})\right) | _ {\boldsymbol {x} = \hat {\boldsymbol {x}} _ {0}}
$$

$$
\stackrel {\circ} {\boldsymbol {\psi}} \left(t _ {1}\right) = \left(\psi_ {0}, n _ {1} (\boldsymbol {x}), \dots , n _ {n} (\boldsymbol {x})\right) | _ {\boldsymbol {x} = \hat {\boldsymbol {x}} _ {1}} \tag {9.7-13}
$$

我们看到，在式(9.7-12)中又引进了 m 个常数 $\mu_{1}, \mu_{2}, \cdots, \mu_{m}$ , 它们是未知的。但是 比前面的讨论中又多了 m-1 个约束方程式 $q_{i}(\boldsymbol{x})=0, i=2,\cdots,m$ 。这样总的未知数和已知条件依然相互平衡，故决定最优控制函数与最优端点的标准方程组式 (9.7-6) 在新的条件下依然是完备的。如果这种问题有解的话，那么式 (9.7-6) 就提供了求解的必要条件。

#### 9.8 最优控制函数综合举例

作为前节所述理论的应用，现研究线性系统内的最优控制函数的综合问题，设受控对象的运动方程是线性方程组

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u} \tag {9.8-1}
$$

和过去的符号一样，A 是 $n \times n$ 阶常量矩阵，B 是 $n \times r$ 阶常量矩阵， $\boldsymbol{u} = (u_{1}, u_{2}, \cdots, u_{r})$ 是 r 个控制量。假定控制量的取值是受限制的，例如

$$
\mid u _ {i} \mid \leqslant 1, \quad i = 1, 2, \dots , r \tag {9.8-2}
$$

令 $\Omega$ 表示系统要求的终点状态区域。即无论受控系统的初始条件如何，经一段时间后，受控对象式(9.8-1)应该以 $\Omega$ 内的任意点作为终点状态。我们假定 $\Omega$ 是一个凸面体，或者是一个凸性区域，它由 m 个不等式

$$
g _ {i} (\boldsymbol {x}) \leqslant 0, \quad i = 1, 2, \dots , m \tag {9.8-3}
$$

所确定，例如，它可能是以原点为中心以 $\rho$ 为半径的小球体，此时

$$
g (\boldsymbol {x}) = \sum_ {i = 1} ^ {n} x _ {i} ^ {2} \leqslant \rho^ {2}
$$

$\rho$ 为某一给定的常数。

过渡过程的质量指标是一个二次型的积分式

$$
J (\boldsymbol {u}) = \int_ {0} ^ {t _ {1}} \left[ (Q \boldsymbol {x}, \boldsymbol {x}) + (P \boldsymbol {u}, \boldsymbol {u}) \right] d t \tag {9.8-4}
$$

上式内 $\Omega$ 为非负定方阵, 即对任何 x 总有

$$
(Q \boldsymbol {x}, \boldsymbol {x}) \geqslant 0
$$

为了讨论简单，假设 P 是一个非负的对角矩阵，即

$$
p _ {i j} = \left\{ \begin{array}{l l} p _ {i i} \geqslant 0, & \text {若} i = j \\ 0, & \text {若} i \neq j \end{array} \right.
$$

这样，式(9.8-4)可以写成

$$
J (\boldsymbol {u}) = \int_ {0} ^ {t _ {1}} \left[ \sum_ {i, j = 1} ^ {n} q _ {i j} x _ {i} x _ {j} + \sum_ {i = 1} ^ {r} p _ {i i} (u _ {i}) ^ {2} \right] d t \tag {9.8-5}
$$

所谓综合问题就是控制装置的设计问题，要求求出一组 n 元函数 $u_{i}(x_{1}, x_{2}, \cdots, x_{n})$ , $i=1,2,\cdots,r$ , 若将其代入式(9.8-1)后所得到的自治系统

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u} (\boldsymbol {x}) \tag {9.8-6}
$$

对任何初始条件 $x_{0}$ ，均能自动地将受控对象引至 $\Omega$ 上的某一点，且使沿此轨线所算出的 J 值取极值。这样求出的函数 $u_{i}(x_{1},\cdots,x_{n}), i=1,2,\cdots,r$ ，正是待求的控制装置必须实现的控制规律。

现用第 9.6 节内所述的原理进行控制装置的设计。首先引进新坐标 $x_{0}=J$ ，它应满足方程式

$$
\frac {d x _ {0}}{d t} = (\Omega \boldsymbol {x}, \boldsymbol {x}) + (P \boldsymbol {u}, \boldsymbol {u}) = \sum_ {i, j = 1} ^ {n} q _ {i j} x _ {i} x _ {j} + \sum_ {i = 1} ^ {r} p _ {i i} u _ {i} ^ {2} \tag {9.8-7}
$$

此式与式(9.8-1)联合后得到一个由 $n + 1$ 个方程式构成的方程组，不难直接检查，它们的共轭方程组

$$
\frac {d \psi_ {0}}{d t} = 0
$$

$$
\frac {d \boldsymbol {\psi}}{d t} = - A ^ {\tau} \boldsymbol {\psi} - 2 \psi_ {0} Q \boldsymbol {x} \tag {9.8-8}
$$

构成哈密顿函数

$$
H (\boldsymbol {x}, \boldsymbol {\psi}, u) = \psi_ {0} [ (Q \boldsymbol {x}, \boldsymbol {x}) + (P \boldsymbol {u}, \boldsymbol {u}) ] + (\boldsymbol {\psi}, A \boldsymbol {x} + B \boldsymbol {u}) \tag {9.8-9}
$$

根据第 9.6 节内的叙述可知, 如果 $\mathbf{\dot{u}}(t)$ 是最优控制, 它应使 H 取极大值

$$
H (\mathring {\boldsymbol {x}} (t), \mathring {\boldsymbol {\psi}} (t), \mathring {\boldsymbol {u}} (t)) = \max _ {\boldsymbol {u} \in U} [ \psi_ {0} (P \boldsymbol {u}, \boldsymbol {u}) + (\mathring {\boldsymbol {\psi}}, B \boldsymbol {u}) + v (t) ] \tag {9.8-10}
$$

上式内 $\dot{\boldsymbol{x}}(t),\dot{\boldsymbol{\psi}}(t)$ 分别为最优运动轨线和其所对应的式(9.8-8)的某一特解。U 为由式(9.8-2)所确定的一个 r 维正方体； $v(t)=\psi(Q\dot{\boldsymbol{x}}(t),\dot{\boldsymbol{x}}(t))+(\dot{\boldsymbol{\psi}}(t),A\dot{\boldsymbol{x}}(t))$ 是一个不依赖于 u 的 t 的函数。条件式(9.8-10)等价于下列条件

$$
\varphi (t) = \psi_ {0} (P \mathring {\boldsymbol {u}} (t), \mathring {\boldsymbol {u}} (t)) + (\mathring {\boldsymbol {\psi}} (t), B \mathring {\boldsymbol {u}} (t)) = \max _ {\boldsymbol {u} \in U} [ \psi_ {0} (P \boldsymbol {u}, \boldsymbol {u}) + (\mathring {\boldsymbol {\psi}}, B \boldsymbol {u}) ]
$$

假定 $p_{ii} \neq 0$ ，若 $i = 1, 2, \cdots, l$ ；当 i > l 时 $p_{ii} = 0$ 。此时将上式右端配方，经过整理后，可以得到

$$
\varphi (t) = \max _ {\boldsymbol {u} \in U} \left[ \sum_ {i = 1} ^ {l} \left(u _ {i} + \frac {\left(\boldsymbol {b} _ {i} \stackrel {\circ} {\psi} (t)\right)}{2 \psi_ {0} p _ {i i}}\right) ^ {2} + \sum_ {\alpha = l + 1} ^ {r} (\dot {\boldsymbol {\psi}} (t), \boldsymbol {b} _ {\alpha}) u _ {\alpha} + w (t) \right]
$$

这里 $w(t)$ 为不含 $\pmb{u}$ 的时间 $t$ 的函数。由上式不难推知，当 $p_{ii} \neq 0$ 时，考虑到 $\psi_0 < 0$ ，唯一的最优控制函数 $\dot{u}_i(t)$ 应具有下列形式

$$
\dot {\pmb {u}} _ {i} (t) = \left\{ \begin{array}{l l} 1, & \text {若} \frac {(\pmb {b} _ {i} , \dot {\pmb {\psi}} (t))}{2 \psi_ {0} p _ {i i}} \leqslant - 1 \\ - 1, & \text {若} \frac {(\pmb {b} _ {i} , \dot {\pmb {\psi}} (t))}{2 \psi_ {0} p _ {i i}} \geqslant 1 \\ - \frac {(\pmb {b} _ {i} , \dot {\pmb {\psi}} (t))}{2 \psi_ {0} p _ {i i}}, & \text {若} - 1 \leqslant \frac {(\pmb {b} _ {i} , \dot {\pmb {\psi}} (t))}{2 \psi_ {0} p _ {i i}} \leqslant 1 \end{array} \right.
$$

$$
i = 1, 2, \dots , l \tag {9.8-11}
$$

对应于 $p_{\alpha \alpha} = 0$ 的那些控制量应为

$$
\dot {\boldsymbol {u}} _ {\alpha} (t) = \operatorname{sign} (\boldsymbol {b} _ {i}, \dot {\boldsymbol {\psi}} (t)), \quad \alpha = l + 1, \dots , r \tag {9.8-12}
$$

如果上式右端符号 sign 后的函数只在一些孤立点上才为零, 那么 $\dot{u}_{\alpha}$ 将唯一地为式(9.8-12)所确定, 否则 $u_{\alpha}$ 的最优控制 $\dot{u}_{\alpha}(t)$ 将不能用这个办法求出。

我们看到，如果 $\dot{\psi}(t)$ 和 $\psi_0$ 都为已知函数和已知数时，最优控制函数 $\mathbf{u}(t)$ 将有希望按式(9.8-11)和(9.8-12)所唯一地被求出。这样，求最优控制函数的问题就转化为求相应的 $\psi_0$ 和 $\dot{\psi}_0(t)$ 。再回来观察式(9.8-8)。为了求出这些函数，必须求出式(9.8-8)的初始条件 $\dot{\psi}(0)$ ，而这是一件十分困难的事。为此，我们必须利用前节内关于不定端点的横截条件。利用这个条件可以写出最优轨线在到达 $\Omega$ 时的终端条件。设 $t_1$ 是受控对象自 $x_0$ 点到达 $\Omega$ 所需的时间；显然，我们有理由断定最优轨线在 $t = t_1$ 时刻所到达的点 $z = \dot{x}(t_1)$ 必位于 $\Omega$ 的边界，而且在 $z$ 点上有

$$
\dot {\boldsymbol {\psi}} (t _ {1}) = - \operatorname{grad} g (\boldsymbol {x}) | _ {x = z} \tag {9.8-13}
$$

而未知数 $\psi_{0}$ 则应满足条件

$$
\max _ {\boldsymbol {u} \in U} \left[ \psi_ {0} (Q \boldsymbol {z}, \boldsymbol {z}) + \psi_ {0} (\boldsymbol {P u}, \boldsymbol {u}) + (- \operatorname{grad} g (\boldsymbol {x}) | _ {\boldsymbol {x} = z}, A \boldsymbol {z} + B \boldsymbol {u}) \right] = 0 \tag {9.8-14}
$$

这样，当终点 $z$ 为已知时 $\dot{\psi}(t)$ 和 $\psi$ 便可以从式(9.8-13)和(9.8-14)求出。这是问题的第二次转化，把求最优控制函数 $\dot{u}(t)$ 又转化为求终点 $z$ 。因为终点 $z$ 也是未知量，表面看来这种转化依然是徒劳的。其实不然，经两次转化后，我们已经接近于最后解决本节初提出的综合问题了。

为此，我们研究原始方程(9.8-1)的逆转运动方程，因为它的右端不含 t,这种方法极易实现，用-t 代替 t 后，方程组(9.8-1)和(9.8-8)可写成

$$
\frac {d \boldsymbol {x}}{d t} = - A \boldsymbol {x} - B \boldsymbol {u}, \boldsymbol {x} (0) = \boldsymbol {z}
$$

$$
\frac {d \psi}{d t} = A ^ {\tau} \psi + 2 \psi_ {0} Q x, \quad \psi (0) = \operatorname{grad} g (\boldsymbol {x}) | _ {x = z}, \quad \psi_ {0} <   0 \tag {9.8-15}
$$

因为我们要解决的是综合问题, 即求出一切到达 $\Omega$ 的最优控制函数, 所以 $\Omega$ 的边界上的任一个点 z 都可能成为某一最优轨线的终点, 或者说任一个 z 都可能是式 (9.8-15) 的始点, 于是 $\Omega$ 边界上的每一个始点 z 都决定一条最优轨线。这样, 当 z 遍历 $\Omega$ 的表面以后, 就可求出一切最优轨线了。任取 $\Omega$ 边界上的一点 z, 即可按式 (9.8-15) 求出 $\psi(0)$ , 再按式 (9.8-14) 求出 $\psi_{0}$ 来。由于 $\psi_{0}$ 沿最优轨线是常量, 故 $\psi_{0}$ 只依赖于 z 点的位置, 再由于式 (9.8-15) 是关于 x 和 $\psi$ 的线性方程组, 有可能在它的通解中消掉 $u(t)$ 或者 $\psi(t)$ , 使 $\psi(t)$ 表达为 $x(t)$ 的函数。

完成上述计算后，x 的相空间对每一个 $u_{i}$ 将分为三类控制区域。第一类区域 $\dot{u}_{i}(x)=1$ ; 第二类区域 $\dot{u}_{i}=-1$ ; 第三类区域

$$
\stackrel {\circ} {u} _ {i} (t) = - \frac {\left(\boldsymbol {b} _ {i} , \stackrel {\circ} {\psi} (t)\right)}{2 \psi_ {0} p _ {i i}} = - \frac {\left(\boldsymbol {b} _ {i} , \stackrel {\circ} {\psi} (\boldsymbol {x})\right)}{2 \psi_ {0} p _ {i i}}
$$

这些区域找到后, 就得到函数 $\mathbf{\dot{u}}(\mathbf{x})$ 。这就是待求的最优控制函数。应指出的是, 用纯分析方法去设计控制装置, 一般看来, 是十分复杂的事, 但是, 如果借助于高速度数字计算机或模拟计算装置这种设计程序就变得轻而易举了。

还有一种情况的最优设计问题有希望直接求出控制器即反馈信号的具体形式。设给定的受控对象的初始状态为 $x_{0}$ ; 控制作用从 t=0 开始, 于给定的时间 $t_{1}$ 结束; 对控制作用 u 没有约束。受控对象的运动方程是式(9.8-1), 而指标泛函改写成更方便的形式

$$
J (\boldsymbol {u}) = \frac {1}{2} \int_ {0} ^ {t _ {1}} [ (Q \boldsymbol {x}, \boldsymbol {x}) + (P \boldsymbol {u}, \boldsymbol {u}) ] d t \tag {9.8-16}
$$

式中 Q 和 P 均假定为正定方阵。今要求设计最优线性反馈控制，使系统在 t=0 时刻开始，在 $[0, t_{1}]$ 的时间间隔内，从任意点 $x_{0}$ 出发向任何方向运动（即端点不固定）指标泛函式(9.8-16)取极小值。

重复本节前面的讨论可知，最优控制应从下列方程组中求出[见式(9.8-8)]

$$
\frac {d \boldsymbol {x}}{d t} = A \boldsymbol {x} + B \boldsymbol {u}, \quad \boldsymbol {x} (0) = \boldsymbol {x} _ {0}
$$

$$
\frac {d \boldsymbol {\psi}}{d t} = - A ^ {\tau} \boldsymbol {\psi} - \phi_ {0} Q \boldsymbol {x}
$$

$$
H (\mathbf {\dot {x}} (t), \mathbf {\dot {\psi}} (t), \mathbf {\dot {u}} (t)) = \max _ {u} \left[ \frac {\psi_ {0} (Q \mathbf {\dot {x}} , \mathbf {\dot {x}}) + \psi_ {0} (P u , u) + (\mathbf {\dot {\psi}} , A \mathbf {\dot {x}} + B u)}{2} \right] \tag {9.8-17}
$$

由于终端状态可以是任意的，根据前节内极大值原理的证明，可推知 $\psi_{0}$ 和 $\psi$ 的终端条件一定是

$$
\psi_ {0} \equiv - 1, \psi (t _ {1}) = 0 \tag {9.8-18}
$$

前面已经讨论过，如果 Q 和 P 是正定矩阵，哈密顿函数 H 是 u 的非蜕化二次型，因而 H 的极大值一定是极值，即对 u 的每一分量 $u_{\alpha}$ 均应有 $\frac{\partial H}{\partial u_{\alpha}} = 0$ 在整个最优轨迹上成立。不难算出，由这个极值条件可得到向量等式

$$
\frac {\partial H}{\partial \boldsymbol {u}} = - P \boldsymbol {u} + B ^ {\tau} \boldsymbol {\psi} = 0
$$

或者

$$
\mathbf {\dot {u}} (t) = P ^ {- 1} B ^ {\tau} \boldsymbol {\psi} (t) \tag {9.8-19}
$$

我们希望把最优反馈控制表示成下列线性形式

$$
\mathbf {\dot {u}} (t) = - K (t) \mathbf {x} (t) \tag {9.8-20}
$$

式中 $K(t)$ 是某一随时间 t 变化的 $r \times n$ 长方矩阵。为此只需把 $\boldsymbol{\psi}(t)$ 表示成 $\mathring{\boldsymbol{x}}(t)$ 的线性函数，然后依式 (9.8-19) 即可得到线性反馈式 (9.8-20)。

令

$$
\boldsymbol {\psi} (t) = - R (t) \boldsymbol {x} (t) \tag {9.8-21}
$$

并和式(9.8-19)一起代入式(9.8-17)，注意到 $\psi = -1$ ，可立即得到下列恒等式

$$
\begin{array}{l} \dot {\boldsymbol {\psi}} (t) = - \dot {R} (t) \boldsymbol {x} (t) - R (t) \dot {\boldsymbol {x}} \\ = - \dot {R} (t) \boldsymbol {x} (t) - R (t) (A \boldsymbol {x} + B \boldsymbol {u}) \\ = A ^ {\tau} R (t) \boldsymbol {x} (t) + Q \boldsymbol {x} (t) \\ \end{array}
$$

注意到式 $(9.8-19)$ ，则上式等价于一个矩阵微分方程

$$
- R (t) = Q + A ^ {\tau} R - R B P ^ {- 1} B ^ {\tau} R + R A \tag {9.8-22}
$$

上两式内矩阵上方的点表示对 t 的导数。式(9.8-22)是一个矩阵微分方程，常称为黎卡提(Riccati)方程，可以证明它的解对任意初始条件是唯一存在的。剩下的只是确定 $R(t)$ 的边界条件。由式(9.8-18)知，在 $t=t_{1}$ 时 $\psi(t_{1})=0$ ，因而 $R(t_{1})=0$ （零矩阵）。由于式(9.8-22)与系统的初始条件无关，当求出式(9.8-22)的一个特解后，即可按式(9.8-20)构造线性反馈控制器，式中

$$
K (t) = P ^ {- 1} B ^ {\tau} R (t)
$$

是待求的线性反馈矩阵，在一般情况下它是变系数矩阵。如果式(9.8-22)有稳态解，即存在一个常量矩阵 R 使下列恒等式成立

$$
Q + A ^ {\tau} R - R B P ^ {- 1} B ^ {\tau} R + R A = 0 \tag {9.8-23}
$$

则最优反馈控制器是线性常系数的，反馈矩阵 K 不仅与系统的初始状态无关，而且也不依赖于时间 $t_{1}$ ，即对任何时间间隔 $[0, t_{1}]$ ，由式(9.8-20)确定的反馈控制总能使指标泛函 J 取极小值。

#### 9.9 短程火箭的最佳推力程序

作为不固定端点的最优控制设计的一个例子，我们试讨论短程飞航式火箭的最佳推力程序设计方法。设 $m(t)$ 是火箭的瞬时质量； $V_{r}$ 是火箭喷射物质的分离相对速度，假定其为常数； $P(t)$ 代表推力， $P_{\max}$ 为发动机的最大可能推力；地心引力 $g$ 认为是常数； $x, y$ 为火箭在以发射点为坐标原点的直角坐标系内的坐标（图 9.9-1）。因为是短射程火箭，我们将假定地心的引力始终平行于 $y$ 轴向下； $\dot{m} = \frac{dm}{dt}$ 为燃料的秒耗量；再假定空气阻力为 $Q = Q(y, V) = Q(y, \dot{x}, \dot{y})$ 。在上述假定的条件下，我们可以通过改变发动机的秒消耗量 $\dot{m}$ 和轨迹角 $\theta$ 来控制火箭的飞行速度

和飞行方向。火箭的运动方程式可写成

$$
\frac {d ^ {2} x}{d t ^ {2}} = \frac {1}{m (t)} (P (t) - Q (y, \dot {x}, \dot {y})) \cos \theta
$$

$$
\frac {d ^ {2} y}{d t ^ {2}} = \frac {1}{m (t)} (P (t) - Q (y, \dot {x}, \dot {y})) \sin \theta - g
$$

$$
\frac {d m}{d t} = - \frac {1}{V _ {r}} P (t) \tag {9.9-1}
$$

引进新的变量 $x_{1} = x, x_{2} = \dot{x}, x_{3} = y, x_{4} = \dot{y}, x_{5} = \frac{m(t)}{m_0}; u_{1} = \frac{P}{P_{\max}}, u_{2} = \theta$ 。方程组 (9.9-1)可改写成一阶方程组

> 此处省略原书 **图 9.9-1**

$$
\frac {d x _ {1}}{d t} = x _ {2}
$$

$$
\frac {d x _ {2}}{d t} = \frac {a u _ {1} - b Q (x _ {2} , x _ {3} , x _ {4})}{x _ {5}} \cos u _ {2}
$$

$$
\frac {d x _ {3}}{d t} = x _ {4}
$$

$$
\frac {d x _ {4}}{d t} = \frac {a u _ {1} - b Q (x _ {2} , x _ {3} , x _ {4})}{x _ {5}} \sin u _ {2} - g
$$

$$
\frac {d x _ {5}}{d t} = - c u ^ {1} \tag {9.9-2}
$$

式中 $a = P_{\mathrm{max}} / m_0, b = \frac{1}{m_0}, c = \frac{P_{\mathrm{max}}}{V_r m_0}$ 。 这个方程组内含有两个控制量 $u_{1}$ 和 $u_{2}$ ，它们的取值是受限制的，限制条件是

$$
0 \leqslant u _ {1} \leqslant 1, \quad 0 \leqslant u _ {2} \leqslant 2 \pi \tag {9.9-3}
$$

对这种飞航式短射程火箭可以提出下列问题：在给定的时间 T 内按预定的方向 n 飞行最远，应如何选择最好的巡航推力程序 $u_{1}(t)(P(t))$ 和 $u_{2}(t)(\theta(t))$ ? 规定飞行最远的方向 n 可以用向量 $(n_{1}, n_{2})$ 表示, $n_{1}^{2} + n_{2}^{2} = 1$ 。当 $n_{1} = 0, n_{2} > 0$ 时, 预定的方向将是垂直飞行。当 $n_{1} > 0, n_{2} = 0$ 时, 将是水平飞行。这里还假定在规定的时间 T 内, 火箭上所储燃料足以使发动机的秒消耗量达最大值。

从这一问题的物理意义来看，最优解是存在的。对于给定的飞行方向显然存在一个程序 $\theta(t)$ , 使每一瞬间速度方向为最优。推力程序 $P(t)$ 受阻力 Q 的约束, 如果速度很大, 则气动阻力急剧增大, 消耗燃料也将随之增加。如果推力很小, 则不能在给定的时间内达到很大的射程。上述运动的指标可以用下式表示

$$
J = n _ {1} x + n _ {2} y = n _ {1} x _ {1} + n _ {2} x _ {3} = \max \tag {9.9-4}
$$

或者

> 此处省略原书 **图 9.9-2**

$$
J = - n _ {1} x _ {1} - n _ {2} x _ {3} = \min \tag {9.9-5}
$$

这一问题可以转换成轨线末端受限制的情况。事实上，过与单位向量 $\boldsymbol{n}_{0}=(n_{1},n_{2},0,0,0)$ 平行的直线 L（图 9.9-2）上的任一点做一垂直的 n-1 维超平面 P, $n_{0}$ 将是它的法向量。上述命题可等价地转述为：将火箭引导到平面 P 上，使交点 S 在直线 L 上离原点最远。交点 S 是未知的，但这并不影响我们对前节所述理论的应用。

取火箭的助推段终点为求解上述问题的初始条件 $\boldsymbol{x}_{0}=(x_{10},x_{20},x_{30},x_{40},x_{50})$ 。于是，可以根据标准方程组（9.7-6）写出求解最优控制的方程组

$$
\frac {d x _ {0}}{d t} = - n _ {1} x _ {2} - n _ {2} \frac {a u _ {1} - b Q (x _ {2} , x _ {3} , x _ {4})}{x _ {5}} \cos u _ {2}, \quad x _ {0} (0) = 0
$$

$$
\frac {d x _ {1}}{d t} = x _ {2}, \quad x _ {1} (0) = x _ {1 0}
$$

$$
\frac {d x _ {2}}{d t} = \frac {a u _ {1} - b Q \left(x _ {2} , x _ {3} , x _ {4}\right)}{x _ {5}} \cos u ^ {2}, \quad x _ {2} (0) = x _ {2 0}
$$

$$
\frac {d x _ {3}}{d t} = x _ {4}, \quad x _ {3} (0) = x _ {3 0}
$$

$$
\frac {d x _ {4}}{d t} = \frac {a u _ {1} - b Q (x _ {2} , x _ {3} , x _ {4})}{x _ {5}} \sin u - g, \quad x _ {4} (0) = x _ {4 0}
$$

$$
\frac {d x _ {5}}{d t} = - c u _ {1}, \quad x _ {5} (0) = x _ {5 0} \tag {9.9-6}
$$

它的共轭方程组是

$$
\frac {d \psi_ {0}}{d t} = 0, \quad \psi_ {0} \leqslant 0
$$

$$
\frac {d \psi_ {1}}{d t} = 0, \quad \psi_ {1} (T) = \psi_ {1} (t) \equiv - n _ {1}
$$

$$
\frac {d \psi_ {2}}{d t} = n _ {1} \psi_ {0} - \psi_ {1} + \frac {\boldsymbol {b}}{x _ {5}} \frac {\partial Q}{\partial x _ {2}} \left(\left(\psi_ {2} - n _ {2} \psi_ {0}\right) \cos u _ {2} + \psi_ {4} \sin u _ {2}\right), \quad \psi_ {2} (T) = - n _ {2}
$$

$$
\frac {d \psi_ {3}}{d t} = \frac {\boldsymbol {b}}{x ^ {5}} \frac {\partial Q}{\partial x ^ {3}} ((\psi_ {2} - n _ {2} \psi_ {0}) \cos u _ {2} + \psi_ {4} \sin u _ {2}), \quad \psi_ {3} (T) = 0
$$

$$
\frac {d \psi_ {4}}{d t} = - \psi_ {3} + \frac {\boldsymbol {b}}{x _ {5}} \frac {\partial Q}{\partial x _ {4}} \left(\left(\psi_ {2} - n _ {2} \psi_ {0}\right) \cos u _ {2} + \psi_ {1} \sin u _ {2}\right), \quad \psi_ {4} (T) = 0
$$

$$
\frac {d \psi_ {5}}{d t} = - \frac {a u _ {1} - b Q \left(x _ {2} , x _ {3} , x _ {4}\right)}{x _ {5} ^ {2}} \left(\left(\psi_ {2} - n _ {2} \psi_ {0}\right) \cos u _ {2} + \psi_ {4} \sin u _ {2}\right), \quad \psi_ {5} (T) = 0 \tag {9.9-7}
$$

哈密顿函数为

$$
\begin{array}{l} H = \varphi (x _ {2}, x _ {4}; \psi_ {0}, \psi_ {3}, \psi_ {1}) - n _ {2} \psi_ {0} \frac {a u _ {1} - b Q}{x ^ {5}} \cos u _ {2} + \psi_ {2} \frac {a u _ {1} - b Q}{x ^ {5}} \cos u _ {2} \\ + \psi_ {4} \frac {a u _ {1} - b Q}{x _ {5}} \sin u _ {2} - c \psi_ {5} u _ {1} \tag {9.9-8} \\ \end{array}
$$

式中

$$
\varphi \left(x _ {2}, x _ {4}; \psi_ {0}, \psi_ {3}, \psi_ {4}\right) = - n _ {1} x _ {2} \psi_ {0} + \psi_ {1} x _ {2} + \psi_ {3} x _ {4} - \psi_ {4} g
$$

从前节的讨论可知，函数 H 沿最优运动取最大值:

$$
H (\mathring {\boldsymbol {x}} (t), \bar {\boldsymbol {\psi}} (t), \mathring {\boldsymbol {u}} (0)) = \max _ {\boldsymbol {u} \in U} H (\mathring {\boldsymbol {x}} (t), \bar {\boldsymbol {\psi}} (t), \boldsymbol {u}) \equiv 0, \quad 0 \leqslant t \leqslant T \tag {9.9-9}
$$

条件式(9.9-9)意味着

$$
\begin{array}{l} \frac {a \stackrel {\circ} {u} _ {1} (t) - b Q \left(\stackrel {\circ} {x} _ {2} , \stackrel {\circ} {x} _ {3} , \stackrel {\circ} {x} _ {4}\right)}{\stackrel {\circ} {x} _ {5} (t)} \left(\left(\stackrel {\circ} {\psi} _ {2} (t) - n _ {2} \psi_ {0}\right) \cos \stackrel {\circ} {u} _ {2} (t) + \stackrel {\circ} {\psi} _ {4} (t) \sin \stackrel {\circ} {u} _ {2} (t)\right) - c \stackrel {\circ} {\psi} _ {5} (t) \stackrel {\circ} {u} _ {1} (t) \\ = \max _ {u \in U} \left[ \frac {a u _ {1} - b Q \left(\stackrel {\circ} {x} _ {2} , \stackrel {\circ} {x} _ {3} , \stackrel {\circ} {x} _ {4}\right)}{\stackrel {\circ} {x} _ {5} (t)} \left(\left(\stackrel {\circ} {\psi} _ {2} (t) - n _ {2} \psi_ {0}\right) \cos u _ {2} + \stackrel {\circ} {\psi} _ {4} (t) \sin u _ {2}\right) - c \stackrel {\circ} {\psi} _ {5} (t) u _ {1} \right] \tag {9.9-10} \\ \end{array}
$$

上面共得到 12 个一阶微分方程式，14 个未知函数，11 个边界条件。未知数 $\psi_{0}$ 可以从式(9.9-7)求出， $\mathring{u}_{1}(t)$ 和 $\mathring{u}_{2}(t)$ 可以从式(9.9-9)或(9.9-10)求出。令

$$
\eta (t, \stackrel {\circ} {x} (t), \stackrel {\circ} {\psi} (t), \stackrel {\circ} {u _ {2}} (t)) = \frac {a}{\stackrel {\circ} {x _ {5}} (t)} (\stackrel {\circ} {\psi_ {2}} (t) - n _ {2} \stackrel {\circ} {\psi_ {0}}) \cos \stackrel {\circ} {u _ {2}} (t) + \stackrel {\circ} {\psi_ {1}} (t) \sin \stackrel {\circ} {u _ {2}} (t) - c \stackrel {\circ} {\psi_ {5}} (t)
$$

则

$$
\stackrel {\circ} {w} (t) = \left\{ \begin{array}{l l} 1, & \text {若} \eta > 0 \\ 0, & \text {若} \eta <   0 \end{array} \right. \tag {9.9-11}
$$

由此可知最优的推力程序是开关式函数，要么以最大推力工作，要么以最小推力工作。最优方向程序 $\dot{u}_{2}(t)$ 的变化规律要复杂些。但是按限制条件式(9.9-3)，它实际上是不受限制的。因此 H 对 $u_{2}$ 应取极值。所以，我们可以对式(9.9-10)右端求对 $u_{2}$ 的偏导数并令其等于零，解出后得

$$
\tan \stackrel {\circ} {u _ {2}} (t) = \frac {\stackrel {\circ} {\psi_ {4}} (t)}{\stackrel {\circ} {\psi_ {2}} (t) - n _ {2} \psi_ {0}}
$$

或者

$$
\cos \stackrel {\circ} {u _ {2}} (t) = \pm \frac {\stackrel {\circ} {\psi_ {2}} (t) - n _ {2} \psi_ {0}}{\sqrt {\stackrel {\circ} {\psi_ {1}} ^ {2} + (\stackrel {\circ} {\psi_ {2}} (t) - n _ {2} \psi_ {0}) ^ {2}}}
$$

$$
\sin \stackrel {\circ} {u _ {2}} (t) = \pm \frac {\stackrel {\circ} {\psi_ {1}} (t)}{\sqrt {\psi_ {1} ^ {2} + (\stackrel {\circ} {\psi_ {2}} - n _ {2} \psi_ {0}) ^ {2}}} \tag {9.9-12}
$$

上式右端之符号应该这样选取，使 $\cos\dot{u}_{2}(t)$ 和 $\sin\dot{u}_{2}(t)$ 均为正。将式(9.9-12)代入式(9.9-11)后， $\dot{u}_{1}(t)$ 也就不依赖于 $\dot{u}_{2}(t)$ 了。

如果在某种特定的条件下，空气阻力可以忽略不计，则式(9.9-6)和(9.9-7)还可以大为化简。但是，不管是否忽略阻力，用一般的理论分析方法求解方程组(9.9-4)—(9.9-10)几乎是不可能的。通常是利用计算机对特定的问题进行研究并求解。

#### 9.10 动态规划与最优控制原理

归纳前面几节的讨论，为了求得受控系统满足某一给定的积分型指标的最优控制，必须同时研究问题的全局特征，写出完整的标准方程组，然后才可能求出最优控制规律。这是变分方法的基本特点，特别适宜于对控制问题的分析处理.然而用分析方法只能处理比较简单的情况。在实际问题中，大多数受控运动方程是比较复杂的，只能用数字计算机去作最优控制设计。本节内我们再介绍另一种最优控制的设计方法，叫动态规划法。这种方法的基本思想和变分方法不同，对某些问题更适宜于在计算机上作最优设计。

> 此处省略原书 **图 9.10-1**

动态规划的基本思想是把整个控制过程分为若干段，在每一段内选择最优控制，使满足给定的指标要求。它可以概括成一个原理：无论系统的初始状态如何，也无论第一段运动过程中的最优控制是何种形式，全局为最优的控制函数，对应于第一阶段的终点状态，第二段运动过程中控制函数的选择，按给定的指标也一定是最优的。这就是最优控制原理。用图 9.10-1 对这一原理略作说明，设自 $A$ 点至 $C$ 点的按某种意义最优的运动是 $\pmb {x}(t),0\leqslant t\leqslant T$ ，其相应的最优控制是 $\pmb {u}(t),0\leqslant t\leqslant T$ 。系统 运动经过 B 点的时刻记作 $\tau, 0 < \tau < T$ 。最优控制原理的几何含意是，以 A 点为始点，以 C 点为终点的最优控制 $\boldsymbol{u}(t), 0 \leqslant t \leqslant T$ ，也一定是以 B 点为始点，以 C 点为终点，定义于时间 $\tau \leqslant t \leqslant T$ 上的最优控制。

为简单起见，先假定受控对象是一个一阶非线性系统

$$
\frac {d x}{d t} = f (x, u), \quad x (0) = x _ {0} \tag {9.10-1}
$$

终点状态假定是完全“自由”的，无任何约束，但是对控制量 u 的约束形式不是像前面讨论的那样，而是具有下列形式

$$
g _ {1} (\boldsymbol {x}) \leqslant u \leqslant g _ {2} (\boldsymbol {x}) \tag {9.10-2}
$$

我们看到， $\pmb{u}$ 的取值范围不是一成不变的，而与系统的状态有关，上式内左右端的函数 $g_{1}(x)$ 和 $g_{2}(x)$ 是预先给定的。选择控制量 $u(t)$ 的目的是在给定的时间间隔 $T$ 内，使下列泛函取极小值

$$
J (u) = \int_ {0} ^ {T} f _ {0} (x, u) d t = \min \tag {9.10-3}
$$

由于终点状态无任何约束，如果这种最优控制存在且唯一的话，极小值 $J(u(t))$ 将是初始条件 $x_{0}$ 和时间间隔 T 的单值函数。这个泛函的最小值记为 $F(x_{0},T)$ ,于是

$$
F (x _ {0}, T) = \min J (u (t)) \tag {9.10-4}
$$

如果将时间间隔 T 稍微增大，使终端时刻变为 $T + \tau$ ,则上述等式将变成

$$
F (x _ {0}, \tau + T) = \min_ {\substack {u (t), \\ 0 \leqslant t \leqslant \tau}} \left[ \int_ {0} ^ {\tau} f _ {0} (x, u) d t + F (x (\tau), T) \right] \tag{9.10 - 5}
$$

而且 $u(t)$ 的取值范围应该满足条件式(9.10-2)的限制。

如果设 $f(x,u)$ 和 $F(x_{0},T)$ 均为连续可微的二元函数，则

$$
F (x _ {0}, T + \tau) = F (x _ {0}, T) + \frac {\partial F}{\partial T} \tau + O (\tau)
$$

$$
F (x (\tau), T) = F (x _ {0}, T) + \frac {\partial F}{\partial x _ {0}} f (x _ {0}, u) \tau + O (\tau)
$$

当 $\tau\rightarrow0$ 时，应用上面两式的关系，式(9.10-5)可以写成

$$
\frac {\partial F}{\partial T} = \min _ {u} \left[ f _ {0} \left(\boldsymbol {x} _ {0}, \boldsymbol {u}\right) + \frac {\partial F}{\partial x _ {0}} f \left(\boldsymbol {x} _ {0}, \boldsymbol {u}\right) \right] \tag {9.10-6}
$$

如果函数 $F(x_0, T)$ 为已知，则式(9.10-6)将给予可能求出最优控制函数 $\mathring{u}(t)$ 的初始值 $\mathring{u}(t)$ 。我们看到，式(9.10-6)是一个一阶偏微分方程。其中 $f_0$ 和 $f$ 为已知二元函数。为了求解此方程式，需要给定某些边界条件。如果在全平面内求出函数 $F(x_0, T)$ ，那么在每一瞬间的最优控制 $\mathring{u}$ 即可按式(9.10-6)求出。

对于更为一般的受控对象

$$
\frac {d \boldsymbol {x}}{d t} = \boldsymbol {f} (\boldsymbol {x}, \boldsymbol {u}), \quad \boldsymbol {u} \in U (\boldsymbol {x}) \tag {9.10-7}
$$

和泛函指标

$$
J (\boldsymbol {u} (t)) = \int_ {0} ^ {T} f _ {0} (\boldsymbol {x}, \boldsymbol {u}) d t = \min \tag {9.10-8}
$$

记

$$
F (\boldsymbol {x}; T) = \min _ {\boldsymbol {u} \in U (\boldsymbol {x})} J (\boldsymbol {u} (t)) \tag {9.10-9}
$$

符号 $U(x)$ 表示 u 的取值范围随受控对象的状态 x 的变化而变化。重复前面的讨论，并注意到多元自变量的特点，基本函数方程可按下列次序推出

$$
F (\boldsymbol {x}, T + \tau) = \min_ {\substack {\boldsymbol {u} (t) \in U (\boldsymbol {x}) \\ 0 \leqslant t \leqslant \tau}} \left[ \int_ {0} ^ {\tau} f _ {0} (\boldsymbol {x}, \boldsymbol {u}) d t + F (\boldsymbol {x} (\tau), T) \right] \tag{9.10 - 10}
$$

当 $\tau$ 很小时

$$
\boldsymbol {x} (\tau) = \boldsymbol {x} (0) + \boldsymbol {f} (\boldsymbol {x} (0), \boldsymbol {u} (0)) \tau + O (\tau)
$$

$$
F (\boldsymbol {x} (0), T + \tau) = F (\boldsymbol {x} (0), T) + \frac {\partial F}{\partial T} \tau + O (\tau)
$$

$$
\begin{array}{l} F (\boldsymbol {x} (\tau), T) = F (\boldsymbol {x} (0), T) + \sum_ {\alpha = 1} ^ {n} \frac {\partial F}{\partial x _ {\alpha}} f _ {\alpha} (\boldsymbol {x} (0), \boldsymbol {u} (0)) \tau + O (\tau) \\ = F (\boldsymbol {x} (0), T) + \tau \left(\operatorname{grad} _ {x} F (\boldsymbol {x} (0), T), \boldsymbol {f} (\boldsymbol {x} (0), \boldsymbol {u} (0))\right) + O (\tau) \\ \end{array}
$$

令 $\tau\rightarrow0$ , 按上面讨论次序, 可最后得到关于函数 F 的特种偏微分方程

$$
\frac {\partial F}{\partial T} = \min _ {\boldsymbol {u} (0) \in U (\boldsymbol {x} (0))} (\operatorname{grad} _ {x} F (\boldsymbol {x} (0), T), \boldsymbol {f} (\boldsymbol {x} (0), \boldsymbol {u} (0))) \tag {9.10-11}
$$

根据最优控制原理，上面的讨论不仅对始点 $\boldsymbol{x}(0)$ 是正确的，对最优轨线上的任何点也都成立。故上式也可对任意点 $\boldsymbol{x}(\tau)$ 改写为

$$
\frac {\partial F}{\partial \theta} = \min _ {\boldsymbol {u} (\tau) \in U (\boldsymbol {x} (\tau))} \left(\operatorname{grad} _ {\boldsymbol {x}} F (\boldsymbol {x} (\tau), \theta), \boldsymbol {f} (\boldsymbol {x} (\tau), \boldsymbol {u} (\tau))\right) \tag {9.10-12}
$$

式中 $\theta=T-\tau$ ，符号 $\operatorname{grad}_{x}F$ 表示只对 x 取偏导数的梯度向量

$$
\operatorname{grad} _ {x} F (\boldsymbol {x}, \theta) = \left[ \frac {\partial F}{\partial x _ {1}}, \dots , \frac {\partial F}{\partial x _ {n}} \right]
$$

基本方程(9.10-11)或(9.10-12)有两种用途。当函数 $F(x, T)$ 为已知时，可由此求出最优控制 $\mathbf{\dot{u}}(t)$ 。反之，当 $\mathbf{\dot{u}}(t)$ 为已知时，可以由此求出函数 $F(x, \theta)$ 。有时函数 $F$ 可由其他途径求出，此时按式(9.10-12)即可完全确定最优控制函数了。在第八章讨论最速控制系统时，我们曾得到过类似的方程（参看第 8.6 节）。那里我们曾指出求解此方程式的方法。实际上这个方程式与那里得到的结果有深刻联系。此外，对控制量不受限制的情况至今研究得比较详细。读者在文献[2]中可以找到对这一类特殊问题的计算方法。

#### 9.11 拦截问题中的导引律

作为最优控制理论的一个很好的应用，我们介绍一下关于拦截问题中的导引规律的最优选择 $^{[4]}$ 。设有一目标 M 以速度向量 $v_{M}$ 飞来（见图 9.11-1)。今用一个横向可机动的拦截飞行器 D 对目标进行拦截，速度向量为 $v_{D}$ 。用 $x_{M}$ 和 $x_{D}$ 分别表示目标和拦截器的空间坐标，它们之间的相对距离是 $x = x_{M} - x_{D}$ ,相对速度 是 $v=v_{M}-v_{D}$ 。拦截器 D 的飞行方向可以用改变横向加速度 $\alpha_{D}$ 的办法加以控制。拦截任务的目的是找出一种控制规律，使拦截器 D 在某一时刻与目标 M 相碰撞，或者使相对距离 x 在某一时刻达到极小值。相对距离 $\boldsymbol{x}(t)=\boldsymbol{x}_{M}(t)-\boldsymbol{x}_{D}(t)$ 在 t>0 以后的极小值称为拦截脱靶量。为了达到拦截目的而选择的控制规律称为导引律。

导引律是由系统的实时状态决定的控制律。这种控制律使系统在某一时刻达到零脱靶，或达到某一种终止状态。从控制理论的观点看，导引律就是依赖于实时状态的综合控制 (或反馈控制)。下面将看到，用最优控制的综合理论讨论各种导引律可以得到一些新的、很有意思的结论。在这一节中，我们先用最优控制理论推导空间比例导引律，然后引进“零控拦截状态”及“零控拦截曲面 L”的概念，并用这些概念讨论各种导引律。

> 此处省略原书 **图 9.11-1**

在相对体制下，导引问题的运动方程可描述为

$$
\dot {\boldsymbol {x}} = v
$$

$$
\dot {v} = \alpha + \boldsymbol {u} \tag {9.11-1}
$$

这里， $x, v, \alpha$ 分别为目标和拦截器之间的相对位置、相对速度和相对加速度向量，而 $u$ 为控制加速度向量。相对加速度 $\alpha$ 可以叫做固有加速度，它是不能随意改变的，它的大小和方向依赖于状态变量。为简单起见，通常假定 $\alpha$ 是关于 $t$ 的已知函数。

在导引问题中，通常假定系统的初始状态 $x_{0}, v_{0}$ 为已知，而对终点状态可以提出各种不同要求。例如，要求终点状态为零脱靶，即 $x(T)=0$ (T 为导引终止时刻)。一般地，终点状态可描述为

$$
\mathbf {g} (\boldsymbol {x} (T), \upsilon (T)) = \mathbf {0} \tag {9.11-2}
$$

g 是向量，由终点状态约束条件决定。除终点状态约束外，还可能有表明导引过程好坏的性能指标。在系统式(9.11-1)中，加速度 u 是由过载或推力产生的控制。这时，通常以所消耗的总能量的大小，即

$$
\boldsymbol {J} = \frac {1}{2} \int_ {0} ^ {T} \boldsymbol {\mathbf {u}} ^ {\tau} \boldsymbol {\mathbf {u}} d t \tag {9.11-3}
$$

作为性能指标。这里 T 是事先给定的时刻。式(9.11-1)，(9.11-2)，(9.11-3)是典型的最优控制问题。

所谓最优导引律，就是这个最优控制问题的综合控制 $\mathring{u}(x,v)$ 。如果把这个综 合控制求出来，并代入方程(9.11-1)中，则方程组的任意轨线都应该是上述最优控制问题的最优轨线。综合控制 $\mathring{u}(x,v)$ 可按如下方式确定：对任意给定的初值 $x_{0}, v_{0}$ ，先按极大值原理求出最优程序控制 $\mathring{u}(t, x_{0}, v_{0})$ ，然后令 t=0 得 $\mathring{u}(0, x_{0}, v_{0})$ 。控制 $\mathring{u}(0, x_{0}, v_{0})$ 是系统处于 $x_{0}, v_{0}$ 状态时所应取的控制量，因此有 $\mathring{u}(x_{0}, v_{0}) = \mathring{u}(0, x_{0}, v_{0})$ 。

下面求解最优控制问题式(9.11-1)—(9.11-3)。为此，先用 $x^{0}(t)$ ， $v^{0}(t)$ 表示 $u\equiv0$ 时系统运动的轨线（叫做零控弹道）。积分方程组(9.11-1)得

$$
\boldsymbol {x} ^ {0} (t) = \boldsymbol {x} _ {0} + v _ {0} t + \int_ {0} ^ {t} (t - \tau) \alpha (\tau) d \tau
$$

$$
v ^ {0} (t) = v _ {0} + \int_ {0} ^ {t} \alpha (\tau) d \tau \tag {9.11-4}
$$

引入零控平均速度 $\bar{v}^0 (t) = v_0 + \frac{1}{t}\int_0^t (t - \tau)\alpha (\tau)d\tau$ ，则 $x^0 (t)$ 又可表示为

$$
\boldsymbol {x} ^ {0} (t) = \boldsymbol {x} _ {0} + \bar {v} ^ {0} (t) t
$$

当 $u(t) \neq 0$ 时, 方程组(9.11-1)的轨线为

$$
\boldsymbol {x} (t) = \boldsymbol {x} ^ {0} (t) + \int_ {0} ^ {t} (t - \tau) \boldsymbol {u} (\tau) d \tau
$$

$$
v (t) = v ^ {0} (t) + \int_ {0} ^ {t} u (\tau) d \tau \tag {9.11-5}
$$

最优控制问题式(9.11-1)—(9.11-3)的哈密顿函数为 $^{①}$

$$
H = \boldsymbol {\psi} _ {1} ^ {\tau} v + \boldsymbol {\psi} _ {2} ^ {\tau} \alpha + \boldsymbol {\psi} _ {2} ^ {\tau} \boldsymbol {u} - \frac {1}{2} \boldsymbol {u} ^ {\tau} \boldsymbol {u} \tag {9.11-6}
$$

而共轭方程和边界条件为

$$
\left\{ \begin{array}{l} \dot {\boldsymbol {\psi}} _ {1} = 0, \boldsymbol {\psi} _ {1} (T) = \lambda_ {1} \\ \dot {\boldsymbol {\psi}} _ {2} = - \boldsymbol {\psi} _ {1}, \boldsymbol {\psi} _ {2} (T) = \lambda_ {2} \end{array} \right. \tag {9.11-7}
$$

其中 $\lambda_{1}, \lambda_{2}$ 分别等于 $\frac{\partial}{\partial x(T)}(\lambda^{\tau}g(x(T), v(T))), \frac{\partial}{\partial v(T)}(\lambda^{\tau}g(x(T), v(T))), \lambda$ 为待定向量。如果 $g(x(T), v(T)) = x(T)$ ，则 $\lambda_{2} = 0$ 。积分方程组(9.11-7)得

$$
\boldsymbol {\psi} _ {1} (t) = \lambda_ {1}, \boldsymbol {\psi} _ {2} (t) = \lambda_ {1} (T - t) + \lambda_ {2} \tag {9.11-8}
$$

根据极大值原理，最优控制 $\mathbf{\dot{u}}(t)$ 为

$$
\mathbf {\dot {u}} (t) = \boldsymbol {\psi} _ {2} (t) = \lambda_ {1} (T - t) + \lambda_ {2} \tag {9.11-9}
$$

取 $t = 0$ ，得

$$
\dot {\boldsymbol {u}} (0) = \lambda_ {1} T + \lambda_ {2} \tag {9.11-10}
$$

为了求出综合控制 $\mathring{u}(x_{0},v_{0})$ ，必须把 $\lambda_{1},\lambda_{2}$ 表示成初始状态 $x_{0},v_{0}$ 的函数。为此，

把式 $(9.11-9)$ 代到式 $(9.11-5)$ 中，然后积分，取 t=T,得

$$
\boldsymbol {x} (T) = \boldsymbol {x} ^ {0} (T) + \frac {T ^ {3}}{3} \lambda_ {1} + \frac {T ^ {2}}{2} \lambda_ {2}
$$

$$
\upsilon (T) = \upsilon^ {0} (T) = \frac {T ^ {2}}{2} \lambda_ {1} + T \lambda_ {2} \tag {9.11-11}
$$

其次，用条件 $\boldsymbol{g}(\boldsymbol{x}(T),\upsilon(T))=\boldsymbol{0}$ 和 $\lambda_{1},\lambda_{2}$ 的表达式决定待定向量 $\lambda$ 作为 $\boldsymbol{x}^{0}(T)$ ， $\upsilon^{0}(T)$ 的函数，从而把控制 $\dot{\boldsymbol{u}}(0)$ 表示成零控弹道终止状态 $\boldsymbol{x}^{0}(T),\upsilon^{0}(T)$ 的函数。如果再把 $\boldsymbol{x}^{0}(T),\upsilon^{0}(T)$ 表示成 $x_{0},\upsilon_{0}$ 的函数，就得综合控制 $\dot{\boldsymbol{u}}(\boldsymbol{x}_{0},\upsilon_{0})$ 。用零控弹道终止状态 $\boldsymbol{x}^{0}(T),\upsilon^{0}(T)$ 表示出来的控制律 $\dot{\boldsymbol{u}}(\boldsymbol{x}^{0}(T),\upsilon^{0}(T))$ 叫做“预测导引律”。

当 $\boldsymbol{g}(\boldsymbol{x}(T),\upsilon(T))=\boldsymbol{x}(T)$ (即终止状态为零脱靶状态）时， $\lambda_{2}=\mathbf{0},\lambda_{1}=\lambda$ ，从而 $\dot{\boldsymbol{u}}(0)=\lambda_{1}T,\boldsymbol{x}(T)=\boldsymbol{x}^{0}(T)+\frac{T^{3}}{3}\lambda_{1}$ 。由 $\boldsymbol{x}(T)=\boldsymbol{0}$ 得

$$
\mathring {\boldsymbol {u}} (0) = - \frac {3 \boldsymbol {x} ^ {0} (\boldsymbol {T})}{T ^ {2}} \tag {9.11-12}
$$

这是终止状态为零脱靶时的“预测导引律”。 $x^{0}(T)$ 叫做“预测脱靶量”。

再讨论空间比例导引律。把式(9.11-12)中的预测脱靶量具体表示出来，得

$$
\mathbf {\dot {u}} (0) = - \frac {3 (\boldsymbol {x} _ {0} + \bar {v} ^ {0} (T) T)}{T ^ {2}} \tag {9.11-13}
$$

这里 T 是事先给定的, 可按适当方式选取。如果取

$$
T = - \frac {\left(\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T)\right)}{\mid \bar {v} ^ {0} (T) \mid^ {2}}
$$

则式 $(9.11-13)$ 变为

$$
\begin{array}{l} \dot {\boldsymbol {u}} (0) = - 3 \frac {\boldsymbol {x} _ {0} (\bar {v} ^ {0} (T) , \bar {v} ^ {0} (T)) - \bar {v} ^ {0} (T) (\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T))}{(\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T)) ^ {2}} | \bar {v} ^ {0} (T) | ^ {2} \\ = 3 \frac {\left| \boldsymbol {x} _ {0} \right| ^ {2} \left| \bar {v} ^ {0} (T) \right| ^ {2}}{\left(\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T)\right) ^ {2}} \frac {\left(\boldsymbol {x} _ {0} \times \bar {v} ^ {0} (T)\right)}{\left| \boldsymbol {x} _ {0} \right| ^ {2}} \times \bar {v} ^ {0} (T) \\ \end{array}
$$

其中用 $x \times y$ 表示两个向量的向量积，而 $(\boldsymbol{x}_{0} \times \bar{\upsilon}^{0}(T)) / |\boldsymbol{x}_{0}|^{2}$ 是由平均速度 $\bar{\upsilon}^{0}(T)$ 引起的视线 $x_{0}$ 的旋转角速度——视线转率。如果把这个视线转率记成 $\omega$ ，则有

$$
\dot {\boldsymbol {u}} (0) = 3 \frac {\left| \boldsymbol {x} _ {0} \right| ^ {2} \left| \bar {v} ^ {0} (T) \right| ^ {2}}{\left(\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T)\right) ^ {2}} \omega \times \bar {v} ^ {0} (T) \tag {9.11-14}
$$

如果在系统式(9.11-1)中假定 $\alpha\equiv0$ ，则 $\bar{v}^{0}(T)=v_{0}$ 从而式(9.11-14)变为

$$
\mathring {\boldsymbol {u}} (0) = 3 \frac {\left| \boldsymbol {x} _ {0} \right| ^ {2} \left| v _ {0} \right| ^ {2}}{\left(\boldsymbol {x} _ {0} , v _ {0}\right) ^ {2}} \omega \times v _ {0} \tag {9.11-15}
$$

这就是我们所说的空间比例导引律：控制式(9.11-15)的大小与视线转率成正比，而控制方向垂直于相对速度 $v_{0}$ 。

如果取

$$
T = - \frac {\mid \boldsymbol {x} _ {0} \mid^ {2}}{\left(\boldsymbol {x} _ {0} , \bar {v} ^ {0} (T)\right)}
$$

则得到另一种比例导引律

$$
\mathbf {\dot {u}} (0) = 3 \frac {\left(\boldsymbol {x} _ {0} , \overline {{v}} ^ {0} (T)\right)}{\mid \boldsymbol {x} _ {0} \mid^ {2}} \omega \times \boldsymbol {x} _ {0} \tag {9.11-16}
$$

这个控制方向是垂直于视线 $x_{0}$ 的。

在导引问题中，一般“初始偏差”都比较大。通常希望在导引的初始阶段，用较大的控制力把初始偏差的大部分消除掉。比较理想的导引律应该是在导引的初始阶段能提供较大的控制力以便消除较大的初始偏差，而在导引过程的后期，则用较小的控制力进行“微调”。但是，导引律式(9.11-12)—(9.11-16)都不能做到这一点。因为，它们都是从“整个导引过程都在消除初始偏差”这样观点出发推导的公式，因而横向过载的分布在整个导引过程中是比较平均的。横向过载的这种平均分布在实际上是很不理想的。因为在拦截器接近目标时，为了保持导引规律不被破坏，需要付出很大的横向控制过载，而这在实际上是做不到的。事实上，当 $T\to0$ 或 $|x_{0}| \to0$ 时，只要 $x^{0}(T)$ 或 $\omega$ 不趋于零，控制过载式(9.11-12)—(9.11-16)都将趋于无穷大，这就是通常的比例导引法在导引过程后期出现“过载饱和”的原因。有没有一种办法能克服这种缺点呢？把上面的“整个过程的平均”换成“短时间内的平均”是克服上述缺点的一种办法。

为了进一步研究导引问题，“零控拦截状态”及曲面 L 的概念很有用处。从控制律式(9.11-12)，(9.11-14)和(9.11-16)中可看出，如果零控预测脱靶 $\boldsymbol{x}^{0}(T)$ 或 $\omega$ 等于零，控制力 $\dot{\boldsymbol{u}}(0)$ 也等于零，并且在整个过程中不加控制力也能实现拦截。如果系统在某一时刻已处于这样的状态，从这个状态预测的零控脱靶量为零，那么不加控制力，经有限时间也能实现准确命中。我们把这种特殊的状态称之为“零控拦截状态”，即无控也能实现拦截的状态，在导引问题中“零控拦截状态”的存在是一个普遍现象。古典导引法中的所有直线弹道和所谓基准弹道，实质上都是由零控拦截状态所组成的。

由方程(9.11-1)所描述的导引问题中，凡是满足条件

$$
\boldsymbol {x} ^ {0} (\mu) = \boldsymbol {x} _ {0} + \mu \bar {\upsilon} (\mu) = 0 \tag {9.11-17}
$$

的初始状态 $x_{0}, v_{0}$ ，都是零控拦截状态。这里 $\mu$ 是非负数。如果 $\alpha \equiv 0$ ，则 $\bar{v}^{0}(\mu) = v_{0}$ 。这时零控拦截状态为满足

$$
\boldsymbol {x} _ {0} + \mu v _ {0} = 0, \quad \mu \geqslant 0 \tag {9.11-18}
$$

的初始状态。所有这种状态在整个状态空间(6 维空间）中组成 4 维曲面[式(9.11-18)是含 7 个变量 $x_{0}, v_{0}, \mu$ 的三个方程]。所有零控拦截状态所组成的曲面叫做“零控拦截曲面”，用 L 记之，简称 L 曲面，或曲面 L。

如果导引问题的系统方程写成

$$
\left\{ \begin{array}{l} \dot {\boldsymbol {x}} = v, \boldsymbol {x} (0) = \boldsymbol {x} _ {0} \\ \dot {v} = - \omega^ {2} \boldsymbol {x} + \boldsymbol {u}, \quad v (0) = v _ {0} \end{array} \right.
$$

则零控预测脱靶量为

$$
\boldsymbol {x} ^ {0} (T) = \cos \omega T \boldsymbol {x} _ {0} + \frac {1}{\omega} \sin \omega T v _ {0}
$$

于是 $x_{0}, v_{0}$ 为零控拦截状态的充分必要条件是

$$
\boldsymbol {x} _ {0} + \mu v _ {0} = 0, \quad \mu = \frac {1}{\omega} \tan \omega T
$$

这里 $\mu$ 的取值可正可负。

对一般情形，分别用目标和拦截器的运动方程式能更好地说明零控拦截状态的意义。设目标和拦截器的运动方程分别为

$$
\begin{array}{l} \left\{ \begin{array}{l} \dot {\boldsymbol {x}} _ {M} = v _ {M} \\ \dot {v} _ {M} = \alpha_ {M} (\boldsymbol {x} _ {M}, v _ {M}) \end{array} \right. \\ \left\{ \begin{array}{l} \dot {\boldsymbol {x}} _ {D} = v _ {D} \\ \dot {v} _ {D} = \alpha_ {D} (\boldsymbol {x} _ {D}, v _ {D}) + \boldsymbol {u} \end{array} \right. \\ \end{array}
$$

给定了目标的初始状态 $x_{M0}, v_{M0}$ 以及拦截器的初始位置 $x_{D0}$ 和导弹的初始速度 $|v_{D0}|$ 以后，这时只要 $|v_{D0}|$ 足够大，我们总可以选择拦截器的速度方向，使得它沿这个方向飞行，没有控制力作用也能实现拦截。这种方向叫做“零控拦截方向”。这个零控拦截方向和给定的目标、拦截器的初始条件一起组成一个零控拦截状态。所有这种零控拦截状态，在整个状态空间（12 维空间）中组成 10 维曲面 $L$ （由于只有 10 个独立变量 $x_{M0}, v_{M0}, x_{D0}, |v_{D0}|$ ）。在一般的导引问题中，要精确描述出曲面 $L$ 是个复杂的问题。但是，导引问题中存在着曲面 $L$ ，是肯定的。

再看一看古典导引法和曲面 L 的关系。追踪法、平行接近法、前置量法及三点法等古典导引法，指的是受控制力作用之后的系统状态所应满足的条件。这些导引法并不直接回答“怎样加控制力”的问题。它们只说明，如果系统的状态始终保持在那种状态，就能够实现准确拦截。从前面的讨论中可以看出，系统受控制力作用之后所应保持的理想的状态是零控拦截状态。古典导引法实质上是对各种特殊情况下的 L 曲面的近似描述。

先讨论追踪法。用各自的速度描述零控拦截状态所满足的条件式(9.11-17)是

$$
\boldsymbol {x} _ {0} + \mu \bar {\upsilon} _ {M} ^ {0} (\mu) = \mu \bar {\upsilon} _ {D} ^ {0} (\mu), \quad \mu \geqslant 0 \tag {9.11-19}
$$

如果假定 $|\bar{v}_M^0 (\mu)|\ll |\bar{v}_D^0 (\mu)|$ ，即 $|\bar{v}_M^0 (\mu)|$ 比 $|\bar{v}_D^0 (\mu)|$ 小得多，则近似地有

$$
\boldsymbol {x} _ {0} = \mu \bar {v} _ {D} ^ {0} (\mu), \quad \mu \geqslant 0
$$

即视线 $x_{0}$ 与速度 $\bar{v}_{D}^{0}(\mu)$ 方向一致。再假定 $\alpha\equiv0$ ，则 $\bar{v}_{D}^{0}(\mu)=v_{D0}$ ，因而有

$$
\boldsymbol {x} _ {0} = \mu v _ {D 0}, \quad \mu \geqslant 0
$$

现在把 $x_{0}, v_{D0}$ 看做受控制作用后的状态, 那么受控制作用后的拦截器的速度方向应指向目标, 这就是追踪法。追踪法是目标速度（相对于拦截器速度）很小时的曲面 L 的近似描述。

再看平行接近法。对式(9.11-18)的两边向量乘上 $x_{0}$ ，得

$$
\boldsymbol {x} _ {0} \times \bar {v} _ {M} ^ {0} (\mu) = \boldsymbol {x} _ {0} \times \bar {v} _ {D} ^ {0} (\mu) \tag {9.11-20}
$$

如果假定 $\alpha_{M} \equiv 0, \alpha_{D} \equiv 0$ ，则 $\bar{v}_{M}^{0}(\mu) = v_{M0}, \bar{v}_{D}^{0}(\mu) = v_{D0}$ ，这时上式变成

$$
\boldsymbol {x} _ {0} \times v _ {M 0} = \boldsymbol {x} _ {0} \times v _ {D 0}
$$

受控制力作用后的拦截器速度 $\upsilon_{D0}$ 应使上式成立。这就是平行接近法。用 $\varphi$ 记 $x_{0}$ 与 $\upsilon_{D0}$ 的夹角， $\delta$ 记 $x_{0}$ 与 $\upsilon_{M0}$ 的夹角，则由上式得

$$
\sin \varphi = \frac {\mid v _ {M 0} \mid}{\mid v _ {D 0} \mid} \sin \delta
$$

平行接近法是自由运动（无控弹道）为等速运动时的曲面 L 的描述。

在前置量导引法中，先把 $\overline{v}_{D}^{0}(\mu)$ , $\overline{v}_{M}^{0}(\mu)$ 具体表示出来

$$
\bar {v} _ {D} ^ {0} (\mu) = v _ {D 0} + \frac {1}{\mu} \int_ {0} ^ {\mu} (\mu - \tau) \alpha_ {D} (\tau) d \tau
$$

$$
\bar {v} _ {M} ^ {0} (\mu) = v _ {M 0} + \frac {1}{\mu} \int_ {0} ^ {\mu} (\mu - \tau) \alpha_ {M} (\tau) d \tau
$$

记

$$
\Delta \bar {v} = \frac {1}{\mu} \int_ {0} ^ {\mu} (\mu - \tau) (\alpha_ {M} (\tau) - \alpha_ {D} (\tau)) d \tau
$$

这时从式(9.11-20)可得到

$$
\boldsymbol {x} _ {0} \times (\upsilon_ {M 0} + \Delta \bar {\upsilon}) = \boldsymbol {x} _ {0} \times \upsilon_ {D 0}
$$

记 $\varphi$ 为 $x_{0}$ 与 $v_{D0}$ 的夹角， $\delta$ 为 $x_{0}$ 与 $v_{M0}$ 的夹角，而 $\delta + \Delta\delta$ 为 $x_{0}$ 与 $v_{M0} + \Delta\bar{v}$ 的夹角，则有

$$
\sin \varphi = \frac {\mid v _ {M 0} + \Delta v \mid}{\mid v _ {D 0} \mid} \sin (\delta + \Delta \delta) \tag {9.11-21}
$$

受控制力作用后的拦截器前置角（视线 $x_{0}$ 与拦截器速度之间夹角 $\varphi$ )可由式(9.11-21)的右端来估计。当然，一般来说，这种估计只能是近似的。从这里看出，前置量法是 $\alpha\neq0$ 时的曲面 L 的近似描述。

最后再讨论三点法。由于 $x_{0}=x_{M0}-x_{D0}$ ，故式(9.11-19)可改写为

$$
\boldsymbol {x} _ {M 0} + \mu \bar {v} _ {M} ^ {0} (\mu) = \boldsymbol {x} _ {D 0} + \mu \bar {v} _ {D} ^ {0} (\mu), \quad \mu \geqslant 0
$$

如果 $\mu\bar{v}_{M}^{0}(\mu)$ 比较小, 则近似地有

$$
\boldsymbol {x} _ {M 0} = \boldsymbol {x} _ {D 0} + \mu \bar {v} _ {D} ^ {0} (\mu), \quad \mu \geqslant 0
$$

这个近似等式说明，当 $x_{D0}$ 平行于 $x_{M0}$ 时， $\upsilon_{D0}$ 也应平行于 $x_{M0}$ ，而当 $x_{D0}$ 不平行于 $x_{M0}$ 时，拦截器的速度 $\upsilon_{D0}$ 应使 $x_{D0}$ 接近 $x_{M0}$ 方向（因为 $\mu \geqslant 0$ ），这就是三点法的几何意义。因此，三点法是目标速度（相对于拦截器速度）比较小时，曲面 $L$ 在绝对坐标系中的近似表示。

从以上讨论可看出，古典导引法给出的是受控制后的系统状态所应满足的条件，并没有给出加控制力的办法。用什么样的控制去实现古典导引法呢?这个问题，实质上是用什么样的控制律把系统引到曲面 L 上的问题。

现在我们讨论曲面 L 上的一般导引律。导引的最终目的是实现拦截，即达到零脱靶、有了曲面 L，我们可以把导引的着眼点从“终点零脱靶”移到“曲面 L”上，即把系统导引到曲面 L 上并消除控制力的办法达到拦截的目的。这种导引律可以统称“曲面 L 上的导引律”，也就是说，实质上是把拦截器的速度方向对准到零控拦截方向上。因此，也可以叫做“对准法”或“瞄准法”。

下面就 $\alpha\equiv0$ 的情形讨论在零控曲面 L 上的导引律。作为最优控制问题，这里的终止状态为曲面 L，它在相空间中的方程式是

$$
\boldsymbol {x} (T) = \mu v (T) = 0, \quad \mu \geqslant 0 \tag {9.11-22}
$$

即

$$
\mathbf {g} (\boldsymbol {x} (T), v (T)) = \boldsymbol {x} (T) + \mu v (T)
$$

其中 $\mu$ 为某个独立参数。用待定常向量 $\lambda$ 乘式(9.11-22)，便得内积恒等式

$$
(\lambda , \boldsymbol {x} (T) + \mu v (T)) = 0 \tag {9.11-23}
$$

由于 $\mu$ 是独立参数, 上式左端对它微分后得

$$
(\lambda , \upsilon (T)) = 0 \tag {9.11-24}
$$

就是说，待定常向量 $\lambda$ 应满足上式。在式(9.11-23)中对 $x(T)$ 和 $v(T)$ 的分量微分，得最优问题的共轭方程的边界条件[见式(9.11-7)]

$$
\lambda_ {1} = \lambda , \lambda_ {2} = \mu \lambda
$$

把这个 $\lambda_{1}, \lambda_{2}$ 代到式(9.11-10)和(9.11-11)，又得到

$$
\dot {\boldsymbol {u}} (0) = \lambda (T + \mu) \tag {9.11-25}
$$

$$
\boldsymbol {x} (T) = \boldsymbol {x} ^ {0} (T) + \lambda \left[ \frac {T ^ {3}}{3} + \frac {T ^ {2}}{2} \mu \right]
$$

$$
v (T) = v ^ {0} (T) + \lambda \left[ \frac {T ^ {2}}{2} + T \mu \right] \tag {9.11-26}
$$

从式(9.11-25)中解出 $\lambda$

$$
\lambda = \frac {\mathring {u} (0)}{T + \mu}
$$

再把它代到式 $(9.11-26)$ 中，得

$$
\boldsymbol {x} (T) = \boldsymbol {x} ^ {0} (T) + \hat {\boldsymbol {u}} (0) \left[ \frac {T ^ {3}}{3} + \frac {T ^ {2}}{2} \mu \right] / (T + \mu)
$$

$$
v (T) = v ^ {0} (T) + \mathbf {\dot {u}} (0) \left[ \frac {T ^ {2}}{3} + T \mu \right] / (T + \mu) \tag {9.11-27}
$$

将第二式乘上 $\mu$ 后加到第一式, 可解出

$$
\mathbf {\dot {u}} (0) = - \frac {(\boldsymbol {x} ^ {0} (T) + \mu v ^ {0} (T)) (T + \mu)}{\left[ \frac {T ^ {2}}{3} + T \mu + \mu^ {2} \right] T} \tag {9.11-28}
$$

这里，参数 $\mu$ 还没有被确定.根据式(9.11-24),(9.11-25)知, $\mathring{\boldsymbol{u}}(0)$ 垂直于 $v(T)$ 。因此，由式(9.11-26)又得到

$$
(\mathring {\boldsymbol {u}} (0), v (T)) = (\mathring {\boldsymbol {u}} (0), v ^ {0} (T)) + | \mathring {\boldsymbol {u}} (0) | ^ {2} \left[ \frac {T ^ {2}}{2} + T \mu \right] / (T + \mu) = 0 \tag {9.11-29}
$$

这正是决定参数 $\mu$ 的方程式。

显然，当 $\alpha\equiv0$ 时， $v^{0}(T)=v_{0}$ ， $x^{0}(T)=x_{0}+v_{0}T$ ，故式(9.11-28)，(9.11-29)分别成为

$$
\dot {\boldsymbol {u}} (0) = - \left(\boldsymbol {x} _ {0} + v _ {0} (T + \mu)\right) (T + \mu) / \left[ \frac {T ^ {2}}{3} + T \mu + \mu^ {2} \right] T \tag {9.11-30}
$$

$$
(\hat {\boldsymbol {u}} (0), v (T)) = (\hat {\boldsymbol {u}} (0), v _ {0}) + \left| \hat {u} (0) \right| ^ {2} \left[ \frac {T}{2} + \mu \right] T / (T + \mu) \tag {9.11-31}
$$

为了便于讨论，引入新的参数 S

$$
S = \frac {T}{T + \mu}
$$

这是从初始状态到曲面 L 的过渡时间 T（这个时间可称为“引入”时间）和从初始状态到实现拦截的整个过渡时间 $T + \mu$ 的比值，是拦截过程中“引入”时间所占的比例。显然， $0 \leqslant S \leqslant 1$ 。利用这个参数可把式(9.11-30)和(9.11-31)整理成如下形式

$$
\mathring {\boldsymbol {u}} (0) = - \frac {1}{S \left[ 1 - S + \frac {1}{3} S ^ {2} \right]} \frac {\boldsymbol {x} _ {0} + v _ {0} (T + \mu)}{(T + \mu) ^ {2}} \tag {9.11-32}
$$

$$
\left[ \frac {T}{3} \left(\boldsymbol {x} _ {0}, v _ {0}\right) + \frac {\left| \boldsymbol {x} _ {0} \right| ^ {2}}{2} \right] S ^ {2} - \left[ \left| \boldsymbol {x} _ {0} \right| ^ {2} - \frac {T ^ {2}}{3} \left| v _ {0} \right| ^ {2} \right] S - \left[ \left(\boldsymbol {x} _ {0}, v _ {0}\right) T + \frac {T ^ {2}}{2} \left| v _ {0} \right| ^ {2} \right] = 0 \tag {9.11-33}
$$

这两式结合在一起就构成把系统引入到曲面 L 的最优控制律。按这种规律实现最优控制的程序是先给定引入时间 T，然后从式(9.11-33)中解出满足 $0 \leqslant S \leqslant 1$ 的根 S。有了 S，就可按定义求 $\mu$ 。从而由式(9.11-32)决定出所需的控制 $\mathbf{u}(0)$ 。这样决定的控制就是 T 时间内把系统引到曲面 L 上的“需用加速度”。如果这个加速度超出允许加速度的限制范围，那么另选一个较大的引入时间 T， 并重新计算。这样，我们总可以选取比较合适的引入时间 T。按这种方式决定控制，可以在导引的初始阶段用较大的加速度尽快消除初始偏差，从而克服了前面讨论过的比例导引的缺点。在方程(9.11-33)中，也可以先给定比值 S 或 $\mu$ ，然后反过来决定 T。当 $S=1(\mu=0)$ 时，导引律式(9.11-32)就变成导引律式(9.11-12)。这说明，导引律式(9.11-12)是把整个拦截过程都当做引入时间的导引律。

上面讨论的是终止状态为整个曲面 L 的情况，而 L 由方程 $\boldsymbol{x}(T)+\mu v(T)=0,\mu\geqslant0$ ，所决定。如果给定参数 $\mu$ 的特定值 $\mu_{0}$ ，则方程

$$
L _ {0}: \boldsymbol {x} (T) + \mu_ {0} v (T) = 0
$$

决定出 L 的子曲面。我们也可以讨论以 $L_{0}$ 为终止状态的最优控制律。这时的控制律仍然是式(9.11-32)。但是，在这里 $S_{0}=T/(T+\mu_{0})$ 是确定的，因此方程(9.11-33)就不需要了。从以上讨论可以看出，导引律式(9.11-32)，(9.11-33)中的参数 T, $\mu$ , S，都可以按需要“灵活地”改变。

如果取 $T + \mu_0$ 等于

$$
\frac {- \left| \begin{array}{c} x _ {0} \end{array} \right| ^ {2}}{\left(x _ {0} , v _ {0}\right)}
$$

或

$$
\frac {- \left(\boldsymbol {x} _ {0} , v _ {0}\right)}{\mid v _ {0} \mid^ {2}}
$$

和空间比例导引的推导一样，可分别得到导引到曲面 $L_{0}$ 上的比例导引律

$$
\mathbf {\dot {u}} (0) = S _ {0} ^ {\prime} \frac {\left(\boldsymbol {x} _ {0} , v _ {0}\right)}{\mid \boldsymbol {x} _ {0} \mid^ {2}} \omega \times \boldsymbol {x} _ {0}
$$

或

$$
\mathring {\boldsymbol {u}} (0) = S _ {0} ^ {\prime} \frac {\left| \boldsymbol {x} _ {0} \right| ^ {2} \left| v _ {0} \right| ^ {2}}{\left(\boldsymbol {x} _ {0} , v _ {0}\right) ^ {2}} \omega \times v _ {0}
$$

其中

$$
S _ {0} ^ {\prime} = \frac {1}{S _ {0} \left[ 1 - S _ {0} + \frac {1}{3} S _ {0} ^ {2} \right]}
$$

当 $S_{0}$ 从 1 变到 0 时， $S_{0}^{\prime}$ 从 3 变到 $\infty$ 。这说明，比例导引律中的放大系数 $S_{0}^{\prime}$ ，只要它大于 3，都是对应于某一子曲面 $L_{0}$ 的最优控制律。

对 $\alpha\neq0$ 的情形，利用平均速度也可以讨论曲面 L 上的导引律。也可以讨论，除总能量最小指标外的其他性能指标的最优控制律（见文献 $[4]$ )。

#### 9.12 参考文献

[1] 张嗣瀛, 轨线末端受限制时的最优控制问题, 自动化学报, 1(1963), 2.

[2] 黄琳, 郑应平, 张迪: 李雅普诺夫第二方法与最优控制器分析设计问题, 自动化学报, 2(1964), 4.

[3] 宋健, 具有一般质量指标的控制系统综合, 自动化学报, 1(1963), 1.

[4] 韩京清, 拦截问题中的导引律, 国防工业出版社, 北京, 1977.

[5] Balakrishnan, A. V., Optimal Control Problems in Banach Spaces, J. SIAM Control-3, 1965, 152–180.

[6] Bellman, R. E., Applied Dynamic Programming, Princeton Univ. Press, 1962.

[7] Bliss, G. A., Lectures on the Calculus of Variations. 1959.

[8] Boksenbom, A.S. & Hood, R., NASA TR 1068, 1952.

[9] Bryson, A. E., & Ho Yu-Chi, Applied Optimal Control, Wiley, 1975.

[10] Garber, V., Optimum intercept laws for accelerating targets, AIAA Journal, 6(1968), 11, 2196–2198.

[11] Ho, Y. C., Bryson A. E. & Baron, S., Differential games and optimal pursuit-evasion strategies, IEEE Trans., AC-10(1965), 385–389.

[12] Lanczos, C., The Variational Principle of Mechanics, Univ. of Toronto Press, 1946.

[13] Neustadt, L., An Abstract variational theory with applications to a borad class of optimization problems, J. SIAM, Control-4, 5, 1966–1967.

[14] Sage, A. P., Optimum Systems Control. Printice-Hall, 1968.

[15] Salmon, D. M., Multi-points guidance—an efficient implementation of predictive guidance, AIAA J., 11(1973), 1749–1755.

[16] Tou, J. T., Modern Control Theory, McGraw-Hill, 1964.

[17] Tsien, H. S., (钱学森) & Evans, R. C., Optimum thrust programming for a sounding rocket, J. ARS, 21(1951), 5.

[18] Воронов А. А., Теория автоматического управления, 2, Москва, 1977.

[19] Кельзон, А. С., Динамические задачи кнбер нетики, Судпромгиз, 1959.

[20] Кочетов, В. Т., Половко А. М., Пономарев В. М., Теория систем телеуправления ракет, Наука, Москва, 1969.

[21] Гельфанд, И. М., Фомин С. В., Вариационное исчисление, ФИЗМАТГИЗ, Москва, 1961.

[22] Понтрягин Л. С., Болтянский В. Г. Гамкрелизе Р. В., Мищенко Е. Ф., Математическая теория оптимальных процесов, ФИЗМАТГНЗ, Москва, 1961.

[23] Розонозр Л.И., Принцип максимума понтрягина в теории оптимальных систем, Автоматика и Телемеханика. 20(1959), 10, 11, 12.

[24] Фелъдбаум, А. Я., Основы Теории Оптимальных Автоматических Систем, ФИЗМАТГИЗ, 1963.

[25] Чжан Жен-вей (章仁为), Синтез релейных систем по минимуму интегральных квадратичных отклонений, Автоматика и Телемеханика, 22(1961), 12.
