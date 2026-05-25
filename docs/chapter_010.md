# 工程控制论（上册）

（第三版）

钱学森 宋健 著

## 正文（010）

### 第十章 离散控制系统

到现在为止，我们所讨论的各系统中，输入和输出量或者说受控量和控制量都是时间 t 的连续函数，即时间是连续变化的。但是，随着计算机和数字式通信线路的大量使用，很多情况下信号不是连续传输的，而是用离散的数据序列去传递信息，这种数据序列又常以各种不同的编码形式通过信道进入控制器或计算装置。举例来说，某一信号 $x(t)$ ,只有在间隔相等的各时刻 $t=0, T, 2T\cdots$ 的值 $x(nT), n=0, 1, 2, \cdots$ ,才有可能被采集、传输和接收，而在这些采样时刻之间的信号值或者被遗弃，或者无法确定，这就是离散形信号。

如果一个控制系统的输入信号是离散型的，输出量则可能是连续型的；为了计算方便，常对这种连续输出量进行同步采样或异步采样，把一个连续信号转变成数据序列。如果一个控制系统的输入和输出都是以离散数据列的形式被采集和接收，就称它为离散控制系统，或叫采样控制系统。还有一类系统，虽然输入和输出都是连续的，但它的工作方式是离散的。例如，用脉冲调制方式工作的电机，含有脉冲调制的放大器等，都具有采样器件的特征。含有采样器件的系统常当做离散系统去研究。在本书内采样系统和离散系统将被认为是同义语。

离散系统在现代控制技术中得到越来越广泛的应用，这是因为很多系统中的执行机构或放大器件应用了采样器件；另一方面，也是主要的，因为数字技术的发展，而数字技术中的器件大多数只能以离散的方式工作。中小型过程控制计算机的大量采用，特别是微型计算机的普及，使绝大部分的精密控制系统和复杂的过程控制走向数字化。数字机和数字器件所能达到的精度远高于连续器件，它的容量和功能也是连续工作的器件所不能比拟的。

由常微分方程描述的运动过程本身也常常可以用离散的方法进行计算。由数值计算方法可知，当计算步长足够小时，用离散方法所得到的结果与原连续工作方式的结果相比差别很小。所以在分析和设计连续系统时也可以用离散系统的处理方法去简化计算过程，而不致产生很大误差。

任一离散控制系统，可以用一种标准的方框图表示，如图 10.0-1 所示。可以认为系统的输入信号 $x(t)$ ，反馈信号 $f(t)$ ，误差信号 $\varepsilon(t)$ 和输出量 $y(t)$ 都是时间 $t$ 的连续函数，而采样器件把连续量 $\varepsilon(t)$ 按某一采样频率转换成数字序列 $\varepsilon(nT)$ ，送到数字控制器中进行数字运算，然后经过数模转换把数字序列变成连续控制作用 $u(t)$ 去驱动受控对象。采样器件通常可以认为是一个模数转换装置，它的工作方 式如图 10.0-2 所示, 它把连续信号 $\varepsilon(t)$ 变换成一个数字序列 $\varepsilon(nT)=\{\varepsilon(0), \varepsilon(T), \varepsilon(2T), \cdots, \varepsilon(nT), \cdots\}$ , T 是采样周期。

> 此处省略原书 **图 10.0-1**

> 此处省略原书 **图 10.0-2**

然而从动力学观点来看，采样器件的工作方式与图 10.0-2 所示的有所不同，可以把离散控制器的输出表示成图 10.0-3(a)的形式：把系统中的连续工作部分集中起来，把离散的特点集中于采样器件本身，而后者对连续信号进行脉冲调制、调幅、调宽或调频，这种调制方法示意于图 10.0-3(b)(c)和(d)中。从动力学的观点来看，脉冲宽度为常数的脉冲调幅，脉宽很窄的脉冲调频都属于线性调制方式，而脉冲调宽（频率固定）则是非线性的。本章内我们将主要讨论线性调制的情况，即线性采样系统或线性离散系统。

> 此处省略原书 **图 10.0-3**

#### 10.1 离散系统的运动规律——差分方程式

差分方程最适合于描述采样系统的运动，借助于差分方程可以顺利地研究采样系统的一切特性，诸如稳定性和动态品质的分析，线性系统和最优系统的综合等。因此，研究采样系统的第一步就是正确地建立描绘它的运动规律的差分方程式或差分方程组。本节内我们将详细地讨论这个问题。

以图 10.0-3(a)为例，设受控对象的连续部分的运动方程是常微分方程式

$$
a _ {n} \frac {d ^ {n} y}{d t ^ {n}} + a _ {n - 1} \frac {d ^ {n - 1} y}{d t} + \dots + a _ {1} \frac {d y}{d t} + a _ {0} y = k _ {0} u \tag {10.1-1}
$$

或方程组

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + B \mathbf {u} \tag {10.1-2}
$$

方程式(10.1-1)内假定控制量仅有一个，而(10.1-2)内则假定有多个相互独立的控制量 $\boldsymbol{u}=(\boldsymbol{u}_{1},\boldsymbol{u}_{2},\cdots,\boldsymbol{u}_{r})$ 。根据第二章内的讨论知道，方程式(10.1-1)总可以化为一阶方程组

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + \boldsymbol {b} u, \quad \boldsymbol {b} = (b _ {1}, b _ {2}, \dots , b _ {n}) \tag {10.1-3}
$$

上式内矩阵 A 和向量 b 的每一个元素由方程式(10.1-1)的诸系数所单一确定，它们可以用比较系数法得到。

设控制量 $u(t)$ 是被第一类采样器件所调制出来的脉冲序列，如图 10.0-3(b)所示。设脉冲宽度为 $\gamma T, T$ 为脉冲重复周期，即采样周期， $0 < \gamma \leqslant 1$ 。我们先讨论高阶方程式(10.1-1)，即方程组(10.1-3)，并在 $0 \leqslant t \leqslant T$ 的时间内求解方程(10.1-3)。令 $\Phi(t) = e^{At}$ 为方程(10.1-3)的齐次方程组的基本解矩阵， $\Phi(0) = E$ 为单位矩阵。于是在 $t = T$ 这一时刻有

$$
\mathbf {y} (T) = e ^ {A T} \mathbf {y} (0) + \int_ {0} ^ {T} e ^ {A (T - \tau)} \boldsymbol {b u} (\tau) d \tau
$$

$$
\begin{array}{l} = e ^ {A T} \mathbf {y} (0) + \int_ {0} ^ {\gamma T} e ^ {A (T - \tau)} \mathbf {b u} (0) d \tau \\ = e ^ {A T} \mathbf {y} (0) + \left[ \int_ {0} ^ {\gamma T} e ^ {A (T - \tau)} \boldsymbol {b} d \tau \right] \cdot u (0) \\ \end{array}
$$

同样，如果以 $y(T)$ 作为新的初始条件，又可以求出在 t=2T 时刻的输出 $y(2T)$ 的值

$$
\mathbf {y} (2 T) = e ^ {A T} \mathbf {y} (T) + \left[ \int_ {0} ^ {\gamma T} e ^ {A (T - \tau)} \boldsymbol {b} d \tau \right] u (T)
$$

依此类推，若记

$$
\boldsymbol {c} = \int_ {0} ^ {\gamma T} e ^ {A (T - \tau)} \boldsymbol {b} d \tau , \quad D = e ^ {A T}
$$

则对任何 t = NT 有

$$
\mathbf {y} [ (N + 1) T ] = D \mathbf {y} (N T) + \mathbf {c u} (N T) \tag {10.1-4}
$$

这样，我们就得到了采样控制对象的第一种差分方程式。

如果矩阵 A 是可逆的, 向量 c 可以由下式算出

$$
\begin{array}{l} \boldsymbol {c} = e ^ {A T} \int_ {0} ^ {\gamma T} e ^ {- A \tau} \boldsymbol {b} d \tau \\ = e ^ {A T} \left[ \int_ {0} ^ {\gamma T} e ^ {- A \tau} d \tau \right] \boldsymbol {b} \\ = A ^ {- 1} \left(e ^ {A T} - e ^ {(1 - \gamma) A T}\right) \boldsymbol {b} \tag {10.1-5} \\ \end{array}
$$

当矩阵 A 为不可逆时, 上式依然有效, 此时应理解为

$$
\boldsymbol {c} = \left[ \gamma T E - \frac {1}{2 !} (\gamma T) ^ {2} A + \frac {1}{3 !} (\gamma T) ^ {3} A ^ {2} - \dots \right] e ^ {A T} \boldsymbol {b} \tag {10.1-6}
$$

显然，上式右端的级数对任何矩阵 A 总是收敛的，因而(10.1-5)内的向量 c 总有定义。

差分方程组(10.1-4)内的向量 $y=(y_{1},y_{2},\cdots,y_{n})$ 中的各分量是方程式(10.1-1)内受控量 y 的各阶导数和控制量 $u(t)$ 在 t=NT 时刻的值的线性组合。因此，它们代表受控对象的主要输出 $y_{1}=y$ 和它的各阶导数在各采样点的取值。如果我们只对系统的主要输出 $y(NT)$ 感兴趣的话，差分方程组(10.1-4)可以化为仅含有一个主要输出变数 $y_{1}$ 的高阶差分方程式。为此，我们想法消掉式(10.1-4)内除 $y_{1}$ 以外的其他变数。例如写出下列 $n^{2}$ 个方程式

$$
\mathbf {y} [ (N + 1) T ] = D \mathbf {y} (N T) + \mathbf {c u} (N T)
$$

$$
\mathbf {y} [ (N + 2) T ] = D \mathbf {y} [ (N + 1) T ] + \mathbf {c u} [ (N + 1) T ]
$$

$$
\dots
$$

$$
\mathbf {y} [ (N + n) T ] = D \mathbf {y} [ (N + n - 1) T ] + \mathbf {c u} [ (N + n - 1) T ]
$$

在 $n^{2}$ 个方程式中包括了 $y_{i}(NT)$ ， $y_{i}[(N+1)T]$ ， $\cdots$ ， $y_{i}[(N+n)T]$ ，i=1，2， $\cdots$ ，n 等 $(n+1)\cdot n=n^{2}+n$ 个未知量，从中消掉下列 $(n+1)(n-1)=n^{2}-1$

个量：

$$
\begin{array}{l} y _ {2} (N T), \dots , y _ {2} [ (N + n) T ] \\ y _ {3} (N T), \dots , y _ {3} [ (N + n) T ] \\ \dots \\ y _ {n} (N T), \dots , y _ {n} [ (N + n) T ] \\ \end{array}
$$

最后剩下一个方程式，其中仅含有 $y_{1}[(N+n)T],\cdots,y_{1}(NT)$ 等 $n+1$ 个量。由于矩阵 D 的特性，这种消除是可能的。这样消掉的结果便得到一个 n 阶差分方程，其内只包括系统的主要受控量 $y_{1}=y$ ,它的形式是

$$
\begin{array}{l} y [ (N + n) T ] + e _ {1} y [ (N + n - 1) T ] + \dots + e _ {n} y (N T) \\ = f _ {1} u [ (N + n - 1) T ] + f _ {2} u [ (N + n - 2) T ] + \dots + f _ {n} u (N T) \tag {10.1-7} \\ \end{array}
$$

式中诸系数 $e_{1}, \cdots, e_{n}; f_{1}, \cdots, f_{n}$ 为常量，它们是由矩阵 D 和向量 c 的元素所单一确定的。于是，我们又得到另一种只含主要输出变量的差分方程式。这种方程式常称为 n 阶线性差分方程式。我们可以看到，高阶差分方程式(10.1-7)与差分方程组(10.1-4)是等价的。

在实际工作中常可采用差分方程式的第三种形式。引进符号

$$
\Delta y (N T) = y [ (N + 1) T ] - y (N T)
$$

$$
\begin{array}{l} \Delta^ {2} y (N T) = \Delta y [ (N + 1) T ] - \Delta y (N T) \\ = y [ (N + 2) T ] - 2 y [ (N + 1) T ] + y (N T) \\ \dots \\ \end{array}
$$

$$
\Delta^ {n} y (N T) = \sum_ {i = 0} ^ {n} (- 1) ^ {n - i} C _ {n} ^ {i} y [ (N + i) T ] \tag {10.1-8}
$$

式中 $C_{n}^{i}$ 为 n 对 i 的组合数

$$
C _ {n} ^ {i} = \frac {n (n - 1) \cdots (n - i + 1)}{i !} = \frac {n !}{i ! (n - i) !}
$$

从式(10.1-8)内解出 $y(iT)$ 代入式(10.1-7)后就得到差分方程式的另一种形式

$$
\begin{array}{l} g _ {0} \Delta^ {n} y (N T) + g _ {1} \Delta^ {n - 1} y (N T) + \dots + g _ {n} y (N T) \\ = h _ {1} \Delta^ {n - 1} u (N T) + h _ {2} \Delta^ {n - 2} u (N T) + \dots + h _ {n} u (N T) \tag {10.1-9} \\ \end{array}
$$

式中 $g_{0}, g_{1}, \cdots, g_{n}; h_{1}, h_{2}, \cdots, h_{n}$ 均为常量，它们为(10.1-7)内的诸系数 $e_{i}$ 和 $f_{j}$ 所单值确定。不难看出差分方程式(10.1-9)与(10.1-7)是相互等价的，两者可以按关系式(10.1-8)互化，因此式(10.1-9)与(10.1-4)也等价。

最后，式(10.1-7)还可以写成另一种形式。引进新变量， $y_{1}(NT)=y(NT)$ ，并设符号 H 表示移位算子，即 $Hy_{i}(NT)=y_{i}[(N+1)T]$ ，那么，方程式(10.1-7)可以化为新的方程组

$$
H y _ {1} (N T) = y _ {2} (N T) + b _ {1} u (N T)
$$

$$
H y _ {2} (N T) = y _ {3} (N T) + b _ {2} u (N T)
$$

$$
\dots
$$

$$
H y _ {n} (N T) = - a _ {n} y _ {1} (N T) - a _ {n - 1} y _ {2} (N T) - \dots - a _ {1} y _ {n} (N T) + b _ {n} u (N T) \tag {10.1-10}
$$

式中各系数为方程式(10.1-7)的各系数所单一确定。

若令

$$
\mathbf {y} = \left(y _ {1}, \dots , y _ {n}\right)
$$

$$
\boldsymbol {c} = \left(b _ {1}, \dots , b _ {n}\right)
$$

$$
A = \left( \begin{array}{c c c c c c} 0 & 1 & 0 & 0 & \dots & 0 \\ 0 & 0 & 1 & 0 & \dots & 0 \\ \vdots & \vdots & \vdots & \vdots & & \vdots \\ - a _ {n} & - a _ {n - 1} & - a _ {n - 2} & - a _ {n - 3} & \dots & - a _ {1} \end{array} \right)
$$

则上式又可以写成向量形式

$$
H \mathbf {y} (N T) = A \mathbf {y} (N T) + \mathbf {c u} (N T) \tag {10.1-11}
$$

这就得到了描绘采样系统的第四种差分方程式。方程式(10.1-11)虽然形式上与式(10.1-4)相同，但是实际上完全是两回事。因为式(10.1-11)y 的各分量是主输出量 y 和控制量 u 在各个不同采样时刻的值，而方程式,(10.1-4)的各分量是由主输出量 y 和控制量 u 的各阶导数所构成。所以方程式(10.1-4)和(10.1-11)是截然不同的两类方程式。但是，从描述采样系统的运动规律这一意义来看，他们是等价的，是可以互化的。

这样，我们讨论了描述采样系统的四种差分方程，它们是式(10.1-4),(10.1-7),(10.1-9)和(10.1-11)。在实际工作中究竟采用何种形式，要由具体情况而定。从原理上来看，它们都可以作为对采样系统分析或综合的基础。

现举例以说明这四种方程式的求法。设连续受控对象的方程式是

$$
\frac {d ^ {3} y}{d t ^ {3}} + a _ {1} \frac {d ^ {2} y}{d t ^ {2}} + a _ {2} \frac {d y}{d t} + a _ {3} y = k _ {1} \frac {d ^ {2} u}{d t ^ {2}} + k _ {2} \frac {d u}{d t} + k _ {3} u \tag {10.1-12}
$$

令 $y=y_{1}$ ，于是式(10.1-12)可写为方程组

$$
\frac {d y _ {1}}{d t} = y _ {2} + b _ {1} u
$$

$$
\frac {d y _ {2}}{d t} = y _ {3} + b _ {2} u
$$

$$
\frac {d y _ {3}}{d t} = - a _ {3} y _ {1} - a _ {2} y _ {2} - a _ {1} y _ {3} + b _ {3} u
$$

式中 $b_{1}=k_{1}$ ， $b_{2}=k_{2}-a_{1}k_{1}$ ， $b_{3}=k_{3}+a_{1}^{2}k_{1}-a_{2}k_{1}-a_{1}k_{2}$

令

$$
\boldsymbol {b} = \left(b _ {1}, b _ {2}, b _ {3}\right)
$$

$$
\mathbf {y} = \left(y _ {1}, y _ {2}, y _ {3}\right)
$$

$$
A = \left( \begin{array}{c c c} 0 & 1 & 0 \\ 0 & 0 & 1 \\ - a _ {3} & - a _ {2} & - a _ {1} \end{array} \right)
$$

则上式可以写成向量等式

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + \boldsymbol {b u}
$$

设 $u(t)$ 为第一类采样元件（图 10.0-3b)所调制, 则第一种差分方程是

$$
\mathbf {y} [ (N + 1) T ] = D \mathbf {y} (N T) + \mathbf {c u} (N T) \tag {10.1-13}
$$

式中

$$
D = e ^ {A T}, \quad \boldsymbol {c} = A ^ {- 1} (e ^ {A T} - e ^ {A T (1 - v t)}) \boldsymbol {b}
$$

第二种差分方程是

$$
y [ (N + 3) T ] + e _ {1} y [ (N + 2) T ] + e _ {2} y [ (N + 1) T ] + e _ {3} y (N T)
$$

$$
= f _ {1} u [ (N + 2) T ] + f _ {2} u [ (N + 1) T ] + f _ {3} u (N T) \tag {10.1-14}
$$

第三种差分方程是

$$
g _ {0} \Delta^ {3} y (N T) + g _ {1} \Delta^ {2} y (N T) + g _ {2} \Delta y (N T) + g _ {3} y (N T)
$$

$$
= h _ {1} \Delta^ {2} u (N T) + h _ {2} \Delta u (N T) + h _ {3} u (N T) \tag {10.1-15}
$$

式中

$$
g _ {0} = 1, \quad g _ {1} = 3 + e _ {1}, \quad g _ {2} = 3 + 2 e _ {1} + e _ {2}, \quad g _ {3} = 1 + e _ {1} + e _ {2} + e _ {3}
$$

$$
h _ {1} = f _ {1}, \quad h _ {2} = 2 f _ {1} + f _ {2}, \quad h _ {3} = f _ {1} + f _ {2} + f _ {3}
$$

再令 $y_{1}(NT)=y(NT)$ ，式(10.1-14)又可写成

$$
H y _ {1} (N T) = y _ {2} (N T) + c _ {1} u (N T)
$$

$$
H y _ {2} (N T) = y _ {3} (N T) + c u (N T)
$$

$$
H y _ {3} (N T) = - d _ {3} y _ {1} (N T) - d _ {2} y _ {2} (N T) - d _ {1} y _ {3} (N T) + c _ {3} u (N T) \tag {10.1-16}
$$

式中

$$
c _ {1} = f _ {1}, \quad c _ {2} = f _ {2} - e _ {1} f _ {1}, \quad c _ {3} = f _ {3} + e _ {1} ^ {2} f _ {1} - e _ {2} f _ {1} - e _ {1} f _ {2}
$$

$$
d _ {1} = e _ {1}, \quad d _ {2} = e _ {2}, \quad d _ {3} = e _ {3}
$$

这就得到了第四种差分方程组

$$
H \mathbf {y} (N T) = A \mathbf {y} (N T) + \mathbf {c u} (N T) \tag {$10.1-16^{\prime$}}
$$

式中

$$
A = \left[ \begin{array}{c c c} 0 & 1 & 0 \\ 0 & 0 & 1 \\ - d _ {3} & - d _ {2} & - d _ {1} \end{array} \right], \quad \boldsymbol {c} = (c _ {1}, c _ {2}, c _ {3})
$$

对于有多个控制量的系统，差分方程式(10.1-2)的建立方法是完全类似的。相应的向量方程式的形式是

$$
\mathbf {y} [ (N + 1) T ] = D \mathbf {y} (N T) + C \mathbf {u} (N T) \tag {10.1-17}
$$

式中

$$
D = e ^ {A T}, \quad C = (e ^ {A T} - e ^ {A T (1 - \gamma)}) A ^ {- 1} B
$$

这里与式(10.1-4)所不同的是 C 是 $n \times r$ 阶矩阵，u 是 r 维向量，而式(10.1-4)内的 c 是一个 n 维向量，u 是一维控制量。用前面叙述过的方法可以类似地得到具有多个控制量的第二种至第四种差分方程式，只不过后者的具体形式略有变化罢了。上述的第一、第二和第四种差分方程式以后都将在不同的场合分别采用。

用差分方程式描绘采样系统时，我们只能得到输出变量在各采样时刻的取值变化规律。至于在两个采样时刻的中间输出量的变化情况从上列任何一种差分方程式的解中都得不到任何解答。但是采样系统的输出量恰恰是连续变化的，这与输入量或控制量的脉冲序列完全不同，后者本身是不连续的信号，而前者本来是连续变化的，只是为了信息处理的方便，我们才人为地取其在采样点的值加以研究。为了更全面地了解输出量的变化情况，可以将前述各差分方程改写，使其所描绘的输出量（受控量）的值不在采样点上，而在采样点的中间，或者说，使差分方程的解，表示受控量 y 在 $t=\varepsilon T, T+\varepsilon T, 2T+\varepsilon T, \cdots, NT+\varepsilon T, \cdots$ 等时刻的值。

设 $0 \leqslant \varepsilon \leqslant \gamma$ ，那么根据式(10.1-2)有

$$
\mathbf {y} (\varepsilon T) = e ^ {A \varepsilon T} \mathbf {y} (0) + e ^ {A \varepsilon T} \int_ {0} ^ {\varepsilon T} e ^ {- A \tau} B \mathbf {u} (0) d \tau
$$

$$
\mathbf {y} (T + \varepsilon T) = e ^ {A T} \mathbf {y} (\varepsilon T) + e ^ {A T} \int_ {0} ^ {(\gamma - \varepsilon) T} e ^ {- A \tau} B \mathbf {u} (0) d \tau + e ^ {A \varepsilon T} \int_ {0} ^ {\varepsilon T} e ^ {- A \tau} B \mathbf {u} (T) d \tau
$$

依此类推，可以得到

$$
\mathbf {y} [ (N + 1 + \varepsilon) T ] = D \mathbf {y} [ (N + \varepsilon) T ] + B _ {1} (\varepsilon) \mathbf {u} (N T) + B _ {2} (\varepsilon) \mathbf {u} [ (N + 1) T ] \tag {10.1-18}
$$

式中

$$
D = e ^ {A T}, \quad B _ {1} (\varepsilon) = e ^ {A T} \int_ {0} ^ {(\gamma - \varepsilon) T} e ^ {- A \tau} B d \tau , \quad B _ {2} (\varepsilon) = e ^ {A \varepsilon T} \int_ {0} ^ {\varepsilon T} e ^ {- A \tau} B d \tau
$$

当 $\gamma < \varepsilon \leqslant 1$ 时，则有

$$
\mathbf {y} [ (N + 1 + \varepsilon) T ] = D \mathbf {y} [ (N + \varepsilon) T ] + B _ {3} (\varepsilon) \mathbf {u} [ (N + 1) T ] \tag {10.1-19}
$$

式中

$$
B _ {3} (\varepsilon) = e ^ {A \varepsilon T} \int_ {0} ^ {\varepsilon T} e ^ {- A \tau} B d \tau
$$

从式(10.1-18)和(10.1-19)内可以看出；当输出量的采样时刻与输入量的采样时刻不同时，差分方程式的形式也不相同。与(10.1-17)比较这种差别就一目了然了。根据式(10.1-18)和(10.1-19)又可以推出第二种至第四种差分方程式， 如式 $(10.1-7)$ ， $(10.1-9)$ 和 $(10.1-11)$ 那样。

讨论上面的采样系统时，我们假定脉冲调制后的每一个脉冲是方形的，其高度仅与输入量 $g(t)$ 在采样时刻的值有关（图 10.0-3b)。有时为了更好地逼近输入信号，脉冲元件的调制规律可采用一次线性外插，输出端的脉冲序列中的每一脉冲均为“斜顶”，它的形状如图 10.1-1 所示。脉冲顶部的斜率与相邻两个采样时刻的输入信号 $g(NT)$ 和 $g[(N - 1)T]$ 的连线斜率相同，此时第一种差分方程式将具有下列形式

$$
\mathbf {y} [ (N + 1) T ] = D \mathbf {y} (N T) + B _ {1} \mathbf {u} (N T) + B _ {2} \mathbf {u} [ (N - 1) T ] \tag {10.1-20}
$$

式中

$$
D = e ^ {A T}, \quad B _ {1} = e ^ {A T} \int_ {0} ^ {\gamma T} e ^ {- A \tau} B \left(1 + \frac {\tau}{T}\right) d \tau
$$

$$
B _ {2} = - e ^ {A T} \int_ {0} ^ {\gamma_ {T}} e ^ {- A \tau} B \cdot \frac {\tau}{T} d \tau
$$

以式(10.1-20)做基础可以推出其他几种差分方程式。由此我们看到，图 10.1-1 所示的调制方式是线性的。

本节内讨论过的方法同样适用于变系数系统。如果受控对象是由变系数常微分方程所描绘，那么相应的差分方程式也是具有变系数的线性方程。例如式(10.1-17)此时变为

$$
\mathbf {y} [ (N + 1) T ] = D (N T) \mathbf {y} (N T) + C (N T) \mathbf {u} (N T) \tag {10.1-21}
$$

式中矩阵 $D(NT)$ 和 $C(NT)$ 的每一元素是时间的函数。这两个矩阵的求算公式与式(10.1-17)内的矩阵求法相同，只需将 $e^{AT}$ 换为变系数系统的基本解矩阵 $\Phi(t, t+T)$ 即可，此处 $t=0, T, 2T, \cdots, NT, \cdots$ 。

> 此处省略原书 **图 10.1-1**

前面讨论中的输出向量 y 是离散系统的状态向量。为了设计控制规律 $u(t)$ 当然要不间断地对系统的状态进行测量。然而并不是状态向量的每一个坐标在 实际上都可以直接用传感器或测量装置测出。这和连续系统中的情况完全类似，能够测到的关于系统状态的信息往往必须通过某种函数关系表达出来。最典型的例子是用雷达测量运动物体的坐标，雷达测得的数据要经换算后才能求出运动体的坐标，这在本书的前几章已经提到过。一般来讲，假定测量装置可以直接测到 m 个参数： $z_{1}, z_{2}, \cdots, z_{m}$ ，用向量 z 表示，称为离散系统的观测向量。观测向量 z 和状态向量 y 之间的函数关系可表示成

$$
\mathbf {z} (N T) = \mathbf {f} (\mathbf {y} (N T), N T) \tag {10.1-22}
$$

式中 f 为 m 维的非线性向量函数。由于通常能够观测到的参数 $z_{1}, \cdots, z_{m}$ 的个数小于状态向量的维数，也就是说，在每一瞬间不能由关系式(10.1-22)反解出 $y(NT)$ 来。即使向量函数 f 的 m 个分量都是相互独立的，这在实际问题中是最常见的情况。在简单的情况下，观测方程(10.1-22)右端是状态变量的线性函数，此时用 $F(NT) = (f_{ij}(NT))$ 表示 $m \times n$ 阶长方矩阵，它的每一元素 $f_{ij}(nT)$ 是时间 t 的函数。于是观测方程变为

$$
\mathbf {z} (N T) = F (N T) \mathbf {y} (N T) \tag {10.1-23}
$$

另一方面，当函数关系式(10.1-22)中的 f 是各自变量的足够光滑的函数，而且 $F(0, NT)=0$ ，那么在小范围内可以将函数 f 按泰勒级数展开，只保留展式中的线性项，忽略高次项，线性表达式(10.1-23)将在一定程度上逼近式(10.1-22)。因此，线性观测方程对研究非线性观测问题也是有意义的。由这种方程描述的测量装置也有人称之为观测器。

归纳上述，一个离散线性系统的完整的方程式将由受控对象的运动方程式和观测方程式两者所组成

$$
\mathbf {y} ((N + 1) T) = D (N T) \mathbf {y} (N T) + C (N T) \mathbf {u} (N T)
$$

$$
\mathbf {z} (N T) = F (N T) \mathbf {y} (N T) \tag {10.1-24}
$$

我们称方程(10.1-24)为离散系统的完全描述模型。

#### 10.2 差分方程式解的特性

前节内我们讨论了各种差分方程式的建立方法和运算步骤。本节内我们将讨论各种差分方程的特解和通解的特性。对这些特性的讨论将有助于对离散系统运动规律的细致了解，同时对离散系统的分析和综合将提供足够的理论基础。四种差分方程式中，我们将重点讨论第一种式(10.1-4)、第二种式(10.1-7)和第四种式(10.1-11)，因为这几种在实际工作中使用最广泛，应用也较方便。其中第一种和第四种，即式(10.1-4)和式(10.1-11)，虽然物理意义不同，但数学结构却完全相同，它们的通解和特解的性质也完全一致。所以我们先讨论第一种，然后再讨论第二种。

第一种差分方程是

$$
H \mathbf {y} (N T) = D \mathbf {y} (N T) + C \mathbf {u} (N T) \tag {10.2-1}
$$

式中符号 $H$ 表示移位算子，其作用规律是 $Hy(NT) = y[(N + 1)T]$ ， $D$ 和 $C$ 为常量矩阵。如果 $D$ 和 $C$ 是时间 $NT$ 的函数则系统变成变系数系统，但下面得到的很多结论略作修改后将完全适用于这种变系数离散系统。式(10.2-1)内 $\pmb{u}(NT)$ 为控制向量，它的每一个分量 $w_i(NT)$ 是相互独立的控制量，如果控制量只有一个，则 $\pmb{u}(NT)$ 只包含一个分量，而矩阵 $C$ 则变为一个向量 $\pmb{c}$ 。

当式(10.2-1)之右端 $u(NT) \equiv 0$ 时, 方程式

$$
H \mathbf {y} (N T) = D \mathbf {y} (N T) \tag {10.2-2}
$$

称为式 $(10.2-1)$ 的齐次方程式。

齐次线性差分方程式的解与齐次线性常微分方程式的解有很多共同的特点。如果式(10.2-2)是由 n 个方程式组成，则必有 n 个线性不相关的特解，而且只有 n 个这种解，任何其他解均可用这 n 个“基本解”的线性组合表示出来。设这 n 个线性不相关的解已经找到，它们是

$$
\begin{array}{l} \mathbf {y} _ {1} (N T) = \left(y _ {1 1} (N T), y _ {2 1} (N T), \dots , y _ {n 1} (N T)\right) \\ \mathbf {y} _ {2} (N T) = \left(y _ {1 2} (N T), y _ {2 2} (N T), \dots , y _ {n 2} (N T)\right) \\ \dots \\ \mathbf {y} _ {n} (N T) = \left(y _ {1 n} (N T), y _ {2 n} (N T), \dots , y _ {n n} (N T)\right) \\ \end{array}
$$

由于对任何 $t=NT, N=0,1,2,\cdots$ ，上述 n 个解线性不相关，那么，由它们所构成的行列式对任何 NT 总不为零。于是，对式(10.2-2)的任何特解 $y(NT)$ 存在一组常数 $c_{1}, c_{2}, \cdots, c_{n}$ ，使

$$
\mathbf {y} (N T) = c _ {1} \mathbf {y} _ {1} (N T) + c _ {2} \mathbf {y} _ {2} (N T) + \dots + c _ {n} \mathbf {y} _ {n} (N T)
$$

而这 n 个基本解是什么呢？从原则上看任何 n 个线性不相关的解均可成为基本解。现在我们只选择一种，作为以后讨论的基础。

由于式(10.2-2)内的 $D=e^{AT}$ ，A 是描述连续受控对象的常微分方程中的矩阵，故矩阵 D 的行列式永不为零。现在证明，式(10.2-2)的 n 个基本解是矩阵 $D^{N}=e^{NAT}$ 的几个列向量。显然，矩阵 $D^{N}$ 满足方程式(10.2-2)，因为

$$
H D ^ {N} = D D ^ {N} = D ^ {N + 1}
$$

于是

$$
\begin{array}{l} \mathbf {y} _ {1} (N T) = \left(D ^ {N}\right) _ {1} = \left(e ^ {N A T}\right) _ {1} \\ \dots \\ \mathbf {y} _ {n} (N T) = \left(D ^ {N}\right) _ {n} = \left(e ^ {N A T}\right) _ {n} \tag {10.2-3} \\ \end{array}
$$

上式右端的右下角注 $i, i=1,2,\cdots,n$ 表示矩阵的第 i 列向量。或者用 $Y(NT)$ 表示式 (10.2-2) 的基本解矩阵，有

$$
Y (N T) = D ^ {N} = e ^ {N A T} = \left(\mathbf {y} _ {1} (N T), \dots , \mathbf {y} _ {n} (N T)\right)
$$

$$
\begin{array}{l} y _ {1 1} (N T) \dots y _ {1 n} (N T) \\ = \left( \begin{array}{c c c} y _ {2 1} (N T) & \dots & y _ {2 n} (N T) \\ \vdots & & \vdots \\ y _ {n 1} (N T) & \dots & y _ {n n} (N T) \end{array} \right) \\ \end{array}
$$

上式左边的矩阵的第一列是 $y_{1}(NT)$ 的各分量，第二列是 $y_{2}(NT)$ 的分量，如此等。由于 A 是已知矩阵，故 $D=e^{AT}$ 也为已知，则式 (10.2-2) 的基本解矩阵 $D^{N}=e^{NAT}$ 马上可以算出。再由于矩阵 D 是非蜕化的，即 $|D|\neq0$ ，那么，它的任何次整数幂都不为零。因此，基本解矩阵 $D^{N}=Y(NT)$ 对任何 N 均为非蜕化，而式 (10.2-3) 内的 n 个解对任何 NT 是线性不相关的。

设受控对象的 n 个初始条件是 $\boldsymbol{c}=(c_{1},\cdots,c_{n})$ ，即 $y_{1}(0)=c_{1},y_{2}(0)=c_{2},\cdots,y_{n}(0)=c_{n}$ ，或者 $\boldsymbol{y}(0)=\boldsymbol{c}_{0}$ 。那么，满足这一组初始条件的式(10.2-2)的特解将是

$$
\mathbf {y} (N T) = e ^ {N A T} \mathbf {c} = D ^ {N} \mathbf {c} = D ^ {N} \mathbf {y} (0) \tag {10.2-4}
$$

事实上

$$
H \mathbf {y} (N T) = D D ^ {N} \mathbf {c} = D ^ {N + 1} \mathbf {c} = \mathbf {y} [ (N + 1) T ]
$$

而且， $y(0)=D^{0}c=c$ 。因为按矩阵函数的定义，任何矩阵的零次幂为单位矩阵。由于上述初始条件 c 是任意的，故式(10.2-4)称为齐次差分方程式(10.2-2)的通解。

现在求非齐次方程式(10.2-1)的通解，我们用待定系数法求解。设式(10.2-1)的通解为下列形式

$$
\mathbf {y} (N T) = Y (N T) \mathbf {c} (N T) = D ^ {N} \mathbf {c} (N T) \tag {10.2-5}
$$

式中 $\boldsymbol{c}(NT)=(c_{1}(NT),c_{2}(NT),\cdots,c_{n}(NT))$ 。令式(10.2-1)的初始条件为常向量 $y_{0}$ ，现求出满足这个初始条件的解式(10.2-5)。将式(10.2-5)代入式(10.2-1)后有

$$
\begin{array}{l} H \mathbf {y} (N T) = \mathbf {y} [ (N + 1) T ] \\ = Y [ (N + 1) T ] \boldsymbol {c} [ (N + 1) T ] \\ = D Y (N T) \boldsymbol {c} (N T) + C \boldsymbol {u} (N T) \\ = Y [ (N + 1) T ] \boldsymbol {c} (N T) + C \boldsymbol {u} (N T) \\ \end{array}
$$

移项后有

$$
\boldsymbol {c} [ (N + 1) T ] - \boldsymbol {c} (N T) = Y ^ {- 1} [ (N + 1) T ] C \boldsymbol {u} (N T)
$$

对上式两端求和得

$$
\boldsymbol {c} (m T) - \boldsymbol {c} (0) = \sum_ {N = 0} ^ {m - 1} Y ^ {- 1} [ (N + 1) T ] C \boldsymbol {u} (N T)
$$

将 $c(mT)$ 代入式(10.2-5)，并考虑 $y(0)=y_{0}$ ，最后得到

$$
\mathbf {y} (m T) = D ^ {m} \mathbf {y} _ {0} + D ^ {m} \sum_ {N = 0} ^ {m - 1} Y ^ {- 1} [ (N + 1) T ] C \mathbf {u} (N T)
$$

或者改写成

$$
\mathbf {y} (N T) = D ^ {N} \mathbf {y} _ {0} + \sum_ {m = 0} ^ {N - 1} D ^ {N - (m + 1)} C \mathbf {u} (m T) \tag {10.2-6}
$$

不难检查，式(10.2-6)满足方程式(10.2-1),并且同时满足初始条件 $y(0)=y_{0}$ 。推导时我们曾假定 $u(mT)$ 当 m<0 恒为零向量，因为控制作用是在 t=0 时开始作用的。这样，由于 $y_{0}$ 是任意的，式(10.2-1)的解式(10.2-6)我们将称为非齐次方程的通解。

其次，令向量函数 $\psi(NT)$ 是下列方程式

$$
H ^ {*} \boldsymbol {\psi} (N T) = \boldsymbol {\psi} [ (N - 1) T ] = D ^ {\tau} \boldsymbol {\psi} (N T) \tag {10.2-7}
$$

的基本解， $H^{*}$ 是逆移位算子，则

$$
\boldsymbol {\psi} (N T) = e ^ {- A ^ {\tau} N T} \boldsymbol {\psi} _ {0} = (D ^ {\tau}) ^ {- N} \boldsymbol {\psi} _ {0} \tag {10.2-8}
$$

是式(10.2-7)的解，其中 $\psi_{0}$ 为任意非零常向量，是式(10.2-7)的初始条件，因为

$$
H ^ {*} \boldsymbol {\psi} (N T) = H ^ {*} \left(D ^ {\tau}\right) ^ {- N} \boldsymbol {\psi} _ {0} = D ^ {\tau} \left(D ^ {\tau}\right) ^ {- N} \boldsymbol {\psi} _ {0} = \left(D ^ {\tau}\right) ^ {- (N - 1)} \boldsymbol {\psi} _ {0} = \boldsymbol {\psi} [ (N - 1) T ]
$$

不难看出，式(10.2-7)的任何非零解 $\psi(NT)$ 与齐次方程式(10.2-2)的任何非零解 $y(NT)$ 的内积为常数，而与 N 无关，因为

$$
\begin{array}{l} (\mathbf {y} [ (N + 1) T ], \boldsymbol {\psi} [ (N + 1) T ]) - (\mathbf {y} (N T), \boldsymbol {\psi} (N T)) \\ = \left(D ^ {N + 1} \boldsymbol {c}, \left(D ^ {\tau}\right) ^ {- (N + 1)} \boldsymbol {\psi} _ {0}\right) - \left(D ^ {N} \boldsymbol {c}, \left(D ^ {\tau}\right) ^ {- N} \boldsymbol {\psi} _ {0}\right) \\ = (\boldsymbol {c}, \boldsymbol {\psi} _ {0}) - (\boldsymbol {c}, \boldsymbol {\psi} _ {0}) = 0 \\ \end{array}
$$

故与齐次常微分方程相似，满足关系式

$$
(\boldsymbol {\psi} (N T), \mathbf {y} (N T)) = \text { const }
$$

的 $\psi (NT)$ 的方程组(10.2-7)称为式(10.2-2)的共轭方程组，有时也称其为伴随方程组。而 $\psi (NT)$ 则称为式(10.2-2)的共轭解。

设离散受控系统式(10.2-1)的初始条件为 $y_{0}$ ，在其输入端作用的 $u(NT)$ 不是控制量，而是扰动作用。那么，容易证明，由于扰动所引起的输出 $y(NT)$ 可以通过共轭方程式的解表示出来。首先写出下列恒等式

$$
\begin{array}{l} (\mathbf {y} [ (m + 1) T ], \boldsymbol {\psi} [ (m + 1) T ]) - (\mathbf {y} (m T), \boldsymbol {\psi} (m T)) \\ = (D \mathbf {y} (m T) + C \mathbf {u} (m T), (D ^ {\tau}) ^ {- 1} \boldsymbol {\psi} (m T)) - (\mathbf {y} (m T), \boldsymbol {\psi} (m T)) \\ = (C \boldsymbol {u} (m T), (D ^ {\tau}) ^ {- 1} \boldsymbol {\psi} (m T)) \\ \end{array}
$$

令 $N_{1}$ 为一固定正整数, 将上式两端对 m 求和后有

$$
(\mathbf {y} (N _ {1} T), \boldsymbol {\psi} (N _ {1}, T)) - (\mathbf {y} (0), \boldsymbol {\psi} (0))
$$

$$
= \sum_ {m = 0} ^ {N _ {1} - 1} (C u (m T), (D ^ {\tau}) ^ {- 1} \psi (m T)) \tag {10.2-9}
$$

设受控对象的初始条件为零, 即 $y_{0}=0$ , 再令 $\psi(N_{1}, T)=(1,0,0,\cdots,0)$ , 向量 $y(N_{1}T)$ 的第一个坐标 $y_{1}$ 在 $N_{1}T$ 时刻由扰动所积累的值将为

$$
y _ {1} \left(N _ {1} T\right) = \sum_ {m = 0} ^ {N _ {1} - 1} \left(C u (m T), \left(D ^ {\tau}\right) ^ {- 1} \psi (m T)\right) \tag {10.2-10}
$$

等式(10.2-9)称为格林公式，而式(10.2-10)是它的一个特殊形式。利用式(10.2-10)常可简单地求出系统受干扰后在指定时间间隔内所积累的输出误差。

至于第二种差分方程(10.1-7)，因为它可以化成第四种方程，所以上面讨论中所得到的一些结论对它也完全有效。这里只简单地列举有关方程式(10.1-7)的一些特性，而不再重复前面的证明。方程(10.1-7)内若 $u(NT)\equiv0$ ，则

$$
y [ (N + n) T ] + e _ {1} y [ (N + n - 1) T ] + \dots + e _ {n} y (N T) = 0 \tag {10.2-11}
$$

称为它的齐次差分方程式。n 阶方程式(10.2-11)必有 n 个线性不相关的解 $y_{1}(NT)$ , $y_{2}(NT)$ , $\cdots$ , $y_{n}(NT)$ ，其中每一个均满足方程式(10.2-11)。根据方程(10.1-10)和(10.1-11)的特点可知，这 n 个线性不相关的解可以是矩阵

$$
D ^ {N} = \left( \begin{array}{c c c c c} 0 & 1 & 0 & \dots & 0 \\ 0 & 0 & 1 & \dots & 0 \\ \vdots & \vdots & \vdots & & \vdots \\ e _ {n} & e _ {n - 1} & e _ {n - 2} & \dots & e _ {1} \end{array} \right) ^ {N}
$$

内第一列的 n 个元素。齐次方程式(10.2-11)的通解可写成下列形式

$$
y (N T) = c _ {1} y _ {1} (N T) + c _ {2} y _ {2} (N T) + \dots + c _ {n} y _ {n} (N T)
$$

式中诸系数 $c_{i}$ 由 n 个初始条件 $y(0), y(T), \cdots, y[(n-1)T]$ 所单一决定。为了求出 n 个线性不相关的解，还可用另外的办法求出，令式(10.2-11)的解具有下列形式： $y(NT)=\lambda^{N}$ ，代入原式并化简后得到一个 n 阶代数方程

$$
\lambda^ {n} + e _ {1} \lambda^ {n - 1} + e _ {2} \lambda^ {n - 2} + \dots + e _ {n - 1} \lambda + e _ {n} = 0 \tag {10.2-12}
$$

它是式(10.2-11)的特征方程。由于上式是 n 阶的，故有 n 个根 $\lambda_{1}, \lambda_{2}, \cdots, \lambda_{n}$ 。如果它们之间没有重根，则 n 个线性不相关的解便是

$$
y _ {1} (N T) = \lambda_ {1} ^ {N}, y _ {2} (N T) = \lambda_ {2} ^ {N}, \dots , y _ {n} (N T) = \lambda_ {n} ^ {N}
$$

容易看出，它们是线性不相关的。

如果特征方程式的根中有复根，则一定成双共轭出现，例如 $\lambda_{1}=\rho(\cos\omega+i\sin\omega)$ ， $\lambda_{2}=\rho(\cos\omega-i\sin\omega)$ 。那么，适当的选取 $c_{1}$ 和 $c_{2}$ ，可以使前两个基本解变为

$$
y _ {1} (N T) = \rho^ {N} \cos \omega N, \quad y _ {2} (N T) = \rho^ {N} \sin \omega N, \quad N = 0, 1, 2, \dots
$$

与常微分方程类似, 当 $\lambda$ 是重根时, 例如 s 次重根, 它所对应的 s 个线性不相关的解是

$$
y _ {1} (N T) = \lambda^ {N}, y _ {2} (N T) = N \lambda^ {N}, \dots , y _ {s} (N T) = N ^ {s - 1} \lambda^ {N}
$$

至于非齐次方程式的通解，仍可以利用式(10.2-6)的第一个分量等式写出。

前面的讨论中经常利用矩阵 $D^{N}$ 作为齐次方程组的基本解矩阵, 如何求出 $D^{N}$ 呢? 最简单的方法是把它写为连乘式 $D^{N}=DD\cdots D$ 逐步相乘 N 次算出。但是, 这样求不出 $D^{N}$ 的解析表达式。为了求出各基本解的解析表达式, 可以用矩阵函数 的方法进行。从代数学中我们知道，对任一矩阵 D, 总可以找到一个非蜕化矩阵 Q, 使

$$
J = Q ^ {- 1} D Q
$$

变为约当标准形。于是

$$
J ^ {\frac {t}{T}} = \left( \begin{array}{c c c c} J _ {1} ^ {\frac {t}{T}} & & & \\ & J _ {2} ^ {\frac {t}{T}} & & \\ & & \ddots & \\ & & & J _ {k} ^ {\frac {t}{T}} \end{array} \right), \quad t = 0, T, 2 T, \dots , N T
$$

其中 $J_{i}$ 是标准形内的标准块（约当块)。将每一个约当块展开后具有下列形式：

$$
J _ {i} ^ {\frac {t}{T}} = \left( \begin{array}{c c c c} \lambda_ {i} ^ {\frac {t}{T}} & \frac {t}{T} \lambda_ {i} ^ {\frac {t}{T} - 1} & \frac {1}{2}! \frac {t}{T} \bigg (\frac {t}{T} - 1 \bigg) \lambda_ {i} ^ {\frac {t}{T} - 2} & \dots \\ 0 & \lambda_ {i} ^ {\frac {t}{T}} & \frac {t}{T} \lambda_ {i} ^ {\frac {t}{T} - 1} & \dots \\ \vdots & \vdots & & \vdots \\ 0 & 0 & \dots & \lambda_ {i} ^ {\frac {t}{T}} \end{array} \right)
$$

矩阵 $J_{i}$ 的阶数决定于约当块的阶数, $\lambda_{i}$ 是矩阵 D 的特征根, 若 D 的 n 个特征根内无重根, 则

$$
J ^ {\frac {t}{T}} = \left( \begin{array}{c c c c c} \lambda_ {1} ^ {\frac {t}{T}} & 0 & 0 & \dots & 0 \\ 0 & \lambda_ {2} ^ {\frac {t}{T}} & 0 & \dots & 0 \\ \vdots & \vdots & \vdots & & \vdots \\ 0 & 0 & 0 & \dots & \lambda_ {n} ^ {\frac {t}{T}} \end{array} \right)
$$

由此便得到 $D^{\frac{t}{T}}$ 的解析表达式为

$$
D ^ {N} = Q J ^ {N} Q ^ {- 1}
$$

至于如何将矩阵 D 化为标准型, 即如何求出变换矩阵 Q, 在代数学中有详细讨论, 这里不再赘述。

下面我们把线性离散系统的通解式(10.2-6)推广到变系数线性系统，并且把通解的形式写得更简单些。首先记 $y(kT)=y(k)$ ，即省掉采样周期 T，仅用 k 表示 kT，用 l 表示 lT 等。设差分方程组(10.2-1)中的矩阵 D 和 C 不是常量矩阵，而是 t 的某一函数，那么方程式(10.2-1)就变为

$$
\mathbf {y} (k + 1) = D (k) \mathbf {y} (k) + C (k) \mathbf {u} (k) \tag {10.2-13}
$$

定义双变量函数 $\Phi (k,l)$

$$
\Phi (k, l) = \prod_ {i = l} ^ {k - 1} D (i), \quad \Phi (k, k) = E \tag {10.2-14}
$$

式中 E 为单位方阵。直接把上式代入式(10.2-13)的齐次方程中，极易检验，下列恒等式

$$
\Phi (k + 1, l) = D (k) \Phi (k, l) \tag {10.2-15}
$$

对一切正整数 k 和 $l, k \geqslant l$ ，都成立。而且 $\Phi(k, l)$ 还有下列特性

$$
\Phi^ {- 1} (k, l) = \Phi (l, k)
$$

$$
\Phi (k, m) \Phi (m, l) = \Phi (k, l) \tag {10.2-16}
$$

上式对一切正整数 k, l, m 都成立。利用函数矩阵 $\Phi(k, l)$ ，应用前面用过的待定系数法，线性变系数离散系统式(10.2-13)的通解可写成更为方便简捷的形式

$$
\mathbf {y} (k) = \Phi (k, l) \mathbf {y} (l) + \sum_ {i = l} ^ {k - 1} \Phi (k, i + 1) C (i) \mathbf {u} (i) \tag {10.2-17}
$$

不难检查, 当 l=0 和 D, C 是常矩阵时, 此式与式(10.2-6)完全重合。但是, 式(10.2-17)确定线性离散系统任何两个时刻 t=kT 和 $t^{\prime}=lT$ 的状态之间的关系, 所以这种写法往往更为方便。

本节讨论的内容是进一步研究系统分析和综合的基础。这里需要进行较复杂的计算工作是求出矩阵 D 和 C，因为要从常微分方程转变为差分方程的形式，需要找出常微分方程的基本解矩阵和通解表达式。为了做到这一点，我们还可以应用离散拉氏变换的方法。这种方法对常系数系统是很有效的，下一节内我们将进行详细的讨论。

得到线性离散系统通解的一般表达式以后，我们又可以讨论它的能控性和能观测性。和常微分方程描述的连续系统类似，设系统式(10.2-13)在 $t_{0}=l_{0}T$ 时刻的状态是 $y(l_{0}T)=y(l_{0})$ , 如果对任何初始状态都能找到一个控制 $u(iT)=u(i)$ , $i=l_{0},\cdots,k$ , 使 $y(k)=0$ , 则系统称为在 $l_{0}$ 时刻能控。如果该系统在任何时刻都是能控的, 则系统式(10.2-13)是完全能控的。

由式(10.2-17)可知，为了在 t=kT 时刻能使 $y(k)=0$ , 必须有

$$
\Phi (k, l _ {0}) \mathbf {y} (l _ {0}) = - \sum_ {i = l _ {0}} ^ {k - 1} \Phi (k, i + 1) C (i) \mathbf {u} (i) \tag {10.2-18}
$$

因为矩阵 $\Phi(k,l_{0})$ 是 $n\times n$ 阶满秩方阵， $y(l_{0})$ 是任意向量，故上式右端的一切可能的 n 维向量必须能充满整个空间；换言之，因为 $\Phi(k,l_{0})$ 是非蜕化方阵，上式等价于 n 个代数方程式构成的方程组，共有 $r(k-l_{0})$ 个未知量 $\{\boldsymbol{u}(l_{0}),\boldsymbol{u}(l_{0}+1),\cdots,\boldsymbol{u}(k-1)\}$ 。如果对任何给定的初始状态 $y(l_{0})$ ，都至少存在一组解 $\{\boldsymbol{u}(i)\}$ ，使等式 (10.2-18) 成立，则系统必是完全能控的。如果记

$$
T _ {k, l _ {0}} \boldsymbol {u} = \sum_ {i = l _ {0}} ^ {k - 1} \Phi (k, i + 1) C (i) \boldsymbol {u} (i)
$$

式中 $\widetilde{\boldsymbol{u}}=\left\{\boldsymbol{u}(l_{0}),\boldsymbol{u}(l_{0}+1),\cdots,\boldsymbol{u}(k-1)\right\}$ ，上述讨论要求算子 $T_{k,l_{0}}$ 是满秩的，或者说要求 $T_{k,l_{0}}T_{k,l_{0}}^{\tau}$ 是正定算子， $T_{k,l_{0}}^{\tau}$ 是 $T_{k,l_{0}}$ 的转置矩阵，即对任何非零 n 维向量 z

$$
\left(T _ {k, l _ {0}} T _ {k, l _ {0}} ^ {\tau} \mathbf {z}, \mathbf {z}\right) = \left(T _ {k, l _ {0}} ^ {\tau} \mathbf {z}, T _ {k, l _ {0}} ^ {\tau} \mathbf {z}\right) > 0
$$

把 $T_{k,l_0}T_{k,l_0}^{\tau}$ 展开得

$$
T _ {k, l _ {0}} T _ {k, l _ {0}} ^ {\tau} = \sum_ {i = l _ {0}} ^ {k - 1} \Phi (k, i + 1) C (i) C ^ {\tau} (i) \Phi^ {\tau} (k, i + 1) \tag {10.2-19}
$$

和连续系统一样，离散系统式(10.2-13)完全能控的充要条件是式(10.2-19)定义的算子对任何 $l_{0}$ 是正定的。

如果离散系统是常系数的，如式(10.2-1)所描述的系统为完全能控的充要条件是矩阵

$$
(C, D C, D ^ {2} C, \dots , D ^ {n - 1} C)
$$

的秩为 $n$ 。

设离散系统式(10.2-13)的观测方程是

$$
\mathbf {z} (k) = F (k) \mathbf {y} (k) \tag {10.2-20}
$$

系统式(10.2-13)和(10.2-20)在 $t_{0}=l_{0}$ T 时刻叫做能观测的，是指如果存在一个时刻 $t_{1}=kT$ ，由观测数据 $z(l_{0}), z(l_{0}+1), \cdots, z(k)$ 和控制信息 $u(l_{0}), \cdots, u(k)$ 可唯一地确定系统式(10.2-13)的初始状态 $y(l_{0})$ 。如果该系统在任何时刻都是能观测的，则称为完全能观测的。将式(10.2-17)代入式(10.2-20)后有

$$
\mathbf {z} (k) = F (k) \left[ \Phi (k, l _ {0}) \mathbf {y} (l _ {0}) + \sum_ {i = l _ {0}} ^ {k - 1} \Phi (k, i + 1) C (i) \mathbf {u} (i) \right]
$$

或者

$$
\boldsymbol {z} (k) - F (k) \sum_ {i = l _ {0}} ^ {k - 1} \Phi (k, i + 1) C (i) \boldsymbol {u} (i) = F (k) \Phi (k, l _ {0}) \boldsymbol {y} (l _ {0})
$$

依设，上式左端两项都是已知的 m 维向量, $m \leqslant n$ , n 是状态向量 y 的维数。将上式改写为

$$
\boldsymbol {x} (k) = F (k) \Phi (k, l _ {0}) \boldsymbol {y} (l _ {0})
$$

并展开

$$
\begin{array}{l} \boldsymbol {x} \left(l _ {0}\right) = F \left(l _ {0}\right) \boldsymbol {y} \left(l _ {0}\right) \\ \boldsymbol {x} (l _ {0} + 1) = F (l _ {0} + 1) \Phi (l _ {0} + 1, l _ {0}) \boldsymbol {y} (l _ {0}) \\ \dots \\ \boldsymbol {x} (k) = F (k) \Phi (k, l _ {0}) \boldsymbol {y} (l _ {0}) \\ \end{array}
$$

这里共有 $m(k+1)$ 个方程式，并且有 n 个未知量 $y(l_{0})=\left\{y_{1}(l_{0}),y_{2}(l_{0}),\cdots,y_{n}(l_{0})\right\}$ 。从代数学中我们知道，为了从上述方程组中解出这 n 个未知数，必须且只需存在一个 k 使下列矩阵的秩等于 n

$$
D _ {k, l _ {0}} = \left( \begin{array}{l} F (l _ {0}) \\ F (l _ {0} + 1) \Phi (l _ {0} + 1, l _ {0}) \\ \vdots \\ F (k) \Phi (k, l _ {0}) \end{array} \right) \tag {10.2-21}
$$

或者，完全等价地讲，必须且只需 $D_{k,l_{0}}^{\tau}D_{k,l_{0}}$ 是满秩的。

显然，为了使系统式(10.2-13)和(10.2-20)是完全能观测的，则要求对任何时刻 $i, l_{0} \leqslant i \leqslant k$ , 矩阵 $F(i) \Phi(i, l_{0})$ 的各列向量是线性独立的。对常系数系统，上述条件等价于下列矩阵

$$
\left( \begin{array}{c} F \\ F D \\ \vdots \\ F D ^ {n - 1} \end{array} \right)
$$

的秩等于 $n_{0}$

#### 10.3 离散拉氏变换与传递函数

第四章讨论过的拉氏变换方法对常系数微分方程的研究曾发挥了很大的作用。但是由于离散系统内自变量的断续性，那种方法不能直接应用到这里来。为了适应离散系统的特点，必须对拉氏变换的定义作必要的改变。在离散系统内，我们所研究的过程是一个函数序列 $u(NT)$ 或 $y(NT)$ 。一般来讲，我们只对这些变量在特定时刻的值感兴趣。为此，我们引进新定义。设 $y(NT)$ 是一个采样函数，或者说它是一个函数序列。复变函数

$$
Y ^ {*} (s) = \sum_ {N = 0} ^ {\infty} y (N T) e ^ {- N T s} \tag {10.3-1}
$$

称为采样函数的象函数，而 $y(NT)$ 称为 $Y^{*}(s)$ 的原函数。由原函数 $y(NT)$ 求象函数 $Y^{*}(s)$ 的运算称为离散拉氏变换，用符号 $L^{*}$ 表示。

并不是一切采样函数都可以进行拉氏变换的，只有使式(10.3-1)的右端级数收敛的那些采样函数才可能有自己的象函数。与第四章的讨论类似，对 $y(NT)$ 的要求是它的增长速度不大于某一指数函数，即它对任何 N 均应满足不等式

$$
\mid y (N T) \mid <   M e ^ {\sigma_ {0} N T}
$$

式中 $\sigma_{0}$ 为某一有限的正数, 称为 $y(NT)$ 的收敛横标。

离散拉氏变换具有连续拉氏变换的一切特性：

(1) 它是线性变换, 即

$$
\begin{array}{l} L ^ {*} \left[ a y _ {1} (N T) + b y _ {2} (N T) \right] = a L ^ {*} y _ {1} (N T) + b L ^ {*} y _ {2} (N T) \\ = a Y _ {1} ^ {*} (s) + b Y _ {2} ^ {*} (s) \\ \end{array}
$$

(2) 对自变数的推移公式为

$$
L ^ {*} y [ (N + k) T ] = e ^ {k T s} Y ^ {*} (s) - \sum_ {m = 0} ^ {k - 1} e ^ {(k - m) T s} y (m T) \tag {10.3-2}
$$

（3）对复变数的推移公式。设 $\lambda$ 为实数，则有

$$
L ^ {*} \left[ e ^ {\pm \lambda N T} y (N T) \right] = Y ^ {*} (s \mp \lambda) \tag {10.3-3}
$$

(4) 对差分的变换公式

$$
\begin{array}{l} L ^ {*} [ \Delta y (N T) ] = \sum_ {N = 0} ^ {\infty} [ y [ (N + 1) T ] - y (N T) ] e ^ {- N s T} \\ = (e ^ {T s} - 1) Y ^ {*} (s) - e ^ {s T} y (0) \tag {10.3-4} \\ \end{array}
$$

此外，下列几个公式在实际计算中很有用:

(5) $\frac{d^kY^*(s)}{ds^k} = (-1)^k L^*[ (NT)^k y (NT)]$ (10.3-5)

(6) $L^{*}\left[\sum_{m = 0}^{N}y_{1}(mT)y_{2}((N - m)T)\right] = Y_{1}^{*}(s)\bullet Y_{2}^{*}(s)$ (10.3-6)

(7) $Y^{*}(0) = \sum_{N = 0}^{\infty}y(NT)$ (10.3-7)

(8) $\lim_{N\to \infty}y(NT) = \lim_{s\to 0}(e^{sT} - 1)Y^{*}(s)$ (10.3-8)

(9) $y(0) = \lim_{s \to \infty} Y^{*}(s)$ (10.3-9)

当然式(10.3-7)只有当右端级数收敛时才有意义，而式(10.3-8)只有当 $y(NT)$ 确有极限时才能使用。(1)—(9)的正确性是容易检验的，此处不再赘述。下面列出一个小字典，以供查对，表内设 T=1。

$$
\begin{array}{l l} y (N) & Y ^ {*} (s) \\ 1 & \frac {e ^ {s}}{e ^ {s} - 1} \\ N & \frac {e ^ {s}}{(e ^ {s} - 1) ^ {2}} \\ N ^ {2} & \frac {e ^ {s} (e ^ {s} + 1)}{(e ^ {s} - 1) ^ {3}} \\ e ^ {a N} & \frac {e ^ {s}}{e ^ {s} - e ^ {a}} \\ N e ^ {a N} & \frac {e ^ {s} e ^ {a}}{(e ^ {s} - e ^ {a}) ^ {2}} \\ \cos a N & \frac {e ^ {2 s} - e ^ {s} \cos a}{e ^ {2 s} - 2 e ^ {s} \cos a + 1} \\ \sin a N & \frac {e ^ {s} \sin a}{e ^ {2 s} - 2 e ^ {s} \cos a + 1} \end{array}
$$

$$
\operatorname{ch} a N \quad \frac {e ^ {2 s} - e ^ {s} \operatorname{ch} a}{e ^ {2 s} - 2 e ^ {s} \operatorname{ch} a + 1}
$$

$$
\operatorname{sh} a N \quad \frac {e ^ {s} \operatorname{sh} a}{e ^ {2 s} - 2 e ^ {s} \operatorname{ch} a + 1}
$$

上面我们已经熟悉了如何从原函数求象函数的方法。下面再看看如何根据象函数求原函数。这种运算称为离散拉氏反变换，并用符号 $L^{*-1}$ 表示

$$
y (N T) = L ^ {* - 1} Y ^ {*} (s)
$$

不难证明，如果复变函数 $Y^{*}(s)$ 确实有自己的原函数，那么有（图 10.3-1)

$$
y (N T) = \frac {T}{2 \pi i} \int_ {c - i \frac {\pi}{T}} ^ {c + i \frac {\pi}{T}} Y ^ {*} (s) e ^ {N T s} d s \tag {10.3-10}
$$

> 此处省略原书 **图 10.3-1**

这个公式就是拉氏反变换公式，式中 c 为某一实数，它应大于 $Y^{*}(s)$ 的一切奇点的实部。反变换公式可用下法推得，将式(10.3-1)的两端乘以 $e^{mTs}$ 后，沿线段 $\left[c-\frac{i\pi}{T},c+\frac{i\pi}{T}\right]$ 积分

$$
\begin{array}{l} \int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} Y ^ {*} (s) e ^ {m T s} d s = \int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} \left(\sum_ {N = 0} ^ {\infty} y [ N T ] e ^ {- N s T}\right) e ^ {m T s} d s \\ = \sum_ {N = 0} ^ {\infty} y [ N T ] \int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} e ^ {- (N T - m T) s} d s \\ \end{array}
$$

积分与求和之所以能互换，是由于级数绝对收敛，因为沿积分路线上的 $\mathrm{Re}s > \sigma$ , 当 $N \neq m$ 时

$$
\int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} e ^ {- (N - m) T s} d s = \left[ \frac {- e ^ {- (N - m) T s}}{(N - m) T} \right] _ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} = 0
$$

当 N=m 时, 则有

$$
\int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} e ^ {- (N - m) T s} d s = \frac {2 i \pi}{T}
$$

由此，式 $(10.3-10)$ 便得到证明。

一般来讲，当 $Y^{*}(s)$ 为已知时；总可以按式(10.3-10)求出 $y(NT)$ 。当 $Y^{*}(s)$ 为 $e^{sT}$ 的有理分式时，一般可不直接计算积分式(10.3-10)，而是将 $Y^{*}(s)$ 化为有理最简分式，然后利用拉氏变换的线性特点，逐项去查表，按“字典”求出原函数，后面这一方法最为简便。

上面拉氏变换是指一个采样函数而言的。拉氏变换也可以对向量采样函数作用。对向量函数序列变换的定义与式(10.3-1)相同。令 $\mathbf{y}(NT)=(y_{1}(NT), y_{2}(NT), \cdots, y_{n}(NT))$ ，则

$$
\mathbf {Y} ^ {*} (s) = \sum_ {N = 0} ^ {\infty} \mathbf {y} [ N T ] e ^ {- N T s} = \left(Y _ {1} ^ {*} (s), Y _ {2} ^ {*} (s), \dots , Y _ {n} ^ {*} (s)\right) \tag {10.3-11}
$$

反变换公式为

$$
\mathbf {y} (N T) = \frac {T}{2 \pi i} \int_ {c - \frac {i \pi}{T}} ^ {c + \frac {i \pi}{T}} \mathbf {Y} ^ {*} (s) e ^ {N s T} d s \tag {10.3-12}
$$

不难看出，对向量函数序列的变换与对普通函数序列的变换本质上没有差别。前面列举过的性质式(10.3-2)至式(10.3-9)也依然有效。

讨论了拉氏变换的定义及公式后，现在可以建立传递函数的概念了。首先研究如何用拉氏变换的方法去求解第二种差分方程式。设差分方程式(10.1-7)的初始条件是 $y(0)$ , $y(T)$ , $y(2T)$ , $\cdots$ , $y[(n-1)T]$ ，对式(10.1-7)的两端进行拉氏变换。利用特性式(10.3-2)有

$$
\left(e ^ {n s T} + e _ {1} e ^ {(n - 1) s T} + \dots + e _ {n}\right) Y ^ {*} (s) = \left(f _ {1} e ^ {(n - 1) s T} + \dots + f _ {n}\right) U ^ {*} (s) + R ^ {*} (s)
$$

上式内 $R^{*}(s)$ 为 $e^{sT}$ 的多项式, 其诸系数由上述初始条件所确定。将上式移项后得

$$
Y ^ {*} (s) = \frac {Q ^ {*} (s)}{P ^ {*} (s)} U ^ {*} (s) + \frac {R ^ {*} (s)}{P ^ {*} (s)} \tag {10.3-13}
$$

上式右端包含两项，它们都是 $e^{sT}$ 的有理分式。第一项所确定的运动是由控制量 $u(NT)$ 所引起的，称为离散系统的强迫运动，第二项称为系统的特解，或称为系统的自由运动，它完全由系统的初始条件所决定，若初始条件均为零，则 $R^{*}=0$ 。令

$$
F ^ {*} (s) = \frac {Q ^ {*} (s)}{P ^ {*} (s)} \tag {10.3-14}
$$

$F^{*}(s)$ 称为输出 $y(NT)$ 对控制量 $u(NT)$ 的采样传递函数。换句话说，采样传递函数就是受控对象的初始条件（状态）为零时输出和输入拉氏变换之比。如果控制量 $u(NT)$ 的规律给定，则可用拉氏反变换法求出系统的受控运动 $y_{i}(NT)$ 。同样，当初始条件给定时， $R^{*}(s)$ 也即被确定，自由运动 $y_{c}(NT)$ 也就可以用拉氏反变换的方法求出。这样输出量

$$
y (N T) = y _ {i} (N T) + y _ {c} (N T)
$$

其中

$$
y _ {i} (N T) = L ^ {* - 1} \left[ F ^ {*} (s) U ^ {*} (s) \right]
$$

$$
y _ {c} (N T) = L ^ {* - 1} \left[ \frac {R ^ {*} (s)}{P ^ {*} (s)} \right]
$$

这种反变换可以先将复变函数 $F^{*}(s)U^{*}(s)$ 及 $\frac{R^{*}(s)}{P^{*}(s)}$ 分解为部分分式，再按字典去查出每一项的原函数，相加后便得到 $y(NT)$ 。如果方便的话也可以直接采用反变换公式(10.3-10)。

设在式(10.1-7)所代表的受控对象内引进负反馈（也称硬反馈)，使它变成闭路控制系统，如图 10.3-2 所示。系统的输入作用为 $g(t)$ ，它是连续函数。因为系统的输出 $y(t)$ 本来是连续函数，所以误差 $\varepsilon(t)=g(t)-y(t)$ 也是连续函数。只有经过采样装置的调制后 $u(NT)$ 才变为一个采样函数现试写出闭路系统的传递函数。根据图 10.3-2 当诸初始条件为零时离散系统的运动方程式为

$$
Y ^ {*} (s) = F ^ {*} (s) U ^ {*} (s)
$$

$$
U ^ {*} (s) = E ^ {*} (s)
$$

$$
E ^ {*} (s) = G ^ {*} (s) - Y ^ {*} (s)
$$

> 此处省略原书 **图 10.3-2**

从上列三式中消掉 $U^{*}(s)$ , $E^{*}(s)$ 后, 便得到

$$
Y ^ {*} (s) = \frac {F ^ {*} (s)}{1 + F ^ {*} (s)} G ^ {*} (s) \tag {10.3-15}
$$

这里的

$$
\Phi^ {*} (s) = \frac {F ^ {*} (s)}{1 + F ^ {*} (s)}
$$

称为闭路系统的传递函数。如果从前述三式中消掉 $Y^{*}(s)$ , $U^{*}(s)$ 后, 便得到

$$
E ^ {*} (s) = \frac {1}{1 + F ^ {*} (s)} G ^ {*} (s) \tag {10.3-16}
$$

其中

$$
\Phi_ {\varepsilon} ^ {*} (s) = \frac {1}{1 + F ^ {*} (s)}
$$

称为闭路系统对误差的传递函数。我们看到，离散系统的传递函数与第三章内的闭路传递函数的形式是完全类似的。

如果反馈回路中还包含另一个传递函数 $F_{1}^{*}(s)$ ，如图 10.3-3 所示，那么，对输出和误差的闭路传递函数将是

> 此处省略原书 **图 10.3-3**

$$
\Phi^ {*} (s) = \frac {F ^ {*} (s)}{1 + F ^ {*} (s) F _ {1} ^ {*} (s)}
$$

$$
\Phi_ {\varepsilon} ^ {*} (s) = \frac {1}{1 + F _ {1} ^ {*} (s) F ^ {*} (s)}
$$

由第一种和第四种差分方程组(10.1-4)和(10.1-11)可以确定与传递函数相类似的传递矩阵。我们将以式(10.1-17)为依据求传递矩阵。对式(10.1-17)的两端进行拉氏变换，移项整理后得到

$$
\mathbf {Y} ^ {*} (s) = \left(E e ^ {s T} - D\right) ^ {- 1} C \mathbf {U} ^ {*} (s) + \left(E e ^ {s T} - D\right) ^ {- 1} \mathbf {y} (0) \tag {10.3-17}
$$

上式 E 为单位矩阵，并假定 $\boldsymbol{u}(0)=\boldsymbol{0}$ 。矩阵函数

$$
F ^ {*} (s) = \left(E e ^ {s T} - D\right) ^ {- 1} C
$$

称为受控对象的传递矩阵。而式(10.3-17)的第二项决定系统的自由运动。如果用硬反馈（图 10.3-4)

> 此处省略原书 **图 10.3-4**

$$
\boldsymbol {u} (N T) = K [ \boldsymbol {g} (N T) - \boldsymbol {y} (N T) ]
$$

式中 K 为 $n \times r$ 阶矩阵, 则闭路运动方程式是

$$
\boldsymbol {Y} ^ {*} (s) = \boldsymbol {F} ^ {*} (s) \boldsymbol {U} ^ {*} (s)
$$

$$
\boldsymbol {U} ^ {*} (s) = K (\boldsymbol {G} ^ {*} (s) - \boldsymbol {Y} ^ {*} (s))
$$

消掉 $U^{*}(s)$ 后, 则有

$$
\boldsymbol {Y} ^ {*} (s) = \left(E + F ^ {*} (s) K\right) ^ {- 1} F ^ {*} (s) K \boldsymbol {G} ^ {*} (s) \tag {10.3-18}
$$

式中

$$
\Phi^ {*} (s) = \left(E + F ^ {*} (s) K\right) ^ {- 1} F ^ {*} (s) K
$$

称为闭路系统的传递矩阵。令 $E^{*}(s)=G^{*}(s)-Y^{*}(s)$ 为误差向量 $\varepsilon(NT)$ 的拉氏变换，不难推出

$$
\boldsymbol {E} ^ {*} (s) = \left(E + F ^ {*} (s) K\right) ^ {- 1} \boldsymbol {G} ^ {*} (s) = \Phi_ {\varepsilon} ^ {*} (s) \boldsymbol {G} ^ {*} (s) \tag {10.3-19}
$$

此处

$$
\Phi_ {\varepsilon} ^ {*} (s) = (E + F ^ {*} (s) K) ^ {- 1}
$$

称为对误差向量的传递矩阵。由式(10.3-18)和式(10.3-19)可以看到，方程组的传递矩阵与方程式的传递函数形式类似，只是由于两个矩阵一般没有互换性，故不能将它写成分式。

现令式(10.1-7)右端之控制量按余弦规律变化，即 $u(NT)=\cos\omega NT$ ，要求求出输出受控量 $y(NT)$ 的变化规律。为此，我们利用线性系统的叠加原理。假定 $u(NT)$ 由两部分组成，一部分是前面给定的 $u_{1}(NT)=\cos\omega NT$ ，另一部分是 $u_{2}(NT)=i\sin\omega NT$ 。两者的和是 $u(NT)=u_{1}(NT)+u_{2}(NT)=\cos\omega NT+i\sin\omega NT=e^{i\omega NT}, N=0,1,2,\cdots$ 。因为式(10.1-7)的诸系数均为实数，故对控制量 $u(NT)=e^{i\omega NT}$ 有两个独立（互不影响）的解，解的实函数部分对应 $u_{1}(NT)$ ，虚部则对应 $u_{2}(NT)$ 。于是求出系统对 $u(NT)$ 的响应后，便同时求出了两个特解，其实数部分恰恰是待求的特解。

设受控量的运动规律是 $A(i\omega)e^{i\omega NT}$ ，需要求出系数 $A(i\omega)$ 。将 $u=e^{i\omega NT}$ 和 $A(\omega)e^{i\omega NT}$ 代入式(10.1-7)之两端，消去不为零的因子 $e^{i\omega NT}$ 后，可以求得待求系数

$$
A (i \omega) = \frac {f _ {1} e ^ {i \omega (n - 1) T} + f _ {2} e ^ {i \omega (n - 2) T} + \cdots + f _ {n}}{e ^ {i \omega n T} + e _ {1} e ^ {i \omega (n - 1) T} + \cdots + e _ {n}} \tag {10.3-20}
$$

我们立刻看到， $A(i\omega)$ 不是别的，正是离散系统的传递函数式(10.3-14)，只不过将变数 s 换为 $i\omega$ 罢了。由此可知，式(10.1-7)对 $u=e^{i\omega NT}$ 的响应是

$$
y (N T) = F ^ {*} (i \omega) e ^ {i \omega N T} \tag {10.3-21}
$$

$F^{*}(i\omega)$ 称为采样频率特性。如果系统式(10.1-17)中的控制量是正弦函数

$$
\boldsymbol {u} (N T) = \left(b _ {1} e ^ {i \omega N T}, b _ {2} e ^ {i \omega N T}, \dots , b _ {n} e ^ {i \omega N T}\right)
$$

$$
= \boldsymbol {b e} ^ {i \omega N T} \tag {10.3-22}
$$

那么，输出向量 $\mathbf{y}(NT)=F^{*}(i\omega)\mathbf{b}e^{i\omega NT}$ , 式中

$$
F ^ {*} (i \omega) = (E e ^ {i \omega T} - D) ^ {- 1} C
$$

称为频率特性矩阵。

若图 10.3-2 所示之闭路系统的输入作用为 $g(t)=e^{i\omega t}$ ，那么，输出 $y(t)$ 在 $t=0, T, 2T, \cdots$ ，等采样点上的稳态值将是

$$
y (N T) = \Phi^ {*} (i \omega) e ^ {i \omega N T} = \frac {F ^ {*} (i \omega)}{1 + F ^ {*} (i \omega)} e ^ {i \omega N T} \tag {10.3-23}
$$

而误差

$$
\varepsilon (N T) = \Phi_ {\epsilon} ^ {*} (i \omega) e ^ {i \omega N T} = \frac {1}{1 + F ^ {*} (i \omega)} e ^ {i \omega N T} \tag {10.3-24}
$$

$\Phi^{*}(i\omega)$ 称为闭路系统输出对输入的采样频率特性, $\Phi^{*}(i\omega)$ 称为闭路系统误差采样频率特性。如果在式(10.1-17)所构成的闭路系统的输入端加上 $g(NT)=$

$g_{0}e^{i\omega t}$ ，则闭路系统的输出将是

$$
\mathbf {y} (N T) = \Phi^ {*} (i \omega) \mathbf {g} _ {0} e ^ {i \omega N T} = (E + F ^ {*} (i \omega) K) ^ {- 1} F ^ {*} (i \omega) K \mathbf {g} _ {0} e ^ {i \omega N T} \tag {10.3-25}
$$

误差向量的运动将是

$$
\begin{array}{l} \varepsilon (N T) = \Phi_ {\varepsilon} ^ {*} (i \omega) \mathbf {g} _ {0} e ^ {i \omega N T} \\ = (E + F ^ {*} (i \omega) K) ^ {- 1} \mathbf {g} _ {0} e ^ {i \omega N T} \tag {10.3-26} \\ \end{array}
$$

式中

$$
F ^ {*} (i \omega) = (E e ^ {i \omega T} - D) ^ {- 1} C
$$

复函数 $F^{*}(i\omega)$ 称为开路系统式(10.1-7)的采样频率特性。将 $F^{*}(i\omega)$ 写成 $K^{*}(\omega)e^{-i\theta^{*}(\omega)}$ 后，得到两个 $\omega$ 的实函数 $K^{*}(\omega)$ 和 $\theta^{*}(\omega)$ ，式(10.3-21)可以改写为

$$
y (N T) = K ^ {*} (\omega) e ^ {i (N T \omega - \theta^ {*} (\omega))} \tag {10.3-27}
$$

显然， $K^{*}(\omega)$ 表示输出运动的幅度， $\theta^{*}(\omega)$ 表示相位移动。因此， $K^{*}(\omega)$ 称为离散系统的幅频特性，而 $\theta^{*}(\omega)$ 称为它的相频特性。将式(10.3-27)分为实虚两部分后，便得到式(10.1-7)对 $\cos\omega NT$ 的响应

$$
y _ {1} (N T) = K ^ {*} (\omega) \cos (\omega N T - \theta^ {*} (\omega)) \tag {10.3-28}
$$

对式(10.3-22)进行同样的处理，便可得到系统式(10.1-17)的开路和闭路的幅频和相频特性矩阵。利用矩阵函数的运算规律即可求出，我们把它们的推导留给读者。

例.设连续受控对象的运动方程式是

$$
\frac {d ^ {2} y}{d t ^ {2}} = u \tag {10.3-29}
$$

脉冲元件是方波幅度调制，重复周期为 T=1,脉冲宽度为 $\gamma T,\gamma=1$ ,于是式(10.3-29)的开路传递函数是

$$
F ^ {*} (s) = \frac {\frac {1}{2} \left(e ^ {s} + 1\right)}{\left(e ^ {s} - 1\right) ^ {2}}
$$

其中各参数的值用 $i\omega$ 置换复变数 s 后, 便得到开路采样频率特性

$$
F ^ {*} (i \omega) = K ^ {*} (\omega) e ^ {+ i \theta^ {*} (\omega)}
$$

其中

$$
K ^ {*} (\omega) = \frac {1}{2 \sqrt {2}} \frac {\sqrt {\cos \omega + 1}}{\cos \omega - 1}
$$

$$
\theta^ {*} (\omega) = \tan^ {- 1} \frac {- \sin \omega}{1 + \cos \omega}
$$

这样，我们就不难画出频率特性了。用-1 作为系统的反馈，式(10.3-29)变为闭路系统，通过简单的计算，可以得出闭路传递函数。

$$
\Phi^ {*} (s) = \frac {\frac {1}{2} \left(e ^ {s} + 1\right)}{\left(e ^ {s} - 1\right) ^ {2} + \frac {1}{2} \left(e ^ {s} + 1\right)}
$$

$$
\Phi_ {\varepsilon} ^ {*} (s) = \frac {(e ^ {s} - 1) ^ {2}}{(e ^ {s} - 1) ^ {2} + \frac {1}{2} (e ^ {s} + 1)}
$$

其相应的频率特性为

$$
\Phi^ {*} (i \omega) = K ^ {*} (\omega) e ^ {+ i \theta^ {*} (\omega)}
$$

其中

$$
K ^ {*} (\omega) = \frac {\sqrt {1 2 \cos^ {3} \omega - \cos^ {2} \omega - 1 0 \cos \omega + 5}}{1 2 \cos^ {2} \omega - 1 5 \cos \omega + 5}
$$

$$
\theta^ {*} (\omega) = \tan^ {- 1} \frac {2 \sin \omega (1 - \cos \omega)}{2 \cos^ {2} \omega + \cos \omega - 1}
$$

当然，也可以画出闭路系统的频率特性。

上面我们讨论的传递函数都是以输出和输入量在采样点上， $t=0,T,2T,\cdots$ ，的值为依据的。如果我们关心的不是采样点的值，而是在两个采样点中间某一时刻的输出量的变化情况，例如输出量在 $t=NT+\varepsilon T,N=0,1,2,\cdots$ ，各点上的变化规律，在 $0\leqslant\varepsilon<r$ 时，可应用公式(10.1-18)，或在 $1>\varepsilon>r$ 时，应用式(10.1-19)求开路系统和闭路系统的传递函数及频率特性。此时传递函数中将含有参数 $\varepsilon$ 。对式(10.1-18)的两端进行拉氏变换，再加以整理后，可以写出开路传递函数矩阵

$$
F ^ {*} (s, \varepsilon) = (E e ^ {s T} - D) ^ {- 1} (B _ {1} (\varepsilon) + e ^ {s T} B _ {2} (\varepsilon)) \tag {10.3-30}
$$

而闭路系统传递矩阵为

$$
\Phi^ {*} (s, \varepsilon) = (E + F ^ {*} (s, \varepsilon)) ^ {- 1} F ^ {*} (s, \varepsilon) \tag {10.3-31}
$$

上式内代入 $s=i\omega$ 后，又得到频率特性矩阵。

#### 10.4 一种特殊情况下 $F^{*}(s)$ 的计算

前节内传递函数的推导是基于方程组的基本解矩阵得到的。在某些特殊情形下，采样传递函数可以从受控对象的连续传递函数 $F(s)$ 出发经过变换后，直接求出来，而不必首先求出离散系统的差分方程式。 $F(s)$ 与 $F^{*}(s)$ 这两个函数都是用来表示控制系统的特性的，当控制系统是连续作用的组成部分时， $F(s)$ 就是很重要的特性。但是，当控制系统用在离散控制系统上的时候， $F^{*}(s)$ 就成为重要的特性了。从数学上看 $F(s)$ 比 $F^{*}(s)$ 简单得多，而且我们也常常把 $F(s)$ 直接用到设计系统的方法上去，因此，当可能时，找出 $F^{*}(s)$ 与 $F(s)$ 的关系，就是很重要的事情了。当然，直接从 $F(s)$ 求 $F^{*}(s)$ 并不是对所有离散系统都那么简单可行。但 是，当脉冲元件所调制的脉冲宽度 $\gamma T \ll T$ , 即 $\gamma \ll 1$ 时, 这种直接换算是可能的。

重新研究方程组(10.1-3)，它是受控对象的连续运动方程组。设系统的初始条件为零，那么式(10.1-3)的特解是

$$
\mathbf {y} (t) = \int_ {0} ^ {t} e ^ {A (t - \tau)} \boldsymbol {b u} (\tau) d \tau \tag {10.4-1}
$$

令 $e^{A(t-\tau)}\boldsymbol{b}=\boldsymbol{h}(t-\tau)$ ，显然， $\boldsymbol{h}(t)$ 是系统的脉冲过渡函数（见第二章）。根据连续拉氏变换的特点可知

$$
\boldsymbol {Y} (s) = \boldsymbol {F} (s) U (s), \boldsymbol {F} (s) = \left(F _ {1} (s), F _ {2} (s), \dots , F _ {n} (s)\right)
$$

而

$$
\boldsymbol {F} (s) = \int_ {0} ^ {\infty} \boldsymbol {h} (t) e ^ {- s t} d t \tag {10.4-2}
$$

当 $u(t)$ 是一个方形脉冲序列时, 式(10.4-1)可以写成

$$
\begin{array}{l} \mathbf {y} (N T) = \sum_ {m = 0} ^ {N} \int_ {m T} ^ {(m + 1) T} \mathbf {h} (N T - \tau) u (\tau) d \tau \\ = \sum_ {m = 0} ^ {N} \int_ {m T} ^ {(m + \gamma) T} \boldsymbol {h} (N T - \tau) u (\tau) d \tau \tag {10.4-3} \\ \end{array}
$$

当 $\gamma\ll1$ 时, 上式右端的积分间隔远远小于 T。当 $h(t)$ 的变化较慢时, 可以以足够的精度认为

$$
\int_ {m T} ^ {(m + \gamma) T} \boldsymbol {h} (N T - \tau) u (\tau) d \tau = \gamma T \boldsymbol {h} (N T - m T) u (m T) \tag {10.4-4}
$$

将式 $(10.4-4)$ 代入式 $(10.4-3)$ 后有

$$
\mathbf {y} (N T) = \gamma T \sum_ {m = 0} ^ {N} \mathbf {h} (N T - m T) u (m T)
$$

对上式两端进行拉氏变换

$$
\mathbf {Y} ^ {*} (s) = \sum_ {N = 0} ^ {\infty} \mathbf {y} (N T) e ^ {- N T s} = \gamma T \sum_ {N = 0} ^ {\infty} \left[ \sum_ {m = 0} ^ {N} \mathbf {h} (N T - m T) u (m T) \right] e ^ {- N T s}
$$

根据前节拉氏变换特性式(10.3-6)，上式可以写成

$$
\boldsymbol {Y} ^ {*} (s) = \boldsymbol {F} ^ {*} (s) U ^ {*} (s) \tag {10.4-5}
$$

式中

$$
\boldsymbol {F} ^ {*} (s) = \gamma T \sum_ {N = 0} ^ {\infty} \boldsymbol {h} (N T) e ^ {- N T s} \tag {10.4-6}
$$

$$
U ^ {*} (s) = \sum_ {N = 0} ^ {\infty} u (N T) e ^ {- N T s} \tag {10.4-7}
$$

式(10.4-6)和(10.4-3)是两个向量等式。取它们的第一个分量，即系统的主受控量 $y_{1}$ ，后者对应的两个传递函数是 $F(s)$ 和 $F^{*}(s)$ ，前者对应的脉冲过渡函数写为 $h(t)$ 。于是有

$$
F (s) = \int_ {0} ^ {\infty} h (t) e ^ {- s t} d t
$$

$$
F ^ {*} (s) = \gamma T \sum_ {N = 0} ^ {\infty} h (N T) e ^ {- s N T} \tag {10.4-8}
$$

将

$$
h (t) = \frac {1}{2 \pi i} \int_ {c - i ^ {\infty}} ^ {c + i ^ {\infty}} F (s) e ^ {s t} d s
$$

代入式(10.4-8)的第二式后有

$$
\begin{array}{l} F ^ {*} (s) = \frac {\gamma T}{2 \pi i} \sum_ {N = 0} ^ {\infty} e ^ {- s N T} \int_ {c - i ^ {\infty}} ^ {c + i ^ {\infty}} F (q) e ^ {N T q} d q \\ = \frac {\gamma T}{2 \pi i} \int_ {c - i ^ {\infty}} ^ {c + i ^ {\infty}} F (q) \left[ \sum_ {N = 0} ^ {\infty} e ^ {- N T (s - q)} \right] d q \\ = \frac {\gamma T}{2 \pi i} \int_ {c - i ^ {\infty}} ^ {c + i ^ {\infty}} \frac {F (q)}{1 - e ^ {- T (s - q)}} d q \tag {10.4-9} \\ \end{array}
$$

上式内当 s 的实部 $\operatorname{Re}s > \sigma$ 时，级数绝对收敛，故上面的运算是正确的。这样，在一种特殊情况下我们获得了自 $F(s)$ 至 $F^{*}(s)$ 的直接变换公式。以下我们就用留数方法来计算式(10.4-9)右端的积分。

被积函数有无穷多个极点： $F(s)$ 的极点都在积分路线的左方；但是那些由方程 $1 - e^{-T(s-q)} = 0$ 的零点所构成的极点都在积分路线的右方。不难看出：沿着从 $c - i^{\infty}$ 到 $c + i^{\infty}$ 的直线的积分值等于在顺时针方向上，沿着这样一条闭合积分路线上的积分值：这条闭合路线是由原来的直线和右半平面上以那条直线为直径的一个无限大的半圆周所组成的。因此，方程 (10.4-9) 右端的积分值等于 $-\gamma T$ 与被积函数在方程 $1 - e^{-T(s-q)} = 0$ 的各个零点的留数的和的乘积。

方程 $1 - e^{-T(s - q)} = 0$ 的零点的一般形式是 $q = s + (2\pi im / T)$ ， $m$ 是任何整数。被积函数在这样一个极点处的留数是 $-\left[\frac{1}{T}\right]F[s + (2\pi im / T)]$ 。所以，就得出

$$
F ^ {*} (s) = \gamma \sum_ {m = - \infty} ^ {\infty} F \left[ s + \frac {2 \pi i m}{T} \right] \tag {10.4-10}
$$

这个公式使我们能够相当深刻的看出 $F^{*}(s)$ 的性质，有时候也可以利用这个公式进行近似的计算。但是，我们还可以用相当简单的有限形式把 $F^{*}(s)$ 精确地表示出来。

函数 $F(s)$ 可以写成有限多个部分分式的和

$$
F (s) = \sum_ {k = 1} ^ {n} \frac {a _ {k}}{s - s _ {k}} \tag {10.4-11}
$$

这里的各个 $a_{k}$ 和 $s_{k}$ 都是常数，n 是 $F(s)$ 的分母多项式的次数。于是，利用方程式

(10.4-10)并令 $\gamma=1$ 就有

$$
\begin{array}{l} F ^ {*} (s) = \sum_ {k = 1} ^ {n} a _ {k} \left\{\frac {1}{s - s _ {k}} + \sum_ {m = 1} ^ {\infty} \left[ \frac {1}{(2 \pi i m / T) + (s - s _ {k})} - \frac {1}{(2 \pi i m / T) - (s - s _ {k})} \right] \right\} \\ = \sum_ {k = 1} ^ {n} a _ {k} \left[ \frac {1}{s - s _ {k}} + \sum_ {m = 1} ^ {\infty} \frac {2 (s - s _ {k})}{\left(4 \pi^ {2} m ^ {2} / T ^ {2}\right) + (s - s _ {k}) ^ {2}} \right] \tag {10.4-12} \\ \end{array}
$$

但是，我们知道 $\coth z$ 有如下的展开式

$$
\coth z = \frac {1}{z} + 2 z \sum_ {m = 1} ^ {\infty} \frac {1}{m ^ {2} \pi^ {2} + z ^ {2}}
$$

所以，方程(10.4-12)中对 m 所求的和数可以计算出来，因此就得出

$$
F ^ {*} (s) = \frac {T}{2} \sum_ {k = 1} ^ {n} a _ {k} \coth \left[ \frac {(s - s _ {k}) T}{2} \right] \tag {10.4-13}
$$

利用这个公式，对于任意的 s 值都可以把 $F^{*}(s)$ 准确地计算出来。

如果 T 很小， $F(i\omega)$ 的值在 $-\pi/T<\omega<\pi/T$ 间隔之外小到略去不计的程度，那么，根据方程(10.4-10)就可以很清楚地看出 $F^{*}(s)$ 的定性的性质。事实上，在间隔 $-\pi/T<\omega<\pi/T$ 里 $F^{*}(i\omega)$ 差不多就等于 $F(i\omega)$ 。我们将要看到，如果 T 相当大，我们也还可以得到一个相当简单的 $F^{*}(i\omega)$ 的近似表示式。把各个零点 $s_{k}$ 写作

$$
s _ {k} = - \lambda_ {k} + i \omega k \tag {10.4-14}
$$

这些 $\lambda_{k}$ 和 $\omega_{k}$ 都是实数。我们假设，所有的 $\lambda_{k}$ 都是正数。按照方程(10.4-13)现在就得出

$$
\begin{array}{l} F ^ {*} (i \omega) = \frac {T}{2} \sum_ {k = 1} ^ {n} a _ {k} \coth \left\{\frac {T}{2} \left[ \lambda_ {k} + i (\omega - \omega_ {k}) \right] \right\} \\ = \frac {T}{2} \sum_ {k = 1} ^ {n} a _ {k} \frac {1 + e ^ {- T \left[ \lambda_ {k} + i (\omega - \omega_ {k}) \right]}}{1 - e ^ {- T \left[ \lambda_ {k} + i (\omega - \omega_ {k}) \right]}} \\ \end{array}
$$

因此，对于大的 T 值就有

$$
F ^ {*} (i \omega) \cong \frac {T}{2} \sum_ {k = 1} ^ {n} a _ {k} \left\{1 + 2 e ^ {- T \left[ \lambda_ {k} + i (\omega - \omega_ {k}) \right]} \right\} \tag {10.4-15}
$$

当 s 很大的时候, 方程式(10.4-11)可以写作

$$
F (s) = \frac {1}{s} \sum_ {k = 1} ^ {n} a _ {k} + \frac {1}{s ^ {2}} \sum_ {k = 1} ^ {n} a _ {k} s _ {k} + \dots
$$

但是我们曾经假定：反馈线路对于 $\delta$ 函数的反应是连续的。所以，当 s 很大时; $F(s) \simeq 1/s^{2}$ , 因此

$$
\sum_ {k = 1} ^ {n} a _ {k} = 0 \tag {10.4-16}
$$

这样一来，方程(10.4-15)就变成

$$
F ^ {*} (i \omega) \cong T e ^ {- i T \omega} \sum_ {k = 1} ^ {n} a _ {k} e ^ {T s _ {k}} \tag {10.4-17}
$$

对于实际的物理系统来说, $s_{k}$ 或者是实数，或者成复共轭对出现，所以方程(10.4-17)中的和数一定是实数。因此，当 $\omega$ 从 $-\pi/T$ 变到 $\pi/T$ 的时候, $F^{*}(i\omega)$ 的图线是一个圆，这个圆的半径是

$$
\left| T \sum_ {k = 1} ^ {n} a _ {k} e ^ {T s _ {k}} \right| \tag {10.4-18}
$$

在实际情况中， $F(s)$ 很可能在 s=0 处有一个极点。为了避免某些不必要的麻烦；以前我们并没有考虑这种情形。现在，我们把这种情形简短的讨论一下。

首先，我们可以看到，如 s=0 是 $F(s)$ 的一个极点，那么常数 c 就必须是正数，而且 $F^{*}(s)$ 的无穷级数表示式(10.4-10)只在 s 的实数部分是正数时成立。这种情形中, $F^{*}(s)$ 的有限表示式,(10.4-13)仍然成立。如果，设 $s_{1}=0$ ,那么，方程(10.4-13)就变为

$$
F ^ {*} (i \omega) = \frac {T}{2} \left\{- i a _ {1} \cot \frac {\omega T}{2} + \sum_ {k = 2} ^ {n} a _ {k} \coth \frac {T [ \lambda_ {k} + i (\omega - \omega_ {k}) ]}{2} \right\}
$$

如果 T 的值很大，我们就得到一个类似于方程(10.4-15)的公式

$$
F ^ {*} (i \omega) = \frac {T}{2} \left[ - i a _ {1} \cot \frac {\omega T}{2} + \sum_ {k = 2} ^ {n} a _ {k} \left\{1 + 2 e ^ {- T \left[ \lambda_ {k} + i (\omega - \omega_ {k}) \right]} \right\} \right]
$$

但是按照式(10.4-16)

$$
a _ {2} + a _ {3} + \dots + a _ {n} = - a _ {1}
$$

所以

$$
F ^ {*} (i \omega) = \frac {- a _ {1} T}{2} \left[ 1 + i \cot \frac {\omega T}{2} \right] + T e ^ {- i T \omega} \sum_ {k = 2} ^ {n} a _ {k} e ^ {T s _ {k}} \tag {10.4-19}
$$

常数 $a_{1}$ 当然是一个正实数。当 $\omega$ 从 $-\pi / T$ 变化到 $\pi / T$ 时，式(10.4-19)的第一项就给出一条平行于虚轴的直线，其余部分是一个正弦函数。

#### 10.5 闭路离散系统分析

在讨论了描述离散系统的差分方程的建立方法及各种求解方法以后，可以开始研究闭路离散系统的动态和静态品质。如前几章内曾叙述过的那样，我们将研究闭路离散系统的稳定性、静差和过渡过程。本节内我们主要研究系统的稳定性判别准则，最后将讨论系统的静态误差。这也是线性系统的两个最重要的品质特性。关于如何设计系统使之具有良好的过渡特性，将在下一节内讨论。

首先讨论系统的稳定性问题。设受控对象的运动方程式是式(10.1-17)，即第一种和第四种差分方程

$$
H \mathbf {y} (N T) = D \mathbf {y} (N T) + C \mathbf {u} (N T) \tag {10.1-17}
$$

令系统的输入作用是 $\mathbf{g}(t)$ ，它是一个连续向量函数（或采样输入）。用简单的硬反馈所构成的闭路系统如图 10.3-4 所示。用 $Cu(NT)=K\varepsilon(NT)=K(\mathbf{g}(NT)-\mathbf{y}(NT))$ 代入式 (10.1-17) 后，得到闭路运动方程式

$$
H \mathbf {y} (N T) = (D - K) \mathbf {y} (N T) + K \mathbf {g} (N T) \tag {10.5-1}
$$

式中 K 为一 $n \times n$ 阶常量方阵，它表示了采样装置的增益矩阵。这样，系统的输出量 y 便受到输入作用的驱动。设 $g(t)$ 为任意已知的时间函数。显然，当系统的初始状态给定后， $y(t)$ 的运动规律便已经完全确定了。再令这个初始状态为 $y_{0}$ ，它所对应的运动是 $y(t)$ 。读者应该注意 $y(t)$ 实际上可以是连续函数，虽然差分方程 (10.1-17) 只能描绘它在采样时刻 $t = 0, T, 2T, \cdots$ ，上的变化情况但对任何 t 它都有确定的值。按李雅普诺夫定义，如果对给定的 $y_{0}$ 和 $g(t)$ ，系统的运动是稳定的，则对任何 $\varepsilon > 0$ ，总有 $\delta > 0$ ，一旦 $\|x_{0}\| < \delta, x_{0}$ 为任意 n 维向量，则对应于初始条件 $x_{0} + y_{0}$ 和 $g(t)$ 的系统运动 $z(t)$ 将永远满足不等式

$$
\| \mathbf {z} (t) - \mathbf {y} (t) \| <   \varepsilon
$$

这里 $x_{0}$ 称为对 $y(t)$ 的初始扰动， $z(t)$ 称为系统的受扰运动， $y(t)$ 则称为未受扰运动。显然，受扰运动也满足式(10.5-1)

$$
H \mathbf {z} (N T) = (D - K) \mathbf {z} (N T) + K \mathbf {g} (N T), \quad \mathbf {z} (0) = \mathbf {x} _ {0} + \mathbf {y} _ {0} \tag {10.5-2}
$$

受扰运动与未受扰运动的差是 $\boldsymbol{x}(t)=\boldsymbol{z}(t)-\boldsymbol{y}(t)$ 。自式(10.5-2)分别减掉式(10.5-1)的两端，得到 $\boldsymbol{x}(t)$ 在采样点上的运动规律

$$
H \boldsymbol {x} (N T) = (D - K) \boldsymbol {x} (N T), \quad \boldsymbol {x} (0) = \boldsymbol {x} _ {0} \tag {10.5-3}
$$

由于系统是线性的，我们也可以称 $x(t) \equiv 0$ 为系统的未受扰运动，因为此时 $z(t) \equiv y(t)$ 。由此可知，为了研究式(10.5-1)内 $y(NT)$ 的运动稳定性，只要研究式(10.5-3)的零解稳定性就够了。我们看到这里的情形与第四章内的情况相同。如果线性系统的齐次方程式的零解稳定，则系统的一切可能的运动都是稳定的。反之，如果任何一个运动是稳定的，则它的零解（平衡状态）也是稳定的，于是系统的一切运动都是稳定的。因此，我们可以一般地讲系统的稳定性。这里再一次指出，对非线性系统这一事实一般是不存在的，如果系统的平衡状态（零解）稳定，不能保证系统的任何运动稳定，所以对非线性系统，一般的去讲系统稳定有时是没有意义的。

式(10.5-3)的零解何时稳定？用什么方法判别？这正是我们想要解决的问题。根据式(10.2-4)，如果式(10.5-3)的初始条件是 $x_{0}$ ，那么，它的特解是

$$
\boldsymbol {x} (N T) = (D - K) ^ {N} \boldsymbol {x} _ {0} = A ^ {N} \boldsymbol {x} _ {0}, \quad A = (D - K) \tag {10.5-4}
$$

因为 $A^{N}$ 可以写成

$$
A ^ {N} = Q ^ {- 1} J ^ {N} Q
$$

$Q$ 是某一非蜕化（即其行列式不为零）矩阵。如果对任何 $\pmb{x}_0, \pmb{x}(NT)$ 都随着 $N$ 的增长而趋近于零向量，显然式(10.5-4)的零解将是稳定的。根据第 10.2 节内的 讨论可知，只要矩阵 A 所构成的特征方程式

$$
\mid A - E \lambda \mid = 0 \tag {10.5-5}
$$

的一切根的模小于 1 即可。其实， $J^{N}$ 内的每一元素都是由 $\lambda_{i}^{N}$ 所构成的，当 $|\lambda_{i}|<1, N\to\infty$ 时，总有 $|\lambda_{i}^{N}|\to0$ 。因此，当 $|\lambda_{i}|<1$ 时， $J^{N}$ 趋于零矩阵，由此可知 $A^{N}$ 也趋于零。故有

$$
\lim _ {N \rightarrow \infty} A ^ {N} \boldsymbol {x} _ {0} = \mathbf {0}
$$

> 此处省略原书 **图 10.5-1**

这时，式(10.5-1)稳定的充分条件是矩阵 $A = D - K$ 的一切特征根在复平面上均位于单位圆的内部（图 10.5-1)。反之，哪怕特征根中有一个位于单位圆之外，则系统将是不稳定的。因为此时至少有一个约当块 $J_{i}^{N}$ ，它的某一些元素随 $N$ 的无限增大而无限增长，对某一初始条件 $\pmb{x}_{0}$ ，使 $\lim_{N\to \infty}\pmb{x}(NT) = \infty$ 。由此可以断言，系统式(10.5-1)不稳定的充分条件是矩阵 $A = D - K$ 至少有一个特征根的模大于 1，即位于复平面的单位圆外。如果一部分在单位圆内，另一部分在单位圆上，圆外无根，这是一种临界状态，即系统处于稳定边缘。对这类系 统的研究只具有数学上的意义，实际上是不允许出现的。

让我们再看看稳定系统的传递函数应具有何种性质。回顾式(10.3-17)可以看到，如果输入作用 $\mathbf{g}(t)\equiv\mathbf{0}$ 且 C 为单位矩阵时有

$$
\boldsymbol {Y} ^ {*} (s) = \left(E e ^ {s T} - D\right) ^ {- 1} \boldsymbol {y} _ {0} = \Phi^ {*} (s) \boldsymbol {y} _ {0}
$$

式中 $\Phi^{*}(s)$ 的每一元素为 $e^{sT}$ 的有理分式，上式可以写成一个线性方程组

$$
Y _ {i} ^ {*} (s) = \sum_ {j = 1} ^ {n} \varphi_ {i j} ^ {*} (s) y _ {0 j}, \quad i = 1, 2, \dots , n
$$

根据拉氏变换的特性可知，当一切 $\varphi_{ij}^{*}(s)$ 的极点 $s_i$ 均为负实部时， $\lim_{N \to \infty} y_i (NT) = 0$ 。由此可以断言，闭路系统稳定的另一充分条件是传递矩阵的每一元素的极点都位于复平面的左半平面上。这个充分条件对第二种差分方程式的传递函数式(10.3-14)也是完全适用的。读者从式(10.3-13)可以直接看出，这里不再赘述。由于逆矩阵的特点， $\varphi_{ij}^{*}(s)$ 的极点又恰恰是行列式

$$
\Delta (s) = \mid E e ^ {s T} - D \mid = \det (E e ^ {s T} - D) = 0 \tag {10.5-6}
$$

的零点。上式称为离散系统的特征方程式，而且式(10.5-6)的零点也正是 $\Phi^{*}(s)=(\Phi_{1}^{*}(s),\cdots,\Phi_{n}^{*}(s))$ 每一个分量的极点。因此，欲检查闭路系统的稳定性，可以检查 $\Delta(s)$ 的零点，或者检查任一 $\Phi_{i}^{*}(s)$ 的极点是否位于复数平面的左半平面即可。

当 $\Phi_{i}^{*}(s)$ 的极点或 $\Delta(s)$ 的零点 $s_{j}, j=1,2,\cdots,n$ ，有负实部时，可保证序列 $\{\mathbf{y}(NT)\}$ 中的每一个分量序列当 $N\to\infty$ 时趋于零。但系统的输出量 $\mathbf{y}(t)$ 实际上是 t 的连续函数。仅仅在采样点 0, T, 2T, $\cdots$ , NT, $\cdots$ 上趋近于零，严格说来还不能保证 $\lim_{t\to\infty}\mathbf{y}(t)=\mathbf{0}$ 。 为了检查后者的存在，还要检查在节点

> 此处省略原书 **图 10.5-2**

的 $\varepsilon T$ 位移，即在 $NT + \varepsilon T$ 上的运动规律， $N = 0, 1, 2, \cdots$ 。例如，原理上可能出现图 10.5-2 所示的情况，虽然， $y_{i}(NT) \rightarrow 0$ ，但在采样点的位移点上， $y_{i}(NT + \varepsilon T)$ 不趋向于零，故为了确信系统的输出 $y(t) \rightarrow 0$ ，必须对某一 $\varepsilon > 0$ ，检查式 (10.3-31) 的任一分量的极点分布情况，稳定系统的传递函数 $\Phi_{i}^{*}(s, \varepsilon)$ 的一切极点 $s_{j}$ 也必须满足前述条件，即所有 $s_{j}$ 均在复平面的左半平面上。虽然如此，图 10.5-2 的情况是非常罕见的，因此，一般来讲只检查在节点 $\Phi_{i}^{*}(s)$ 的极点即够了。为了不发生意外情况，当然可以选取某一 $\varepsilon > 0$ ，再检查一次 $\Phi_{i}^{*}(s, \varepsilon)$ 的极点。

实际上，求特征方程式的根，只有在一次和二次方程式时，求解才比较容易。三次以上的方程式根的一般表达式或者过于繁冗，或者不可能写出。更高次的方程式，一般地说没有根的普遍表达式。因此，不必解出根来而能决定系统稳定性的法则就具有很大的实际意义了。利用这类所谓稳定判据的法则，我们不仅能够确定系统是否稳定，同时也能说明系统中各种参量和结构变化时对稳定性的影响。

连续系统中现有的几种稳定判据稍加改变后同样能用到离散系统上来。各种形式的稳定判据，它们所表示的是同一个事实：特征方程式所有的根都位于复平面上单位圆内。但是，在解决具体问题时，如果方法选择得当，就可以收到计算简单的效益。下面将要讨论的几种稳定判据，是以复变函数理论中所熟知的幅角定理为基础的。首先我们用米哈依洛夫（Михайлов）判别法来研究差分方程式的稳定性。设差分方程的特征方程式为

$$
\mid D - \lambda E \mid = f (\lambda) = (\lambda - \lambda_ {1}) (\lambda - \lambda_ {2}) \dots (\lambda - \lambda_ {n}) \tag {10.5-7}
$$

令 $\lambda=e^{i\theta},\lambda_{1}=\rho_{1}e^{i\theta_{1}},\lambda_{2}=\rho_{2}e^{i\theta_{2}},\cdots,\lambda_{n}=\rho_{n}e^{i\theta_{n}}$ ,代入式(10.5-7)中后

$$
\begin{array}{l} f \left(e ^ {i \theta}\right) = \left(e ^ {i \theta} - \rho_ {1} e ^ {i \theta_ {1}}\right) \left(e ^ {i \theta} - \rho_ {2} e ^ {i \theta_ {2}}\right) \dots \left(e ^ {i \theta} - \rho_ {n} e ^ {i \theta_ {n}}\right) \\ = R _ {1} (\theta) e ^ {i \varphi_ {1} (\theta)} R _ {2} (\theta) e ^ {i \varphi_ {2} (\theta)} \dots R _ {n} (\theta) e ^ {i \varphi_ {n} (\theta)} \\ = R (\theta) e ^ {i \sum_ {j = 1} ^ {n} \varphi_ {j} (\theta)} \tag {10.5-8} \\ \end{array}
$$

式(10.5-8)中我们取出 $R_{1}(\theta)e^{i\varphi_{1}(\theta)}$ 来研究。若 $\lambda_{1}$ 点在单位圆内，也就是说 $\rho_{1}<1$ ，由图 10.5-3(a) 中可以看出，当 $\theta$ 角由 0 变到 $2\pi$ 时， $R_{1}(\theta)e^{i\varphi_{1}(\theta)}$ 向量绕 $\lambda_{1}$ 点转 $2\pi$ 角度。当 $\lambda_{1}$ 在单位圆外，也就是 $\rho_{1}>1$ ，由图 10.5-3(b) 中可以看出，当 $\theta$ 角由 0 变到 $2\pi$ 时， $R_{1}(\theta)e^{i\varphi_{1}(\theta)}$ 绕 $\lambda_{1}$ 点转之角度为零。但是 n 阶方程一定有 n 个根，如果 n 个根均在单位圆内，则式 (10.5-8) 的总转角为 $2n\pi$ ，若都在单位圆外则转角为零。若一部分根在单位圆内另一部分在单位圆外时，转角一定小于 $2n\pi$ 。于是我们把米哈依洛夫稳定判别法则转述如下：当 $\theta$ 角由 0 变到 $2\pi$ 时，曲线 $f(\lambda)$ 绕原点转 $2n\pi$ 角度，则系统稳定。否则是不稳定的。

> 此处省略原书 **图 10.5-3**

> 此处省略原书 **图 10.5-4**

稳定性的另一判据方法是把闭环系统的稳定条件化为代数中著名的劳斯-霍尔维茨不等式。为此，在多项式(10.5-7)中进行分式线性变换

$$
s = \frac {\lambda - 1}{\lambda + 1} \text {或} \lambda = \frac {s + 1}{s - 1}
$$

这种变换把 $\lambda$ 平面上之单位圆的内部变换成 $S$ 复平面上的左半平面。如图 10.5-4 所示。也就是把

$$
f (\lambda) = a _ {n} \lambda^ {n} + a _ {n - 1} \lambda^ {n - 1} + a _ {n - 2} \lambda^ {n - 2} + \dots + a _ {0}
$$

变成

$$
F (s) = b _ {n} s ^ {n} + b _ {n - 1} s ^ {n - 1} + \dots + b _ {0}
$$

经过变换后多项式的系数由下式确定

$$
\begin{array}{l} b _ {k} = \sum_ {m = 0} ^ {n} a _ {n - m} (- 1) ^ {m} \left[ C _ {n - m} ^ {k} - C _ {m} ^ {\prime} C _ {n - m} ^ {k - 1} + C _ {m} ^ {2} C _ {n - m} ^ {k - 2} + \dots \right. \\ \left. + (- 1) ^ {k - 1} C _ {m} ^ {k - 1} C _ {n - m} ^ {\prime} + (- 1) ^ {k} C _ {m} ^ {k} \right] \\ \end{array}
$$

式中

$$
C _ {m} ^ {k} = \frac {m !}{k ! (m - k) !}
$$

如果 $f(\lambda)$ 的一切零点均位于单位圆内，则 $F(s)$ 的一切零点将位于 $S$ 平面上之左半平面内。这样，我们便可以用霍尔维茨行列式判别离散系统的稳定性。这些行列式是

$$
\begin{array}{c c c c c c c c c c} b _ {1} & b _ {0} & 0 & 0 & 0 & \dots & & \\ b _ {3} & b _ {2} & b _ {1} & b _ {0} & 0 & \dots & & \\ \hline b _ {5} & b _ {4} & b _ {3} & b _ {2} & b _ {1} & b _ {0} & 0 & \dots & \\ \hline b _ {7} & b _ {6} & b _ {5} & b _ {4} & b _ {3} & b _ {2} & b _ {1} & b _ {0} & 0 & \dots \\ \hline \dots \end{array}
$$

记

$$
\Delta_ {1} = b _ {1}, \quad \Delta_ {2} = \left| \begin{array}{l l} b _ {1} & b _ {0} \\ b _ {3} & b _ {2} \end{array} \right|, \quad \Delta_ {3} = \left| \begin{array}{c c c} b _ {1} & b _ {0} & 0 \\ b _ {3} & b _ {2} & b _ {1} \\ b _ {5} & b _ {4} & b _ {3} \end{array} \right|, \dots
$$

于是，霍尔维茨判据可以叙述如下：系统稳定的充分条件为不等式 $b_{0}>0$ ，并且各个霍尔维茨行列式 $\Delta_{1},\Delta_{2},\Delta_{3},\cdots,\Delta_{n}$ 均大于零。此时 $F(s)$ 的一切根均有负实部。

上面介绍的两种方法简化了稳定判别的过程，从而使我们比较直观地看出离散系统的稳定情况。

我们在开始时还提到过一个重要的系统品质指标，即系统的静态误差。这一概念是在跟踪问题中产生的。欲使受控对象式(10.1-4)的输出状态向量 $y(t)$ 跟随着某一输入作用变化，控制量 $u(t)$ 应使在 $t \to \infty$ 时跟踪误差最小或为零。遗憾的是并不是任何系统对任何输入作用都可以使跟踪误差为零，而只有某些所谓无静差系统，对某些特定类型的输入作用，才有这种性能。下面我们将研究一个系统无静差的充分条件。设 n 维向量函数 $g(t) = (g_{1}(t), g_{2}(t), g_{3}(t), \cdots, g_{n}(t))$ ， $t = 0, T, 2T, \cdots, mT, \cdots$ ，为系统的输入作用，受控系统输出 $y(t)$ 应跟踪它。或者，需选择控制参数，使经过足够大时间后，误差向量

$$
\varepsilon (t) = \mathbf {g} (t) - \mathbf {y} (t) \tag {10.5-9}
$$

将一致趋于零。我们将 $\mathbf{y}(t)=\mathbf{g}(t)-\varepsilon(t)$ 代入式(10.1-4)就得到

$$
H \mathbf {g} (t) - H \varepsilon (t) = D \mathbf {g} (t) - D \varepsilon (t) + \mathbf {c u} (t)
$$

或

$$
H \varepsilon (t) = D \varepsilon (t) - c u (t) + H g (t) - D g (t) \tag {10.5-10}
$$

现将 $\varepsilon(t)=(\varepsilon_{1}(t),\varepsilon_{2}(t),\varepsilon_{3}(t),\cdots,\varepsilon_{n}(t))$ 看成系统的状态向量。控制量 u 的作用是使 $\varepsilon(t)$ 的每一个坐标趋于零。方程式 (10.5-10) 与 (10.1-4) 的差别，就在于前者有干扰作用。此外两种方程式本身无大的差别，其中 D 矩阵和 c 向量都保持了原来的形式。显然，若输入作用满足差分方程式

$$
H \mathbf {g} (t) = D \mathbf {g} (t) \tag {10.5-11}
$$

而且按误差反馈的闭路系统是渐近稳定的，则无论系统初始状态如何，误差 $\varepsilon (NT)$ 将趋于零。我们常称系统式(10.1-4)对满足条件式(10.5-11)的输入作用为无静差系统，而等式(10.5-11)为系统无静差的充分条件。我们把满足方程式(10.5-11)的输入函数称之为系统的固有输入作用类。

例. 讨论具有两个积分环节的系统, 如图 10.5-5 所示。令 $\gamma=1, T=1$ , 则其差分方程式为

$$
H \mathbf {y} (m T) = D \mathbf {y} (m T) + \mathbf {c u}
$$

式中

$$
D = \left( \begin{array}{c c} 1 & T \\ 0 & 1 \end{array} \right), \quad \boldsymbol {c} = \binom{\frac {T ^ {2}}{2}}{1}
$$

> 此处省略原书 **图 10.5-5**

设输入作用 $g_{1}(t)=a_{0}+a_{1}t$ ，式中 $a_{0}, a_{1}$ 均为常系数，该输入作用所确定的相对应的输入作用向量为

$$
\mathbf {g} (t) = \binom {a _ {0} + a _ {1} t} {a _ {1}}
$$

不难检查, $g(t)$ 满足方程式(10.5-11)

$$
H \mathbf {g} (m T) - D \mathbf {g} (m T) = \binom {a _ {0} + a _ {1} (m + 1) T} {a _ {1}} - \left( \begin{array}{c c} 1 & T \\ 0 & 1 \end{array} \right) \binom {a _ {0} + a _ {1} m T} {a _ {1}} = \mathbf {0}
$$

因此，上述系统对这样的输入作用 $\mathbf{g}(t)$ 是无静差系统。但是当输入作用不为 t 的线性函数，而含有 t 的二次项时，系统将变为有静差的了。

如 $g_{1}(t)=a_{0}+a_{1}t+a_{2}t^{2}$ ，式中 $a_{0}, a_{1}$ 和 $a_{2}$ ，均为常量。对于这样的输入作用所确定的相对应的输入作用向量为

$$
\mathbf {g} (t) = \binom {a _ {0} + a _ {1} t + a _ {2} t ^ {2}} {a _ {1} + 2 a _ {2} t}
$$

我们计算出

$$
H \mathbf {g} (m T) - D \mathbf {g} (m T) = \binom {a _ {2} T ^ {2}} {2 a _ {2} T} = \boldsymbol {f}
$$

不为零向量，所以系统是有静差系统。把上式代入式(10.5-10)中，便得到

$$
H \varepsilon (m T) = D \varepsilon (m T) - c u (m T) + f
$$

当我们把上式变成以误差反馈的闭路系统时，例如，令 $u(mT) = k_{1}\varepsilon_{1}(mT) + k_{2}\varepsilon_{2}(mT)$ ，当 $t$ 足够大而系统达到稳态时， $\lim_{m\to \infty}H\varepsilon (mT) = \varepsilon (mT)$ 。不难检查，当 $k_{1}\neq 0, c_{2}\neq 0$ 时， $(E + K - D)$ 是可逆矩阵，此处

$$
K = \left( \begin{array}{c c} c _ {1} k _ {1} & c _ {1} k _ {2} \\ c _ {2} k _ {1} & c _ {2} k _ {2} \end{array} \right)
$$

$$
\det (E + K - D) = c _ {2} k _ {1} T \neq 0
$$

于是，系统的静态误差为

$$
\begin{array}{l} \varepsilon (m T) = (E + K - D) ^ {- 1} f \\ = \left( \begin{array}{c c} \frac {k _ {2}}{k _ {1} T} & \frac {1}{c _ {2} k _ {1}} - \frac {c _ {1} k _ {2}}{c _ {2} k _ {1} T} \\ - \frac {1}{T} & \frac {c _ {1}}{c _ {2} T} \end{array} \right) \binom {a _ {2} T ^ {2}} {2 a _ {2} T} = \begin{array}{l} a _ {2} \left[ \frac {k _ {2}}{k _ {1}} + 2 \frac {T - c _ {1} k _ {2}}{c _ {2} k _ {1}} \right] \\ a _ {2} \left[ \frac {2 c _ {1}}{c _ {2}} - T \right] \end{array} \\ \end{array}
$$

从上式我们可以看出，系统的静差与输入作用的加速度 $\alpha_{2}$ 成正比，并和采样周期 T 有关。而矩阵

$$
(E + K - D) ^ {- 1} = \left( \begin{array}{c c} \frac {k _ {2}}{k _ {1} T} & \frac {1}{c _ {2} k _ {1}} - \frac {c _ {1} k _ {2}}{c _ {2} k _ {1} T} \\ - \frac {1}{T} & \frac {c _ {1}}{c _ {2} T} \end{array} \right)
$$

称为系统的静差系数矩阵。

当然，上列关于静态误差的讨论仅对按误差反馈的闭路系统才是正确的。如果采用复合控制方法，即 $u$ 不仅是 $\varepsilon$ 的线性函数，而且也是 $\pmb{g}(t)$ 的线性函数时，原来是有静差的系统，现在就可能变为无静差了。关于复合控制系统的理论在线性连续系统的理论中已做过详细讨论。那些计算方法可以完全类似地适用于对离散系统的分析，故此处不再重复。

#### 10.6 线性离散系统的综合

前面几节我们对线性离散系统进行了分析，这一节将研究线性离散系统的综合问题。由于高阶差分方程式和一阶方程组等价，故只研究方程组的情形，所得到的结论可直接应用到高阶差分方程式所描述的离散系统。

设受控对象的运动规律是由下述线性常系数差分方程组描述的，

$$
H \mathbf {y} (N T) = D \mathbf {y} (N T) + \mathbf {c u} (N T)
$$

其中控制量 $u(t)$ 假定不受限制。当然，在实际问题中，一般说来这是不可能的。但当 $u(t)$ 为误差坐标的线性组合，而误差又比较小时，此时 $u(t)$ 的取值也不会很大，往往处于其可准取值范围之内。这样就可以认为 $u(t)$ 取值不受限制。在这种假定下设计出来的系统，一般能满足对系统的基本要求，如稳定性，较短的过渡过程时间等。

若系统初始误差为 $y_{0}=(y_{10},y_{20},\cdots,y_{n0})$ ，按差分方程的通解公式有

$$
\mathbf {y} (N T) = D ^ {N} \mathbf {y} _ {0} + D ^ {N} \sum_ {m = 0} ^ {N - 1} D ^ {- (m + 1)} \mathbf {c u} (m T)
$$

现选择控制规律，使系统误差为零。我们先来证明一个简单的事实，就是在断续系统中，利用线性控制规律，可以使任何初始条件在有限时间内使其误差为零。设系统的差分方程是 n 阶的，或者说差分方程组含有 n 个方程式，现证明对完全能控的系统可以选择一种线性控制规律，在 nT 时间内无论初始偏差为何，总有 $y(nT)=0$ 。为此将式(10.2-6)整理后令 $y(nT)=0$ ,有

$$
\mathbf {y} _ {0} = - D ^ {- n} \boldsymbol {c u} [ (n - 1) T ] - D ^ {- n + 1} \boldsymbol {c u} [ (n - 2) T ] - \dots - D ^ {- 1} \boldsymbol {c u} (0) \tag {10.6-1}
$$

或者写成

$$
D ^ {n} \mathbf {y} _ {0} = - \mathbf {c u} [ (n - 1) T ] - D \mathbf {c u} [ (n - 2) T ] - \dots - D ^ {n - 1} \mathbf {c u} (0)
$$

当系统为完全能控时向量

$$
\boldsymbol {c}, D \boldsymbol {c}, D ^ {2} \boldsymbol {c}, \dots , D ^ {n - 1} \boldsymbol {c} \tag {10.6-2}
$$

线性不相关，他们构成 n 维相空间的基底向量，任何误差向量所确定的 $D^{n}y_{0}$ 均可由式(10.6-2)各向量的线性组合表示出来。不难检查，若 c, Dc, $D^{2}c\cdots D^{n-1}c$ 线性不相关，那么向量

$$
\boldsymbol {r} _ {1} = - D ^ {- 1} \boldsymbol {c}, \boldsymbol {r} _ {2} = - D ^ {- 2} \boldsymbol {c}, \dots , \boldsymbol {r} _ {n} = - D ^ {- n} \boldsymbol {c}
$$

也必然线性无关。将 $r_{i}=(r_{i1},r_{i2},\cdots,r_{in})$ 代入式(10.6-1)中后，得到线性代数方程组

$$
y _ {1 0} = r _ {n 1} u _ {n - 1} + r _ {n - 1, 1} u _ {n - 2} + \dots + r _ {1 1} u _ {0}
$$

$$
y _ {2 0} = r _ {n 2} u _ {n - 1} + r _ {n - 1, 2} u _ {n - 2} + \dots + r _ {1 2} u _ {0}
$$

$$
\dots
$$

$$
y _ {n 0} = r _ {n n} u _ {n - 1} + r _ {n - 1, n} u _ {n - 2} + \dots + r _ {1 n} u _ {0} \tag {10.6-3}
$$

其中 $y_{10}, y_{20}, \cdots, y_{n0}$ 为给定的系统初始误差坐标。 $u_i = u(iT), i=0,1,2,\cdots,n-1$ ，为待求的控制量。由于诸向量 $r_i$ 所组成的矩阵行列式不为零，即 $\det(r_1, r_2, r_3, \cdots, r_n) \neq 0$ ，所以代数方程式中的 $u_i$ 有唯一解

$$
u _ {i} = \frac {\det (\boldsymbol {r} _ {1} , \cdots , \boldsymbol {r} _ {i - 1} , \boldsymbol {y} _ {0} , \boldsymbol {r} _ {i + 1} \cdots \boldsymbol {r} _ {n})}{\det (\boldsymbol {r} _ {1} , \boldsymbol {r} _ {2} , \cdots , \boldsymbol {r} _ {n})}, \quad i = 1, 2, \dots , n \tag {10.6-4}
$$

将 $u_{i}$ 之值代入式(10.2-6)中后，无论系统初始误差状态如何，式(10.6-4)所决定的控制参数将最多在 n 步内使系统的误差归零。或者说任何过渡过程都在 n 个采样周期内结束。当然过渡时间也可以小于 nT。初看式(10.6-4)似乎是为了确定控制参数之值，必须算出它的 n 步内之诸值： $u(0), u(T), u(2T), \cdots, u[(n-1)T]$ 。其实为了使离散系统获得上述性能，只需算出 $u(0)$ 之值就足够了。因为差分方程(10.1-4)为常系数方程式，在任何时刻 $t = \alpha T$ 均能将 $y(\alpha T)$ 看作下一步的初始条件，只要系统诸坐标的值能不断地测量即可。根据式(10.6-4)可求出

$$
\begin{array}{l} u _ {0} = u (0) \\ = \frac {\det \left(\mathbf {y} _ {0} , \mathbf {r} _ {2} , \mathbf {r} _ {3} , \cdots , \mathbf {r} _ {n}\right)}{\det \left(\mathbf {r} _ {1} , \mathbf {r} _ {2} , \cdots , \mathbf {r} _ {n}\right)} \\ = \frac {R _ {1 1}}{\Delta} y _ {1 0} + \frac {R _ {1 2}}{\Delta} y _ {2 0} + \dots + \frac {R _ {1 n}}{\Delta} y _ {n 0} \tag {10.6-5} \\ \end{array}
$$

其中 $\Delta=\det(\boldsymbol{r}_{1},\boldsymbol{r}_{2},\cdots,\boldsymbol{r}_{n}),R_{ni}$ 为此行列式元素 $r_{ni}$ 之代数余子式。将 $u(0)$ 之值代入式 (10.1-4)，去掉 $y_{10},y_{20},\cdots,y_{n0}$ 的零注角则得到闭路方程式。

$$
\begin{array}{l} H \mathbf {y} (t) = D \mathbf {y} (t) + \mathbf {c u} (t) \\ = D \mathbf {y} (t) + \boldsymbol {c} \left[ \frac {R _ {1 1}}{\Delta} y _ {1} + \frac {R _ {1 2}}{\Delta} y _ {2} + \dots + \frac {R _ {1 n}}{\Delta} y _ {n} \right] \\ = (D + C) \mathbf {y} (t) = B \mathbf {y} (t), t = 0, T, 2 T, \dots \tag {10.6-6} \\ \end{array}
$$

式中

$$
B = (D + C)
$$

$$
C = \frac {1}{\Delta} \left( \begin{array}{c c c c} c _ {1} R _ {1 1} & c _ {1} R _ {1 2} & \dots & c _ {1} R _ {1 n} \\ c _ {2} R _ {1 1} & c _ {2} R _ {1 2} & \dots & c _ {2} R _ {1 n} \\ \vdots & \vdots & & \vdots \\ c _ {n} R _ {1 1} & c _ {n} R _ {1 2} & \dots & c _ {n} R _ {1 n} \end{array} \right)
$$

由此可知，用上述办法综合的闭路系统依然是一个为线性差分方程所描绘的系统。由于它能在 n 步内使任何初始误差归零，故式(10.6-6)所描述的闭路系统常称之为最优线性离散系统。

作为例子，试综合受控对象为串联的两个积分环节的系统。我们可以写出开环系统的运动微分方程式

$$
\frac {d y _ {1}}{d t} = y _ {2}, \quad \frac {d y _ {2}}{d t} = u
$$

或者

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + \mathbf {b u}
$$

其中

$$
A = \left( \begin{array}{c c} 0 & 1 \\ 0 & 0 \end{array} \right), \quad \boldsymbol {b} = \binom{0}{1}
$$

又可以求出相应的差分方程式

$$
H \mathbf {y} (N T) = D \mathbf {y} (N T) + \mathbf {c u} (N T)
$$

式中

$$
D = \left( \begin{array}{c c} 1 & T \\ 0 & 1 \end{array} \right), \quad \boldsymbol {c} = \binom{\gamma T ^ {2} \left( \begin{array}{c} 1 - \frac {1}{2} \gamma \end{array} \right)}{\gamma T}
$$

经过检查可知 c 和 Dc 是线性不相关的。根据上述讨论可以求出

$$
\boldsymbol {r} = - D ^ {- 1} \boldsymbol {c} = - \left( \begin{array}{c c} 1 & - T \\ 0 & 1 \end{array} \right) \binom{\gamma T ^ {2} \left[ 1 - \frac {1}{2} \gamma \right]}{\gamma T} = \binom{\frac {1}{2} (\gamma T) ^ {2}}{- \gamma T}
$$

$$
\boldsymbol {r} _ {2} = - D ^ {- 2} \boldsymbol {c} = \left( \begin{array}{c c} 1 & - T \\ 0 & 1 \end{array} \right) \binom {\frac {1}{2} (\gamma T) ^ {2}} {- \gamma T} = \binom {\gamma T ^ {2} \left[ 1 + \frac {1}{2} \gamma \right]} {- \gamma T}
$$

$$
\Delta = \left| \begin{array}{c c} \frac {1}{2} (\gamma T) ^ {2} & \gamma T ^ {2} \left[ 1 + \frac {1}{2} \gamma \right] \\ - \gamma T & - \gamma T \end{array} \right| = \gamma^ {2} T ^ {3}
$$

再根据式 $(10.6-5)$ 求出

$$
R _ {1 1} = - \gamma T, \quad R _ {1 2} = - \gamma T ^ {2} \left(1 + \frac {1}{2} \gamma\right)
$$

代入式 $(10.6-5)$ 即求出控制函数

$$
u (0) = \frac {- 1}{\gamma T ^ {2}} y _ {0 1} - \frac {\left[ 1 + \frac {1}{2} \gamma \right]}{\gamma T} y _ {0 2} \tag {10.6-7}
$$

所以

$$
C = \left( \begin{array}{c c} - \Big (1 - \frac {1}{2} \gamma \Big) & - T \Big (1 - \frac {1}{4} \gamma^ {2} \Big) \\ - \frac {1}{T} & - \Big (1 + \frac {1}{2} \gamma \Big) \end{array} \right)
$$

$$
B = \left( \begin{array}{c c} \frac {1}{2} \gamma & \frac {1}{4} \gamma^ {2} T \\ - \frac {1}{T} & - \frac {1}{2} \gamma \end{array} \right)
$$

于是闭路系统差分方程式

$$
H \mathbf {y} = B \mathbf {y}, \quad \boldsymbol {c u} (\alpha T) = C \mathbf {y} (\alpha T), \quad \alpha = 0, 1, 2, \dots , (n - 1)
$$

或者，写成展开形式:

$$
y _ {1} (m T) = \frac {1}{2} \gamma y _ {1} [ (m - 1) T ] + \frac {1}{4} \gamma^ {2} T y _ {2} [ (m - 1) T ]
$$

$$
y _ {2} (m T) = - \frac {1}{T} y _ {1} [ (m - 1) T ] - \frac {1}{2} \gamma y _ {2} [ (m - 1) T ] \tag {10.6-8}
$$

不难检查式(10.6-8)是最优系统，因为无论 $y_{0}=(y_{10},y_{20})$ 为何，只需 m=2 便有 $y_{1}(2T)=0,y_{2}(2T)=0$ 。且此后 $y_{1}(mT)\equiv y_{2}(mT)\equiv0,m>2$ 。事实上，根据通解公式有

$$
\mathbf {y} (m T) = B ^ {m} \mathbf {y} _ {0}
$$

但是

$$
B ^ {2} = \left( \begin{array}{c c} \frac {1}{2} \gamma & \frac {1}{4} \gamma^ {2} T \\ - \frac {1}{T} & - \frac {1}{2} \gamma \end{array} \right) \left( \begin{array}{c c} \frac {1}{2} \gamma & \frac {1}{4} \gamma^ {2} T \\ - \frac {1}{T} & - \frac {1}{2} \gamma \end{array} \right) = \left( \begin{array}{c c} 0 & 0 \\ 0 & 0 \end{array} \right)
$$

所以， $m \geqslant 2$ 时， $y(mT) \equiv 0$ 。这样我们就可以按式(10.6-7)中的关系式得到待求之控制装置。

#### 10.7 最优控制函数的综合

前节内我们讨论的线性系统，曾假定控制量 u 取值范围没有限制，这只是在某些情况下，例如在小扰动的情况下才有意义。几乎所有的线性理论的应用范围都大致如此。但是，在实际技术问题中控制量 u 不受限制的情况是比较少见的。当控制量有了限制之后，系统的运动状态就要发生重要的变化，其综合方法也与以前讨论的不同。一般来讲，系统的限制条件有两类，一类为对控制量的限制，一类为对某些系统状态坐标的限制。这两种限制不是一回事，在设计系统时应考虑这两种限制。实际技术问题中，对坐标限制往往能利用一些特殊装置自动地实 现。如随动系统常用的角度限制器，速度限制器与加速度限制器等。对控制量的限制是由控制器本身的特性决定的。例如放大器输出的最大电压和最大功率，已经由它的结构参数所确定，飞行器舵的最大转角常由机械结构情况和飞行器的气动特性所确定。从控制系统综合来看，以上两种限制都应该考虑。

在本节内我们只讨论控制量有限制的控制装置的综合问题，因为在这方面的研究工作近些年来有不少进展 $^{[25-27]}$ 。对最速控制系统已经提出了一些工程技术上可以采用的理论结果和计算方法。现讨论前面提出的线性差分方程

$$
H \mathbf {y} = D \mathbf {y} + \mathbf {c u} \tag {10.7-1}
$$

其中 u 的取值范围受到下列条件的限制：

$$
\mid u \mid \leqslant M \tag {10.7-2}
$$

满足式 $(10.7-2)$ 的控制 u 叫做可准控制。

设已知系统式(10.7-1)的初始状态为 $y_{0}=(y_{10},y_{20},\cdots,y_{n0})$ ，需要求出一个可准控制 $u(t), t=0, T,2T,\cdots,NT$ ; 代入式(10.7-1)后，系统将以最短时间，即最少采样周期，到达预定的状态。当然，预定状态不同，最优控制也将不同。下面我们将认为预定的终点状态是原点。

我们再讨论一下系统的能控性问题。在 10.2 节中我们曾讨论了线性系统能控性的充要条件。那个条件是在控制量不受限制的情况下得到的，在控制量受限制的条件下，情况将发生变化。我们需要重新定义系统的能控性。设 $y_0$ 是系统的初始状态，如果可以用某一可准控制 $u(t), |u(t)| \leqslant M$ ，可把 $y_0$ 引到原点，我们称 $y_0$ 为可控点；如果状态空间中有一个区域完全由可控点组成，则称为可控区；如果全部状态空间中的点都是可控的，则该系统称为全局可控。在控制量受限制的情况下，弄清可控性当然是很重要的。因为如果受控量和控制量不受限制的线性系统是完全能控的，当控制量受限制时就不一定是能控的，此时所谓最优控制问题就不一定有解。下面我们介绍全局可控性的充要条件。设式(10.7-1)为常系数线性系统，限制条件为式(10.7-2)，D 为非蜕化矩阵。系统为全局可控的充要条件是

(1) n 个向量 c, Dc, $D^{2}c,\cdots,D^{n-1}c$ 线性无关。 (10.7-3)

(2) 矩阵 D 的一切本征值满足不等式。

$$
\mid \lambda_ {i} \mid \leqslant 1, \quad i = 1, 2, \dots , n \tag {10.7-4}
$$

为了说明这两个条件的意义，我们再把式(10.7-1)的通解写出

$$
\mathbf {y} (N T) = D ^ {N} \mathbf {y} _ {0} + D ^ {N - 1} \mathbf {c u} (0) + \dots + \mathbf {c u} ((n - 1) T)
$$

设存在自然数 N，用控制 $u(t)=\{u(0),u(T),\cdots,u((N-1)T)\}$ 可把 $y_{0}$ 引到原点， $y(NT)=0$ 。因为 D 为非蜕化矩阵，上式可改写为式(10.6-1)的形式。令

$$
\boldsymbol {r} _ {1} = - D ^ {- 1} \boldsymbol {c}, \boldsymbol {r} _ {2} = - D ^ {- 2} \boldsymbol {c}, \dots , \boldsymbol {r} _ {N} = - D ^ {- N} \boldsymbol {c} \tag {10.7-5}
$$

于是有

$$
\mathbf {y} _ {0} = u _ {0} \mathbf {r} _ {1} + u _ {1} \mathbf {r} _ {2} + \dots + u _ {N - 1} \mathbf {r} _ {N} \tag {10.7-6}
$$

式中 $u_{i}$ 满足限制条件 $\left|u_{i}\right|\leqslant M$ 。从上式可以看出，凡是能用式(10.7-6)表达出来的 $y_{0}$ 点均为可控点，并且可以用可准控制在不大于 NT 的时间内到达原点。依据这种几何概念，我们来检查条件式(10.7-3)和(10.7-4)的充分性和必要性。

若 $c, Dc, D^{2}c, \cdots, D^{n-1}c$ 向量线性相关，那么，式(10.7-5)向量序列中任意 N 个线性相关， $N \geqslant n$ 。由定义式(10.7-5)知此时 $r_{1}, r_{2}, \cdots, r_{n}$ 线性相关，即存在 n 个不全为零的常数 $C_{1}, C_{2}, \cdots, C_{n}$ ，使

$$
C _ {1} \boldsymbol {r} _ {1} + C _ {2} \boldsymbol {r} _ {2} + \dots + C _ {n} \boldsymbol {r} _ {n} = \mathbf {0} \tag {10.7-7}
$$

由此可知， $r_{n}$ 向量可由前面 n-1 个向量的线性组合表示出来，它属于前 m 个向量所构成的子空间 $R_{m}$ ，其中 m<n。不难检查，无论 N 为多么大，式(10.7-7)所能达到的点均属于 $R_{m}$ 。由于子空间 $R_{m}$ 的维数小于 n，那么必存在大于 1 维的子空间 $R_{l}, l=n-m, l \geqslant 1$ ，其中任何点均不能用式(10.7-6)表示出来。换言之，若式(10.1-4)的初始状态为 $R_{l}$ 中之某一点，那么无论用什么可准控制都不能使系统归零。这就说明条件式(10.7-3)是全局可控的必要条件。

设式(10.7-4)不等式不成立，也就是说某个根 $|\lambda_{i}|>1$ 。现对式(10.1-4)进行坐标变换，令 P 为某一非蜕化方阵，令

$$
\boldsymbol {x} = P \boldsymbol {y}, \quad \det P \neq 0
$$

代入式(10.1-4)后有

$$
H \boldsymbol {x} = P D P ^ {- 1} \boldsymbol {x} + P \boldsymbol {c u} \tag {10.7-8}
$$

选择矩阵 P 使 $J = PDP^{-1}$ 成为约当标准型。用 $J_{1}$ 表示对应于 $\lambda_{1}$ 的约旦块，它的行数为 l，用 d 表示 Pc，则方程式 (10.7-8) 到达零点的通解可以写成

$$
\boldsymbol {x} _ {0} = u _ {0} \boldsymbol {r} _ {1} + u _ {1} \boldsymbol {r} _ {2} + \dots + u _ {N - 1} \boldsymbol {r} _ {N - 1} \tag {$10.7-6^{\prime$}}
$$

其中

$$
\boldsymbol {r} _ {1} = - J ^ {- 1} \boldsymbol {d}, \boldsymbol {r} _ {2} = - J ^ {- 2} \boldsymbol {d}, \dots , \boldsymbol {r} _ {N} = - J ^ {- N} \boldsymbol {d}
$$

而

$$
\begin{array}{l} J ^ {- m} = \left(J _ {1} ^ {- m}, \dots , J _ {k} ^ {- m}\right) \\ J _ {1} ^ {- m} = \left( \begin{array}{c c c c} \frac {1}{\lambda_ {1} ^ {m}} & - \frac {m}{\lambda_ {1} ^ {m + 1}} & \dots & - \frac {d ^ {l - 1} \left(\frac {1}{\lambda_ {1} ^ {m}}\right) / d \lambda_ {1} ^ {l - 1}}{(l - 1) !} \\ 0 & \frac {1}{\lambda_ {1} ^ {m}} & \dots & \dots \\ \vdots & \vdots & \vdots & \vdots \\ 0 & 0 & \dots & \frac {1}{\lambda_ {1} ^ {m}} \end{array} \right) \\ \end{array}
$$

令 $\boldsymbol{d}=(d_{1},d_{2},\cdots,d_{n})$ ，其中至少有一个 $d_{l}\neq0$ ，设 $\lambda_{1}$ 为实数。某一个向量 $x_{0}$ 能用

式 $(10.7-6')$ 之右端有限项之和表示的必要条件之一是 $x_{0}$ 的第 l 个分量 $x_{0l}$ 需能写成

$$
x _ {0 l} = d _ {l} \left[ \frac {u _ {0}}{\lambda_ {1}} + \frac {u _ {1}}{\lambda_ {1} ^ {2}} + \dots + \frac {u _ {m - 1}}{\lambda_ {1} ^ {m}} + \dots + \frac {u _ {N - 1}}{\lambda_ {1} ^ {N}} \right]
$$

由于 $|\lambda_1| > 1$ ，则右端之和满足下列不等式

$$
\mid x _ {0 l} \mid \leqslant \mid d _ {l} M \mid \sum_ {\alpha = 1} ^ {\infty} \frac {1}{\mid \lambda^ {\alpha} \mid} = \frac {\mid d _ {l} M \mid}{\mid \lambda_ {l} \mid - 1} = M _ {1}
$$

若取向量 $x_{0}$ ，它的分量 $x_{0l} > M_{1}$ ，则用任何可准控制均不能使受控对象由点 $x_{0} = (x_{10}, x_{20}, \cdots, x_{l-1,0}, \cdots, x_{n0})$ 在有限时间内到达原点。当 $\lambda_{1}$ 为复数时，上述讨论变化不大，而结论相同。这说明，为了使式(10.1-4)为全局可控，条件式(10.7-4)和(10.7-3)必须成立。

其次我们再证明当这些条件满足时，对任何非零的初始误差 $y_{0}$ 和对任何自然数 p 均能找到一组不为零的控制参数 $u_{p+1}, u_{p+2}, \cdots, u_{p+n}$ ，使

$$
\mathbf {y} _ {0} = q \left(u _ {p} \boldsymbol {r} _ {p + 1} + u _ {p + 1} \boldsymbol {r} _ {p + 2} + \dots + u _ {p + n - 1} \boldsymbol {r} _ {p + n}\right) = q \eta_ {p}
$$

$p=0,1,2,\cdots,|u_{p+i}|\leqslant M,q>0$ 。这是因为对任何 p 诸向量 $r_{p+1},r_{p+2},\cdots,r_{p+n}$ 为线性不相关，可以构成 n 维空间的基底，任何一个向量均可以用它们的线性组合表示。依假定我们知道，矩阵 D 的特征根 $|\lambda_{i}|\leqslant1$ ，重复前面的讨论可知，向量 $r_{p+i},i=1,2,\cdots,n$ 的长度不随 p 的增加而减小，于是上式内向量 $\eta_{p}$ 的长度总大于某一正数。对于任何 $y_{0}$ 均可取有限个向量，使

$$
\mathbf {y} _ {0} = \sum_ {\alpha = 1} ^ {N} \eta_ {\alpha}
$$

由上述讨论可知，若系统式(10.1-4)满足式(10.7-3)和(10.7-4)两个条件，对任何初始点 $y_{0}$ 都可以找到一个可准控制 $u(\alpha T), \alpha=1,2,\cdots,N$ 使系统在有限时间内归零。

参照对连续系统的讨论，在解决综合问题时我们主要应用等时区的概念。下面我们就来研究等时区的性质。从线性离散系统的运动规律式(10.7-6)可知，当 $N$ 为有限数时所能得到的 $\mathbf{y}_0$ 的范围总是有限的。这是因为诸向量的系数 $u_i$ 受到条件式(10.7-2)的限制。我们称由式(10.7-6)所决定的一切 $\mathbf{y}_0$ 点的集合为等时区，记为 $G(NT)$ 。同样我们从式(10.7-6)的几何意义可知， $G(NT)$ 在 $N \geqslant n$ 时构成 $n$ 维多面体，坐标原点为它的内点。当 $N = 1$ 时， $G(T)$ 只含有一个通过原点的向量， $\mathbf{y} = \mathbf{r}_1 u_0 = -D^{-1}cu_0, -M \leqslant u_0 \leqslant M; G(2T)$ 为包含原点的一个平行四边形，其各边为 $\pm Mr_1$ 和 $\pm Mr_2; G(3T)$ 为包含原点的一个平行六面体，其各棱边为 $\pm Mr_1, \pm Mr_2$ 和 $\pm Mr_3$ ；依此类推， $G(nT)$ 为包含原点在内的一个 $n$ 维多面体，其棱边分别为 $\pm Mr_1, \pm Mr_2, \dots, \pm Mr_n$ 。

容易检查， $G(NT)$ 是闭凸多面体，若 $\mathbf{y}_1$ 属于 $G(NT),\mathbf{y}_2$ 也属于 $G(NT)$ ，那么它们连线上的任一点 $\mathbf{y}$ 也属于 $G(NT)$ 。

因为对 $\lambda, 0 \leqslant \lambda \leqslant 1$ ，有

$$
\begin{array}{l} \mathbf {y} = (1 - \lambda) \mathbf {y} _ {1} + \lambda \mathbf {y} _ {2} \\ = (1 - \lambda) \sum_ {\alpha = 1} ^ {N} u _ {\alpha - 1} ^ {(1)} \boldsymbol {r} _ {\alpha} + \lambda \sum_ {\alpha = 1} ^ {N} u _ {\alpha - 1} ^ {(2)} \boldsymbol {r} _ {\alpha} \\ = \left[ (1 - \lambda) \sum_ {\alpha = 1} ^ {N} u _ {\alpha - 1} ^ {(1)} + \lambda \sum_ {\alpha = 1} ^ {N} u _ {\alpha - 1} ^ {(2)} \right] r _ {\alpha} \\ = \sum_ {\alpha = 1} ^ {N} \left[ (1 - \lambda) u _ {\alpha - 1} ^ {(1)} + \lambda u _ {\alpha - 1} ^ {(2)} \right] r _ {\alpha} \\ \end{array}
$$

而 $|u_{\alpha -1}^{(1)}|\leqslant M, |u_{\alpha -1}^{(2)}|\leqslant M$ 。所以 $|(1 - \lambda)u_{\alpha -1}^{(1)} + \lambda u_{\alpha -1}^{(2)}|\leqslant M$ 。这就证明了 $y$ 点用可准控制在 $N$ 步内可以到达。当 $N \geqslant n$ 时， $G(NT)$ 为一个 $n$ 维凸多面体，它的表面是有限个平面和棱线组合成的。按等时区的定义可知，若有一点 $y$ 不属于 $G(NT)$ ，那么，自该点到达原点，如果可能的话，所费时间一定大于 $NT$ 。若 $y$ 点属于 $G(NT)$ 而不属于 $G[(N - 1)T]$ ，则自该点到达原点至少需要 $N$ 步。

例.一个系统运动的方程式为

$$
\frac {d y _ {1}}{d t} = y _ {2}
$$

$$
\frac {d y ^ {2}}{d t} = u, \quad | u | \leqslant 1
$$

相应的离散运动方程式为

$$
H y _ {1} (m T) = y _ {1} (m T) + T y _ {2} (m T) + \gamma T ^ {2} \left[ 1 - \frac {1}{2} \gamma \right] u (m T)
$$

$$
H y _ {2} (m T) = y _ {2} (m T) + \gamma T u (m T)
$$

当 $\gamma = 1, T = 1$ 时有

$$
H y _ {1} (m T) = y _ {1} (m T) + y _ {2} (m T) + \frac {1}{2} u (m T)
$$

$$
H y _ {2} (m T) = y _ {2} (m T) + u (m T)
$$

由此可知

$$
\begin{array}{l} D = \left( \begin{array}{c c} 1 & 1 \\ 0 & 1 \end{array} \right) \\ \boldsymbol {c} = \left( \begin{array}{l} \frac {1}{2} \\ 1 \end{array} \right) \\ \boldsymbol {r} = - D ^ {- 1} \boldsymbol {c} = - \left( \begin{array}{l l} 1 & - 1 \\ 0 & 1 \end{array} \right) \left( \begin{array}{l} \frac {1}{2} \\ 1 \end{array} \right) = \left( \begin{array}{l} \frac {1}{2} \\ - 1 \end{array} \right) \\ \boldsymbol {r} _ {2} = - D ^ {- 2} \boldsymbol {c} = \left( \begin{array}{c c} 1 & - 1 \\ 0 & 1 \end{array} \right) \left( \begin{array}{l} \frac {1}{2} \\ - 1 \end{array} \right) = \left( \begin{array}{l} \frac {3}{2} \\ - 1 \end{array} \right) \\ \end{array}
$$

$$
\begin{array}{l} \boldsymbol {r} _ {3} = - D ^ {- 2} \boldsymbol {c} = \left( \begin{array}{c c} 1 & - 1 \\ 0 & 1 \end{array} \right) \binom {\frac {3}{2}} {- 1} = \binom {\frac {5}{2}} {- 1} \\ \dots \end{array}
$$

$$
\boldsymbol {r} _ {N} = - D ^ {- N} \boldsymbol {c} = \binom {\frac {2 N - 1}{2}} {- 1}
$$

按定义知， $G(NT)$ 是由下列一切向量组成的凸多面体

$$
\mathbf {y} = \sum_ {\alpha = 1} ^ {N} \mathbf {r} _ {\alpha} u _ {\alpha - 1}, \quad | u _ {\alpha} | \leqslant 1, \quad \alpha = 1, 2, \dots , N
$$

图 10.7-1 内画出了 $N = 1,2,3,4$ 时的等时区的几何形状。当 $N = 1$ 时， $G(T)$ 为由 $+\mathbf{r}_1$ 和 $-\mathbf{r}_1$ 组成的通过原点的一段直线； $G(2T)$ 为 $\mathbf{r}_1$ 和 $\mathbf{r}_2$ 所决定的平行四边形； $G(3T)$ 为 $\mathbf{r}_1,\mathbf{r}_2$ 和 $\mathbf{r}_3$ 所组成的平面六边形； $G(4T)$ 为 $\mathbf{r}_1,\mathbf{r}_2,\mathbf{r}_3$ 和 $\mathbf{r}_4$ 所组成的平面八边形。依此类推，可以画出任意 $G(NT)$ 来。可以看出，由于 $G(NT)$ 是凸的，所以只要求出所有的顶点用直线连接即可以。从上例中，我们得到启发，欲从 $G[(N - 1)T]$ 中得到 $G(NT)$ ，只需在 $G[(N - 1)T]$ 中的一切边界点上加上一个向量 $\pm Mr_N$ 经过一切 $G[(N - 1)T]$ 的边界点之后，便画出 $G(NT)$ 的一切边界点。不难看出这种作图法，对任何具有式(10.1-4)形式的系统都适合，这一事实可以写成

$$
G (N T) \supset G [ (N - 1) T ]
$$

这种包含关系，不仅是终点为原点时才成立，而对于一切满足代数式 $(D-E)\mathbf{y}_{0}+\mathbf{c}\mathbf{u}_{0}=\mathbf{0},|u|<M$ 的系统终点状态 $y_{0}$ 均有这种包含关系。此时我们称等时区为非降的。显然，当系统的终点为原点时，等时区总是非降的。

下面我们开始研究最优控制系统的综合方法。所谓最优控制函数的综合是指找出一个多元函数 $u(y_{1}, y_{2}, \cdots, y_{n})$ 将其代入式(10.1-4)后，系统从任何初始状态出发，均能以最短的步数自动回到原点。一般来讲，这一 n 元最优控制函数难以用解析式表达出来，而是分段取常值的离散函数。下面我们将通过对等时区的详细研究，求出最优控制函数之值在状态空间的分布规律。

设系统式(10.1-4)的初始条件为 $y_{0}$ ，若存在一个可准控制函数 $|u(t)| \leqslant M$ ， $t = 0, T, 2T, \cdots, NT$ ，它能使系统以最短的时间（最少步数）到达原点，就称 $u(t)$ 是最速控制函数。我们将要看到，在绝大多数情况下与连续系统相反，最速控制函数不是唯一的，自 $y_{0}$ 点有无穷多个不同的可准控制函数均能使系统以最短的时间到达原点，此时我们可以任选其中的一个作为设计的依据。设 $y_{0}$ 位于等时区 $G(NT)$ 内，但不属于 $G[(N-1)T]$ ，那么按等时区的定义，自 $y_{0}$ 到达原点的最短时间为 NT。任何可准控制函数 $u(t)$ 若能在 N 步内使描绘点到达原点，它就是最 速的。其次，若 $y_{0} \in G(NT)$ ，N > 2，但 $y_{0}$ 不属于 $G[(N-1)T]$ ，此时不存在任何可准控制 $u(0)$ 使 $y_{0}$ 在一步内进入 $G[(N-2)T]$ ，否则此点必属于 $G[(N-1)T]$ 。于是，任何可准控制 $u(t)$ ， $t = 0, T, \cdots, (N-1)T$ ，如果它能使系统按下列规律变化

> 此处省略原书 **图 10.7-1**

$$
\mathbf {y} _ {0} \in G (N T), \mathbf {y} (T) \in G [ (N - 1) T ], \dots , \mathbf {y} [ (N - 1) T ] \in G (T), \mathbf {y} (N T) = \mathbf {0} \tag {10.7-9}
$$

它一定是最速控制。因此在任何瞬间 $t = t_{0}$ ，若 $u(t_{0})$ 能保证使 $y_{0}$ 进入相邻更小的等时区，则控制函数的该值为最优。

由于等时区形状为凸性多面体，所以它的一切顶点足以决定等时区的全体，又因为任何一条棱线都是两个顶点的连线，而任一平面都是两条棱线组成的平面，因此为了得到等时区，必须首先研究如何得到它的顶点。设 $y_{0}$ 是等时区 $G(NT)$ 的一个顶点，由于它是凸的，从此点出发通过 $G(NT)$ 的任何两条射线的夹角均小于 $180^{\circ}$ ,否则 $y_{0}$ 不会是等时区的顶点。通过 $y_{0}$ 作一支面 P,使 $G(NT)$ 完全位于支面 P 的一侧，而且 $G(NT)$ 与 P 只有一个交点 $y_{0}$ 如图 10.7-2 所示。过 $y_{0}$ 点作 P 平面之外法向量 $\psi_{0},\psi_{0}$ 与 $G(NT)$ 不在同一侧，而 $y_{0}$ 为顶点，所以对 $G(NT)$ 内任何异于 $y_{0}$ 之点 y 均有不等式

$$
(\boldsymbol {\psi} _ {0}, \mathbf {y} - \mathbf {y} _ {0}) \leqslant 0 \tag {10.7-10}
$$

设自 $y_{0}$ 点到达原点的最速控制为 $u(t)$ ，而自 y 点到达原点的控制为 $u(t)$ ，那么根据式(10.7-6)和(10.7-10)可得

$$
\left[ \boldsymbol {\psi} _ {0}, \sum_ {\alpha = 1} ^ {N} \{\left[ \mathring {u} (\alpha - 1) T \right] - \left[ u (\alpha - 1) T \right] \} \boldsymbol {r} _ {\alpha} \right] \geqslant 0
$$

> 此处省略原书 **图 10.7-2**

> 此处省略原书 **图 10.7-3**

因为 y 是任意选的, 若令

$$
u [ (\alpha - 1) T ] = \left\{ \begin{array}{l} \dot {u} [ (\alpha - 1) T ], \quad \alpha \neq N \\ u ^ {\prime}, u ^ {\prime} \neq \dot {u} [ (\alpha - 1) T ], \quad \alpha = N, | u ^ {\prime} | \leqslant 1 \end{array} \right.
$$

此时有

$$
\left(\boldsymbol {\psi} _ {0}, \boldsymbol {r} _ {N}\right) \left(\mathring {u} [ (N - 1) T ] - u ^ {\prime}\right) \geqslant 0
$$

根据前面的讨论可知，若将 $r_{N} = -D^{-N}c$ 代入上式后有

$$
\left(- \left(D ^ {- N}\right) ^ {\tau} \boldsymbol {\psi} _ {0}, \boldsymbol {c}\right) \left(\stackrel {\circ} {u} [ (N - 1) T ] - u ^ {\prime}\right) \geqslant 0
$$

则

$$
\mathring {u} [ (N - 1) T ] = - M \text {sign} ((D ^ {- N}) ^ {\tau} \boldsymbol {\psi} _ {0}, \boldsymbol {c})
$$

重复上面的讨论，使 $y_{0}$ 点到达原点的最速控制 $\dot{u}(t)$ , 在任意时刻 $t=0, T, 2T, \cdots, mT$ 满足不等式

$$
- \left(\left(D ^ {- m}\right) ^ {\tau} \boldsymbol {\psi} _ {0}, \boldsymbol {c}\right) (\mathring {u} [ (m - 1) T ] - u [ (m - 1) T ] \geqslant 0 \tag {10.7-11}
$$

式中 $\dot{u}[(m-1)T]-u[(m-1)T]\neq0$ ; 欲使不等式(10.7-11)成立, 则要求向量 $\psi_{0}$ 满足下列条件

$$
\left(\left(D ^ {- m}\right) ^ {\tau} \boldsymbol {\psi} _ {0}, \boldsymbol {c}\right) \neq 0, \quad m = 1, 2, \dots , N
$$

因为 $(D^{-m})^{\tau}\pmb{\psi}_0$ 是式(10.2-7)的解，我们可以把上面讨论的问题归纳成下列必要条件：设 $\mathring{u}(t)$ 为自等时区 $G(NT)$ 的顶点 $\mathbf{y}_0$ 到达原点的最速控制，那么必存在一个非零向量 $\pmb{\psi}$ ，以它作为下列方程式的初始条件

$$
H ^ {*} \boldsymbol {\psi} (m T) = \boldsymbol {\psi} [ (m - 1) T ] = D ^ {\tau} \boldsymbol {\psi} (m T), \quad \boldsymbol {\psi} (0) = \boldsymbol {\psi} _ {0} \tag {10.7-12}
$$

$$
(\boldsymbol {\psi} (m T), \boldsymbol {c}) \neq 0, \quad m = 1, 2, \dots , N
$$

那么最速控制可表示为

$$
\dot {u} (m T) = - M \text {sign} (\boldsymbol {\psi} ((m + 1) T), \boldsymbol {c}) \tag {10.7-13}
$$

式(10.7-12)和(10.7-13)说明由等时区 $G(NT)$ 任意顶点到达原点的最速控制一定是极性控制，即 $\dot{u}(t)$ 的值只能是 $\pm M$ ，任何其他控制作用均不是最优的。为了以后讨论方便，和方程(10.1-4)一起讨论它的逆运动方程式

$$
H \mathbf {y} (m T) = D ^ {- 1} \mathbf {y} (m T) - \mathbf {r} _ {1} u (m T) \tag {10.7-14}
$$

式中 $r_{1}=D^{-1}c$ 。式(10.7-14)的共轭方程为

$$
H ^ {*} \boldsymbol {\psi} (m T) = (D ^ {- 1}) ^ {\tau} \boldsymbol {\psi} (m T) \tag {10.7-15}
$$

前面所述的自 $G(NT)$ 的顶点至原点的最速控制，同时也将是方程式(10.7-14)自原点到 $G(NT)$ 的顶点的最优控制。等时区 $G(NT)$ 同样可以认为是在 $NT$ 的时间内系统式(10.7-14)自原点所能到达的一切点的集合，而等式(10.7-6)恰恰是式(10.7-14)的通解。这样，必要条件式(10.7-12)和(10.7-13)可转变为系统式(10.7-14)自原点到达等时区 $G(NT)$ 顶点的最速控制的必要条件。因此，如果存在一个 $\psi_0$ ，使共轭方程式

$$
H ^ {*} \boldsymbol {\psi} (m T) = \left(D ^ {- 1}\right) ^ {\tau} \boldsymbol {\psi} (m T), \quad \boldsymbol {\psi} _ {0} = \boldsymbol {\psi} (N T)
$$

的解满足条件

$$
(\psi (m T), r _ {1}) \neq 0, \quad m = 1, 2, \dots , N
$$

则最速控制必为

$$
\mathring {u} (m T) = M \operatorname{sign} (\boldsymbol {\psi} [ (m + 1) T ], \boldsymbol {r}), \quad m = 0, 1, \dots , N - 1
$$

我们再研究等时区 $G(NT)$ 内部一点 $\mathbf{y}$ ，这里 $N \geqslant n$ ，并设它不属于更小的 $G[(N - 1)T]$ 。自此点到达原点至少要 $N$ 步。这时最优控制 $\mathring{u}(t)$ 不是唯一的，而是有无穷多个不相同的控制能在 $NT$ 时间内将 $\mathbf{y}$ 点引至原点。为了说明这一事实，我们在图 10.7-2 中通过 $\mathbf{y}$ 点作一任意直线与 $G(NT)$ 边界相交于 $\pmb{p}_1$ 和 $\pmb{p}_2$ ，自 $\pmb{p}_1$ 和 $\pmb{p}_2$ 两点到达原点的控制分别为 $u_1(t)$ 和 $u_2(t)$ ，它们是不相等的。令 $u_1(t)$ 和 $u_2(t)$ 分别表示自 $\pmb{p}_1$ 和 $\pmb{p}_2$ 点到达原点的最速控制，则

$$
u (t) = \lambda u _ {1} (t) + (1 - \lambda) u _ {2} (t), \quad 0 \leqslant \lambda \leqslant 1
$$

必将 y 点于 N 步内引至原点, 式中 $\lambda$ 由下式确定:

$$
\frac {\lambda}{1 - \lambda} = \frac {\| \mathbf {y} - \mathbf {p} _ {2} \|}{\| \mathbf {y} - \mathbf {p} _ {1} \|}
$$

因为过 y 点可以作无穷多直线与等时区边界相交，因而这种控制也有无穷多个，即是说自 y 点到达原点的控制不是唯一的。如果 $y_{0}$ 是等时区的顶点，则自 $y_{0}$ 到达原点的最速控制是唯一的。显然，设两个不相等的最速控制 $w_{1}(t)$ 和 $w_{2}(t)$ 都能将 $y_{0}$ 点在 N 步内控制到原点则用控制

$$
\stackrel {\circ} {u} (t) = \frac {u _ {1} (t) + u _ {2} (t)}{2}
$$

也能使 $y_{0}$ 点在 N 步内到达原点。但是根据必要条件 $u_{1}(t)$ 和 $u_{2}(t)$ 必为极性控制，这与上述假定矛盾，因为若两个控制不相等时则至少有一个时刻二者符号相反，此时 $\dot{u}(t)=0$ ，这不是极性控制，由此知 $u_{1}(t)\equiv u_{2}(t)$ 所以自顶点至原点的最速控制是唯一的。

在一定条件下，可以证明由等时区的边界点到达原点的最速控制也是唯一

的。下面我们指出一个充分条件。

设受控对象的差分方程式的基本解矩阵 D 能使 N 个向量 (N > n)

$$
\boldsymbol {r} _ {1} = - D ^ {- 1} \boldsymbol {c}, \boldsymbol {r} _ {2} = - D ^ {- 2} \boldsymbol {c}, \boldsymbol {r} _ {3} = - D ^ {- 3} \boldsymbol {c}, \dots , \boldsymbol {r} _ {N} = - D ^ {- N} \boldsymbol {c} \tag {10.7-5}
$$

中的任意 n 个 $r_{m_{1}}, r_{m_{2}}, r_{m_{3}}, \cdots, r_{m_{n}}$ 线性无关，那么自等时区边界上的任一点到达原点的最速控制是唯一的。设 $y_{1}$ 为等时区 G(NT) 边界上的任一点，如图 10.7-2 所示。因为 G(NT) 的边界是由若干个 n-1 维超平面组成的，故可以假定 $y_{1}$ 点是位于 n-1 维超平面 $P'$ 上，其外法向量为 $\psi_{1}$ ，对 G(NT) 内的任何点 y，包括超平面 $P'$ 上的点在内，有不等式

$$
\left(\boldsymbol {\psi} _ {1}, \mathbf {y} _ {1} - \mathbf {y}\right) \geqslant 0
$$

设 $u(t)$ 与 $v(t), t=0, T, 2T, \cdots, NT$ ，分别为自 $y_{1}$ 点和 y 点到达原点的控制，与前面的讨论类似，我们有

$$
\left[ \boldsymbol {\psi} _ {1}, \sum_ {\alpha = 1} ^ {N} (u [ (\alpha - 1) T ] - v [ (\alpha - 1) ] T) \boldsymbol {r} _ {\alpha} \right] \geqslant 0
$$

或改写为

$$
\sum_ {\alpha = 1} ^ {N} (\boldsymbol {\psi} _ {1}, \boldsymbol {r} _ {\alpha}) (u [ (\alpha - 1) T ] - v (\alpha - 1) T) \geqslant 0 \tag {10.7-16}
$$

由于向量序列式(10.7-5)中，任意 n 个线性无关，故关系式(10.7-16)的左端诸内积为零的项数不多于 n-1 个。否则 $\psi_{1}$ 与 n 个线性无关的向量正交，则自己一定为零向量，这与 $\psi_{1}$ 为超平面 $P'$ 的外法向量的假定相矛盾，故为不可能。从式(10.7-16)可看出，如果内积 $(\psi_{1}, r_{\alpha}) \neq 0$ ,那么自边界点 $y_{1}$ 到达原点的控制必为

$$
u [ (\alpha - 1) T ] = M \operatorname{sign} \left(\boldsymbol {\psi} _ {1}, \boldsymbol {r} _ {\alpha}\right) \tag {10.7-17}
$$

只有当上述内积为零时，u 之值才不可能由上式确定。此时为了定出控制函数 $u(t)$ 之值，需研究其他附加条件。假设有两个控制 $u^{1}(t)$ 和 $u^{2}(t), t=0, T, 2T, \cdots, NT$ 。它们均能于 N 步内把 $y_{1}$ 点引到原点，我们把两值代入到式 (10.7-6) 中，两者相减则得出

$$
\sum_ {\alpha = 1} ^ {N} \left(u ^ {1} [ (\alpha - 1) T ] - u ^ {2} [ (\alpha - 1) T ]\right) r _ {\alpha} = 0 \tag {10.7-18}
$$

$u^{1}(t)$ 和 $u^{2}(t)$ 是最优控制，它们必须满足条件式(10.7-17)，对一切 $\alpha$ 若 $(\psi_{1}, r_{\alpha}) \neq 0$ 。则有

$$
u ^ {1} [ (\alpha - 1) T ] = u ^ {2} [ (\alpha - 1) T ] = M \operatorname{sign} \left(\boldsymbol {\psi} _ {1}, \boldsymbol {r} _ {\alpha}\right)
$$

故式(10.7-18)中最多有 n-1 项系数不为零，但我们已知任意 n 个向量 $r_{m_{1}}$ , $r_{m_{2}}$ , $\cdots$ , $r_{m_{n}}$ 线性不相关，当然 n-1 个向量也线性不相关，这样若

$$
\sum_ {\alpha = 1} ^ {N} C _ {m _ {\alpha}} \boldsymbol {r} _ {m _ {\alpha}} = \mathbf {0}
$$

必有 $C_{m_{1}} = C_{m_{2}} = \cdots = C_{m_{n}} = 0$ ，这意味着对任何 t 均有等式 $u^{1}(t) \equiv u^{2}(t)$ 。由此可

以看出，自边界点到达原点是唯一的。

顺便指出，我们在上面唯一性的证明中，还得到这样一个结论：自边界点到达原点的最速控制 $u(t)$ 最多有 n-1 个时刻不为极值 $\pm M$ 。同理可推知，对应于两个顶点连线上某点的最速控制最多有一个时刻不为极值。 $G(2T)$ 的二维边界线上的任意点所对应的最速控制，最多有一个时刻的值不为 $\pm M$ ,如此等。由此，不难理解，任何自边界点到达原点的最速控制，均可由包含此点在内的边界超平面 $G(NT)$ 的顶点所对应的最速控制线性组合而成。即

$$
u (t) = \sum_ {i = 1} ^ {l} \lambda_ {i} u ^ {i} (t), \quad 1 \geqslant \lambda_ {i} \geqslant 0
$$

这里 $u^{i}(t)$ 为第 i 个顶点所对应的最速控制。

为了确定自 $G(NT)$ 的边界点至原点的最速控制的唯一性, 需指出一些判别条件。这些条件满足后, 唯一性就有了保证。我们在这里指出两个不完全等价的判别条件。

(1) 若受控对象的运动方程式为

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + \boldsymbol {b} u \tag {10.7-19}
$$

其中矩阵 A 的一切特征根均为实数，而向量

$$
\boldsymbol {c} = e ^ {A T} \int_ {0} ^ {\gamma T} e ^ {- A \tau} \boldsymbol {b} d \tau \tag {10.1-5}
$$

的一切分量均不为零，则序列式(10.7-5)中任意 n 个向量线性无关。

（2）设运动方程式的矩阵 A 为正规矩阵，即 $AA^{\tau}=A^{\tau}A$ 。若斜对称矩阵 $(A-A^{\tau})$ 的一切特征根中至少有一个，如 $b_{k}$ ，使 $ib_{k}T$ 不为 $2\pi$ 的有理数倍，那么，向量序列式(10.7-5)内任取 n 个向量都为线性无关。

以上两个条件的证明因为与综合无关，在此不再叙述。

这里我们再指出一个连续系统内曾有过的类似事实。设受控对象的运动方程为

$$
\frac {d \mathbf {y}}{d t} = A \mathbf {y} + \boldsymbol {b u}, \quad | u | \leqslant M \tag {$10.7-19^{\prime$}}
$$

式中矩阵 A 的特征根均为实数（包括零根在内)，那么有如下 n 段定理：自等时区的任何顶点到达原点的最速控制最多由 n 段组成，在每一段内最速控制 u 取值 + M 和 - M，在相邻两段内符号相反，如图 10.7-3 所示。前面已经证明，自等时区的顶点到达原点的最速控制在任一节点上，均不为零，并且满足必要条件式(10.7-13)。当式(10.7-19') 内矩阵 A 的一切特征根 $\lambda_{\alpha}, \alpha=1,2,\cdots,n$ 均为实数时，上列微分方程所对应的共轭差分方程式

$$
H ^ {*} \boldsymbol {\psi} (m T) = D ^ {\tau} \boldsymbol {\psi} (m T) \tag {10.7-20}
$$

的任何解 $\boldsymbol{\psi}(mT)=(D^{\tau})^{-m}\boldsymbol{\psi}_{0}$ 与向量 c 所构成的内积为

$$
(\boldsymbol {\psi} (m T), \boldsymbol {c}) = \sum_ {\alpha = 1} ^ {n} C _ {\alpha} a _ {\alpha} (m T) e ^ {- m T \lambda_ {\alpha}} \tag {10.7-21}
$$

上式内 $C_{\alpha}, \alpha=1,2,\cdots,n$ 为与向量 $\psi$ 有关的常数， $a_{\alpha}(mT), \alpha=1,2,\cdots,n$ 为 m 的单调函数。因此，这一内积是由 n 个单调函数组合而成，那么对自变数 m 的方程式，

$$
\varphi (m T) = (\boldsymbol {\psi} (m T), \boldsymbol {c}) = 0
$$

最多有 n-1 个实根，两个根之间的 $\varphi(mT)$ 的符号相同。故由式(10.7-13)所决定的控制函数，最多只变号 n-1 次，换言之， $u(mT)$ 最多由 n 段常值组成，至于每段内的脉冲数，则由初始条件 $\varphi_{0}$ 所单值决定。根据前面讨论可知，欲求控制函数 $u(t)$ ，只要找出 $u(t)$ 的诸变号点的位置即可。

具备了上面的几个概念后，我们可以开始研究最速控制函数的综合问题。综合的任务是找出一个以系统状态 $y=(y_{1},y_{2},\cdots,y_{n})$ 为自变量的 n 元函数 $u(y_{1},y_{2},\cdots,y_{n})$ , 将其代入式(10.1-4)中, 就得到一个差分方程式:

$$
H \mathbf {y} = D \mathbf {y} + \boldsymbol {c u} (\mathbf {y}) \tag {10.7-22}
$$

若系统式(10.1-4)为全局可控，则式(10.7-22)对任何初始条件能以最少的步数到达原点。求出这个多元函数的过程就叫做最速控制函数的综合。与常微分方程描述的系统不同的是，对任取的初始条件 $y_{0}$ , 最速控制一般没有唯一性, 这给综合问题带来了一些困难。但是, 如果能够在很多种最速控制中选定一种来加以实现, 综合问题也就得到了解决。

最速控制综合方法的基本思想和连续系统一样，是寻找开关曲面，在状态空间中，求出等时区 $G(NT)$ ，当 $N$ 足够大时，它将包含以原点为中心的足够大的区域。在 $G(NT)$ 中按控制 $u$ 的不同取值，划分为两个半区域 $G^{+}(NT)$ 和 $G^{-}(NT)$ ，在 $G^{+}(NT)$ 中 $u = +M$ ，而在 $G^{-}(NT)$ 中 $u = -M$ 。当 $N > n$ 时，两个半区域的分界面将是 $n - 1$ 维超平面。显然，如果系统是全局可控的，当 $N \to \infty$ 时， $G(NT)$ 的这种分界曲面也将随之扩大，最后能将整个状态空间分为两半。用一个函数 $f$ 表示这个分界曲面，开关曲面上的点应满足等式 $f(y) = 0$ ；在半空间 $G^{-}$ 中 $f(y) < 0$ ，在半空间 $G^{+}$ 中 $f(y) > 0$ 。由 $f(y) = 0$ 所决定的这个曲面就是开关曲面。于是最速控制就可以表示成

$$
\mathring {u} (\mathbf {y}) = M \text { sign } f (\mathbf {y}) \tag {10.7-23}
$$

对于给定的离散系统，用计算机来求出开关曲面的办法很多。如果矩阵 D 的特征根是 n 个不同的实数，则可以根据本节中前面讨论过的性质（任一最速控制由 n 段组成),应用逆轨线方法求出整个开关曲面。计算过程如下:

(1) 将原方程式中的过程逆转，

$$
\mathbf {y} (N T) = D ^ {- 1} \mathbf {y} ((N + 1) T) - D ^ {- 1} \mathbf {c u} (N T)
$$

或者

$$
\mathbf {y} ((N - 1) T) = D ^ {- 1} \mathbf {y} (N T) - D ^ {- 1} \mathbf {c u} ((N - 1) T) \tag {10.7-24}
$$

(2) 令 $u \equiv +M, y(0) = 0$ , 求解式 (10.7-24) 得到一组解 $y(0), y(-T), y(-2T), \cdots, y(-NT), \cdots$ 。用直线将这些点分段连接起来, 得到一条由原点出发的折线, 记为 $\Gamma_1^+$ 。

（3）令 $y(0)=0, u \equiv -M$ 递推求解式(10.7-24)，可得到另一条发自原点的折线 $\Gamma_{1}^{-}$ 。

（4）将 $\Gamma_{1}^{+}$ 和 $\Gamma_{1}^{-}$ 上任何点作为初始条件求解式(10.7-24)，分别取 u 为 -M 和 +M，使其符号与第一次取号相反。当初始条件历遍 $\Gamma_{1}^{+}$ 和 $\Gamma_{1}^{-}$ 后就得到一个二维曲面，记为 $\Gamma_{2}$ 。当然 $\Gamma_{2}$ 是由 $\Gamma_{2}^{+}$ 和 $\Gamma_{2}^{-}$ 组成的，第一半是由 $\Gamma_{1}^{-}$ 和 $u\equiv+M$ 生成的，第二半是以 $\Gamma_{1}^{+}$ 为初始条件， $u\equiv-M$ 生成的；

（5）以此类推到第 $n - 1$ 次就得到一个 $n - 1$ 维超曲面 $\Gamma_{n - 1}$ 。用某一满足前述要求的 $n$ 元函数 $f(\mathbf{y}) = 0$ 去逼近 $\Gamma_{n - 1}$ ，最速控制函数 $\dot{u} (\mathbf{y})$ 即可按式(10.7-23)确定。

由于这种方法的近似性，在原点附近可能发生振荡。为了克服这一缺点，系统设计可以分为两种工作状态进行。当大偏差时采用式(10.7-23)所确定的控制规律，在小偏差时采用第 10.6 节内所介绍的线性控制规律，这样就可以避免系统在原点附近的振荡现象。上面讨论的方法只对矩阵 $D$ 有纯实根的情况有效。对任意矩阵 $D$ 的最速控制综合是比较复杂的，没有简便的方法可以采用。本章后的参考文献[10]中介绍了一种较为精密的方法，应用的范围可以更广泛些。

对于二阶系统，由于可以在平面上作图，因此用等时区的方法可以有效地求出任何系统的开关曲线。我们再回过来讨论本节前面举的例。我们把图 10.7-1 中的四个等时区画在一块，就可以很明显地找出开关曲线了。从图 10.7-4 中可以看出，一切属于 $G(4T)$ 而不属于 $G(3T)$ 的点 $\pmb{y}$ 都可以用 $u = 1$ 或 $u = -1$ 一步到达 $G(3T)$ 而不能到达 $G(2T)$ 。 $G(4T)$ 的一切边界点一步以后只能到达 $G(3T)$ 的边界，而不属于 $G(3T)$ 的 $G(4T)$ 的内点则可以于一步后进入 $G(3T)$ 的内部，但不可能进入 $G(2T)$ 。由 $\mathbf{r}_1, \mathbf{r}_2, \mathbf{r}_3$ 和 $\mathbf{r}_4$ 连成的折线 $\Gamma_1^+$ ，由 $-\mathbf{r}_1, -\mathbf{r}_2, -\mathbf{r}_3$ 和 $-\mathbf{r}_4$ 连成的折线记为 $\Gamma_1^-$ ，它们和成 $\Gamma_1$ 。在折线 $\Gamma_1$ 的上面 $u$ 都必须取 $+1$ ，在折线 $\Gamma_1$ 的下面 $u$ 应取 $-1$ 。因此，折线 $\Gamma_1$ 正是待求的开关曲线。这里有两个问题。一个问题是靠近 $\Gamma_1$ 的点有可能在一步之后超过开关线而进入另一半平面，甚至进入步数比原来更多的等时区。另一个问题是 $G(2T)$ 中的情况，这里几乎所有的点按照规律式(10.7-23)都不能在两步之内达到原点。因此对平面上多数点来说，控制值总取极值的控制并不一定是最速控制。为了实现最速控制必须对控制规律作适当修改，这方面的详细研究读者可参看文献[10]。

这里需要指出，线性断续系统的最速控制与线性连续系统不同，并不是所有时刻最速控制都取极值。这是因为线性断续系统的控制只能在采样时刻变化，并且这样的取值要延续一个采样周期，而线性连续系统的控制在任何时刻都可变 化。当采样周期愈来愈小时，线性断续系统的最速控制就愈来愈趋于线性连续系统的最速控制。

#### 10.8 对固定的初始状态求最速控制

在上一节，我们主要讨论了最速离散控制系统的综合方法，可以看出主要在于分析开关曲面，然后根据开关曲面来设计采样系统的控制装置。对于系统可控区内任意点作为初始状态的情形，很明显，控制装置的任务是对于任意初始状态都能决定相应的控制，能使系统以最短的时间归零。这种方法对于低阶系统是有效的，而且也必须这样才能解决问题。对于阶数高的采样系统，按上述方法就比较复杂。在第八章我们曾经讨论过有一类系统，初始状态已给定，而且这种系统只使用一次，在这种情况下，只要决定与初始状态相对应的控制，即具体求出控制量 u 在 $t=0, T, 2T, \cdots$ 的值就能满足要求，这一节就来讨论关于对给定的初始条件最速控制的一种综合方法。

假设受控系统的误差用 y 表示, 初始误差等于 $y_{0}$ , 系统特性由方程(10.1-4)描绘, 控制量 u 的取值范围受到式(10.7-2)的限制。要求选择满足限制条件的控制, 使系统初始误差 $y_{0}$ 在最短时间之内归零。

这里仍然从等时区入手。前面已经谈到，在满足某些条件情况下，当 $N \geqslant n$ （ $n$ 是系统阶数）时，等时区 $G(NT)$ 是一个 $n$ 维凸多面体，它的边界由有限个小于或等于 $n - 1$ 维的超平面组合而成。当 $N$ 增大时， $G(NT)$ 随着 $N$ 的增大而向外扩张，用 $z(N, \psi)$ 表示等时区 $G(NT)$ 边界上的点， $G(NT)$ 过该点支面的外法向量等于 $\psi$ ，由 $z(N, \psi)$ 到达原点的控制形如式(10.7-17)所示

$$
u [ (\alpha - 1) T ] = M \operatorname{sign} (\boldsymbol {\psi}, \boldsymbol {r} _ {\alpha})
$$

其中 $\alpha=1,2,\cdots,N,$

$$
\boldsymbol {z} (N, \boldsymbol {\psi}) = u _ {0} (\boldsymbol {\psi}) \boldsymbol {r} _ {1} + u _ {1} (\boldsymbol {\psi}) \boldsymbol {r} _ {2} + \dots + u _ {N - 1} (\boldsymbol {\psi}) \boldsymbol {r} _ {N} \tag {10.8-1}
$$

当 $z(N,\psi)$ 是 $G(NT)$ 的顶点时， $(\psi,r_{\alpha})\neq0,\alpha=1,2,\cdots,N$ ，当 $z(N,\psi)$ 不是顶点时，则在 N 个 $(\psi,r_{\alpha})$ 中至多有 n-1 个等于零，这时候与其相应的控制是绝对值小于 M 的任意实数。有了等时区的概念，那么要求系统的初始误差 $y_{0}$ 以最短时间归零的问题可以理解为：在 n 维空间中给定一点 $y_{0}$ ，另外有一个随着 N 的增加而向外扩张的凸多面体 $G(NT)$ ，使 $y_{0}\in G(N_{0}T)$ ，而 $y_{0}\in G[(N_{0}-1)T]$ 的正整数 $N_{0}$ ，就是使系统由 $y_{0}$ 归零的最少步数， $N_{0}T$ 就是归零的最短时间。如果 $y_{0}$ 恰好位于 $G(N_{0}T)$ 的边界面上，那么最优控制由式(10.7-17)确定，这时候，根据式(10.7-6)

$$
\mathbf {y} _ {0} = u _ {0} \left(\boldsymbol {\psi} _ {0}\right) \mathbf {r} _ {1} + u _ {1} \left(\boldsymbol {\psi} _ {0}\right) \mathbf {r} _ {2} + \dots + u _ {N - 1} \left(\boldsymbol {\psi} _ {0}\right) \mathbf {r} _ {N} \tag {10.8-2}
$$

其中 $\psi_{0}$ 表示 $G(N_{0}T)$ 过 $y_{0}$ 点的支面外法向量。另一种可能性是 $y_{0}$ 位于 $G(N_{0}T)$ 的内部，这时候最优控制不是唯一的。进一步分析就会发现，问题的焦点在于，不 容易根据 $y_{0}$ 来确定使系统由 $y_{0}$ 归零的最短时间 $N_{0} T$ ，以及 $y_{0}$ 究竟是 $G(N_{0} T)$ 的边界点呢？还是 $G(N_{0} T)$ 的内点。为此从直观方面来加以考虑。对于任意给定小于 $N_{0}$ 的正整数 N，如果控制量的限制条件 $|u| \leqslant M$ 的界限放得宽一些，并且当控制量能取较大值时，系统可以在 NT 时间内，由 $y_{0}$ 归零。反之，对于任意大于 $N_{0}$ 的正整数，即使控制量的取值范围缩小一些，也能使系统由 $y_{0}$ 在 NT 时间内归零。这一事实是很简单而明显的，说得确切一些，把式(10.7-2)的限制条件改变成

$$
\mid u \mid \leqslant \alpha M \tag {10.8-3}
$$

其中 $\alpha$ 满足下述条件

$$
0 <   \alpha <   + \infty \tag {10.8-4}
$$

在 $u$ 满足式(10.8-3)的限制条件情况下，相应的等时区用符号 $G_{\alpha}(NT)$ 表示，通过 $\alpha$ 的变化就可以把等时区 $G(NT)$ 加以放大或缩小。很明显 $G_{\alpha}(NT)$ 也具有 $G(NT)$ 所具有的一切性质，且随着 $\alpha$ 的变化而连续变化。引进 $G_{\alpha}(NT)$ 以后，对于给定的 $y_0$ ，一定可以确定一个相应的 $\alpha_0$ ，使 $y_0$ 位于 $G_{\alpha_0}(NT)$ 的边界面上，这样就排除了 $y_0$ 可能是 $G_{\alpha}(NT)$ 的内点的情形，由于进行系统设计时，限制条件是预先给定而不能改变的，即式(10.7-2)中的 $M$ 是给定数，所以最后确定的控制仍然不能超过 $M$ 。这就需要确定适当的最短归零时间 $N_0T$ 。很明显， $\alpha_0,N_0$ 和 $N$ 之间有如下关系：

如果 $N < N_{0}$ ，则 $\alpha > 1$ ; $N \geqslant N_{0}$ ，则 $\alpha \leqslant 1$ (10.8-5)

由 $\alpha_{0}$ 是否大于 1, 就可以用来决定 $N_{0}$ 。为了确定 $\alpha_{0}$ 引进函数

$$
F (\boldsymbol {\psi}, \alpha) = (\boldsymbol {\psi}, [ - \mathbf {y} _ {0} + \alpha \mathbf {z} (N, \boldsymbol {\psi}) ]) \tag {10.8-6}
$$

上述函数中的 $z(N, \psi)$ 表示 $G(NT)$ 边界上的点，它的表达式由式(10.8-1)给出。由于 $G(NT)$ 具有凸性，因此当 $y \in G(NT)$ 则有

$$
(\boldsymbol {\psi}, - \boldsymbol {z} (N, \boldsymbol {\psi}) + \boldsymbol {y}) \leqslant 0
$$

或

$$
(\boldsymbol {\psi}, \mathbf {z} (N, \boldsymbol {\psi})) = \max _ {\gamma \in G (N T)} (\boldsymbol {\psi}, \mathbf {y}) \tag {10.8-7}
$$

又由于 $G(NT)$ 包含原点, 所以上式左端是一个非负的量。如果只考虑满足下列条件的 $\psi$ :

$$
(\boldsymbol {\psi}, - \mathbf {y} _ {0}) <   0 \tag {10.8-8}
$$

那么， $F(\psi, \alpha = 0) < 0$ ，而 $F(\psi, \alpha)$ 是 $\alpha$ 的连续单调递增函数，任给一个满足式(10.8-8)的 $\psi$ ，就可以由 $\psi$ 确定一个相应的 $\alpha(\psi)$ ，使

$$
F (\boldsymbol {\psi}, \alpha (\boldsymbol {\psi})) = 0 \tag {10.8-9}
$$

由于函数 F 表示两个向量的内积, 所以有两种情形使式(10.8-9)成立:

(1) 向量 $\psi$ 和向量 $-y_{0} + az(N, \psi)$ 正交。

(2) $-\mathbf{y}_0 + \alpha \mathbf{z}(N, \boldsymbol{\psi}) = \mathbf{0}$ 。

我们感兴趣的是第(2)种情形。下面就来分析使第二种情形成立的 $\psi_0$ 和 $\alpha_0(\psi_0)$ 。这时候

$$
\mathbf {y} _ {0} = \alpha_ {0} (\boldsymbol {\psi} _ {0}) \mathbf {z} (N, \boldsymbol {\psi} _ {0}) \tag {10.8-10}
$$

即 $y_{0}$ 是 $G_{\alpha_{0}}(NT)$ 边界上的点， $\alpha_{0}$ 所具有的性质可以这样分析，对任意符合式(10.8-8)的 $\psi, \psi \neq \psi$ ，那么由式(10.8-1)，这个 $\psi$ 将确定 $G_{\alpha_{0}}(NT)$ 上的某一点 $\alpha_{0}z(\psi)$ ，根据 $G_{\alpha_{0}}(NT)$ 的凸性，向量 $-y_{0} + \alpha_{0}z(NT)$ 与 $\psi$ 的夹角小于 $\pi/2$ 。于是得到

$$
F (\boldsymbol {\psi}, \alpha_ {0}) = (\boldsymbol {\psi}, - \mathbf {y} _ {0} + \alpha_ {0} z (N, \boldsymbol {\psi})) > 0
$$

前面已经提到函数 $F(\psi, \alpha)$ 是 $\alpha$ 的单调增函数，故可以找到一个 $\alpha(\psi), 0 < \alpha(\psi) < \alpha_0$ ，使 $F(\psi, \alpha(\psi)) = 0$ 成立。这个结论对于任意满足式(10.8-8)的 $\psi$ 都成立，只要 $\psi \neq \psi_0$ ，那么 $\alpha(\psi)$ 就小于 $\alpha_0$ ，因此得出 $\psi_0$ 使 $\alpha(\psi)$ 取极大值的结论。从 $F(\psi, \alpha(\psi)) = 0$ 解出 $\alpha(\psi)$

$$
\alpha (\boldsymbol {\psi}) = \frac {(\boldsymbol {\psi} , \mathbf {y} _ {0})}{(\boldsymbol {\psi} , \mathbf {z} (N , \boldsymbol {\psi}))} \tag {10.8-11}
$$

然后求 $\alpha(\psi)$ 的极大值就可以得到 $\alpha$ ，即

$$
\alpha_ {0} \left(\boldsymbol {\psi} _ {0}\right) = \max _ {\boldsymbol {\psi}} \alpha (\boldsymbol {\psi}) = \max _ {\boldsymbol {\psi}} \frac {\left(\boldsymbol {\psi} , \mathbf {y} _ {0}\right)}{\left(\boldsymbol {\psi} , z (N , \boldsymbol {\psi})\right)} \tag {10.8-12}
$$

这里 $\psi$ 只受到 $(\psi, -y_0) < 0$ 的限制。求 $\alpha(\psi)$ 的极大值就仅仅是多元函数的极值问题。

以下我们不直接求 $\alpha(\psi)$ 的极大值，而间接地用最速下降法求 $F(\psi, \alpha)$ 的极小值。逐步逼近的步骤大致是，先取一个 $\psi_{1}$ ，由 $\psi_{1}$ 决定 $\alpha_{1}(\psi_{1})$ ，使 $F(\psi_{1}, \alpha_{1}(\psi_{1})) = 0$ 。然后求 $F(\psi, \alpha_{1})$ 的极小，这时候 $\alpha_{1}$ 是固定的数。可以知道

$$
\operatorname{grad} F (\boldsymbol {\psi}, \alpha_ {1}) = - \mathbf {y} _ {0} + \alpha_ {1} \mathbf {z} (N, \boldsymbol {\psi}) \tag {10.8-13}
$$

令

$$
\boldsymbol {\psi} _ {2} = \boldsymbol {\psi} _ {1} - K [ - \mathbf {y} _ {0} + \alpha_ {1} \mathbf {z} (N, \boldsymbol {\psi} _ {1}) ] \tag {10.8-14}
$$

其中 $K$ 是正数，只要适当选择 $K$ ，那么就求得一个新的 $\psi_{2}$ ，并且可以证明此 $\psi_{2}$ 仍满足条件式(10.8-8)，且

$$
F \left(\boldsymbol {\psi} _ {2}, \alpha_ {1}\right) <   F \left(\boldsymbol {\psi} _ {1}, \alpha_ {1}\right) = 0 \tag {10.8-15}
$$

因为 F 是 $\alpha$ 的单增函数, 由 $\psi_{2}$ 就可以确定一个 $\alpha_{2}(\psi_{2})$ , 使得

$$
F (\boldsymbol {\psi} _ {2}, \alpha_ {2} (\boldsymbol {\psi} _ {2})) = 0 \tag {10.8-16}
$$

并且

$$
\alpha_ {2} \left(\boldsymbol {\psi} _ {2}\right) > \alpha_ {1} \left(\boldsymbol {\psi} _ {1}\right) \tag {10.8-17}
$$

可以看出，使 $F(\psi,\alpha)$ 最速下降的方向实际上也就是使 $\alpha(\psi)$ 最速上升的方向。求得 $\psi_{2}$ 后，再以它代替原先的 $\psi_{1}$ 继续进行，最后逼近到 $\psi_{0}$ 。

按上述步骤进行时，可能发生这种情况，到第 i 次逼近时, $(\boldsymbol{\psi}_{i},\boldsymbol{r}_{\alpha})$ 中有 $\sigma$ 个等 于 $0(1 \leqslant \sigma \leqslant n-1)$ 。其原因在于 $G_{\alpha}(NT)$ 的边界面由有限个小于等于 n-1 维的平面组成，因此由 $\psi_{i}$ 决定的控制量在 $\sigma$ 个采样点的值只能确定到绝对值小于 M 的程度，遇到这种情形时，把未能完全确定的量表示成 $u_{N_{1}}, u_{N_{2}}, \cdots, u_{N_{\sigma}}$ ，然后求解退化线性代数方程

$$
- \mathbf {y} _ {0} + \alpha \mathbf {z} (N, \boldsymbol {\psi} _ {i}) = 0 \tag {10.8-18}
$$

把 $y_{0}$ 和 $z(N,\psi_{i})$ 中确定的项移到等式的另一端，并且用 $\beta$ 表示，于是上式可写成

$$
u _ {N _ {1}} \boldsymbol {r} _ {N _ {1}} + u _ {N _ {2}} \boldsymbol {r} _ {N _ {2}} + \dots + u _ {N _ {\sigma}} \boldsymbol {r} _ {N _ {\sigma}} = \beta \tag {10.8-19}
$$

如果解上述方程所得 $\sigma$ 个量的绝对值小于等于 $M$ ，这就意味着控制是可准控制，在 $\sigma$ 个量中只要有一个的绝对值大于 $M$ ，则控制不是可准控制，当出现这种情况时只消把 $\sigma$ 个量都取为 0（或者每个量的绝对值都小于 $M$ 的一组数），然后求出 $\operatorname{grad} F(\boldsymbol{\psi}_i, \alpha(\boldsymbol{\psi}_i))$ ，继续进行。有一点重要的事实是值得注意的，对于给定的 $\mathbf{y}_0$ ，我们是从较小的正整数 $N$ 开始计算的，在计算过程中，没有必要求出 $\alpha_0$ ，当第 $i$ 次逼近，只要 $\alpha(\boldsymbol{\psi}_i) > 1$ ，就不必继续下去，因为再往下其值会更大。由关系式(10.8-5)知，一旦 $\alpha > 1$ ，说明 $N < N_0$ ，此时自然把 $N$ 换成 $N + 1$ 再进行。这样交替的修改 $\boldsymbol{\psi}$ 和 $N$ ，当 $N = N_0 - 1$ 时， $\alpha_0 > 1$ 而 $N = N_0$ 时， $\alpha_0 \leqslant 1$ ，那么 $N_0 T$ 就是使系统由 $\mathbf{y}_0$ 归零的最短时间，这个使 $\alpha$ 取极大值 $\alpha_0$ 的 $\boldsymbol{\psi}_0$ ，就完全决定了最速控制。

以上只叙述了从初始状态，到达原点的最速控制综合方法，至于到达给定区域的问题，完全可以用类似方法进行，这里不再加以讨论。具体计算方法及例题读者可参看文献[8]。

#### 10.9 具有其他指标的最优控制

前面几节中，我们主要讨论了最速控制的一些特性和控制装置的设计，即所谓综合问题。在某些系统中速度问题并不是特别重要的，例如卫星的姿态控制或某一慢变过程的控制，那里有关于能量消耗或均方误差方面的要求，于是主要要求将是按别的指标达到尽量好的性能。正像在连续系统中那样，这种质量指标常可以用下列形式表示出来

$$
J = \sum_ {i = 0} ^ {k - 1} f _ {0} (\boldsymbol {x} (i T), \boldsymbol {u} (i T)) = \min \tag {10.9-1}
$$

式中 $x(iT)$ 和 $u(iT)$ 是某一离散受控系统的相应维数的状态向量和控制向量，它们满足方程组

$$
H \boldsymbol {x} (k T) = \boldsymbol {x} ((k + 1) T) = \boldsymbol {f} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \tag {10.9-2}
$$

式中 $f=(f_{1},f_{2},\cdots,f_{n})$ ；我们先假定 $f_{i}$ 是各自变量的连续可微函数，而不必是线性函数。

类似于在连续系统中的处理方法，我们引进新的状态变量 $x_{0}(kT)=J$ , 由式

(10.9-1)显然有

$$
H x _ {0} (k T) = x _ {0} ((k + 1) T) = f _ {0} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) + x _ {0} (k T) \tag {10.9-3}
$$

现在把式(10.9-3)和式(10.9-2)联立起来，就得到一个扩大了的方程组

$$
H x _ {0} (k T) = x _ {0} (k T) + f _ {0} (\boldsymbol {x} (k T), \boldsymbol {u} (k T))
$$

$$
H x _ {1} (k T) = f _ {1} (\boldsymbol {x} (k T), \boldsymbol {u} (k T))
$$

...

$$
H x _ {n} (k T) = f _ {n} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \tag {10.9-4}
$$

上式内符号 H 是右移算子。

为了下面讨论的需要，再引进一个 $n+1$ 维的向量函数 $\overline{\psi}=(\psi_{0},\psi_{1},\psi_{2},\cdots,\psi_{n})$ ,用它和状态向量构成函数

$$
\begin{array}{l} \Pi (k T) = (\overline {{{{\psi}}}} (k T), \overline {{{{x}}}} (k T)) \\ = \psi_ {0} (k T) \left(x _ {0} (k T) + f _ {0} (k T)\right) + \sum_ {\alpha = 1} ^ {n} \psi_ {\alpha} (k T) f (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \tag {10.9-5} \\ \end{array}
$$

并要求向量 $\overline{\psi}(kT)$ 满足方程组

$$
H ^ {*} \psi_ {i} (k T) = \frac {\partial \Pi}{\partial x _ {i}}, \quad i = 0, 1, 2, \dots , n \tag {10.9-6}
$$

$H^{*}$ 是左移算子, 将上式展开后有

$$
\begin{array}{l} H ^ {*} \psi_ {0} (k T) = \psi_ {0} ((k - 1) T) = \frac {\partial \Pi}{\partial x _ {0}} = \psi_ {0} (k T) \\ H ^ {*} \psi_ {1} (k T) = \psi_ {1} ((k - 1) T) = \frac {\partial \Pi}{\partial x _ {1}} = \sum_ {\alpha = 0} ^ {n} \psi_ {\alpha} (k T) \frac {\partial f _ {\alpha}}{\partial x _ {1}} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \\ H ^ {*} \psi_ {n} (k T) = \psi_ {n} ((k - 1) T) = \frac {\partial \Pi}{\partial x _ {n}} = \sum_ {\alpha = 0} ^ {n} \psi_ {\alpha} (k T) \frac {\partial f _ {\alpha}}{\partial x _ {n}} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \tag {$10.9-6^{\prime$}} \\ \end{array}
$$

...

所谓最优控制问题，是指对给定的初始条件 $\overline{\boldsymbol{x}}(0)=\overline{\boldsymbol{x}}_{0}=(0,x_{01},x_{02},\cdots,x_{0n})$ ，求控制函数 $\dot{\boldsymbol{u}}(kT)=(\dot{\boldsymbol{u}}(kT),\dot{\boldsymbol{u}}(kT),\cdots,\dot{\boldsymbol{u}}(kT)),k=0,1,\cdots$ ，使系统式(10.9-2)在有限时间内归零。假定 $N_{0}T$ 表示到达原点的时间，那么最优控制应使 $x_{0}(N_{0}T)$ 达最小值。

用第九章内曾用过的方法，可以把极大值原理移植到离散系统的情况中来。类似在第 9.6 节中的讨论，可以得到最优控制所必须满足的极值条件。用 $\dot{\boldsymbol{x}}(kT)$ 和 $\dot{\boldsymbol{u}}(kT)$ 分别表示最优轨迹和与其对应的最优控制。那么，必存在一个非零向量函数 $\dot{\boldsymbol{\psi}}(kT), k=0,1,\cdots,N_{0}$ 满足式(10.9-6),使在每一时刻均有

$$
\Pi (\stackrel {\circ} {\boldsymbol {x}} (k T), \stackrel {\circ} {\boldsymbol {\psi}} (k T), \stackrel {\circ} {\boldsymbol {u}} (k T)) = \max _ {\boldsymbol {u} \in U} \Pi (\stackrel {\circ} {\boldsymbol {x}} (k T), \stackrel {\circ} {\boldsymbol {\psi}} (k T), \boldsymbol {u})
$$

$$
k = 0, 1, \dots , N _ {0} \tag {10.9-7}
$$

上式内 U 是控制 u 的被允许的取值集合；而且，沿最优轨迹恒有

$$
\Pi (\stackrel {\circ} {\boldsymbol {x}} (k T), \stackrel {\circ} {\boldsymbol {\Psi}} (k T), \stackrel {\circ} {\boldsymbol {u}} (k T)) = \text { const } \geqslant 0
$$

$$
k = 0, 1, \dots , N _ {0} \tag {10.9-8}
$$

这就是极大值原理对离散系统的应用。它的证明留给读者。实际上这个证明与第九章中的证明完全类似，只需要注意到三点：第一，这里对最优轨迹可以用点变分，而不是像在连续系统中那样在小区间内变分；第二，系统式(10.9-4)的变分 $\delta\bar{x}$ 满足方程式

$$
H \delta x _ {i} (k T) = \sum_ {\alpha = 0} ^ {n} \frac {\partial f _ {\alpha} \left(\mathring {x} _ {0} (k T) , \mathring {u} _ {0} (k T)\right)}{\partial x _ {i}} \delta x _ {i} (k T), \quad i = 0, 1, \dots , n
$$

它与 $\overline{\psi}(kT)$ 之间有关系式

$$
(\stackrel {\circ} {\boldsymbol {\psi}} (k T), \overline {{\boldsymbol {x}}} (k T)) = \text { const } \tag {10.9-9}
$$

第三， $\bar{\psi}(N_{0}T)$ 是一切变分后的轨线终点构成的锥体的外法向量。

注意到上述事实和式 $(10.9-6')$ 的第一式知 $\psi_{0}$ 为常数。又因式 $(10.9-7)$ 是一个线性齐次方程组，故可取 $\psi_{0}=-1$ 。于是，决定最优控制的全部问题变为两点边值问题

$$
H \boldsymbol {x} (k T) = \boldsymbol {f} (\boldsymbol {x} (k T), \boldsymbol {u} (k T)), \boldsymbol {x} (0) = \boldsymbol {x} _ {0}
$$

$$
H ^ {*} \boldsymbol {\psi} (k T) = F (\boldsymbol {x} (k T), \boldsymbol {u} (k T)) \boldsymbol {\psi} (k T), \boldsymbol {\psi} (N _ {0} T) = \boldsymbol {\psi} _ {0}
$$

$F(\boldsymbol{x}(kT),\boldsymbol{u}(kT))$ 是由 $\frac{\partial f_{i}}{\partial x_{i}}$ 构成的 $(n+1)\times(n+1)$ 阶方阵

$$
F = \left( \begin{array}{c c c c} 1, & 0 & \dots & 0 \\ \frac {\partial f _ {0}}{\partial x _ {1}} & \frac {\partial f _ {1}}{\partial x _ {1}} & \dots & \frac {\partial f _ {n}}{\partial x _ {1}} \\ \vdots & \vdots & & \vdots \\ \frac {\partial f _ {0}}{\partial x _ {n}} & \frac {\partial f _ {1}}{\partial x _ {n}} & \dots & \frac {\partial f _ {n}}{\partial x _ {n}} \end{array} \right)
$$

最后 $u(kT)$ 应满足极值条件式(10.9-7)。如果从某些其他考虑能决定边值条件 $\psi_{0}$ ，那么问题就完全解决了。实质上在第 10.7 节中我们对最速控制问题就是用等时区的概念来确定 $\psi_{0}$ 的。

最后，我们应用上面得到的条件，具体讨论一下具有二次型指标的线性离散系统的最优控制问题。设到达终点的时间 $N_{0} T$ 是给定的，而且终点是不固定的，指标泛函是

$$
\begin{array}{l} J = \sum_ {i = 0} ^ {N _ {0} - 1} (\boldsymbol {x} (i T), Q \boldsymbol {x} (i T)) + \sum_ {i = 0} ^ {N _ {0} - 1} (\boldsymbol {u} (i T), R \boldsymbol {u} (i T)) \\ + \left(\boldsymbol {x} (N _ {0} T), S \boldsymbol {x} (N _ {0} T)\right) \tag {10.9-10} \\ \end{array}
$$

式中 Q, R, S 都是正定矩阵。记 $x_{0}(N_{0}T)=J$ ，于是有

$$
H x _ {0} (k T) = x _ {0} (k T) + (\boldsymbol {x} (k T), Q \boldsymbol {x} (k T)) + (\boldsymbol {u} (k T), R \boldsymbol {u} (k T))
$$

$$
\boldsymbol {x} _ {0} (0) = (\boldsymbol {x} (N _ {0} T), S \boldsymbol {x} (N _ {0} T)) \tag {10.9-11}
$$

受控对象的方程式是

$$
H \boldsymbol {x} (k T) = D \boldsymbol {x} (k T) + C \boldsymbol {u} (k T), \quad \boldsymbol {x} (0) = \boldsymbol {x} _ {0} \tag {10.9.12}
$$

构造函数

$$
\begin{array}{l} \Pi (k T) = \psi_ {0} [ x _ {0} (k T) + (\boldsymbol {x}, Q \boldsymbol {x}) + (\boldsymbol {u}, R \boldsymbol {u}) ] + (\psi (k T), D \boldsymbol {x} (k T)) \\ + (\boldsymbol {\psi} (k T), C \boldsymbol {u} (k T)) \tag {10.9-13} \\ \end{array}
$$

我们看到，函数 $\Pi(kT)$ 在每一时刻都是 u 的二次型。注意到 $\psi = -1$ ,有

$$
\Pi (k T) = g (\boldsymbol {x}, \boldsymbol {\psi}) + (\boldsymbol {\psi} (k T), C \boldsymbol {u} (k T)) - (\boldsymbol {u} (k T), R \boldsymbol {u} (k T))
$$

由最大值条件知, $\Pi$ 的最大值正是 u 对应的极值。于是由极值条件

$$
\frac {\partial \Pi}{\partial u _ {i}} = 0, \quad i = 1, 2, \dots , r \tag {10.9-14}
$$

立即可以求出最优控制与 $\psi(kT)$ 之间的线性关系

$$
\boldsymbol {u} (k T) = \frac {1}{2} R ^ {- 1} C ^ {\pi} \boldsymbol {\psi} (k T) \tag {10.9-15}
$$

式中 $C^{x}$ 是 C 的转置矩阵。把 $u(kT)$ 的值代入式(10.9-12)，并同时按式(10.9-6)写出 $\psi(kT)$ 所应满足的方程式，最后便得到最优控制系统的结构

$$
\begin{array}{l} H \boldsymbol {x} (k T) = D \boldsymbol {x} (k T) + \frac {1}{2} C R ^ {- 1} C ^ {\tau} \boldsymbol {\psi} (k T), \quad \boldsymbol {x} (0) = \boldsymbol {x} _ {0} \\ H ^ {*} \boldsymbol {\psi} (k T) = D ^ {\tau} \boldsymbol {\psi} (k T) - 2 Q \boldsymbol {x} (k T), \quad \boldsymbol {\psi} (N _ {0} T) = \boldsymbol {\psi} _ {0} \tag {10.9-16} \\ \end{array}
$$

我们看到，为了具体地求出最优控制，在这两个联立的方程组中，必须也只需求出 $\psi(kT)$ 在另一端点的边界条件 $\psi(N_{0}T)=\psi_{0}$ ,这就是两点边值问题。在这个具体问题中，应该存在 $x_{0}$ 和 $\psi_{0}$ 之间的一一对应关系，如何去求出这种关系的表达式，就是最优控制的综合问题。这需要其他的补充知识，例如，像第九章中所作过的那样，把综合问题转化成一个黎卡提矩阵方程的求解问题；或者应用等损耗区的概念去求出 $x_{0}$ 和 $\psi_{0}$ 之间的关系等。最后，还可以用数字计算方法去迭代逼近，求出使 J 达极小值的 $\psi_{0}$ 。

#### 10.10 参考文献

[1] 钟士模、郑维敏、童诗白，电子调节器，清华大学学报，1956,2,164-169.

[2] 王新民，采用多拍脉冲的快速脉冲系统，自动化学报,1(1963),1.

[3] 范崇惠、施颂平、余雅声，内燃机车驾驶自动化，自动化学报，1(1963)，1.

[4] 薛景瑄, 脉冲控制系统综述, 自动化技术进展, 科学出版社, 1963.

[5] 王传善等, 远动技术, 上册, 科学出版社, 1965.

[6] 赵访熊, Power Series Transform, 清华大学科学报告, 5, A 类, 1948, 2, 122-138.

[7] 福田武熊, 差分方程, 穆鸿基译, 上海科学技术出版社, 1962.

[8] 戴汝为、李宝绶，关于离散线性快速控制的一个计算方法，中国自动化学会代表大会报告，北京，1965.

[9] 宋健、韩京清，最速控制系统的分析与综合，自动化学报，3(1965)，3.

[10] 宋健、韩京清、唐志强，线性常系数断续系统最速控制的综合，常微分方程会议报告，北京，1962.

[11] Bertram, J. E., Factors in the Design of Digital Controllers for Sampled-Data Feedback control Systems, Trans. AIEE, 75(1956), 151–159.

[12] Cheng, G-S.J., Tarn, T.J., & Elliot, D.L., Controllability of Bilinear Systems, In “Lecture Note in Economics and Mathematical Systems, Variable Structure Systems with Application to Economics and Biology”, ed. by A. Ruberti & R. R. Mohler, Springer-Verlag. New York, 1975.

[13] Chestnut, H., Dabul, A., & Leiby. D., Analog computer study of sampled-data systems, Trans. AIEE 78(1959). pt. II. 634–640.

[14] Desoer. C. A., Polak. E., & Wing J., Theory of Minimum Time Discrete Regulators Proc. of the Second IFAC Congress, Basel, 1963.

[15] Jury, E. I., Sampled-Data Control Systems. New York, 1958.

[16] Kalman, R. E., Optimal nonlinear control of saturating systems by intermittent action, IRE, Wescon. Conv. Record, 1(1957), part 4, 130-135.

[17] Kranc, G. M., Compensation of an error-sampled systems by multirate controller, Trans., AIEE, 76(1957), pt. II, 149–158.

[18] Milne-Tomson, L. M., On the operational solution of linear finite difference equations, Proc. of Cambridge Philosophical Society, 27(1931).1.

[19] Polak, E., Stability and graphical analysis of First-Order pulse-width-modulated sampled-Data regulator systems, Trans. IRE, PGAC-6, (1961), 3, 376–382.

[20] Ragazzini, J. R., & Zadeh, L. A., Analysis of sampled-data systems, AIEE Trans., 71(1952).pt. II, 225-234.

[21] Stone, W. M., The Generalized Laplace transformation with applications to problems involving finite difference, J. of Science, Jowa College, 21(1947), 81–83.

[22] Tarn, T. J., Elliott, D. L., & Goka, Controllability of discrete bilinear systems with bounded control, IEEE Trans. on AC, AC-18(1973), 3, 289–301.

[23] Temam, R., Numerical Analysis, D. Reidel Publishing Company, 1973.

[24] Tou, J. T., Digital and Sampled-Data Control Systems, McGraw-Hill Book Company, Inc., 1959.

[25] Антомонов, Ю. Г., Автоматическое Управление с Применением Вычислительных Машин,

Ленинград, 1962.

[26] Ван Синь-Минь (王新民), Получение конечного времени переходного процесса в непрерывных системах автом. регулирования, Автоматическое управление, Изэ. АН СССР, 1960.

[27] Гельфанд, А. О., Исчисление Конечных Разностей, Москва, 1952. (有限差计算, 刘绍祖译, 高等教育出版社, 1960.)

[28] Кузин, Л. Т., Расчет и Проектирование Дискретных Систем Управления, Москва, 1961.

[29] Пышкин, И. В., Процессы конечной длительности в широтно-импульсных системах, Автоматика и Телемеханика, 21(1960), 2.

[30] Рутман, Р. С., Быстродействующие импульсные системы с переключениями внутри такта, Автоматика и Телемеханика, 23(1962), 9.

[31] Тартаковский, Г. П., Устойчивость линейных импульсных систем с переменными параметрамп, Раэютехника и Электроника, 2(1957), 1.

[32] Фань Чун-вуй (范崇惠), Об импульсных следящих системах, содержащих два импульсных элемента с неравными периодами повторения, Автоматика и Телемеханика, 19(1958).

[33] Фань Чун-вуй (范崇惠), Об одном методе анализа импульсных следящих систем, Автоматика и Телемеханика, 20(1959), 4.

[34] Цыпкин, Я.З., Теория Импульсных Систем, Физматгиз, 1958. (脉冲系统理论, 王众托译, 科学出版社, 1962.)
