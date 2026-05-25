# 工程控制论（上册）

（第三版）

钱学森 宋健 著

## 正文（012）

### 第十二章 分布参数控制系统

在第一章里，我们曾经讲过，有很多受控对象的运动规律，不能用常微分方程来描述。例如，弹性梁型的运动体、大型加热炉、水轮机和汽轮机，物理学中的电磁场、流场、等离子体约束、温度场以及化学中的扩散过程等。这些物理量的变化规律，必须用偏微分方程才能准确地加以描述。而且在工程技术上，常常要求对这些物理量加以控制，使其变化规律满足技术上的要求。受控对象如此，控制装置或执行机构也有类似的情况。如液压和气动执行机构是目前应用比较广泛的元件。当油路和气路结构比较复杂且路线过长时，在其运动规律中也要考虑流体（工作体）本身的状态变化，而这种状态同样是由偏微分方程描述的。前一章讨论过的具有时滞的系统，如果时滞是由于运动在某种场内传递而造成的话，那么时滞系统就是分布参数系统的一个特例。

由此看来，工程实践向我们提出了不同于集中参数系统的一种控制系统。在这种系统中，一部分环节的运动用偏微分方程描述，而另一部分环节则用常微分方程描述，或者全部环节都用偏微分方程来描述。我们把这种动力学系统称之为分布参数控制系统。如弹性体的振动控制、装有流体的刚性容器的晃动控制、温度场的控制，以及热核受控反应中的等离子体约束的控制等，都是典型的分布参数控制系统。

从工程技术角度来说，对于这类系统，我们自然会提出，什么是系统的稳定性，什么是它的过渡特性，如何进行系统分析，怎样设计一个满足实际限制而又能达到既定指标的控制装置，使系统满足规定的技术要求等。对于集中参数控制系统，这些方面的理论和实践都较成熟，但对分布参数系统来说，尚处在发展阶段。五十年代，当分布参数系统的理论还没有建立起来时，人们曾用集中参数的理论去逼近，如用带有时滞环节的常微分方程去讨论特殊类型的分布参数控制系统 $^{[41]}$ 。即使这种比较简单的分布参数系统，就已经表现出了它的复杂性。以线性常系数分布参数系统来说，我们将会看到，第三章用过的传递函数方法对它还是可以应用的。但是，其传递函数已不再是有理分式，而是亚纯函数。系统的特征方程也不是多项式而是整函数，它的特征根也不是有限个而是无穷多个。显然，分析这种系统比集中参数系统复杂得多。至于线性变系数系统和非线性系统就更为复杂。

近十几年来，由于理论和实践的发展，特别是在分布参数控制系统的研究中，由于广泛应用现代偏微分方程和泛函分析的理论成果，不仅为分布参数系统建立 了比较严格的理论基础，同时也提供了比较有力的工具，从而使分布参数系统的研究有了很大进展，成为现代控制理论中一个重要分支，并越来越引起人们的广泛重视。

目前，在分布参数系统理论的研究中，某些方面是和集中参数系统平行进行的。在某种意义上，它是集中参数系统理论的推广。如分布参数系统的镇定问题、最优控制问题、能控性和能观测性问题，以及分布参数系统的辨识和滤波问题等，都取得了类似于集中参数系统的结果。但是，由于分布参数系统描述的物理现象的复杂性，它具有无穷多个自由度，这一事实本身就决定了分布参数系统有其固有特点，而这些特点是集中参数系统所没有的。

在这一章里，我们仅就分布参数系统的基本特点和典型分布参数系统的构成，以及系统分析和综合的基本方法和概念，作一些初步介绍。对于这些问题的各种专门研究，读者可参阅本章所附的文献。

应该说明，十几年来，关于分布参数系统的研究工作很多，这当然是很好的事情，但用来解决工程实际问题的研究还不够多。而且偏微分方程理论本身也还有很多空白，尤其是从控制理论的角度提出的新问题还需要进一步深入地研究。

#### 12.1 分布参数环节的数学描述

具有分布参数特性的物质运动，其运动状态不仅依赖于时间，而且还依赖于空间变量。例如横向振动的弦，它的横向位移 $u(t,x)$ ,既是时间 t 又是弦上不同点位置 x 的函数。不同的时间，弦的位移是不同的，即使同一时间，在弦的不同点 x 处的位移也不同。在工程上，所有具有分布参数特性的对象和元件，都有着同样的性质。描述这类对象的运动方程是偏微分方程或积分方程。

例如，一个受控的均匀圆柱体的扭转运动。设其长为 l, 材料的剪切模量为 G, 质量密度为 $\rho$ 。若 t 时刻 x 点处的扭角为 $r(t, x)$ , 则圆柱体的扭转振动, 可以用下述偏微分方程描述

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = \frac {G}{\rho} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}} + f (t, x), \quad 0 <   x <   l, \quad 0 <   t <   \infty \tag {12.1-1}
$$

其中 $f(t, x)$ 是控制作用。

再如，一个均匀各向同性的物体，它在三维空间占有的区域为 $\Omega$ ，其边界为 $\partial\Omega$ 。设它的热传导系数为 k，比热为 c，密度为 $\rho$ 。用 $u = u(t, x, y, z)$ 表示物体在 $(x, y, z)$ 点处 t 时刻的温度，那么，这个物体的温度变化应满足方程

$$
\frac {\partial u}{\partial t} = a ^ {2} \left[ \frac {\partial^ {2} u}{\partial x ^ {2}} + \frac {\partial^ {2} u}{\partial y ^ {2}} + \frac {\partial^ {2} u}{\partial z ^ {2}} \right] + f (t, x, y, z), \quad (x, y, z) \in \Omega , \quad 0 <   t <   \infty \tag {12.1-2}
$$

其中 $a^2 = \frac{k}{c\rho}, f(t, x, y, z)$ 为可调的热源。

如果不加热源，即 $f(t,x,y,z)\equiv 0$ ，而且物体的外部环境不随时间变化，这时，不管初始温度如何，经过一段时间之后，物体内部温度趋于平衡，此时热量仍在流动，只是流出和流入物体热量的代数和等于零，物体内部的温度 $u(t,x,y,z)$ 已与 $t$ 无关，在这种情况下，它满足所谓拉普拉斯方程

$$
\frac {\partial^ {2} u}{\partial x ^ {2}} + \frac {\partial^ {2} u}{\partial y ^ {2}} + \frac {\partial^ {2} u}{\partial z ^ {2}} = 0, (x, y, z) \in \Omega \tag {12.1-3}
$$

上述这些方程都是典型的偏微分方程，而且都是线性的，即在方程中对未知函数及其导数都是线性的。当方程中所有系数都是常数时，叫做常系数方程。如果右端函数[如式(12.1-1)中的 $f(t,x)]$ 不为零时，叫做非齐次方程。否则叫做齐次方程，如式(12.1-3)。对线性二阶方程，按其特点又分为双曲型、抛物型和椭圆型三种。许多分布参数环节是由这些方程描述的，所以我们稍微介绍得详细一点。

方程(12.1-1)是双曲型方程中的一种。这类方程含有对时间 t 的二阶偏导数项，即加速度项。自然界中波的传播，物体振动等的运动方程大都属于这一类。它们表现出对时间具有可逆的性质。同是双曲型方程，可以描述完全不同的物理现象。比如一维双曲型方程

$$
\frac {\partial^ {2} u}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} u}{\partial x}
$$

当 $a^{2}=\frac{T}{\rho}$ ，T 是张力， $\rho$ 是质量密度时，它描述了弦的横向振动。但是一个充满气体的细长管子受到小扰动时，管中气体压力 p 也满足相同形式的方程，

$$
\frac {\partial^ {2} p}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} p}{\partial x ^ {2}}
$$

只是系数 $a^{2}$ 的物理意义不同了。此时 $a^{2}=\frac{kp_{0}}{\rho_{0}}, p_{0}, \rho_{0}$ 分别是初始时刻气体压力和密度， $k=\frac{c_{p}}{c_{v}}$ 是比热比， $c_{p}$ 是定压比热， $c_{v}$ 是定容比热。

方程(12.1-2)是抛物型方程中的一种。这类方程中，含有对 $t$ 的一阶偏导数项，即速度项。它描述着自然界中的热传导过程、气体扩散以及电磁场传播等物理过程。同样，在量子力学、统计物理、概率论等理论研究中也会遇到这类方程。这类运动过程在时间上，通常没有可逆性。和双曲型方程类似，同一方程描述完全不同的物理现象。比如，导电线圈所围圆柱体内的磁场 $H$ ，就用方程(12.1-2)来描述

$$
\frac {\partial H}{\partial t} = a ^ {2} \left(\frac {\partial^ {2} H}{\partial x ^ {2}} + \frac {\partial^ {2} H}{\partial y ^ {2}} + \frac {\partial^ {2} H}{\partial z ^ {2}}\right)
$$

其中 $a^2 = \frac{c^2}{4\pi\sigma\mu}, c$ 是光速， $\mu$ 是磁导率， $\sigma$ 是电导率。

双曲型和抛物型方程，描述了运动的动态过程，而式(12.1-3)这类椭圆型方程，则描述了运动的稳态过程。诸如稳态下的热传导问题，在固定外力作用下，膜的平衡问题以及不可压缩理想流体无旋流动的速度势，静电场的电位等，都属于椭圆型方程。

从工程技术上说，所谓分布参数受控对象和元件，即分布参数环节，就是指其运动方程是由上述各类偏微分方程描述的。这些描述运动过程的方程式也叫发展方程。如果方程和边界条件都是线性的，则这个环节就叫做线性环节。

例如，在飞行控制中，一个细长体飞行器，有时不能完全看成刚体而必须考虑弹性振动。此时作为弹性体，它的运动可以近似用弹性梁的运动来描述，其运动方程就是 $^{[9]}$

$$
m (x) \frac {\partial^ {2} u}{\partial t ^ {2}} + C (x) \frac {\partial u}{\partial t} + B (x) \frac {\partial u}{\partial x} + \frac {\partial^ {2}}{\partial x ^ {2}} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} = f (t, x), \quad 0 <   x <   l, \quad 0 <   t <   \infty \tag {12.1-4}
$$

其中 $m(x)$ 是梁的质量密度, E 是杨氏模量, $EJ(x)$ 是 x 处的弯曲刚度, $C(x)$ 是介质对梁横向振动的阻尼系数, $B(x)$ 是局部升力系数, $f(t, x)$ 是控制作用。 $u = u(t, x)$ 是梁在 x 点处 t 时刻的横向位移。显然, 这样的受控对象就是分布参数对象。

和集中参数系统一样，为了进行系统分析，首先要分析分布参数环节的动态特性和静态特性，因此就必须对描述环节的方程求解。但是这个问题要比集中参数环节复杂得多。

一个用常微分方程描述的对象，只要初始状态给定，它的运动就唯一确定了。对偏微分方程描述的对象，为了确定它的解，也必须给出初始状态，即初始条件。对双曲型方程要给出初始位移和初始速度，比如方程(12.1-1),它的初始条件可以是

$$
r (t, x) \mid_ {t = 0} = \varphi (x), \quad \left. \frac {\partial r (t , x)}{\partial t} \right| _ {t = 0} = \psi (x) \tag {12.1-5}
$$

对抛物型方程要给出初始位置，比如，方程(12.1-2)的初始条件可为

$$
u (t, x, y, z) \mid_ {t = 0} = \varphi (x, y, z) \tag {12.1-6}
$$

但是，只有初始条件，对偏微分方程来说，往往还不能唯一确定它的解。比如，同样作扭转振动的圆柱体，它可以是两端固定不动的，也可以是一端固定不动而另一端是自由的。这两种不同的边界情况，圆柱体的振动规律显然不一样。同样，一个传热介质的边界，如方程(12.1-2)中的 $\partial \Omega$ ，它可以是绝热的，也可以和外界有热交换，在这两种边界条件下，介质的热传导规律也不一样。因此，为了使方程的解确定，除了初始条件外，还必须有所谓的边界条件，这是不同于集中参数系统的。例如，上述圆柱体的扭转振动，当两端固定时，边界条件为

$$
r (t, x) \mid_ {x = 0} = 0, r (t, x) \mid_ {x = l} = 0 \tag {12.1-7}
$$

如果 x=0 一端固定, x=l 一端是自由的, 则边界条件为

$$
r (t, x) \mid_ {x = 0} = 0, \frac {\partial r (t , x)}{\partial x} \Bigg | _ {x = l} = 0 \tag {12.1-8}
$$

边界条件反映了在物体运动过程中，加在其边界上的约束。不同的约束条件，其运动规律也不一样。当初始条件和边界条件都给定以后，方程的解才能唯一确定，这在数学中叫做偏微分方程的定解问题，而初始条件和边界条件叫做定解条件。给定了运动方程，它描述了物体的一般运动，在方程和定解条件都给定的情况下，方程的解就描述了物体的一类特殊运动。

对上述三种不同类型的方程，在形式上有着完全相似的三种边界条件 $^{[2,3]}$ 。以方程(12.1-2)为例，第一类边界条件是

$$
u (t, x, y, z) \mid_ {\partial \Omega} = \varphi_ {1} (t, x, y, z), \quad (x, y, z) \in \partial \Omega \tag {12.1-9}
$$

它表示在物体边界上， $u(t,x,y,z)$ 的变化规律是已知的。

第二类边界条件是

$$
\left. \frac {\partial u (t , x , y , z)}{\partial n} \right| _ {\partial \Omega} = \varphi_ {2} (t, x, y, z), \quad (x, y, z) \in \partial \Omega \tag {12.1-10}
$$

其中 n 表示边界曲面 $\partial\Omega$ 的外法线方向。这个条件表明，在物体边界 $\partial\Omega$ 的法线方向上， $u(t, x, y, z)$ 的变化规律是给定的。

第三类边界条件是

$$
\left[ \frac {\partial u (t , x , y , z)}{\partial n} + k u (t, x, y, z) \right] \Bigg | _ {\partial \Omega} = \varphi_ {3} (t, x, y, z), \quad (x, y, z) \in \partial \Omega \tag {12.1-11}
$$

其中 $k$ 是已知常数。这个条件是式(12.1-9)和(12.1-10)的线性组合，它表明在物体边界 $\partial \Omega$ 及 $\partial \Omega$ 的法线方向上，两者合在一起 $u(t,x,y,z)$ 的变化规律是已知的。

如果 $\varphi_{1}=\varphi_{2}=\varphi_{3}=0$ ，则叫做齐次边界条件，否则叫做非齐次边界条件。

在受控对象的分析中，我们能够遇到的有三种问题，即初值问题，边值问题，混合问题。

所谓初值问题（柯西问题）是指只有初始条件就可定解。这类问题描述的是相当于空间变量的变化区域为无限大时的动态过程。它往往出现在双曲型和抛物型方程中。如无限长圆柱体的扭转振动，无限大介质中的热传导，无限长电力线的传输等。所谓无限大的区域，是指当物体的体积很大，而所要研究的问题是在较短时间里，较小范围内的变化规律。比如大气中某个局部范围短期内温度变化的情况，那时边界条件产生的影响很小，以致可以忽略，这时不妨把整个物体看成无限大，而把边界条件去掉。于是就变成了只有初始条件的初值问题。

边值问题是在定解条件中只有边界条件，没有初始条件。这类问题描述的是

运动的稳态过程。边值问题往往出现在椭圆型方程中。

混合问题是在定解条件中既有初始条件也有边界条件。这类问题描述了空间区域为有限时的动态过程。它大多出现在双曲型和抛物型方程中。如有限长弦的横向振动，有限体积内物体热传导，有限长电力线的传输等。从控制观点看，我们首先感兴趣的是动态过程，然后才是稳态过程，因此，我们讨论的重点是混合问题。

> 此处省略原书 **图 12.1-1**

以上所讲的分布参数对象，其空间区域和边界，在运动过程中始终保持不变，这叫做固定域分布参数对象。与此相反，当空间区域和边界在运动过程中随着时间而变化时，叫做可变域分布参数对象。比如，带有烧蚀表面的再入飞行器的烧蚀问题 $^{[33]}$ 。我们研究再入飞行器烧蚀部分最简单的一维模型。设厚为 l 的烧蚀板，在 x=0 处有热输入为 $Q(t)$ , $Q(t)$ 可表 示为宇宙飞行器再入大气层速度 $v(t)$ 的函数，即 $Q(t)=q(v(t))$ 。在 x=l 处烧蚀板被绝热。如图 12.1-1。

在 $t_{0}$ 时飞行器开始再入飞行，由于气动加热，在 x=0 处到 $t_{1}$ 时达到了烧蚀板的熔点 $u_{m}$ 。在 $t_{0}\leqslant t\leqslant t_{1}$ 这段时间内，烧蚀板内的温度分布可用一维热传导方程描述

$$
\frac {\partial u (t , x)}{\partial t} = \mu \frac {\partial^ {2} u (t , x)}{\partial x ^ {2}}, \quad 0 <   x <   l \tag {12.1-12}
$$

初始条件是

$$
u (t, x) \mid_ {t = t _ {0}} = u ^ {0} (x) \tag {12.1-13}
$$

边界条件为

$$
\left. \frac {\partial u (t , x)}{\partial x} \right| _ {x = 0} = \frac {1}{k} q (v (t)), \quad \left. \frac {\partial u (t , x)}{\partial x} \right| _ {x = l} = 0 \tag {12.1-14}
$$

其中 k 是热传导系数。

由于板的一端是绝热的，随着时间 t 的增大，热量不断积累，当 $t > t_{1}$ 时板开始熔解。这时板的边界和内部温度都将发生变化。用 $S(t)$ 表示板的固体部分的边界，用 $\tilde{u}(t,x)$ 表示板内温度分布。当 $t > t_{1}$ 时, $\tilde{u}(t,x)$ 满足下述方程

$$
\frac {\partial \tilde {u} (t , x)}{\partial t} = \mu \frac {\partial^ {2} \tilde {u} (t , x)}{\partial x ^ {2}}, \quad S (t) <   x <   l, \quad t _ {1} <   t \tag {12.1-15}
$$

初始条件为

$$
S (t _ {1}) = 0, \quad \tilde {u} (t _ {1}, x) = u (t _ {1}, x) \tag {12.1-16}
$$

边界条件是

$$
\tilde {u} (t, x) \mid_ {x = S (t)} = u _ {m}
$$

$$
\rho \alpha \frac {d S (t)}{d t} - k \left. \frac {\partial \tilde {u} (t , x)}{\partial x} \right| _ {x = S (t)} = q (v (t))
$$

$$
\left. \frac {\partial \tilde {u} (t , x)}{\partial x} \right| _ {x = l} = 0 \tag {12.1-17}
$$

其中 $\rho$ 是板的密度, $\alpha$ 是熔解热。

在这个例子中，分布参数对象的区域和边界都是随着时间而变化的。因此，它是可变域的分布参数对象。但是，经过适当的变换可以把可变域的分布参数系统变成一个固定域分布参数系统耦合一个集中参数系统，对于后者研究起来就比较方便。今后，我们主要讨论固定域的分布参数对象。

下面，我们再说明一下偏微分方程解的含义。在定解问题中，解函数的类别与具体问题的性质有关，需要每次具体确定。例如它可以是指这样的函数，它以及出现在定解条件中它的偏导数，都在所考虑的区域上连续，而在方程中所出现的它的导数在区域内部连续，他们都同时满足方程，当区域内部的点以任意方式趋于边界时，他们满足定解条件。以方程(12.1-2)为例。运动方程和定解条件如下:

$$
\frac {\partial u}{\partial t} = a ^ {2} \left[ \frac {\partial^ {2} u}{\partial x ^ {2}} + \frac {\partial^ {2} u}{\partial y ^ {2}} + \frac {\partial^ {2} u}{\partial z ^ {2}} \right], \quad (x, y, z) \in \Omega , \quad 0 <   t <   \infty
$$

$$
u (t, x, y, z) \mid_ {t = 0} = \varphi (x, y, z), \quad (x, y, z) \in \Omega , \quad t = 0
$$

$$
\left. \left(\frac {\partial u}{\partial n} + k u\right) \right| _ {\partial \Omega} = \psi (t, x, y, z), \quad (x, y, z) \in \partial \Omega , \quad t \geqslant 0
$$

它的解 $u(t, x, y, z)$ 是指它在 $\Omega$ 和 $\partial \Omega$ 上以及 $t \geqslant 0$ 时连续， $\frac{\partial u}{\partial n}$ 在 $\partial \Omega$ 和 $t \geqslant 0$ 时连续。其次， $\frac{\partial u}{\partial t}, \frac{\partial^2 u}{\partial x^2}, \frac{\partial^2 u}{\partial y^2}, \frac{\partial^2 u}{\partial z^2}$ 在 $\Omega$ 和 $t > 0$ 处连续，把这个 $u(t, x, y, z)$ 代到方程 (12.1-2) 中使其成为恒等式。当 $t \to 0$ 时， $u(t, x, y, z) \to \varphi(x, y, z)$ 对任意的点 $(x, y, z) \in \Omega$ 处处成立。当 $(x, y, z) \in \Omega$ 并以任意方式趋于边界 $\partial \Omega$ 上任意点 $(x_0, y_0, z_0)$ 时，对 $t \geqslant 0$ 都有 $\left[\frac{\partial u}{\partial n} + ku\right] \to \psi(t, x_0, y_0, z_0)$ 成立。这样的解通常叫做方程的古典解。古典解的存在往往对初始条件要求比较严格，而实际中给定的初始条件常常不能满足这些要求。因此，古典解有很大的局限性。为了满足实际问题的需要，要用广义解代替古典解，它在较广的范围内给出了定解问题的解。这样就比较接近工程实际问题的特点。关于广义解的定义和求解方法，将在本章第 12.6 节中讨论。

#### 12.2 分布参数环节的传递函数

分布参数环节是由偏微分方程描述的，为了分析这种环节的特性，需要求解 偏微分方程。在给定了定解条件后，解偏微分方程的方法很多，但在控制理论中常用的是拉普拉斯变换法和分离系数法。特别是拉普拉斯变换法，还可以使我们去定义分布参数环节的传递函数。

我们首先定义分布参数系统中遇到的拉普拉斯变换 $^{①}$ 。

设二元函数 $y(t, x)$ ，在 t > 0 时是逐段连续的函数。在 t < 0 时为零。对任意固定的 x，作为 t 的函数 $y(t, x)$ 的增长速度小于 $e^{\sigma_{0}t}, 0 < \sigma_{0} < \infty$ 。我们定义

$$
Y (s, x) = \int_ {0} ^ {\infty} y (t, x) e ^ {- s t} d t, \quad \mathrm{Re} s > \sigma_ {0} \tag {12.2-1}
$$

式中 $s$ 为复数。 $\operatorname{Res}$ 是 $s$ 的实部。 $Y(s,x)$ 称为函数 $y(t,x)$ 的拉氏变换。 $Y(s,x)$ 在 $\operatorname{Res} \leqslant \sigma$ 上的值可用解析延拓方法确定。今后把 $Y(s,x)$ 叫做 $y(t,x)$ 的象函数，而 $y(t,x)$ 为 $Y(s,x)$ 的原函数。容易验证，第二章所讲的拉氏变换性质，在这里也是正确的。例如，当 $y(0,x) = \varphi(x)$ 时，则有

$$
\int_ {0} ^ {\infty} \frac {d y (t , x)}{d t} e ^ {- s t} d t = y (t, x) e ^ {- s t} \left. \right| _ {0} ^ {\infty} + s \int_ {0} ^ {\infty} y (t, x) e ^ {- s t} d t = - \varphi (x) + s Y (s, x)
$$

即 $\frac{dy(t,x)}{dt}$ 的象函数为 $-\varphi(x)+sY(s,x)$ 。

除此而外，还有以下性质:

(1) $Y(s,0) = \int_{0}^{\infty}y(t,0)e^{-st}dt$

$$
Y (s, l) = \int_ {0} ^ {\infty} y (t, l) e ^ {- s t} d t
$$

(2) 若 $\frac{\partial y(t,x)}{\partial x}$ 对任意固定的 x，作为 t 的函数其增长速度不大于 $e^{\beta t}, \beta \geqslant \sigma_{0}$ ，则

$$
\int_ {0} ^ {\infty} \frac {\dot {\partial} y (t , x)}{\partial x} e ^ {- s t} d t = \frac {\dot {\partial}}{\partial x} \int_ {0} ^ {\infty} y (t, x) e ^ {- s t} d t = \frac {\dot {\partial} Y (s , x)}{\partial x}, \quad \mathrm{Re} s > \beta
$$

$\mathrm{Re}s \leqslant \beta$ 的值可用解析延拓方法得到。这就是说，在上述条件下， $\frac{\dot{\partial}y(t,x)}{\partial x}$ 的象函数为 $\frac{\dot{\partial}Y(s,x)}{\partial x}$ 。

(3) 当 $Re s > \sigma_{0}$ 时，

$$
\lim _ {x \rightarrow \infty} Y (s, x) = \int_ {0} ^ {\infty} \lim _ {x \rightarrow \infty} y (t, x) e ^ {- s t} d t
$$

$Re s \leqslant \sigma_{0}$ 的值可用解析延拓方法确定。

设 $Y(s,x)$ 是 $y(t,x)$ 的象函数，则 $y(t,x)$ 可用拉氏反变换求得

$$
y (t, x) = \frac {1}{2 \pi i} \int_ {\gamma - i \infty} ^ {\gamma + i \infty} Y (s, x) e ^ {s t} d s, \quad \gamma > \sigma \tag {12.2-2}
$$

在常微分方程中，应用拉氏变换将原函数的微分方程变成了象函数的代数方程。在偏微分方程中，应用拉氏变换后，仍是象函数的偏微分方程，但自变量的数目将减少一个（有时变成了象函数的常微分方程)。然后我们应用边界条件将象函数的微分方程解出，再进行拉氏反变换就得到了方程的解。这个解由两部分组成，一部分是由初始条件引起的运动，叫做自由运动。另一部分由外加作用引起的运动，叫做强迫运动。当把外加作用看成输入，而把它引起的运动看作输出，这时输出输入象函数的比，仍是一个以 $s$ 为自变量的函数，我们把这个函数叫做分布参数环节的传递函数。和集中参数环节不同的是，这个传递函数不再是有理分式，一般地说，它是 $s$ 的超越函数，而且还是空间变量的函数。

我们举几个例子，说明拉氏变换法的应用。

例 1. 求初始位移为 $\varphi(x)$ ，初始速度为 $\psi(x)$ ，在 x=0 点处受集中力矩 $u(t)$ 控制，两端自由的圆柱体扭转振动的传递函数（见图 12.2-1）。

> 此处省略原书 **图 12.2-1**

圆柱体扭转振动方程及定解条件为

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}}, \quad 0 <   x <   l, \quad 0 <   t <   \infty
$$

$$
\left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = 0} = u (t), \quad \left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = l} = 0
$$

$$
r (0, x) = \varphi (x), \quad \left. \frac {\partial r (t , x)}{\partial t} \right| _ {t = 0} = \psi (x) \tag {12.2-3}
$$

对上述方程进行拉氏变换，则得到

$$
a ^ {2} \frac {d ^ {2} R (s , x)}{d x ^ {2}} = s ^ {2} R (s, x) - s \varphi (x) - \psi (x), \quad \left. \frac {d R (s , x)}{d x} \right| _ {x = 0} = U (s)
$$

$$
\left. \frac {d R (s , x)}{d x} \right| _ {x = l} = 0 \tag {12.2-4}
$$

把 x 看成参数, 这就是常微分方程的两点边值问题, 它的通解是

$$
R (s, x) = c _ {1} e ^ {\frac {s}{a} x} + c _ {2} e ^ {- \frac {s}{a} x} - a s \int_ {0} ^ {x} \mathrm{sh} \frac {s}{a} (x - \zeta) [ s \varphi (\zeta) + \psi (\zeta) ] d \zeta \tag {12.2-5}
$$

$c_{1}, c_{2}$ 是任意常数, 利用边界条件, 得到 $c_{1}, c_{2}$ 应满足的方程式

$$
U (s) = \frac {s}{a} c _ {1} - \frac {s}{a} c _ {2}
$$

$$
0 = \frac {s}{a} c _ {1} e ^ {\frac {s}{a} l} - c _ {2} \frac {s}{a} e ^ {- \frac {s}{a} l} - \frac {1}{a ^ {2}} \int_ {0} ^ {l} \mathrm{ch} \frac {s}{a} (l - \zeta) [ s \varphi (\zeta) + \psi (\zeta) ] d \zeta \tag {12.2-6}
$$

解出 $c_{1}, c_{2}$ 代到式(12.2-5)中, 便得到

$$
\begin{array}{l} R (s, x) = - \frac {a \cdot \operatorname{ch} \frac {l - x}{a} s}{s \cdot \operatorname{sh} \frac {l}{a} s} U (s) + 2 s a \cdot \operatorname{sh} \frac {l}{a} s \left\{\int_ {0} ^ {l} \operatorname{ch} \frac {s}{a} (l - x - \zeta) \right. \\ \cdot [ s \varphi (\zeta) + \psi (\zeta) ] d \zeta + \int_ {0} ^ {x} \mathrm{ch} \frac {s}{a} (l - x + \zeta) [ s \varphi (\zeta) + \psi (\zeta) ] d \zeta \\ + \int_ {x} ^ {l} \mathrm{ch} (l + x - \zeta) [ s \varphi (\zeta) + \varphi (\zeta) ] d \zeta \tag {12.2-7} \\ \end{array}
$$

我们可以看到，第一项是由控制作用 $u(t)$ 引起的输出，其余是由初始条件引起的输出。当初始条件为零时，输出为

$$
R (s, x) = - \frac {a \cdot \operatorname{ch} \frac {l - x}{a} s}{s \cdot \operatorname{sh} \frac {l}{a} s} U (s) \tag {12.2-8}
$$

由此，环节的传递函数为

$$
W (s, x) = \frac {R (s , x)}{U (s)} = - \frac {a}{s} \frac {\operatorname{ch} \frac {l - x}{a} s}{\operatorname{sh} \frac {l}{a} s} \tag {12.2-9}
$$

> 此处省略原书 **图 12.2-2**

例 2. 研究一维热传导问题。一座墙壁（见图 12.2-2），它的厚度为 l，高度和宽度认为是无限大。墙的热传导系数为 k，热容量（即密度和比热之积）是 c，墙的左面（x=0 处）的温度是一个已知的时间函数 $u(t)$ ，它是控制量。墙的右面（ $x \geqslant l$ 处）是绝热的。墙的初始温度为零。我们感兴趣的是墙在 x=l 处的温度随 $u(t)$ 的变化规律。

设墙内各点的温度为 $y(t, x)$ , $y(t, x)$ 应满足抛物型方程

$$
c \frac {\partial y (t , x)}{\partial t} = k \frac {\partial^ {2} y (t , x)}{\partial x ^ {2}}, \quad 0 <   x <   l, \quad 0 <   t <   \infty
$$

$$
y (t, x) \mid_ {x = 0} = u (t), \quad \left. \frac {\partial y (t , x)}{\partial x} \right| _ {x = l} = 0
$$

$$
y (t, x) \mid_ {t = 0} = 0 \tag {12.2-10}
$$

应用拉氏变换方法，可以得到

$$
c s Y (s, x) = k \frac {d ^ {2} Y (s , x)}{d x ^ {2}}
$$

$$
Y (s, 0) = U (s), \quad \left. \frac {d Y (s , x)}{d x} \right| _ {x = l} = 0 \tag {12.2-11}
$$

令 $\beta^{2}=\frac{cs}{k}$ ，则方程的解为

$$
Y (s, x) = \frac {\operatorname{ch} \beta (l - x)}{\operatorname{ch} \beta l} U (s) \tag {12.2-12}
$$

当 $x = l$ 时，便有

$$
Y (s, l) = \frac {U (s)}{\operatorname{ch} \beta l}
$$

而传递函数为

$$
W (s) = \frac {Y (s , l)}{U (s)} = \frac {1}{\operatorname{ch} \sqrt {\frac {c s}{k}} l} \tag {12.2-13}
$$

例 3. 考虑一个电力线传输问题。有一半无限长的电力传输线，每单位长度的电阻为 R，电容为 C，假定导线上的电感和电漏为零，传输线端点接入一电压源，其电压 $e = e(t)$ 可以人为改变，把它作为控制量。电力传输线上各点处的电流 $i(t, x)$ 及电压 $u(t, x)$ 应满足方程

$$
- \frac {\partial i (t , x)}{\partial x} = C \frac {\partial u (t , x)}{\partial t}
$$

$$
- \frac {\partial u (t , x)}{\partial x} = R i (t, x) \tag {12.2-14}
$$

初始条件和边界条件为

$$
i (0, x) = 0, \quad u (0, x) = 0
$$

$$
u (t, 0) = e (t), \quad \lim _ {x \rightarrow \infty} u (t, x) <   \infty \tag {12.2-15}
$$

应用拉氏变换法，由式(12.2-14)和(12.2-15)可得到

$$
- \frac {d I (s , x)}{d x} = C s U (s, x)
$$

$$
- \frac {d U (s , x)}{d x} = R I (s, x)
$$

$$
U (s, 0) = E (s), \quad \lim _ {x \rightarrow \infty} U (s, x) <   \infty \tag {12.2-16}
$$

解方程组便得到

$$
U (s, x) = E (s) e ^ {- \sqrt {C R s} x}
$$

$$
I (s, x) = \sqrt {\frac {C s}{R}} E (s) e ^ {- \sqrt {C R s} x} \tag {12.2-17}
$$

若感兴趣的是传输线上某点 $x = x_{1}$ 处的电压 $U(s, x_{1})$ ，则传递函数为

$$
W (s, x _ {1}) = \frac {U (s , x _ {1})}{E (s)} = e ^ {- \sqrt {C R s} x _ {1}} \tag {12.2-18}
$$

> 此处省略原书 **图 12.2-3**

例 4. 我们再来考虑一个二维机翼的理论问题 $^{[31]}$ ，第十四章里将要用到它。假定在均匀的以水平速度 V 流动的气流里，有一个弦长为 c 的机翼（见图 12.2-3）。

若气流在 x=0 点的垂直方向上发生了一个扰动速度 $v(t)$ ，那么，沿着翼弦方向 x 便有扰动的分布升力产生，记扰动升力密度为 $f(t,x)$ ，它满足气体动力学中的偏微分方 程。流过机翼的气体是分布参数的。把升力密度 $f(t, x)$ 对 $x$ 从 0 到 $c$ 积分，所得到的合力就是升力

$$
Y (t) = \int_ {0} ^ {c} f (t, x) d x
$$

机翼每单位面积所受到的升力和速压头 $\frac{1}{2}\rho V^{2}$ 之比称为升力系数 $\omega(t)$ ，这里 $\rho$ 是气体密度。西尔思(Sears)证明了 $^{[31]}$ ，当扰动速度为正弦函数时

$$
v (t) = \alpha_ {m} V e ^ {i \omega t} \tag {12.2-19}
$$

升力系数的稳态解 $c_{\mathrm{est}}(t)$ 为

$$
c _ {\text {est}} (t) = 2 \pi \alpha_ {m} e ^ {i \omega t} \varphi (k) = \frac {2 \pi}{V} \varphi (k) v (t) \tag {12.2-20}
$$

式中 $k=\frac{\omega c}{2V}$ ，而

$$
\varphi (k) = \frac {J _ {0} (k) K _ {1} (i k) + i J _ {1} (k) K _ {0} (i k)}{K _ {1} (i k) + K _ {0} (i k)} \tag {12.2-21}
$$

这里 $J_{0}$ 和 $J_{1}$ 分别是零阶和一阶第一类贝塞尔函数， $K_{0}$ 和 $K_{1}$ 表示第二类变态的贝塞尔函数。

如果把 $v(t)$ 当做输入, $c_{e}(t)$ 作为输出, 那么环节传递函数为

$$
W (s) = \frac {C _ {e} (s)}{V (s)}
$$

取 $s=i\omega$ ，代到上式，便得到了环节的频率特性

$$
W (i \omega) = \frac {2 \pi}{V} \varphi (k) \tag {12.2-22}
$$

用拉氏变换法解偏微分方程时，一般来说，应该检查它的原函数是否是方程的解，是否满足初始条件和边界条件。更详细的步骤，读者可参看书后的文献 $[17,2,3]$ 。

由上边的例子可以看出，对线性常系数的分布参数环节，传递函数方法是可以应用的，但这时传递函数是超越函数，而且还依赖于空间变量。在对象的不同点上，传递特性是不一样的，这也说明了分布参数环节的特点。

在结束本节之前，再讨论一下解线性偏微分方程的分离变量法。这个方法的物理依据就是叠加原理。大家知道电子学中的振荡回路和力学中的简谐振动，它们的特点是运动可以表达成一个时间 t 的函数和一个空间变量 x 的函数之积，而较为复杂的振动就是这些不同频率谐波的叠加。基于这样的想法，在解线性偏微分方程时，认为它的解 $u(t,x)$ 是两个单变量的函数之积即 $u(t,x)=T(t)X(x)$ ,然后利用初始条件和边界条件求出 $T(t)$ 和 $X(x)$ ,从而也就得到了 $u(t,x)$ 。

我们考察例 1 中圆柱体的扭转振动。作用在 x=0 处的力矩 $u(t)$ ，可以用集中力矩的形式反映在运动方程中，这时有

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}} - a ^ {2} u (t) \delta (x)
$$

$$
\left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = 0} = 0, \left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = l} = 0
$$

$$
r (0, x) = \varphi (x), \quad \left. \frac {\partial r (t , x)}{\partial t} \right| _ {t = 0} = \psi (x) \tag {12.2-23}
$$

其中 $\delta(x)$ 是狄拉克函数 $^{①}$ 。此时边界条件是齐次的。

首先解齐次方程

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}} \tag {12.2-24}
$$

寻求形式为 $r(t,x)=T(t)X(x)$ 的解，代到式(12.2-24)中，有

$$
\ddot {T} (t) X (x) = a ^ {2} T (t) \ddot {X} (x) \tag {12.2-25}
$$

或写成

$$
a ^ {2} \frac {\ddot {X} (x)}{X (x)} = \frac {\ddot {T} (t)}{T (t)}
$$

两个不同自变量的函数值相等，只有当它们共同为某一常数时才能成立。即

$$
a ^ {2} \frac {\ddot {X} (x)}{X (x)} = \frac {\ddot {T} (t)}{T (t)} = - \lambda^ {2} \tag {12.2-26}
$$

其中 $\lambda$ 是常数。于是 $X(x)$ 应满足方程式

$$
a ^ {2} \ddot {X} (x) + \lambda^ {2} X (x) = 0 \tag {12.2-27}
$$

把解 $r(t,x)=T(t)X(x)$ 代到边界条件中, 又得到

$$
\dot {X} (0) = 0, \quad \dot {X} (l) = 0 \tag {12.2-28}
$$

于是方程(12.2-27)的通解为

$$
X (x) = c \sin \frac {\lambda}{a} x + c \cos \frac {\lambda}{a} x
$$

为了使 $X(x)$ 能满足边界条件式(12.2-28)，只有当 $\lambda=0, \lambda_{n}=\frac{n\pi a}{l}, n=1,2,\cdots$ ，才有可能，而相应的解 $X_{n}(x)$ 为

$$
X _ {0} (x) = 1, \quad X _ {n} (x) = \cos \frac {n \pi}{l} x, \quad n = 1, 2, \dots
$$

我们把 $\lambda_{n}=\frac{n\pi a}{l}$ 叫做圆柱扭转振动的固有频率，而 $X_{n}(x)$ 叫做固有振型。 $X_{0}(x)$ ， $X_{n}(x), n=1,2,\cdots$ 构成了 $L_{2}$ 空间一组直交基。

对非齐次方程(12.2-23)的解 $r(t,x)$ ，应用叠加原理，先把 $r(t,x)$ 依上组直交基展成级数

$$
r (t, x) = P _ {0} (t) + \sum_ {n = 1} ^ {\infty} P _ {n} (t) X _ {n} (x) \tag {12.2-29}
$$

式中 $P_{0}(t)$ , $P_{1}(t)$ , …叫做广义坐标。把式(12.2-29)代到式(12.2-23)中，便得到

$$
\ddot {P} _ {0} (t) + \sum_ {n = 1} ^ {\infty} \ddot {P} _ {n} (t) X _ {n} (x) = - \sum_ {n = 1} ^ {\infty} P _ {n} (t) \left[ \frac {n \pi a}{l} \right] ^ {2} X _ {n} (x) - a ^ {2} u (t) \delta (x) \tag {12.2-30}
$$

利用固有振型的正交性

$$
\int_ {0} ^ {l} X _ {n} (x) X _ {m} (x) d x = \left\{ \begin{array}{l l} 0, & n \neq m \\ \frac {l}{2}, & n = m \end{array} \right.
$$

把方程(12.2-30)两端乘以 $X_{m}(x)$ 并从 0 到 l 积分，则得到广义坐标满足的无限维方程组

$$
\ddot {P} _ {0} (t) = - \frac {a ^ {2}}{l} u (t)
$$

$$
\ddot {P} _ {n} (t) = - \left[ \frac {n \pi a}{l} \right] ^ {2} P _ {n} (t) - \frac {2 a ^ {2}}{l} u (t), \quad n = 1, 2, \dots \tag {12.2-31}
$$

在解式(12.2-29)时，将方程(12.2-23)中的初始条件代入，并利用振型正交性，两

端乘以 $X_{m}(x)$ ，从 0 到 l 积分后，便得到

$$
P _ {0} (0) = \frac {1}{l} \int_ {0} ^ {l} \varphi (x) d x
$$

$$
P _ {n} (0) = \frac {2}{l} \int_ {0} ^ {l} \varphi (x) X _ {n} (x) d x, \quad n = 1, 2, \dots
$$

$$
\dot {P} (0) = \frac {1}{l} \int_ {0} ^ {l} \psi (x) d x
$$

$$
\dot {P} _ {n} (0) = \frac {2}{l} \int_ {0} ^ {l} \psi (x) X _ {n} (x) d x, \quad n = 1, 2, \dots \tag {12.2-32}
$$

在式(12.2-32)的初始条件下，解无穷维方程组(12.2-31),求出 $P_{0}(t)$ , $P_{n}(t)$ , n=1,2,…再代到式(12.2-29)中，就得到解 $r(t,x)$ 。

若初始条件为零，则 $P_{0}(0)=0,\dot{P}_{0}(0)=0,P_{n}(0)=0,\dot{P}_{n}(0)=0,n=1,2,\cdots$ , 这时可解出广义坐标为

$$
P _ {0} (t) = - \frac {a ^ {2}}{l} \int_ {0} ^ {t} (t - \tau) u (\tau) d \tau
$$

$$
P _ {n} (t) = - \frac {2 a}{n \pi} \int_ {0} ^ {t} \sin \frac {n \pi a}{l} (t - \tau) u (\tau) d \tau , \quad n = 1, 2, \dots \tag {12.2-33}
$$

代到式 $(12.2-29)$ 中，有

$$
r (t, x) = - \frac {a ^ {2}}{l} \int_ {0} ^ {t} (t - \tau) u (\tau) d \tau + \sum_ {n = 1} ^ {\infty} \cos \frac {n \pi}{l} x \left[ - \frac {2 a}{n \pi} \right] \int_ {0} ^ {t} \sin \frac {n \pi a}{l} (t - \tau) u (\tau) d \tau
$$

$$
= - \frac {a ^ {2}}{l} \int_ {0} ^ {t} (t - \tau) u (\tau) d \tau - \frac {2 a}{\pi} \sum_ {n = 1} ^ {\infty} \frac {1}{n} \cos \frac {n \pi}{l} x \int_ {0} ^ {t} \sin \frac {n \pi a}{l} (t - \tau) u (\tau) d \tau \tag {12.2-34}
$$

将上式两端进行拉氏变换

$$
R (s, x) = - \frac {a ^ {2}}{l} \left[ \frac {1}{s ^ {2}} + 2 \sum_ {n = 1} ^ {\infty} \frac {1}{s ^ {2} + \left(\frac {n \pi a}{l}\right) ^ {2}} \cos \frac {n \pi}{l} x \right] U (s)
$$

由此推得传递函数为

$$
W (s, x) = \frac {R (s , x)}{U (s)} = - \frac {a ^ {2}}{l} \left[ \frac {1}{s ^ {2}} + 2 \sum_ {n = 1} ^ {\infty} \frac {1}{s ^ {2} + \left(\frac {n \pi a}{l}\right) ^ {2}} \cos \frac {n \pi}{l} x \right] \tag {12.2-35}
$$

这就是传递函数的级数表达式。利用复变函数论中亚纯函数最简分式展开定理，可以证明，这个级数形式的传递函数，就是我们已经得到过的传递函数式(12.2-9)

$$
W (s, x) = - \frac {a}{s} \frac {\operatorname{ch} \frac {l - x}{a} s}{\operatorname{sh} \frac {l}{a} s}
$$

#### 12.3 分布参数控制系统的构成和特点

上两节我们讨论了分布参数环节的一些特点，在这一节里，我们要讨论由分布参数环节组成分布参数控制系统的一些特点。

如同集中参数控制系统一样，分布参数控制系统的主要组成部分是受控对象，观测器和控制器。观测器测得受控对象的运动状态，并将测得的信息送到控制器。控制器根据控制要求，把观测信息经过变换、处理和加工，然后形成控制信号，再将它加在受控对象上，使其按控制作用而运动。

> 此处省略原书 **图 12.3-1**

以图 12.2-1 所示的系统为例, 假定要求控制弹性圆柱体的扭转运动, 使 $x = x_{g}$ 处的扭角保持为零。为此, 只要在 $x = x_{g}$ 处放一个传感器, 当 $x_{g}$ 处出现扭角, 传感器敏感出来后便立即产生信号, 并把该信号送到电动机, 使其产生扭矩, 即控制作用。这个控 制信号经放大后，加在圆柱体 x=0 处，控制圆柱体以消除在 $x_{g}$ 处产生的扭角（见图 12.3-1)。

在这个例子中，受控对象就是圆柱体，受控量是 $r(t, x_{g})$ 。观测器就是传感器，而电动机和放大器构成了控制器。

受控对象的动力学方程为

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}} - a ^ {2} u (t) \delta (x)
$$

$$
\left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = 0} = 0, \quad \left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = l} = 0
$$

$r(t,x)$ 是圆柱体的扭角， $u(t)$ 是控制作用，它由传感器感受扭角而产生信号，经放大后驱动电机产生的扭转力矩其动力学方程为

$$
T \frac {d u (t)}{d t} + u (t) = - k r (t, x _ {\mathrm{g}})
$$

观测器（传感器）输出方程为

$$
r (t, x _ {g}) = \int_ {0} ^ {l} r (t, x) \delta (x - x _ {g}) d x = S r (t, x)
$$

其中 S 是测量算子, $\delta(x)$ 是狄拉克函数。

这样，整个闭路控制系统的方程就为

$$
\frac {\partial^ {2} r (t , x)}{\partial t ^ {2}} = a ^ {2} \frac {\partial^ {2} r (t , x)}{\partial x ^ {2}} - a ^ {2} u (t) \delta (x)
$$

$$
\left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = 0} = 0, \left. \frac {\partial r (t , x)}{\partial x} \right| _ {x = l} = 0
$$

$$
T \frac {d u (t)}{d t} + u (t) = - k S r (t, x) \tag {12.3-1}
$$

这就是一个具有反馈控制的分布参数控制系统。

所谓分布参数控制系统，就是指系统中至少含有一个分布参数环节的系统。如果系统全部由分布参数环节组成，就叫纯分布参数控制系统。对这类系统，理论研究工作比较多，但由于技术实现上的困难，实际应用中还很少见到。

目前，在工程实际中，经常遇到的分布参数系统，往往是分布参数环节和集中参数环节互相耦合而成的控制系统，而且多数是受控对象为分布参数环节，而控制器是集中参数环节，如上例所述的系统。

我们再来考察一个典型的分布参数控制系统。受控对象是式(12.1-4)描述的弹性梁，其运动方程为

$$
m (x) \frac {\partial^ {2} u}{\partial t ^ {2}} + C (x) \frac {\partial u}{\partial t} + B (x) \frac {\partial u}{\partial x} + \frac {\partial^ {2}}{\partial x ^ {2}} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} = f (t, x), \quad 0 <   x <   l, \quad 0 <   t <   \infty \tag {12.3-2}
$$

边界条件是两端自由的，即

$$
\left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = 0} = 0, \quad \left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = l} = 0
$$

$$
\frac {\partial}{\partial x} E J (x) \left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = 0} = 0, \quad \frac {\partial}{\partial x} E J (x) \left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = l} = 0 \tag {12.3-3}
$$

初始条件为

$$
u \big | _ {t = 0} = \varphi (x), \quad \frac {\partial u}{\partial t} \big | _ {t = 0} = \psi (x) \tag {12.3-4}
$$

为了实现反馈控制，必须测量受控对象的运动状态，如运动的位移、速度、加速度；角度，角速度等，并用它们来形成反馈信号。为了测量这些状态，可以在梁上安装各种传感器，如加速度表，速率陀螺等惯性元件。在实际工程问题中，不可能测出对象所有点上的状态，只能测出有限个孤立点上的状态或者某个区域上的平均状态。我们研究两种反馈信号，即“姿态”反馈和速度反馈。姿态是指位移和偏角，而速度则指它们对时间 $t$ 的一次微商，如位移速度，角速度等。传感器的输出可以表达如下，设 $a_{i}(x), i = 1,2$ 是定义在 $[0,l]$ 上两个确定的函数，它由传感器的安装位置确定。 $S_{i}, i = 1,2$ 表示状态测量的线性算子（有界或无界），它决定于被测量状态的性质。这样，姿态传感器的输出就可以表示成

$$
q _ {1} (a _ {1}, t) = \int_ {0} ^ {l} S _ {1} u (t, x) a _ {1} (x) d x \tag {12.3-5}
$$

速度传感器的输出为

$$
q _ {2} (a _ {2}, t) = \int_ {0} ^ {l} S _ {2} \frac {\partial u (t , x)}{\partial t} a _ {2} (x) d x = \frac {\partial}{\partial t} \int_ {0} ^ {l} S _ {2} u (t, x) a _ {2} (x) d x \tag {12.3-6}
$$

例如，当 $S_{1}=S_{2}=I$ (恒等算子)，且

$$
a _ {i} (x) = \left\{ \begin{array}{l l} \frac {1}{\Delta}, & x \in \left[ x _ {0} - \frac {\Delta}{2}, x _ {0} + \frac {\Delta}{2} \right] \\ 0, & x \overline {{\in}} \left[ x _ {0} - \frac {\Delta}{2}, x _ {0} + \frac {\Delta}{2} \right], \quad x _ {0} \in (0, l), \quad i = 1, 2 \end{array} \right.
$$

其中 $\Delta$ 是一个小的常数，这时 $q_{1}, q_{2}$ 分别是 $x_{0}$ 点附近小区域 $\Delta$ 上的平均位移和平均速度。而当 $S_{1} = S_{2} = \frac{\partial}{\partial x}$ (无界算子) 时， $q_{1}, q_{2}$ 就是 $x_{0}$ 点附近小区域 $\Delta$ 上的平均偏角和平均角速度。特别是当 $a_{i}(x) = \delta(x - x_{0})$ 时， $q_{1}, q_{2}$ 就是对象在 $x_{0}$ 点的姿态和速度，这就是点测量，而前者叫做分布测量 $^{[10]}$ 。

传感器的输出 $q_{1}, q_{2}$ ，要经过放大，网络变换和计算机处理。完成这些任务的装置就是控制器，它是由常微分方程描述的。设 $x(t) = (x_{1}(t), x_{2}(t), \cdots, x_{n}(t))$ 是控制器的 n 个输出信息， $k_{1}, k_{2}$ 是诸通道对量测量 $q_{1}, q_{2}$ 的放大系数， $k_{i} = (k_{1i}, k_{2i}, \cdots, k_{ni}), i = 1, 2$ 。则控制器的动力学方程为

$$
\frac {d \boldsymbol {x} (t)}{d t} = J \boldsymbol {x} (t) + \boldsymbol {k} _ {1} q _ {1} (a _ {1}, t) + \boldsymbol {k} _ {2} q _ {2} (a _ {2}, t) \tag {12.3-7}
$$

$J$ 是 $n \times n$ 阶方阵。

控制器的输出 $x(t)$ 经过执行机构功率放大后, 变成为受控对象上某一点或某一区域上的控制力（或力矩) $f(t, x)$

$$
f (t, x) = \left[ \sum_ {i = 1} ^ {n} x _ {i} (t) g _ {i} \right] b (x)
$$

$g=(g_{1},g_{2},\cdots,g_{n})$ 是诸通道中的功率放大系数。 $b(x)$ 是定义在 $[0,l]$ 上的确定函数，它由控制力（或力矩）的作用点或区域决定。例如，取

$$
b (x) = \left\{ \begin{array}{l l} 1, & x \in \left[ x _ {c} - \frac {\Delta}{2}, x _ {c} + \frac {\Delta}{2} \right] \\ 0, & x \overline {{\in}} \left[ x _ {c} - \frac {\Delta}{2}, x _ {c} + \frac {\Delta}{2} \right], \quad x _ {c} \in (0, l) \end{array} \right.
$$

则 $b(x)$ 表示控制力加在 $x_{c}$ 点附近的小区域 $\Delta$ 上。特别当 $b(x)=\delta(x-x_{c})$ 时，则它表示是在 $x_{c}$ 处的点控制，而前者叫做分布控制。

于是，整个反馈闭合系统的方程组为

$$
m (x) \frac {\partial^ {2} u}{\partial t ^ {2}} + C (x) \frac {\partial u}{\partial t} + B (x) \frac {\partial u}{\partial x} + \frac {\partial^ {2}}{\partial x ^ {2}} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} = - \left[ \sum_ {i = 1} ^ {n} x _ {i} (t) g _ {i} \right] b (x)
$$

$$
\left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = 0} = 0, \quad \left. \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = l} = 0
$$

$$
\left. \frac {\partial}{\partial x} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = 0} = 0, \quad \left. \frac {\partial}{\partial x} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} \right| _ {x = l} = 0
$$

$$
u \mid_ {t = 0} = \varphi (x), \quad \left. \frac {\partial u}{\partial t} \right| _ {t = 0} = \psi (x)
$$

$$
\frac {d \boldsymbol {x} (t)}{d t} = J \boldsymbol {x} (t) + \boldsymbol {k} _ {1} q _ {1} (a _ {1}, t) + \boldsymbol {k} _ {2} q _ {2} (a _ {2}, t)
$$

$$
q _ {1} (a _ {1}, t) = \int_ {0} ^ {l} S _ {1} u (t, x) a _ {1} (x) d x
$$

$$
q ^ {2} (a _ {2}, t) = \int_ {0} ^ {l} S _ {2} \frac {\partial u (t , x)}{\partial t} a _ {2} (x) d x \tag {12.3-8}
$$

系统的方块图示于图 12.3-2 中。

> 此处省略原书 **图 12.3-2**

这是一个用常微分方程描述的控制器作线性反馈的分布参数控制系统。对这个系统，后面我们还要详细讨论。

一个分布参数控制系统，如果组成系统的所有环节都是线性的，则叫做线性系统。这里再强调一下，对线性分布参数环节，不仅指描述它的方程是线性的，同时它的边界条件也必须是线性的。对线性系统来说，叠加原理总是成立的。反之，当系统中含有非线性环节时，就叫做非线性分布参数控制系统。

在线性系统中，如果所有环节对时间变量 t 都是常系数的，则叫做线性常系数系统。而当环节的系数随着时间 t 而变化时，就叫做线性变系数系统。如前面所述的圆柱体扭角控制系统(12.2-1)就是线性常系数系统。

一般来说，开环分布参数控制系统，可用偏微分方程组表示如下

$$
\frac {\partial u _ {i} (t , \boldsymbol {x})}{\partial t} = L _ {i} \left(u _ {1} (t, \boldsymbol {x}), u _ {2} (t, \boldsymbol {x}), \dots u _ {n} (t, \boldsymbol {x}), f ^ {1} (t, \boldsymbol {x}), \dots f ^ {r} (t, \boldsymbol {x})\right), i = 1, 2, \dots , n
$$

其中 $\boldsymbol{x}=(x_{1},x_{2},\cdots,x_{m})\in\Omega,\Omega$ 是空间变量的变化区域，其边界为 $\partial\Omega,\Omega$ 是 m 维欧氏空间中的某一连通区域。 $f^{j}(t,\boldsymbol{x}),j=1,2,\cdots,r$ 是系统的控制量。 $L_{i},i=1,2,\cdots,n$ ，是偏微分算子。令 $\boldsymbol{U}(t,\boldsymbol{x})=(u_{1}(t,\boldsymbol{x}),u_{2}(t,\boldsymbol{x}),\cdots,u_{n}(t,\boldsymbol{x}))$ ， $\boldsymbol{f}(t,\boldsymbol{x})=(f^{1}(t,\boldsymbol{x}),f^{2}(t,\boldsymbol{x}),\cdots,f^{r}(t,\boldsymbol{x}))$ ， $\boldsymbol{L}=(L_{1},L_{2},\cdots,L_{n})$ ，那么上述方程可以写成向量形式

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = \boldsymbol {L} (\boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} (t, \boldsymbol {x})), \quad \boldsymbol {x} \in \Omega \tag {12.3-9}
$$

系统的初始条件为

$$
\boldsymbol {U} (t, \boldsymbol {x}) \mid_ {t = 0} = \boldsymbol {U} _ {0} (\boldsymbol {x}), \tag {12.3-10}
$$

边界条件为

$$
M _ {j} \left(u _ {1} \left(t, \boldsymbol {x} ^ {\prime}\right), \dots , u _ {n} \left(t, \boldsymbol {x} ^ {\prime}\right)\right) = 0, \quad j = 1, 2, \dots , N, \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega
$$

如令 $M=(M_{1},M_{2},\cdots,M_{N})$ ，则边界条件可写成向量方程

$$
\boldsymbol {M} \left(\boldsymbol {U} \left(t, \boldsymbol {x} ^ {\prime}\right)\right) = 0, \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega \tag {12.3-11}
$$

其中 $M_{j}, j=1,2,\cdots,N$ 是偏微分算子。

如果系统是线性的, L 将是线性算子, 这时式(12.3-9)将变成

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L (t, \boldsymbol {x}) \boldsymbol {U} (t, \boldsymbol {x}) + D (t, \boldsymbol {x}) \boldsymbol {f} (t, \boldsymbol {x}), \quad \boldsymbol {x} \in \Omega \tag {12.3-12}
$$

边界条件为

$$
M \boldsymbol {U} (t, \boldsymbol {x} ^ {\prime}) = 0, \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega \tag {12.3-13}
$$

其中 L 和 M 分别是 $n \times n, N \times n$ 阶矩阵线性微分算子。 $D(t, x)$ 是 $n \times r$ 阶矩阵。

在这些方程中， $U(t, x)$ 叫做系统的状态， $f(t, x)$ 也叫做系统的输入。在一般情况下，系统状态不能直接测量到，测量元件所能给出的量往往是系统状态的一个函数，这时观测器方程可以表示为

$$
\boldsymbol {V} (t, \boldsymbol {x}) = s \boldsymbol {U} (t, \boldsymbol {x}) \tag {12.3-14}
$$

其中 $V(t, x)$ 叫做系统的输出。S 是测量算子。

一个分布参数系统，就其控制和测量方式来说，较集中参数系统有更大的灵活性和多样性，这是分布参数控制系统的一个重要特点。比如，为了控制一个物体内部温度的分布，我们可以在物体内部有限个点（或区域）上进行控制，也可以在物体边界的有限个点（或区域）上进行控制，甚至在整个区域内部或整个边界上进行控制等。目前，分布参数控制系统，按其控制方式，常见到的有以下几种。

一种是点控制。这种控制的特点是控制作用集中加在分布参数对象的有限个孤立点上，如前面所说的弹性梁的点控制，就是控制力 $f(t, x)$ 集中加在梁上一点 $x_{c}$ 处。再如温度场的控制。在式(12.1-2)中，如果 $f(t, x, y, z) = \sum_{i=1}^{n} \theta_{i}(t) \delta(x - x_{i}, y - y_{i}, z - z_{i})$ ， $(x_{i}, y_{i}, z_{i}) \in \Omega, i = 1, 2, \cdots, n, \theta_{i}(t)$ 是集中可调热源。这就是在 $\Omega$ 内有限个孤立点上集中加热来控制 $\Omega$ 内的温度分布 $^{[10]}$ 。

在点控制的情况下，系统方程中出现 $\delta$ 函数，这种函数不同于一般的函数，叫做广义函数，在第 12.6 节中我们将讨论这种系统的分析方法。

另一种控制方式是分布控制。即控制作用分别加在受控对象的有限个区域上，甚至在整个受控对象上。如弹性梁的分布控制，控制作用是加在 $x_{c}$ 点附近的小区域 $\Delta$ 上。同样，在温度控制中，如果控制作用取成 $f(t,x,y,z) = \sum_{i=1}^{n}\theta_i(t)W_i(x,$

$y, z)$ , $W_{i}(x, y, z)$ 是定义在 $\Omega_{i}$ 上的函数， $\Omega_{i} \subset \Omega$ ，这就是温度分布控制。

第三种方式是边界控制，控制作用只加在受控对象的边界上。反映在系统方程中，控制作用将出现在边界条件里，对式(12.3-9)的边界条件式(12.3-11)将变成以下形式

$$
\boldsymbol {M} \left(\boldsymbol {U} \left(t, \boldsymbol {x} ^ {\prime}\right), \boldsymbol {f} _ {\partial \Omega} \left(t, \boldsymbol {x} ^ {\prime}\right)\right) = 0, \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega \tag {12.3-15}
$$

其中 $f_{\partial\Omega}(t,x^{\prime})$ 是边界控制输入。而对式(12.3-12)的线性系统其边界条件式(12.3-13)将变成

$$
\boldsymbol {M} \boldsymbol {U} (t, \boldsymbol {x} ^ {\prime}) = \boldsymbol {f} _ {\partial \Omega} (t, \boldsymbol {x} ^ {\prime}), \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega \tag {12.3-16}
$$

所以对线性系统来说，变成了非齐次边界条件问题。

控制作用加在边界上的方法，可以是点控制，也可以是分布控制。比如，在圆柱体扭角控制系统中，就是在边界 x=0 处加的控制作用，因而是点控制。再如前面说过的温度场控制，如把边界 $\partial\Omega$ 分成两部分 $\partial\Omega_{1},\partial\Omega_{2}$ , 在 $\partial\Omega_{1}$ 上 $\frac{\partial u}{\partial n}=0$ , 在 $\partial\Omega_{2}$ 上, $\left.\frac{\partial u}{\partial n}\right|_{\partial\Omega_{2}}=W(t,x,y,z),(x,y,z)\in\partial\Omega_{2}$ , $W(t,x,y,z)$ 是控制作用，这就是边界分布控制。

相应于上面的几种控制方式，也有相应的测量方式。这就是点测量，分布测量和边界测量。

在点测量的情况下，测得的是分布参数对象的一个或有限个孤立点上的运动状态。例如弹性梁的点测量，温度场的点测量等。

如果观测器能够测量到受控对象的一个或有限个区域甚至是整个区域上各点的运动状态，那就是分布测量。在实际工程问题中这种测量是很难实现的。

当测量元件放在对象的边界上，测得的量是对象边界上的运动状态，这就是边界测量。这种测量可以是点测量也可以是分布测量。

分布参数控制系统在控制和测量方式上的这些特点，相应地带来了系统分析和设计上的复杂性。如点测量点控制的分布参数系统分析问题，就是一个比较复杂而困难的问题。

下面，我们再简单地讨论一下分布参数系统分析的传递函数方法。

研究一维空间变量的分布参数控制系统，其运动方程为

$$
a _ {n 0} (x) \frac {\partial^ {n} \gamma (t , x)}{\partial t ^ {n}} = \sum_ {i + j = r} a _ {i j} (x) \frac {\partial^ {r} \gamma (t , x)}{\partial x ^ {j} \partial t ^ {i}} + u (t) \delta (x), \quad 0 <   x <   l, \quad 0 <   t <   \infty \tag {12.3-17}
$$

初始条件为

$$
y (0, x) = \varphi_ {0} (x), \frac {\partial y (t , x)}{\partial t} \Bigg | _ {t = 0} = \varphi_ {1} (x), \dots , \frac {\partial^ {n - 1} y (t , x)}{\partial t ^ {n - 1}} \Bigg | _ {t = 0} = \varphi_ {n - 1} (x) \tag {12.3-18}
$$

边界条件为

$$
\sum_ {i = 0} ^ {k - 1} c _ {i j} \frac {\partial^ {i} y}{\partial x ^ {i}} \Bigg | _ {x = 0} + \sum_ {i = 0} ^ {k - 1} d _ {i j} \frac {\partial^ {i} y}{\partial x ^ {i}} \Bigg | _ {x = l} = 0, \quad j = 1, 2, \dots , k \tag {12.3-19}
$$

其中 $c_{ij}, d_{ij}$ 都是常数，k 是方程中 $y(t, x)$ 对 x 偏导数的最高次项。 $y(t, x)$ 对 x 的零阶导数就是 $y(t, x)$ 本身。这是齐次边界条件。 $u(t) \delta(x)$ 一项是控制器的输出并且以集中力的形式作用在 x=0 处。控制器的动力学方程为

$$
b _ {0} \frac {d ^ {m} u (t)}{d t ^ {m}} + b _ {i} \frac {d ^ {m - 1} u (t)}{d t ^ {m - 1}} + \dots + b _ {m} u (t) = f (t) - y (t, x _ {g}) \tag {12.3-20}
$$

其中 $b_{i}, i=0,1,2,\cdots,m$ 是常数， $f(t)$ 是系统的输入， $y(t, x_{g})$ 是受控对象在 $x=x_{g}$ 处的状态。m 个初始条件为

$$
u (0) = u _ {0 0}, \frac {d u}{d t} \Big | _ {t = 0} = u _ {1 0}, \dots , \frac {d ^ {m - 1} u}{d t ^ {m - 1}} \Big | _ {t = 0} = u _ {m - 1, 0}
$$

整个系统是一个点测量，边界点控制的分布参数反馈系统。

用高阶方程化成方程组的方法，可以把它化成式(12.3-12),(12.3-13)的形式。但我们直接对式(12.3-17)和(12.3-19)作拉氏变换。

在式(12.3-17)两边作拉氏变换后，得到象函数的 k 阶微分方程

$$
\begin{array}{l} a _ {n 0} (x) \left[ s ^ {n} Y (s, x) - s ^ {n - 1} \varphi_ {0} (x) - \dots - \varphi_ {n - 1} (x) \right] \\ = \sum_ {i + j = r} a _ {i j} (x) \frac {d ^ {j}}{d x ^ {j}} \left[ s ^ {i} Y (s, x) - s ^ {i - 1} \varphi_ {0} (x) - \dots - \varphi_ {i - 1} (x) \right] + U (s) \delta (x) \tag {12.3-21} \\ \end{array}
$$

同样，对边界条件式(12.3-19)两边作拉氏变换，得到

$$
\left. \sum_ {i = 0} ^ {k - 1} c _ {i j} \frac {d ^ {i} Y (s , x)}{d x ^ {i}} \right| _ {x = 0} + \left. \sum_ {i = 0} ^ {k - 1} d _ {i j} \frac {d ^ {i} Y (s , x)}{d x ^ {i}} \right| _ {x = l} = 0, \quad j = 1, 2, \dots , k \tag {12.3-22}
$$

将方程(12.3-21)整理后，可以变成

$$
\begin{array}{l} P _ {k} (s, x) \frac {d ^ {k} Y}{d x ^ {k}} + P _ {k - 1} (s, x) \frac {d ^ {k - 1} Y}{d x ^ {k - 1}} + \dots + P _ {0} (s, x) Y \\ = \sum_ {c = 0} ^ {n - 1} Q _ {i} (x, s, \varphi_ {i} (x)) + U (s) \delta (x) \\ \end{array}
$$

式中

$$
P _ {j} (s, x) = \sum_ {p, q, j} s ^ {p} a _ {q j} (x)
$$

$$
Q _ {i} (x, s, \varphi_ {i} (x)) = \sum_ {\substack {\alpha = 0 \\ p, q, l}} s ^ {p} a _ {q l} (x) \frac {d ^ {x} \varphi_ {i} (x)}{d x ^ {\alpha}}
$$

当 $\alpha=0$ 时， $\frac{d^{\alpha}\varphi_{i}}{dx^{\alpha}}$ 就是 $\varphi_{i}$ 本身。

在边界条件式(12.3-22)下，求解方程

$$
P _ {k} (s, x) \frac {d ^ {k} Y (s , x)}{d x ^ {k}} + P _ {k - 1} (s, x) \frac {d ^ {k - 1} Y (s , x)}{d x ^ {k - 1}} + \dots + P _ {0} (s, x) Y (s, x) = \delta (x - \xi) \tag {12.3-23}
$$

设式(12.3-23)对应的齐次方程的基本解组为 $Y_{1}(s,x),\cdots,Y_{k}(s,x)$ ，而系统的脉冲过渡函数为 $G(x,\eta,s)$ ，则式(12.3-23)的通解为

$$
\begin{array}{l} Y (s, x) = \sum_ {i = 1} ^ {k} A _ {i} Y _ {i} (s, x) + \int_ {0} ^ {x} G (x, \eta , s) \delta (\eta - \xi) d \eta \\ = \left\{ \begin{array}{l} \sum_ {i = 1} ^ {k} A _ {i} Y _ {i} (s, x) + G (x, \xi , s), \quad x > \xi \\ \sum_ {i = 1} ^ {k} A _ {i} Y _ {i} (s, x), \quad x <   \xi \end{array} \right. \tag {12.3-24} \\ \end{array}
$$

式中 $A_{i}$ 为任意常数。根据 $k$ 个边界条件式(12.3-22)，可以得到 $A_{i}$ 应满足的代数方程，从方程中解出 $A_{i}$ 再代到式(12.3-24)中，这时得到的 $Y(s,x)$ 便是方程(12.3-23)在边界条件式(12.3-22)下的解。这个解有明确的物理意义，它是在 $x = \xi$ 处加一集中力作为控制量对环节的响应 $y(t,x)$ 之间的传递函数。我们用 $\mathcal{H}(x,\xi ,s)$ 来记它，即

$$
\mathcal {H} (x, \xi , s) = \left\{ \begin{array}{l l} \sum_ {i = 0} ^ {k} A _ {i} Y _ {i} (s, x) + G (x, \xi , s), & x > \xi \\ \sum_ {i = 0} ^ {k} A _ {i} Y _ {i} (s, x), & x <   \xi \end{array} \right. \tag {12.3-25}
$$

$\mathcal{H}(x, \xi, s)$ 就是方程(12.3-23)的格林函数。一旦知道了格林函数，方程(12.3-21)的解就可以很容易地给出。它是

$$
\begin{array}{l} Y (s, x) = \int_ {0} ^ {l} \mathcal {H} (x, \xi , s) \left[ \sum_ {i = 1} ^ {n - 1} Q _ {i} (\xi , s, \varphi_ {i} (\xi)) + U (s) \delta (\xi) \right] d \xi \\ = W (x, s) U (s) + \sum_ {i = 1} ^ {n - 1} \int_ {0} ^ {l} \mathcal {H} (x, \xi , s) Q _ {i} (\xi , s, \varphi_ {i} (\xi)) d \xi \tag {12.3-26} \\ \end{array}
$$

式中 $W(x,s) = \mathcal{H}(x,0,s)$ ，它的物理意义是在 $x = 0$ 处加集中力作为控制量对环节响应 $y(t,x)$ 之间的传递函数。由式(12.3-26)看出， $y(t,x)$ 由两部分组成，第一部分 $W(x,s)U(s)$ 是控制作用引起的强迫运动，而第二部分则是由初始条件引起的自由运动。

按第二章已经讲过的常微分方程拉氏变换解法，求解控制器方程，其解为

$$
U (s) = \frac {1}{D (s)} [ F (s) - Y (s, x _ {g}) ] + \frac {N _ {0} (s)}{D (s)} \tag {12.3-27}
$$

式中 $D(s)=b_{0}s^{m}+b_{1}s^{m-1}+\cdots+b_{m-1}s+b_{m},N_{0}(s)=b_{0}u_{00}s^{m-1}+(b_{0}u_{10}+b_{1}u_{00})s^{m-2}+\cdots+(b_{0}u_{m-1,0}+b_{1}u_{m-2,0}+\cdots+b_{m}u_{00})$ 。

$\frac{1}{D(s)}$ 为控制器对输入的传递函数。将式(12.3-27)代到式(12.3-26)中，便

得到

$$
\begin{array}{l} Y (s, x) = W (x, s) \left\{\frac {1}{D (s)} [ F (s) - Y (s, x _ {g}) ] + \frac {N _ {0} (s)}{D (s)} \right\} \\ + \sum_ {i = 0} ^ {n - 1} \int_ {0} ^ {l} \mathcal {K} (x, \xi , s) Q _ {i} (\xi , s, \varphi_ {i} (\xi)) d \xi \tag {12.3-28} \\ \end{array}
$$

在该式中，令 $x = x_{g}$ ，便有

$$
\begin{array}{l} Y (s, x _ {g}) = W \left(x _ {g}, s\right) \left\{\frac {1}{D (s)} [ F (s) - Y (s, x _ {g}) ] + \frac {N _ {0} (s)}{D (s)} \right\} \\ + \sum_ {i = 0} ^ {n - 1} \int_ {0} ^ {l} \mathcal {K} (x _ {g}, \xi , s) Q _ {i} (\xi , s, \varphi_ {i} (\xi)) d \xi \tag {12.3-29} \\ \end{array}
$$

解出 $Y(s, x_g)$ , 得到

$$
\begin{array}{l} Y (s, x _ {g}) = \frac {W \left(x _ {g} , s\right) \frac {1}{D (s)}}{1 + W \left(x _ {g} , s\right) \frac {1}{D (s)}} F (s) \\ + \frac {\frac {W \left(x _ {g} , s\right) N _ {0} (s)}{D (s)} + \sum_ {i = 0} ^ {n - 1} \int_ {0} ^ {l} \mathscr {K} \left. x _ {g} , \xi , s\right) Q _ {i} (\xi , s , \varphi_ {i} (\xi)) d \xi}{1 + W \left(x _ {g} , s\right) \frac {1}{D (s)}} \tag {12.3-30} \\ \end{array}
$$

当系统的初始条件为零时，式(12.3-30)第二项为零，这时有

$$
Y (s, x _ {g}) = \frac {W (x _ {g} , s) \frac {1}{D (s)}}{1 + W (x _ {g} , s) \frac {1}{D (s)}} F (s) \tag {12.3-31}
$$

由此

$$
\frac {Y (s , x _ {g})}{F (s)} = \frac {W (x _ {g} , s) \frac {1}{D (s)}}{1 + W (x _ {g} , s) \frac {1}{D (s)}} \tag {12.3-32}
$$

这就是闭路系统输出对输入的传递函数。

把式 $(12.3-31)$ 代到式 $(12.3-27)$ （此时 $N_{0}(s)\equiv0$ ），得到

$$
U (s) = \frac {\frac {1}{D (s)}}{1 + W \left(x _ {g} , s\right) \frac {1}{D (s)}} F (s) \tag {12.3-33}
$$

将式(12.3-33)代回到式(12.3-26)中（此时 $Q_{i}(\xi,s,\varphi_{i}(\xi))\equiv0$ )，便有

$$
Y (s, x) = \frac {W (x , s) \frac {1}{D (s)}}{1 + W \left(x _ {\mathrm{g}} , s\right) \frac {1}{D (s)}} F (s)
$$

由此

$$
\frac {Y (s , x)}{F (s)} = \frac {W (x , s) \frac {1}{D (s)}}{1 + W (x _ {g} , s) \frac {1}{D (s)}} \tag {12.3-34}
$$

这就是系统状态对输入的闭路传递函数。

我们注意到系统输出对输入的传递函数

$$
\Phi (s, x _ {g}) = \frac {Y (s , x _ {g})}{F (s)}
$$

是闭环传递函数，而

$$
K (s, x _ {g}) = \frac {W (x _ {g} , s)}{D (s)}
$$

是开环传递函数，它们之间的关系是

$$
\Phi (s, x _ {g}) = \frac {K (s , x _ {g})}{1 + K (s , x _ {g})}
$$

这和第三章中式(3.7-7)完全一致。

对本节式(12.3-1)的系统，分布参数对象的传递函数由式(12.2-9)知道为

$$
W (x, s) = - \frac {a \operatorname{ch} \frac {l - x}{a} s}{s \cdot \operatorname{sh} \frac {l}{a} s}
$$

控制器的传递函数为

$$
\frac {1}{D (s)} = \frac {k}{T s + 1}
$$

所以系统的闭环传递函数为

$$
\Phi (s, x) = \frac {- a k \mathrm{ch} \frac {l - x}{a} s}{s (T s + 1) \mathrm{sh} \frac {l}{a} s - a k \mathrm{ch} \frac {l - x}{a} s}
$$

最后，我们特别指出一类经常遇到的分布参数系统。在这类系统中，分布参数环节的传递函数是亚纯函数。所谓亚纯函数就是除去极点外再没有其他奇点并在所有其余点上解析的复变函数。亚纯函数一定能表示成两个整函数之比。整函数是在复平面上处处解析的复函数。分母整函数的零点就是亚纯函数的极点。因为整函数至多有可数多个零点，所以亚纯函数也至多有可数多个极点，而且没有有穷聚点。亚纯函数可以看成有理分式的推广，整函数可以看成多项式的推广。亚纯函数和有理分式有许多类似的性质。

当分布参数系统传递函数为亚纯函数时，我们把这种分布参数系统叫做正则系统。

对于前面讨论的这类系统，如果是正则系统，根据式(12.3-25),格林函数可以写成

$$
\mathscr {K} (x, \xi , s) = \frac {B (x , \xi , s)}{A (s)}
$$

式中 $B(x, \xi, s)$ 和 $A(s)$ 都是 s 的整函数，而

$$
W (x, s) = \mathscr {H} (x, 0, s) = \frac {B (x , 0 , s)}{A (s)}
$$

由式(12.3-31)知道

$$
Y (s, x _ {g}) = \frac {\frac {B (x _ {g} , 0 , s)}{A (s) D (s)}}{1 + \frac {B (x _ {g} , 0 , s)}{A (s) D (s)}} F (s) = \frac {B (x _ {g} , 0 , s)}{A (s) D (s) + B (x _ {g} , 0 , s)} F (s)
$$

我们把方程

$$
\mathscr {D} (s) = A (s) D (s) + B \left(x _ {\mathrm{g}}, 0, s\right) = 0 \tag {12.3-35}
$$

叫做系统的特征方程。显然 $\mathcal{D}(s)$ 是个整函数。以后会看到，这个整函数的零点（即特征根）分布，决定了这个系统的稳定性。

#### 12.4 分布参数控制系统的稳定性

对于分布参数控制系统的动态性能，首要和基本的要求是系统的稳定性。也就是要求系统在各种不利因素的影响下，仍能稳定地工作而不发散。这一点和对集中参数系统稳定性的要求是一样的。但是，由于分布参数系统有无穷多个自由度，其稳定性问题要比集中参数系统复杂。例如，对线性集中参数系统，只要系统所有的本征值都有负实部，那么系统一定是渐近稳定的。但对分布参数系统来说，即使系统的本征值都有负实部，系统也不一定渐近稳定。目前，关于分布参数系统稳定性的研究，仍然是个十分重要的问题。

分布参数系统的稳定性包括两个方面的问题，一个是系统稳定性的准则是什么，另一个就是按给定的准则如果系统不稳定时，如何能使系统稳定，即所谓系统的镇定问题。我们先来说明分布参数系统稳定性的概念。

我们知道，稳定性概念的一个中心思想就是未受扰运动 $U(t)$ 和一切相对于 $U(t)$ 的受扰运动作比较，也就是说，把系统的预定工作状态和一切受到扰动后的工作状态作比较，由此来研究系统在受到扰动后，是否仍能保持在预定的工作状态上。为了要做这种比较，就必须有一个用来权衡系统所处的两个不同状态是“接近”还是“远离”的尺度。这个尺度就是两种状态的“距离”。对于集中参数系统来说，这种尺度就是第二章中式(2.4-3)所规定的欧氏空间中两点的距离。由于分布参数系统有无穷多个自由度，我们自然会想到，应该在无穷维空间来研究 这个问题。第二章中所讲的距离空间，希尔伯特空间等就是我们所需要的这种空间。

我们先从一个具体系统的稳定性问题研究起，然后就一般系统的稳定性给出严格定义。

给定系统的状态方程为

$$
\frac {\partial^ {n} y (t , x)}{\partial t ^ {n}} = F \left[ t, x, y, \frac {\partial y}{\partial t}, \dots , u \right]
$$

$$
\frac {d ^ {m} u (t)}{d t ^ {m}} = f \left[ t, u, \frac {d u}{d t}, \dots , y \right] \tag {12.4-1}
$$

当系统的边界条件和初始条件给定后，系统的解就唯一确定了。

这个系统的状态是由 n 个双变量函数 $y(t, x)$ , $\frac{\partial y(t, x)}{\partial t}$ , $\cdots$ , $\frac{\partial^{n-1} y(t, x)}{\partial t^{n-1}}$ 及 m 个单变量函数 $u(t)$ , $\frac{du(t)}{dt}$ , $\cdots$ , $\frac{d^{m-1} u(t)}{dt^{m-1}}$ 描述的。固定任一时刻 $t_{1}$ ，系统状态是 n 个 x 的函数和 m 个数，即 $y(t, x)_{t=t_{1}}$ , $\left.\frac{\partial y(t, x)}{\partial t}\right|_{t=t_{1}}$ , $\cdots$ , $\left.\frac{\partial^{n-1} y(t, x)}{\partial t^{n-1}}\right|_{t=t_{1}}$ , $u(t)\big|_{t=t_{1}}, \frac{du(t)}{dt}\big|_{t=t_{1}}, \cdots, \frac{d^{m-1} u(t)}{dt^{m-1}}\big|_{t=t_{1}}$ 。要想在欧氏空间来描述这种状态显然是不行的。但我们可以仿照欧氏空间的情况，把 n 个单变量 x 的函数 $\alpha_{1}(x)$ , $\cdots$ , $\alpha_{n}(x)$ 和 m 个数 $\beta_{1}, \beta_{2}, \cdots, \beta_{m}$ 看成一个向量（或点）z，并记作 $z=(\alpha_{1}(x), \cdots, \alpha_{n}(x), \beta_{1}, \beta_{2}, \cdots, \beta_{m})$ ，其中 $\alpha_{i}(x), i=1,2,\cdots,n; \beta_{j}, j=1,2,\cdots,m$ 仍叫做向量的分量。我们规定，当且仅当 z 中所有分量都恒为零时，叫 z 为零向量。两个向量 $z_{1}$ 和 $z_{2}$ ，当且仅当它们对应的分量都相等时，则称 $z_{1}$ 和 $z_{2}$ 是相等的。把所有这种向量的全体记作 $\zeta_{0}$ ，对 $\zeta_{0}$ 中任意两个向量 $z_{1}=(\alpha_{11}(x), \alpha_{21}(x), \cdots, \alpha_{n1}(x), \beta_{11}, \beta_{21}, \cdots, \beta_{m1})$ 和 $z_{2}=(\alpha_{22}(x), \alpha_{22}(x), \cdots, \alpha_{n2}(x), \beta_{21}, \beta_{22}, \cdots, \beta_{m2})$ 定义一个正的实数和它们对应

$$
\begin{array}{l} \rho \left(\mathbf {z} _ {1}, \mathbf {z} _ {2}\right) = \left\{\sum_ {i = 1} ^ {n} \left(\max _ {x} | \alpha_ {i 1} (x) - \alpha_ {i 2} (x) |\right) ^ {2} + \sum_ {i = 1} ^ {n} \left(\max _ {x} \left| \frac {d \alpha_ {i 1} (x)}{d x} - \frac {d \alpha_ {i 2} (x)}{d x} \right|\right) ^ {2} \right. \\ + \dots + \sum_ {i = 1} ^ {n} \left(\max _ {x} \left| \frac {d ^ {n - 1} \alpha_ {i 1} (x)}{d x ^ {n - 1}} - \frac {d ^ {n - 1} \alpha_ {i 2} (x)}{d x ^ {n - 1}} \right|\right) ^ {2} \\ \left. + \left(\beta_ {1 1} - \beta_ {2 1}\right) ^ {2} + \dots + \left(\beta_ {m 1} - \beta_ {m 2}\right) ^ {2} \right\} ^ {\frac {1}{2}} \tag {12.4-2} \\ \end{array}
$$

我们把 $\rho(\cdot,\cdot)$ 叫做 $\mathfrak{H}$ 中的距离。它有以下三个性质：

(1) $\rho(z_{1}, z_{2}) \geqslant 0$ ，当且仅当 $z_{1} = z_{2}$ 时 $\rho(z_{1}, z_{1}) = 0$ ，(非负性)。

(2) $\rho(z_{1}, z_{2}) = \rho(z_{2}, z_{1})$ , (对称性)。

(3) $\rho(z_1, z_2) \leqslant \rho(z_1, z_3) + \rho(z_3, z_2)$ , (三角不等式)。在 $\mathfrak{H}$ 上赋予距离 $\rho$ 以后， $\mathfrak{H}$ 叫做距离空间。当然，式(12.4-2)并不是 $\mathfrak{H}$ 上赋距的唯一方法。可以根据具体

问题的需要而赋予不同的距离。

如同欧氏空间中两个点间距离一样，式(12.4-2)定义的距离 $\rho$ 就表示了 $\mathfrak{H}$ 中两点 $z_{1}, z_{2}$ 的“接近”或“远离”的程度。如果 $z_{1}$ 和 $z_{2}$ 很接近，即 $\alpha_{1}(x) - \alpha_{2}(x)$ ， $i = 1, 2, \cdots, n; \beta_{j1} - \beta_{j2}, j = 1, 2, \cdots, m$ 都很小时，那么 $\rho$ 就很小。反之，如果距离 $\rho$ 很小，那么这些差值也就很小，从而 $z_{1}$ 和 $z_{2}$ 就很接近。当 $\rho = 0$ 时， $z_{1}$ 和 $z_{2}$ 就完全相等了。距离 $\rho$ 好比一把尺子，用它可以度量空间中任意两点之间的相对距离。

在 $\mathfrak{S}$ 中给定一个点 $z_{1}$ 和一个小的正数 $\varepsilon$ ，一切和 $z_{1}$ 的距离小于 $\varepsilon$ 的点 $z$ 的全体，叫做点 $z_{1}$ 的 $\varepsilon$ 邻域。它是一个以 $z_{1}$ 为球心 $\varepsilon$ 为半径的小球。凡在这个小球内的点和 $z_{1}$ 的距离都小于 $\varepsilon$ 。

如果距离空间 $\mathfrak{H}$ 中的点 $z$ 是 $t$ 的函数，即 $z$ 的每个分量都是 $t$ 的函数，记作 $z(t) = (\alpha_1(t,x),\alpha_2(i,x),\dots ,\alpha_n(t,x),\beta_1(t),\dots ,\beta_m(t))$ 。那么当 $t$ 变化时，点 $z(t)$ 便从空间 $\mathfrak{H}$ 中一个点变到另一个点。我们把由于 $t$ 的变化而使 $z(t)$ 变化所历经的点集合，叫做 $\mathfrak{H}$ 中的“曲线”。若 $z(t)$ 的每个分量对 $t$ 都是连续函数，就说曲线 $z(t)$ 对 $t$ 也是连续的。

假如我们任意固定一个时刻 t，并令 $y(t, x) = \alpha_{1}(x)$ ， $\frac{\partial y(t, x)}{\partial t} = \alpha_{2}(x)$ ，…， $\frac{\partial^{n-1}y(t, x)}{\partial t^{n-1}} = \alpha_{n}(x)$ ， $u(t) = \beta_{1}, \cdots, \frac{d^{m-1}u(t)}{dt^{m-1}} = \beta_{m}$ ，那么系统式(12.4-1)在 t 时刻的状态便对应于距离空间 $\xi$ 中一个点 $z = (\alpha_{1}(x), \cdots, \alpha_{n}(x), \beta_{1}, \cdots, \beta_{m})$ ，称 z 为系统的描绘点。当 t 连续变化时，系统状态也随之变化，从而描绘点 z 在 $\xi$ 中对应地描绘出一条“曲线”，把它叫做系统的运动轨迹，记作 $z(t)$ 。因此，系统式(12.4-1)是在 $t = t_{0}$ 初始条件为 $z_{0} = (\varphi_{0}(x), \cdots, \varphi_{n-1}(x), w_{00}, w_{10}, \cdots, w_{m-1,0})$ 时的运动，并在空间 $\xi$ 中对应一条从 $z_{0}$ 出发的运动轨迹 $z(t)$ 。

现在，我们来建立系统式(12.4-1)的稳定性概念。

设系统在 $t=t_{0}$ 时从 $z_{0}$ 出发的运动轨迹为 $z(t)$ ，它是系统的预定工作状态，称它为未受扰运动，如果系统在 $t=t_{0}$ 时受到了某种干扰，使初始条件不再是 $z_{0}$ ，而是 $\widetilde{z}_{0}=(\widetilde{\varphi}_{0}(x),\widetilde{\varphi}_{1}(x),\cdots,\widetilde{\varphi}_{n-1}(x),\widetilde{u}_{00},\cdots,\widetilde{u}_{m-1,0})$ ， $z_{0}\neq\widetilde{z}_{0}$ 。那么，受到干扰后的系统工作状态，便是一条在 $t=t_{0}$ 时，从 $\widetilde{z}_{0}$ 出发的运动轨迹 $\widetilde{z}(t)$ ，它称之为相对于 $z(t)$ 的受扰运动。

如果任意给定一个正数 $\varepsilon$ ，总存在一个正数 $\delta$ ，它只和 $t_0, \varepsilon$ 有关，对任意 $\rho(z_0, \tilde{z}_0) < \delta$ 的 $\tilde{z}_0$ ，使所有 $t > t_0$ 都有 $\rho(z(t), \tilde{z}(t)) < \varepsilon$ ，我们就说未受扰运动 $z(t)$ 是稳定的。此外，如果当 $t \to \infty$ 时，若有 $\rho(z(t), \tilde{z}(t)) \to 0$ ，则称未受扰运动 $z(t)$ 是渐近稳定的。当 $\delta$ 只和 $\varepsilon$ 有关而与 $t_0$ 无关时，则叫做一致渐近稳定。

反之，对任意的正数 $\varepsilon$ ，找不到这样的 $\delta$ ，那么未受扰运动 $z(t)$ 就是不稳定的。

未受扰运动 $z(t)$ 是空间 $\mathfrak{H}$ 中一条从 $z_0$ 开始的连续曲线。我们沿这曲线的每 个点 $z(t)$ ，作出它的 $\varepsilon$ 邻域，同时对 $z_{0}$ 点作出它的 $\delta$ 邻域。如果系统在 $t_{0}$ 时从 $z_{0}$ 的 $\delta$ 邻域内任意点出发，其运动轨迹在任意时刻 $t > t_{0}$ 时的状态，总位于未受扰运动同一时刻 t 的状态 $z(t)$ 的 $\varepsilon$ 邻域内，那么未受扰运动 $z(t)$ 是稳定的，这就是运动稳定性的定义在距离空间 $\xi$ 中的几何解释。

可以看出，分布参数系统稳定性的这种定义，实质上是集中参数系统李雅普诺夫稳定性定义的推广。

我们来讨论一个例子。式(12.3-1)给出的分布参数系统，其状态是 $r(t,x)$ $\frac{\partial r(t,x)}{\partial t},u(t)$ 。令 $\mathbf{z} = (\alpha_1(x),\alpha_2(x),u),0\leqslant x\leqslant l$ 。定义距离

$$
\rho \left(\mathbf {z} _ {1}, \mathbf {z} _ {2}\right) = \left\{\left(\max _ {x} \mid \alpha_ {1 1} (x) - \alpha_ {1 2} (x) \mid\right) ^ {2} + \left(\max _ {x} \mid \alpha_ {2 1} (x) - \alpha_ {2 2} (x) \mid\right) ^ {2} + \left(u _ {1} - u _ {2}\right) ^ {2} \right\} ^ {\frac {1}{2}},
$$

则所有的 z 构成距离空间 $\tilde{y}$ ，系统的运动描述了 $\tilde{y}$ 中一条曲线 $z(t)=\left\{\begin{aligned}&r(t,x),\\&\frac{\partial r(t,x)}{\partial t},u(t)\end{aligned}\right\}$ 。

现在看一下系统零解的稳定性，即 $r(t,x)\equiv 0,\frac{\partial r(t,x)}{\partial t}\equiv 0,u(t)\equiv 0$ 的稳定性，它相当于零初始条件下系统的解（平凡解)。现给任一非零初始条件 $r(0,x) = \varphi_0(x),\frac{\partial r(t,x)}{\partial t}\Big|_{t = 0} = \varphi_1(x),u(0) = u_0$ ，即 $\mathbf{z}_0 = (\varphi_0(x),\varphi_1(x),u_0)$ ，由 $\mathbf{z}_0$ 出发的系统运动记为 $z(t) = \left[r(t,x),\frac{\partial r(t,x)}{\partial t},u(t)\right]$ ，这时零解的稳定性就是，对任意给定的正数 $\varepsilon$ ，总存在正数 $\delta$ ，它只和 $\varepsilon$ 有关，对任意的 $\mathbf{z}_0$ 只要 $\{(\max_x|\varphi_0(x)|)^2 +$ $(\max_x|\varphi (x)|)^2 +w^2\}^{\frac{1}{2}} <   \delta ,$ 就有 $\left\{(\max_x|r(t,x)|)^2 +\left[\max_x\left|\frac{\partial r(t,x)}{\partial t}\right|\right]^2 +u^2 (t)\right\}^{\frac{1}{2}} <   \varepsilon ,$ 则零解是稳定的。此外，当 $t\to \infty$ 时，还有 $\left\{(\max_x|r(t,x)|)^2 +\left[\max_x\left|\frac{\partial r(t,x)}{\partial t}\right|\right]^2 +\right.$ $u^{2}(t)\Bigg\}^{\frac{1}{2}}\rightarrow 0$ ，则系统是渐近稳定的。

如果系统的任务是保持圆柱体在 $x = x_{g}$ 处的扭角为零，这时受扰运动和未受扰运动就不必作全局性比较，只要对 $\mathbf{z}(t)$ 中的一个分量 $r(t,x_g)$ 和零状态作比较就能反映出系统工作性能了。这时稳定性可以定义如下：对任意给定的正数 $\varepsilon$ ，总存在正数 $\delta$ ，它只和 $\varepsilon$ 有关，对任意 $\mathbf{z}_0$ ，只要 $\{(\max_x|\varphi_0(x)|)^2 + (\max_x|\varphi_1(x)|)^2 + w_0^2\}^{\frac{1}{2}} < \delta$ ，就有 $|r(t,x_g)| < \varepsilon$ ，我们就说系统的零解是稳定的。此外，当 $t\to \infty$ 时，还有 $|r(t,x_g)|\to 0$ ，那么系统就是渐近稳定的。

下面，我们讨论一般分布参数系统的稳定性定义。

在第 12.3 节中，我们曾指出，一般分布参数系统可以用偏微分方程组表示成 式(12.3-9)的形式。稳定性问题只考虑系统的自由运动就够了，即可令 $f(t,x)\equiv0$ 。这时给定系统的状态方程为

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = \boldsymbol {L} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x})) \tag {12.4-3}
$$

边界条件和初始条件分别由式(12.3-11)和(12.3-10)确定。我们假定系统的解存在而且是唯一的。

设系统的状态空间为 $\mathfrak{H}$ , 在其上定义的距离为 $\rho$ , 它具有前面说过的距离的三个性质, 因此 $\mathfrak{H}$ 就是距离空间。在讨论稳定性的问题时, 只要有了距离就够了。但在讨论分布参数系统其他问题时, 仅仅有了距离还不够, 还必须要求状态空间有更多的性质, 这时一般的距离空间不便于作为系统的状态空间, 通常是巴拿赫 (Banach) 空间或希尔伯特空间等作为系统的状态空间。选取什么样的函数空间作为系统的状态空间, 这与研究分布参数系统的具体问题有关。

对系统式(12.4-3)，在给定边界条件式(12.3-11)和初始条件 $U(t, x) \mid_{t=t_0} = U_0(x)$ 后，方程的解便决定了系统的一个特殊运动，用 $\Phi(t, x, U_0(x), t_0)$ 表示这个解，它是 $\mathfrak{H}$ 中的一条曲线，用 $\Gamma v_0$ 表示 $\Gamma v_0 \subset \mathfrak{H}$ 。 $\mathfrak{H}$ 中任意点 $U$ 到 $\Gamma v_0$ 的距离定义为

$$
\rho (\boldsymbol {U}, \Gamma_ {\boldsymbol {v} _ {0}}) = \inf _ {\boldsymbol {u} ^ {\prime} \in \Gamma_ {\boldsymbol {v} _ {0}}} \rho (\boldsymbol {U}, \boldsymbol {U} ^ {\prime}) \tag {12.4-4}
$$

现给定另一初始条件 $\widetilde{U}_0(x)$ ，系统式(12.4-3)在这个初始条件和边界条件式(12.3-11)下的解 $\Phi(t, x, \widetilde{U}_0(x), t_0)$ 也是 $\zeta$ 中的一条曲线，记作 $\Gamma_{\widetilde{u}_0}$ ，定义 $\Gamma_{v_0}$ 和 $\Gamma_{\widetilde{u}_0}$ 的距离为

$$
\rho (\Gamma_ {u _ {0}}, \Gamma_ {\widetilde {u} _ {0}}) = \sup _ {u \in \Gamma_ {\widetilde {u} _ {0}}} \rho (U, \Gamma_ {u _ {0}}) \tag {12.4-5}
$$

现在来定义系统式(12.4-3)的运动 $\Phi(t, x, U_0(x), t_0)$ 的稳定性。如果对任意给定的正数 $\varepsilon$ ，总存在一个正实数 $\delta$ ，它依赖于 $\varepsilon$ 和 $t_0$ ，当任意给定的 $\tilde{U}_0(x)$ 使 $\rho(\tilde{U}_0, \Gamma_{u_0}) < \delta(\varepsilon, t_0)$ 时，总有 $\rho(\Gamma_{\tilde{u}_0}, \Gamma_{u_0}) < \varepsilon$ 成立，我们就说未受扰运动 $\Phi(t, x, U_0(x), t_0)$ 是稳定的。此外，如果当 $t \to \infty$ 时，还有 $\rho(\Gamma_{\tilde{u}_0}, \Gamma_{u_0}) \to 0$ ，我们就说未受扰运动 $\Phi(t, x, U_0(x), t_0)$ 是渐近稳定的。如果 $\delta$ 只和 $\varepsilon$ 有关而和 $t_0$ 无关时，则叫做一致渐近稳定。

当给定了正数 $\varepsilon$ ，找不到上述的 $\delta(\varepsilon, t_{0})$ 时，则未受扰运动 $\Phi(t, x, U_{0}(x), t_{0})$ 叫做不稳定的。

运动稳定性的这个定义和我们对系统式(12.4-1)所作的定义实质上都是一致的。

需要强调指出的是，未受扰运动的稳定性显然与距离 $\rho$ 的具体选择形式有关。同一个系统，未受扰运动在这样规定的距离下是稳定的，而在另外规定的距离下却可能是不稳定的。因此，对具体系统所选择的距离 $\rho$ 必须能反映系统的工作性能和工程实际的需要。

如果系统是线性的，则式(12.4-3)变成了如下形式:

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L (t, \boldsymbol {x}) \boldsymbol {U} (t, \boldsymbol {x}) \tag {12.4-6}
$$

其中 $L(t, x)$ 是矩阵微分算子。

和集中参数系统一样，对于线性系统，任何一个未受扰运动的稳定性等价于系统零解的稳定性（所谓零解就是系统在零初始条件下的解，它在任何时刻的状态都为零)。从而系统要么全体运动都稳定，要么全体运动都不稳定。因此，对线性系统来说，提系统是否稳定是有意义的。

但对非线性系统来说，一般存在稳定和不稳定两类运动。系统可能在这种预定状态下是稳定的，而在另外预定的工作状态下却是不稳定的。因此，对非线性系统，应严格区别某个运动的稳定性和整个系统的稳定性。

在给出了系统稳定性准则以后，如何判断一个系统的运动是否稳定呢?对集中参数系统有李雅普诺夫函数直接方法。这个方法不要求解系统的运动方程，而是构造一个李雅普诺夫函数，根据这个函数的性质去判别系统运动是否稳定。无论线性或非线性系统，常系数和变系数系统，这个方法都可以应用。但是在应用中，一个很大的困难就是不容易找到李雅普诺夫函数。

对于分布参数系统，把集中参数系统的李雅普诺夫方法推广到分布参数系统上来，也有许多工作，下面我们介绍一下这方面的内容 $^{[33]}$ 。

对系统式(12.4-3)，当初始条件 $U_0(x)$ 给定后，令在边界条件式(12.3-11)下的解 $\Phi(t, x, U_0(x), t_0)$ 是未受扰运动。它是 $\mathfrak{S}$ 中一条曲线，用 $\Gamma v_0$ 表示它。 $\Gamma v_0$ 的 $r$ 邻域是指凡是 $\rho(U, \Gamma v_0) < r$ 的 $\mathfrak{S}$ 中点 $U$ 的集合，记作 $N(\Gamma v_0, r)$ 。任给一初始条件 $\tilde{U}_0(x)$ ，在这个初始条件下，系统式(12.4-3)的运动 $\Phi(t, x, \tilde{U}_0(x), t_0)$ 对 $\Phi(t, x, U_0(x), t_0)$ 是受扰运动，记 $\Phi(t, x, \tilde{U}_0(x), t_0)$ 对应 $\mathfrak{S}$ 中的曲线为 $\Gamma \tilde{v}_0$ 。

未受扰运动 $\Phi(t, x, U_0(x), t_0)$ 稳定的必要和充分条件是，存在一个实泛函 $V(t, U(x))$ ，它对所有 $t \geqslant 0$ 和 $N(\Gamma u_0, r)$ 中的点 $U(x)$ 都有定义。并且

（1）对任意充分小的正数 $\varepsilon_{1}$ ，当 $\rho(\boldsymbol{U},\Gamma v_{0})>\varepsilon_{1}$ 时，总存在一个正数 $\varepsilon_{2}$ ，使得对所有的 $t\geqslant0$ ，都有 $V(t,\boldsymbol{U}(\boldsymbol{x}))>\varepsilon_{2}$ 。

(2) 当 $\rho(\boldsymbol{U},\Gamma_{U_{0}})\rightarrow0$ 时，对 $t\geqslant t_{0}$ 一致地有

$$
\lim V (t, \boldsymbol {U} (\boldsymbol {x})) = 0
$$

(3) 泛函 $V(t, \boldsymbol{U}(\boldsymbol{x}))$ 在 $\Gamma\widetilde{v}_{0}$ 上的最大值，即

$$
V ^ {\prime} (t, \widetilde {U} _ {0} (\boldsymbol {x}), t _ {0}) = \sup _ {\boldsymbol {u} ^ {\prime} \in \Gamma_ {\widetilde {U} _ {0}} ^ {-}} V (t, \boldsymbol {U} ^ {\prime} (\boldsymbol {x}))
$$

对所有 $t \geqslant t_{0}$ 是不增加的。

以上是系统运动稳定的必要充分条件。在这些条件下，如果还有

(4) 函数 $V'(t, \tilde{U}_{0}(x), t_{0})$ 对于 $\Gamma_{v_{0}}$ 的 $\delta$ 邻域 $N(\Gamma_{v_{0}}, \delta)$ 内的所有 $\tilde{U}_{0}(x)$ ，当 $t\rightarrow\infty$ 时， $V^{\prime}(t,\widetilde{U}_{0},t_{0})\rightarrow0$ ，那么(1)—(4)是运动 $\Phi(t,x,U_{0}(x),t_{0})$ 渐近稳定的必要充分条件。

（5）如果对 $\Gamma v_{0}$ 的 $\delta$ 邻域 $N(\Gamma v_{0},\delta)$ 内的所有 $\widetilde{\boldsymbol{U}}_{0}(\boldsymbol{x})$ ，对 $t_{0}$ 一致地有 $\lim_{t\to t_{0}\to\infty}V'(t,\widetilde{\boldsymbol{U}}_{0}(\boldsymbol{x}),t_{0})=0$ ，则(1)—(5)是运动 $\Phi(t,\boldsymbol{x},\boldsymbol{U}_{0}(\boldsymbol{x}),t_{0})$ 一致渐近稳定的必要充分条件。

这一事实的详细证明，可参阅文献[33]。从上述我们可以看出，问题的关键在于找到实泛函 $V(t,U(x))$ 。对于一般的分布参数系统，找到这个实泛函 $V(t,U(x))$ 是比较困难的，但对某些特殊系统, $V(t,U(x))$ 是可以作出来的。作为上述结果的应用，我们讨论下述的线性系统

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L \boldsymbol {U} (t, \boldsymbol {x}) \tag {12.4-7}
$$

系统的状态空间 $\mathfrak{H}=L_{2}(\Omega)\times L_{2}(\Omega)\times\cdots\times L_{2}(\Omega)$ ， $L_{2}(\Omega)$ 是希尔伯特空间， $\mathfrak{H}$ 是 n 个 $L_{2}(\Omega)$ 空间的积空间，它仍是一个希尔伯特空间。L 是 $\mathfrak{H}$ 中矩阵线性算子。 $\mathfrak{H}$ 中的函数（也叫 $\mathfrak{H}$ 中的元） $U(t,x)$ 的范数定义为

$$
\| \boldsymbol {U} (t, \boldsymbol {x}) \| = \langle \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {U} (t, \boldsymbol {x}) \rangle_ {\mathfrak {H}} ^ {1 / 2} = \left\{\int_ {\Omega} \boldsymbol {U} ^ {\tau} (t, \boldsymbol {x}) \boldsymbol {U} (t, \boldsymbol {x}) d \Omega \right\} ^ {1 / 2} \tag {12.4-8}
$$

式中 $\tau$ 表示向量的转置， $\langle\cdot,\cdot\rangle_{\mathfrak{H}}$ 表示 $\mathfrak{H}$ 中的内积。由范数式(12.4-8)，可以给出 $\mathfrak{H}$ 中任意两个元的距离

$$
\rho \left(\boldsymbol {U} _ {1}, \boldsymbol {U} _ {2}\right) = \| \boldsymbol {U} _ {1} - \boldsymbol {U} _ {2} \|, \boldsymbol {U} _ {1}, \boldsymbol {U} _ {2} \in \mathfrak {H} \tag {12.4-9}
$$

由于式(12.4-7)是线性系统，我们可以只考虑零解的稳定性。为此，考虑如下的正定实泛函

$$
V (t, \boldsymbol {U} (\boldsymbol {x})) = \int_ {\Omega} \boldsymbol {U} ^ {\tau} (t, \boldsymbol {x}) \boldsymbol {U} (t, \boldsymbol {x}) d \Omega = \langle \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {U} (t, \boldsymbol {x}) \rangle \mathfrak {H} \tag {12.4-10}
$$

容易验证，上述的(1)—(2)条件, $V(t,U(x))$ 都自动满足。如果 $V(t,U(x))$ 对 t 的导数小于或等于零，即

$$
\begin{array}{l} \frac {d}{d t} V (t, \boldsymbol {U} (\boldsymbol {x})) = \frac {d}{d t} \langle \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {U} (t, \boldsymbol {x}) \rangle_ {\mathfrak {H}} \\ = \langle L U (t, x), U (t, x) \rangle_ {\mathfrak {H}} + \langle U (t, x), L U (t, x) \rangle_ {\mathfrak {H}} \leqslant 0 \tag {12.4-11} \\ \end{array}
$$

其中 $U(t,x)$ 是非零初始条件 $U_{0}(x)$ 下，方程(12.4-7)的解。条件式(12.4-11)说明 $V(t,U(x))$ 对 t 是不增的，因此(3)中的， $V'(t,U_{0}(x),t_{0})$ 也是对 $t\geqslant t_{0}$ 不增加的，这样，条件(3)满足，所以系统式(12.4-7)是稳定的。式(12.4-11)有明确的物理意义。在很多实际系统中， $V(t,U(x))$ 代表系统的能量，当条件式(12.4-11)满足时，表明这种系统只有能量的转换和耗损，而没有能量的增加。所以它是稳定的系统。线性算子 L，在满足条件式(12.4-11)时，叫做逸散算子。

以上关于系统运动稳定性的准则，并没有和系统的具体结构建立直接联系。

因此，它适用的范围比较大。在考虑到具体系统的特点时，我们还可以有其他稳定性判定准则。下面我们就线性常系数系统的稳定性作进一步的讨论。

我们知道，一个线性常系数集中参数系统

$$
\frac {d \boldsymbol {x} (t)}{d t} = A \boldsymbol {x} (t), \boldsymbol {x} (0) = \boldsymbol {x} _ {0}
$$

的解为 $x(t) = e^{At}x_0, e^{At}$ 是系统的基本解矩阵，它是 $R_{n}$ 中的算子函数（矩阵函数），具有以下性质， $e^{At}|_{t=0} = E(R_n$ 中恒等矩阵）， $e^{At_1} \cdot e^{At_2} = e^{A(t_1 + t_2)}, e^{At_1} \cdot (e^{At_1})^{-1} = e^{At_1} \cdot e^{-At_1} = E[(e^{At_1})^{-1}\text{表示} e^{At_1}\text{的逆矩阵}]$ 。这就是说 $e^{At}$ 具有群的性质。这个系统的稳定性完全取决于算子（矩阵) $A$ 的本征值在复平面上的分布。例如， $A$ 的本征值均有负实部时，这个系统一定是渐近稳定的。

对于线性常系数分布参数系统，在一定条件下，也有类似的性质。考虑下述线性分布参数系统

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {U} (t, \boldsymbol {x}) | _ {t = t _ {0}} = \boldsymbol {U} _ {0} (\boldsymbol {x}) \tag {12.4-12}
$$

L 的定义域记作 $D(L)$ 。 $U_{0}(x) \in D(L)$ 。

系统式(12.4-12)的解 $U(t, x)$ ，一般来说，不是群而是半群。在第二章里已经讲过，当 L 是 $\tilde{Q}$ 中有界算子半群 $T(t)$ 的生成算子时，式(12.4-12)的解可以表示成

$$
\boldsymbol {U} (t, \boldsymbol {x}) = T (t) \boldsymbol {U} _ {0} (\boldsymbol {x}) = e ^ {L t} \boldsymbol {U} _ {0} (\boldsymbol {x}), \boldsymbol {U} _ {0} (\boldsymbol {x}) \in D (L) \tag {12.4-13}
$$

这时系统式(12.4-12)的稳定性完全取决于 L 的本征值在复平面上的分布 $^{①}$ 。类似于集中参数系统，对于系统式(12.4-12)有以下事实成立。

对于系统式(12.4-12)，假如 L 是有界算子半群的生成算子，L 的本征值都有负实部，并且所有本征值负实部的上确界 $\gamma$ 小于零，即 $\gamma<0$ ，那么系统式(12.4-12)是渐近稳定的。如果 L 的本征值都是单重的，并且都有负实部，那么系统式(12.4-12)是稳定的。假如至少有一个本征值具有正实部，那么系统式(12.4-12)一定是不稳定的。

作为例子，我们讨论第 12.3 节中带有常微分控制器的分布参数反馈系统式 $(12.3-8)^{[9]}$ 。

受控对象的运动方程为

$$
m (x) \frac {\partial^ {2} u}{\partial t ^ {2}} + C (x) \frac {\partial u}{\partial t} + B (x) \frac {\partial u}{\partial x} + \frac {\partial^ {2}}{\partial x ^ {2}} E J (x) \frac {\partial^ {2} u}{\partial x ^ {2}} = - \left[ \sum_ {i = 1} ^ {n} x _ {i} (t) g _ {i} \right] b (x)
$$

取 $L_{2}$ 空间作为受控对象的状态空间, 即一切在 $(0, l)$ 上平方可积复值函数的全体, 按通常的函数相加和乘以复数的运算, 构成线性空间。若在其中引入内积

$$
\langle \varphi , \psi \rangle = \int_ {0} ^ {l} \varphi (x) \overline {{{{\psi (x)}}}} d x \tag {12.4-14}
$$

和范数

$$
\| \varphi \| = \langle \varphi , \varphi \rangle^ {\frac {1}{2}} = \left\{\int_ {0} ^ {l} | \varphi (x) | ^ {2} d x \right\} ^ {\frac {1}{2}} \tag {12.4-15}
$$

则 $L_{2}$ 是一个完备可分的复希尔伯特空间。记这个空间为 $L_{2}(0, l)$ ，该空间的函数叫做空间中的元。

受控对象的状态 $u(t,x)$ ，当 $t$ 给定后是 $x$ 的函数，它是 $L_{2}(0,l)$ 中的一个元。因此， $u(t,x)$ 可以看成是自变量为 $t$ 取值于 $L_{2}(0,l)$ 中的函数，今后记作 $u(t)$ 。于是，上述方程可以写成

$$
m (x) \frac {d ^ {2} u}{d t ^ {2}} + C \frac {d u}{d t} + B u + A u = - (\boldsymbol {x}, \boldsymbol {g}) b \tag {12.4-16}
$$

其中 $A, B, C$ 是 $L_{2}(0, l)$ 中的线性算子

$$
A = \frac {\partial^ {2}}{\partial x ^ {2}} E J (x) \frac {\partial^ {2}}{\partial x ^ {2}}
$$

A 的定义域 $D(A)$ 是由 $L_{2}(0, l)$ 中具有下述性质的函数 $u(x)$ 所组成: $\frac{du(x)}{dx}$ , $EJ(x) \times \frac{d^{2}u(x)}{dx^{2}}$ , $\frac{d}{dx}EJ(x)\frac{d^{2}u(x)}{dx^{2}}$ 都是绝对连续函数且属于 $L_{2}(0, l)$ , $\frac{d^{2}}{dx^{2}}EJ(x)\frac{d^{2}u(x)}{dx^{2}}$ 也属于 $L_{2}(0, l)$ , 并且 $EJ(x)\frac{d^{2}u(x)}{dx^{2}}\bigg|_{x=0} = 0$ , $\frac{d}{dx}EJ(x)\frac{d^{2}u(x)}{dx^{2}}\bigg|_{x=0} = 0$ 。此外设

$$
B = B (x) \frac {\partial}{\partial x}
$$

B 的定义域 $D(B)$ 是由 $L_{2}(0,l)$ 中那些绝对连续函数且其导数仍属于 $L_{2}(0,l)$ 的函数 $u(x)$ 所组成。设 $C(x)$ 是有界函数，则算子 C 是定义在全空间 $L_{2}(0,l)$ 上的有界算子，而 A, B 是无界算子。

在式(12.4-16)中 b 是 $L_{2}(0,l)$ 中的元。(·,·)表示 $R_{n}$ 中的内积。如记 $Gx=(x,g)b$ ，那么 G 就是一个从 $R_{n}$ 到 $L_{2}(0,l)$ 中的线性算子，叫做反馈算子。

控制方程为

$$
\frac {d \boldsymbol {x}}{d t} = J \boldsymbol {x} + \boldsymbol {k} _ {1} \mathrm{q} _ {1} + \boldsymbol {k} _ {2} q _ {2}
$$

$k_{1}, k_{2}$ 是 $R_{n}$ 中固定的常向量，J 是 $n \times n$ 阶方阵，它是 $R_{n}$ 到 $R_{n}$ 中的线性算子。利用 $L_{2}(0, l)$ 中的内积符号，可以把测量方程 $q_{1}, q_{2}$ 写成

$$
\boldsymbol {k} _ {1} q _ {1} (a _ {1}, t) = \boldsymbol {k} _ {1} \int_ {0} ^ {l} S _ {1} u (t, x) a _ {1} (x) d x = \langle S _ {1} u, a _ {1} \rangle \boldsymbol {k} _ {1} = S _ {1} u
$$

$$
\boldsymbol {k} _ {2} q _ {2} (a _ {2}, t) = \boldsymbol {k} _ {2} \int_ {0} ^ {l} S _ {2} \frac {\partial u (t , x)}{\partial t} a _ {2} (x) d x = \left\langle S _ {2} \frac {d u}{d t}, a _ {2} \right\rangle \boldsymbol {k} _ {2} = S _ {2} \frac {d u}{d t} \tag {12.4-17}
$$

式中 $a_{1}, a_{2}$ 是 $L_{2}(0, l)$ 中固定的元。显然， $S_{1}, S_{2}$ 是从 $L_{2}(0, l)$ 到 $R_{n}$ 中的线性算子，叫做测量算子。因此，控制器方程可以写成

$$
\frac {d \boldsymbol {x}}{d t} = J \boldsymbol {x} + S _ {1} u + S _ {2} \frac {d u}{d t}
$$

整个系统的方程为

$$
m \frac {d ^ {2} u}{d t ^ {2}} + C \frac {d u}{d t} + B u + A u = - G x
$$

$$
\frac {d \boldsymbol {x}}{d t} = J \boldsymbol {x} + S _ {1} u + S _ {2} \frac {d u}{d t} \tag {12.4-18}
$$

式中 $m=m(x)$ 是梁的质量密度。在式(12.4-14)中，如果带有权 $m(x)>0$ ，即

$$
\langle \varphi , \psi \rangle_ {m} = \int_ {\Omega} m (x) \varphi (x) \overline {{{{\psi (x)}}}} d x
$$

则两者定义的范数等价。此时将式(12.4-18)第一式中的首项系数变为 1,从而得到

$$
\frac {d ^ {2} u}{d t ^ {2}} + C \frac {d u}{d t} + B u + A u = - G x \tag {12.4-19}
$$

$$
\frac {d \boldsymbol {x}}{d t} = J \boldsymbol {x} + S _ {1} U + S _ {2} \frac {d u}{d t}
$$

现把式(12.4-19)化成方程组，令 $w_{1}=u,u_{2}=\frac{du}{dt},y=x-S_{2}w_{1}$ ，则上述方程变为

$$
\frac {d u _ {1}}{d t} = u _ {2}
$$

$$
\frac {d u _ {2}}{d t} = - (A + B) u _ {1} - C u _ {2} - G y - G S _ {2} u _ {1}
$$

$$
\frac {d \mathbf {y}}{d t} = J \mathbf {y} + (S _ {1} + J S _ {2}) u _ {1} \tag {12.4-20}
$$

式中 $u_{1}, u_{2} \in L_{2}(0, l), y \in R_{n}$ 。积空间 $\mathfrak{H} = L_{2}(0, l) \times L_{2}(0, l) \times R_{n}$ 是一个希尔伯特空间，取 $\mathfrak{H}$ 作为系统式(12.4-20)的状态空间，上述方程组可以写成

$$
\frac {d Y}{d t} = \mathcal {B} Y \tag {12.4-21}
$$

式中 $Y=(u_{1},u_{2},y)\in\mathfrak{H}_{\circ}$

$$
\mathcal {B} = \left( \begin{array}{c c c} 0 & I & 0 \\ - (A + B) - G S _ {2} & - C & - G \\ S _ {1} + J S _ {2} & 0 & J \end{array} \right) \tag {12.4-22}
$$

$\mathcal{B}$ 是 $\mathfrak{H}$ 中的线性算子。式(12.4-21)就是系统的状态方程。状态空间 $\mathfrak{H}$ 中的元 $Y = (u_{1}, u_{2}, y)$ 的范数为

$$
\| Y \| = \left\{\| u _ {1} \| _ {L _ {2}} ^ {2} + \| u _ {2} \| _ {L _ {2}} ^ {2} + \| y \| _ {R _ {n}} ^ {2} \right\} ^ {\frac {1}{2}} \tag {12.4-23}
$$

在这个空间中任意两点 $Y=(u_{1}, u_{2}, y)$ 和 $Z=(v_{1}, v_{2}, z)$ 的距离就是

$$
\rho (Y, Z) = \| Y - Z \| = \left\{\| u _ {1} - v _ {1} \| _ {L _ {2}} ^ {2} + \| u _ {2} - v _ {2} \| _ {L _ {2}} ^ {2} + \| y - z \| _ {R _ {n}} ^ {2} \right\} ^ {\frac {1}{2}}
$$

根据前面的讨论，系统式(12.4-21)的稳定性问题，完全取决于算子 B 及其本征值的分布。关于这个系统的稳定性问题在第 12.5 节中还要详细研究。

在应用传递函数方法研究线性集中参数系统稳定性时，传递函数的极点分布完全决定了系统的稳定性。根据极点是否在左半平面，提出了各种稳定性判据。这种方法也可以相应地推广到线性常系数分布参数系统，我们以第 12.3 节讲到的正则系统为例来说明这个问题。

式 $(12.3-30)$ 系统的输出为

$$
\begin{array}{l} Y (s, x _ {g}) = \frac {W (x _ {g} , s) \frac {1}{D (s)}}{1 + W (x _ {g} , s) \frac {1}{D (s)}} F (s) \\ + \frac {W (x _ {g} , s) \frac {N _ {0} (s)}{D (s)} + \sum_ {i = 0} ^ {n - 1} \int_ {0} ^ {l} \mathscr {K} (x _ {g} , \xi , s) Q _ {i} (\xi , s , \varphi_ {i} (\xi)) d \xi}{1 + W (x _ {g} , s) \frac {1}{D (s)}} \\ \end{array}
$$

在讨论稳定性时，令 $F(s)=0$ 。将 $W(x_{g},s)=\frac{B(x_{g},0,s)}{A(s)}$ 代到上式便得到

$$
Y (s, x _ {g}) = \frac {N _ {0} (s) B \left(x _ {g} , 0 , s\right) + D (s) \sum_ {i = 0} ^ {n - 1} \int_ {0} ^ {l} B \left(x _ {g} , \xi , s\right) Q _ {i} (\xi , s , \varphi_ {i} (\xi)) d \xi}{A (s) D (s) + B \left(x _ {g} , 0 , s\right)} \tag {12.4-24}
$$

它是由初值引起的自由运动 $y(t, x_g)$ 的象函数。设它满足第 12.2 节中有关拉氏变换的一切性质，这时 $y(t, x_g)$ 可由反演公式求出

$$
y (t, x _ {g}) = \frac {1}{2 \pi i} \int_ {\gamma - i ^ {\infty}} ^ {\gamma + i ^ {\infty}} Y (s, x _ {g}) e ^ {s t} d s \tag {12.4-25}
$$

根据式 $(12.3-35)$ 知

$$
\mathcal {D} (s) = A (s) D (s) + B \left(x _ {\mathrm{g}}, 0, s\right) = 0 \tag {12.4-26}
$$

是系统的特征方程。

可以证明, 解(12.4-25)的稳定性取决于特征方程式(12.4-26)特征根的分布。

如果正则系统特征方程(12.4-26)的特征根都有负实部，且负实部都小于某一负数 $\gamma<0$ ,那么系统一定是渐近稳定的。

同样，利用位移定理还可以证明，如果正则系统的特征根至少有一个具有正实部，那么系统一定是不稳定的。

这种根据特征方程的根在复平面上的分布来判别运动的稳定性，和前面所讲 的根据算子本征值在复平面上的分布来判别运动的稳定性，这两者完全是一回事，特征根就是算子本征值。事实上，当用拉氏变换法解方程时，设方程的解 $y(t, x)$ 的象函数 $Y(s, x) = \frac{M(s, x)}{\mathcal{D}(s)}, \mathcal{D}(s) = 0$ 是系统的特征方程， $M(s, x)$ 是包括系统初值在内的关于 $s$ 的整函数。如果这个系统在希尔伯特空间 $\mathfrak{Q}$ 内化成如下微分方程：

$$
\frac {\partial y (t , x)}{\partial t} = A y (t, x), y (t, x) \mid_ {t = 0} = \varphi (x) \tag {12.4-27}
$$

其中 $A$ 是根据方程边界条件决定的微分算子。假定它是 $\mathfrak{H}$ 中有界算子半群 $T(t)$ 的生成算子，根据半群的性质，这时方程(12.4-27)的解为

$$
y (t, x) = T (t) \varphi (x) \tag {12.4-28}
$$

将式 $(12.4-28)$ 两边进行拉氏变换，便得到

$$
\begin{array}{l} \int_ {0} ^ {\infty} y (t, x) e ^ {- s t} d t = \int_ {0} ^ {\infty} e ^ {- s t} T (t) \varphi (x) d t = \int_ {0} ^ {\infty} e ^ {- s t} T (t) d t \varphi (x) \\ = (s - A) ^ {- 1} \varphi (x) \tag {12.4-29} \\ \end{array}
$$

这里利用了半群性质： $(s - A)^{-1} = \int_0^\infty e^{-st}T(t)dt^{[12,24]}$ 。由此得到

$$
Y (s, x) = (s - A) ^ {- 1} \varphi (x)
$$

或者

$$
\frac {M (s , x)}{\mathcal {D} (s)} = (s - A) ^ {- 1} \varphi (x) \tag {12.4-30}
$$

下一节我们会看到， $(s - A)^{-1}$ 是算子 $A$ 的预解式，它的极点就是 $A$ 的本征值（我们这里仅指具有紧预解式的算子）。而式(12.4-30)左边的极点就是 $\mathcal{D}(s)$ 的零点，也就是特征根。

和集中参数系统一样, 如令传递函数中 $s = i\omega$ , 得到的便是系统的频率特性。上述按特征方程根的分布判别系统稳定性的方法, 也可以使我们建立频率判据, 如乃奎斯特准则。同样, 也可以建立类似于路斯-霍尔维茨的准则。所有这些, 这里就不详细介绍了。

#### 12.5 带有常微分控制器的分布参数系统

在第 12.4 节中, 曾把带有常微分方程控制器的弹性梁控制系统式(12.3-8)化成积空间 $\xi_{2}=L_{2}(0,l)\times L_{2}(0,l)\times R_{n}$ 中的微分方程（也叫发展方程)

$$
\frac {d Y}{d t} = \mathcal {B} Y \tag {12.5-1}
$$

其中

$$
\mathcal {B} = \left( \begin{array}{c c c} 0 & 1 & 0 \\ - (A + B + G S _ {2}) & - C & - G \\ (S _ {1} + J S _ {2}) & 0 & J \end{array} \right)
$$

$\mathcal{B}$ 是 $\mathfrak{H}$ 中的线性算子。

用双曲型方程描述的弹性膜、板等一类受控对象的运动，最后也都能化成类似的方程。不同的只是空间变量不是一维而是多维的。因此，没有必要把问题限制在一个空间变量的情况，我们可以讨论更广泛一些的问题。为此，在 m 维欧氏空间 $R_{m}$ 中，取一有界开连通域 $\Omega$ ，其边界为 $\partial\Omega$ 。和第 12.4 节中所讨论的情况一样，作 $L_{2}(\Omega)$ 空间，即一切在 $\Omega$ 上平方可积复值函数的全体，在其中定义内积

$$
\langle \varphi , \psi \rangle = \int_ {\Omega} \varphi (p) \overline {{{{\psi (p)}}}} d p, \quad p \in \Omega \tag {12.5-2}
$$

和范数

$$
\| \varphi \| = \langle \varphi , \varphi \rangle^ {\frac {1}{2}} = \left\{\int_ {\Omega} | \varphi (p) | ^ {2} d p \right\} ^ {\frac {1}{2}}, \quad p \in \Omega \tag {12.5-3}
$$

则 $L_{2}(\Omega)$ 就是一个可分的希尔伯特空间。显然，当 $\Omega$ 是 $R_{1}$ （直线）上的 $(0, l)$ 时， $L_{2}(\Omega)$ 就是前面用到过的 $L_{2}(0, l)$ 。

作积空间 $\mathfrak{H} = L_2(\Omega) \times L_2(\Omega) \times R_n$ ，它仍是希尔伯特空间。 $\mathfrak{H}$ 中任一元 $Y = (u_1, u_2, y)$ 的范数定义为

$$
\| Y \| _ {\mathfrak {H}} = \left\{\| u _ {1} \| _ {L _ {2}} ^ {2} + \| u _ {2} \| _ {L _ {2}} ^ {2} + \| y \| _ {R _ {n}} ^ {2} \right\} ^ {\frac {1}{2}} \tag {12.5-4}
$$

研究控制系统

$$
\frac {d ^ {2} u}{d t ^ {2}} + C \frac {d u}{d t} + B u + A u = - G x,
$$

$$
\frac {d \boldsymbol {x}}{d t} = J \boldsymbol {x} + S _ {1} u + S _ {2} \frac {d u}{d t} \tag {12.5-5}
$$

其中

$$
G \boldsymbol {x} = (\boldsymbol {x}, \boldsymbol {g}) b
$$

$$
S _ {1} u = \left\langle S _ {1} u, a _ {1} \right\rangle k _ {1}
$$

$$
S _ {2} \frac {d u}{d t} = \langle S _ {2} \frac {d u}{d t}, a _ {2} \rangle k _ {2} \tag {12.5-6}
$$

$u=u(t,p)$ 是受控对象（梁、板、膜等）的状态。A,B,C 都是 $L_{2}(\Omega)$ 中的线性算子。 $a_{i}(p),i=1,2,b(p)$ 都是 $L_{2}(\Omega)$ 中固定的元。

控制系统式(12.5-5)同样可以化成$\mathfrak{S}$中的微分方程

$$
\frac {d Y}{d t} = \mathcal {B} Y \tag {12.5-7}
$$

其中 $Y \in \mathfrak{H}, \mathcal{B}$ 是 $\mathfrak{H}$ 中的线性算子。

在受控对象的方程中，算子 A 的一些属性是比较重要的。一方面，受控对象 的边界条件能单独决定 A 的定义域 $D(A)$ ; 另一方面, 算子 B, C, $S_{i}$ , i=1,2 的定义域一般都大于 $D(A)$ , 即 $D(B) \supset D(A)$ , $D(C) \supset D(A)$ , $D(S_{i}) \supset D(A)$ , i=1,2。今后把 A 叫做主算子。

算子 $A$ 通常是闭稠定的无界算子。不失一般性，还假定它是自伴、正定算子。它的逆（如果存在的话）是紧算子，所以也把这种算子叫做具有紧预解式的算子。比如，两端自由的弹性梁，其主算子 $A$ 就是描述弹性恢复力 $\frac{\partial^2}{\partial x^2} EJ(x)\frac{\partial^2u}{\partial x^2}$ 一项加上边界条件所确定的算子。 $A$ 的定义域 $D(A)$ 就是 $D(A) = \left\{u\mid u\in L_2(0,l), u,\dot{u}_x,EJ(x)\ddot{u}_{xx},\frac{\partial}{\partial x} EJ(x)\ddot{u}_{xx}\right.$ 都是绝对连续函数，且 $\frac{\partial^2}{\partial x^2} EJ(x)\ddot{u}_{xx}\in L_2(0,l), EJ(x)\ddot{u}_{xx}\big|_{x = 0\xrightarrow{x = l}} = 0,\frac{\partial}{\partial x} EJ(x)\ddot{u}_{xx}\bigg|_{x = 0\xrightarrow{x = l}} = 0\bigg\}$ 。容易验证 $A$ 是自伴算子，即 $\langle Au,v\rangle = \langle u,Av\rangle ,\forall u,v\in D(A)$ 。但不是正定的，因为当 $u = k$ （常数）和 $u = x$ 时， $Au = 0,\langle Au,u\rangle = 0$ 。这就是说， $u = k$ 和 $u = x$ 构成了 $A$ 的零子空间。以后我们会看到，它们恰好是弹性振动的零阶振型，对应的是刚体运动。

利用泛函分析中商空间的办法 $^{[4]}$ ，可以去掉 A 的零子空间，从而使其变为正定算子。泛函分析中还证明了，在这种情况下， $A^{\frac{1}{2}}$ 也是自伴正定、具有紧预解式的算子。

今后还假定 $D(B) \supset D(A^{\frac{1}{2}}), D(C) \supset D(A^{\frac{1}{2}}), D(S_i) \supset D(A^{\frac{1}{2}}), i = 1,2$ 。并且 $C, BA^{-\frac{1}{2}}, S_i A^{-\frac{1}{2}}, i = 1,2$ 都是定义在全空间 $L_2(\Omega)$ 上的有界算子。在实际问题中，这些条件通常是能满足的。下面的所有讨论都在这些假定下进行，以后不再重复。

现在把方程组(12.5-5)化成更对称的形式。为此，设 $u = u_{1} = A^{-\frac{1}{2}}\varphi ,u_{2} =$ $\dot{u}_1 = \psi ,\mathbf{y} = \mathbf{x} - S_2u_1$ ，则

$$
\frac {d \varphi}{d t} = A ^ {\frac {1}{2}} \psi
$$

$$
\frac {d \psi}{d t} = - A ^ {\frac {1}{2}} \varphi - B A ^ {- \frac {1}{2}} \varphi - C \psi - G S _ {2} A ^ {- \frac {1}{2}} \varphi - G y
$$

$$
\frac {d \mathbf {y}}{d t} = J \mathbf {y} + (S _ {1} + J S _ {2}) A ^ {- \frac {1}{2}} \varphi \tag {12.5-8}
$$

令 $W=(\varphi,\psi,y)$

$$
\mathcal {A} = \left( \begin{array}{c c c} 0 & A ^ {\frac {1}{2}} & 0 \\ - A ^ {\frac {1}{2}} - B A ^ {- \frac {1}{2}} - G S _ {2} A ^ {- \frac {1}{2}} & - C & - G \\ (S _ {1} + J S _ {2}) A ^ {- \frac {1}{2}} & 0 & J \end{array} \right)
$$

则式 $(12.5-8)$ 可以写成向量形式

$$
\frac {d W}{d t} = \mathcal {A} W \tag {12.5-9}
$$

再令

$$
\begin{array}{l} \mathcal {A} = \left( \begin{array}{c c c} 0 & A ^ {\frac {1}{2}} & 0 \\ - A ^ {\frac {1}{2}} & 0 & 0 \\ 0 & 0 & i E _ {1} \end{array} \right) \\ \mathcal {P} = \left( \begin{array}{c c c} 0 & 0 & 0 \\ - B A ^ {- \frac {1}{2}} & - C & 0 \\ 0 & 0 & J - i E _ {1} \end{array} \right) \\ \mathcal {F} = \left( \begin{array}{c c c} 0 & 0 & 0 \\ - G S _ {2} A ^ {- \frac {1}{2}} & 0 & - G \\ (S _ {1} + J S _ {2}) A ^ {- \frac {1}{2}} & 0 & 0 \end{array} \right) \\ \end{array}
$$

则 $A = A_{0} + P + T$ 。 $E_{1}$ 是 $n \times n$ 阶对角矩阵

$$
E _ {1} = \left( \begin{array}{c c c c} \alpha_ {1} & & & \\ & \alpha_ {2} & 0 \\ & & \ddots & \\ & 0 & & \\ & & & \alpha_ {n} \end{array} \right), \quad 0 <   \alpha_ {1} <   \alpha_ {2} <   \dots <   \alpha_ {n} <   \mu_ {1} ^ {2}
$$

$\mu_{1}^{2}$ 是 A 的最小本征值。

不失一般性可设 A 是自伴正定算子 $^{①}$ ，A 是反自伴算子，即 $A_{0} = -A_{0}$ ， $A_{0}$ 是 $A_{0}$ 的伴随算子。P 和 T 是 $\check{Q}$ 上的有界算子，因此有 $D(A) = D(A_{0})$ 。显然，算子 $A_{0} + P$ 是由受控对象和控制器的结构决定的，而 T 是把受控对象和控制器耦合起来的反馈算子。

现用分离变量法求解方程(12.5-7)，令 $U(t)=(w\ e^{\lambda t},w\ e^{\lambda t},y\ e^{\lambda t})$ 是它的某一非零解，代到方程中消去非零因子 $e^{\lambda t}$ ，便得到

$$
\begin{array}{l} \lambda u _ {1} = u _ {2} \\ \lambda u _ {2} = - A u _ {1} - B u _ {1} - C u _ {2} - G y - G S _ {2} u _ {1} \\ \lambda \mathbf {y} = J \mathbf {y} + (S _ {1} + J S _ {2}) u _ {1} \tag {12.5-10} \\ \end{array}
$$

即有

$$
\lambda Y = \mathcal {B} Y \tag {12.5-11}
$$

式中 $Y=(u_{1},u_{2},y)$ 。

同理，如设 $\Phi(t)=(\varphi_{1}e^{\lambda t},\varphi_{2}e^{\lambda t},ze^{\lambda t})$ 是方程(12.5-9)的非零解，代到方程中消去 $e^{\lambda t}$ ,便得到

$$
\lambda \varphi_ {1} = A ^ {\frac {1}{2}} \varphi_ {2}
$$

$$
\lambda \varphi_ {2} = - A ^ {\frac {1}{2}} \varphi_ {1} - B A ^ {- \frac {1}{2}} \varphi_ {1} - C \varphi_ {2} - G z - G S _ {2} A ^ {- \frac {1}{2}} \varphi_ {1}
$$

$$
\lambda z = J z + (S _ {1} + J S _ {2}) A ^ {- \frac {1}{2}} \varphi_ {1} \tag {12.5-12}
$$

即有

$$
\lambda W = \mathcal {A} W \tag {12.5-13}
$$

其中 $W=(\varphi_{1},\varphi_{2},z)$ 。

可以看出，用分离变量法求解方程时，如果 $U(t) = (u_1, u_2, y)e^{\lambda t}(\Phi(t) = (\varphi_1, \varphi_2, z)e^{\lambda t})$ 是方程(12.5-7)((12.5-9))的解，那么 $\lambda$ 和对应的 $(u_1, u_2, y)((\varphi_1, \varphi_2, z))$ 必是方程(12.5-11)((12.5-13))的解。反之，如果 $\lambda, (u_1, u_2, y)((\varphi_1, \varphi_2, z))$ 是方程(12.5-11)((12.5-13))的解，那么 $U(t) = (u_1, u_2, y)e^{\lambda t}((\varphi_1, \varphi_2, z)e^{\lambda t})$ 必是方程(12.5-7)((12.5-9))的解。 $\lambda$ 和 $(u_1, u_2, y)((\varphi_1, \varphi_2, z))$ 不是别的，就是算子 $\mathcal{B}(\mathcal{A})$ 的本征值和本征元。

设 $H$ 为希尔伯特空间， $T$ 是 $H$ 中的线性算子（有界或无界）。对于复数 $\lambda$ ，如果 $H$ 中有非零元 $u$ 存在，使 $\lambda u = Tu$ 成立，或 $(\lambda - T)u = 0$ ，那么 $\lambda$ 叫做算子 $T$ 的本征值，而 $u$ 叫做对应于 $\lambda$ 的 $T$ 的本征元。如果对于 $\lambda, (\lambda - T)$ 有有界逆算子 $(\lambda - T)^{-1}$ 存在，则 $\lambda$ 叫做 $T$ 的正则点。这时非齐次方程 $(\lambda - T)u = f$ 有唯一解 $u = (\lambda - T)^{-1}f$ 。 $(\lambda - T)^{-1}$ 也叫做 $T$ 的预解式，它使 $(\lambda - T)(\lambda - T)^{-1} = (\lambda - T)^{-1}(\lambda - T) = I$ 成立， $I$ 是 $H$ 中的恒等算子。

当 $\lambda$ 是 T 的本征值时，对应于 $\lambda$ 的本征元可能是一个，也可能是有限多个，甚至是无穷多个。这些本征元之间是线性无关的，它们张成 H 中一个子空间，叫做本征子空间。这个子空间的维数叫做 $\lambda$ 的几何重数。显然，本征元构成本征子空间一组基底。

设 $\lambda$ 是 T 的本征值， $w_{0}$ 是对应于 $\lambda$ 的 T 的本征元，此外，如果 H 中还有 n-1 个元 $w_{1}, w_{2}, \cdots, w_{n-1}$ 使得

$$
(T - \lambda) u _ {0} = 0
$$

$$
(T - \lambda) u _ {1} = u _ {0}
$$

$$
\dots
$$

$$
(T - \lambda) u _ {n - 1} = u _ {n - 2} \tag {12.5-14}
$$

成立，则 $u_{1}, u_{2}, \cdots, u_{n-1}$ 叫做对应于 $\lambda$ 的 T 的广义本征元（也叫根元）。它们也是线性无关的，由它们张成的子空间叫做广义本征子空间（也叫根子空间）。

假如 $\lambda$ 的几何重数为 m，而所有根子空间的维数为 n，那么 $m+n$ 就叫做 $\lambda$ 的

代数重数 $^{[24]}$ 。

在线性算子谱理论中，一个算子有三种谱，即点谱，连续谱，剩余谱。所谓点谱就是算子的本征值。一个算子可能三种类型的谱都有，也可能只有其中一种，甚至有的算子根本没有谱点。

我们前面说过的具有紧预解式的线性算子就只有一种谱，即点谱。在数学物理方程中遇到的大多数微分算子，如梁，板，膜等的主算子都是这种类型的。它只有纯点谱并以无穷远点为唯一聚点，每个点谱（本征值）对应的本征子空间都是有穷维的，而且在一定条件下，这些本征元构成空间的基 $^{[16,24]}$ ，即空间中任何元都可按这个基展成傅氏级数。

本征值和本征元有明确的物理意义。以梁的主算子 A 为例，零是它的本征值，对应有两个本征元 $u_{1}=k, u_{2}=x$ 。其他本征值就是梁的固有振动频率，对应的本征元就是固有振型。零本征值对应的是刚体运动， $u_{1}=k$ 对应质心的平移， $u_{2}=x$ 则对应于刚体的旋转。

现在回来讨论方程(12.5-11)和(12.5-13)，可以证明 $\mathcal{A}$ 和 $\mathcal{B}$ 的本征值问题是等价的，就是说 $\mathcal{A}$ 和 $\mathcal{B}$ 有相同的本征值，而且对应于同一本征值的代数重数也是相同的，在本征元和广义本征元之间有一一对应关系[9]。设 $\lambda_{l}$ 是 $\mathcal{A}$ 和 $\mathcal{B}$ 的本征值， $m_{l}$ 是 $\lambda_{l}$ 的代数重数， $\mathcal{A}$ 的广义本征元为 $\{\Phi_{lj}\}_{j=0}^{m_l - 1}$ ， $\mathcal{B}$ 的广义本征元为 $\{Y_{lj}\}_{j=0}^{m_l - 1}$ ，则它们之间有以下对应关系

$$
Y _ {l j} = \mathscr {H} \Phi_ {l j}, \quad j = 0, 1, \dots , m _ {l} - 1
$$

$$
\mathcal {H} = \left[ \begin{array}{c c c} A ^ {- \frac {1}{2}} & 0 & 0 \\ 0 & I & 0 \\ 0 & 0 & E \end{array} \right] \tag {12.5-15}
$$

I, E 分别是 $L_{2}(\Omega)$ 和 $R_{n}$ 中的恒等算子。

既然 $\mathcal{A}$ 和 $\mathcal{B}$ 的本征值问题是等价的，那么我们只要研究一个算子的本征值问题所得到的结论对另外一个也适用。下面我们以 $\mathcal{A}$ 为主来讨论本征值问题。

算子 $A = A_{0} + P + T = A_{3} + T$ ，其中 $A_{3} = A_{0} + P$ 。A 是由受控对象和控制器结构决定的。在没加反馈算子 T 前，它们是分开的。设 A 是具有紧预解式的算子，它只有点谱。复平面上的点，或者是它的本征值，或者是它的正则点，而它的本征值和本征元，一般说来，可以事先求出。

当系统闭合后，由于 $\mathcal{A}$ 的作用，有可能使 $\mathcal{A}$ 的正则点变成 $\mathcal{A}$ 的本征值，也有可能使 $\mathcal{A}$ 的本征值变成 $\mathcal{A}$ 的正则点。设计控制器的目的之一就是为了使 $\mathcal{A}$ 的本征值经过反馈算子 $\mathcal{A}$ 闭合后，使本征值朝着我们需要的方向变化。比如 $\mathcal{A}$ 的本征值具有正实部，系统不稳定，但适当设计控制器，使 $\mathcal{A}$ 经扰动后，新的本征值具有负实部，从而使系统稳定，这就是系统的镇定问题。

为了书写方便，把 A 改变一下形式。令

$$
\Gamma_ {0} = \left( \begin{array}{c c} 0 & A ^ {\frac {1}{2}} \\ - A ^ {\frac {1}{2}} - B A ^ {- \frac {1}{2}} & - C \end{array} \right)
$$

则

$$
\mathcal {A} = \left( \begin{array}{c c} \Gamma_ {0} & 0 \\ 0 & J \end{array} \right)
$$

再设 $\boldsymbol{a}_{1}=(0,a_{1}),\boldsymbol{a}_{2}=(0,a_{2}),\boldsymbol{b}=(0,b)$ ,

$$
\mathfrak {S} = \left( \begin{array}{c c} 0 & 0 \\ S _ {i} A ^ {- \frac {1}{2}} & 0 \end{array} \right), \quad i = 1, 2
$$

则 $\mathcal{F}$ 变成

$$
\mathcal {F} = \left[ \begin{array}{c c} - \langle \widetilde {\mathfrak {S}} \cdot , a _ {2} \rangle \langle k _ {2}, g \rangle b & - (\cdot , g) b \\ \langle \widetilde {\mathfrak {S}} \cdot , a _ {1} \rangle k _ {1} + \langle \widetilde {\mathfrak {S}} \cdot , a _ {2} \rangle J k _ {2} & 0 \end{array} \right]
$$

$\Gamma_{0},\widetilde{\mathfrak{S}},i=1,2$ 是 $L_{2}(\Omega)\times L_{2}(\Omega)$ 中的线性算子，而 $a_{i},i=1,2,b$ 是 $L_{2}(\Omega)\times L_{2}(\Omega)$ 中固定的元。算子 $\Gamma_{0}$ 完全由受控对象决定， $\widetilde{\mathfrak{S}},i=1,2$ 是由测量算子决定的，而 J 是由控制器决定的。

这样，把三维矩阵算子变成了二维矩阵算子。显然,A 的预解式是

$$
\mathcal {R} (\lambda , \mathcal {A}) = (\lambda - \mathcal {A}) ^ {- 1} = \left( \begin{array}{c c} R (\lambda , \Gamma_ {0}) & 0 \\ 0 & R _ {J} (\lambda) \end{array} \right)
$$

其中 $R(\lambda, \Gamma_{0}) = (\lambda - \Gamma_{0})^{-1}$ , $R_{J}(\lambda) = (\lambda - J)^{-1}$ 。

定义以下复值函数，它对下面讨论谱扰动是很重要的。

$$
W _ {1} (\lambda) = \left(R _ {J} (\lambda) \boldsymbol {k} _ {1}, \boldsymbol {g}\right), W _ {2} (\lambda) = \left(R _ {J} (\lambda) \boldsymbol {k} _ {2}, \boldsymbol {g}\right)
$$

$$
H _ {1} (\lambda) = \left\langle \widetilde {\mathfrak {S}} R \left(\lambda_ {1}, \Gamma_ {0}\right) \boldsymbol {b}, \boldsymbol {a} _ {1} \right\rangle , H _ {2} (\lambda) = \left\langle \widetilde {\mathfrak {S}} R \left(\lambda , \Gamma_ {0}\right) \boldsymbol {b}, \boldsymbol {a} _ {2} \right\rangle
$$

$$
K (\lambda) = 1 + W _ {1} (\lambda) H _ {1} (\lambda) + \lambda W _ {2} (\lambda) H _ {2} (\lambda) \tag {12.5-16}
$$

先看一下 A 的正则点经 T 扰动后的变化情况。

设 $\lambda$ 是 A 的正则点, 如果 $K(\lambda) \neq 0$ , 则 $\lambda$ 仍是 $A = A + T$ 的正则点; 但若 $K(\lambda) = 0$ , 那么 $\lambda$ 必是 A 的本征值, 相应的本征元为

$$
\Phi = \left\{R (\lambda , \Gamma_ {0}) \boldsymbol {b}, R _ {J} (\lambda) (H _ {1} \boldsymbol {k} _ {1} + H _ {2} J \boldsymbol {k} _ {2}) \right\} \tag {12.5-17}
$$

此时， $\lambda$ 的几何重数为 1，而代数重数是 $K(\lambda)=0$ 的零点重数。设 $\lambda$ 是 $K(\lambda)$ 的 m 重零点， $\left.\frac{d^{l}K(\xi)}{d\xi^{l}}\right|_{\xi=\lambda}=0, l=0,1,2,\cdots,m-1$ ，则对应的广义本征元为

$$
\Phi_ {j} = \left\{(- 1) ^ {j} R ^ {j + 1} (\lambda , \Gamma_ {0}) \boldsymbol {b}, \sum_ {i = 0} ^ {j} \frac {(- 1) ^ {i + j}}{i !} R _ {J} ^ {j + 1 - i} (\lambda) (H _ {1} ^ {(i)} (\lambda) \boldsymbol {k} _ {1} + H _ {2} ^ {(i)} (\lambda) J \boldsymbol {k} _ {2}) \right\} \tag {12.5-18}
$$

式中 $H_{s}^{(i)}(\lambda) = \frac{d^{i}H_{s}(\xi)}{d\xi^{i}}\Bigg|_{\xi = \lambda},s = 1,2$ 。

再看一下 $\mathcal{A}$ 的本征值经 $\mathcal{T}$ 扰动后的变化情况。设 $\lambda$ 是 $\Gamma_0$ 的本征值 $J$ 的正则点。对应 $\lambda$ 的 $\Gamma_0$ 本征元为 $\varphi_l$ 。 $\overline{\lambda}$ 是 $\Gamma_0^*$ 的本征值，对应的本征元为 $\psi_l, \Gamma_0^*$ 是 $\Gamma_0$ 的伴随算子。再设 $\lambda$ 的几何重数、代数重数都是 1。这时 $\lambda$ 是 $\mathcal{A}$ 的本征值，而对应的本征元为 $(\varphi_l, 0)$ ，其几何、代数重数也都是 1。由于 $\lambda$ 是 $J$ 的正则点，所以式(12.5-16)中定义的函数 $W_1(\lambda), W_2(\lambda)$ 都有意义。再定义函数

$$
W (\lambda) = W _ {1} (\lambda) \langle \widetilde {\mathfrak {S}} \varphi_ {l}, \boldsymbol {a} _ {1} \rangle + \lambda W _ {2} (\lambda) \langle \widetilde {\mathfrak {S}} \varphi_ {l}, \boldsymbol {a} _ {2} \rangle \tag {12.5-19}
$$

这时，经反馈算子 $\mathcal{F}$ 闭合后，可能有以下几种情况。

(1) 如果 $\langle b, \psi_{l} \rangle \neq 0, W(\lambda) \neq 0$ ，则 $\lambda$ 是 $A = A + T$ 的正则点。

(2) 如果 $\langle b, \psi_{i} \rangle \neq 0, W(\lambda) = 0$ ，则 $\lambda$ 是 A 的本征值，且几何重数不变。

（3）如果 $\langle b,\psi_{l}\rangle=0$ ，则 $\lambda$ 是 A 的本征值，并且当 $W(\lambda)\neq0$ 时， $\lambda$ 的几何重数不变，而 $W(\lambda)=0$ 时， $\lambda$ 的几何重数可能为 2，且至多为 2。

这个事实对控制器同样也是适用的。设 $\alpha$ 是 $J$ 的本征值， $\Gamma_0$ 的正则点。对应于 $\alpha$ 的 $J$ 的本征元为 $z_l, \overline{\alpha}$ 是 $J^*$ 的本征值，对应的本征元为 $y_l, J^*$ 是 $J$ 的伴随矩阵。 $\alpha$ 的几何、代数重数都为 1。显然， $\alpha$ 是 $\mathcal{A}$ 的本征值，对应的本征元为 $(0, z_l)$ 。同样定义函数

$$
H (\alpha) = H _ {1} (\alpha) \left(\boldsymbol {k} _ {1}, \boldsymbol {y} _ {l}\right) + \alpha H _ {2} (\alpha) \left(\boldsymbol {k} _ {2}, \boldsymbol {y} _ {l}\right) \tag {12.5-20}
$$

这时， $\mathcal{A}$ 的本征值 $\alpha$ 经 $\mathcal{T}$ 反馈闭合后，可能有以下几种情况：

(1) 如果 $(\mathbf{z},\mathbf{g})\neq0,H(\alpha)\neq0$ ，那么 $\alpha$ 是 $A=B+T$ 的正则点。

(2) 如果 $(\mathbf{z}_{l},\mathbf{g})\neq0$ , $H(\alpha)=0$ , 则 $\alpha$ 是 A 的本征值, 且几何重数不变。

（3）如果 $(z_{1},g)=0,\alpha_{1}$ 一定是 A 的本征值，若 $H(\alpha_{1})\neq0$ 时， $\alpha_{1}$ 的几何重数不变，而 $H(\alpha_{1})=0$ 时， $\alpha_{1}$ 的几何重数可能变为 2，且至多为 2。

以上是受控对象 $\mathcal{A}$ 的某个本征值在反馈闭合后的变化情况。根据上面所述不难得到 $\mathcal{A}$ 全部本征值经 $\mathcal{T}$ 反馈后的变化情况。

设 $\Gamma_0$ 的全部本征值为 $\{\lambda_l\}_{l = -\infty}^{\infty}$ ，对应的本征元为 $\{\varphi_l\}_{l = -\infty}^{\infty}, \{\bar{\lambda}_l\}_{l = -\infty}^{\infty}$ 是 $\Gamma_0^*$ 的本征值列，对应的本征元列为 $\{\boldsymbol{\psi}_l\}_{l = -\infty}^{\infty}$ 。 $\{\lambda_l\}_{l = -\infty}^{\infty}$ 是 $J$ 的正则点。这时 $\{\lambda_l\}_{l = -\infty}^{\infty}$ 是 $\mathcal{A}$ 的本征值，而对应的本征元为 $\{(\varphi_l, 0)\}_{l = -\infty}^{\infty}$ 。

其次设 J 的本征值为 $\{\alpha_{l}\}_{l=1}^{n}$ ，对应的本征元为 $\{z_{l}\}_{l=1}^{n}$ ， $\{\overline{\alpha}_{l}\}_{l=1}^{n}$ 是 $J^{*}$ 的本征值，对应的本征元为 $\{y_{l}\}_{l=1}^{n}$ ， $\{\alpha_{l}\}_{l=1}^{n}$ 是 $\Gamma_{0}$ 的正则点。此时 $\{\alpha_{l}\}_{l=1}^{n}$ 是 A 的本征值，对应的本征元为 $\{(0,z_{l})\}_{l=1}^{n}$ 。所以 A 的本征值为 $\{\lambda_{l}\}_{l=-\infty}^{\infty}$ 和 $\{\alpha_{l}\}_{l=1}^{n}$ 。由以上的事实可以看到，当下述条件同时成立时

$$
\langle \boldsymbol {b}, \boldsymbol {\psi} _ {l} \rangle \neq 0, \quad l = \pm 1, \pm 2, \dots
$$

$$
W (\lambda) \neq 0, \quad l = \pm 1, \pm 2, \dots
$$

$$
\left(\mathbf {z} _ {l}, \mathbf {g}\right) \neq 0, \quad l = 1, 2, \dots , n
$$

$$
H (\alpha) \neq 0, \quad l = 1, 2, \dots , n \tag {12.5-21}
$$

算子 $\mathcal{A}$ 和 $\mathcal{A}$ 没有共同的本征值。反之，只要有一个条件对某个 $l$ 不成立，那时 $\mathcal{A}$ 和 $\mathcal{A}$ 必有共同的本征值，这个本征值就是 $l$ 所对应的那个 $\lambda_l$ 或 $\alpha_l$ 。因此，当式(12.5-21)成立时， $\mathcal{A}$ 的本征值只能由 $\mathcal{A}$ 的正则点经 $\mathcal{T}$ 反馈而来，它就是前面说过的 $K(\lambda)$ 的零点。由此可以推出，当式(12.5-21)成立时，复数 $\lambda$ 是 $\mathcal{A}$ 的 $m$ 重本征值的必要充分条件是

$$
K (\lambda) = 0
$$

$$
\left. \frac {d ^ {l} K (\xi)}{d \xi^ {l}} \right| _ {\xi = \lambda} = 0, \quad l = 1, 2, \dots , m - 1 \tag {12.5-22}
$$

下面，我们来讨论方程(12.5-7)和(12.5-9)的定解和稳定性问题。为此，我们先说明一下 A 的本征子空间的几何结构，它对研究系统运动的特点是非常有用的。

设 $\lambda_{l}$ 是 $\mathcal{A}$ 的本征值，几何重数为 1，代数重数为 $m_{l}$ ，对应的本征元和广义本征元为 $\{\Phi_{lj}\}_{j=0}^{m_l - 1}$ ，本征子空间记为 $M_{l}$ 。 $\overline{\lambda}_{l}$ 是 $\mathcal{A}^{*}$ 的本征值，具有和 $\lambda_{l}$ 一样的几何、代数重数，对应于 $\overline{\lambda}_{\infty}\mathcal{A}^{*}$ 的本征元和广义本征元为 $\{\Psi_{lj}\}_{j=0}^{m_l - 1}$ ，本征子空间记作 $M_{l}^{*}$ 。按定义有

$$
\mathscr {A} \Phi_ {l j} = \lambda \Phi_ {l, j - 1}, \mathscr {A} ^ {*} \Psi_ {l j} = \bar {\lambda} \Psi_ {l, j + 1}, \quad j = 0, 1, \dots , m _ {l} - 1 \tag {12.5-23}
$$

不难证明 $\{\Phi_{lj}\}_{j=0}^{m_l - 1}$ 和 $\{\Psi_{lj}\}_{j=0}^{m_l - 1}$ 是双直交的，即

$$
\langle \Phi_ {l j}, \Psi_ {l, i} \rangle = \left\{ \begin{array}{l l} 0, & j \neq i \\ \neq 0, & j = i \end{array} \right.
$$

如果 $\Phi_{lj} = (\varphi_{lj}^{1},\varphi_{lj}^{2},\mathbf{y}_{lj}),\Psi_{lj} = (\psi_{lj}^{1},\psi_{lj}^{2},\mathbf{z}_{lj})$ ，按下述方法规范化

$$
\left\| \Phi_ {l j} \right\| = \{\left\| \varphi_ {l j} ^ {1} \right\| ^ {2} + \left\| \varphi_ {l j} ^ {2} \right\| ^ {2} + \left\| \mathbf {y} _ {l j} \right\| ^ {2} \} ^ {\frac {1}{2}} = 1
$$

$$
\langle \Phi_ {l j}, \Psi_ {l j} \rangle = \left\langle \varphi_ {l j} ^ {1}, \psi_ {l j} ^ {1} \right\rangle + \left\langle \varphi_ {l j} ^ {2}, \psi_ {l j} ^ {2} \right\rangle + \left(\mathbf {y} _ {l j}, \mathbf {z} _ {l j}\right) = 1
$$

则 $\{\Phi_{lj}\}_{j=0}^{m_l-1},\{\Psi_{lj}\}_{j=0}^{m_l-1}$ 是归范双直交基。

这时，在本征子空间 $M_{l}$ 上的投影算子 $Q_{l}$ ，即 $Q_{l}\mathfrak{H}=M_{l}$ 为

$$
Q _ {l} = \sum_ {j = 0} ^ {m _ {l} - 1} \langle \bullet , \Psi_ {l j} \rangle \Phi_ {l j} \tag {12.5-24}
$$

在 $M_{l}^{*}$ 上的投影算子 $Q_{l}^{*}$ ，即 $Q_{l}^{*}\mathfrak{H}=M_{l}^{*}$ 可以表述成

$$
Q _ {l} ^ {*} = \sum_ {j = 0} ^ {m _ {l} - 1} \langle \cdot , \Phi_ {l j} \rangle \Psi_ {l j} \tag {12.5-25}
$$

由于 $M_{l} \subset D(\mathcal{A})$ ，当把 $\mathcal{A}$ 限制在 $M_{l}$ 上时，即对任意的 $u \in M_{l}, \mathcal{A}u = \mathcal{A}u$ ，则 $\mathcal{A}$ 叫做 $\mathcal{A}$ 在 $M_{l}$ 上的缩，它可以表示为

$$
\mathcal {A} = \mathcal {A} Q _ {l} = \lambda_ {l} Q _ {l} + D _ {l} \tag {12.5-26}
$$

其中 $D_{l}$ 是幂零算子

$$
D _ {l} = \sum_ {j = 0} ^ {m _ {l} - 2} \langle \cdot , \Psi_ {l, j + 1} \rangle \Phi_ {l j}
$$

同样 $\mathcal{A}^{*}$ 在 $M_{l}^{*}$ 上的缩 $\mathcal{A}^{*}$ 为

$$
\mathcal {A} ^ {*} = \mathcal {A} ^ {*} Q _ {l} ^ {*} = \overline {{{{\lambda}}}} Q _ {l} ^ {*} + D _ {l} ^ {*} \tag {12.5-27}
$$

其中 $D_{l}^{*}$ 为

$$
D _ {l} ^ {*} = \sum_ {j = 0} ^ {m _ {l} - 2} \langle \cdot , \Phi_ {l, j + 1} \rangle \Psi_ {l j}
$$

特别当 $\lambda_{i}$ 是单重本征值时，则有

$$
Q _ {l} = \langle \cdot , \Psi_ {l} \rangle \Phi_ {l}, \quad D _ {l} = 0
$$

$$
Q _ {l} ^ {*} = \langle \cdot , \Phi_ {l} \rangle \Psi_ {l}, \quad D _ {l} ^ {*} = 0 \tag {12.5-28}
$$

而

$$
\mathscr {A} = \lambda_ {l} \langle \cdot , \Psi_ {l} \rangle \Phi_ {l}
$$

$$
\mathcal {A} ^ {*} = \bar {\lambda} \langle \bullet , \Phi_ {l} \rangle \Psi_ {l} \tag {12.5-29}
$$

容易算出, $\mathcal{A}$ 的预解式 $\mathcal{R}(\lambda,\mathcal{A})$ 在 $M_{l}$ 上的缩为

$$
\mathcal {R} (\lambda , \mathcal {A}) Q _ {l} = \frac {Q _ {l}}{\lambda - \lambda_ {l}} + \frac {D _ {l}}{(\lambda - \lambda_ {l}) ^ {2}} + \dots + \frac {D _ {l} ^ {m _ {l} - 1}}{(\lambda - \lambda_ {l}) ^ {m _ {l}}} \tag {12.5-30}
$$

前面我们曾经说过，一个算子的本征元在一定条件下构成空间的基。现在我们讨论一下，算子 $\mathcal{A}$ 的本征元在什么条件下构成 $\mathfrak{H}$ 中的基。首先来说明 $\mathcal{A}$ 的投影算子列 $\{Q_l\}_{l = -\infty}^{\infty}$ 构成 $\mathfrak{H}$ 中基的概念。如果投影算子列 $\{Q_l\}_{l = -\infty}^{\infty}$ 使得 $\mathfrak{H}$ 中任意元 $F$ 都有

$$
\sum_ {l = - \infty} ^ {\infty} Q _ {l} F = F \tag {12.5-31}
$$

这里，级数是按 $\mathfrak{H}$ 中范数收敛（也叫强收敛)。也就是说

$$
\sum_ {l = - \infty} ^ {\infty} Q _ {l} = I (\text {强})
$$

式中 I 是 $\mathfrak{H}$ 中的恒等算子，我们就称 $\{Q_{l}\}_{l=-\infty}^{\infty}$ 构成 $\mathfrak{H}$ 中基。由式 (12.5-24) 和 (12.5-31)，对 $\mathfrak{H}$ 中任意元 F 都可依 A 的本征元和广义本征元展成傅氏级数

$$
\boldsymbol {F} = \sum_ {l = - \infty} ^ {\infty} \left[ \sum_ {j = 0} ^ {m _ {l} - 1} \langle \boldsymbol {F}, \Psi_ {l j} \rangle \Phi_ {l j} \right] \tag {12.5-32}
$$

特别是当 $m_{l}=1$ 时（对所有的 l)，式(12.5-32)就变成

$$
F = \sum_ {l = - \infty} ^ {\infty} \langle F, \Psi_ {l} \rangle \Phi_ {l}
$$

这里 $\Phi_{l}$ 相当于欧氏空间的坐标轴，而 $\langle F, \Psi_{l} \rangle$ 就是 F 向这个轴上的投影。这种展开是唯一的。

由上所述，如果 $\mathcal{A}$ 的投影算子列构成 $\mathfrak{H}$ 中基，那么 $\mathcal{A}$ 的本征元和广义本征元也构成 $\mathfrak{H}$ 中的基。在什么条件下, $\mathcal{A}$ 的投影算子列构成 $\mathfrak{H}$ 中的基呢?在文献[24]中曾证明过一个重要的命题，我们下面叙述的事实是这个命题的具体应用。

如果式(12.5-5)的算子 $A$ 是自伴、正定、有紧预解式的线性算子， $\{\mu_i^2\}_{i=1}^\infty$ 是它的本征值并按大小顺序排成的自然列，每个本征值都是单重的，且满足条件 $\lim_{n \to \infty} (\mu_n - \mu_{n-1}) = \infty$ ，这时 $\mathcal{A} = \mathcal{A}_0 + \mathcal{P} + \mathcal{T}\mathcal{P}$ 和 $\mathcal{T}$ 是 $\mathfrak{S}$ 上的有界算子）也是具有紧预解式的闭算子。 $\mathcal{A}(\mathcal{A}^*)$ 的本征值 $\{\lambda_l\}_{l=-\infty}^\infty (\{\overline{\lambda}_l\}_{l=-\infty}^\infty)$ 对应的 $\mathcal{A}(\mathcal{A}^*)$ 的本征子空间为 $\{M_l\}_{l=-\infty}^\infty (\{M_l^*\}_{l=-\infty}^\infty)$ ，这时在本征子空间 $\{M_l\}_{l=-\infty}^\infty (\{M_l^*\}_{l=-\infty}^\infty)$ 上的投影算子 $\{Q_l\}_{l=-\infty}^\infty (\{Q_l^*\}_{l=-\infty}^\infty)$ 在 $\mathfrak{S}$ 中构成基，而且除有穷个外，所有的 $Q_l(Q_l^*)$ 都是一维的。对 $\mathfrak{S}$ 中任意元 $F$ 都可展成级数

$$
F = \sum_ {l = - \infty} ^ {\infty} Q _ {l} F = \sum_ {| l | \leqslant N _ {0}} \left[ \sum_ {j = 0} ^ {m _ {l} - 1} \langle F, \Psi_ {l j} \rangle \Phi_ {l j} \right] + \sum_ {| l | > N _ {0}} \langle F, \Psi_ {l} \rangle \Phi_ {l}
$$

$$
F = \sum_ {l = - \infty} ^ {\infty} Q _ {l} ^ {*} F = \sum_ {| l | \leqslant N} \left[ \sum_ {j = 0} ^ {m _ {l} - 1} \langle F, \Phi_ {l j} \rangle \Psi_ {l j} \right] + \sum_ {| l | > N _ {0}} \langle F, \Phi_ {l} \rangle \Psi_ {l} \tag {12.5-33}
$$

其中 $N_{0}$ 是 $Q_{l}$ 的维数不为 1 的投影算子的个数。 $\left\{\Phi_{lj}\right\}_{j=0}^{m_{l}-1},\left\{\Psi_{lj}\right\}_{j=0}^{m_{l}-1},l=\pm1,\pm2,\cdots$ 分别为 A 和 $\tilde{A}$ 对应于 $\lambda_{l}$ 及 $\bar{\lambda}_{l}$ 的广义本征元。

如果在式(12.5-33)中， $F \in D(\mathcal{A}), \mathcal{A}F \in \mathfrak{H}$ ，则有

$$
\begin{array}{l} \mathcal {A} F = \sum_ {1 l \leqslant N _ {0}} \left[ \sum_ {j = 0} ^ {m _ {l} - 1} \langle \mathcal {A} F, \Psi_ {l j} \rangle \Phi_ {l j} \right] + \sum_ {1 l > N _ {0}} \langle \mathcal {A} F, \Psi_ {l} \rangle \Phi_ {l} \\ = \sum_ {\left\lfloor l \right\rfloor \leqslant N _ {0}} \left(\sum_ {j = 0} ^ {m _ {l} - 1} \langle F, \mathscr {A} \Psi_ {l j} \rangle \Phi_ {l j}\right) + \sum_ {\left\lfloor l \right\rfloor > N _ {0}} \langle F, \mathscr {A} \Psi_ {l} \rangle \Phi_ {l} \\ = \sum_ {1 l l \leqslant N _ {0}} \left(\lambda_ {l} \sum_ {j = 0} ^ {m _ {l} - 1} \langle F, \Psi_ {l j} \rangle \Phi_ {l j} + \sum_ {j = 0} ^ {m _ {l} - 2} \langle F, \Psi_ {l, j + 1} \rangle \Phi_ {l j}\right) + \sum_ {1 l l > N _ {0}} \lambda_ {l} \langle F, \Psi_ {l} \rangle \Phi_ {l} \\ \end{array}
$$

这里利用了关系式 $\mathcal{A}\quad\Psi_{l}=\bar{\lambda}\Psi_{l}$ ，以及 $\mathcal{A}\quad\Psi_{lj}=\bar{\lambda}\Psi_{lj}+\Psi_{l,j+1}$ 。因此，A 在其定义域 $D(\mathcal{A})$ 上，可表示为

$$
\mathcal {A} = \sum_ {| l | \leqslant N _ {0}} \left[ \lambda \sum_ {j = 0} ^ {m _ {l} - 1} \langle \cdot , \Psi_ {l j} \rangle \Phi_ {l j} + \sum_ {j = 0} ^ {m _ {l} - 2} \langle \cdot , \Psi_ {l, j + 1} \rangle \Phi_ {l j} \right] + \sum_ {| l | > N _ {0}} \lambda_ {l} \langle \cdot , \Psi_ {l} \rangle \Phi_ {l} \tag {12.5-34}
$$

根据式(12.5-30)， $\mathcal{A}$ 的预解式可以表达如下

$$
\mathscr {R} (\lambda , \mathscr {A}) = \sum_ {| l | \leqslant N _ {0}} \left[ \frac {Q _ {l}}{\lambda - \lambda} + \frac {D _ {l}}{(\lambda - \lambda) ^ {2}} + \dots + \frac {D _ {l} ^ {m _ {l} - 1}}{(\lambda - \lambda) ^ {m _ {l}}} \right] + \sum_ {| l | > N _ {0}} \frac {Q _ {l}}{\lambda - \lambda} \tag {12.5-35}
$$

有了以上这些准备之后，现在我们来讨论方程(12.5-9)的定解和稳定性问题。先从本征运动研究起。假定系统式(12.5-9)的初值 $W_{0}=(\varphi_{0},\psi_{0},y_{0})\in M_{l}$ ，这时，可以证明 $^{[9]}$

$$
W (t) = U _ {l} (t) W _ {0} = e ^ {\lambda_ {l} t} \left\{Q _ {l} + t D _ {l} + \frac {(t D _ {l}) ^ {2}}{2 !} + \dots + \frac {(t D _ {l}) ^ {m _ {l} - 1}}{(m - 1) !} \right\} W _ {0} \tag {12.5-36}
$$

是方程(12.5-9)的唯一解。

从解 $W(t)$ 的结构可以看出， $W(t) \in M_l$ ，这就是说，当 $W_0 \in M_l$ 时，由 $W_0$ 出发的系统运动将永远保持在本征子空间 $M_l$ 中，我们把它叫做本征运动。其次， $U_l(0) = Q_l$ 。可以验证 $U_l(t)$ 构成有界单参数群，即 $U_l(t + s) = U_l(t) \cdot U_s(t)$ ， $-\infty < t, s < +\infty$ ，

由本征运动 $U_{1}(t)W_{0}$ 的表达式可以看出, 如果本征值 $\lambda$ 具有负实部时, 本征运动是渐近稳定的。因为对 t>0, 有

$$
\begin{array}{l} \left\| U _ {l} (t) W _ {0} \right\| \leqslant e ^ {\lambda_ {l} t} \left\| Q _ {l} + t D _ {l} + \dots + \frac {(t D _ {l}) ^ {m _ {l} - 1}}{(m _ {l} - 1) !} \right\| \| W _ {0} \| \\ \leqslant e ^ {\lambda_ {l} t} \left[ \| Q _ {l} \| + \sum_ {n = 1} ^ {m _ {l} - 1} \frac {(t \| D _ {l} \|) ^ {n}}{n !} \right] \| W _ {0} \| \\ \end{array}
$$

$\lambda$ 具有负实部时, 不等式右边当 $t \rightarrow \infty$ 时趋于零, 所以

$$
\lim _ {t \rightarrow \infty} \| U _ {l} (t) W _ {0} \| = 0
$$

如果 $\lambda_{l}$ 是纯虚数且 $m_{l}=1$ ，这时本征运动为

$$
U _ {l} (t) W _ {0} = e ^ {\lambda_ {l} t} Q _ {l} W _ {0}, \quad W _ {0} \in M _ {l}
$$

不难看出，本征运动 $U_{l}(t)W_{0}$ 是稳定的（但不渐近稳定)。这是由于

$$
\left\| U _ {l} (t) W _ {0} \right\| = \left\| e ^ {\lambda_ {l} t} Q _ {l} W _ {0} \right\| \leqslant \left\| Q _ {l} W _ {0} \right\|
$$

但如果 $m_{l}>1$ ，本征运动就是不稳定的。

如果 $\lambda$ 具有正实部，从式(12.3-36)中可以看出，本征运动一定是不稳定的。

综上所述，本征运动稳定与否完全取决于本征值是否具有负实部，当实部为零时，则取决于 $\lambda_{i}$ 的代数重数大小。

现在讨论方程(12.5-9)对任意初始条件 $W_0 \in D(\mathcal{A})$ 的解。首先，我们指出，对 $\mathcal{A}$ 中的主算子 $A$ ，除了满足式(12.5-33)展开所要求的条件外，还满足条件 $\sum_{-\infty}^{\infty} (\mu_n - \mu_{n-1})^{-1} < \infty$ 时， $\mathcal{A}$ 一定是强连续单参数有界算子群 $U(t)$ 的生成算子，而 $U(t)$ 就是 $\mathcal{A}$ 的一切本征运动群之和，即

$$
U (t) = \sum_ {l = - \infty} ^ {\infty} U _ {l} (t) = \sum_ {| l | \leqslant N _ {0}} e ^ {\lambda_ {l} t} \left[ Q _ {l} + t D _ {l} + \dots + \frac {(t D _ {l}) ^ {m _ {l} - 1}}{(m _ {l} - 1) !} \right] + \sum_ {| l | > N _ {0}} e ^ {\lambda_ {l} t} Q _ {l} \tag {12.5-37}
$$

这里，级数是按 $\xi$ 中算子范数收敛的。 $U(t)$ 有以下性质:

(1) $U(0) = \sum_{l = -\infty}^{\infty}U_l(0) = \sum_{l = -\infty}^{\infty}Q_l = 1$ (强)

(2) $U(t)$ 是算子群, 即 $U(t+s)=U(t)U(s)$ 。

(3) 对任意 $W_{0} \in D(\mathcal{A})$

$$
U (t) W _ {0} = \sum_ {| l | \leqslant N _ {0}} e ^ {\lambda_ {l} t} \left[ Q _ {l} + t D _ {l} + \dots + \frac {(t D _ {l}) ^ {m _ {l} - 1}}{(m _ {l} - 1) !} \right] W _ {0} + \sum_ {| l | > N _ {0}} e ^ {\lambda_ {l} t} Q _ {l} W _ {0} \tag {12.5-38}
$$

是方程(12.5-9)的唯一解，即

$$
\frac {d U (t) W _ {0}}{d t} = \mathcal {A} U (t) W _ {0}, \quad U (0) W _ {0} = W _ {0}
$$

由式(12.5-38)可以看到，只要知道了 $\mathcal{A}$ 的本征值列 $\{\lambda_l\}_{l = -\infty}^{\infty}$ ，本征元和广义本征元列 $\{\Phi_{ij}\}, \{\Psi_{ij}\}$ ，那么方程(12.5-9)的解就可解析表达成式(12.5-38)的形式。这为我们研究系统的稳定性带来了很大方便。

最后，我们讨论系统式(12.5-9)的全局稳定性:

（1）如果 $\mathcal{A}$ 的一切本征值都有负实部，而且对所有本征值 $\lambda$ ，都有 $\mathrm{Re}\lambda \leqslant \alpha < 0$ ，那么系统是渐近稳定的（充分条件)。这个结论和第 12.4 节已讨论过的结论完全一致。

（2）如果 $\mathcal{A}$ 的本征值都位于左半平面（包括虚轴)，而所有纯虚数本征值都是单重的，那么系统式(12.5-9)是稳定的。但不一定渐近稳定。假如至少有一个纯虚数本征值，它的代数重数大于 1，那么系统一定是不稳定的。

（3）如果至少有一个本征值具有正实部，则系统一定是不稳定的。

这些结论的详细证明，可看文献[9]。

由上所述可以看出，系统的稳定性完全取决于算子 A 的本征值在复平面上的分布。

值得指出的是，在实际问题中，系统全局稳定性并没有像在理论分析中所赋予的那种重要意义。一个实际系统高于某一频率（本征值）的振型，事先就能预料不会出现。这种与线性模型不一致的地方，不是实际观测数据的不对，而是模型的缺点。比如，弹性梁的振动控制中，材料的内阻尼在方程(12.3-2)中就没有考虑，但实际上是存在的，尽管它很小，但对高阶振型却有较大影响。在工程实际中，重要的往往不是考察反馈系统的全局稳定性，而是某几个低频本征运动的稳定性。这时，我们前面所述的结论可直接应用于工程计算。计算步骤大致如下：

（1）首先计算未加反馈时，受控对象和控制器的本征值，即 A 的本征值和本征元，特别是对系统功能影响最大的前几个固有频率和振型。

（2）加反馈算子 $\mathcal{F}$ 使系统闭合后，研究这些本征值是否发生变化，判别的方法可按前面讲过的谱扰动方法。如果本征值没有变化，那就必须改变反馈方法和参数。比如，为了使闭合后系统是稳定的，这时反馈算子的选择必须使闭合后系统本征值具有负实部。要想做到这一点，可以改变放大系数 $k_{1}, k_{2}, g$ ，控制器矩阵

J 的参数，也可以改变观测器的位置（相当于改变 $a_{1}, a_{2}$ )和控制作用位置 b。

（3）如果反馈作用的结果，使 $\mathcal{A}$ 的正则点变成了 $\mathcal{A}$ 的本征值，这时可按式(12.5-22)求出这个本征值和本征元。

在文献[8]中讨论弹性振动的镇定问题时，曾经找到了闭合后系统本征值具有负实部和反馈算子的直接关系，通过这个关系设计控制器，可以达到使系统稳定的目的。

#### 12.6 点测量、点控制的分布参数系统

对于点测量点控制的分布参数系统，由于在系统方程中出现了广义函数，致使对系统的研究遇到了一定的数学困难。以上节讨论的带有常微分方程控制器的分布参数系统为例，在点测量和点控制的情况下， $a_{i}(p), i=1,2; b(p)$ 都是 $\delta$ 函数或它们的导数。正如我们知道的那样，这类函数并不包括在 $L_{2}(\Omega)$ 空间内，因此，在系统方程中出现的一些项，如 $(x, g) b$ 就不在 $L_{2}(\Omega)$ 空间内。同样，当 $a_{i}(p)=\delta(p-p_{i})$ 时，测量算子 $\langle S_{i}u, a_{i}\rangle$ 在 $L_{2}(\Omega)$ 中也没有意义。这样，整个系统在 $L_{2}(\Omega)$ 空间内进行讨论就失去了严格的理论基础。

下面，我们介绍一种处理这个问题比较可行的方法，其结果是，前面得到的一些结论，都可稍加改变后推广到点测量和点控制的情况 $^{[10]}$ 。

这种方法的基本思想是选择含有 $\delta$ 函数的空间，即有限阶广义函数空间（阴范空间）作为系统的状态空间。这个空间比 $L_{2}(\Omega)$ 空间要大，包含着 $L_{2}(\Omega)$ 。然后把原来定义在 $L_{2}(\Omega)$ 空间中的线性算子 A, B, C, $S_{i}$ 延拓到阴范空间，从而把整个系统放在阴范空间中去研究。这样，在系统方程中出现 $\delta$ 函数及其导数就是很平常的事了。同时，阴范空间又是一个希尔伯特空间，它和 $L_{2}(\Omega)$ 空间一样，有着明晰的几何结构。

一般的广义函数空间，由于对基本空间函数要求太严，而且这个空间的内部结构也比较复杂，所以在应用中造成一定的困难。一个有效的方法是根据受控对象的特点，把 $L_{2}(\Omega)$ 空间适当扩大，使它包含系统方程中出现的给定阶广义函数，同时又能保持希尔伯特空间的优点。吉田耕作（Yosida）、利翁斯（Lions）、别列赞斯基（Березанский）等提出的阴范空间[34,25,39]，恰恰具有这些特点，比较适合于我们的目的。

我们从主算子 A 出发，构造所需要的阴范空间。

设 A 是 $L_{2}(\Omega)$ 中闭稠定算子, 对其定义域 $D(A)$ 中的元 u, 赋予图像范数

$$
\| u \| _ {+ 1} = \langle u, u \rangle_ {+ 1} ^ {\frac {1}{2}} = (\langle u, u \rangle_ {0} + \langle A u, A u \rangle_ {0}) ^ {\frac {1}{2}} \tag {12.6-1}
$$

容易验证， $D(A)$ 在这个范数下构成希尔伯特空间。记成 $H_{+1}(A)$ ， $\|\cdot\|_{+1}$ 是

$H_{+1}(A)$ 中的范数。为了区别，今后把 $L_{2}(\Omega)$ 记成 $H_{0}$ ，其上的范数记作 $\| \cdot \|_{0}$ 。

范数式 $(12.6-1)$ 还可等价定义为

$$
\| u \| _ {+ 1} = \left\langle \left(1 + A ^ {*} A\right) ^ {\frac {1}{2}} u, \left(1 + A ^ {*} A\right) ^ {\frac {1}{2}} u \right\rangle_ {0} ^ {1 / 2} = \left\langle T u, T u \right\rangle_ {0} ^ {1 / 2}, \quad \forall u \in D (A) \tag {12.6-2}
$$

其中 $T=(1+A^{*}A)^{\frac{1}{2}}$ 。 $(1+A^{*}A)$ 是 $H_{0}$ 中自伴正定算子，这时 $(1+A^{*}A)^{\frac{1}{2}}$ 也存在，而且它的逆算子同样存在，记 $R=T^{-1}=(1+A^{*}A)^{-\frac{1}{2}}$ 。T 把 $H_{+1}(A)$ 等距映到 $H_{0}$ 中，而且也容易验证，T 的值域是整个空间 $H_{0}=L_{2}(\Omega)$ 。因此，T 是 $H_{+1}(A)$ 到 $H_{0}$ 上的等距算子，而 R 是 $H_{0}$ 到 $H_{+1}(A)$ 上的等距算子。

由于 $D(A)$ 在 $H_0$ 中稠，所以 $H_{+1}(A)$ 也在 $H_0$ 中稠， $H_{+1}(A) \subset H_0$ 。对 $H_{+1}(A)$ 中的元 $u$ 有两种范数，一种是 $\| u \|_{+1}$ ，另一种是把 $u$ 看成 $H_0$ 中的元时，它还有范数 $\| u \|_0$ ，从式(12.6-1)可以看出

$$
\| u \| _ {0} \leqslant \| u \| _ {+ 1}, \quad \forall u \in H _ {+ 1} (A) \tag {12.6-3}
$$

对 $H_0$ 中的元 $f, g$ , 可以推出

$$
\langle f, g \rangle_ {0} = \langle R f, R g \rangle_ {+ 1} \tag {12.6-4}
$$

现在我们看一下， $H_{+1}(A)$ 的对偶空间是什么。 $H_{+1}(A)$ 的对偶空间就是一切定义在 $H_{+1}(A)$ 上有界线性泛函的全体。按这个定义，对任意 $f \in H_{0}$ ，线性泛函 $f(u) = \langle f, u \rangle_{0}$ ，因为 $|f(u)| = |\langle f, u \rangle_{0}| \leqslant \|f\|_{0} \|u\|_{0} \leqslant \|f\|_{0} \|u\|_{+1}$ ，所以 $f(u)$ 是 $H_{+1}(A)$ 上的有界线性泛函。这就是说，f 属于 $H_{+1}(A)$ 的对偶空间，即 $H_{0}$ 是 $H_{+1}(A)$ 对偶空间的子集。 $f(u) = \langle f, u \rangle_{0}$ 作为 $H_{+1}(A)$ 上的有界线性泛函，其范数为

$$
\| f \| _ {- 1} = \sup _ {u \in H _ {+ 1} (A)} \frac {| \langle f , u \rangle_ {0} |}{\| u \| _ {+ 1}}, \quad f \in H _ {0} \tag {12.6-5}
$$

以后我们会看到，按这个范数完备化 $H_{0}$ 后，得到的就是 $H_{+1}(A)$ 的对偶空间。

在 $H_0$ 中我们引入另外一种内积和由它产生的范数，即对任意 $f, g \in H_0$ ，定义

$$
\langle f, g \rangle_ {- 1} = \langle R f, R g \rangle_ {0} \tag {12.6-6}
$$

由于 $R$ 是 $H_0$ 中自伴正定算子，式(12.6-6)满足内积的一切要求。由它引出的范数仍记作 $\| \cdot \|_{-1}$

$$
\| f \| _ {- 1} = \| R f \| _ {0}, \quad \forall f \in H _ {0} \tag {12.6-7}
$$

对 $H_{0}$ 中的元, 我们引出的两种范数式(12.6-5)和(12.6-7), 其实是相等的, 即

$$
\| f \| _ {- 1} = \sup _ {u \in H _ {+ 1} (A)} \frac {| \langle f , u \rangle_ {0} |}{\| u \| _ {+ 1}} = \| R f \| _ {0} \tag {12.6-8}
$$

因为对任意 $f \in H_0$

$$
\| f \| _ {- 1} = \sup _ {u \in H + 1 (A)} \frac {| \langle f , u \rangle_ {0} |}{\| u \| _ {+ 1}} = \sup _ {\| u \| _ {+ 1} = 1} | \langle f, u \rangle_ {0} | = \sup _ {\| T u \| _ {0} = 1} | \langle R f, T u \rangle | _ {0} \leqslant \| R f \| _ {0}
$$

另一方面，由于 $R^{2}f \in H_{+1}(A)$ ，令 $u = R^{2}f$ ，则有

$$
\frac {\left| \langle f , u \rangle_ {0} \right|}{\left\| u \right\| _ {+ 1}} = \frac {\left\| R f \right\| _ {0} ^ {2}}{\left\| R ^ {2} f \right\| _ {+ 1}} = \frac {\left\| R f \right\| _ {0} ^ {2}}{\left\| R f \right\| _ {0}} = \left\| R f \right\| _ {0}
$$

由此推得

$$
\sup _ {u \in H _ {+ 1} (A)} \frac {\left| \langle f , u \rangle_ {0} \right|}{\left\| u \right\| _ {+ 1}} \geqslant \| R f \| _ {0}
$$

综合两个不等式，便得到

$$
\| f \| _ {- 1} = \sup _ {u \in H _ {+ 1} (A)} \frac {| \langle f , u \rangle_ {0} |}{\| u \| _ {+ 1}} = \| R f \| _ {0}
$$

按这个范数完备化 $H_{0}$ ，得到的空间记作 $H_{-1}(A)$ ，它是一个完备的希尔伯特空间， $H_{-1}(A)$ 就是 $H_{+1}(A)$ 的对偶空间。

对于 $H_{-1}(A)$ 中任意元 $\alpha, \langle \alpha, u \rangle_0$ 是定义在 $H_{+1}(A)$ 上的有界线性泛函，反之， $H_{+1}(A)$ 上的有界线性泛函 $\alpha(u)$ 也必可唯一地表示成

$$
\alpha (u) = \langle \alpha , u \rangle_ {0}, \quad \forall u \in H _ {+ 1} (A) \tag {12.6-9}
$$

而 $\alpha\in H_{-1}(A)$ 。

由于 $H_{-1}(A)$ 是 $H_0$ 经完备化后得到的，所以 $H_0 \subseteq H_{-1}(A)$ ，而 $H_{+1}(A) \subseteq H_0$ ，因此三个空间有如下关系

$$
H _ {+ 1} (A) \subseteq H _ {0} \subseteq H _ {- 1} (A) \tag {12.6-10}
$$

其中 $H_{0}$ 叫做基本空间， $H_{+1}(A)$ 叫做阳范空间， $H_{-1}(A)$ 叫做阴范空间。

为了进一步说明这三个空间的关系，我们把算子 T,R 加以延拓。首先看 T 的延拓。

对 $H_0$ 中任意元 $f, \langle f, Tu \rangle_0$ 是 $H_{+1}(A)$ 上有界线性泛函，这是因为 $|\langle f, Tu \rangle_0| \leqslant \| f \|_0 \| Tu \|_0 = \| f \|_0 \| u \|_{+1}$ 。根据上面所说的事实，它一定能表示成 $\langle f, Tu \rangle_0 = \langle \alpha_f, u \rangle_0$ 的形式，而 $\alpha_f \in H^{-1}(A)$ 。如令 $\alpha_f = T^+ f$ ，则有 $\langle f, Tu \rangle_0 = \langle T^+ f, u \rangle_0$ ，这里 $T^+$ 是 $T$ 的伴随算子，它把 $H_0$ 映到 $H^{-1}(A)$ 上。不仅如此，它还是等距算子，即对任意 $f \in H_0$ ，有 $\| f \|_0 = \| T^+ f \|_{-1}$ 。事实上，由于 $H_{+1}(A)$ 在 $H_0$ 中稠，对 $f \in H_0$ ，必有 $H_{+1}(A)$ 中的元列 $\{u_n\}$ 存在，使 $\lim_{n \to \infty} \| u_n - f \|_0 = 0$ ，且 $\lim_{n} \| u_n \|_0 = \| f \|_0$ 。对 $u_n, Tu_n \in H_0$ ，下述极限等式成立

$$
\begin{array}{l} \lim _ {n} \| T u _ {n} - T ^ {+} f \| _ {- 1} = \lim _ {n, m} \| T u _ {n} - T ^ {+} u _ {m} \| _ {- 1} = \lim _ {n, m} \| T (u _ {n} - u _ {m}) \| _ {- 1} \\ = \lim _ {n, m} \| u _ {n} - u _ {m} \| _ {0} = 0 \\ \end{array}
$$

所以有 $\lim_{n} Tu_n = T^+ f, \lim_{n} \| Tu_n \|_{-1} = \| T^+ f \|_{-1}$ 。但是 $\| Tu_n \|_{-1} = \| u_n \|_0$ 最后得到 $\| f \|_0 = \| T^+ f \|_{-1}$ ，这就说明 $T^+$ 是等距映 $H_0$ 到 $H^{-1}(A)$ 中。另外， $T^+$ 的值域必充满整个空间， $H^{-1}(A)$ 。如果不是这样，存在 $H^{-1}(A)$ 中一元 $\alpha$ ，它不在 $T^+$ 的值域内，这时，由于 $\langle \alpha, u \rangle_0$ 是 $H^{+1}(A)$ 上的有界线性泛函，根据黎斯（Riesz）有界线性泛函表现定理[34]知道

$$
\langle \alpha , u \rangle_ {0} = \left\langle v _ {\alpha}, u \right\rangle_ {+ 1} = \left\langle T v _ {\alpha}, T u \right\rangle_ {0} = \left\langle T ^ {+} T v _ {\alpha}, u \right\rangle_ {0}
$$

所以有 $\alpha = T^{+}Tv_{\alpha}$ ，这时 $\alpha$ 又在 $T^{+}$ 的值域内，因此出现了矛盾， $T^{+}$ 的值域是全空间 $H_{-1}(A)$ 。这就表明 $T^{+}$ 是 $H_0$ 到 $H_{-1}(A)$ 上的等距算子。今后记 $T^{+} = T,T$ 就是 $T$ 的延拓。 $\pmb{T}$ 的逆算子 $R = T^{-1}$ 也是等距算子，它是 $R$ 的延拓，是 $H_{-1}(A)$ 到 $H_0$ 上的等距算子。

综上所述，三个空间的范数关系如下

$$
\| \alpha \| _ {- 1} = \| \boldsymbol {R} \alpha \| _ {0} = \| R \boldsymbol {R} \alpha \| _ {+ 1}, \quad \forall \alpha \in H _ {- 1} (A)
$$

$$
\| u \| _ {+ 1} = \| T u \| _ {0} = \| \boldsymbol {T} T u \| _ {- 1}, \quad \forall u \in H _ {+ 1} (A) \tag {12.6-11}
$$

这三个空间的关系，可表示为

$$
\begin{array}{c} \overbrace {H _ {- 1} (A) \supseteq H _ {0} \supseteq H _ {+ 1} (A)} ^ {R} \\ \overbrace {T} ^ {T} \end{array}
$$

这样，我们由算子 A 出发，构造了阴范空间，它确实是包含 $L_{2}(\Omega)=H_{0}$ 的一个希尔伯特空间。但这个空间是否包括 $\delta$ 函数及其导数呢?下面来回答这个问题。

假如 $H_{+1}(A)$ 中（也就是 $D(A)$ 中）的函数 $u(p)$ ，在 $\Omega$ 和 $\partial\Omega$ 上有直到 q 阶连续导数。 $\delta$ 函数及其导数的定义是

$$
\langle u, \delta (p - p _ {0}) \rangle_ {0} = \int_ {\Omega} u (p) \delta (p - p _ {0}) d p = u (p _ {0})
$$

$$
\langle u, \delta^ {(q)} (p - p _ {0}) \rangle_ {0} = \int_ {\Omega} u (p) \delta^ {(q)} (p - p _ {0}) d p = (- 1) ^ {q} u ^ {(q)} (p _ {0}) \tag {12.6-12}
$$

其中

$$
u ^ {(q)} (p) = \frac {\partial^ {q} u}{\partial x _ {1} ^ {q _ {1}} \cdots \partial x _ {n} ^ {q _ {n}}}, \quad q = q _ {1} + q _ {2} + \dots + q _ {n}
$$

可以证明，如果 $H_{+1}(A)$ 包含在 l 阶索波列夫(Соболев)空间 $^{①}$ 内，只要 $q < l - \frac{n}{2}$ , n 是空间变量的维数，那么式(12.6-12)定义的 $\delta$ 函数及其导数一定属于 $H_{-1}(A)$ 。这就是说 $H_{-1}(A)$ 是含有广义函数的空间。对于梁、板、膜等一类受控对象，从主算子 A 出发构造的阴范空间 $H_{-1}(A)$ 确实包含有 $\delta$ 函数及其导数。

如果 RR 是正定的紧算子；并且有格林函数 $K(p,s)$ 时, $\delta$ 函数及其导数作为 $H_{-1}(A)$ 中的元, 它们的阴范数还可以用格林函数表示如下

$$
\left\| \delta (p - p _ {0}) \right\| _ {- 1} = \sqrt {K (p _ {0} , p _ {0})}
$$

$$
\left\| \delta^ {(q)} \left(p - p _ {0}\right) \right\| _ {- 1} = \sqrt {K _ {p s} ^ {(2 q)} \left(p _ {0} , p _ {0}\right)}, \quad q = 0, 1, 2, \dots , \quad k <   l - \frac {n}{2} \tag {12.6-13}
$$

其中

$$
K _ {p s} ^ {(2 q)} \left(p _ {0}, p _ {0}\right) = \frac {\partial^ {2 q} K (p , s)}{\partial p ^ {q} \partial s ^ {q}} \Bigg | _ {p = s = p _ {0}}
$$

在把 $L_{2}(\Omega)$ 空间扩大到 $H_{-1}(A)$ 后，它包含了所需要的广义函数，因此，用 $H_{-1}(A)$ 作为状态空间就解决了由于点测量，点控制时出现 $\delta$ 函数及其导数所带来的困难。但是，在空间这样扩大以后，还必须解决系统方程中诸算子 A, B, C 等的延拓问题，因为这些算子都是在 $L_{2}(\Omega)$ 空间中的某些子集上定义的。

首先讨论有界算子的延拓。设 L 是 $H_{0}=L_{2}(\Omega)$ 上的有界算子，在 $H_{0}$ 上 L 和 R 可交换，即 RL=LR。我们的目的是把 L 延拓到 $H_{-1}(A)$ 上，使其成为 $H_{-1}(A)$ 中的有界算子。容易验证，TLR 就是 L 的这种延拓。实际上，R 是 R 的延拓，对凡 $H_{0}$ 中的元 Rf=Rf，而 T 是 T 的延拓，对凡是 $H_{+1}(A)$ 中的元 u，Tu=Tu。因此，TLRf=TLRf=TRLf=TRLf=Lf，这就是说对凡是 $H_{0}$ 中的元 f，恒有 TLRf=Lf。对 $H_{-1}(A)$ 中的元，L 没有定义，但 TLR 却有意义，当 $\alpha\in H_{-1}(A)$ 时， $TLR\alpha\in H_{-1}(A)$ ，所以 TLR 确实是 L 的延拓。不仅如此，TLR 还是 $H_{-1}(A)$ 中的有界算子，而且依 $H_{-1}(A)$ 中的算子范数和 L 依 $H_{0}$ 中的算子范数是相等的。也就是说 TLR 是 L 的有界保范延拓。事实上，根据式(12.6-11)有

$$
\left| \boldsymbol {T L R} \right| _ {- 1} = \sup _ {\| a \| _ {- 1} \leqslant 1} \| \boldsymbol {T L R} \alpha \| _ {- 1} = \sup _ {\| R a \| _ {0} \leqslant 1} \| L R \alpha \| _ {0} = \sup _ {\| f \| _ {0} \leqslant 1} \| L f \| _ {0} = | L | _ {0}
$$

其中 $f=R\alpha$ 。

这一事实说明，在 $H_{0}$ 上定义的与 R 可交换的有界算子，可保范延拓到 $H_{-1}(A)$ 中。但在 $H_{0}$ 上的一般有界算子，这一事实并不成立。对于一般情况有以下事实成立：

设 L 是定义在 $H_{0}$ 上的任意有界算子， $L^{*}$ 是它的伴随算子。如果 $L^{*}D(T) \subseteq D(T)(D(T)$ 是算子 T 的定义域），那么 L 一定可以延拓到 $H_{-1}(A)$ 中，并成为 $H_{-1}(A)$ 中的有界算子 $^{[10]}$ 。

再看 $H_0$ 中投影算子的延拓问题。设 $P$ 是 $H_0$ 中的直交投影算子， $\{\varphi_i\}_{i=1}^{\nu}$ 是投影子空间 $PH_0$ 中的直交基，如果 $\{\varphi_i\}_{i=1}^{\nu} \subset D(T)$ ，那么 $P$ 在 $H^{-1}(A)$ 中有有界延拓 $P$

$$
\boldsymbol {P} = \sum_ {i = 1} ^ {\nu} \left\langle \boldsymbol {R} \cdot , T \varphi_ {i} \right\rangle_ {0} \varphi_ {i} \tag {12.6-14}
$$

事实上，对任意 $f \in H_{0}$

$$
\boldsymbol {P} f = \sum_ {i = 1} ^ {\nu} \left\langle \boldsymbol {R} f, T \varphi_ {i} \right\rangle_ {0} \varphi_ {i} = \sum_ {i = 1} ^ {\nu} \left\langle R f, T \varphi_ {i} \right\rangle_ {0} \varphi_ {i} = \sum_ {i = 1} ^ {\nu} \left\langle f, \varphi_ {i} \right\rangle_ {0} \varphi_ {i} = P f
$$

而对任意 $\alpha\in H_{-1}(A)$ ， $P\alpha$ 有意义，所以 P 确实是 P 的延拓。P 不仅是 $H_{-1}(A)$ 中的有界延拓，而且还是 $H_{-1}(A)$ 中的投影算子，因为

$$
\begin{array}{l} \boldsymbol {P} ^ {2} \alpha = \boldsymbol {P} \sum_ {i = 1} ^ {\nu} \left\langle \boldsymbol {R} \alpha , T \varphi_ {i} \right\rangle_ {0} \varphi_ {i} = \sum_ {i = 1} ^ {\nu} \left\langle \boldsymbol {R} \alpha , T \varphi_ {i} \right\rangle_ {0} \sum_ {j = 1} ^ {\nu} \left\langle \boldsymbol {R} \varphi_ {i}, T \varphi_ {j} \right\rangle_ {0} \varphi_ {j} \\ = \sum_ {i = 1} ^ {\nu} \left\langle \boldsymbol {R} \alpha , T \varphi_ {i} \right\rangle_ {0} \varphi_ {i} = \boldsymbol {P} \alpha \\ \end{array}
$$

即 $P^{2}\alpha=P\alpha$ 。但一般说来，P 已不是直交投影算子了。如果 P 和 R 可交换，那么 P 的延拓 P 仍是 $H_{-1}(A)$ 中的直交投影算子。

类似上边的讨论, 还可以推出, 在 $H_{0}$ 上的任意有穷维线性算子 $K = \sum_{i=1}^{n} \langle \cdot, \psi_{i} \rangle \varphi_{i}$ , 只要 $\{\psi_{i}\}_{i=1}^{n} \subset D(T)$ , 那么 K 在 $H_{-1}(A)$ 中有有界延拓 K

$$
\boldsymbol {K} \alpha = \sum_ {i = 1} ^ {n} \langle \boldsymbol {R} \alpha , T \psi_ {i} \rangle_ {0} \varphi_ {i} \tag {12.6-15}
$$

其中 $\alpha \in H^{-1}(A)$ 。 $K$ 仍是有穷维算子。

如果 $\{\varphi_i\}, \{\psi_i\}$ 是 $H_0$ 中规范双直交基，即

$$
\langle \varphi_ {i}, \psi_ {j} \rangle_ {0} = \delta_ {i j}, \quad \delta_ {i j} = \left\{ \begin{array}{l l} 0, & i \neq j \\ 1, & i = j \end{array} \right.
$$

这时， $\{T\varphi_{i}\}$ ， $\{T\psi_{i}\}$ 是 $H_{-1}(A)$ 中规范双直交基。这是因为

$$
\langle \boldsymbol {T} \varphi_ {i}, \boldsymbol {T} \psi_ {j} \rangle_ {- 1} = \left\langle \boldsymbol {R T} \varphi_ {i}, \boldsymbol {R T} \psi_ {j} \right\rangle_ {0} = \left\langle \varphi_ {i}, \psi_ {j} \right\rangle_ {0} = \delta_ {i j}
$$

于是 $H_{-1}(A)$ 中任意元 $\alpha$ ，均可按双直交基 $\{T\varphi_{i}\}$ ， $\{T\psi_{i}\}$ 展开

$$
\alpha = \sum_ {i = 1} ^ {\infty} \langle \alpha , T \psi_ {i} \rangle_ {- 1} T \varphi_ {i} = \sum_ {i = 1} ^ {\infty} \langle \alpha , R \psi_ {i} \rangle_ {0} T \varphi_ {i} \tag {12.6-16}
$$

右端级数按 $H_{-1}(A)$ 中范数强收敛。显然，这个级数在 $H_{0}$ 中是没有意义的。

以上是有界算子的延拓问题。下面再讨论一下 $H_0$ 中无界算子向 $H_{-1}(A)$ 中扩张的问题。

设 M 是 $H_{0}$ 中的稠定算子， $D(M) \supset D(A)$ ，M 的值域 $\mathcal{R}(M) \subset H_{0}$ ，如何把 M 扩张到 $H_{-1}(A)$ 中成为 $H_{-1}(A)$ 中的稠定算子，这就是无界算子的扩张问题。

如果 $RM$ 在 $D(M)$ 上是有界算子，由于 $D(M)$ 在 $H_0$ 中稠，故 $RM$ 可有界延拓到 $H_0$ 上，记这个延拓为 $RM$ ，即凡是 $u \in D(M)$ ，都有 $RMu = RMu$ ，而对于属于 $H_0$ 不在 $D(M)$ 中的元， $RM$ 都有定义。对凡是 $D(M)$ 中的元 $u, Mu = TRMu$ 是恒等式，但 $RM$ 有延拓 $RM, T$ 有延拓 $T$ ，这时可把 $M$ 扩张到 $H_{-1}(A)$ 中 $M = TRM, M$ 就是 $M$ 的一种扩张。因为对凡是 $u \in D(M)$ ，都有 $RMu = RMu, RMu \in H_{+1}(A)$ ，所以 $TRMu = TRMu = Mu$ 。而对 $H_0$ 中不在 $D(M)$ 里的元， $M$ 都有意义，因此 $M$ 是定义在 $H_0$ 上而值域 $\mathcal{R}(M) \subset H_{-1}(A)$ 中的算子，又因 $H_0$ 在 $H_{-1}(A)$ 中稠，所以 $M$ 是 $H_{-1}(A)$ 中的稠定算子， $M$ 确实是 $M$ 的一种扩张。

特别是当 M=A 时，A 在 $H_{-1}(A)$ 中的扩张为 A=TAR。A 在 $H_{+1}(A)$ 上和 R, T 可交换，在 $H_{0}$ 中是自伴算子，A 的扩张 A 在 $H_{-1}(A)$ 中也是自伴算子，也就 是说，A 是 A 在 $H_{-1}(A)$ 中的自伴扩张。实际上，对 $D(A)$ 中的元 u, Au = TARu = TARu = TRAu = Au。TAR 是定义在 $H_{0}$ 上其值域 $\mathcal{R}(A) \subset H_{-1}(A)$ ，所以 A 确实是 A 的扩张。另外，对任意 $f, g \in H_{0}$ ，有

$$
\langle f, \boldsymbol {T A R} g \rangle_ {- 1} = \langle \boldsymbol {R f}, \boldsymbol {A R} g \rangle_ {0} = \langle \boldsymbol {A R f}, \boldsymbol {R g} \rangle_ {0} = \langle \boldsymbol {T A R f}, g \rangle_ {- 1}
$$

因此， $A = TAR$ 是 $H^{-1}(A)$ 中的自伴算子， $A$ 是 $A$ 的自伴扩张。不难证明 $A$ 的这种扩张 $A$ ，有一个非常重要的性质，就是 $A$ 和 $A$ 有完全相同的本征值， $A$ 的本征值并不由于扩张而有变化 $^{[10]}$ 。

下面，我们用阴范空间作为系统的状态空间来讨论系统式(12.5-9)的定解和稳定性问题。在方程(12.5-9)中

$$
\frac {d W}{d t} = \mathcal {A} W = (\mathcal {A} + \mathcal {P} + \mathcal {T}) W
$$

$\mathcal{A}$ 是基本空间 $\mathfrak{H} = L^2 (\Omega)\times L^2 (\Omega)\times R_n = H_0\times H_0\times R_n$ 中的反自伴算子，它的定义域 $D(\mathcal{A}) = D(A^{\frac{1}{2}})\times D(A^{\frac{1}{2}})\times R_n\subset \mathfrak{H}$ ，而其值域 $\mathcal{R}(\mathcal{A})\subseteq \mathfrak{H}$ 。在 $D(\mathcal{A})$ 上引进图像范数后，构成阳范空间，记作 $\mathfrak{H}^{+1},\mathfrak{H}^{+1} = H_{+1}(A^{\frac{1}{2}})\times H_{+1}(A^{\frac{1}{2}})\times R_n$ 。 $\mathfrak{H}^{+1}$ 的对偶空间记作 $\mathfrak{H}^{-1},\mathfrak{H}^{-1} = H_{-1}(A^{\frac{1}{2}})\times H_{-1}(A^{\frac{1}{2}})\times R_n$ ，这三个空间的关系是

$$
\mathfrak {H} _ {\mathcal {C}} ^ {+ 1} (\mathscr {A}) \subset \mathfrak {H} _ {\mathcal {C}} \subset \mathfrak {H} _ {\mathcal {C}} ^ {- 1} (\mathscr {A}) \tag {12.6-17}
$$

由 $\mathfrak{H}^{+1}$ 到 $\mathfrak{H}$ 的等距算子 $T$ 为

$$
T = \left[ \begin{array}{c c c} (1 + A) ^ {\frac {1}{2}} & 0 & 0 \\ 0 & (1 + A) ^ {\frac {1}{2}} & 0 \\ 0 & 0 & (E + E _ {1}) ^ {\frac {1}{2}} \end{array} \right] \tag {12.6-18}
$$

而由 $\mathfrak{H}$ 到 $\mathfrak{H}^{+1}$ 上的等距算子 $R = T^{-1}$ 为

$$
R = \left[ \begin{array}{c c c} (1 + A) ^ {- \frac {1}{2}} & 0 & 0 \\ 0 & (1 + A) ^ {- \frac {1}{2}} & 0 \\ 0 & 0 & (E + E _ {1}) ^ {- \frac {1}{2}} \end{array} \right] \tag {12.6-19}
$$

按前面讲过的方法，把 T, R 分别延拓，记作 T, R，则 R 是 $\mathfrak{H}^{-1}$ 到 $\mathfrak{H}$ 上的等距算子，而 T 是 $\mathfrak{H}$ 到 $\mathfrak{H}^{-1}$ 上的等距算子。

反自伴算子 $\mathcal{A}_0$ 在 $\mathfrak{H}_{-1}$ 中有反自伴扩张，记作 $\mathcal{A}_0$ ，它和 $\mathcal{A}_0$ 有相同的本征值。

算子 $\mathcal{P}$ 是 $\mathfrak{H}$ 中的有界算子，根据前面讲过的对有界算子的延拓， $\mathcal{P}$ 中的算子 $BA^{-\frac{1}{2}}$ ， $(BA^{-\frac{1}{2}})^{*} = A^{-\frac{1}{2}}B^{*}$ ， $A^{-\frac{1}{2}}B^{*}D(A^{\frac{1}{2}})\subseteq D(A^{\frac{1}{2}})$ ，所以 $BA^{-\frac{1}{2}}$ 可有界延拓到 $H_{-1}(A^{\frac{1}{2}})$ 中，同理对算子 $C$ ，只要 $C^* D(A^{\frac{1}{2}})\subseteq D(A^{\frac{1}{2}})$ ，那么 $C$ 也可有界延拓到 $H_{-1}(A^{\frac{1}{2}})$ ，从而 $\mathcal{P}$ 可有界延拓到 $\mathfrak{H}_{-1}$ 中成为 $\mathfrak{H}_{-1}$ 中的有界算子，记作 $\widetilde{\mathcal{P}}$ 。

反馈算子 $\mathcal{F}$ , 其中控制算子 $G = (\cdot, g) b$ , 在点控制时, $b = \delta(p - p_0)$ , 只要

$\delta (p - p_0)\in H_{-1}(A^{\frac{1}{2}})$ ，那么 $G$ 是从 $R_{n}$ 到 $H_{-1}(A^{\frac{1}{2}})$ 中的有界算子。

至于测量算子 $S_{i}A^{-\frac{1}{2}}\varphi = \langle S_{i}A^{-\frac{1}{2}}\varphi ,a_{i}\rangle \pmb{k}_{i},i = 1,2,\varphi \in H_{0}$ ，在点测量时， $a_{i}(p)$ $= \delta (p - p_{0})$ ，如果 $S_{i}A^{-\frac{1}{2}}\varphi \in H_{+1}(A^{\frac{1}{2}})$ ，那么 $S_{i}A^{-\frac{1}{2}}$ 可有界延拓到 $H_{-1}(A^{\frac{1}{2}})$ 上。

这样，反馈算子 $\mathcal{T}$ 可有界延拓到 $\widetilde{\mathfrak{H}}^{-1}$ 上，记作 $\widetilde{\mathcal{T}}$ 。

综上所述，我们把原来的系统状态空间由 $\mathfrak{H}$ 扩大到 $\mathfrak{H}^{-1}$ , 它仍然是希尔伯特空间, 且含有所要求的广义函数。把 $\mathfrak{H}^{-1}$ 作为系统式(12.5-9)的状态空间, $\mathcal{A}_0$ 在 $\mathfrak{H}^{-1}$ 有自伴扩张 $\tilde{\mathcal{A}_0}$ , 它和 $\mathcal{A}_0$ 有相同的本征值, 而算子 $\mathcal{P}, \mathcal{T}$ 都可有界延拓到 $\mathfrak{H}^{-1}$ 中。这样, 式(12.5-9)在 $\mathfrak{H}^{-1}$ 中就成为

$$
\frac {d W}{d t} = \tilde {\mathcal {A}} W = (\tilde {\mathcal {A}} _ {0} + \tilde {\mathcal {P}} + \tilde {\mathcal {T}}) W \tag {12.6-20}
$$

$\tilde{A}_{0}$ 的定义域是 $D(\tilde{A}_{0}) = H_{0} \times H_{0} \times R_{n}$ 。

方程(12.6-20)的本征值问题和定解问题，与分布测量、分布控制时方程(12.5-9)是完全类似的，重复上节的讨论，可以证明以下事实：如果 $A$ 是自伴正定有紧预解式的算子，它的本征值列 $\{\mu_n^2\}$ 都是单重的，且满足 $\lim_{n} \mu_n - \mu_{n-1} = \infty$ ，而 $BA^{-\frac{1}{2}}$ ， $C$ 是 $H_0$ 中的有界算子， $C^* D(A^{\frac{1}{2}}) \subseteq D(A^{\frac{1}{2}})$ ， $S_i A^{-\frac{1}{2}}$ 是 $H_0$ 到 $R_n$ 中的有界算子，且对 $H_0$ 中的元 $S_i A^{-\frac{1}{2}} \varphi \in H_{+1}(A^{\frac{1}{2}})$ ， $i = 1, 2, a_i(p) \in H_{-1}(A^{\frac{1}{2}})$ ， $G$ 中 $b \in H_{-1}(A^{\frac{1}{2}})$ 。那么， $\tilde{\mathcal{A}}$ 在 $\tilde{\mathcal{Q}}^{-1}$ 中的本征值除有穷个外都是单重的，且它的本征元列 $\{(\Phi_{lj})_{j=0}^{m_l-1}\}_{l=-\infty}^{\infty}$ 与伴随算子 $\tilde{\mathcal{A}}^*$ 的本征元列 $\{(\Psi_{lj})_{j=0}^{m_l-1}\}_{l=-\infty}^{\infty}$ 构成 $\tilde{\mathcal{Q}}^{-1}$ 中的双直交基，对任意 $W \in \tilde{\mathcal{Q}}^{-1}$ ，可展成下列强收敛级数

$$
W = \sum_ {1 l | \leqslant N _ {0}} \left(\sum_ {j = 0} ^ {m _ {l} - 1} \langle W, \Psi_ {l j} \rangle_ {- 1} \Phi_ {l j}\right) + \sum_ {1 l | > N _ {0}} \langle W, \Psi_ {l} \rangle_ {- 1} \Phi_ {l}
$$

$$
W = \sum_ {1 l l \leqslant N _ {0}} \left[ \sum_ {j = 0} ^ {m _ {l} - 1} \langle W, \Phi_ {l j} \rangle_ {- 1} \Psi_ {l j} \right] + \sum_ {1 l l > N _ {0}} \langle W, \Phi_ {l} \rangle_ {- 1} \Psi_ {l} \tag {12.6-21}
$$

这里右端级数按 $\mathfrak{S}_{\mathfrak{C}^{-1}}$ 中的阴范数收敛。如果 $A$ 的本征值还满足 $\sum (\mu_n - \mu_{n-1})^{-2} < \infty$ ，同样可以证明 $\tilde{\mathcal{A}}$ 是 $\mathfrak{S}_{\mathfrak{C}^{-1}}$ 中强连续单参数有界算子群 $U(t)$ 的生成算子，它是一切本征运动群之和

$$
U (t) = \sum_ {l = - \infty} ^ {\infty} U _ {l} (t) = \sum_ {| l | \leqslant N _ {0}} e ^ {\lambda_ {l} t} \left[ Q _ {l} + t D _ {l} + \dots + \frac {(t D _ {l}) ^ {m _ {l} - 1}}{(m _ {l} - 1) !} \right] + \sum_ {| l | > N _ {0}} e ^ {\lambda_ {l} t} Q _ {l} \tag {12.6-22}
$$

上式右端按算子阴范数收敛。而

$$
Q _ {l} = \sum_ {j = 0} ^ {m _ {l} - 1} \langle \bullet , \Psi_ {l j} \rangle_ {- 1} \Phi_ {l j}, \quad D _ {l} = \sum_ {j = 0} ^ {m _ {l} - 1} \langle \bullet , \Psi_ {l, j + 1} \rangle_ {- 1} \Phi_ {l j}
$$

$\Phi_{lj}$ , $\Psi_{lj}$ 分别是 $\tilde{\mathcal{A}}$ 和 $\tilde{\mathcal{A}}^{*}$ 对应于 $\lambda_l$ 和 $\bar{\lambda}_l$ 的规范广义本征元。

方程(12.6-20)对任意初值 $W_{0} \in H_{0} \times H_{0} \times R_{n}$ 有唯一解 $W(t) = U(t)W_{0}$ 。

解 $U(t)W_0$ 和分布测量、分布控制时(12.5-9)的解 $U(t)W_0$ 有两点不同：一个是 $W_0 \in H_0 \times H_0 \times R_n$ 而 $W_0 \in D(A^{\frac{1}{2}}) \times D(A^{\frac{1}{2}}) \times R_n, D(A^{\frac{1}{2}}) \times D(A^{\frac{1}{2}}) \times R_n \subset H_0 \times H_0 \times R_n$ 。这就是说，点控制、点测量时，系统方程有解的初值范围要比分布控制、分布测量时大。另一个是 $U(t)W_0 \in H_0 \times H_0 \times R_n$ 而 $U(t)W_0 \in H_{-1}(A^{\frac{1}{2}}) \times H_{-1}(A^{\frac{1}{2}}) \times R_n = \mathfrak{S}_{-1}$ ，也就是说分布测量、分布控制时系统方程的解在 $L_2$ 空间 $\mathfrak{S}_0$ 中，而点测量、点控制时，这个解在阴范空间 $\mathfrak{S}_{-1}$ 中。 $U(t)W_0$ 叫做方程的古典解，而 $U(t)W_0$ 则叫做广义解。当初始条件 $W_0 \in D(A^{\frac{1}{2}}) \times D(A^{\frac{1}{2}}) \times R_n$ ，而且方程式内不含 $\delta$ 函数时，古典解和广义解是一致的。否则，古典解不存在，但广义解是存在的。

在点测量、点控制情况下，线性系统稳定性问题和分布测量、分布控制时的情况一样，完全取决于系统本征值在复平面上的分布，这里就不再重复了。

目前，在工程技术中应用的振型分析方法，是分析分布参数系统一种比较有效的方法。我们上边所讨论的结果恰好为这种方法建立了严格的理论基础。这种方法不仅对分布测量、分布控制的系统是有效的，对点测量、点控制的分布参数系统也是有效的。同时还可以看出，在对分布参数系统作有穷维逼近时是有严格理论根据的。依据实际问题的精度要求，对无穷维系统作有穷维逼近时，除去逼近误差外，再没有别的误差。

#### 12.7 分布参数系统的能控性和能观测性

在第 4.10 节和 4.11 节中，我们介绍了线性集中参数系统能控性和能观测性的概念。文献[33]是最早把集中参数系统能控性和能观测性概念推广到线性分布参数系统，并且得到了类似于集中参数系统的完全能控性和完全能观测性的条件。

系统能控性概念是系统控制能力的表现，它反映了系统状态和输入（控制）之间的关系。由于分布参数系统的状态空间是希尔伯特空间，所以我们将在这种空间中来讨论这个问题 $^{[12]}$ 。设给定的分布参数系统为

$$
\frac {d U (t)}{d t} = A U (t) + B F (t) \tag {12.7-1}
$$

其中 $U(t)$ 是系统状态。设系统状态空间 $\mathfrak{H}$ 是一可分的希尔伯特空间，对任意固定的 $t, U(t) \in \mathfrak{H}$ 。A 是 $\mathfrak{H}$ 中的线性算子，其定义域为 $D(A)$ 。 $F(t)$ 是系统的控制，也就是系统的输入，它的取值也是一可分希尔伯特空间，记作 $\mathfrak{H}^{c}$ 。B 是从 $\mathfrak{H}^{f}$ 到 $\mathfrak{H}$ 中的有界线性算子。

在第 12.3 节中我们曾经说过，分布参数系统的控制 $F(t,x)$ 不仅是 t 而且也 是空间变量 x 的函数。当 t 固定后，它是 x 的函数，即空间 $\mathfrak{H}_{F}$ 中的元。所以控制 $F(t)$ 是自变量为 $t, 0 \leqslant t \leqslant T, T < \infty$ ，取值于 $\mathfrak{H}_{F}$ 的函数。在讨论能控性问题时，先限定控制 $F(t)$ 的类别：要求对 $\mathfrak{H}_{F}$ 中每一个元 v， $\langle F(t), v \rangle$ 是 t 的可测函数（勒贝格意义下），并且 $\int_{0}^{T} \| F(t) \| dt$ 对每个有限的 T 都是有穷值。也就是说，对每个控制 $F(t), \| F(t) \|$ 是一可积函数。这种控制的全体构成了在 $\mathfrak{H}_{F}$ 上的 $L_{1}$ 空间，今后记作 $L_{1}((0, T), \mathfrak{H}_{F})$ 。

在系统式(12.7-1)中, 假定 A 是 $\S$ 中强连续有界算子半群 $S(t)$ 的生成算子, 当给定 $U(0) \in D(A)$ , 在 $(0, T)$ 上 $F(t)$ 是强连续函数时, 方程(12.7-1)有唯一解, 并可表达为

$$
U (t) = S (t) U (0) + \int_ {0} ^ {t} S (t - \tau) B F (\tau) d \tau \tag {12.7-2}
$$

其中第一项 $S(t)U(0)$ 只与初值有关，而第二项是由控制 $F(t)$ 决定的。在讨论能控性问题时，主要和这一项有关。整个解式(12.7-2)表示了在给定初值 $U(0)$ 和控制 $F(t)$ 的情况下，系统状态的演化过程。但这里对初值 $U(0)$ 和控制 $F(t)$ 的要求比较强，事实上当 $U(0)$ 不在 $D(A)$ 内或者控制 $F(t) \in L_1((0, T), \mathfrak{H})$ 时，解式(12.7-2)仍然是存在的，这时它在下述意义下满足方程(12.7-1): 对 $D(A^*) (A^*$ 是 $A$ 的伴随算子）中每个元 $v$ ，都有

$$
\frac {d}{d t} \langle U (t), v \rangle = \langle U (t), A ^ {*} v \rangle + \langle F (t), B ^ {*} v \rangle \tag {12.7-3}
$$

以及

$$
\lim _ {t \rightarrow 0} \langle U (t), v \rangle = \langle U (0), v \rangle \tag {12.7-4}
$$

而且满足式(12.7-3)和(12.7-4)的解式(12.7-2)是唯一的。

这就是说解式(12.7-2)在两种意义下满足式(12.7-1)，一种是当 $U(0)\in D(A)$ ， $F(t)$ 强连续时，这时解 $U(t)$ 叫做强解，而在式(12.7-3)和(12.7-4)意义下的解叫弱解。在讨论能控性问题时，式(12.7-1)的解是指它的弱解。

现假定初值为零， $F(t) \in L_{1}((0, T), \mathfrak{H}_{F})$ ，定义算子

$$
K F = \int_ {0} ^ {T} S (T - \tau) B F (\tau) d \tau \tag {12.7-5}
$$

它是从 $L_{1}((0,T),\mathfrak{H}_{T})$ 到 $\mathfrak{H}$ 中的有界算子。用 $\omega (T)$ 表示算子 $K$ 的值域，它是系统式(12.7-1)在所有 $F(t)\in L_1((0,T),\mathfrak{H}_F)$ 控制作用下，从初始零状态出发，在 $T$ 时刻系统能够到达的所有状态，这和集中参数系统的等时区很相似。显然， $\omega (T)$ 是 $\mathfrak{H}$ 中的子空间，当 $T_{1} > T_{2}$ 时， $\omega (T_{1})\supseteq \omega (T_{2})$ ，这就是说，当 $T$ 增大时， $\omega (T)$ 也变大。把所有 $\omega (T)$ 合起来，它仍是 $\mathfrak{H}$ 中的子空间，用 $\omega = \bigcup_{T > 0}\omega (T)$ 记这个子空间（这里 U 表示集合的并），则 $\omega$ 叫做系统的能达状态集。

系统式(12.7-1)叫做完全能控的，是指它的能达状态集 $\omega$ 在状态空间 $\mathfrak{H}$ 中 稠，即 $\overline{\omega} = \mathfrak{H},\overline{\omega}$ 表示 $\omega$ 的闭包。这就是说，对 $\mathfrak{H}$ 中任意状态 $V$ ，总可以找到能达状态集 $\omega$ 中的状态 $U$ ，使 $U$ 和 $V$ 非常接近， $\| V - U\| < \varepsilon ,\varepsilon$ 是任意小的正数。确切地说，对 $\mathfrak{H}$ 中任意状态 $V$ 和任意小的正数 $\varepsilon$ ，总存在有限的时间 $T(T$ 依赖于 $V$ 和 $\varepsilon)$ ，以及控制 $F(t)\in L_{1}((0,T),\mathfrak{H}_{c})$ 使

$$
U (T) = \int_ {0} ^ {T} S (T - \tau) B F (\tau) d \tau \in \omega (T) \subset \omega
$$

并且有 $\| V - U(T)\| < \varepsilon$ 成立。

值得注意的是，分布参数系统完全能控性只要求能达状态集 $\omega$ 在 $\mathfrak{H}$ 中稠，而不是 $\omega=\mathfrak{H}$ ,这和集中参数系统是不一样的。

下面，我们进一步讨论系统完全能控的判定准则。

首先我们注意到， $S(t)B$ 是 $\mathfrak{H}$ 到 $\mathfrak{H}$ 中的有界算子，记这个算子的值域为 $\mathcal{R}(S(t)B)$ ， $t$ 不同时， $\mathcal{R}(S(t)B)$ 也不相同。把所有 $\mathcal{R}(S(t)B)$ 合起来，记作 $\mathcal{R} = \bigcup_{t\geqslant 0}\mathcal{R}(S(t)B)$ ，它仍是 $\mathfrak{H}$ 中子空间。现在我们来说明，如果 $\mathcal{R}$ 在 $\mathfrak{H}$ 中稠必有 $\omega$ 在 $\mathfrak{H}$ 中稠，从而系统是完全能控的。

我们反证，设 $\mathcal{R}$ 在 $\mathfrak{H}$ 中稠，而 $\omega$ 在 $\mathfrak{H}$ 中不稠，看看会出现什么矛盾。如果 $\omega$ 在 $\mathfrak{H}$ 中不稠，必存在 $\mathfrak{H}$ 中的元 $y$ ，它和 $\omega$ 直交，也就是对每个有限的 $T, y$ 直交于 $\omega(T)$ ，即

$$
\left\langle \int_ {0} ^ {T} S (T - \tau) B F (\tau) d \tau , y \right\rangle = \int_ {0} ^ {T} \left\langle S (T - \tau) B F (\tau), y \right\rangle d \tau = 0
$$

但 $\langle S(T-\tau)BF(\tau),y\rangle=\langle F(\tau),B^{*}S^{*}(T-\tau)y\rangle$ ，所以有

$$
\int_ {0} ^ {T} \langle S (T - \tau) B F (\tau), y \rangle d \tau = \int_ {0} ^ {T} \langle F (\tau), B ^ {*} S ^ {*} (T - \tau) y \rangle d \tau = 0
$$

现选择一个特殊的控制 $F(\tau)$

$$
F (\tau) = B ^ {*} S ^ {*} (T - \tau) y
$$

它显然属于 $L_{1}((0,T),\mathfrak{S}_{F})$ ，代到上式则有

$$
\int_ {0} ^ {T} \left\| B ^ {*} S ^ {*} (T - \tau) y \right\| ^ {2} d \tau = 0
$$

因而有 $B^{*}S^{*}(T - \tau)y = 0,0\leqslant \tau \leqslant T$ 。对固定的 $\tau ,B^{*}S^{*}(T - \tau)y\in \mathfrak{H}_{\mathcal{C}}$ ，由于它是零元，故必和 $\mathfrak{H}_x$ 中所有元 $x$ 直交，即

$$
\langle B ^ {*} S ^ {*} (T - \tau) y, x \rangle = 0
$$

或者

$$
\langle y, S (T - \tau) B x \rangle = 0
$$

这个等式对于所有有限 T 和 $\xi_{F}$ 中所有元 x 都成立, 也就是对所有 $t \geqslant 0$ 有

$$
\langle y, S (t) B x \rangle = 0 \tag {12.7-6}
$$

这说明，算子 $S(t)B, t \geqslant 0$ 的值域 R 在 $\mathfrak{H}$ 中不稠, 因而和原来假定 R 在 $\mathfrak{H}$ 中稠相矛盾。所以必须有 $\omega$ 在 $\mathfrak{H}$ 中稠。

这个事实反过来也是对的, 就是说, 如果 $\omega$ 在 $\mathfrak{H}$ 中稠, 那么 R 也一定在 $\mathfrak{H}$ 中稠。因此, $\omega$ 在 $\mathfrak{H}$ 中稠和 R 在 $\mathfrak{H}$ 中稠是等价的, 这样, 我们就可以用 R 是否在 $\mathfrak{H}$ 中稠来判别系统是否完全能控。

应用类似的方法还可以证明，系统式(12.7-1)完全能控的必要充分条件是，对每个 t>0,如果 $\xi$ 中有某个元 x,使

$$
\int_ {0} ^ {t} S (\tau) B B ^ {*} S ^ {*} (\tau) x d \tau = 0 \tag {12.7-7}
$$

则必定有 x=0。

分布参数系统完全能控性的这两个准则，可以看成是集中参数系统完全能控性的相应推广。当 $\mathfrak{H}$ 是有穷维空间时，这时算子 $K$ 是有穷维算子，系统完全能控性就是要求 $K$ 的值域 $\omega = \mathfrak{H}$ ，即 $K$ 是不降秩的。这时上述两个能控性准则就简化为线性集中参数系统的能控性准则。

下面，我们再介绍一下系统能观测性的概念。在线性系统式(12.7-1)中，由于测量手段的限制，往往不能直接测量到全部状态 $U(t)$ , 直接测量到的系统输出，通常是状态 $U(t)$ 的函数。它可以表达成

$$
y (t) = C U (t) \tag {12.7-8}
$$

$y(t)$ 叫做系统输出或叫状态的观测值，它属于希尔伯特空间 $\mathfrak{H}_c$ 。 $C$ 是由 $\mathfrak{H}$ 到 $\mathfrak{H}_c$ 上的有界算子（ $C$ 可以是无界算子，这里为了说明方便，假定 $C$ 是有界的）。

系统能观测性概念，反映了输出和状态之间的关系。就是说能否根据系统的输出 $y(t)$ 来唯一确定系统的状态。比如，当控制 $F(t) = 0$ 时，系统的运动是初值引起的，这时方程(12.7-1)的解是 $U(t) = S(t)U(0)$ ，能观测到的系统输出是 $y(t) = CS(t)U(0)$ 。如果测得到在[0, T]时间内系统的输出 $y(t)$ ，我们能否根据 $y(t)$ 唯一确定初值 $U(0)$ ，因为一旦 $U(0)$ 确定，系统的状态 $U(t)$ 也就确定了。显然，这一点和算子 $CS(t)$ 的性质有直接关系。

首先需要定义算子 $CS(t)$ 的零子空间 $\mathfrak{H}, \mathfrak{H} = \{u \mid u \in \mathfrak{H}, CS(t) u = 0, t \geqslant 0\}$ 容易检查它确是 $\mathfrak{H}$ 的子空间。显然，凡 $\mathfrak{H}$ 中的元无法根据输出来唯一确定，因为 $\mathfrak{H}$ 中不同的元输出都是零，在输出和状态之间没有一一对应关系。

给定线性系统式(12.7-1)和(12.7-8)，系统叫做完全能观测的是指子空间 $\mathfrak{H}$ 是空集，即

$$
\mathfrak {H} = \{u | u \in \mathfrak {H}, C S (t) u = 0, t \geqslant 0 \} = \emptyset \tag {12.7-9}
$$

其中 ∅ 表示空集。

现在我们看一下，如何判断一个线性系统是完全能观测的：对 $t \geqslant 0$ , 若 $CS(t)u = 0$ , 则它必和 $\xi_{x}$ 中所有元 y 直交

$$
\langle y, C S (t) u \rangle = 0 \tag {12.7-10}
$$

但 $\langle y, CS(t)u\rangle = \langle S^{*}(t)C^{*}y,u\rangle$ ，所以对 $t \geqslant 0$ ，有 $\langle S^{*}(t)C^{*}y,u\rangle = 0$ 。根据定义，完全能观测性要求 $u = 0$ ，由此推得，对 $t \geqslant 0$ ，如果算子 $S^{*}(t)C^{*}$ 的值域 $\mathcal{R}(S^{*}(t)C^{*})$

在 $\mathfrak{H}$ 中稠的话, 必有 u=0, 因此, 我们得到完全能观测性的第一个准则是

$$
\bigcup_ {t \geqslant 0} \mathcal {R} (S ^ {*} (t) C ^ {*}) \tag {12.7-11}
$$

在 $\mathfrak{H}$ 中稠。

和讨论能控性问题时一样，式(12.7-11)又等价于下面这样的事实，对 t>0,如果 $\xi$ 中存在某个元 u,使

$$
\int_ {0} ^ {t} S ^ {*} (\tau) C ^ {*} C S (\tau) u d \tau = 0 \tag {12.7-12}
$$

则一定有 u=0。

这就是完全能观测性的第二个准则。

下面举个例子来说明完全能观测性和完全能控性的物理意义。

在第 12.5 节中, 讨论带有常微分控制器的分布参数反馈系统时, 曾经得到过, 算子 A 和 B 没有共同本征值的充要条件是式(12.5-21)成立, 即

$$
\begin{array}{l} \langle \boldsymbol {b}, \boldsymbol {\psi} _ {l} \rangle \neq 0, \quad l = \pm 1, \pm 2, \dots \\ W (\lambda) \neq 0, \quad l = \pm 1, \pm 2, \dots \\ \left(\mathbf {z} _ {l}, \mathbf {g}\right) \neq 0, \quad l = 1, 2, \dots , n \\ H (\alpha) \neq 0, \quad l = 1, 2, \dots , n \\ \end{array}
$$

这组条件和系统能控性、能观测性有密切关系。

现把第 12.4 节中式(12.4-19)化成(12.7-1)的形式。令 $u_{1}=u, u_{2}=\dot{u}_{1}, x=z, U=(u_{1}, u_{2}, z)$ ，则有

$$
\frac {d U (t)}{d t} = \mathcal {A} U (t) + \mathcal {B} F (t) \tag {12.7-13}
$$

其中

$$
\mathcal {A} = \left( \begin{array}{c c c} 0 & I & 0 \\ - A - B & - C & 0 \\ 0 & 0 & J \end{array} \right), \quad \mathcal {B} = \left( \begin{array}{c c c} 0 & 0 & 0 \\ 0 & 0 & b \\ \boldsymbol {k} _ {1} & \boldsymbol {k} _ {2} & 0 \end{array} \right)
$$

$F(t)=(f_{1}(t),f_{2}(t),f_{3}(t))$ 是系统的输入, $f_{1},f_{2},f_{3}$ 是连续的实值函数。

假定测量方程是

$$
V (t) = C U (t) \tag {12.7-14}
$$

其中

$$
C = \left[ \begin{array}{c c c} \langle S _ {1} \bullet , a _ {1} \rangle & 0 & 0 \\ 0 & \langle S _ {2} \bullet , a _ {2} \rangle & 0 \\ 0 & 0 & (\bullet , \mathbf {g}) \end{array} \right]
$$

$V(t)$ 是系统输出。

我们指出，在式(12.5-21)条件中

$$
\langle \boldsymbol {b}, \boldsymbol {\psi} _ {l} \rangle \neq 0, \quad l = \pm 1, \pm 2, \dots
$$

$$
H (\alpha) \neq 0, \quad l = 1, 2, \dots , n \tag {12.7-15}
$$

是系统式(12.7-13)完全能控的必要充分条件，而

$$
\left(\mathbf {z} _ {l}, \mathbf {g}\right) \neq 0, \quad l = 1, 2, \dots , n
$$

$$
W (\lambda) \neq 0, \quad l = \pm 1, \pm 2, \dots \tag {12.7-16}
$$

是系统式(12.7-13)，(12.7-14)完全能观测的必要充分条件。为了更明显地看出它的物理意义，我们讨论式(12.7-13)和(12.7-14)的一个特殊情况

$$
\frac {d ^ {2} u}{d t ^ {2}} + A u = b f (t) \tag {12.7-17}
$$

测量方程是

$$
V (t) = \left\langle S \frac {d u}{d t}, a \right\rangle \tag {12.7-18}
$$

其中 $S$ 是微分算子 $\frac{\partial}{\partial x}, a \in \mathfrak{H}$ 。 $V(t)$ 表示测量的是弹性梁的角速度。现把它化成式(12.7-13)的形式，令 $u = u_1, u_2 = \dot{u}_1 = \dot{u}, U = (u_1, u_2), F(t) = (0, f(t))$ ，则有

$$
\frac {d U (t)}{d t} = \mathcal {A} U (t) + \mathcal {B} F (t) \tag {12.7-19}
$$

其中

$$
\mathcal {A} = \left( \begin{array}{c c} 0 & I \\ - A & 0 \end{array} \right), \quad \mathcal {B} = \left( \begin{array}{c c} 0 & 0 \\ 0 & b \end{array} \right)
$$

测量方程是

$$
V (t) = \left[ \begin{array}{c c} 0 & 0 \\ 0 & \langle S \bullet , a \rangle \end{array} \right] U (t) = C U (t) \tag {12.7-20}
$$

在文献[8]中曾证明，系统式(12.7-19)完全能控的必要充分条件是

$$
\langle \varphi_ {n}, b \rangle \neq 0, \quad n = 1, 2, \dots \tag {12.7-21}
$$

其中 $\varphi_{n}, n=1,2,\cdots$ 是算子 A 的本征元，也就是梁的固有振型。系统完全能观测的必要充分条件是

$$
\langle S \varphi_ {n}, a \rangle \neq 0, \quad n = 1, 2, \dots \tag {12.7-22}
$$

这两组条件有明确的物理意义。 $\langle\varphi_{n},b\rangle\neq0,n=1,2,\cdots$ 说明控制作用分布函数 b 在 A 的所有本征子空间上都有投影分量，因而在 b 上施加控制作用 $f(t)$ 时，对所有振型 $\varphi_{n}$ 都能产生影响。如果某个振型 $\varphi_{m}$ ，使 $\langle\varphi_{m},b\rangle=0$ ，那么控制作用对这个振型以及由它张成的本征子空间不产生任何效果，而系统状态也到达不了由 $\varphi_{m}$ 产生的子空间内。为了说明这一点，看一下系统式(12.7-19)的算子 K 的具体形式。按式(12.7-5)，有

$$
K F (t) = \int_ {0} ^ {t} S (t - \tau) \mathcal {B} F (\tau) d \tau \tag {12.7-23}
$$

$S(t)$ 是 $\mathfrak{H}$ 中有界算子半群， $\mathcal{A}$ 是它的生成算子。 $S(t)$ 可表示成

$$
S (t) = \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \langle \bullet , \varphi_ {n} \rangle \varphi_ {n} \tag {12.7-24}
$$

其中 $\omega_{n}, \varphi_{n}$ 是 A 的本征值和相应的本征元。若 $\{\mu_{n}^{2}\}_{1}^{\infty}$ 是 A 的本征值， $\{\varphi_{n}\}_{1}^{\infty}$ 是对应的本征元，容易验证， $\omega_{n} = \pm \mu_{n} i$ ，而 $\varphi_{n} = (\varphi_{n}, \omega_{n} \varphi_{n})$ ，令 $\mu_{n} = \mu_{-n}, \varphi_{n} = \varphi_{-n}, \omega_{-n} = -i \mu_{n}, n = \pm 1, \pm 2, \cdots$ ，这时，半群 $S(t)$ 可具体表示为

$$
S (t) = \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \left\langle \cdot , \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} \right\rangle \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} \tag {12.7-25}
$$

式中要求 $\varphi_{n}$ 是规范本征元， $\| \varphi_{n} \|_{\mathfrak{H}} = 1$ 必须要求 $\| \varphi_{n} \|_{L_{2}} = \frac{1}{\sqrt{1 + \omega_{n}^{2}}}$ 将它代到式(12.7-23)中，则有

$$
\begin{array}{l} K F (t) = \int_ {0} ^ {t} \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} (t - \tau)} \left\langle \mathcal {B} F (\tau), \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} \right\rangle \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} d \tau \\ = \sum_ {- \infty} ^ {\infty} \int_ {0} ^ {t} e ^ {\omega_ {n} (t - \tau)} \langle b f (\tau), \omega_ {n} \varphi_ {n} \rangle \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} d \tau \\ = \sum_ {- \infty} ^ {\infty} \omega_ {n} \langle b, \varphi_ {n} \rangle \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} \int_ {0} ^ {t} e ^ {\omega_ {n} (t - \tau)} f (\tau) d \tau \\ \end{array}
$$

令 $\omega_{n}\int_{0}^{t}e^{\omega_{n}(t - \tau)}f(\tau)d\tau = \alpha_{n}(t)$ ，则上式变成

$$
K F (t) = \sum_ {- \infty} ^ {\infty} \alpha_ {n} (t) \langle b, \varphi_ {n} \rangle \binom {\varphi_ {n}} {\omega_ {n} \varphi_ {n}} \tag {12.7-26}
$$

由此可以明显看出，如果 $\langle b, \varphi_m \rangle = 0$ ，无论控制 $F(t)$ 如何选择，这时算子 $K$ 的值域中不含有 $\left( \begin{array}{c} \varphi_m \\ \omega_m \varphi_m \end{array} \right)$ 生成的子空间。因此， $K$ 的值域在 $\mathfrak{H} \times \mathfrak{H}$ 中不稠，从而系统不是完全能控的。

完全类似，条件式(12.7-22)说明，当且仅当所有振型 $\varphi_{n}, n=1,2,\cdots$ , 都能测量并有输出的时候，系统是完全能观测的。比如，对某一振型 $\varphi_{m}, \langle S\varphi_{m}, a\rangle=0$ , 这时系统不是完全能观测的。因为在这种情况下，根据系统输出确定不了初值（只考虑非强迫运动)。设系统初值为 $U(0)=(u_{1}(0), u_{2}(0))$ , 系统的输出为

$$
V (t) = C S (t) U (0)
$$

根据式 $(12.7-20)$ 和 $(12.7-25)$ ，可以得到

$$
\begin{array}{l} V (t) = C \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \langle U (0), \varphi_ {n} \rangle \varphi_ {n} \\ = \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \langle U (0), \varphi_ {n} \rangle C \varphi_ {n} \\ \end{array}
$$

$$
\begin{array}{l} = \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \langle U (0), \varphi_ {n} \rangle \left( \begin{array}{c c} 0 & 0 \\ 0 & \langle S \bullet , a \rangle \end{array} \right) \binom{\varphi_ {n}}{\omega_ {n} \varphi_ {n}} \\ = \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \langle U (0), \varphi_ {n} \rangle \left( \begin{array}{c} 0 \\ \omega_ {n} \langle S \varphi_ {n}, a \rangle \end{array} \right) \\ = \left[ \begin{array}{c} 0 \\ \sum_ {- \infty} ^ {\infty} e ^ {\omega_ {n} t} \omega_ {n} \langle S \varphi_ {n}, a \rangle \langle U (0), \varphi_ {n} \rangle \end{array} \right] \tag {12.7-27} \\ \end{array}
$$

如果 $\langle S\varphi_{m},a\rangle=0$ ，不论初值 $U(0)$ 如何，在输出 $V(t)$ 中，不含有初值 $U(0)$ 在 $\varphi_{m}$ 张成子空间内的分量，因此根据输出 $V(t)$ 不能唯一确定初值 $U(0)$ 。

#### 12.8 满足给定积分指标的控制设计

在前面几节中，讨论了分布参数系统的稳定性、能控性以及能观测性等问题，它们属于系统分析的范畴。从这节起，将讨论给定了系统指标要求后，如何设计控制器，使系统性能满足某些预定的要求，这就是系统的设计问题。系统性能指标通常可用受控量和控制量函数的一个积分来表达，如能量指标，时间指标等都可用积分形式来表示。和集中参数系统一样，在给定了系统性能指标后，如何寻找使性能指标达到极小（或极大）的控制问题，即所谓的最优控制问题。实际的工程系统，受控量和控制量由于受到结构和技术实现上的限制，它们只能在一定范围内变化，这种控制受到约束的最优控制问题，将在下一节里讨论。

在这一节里，假定控制量的取值不受限制。这种控制没有约束的最优设计问题仍有实际意义。比如，当受控对象偏离预定状态很小时，用来修正这个偏差的控制量往往也很小，在这种情况下，可以认为控制量不受任何约束。

在控制不受约束的情况下，可用变分法求出最优控制。

设给定系统的运动方程为

$$
\frac {\partial u (t , x)}{\partial t} = f \left[ t, x, u \frac {\partial^ {2} u}{\partial x ^ {2}}, F (t, x) \right], \quad 0 <   x <   l \tag {12.8-1}
$$

边界条件是

$$
u (t, 0) = 0, \quad u (t, l) = 0 \tag {12.8-2}
$$

初始条件为

$$
u (0, x) = \varphi (x) \tag {12.8-3}
$$

其中 $F(t, x)$ 是系统的控制。

系统的积分指标是

$$
J [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} Q \left[ t, x, u, \frac {\partial u}{\partial x}, F \right] d x d t \tag {12.8-4}
$$

式中 T 是给定的正常数。

我们的目的是找出控制规律 $F(t, x)$ ，它使受控对象在 $t = T$ 时刻到达状态 $u(T, x) = u^{*}(x), u^{*}(x)$ 是事先给定的状态，同时使性能指标 $J$ 达到极小。这里对控制 $F(t, x)$ 不加约束，只要求它是 $x$ 和 $t$ 的连续函数。假定 $f, Q$ 分别对各自的自变量有一至二阶连续偏导数。设使指标 $J$ 达到极小的最优控制存在，记为 $\mathring{F}(t, x)$ ，而相应的最优轨迹记为 $\mathring{u}(t, x)$ 。现对控制 $\mathring{F}(t, x)$ 作一个微小变动（控制变分），

$$
F (t, x) = F (t, x) + \delta F (t, x) \tag {12.8-5}
$$

这时，在 $F(t, x)$ 的作用下，受控对象的运动也发生相应变化，

$$
u (t, x) = \mathring {u} (t, x) + \delta u (t, x) \tag {12.8-6}
$$

控制的变分 $\delta F(t,x) = F(t,x) - F(t,x)$ 引起了受控对象运动的变分， $\delta u(t,x) = u(t,x) - u(t,x)$ ，它们是通过方程(12.8-1)联系起来的。使 $J$ 达到极小的控制 $\dot{F}(t,x)$ 是 $J$ 在方程(12.8-1)约束下的条件极值问题。根据变分学中拉格朗日乘子法，可以把这个条件极值变成无条件极值问题。令

$$
R = Q \left[ t, x, u, \frac {\partial u}{\partial x}, F \right] + \psi (x, t) \left[ f \left[ t, x, u, \frac {\partial^ {2} u}{\partial x ^ {2}}, F \right] - \frac {\partial u}{\partial t} \right] \tag {12.8-7}
$$

其中 $\psi(x,t)$ 是拉格朗日乘子, 是待定的未知函数。这样, 寻求最优控制 $F(t,x)$ 的问题, 就变成了使

$$
I [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} R d t d x \tag {12.8-8}
$$

取极小的无条件极值问题。

记 $\frac{\partial u}{\partial x} = \dot{u}_x, \frac{\partial^2 u}{\partial x^2} = \ddot{u}_{xx}, \frac{\partial u}{\partial t} = \dot{u}_t$ ，而 $\delta \dot{u}_x, \delta \ddot{u}_{xx}, \delta \dot{u}_t$ ，分别表示 $\dot{u}_x, \ddot{u}_{xx}, \dot{u}_t$ 的变分。略去高阶小量，指标 $I[F(t,x)]$ 的变分为

$$
\begin{array}{l} \delta I [ F (t, x) ] = I [ F (t, x) ] - I [ \stackrel {\circ} {F} (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} (R - \stackrel {\circ} {R}) d t d x \\ = \int_ {0} ^ {T} \int_ {0} ^ {l} \left\{Q \left[ t, x, u, \frac {\partial u}{\partial x}, F \right] + \psi (x, t) \left[ f \left[ t, x, u, \frac {\partial^ {2} u}{\partial x ^ {2}}, F \right] - \frac {\partial u}{\partial t} \right] \right. \\ - Q \left[ t, x, \dot {u}, \frac {\partial \dot {u}}{\partial x}, \stackrel {\circ} {F} \right] - \psi (x, t) \left[ f \left[ t, x, \dot {u}, \frac {\partial^ {2} \dot {u}}{\partial x ^ {2}}, \stackrel {\circ} {F} \right] - \frac {\partial \dot {u}}{\partial t} \right] \rbrace d t d x \\ = \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial u} \delta u + \frac {\partial Q}{\partial \dot {u} _ {x}} \delta \dot {u} _ {x} + \frac {\partial Q}{\partial F} \delta F + \psi (x, t) \frac {\partial f}{\partial u} \delta u \right. \\ \left. + \psi (x, t) \frac {\partial f}{\partial \dot {u} _ {x x}} \delta \ddot {u} _ {x x} + \psi (x, t) \frac {\partial f}{\partial F} \delta F - \psi (x, t) \delta \dot {u} _ {t} \right] d t d x \\ = \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial u} \delta u + \psi (x, t) \frac {\partial f}{\partial u} \delta u + \frac {\partial Q}{\partial \dot {u} _ {x}} \delta \dot {u} _ {x} + \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \delta \ddot {u} _ {x x} \right. \\ \end{array}
$$

$$
- \psi (x, t) \delta \dot {u} _ {t} ] d t d x + \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial F} \delta F + \psi (x, t) \frac {\partial f}{\partial F} \delta F \right] d t d x \tag {12.8-9}
$$

式中 $Q$ 和 $f$ 的各阶偏导数都在点 $\left[ t, x, \mathring{u}(t, x), \frac{\partial \mathring{u}(t, x)}{\partial x}, \mathring{F}(t, x) \right]$ 上取值。因为

$$
\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \delta \ddot {u} _ {x x} = \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \delta \dot {u} _ {x} \right] - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \delta \dot {u} _ {x}
$$

所以有

$$
\begin{array}{l} \int_ {0} ^ {T} \int_ {0} ^ {l} \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \delta \ddot {u} _ {x x} d t d x = - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \delta \dot {u} _ {x} d t d x \\ + \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \dot {u} _ {x x}} \delta \dot {u} _ {x} \right] d t d x \\ = - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \delta \dot {u} _ {x} d t d x \\ + \int_ {0} ^ {T} \psi (x, t) \left. \frac {\partial f}{\partial \dot {u} _ {x x}} \delta \dot {u} _ {x} \right| _ {0} ^ {l} d t \\ \end{array}
$$

若令

$$
\psi (0, t) = 0, \quad \psi (l, t) = 0 \tag {12.8-10}
$$

则有

$$
\int_ {0} ^ {T} \int_ {0} ^ {l} \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \delta \ddot {u} _ {x x} d t d x = - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \delta \dot {u} _ {x} d t d x \tag {12.8-11}
$$

把式 $(12.8-11)$ 代到式 $(12.8-9)$ ，便得到

$$
\begin{array}{l} \delta I [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} \left\{\frac {\partial Q}{\partial u} \delta u + \psi (x, t) \frac {\partial f}{\partial u} \delta u + \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] \delta \dot {u} _ {x} \right. \\ \left. - \psi (x, t) \delta \dot {u} _ {t} \right\} d t d x + \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} \right] \delta F d t d x \tag {12.8-12} \\ \end{array}
$$

另一方面，由于

$$
\begin{array}{l} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left(\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}}\right) \right] \delta \dot {u} _ {x} = \frac {\partial}{\partial x} \left\{\left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left(\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}}\right) \right] \delta u \right\} \\ - \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] \delta u \\ \end{array}
$$

从而有

$$
\begin{array}{l} \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left(\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}}\right) \right] \delta \dot {u} _ {x} d t d x \\ = - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] \delta u d t d x \\ \end{array}
$$

$$
+ \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left\{\left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left(\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}}\right) \right] \delta u \right\} d t d x
$$

$$
= - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] \delta u d t d x
$$

$$
+ \int_ {0} ^ {T} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left(\psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}}\right) \delta u \right] \Bigg | _ {0} ^ {l} d t
$$

$$
= - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] \delta u d t d x
$$

其中第二项积分为零, 是因为边界条件是固定的, 所以 $\delta u(t, x) \mid_{x=0} = 0, \delta u(t, x) \mid_{x=l} = 0$ 。把上式代到式(12.8-12)中, 则有

$$
\begin{array}{l} \delta I [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial u} \delta u + \psi (x, t) \frac {\partial f}{\partial u} \delta u \right. \\ - \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \dot {u} _ {x x}} \right] \right] \delta u \\ \left. - \psi (x, t) \delta \dot {u} _ {t} \right] d t d x + \int_ {0} ^ {T} \int_ {0} ^ {t} \left[ \frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} \right] \delta F d t d x \tag {12.8-13} \\ \end{array}
$$

此外

$$
\begin{array}{l} \int_ {0} ^ {T} \int_ {0} ^ {l} \psi (x, t) \delta \dot {u} _ {t} d t d x = \int_ {0} ^ {l} [ \psi (x, t) \delta u ] \Bigg | _ {0} ^ {T} d x - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial \psi (x , t)}{\partial t} \delta u d t d x \\ = - \int_ {0} ^ {T} \int_ {0} ^ {l} \frac {\partial \psi (x , t)}{\partial t} \delta u d t d x \tag {12.8-14} \\ \end{array}
$$

其中第一项积分为零, 是因为 $\delta u(t, x) \mid_{t=0} = 0, \delta u(t, x) \mid_{t=T} = 0$ (初始条件和终端条件是固定不动的)。

将式 $(12.8-14)$ 代到式 $(12.8-13)$ 中，便得到

$$
\begin{array}{l} \delta I [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial u} + \psi (x, t) \frac {\partial f}{\partial u} - \frac {\partial}{\partial x} \right] \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} \right. \\ \left. - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right]\right) + \frac {\partial \psi (x , t)}{\partial t} \Bigg ] \delta u d t d x \\ + \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} \right] \delta F d t d x \tag {12.8-15} \\ \end{array}
$$

我们这样选择 $\psi (x,t)$ ，使它满足方程

$$
\frac {\partial \psi (x , t)}{\partial t} = \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] - \psi (x, t) \frac {\partial f}{\partial u} - \frac {\partial Q}{\partial u} \tag {12.8-16}
$$

及边界条件式(12.8-10)。于是式(12.8-15)的第一项为零，而

$$
\delta I [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} \right] \delta F d t d x \tag {12.8-17}
$$

当 $F(t,x)$ 是最优控制， $\dot{u}(t,x)$ 是对应的系统的最优轨迹时，应有 $\delta I[F(t,x)] = 0$ ，于是得到

$$
\int_ {0} ^ {T} \int_ {0} ^ {l} \left[ \frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} \right] \delta F d t d x = 0 \tag {12.8-18}
$$

由于控制 F 不受拘束, $\delta F$ 可以任意选择, 式(12.8-18)只有当

$$
\frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} = 0 \tag {12.8-19}
$$

才能得到满足。这个方程就是使 J 达到极小的最优控制所应满足的必要条件。

我们把方程 $(12.8-1)$ ， $(12.8-16)$ ， $(12.8-19)$ 以及边界条件和初始条件 $(12.8-2)$ ， $(12.8-3)$ ， $(12.8-10)$ 写在一起，构成一组联立方程式

$$
\frac {\partial u}{\partial t} = f \left[ t, x, u, \frac {\partial^ {2} u}{\partial x ^ {2}}, F \right]
$$

$$
u (t, 0) = 0, \quad u (t, l) = 0
$$

$$
u (0, x) = \varphi (x), \quad u (T, x) = u ^ {*} (x)
$$

$$
\frac {\partial \psi (x , t)}{\partial t} = \frac {\partial}{\partial x} \left[ \frac {\partial Q}{\partial \dot {u} _ {x}} - \frac {\partial}{\partial x} \left[ \psi (x, t) \frac {\partial f}{\partial \ddot {u} _ {x x}} \right] \right] - \psi (x, t) \frac {\partial f}{\partial u} - \frac {\partial Q}{\partial u}
$$

$$
\psi (0, t) = 0, \quad \psi (l, t) = 0
$$

$$
\frac {\partial Q}{\partial F} + \psi (x, t) \frac {\partial f}{\partial F} = 0 \tag {12.8-20}
$$

注意到， $\frac{\partial Q}{\partial F} +\psi (x,t)\frac{\partial f}{\partial F} = \frac{\partial}{\partial F}\big[Q + \psi (x,t)f\big]$ ，如果令 $H = Q + \psi (x,t)f$ ，则有

$$
\frac {\partial H}{\partial F} = 0 \tag {12.8-21}
$$

这就是说，最优控制 $F$ 应使 $H$ 达到极值。由式(12.8-21)解出 $F$ ，它是 $t, x, u, \dot{u}_x$ ， $\ddot{u}_{xx}, \psi$ 的函数，把 $\dot{F}$ 代到方程(12.8-20)中，解出 $u$ 和 $\psi$ ，再代回到 $\dot{F}$ 的表达式中， $\dot{F}$ 就是待求的最优控制。

现在讨论一个例子。设受控对象方程为

$$
\frac {\partial u (t , x)}{\partial t} = a ^ {2} \frac {\partial^ {2} u (t , x)}{\partial x ^ {2}} + F (t, x), \quad 0 <   x <   l
$$

$$
u (t, 0) = 0, \quad u (t, l) = 0
$$

$$
u (0, x) = \varphi (x) \tag {12.8-22}
$$

式中 $u(t,x)$ 是受控量， $F(t,x)$ 是控制量。这是一维热传导问题。 $F(t,x)$ 的物理意义就是单位时间内在单位长度上加入或传出的热量。它是连续取值不受约束的控制量。今要求在给定时间 $T$ 内，使对象由 $t = 0$ 时的温度分布 $u(0,x) = \varphi (x)$ 下降到零度， $u(T,x) = 0$ ，并使性能指标

$$
J [ F (t, x) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} F ^ {2} (t, x) d t d x \tag {12.8-23}
$$

达到极小值。J 代表了在受控过程中, 加入或流出热量的总和。

从问题的物理意义上看，这个最优控制是存在的。另外,J 是一个正定泛函，极小值总是存在的。现按前面说过的方法，找出这个最优控制。

方程组(12.8-20)，这时可改写成

$$
\frac {\partial u}{\partial t} = a ^ {2} \frac {\partial^ {2} u}{\partial x ^ {2}} + F (t, x)
$$

$$
u (t, 0) = 0, \quad u (t, l) = 0
$$

$$
u (0, x) = \varphi (x), \quad u (T, x) = 0
$$

$$
\frac {\partial \psi}{\partial t} = - a ^ {2} \frac {\partial^ {2} \psi}{\partial x ^ {2}}
$$

$$
\psi (0, t) = 0, \quad \psi (l, t) = 0
$$

$$
2 F (t, x) + \psi (x, t) = 0 \tag {12.8-24}
$$

由式(12.8-24)可得

$$
F (t, x) = - \frac {1}{2} \psi (x, t)
$$

代到第一个方程后得

$$
\frac {\partial u}{\partial t} = a ^ {2} \frac {\partial^ {2} u}{\partial x ^ {2}} - \frac {1}{2} \psi (x, t) \tag {12.8-25}
$$

应用分离变量法可以求得 $\psi(x,t)$

$$
\psi (x, t) = \sum_ {n = 1} ^ {\infty} c _ {n} e ^ {\left(\frac {n \pi}{l}\right) ^ {2} a ^ {2} t} \sin \frac {n \pi}{l} x \tag {12.8-26}
$$

式中 $c_{n}, n=1,2,\cdots$ 是待定常数。将式(12.8-26)代到式(12.8-25)中

$$
\frac {\partial u}{\partial t} = a ^ {2} \frac {\partial^ {2} u}{\partial x ^ {2}} - \frac {1}{2} \sum_ {n = 1} ^ {\infty} c _ {n} e ^ {\left(\frac {n \pi}{T}\right) ^ {2} a ^ {2} t} \sin \frac {n \pi}{l} x \tag {12.8-27}
$$

同样用分离变量法求解式(12.8-27)，得到

$$
u (t, x) = \sum_ {n = 1} ^ {\infty} b _ {n} e ^ {- a ^ {2} \left(\frac {n \pi}{l}\right) ^ {2} t} \sin \frac {n \pi}{l} x - \sum_ {n = 1} ^ {\infty} \frac {c _ {n} l ^ {2}}{2 a ^ {2} n ^ {2} \pi^ {2}} \mathrm{sh} a ^ {2} \left[ \frac {n \pi}{l} \right] ^ {2} t \cdot \sin \frac {n \pi}{l} x \tag {12.8-28}
$$

利用边界条件和初始条件可以确定出 $b_{n}, c_{n}, n = 1, 2, \cdots$ 。由 $u(0, x) = \varphi(x) = \sum_{n=1}^{\infty} b_{n} \sin \frac{n\pi}{l} x, n = 1, 2, \cdots$ 得到

$$
b _ {n} = \frac {2}{l} \int_ {0} ^ {l} \varphi (x) \sin \frac {n \pi}{l} x d x, \quad n = 1, 2, \dots \tag {12.8-29}
$$

再由 $u(T, x)=0$ 得到

$$
u (T, x) = 0 = \sum_ {n = 1} ^ {\infty} b _ {n} e ^ {- a ^ {2} \left(\frac {n \pi}{l}\right) ^ {2} T} \sin \frac {n \pi}{l} x - \sum_ {n = 1} ^ {\infty} \frac {c _ {n} l ^ {2}}{2 a ^ {2} n ^ {2} \pi^ {2}} \mathrm{sh} a ^ {2} \left(\frac {n \pi}{l}\right) ^ {2} T \cdot \sin \frac {n \pi}{l} x
$$

由此推得

$$
c _ {n} = \frac {e ^ {- a ^ {2} \left(\frac {n \pi}{l}\right) ^ {2} T}}{\operatorname{sh} a ^ {2} \left[ \frac {n \pi}{l} \right] ^ {2} T} \frac {2 a ^ {2} n ^ {2} \pi^ {2} b _ {n}}{l ^ {2}}, \quad n = 1, 2, \dots \tag {12.8-30}
$$

得到 $\psi(x,t)$ 以后，便可以最后求出最优控制 $F(t,x)$

$$
\stackrel {\circ} {F} (t, x) = - \frac {1}{2} \psi (x, t) = - \sum_ {n = 1} ^ {\infty} \frac {e ^ {- a ^ {2} \left(\frac {n \pi}{l}\right) ^ {2} T}}{\operatorname{sh} a ^ {2} \left[ \frac {n \pi}{l} \right] ^ {2} T} \frac {a ^ {2} n ^ {2} \pi^ {2} b _ {n}}{l ^ {2}} e ^ {\left[ \frac {n \pi}{l} \right] ^ {2} a ^ {2} t} \sin \frac {n \pi}{l} x \tag {12.8-31}
$$

这是开环分布最优控制。

#### 12.9 分布参数系统最优控制

在上一节中，我们讨论了控制为时间的连续函数，并且是在没有约束情况下的最优控制问题。但在工程技术中，经常遇到的分布参数系统，其控制并不总是连续的（比如系统中含有继电元件时）。特别是由于技术实现上的限制，控制通常是有约束的。例如第 12.2 节例 1 中受控的弹性圆柱体，控制是加在 $x = 0$ 处的外力矩，这个力矩由于电动机功率上的限制其大小也要受到限制。同样，在例 2 中，受控对象是金属板，控制作用是在一端人为改变的温度。这个温度也只能在有限范围内变化。对这类控制有约束的问题，上一节的结论不能应用。而且由于控制有约束，古典变分法不能用来解决这类问题。比如上节的式(12.8-18)中，由于控制受到约束， $\delta F$ 就不能任意选取，因而也就推不出式(12.8-19)。

对于控制有约束的分布参数系统的最优控制问题，近年来有大量的研究工作 $^{[26,33,39]}$ 。在这一节里，主要介绍这方面的基本思想和方法。

首先讨论用式(12.3-9)描述的分布参数系统最优控制问题。设系统状态方程为

$$
\frac {\partial \boldsymbol {U} (t , x)}{\partial t} = \boldsymbol {L} (\boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})), \quad \boldsymbol {x} \in \Omega \tag {12.9-1}
$$

式中 $U(t,x)=(u_{1}(t,x),u_{2}(t,x),\cdots,u_{n}(t,x))$ 是系统的状态向量。对固定的 t, $u_{i}(t,x)\in\mathfrak{H}, i=1,2,\cdots,n,\mathfrak{H}$ 是希尔伯特空间，于是系统的状态空间 $\mathfrak{H}=\mathfrak{H}\times\mathfrak{H}\times\cdots\times\mathfrak{H}$ 仍是希尔伯特空间； $f_{\Omega}(t,x)=(f_{\Omega}^{1}(t,x),f_{\Omega}^{2}(t,x),\cdots,f_{\Omega}^{r}(t,x))$ 是系统的控制向量，它满足给定的约束条件。满足约束条件的控制向量的全体，叫做可准控制类，记成 $\mathcal{A}[0,\infty)\times\Omega)$ 。如果指定 t 的变化区间为 $[t_{0},t_{1}]$ ，则可准控制类记成 $\mathcal{A}[t_{0},t_{1}]\times\Omega)$ 。 $L(U(t,x),f_{\Omega}(t,x))=(L_{1}(U(t,x),f_{\Omega}(t,x)),\cdots,L_{m}(U(t,x),f_{\Omega}(t,x))),L_{i}(U(t,x),f_{\Omega}(t,x)),i=1,2,\cdots,n$ 是把 $\mathfrak{H}\times\mathcal{A}[0,\infty)\times\Omega)$ 映 到 $\mathfrak{H}$ 的微分算子。整个系统式(12.9-1)是一偏微分方程组，它能描述相当广泛的分布参数系统。

系统式(12.9-1)的边界条件是用下述向量方程给定的

$$
\boldsymbol {M} \left(\boldsymbol {U} \left(t, \boldsymbol {x} ^ {\prime}\right), \boldsymbol {f} _ {\partial \Omega} \left(t, \boldsymbol {x} ^ {\prime}\right)\right) = 0, \quad \boldsymbol {x} ^ {\prime} \in \partial \Omega \tag {12.9-2}
$$

式中 $M=(M_{1},M_{2},\cdots,M_{N})$ , $M_{i}(U(t,x^{\prime}),f_{\partial\Omega}(t,x^{\prime}))$ , $i=1,2,\cdots,N$ 是边界条件微分算子，它依实际问题的物理意义而确定； $f_{\partial\Omega}(t,x^{\prime})=(f_{\partial\Omega}^{1}(t,x^{\prime}),f_{\partial\Omega}^{2}(t,x^{\prime}),\cdots,f_{\partial\Omega}^{s}(t,x^{\prime}))$ 是边界控制向量，它同样满足一定约束条件，满足约束条件的边界控制的全体，叫做可准边界控制类，记成 $\mathcal{K}([0,\infty)\times\partial\Omega)$ 。当指定 t 的变化区间 $[t_{0},t_{1}]$ 后，可准边界控制类记成 $\mathcal{K}([t_{0},t_{1}]\times\partial\Omega)$ 。

系统的初始条件是

$$
\boldsymbol {U} (t, \boldsymbol {x}) \mid_ {t = t _ {0}} = \boldsymbol {U} _ {0} (\boldsymbol {x}), \quad \boldsymbol {x} \in \Omega \tag {12.9-3}
$$

$U_{0}(x)$ 是 $\xi$ 中的元。

为了今后讨论上的方便，把 $\Omega$ 上的可准控制 $f_{\Omega}(t, x)$ 和边界 $\partial \Omega$ 上的可准控制 $f_{\partial \Omega}(t, x')$ 的全体记成 $\mathcal{A}([0, \infty) \times \overline{\Omega}), \overline{\Omega} = \Omega \cup \partial \Omega$ 。给定 $f_{\Omega}(t, x) \in \mathcal{F}([0, \infty) \times \overline{\Omega})$ ，意味着在 $\Omega$ 和 $\partial \Omega$ 上的控制都已给定。当指定 $t$ 的变化区间 $[t_0, t_1]$ 后，这个可准控制类记成 $\mathcal{A}[t_0, t_1] \times \overline{\Omega})$ 。

加在控制 $f_{\overline{\Omega}}(t,x)$ 上的约束条件, 是由系统的实际结构和技术实现上的限制而确定的。例如, 控制量的幅值约束, 可以写成

$$
\mid f _ {\Omega} ^ {i} (t, \boldsymbol {x}) \mid \leqslant g _ {i}, \quad i = 1, 2, \dots , r \tag {12.9-4}
$$

$g_{i}>0$ , 它可以是常值, 也可以是 t 或者 x 的已知函数。

在有的问题中，对控制量的变化速度要加以限制，例如

$$
\left| \frac {\partial f _ {\overline {{{\Omega}}}} ^ {i} (t , \boldsymbol {x})}{\partial t} \right| \leqslant A _ {i}, \quad i = 1, 2, \dots , r \tag {12.9-5}
$$

式中 $A_{i} \geqslant 0$ 。

在一般情况下，控制约束条件可以写成

$$
d _ {i} = Q _ {i} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), f _ {\Omega} (t, \boldsymbol {x})) \leqslant g _ {i}, \quad i = 1, 2, \dots , l \tag {12.9-6}
$$

$Q_{i}$ 是 $U(t, x), f_{\Omega}(t, x)$ 的泛函， $g_{i}, d_{i}$ 是常数，也可以是 t 或者 x 的已知函数。例如，积分不等式约束

$$
\int_ {t _ {0}} ^ {t _ {1}} \int_ {\overline {{{\Omega}}}} q _ {i} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\overline {{{\Omega}}}} (t, \boldsymbol {x})) d t d \Omega \leqslant g _ {i}, \quad i = 1, 2, \dots , l \tag {12.9-7}
$$

$g_{i}$ 是已知常数。在这种约束形式中，不仅对控制 $f_{\overline{\Omega}}(t, x)$ 有约束，而且对系统状态 $U(t, x)$ 也有约束。

对可准控制类 $\mathcal{F}([0,\infty)\times \overline{\Omega})$ 中任意控制 $f_{\Omega}(t,x)$ ，给定初始条件和边界条件以后，我们总假定系统存在唯一的解，而且这个解连续依赖于初值，也就是说，初值的微小变化，对应解的变化也很小。

系统状态演化用算子 $\Phi(t, x, U_0(x), T_0, f_{\overline{\Omega}}(t, x))$ 表示，即系统式(12.9-1)和边界条件式(12.9-2)，在给定初值 $U_0(x)$ 和可准控制 $f_{\overline{\Omega}}(t, x)$ 后，系统在 $t$ 时刻所到达的状态 $U(t, x) = \Phi(t, x, U_0(x), t_0, f_{\overline{\Omega}}(t, x))$ ，今后把 $U(t, x)$ 写成 $U_{f_{\overline{\Omega}}} (t, x, U_0(x), t_0), U_{f_{\overline{\Omega}}} (t, x, U_0(x), t_0) = \Phi(t, x, U_0(x), t_0, f_{\overline{\Omega}}(t, x))$ 。如果系统式(12.9-1)是线性系统，且 $L$ 是中强连续有界算子半群的生成算子，这时 $\Phi$ 可用半群表示出来，如式(12.7-2)的形式。

在有控制作用 $f_{\bar{\Omega}}(t,x)$ 的情况下，系统运动是强迫运动，如果 $f_{\bar{\Omega}}(t,x)\equiv0$ ，则是自由运动。特别当 $\frac{\partial U}{\partial t}\equiv0, f_{\bar{\Omega}}\equiv0$ ，即 $L(U(t,x),t,x)=0, M(U(t,x'))=0$ 时的解叫做系统的平衡态或稳态。

系统的性能指标，可用一个泛函来表示

$$
\begin{array}{l} J = \int_ {\overline {{{\Omega}}}} g ^ {0} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\overline {{{\Omega}}}}} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0})) d \overline {{{\Omega}}} \\ + \int_ {t _ {0}} ^ {t _ {1}} \int_ {\overline {{{\Omega}}}} g ^ {1} (t, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\overline {{{\Omega}}}}} (t, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}), \boldsymbol {f} _ {\overline {{{\Omega}}}} (t, \boldsymbol {x})) d t d \overline {{{\Omega}}} \tag {12.9-8} \\ \end{array}
$$

右端第一项代表终端 $t_1$ 时的指标要求，第二项代表在整个 $[t_0, t_1]$ 过程上的指标要求。各种不同的最优控制问题的性能指标常能表示成式(12.9-8)的形式。

系统的终端状态，可以是自由的，也可以是固定的。在后一种情况下，它是 $\mathfrak{H}$ 中的一个子集。用 $\mathfrak{H}_{l}$ 表示, $\mathfrak{H}_{l}\subset\mathfrak{H},\mathfrak{H}_{l}$ 也叫目标集。

现在，可以把控制有约束的最优控制问题叙述如下:

对系统式(12.9-1)，给定边界条件式(12.7-2)和初值 $U_{0}(x)$ 以后，要求找到一个可准控制 $f_{\Omega}(t,x)\in\mathcal{F}([t_{0},t_{1}]\times\overline{\Omega})$ ，使系统从 $U_{0}(x)$ 出发的运动 $\dot{U}_{f_{\Omega}}(t,x,U_{0}(x),t_{0})$ 在 $t_{1}$ 时刻到达目标集 $\tilde{S}_{t}^{j}$ ，并使得 J 对所有其他可准控制来说达到极小值（或极大值）。这时 $f_{\Omega}(t,x)$ 叫做最优控制，而 $\dot{U}_{f_{\Omega}}(t,x,U_{0}(x),t_{0})$ 叫做最优轨道。如果最优控制 $f_{\Omega}(t,x)$ 存在，那么这是一种开环控制。假如我们还能找到最优控制 $f_{\Omega}(t,x)$ 和系统状态 $U(t,x)$ 的关系，即 $f_{\Omega}(t,x)=F(U(t,x))$ ，这时最优控制是系统状态的反馈，因此是闭环最优控制。

以上是分布参数系统最优控制的一般提法，当给定性能指标的具体形式后，就可描述各种特殊形式的最优控制问题。

（1）最速控制。给定系统式(12.9-1)在 $t = t_0$ 时的初值 $\pmb{U}_0(\pmb{x})$ 和系统的终端值 $\pmb{U}_d(\pmb{x})$ （即目标集 $\hat{\mathfrak{S}}_d = \{\pmb{U}_d(\pmb{x})\}$ 以后，要求找到一个可准控制 $\hat{\pmb{f}}_{\Omega}(t,\pmb {x})$ ，使系统从 $\pmb{U}_0(\pmb{x})$ 出发到达 $\pmb{U}_d(\pmb{x})$ 的时间最小，这就是最速控制。此时

$$
\begin{array}{l} g _ {0} = 0, \int_ {\overline {{{\Omega}}}} g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\overline {{{\Omega}}}}} (t, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}), \boldsymbol {f} _ {\overline {{{\Omega}}}} (t, \boldsymbol {x})) d \overline {{{\Omega}}} = 1 \\ J = t - t _ {0} \tag {12.9-9} \\ \end{array}
$$

（2）最优终端控制。给定系统式(12.9-1)在 $t_{0}$ 时的初值 $U_{0}(x)$ 和目标集 $\mathfrak{S}_{t}$ ， $t_{1}$ 固定。要求找到一个可准控制 $f_{\Omega}(t,x)$ ，使系统从 $U_{0}(x)$ 出发在 $t_{1}$ 时刻的状态 $U_{f_{\Omega}}(t_{1},x,U_{0}(x),t_{0})$ 和 $\mathfrak{S}_{t}$ 的距离最小，这就是最优终端控制。此时， $g_{1}=0$ ，而 $\int_{\overline{\Omega}}g_{0}(t_{1},x,U_{f_{\Omega}}(t_{1},x,U_{0}(x),t_{0}))d\overline{\Omega}$ 被距离

$$
\begin{array}{l} J = \min _ {f _ {\overline {{\Omega}}} \in \mathcal {I} _ {0} ([ t _ {0}, t _ {1} ] \times \overline {{\Omega}})} \rho (\boldsymbol {U} _ {f _ {\overline {{\Omega}}}} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}), \boldsymbol {\mathfrak {H}} ^ {t}) \\ = \min _ {f _ {\overline {{\Omega}}} \in \mathcal {Z} _ {0} ([ t _ {0}, t _ {1} ] \times \overline {{\Omega}})} \min _ {U _ {d} (\boldsymbol {x}) \in \tilde {\Omega}} \int_ {\Omega} \| \boldsymbol {U} _ {f _ {\overline {{\Omega}}}} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}) - \boldsymbol {U} _ {d} (\boldsymbol {x}) \| ^ {2} d \overline {{\Omega}} \tag {12.9-10} \\ \end{array}
$$

所代替。

（3）最小能量问题。给定系统的初值 $U_{0}(x)$ ， $t_{1}$ 固定，终端状态给定 $U_{d}(x)$ ，要求找到一个可准控制 $f_{\Omega}(t,x)$ ，使系统从 $U_{0}(x)$ 出发，在 $t_{1}$ 时刻到达 $U_{d}(x)$ 并使消耗的控制能量最小。这时 $g_{0}=0$ ， $g_{1}$ 是控制 $f_{\Omega}(t,x)$ 的非负函数，且不依赖于 $U_{f_{\Omega}}(t,x,U_{0}(x),t_{0})$ ，这就是最小能量问题。

以上这些问题，在文献[33]中最先进行了研究，那里应用动态规划方法，得到了最优控制所满足的偏微分-积分方程。这个方程类似于集中参数系统的哈密顿-雅各比(Hamilton-Jacobi)方程。由它可以求出最优控制。下面来讨论这个问题。

给定系统式(12.9-1)，初始条件和边界条件由式(12.9-3)和(12.9-2)确定，但假定边界条件中 $f_{\partial\Omega}(t,x)=0$ ，即不加边界控制，只考虑在 $\Omega$ 上的控制，因此，可准控制类是 $\mathcal{A}[t_{0},t_{1}]\times\Omega$ 。系统性能指标为

$$
\begin{array}{l} J = \int_ {\Omega} g _ {0} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\Omega}} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0})) d \Omega \\ + \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} g ^ {1} (t, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\Omega}} (t, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) d t d \Omega \tag {12.9-11} \\ \end{array}
$$

我们的目的是找到一个可准控制， $f_{\Omega}(t,x)\in\mathcal{A}[t_{0},t_{1}]\times\Omega)$ ，使系统式(12.9-1)在 $t_{0}$ 时刻从状态 $U_{0}(x)$ 出发的运动为 $\dot{U}_{f_{\Omega}}(t,x,U_{0}(x),t_{0})$ ，把它们代到式(12.9-12)中，使 J 达到极小（或极大）值 $\dot{J}$ 。求最优控制 $\dot{f}_{\Omega}(t,x)$ 的实质，就是在有约束条件下，求泛函式(12.9-11)的极值问题。动态规划方法是解决这类问题的有力工具，现应用它去解决上述最优控制问题。

引入记号

$$
\begin{array}{l} \Pi \left(\boldsymbol {U} _ {0} (\boldsymbol {x}), T\right) = \min _ {\boldsymbol {f} _ {\Omega} \in \mathscr {I} \left(\left[ t _ {0}, t _ {1} \right] \times \Omega\right)} J \\ = \min _ {f _ {\Omega} \in \mathcal {I} \left[ t _ {0}, t _ {1} \right] \times \Omega} \left\{\int_ {\Omega} g ^ {0} \left(t _ {1}, x, U _ {f _ {\Omega}} \left(t _ {1}, x, U _ {0} (x), t _ {0}\right)\right) d \Omega \right. \\ \left. + \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} _ {f _ {\Omega}} (t, \boldsymbol {x}, \boldsymbol {U} _ {0} (\boldsymbol {x}), t _ {0}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) d t d \Omega \right\} \tag {12.9-12} \\ \end{array}
$$

其中 $T=t_{1}-t_{0}$

应用动态规划最优原理，可以得到 $^{[33]}$

$$
\begin{array}{l} \frac {\partial \Pi (\boldsymbol {U} _ {0} (t , \boldsymbol {x}) , T)}{\partial T} = \min _ {f _ {\Omega} \in \mathcal {A} [ t _ {0}, t _ {1} ] \times \Omega} \int_ {\Omega} \left\{\left[ \frac {\partial \Pi (\boldsymbol {U} (t , \boldsymbol {x}) , T)}{\partial \boldsymbol {U} (t , x)} \right] ^ {\tau} \boldsymbol {L} (\boldsymbol {U} (T, \boldsymbol {x}), f _ {\Omega} (t, \boldsymbol {x})) \right. \\ \left. + g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) \right\} d \Omega \tag {12.9-13} \\ \end{array}
$$

这是一个偏微分-积分方程，类似于哈密顿-雅各比方程，它的初始条件为

$$
\Pi (\boldsymbol {U} (t _ {1}, \boldsymbol {x}), 0) = \int_ {\Omega} g _ {0} (t _ {1}, \boldsymbol {x}, \boldsymbol {U} (t _ {1}, \boldsymbol {x})) d \Omega \tag {12.9-14}
$$

令

$$
\begin{array}{l} \boldsymbol {p} = \left(p _ {1}, p _ {2}, \dots , p _ {n}, p _ {n + 1}\right) = \left[ \frac {\delta \Pi (\boldsymbol {U} (t , \boldsymbol {x}) , T)}{\delta u _ {1} (t , \boldsymbol {x})}, \dots , \frac {\delta \Pi (\boldsymbol {U} (t , x) , \boldsymbol {T})}{\delta u _ {n} (t , \boldsymbol {x})}, 1 \right] \\ \boldsymbol {q} = \left(q _ {1}, q _ {2}, \dots , q _ {n}, q _ {n + 1}\right) = \left(L _ {1}, L _ {2}, \dots , L _ {n}, g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), f _ {\Omega} (t, \boldsymbol {x}))\right) \\ \end{array}
$$

于是式(12.9-13)的右端可以写成

$$
\begin{array}{l} \int_ {\Omega} \left\{\left[ \frac {\delta \Pi (\boldsymbol {U} (t , \boldsymbol {x}) , T)}{\delta \boldsymbol {U} (t , \boldsymbol {x})} \right] ^ {\tau} L (\boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) + g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) \right\} d \Omega \\ = \int_ {\Omega} \left[ \sum_ {i = 1} ^ {n + 1} p _ {i} q _ {i} \right] d \Omega \\ \end{array}
$$

设

$$
H (\boldsymbol {U}, \boldsymbol {p}, \boldsymbol {f} _ {\Omega}, t) = \int_ {\Omega} \left[ \sum_ {i = 1} ^ {n + 1} p _ {i} q _ {i} \right] d \Omega \tag {12.9-15}
$$

$H(U, p, f_{\Omega}, t)$ 叫做哈密顿量，而 $H_{0} = \sum_{i=1}^{n+1} p_{i} q_{i}$ 叫做哈密顿密度。p 叫做协态变量。
因此，最优控制 $\mathbf{f}_{\Omega}(t,\mathbf{x})$ 是使哈密顿量 H 达到极小的可准控制。记

$$
\stackrel {\circ} {H} (\boldsymbol {U}, \boldsymbol {p}, t) = \min _ {f _ {\Omega} \in \mathcal {A} [ t _ {0}, t _ {1} ] \times \Omega)} H (\boldsymbol {U}, \boldsymbol {p}, f _ {\Omega}, t)
$$

于是方程(12.9-13)变成

$$
\frac {\partial \Pi (\boldsymbol {U} (t , \boldsymbol {x}) , T)}{\partial T} = \stackrel {\circ} {H} (\boldsymbol {U}, \boldsymbol {p}, t)
$$

初始条件是式(12.9-14)。

系统最优轨道是下述哈密顿典型方程的解

$$
\begin{array}{l} \frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = \frac {\delta H (\boldsymbol {U} , \boldsymbol {p} , t)}{\delta p (t , x)} \\ \frac {\partial \boldsymbol {p} (t , \boldsymbol {x})}{\partial t} = - \frac {\delta H (\boldsymbol {U} , \boldsymbol {p} , t)}{\delta \boldsymbol {U} (t , \boldsymbol {x})} \tag {12.9-16} \\ \end{array}
$$

方程组的初始条件为

$$
\boldsymbol {U} (t _ {0}, \boldsymbol {x}) = \boldsymbol {U} _ {0} (\boldsymbol {x})
$$

至于终端条件，如果 $U(t_{1},x)$ 给定，则 $p(t_{1},x)$ 是自由的，如果 $U(t_{1},x)$ 是自由的，那么 $p(t_{1},x)$ 为

$$
\boldsymbol {p} \left(t _ {1}, \boldsymbol {x}\right) = \left[ \frac {\partial g _ {0} \left(t _ {1} , \boldsymbol {x} , \boldsymbol {U} \left(t _ {1} , \boldsymbol {x}\right)\right)}{\partial u _ {1} \left(t _ {1} , \boldsymbol {x}\right)}, \dots , \frac {\partial g _ {0} \left(t _ {1} , \boldsymbol {x} , \boldsymbol {U} \left(t _ {1} , \boldsymbol {x}\right)\right)}{\partial u _ {n} \left(t _ {1} , \boldsymbol {x}\right)}, 1 \right]
$$

于是解方程组(12.9-16)的问题，就变成了两点边值问题。

综合上述，要求出系统式(12.9-1),(12.9-12)的最优控制 $\boldsymbol{f}_{\Omega}(t,\boldsymbol{x})$ ,首先要作哈密顿量 $H(\boldsymbol{U},\boldsymbol{p},\boldsymbol{f}_{\Omega},t)$ ,然后，求出使 H 达到极小的控制 $\boldsymbol{f}_{\Omega}$ ,它是 U,p,t 的函数, $\boldsymbol{f}_{\Omega}=\boldsymbol{f}_{\Omega}(\boldsymbol{U},\boldsymbol{p},t)$ 将 $\boldsymbol{f}_{\Omega}$ 代到 H 中得到 $\dot{H}(\boldsymbol{U},\boldsymbol{p},t)$ ,最后解式(12.9-16)的两点边值问题，得到系统最优轨道 $U(t,\boldsymbol{x})$ 和协态变量 $\boldsymbol{p}(t,\boldsymbol{x})$ ,再将 U,p 代到 $\dot{\boldsymbol{f}}_{\Omega}$ 中，就得到了所要求的最优控制。

作为一个例子，下面求线性常系数系统最小能量问题的最优控制。系统状态方程为

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L \boldsymbol {U} (t, \boldsymbol {x}) + D \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x}) \tag {12.9-17}
$$

$U=(u_{1},u_{2},\cdots,u_{n}),f_{\Omega}=(f_{1},\cdots,f_{r}),L$ 是 $n\times n$ 阶矩阵线性微分算子，D 是 $n\times r$ 阶常值矩阵。

系统的初始条件为

$$
\boldsymbol {U} (t, \boldsymbol {x}) \mid_ {t = t _ {0}} = \boldsymbol {U} _ {0} (\boldsymbol {x}) \tag {12.9-18}
$$

终端条件是

$$
\boldsymbol {U} (t, \boldsymbol {x}) \mid_ {t = t _ {1}} = 0 \tag {12.9-19}
$$

性能指标为

$$
\boldsymbol {J} = \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} \boldsymbol {f} _ {\Omega} ^ {\tau} \boldsymbol {f} _ {\Omega} d t d \Omega \tag {12.9-20}
$$

要求找到一个可准控制 $f_{\Omega}(t,x)$ ，使系统式(12.9-17)从 $U_{0}(x)$ 出发在 $t_{1}$ 时刻到达原点而消耗的控制能量最小。

应用前述的结果，注意到这里 $g_{0}=0$ , $g_{1}=f_{\Omega}^{x}f_{\Omega}$ , 因此相应于方程(12.9-13), 有

$$
\frac {\partial \Pi (\boldsymbol {U} (t , \boldsymbol {x}) , T)}{\partial T} = \min _ {f _ {\Omega} \in \mathcal {R} [ t _ {0}, t _ {1} ] \times \Omega} \int_ {\Omega} \left\{\left[ \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] ^ {\tau} [ L \boldsymbol {U} + D \boldsymbol {f} _ {\Omega} ] + \boldsymbol {f} _ {\Omega} ^ {x} \boldsymbol {f} _ {\Omega} \right\} d \Omega \tag {12.9-21}
$$

由于 $f_{\Omega}$ 没有任何约束, 故使式(12.9-21)取极小的 $f_{\Omega}$ 为

$$
\mathbf {\dot {f}} _ {\Omega} = - \frac {1}{2} D ^ {\tau} \frac {\delta \Pi}{\delta \boldsymbol {U}}
$$

由此

$$
\begin{array}{l} \stackrel {\circ} {H} = \int_ {\Omega} \left\{\left[ \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] ^ {\tau} \left[ L \boldsymbol {U} - \frac {1}{2} D D ^ {\tau} \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] + \frac {1}{4} \left[ \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] ^ {\tau} D D ^ {\tau} \left[ \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] \right\} d \Omega \\ = \int_ {\Omega} \left[ \frac {\delta \Pi}{\delta \boldsymbol {U}} \right] ^ {\tau} \left[ L \boldsymbol {U} - \frac {1}{4} D D ^ {\tau} \left(\frac {\delta \Pi}{\delta \boldsymbol {U}}\right) \right] d \Omega \tag {12.9-22} \\ \end{array}
$$

令

$$
\boldsymbol {p} = \frac {\delta \Pi}{\delta \boldsymbol {U}} = (p _ {1}, p _ {2}, \dots , p _ {n})
$$

$$
\boldsymbol {q} = L \boldsymbol {U} = (q _ {1}, q _ {2}, \dots , q _ {n})
$$

哈密顿典型方程为

$$
\frac {\partial \boldsymbol {U} (t , \boldsymbol {x})}{\partial t} = L \boldsymbol {U} (t, \boldsymbol {x}) - \frac {1}{2} D D ^ {\tau} \boldsymbol {p} (t, \boldsymbol {x})
$$

$$
\frac {\partial \boldsymbol {p} (t , \boldsymbol {x})}{\partial t} = - L ^ {*} \boldsymbol {p} (t, \boldsymbol {x}) \tag {12.9-23}
$$

式中 $L^{*}$ 是 L 的伴随算子。

假定 $L$ 是 $\mathfrak{H}$ 中有界算子半群 $T(t)$ 的生成算子, 则式(12.9-23)第一个方程的解是

$$
\boldsymbol {U} (t, \boldsymbol {x}) = T (t) \boldsymbol {U} _ {0} (\boldsymbol {x}) - \frac {1}{2} \int_ {t _ {0}} ^ {t} T (t - s) D D ^ {\tau} \boldsymbol {p} (s, \boldsymbol {x}) d s
$$

第二个方程的解为

$$
\boldsymbol {p} (t, \boldsymbol {x}) = T ^ {*} (t) \boldsymbol {p} _ {0} (\boldsymbol {x})
$$

这里 $\boldsymbol{p}_{0}(\boldsymbol{x})$ 是 $\boldsymbol{p}(t,\boldsymbol{x})$ 的待求初值。

把它代到 $U(t, x)$ 的表达式中, 就有

$$
\begin{array}{l} \boldsymbol {U} (t, \boldsymbol {x}) = T (t) \boldsymbol {U} _ {0} (\boldsymbol {x}) - \frac {1}{2} \int_ {t _ {0}} ^ {t} T (t - s) D D ^ {\tau} T ^ {*} (s) \boldsymbol {p} _ {0} (\boldsymbol {x}) d s \\ = T (t) \boldsymbol {U} _ {0} (\boldsymbol {x}) - \frac {1}{2} \int_ {t _ {0}} ^ {t} T (t - s) D D ^ {\tau} T ^ {*} (s) d s \boldsymbol {p} _ {0} (\boldsymbol {x}) \\ \end{array}
$$

再利用终端条件 $U(t_{1}, x)=0$ ，又有

$$
2 T (t _ {1}) \boldsymbol {U} _ {0} = \int_ {t _ {0}} ^ {t _ {1}} T (t _ {1} - s) D D ^ {\tau} T ^ {*} (s) d s \boldsymbol {p} _ {0} (\boldsymbol {x})
$$

令 $S = \int_{t_0}^{t_1} T(t_1 - s) DD^\tau T^*(s) ds$ ，并假定 $S$ 有逆，则有

$$
\boldsymbol {p} _ {0} (\boldsymbol {x}) = 2 S ^ {- 1} T (t _ {1}) \boldsymbol {U} _ {0} (\boldsymbol {x})
$$

这样，协态变量就为

$$
\boldsymbol {p} (t, \boldsymbol {x}) = 2 T ^ {*} (t) S ^ {- 1} T (t _ {1}) \boldsymbol {U} _ {0} (\boldsymbol {x})
$$

将它代到最优控制表达式中，便得到

$$
\mathbf {\dot {f}} _ {\Omega} = - D ^ {\tau} T ^ {*} (t) S ^ {- 1} T \left(t _ {1}\right) \mathbf {U} _ {0} (\boldsymbol {x}) \tag {12.9-24}
$$

这是闭环最优控制。

以上我们讨论了用偏微分方程描述的分布参数系统的最优控制问题。在有些情况下，分布参数系统可以用积分方程或积分方程组来描述，它对讨论系统的最优控制问题有时比较方便。而且这种描述方式还有一个好处，就是系统的边界条件已包含在积分方程的表达式中。

一般来说，一个高阶方程或偏微分方程组描述的分布参数系统，如果能求出它的格林函数，就都可化成积分方程或方程组的形式。

在一般情况下，用积分方程组描述的分布参数系统，可以表达为

$$
\begin{array}{l} \boldsymbol {U} (t, \boldsymbol {x}) = \int_ {\Omega} \boldsymbol {K} _ {0} (t, t _ {0}, \boldsymbol {x}, \boldsymbol {x} ^ {\prime}, \boldsymbol {U} _ {0} (\boldsymbol {x} ^ {\prime})) d \Omega^ {\prime} \\ + \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} \boldsymbol {K} (t, t ^ {\prime}, \boldsymbol {x}, \boldsymbol {x} ^ {\prime}, \boldsymbol {U} (t ^ {\prime}, \boldsymbol {x} ^ {\prime}), \boldsymbol {f} _ {\Omega} (t ^ {\prime}, \boldsymbol {x} ^ {\prime})) d t ^ {\prime} d \Omega^ {\prime} \tag {12.9-25} \\ \end{array}
$$

式中 $K_{0}$ ，K 是 n 维向量函数， $U=(u_{1}, u_{2}, \cdots, u_{n})$ ， $f_{\Omega}=(f_{\Omega}^{1}, \cdots, f_{\Omega}^{r})$ 分别是系统的状态向量和控制向量。 $K_{0}$ 应具有如下性质

$$
\int_ {\Omega} \boldsymbol {K} _ {0} \left(t _ {0}, t _ {0}, \boldsymbol {x}, \boldsymbol {x} ^ {\prime}, \boldsymbol {U} _ {0} \left(\boldsymbol {x} ^ {\prime}\right)\right) d \Omega^ {\prime} = \boldsymbol {U} _ {0} (\boldsymbol {x})
$$

$U_{0}(x)$ 是系统的初值。下面将假定， $K_{0}, K_{1}$ 是定义在 $[t_{0}, t_{1}] \times \Omega$ 上的平方可积函数，且相对于 $U(t, x)$ 的分量 $u_{i}, i=1,2,\cdots,n$ 有连续一阶偏导数。不失一般性，还假定 $U_{0}(x)=0$ 。

系统式(12.9-25)的约束条件是

$$
\mathcal {Z} _ {i} \big [ \zeta (\boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\Omega} (t, \boldsymbol {x})) \big ] = 0, \quad i = 1, 2, \dots , N \tag {12.9-26}
$$

这里 Z 是泛函, 而 $\zeta$ 为向量

$$
\zeta = \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} \boldsymbol {z} (t ^ {\prime}, \boldsymbol {x} ^ {\prime}, \boldsymbol {U} (t ^ {\prime}, \boldsymbol {x} ^ {\prime}) \boldsymbol {f} _ {\Omega} (t ^ {\prime}, \boldsymbol {x} ^ {\prime})) d t ^ {\prime} d \Omega^ {\prime} \tag {12.9-27}
$$

z 是向量， $z=(z_{1},z_{2},\cdots,z_{l})$ ，这里假定 $Z_{i}$ 对 $\zeta$ 和 $z_{i}$ 对 U 都有一阶连续偏导数。这种类型的约束条件，不仅对控制 $f_{n}$ 有约束，而且对系统状态 U 也有约束。满足约束条件式(12.9-26)和(12.9-27)的可准控制类记成 $\mathcal{A}[t_{0},t_{1}]\times\overline{\Omega}$ 。

设系统性能指标有下列形式

$$
\boldsymbol {J} = \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), f _ {\Omega} (t, \boldsymbol {x})) d t d \Omega \tag {12.9-28}
$$

系统式(12.9-25)的最优控制问题，就是要求找到一可准控制 $f_{\bar{n}}(t,x)\in\mathcal{F}([t_{0},t_{1}]\times\overline{\Omega})$ , 它以及由它决定的系统状态 $\dot{U}(t,x)$ 满足条件式(12.9-26), 并使性能指标式(12.9-28)达到极小值。 $f_{\bar{n}}(t,x)$ 就是系统的最优控制。

下述事实给出了这个问题最优控制存在的必要条件。如果 $\hat{f}_{0}$ 是最优控制，那么一定存在一非零向量 $\boldsymbol{c}=(c_{0},c_{1},c_{2},\cdots,c_{N})$ ， $c_{0}=-1$ ，使得对一切 $(t,\boldsymbol{x})\in[t_{0},t_{1}]\times\overline{\Omega}$ ， $\hat{f}_{0}$ 使下列函数 $H(t,\boldsymbol{x},\hat{f}_{0})$ 相对一切 $\hat{f}_{0}(t,\boldsymbol{x})\in\mathcal{A}[t_{0},t_{1}]\times\overline{\Omega})$ 达到极大值

$$
\begin{array}{l} H (t, \boldsymbol {x}, \boldsymbol {f} _ {\overline {{\Omega}}}) = c _ {0} g _ {1} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\overline {{\Omega}}} (t, \boldsymbol {x})) \\ + \omega \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} \frac {\partial g _ {1} \left(t ^ {\prime \prime} , x ^ {\prime \prime} , U \left(t ^ {\prime \prime} , x ^ {\prime \prime}\right) , f _ {\Omega} \left(t ^ {\prime \prime} , x ^ {\prime \prime}\right)\right)}{\partial U} \left\{K \left(t ^ {\prime \prime}, x ^ {\prime \prime}, t, x, U (t, x), f _ {\Omega} (t, x)\right) \right. \\ \left. - \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} M \left(t ^ {\prime \prime}, x ^ {\prime \prime}, t ^ {\prime}, x ^ {\prime}\right) K \left(t ^ {\prime}, x ^ {\prime}, t, x, U (t, x), f _ {\Omega} (t, x)\right) d t ^ {\prime} d \Omega^ {\prime} \right\} d t ^ {\prime \prime} d \Omega^ {\prime \prime} \\ + \sum_ {i = 1} ^ {N} c _ {i} \frac {\partial \mathcal {Z} _ {i} (\zeta)}{\partial \zeta} \left\{\boldsymbol {z} (t, \boldsymbol {x}, \boldsymbol {U} (t, \boldsymbol {x}), \boldsymbol {f} _ {\overline {{\Omega}}} (t, \boldsymbol {x})) \right. \\ + \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} \frac {\partial z \left(t ^ {\prime \prime} , x ^ {\prime \prime} , U \left(t ^ {\prime \prime} , x ^ {\prime \prime}\right) , f _ {\Omega} \left(t ^ {\prime \prime} , x ^ {\prime \prime}\right)\right)}{\partial U} \left[ K \left(t ^ {\prime \prime}, x ^ {\prime \prime}, t, x, U (t, x), f _ {\Omega} (t, x)\right) \right. \\ \left. - \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} M \left(t ^ {\prime \prime}, x ^ {\prime \prime}, t ^ {\prime}, x ^ {\prime}\right) K \left(t ^ {\prime}, x ^ {\prime}, U (t, x), f _ {\Omega} (t, x)\right) d t ^ {\prime} d \Omega^ {\prime} \right] d t ^ {\prime \prime} d \Omega^ {\prime \prime} \Bigg \} \tag {12.9-29} \\ \end{array}
$$

也就是说

$$
H (t, \boldsymbol {x}, \boldsymbol {f} _ {\Omega}) = \sup _ {f _ {\overline {{\Omega}}} \in \mathcal {A} [ t _ {0}, t _ {1} ] \times \overline {{\Omega}}} H (t, \boldsymbol {x}, \boldsymbol {f} _ {\Omega}) \tag {12.9-30}
$$

式中函数矩阵 $M(t'', x'', t', x')$ 满足如下积分方程

$$
\begin{array}{l} M \left(t ^ {\prime \prime}, x ^ {\prime \prime}, t ^ {\prime}, x ^ {\prime}\right) = \int_ {t _ {0}} ^ {t _ {1}} \int_ {\Omega} M \left(t ^ {\prime \prime}, x ^ {\prime \prime \prime}, t, x\right) \frac {\partial K (t , x , t ^ {\prime} , x ^ {\prime} , U \left(t ^ {\prime} , x ^ {\prime}\right) , f _ {\Omega} \left(t ^ {\prime} , x ^ {\prime}\right))}{\partial U} d t d \Omega \\ - \frac {\partial \boldsymbol {K} \left(t ^ {\prime \prime} , \boldsymbol {x} ^ {\prime \prime} , t ^ {\prime} , \boldsymbol {x} ^ {\prime} , \boldsymbol {U} \left(t ^ {\prime} , \boldsymbol {x} ^ {\prime}\right) , \boldsymbol {f} _ {\overline {{\Omega}}} \left(t ^ {\prime} , \boldsymbol {x} ^ {\prime}\right)\right)}{\partial \boldsymbol {U}} \tag {12.9-31} \\ \end{array}
$$

这个事实类似于集中参数系统的极大值原理，所以也叫分布参数系统的极大值原理, $H(t,x,f_{\bar{\Omega}})$ 叫做哈密顿函数 $^{[37,38]}$ 。

我们现在应用上面建立的关系式来讨论圆柱扭转运动的最优控制。利用格林函数，解出

$$
r (t, x) = \int_ {0} ^ {T} \int_ {0} ^ {l} K (t, x, \tau , \xi) u (\tau) d \tau d \xi \tag {12.9-32}
$$

设圆柱体两端是自由的，初始条件为零，在 x=0 一端加控制 $u(t)$ 。

假定控制量是分段连续函数，且受到 $|u(t)|\leqslant1$ 的约束。又设性能指标为

$$
J [ u (t) ] = \int_ {0} ^ {l} [ r (t, x) - r _ {0} ] ^ {2} d x \tag {12.9-33}
$$

式中 $r_0$ 是常数。

要求找到可准控制 $u(t)$ ，使圆柱体在零初始条件下和给定时间 T 内，到达某一状态和 $r_{0}$ 的均方差最小。为了应用上面的极大值原理，把性能指标改写为

$$
J [ u (t) ] = \int_ {0} ^ {T} \int_ {0} ^ {l} [ r (t, x) - r _ {0} ] ^ {2} \delta (t - T) d t d x \tag {12.9-34}
$$

式中 $\delta(t)$ 是狄拉克函数。

因为式(12.9-32)中 $K(t,x,\tau,\xi)$ 不含未知函数 $r(t,x)$ ，根据式(12.9-31)，

$M(t,x,\tau,\xi)\equiv0$ 。由式(12.9-29)得到哈密顿函数为

$$
\begin{array}{l} H (t, x, u) = - \left\{\int_ {0} ^ {T} \int_ {0} ^ {l} 2 \left(r \left(t ^ {\prime}, x ^ {\prime}\right) - r _ {0}\right) \delta \left(t ^ {\prime} - T\right) \left[ K \left(t ^ {\prime}, x ^ {\prime}, t, x\right) u (t) \right] d t ^ {\prime} d x ^ {\prime} \right. \\ \left. + \left[ r (t, x) - r _ {0} \right] ^ {2} \delta (t - T) \right\} \\ = - \left\{2 u (t) \int_ {0} ^ {l} \left[ r \left(T, x ^ {\prime}\right) - r _ {0} \right] K \left(T, x ^ {\prime}, t, x\right) d x ^ {\prime} + \left[ r (t, x) - r _ {0} \right] ^ {2} \delta (t - T) \right\} \\ = - \left\{2 u (t) l \int_ {0} ^ {l} [ r (T, x ^ {\prime}) - r _ {0} ] K (T - t, x ^ {\prime}) d x ^ {\prime} + [ r (t, x) - r _ {0} ] ^ {2} \delta (t - T) \right\} \\ \end{array}
$$

按式 $(12.9-31)$ ，最优控制应使上式达到极大值，于是

$$
u (t) = \operatorname{sgn} \left\{- \int_ {0} ^ {l} \left[ r \left(T, x ^ {\prime}\right) - r _ {0} \right] K \left(T - t, x ^ {\prime}\right) d x ^ {\prime} \right\} \tag {12.9-35}
$$

但 $r(T,x)$ 又可表示成

$$
r (T, x ^ {\prime}) = \int_ {0} ^ {T} K (T - \tau , x ^ {\prime}) u (\tau) d \tau
$$

代到式(12.9-35)中

$$
u (t) = \operatorname{sgn} \left\{- \int_ {0} ^ {l} \left[ \int_ {0} ^ {T} K \left(T - \tau , x ^ {\prime}\right) u (\tau) d \tau - r _ {0} \right] K \left(T - t, x ^ {\prime}\right) d x ^ {\prime} \right\}
$$

最后，令

$$
\begin{array}{l} R (t) = \int_ {0} ^ {l} K (T - t, x ^ {\prime}) d x ^ {\prime} \\ S (\tau , t) = \int_ {0} ^ {l} K (T - \tau , x ^ {\prime}) K (T - t, x ^ {\prime}) d x ^ {\prime} \\ \end{array}
$$

得到

$$
u (t) = \operatorname{sgn} \left\{r _ {0} R (t) - \int_ {0} ^ {T} S (\tau , t) u (\tau) d \tau \right\} \tag {12.9-36}
$$

这就是最优控制应满足的积分方程, 解出 $u(t)$ 便是系统最优控制。它是一个边界最优控制问题。一般来说, 分布参数极大值原理, 可以用来解决边界最优控制问题。这是与前面叙述的动态规划方法所不同的。

#### 12.10 分布参数系统的最速控制

在这一节里，我们讨论一类用积分方程描述的分布参数系统的最速控制问题，应用矩量法给出最速控制应满足的必要条件，这种方法有可能用近似方法求出最速控制，这样得到的最速控制，虽然不是最优的，但接近最优，所以把它叫做次最优控制，而次最优控制在工程上往往容易实现。

给定一维分布参数系统

$$
y (t _ {1}, x) = \int_ {0} ^ {t _ {1}} K (t _ {1} - \tau , x) u (\tau) d \tau \tag {12.10-1}
$$

$y(t_{1},x)$ 是系统在 $t_{1}$ 时刻的状态， $u(t)$ 是系统控制量， $K(t,x)$ 是积分方程的核，它是平方可积函数。

我们假定控制 $u(t)$ 是分段连续函数, 具有幅值约束

$$
\mid u (t) \mid \leqslant \alpha \tag {12.10-2}
$$

满足这个要求的控制就是可准控制类 C。再假定系统初值为零，终端状态是预先给定的 $y^{*}(x)$ 。所谓最速控制问题，就是找到可准控制 $\stackrel{\circ}{u}(t) \in C$ ，使系统式 (12.10-1) 从零状态出发到达状态 $y^{*}(x)$ 的时间 $t_{1}$ 最小。

这个问题可以转化成矩量问题。事实上，由第二章所讲过的 $L_{2}$ 空间性质，我们在实希尔伯特空间 $L_{2}$ 中，可以选择一组归范直交基 $\varphi_{i}(x) \in L_{2}, i = 1, 2, \cdots$ ，把平方可积函数 $y^{*}(x)$ 和 $K(t, x)$ 依这组基展开

$$
K (t, x) = \sum_ {i = 1} ^ {\infty} g _ {i} (t) \varphi_ {i} (x)
$$

$$
y ^ {*} (x) = \sum_ {i = 1} ^ {\infty} c _ {i} \varphi_ {i} (x)
$$

这两个级数依 $L_{2}$ 空间范数收敛。把这两个级数代到方程(12.10-1)中，便得到

$$
\sum_ {i = 1} ^ {\infty} = c _ {i} \varphi_ {i} (x) = \sum_ {i = 1} ^ {\infty} \varphi_ {i} (x) \int_ {0} ^ {t _ {1}} g _ {i} (t _ {1} - \tau) u (\tau) d \tau
$$

由于 $\{\varphi_{i}\}$ 是基，因此有

$$
c _ {i} = \int_ {0} ^ {t _ {1}} g _ {i} (t _ {1} - \tau) u (\tau) d \tau , \quad i = 1, 2, \dots \tag {12.10-3}
$$

由于 $y^{*}(x)$ , $K(t, x)$ 都是已知函数，故 $c_{i}, g_{i}, i=1,2,\cdots$ 都是已知的。这样，寻求最速控制 $u(t)$ 的问题，就变成了寻求函数 $u(t), |u(t)| \leqslant \alpha$ ，使式(12.10-3)无穷多个等式成立，且 $t_{i}$ 是最小的。

为了应用矩量法解决最速控制问题；我们先简单介绍一下矩量问题的基本概念和性质。各种矩量问题的详细讨论，可参考有关文献[36]。

设 $[0,T]$ 是实轴上的有限区间，E 是定义在 $[0,T]$ 上可测并可积的函数全体所组成的集合。对 E 中任一函数 $x(t)$ ，定义范数

$$
\| x \| = \int_ {0} ^ {T} | x (t) | d t \tag {12.10-4}
$$

容易验证， $E$ 是一线性赋范空间。 $E$ 上的每一线性泛函 $F(x)$ 都有如下表述式

$$
F (x) = \int_ {0} ^ {T} x (t) f (t) d t, \quad x (t) \in E \tag {12.10-5}
$$

$f(t)$ 是 $[0,T]$ 上的可测函数，并且在 $[0,T]$ 上是有界函数。定义 $F(x)$ 的范数为

$$
\| F (x) \| = \operatorname{Vrai} _ {t \in [ 0, T ]} \max | f (t) | \tag {12.10-6}
$$

符号 Vrai max 称为真性最大值, 它是指在 $[0, T]$ 上除去零测集外使 $f(t)$ 为有界函数所达到的最大值。

对 E 中任意 n 个函数 $x_{i}(t), i=1,2,\cdots,n$ ，叫做完全独立的，是指如果对任意一组不完全为零的数 $\xi_{i}, i=1,2,\cdots,n$ ，使线性组合 $\sum_{i=1}^{n}\xi_{i}x_{i}(t)$ 在 $[0,T]$ 中的任何测度大于零的子集上都不为零。

如果给定 E 中 n 个完全独立的函数 $x_{i}(t), i=1,2,\cdots,n$ ，同时给定常数 $c_{1}, c_{2}, \cdots, c_{n}, \alpha\left[\alpha>0, \sum_{i=1}^{n}c_{i}^{2}>0\right]$ ，要求找到形如式(12.10-5)的泛函 F（也就是函数 $f(t)$ ）满足 $\|F\|=\alpha$ ，并使如下 n 个等式成立

$$
F (x _ {i}) = \int_ {0} ^ {T} x _ {i} (t) f (t) d t = c _ {i}, \quad i = 1, 2, \dots , n \tag {12.10-7}
$$

这就是赋范空间 E 中的矩量问题。

在讨论矩量问题的同时，还考虑如下的极值问题，即在 $\sum_{i=1}^{n}\xi_{i}c_{i}=1$ 的条件下，求使积分

$$
\int_ {0} ^ {T} \left| \sum_ {i = 1} ^ {n} \xi_ {i} x _ {i} (t) \right| d t
$$

达到极小的点 $\xi_{i}, i=1,2,\cdots,n$ 。记这时的极小值为 $\lambda_{n}$

$$
\lambda_ {n} = \min _ {\sum_ {i = 1} ^ {n} \xi_ {i} c _ {i} = 1} \int_ {0} ^ {T} \left| \sum_ {i = 1} ^ {n} \xi_ {i} x _ {i} (t) \right| d t \tag {12.10-8}
$$

上述矩量问题和式(12.10-8)的极值问题有密切关系，在文献[36]中指出，矩量问题有解的必要充分条件是 $\lambda_{n}\geqslant\frac{1}{\alpha}$ , 当且仅当 $\lambda_{n}=\frac{1}{\alpha}$ 时,(α 是泛函 F 的范数) 矩量问题有唯一解, 这个解 $f(t)$ 由下式给出

$$
f (t) = \alpha \cdot \operatorname{sign} \left[ \sum_ {i = 1} ^ {n} \xi_ {i} x _ {i} (t) \right] \tag {12.10-9}
$$

式中 $\xi_{i}, i=1,2,\cdots,n$ 是使式(12,10-8)取极小的 $\xi_{i}, i=1,2,\cdots,n$ 值。关于式(12.10-8)的极值问题，还有以下性质：

$$
\frac {\mu}{\left(\sum_ {i = 1} ^ {n} c _ {i} ^ {2}\right) ^ {\frac {1}{2}}} \leqslant \lambda_ {n} \leqslant \frac {M}{\left(\sum_ {i = 1} ^ {n} c _ {i} ^ {2}\right) ^ {\frac {1}{2}}} \tag {1}
$$

$\mu, M$ 是两个正数。

(2) 当 $m > n$ 时, $\lambda_{m} \leqslant \lambda_{n}$ 。

（3）当 T 给定时，把 $\lambda_{n}$ 看成 $c_{i}, i=1,2,\cdots,n$ 的函数， $\lambda_{n}=\lambda_{n}(c_{1},c_{2},\cdots,c_{n})$ 是 $c_{i}$ 的凸函数。

下面我们应用矩量问题的这些基本事实，来讨论上边提到的最速控制问题。

设函数组 $g_{i}(t), i=1,2,\cdots$ 中每个函数 $g_{i}(t)$ 在区间 $[0,\infty)$ 是可测函数，并是可积的。假定其中任意 n 个函数是完全独立的，也就是说对任意二组不完全为零的数 $\xi_{i}, i=1,2,\cdots,n$ ，使线性组合 $\sum_{i=1}^{n}\xi_{i}g_{i}(t)$ 在区间 $[0,\infty)$ 任意测度不为零的子集上都不为零，我们把这个条件叫做非蜕化条件。

现在要寻找 $u(t), |u(t)| \leqslant \alpha$ ，使

$$
\int_ {0} ^ {T} g _ {i} (t) u (t) d t = c _ {i}, \quad i = 1, 2, \dots , n
$$

并使 T 为最小。

根据上面说过的矩量问题的性质，为了解决这个问题，在给定终端时刻 T 后，可先求出极值

$$
\min _ {\sum_ {i = 1} ^ {n} \xi_ {i} c _ {i} = 1} \int_ {0} ^ {T} \left| \sum_ {i = 1} ^ {n} \xi_ {i} g _ {i} (T - \tau) \right| d \tau = \lambda_ {n} (T) \tag {12.10-10}
$$

然后按式(12.10-9)求出 $u(t)$ 。

我们总假定存在一个 $T^{*}$ 使得 $\lambda_{n}(T^{*})\geqslant\frac{1}{\alpha}$ ，否则最速控制 $u(t)$ 就不存在了。由式(12.10-10)和系统非蜕化条件，不难验证函数 $\lambda_{n}(T)$ 是 T 的单调递增函数，同时，由于 $\lambda_{n}(0)=0,\lambda_{n}(T^{*})\geqslant\frac{1}{\alpha},0\leqslant T^{*}<\infty$ ，则必存在一个 $\stackrel{\circ}{T}_{n}$ ，使 $\lambda_{n}(\stackrel{\circ}{T}_{n})=\frac{1}{\alpha}$ 。显然，在一切使等式 $\int_{0}^{T}g_{i}(t)u(t)dt=c_{i},i=1,2,\cdots,n$ 成立的 T 中， $\stackrel{\circ}{T}_{n}$ 是最小的。按上面矩量问题的性质，这时必存在唯一解

$$
u _ {n} (t) = \alpha \cdot \mathrm{sing} \left[ \sum_ {i = 1} ^ {n} \xi_ {i} ^ {n} g _ {i} (\stackrel {\circ} {T} _ {n} - t) \right] \tag {12.10-11}
$$

式中 $\xi_i^n$ 是极值问题

$$
\min _ {\sum_ {i = 1} ^ {n} \xi_ {i} c _ {i} = 1} \int_ {0} ^ {\stackrel {\circ} {T} _ {n}} \left| \sum_ {i = 1} ^ {n} \xi_ {i} g _ {i} (\stackrel {\circ} {T} _ {n} - t) \right| d t = \lambda_ {n} (\stackrel {\circ} {T} _ {n}) = \frac {1}{\alpha} \tag {12.10-12}
$$

的极值点。

可以证明，由式(12.10-11)给出的 $u_{n}(t)$ ，当 $n \to \infty$ 时， $u_{n}(t)$ 的极限 $\mathring{u}(t)$ 存在，且 $|\mathring{u}(t)| \leqslant \alpha, \mathring{u}(t)$ 便是系统式(12.10-1)的最速控制[37,38]。由于 $u_{n}(t)$ 是 $\mathring{u}(t)$ 的 $n$ 阶近似，用它代替 $\mathring{u}(t)$ 可以得到足够的准确性，这一点对工程来说是有重要意义的。但是，用矩量法求出的 $n$ 阶逼近毕竟不是真正的最优控制 $\mathring{u}(t)$ ，所以把 $u_{n}(t)$ 叫做系统的次最优控制。

根据 $\lambda_{n}$ 的性质和条件 $\sum_{i=1}^{\infty} c_{i}^{2} < \infty$ ，可以看出，序列 $\{\lambda_{n}(T)\}$ 是一单调下降有界序列，因此必有极限存在， $\lambda(T) = \lim_{n \to \infty} \lambda_{n}(T)$ 。 $\lambda(T)$ 也是 $T$ 的单调函数，于是方程

$$
\lambda (T) = \frac {1}{\alpha}
$$

必有唯一解 T=T，它就是系统在最速控制 $\stackrel{\circ}{u}(t)$ 作用下，由零点到 $y^{*}(x)$ 的最短时间。

以下是在带有自动寻优器的计算装置中，实现最速控制的方案。这个方案的程序如下：令

$$
\rho_ {\xi} (T) = \int_ {0} ^ {T} \left| \sum_ {i = 1} ^ {n} \xi_ {i} g _ {i} (T - t) \right| d t \tag {12.10-13}
$$

首先任取一满足条件

$$
(\xi , \boldsymbol {c}) = \sum_ {i = 1} ^ {n} \xi_ {i} c _ {i} = 1 \tag {12.10-14}
$$

$\xi=(\xi_{1},\xi_{2},\cdots,\xi_{n}),c=(c_{1},c_{2},\cdots,c_{n})$ 的 $\xi_{0}$ ，按式(12.10-13)计算出函数 $\rho_{\xi_{0}}(T)$ 。根据上面的讨论，当 T 增大时，函数 $\rho_{\xi_{0}}(T)$ 是从零开始的单调递增函数，并存在 $T^{*}$ ，使 $\rho_{\xi_{0}}(T^{*})\geqslant\frac{1}{\alpha}$ 。我们计算 $\rho_{\xi_{0}}(T)$ ，直到 $P_{\xi_{0}}(T_{0})=\frac{1}{\alpha}$ 为止，这时记下 $T_{0}$ 值，并由寻优器求出函数 $\rho_{\xi}(T_{0})$ 在条件 $(\xi,c)=1$ 下的极值点 $\xi_{1}$ 。由于

$$
\rho_ {\xi_ {1}} \left(T _ {0}\right) = \min _ {\langle \xi , c \rangle = 1} \rho_ {\xi} \left(T _ {0}\right) <   \rho_ {\xi_ {0}} \left(T _ {0}\right) = \frac {1}{\alpha}
$$

因此，用 $\xi_{1}$ 代 $\xi_{0}$ ，重新计算函数 $\rho_{\xi_{1}}(T)$ ，并重复上述程序。这种过程一直进行到第 s 个循环，使得

$$
\left| \rho_ {\xi_ {s}} (T _ {s}) - \frac {1}{\alpha} \right| <   \varepsilon
$$

或

$$
\mid T _ {s} - T _ {s - 1} \mid <   \varepsilon \tag {12.10-15}
$$

为止。 $\varepsilon$ 是事先给定的正数。这时 $\xi_{s}$ 便是式(12.10-12)的极值点， $T_{s}$ 便是最短的过渡时间。

每个循环中，寻求极值。

$$
\min _ {(\xi , c) = 1} \rho_ {\xi} (T)
$$

的方法是很多的，比如梯度法，最速下降法，或者两种方法的结合等。详细的讨论可参看第二章。

作为例子，将矩量法应用到弹性圆柱体的最速控制。设系统状态方程是由积分方程描述的

$$
r (t, x) = \int_ {0} ^ {t} \left[ - \frac {a ^ {2}}{l} (t - \tau) - \sum_ {n = 1} ^ {\infty} \frac {2 a}{n \pi} \cos \frac {n \pi}{l} x \cdot \sin \frac {n \pi a}{l} (t - \tau) \right] u (\tau) d \tau \tag {12.10-16}
$$

系统初值为零，终端状态为给定的 $r^*(x)$ 。求由零状态到 $r^*(x)$ 的最速控制 $\stackrel{\circ}{u}(t)$ 。控制应满足 $|u(t)| \leqslant \alpha$ 的约束。

由第 12.2 节知道，圆柱体扭转振动的固有振型为

$$
\varphi_ {0} (x) = 1, \quad \varphi_ {n} (x) = \cos \frac {n \pi}{l} x, \quad n = 1, 2, \dots
$$

它构成 $L_{2}$ 空间的一组基，积分方程的核函数可以按这组基展开

$$
K (t, x) = - \frac {a ^ {2}}{l} t - \frac {2 a}{\pi} \sum_ {n = 1} ^ {\infty} \frac {1}{n} \cos \frac {n \pi}{l} x \sin \frac {n \pi a}{l} t
$$

这里， $g_{0}=-\frac{a^{2}}{l}t, g_{n}(t)=-\frac{2a}{n\pi}\sin\frac{n\pi a}{l}t, n=1,2,3,\cdots$ 。终端状态 $r^{*}(x)$ 在这组基上的级数展开为

$$
r ^ {*} (x) = c _ {0} + \sum_ {n = 1} ^ {\infty} c _ {n} \varphi_ {n} (x)
$$

式中

$$
\begin{array}{l} a _ {0} = \int_ {0} ^ {l} r ^ {*} (x) d x \\ \dots \\ c _ {n} = \int_ {0} ^ {l} r ^ {*} (x) \cos \frac {n \pi}{l} x d x, \quad n = 1, 2, \dots \\ \end{array}
$$

因此，最速控制问题就转化为求控制 $u(t), |u(t)| \leqslant \alpha$ ，并使无穷多个等式成立

$$
\begin{array}{l} c _ {0} = \int_ {0} ^ {T} g _ {0} (T - \tau) u (\tau) d \tau = - \frac {a ^ {2}}{l} \int_ {0} ^ {T} (T - \tau) u (\tau) d \tau \\ \dots \\ c _ {n} = \int_ {0} ^ {T} g _ {n} (T - \tau) u (\tau) d \tau = - \frac {2 a}{n \pi} \int_ {0} ^ {T} \sin \frac {n \pi a}{l} (T - \tau) u (\tau) d \tau \\ n = 1, 2, \dots \\ \end{array}
$$

且 T 取极小值的问题。

应用矩量法，寻找次最优控制，就是找到 $u(t)$ , $|u(t)| \leqslant \alpha$ , 使下述有限个等式成立

$$
c _ {0} = - \frac {a ^ {2}}{l} \int_ {0} ^ {T} (T - \tau) u (\tau) d \tau
$$

$$
c _ {n} = - \frac {2 a}{n \pi} \int_ {0} ^ {T} \sin \frac {n \pi a}{l} (T - \tau) u (\tau) d \tau , \quad n = 1, 2, \dots , p
$$

并使 T 达到极小。上式内 p 是一正整数。假设式(12.10-16)是非蜕化的，应用前

面的讨论，必须求下述极值问题的解

$$
\min _ {c _ {0} \xi_ {0} + \sum_ {i = 1} ^ {p} \xi_ {i} c _ {i} = 1} \int_ {0} ^ {T} \left| \xi_ {0} \left[ - \frac {a ^ {2}}{l} \right] (T - \tau) + \sum_ {k = 1} ^ {p} \xi_ {k} \left[ - \frac {2 a}{k \pi} \sin \frac {k \pi a}{l} (T - \tau) \right] \right| d \tau = \lambda_ {p} (T) = \frac {1}{\alpha}
$$

得到极值点 $\overline{\xi}=(\overline{\xi}_{0},\overline{\xi}_{1},\cdots,\overline{\xi}_{p})$ 以后，最速控制的 $p+1$ 阶就近似为

$$
u _ {p + 1} (t) = \alpha \sin g \left\{\bar {\xi} _ {0} \left[ \frac {- a ^ {2}}{l} \right] (\stackrel {\circ} {T} _ {p} - t) + \sum_ {k = 1} ^ {p} \bar {\xi} _ {k} \left[ \frac {- 2 a}{k \pi} \sin \frac {k \pi a}{l} (\stackrel {\circ} {T} _ {p} - t) \right] \right\}
$$

式中 $T_{p}$ 为 T 的最小值。当 $p \to \infty$ 时， $u_{p+1}(t)$ 的极限就是系统的最速控制。在 $p+1$ 阶近似下，求解 $\overline{\xi} = (\overline{\xi}_{1}, \overline{\xi}_{2}, \cdots, \overline{\xi}_{p})$ 和 $\overset{\circ}{T}_{p}$ 可容易地由计算机来实现。

在第 12.5 节中，我们曾谈到过对分布参数对象的有穷维逼近问题。在实际问题中实现分布参数系统的最优控制，这种逼近方法对处理具体技术问题具有实际意义。上面讨论的矩量法也是一种有穷维逼近的方法。例如，一个受控的弹性体，有无穷多个固有振动频率和振型。当控制器是由常微分方程描述时，整个系统的通频带是有限的，只能有有限个固有频率（固有振型）位于通频带内，其他高阶振型将被滤掉。在这种情况下，用有穷维运动去逼近无穷维运动是有足够准确度的。经有穷维逼近后，整个系统成为集中参数系统，再应用集中参数系统的最优控制理论解决最优控制问题。从这个意义上讲，用有穷维逼近得到的最优控制叫做次最优控制。在文献[32,35]中研究的数值方法，为分布参数系统的有穷维逼近提供了有力的理论根据。

#### 12.11 等离子体约束的控制问题

在热核受控聚变反应中，等离子体的约束是一个核心问题。目前普遍采用的是磁约束。托卡马克就是这样一种装置。下面仅就托卡马克装置中与等离子体约束有关的最优控制问题 $^{[14]}$ ，作一简单介绍。

托卡马克装置的简单原理如图 12.11-1 所示。当变压器初级线圈通以电流时，在真空室内的等离子体感应产生一环电流（相当变压器的次级线圈）。它产生的“欧姆热”把等离子体加热到高温。同时，产生的磁场约束等离子体。通过真空室外部的环形线圈产生环向磁场，用以把等离子体约束在一个轮环形的磁瓶中。这两个磁场合成的结果，形成一个螺旋磁场 B 使等离子体处于平衡状态。

假定等离子体和导电壳是轮环形的瓶，围绕 z 轴对称。它的截面如图 12.11-2 所示。处在平衡状态的等离子体，其截面为 $\Omega_{p}$ ；边界为 $\Gamma_{p}$ ，真空部分是 $\Omega_{n}$ ，导电壳的截面为 $\Omega = \Omega_{p} \cup \Gamma_{p} \cup \Omega_{v}$ ， $\Omega$ 的边界为 $\Gamma$ 。

如果等离子体特性和各种参数都已给定，这时磁场 B 在边界 $\Gamma_{p}$ 上的值是确定的，用 $B_{m}$ 表示，它是已知的。在平衡状态下, $B_{m}$ 正切于 $\Gamma_{p}$ 。迈赛尔(Mercier)

> 此处省略原书 **图 12.11-1**

> 此处省略原书 **图 12.11-2**

曾建议，在 $\Omega_{v}$ 内装有导体并通以密度为 $J$ 的电流，它在真空室内产生一磁场，并使整个磁场 $B$ 满足使等离子体处于平衡状态的边界条件 $B|_{\Gamma_p} = B_m$ 。问题是如何选择所加的电流 $J$ ，使等离子体的平衡状态具有预定的外形，同时又能使所消耗的能量最小。比如使整个电流

$$
\int_ {\Omega_ {v}} | \boldsymbol {J} | d x
$$

或者使整个能量

$$
\int_ {\Omega_ {v}} | \boldsymbol {J} | ^ {2} d x
$$

达到最小。在文献[14]中，把这个问题化成了分布参数系统的最优控制问题。

电流密度 J 和磁场强度 B 满足麦克斯韦方程

$$
\operatorname{rot} \boldsymbol {B} = \mu_ {0} \boldsymbol {J} \tag {12.11-1}
$$

$$
\operatorname{div} \boldsymbol {B} = 0 \tag {12.11-2}
$$

其中 rot, div 分别是向量的旋度和散度, $\mu_{0}$ 是常数。

在柱面坐标系内，B 可表示成（见图 12.11-3)

$$
\boldsymbol {B} = B _ {\rho} \boldsymbol {e} _ {\rho} + B _ {\varphi} \boldsymbol {e} _ {\varphi} + B _ {z} \boldsymbol {e} _ {z}
$$

> 此处省略原书 **图 12.11-3**

由于轮环相对 z 轴是对称的， $B_{\varphi}$ ， $B_{\varphi}$ ， $B_{z}$ 不依赖于 $\varphi$ ，且 $B_{\varphi} = const$ 。因此式(12.11-2)变为

$$
\frac {1}{\rho} \frac {\partial}{\partial \rho} (\rho B _ {\rho}) + \frac {\partial}{\partial z} B _ {z} = 0 \tag {12.11-3}
$$

这说明，存在一个定义在 $\Omega_{v}$ 上的势函数 $u(\rho,z)$ ,使得

$$
B _ {z} = - \frac {1}{\rho} \frac {\partial u}{\partial \rho}
$$

$$
B _ {\rho} = \frac {1}{\rho} \frac {\partial u}{\partial z} \tag {12.11-4}
$$

对我们有意义的是电流的径向分量，故假定

$$
\boldsymbol {J} = J (\rho , z) \boldsymbol {e} _ {\varphi} \tag {12.11-5}
$$

将式(12.11-1)投影到 $e_{\varphi}$ 轴后，便得到主要方程

$$
\frac {\partial B _ {\rho}}{\partial z} - \frac {\partial B _ {z}}{\partial \rho} = \mu_ {0} J \tag {12.11-6}
$$

考虑到式(12.11-4)，便有

$$
\frac {\partial}{\partial \rho} \left[ \rho^ {- 1} \frac {\partial u}{\partial \rho} \right] + \frac {1}{\rho} \frac {\partial^ {2} u}{\partial z ^ {2}} = \mu_ {0} J \tag {12.11-7}
$$

当等离子体处在平衡状态时，不难推得 $^{[14]}$ 其边界条件为

$$
u \mid_ {\Gamma_ {p}} = 0 \tag {12.11-8}
$$

$$
u \mid_ {\Gamma} = \gamma \tag {12.11-9}
$$

$$
\left. \frac {1}{\rho} \frac {\partial u}{\partial \nu} \right| _ {\Gamma_ {p}} = | \boldsymbol {B} _ {m} | \tag {12.11-10}
$$

其中 $\nu$ 是 $\Gamma_p$ 或 $\Gamma$ 的单位外法线， $|B_m|$ 是 $B_m$ 的模长， $\gamma$ 是未知常数。令 $D = \int_{\Gamma_p} |B_m| dl$ ，则有

$$
\int_ {\Gamma_ {p}} \frac {1}{\rho} \frac {\partial u}{\partial \nu} d l = D \tag {12.11-11}
$$

D 是事先给定的常值。

现在定义希尔伯特空间（一阶索波列夫空间)

$$
H ^ {1} \left(\Omega_ {v}\right) = \left\{u \in L _ {2} \left(\Omega_ {v}\right), \frac {\partial u}{\partial \rho}, \frac {\partial u}{\partial z} \in L _ {2} \left(\Omega_ {v}\right) \right\}
$$

其内积定义为

$$
\langle u, v \rangle_ {H ^ {1} \left(\Omega_ {v}\right)} = \langle u, v \rangle_ {L _ {2} \left(\Omega_ {v}\right)} + \left\langle \frac {\partial u}{\partial p}, \frac {\partial v}{\partial \rho} \right\rangle_ {L _ {2} \left(\Omega_ {v}\right)} + \left\langle \frac {\partial u}{\partial z}, \frac {\partial v}{\partial z} \right\rangle_ {L _ {2} \left(\Omega_ {v}\right)}
$$

在 $H^{1}(\Omega_{a})$ 中取那些凡在 $\Gamma_{p}$ 上为零而在 $\Gamma$ 上为常数的元所构成的集合 V，在其中定义新的内积

$$
\langle u, v \rangle_ {V} = \int_ {\Omega_ {v}} \left[ \frac {\partial u}{\partial \rho} \frac {\partial v}{\partial \rho} + \frac {\partial u}{\partial z} \frac {\partial v}{\partial z} \right] \frac {d \rho d z}{\rho}
$$

容易验证， $V$ 也是希尔伯特空间。取 $V$ 中的元 $G, G(\Gamma)$ 表示 $G$ 在 $\Gamma$ 上的值，文献[14]中指出，方程(12.11-7)—(12.11-11)有解的必要充分条件是 $u$ 满足如下方程

$$
\langle u, G \rangle_ {V} = - \mu_ {0} \int_ {\Omega_ {v}} J (G - G (\Gamma)) d \rho d z + D G (\Gamma), \quad \forall G \in V \tag {12.11-12}
$$

而且，对每一个 $J \in L_2(\Omega_v)$ 都存在唯一的一个 $u \in V$ 满足方程(12.11-12)。

方程(12.11-12)是一分布参数系统，J 是控制，u 是系统状态。V 是状态空间， $L_{2}(\Omega_{n})$ 是控制空间。

系统的性能指标为

$$
I (J) = \int_ {\Omega_ {v}} J ^ {2} d \rho d z \tag {12.11-13}
$$

对系统状态的约束是式(12.11-10)。

于是，最优控制问题为寻找一个分布电流 $J \in L_{2}(\Omega_v)$ ，它使系统状态满足约束条件式(12.11-10)并使消耗的能量式(12.11-13)达到极小。

文献[14]中证明，这个最优控制 J 和最优状态 $u=u(J)$ 存在而且是唯一的。

对于控制 J 也可以加各种约束，比如，整个电流

$$
\int_ {\Omega_ {v}} J d \rho d z = 0
$$

或者在某个面积上（例如放置测量装置的地方）电流为零。如果在真空部分的某些点上加电流（点源)

$$
J = \sum_ {\alpha = 1} ^ {N} J _ {\alpha} \delta (\rho - \rho_ {\alpha}) \delta (z - z _ {\alpha})
$$

这里 $(\rho_{\alpha}, z_{\alpha})$ 是 $\alpha$ 线圈的坐标，N 是线圈的个数。这就是点控制的情况。

在文献[14]中对上述最优控制问题，还给出了数值解，得到了许多有趣的结论。当然真要实施这种控制还有许多待研究的复杂性，如由于小等微秒级的时间特征数的限制，必须把控制信号的传递时间也计算在内。

#### 12.12 液浮陀螺温控问题

在惯性导航系统中，要求陀螺有很高的指向精度，对其漂移率有严格的限制，精度的进一步提高，不仅要靠机械加工方面的努力，还要在误差补偿方面采取措施。对单自由度液浮陀螺来说，其误差力矩 $W_{d}$ 按起因和作用的部位可分离成如下形式

$$
\begin{array}{l} W _ {d} = D _ {F} + D _ {I} (S F) _ {I} + D _ {0} (S F) _ {0} + D _ {S} (S F) _ {S} + D _ {H} (S F) _ {I} ^ {2} \\ + D _ {0 0} (S F) _ {0} ^ {2} + D _ {s s} (S F) _ {s} ^ {2} + D _ {I S} (S F) _ {I} (S F) _ {s} + D _ {0 s} (S F) _ {0} (S F) _ {s} \\ + D _ {I 0} (S F) _ {I} (S F) _ {0} + \dots \tag {12.12-1} \\ \end{array}
$$

其中 $SF$ 是比力向量， $(SF)_1, (SF)_0, (SF)_s$ 分别是比力向量在输入轴、输出轴、转子自旋轴方向上的分量， $D_l, D_0, D_s, D_{00}$ 等是比例系数。这些系数都与温度有关，在温度变化比较小的范围内，式(12.12-1)中零次项和一次项各系数与温度变化有以下关系

$$
\begin{array}{l} D _ {F} = D _ {F 0} + D _ {T F} \overline {{T}} \\ D _ {I} (S F) _ {I} = \left[ U _ {s} - D _ {T S I} \Delta T _ {s} \right] (S F) _ {I} \\ D _ {0} (S F) _ {0} = \left[ U _ {0} + D _ {T 0 0} \Delta T _ {0} \right] (S F) _ {0} \\ D _ {s} (S F) _ {s} = \left[ - U _ {I} + D _ {T I S} \Delta T _ {I} \right] (S F) _ {s} \tag {12.12-2} \\ \end{array}
$$

其中， $\overline{T}$ 是浮液平均温度； $\Delta T_{I}, \Delta T_{0}, \Delta T_{S}$ 分别是沿输入、输出、自旋轴的平均温度梯度； $U_{S}, U_{I}$ 是沿自旋轴和输入轴的质量失配； $U_{0}$ 是沿输出轴的比力引起的漂移分量的比例系数； $D_{TF}, D_{TSI}, D_{T00}, D_{TIS}$ 是温度系数。

当环境温度有了变化时，必然引起陀螺内部温度场的变化，同时将出现浮液的对流，从而产生黏滞型误差力矩。本来，液浮陀螺由于减小了摩擦力矩而提高了精度，但当温度变化引起黏滞型误差力矩时，却又影响了精度的进一步提高。如果能采取温度控制的方法，控制陀螺内部温度场的形态，减小温度因素对各主要系数的影响，这将为陀螺在系统中运用时，进行误差分离和补偿创造便利条件，同时还能减小漂移量。这就是陀螺温度控制问题的物理背景。

热扰动分为外部扰动和内部扰动两种。内部热扰动主要是力矩器和转子马达的功率损耗产生的热量。由于力矩器通常采用等幅电流的正负相位调制方法， 其电流平方为常值，故产生的热功率可以认为是常数。转子的功率耗损在长期工作中也是基本稳定的。所以在下面讨论中，我们假定内部热源总处于稳态。

外部热扰动是由于环境温度变化引起陀螺同外部环境的热交换而产生的热扰动。固体和气体的热交换有三个因素。第一，边界面热传导服从傅里叶定律

$$
q _ {1} (x) = f (x) \left[ T (x) - T _ {e} (x) \right] \tag {12.12-3}
$$

其中 $T(x)$ 是固体在边界面上的温度， $T_{e}(x)$ 是环境温度。 $f(x)$ 是比例因子，在常温下近似与 T， $T_{e}$ 无关。第二，边界面热辐射服从于波耳兹曼(Baltzman)定律

$$
q (x) = k A (x) \left[ T ^ {4} (x) - T _ {e} ^ {4} (x) \right] \tag {12.12-4}
$$

k 是波耳兹曼常数， $A(x)$ 取决于材料表面物理性质的参数。第三，对流热交换这一项比较复杂，同许多因素有关，还有待于气体热动力学的研究。但可以肯定的是这一项 $q_{3}(x)$ 是连续依赖于 $T(x)$ ， $T_{e}(x)$ ，并且是 $T(x)$ 的单调递增函数，同时又是 $T_{e}(x)$ 的单调递减函数。总之，在边界上同环境的热交换率可表达成：

$$
Q (x) = q _ {1} (x) + q _ {2} (x) + q _ {3} (x) = \Phi (x, T (x), T _ {e} (x)) \tag {12.12-5}
$$

$\Phi(x,T,T_{e})$ 对 T 是严格单调递增函数，对 $T_{e}$ 是严格单调递减函数，并且对 T, $T_{e}$ 的依赖具有相当的光滑性。

值得注意的是，关于流体力学中的诺维尔-斯托克斯（Navier-Stokes）方程的稳态解有一个重要性质：在每一特定场合，存在总体稳定性雷诺(Reynold)数 $R_{G}$ ，当雷诺数 $R < R_{G}$ 时，流体有唯一确定的稳定运动。当 $R \geqslant R_{G}$ 时，流体存在至少两种稳定的运动，甚至是湍流解[23]。经各种扰动后，其渐近状态至少也有两种解，因而对浮液来说，存在至少两种可能的误差黏滞力矩。由于 $R$ 正比于 $\nu^{-1}$ ， $\nu$ 是液体的黏度，而黏度又正比于温度。因此，今后我们假定陀螺充液部分的几何特性和浮液工作点的设计，将使运转时的雷诺数 $R$ 永远小于 $R_{G}$ 。于是稳态的温度场连续唯一地决定了一种运动，从而连续唯一地决定了一种黏滞力矩。

进行温度控制的设备有：分布热敏系数的温度传感器，分布电阻的电热片，有限个固体放大器，用它们来构成闭环控制器。

温度控制的目的是，针对外面环境的变化，用若干个分布型温度传感器，分布型电热片构成有限个控制回路，使对流型误差力矩较为稳定，并且使它随环境温度变化而变化最小。

外部环境温度变化是缓慢的，测量和控制以及内部热传导过程较快，控制回路经常处于稳态条件下，所以，我们讨论稳态下的最优控制问题。

温度热传导过程可用第 12.1 节所讲到的抛物型方程来描述。设 $\Omega$ 是三维欧氏空间 $R_{3}$ 中开连通有界集，其边界为 $\partial\Omega$ 。 $R_{+}=\{t,t\geqslant0\}$ 。受控对象热传导方程是

$$
c (\boldsymbol {x}) \rho (\boldsymbol {x}) \frac {\partial T (t , \boldsymbol {x})}{\partial t} = \sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T (t , \boldsymbol {x})}{\partial x _ {j}} \right] + f (t, \boldsymbol {x}), (t, \boldsymbol {x}) \in R _ {+} \times \Omega \tag {12.12-6}
$$

$$
- \sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) x _ {j} \frac {\partial T (t , \boldsymbol {x})}{\partial x _ {i}} = \Phi (\boldsymbol {x}, T (t, \boldsymbol {x}), T _ {e} (t, \boldsymbol {x})) - \Phi_ {T e} (t, \boldsymbol {x}), (t, \boldsymbol {x}) \in R _ {+} \times \partial \Omega \tag {12.12-7}
$$

其中 $c(\boldsymbol{x})$ 是比热， $\rho(\boldsymbol{x})$ 是密度， $K_{ij}(\boldsymbol{x}) = K_{ji}(\boldsymbol{x})$ 是热传导系数， $T(t, \boldsymbol{x})$ 是温度场分布， $T_e(t, \boldsymbol{x})$ 是边界上环境温度分布， $f(t, \boldsymbol{x})$ 是内部热源分布， $\Phi_{Tc}(t, \boldsymbol{x})$ 是供选择的控制作用， $x_j$ 是边界 $\partial\Omega$ 的外法线向量的分量。 $\Phi(\boldsymbol{x}, T, T_c)$ 是同外界总的热交换率，如同前述。

由于限定考虑稳态过程，所以我们考虑下述椭圆型方程的边界控制问题（即令 $\frac{\partial T}{\partial t}=0$ )

$$
\sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T}{\partial x _ {j}} \right] + f (t, \boldsymbol {x}) = 0, \quad x \in \Omega \tag {12.12-8}
$$

$$
- \sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) n _ {j} \frac {\partial T}{\partial x _ {i}} = \Phi (\boldsymbol {x}, T (\boldsymbol {x}), T _ {e} (\boldsymbol {x})) - \Phi_ {T c} (\boldsymbol {x}), \quad x \in \partial \Omega \tag {12.12-9}
$$

考虑到浮液工作温度的要求，一般可将 $\Phi_{Tc}(\boldsymbol{x})$ 分为两项

$$
\Phi_ {T c} (\boldsymbol {x}) = \Phi_ {0} (\boldsymbol {x}) - \Phi_ {c} (\boldsymbol {x}) \tag {12.12-10}
$$

其中 $\Phi_{0}(x)$ 为标称的加热工作点， $\Phi_{c}(x)$ 用于闭环反馈作用。因此式(12.12-6)，(12.12-7)可分解为下述问题

$$
\sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T _ {1}}{\partial x _ {j}} \right] + f (\boldsymbol {x}) = 0, \quad \boldsymbol {x} \in \Omega \tag {12.12-11}
$$

$$
- \sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) n _ {j} \frac {\partial T _ {1}}{\partial x _ {i}} = - \Phi_ {0} (\boldsymbol {x}) + \Phi (\boldsymbol {x}, T _ {1}, \overline {{T}} _ {e}), \quad \boldsymbol {x} \in \partial \Omega \tag {12.12-12}
$$

以及

$$
\sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T _ {2}}{\partial x _ {j}} \right] = 0, \quad \boldsymbol {x} \in \Omega \tag {12.12-13}
$$

$$
- \sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) n _ {j} \frac {\partial T _ {2}}{\partial x _ {i}} = - \Phi_ {c} (\boldsymbol {x}) + \Phi (\boldsymbol {x}, T _ {1} + T _ {2}, T _ {e}) - \Phi (\boldsymbol {x}, T _ {1}, \overline {{T}} _ {e}), \quad \boldsymbol {x} \in \partial \Omega \tag {12.12-14}
$$

式 $(12.12-14)$ 可以线性化为

$$
- \sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) n _ {j} = \frac {\partial T _ {2}}{\partial x _ {i}} = - \Phi_ {c} (\boldsymbol {x}) + \dot {\Phi} _ {1} (\boldsymbol {x}) T _ {2} - \dot {\Phi} _ {2} (\boldsymbol {x}) (T _ {e} - \overline {{T}} _ {e}), \quad x \in \partial \Omega \tag {12.12-15}
$$

式(12.12-11)，(12.12-12)的解是在标称环境温度分布 $\overline{T}_{e}(\boldsymbol{x})$ 下的内部温度分布 $T_{1}(\boldsymbol{x})$ 。式(12.12-13)，(12.12-14)或(12.12-15)的解 $T_{2}(\boldsymbol{x})$ 是当环境温度分布对标称值 $\overline{T}_{e}(\boldsymbol{x})$ 的偏离温度分布。而 $T(\boldsymbol{x}) = T_{1}(\boldsymbol{x}) + T_{2}(\boldsymbol{x})$ 是原来问题 式(12.12-8)，(12.12-9)的解。由于 $\Phi (\pmb {x},T,T_e)$ 对 $T,T_{e}$ 的依赖性相当光滑，可令 $\dot{\Phi}_1(\pmb {x}) = \frac{\partial}{\partial T}\Phi (\pmb {x},T_1,\overline{T_e}),\dot{\Phi}_2(\pmb {x}) = -\frac{\partial}{\partial T_e}\Phi (\pmb {x},T_1,\overline{T_e})$ 。依 $\Phi$ 对 $T,T_{e}$ 的严格递增和递减性质，所以有 $\dot{\Phi}_1(\pmb {x}) > 0,\dot{\Phi}_2(\pmb {x}) <   0$

经这样分解后，现在研究式(12.12-13)，(12.12-15)的边界控制问题。取 $\Phi_T(\boldsymbol {x}) = \Phi_e(\boldsymbol {x}) + \dot{\Phi}_2(\boldsymbol {x})(T_e(\boldsymbol {x}) - \overline{T}_e(\boldsymbol {x}))$ ，考虑

$$
\sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T}{\partial x _ {j}} \right] = 0, \quad \boldsymbol {x} \in \Omega \tag {12.12-16}
$$

$$
\sum_ {i, j = 1} ^ {3} K _ {i j} (\boldsymbol {x}) n _ {j} \frac {\partial T}{\partial x _ {i}} + \dot {\Phi} _ {1} (\boldsymbol {x}) T (\boldsymbol {x}) = \Phi_ {T} (\boldsymbol {x}), \quad \boldsymbol {x} \in \partial \Omega \tag {12.12-17}
$$

的边界控制问题。其中 $\Phi_1(x) > 0$ 。对 $K_{ij}(x),\Phi_1(x)$ 和 $\Phi_T(x)$ 的光滑性作了一些假定之后，在文献[29]中证明了，式(12.12-16)，(12.12-17)存在唯一正则解，且同下列积分方程的解等价

$$
T (\boldsymbol {x}) = 2 \int_ {\partial \Omega} G (\boldsymbol {x}, \eta) \zeta (\eta) d _ {\eta} \sigma , \quad \boldsymbol {x} \in \overline {{{\Omega}}} \tag {12.12-18}
$$

$$
\zeta (\xi) = - 2 \int_ {\partial \Omega} P _ {\xi} G (\xi , \eta) \zeta (\eta) d _ {\eta} \sigma + \Phi_ {T} (\xi), \quad \xi \in \partial \Omega \tag {12.12-19}
$$

其中 $P_{\xi} = \sum_{i,j=1}^{3} K_{ij}(\xi)n_i \frac{\partial}{\partial \xi_i} + \dot{\Phi}_1(\xi)$ 。按迭代核的性质[29]，存在问题的格林函数 $W(x, \eta)$ ，它在 $x \neq \eta$ 处是连续可微的， $W(x, \eta) = W(\eta, x)$ ，同时

$$
T (\boldsymbol {x}) = \int_ {\partial \Omega} W (\boldsymbol {x}, \eta) \Phi_ {T} (\eta) d _ {\eta} \sigma \tag {12.12-20}
$$

注意到当 $\Phi_T(\eta) \in L^2(\partial\Omega)$ 时， $T(x) \in C^{[0,\lambda]}(\overline{\Omega})^①$ 。因此，可按式(12.12-20)来定义原问题的广义解。又因核函数 $W(\eta, x)$ 在 $x \neq \eta$ 上连续，故当 $\Phi_T = \delta(x - x_0)$ ， $x_0 \in \partial\Omega$ 时， $T(x) = W(x, x_0) = \int_{\partial\Omega} W(x, \eta) \delta(\eta - x_0) d_\eta \sigma, x \neq x_0$ 。把式(12.12-20)看成是 $L_2(\partial\Omega)$ 到 $L_2(\partial\Omega)$ 的算子时，它是自伴紧算子，所有本征值是实数并有界，本征子空间是有穷维的，零是本征值的唯一聚点。

单自由度液浮陀螺有四个主要温度因素，即 $D_{TF} \overline{T}, D_{TSI} \Delta T_S, D_{T00} \Delta T_0, D_{TIS} \Delta T_I$ 。在标称环境温度 $\overline{T}_e$ 下，陀螺内部是标称温度场，陀螺转子呈现中性悬浮状态。此时按比例状态分离的各主要线性误差系数分别记成 $\overline{D}_F = D_{F0} + D_{TF} \overline{T}_1, \overline{U}_S = U_S - D_{TSI} \Delta_S T_1, \overline{U}_0 = U_0 + D_{T00} \Delta_0 T_1, \overline{U}_I = U_I - D_{TIS} \Delta_I T_1$ 。当环境温度变化成 $T_e$ 时，内部温度场同标称温度场发生偏离，这个偏离的温度分布是式 (12.12-16)，(12.12-17)的解，上述各系数分别发生 $D_{TF}\overline{T}, - D_{TSI}\Delta_S T, D_{T00}\Delta_0 T,$ $-D_{TIS}\Delta_I T$ 的偏差。

若取 $x_{1}, x_{2}, x_{3}$ 坐标轴同单自由度陀螺 $I, O, S$ 轴重合，则 $\overline{T}, \Delta_{s}T, \Delta_{0}T, \Delta_{I}T$ 分别是 $T(x)$ ， $\frac{\partial T(x)}{\partial x_{3}}$ ， $\frac{\partial T(x)}{\partial x_{2}}$ ， $\frac{\partial T(x)}{\partial x_{1}}$ 诸梯度分量在 $\Omega$ 上的积分平均值 $\int_{\Omega} a_{1}(x)T(x)dx, \int_{\Omega} a_{2}(x)\frac{\partial T(x)}{\partial x_{3}}dx, \int_{\Omega} a_{3}(x)\frac{\partial T(x)}{\partial x_{2}}dx, \int_{\Omega} a_{4}(x)\frac{\partial T(x)}{\partial x_{1}}dx$ ，其中 $0 \leqslant a_{i}(x) \leqslant a < \infty, a_{i}(x)C(\overline{\Omega}), i = 1, 2, 3, 4$ 。

当考虑椭圆方程的狄里克雷(Dirichlet)问题时

$$
\sum_ {i, j = 1} ^ {3} \frac {\partial}{\partial x _ {i}} \left[ K _ {i j} (\boldsymbol {x}) \frac {\partial T}{\partial x _ {j}} \right] = 0, \quad \boldsymbol {x} \in \Omega \tag {12.12-21}
$$

$$
T (\boldsymbol {x}) = T _ {0} (\boldsymbol {x}), \quad \boldsymbol {x} \in \partial \Omega \tag {12.12-22}
$$

则由 $T_0$ 决定的解 $T$ 的关系是由 $L_{2}(\partial \Omega)$ 到一阶索波列夫空间 $H^{1}(\Omega)$ 的线性连续映象。因而 $D_{TF}\overline{T}, - D_{TSI}\Delta_S T, D_{T00}\Delta_0 T, - D_{TIS}\Delta_I T$ 是 $L_{2}(\partial \Omega)$ 中的线性泛函，即存在 $\psi_i(x) \in L_2(\partial \Omega), i = 1,2,3,4$ ，使

$$
M _ {1} = D _ {T F} \overline {{T}} = \int_ {\partial \Omega} T (\boldsymbol {x}) \psi_ {1} (\boldsymbol {x}) d _ {x} \sigma
$$

$$
M _ {2} = - D _ {T S I} \Delta_ {S} T = \int_ {\partial \Omega} T (\boldsymbol {x}) \psi_ {2} (\boldsymbol {x}) d _ {x} \sigma
$$

$$
M _ {3} = D _ {T 0 0} \Delta_ {0} T = \int_ {\partial \Omega} T (\boldsymbol {x}) \psi_ {3} (\boldsymbol {x}) d _ {x} \sigma
$$

$$
M _ {4} = - D _ {T I S} \Delta_ {I} T = \int_ {\partial \Omega} T (\boldsymbol {x}) \psi_ {4} (\boldsymbol {x}) d _ {x} \sigma \tag {12.12-23}
$$

式内 $d_{x}\sigma$ 是边界上的面积元素。

控制的目的是使温度因素引起的误差变化为最小，故定义指标泛函为

$$
J = \sum_ {i = 1} ^ {4} \frac {M _ {i} ^ {2}}{\sigma_ {i} ^ {2}} \tag {12.12-24}
$$

其中 $\sigma_{i}^{2}$ 是设计者根据实际问题需要确定的加权因子。假定控制作用的功率是有限制的，即

$$
\int_ {\partial \Omega} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma \leqslant C \tag {12.12-25}
$$

在条件式(12.12-25)的限制下，使 J 取极小值。这个限制也可取成下述的最优指标

$$
\overline {{J}} = J + \frac {1}{\lambda} \int_ {\partial \Omega} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma , \quad \lambda > 0 \tag {12.12-26}
$$

因此功率限制条件可以通过调节 $\lambda$ 的大小来达到。由上述定义知道

$$
M _ {i} ^ {2} = \int_ {\partial \Omega} \int_ {\partial \Omega} \psi_ {i} (\boldsymbol {x}) \psi_ {i} (\xi) T (\boldsymbol {x}) T (\xi) d _ {x} \sigma d _ {\xi} \sigma \tag {12.12-27}
$$

$$
\overline {{{J}}} = \int_ {\partial \Omega} \lambda^ {- 1} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma + \int_ {\partial \Omega} \int_ {\partial \Omega} T (\boldsymbol {x}) A (\boldsymbol {x}, \xi) T (\xi) d _ {x} \sigma d \xi \sigma \tag {12.12-28}
$$

$$
A (\boldsymbol {x}, \xi) = \sum_ {i = 1} ^ {4} \sigma_ {i} ^ {- 2} \psi_ {i} (\boldsymbol {x}) \psi_ {i} (\xi) \tag {12.12-29}
$$

控制的结果使 $\overline{J}$ 取极小, 就意味着在控制功率限制条件下, 温度因素的变化取极小, 从而使陀螺漂移按式(12.12-1)分解的主要系数因温度变化而引起的变化最小。

有了指标后，可以提出如下最优边界控制问题：求 $\Phi_{c}(x)$ 同 $T(x)|_{\partial\Omega}$ 的关系，使

$$
T (\boldsymbol {x}) = \int_ {\partial \Omega} W (\boldsymbol {x}, \xi) \left[ \Phi_ {c} (\xi) + \dot {\Phi} _ {2} (\xi) \left(T _ {e} (\xi) - \overline {{{T}}} _ {e} (\xi)\right) \right] d \xi \sigma \tag {12.12-30}
$$

并使 $\overline{J}$ 取极小值。下面, 我们应用泛函变分（弱变分）来解决这个问题。

对任意给定的 $T_{e}(\boldsymbol{x}), \boldsymbol{x} \in \partial \Omega,$ 对 $\Phi_{c}$ 作弱变分，则

$$
\delta T (\boldsymbol {x}) = \int_ {\partial \Omega} W (\boldsymbol {x}, \xi) \delta \Phi_ {c} (\xi) d _ {\xi} \sigma \tag {12.12-31}
$$

又因 $A(x,\xi) = A(\xi ,x)$ ，所以 $\overline{J}$ 的变分为

$$
\begin{array}{l} \delta \bar {J} = \int_ {\partial \Omega} \frac {2}{\lambda} \Phi_ {c} (\boldsymbol {x}) \delta \Phi_ {c} (\boldsymbol {x}) d _ {x} \sigma + \int_ {\partial \Omega} \int_ {\partial \Omega} 2 T (\xi) A (\boldsymbol {x}, \xi) \delta \Phi_ {c} (\boldsymbol {x}) d _ {x} \sigma d _ {\xi} \sigma \\ = \int_ {\partial \Omega} \frac {2}{\lambda} \Phi_ {c} (\boldsymbol {x}) \partial \Phi_ {c} (\boldsymbol {x}) d _ {x} \sigma \\ + \int_ {\partial \Omega} \int_ {\partial \Omega} 2 T (\xi) A (\boldsymbol {x}, \xi) \int_ {\partial \Omega} W (\boldsymbol {x}, \eta) \delta \Phi_ {c} (\eta) d _ {\eta} \sigma d _ {x} \sigma d _ {\xi} \sigma \\ = 2 \int_ {\partial \Omega} \left[ \frac {\Phi_ {c} (\boldsymbol {x})}{\lambda} + \int_ {\partial \Omega} \int_ {\partial \Omega} T (\xi) A (\eta , \xi) W (\eta , \boldsymbol {x}) d _ {\xi} \sigma d _ {\eta} \sigma \right] \delta \Phi_ {c} (\boldsymbol {x}) d _ {x} \sigma \\ = 2 \int_ {\partial \Omega} \left[ \frac {\Phi_ {c} (\boldsymbol {x})}{\lambda} + \int_ {\partial \Omega} H (\boldsymbol {x}, \xi) T (\xi) d \xi \sigma \right] \delta \Phi_ {c} (\boldsymbol {x}) d _ {x} \sigma \tag {12.12-32} \\ \end{array}
$$

其中

$$
H (\boldsymbol {x}, \xi) = \int_ {\partial \Omega} A (\eta , \xi) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma \tag {12.12-33}
$$

如果 $\Phi_{c}(\boldsymbol{x})$ 是最优控制, 应有

$$
\delta \overline {{J}} = 0 \tag {12.12-34}
$$

那么最优控制应为

$$
\begin{array}{l} \Phi_ {c} (\boldsymbol {x}) = - \lambda \int_ {\partial \Omega} H (\boldsymbol {x}, \xi) T (\xi) d \xi \sigma \\ = - \lambda \int_ {\partial \Omega} \int_ {\partial \Omega} \sum_ {i = 1} ^ {4} \frac {\psi_ {i} (\eta) \psi_ {i} (\xi)}{\sigma_ {i} ^ {2}} W (\eta , x) d _ {\eta} \sigma T (\xi) d _ {\xi} \sigma \\ \end{array}
$$

$$
= - \lambda \sum_ {i = 1} ^ {4} \frac {1}{\sigma_ {i} ^ {2}} \left[ \int_ {\partial \Omega} \psi_ {i} (\eta) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma \right] \left[ \int_ {\partial \Omega} \psi_ {i} (\xi) T (\xi) d _ {\xi} \sigma \right] \tag {12.12-35}
$$

因而

$$
\begin{array}{l} \overline {{{J}}} = \int_ {\partial \Omega} \frac {1}{\lambda} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma + \int_ {\partial \Omega} \int_ {\partial \Omega} \int_ {\partial \Omega} W (\boldsymbol {x}, \eta) [ \Phi_ {c} (\eta) + \dot {\Phi} _ {z} (\eta) (T _ {e} (\eta) - T _ {e} (n)) ] d _ {\eta} \sigma \\ \cdot \sum_ {i = 1} ^ {4} \frac {\psi_ {i} (\boldsymbol {x}) \psi_ {i} (\xi)}{\sigma_ {i} ^ {2}} \int_ {\partial \Omega} W (\xi , \eta) \left[ \Phi_ {c} (\zeta) + \dot {\Phi} _ {2} (\zeta) \left(T _ {e} (\zeta) - \overline {{T}} _ {e} (\zeta)\right) \right] d \zeta \sigma d _ {x} \sigma d _ {\xi} \sigma \\ = \int_ {\partial \Omega} \frac {1}{\lambda} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma + \sum_ {i = 1} ^ {4} \frac {1}{\sigma_ {i} ^ {2}} \left[ \int_ {\partial \Omega} \int_ {\partial \Omega} W (\boldsymbol {x}, \eta) \left[ \Phi_ {c} (\eta) + \dot {\Phi} _ {2} (\eta) \left(T _ {e} (\eta) - \overline {{T}} _ {e} (\eta)\right) \right] d _ {\eta} \sigma \right. \\ \left. \cdot \psi_ {i} (\boldsymbol {x}) d _ {x} \sigma \right] ^ {2} \\ = \frac {1}{\lambda} \int_ {\partial \Omega} \Phi_ {c} ^ {2} (\boldsymbol {x}) d _ {x} \sigma \\ + \sum_ {i = 1} ^ {4} \frac {1}{\sigma_ {i} ^ {2}} \left\{\int_ {\partial \Omega} \left[ \int_ {\partial \Omega} \psi_ {i} (\eta) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma \right] \left[ \Phi_ {c} (\boldsymbol {x}) + \dot {\Phi} _ {2} (\boldsymbol {x}) \left(T _ {e} (\boldsymbol {x}) - \overline {{T}} _ {e} (\boldsymbol {x})\right) \right] \right\} ^ {2} \tag {12.12-36} \\ \end{array}
$$

由此可以看出， $\overline{J}$ 在 $L^{2}(\partial\Omega)$ 上对 $\Phi_{c}$ 是二次凸泛函。因为

$$
\lim _ {\| \Phi_ {c} \| ^ {2} L _ {2} (\partial \Omega) \rightarrow \infty} \overline {{{J}}} (\Phi_ {c}) = + \infty \tag {12.12-37}
$$

故极小值存在，因此最优控制存在，并具有式(12.12-35)的形式。

再令

$$
M _ {i} (\boldsymbol {x}) = \int_ {\partial \Omega} \psi_ {i} (\eta) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma , \quad i = 1, 2, 3, 4 \tag {12.12-38}
$$

则观测值为

$$
T _ {i} = \int_ {\partial \Omega} \psi_ {i} (\eta) T (\eta) d _ {\eta} \sigma , \quad i = 1, 2, 3, 4 \tag {12.12-39}
$$

最优控制变成

$$
\Phi_ {c} (\boldsymbol {x}) = - \lambda \sum_ {i = 1} ^ {4} \frac {1}{\sigma_ {i} ^ {2}} M _ {i} (\boldsymbol {x}) T _ {i} \tag {12.12-40}
$$

也就是在 $\Omega$ 的边界 $\partial\Omega$ 上，分别安装分布热敏系数为 $\psi_{i}(\boldsymbol{x})$ 的最优温度传感器，使四个加热电流（其平方值为 $T_{i}$ ）分别以 $-\frac{\lambda}{\sigma_{i}^{2}}$ 的增益，并通过阻抗密度为 $M_{i}(\boldsymbol{x})$ 的加热片，就可以实现最优控制。

实现最优控制所需要的参量 $\psi_{i}(\boldsymbol{x}), W(\boldsymbol{x}, \eta)$ 和 $M_{i}(\boldsymbol{x})$ 都可用陀螺温度测试来得到。前已指出

$$
T (\boldsymbol {x}) = W (\boldsymbol {x}, \boldsymbol {y}) = \int_ {\partial \Omega} W (\boldsymbol {x}, \eta) \delta (\eta - \boldsymbol {y}) d _ {\eta} \sigma \tag {12.12-41}
$$

即 $W(x,y)$ ，是在标称的环境温度下，在 $\partial\Omega$ 上 y 处作用以单位点热源后，量得的稳态表面温度分布。而

$$
M _ {i} (\boldsymbol {x}) = \int_ {\partial \Omega} \psi_ {i} (\eta) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma \tag {12.12-42}
$$

是在标称环境温度 $\overline{T}_{e}$ 下，在 x 点处作用以单位点热源后，分离出的诸主要误差系数 $D_{F}, D_{I}, D_{S}, D_{0}$ 同在标称温度下，无其他扰动时的诸系数 $\overline{D}_{F}, \overline{D}_{I}, \overline{D}_{0}, \overline{D}_{S}$ 的增量，即

$$
M _ {1} (\boldsymbol {x}) = D _ {F} - \overline {{D}} _ {F}
$$

$$
M _ {2} (\boldsymbol {x}) = D _ {I} - \overline {{D}} _ {I}
$$

$$
M _ {3} (\boldsymbol {x}) = D _ {0} - \overline {{D}} _ {0}
$$

$$
M _ {4} (\boldsymbol {x}) = D _ {s} - \overline {{D}} _ {s} \tag {12.12-43}
$$

而 $\psi_{i}(\eta)$ 可通过已知量 $M_{i}(x)$ , $W(x,y)$ 按式(12.12-38)求逆来逼近。

在工程实现时，温度量测可由 N 个温度传感器测到的 $\partial\Omega$ 上一些点的温度插值求出。

$$
\hat {T} (\boldsymbol {x}) = \sum_ {j = 1} ^ {N} g _ {j} (\boldsymbol {x}) T _ {j}
$$

其中

$$
T _ {j} = \int_ {\partial \Omega} T (\boldsymbol {x}) \delta (\boldsymbol {x} - \boldsymbol {x} _ {j}) d _ {x} \sigma
$$

或

$$
T _ {j} = \int_ {\partial \Omega} T (\boldsymbol {x}) a _ {j} (\boldsymbol {x}) d _ {x} \sigma
$$

而

$$
\begin{array}{l} T _ {i} = \int_ {\partial \Omega} \psi_ {i} (\boldsymbol {x}) \sum_ {j = 1} ^ {N} g _ {j} (\boldsymbol {x}) T _ {j} d _ {x} \sigma \\ = \sum_ {j = 1} ^ {N} \int_ {\partial \Omega} \psi_ {i} (\boldsymbol {x}) g _ {j} (\boldsymbol {x}) d x \sigma T _ {j}, \quad i = 1, 2, 3, 4 \tag {12.12-44} \\ \end{array}
$$

分层加热片可选用 M 个彼此不重叠的加热片 $b_{k}(\boldsymbol{x})>0, k=1,2,\cdots,M$ 。通过与放大器组闭合来实现最优逼近。选 $\{G_{ik}\}, i=1,2,3,4; k=1,2,\cdots,M$ ，使

$$
\sum_ {k = 1} ^ {M} G _ {i k} b _ {k} (\boldsymbol {x}) \cong M _ {i} (\boldsymbol {x}) = \int_ {\partial \Omega} \psi_ {i} (\eta) W (\eta , \boldsymbol {x}) d _ {\eta} \sigma
$$

上式在下述意义下成立

$$
\int_ {\partial \Omega} (M _ {i} (\boldsymbol {x}) - \sum_ {k = 1} ^ {M} G _ {i k} b _ {k} (\boldsymbol {x})) ^ {2} d _ {x} \sigma = \min _ {G _ {i k}}, \quad i = 1, 2, 3, 4
$$

故

$$
G _ {i k} = \frac {\int_ {\partial \Omega} M _ {i} (\boldsymbol {x}) b _ {k} (\boldsymbol {x}) d _ {x} \sigma}{\int_ {\partial \Omega} b _ {k} ^ {2} (\boldsymbol {x}) d _ {x} \sigma}, \quad i = 1, 2, 3, 4, \quad k = 1, 2, \dots , M
$$

此时近似最优控制为

$$
\begin{array}{l} \widehat {\Phi} _ {c} (\boldsymbol {x}) = - \lambda \sum_ {i = 1} ^ {4} \frac {1}{\sigma_ {i} ^ {2}} \sum_ {k = 1} ^ {M} G _ {i k} b _ {k} (\boldsymbol {x}) \sum_ {j = 1} ^ {N} \left[ \int_ {\partial \Omega} \psi_ {i} (\boldsymbol {x}) g _ {i} (\boldsymbol {x}) d _ {x} \sigma \right] T _ {j} \\ = - \lambda \sum_ {k = 1} ^ {M} \sum_ {j = 1} ^ {N} \left(\sum_ {i = 1} ^ {4} \frac {\boldsymbol {G} _ {i k}}{\sigma_ {i} ^ {2}} \int_ {\partial \Omega} \psi_ {i} (\boldsymbol {x}) \boldsymbol {g} _ {i} (\boldsymbol {x}) d _ {x} \sigma\right) b _ {k} (\boldsymbol {x}) T _ {j} \\ \end{array}
$$

又令

$$
A _ {k j} = \sum_ {i = 1} ^ {4} \frac {G _ {i k}}{\sigma_ {i} ^ {2}} \int_ {\partial \Omega} \psi_ {i} (\eta) g _ {j} (\eta) d _ {\eta} \sigma
$$

则

$$
\widehat {\Phi} _ {c} (\boldsymbol {x}) = - \lambda (b _ {1} (\boldsymbol {x}), \dots , b _ {M} (\boldsymbol {x})) \left( \begin{array}{c} \Phi_ {c 1} \\ \vdots \\ \Phi_ {c M} \end{array} \right)
$$

而

$$
\left( \begin{array}{c} \Phi_ {c 1} \\ \vdots \\ \Phi_ {c M} \end{array} \right) = (A _ {k j}) \left( \begin{array}{c} T _ {1} \\ \vdots \\ T _ {N} \end{array} \right)
$$

式中 $(A_{kj})$ 是 $M \times N$ 阶矩阵。可以看出，这样的控制规律是很容易实现的。

#### 12.13 参考文献

[1] 钱学森, 物理力学讲义, 科学出版社, 1962.

[2] 谷超豪等, 数学物理方程, 上海科学技术出版社, 1960.

[3] 梁昆淼, 数学物理方法, 人民教育出版社, 1958.

[4] 关肇直, 泛函分析讲义, 高等教育出版社, 1958.

[5] 冯康, 广义函数的对偶关系, 数学进展, 3(1957), 2.

[6] 毕大川, 热传导方程的最优边界控制, 应用数学与计算数学, 3(1966), 2.

[7] 毕大川, 王康宁, 具有分布参数控制系统的最优控制问题, 科学通报, 1966, 6.

[8] 王康宁, 关肇直, 弹性振动的镇定问题(Ⅲ), 中国科学, 1976, 2.

[9] 宋健, 于景元, 带有常微分控制器的分布参数反馈系统, 中国科学, 1975, 2.

[10] 宋健, 于景元, 点测量、点控制的分布参数系统, 中国科学, 1979, 2.

[11] 侯天相, 关于常系数线性偏微分方程组柯西问题的弱渐近稳定性, 数学学报, 12, (1962), 1.

[12] Balakrishnan. A. V., Applied Functional Analysis, New York, 1976.

[13] Brogan, W. L. Optimal control theory applied to systems described by partial differential

equations. Advan control systems. 6, 1968.

[14] Boujot, J. P., Morera, J. P., Teman. R., An optimal control problem related to the equilibrium of a plasma in a cavity. Applied Math. and Optimization, 2(1975), 2.

[15] Courant, R., Hilbert, D., Methods of Mathematical Physics Wiley New York, 1953.

[16] Dunford, N., Schwartz, T., Linear Operators, I, II, III, New York. 1958—1972.

[17] Doetch, G., Handbuck der Laplace-Transformations. Basel, 1950—1956.

[18] Fottorini, H. O., On complete controllability of linear systems, Jour. Differential Equations, 3(1967), 3.

[19] Foguel, S. R., Finite dimensional perturbations in Banach space, Amer. Jour. Math. (1960), 2.

[20] Goldberg, S., Unbounded Linear Operators, Theory and Application. New York. 1966.

[21] Goodson. R. E., Klein, R. E., A definition and some results for distributed observability, IEEE Trans. Automatic control, AC-15(1970), 2.

[22] Herget, C.J., On the controllability of distributed parameter systems, Intern. Jour. Control 11(1970), 3.

[23] Joseph.D.D., Stability of connection in containers of arbitrary shape, Jour. Fluid. Mech. 47 (1971), 2.

[24] Kato. T., Perturbation Theory for Linear Operators, Springer-Verlag, 1976.

[25] Lions, J. L., Magenes, E., Problems aux limites Non-homogenes et Applications. Paris 1, Dunod, 1968.

[26] Lions, J. L., Optimal Control of Systems Governed by Partial Differential Equations. Berlin, Springer, 1971.

[27] Lax, P.D., On Cauchy's problme for hyperbolic equations and the differentiability of solutions of elliptic equations. Comm. Pure and Appl. Math. 8(1955). 1-4.615-633.

[28] Leray.J., Hyperbolic Differential Equations, Princeton, 1952.

[29] Miranda, C., Partial Differential Equations of Elliptic Type, 1970.

[30] Russell, D. L., Problems of Control and Stabilization for Partial differential equations. Proceeding of IFAC. Par 1 A. 1975.

[31] Sears, W. R., J. Aeronaut. Sci. 8(1941), 104.

[32] Temam, R., Variational principles related to the equilibrium shape of a plasma in on oxisymmetric torus. Plasma Physics, 17, 1975.

[33] Wang, P. K., Control of distributed parameter systems, Advan. Control Systems. 1, 1964.

[34] Yosida, K., Functional Analysis, Springer-Verlag, 1974.

[35] Yvon, J. P., Some optimal control problems for distributed systems and their numerical solutions, Proceeding of IFAC, Part 1 A, 1975.

[36] Ахиезер, Н., Крейн М., О некоторых вопросах теории моментов, ГОНОИ, Харьков, 1938.

[37] Ђутковский, А. Г., Теория Оптимального Управления Системами С распределенными параметрами, Наука, 1965.

[38] Ђутковский, Г., Лернер А. Я., Об оптимальном управлении системами С распределенными лараметраии, Автоматика и Телемеханика, 21(1960), 6.

[39] Ђерезанский, Ю. М., Разложение по Собственным функциям Самосопряженных операторов, Киев, 1965.

[40] Ђоднер, В. А., Теория Автоматического Управления Полетом, М., «Наука», 1964.

[41] Воробоев, Ю. В., Дроздавиг, В. И., О методах исследования устойчивости систем регулирования с распреденными параметрами, Автоматика и Телемеханика, 10(1949), 2.

[42] Гохберг, И. Ц., Крейи М. Г., Основые положения о дефектных числах и индексах линейных операторов, УМН, 12(1957), 2.

[43] Гохберг, И. Ц., Крейн М. Г., Введение в теорию ленейных несамосопряженных операторов в гильбертовам пространстве, Масква, 1965.

[44] Гельфанд, И. М., Шлов Г. Е., Некоторые вопросы теории дифференцальных уравнений, Москва, 1958.

[45] Егоров, А. Л., Об оптимальным управленим процессом в некоторых системах с распределенными параметрами, Автоматика и Телемеханика, 25(1964), 5.

[46] Лернер, А. Я., Оптнмальное управление непрерывными процессами, доклад на втором конгрессе IFAC, 1963.

[47] Мовган, А. А., Приклаэная Мамематика и механика, 23(1959), 3.

[48] Михлин, С. Г., Проблема минимума квадратичного функционала, гостроиздат, 1952. (二次泛函的极小问题, 王维新译, 1964.)
