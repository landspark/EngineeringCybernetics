# 工程控制论（下册）

（第三版）

钱学森 宋健 著

## 正文（013）

### 第十三章 摄动理论和制导系统

弹道摄动理论是用来计算炮弹、火箭等在标准弹道附近的运动状态的。标准弹道是一条有着特定的初始条件、飞行程序、大气状态以及额定的结构参数的确定性弹道。如果实际情况与这些特定的条件有差别，例如飞行器在飞行过程中受到随机的风的扰动而偏离了标准弹道，这时，实际的弹道就不同于标准弹道了。但是，如果扰动作用都很小，则受扰弹道（实际弹道）还是在标准弹道的附近，而且两者之间的差别也是很小的。标准弹道可以认为是已知的，可由精确的计算得到，所以实际弹道与标准弹道相当接近这一事实就成为实际弹道的微分方程线性化的依据。经过线性化处理后，受扰系统的运动方程就成为变系数的线性微分方程，系数随时间变化是由于飞行器本身的状态和所处的环境是随时间变化的缘故。

应用弹道摄动理论的本来目的只是计算飞行器弹道相对于标准弹道的微小修正量（这种修正是由于飞行器的重量与标准值之间的误差，大气状态的改变，风的扰动作用等因素引起的)。但是，由于现代的大型快速电子计算机的出现，完全可以分别地直接计算每一条受扰弹道，所以弹道摄动理论在弹道计算问题上的用处也就随之消失了。然而，变系数线性控制系统的设计问题却恰好可以应用弹道摄动理论。在这一章里，我们将要通过远程导弹制导问题的讨论来说明这种理论。德瑞尼克(Drenick)曾经研究过这个问题 $^{[7]}$ ,但是，我们的讨论将是更完善的，除了要谈到这样一类飞行器的制导问题外 $^{[14]}$ ,还要把这个问题的讨论推广成为设计一类高精度变系数线性控制系统的一般理论 $^{[2]}$ 。最后，将摄动理论和控制理论相结合，用于弹道火箭惯性制导系统的设计 $^{[3]}$ 。

#### 13.1 飞航式导弹的运动方程

为了使讨论不过分复杂，我们假设火箭在旋转着的地球的赤道平面内运动，如图 13.1-1 所示。在赤道平面内的运动因为不会受到柯氏(Coriolis)力的作用，所以就可以保持平面运动。我们所选取的坐标系统对于旋转的地球来说是固定的，也就是说，坐标系统也是以地球自转的角速度 $\Omega$ 转动着的。在任何一个时刻 t, 火箭在赤道平面内的位置总可以用 r 和 $\theta$ 两个量来确定，这里,r 是向径，也就是从火箭到地心的距离, $\theta$ 是到发射点的角度，也就是火箭所在的位置与发射点之间的经度差。设 $r_{0}$ 是地球的半径。g 是地面上的引力加速度，其中不包含地球自转的离心力的因素。设 R 和 $\Theta$ 分别是火箭的每单位质量平均受到的推力与空气动 力的径向（半径方向）分量和切向（垂直于半径的方向）分量。于是，火箭的重心的运动方程就是

$$
\frac {d r}{d t} = \dot {r}
$$

$$
\frac {d \theta}{d t} = \dot {\theta}
$$

$$
\frac {d \dot {r}}{d t} = R + r (\dot {\theta} \pm \Omega) ^ {2} - g \left[ \frac {r _ {0}}{r} \right] ^ {2}
$$

$$
r \frac {d \dot {\theta}}{d t} = \Theta - 2 \dot {r} (\dot {\theta} \pm \Omega) \tag {13.1-1}
$$

如果火箭从西向东飞行，方程(13.1-1)的右端的第二项中就必须取十号，如果，火箭从东向西飞行，就取一号。

> 此处省略原书 **图 13.1-1**

R 和 $\Theta$ 这两个力都是由推力 S, 升力 L 和阻力 D 组成的。设 W 是火箭对于 g 而言的瞬时重量（也就是火箭的瞬时质量与 g 的乘积); V 是空气对于火箭的相对速度的大小。我们引进下列公式定义的三个参数 $\Sigma$ , $\Lambda$ 和 $\Delta$ 可以使讨论更方便些

$$
\Sigma = \frac {S g}{W}, \quad \Lambda = \frac {L g}{W V}, \quad \Delta = \frac {D g}{W V} \tag {13.1-2}
$$

假设实际的风速 w 是水平方向的，而且也在赤道平面之内，如果是迎风，w 就取正号；反之，如果风向和火箭的飞行方向相同，w 就取负号。我们把 w 看作只是高度 r 的函数。如果 $v_{r}$ 是径向速度， $v_{0}$ 是切向速度，也就是说

$$
v _ {r} = \dot {r}
$$

$$
v _ {\theta} = r \dot {\theta} \tag {13.1-3}
$$

相对的空气速度 V 就可以这样计算

$$
V ^ {2} = \dot {r} ^ {2} + (r \dot {\theta} + w) ^ {2} \tag {13.1-4}
$$

如果 $\beta$ 是推力方向与水平方向之间的角度，那么，单位质量上所受的推力和空气动力的径向分量 R 和切向分量 $\Theta$ 就是

$$
R = \Sigma \sin \beta + (v _ {0} + w) \Lambda - v _ {r} \Delta
$$

$$
\Theta = \Sigma \cos \beta - v _ {r} \Lambda - (v _ {0} + w) \Delta \tag {13.1-5}
$$

如果 N 是对于重心的力矩被火箭对于重心的转动惯量除得的商数，那么，角加速度的方程就是

$$
\frac {d \dot {\beta}}{d t} = \frac {d \dot {\theta}}{d t} + N \tag {13.1-6}
$$

为了完全确定火箭的运动状态，必须用时间函数的形式把升力 L, 阻力 D 和对于重心的力矩 m 表示出来。按照空气动力学的习惯，我们用升力系数 $C_{L}$ 和阻力系数 $C_{D}$ 来表示 L 和 D

$$
L = \frac {1}{2} \rho V ^ {2} A C _ {L}
$$

$$
D = \frac {1}{2} \rho V ^ {2} A C _ {D} \tag {13.1-7}
$$

其中， $\rho$ 是空气的密度，是高度 $r$ 的函数。 $A$ 是一个固定的特征面积，譬如说，可以设火箭的尾翼面积是 $A$ 。在我们所考虑的这个问题里，既然火箭只在赤道平面内运动，从空气动力学计算的角度来看，火箭的运动状态是由冲角 $\alpha$ 决定的（冲角就是推力的作用线与空气的相对速度向量之间的角度（图 13.1-1)）。然而，对于火箭的运动的控制是通过升降舵角 $\gamma$ 的控制来执行的。所以，能够影响 $C_L$ 和 $C_D$ 的参数就是 $\alpha$ 和 $\gamma$ 。此外，这些空气动力学的系数还是雷诺(Reynold)数 Re 和马赫(Mach)数 $M$ 的函数。如果 $a$ 是空气的音速，马赫数就是

$$
M = \frac {V}{\boldsymbol {a}} \tag {13.1-8}
$$

设 $a$ 也是高度 $r$ 的函数。如果 $l$ 是火箭的一个特征长度， $\mu$ 是空气的黏性系数，雷诺数就是

$$
\mathrm{Re} = \frac {\rho V l}{\mu} \tag {13.1-9}
$$

黏性系数 $\mu$ 也是高度 r 的函数。这样，我们就有

$$
C _ {L} = C _ {L} (\alpha , \gamma , M, \mathrm{Re})
$$

$$
C _ {D} = C _ {D} (\alpha , \gamma , M, \mathrm{Re}) \tag {13.1-10}
$$

我们再假定，推力作用线通过火箭的重心；因此，推力就不产生力矩。不难想到在火箭发动机工作的飞行过程中，火箭的角度运动（转动）一定很慢，所以喷射阻尼力矩是可以忽略不计的。因此，空气动力力矩 m 是作用在火箭上的唯一的力 矩，m 也可以按照下列公式用系数 $C_{m}$ 表示

$$
m = \frac {1}{2} \rho V ^ {2} A l C _ {m} \tag {13.1-11}
$$

力矩系数 $C_{m}$ 也是四个变数 $\alpha, \gamma, M$ 和 Re 的函数

$$
C _ {m} = C _ {m} (\alpha , \gamma , M, \mathrm{Re}) \tag {13.1-12}
$$

如果 I 是火箭对于重心的瞬时的横向转动惯量, 方程(13.1-6)里的 N 就是

$$
N = \frac {m}{I} \tag {13.1-13}
$$

利用以上引入的符号，运动的微分方程组可以写成以下形式

$$
\begin{array}{l} \frac {d r}{d t} = v _ {r} \\ \frac {d \theta}{d t} = \frac {v _ {\theta}}{r} \\ \frac {d \beta}{d t} = \dot {\beta} \\ \end{array}
$$

$$
\frac {d v _ {r}}{d t} = \Sigma \sin \beta + (v _ {\theta} + w) \Lambda - v _ {r} \Delta + r \left(\frac {v _ {\theta}}{r} \pm \Omega\right) ^ {2} - g \left(\frac {r _ {0}}{r}\right) ^ {2} = F
$$

$$
\frac {d v _ {\theta}}{d t} = \Sigma \cos \beta - v _ {r} \Lambda - (v _ {\theta} + w) \Delta - 2 v _ {r} \left[ \frac {v _ {\theta}}{r} \pm \Omega \right] + \frac {v _ {\theta} v _ {r}}{r} = G
$$

$$
\frac {d \dot {\beta}}{d t} = \frac {1}{r} \left\{\Sigma \cos \beta - v _ {r} \Lambda - (v _ {0} + w) \Delta - 2 v _ {r} \left[ \frac {v _ {0}}{r} \pm \Omega \right] \right\} + N = H \tag {13.1-14}
$$

这个方程组是六个未知函数 $r, \theta, \beta, v_r, v_\theta$ 和 $\dot{\beta}$ 的一阶方程组。如果要解这个方程组，就必须先知道开始时 $(t = 0)$ 这些未知函数的初始值；而且，推力 $S$ ，重量 $W$ 和转动惯量 $I$ 在每一时刻 $t$ 的瞬时值也必须事先给定。如果要确定各个空气动力，升降舵角 $\gamma$ 的运动也要用一个时间函数 $\gamma(t)$ 事先给定。大气的状态也必须知道，即风速 $w$ ，密度 $\rho$ ，空气的黏性系数 $\mu$ 以及音速 $a$ 都必须是高度 $r$ 的已知的函数。冲角 $\alpha$ 不能预先给定，它必须根据角度 $\beta$ 和相对的空气速度向量 $V$ 来计算。

我们将取标准大气状态和弹体、发动机的额定参数作为式(13.1-14)的参数。利用这些具体的数据，只要给定了升降舵角度 $\gamma$ 的运动规律 $\gamma = \gamma(t)$ ，我们就可以把方程组(13.1-14)积分，从而把火箭的飞行路线（弹道）计算出来。计算工作可以用计算机完成。这样计算出来的飞行路线，是一个标准的火箭在标准的大气状态下的飞行路线，这也就是标准飞行路线或标准弹道。

标准弹道的最重要的特性就是它的射程。所谓射程就是发射点和着陆点之间的距离。所谓火箭的制导问题就是要算出火箭发动机合适的关机时间并且找出飞行过程中升降舵角度的合适的运动规律，使得射程正好是我们所需要的数值。对于标准火箭在标准大气中的制导问题，可以在火箭发射之前用数学方法完 全解决，因为计算这条标准弹道所需要的全部资料都是已知的或者是预先给定了的。

#### 13.2 摄动方程

实际的大气的特性并不一定与所说的标准大气状态相符合。每一个高度上的风速都随气候条件变化；温度 T 也是随时间变化的。因此，我们可以想到，由于大气条件的不同，实际的飞行弹道与标准弹道一定也有些差别。实际的火箭在重量以及发动机性能等方面与理想的标准火箭也总会有些差别，因此，如果升降舵角度 $\gamma$ 仍然采用原来给定的动作程序，那么，实际的飞行弹道就会与标准弹道不同。所以，实际的火箭的制导问题就是要适当地随时修正升降舵角度的动作程序，设法使实际的射程与标准弹道的射程相同，准确无误地在标准着陆点着陆。因为火箭的速度非常高，这样一个制导问题就不能用普通的方法来解决，在普通的制导问题（譬如汽车或轮船的驾驶问题）中，因为速度相当低，惯性作用相当小，所以只要随时根据位置的偏差改正运动路线就可以使总的运动路线符合要求，完全不需要考虑惯性的影响。但是，对于像火箭这样的高速度飞行器的情形来说，就不能只根据运动学的考虑来进行操纵，因为惯性作用相当大，所以，必须考虑系统的动力学的效应才能使路线符合要求，对于这种情形，制导问题就必须依靠高速的自动计算系统来解决，对于每一个离开标准情况的偏差，这个计算系统都能在一段几乎等于零的时间内发生反应，同时发出修正运动状态的信号。我们把实现这种制导的控制系统称为制导系统。

一般性的制导问题实在是非常困难的。但是，我们可以相信离开标准状态的偏差总是很小的，因为，标准弹道毕竟是一条最有代表性的平均弹道。这个事实使我们立刻想到，作为初步近似只要考虑偏差的一阶量就够了。这个“线性化”的做法就是弹道摄动理论的基础。经过线性化以后，新的方程组（当然是线性方程组）的系数都只是根据标准弹道的参数计算出来的，一般说来，这些系数都是随时间变化的。我们关于远程火箭的制导问题所作的讨论也就是这一类控制系统设计的一个例子。这个例子的特定的设计要求，就是设法消除射程的误差。这里，被控制的“输入”就是升降舵角度的修正动作。在以下的讨论中我们就通过具体的情况来说明这些概念。

本章我们用符号上的横线“-”表示标准弹道的各个状态分量，用 $\delta$ 符号表示相同时间上各个状态分量的偏差。所以实际的飞行路线的各个状态分量就是

$$
r = \bar {r} + \delta r, \quad \theta = \bar {\theta} + \delta \theta , \quad \beta = \bar {\beta} + \delta \beta
$$

$$
v _ {r} = \overline {{{{v}}}} _ {r} + \delta v _ {r}, \quad v _ {\theta} = \overline {{{{v}}}} _ {\theta} + \delta v _ {\theta}, \quad \dot {\beta} = \overline {{{{\beta}}}} + \delta \dot {\beta} \tag {13.2-1}
$$

实际的大气状态与标准大气状态之间的偏差是用密度偏差 $\delta\rho$ ，温度偏差 $\delta T$ 和风

速偏差 $\delta w$ 来表示的, 所以

$$
\rho = \overline {{\rho}} + \delta \rho , \quad T = \overline {{T}} + \delta T, \quad w = \overline {{w}} + \delta w \tag {13.2-2}
$$

如果我们假设在任何一个高度上空气的化学成分都与标准大气在这个高度上的成分相同，那么，只要知道 $\delta\rho$ 和 $\delta T$ 也就可以计算出压力偏差（如果需要的话)。假设实际的火箭与标准火箭之间只有重量偏差 $\delta W$ 和转动惯量偏差 $\delta I$ ,也就是说

$$
W = \overline {{W}} + \delta W, \quad I = \bar {I} + \delta I \tag {13.2-3}
$$

还假设推力 S 与标准值完全相同。此外，火箭的尾翼面积 A 以及方程(13.1-10)和(13.1-12)所表示的空气动力特性也都假定是不变的。

把方程(13.2-1)，(13.2-2)和(13.2-3)代入方程(13.1-14)，然后，再从每一个方程里减去相应的标准飞行路线的方程，根据线性化的原则只保留各个偏差的一阶量。我们就得到下列方程

$$
\frac {d \delta r}{d t} = \delta v _ {r}
$$

$$
\frac {d \delta \theta}{d t} = - \frac {\overline {{v}} _ {0}}{\overline {{r}} ^ {2}} \delta r + \frac {1}{\overline {{r}}} \delta v _ {0}
$$

$$
\frac {d \delta \beta}{d t} = \delta \dot {\beta} \tag {13.2-4}
$$

$$
\frac {d \delta v _ {r}}{d t} = a _ {1} \delta r + a _ {2} \delta \beta + a _ {3} \delta v _ {r} + a _ {4} \delta v _ {0} + a _ {5} \delta \gamma + a _ {6} \delta \rho + a _ {7} \delta T + a _ {8} \delta w + a _ {9} \delta W
$$

$$
\frac {d \delta v _ {0}}{d t} = b _ {1} \delta r + b _ {2} \delta \beta + b _ {3} \delta v _ {r} + b _ {4} \delta v _ {0} + b _ {5} \delta \gamma + b _ {6} \delta \rho + b _ {7} \delta T + b _ {8} \delta w + b _ {9} \delta W
$$

$$
\frac {d \delta \beta}{d t} = c _ {1} \delta r + c _ {2} \delta \beta + c _ {3} \delta v _ {r} + c _ {4} \delta v _ {\theta} + c _ {5} \delta \gamma + c _ {6} \delta \rho + c _ {7} \delta T + c _ {8} \delta w + c _ {9} \delta W + c _ {1 0} \delta I \tag {13.2-5}
$$

方程中的系数 $a_{i}, b_{i}, c_{i}$ 都是式(13.1-14)所定义的函数 $F, G, H$ 在标准弹道上计算的偏导数。例如

$$
a _ {1} = \left(\frac {\overline {{\partial F}}}{\partial r}\right), \quad a _ {2} = \left(\frac {\overline {{\partial F}}}{\partial \beta}\right), \quad a _ {3} = \left(\frac {\overline {{\partial F}}}{\partial v _ {r}}\right)
$$

$$
a _ {4} = \left(\frac {\overline {{\partial F}}}{\partial v _ {0}}\right), \quad a _ {5} = \left(\frac {\overline {{\partial F}}}{\partial \gamma}\right), \quad a _ {6} = \left(\frac {\overline {{\partial F}}}{\partial \rho}\right)
$$

$$
a _ {7} = \left[ \frac {\overline {{\partial F}}}{\partial T} \right], \quad a _ {8} = \left[ \frac {\overline {{\partial F}}}{\partial w} \right], \quad a _ {9} = \left[ \frac {\overline {{\partial F}}}{\partial W} \right] \tag {13.2-6}
$$

这些系数的详细表达式见本章附录。

方程(13.2-4)和(13.2-5)是六个偏差量的变系数线性微分方程组。如果已知大气状态的偏差 $\delta\rho,\delta T$ 和 $\delta w$ ，并且给定 $\delta\gamma,\delta W$ 和 $\delta I$ ，则从这个方程组里我们可以解出 $\delta r,\delta\theta,\delta\beta,\delta v_{r},\delta v_{\theta}$ 和 $\delta\dot{\beta}$ 。然而，制导问题的提法和这个问题是不同的，在制导系统的设计里要求根据弹体运动的状态参数来确定控制函数 $\delta\gamma$ （升降舵的修正 程序）使射程偏差为零。正如德瑞尼克所建议的，这个制导问题可以用布利斯(Bliss)的伴随函数法来解决 $^{[6]}$ 。

#### 13.3 伴随方程

设 $y_{i}(t)(i=1,2,\cdots,n)$ 是由下列 n 阶线性微分方程组确定的函数

$$
\frac {d y _ {i}}{d t} - \sum_ {j = 1} ^ {n} a _ {i j} y _ {j} = Y _ {i} (t), \quad i = 1, 2, \dots , n \tag {13.3-1}
$$

其中 $a_{ij}$ 是给定的系数, 它们可以是时间 t 的函数。 $Y_{i}(t)$ 是“驱动”函数（输入)。现在我们再引进一组新的函数 $\lambda_{i}(t)(i=1,2,\cdots,n)$ , 它们满足下列齐次方程组

$$
\frac {d \lambda_ {i}}{d t} + \sum_ {j = 1} ^ {n} a _ {j i} \lambda_ {j} = 0, \quad i = 1, 2, \dots , n \tag {13.3-2}
$$

这样一组函数 $\lambda(t)$ 就称为原来一组 $y_{i}(t)$ 的伴随函数。方程(13.3-2)称为(13.3-1)的伴随方程。用 $\lambda_{i}$ 乘方程(13.3-1)，再用 $y_{i}$ 乘方程(13.3-2)，然后再对于 i 把这些方程加起来，我们就得出

$$
\frac {d}{d t} \sum_ {i = 1} ^ {n} \lambda_ {i} y _ {i} - \sum_ {i = 1} ^ {n} \sum_ {j = 1} ^ {n} (a _ {i j} \lambda_ {i} y _ {j} - a _ {j i} \lambda_ {j} y _ {i}) = \sum_ {i = 1} ^ {n} \lambda_ {i} Y _ {i}
$$

显然，双重和符号后面的两项刚好互相对消，所以，我们就得到

$$
\frac {d}{d t} \sum_ {i = 1} ^ {n} \lambda_ {i} y _ {i} = \sum_ {i = 1} ^ {n} \lambda_ {i} Y _ {i} \tag {13.3-3}
$$

把这个方程从时刻 $t=t_{1}$ 积分到时刻 $t=t_{2}$ ，我们有

$$
\sum_ {i = 1} ^ {n} \lambda_ {i} y _ {i} \Big | _ {t = t _ {2}} = \sum_ {i = 1} ^ {n} \lambda_ {i} y _ {i} \Big | _ {t = t _ {1}} + \int_ {t _ {1}} ^ {t _ {2}} \left(\sum_ {i = 1} ^ {n} \lambda_ {i} Y _ {i}\right) d t \tag {13.3-4}
$$

布利斯称这个方程为基本公式。

对于我们所讨论的远程导弹问题, $y_{i}$ 就是那些摄动量

$$
y _ {1} = \delta r, \quad y _ {2} = \delta \theta , \quad y _ {3} = \delta \beta
$$

$$
y _ {4} = \delta v _ {r}, \quad y _ {5} = \delta v _ {\theta}, \quad y _ {6} = \delta \dot {\beta} \tag {13.3-5}
$$

根据方程(13.2-4)和(13.2-5)，这时伴随函数满足下列方程组

$$
\begin{array}{l} - \frac {d \lambda_ {1}}{d t} = - \frac {\overline {{{v}}} _ {0}}{\overline {{{r}}} ^ {2}} \lambda_ {2} + a _ {1} \lambda_ {4} + b _ {1} \lambda_ {5} + c _ {1} \lambda_ {6} \\ - \frac {d \lambda_ {2}}{d t} = 0 \\ - \frac {d \lambda_ {3}}{d t} = + a _ {2} \lambda_ {4} + b _ {2} \lambda_ {5} + c _ {2} \lambda_ {6} \\ - \frac {d \lambda_ {4}}{d t} = \lambda_ {1} + a _ {3} \lambda_ {4} + b _ {3} \lambda_ {5} + c _ {3} \lambda_ {6} \\ \end{array}
$$

$$
\begin{array}{l} - \frac {d \lambda_ {5}}{d t} = \frac {1}{\bar {r}} \lambda_ {2} + a _ {4} \lambda_ {4} + b _ {4} \lambda_ {5} + c _ {4} \lambda_ {6} \\ - \frac {d \lambda_ {6}}{d t} = \lambda_ {3} \tag {13.3-6} \\ \end{array}
$$

各个输入 $Y_{i}$ 为

$$
Y _ {1} = Y _ {2} = Y _ {3} = 0 \tag {13.3-7}
$$

和

$$
Y _ {4} = a _ {5} \delta \gamma + a _ {6} \delta \rho + a _ {7} \delta T + a _ {8} \delta w + a _ {9} \delta W
$$

$$
Y _ {5} = b _ {5} \delta \gamma + b _ {6} \delta \rho + b _ {7} \delta T + b _ {8} \delta w + b _ {9} \delta W
$$

$$
Y _ {6} = c _ {5} \delta \gamma + c _ {6} \delta \rho + c _ {7} \delta T + c _ {8} \delta w + c _ {9} \delta W + c _ {1 0} \delta I \tag {13.3-8}
$$

#### 13.4 射程控制基本方程

方程(13.3-6)并不能完全确定 $\lambda$ 函数。如果要完全确定 $\lambda$ 函数，就必须给出在某一个一定时刻的一组 $\lambda$ 值。至于应该在哪一个时刻选取一组 $\lambda$ 的值并且究竟等于什么数值，这个问题是与特定的控制系统设计的要求有关的。在我们的制导问题中，我们的设计要求射程偏差是零。或者，作为一次近似，要求射程偏差的一阶量为零。所以，我们感兴趣的量就是 $\delta\theta_{2}$ （火箭落地时刻的 $\delta\theta$ ）。以后，我们用下标“ $_{2}$ ”表示落地时刻的各个量。下面可以看到：射程偏差为零的条件足以完全确定所有的 $\lambda$ 。

如果 $t_{2}$ 是实际的火箭落地时刻， $\bar{t}_{2}$ 是标准弹道的落地时刻，于是，可以用一阶偏差 $\delta$ 近似地代表绝对偏差 $\Delta$

> 此处省略原书 **图 13.4-1**

$$
t _ {2} = \bar {t} _ {2} + \delta t _ {2} \tag {13.4-1}
$$

同样

$$
r _ {2} = \bar {r} _ {2} + \delta r _ {2}
$$

$$
\theta_ {2} = \overline {{{{\theta}}}} _ {2} + \delta \theta_ {2} \tag {13.4-2}
$$

当用一阶偏差近似地表示全偏差, 用 $(\delta\cdot)_{t}$ 表示 t 时刻的等时偏差, 则有

$$
\delta r _ {2} = \left(\bar {v} _ {r}\right) _ {t = \tau_ {2}} \delta t _ {2} + (\delta r) _ {t = \tau_ {2}}
$$

$$
\delta \theta_ {2} = \frac {1}{r _ {0}} (\overline {{v}} _ {0}) _ {t = 7 _ {2}} \delta t _ {2} + (\delta \theta) _ {t = 7 _ {2}} \tag {13.4-3}
$$

然而，因为不论什么弹道的落地点都在地球表面上，即 $r_{2}=\bar{r}_{2}=r_{0}$ ,所以 $\delta r_{2}$ 一定是零。从方程组(13.4-3)中消去 $\delta t_{2}$ 就得

$$
\delta \theta_ {2} = \left[ - \frac {1}{\overline {{r}}} \left(\frac {\overline {{v}} _ {0}}{\overline {{v}} _ {r}}\right) \delta r + \delta \theta \right] _ {t = \tau_ {2}} \tag {13.4-4}
$$

因此，如果让各个 $\lambda$ 函数在标准落地时刻 $t=\bar{t}_{2}$ 时的值为

$$
\lambda_ {1} = - \frac {1}{r} \left[ \frac {\bar {v} _ {0}}{\bar {v} _ {r}} \right], \quad \lambda_ {2} = 1 \tag {13.4-5}
$$

$$
\lambda_ {3} = \lambda_ {4} = \lambda_ {5} = \lambda_ {6} = 0
$$

于是射程偏差就是

$$
\delta \theta_ {2} = \sum_ {i = 1} ^ {6} \lambda_ {i} y _ {i} \Big | _ {\iota = \tau_ {2}} = \left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {\iota = \tau_ {2}} \tag {13.4-6}
$$

如果标准弹道已经确定，则方程组(13.3-6)的各个系数就都是已知的时间函数。方程组(13.3-6)加上终点条件(13.4-5)唯一地完全确定伴随函数 $\lambda_{i}$ 。可以用计算机从 $t=\bar{t}_{2}$ 开始把方程组(13.3-6)进行“倒向”积分（在逆转了的时间内)。伴随函数确定后，我们就可以利用式(13.3-4)来描述制导问题的设计要求

$$
\delta \theta_ {2} = 0 = \left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \dot {\delta \beta} \right] _ {t = t _ {1}}
$$

$$
+ \int_ {\tau_ {1}} ^ {\tau_ {2}} \left[ \lambda_ {4} Y _ {4} + \lambda_ {5} Y _ {5} + \lambda_ {6} Y _ {6} \right] d t \tag {13.4-7}
$$

这就是射程控制的基本方程。

#### 13.5 制导系统

对于远程飞航式地地导弹来说，从 t=0 到 $t=\bar{t}_{1}$ 是发动机工作的助推段，从 $t=\bar{t}_{1}$ 以后到落地时刻为止是滑翔段。在前面我们曾经假设推力 S 与标准值完全相同，这点对于飞航式导弹的冲压式发动机，在采取适当形式的推力控制条件下是可能的。发动机工作的时间对应于一定的射程而言也是固定不变的，即我们准确地按时间 $t=\bar{t}_{1}$ 关闭发动机。在助推段可以不采用弹道控制，也可以采用弹道控制，我们将区别这两种情况来讨论制导系统的设计问题以满足基本方程(13.4-7)。

第一种情况：我们只控制滑翔段的弹道，即我们选择升降舵在滑翔段的机动 规律，使基本方程(13.4-7)在任意干扰规律作用下得到满足。由于助推段的弹道是不控制的，所以在一般情况下式(13.4-7)中的第一项 $\left[\lambda_1\delta r + \lambda_2\delta \theta +\lambda_3\delta \beta +\lambda_4\delta v_r + \lambda_5\delta v_0 + \lambda_6\delta \dot{\beta}\right]_{t = 7_1}$ 自然是不等于零的，但是我们的制导问题并没有必要要求基本方程(13.4-7)中的两项都分别为零。我们只要求在任意干扰规律作用下这两项的总和为零就足够了。当发动机在 $t = \overline{t}_{1}$ 关机以后，根据实际测得的弹道参数和事先存储的标准弹道参数，我们立即可以从制导计算机里得到

$$
\left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \dot {\delta \beta} \right] _ {t = 7 _ {1}} = K \tag {13.5-1}
$$

对应助推段的不同干扰情况来讲 K 当然是变化的，但是只要发动机一关机,K 就是一个确定的数。所以从这个意义上讲对于滑翔段 K 是一个常值。这样的常值偏差我们很容易在滑翔段用一个常值的升降舵偏角来消除掉。现在来看基本方程(13.4-7)的第二项，考虑式(13.3-8),并引入符号

$$
\begin{array}{l} d _ {5} = \lambda_ {4} a _ {5} + \lambda_ {5} b _ {5} + \lambda_ {6} c _ {5} \\ d _ {6} = \lambda_ {4} a _ {6} + \lambda_ {5} b _ {6} + \lambda_ {6} c _ {6} \\ d _ {7} = \lambda_ {4} a _ {7} + \lambda_ {5} b _ {7} + \lambda_ {6} c _ {7} \\ d _ {8} = \lambda_ {4} a _ {8} + \lambda_ {5} b _ {8} + \lambda_ {6} c _ {8} \\ D = - \left(\lambda_ {4} a _ {9} + \lambda_ {5} b _ {9} + \lambda_ {6} c _ {9}\right) \delta W - \lambda_ {6} c _ {1 0} \delta I \tag {13.5-2} \\ \end{array}
$$

和

$$
\delta \gamma = \delta \gamma_ {1} + \delta \gamma_ {2} \tag {13.5-3}
$$

于是有

$$
\begin{array}{l} \int_ {\tau_ {1}} ^ {\tau_ {2}} \left[ \lambda_ {4} Y _ {4} + \lambda_ {5} Y _ {5} + \lambda_ {6} Y _ {6} \right] d t = \int_ {\tau_ {1}} ^ {\tau_ {2}} d _ {5} \delta \gamma_ {1} d t \\ + \int_ {\tau_ {1}} ^ {\tau_ {2}} [ d _ {5} \delta \gamma_ {2} + d _ {6} \delta \rho + d _ {7} \delta T + d _ {8} \delta w - D ] d t \tag {13.5-4} \\ \end{array}
$$

我们把滑翔段升降舵偏角分成两部分，其中常值部分 $\delta\gamma_{1}$ 用以消除助推段干扰的影响 K,这样就可以确定

$$
\delta \gamma_ {1} = - \frac {K}{\int_ {\tau_ {1}} ^ {\tau_ {2}} d _ {5} d t} \tag {13.5-5}
$$

现在我们讨论如何确定 $\delta\gamma_{2}$ 来消除滑翔段干扰的影响。对于滑翔段 $\delta W$ 和 $\delta I$ 是常值性质的干扰，譬如说，在燃料箱内装有液面传感器，发动机关机后就可以确定剩余的燃料量，这样，只要一关机， $\delta W, \delta I$ 也就确定下来了。然而，大气状态的偏差量 $\delta\rho, \delta T$ 和 $\delta w$ 就不同了，只有随时随地加以测量才能得到这些量的数据。它们的变化可以是任意的，事前无法确定它们的规律。因此，要求式(13.5-4)中右端第二项积分在任意干扰规律下等于零的条件就是被积函数必须在整个时间区间上恒等于零，亦即

$$
d _ {5} \delta \gamma_ {2} + d _ {6} \delta \rho + d _ {7} \delta T + d _ {8} \delta w = D \tag {13.5-6}
$$

方程组(13.2-5)可以改写成

$$
a _ {5} \delta \gamma + a _ {6} \delta \rho + a _ {7} \delta T + a _ {8} \delta w = A
$$

$$
b _ {5} \delta \gamma + b _ {6} \delta \rho + b _ {7} \delta T + b _ {8} \delta w = B
$$

$$
c _ {5} \delta \gamma + c _ {6} \delta \rho + c _ {7} \delta T + c _ {8} \delta w = C \tag {13.5-7}
$$

其中

$$
A = \frac {d}{d t} \delta v _ {r} - a _ {1} \delta r - a _ {2} \delta \beta - a _ {3} \delta v _ {r} - a _ {4} \delta v _ {\theta} - a _ {9} \delta W
$$

$$
B = \frac {d}{d t} \delta v _ {\theta} - b _ {1} \delta r - b _ {2} \delta \beta - b _ {3} \delta v _ {r} - b _ {4} \delta v _ {\theta} - b _ {\theta} \delta W
$$

$$
C = \frac {d}{d t} \delta \dot {\beta} - c _ {1} \delta r - c _ {2} \delta \beta - c _ {3} \delta v _ {r} - c _ {4} \delta v _ {\theta} - c _ {9} \delta W - c _ {1 0} \delta I \tag {13.5-8}
$$

如果弹上的测速定位系统和制导计算机随时测量和计算 A, B, C 这三个量，而且，弹上仪器又能把 $\delta\rho, \delta T$ 和 $\delta w$ 这三个量中的某一个随时加以测量，利用这些测量的结果，根据方程组(13.5-7)中的两个方程就可以把其余两个大气情况偏差量用 $\delta\gamma_{2}$ 和已知的时间函数表示出来（譬如说，弹上仪器随时把温度偏差 $\delta T$ 测量出来，再从测得的三个量 A, B, C 中选用 A 和 B 两个量，最后，利用方程组(13.5-7)的前两个方程就可以把 $\delta\rho$ 和 $\delta w$ 用已知的时间函数和 $\delta\gamma$ 表示出来）。这个作法的实质也就是借助于火箭本身来确定 $\delta\rho, \delta T$ 和 $\delta w$ 。这样定出 $\delta\rho, \delta T$ 和 $\delta w$ 以后，把这些量代入方程(13.5-6)就得出 $\delta\gamma_{2}$ 的方程

$$
\delta \gamma_ {2} = \frac {1}{d _ {5}} \left[ D - d _ {6} \delta \rho - d _ {7} \delta T - d _ {8} \delta w \right] \tag {13.5-9}
$$

在式(13.5-5)所确定的常值 $\delta\gamma_{1}$ 上再叠加按式(13.5-9)确定的升降舵机动规律 $\delta\gamma_{2}$ ，我们就可以满足基本方程(13.4-7)。前面已经讲过，这些 a, b, c 和 A, B, C, D 中有一部分是可以预先根据标准弹道计算出来的，而另一部分则是根据对于火箭的位置和速度的测量得出的。如果在实际飞行中使升降舵就按照 $\delta\gamma_{1} + \delta\gamma_{2}$ 的规律运动，那么，尽管实际飞行情况与标准情况之间有各种偏差，火箭还是在规定的地点着陆，这样就达到了预定的目的：射程偏差等于零。

如果对助推段的弹道也加以控制, 就可以做到使基本方程(13.4-7)的两项分别为零。不难看出, 只要在助推段和滑翔段升降舵都按照式(13.5-9)所确定的规律机动, 控制整条弹道, 两项分别为零的要求就满足了。我们同样可以对式(13.4-7)的第一项应用布利斯基本公式, 取起飞时刻为积分的下限, 发动机关机时刻为积分上限, 于是

$$
\left[ \lambda_ {1} \delta \gamma + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {t = 7 _ {1}}
$$

$$
= \left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {t = 0}
$$

$$
+ \int_ {0} ^ {7 _ {1}} \left[ \lambda_ {4} Y _ {4} + \lambda_ {5} Y _ {5} + \lambda_ {6} Y _ {6} \right] d t \tag {13.5-10}
$$

在 t=0 时，显然弹道参数偏差 $\delta r, \delta \theta, \cdots$ 等均为零。所以式(13.4-7)中右边的第一项等于零和式(13.5-10)右边的第二项等于零是等效的。而式(13.5-10)右边的第二项的形式完全类似于式(13.4-7)右边的第二项。助推段和滑翔段的运动方程是完全一样的，都用式(13.1-14)方程组描述，只是在滑翔段的推力用 S=0 代入就可以了，所以它们的摄动方程和伴随方程也都完全一样。在计算助推段伴随函数时所用的终点条件就是用滑翔段伴随方程由 $t=\bar{t}_{2}$ “倒积”到 $t=\bar{t}_{1}$ 时刻的值 $\lambda_{1}(\bar{t}_{1}), \lambda_{2}(\bar{t}_{1}), \cdots, \lambda_{6}(\bar{t}_{1})$ ，所以把式(13.5-10)代入式(13.4-7)得到一个统一的积分形式

$$
\left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {t = \tau_ {2}} = \int_ {0} ^ {\tau_ {2}} \left[ \lambda_ {4} Y _ {4} + \lambda_ {5} Y _ {5} + \lambda_ {6} Y _ {6} \right] d t \tag {13.5-11}
$$

$\lambda$ 函数仍由式(13.3-6)和(13.4-5)确定，积分从 $t = \overline{t}_2$ 时刻开始一直“倒积”到 $t = 0$ 为止。由被积函数在全弹道恒等于零的条件导出了全弹道控制的统一规律。只要注意在助推段计算 $D$ 时需要代入 $\delta W$ 和 $\delta I$ 的瞬时偏差值。

我们还可以进一步看到：在导出射程控制基本方程式(13.4-7)时，积分的下限（弹道的起控时刻）并没有必要一定要求是发动机的关机时刻 $\bar{t}_{1}$ ,它可以是助推段或滑翔段的任意时刻 t,于是，基本方程可以有以下形式

$$
\begin{array}{l} \delta \theta_ {2} = 0 = \left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {t = t} \\ + \int_ {7} ^ {t _ {2}} \left[ \lambda_ {4} Y _ {4} + \lambda_ {5} Y _ {5} + \lambda_ {6} Y _ {6} \right] d t \tag {13.5-12} \\ \end{array}
$$

当然，必须考虑到升降舵的偏转角是有限制的，所以起控时刻 t 不能太晚。否则起控以前的干扰积累造成的偏差太大，有可能超过控制机构的最大可能限制，基本方程(13.5-12)的要求就不能满足了。例如，我们可以进行如下的估值，令

$$
\begin{array}{l} | \delta \gamma | \leqslant M _ {\delta \gamma} \\ | \delta \rho | \leqslant M _ {\delta \rho} \\ | \delta T | \leqslant M _ {\delta T} \\ \mid \delta w \mid \leqslant M _ {\delta w} \\ \mid \delta W \mid \leqslant M _ {\delta W} \\ \mid \delta I \mid \leqslant M _ {\delta I} \tag {13.5-13} \\ \end{array}
$$

则应有

$$
\begin{array}{l} \left. \left[ \lambda_ {1} \delta r + \lambda_ {2} \delta \theta + \lambda_ {3} \delta \beta + \lambda_ {4} \delta v _ {r} + \lambda_ {5} \delta v _ {\theta} + \lambda_ {6} \delta \dot {\beta} \right] _ {t = t} \right| \\ \leqslant \int_ {0} ^ {t} \left[ d _ {5} M _ {\delta 0} \operatorname{sign} d _ {3} + d _ {7} M _ {\delta T} \operatorname{sign} d _ {2} + d _ {8} M _ {\delta w} \operatorname{sign} d _ {3} + \left(\lambda_ {4} a _ {9} + \lambda_ {5} b _ {9} + \lambda_ {6} c _ {9}\right) M _ {\delta W} \right. \\ \end{array}
$$

$$
\times \operatorname{sign} \left(\lambda_ {4} a _ {9} + \lambda_ {5} b _ {9} + \lambda_ {6} c _ {9}\right) + \lambda_ {6} c _ {0} M _ {\delta I} \operatorname{sign} \left(\lambda_ {6} c _ {0}\right) ] d t \leqslant \left| \int_ {\bar {t}} ^ {\tau_ {2}} d _ {5} M _ {\delta \gamma} d t \right| \tag {13.5-14}
$$

同样，从式(13.5-11)我们也可以进一步看到：式(13.5-11)的积分上限也可以是全弹道的任意时刻。如果把 $(\lambda_1, \lambda_2, \lambda_3, \lambda_4, \lambda_5, \lambda_6)$ 看作是一个六维向量，而运动状态 $(\delta r, \delta \theta, \delta \beta, \delta v_r, \delta v_0, \delta \dot{\beta})$ 是另一个向量。则射程偏差为零的条件意味着要求制导系统在任意干扰作用下都要把运动状态向量在 $t = \bar{t}_2$ 时刻控制到 $(\lambda_1, \lambda_2, \lambda_3, \lambda_4, \lambda_5, \lambda_6)_{t = t_2}$ 这一已知法向量所决定的超平面上去。而全弹道控制则意味着受控的运动状态向量和另一已定的，但随时间变化着的伴随向量在全弹道上时正交。如果用全弹道控制来实现射程偏差为零的设计准则时则要求运动状态向量本身每时每刻和伴随向量正交。

制导系统的组成部分包括测速定位系统，制导计算机和升降舵的伺服控制机构。

从理论上讲，计算机收到测量信息时就必须立刻把 $\delta\gamma$ 算出来，不应该有时间的迟延，因为方程(13.5-9)是两个量在同一时刻的值相等的条件。计算出来的 $\delta\gamma_{1}$ 和 $\delta\gamma_{2}$ 与从标准弹道计算出来的已知的 $\overline{\gamma}$ 合并起来就给出实际的升降舵角应取的值 $\gamma=\overline{\gamma}+\delta\gamma$ 。根据这个信号 $\gamma$ 来转动升降舵的控制机构就可以用普通的反馈伺服系统的方法加以设计，使这个机构在反应速度，稳定性和准确性上都能满足要求。这里所用的计算机是安装在火箭上的，它从测速定位系统接收到关于位置和速度的信息，这就是整个控制系统的反馈部分。这里，适当地设计出来的计算机能够使系统具有规定的性能，它们的作用与普通的伺服系统里的放大器或补偿线路的作用是一样的。所以，从总的基本概念上来看，制导系统与以前各章研究过的普通的伺服系统是非常类似的。可是，制导系统是一种很复杂的系统，在它的设计工作中需要用到弹道摄动理论，因而也牵涉到伴随函数的概念。这个远程火箭的制导问题的例子，虽然简化得有些过分，可是，还可以用来说明怎样用弹道摄动理论来设计控制系统的问题。在这个例子里，只有使射程偏差等于零这样一个设计要求。在某些更复杂的系统里，往往会提出若干个设计要求，因而也就需要若干组伴随函数。虽然如此，设计那些系统的原则还是和所讲的简单例子相同。

#### 13.6 控制计算机

在现代化的控制系统中计算机的作用非常重要，所以在这里把它们的特性和对它们的要求一般地讨论一下。至于详细的情形，读者可以去参考这方面的专题文献。

常用的计算机有两类：一类是模拟计算机，另一类是数字计算机。模拟计算 机，正像它的名称的含义一样，是设计者所企图解决的问题的一个物理模拟。所以，模拟计算机也就是具有以下的性质的一个系统：描写这个系统的数学形式（譬如，系统的运动方程）和需要进行计算的问题的数学形式相同。这种计算机的输入总是某种物理量的值，例如，电压，电流，一个轴的转角的度数，一个弹簧的压缩量等。计算机按照它本身的构造的物理规律把这种输入转换成作为输出的其他的物理量，计算机的构造当然是设计者为了代表（模拟）预定的数学形式（或计算程序）而特别设计的。所以，在控制系统中，模拟计算机的输入就是被控制系统的某几个物理量的测量读数，计算机的输出就是一些指令信号，这些指令信号直接送到那些被控制量的个别的伺服系统中去。

与模拟计算机相反，数字计算机是用计数（数值计算）的方式工作的。问题的数据必须用数字的形式放到计算机里去，计算机就按照算术的规则以及其他必需的形式逻辑的规则根据输入的信息进行计算，最后，把计算的结果（输出）仍然用数字的形式表示出来。如果采用这种计算方法，就会产生两个很重要的结论：第一，必须适当地设计转换器（也就是送进输入信号和送出输出信号的装置),设法使数字计算机的“逻辑世界”与被控制系统的“物理世界”之间建立一种合适的转换关系，也就是说，转换器必须能把具体的物理量化为抽象的数字，也能把抽象的数字用具体的物理量表示出来。第二，必须把需要计算的问题明确地用数学方式（计算程序或方程等）表达出来。

在模拟计算机的情形里，问题的性质（数学性质）已经被计算机本身的构造决定了，也就是说，只能解决某些数学性质与计算机的构造的数学性质相同的特别的问题。可是，数字计算机的构造就并不是由某一个特别的物理问题或者某一类物理问题决定的（模拟计算机就是那样的!),而是由解决某一类计算问题所需要的逻辑规则所确定的（请注意计算的逻辑规则相同的问题并不一定是数学性质相同的问题!）。

当计算问题更加复杂的时候（例如这一章所讨论的制导问题的情形）模拟计算机就失去它的优越性，同时我们又可以看到两种计算机的第二个根本的区别：模拟计算机是问题的一个物理模拟装置，所以，计算问题越复杂，模拟计算机也就越复杂，如果它是一个机械系统，那么，系统中的齿轮组，球盘积分器的个数也就越多，而且还需要增加其他的装置；如果模拟计算机是电气的，那么，系统中的放大器的个数也就要越多。在机械的情形里，齿轮和接头的间隙总是不可避免的，虽然在简单的情形里这种影响可以忽略，可是当系统越来越庞大的时候，这些效应就逐渐增加，增加到一定的程度以后，系统的总间隙（或者称为“游隙”)就会比重要的输出量还大，于是这个计算机就毫无用处了。在电模拟机里，在电路中总是有随机的电磁干扰和噪声，这些作用也同样地会随着系统的增大而增加，没有十分有效的办法完全消除这种干扰。然而在高可靠的数字计算机中，这种噪声干 扰的可能性将大为减小，因为大规模集成电路广泛应用以后，可以用冗余技术和纠错技术去纠正那些由干扰引起的偶然性错误。

模拟计算机与数字计算机之间，第三个重要的区别就是可能达到的准确度。在模拟计算机里，对于各个有关的物理量的测量和处理总有一定的误差，而且根据一些理想化的物理定律来表示或设计实际的物理系统也必然有误差，所以模拟计算机的准确度也就受到限制。在实际情况中，最好的模拟计算机的准确度差不多是 1/10000，普通的模拟计算机只能准确到 1/100 或 2/100。对于某些具体问题来说，这种准确度已经够了，对于另外一些问题这种准确度就完全不够了。相反地，数字计算机所处理的是数字，所以，需要多么准确就可以做到多么准确。如果希望提高准确度，我们只要把代表每一个被处理的量的有效数字的位数增加就可以了。当然，整个计算机的准确度由于转换器的准确度的限制也还是有限制的，但是，这并不能改变这样的事实：在需要准确度很高的情况中，数字计算机总是比模拟计算机好得多。

两类计算机之间还有第四个不同之处。我们可以说，模拟计算机是“实时”工作的，这也就是说，它连续地给出它所处理的问题的解，而且，在每一个时刻这个给出的解都相应于在同一时刻进入计算机的所有的输入值。与此相反，数字计算机的工作方式是：把问题先化为数值计算的问题，然后再去解这个计算问题的一个明确的“逻辑模型”。所以，数字计算机只能在一系列离散的时刻上给出输出的数值。因此，就发生了两个问题：第一，如何用内插法把各个离散时刻之间的输出确定出来？第二，如何根据已有输出值用预报法预报以后的输出值，从而可以避免输出的时滞。很明显，如果计算过程所用的时间比被控制系统的时间常数小得很多，就不必考虑预报问题，同时也就可以认为计算机是“实时”工作的。在这一点上，现代的电子数字计算机对于前面所讨论的远程火箭的制导问题来说似乎是足够迅速了，但是，对于高速度的导弹来说，电子计算机的时滞的影响还必须在控制系统的设计中加以考虑。

#### 13.7 问题的一般提法

使用弹道摄动理论设计远程火箭制导系统的讨论，对建立一类高精度要求的变参数线性自动控制系统设计的一般方法提供了启示。远程火箭的飞行由于受到外干扰的影响偏离标准弹道，如果弹上仪器可以把 $\delta\rho,\delta T$ 和 $\delta w$ 这三个干扰中的一个直接加以测量，并利用方程组(13.5-7)来确定另外两个干扰，实质上也就是借助于火箭本身来间接测量干扰，那么，尽管实际飞行条件与标准条件之间有各种未知的偏差，我们在升降舵的机动规律中引进了经过适当变换的含有干扰信息的控制信号后，总能使火箭命中预定弹着点，即射程偏差为零。这样的设计思 想和处理方法可以推广为一般的变参数线性系统对一类高精度指标的设计方法。

设控制对象的特性随时间而变化，它的运动规律由下列变参数的线性微分方程组所描述

$$
\frac {d x _ {i}}{d t} = \sum_ {j = 1} ^ {n} a _ {i j} (t) x _ {j} + \sum_ {k = 1} ^ {m} b _ {i k} (t) u _ {k} + f _ {i} (t), \quad i = 1, 2, \dots , n
$$

或者用向量形式描述

$$
\frac {d \boldsymbol {x}}{d t} = A (t) \boldsymbol {x} + B (t) \boldsymbol {u} + \boldsymbol {f} (t) \tag {13.7-1}
$$

x 为 n 维状态向量, $A(t)$ 为已知时间函数的 $n \times n$ 阶矩阵, 它反映了各个相坐标之间在不同时刻的相互作用关系; u 为 m 维控制向量; $B(t)$ 为 $n \times m$ 阶矩阵, 表征控制向量对状态向量在不同时刻的作用关系; $f(t)$ 为 n 维干扰向量, 对 $f(t)$ 仅加以幅值有界的限制。

如果 $f(t)$ 及 $u(t)$ 为给定的时间函数，并且已知受控对象的初始状态为 $x(t_{0}) = x_{0}$ ，则式(13.7-1)唯一地决定受控对象在 n 维状态空间中的轨道。但是 $f(t)$ 的变化规律是不由我们所掌握的，故 $x(t)$ 受 $f(t)$ 变化的影响，不能保持预定的轨道。例如民航客机总是力图保持水平等高的飞行状态，但大气紊流和阵风的影响迫使飞机偏离预定的飞行规律。我们的任务在于设计 u 的规律，控制在状态空间中的运动轨道，尽量减小以至完全消除干扰作用所产生的不利影响。

控制器本身（如机电、液压系统）具有本征的运动特性，如具有一定的惯性。我们假定控制器运动规律可用以下微分方程组来描述

$$
\frac {d u _ {j}}{d t} = \sum_ {k = 1} ^ {m} d _ {j k} (t) u _ {k} + \sum_ {i = 1} ^ {n} c _ {j i} (t) x _ {i} + U _ {j} (t), \quad j = 1, 2, \dots , m
$$

或者用向量形式写成

$$
\frac {d \boldsymbol {u}}{d t} = D (t) \boldsymbol {u} + C (t) \boldsymbol {x} + \boldsymbol {U} (t) \tag {13.7-2}
$$

$D(t)$ 为 $m \times m$ 阶矩阵，反映控制器本征的运动特性和控制器坐标之间的相互作用； $C(t)$ 为 $m \times n$ 阶矩阵，即通常的偏差反馈控制规律； $U(t)$ 为我们将要讨论的干扰补偿规律。

我们可以提出这样的问题: 假定 $U(t)=0$ , 即不进行干扰补偿, 对 $f(t)$ 只加以幅值有界的限制条件

$$
\| \boldsymbol {f} (t) \| \leqslant M
$$

于是，我们将选择反馈矩阵 $C(t)$ 来使干扰造成的影响趋于极小。例如我们要控制的泛函指标为第一个相坐标 $x_{1}(t)$ 偏离标准轨道 $\overline{x}_1(t)$ 的差值平方的积分 $\int_{t_0}^{t_k}\left[x_1(t) - \overline{x}_1(t)\right]^2 dt$ 或者 $x_{1}$ 在终端的取值 $x_{1}(t_k)$ 。一般的控制泛函指标有以下形式

$$
I = I [ \boldsymbol {x}, C (t), \boldsymbol {f} (t) ]
$$

每当已经选定反馈矩阵 $C(t)$ 后，泛函指标 I 就由初始条件和干扰变化规律唯一地决定，我们可以针对每一个已选定的矩阵 $C(t)$ 选取最不利的干扰变化规律 $f(t)$ 使泛函 I 达到最大值

$$
I = \max _ {f (t)} I [ x (t), C (t), f (t) ]
$$

这样，每一个矩阵 $C(t)$ 将对应一个最不利的干扰规律造成的最大偏差 $\max_{f(t)} I[x(t), C(t), f(t)]$ , 我们的任务是设计反馈矩阵 $C(t)$ , 使这一最不利 $f(t)$ 干扰规律造成的最大偏差趋于极小, 即

$$
I = \min _ {C (t)} \max _ {f (t)} I [ x (t), C (t), f (t) ]
$$

这种最优化问题的提法把控制规律选择范围限制在反馈矩阵 $C(t)$ 之内，所以即使我们找到 $C(t)$ 满足了 $\min\max$ 的最优化条件，但是任意变化的 $f(t)$ 规律总还是会引起一定的 I, $C(t)$ 最优化条件不能完全消除外干扰的影响。因此，在控制规律式(13.7-2)中必须引入干扰补偿向量 $U(t)$ 。

因此，我们在充分利用选择 $C(t)$ 来满足稳定性和精度的基本要求外，我们还将通过引进补偿向量在更大程度上消除外干扰的影响。

如果要求在系统运行过程中的每一时刻指标 I 都完全为零而且又是能够实现的，我们称之为过程不变性问题。

如果只要求在系统运行的终端时刻指标 I 为零, 我们称之为终端不变性问题。

#### 13.8 过程不变性问题

把式(13.7-1)和(13.7-2)联立起来我们就得到描绘整个系统的微分方程组

$$
\frac {d \boldsymbol {x}}{d t} = A (t) \boldsymbol {x} + B (t) \boldsymbol {u} + \boldsymbol {f} (t)
$$

$$
\frac {d \boldsymbol {u}}{d t} = C (t) \boldsymbol {x} + D (t) \boldsymbol {u} + \boldsymbol {U} (t)
$$

或者

$$
\frac {d}{d t} \left[ \begin{array}{c} \boldsymbol {x} \\ \boldsymbol {u} \end{array} \right] = P (t) \left[ \begin{array}{c} \boldsymbol {x} \\ \boldsymbol {u} \end{array} \right] + \left[ \begin{array}{c} \boldsymbol {f} (t) \\ \boldsymbol {U} (t) \end{array} \right]
$$

式中

$$
P (t) = \left[ \begin{array}{l l} A (t) & B (t) \\ C (t) & D (t) \end{array} \right] \tag {13.8-1}
$$

假定在进行补偿向量 $U(t)$ 的设计之前我们已经出于稳定性和精度的各种考虑选定了反馈矩阵 $C(t)$ ，因此将认为式(13.8-1)中 $P(t)$ 是已知的 $(n+m)\times$

$(n+m)$ 阶函数矩阵。

在系统式(13.8-1)中我们将通过 m 维控制向量 u 来控制一个 m 维的指标向量 $I(t)$ 使满足过程不变性的设计要求。为达到这个要求，可通过引进 m 维补偿向量 $U(t)$ 驱动系统的状态向量在 $n+m$ 维的相空间运动，并在任意可测量的干扰作用下使指标 $I(t)\equiv0$

$$
\boldsymbol {I} (t) = \xi (t) \left[ \begin{array}{l} \boldsymbol {x} (t) \\ \boldsymbol {u} (t) \end{array} \right] \tag {13.8-2}
$$

$\xi(t)$ 为给定的 $m\times(n+m)$ 指标矩阵。

初始条件 $\{\boldsymbol{x}(t_{0}),\boldsymbol{u}(t_{0})\}$ 的影响将另作考虑。过程不变性的要求是指 $I(t)$ 对干扰的不变性，系统的状态向量在相空间中的轨道将随初始条件而变化，另外在不同规律的干扰作用下相轨道一般说来也是不同的，然而我们希望各种轨道都满足同一指标的不变性要求。

系统的状态可以通过下式

$$
\binom {\boldsymbol {x} (t)} {\boldsymbol {u} (t)} = G (t, t _ {0}) \binom {\boldsymbol {x} (t _ {0})} {\boldsymbol {u} (t _ {0})} + \int_ {t _ {0}} ^ {t} G (t, \tau) \binom {\boldsymbol {f} (\tau)} {\boldsymbol {U} (\tau)} d \tau \tag {13.8-3}
$$

来表示。

公式(13.8-3)可以通过简单的推导得到。引进 $(n+m)\times(n+m)$ 阶矩阵函数 $G(t,\tau)$ ，对 $G(t,\tau)$ 的解析性质暂不作任何假设，仅要求有 $G(t,\tau)$ 参与的一切运算都是容许的，在我们得到 $G(t,\tau)$ 的微分方程后，则由微分方程解的性质，这一问题自然得到解决。

将式(13.8-1)乘以 $G(t,\tau)$ 并从 $t_{0}$ 积分到 t

$$
\int_ {t _ {0}} ^ {t} G (t, \tau) \frac {d}{d t} \left[ \begin{array}{l} \boldsymbol {x} (\tau) \\ \boldsymbol {u} (\tau) \end{array} \right] d \tau = \int_ {t _ {0}} ^ {t} G (t, \tau) P (\tau) \left[ \begin{array}{l} \boldsymbol {x} (\tau) \\ \boldsymbol {u} (\tau) \end{array} \right] d \tau + \int_ {t _ {0}} ^ {t} G (t, \tau) \left[ \begin{array}{l} \boldsymbol {f} (\tau) \\ \boldsymbol {U} (\tau) \end{array} \right] d \tau
$$

对上式左边进行分部积分后得到

$$
\begin{array}{l} G (t, t) \left[ \begin{array}{l} \boldsymbol {x} (t) \\ \boldsymbol {u} (t) \end{array} \right] - G (t, t _ {0}) \left[ \begin{array}{l} \boldsymbol {x} (t _ {0}) \\ \boldsymbol {u} (t _ {0}) \end{array} \right] \\ = \int_ {t _ {0}} ^ {t} \left[ \frac {\partial G (t , \tau)}{\partial \tau} + G (t, \tau) P (\tau) \right] \binom {\boldsymbol {x} (\tau)} {\boldsymbol {u} (\tau)} d \tau + \int_ {t _ {0}} ^ {t} G (t, \tau) \binom {\boldsymbol {f} (\tau)} {\boldsymbol {U} (\tau)} d \tau \tag {13.8-4} \\ \end{array}
$$

现在我们由式(13.8-4)右边第一个积分号下，列出求 $G(t,\tau)$ 的线性微分方程

$$
\frac {\partial G (t , \tau)}{\partial \tau} = - G (t, \tau) P (\tau), \quad t \geqslant \tau \tag {13.8-5}
$$

初始条件为

$$
G (t, t) = E \tag {13.8-6}
$$

E 为单位矩阵。

如果从式(13.8-5)和(13.8-6)求得 $G(t,\tau), t \geqslant \tau$ ，并代入式(13.8-4)，最后我 们就得到式(13.8-3)。它在研究力学、物理和自动控制的许多问题中都经常遇到，对函数 $G(t,\tau)$ 可赋予不同的名称和物理意义。这里我们称 $G(t,\tau)$ 为脉冲过渡函数。

利用公式(13.8-3)把指标式(13.8-2)分写成初始条件和干扰影响两部分

$$
\boldsymbol {I} (t) = \xi (t) \left[ \begin{array}{l} \boldsymbol {x} (t) \\ \boldsymbol {u} (t) \end{array} \right] = \boldsymbol {I} _ {0} (t) + \boldsymbol {I} _ {1} (t) \tag {13.8-7}
$$

其中 $I_{0}(t)$ 为初始条件对指标的影响, 表示式如下

$$
\boldsymbol {I} _ {0} (t) = \tilde {G} (t, t _ {0}) \left[ \begin{array}{l} \boldsymbol {x} (t _ {0}) \\ \boldsymbol {u} (t _ {0}) \end{array} \right] \tag {13.8-8}
$$

$$
G (t, t _ {0}) = \xi (t) G (t, t _ {0}) \tag {13.8-9}
$$

按照对外干扰不变性的要求，初始条件的影响将另作考虑，我们主要讨论外干扰对控制指标的影响 $I_{1}(t)$ , 考虑式(13.8-3)后 $I_{1}(t)$ 的表达式如下

$$
\boldsymbol {I} _ {1} (t) = \int_ {t _ {0}} ^ {t} \tilde {\boldsymbol {G}} (t, \tau) \left[ \begin{array}{l} \boldsymbol {f} (\tau) \\ \boldsymbol {U} (\tau) \end{array} \right] d \tau \tag {13.8-10}
$$

$$
\tilde {G} (t, \tau) = \xi (t) G (t, \tau) \tag {13.8-11}
$$

$G(t,\tau)$ 为 $m\times(n+m)$ 阶矩阵。为了完全补偿外干扰的影响，满足指标 $I_{1}(t)$ 对外干扰的过程不变性要求，我们在控制规律中引进以下形式的补偿向量

$$
\boldsymbol {U} (\tau) = \int_ {t _ {0}} ^ {\tau} K (\tau , s) \boldsymbol {f} (s) d s \tag {13.8-12}
$$

式中 $K(\tau, s)$ 为待求的 $m \times n$ 阶补偿矩阵。

将 $m \times (n + m)$ 阶矩阵 $G(t, \tau)$ 改写成以下形式

$$
\tilde {G} (t, \tau) = \left(G _ {f} (t, \tau), G _ {U} (t, \tau)\right) \tag {13.8-13}
$$

其中 $\tilde{G}_{f}(t,\tau)$ 为 $m\times n$ 阶矩阵， $\tilde{G}_{U}(t,\tau)$ 为 $m\times m$ 阶矩阵。

将式(13.8-12)和(13.8-13)代入式(13.8-10)得到

$$
\boldsymbol {I} _ {1} (t) = \int_ {t _ {0}} ^ {t} \left[ \tilde {G} _ {f} (t, \tau) \boldsymbol {f} (\tau) + \tilde {G} _ {U} (t, \tau) \int_ {t _ {0}} ^ {\tau} K (\tau , s) \boldsymbol {f} (s) d s \right] d \tau \tag {13.8-14}
$$

式(13.8-14)中包含了两个部分，第一部分是干扰向量 $f(t)$ 通过脉冲过渡函数矩阵 $\tilde{G}_{f}(t,\tau)$ 对系统的控制指标产生的影响，第二部分是在控制规律中引进干扰信息经过脉冲过渡函数矩阵 $K(\tau,s)$ 变换后再作用在脉冲过渡函数矩阵 $\tilde{G}_{U}(t,\tau)$ 上产生补偿干扰影响的作用。由于干扰向量 $f(t)$ 的变化规律是任意的，所以只有在特定的 $K(\tau,s)$ 把输入信息变换后这两部分才能完全对消。为了求出待定的 $K(\tau,s)$ 我们按照狄利克雷公式变换积分次序后得到

$$
\boldsymbol {I} _ {1} (t) = \int_ {t _ {0}} ^ {t} \left[ \tilde {\boldsymbol {G}} _ {f} (t, \tau) + \int_ {\tau} ^ {t} \tilde {\boldsymbol {G}} _ {U} (t, s) K (s, \tau) d s \right] \boldsymbol {f} (\tau) d \tau \tag {13.8-15}
$$

在式(13.8-15)中我们把变化规律不定的 $f(\tau)$ 单独提出来, 如果能选择 $K(s, \tau)$ (如果存在的话）使积分号下的方括弧恒等于零, 则不论外干扰 $f(\tau)$ 如何变化, $I_{1}(t)$ 将总等于零。所以指标向量 $I_{1}(t)$ 对任意干扰的过程不变性要求下列矩阵方程对所有允许的 t 和 $\tau$ 成立

$$
\tilde {G} _ {f} (t, \tau) + \int_ {\tau} ^ {t} \tilde {G} _ {U} (t, s) K (s, \tau) d s \equiv 0 \tag {13.8-16}
$$

矩阵恒等于零的条件相当于每个矩阵元素恒等于零，所以式(13.8-16)决定了 $m \times n$ 个第一类伏尔得拉型积分方程，解这组积分方程可以求得待定的 $m \times n$ 阶补偿矩阵 $K(t, \tau)$ 。

由于

$$
\tilde {G} _ {f} (\tau , \tau) = \xi (\tau) G (\tau , \tau) = \xi (\tau) \neq 0
$$

所以积分方程的解 $K(t,\tau)$ 可能存在于广义函数类中。

干扰信息或者能直接测量，或者可以通过微分方程本身，即通过系统的相坐标和相速度间接测量。由式(13.7-1)得到

$$
\boldsymbol {f} (t) = \frac {d \boldsymbol {x}}{d t} - A (t) \boldsymbol {x} - B (t) \boldsymbol {u} \tag {13.8-17}
$$

把式(13.8-12)和(13.8-17)代入式(13.7-2)，得到以下形式的控制规律

$$
\frac {d \boldsymbol {u}}{d t} = D (t) \boldsymbol {u} + C (t) \boldsymbol {x} + \int_ {t _ {0}} ^ {t} K (t, \tau) \left[ \frac {d \boldsymbol {x}}{d t} - A (\tau) \boldsymbol {x} - B (\tau) \boldsymbol {u} \right] d \tau \tag {13.8-18}
$$

如果系统的初始条件并不处于所需要的状态，则除设计对干扰的补偿向量外，还需要设计在某种意义上的过渡轨道，将系统的初始状态引渡到给定的状态。对于线性系统满足这种最优化问题提法的幅值受限制的控制常常是“继电器式”的，当这种“继电器式”的最优控制全力以赴地把系统引导到给定状态之后，由于系统处于连续作用的干扰影响下，所以干扰将不断使系统偏离给定的状态。这时“继电器式”的全力以赴的控制对抵消连续作用的干扰影响将失去其“最优”的意义，可能引起系统在零点附近振荡，在这种情况下比较切合问题实质的提法是对干扰影响的部分或完全补偿，使系统状态满足不变性要求。可见对于一个复杂的综合性系统不仅同时要求对多种指标进行控制，而且在运行的不同阶段上也要求多种方式的控制。

例.保持飞机水平等高飞行的控制规律。

飞机纵向运动摄动方程如下 $^{[21]}$

$$
\begin{array}{l} \Delta \dot {v} + b _ {1 0} \Delta v + a _ {1 0} \Delta \alpha_ {B} + c _ {1 0} \Delta \vartheta = x _ {1} (t) \\ \Delta \dot {\vartheta} + c _ {2 0} \Delta \vartheta - \Delta \dot {\alpha} _ {B} - a _ {2 0} \Delta \alpha_ {B} + b _ {2 0} \Delta v - \overline {{{Y}}} ^ {\delta} \Delta \delta_ {B} = y _ {1} (t) \\ \Delta \ddot {\vartheta} + c _ {3 1} \Delta \dot {\vartheta} + a _ {3 1} \Delta \dot {\alpha} _ {B} + a _ {3 0} \Delta \alpha_ {B} + b _ {3 0} \Delta v + e _ {3 0} \Delta \delta_ {B} = m _ {1} (t) \\ \end{array}
$$

我们的任务在于设计自动操纵升降舵 $\Delta\delta_{B}$ 的控制规律使飞机不论在何种扰

动因素作用下不变地保持等高飞行状态。

考虑到 $\Delta\alpha_{B}=\Delta\alpha+\Delta\alpha_{T},\Delta\theta=\Delta\vartheta-\Delta\alpha$ ，并引入符号 $x_{1}=\Delta v,x_{2}=\Delta\alpha,x_{3}=\Delta\vartheta,x_{4}=\Delta\dot{\vartheta},u=\Delta\delta_{B}$ 。经过简单运算后，飞机和自动驾驶仪系统的微分方程可写成以下标准形式

$$
\begin{array}{l} \dot {x} _ {1} = a _ {1 1} x _ {1} + a _ {1 2} x _ {2} + a _ {1 3} x _ {3} + f _ {1} (t) \\ \dot {x} _ {2} = a _ {2 1} x _ {1} + a _ {2 2} x _ {2} + a _ {2 3} x _ {3} + a _ {2 4} x _ {4} + b _ {2} u + f _ {2} (t) \\ \dot {x} _ {3} = x _ {4} \\ \dot {x} _ {4} = a _ {4 1} x _ {1} + a _ {4 2} x _ {2} + a _ {4 3} x _ {3} + a _ {4 4} x _ {4} + b _ {4} u + f _ {4} (t) \\ \dot {u} = c _ {2} x _ {2} + c _ {3} x _ {3} + c _ {4} x _ {4} + d u + U (t) \\ \end{array}
$$

首先我们从稳定性或其他角度考虑确定 $c_{2}, c_{3}, c_{4}$ ，然后求出矩阵 $G(t, \tau)$ 。

$$
\begin{array}{c c c c c c}&x _ {1} (t)&x _ {2} (t)&x _ {3} (t)&x _ {4} (t)&u\\&\uparrow&\uparrow&\uparrow&\uparrow&\uparrow\\f _ {1} (\tau) \rightarrow&G _ {1 1} (t, \tau)&G _ {2 1} (t, \tau)&G _ {3 1} (t, \tau)&G _ {4 1} (t, \tau)&G _ {5 1} (t, \tau)\\f _ {2} (\tau) \rightarrow&G _ {1 2} (t, \tau)&G _ {2 2} (t, \tau)&G _ {3 2} (t, \tau)&G _ {4 2} (t, \tau)&G _ {5 2} (t, \tau)\\&G _ {1 3} (t, \tau)&G _ {2 3} (t, \tau)&G _ {3 3} (t, \tau)&G _ {4 3} (t, \tau)&G _ {5 3} (t, \tau)\\f _ {4} (\tau) \rightarrow&G _ {1 4} (t, \tau)&G _ {2 4} (t, \tau)&G _ {3 4} (t, \tau)&G _ {4 4} (t, \tau)&G _ {5 4} (t, \tau)\\U (\tau) \rightarrow&G _ {1 5} (t, \tau)&G _ {2 5} (t, \tau)&G _ {3 5} (t, \tau)&G _ {4 5} (t, \tau)&G _ {5 5} (t, \tau)\end{array}
$$

水平等高飞行的不变性要求指标为

$$
I (t) = \theta (t) = - x _ {2} (t) + x _ {3} (t) \equiv 0
$$

设初始条件为零

$$
x _ {1} \left(t _ {0}\right) = x _ {2} \left(t _ {0}\right) = x _ {3} \left(t _ {0}\right) = x _ {4} \left(t _ {0}\right) = u \left(t _ {0}\right) = 0
$$

由式 $(13.8-3)$ 可得

$$
\begin{array}{l} I (t) = \int_ {t _ {0}} ^ {t} \left\{\left[ G _ {3 1} (t, \tau) - G _ {2 1} (t, \tau) \right] f _ {1} (\tau) + \left[ G _ {3 2} (t, \tau) - G _ {2 2} (t, \tau) \right] f _ {2} (\tau) \right. \\ + \left[ G _ {3 4} (t, \tau) - G _ {2 4} (t, \tau) \right] f _ {4} (\tau) + \left[ G _ {3 5} (t, \tau) - G _ {2 5} (t, \tau) \right] U (\tau) \} d \tau \\ \end{array}
$$

为满足过程不变性 $\Delta\theta(t)\equiv0$ 的要求选取以下形式的补偿量

$$
U (\tau) = \int_ {t _ {0}} ^ {\tau} K _ {1} (\tau , s) f _ {1} (s) d s + \int_ {t _ {0}} ^ {\tau} K _ {2} (\tau , s) f _ {2} (s) d s + \int_ {t _ {0}} ^ {\tau} K _ {4} (\tau , s) f _ {4} (s) d s
$$

把 $U(\tau)$ 代入 $I(t)$ 表示式后得到

$$
\begin{array}{l} I (t) = \int_ {t _ {0}} ^ {t} \left[ G _ {3 1} (t, \tau) - G _ {2 1} (t, \tau) \right] f _ {1} (\tau) d \tau + \int_ {t _ {0}} ^ {t} \left[ G _ {3 5} (t, \tau) - G _ {2 5} (t, \tau) \right] \\ \times \int_ {t _ {0}} ^ {\tau} K _ {1} (\tau , s) f _ {1} (s) d s d \tau + \int_ {t _ {0}} ^ {t} [ G _ {3 2} (t, \tau) - G _ {2 2} (t, \tau) ] f _ {2} (\tau) d \tau \\ + \int_ {t _ {0}} ^ {t} [ G _ {3 5} (t, \tau) - G _ {2 5} (t, \tau) ] \int_ {t _ {0}} ^ {\tau} K _ {2} (\tau , s) f _ {2} (s) d s d \tau \\ \end{array}
$$

$$
\begin{array}{l} + \int_ {t _ {0}} ^ {t} \left[ G _ {3 4} (t, \tau) - G _ {2 4} (t, \tau) \right] f _ {4} (\tau) d \tau \\ + \int_ {t _ {0}} ^ {t} [ G _ {3 5} (t, \tau) - G _ {2 5} (t, \tau) ] \int_ {t _ {0}} ^ {\tau} K _ {4} (\tau , s) f _ {4} (s) d s d \tau \\ \end{array}
$$

变换积分次序后得

$$
\begin{array}{l} I (t) = \int_ {t _ {0}} ^ {t} \left\{\left[ G _ {3 1} (t, \tau) - G _ {2 1} (t, \tau) \right] + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {1} (s, \tau) d s \right\} f _ {1} (\tau) d \tau \\ + \int_ {t _ {0}} ^ {t} \left\{\left[ G _ {3 2} (t, \tau) - G _ {2 2} (t, \tau) \right] + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {2} (s, \tau) d s \right\} f _ {2} (\tau) d \tau \\ + \int_ {t _ {0}} ^ {t} \left\{\left[ G _ {3 4} (t, \tau) - G _ {2 4} (t, \tau) \right] + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {4} (s, \tau) d s \right\} f _ {4} (\tau) d \tau \\ \end{array}
$$

“补偿网络” $K_{1}(s,\tau)$ ， $K_{2}(s,\tau)$ ， $K_{4}(s,\tau)$ 由以下积分方程组求出

$$
G _ {3 1} (t, \tau) - G _ {2 1} (t, \tau) + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {1} (s, \tau) d s = 0
$$

$$
G _ {3 2} (t, \tau) - G _ {2 2} (t, \tau) + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {2} (s, \tau) d s = 0
$$

$$
G _ {3 4} (t, \tau) - G _ {2 4} (t, \tau) + \int_ {\tau} ^ {t} \left[ G _ {3 5} (t, s) - G _ {2 5} (t, s) \right] K _ {4} (s, \tau) d s = 0
$$

干扰信息 $f_{1}(t)$ , $f_{2}(t)$ , $f_{4}(t)$ 由运动微分方程本身获得

$$
\begin{array}{l} f _ {1} (t) = \dot {x} _ {1} - a _ {1 1} x _ {1} - a _ {1 2} x _ {2} - a _ {1 3} x _ {3} \\ f _ {2} (t) = \dot {x} _ {2} - a _ {2 1} x _ {1} - a _ {2 2} x _ {2} - a _ {2 3} x _ {3} - a _ {2 4} x _ {4} - b _ {2} u \\ f _ {4} (t) = \dot {x} _ {4} - a _ {4 1} x _ {1} - a _ {4 2} x _ {2} - a _ {4 3} x _ {3} - a _ {4 4} x _ {4} - b _ {4} u \\ \end{array}
$$

最后得到自动操纵升降舵满足等高飞行不变性条件的控制方程形式如下

$$
\begin{array}{l} \dot {u} = c _ {2} x _ {2} + c _ {3} x _ {3} + c _ {4} x _ {4} + d u + \int_ {t _ {0}} ^ {t} K _ {1} (t, \tau) \left[ \dot {x} _ {1} - a _ {1 1} x _ {1} - a _ {1 2} x _ {2} - a _ {1 3} x _ {3} \right] d \tau \\ + \int_ {t _ {0}} ^ {t} K _ {2} (t, \tau) [ \dot {x} _ {2} - a _ {2 1} x _ {1} - a _ {2 2} x _ {2} - a _ {2 3} x _ {3} - a _ {2 4} x _ {4} - b _ {2} u ] d \tau \\ + \int_ {t _ {0}} ^ {t} K _ {4} (t, \tau) \left[ \dot {x} _ {4} - a _ {4 1} x _ {1} - a _ {4 2} x _ {2} - a _ {4 3} x _ {3} - a _ {4 4} x _ {4} - b _ {4} u \right] d \tau \\ \end{array}
$$

#### 13.9 终端不变性问题

还有一类问题只要求控制系统在终端时刻的状态，指标向量取决于系统在终端时刻 $t_{k}$ 的相坐标。终端不变性问题的提法是要求完全补偿外干扰在整个运行过程中所累积的对终端指标 $I(t_{k})$ 的影响。终端控制指标形式如下

$$
\boldsymbol {I} \left(t _ {k}\right) = \xi_ {k} \left[ \begin{array}{l} \boldsymbol {x} \left(t _ {k}\right) \\ \boldsymbol {u} \left(t _ {k}\right) \end{array} \right] \tag {13.9-1}
$$

式中 $\xi_{k}$ 为 $m\times(n+m)$ 阶终端指标矩阵， $\boldsymbol{x}(t_{k})$ 和 $\boldsymbol{u}(t_{k})$ 分别为控制对象和控制器在

终端时刻的状态。

显然可以把终端不变性的问题归结为过程不变性的问题，假如我们可以使系统的某一个坐标在运动全过程的每时每刻都是保持不变的话。如以上讨论的飞机在每一点的高度都是对干扰不变的，则在终端时刻自然也是不变的。但这个条件当然并不是必要的。我们看到，求出满足过程不变性要求的补偿网络需要解第一类伏尔得拉型积分方程。所以，当只要求我们控制终端的指标时，我们尽可能切合问题的提法，简化系统的设计。例如对要求严格按时刻表运行的班机的运行时间进行自动控制，这类问题的提法既不能是要求运行的时间越短越好（最优化),也不必要求在航迹上每一点的时间都是严格不变的（过程不变性),而恰恰是要求在机场着陆的时刻是严格不变的，这就是终端不变性问题。满足终端不变性要求的设计比过程不变性的设计难度和计算量都显著降低。

按照式(13.8-3)，系统在 $t_{k}$ 时刻的状态由下式表示

$$
\binom {\boldsymbol {x} \left(t _ {k}\right)} {\boldsymbol {u} \left(t _ {k}\right)} = G \left(t _ {k}, t _ {0}\right) \binom {\boldsymbol {x} \left(t _ {0}\right)} {\boldsymbol {u} \left(t _ {0}\right)} + \int_ {t _ {0}} ^ {t _ {k}} G \left(t _ {k}, \tau\right) \binom {\boldsymbol {f} (\tau)} {\boldsymbol {U} (\tau)} d \tau \tag {13.9-2}
$$

这里我们感兴趣的是在整个控制过程中，不同时刻所加的干扰作用和控制作用引起的在终端时刻 $t_{k}$ 的系统响应 $G(t_{k}, \tau)$ 。

按式 $(13.8-5)G(t_{k},\tau)$ 应满足矩阵方程

$$
\frac {d}{d \tau} G (t _ {k}, \tau) = - G (t _ {k}, \tau) P (\tau) \tag {13.9-3}
$$

和终端条件

$$
G (t _ {k}, t _ {k}) = E \tag {13.9-4}
$$

E 为单位矩阵。

把控制指标式(13.9-1)分写成初始条件的影响和干扰的影响两部分

$$
\boldsymbol {I} \left(\boldsymbol {t} _ {k}\right) = \boldsymbol {I} _ {0} \left(\boldsymbol {t} _ {k}\right) + \boldsymbol {I} _ {1} \left(\boldsymbol {t} _ {k}\right) \tag {13.9-5}
$$

其中 $I_{0}(t_{k})$ 为初始条件对终端指标的影响, 表示式如下

$$
\boldsymbol {I} _ {0} \left(t _ {k}\right) = G (t _ {k}, t _ {0}) \left[ \begin{array}{l} \boldsymbol {x} (t _ {0}) \\ \boldsymbol {u} (t _ {0}) \end{array} \right] \tag {13.9-6}
$$

$$
G (t _ {k}, t _ {0}) = \xi_ {k} G (t _ {k}, t _ {0}) \tag {13.9-7}
$$

干扰向量和补偿向量的影响都反映在 $I_{1}(t_{k})$ 中， $I_{1}(t_{k})$ 的表示式如下

$$
\boldsymbol {I} _ {1} (t _ {k}) = \int_ {t _ {0}} ^ {t _ {k}} G (t _ {k}, \tau) \left[ \begin{array}{l} \boldsymbol {f} (\tau) \\ \boldsymbol {U} (\tau) \end{array} \right] d \tau \tag {13.9-8}
$$

$$
G (t _ {k}, \tau) = \xi_ {k} G (t _ {k}, \tau) \tag {13.9-9}
$$

$G(t_{k},\tau)$ 为 $m\times(n+m)$ 阶矩阵, 可以分写成以下形式

$$
\boldsymbol {G} (t _ {k}, \tau) = (\boldsymbol {G} _ {f} (t _ {k}, \tau), \boldsymbol {G} _ {U} (t _ {k}, \tau)) \tag {13.9-10}
$$

其中 $G_{f}(t_{k},\tau)$ 为 $m\times n$ 阶矩阵， $G_{U}(t_{k},\tau)$ 为 $m\times m$ 阶矩阵。

把式(13.9-10)代入式(13.9-8)得到

$$
\boldsymbol {I} _ {1} (t _ {k}) = \int_ {t _ {0}} ^ {t _ {k}} \left[ G _ {f} (t _ {k}, \tau) \boldsymbol {f} (\tau) + G _ {U} (t _ {k}, \tau) \boldsymbol {U} (\tau) \right] d \tau \tag {13.9-11}
$$

在设计满足过程不变性指标的补偿向量 $U(\tau)$ 时，式(13.8-14)中 $G_{f}(t,\tau)$ ， $G_{U}(t,\tau)$ 都是二元函数，所以必须选择二元函数形式的“补偿网络” $K(t,\tau)$ ，这样的问题需要解积分方程才能解决。但现在要满足的终端指标式(13.9-11)中的 $G_{f}(t_{k},\tau)$ 和 $G_{U}(t_{k},\tau)$ ，当终端时刻 $t_{k}$ 确定后就不再是二元函数而是一元函数了。所以补偿向量选择成以下简单的形式

$$
\boldsymbol {U} (\tau) = K (\tau) \boldsymbol {f} (\tau) \tag {13.9-12}
$$

式中 $K(\tau)$ 为待求的 $m \times n$ 阶补偿矩阵。把式(13.9-12)代入式(13.9-11)后得到

$$
\boldsymbol {I} _ {1} \left(t _ {k}\right) = \int_ {t _ {0}} ^ {t _ {k}} \left[ G _ {f} \left(t _ {k}, \tau\right) + G _ {U} \left(t _ {k}, \tau\right) K (\tau) \right] \boldsymbol {f} (\tau) d \tau \tag {13.9-13}
$$

对任意变化规律的 $f(\tau)$ 要求 $I_{1}(t_{k})$ 恒为零的充分必要条件是积分号下的方括号恒等于零，由此得到对任意外干扰 $f(\tau)$ 的补偿条件是

$$
G _ {f} (t _ {k}, \tau) + G _ {U} (t _ {k}, \tau) K (\tau) \equiv 0 \tag {13.9-14}
$$

从以上条件我们求得补偿矩阵

$$
K (\tau) = - \left[ G _ {U} \left(t _ {k}, \tau\right) \right] ^ {- 1} G _ {f} \left(t _ {k}, \tau\right) \tag {13.9-15}
$$

干扰信息或直接测量，或通过方程(13.8-17)测量，我们得到将相速度和相坐标通过变系数补偿矩阵反馈满足终端不变性条件的控制规律是

$$
\frac {d \boldsymbol {u}}{d t} = S (t) \boldsymbol {u} + K (t) \dot {\boldsymbol {x}} + R (t) \boldsymbol {x} \tag {13.9-16}
$$

式中

$$
R (t) = C (t) - K (t) A (t)
$$

$$
S (t) = D (t) - K (t) B (t)
$$

初始条件的影响可以在控制规律中加一个常值的补偿向量 $U_{0}$ 把它消去, $U_{0}$ 由下式决定

$$
\boldsymbol {U} _ {0} = - \left[ \int_ {t _ {0}} ^ {t _ {k}} \boldsymbol {G} _ {U} (t _ {k}, \tau) d \tau \right] ^ {- 1} \boldsymbol {G} (t _ {k}, t _ {0}) \binom {\boldsymbol {x} (t _ {0})} {\boldsymbol {u} (t _ {0})} \tag {13.9-17}
$$

例.飞航式远程导弹制导系统。

在本章第 13.5 节中针对一个飞航式远程导弹的制导系统进行了具体的设计, 这个设计的思路和方法是富有启发性的。但在第 13.5 节的设计过程中我们做了一些假设并加一些限制条件, 如忽略控制机构的惯性, 假设在所有高度上大气的成分与标准大气的成分相同, 火箭空气动力特性和翼面积不变等。在这些假设的前提下, 可以把干扰因素归结为 $\delta\rho, \delta w, \delta T$ 三个量。我们现在试把本节中建 立的一般方法用于这个具体系统的设计中，引进控制器的运动方程，去掉上述限制条件，按利用火箭本身作为干扰测量工具的思想，简化掉 $\delta T$ 干扰测量器。我们假定干扰是任意的，不必限制干扰的具体表示形式和数目。

首先建立系统的摄动运动方程

$$
\begin{array}{l} \frac {d \delta r}{d t} = \delta v _ {r} \\ \frac {d \delta \theta}{d t} = - \frac {\overline {{{v}}} _ {\theta}}{\overline {{{r}}} ^ {2}} \delta r + \frac {1}{\overline {{{r}}}} \delta v _ {\theta} \\ \frac {d \delta \beta}{d t} = \delta \dot {\beta} \\ \frac {d \delta v _ {r}}{d t} = a _ {1} \delta r + a _ {2} \delta \beta + a _ {3} \delta v _ {r} + a _ {4} \delta v _ {\theta} + a _ {5} \delta \gamma + f _ {1} \\ \frac {d \delta v _ {\theta}}{d t} = b _ {1} \delta r + b _ {2} \delta \beta + b _ {3} \delta v _ {r} + b _ {4} \delta v _ {\theta} + b _ {5} \delta \gamma + f _ {2} \\ \frac {d \delta \dot {\beta}}{d t} = c _ {1} \delta r + c _ {2} \delta \beta + c _ {3} \delta v _ {r} + c _ {4} \delta v _ {\theta} + c _ {5} \delta \gamma + f _ {3} \\ \end{array}
$$

$$
\frac {d \delta \gamma}{d t} = d _ {0} \delta \dot {\beta} + d _ {2} \delta \beta + d _ {5} \delta \gamma + K _ {1} f _ {1} + K _ {2} f _ {2} + K _ {3} f _ {3} \tag {13.9-18}
$$

在式(13.9-18)中除第 13.2 节中建立的弹体运动方程(13.2-4)和(13.2-5)外还引入了控制方程。在控制方程中我们考虑了控制机构的惯性。式(13.2-4)和(13.2-5)再加上控制方程就组成了制导系统的运动方程。于是， $\delta\gamma$ 就由原来方程的非齐次项变成了系统状态向量的一个坐标。控制方程的齐次部分就是通常作为姿态稳定的控制规律，例如

$$
\frac {d \delta \gamma}{d t} = \frac {1}{\tau} a _ {0} ^ {\beta} \delta \beta + \frac {1}{\tau} a _ {0} ^ {\beta} T _ {1} \delta \dot {\beta} - \frac {1}{\tau} \delta \gamma \tag {13.9-19}
$$

式中 $\tau, T_{1}$ 为时间常数， $a_{0}^{\beta}$ 为静态放大系数。

系统式(13.9-18)的伴随方程和终端条件如下

$$
\begin{array}{l} - \frac {d \lambda_ {1}}{d t} = - \frac {\overline {{{v}}} _ {0}}{\overline {{{r}}} ^ {2}} \lambda_ {2} + a _ {1} \lambda_ {4} + b _ {1} \lambda_ {5} + c _ {1} \lambda_ {6} \\ - \frac {d \lambda_ {2}}{d t} = 0 \\ - \frac {d \lambda_ {3}}{d t} = a _ {2} \lambda_ {4} + b _ {2} \lambda_ {5} + c _ {2} \lambda_ {6} + d _ {2} \lambda_ {7} \\ - \frac {d \lambda_ {4}}{d t} = \lambda_ {1} + a _ {3} \lambda_ {4} + b _ {3} \lambda_ {5} + c _ {3} \lambda_ {6} \\ - \frac {d \lambda_ {5}}{d t} = \frac {1}{\bar {r}} \lambda_ {2} + a _ {4} \lambda_ {4} + b _ {4} \lambda_ {5} + c _ {4} \lambda_ {6} \\ \end{array}
$$

$$
\begin{array}{l} - \frac {d \lambda_ {6}}{d t} = \lambda_ {3} + d _ {0} \lambda_ {7} \\ - \frac {d \lambda_ {7}}{d t} = + a _ {5} \lambda_ {4} + b _ {5} \lambda_ {5} + c _ {5} \lambda_ {6} + d _ {5} \lambda_ {7} \tag {13.9-20} \\ \end{array}
$$

$$
\lambda_ {1} (\bar {t} _ {2}) = - \frac {1}{\bar {r}} \left(\frac {\bar {v} _ {0}}{\bar {v} _ {r}}\right), \quad \lambda_ {2} (\bar {t} _ {2}) = 1
$$

$$
\lambda_ {3} (\bar {t} _ {2}) = \lambda_ {4} (\bar {t} _ {2}) = \lambda_ {5} (\bar {t} _ {2}) = \lambda_ {6} (\bar {t} _ {2}) = \lambda_ {7} (\bar {t} _ {2}) = 0 \tag {13.9-21}
$$

对外干扰的完全补偿条件为

$$
\lambda_ {4} + K _ {1} \lambda_ {7} \equiv 0, \quad \lambda_ {5} + K _ {2} \lambda_ {7} \equiv 0, \quad \lambda_ {6} + K _ {3} \lambda_ {7} \equiv 0
$$

由此得到

$$
K _ {1} = - \frac {\lambda_ {4}}{\lambda_ {7}}, \quad K _ {2} = - \frac {\lambda_ {5}}{\lambda_ {7}}, \quad K _ {3} = - \frac {\lambda_ {6}}{\lambda_ {7}} \tag {13.9-22}
$$

利用火箭本身作为干扰测量工具时，我们有

$$
\begin{array}{l} f _ {1} = \frac {d \delta v _ {r}}{d t} - a _ {1} \delta r - a _ {2} \delta \beta - a _ {3} \delta v _ {r} - a _ {4} \delta v _ {\theta} - a _ {5} \delta \gamma \\ f _ {2} = \frac {d \delta v _ {\theta}}{d t} - b _ {1} \delta r - b _ {2} \delta \beta - b _ {3} \delta v _ {r} - b _ {4} \delta v _ {\theta} - b _ {5} \delta \gamma \\ f _ {3} = \frac {d \delta \dot {\beta}}{d t} - c _ {1} \delta r - c _ {2} \delta \beta - c _ {3} \delta v _ {r} - c _ {4} \delta v _ {\theta} - c _ {5} \delta \gamma \tag {13.9-23} \\ \end{array}
$$

把式(13.9-22)和(13.9-23)代入式(13.9-18)的控制方程，我们就得到在任何干扰作用下能保证火箭命中目标的控制规律。

$$
\begin{array}{l} \frac {d \delta \gamma}{d t} + \frac {1}{\tau} \delta \gamma = K _ {1} \frac {d \delta v _ {r}}{d t} + K _ {2} \frac {d \delta v _ {\theta}}{d t} + K _ {3} \frac {d \delta \dot {\beta}}{d t} \\ + K _ {4} \delta \dot {\beta} + K _ {5} \delta \beta + K _ {6} \delta r + K _ {7} \delta v _ {r} + K _ {8} \delta v _ {\theta} + K _ {9} \delta \gamma \tag {13.9-24} \\ \end{array}
$$

式中 $K_{i}$ 都是与标准轨道参数有关的已知时间函数。它们的表示式如下

$$
K _ {1} = - \frac {\lambda_ {4}}{\lambda_ {7}}, \quad K _ {2} = - \frac {\lambda_ {5}}{\lambda_ {7}}, \quad K _ {3} = - \frac {\lambda_ {6}}{\lambda_ {7}}, \quad K _ {4} = d _ {0}
$$

$$
K _ {5} = \frac {1}{\lambda_ {7}} (a _ {2} \lambda_ {4} + b _ {2} \lambda_ {5} + c _ {2} \lambda_ {6} + d _ {2} \lambda_ {7})
$$

$$
K _ {6} = \frac {1}{\lambda_ {7}} (a _ {1} \lambda_ {4} + b _ {1} \lambda_ {5} + c _ {1} \lambda_ {6})
$$

$$
K _ {7} = \frac {1}{\lambda_ {7}} (a _ {3} \lambda_ {4} + b _ {3} \lambda_ {5} + c _ {3} \lambda_ {6})
$$

$$
K _ {8} = \frac {1}{\lambda_ {7}} (a _ {4} \lambda_ {4} + b _ {4} \lambda_ {5} + c _ {4} \lambda_ {6})
$$

$$
K _ {9} = \frac {1}{\lambda_ {7}} (a _ {5} \lambda_ {4} + b _ {5} \lambda_ {5} + c _ {5} \lambda_ {6})
$$

下面几节我们将摄动理论和控制理论相结合，研究弹道火箭惯性制导系统的 设计问题。弹道火箭的弹道特点是，在主动段（发动机工作段）结束后，沿自由弹道飞行，将有效载荷送到地球上已知位置的目标点。如作为运载火箭，则是将人造卫星、飞船等空间飞行器送入预定的飞行轨道。弹道火箭具有标准的飞行条件和相应的标准弹道。实际飞行条件在小范围内偏离标准值，使实际弹道对标准弹道产生摄动。火箭的主动段惯性制导系统通过对火箭质心运动的控制，消除实际飞行中各种干扰作用的影响，达到终端受控的要求。例如弹道式导弹射程偏差为零和落点横向偏差为零的要求。用主动段飞行过程中的运动参数，或主动段关机点参数预测终端受控参数（如射程偏差和落点横向偏差或卫星轨道参数偏差），是进行弹道火箭主动段制导的基础。因而弹道火箭的制导系统是一类预测制导系统。当预测的终端受控参数为零时，制导系统处于零控无偏状态，即无须标准飞行条件之外的制导控制，在与标准飞行条件相应的零控加速度作用下达到终端受控参数为零的要求。因而制导系统的任务只在于将系统引导到零控无偏状态。预测制导系统除具有零控无偏状态的特点之外，和通常的反馈控制系统类似，在有导航计算的条件下可看成是状态反馈控制系统。若直接利用加速度表的测量值进行制导计算，则可看成是加速度表输出反馈控制系统。皮特曼(Pitman)和依斯林斯基(Ишлинский)都曾研究过弹道火箭的惯性制导问题[12,16]。我们在这里将用控制理论中的状态变量方法和极大值原理，并与摄动理论相结合，运用文献[3]中提出的“零控无偏状态”的概念来设计惯性制导系统。由于射程控制系统和横向控制系统各具有不同的特点，我们将分别加以研究。

#### 13.10 弹道火箭的运动方程

弹道式火箭普遍采用惯性制导系统。为便于研究火箭的惯性制导问题，我们在发射点惯性坐标系内建立火箭的运动方程。这种运动方程不仅直接反映了惯性器件测量的火箭运动参数，而且不出现由于地球自转引起的哥氏加速度项，运动方程显得十分简单，物理意义也很明确。

首先建立发射点惯性坐标系（见图 13.10-1). 坐标原点取在火箭的发射点, OY 轴通过地心 $O_{E}$ 和发射点 O 指向上方, OX 轴垂直于 OY 轴指向火箭的瞄准方向。OX 轴与过发射点 O 的子午线正北方向之夹角为 $\psi_{a}$ , 称 $\psi_{a}$ 为发射方位角。OZ 轴按右手坐标系确定。发射瞬间将此坐标系固定在惯性空间。

弹道火箭制导系统的控制对象是火箭的质心运动， 我们研究制导系统时，通常只需建立火箭的质心运动方程，这个方程可以写成作用在火箭质心上的力平衡方程的形式

> 此处省略原书 **图 13.10-1**

$$
\dot {\boldsymbol {x}} = \left( \begin{array}{c c} 0 & 0 \\ \hline I & 0 \end{array} \right) \boldsymbol {x} + \binom {I} {- 0} \boldsymbol {g} + \binom {I} {- 0} \dot {\boldsymbol {\omega}} \tag {13.10-1}
$$

式中

$$
I = \left( \begin{array}{c c c} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{array} \right)
$$

$$
\boldsymbol {x} = \left(v _ {x}, v _ {y}, v _ {z}, x, y, z\right) ^ {\tau}
$$

为火箭质心运动的参数。 $v_{x}, v_{y}, v_{z}$ 为火箭质心速度在发射点惯性坐标系中的三个分量，x, y, z 为火箭质心位置的三个分量。这里 $\tau$ 表示向量的转置。

$$
\dot {\omega} = (\dot {\omega} _ {x}, \dot {\omega} _ {y}, \dot {\omega} _ {z}) ^ {\tau}
$$

是作用于火箭上除地球引力以外的各种力产生的加速度，即发动机推力加速度和空气动力加速度，通常称 $\dot{\omega}$ 为视加速度，它在惯性坐标系中的三个分量为 $\dot{\omega}_{x}$ 、 $\dot{\omega}_{y}$ 、 $\dot{\omega}_{z}$ ,可在惯性稳定平台上按 X,Y,Z 定向的三个加速度表测量出来。

$$
\mathbf {g} = \left(g _ {x}, g _ {y}, g _ {z}\right) ^ {\tau}
$$

表示作用于火箭上的地球引力加速度，它在发射点惯性坐标系中的三个分量为

$$
g _ {x} = - \mu \frac {x}{r ^ {3}}
$$

$$
g _ {y} = - \mu \frac {(r _ {0} + y)}{r ^ {3}}
$$

$$
g _ {z} = - \mu \frac {z}{r ^ {3}}
$$

$$
\mu = g _ {0} r _ {0} ^ {2} \tag {13.10-2}
$$

火箭质心到地心 $O_{E}$ 的距离为向径 r

$$
r = \left[ x ^ {2} + (r _ {0} + y) ^ {2} + z ^ {2} \right] ^ {\frac {1}{2}} \tag {13.10-3}
$$

$g^{0}$ 是地面引力加速度, $r^{0}$ 是地球半径。显然引力加速度 g 是火箭位置的非线性函数。

在标准推力程序和标准空气动力条件下飞行的弹道式火箭，可按式(13.10-1)和(13.10-2)计算出主动段的标准飞行弹道。

式(13.10-1)是非线性微分方程，不便于用线性系统的理论来研究，像本章第 13.2 节中的情况一样，我们用弹道摄动理论对式(13.10-1)作线性化处理。注意到式(13.10-1)中火箭运动视加速度 $\dot{\omega}$ 是可以直接用加速度表测量出来的物理量，因而线性化时把它作为方程的驱动项，不必将 $\dot{\omega}$ 再分成推力加速度部分和气动力加速度部分。引力加速度是火箭位置的非线性函数，不能用惯性仪表来测 量，它只能在知道火箭位置后按式(13.10-2)计算出来。我们只要对引力加速度 g 进行线性化处理，就可以使式(13.10-1)成为变系数线性微分方程。

首先，完全类似于第 13.2 节的做法，用 $\delta$ 表示同一时刻各参量的偏差，很容易推出式(13.10-1)的摄动方程 $^{[16]}$

$$
\delta \dot {\boldsymbol {x}} (t) = A (t) \delta \boldsymbol {x} (t) + B \delta \dot {\omega} (t) \tag {13.10-4}
$$

式中

$$
\delta \boldsymbol {x} (t) = \boldsymbol {x} (t) - \overline {{{{\boldsymbol {x}}}}} (t) \tag {13.10-5}
$$

$$
\delta \dot {\omega} (t) = \dot {\omega} (t) - \overline {{{{\omega}}}} (t)
$$

系数矩阵

$$
A (t) = \left( \begin{array}{c c} 0 & G (t) \\ \hline I & 0 \end{array} \right), \quad B = \binom {I} {0} \tag {13.10-6}
$$

$$
G (t) = \left[ \begin{array}{l l l} \frac {\partial g _ {x}}{\partial x} & \frac {\partial g _ {x}}{\partial y} & \frac {\partial g _ {x}}{\partial z} \\ \frac {\partial g _ {y}}{\partial x} & \frac {\partial g _ {y}}{\partial y} & \frac {\partial g _ {y}}{\partial z} \\ \frac {\partial g _ {z}}{\partial x} & \frac {\partial g _ {z}}{\partial y} & \frac {\partial g _ {z}}{\partial z} \end{array} \right] \tag {13.10-7}
$$

$G(t)$ 中各元素是由标准弹道确定的随时间变化的量，它们的计算公式如下

$$
\begin{array}{l} \frac {\partial g _ {x}}{\partial x} = N \left[ 1 - \frac {3 x ^ {2}}{r ^ {2}} \right] \\ \frac {\partial g _ {x}}{\partial y} = N \left[ - \frac {3 x (r _ {0} + y)}{r ^ {2}} \right] \\ \frac {\partial g _ {x}}{\partial z} = N \left[ - \frac {3 x z}{r ^ {2}} \right] \\ \end{array}
$$

$$
\frac {\partial g _ {y}}{\partial x} = \frac {\partial g _ {x}}{\partial y}
$$

$$
\frac {\partial g _ {y}}{\partial y} = N \left[ 1 - \frac {3 (r _ {0} + y) ^ {2}}{r ^ {2}} \right]
$$

$$
\frac {\partial g _ {y}}{\partial z} = N \left[ - \frac {3 (r _ {0} + y) z}{r ^ {2}} \right]
$$

$$
\frac {\partial g _ {z}}{\partial x} = \frac {\partial g _ {x}}{\partial z}
$$

$$
\frac {\partial g _ {z}}{\partial y} = \frac {\partial g _ {y}}{\partial z}
$$

$$
\frac {\partial g _ {z}}{\partial z} = N \left(1 - \frac {3 z ^ {2}}{r ^ {2}}\right)
$$

$$
N = - \frac {g}{r}
$$

$$
g = g ^ {0} \left(\frac {r _ {0}}{r}\right) ^ {2} \tag {13.10-8}
$$

注意到式(13.10-1)的非线性因素仅仅是引力加速度 g 造成的，我们只需对引力加速度 g 作线性化处理，不必把方程(13.10-1)的状态量化为偏差量，也可以推出一组线性方程。引力加速度沿标准弹道的一阶近似线性展式为

$$
\mathbf {g} (t) = \overline {{{\mathbf {g}}}} (t) + \delta \mathbf {g} (t) = \overline {{{\mathbf {g}}}} (t) + (0: G (t)) \tag {13.10-9}
$$

将式(13.10-5)代入式(13.10-9)后有

$$
\boldsymbol {g} (t) = \overline {{\boldsymbol {g}}} (t) - (0 \vdots G (t)) \overline {{\boldsymbol {x}}} (t) + (0 \vdots G (t)) \boldsymbol {x} (t) \tag {13.10-10}
$$

记

$$
\boldsymbol {d} (t) = \binom {\overline {{\boldsymbol {g}}} (t)} {\overline {{0}}} - \left( \begin{array}{c c} 0 & G (t) \\ \overline {{0}} & 0 \end{array} \right) \overline {{\boldsymbol {x}}} (t) \tag {13.10-11}
$$

$d(t)$ 为由标准弹道确定的已知时间函数组成的向量。再将式(13.10-10)和(13.10-11)代入式(13.10-1)，得到

$$
\dot {\boldsymbol {x}} (t) = A (t) \boldsymbol {x} (t) + B \dot {\omega} (t) + \boldsymbol {d} (t) \tag {13.10-12}
$$

式(13.10-12)是火箭主动段质心运动的线性方程，它的状态变量是火箭质心运动的参数 $\boldsymbol{x}(t)$ , 而不是偏差量 $\delta\boldsymbol{x}(t)$ , 驱动项是 $(B\dot{\omega}(t)+\boldsymbol{d}(t))$

本节推导出的摄动方程(13.10-4)和线性方程(13.10-12)将在本章以后各节用状态变量法去设计制导系统时应用。

#### 13.11 终端受控参数

弹道式导弹制导的任务在于通过控制火箭推力向量，以达到主动段推力终止条件，使关机点的参数符合能精确命中目标的要求。当精确命中目标时，则落点的射程偏差和横向偏差均为零。在只进行主动段制导的情况下，火箭的被动段及其落点完全由主动段关机点的参数确定，我们可以用主动段关机点参数预测出弹道式导弹的射程偏差和落点横向偏差。这些偏差就是弹道式导弹主动段制导的终端受控参数。

同样，发射人造地球卫星或宇宙飞船时，运载火箭制导系统的任务也是通过对主动段弹道的控制，使关机点的参数满足卫星或飞船预定轨道的要求。因而用关机点运动参数表示的轨道参数偏差就是运载火箭主动段终端受控参数。下面我们分别研究这些终端受控参数的具体表达式。

假设地球为球形，不考虑大气和地球以外其他天体对火箭运动的摄动影响，火箭在被动段只受到地球引力的作用，被动段弹道是惯性空间的平面椭圆轨道，椭圆的一个焦点为地心。利用椭圆运动的基本关系，可推导用关机点运动参数表达的射程或卫星轨道参数的解析公式。[5][22]

首先讨论弹道式导弹的射程及落点偏差计算公式。计算弹道式导弹的射程，就是计算导弹在地球上的发射点 O 和落点 b 之间在地球表面上的最短距离 L，也就是计算发射点和落点之间的地心角 $\beta$ 。落点在地球上的位置由导弹在惯性坐标系中的运动与地球在惯性坐标系中的运动共同决定，发射点 O 也是随着地球一起运动的。为了描述地球在惯性空间的运动，我们引入一个紧套在地球表面的球壳，火箭发射瞬间，将此球壳固定在惯性空间，不随地球运动。称这个球壳为惯性球壳。在惯性球壳上可以找出各时刻发射点的位置和落地时刻落点的位置。图 13.11-1 中，NMP 表示惯性球壳，O 表示发射时刻发射点的位置，角 $\varphi_{0}$ 为发射点纬度。 $O_{k}$ 表示关机时刻发射点在惯性球壳上的位置， $K'$ 表示关机时刻导弹在惯性球壳上投影点的位置，角 $\varphi_{k}$ 为 $K'$ 点的纬度。 $O_{b}$ 表示落地时刻发射点的位置，b 表示落地时刻的落点位置，角 $\varphi_{b}$ 为落点的纬度。

> 此处省略原书 **图 13.11-1**

过 b 点的子午面与过 $O_{b}$ 点的子午面之间的夹角为 $\lambda_{k}, \lambda_{b}$ 表示落地时刻发射点与落点间的经度差。 $\omega_{E}$ 表示地球自转角速度， $T_{c}$ 表示导弹在被动段飞行的时间。过 $O_{k}$ 的子午面与过 $O_{b}$ 点子午面之间的夹角 $\omega_{E} T_{c}$ 表示在被动段飞行时间内，发射点随地球转过的经度。 $t_{k}$ 表示在主动段飞行的时间，过 O 点的子午面与过 $O_{k}$ 点的子午面之间的夹角 $\omega_{E} t_{k}$ ，表示主动段飞行时间内发射点随地球转过的经度。 $\lambda_{k}$ 表示由于导弹的主动段飞行引起的关机点的投影点 $K^{I}$ 与点 $O_{k}$ 间的经度差。所要求的射 程 L, 就是过 $O_{b}$ , b 两点的地球大圆面上的弧长 $O_{b}b$ 。用 $r_{0}$ 表示地球半径, 显然有

$$
\mathcal {L} = r _ {0} \beta \tag {13.11-1}
$$

实际落点 b 与预定目标 $\bar{b}$ 不重合，产生射程偏差 $\Delta\mathcal{L}=r_{0}(\beta-\bar{\beta})$ ，而落点的横向偏差 H 是由射向角 $\psi$ 的偏差引起的。

为了直接用椭圆弹道的基本公式来计算被动段对应的地心角 $\beta_{c}$ 和被动段飞行时间 $T_{c}$ ，需要在关机点惯性坐标系中来描述导弹关机点的运动参数。关机点惯性坐标系的原点为 $K^{\prime}$ 点， $K^{\prime}Y_{A}$ 轴通过地心 $O_{E}$ 和 $K^{\prime}$ 点指向上方， $K^{\prime}X_{A}$ 轴垂直于 $K^{\prime}Y_{A}$ 轴并取在 $O_{E}OK^{\prime}$ 平面内， $K^{\prime}Z_{A}$ 轴按右手坐标系确定。关机时刻导弹在该坐标系中的位置和速度分别用 $x_{A}, y_{A}, z_{A}, v_{xA}, v_{yA}, v_{zA}$ 表示。关机点惯性坐标系和发射点惯性坐标系的关系由角 $\gamma_{k}$ 和角 $\beta_{k}$ 确定。 $\gamma_{k}$ 角是由于关机点横向位移引起 $OK^{\prime}$ 弧对发射方向 OX 的偏角， $\beta_{k}$ 角是 $K^{\prime}$ 点与发射点 O 间的地心角。不难看出

$$
\sin \gamma_ {k} = z _ {k} / (x _ {k} ^ {2} + z _ {k} ^ {2}) ^ {\frac {1}{2}} \tag {13.11-2}
$$

$$
\sin \beta_ {k} = (x _ {k} ^ {2} + z _ {k} ^ {2}) ^ {\frac {1}{2}} / r _ {k} \tag {13.11-3}
$$

$$
\boldsymbol {r} _ {k} = \left[ x _ {k} ^ {2} + (y _ {k} + r _ {0}) ^ {2} + z _ {k} ^ {2} \right] ^ {\frac {1}{2}} \tag {13.11-4}
$$

$$
\left[ \begin{array}{l} v _ {x A} \\ v _ {y A} \\ v _ {z A} \end{array} \right] = \left[ \begin{array}{c c c} \cos \gamma_ {k} \cos \beta_ {k} & - \sin \beta_ {k} & \sin \gamma_ {k} \cos \beta_ {k} \\ \cos \gamma_ {k} \sin \beta_ {k} & \cos \beta_ {k} & \sin \gamma_ {k} \sin \beta_ {k} \\ - \sin \gamma_ {k} & 0 & \cos \gamma_ {k} \end{array} \right] \left[ \begin{array}{l} v _ {x k} \\ v _ {y k} \\ v _ {z k} \end{array} \right] \tag {13.11-5}
$$

式中，下标 k 表示在发射点惯性坐标系中导弹的关机点对应的参数。显然，导弹在关机点的当地速度倾角 $\Theta_{A}$ (即关机点速度矢量与当地水平面的夹角) 可按下式计算

$$
\cos \Theta_ {A} = (v _ {x A} ^ {2} + v _ {z A} ^ {2}) ^ {\frac {1}{2}} / v _ {A} \tag {13.11-6}
$$

$$
v _ {A} = \left(v _ {x k} ^ {2} + v _ {y k} ^ {2} + v _ {z k} ^ {2}\right) ^ {\frac {1}{2}} = v _ {k} \tag {13.11-7}
$$

由于导弹在关机点存在横向速度分量 $v_{zA}$ ，所以引起被动段椭圆弹道平面偏离 $K^{\prime}X_{A}Y_{A}$ 平面，偏离角 $\gamma_{A}$ 可用下式计算

$$
\sin \gamma_ {A} = v _ {z A} / (v _ {x A} ^ {2} + v _ {z A} ^ {2}) ^ {\frac {1}{2}} \tag {13.11-8}
$$

因而，导弹在关机点处的射向角 $\psi_{k}$ 为

$$
\psi_ {k} = \psi_ {A} + \gamma_ {A} \tag {13.11-9}
$$

式中 $\psi_{A}$ 是 $K^{\prime}X_{A}$ 轴与过 $K^{\prime}$ 点的子午线正北方向的夹角。

我们在关机点惯性坐标系中应用椭圆轨道方程来建立计算被动段地心角 $\beta_{i}$ 的公式。我们知道，椭圆轨道的参数方程式为

$$
r = \frac {p}{1 + e \cos f} \tag {13.11-10}
$$

式中 p 为半通径, e 为偏心率, f 为真近点角。分别对关机点 K 和落点 b (见图 13.11-2) 运用轨道方程, 可得出被动段地心角 $\beta_{c}$ 的计算公式

$$
\beta_ {e} = \cos^ {- 1} \left[ \frac {1}{e} \left(1 - \frac {p}{r _ {0}}\right) \right] + \cos^ {- 1} \left[ \frac {1}{e} \left(1 - \frac {p}{r _ {k}}\right) \right] \tag {13.11-11}
$$

> 此处省略原书 **图 13.11-2**

为了计算被动段飞行时间 $T_{c}$ ，我们看椭圆运动的开普勒(Kepler)方程

$$
t - t _ {p} = \sqrt {\frac {a ^ {3}}{\mu}} (E - e \sin E) \tag {13.11-12}
$$

$$
E = \cos^ {- 1} \frac {1}{e} \left[ 1 - \frac {r}{a} \right] \tag {13.11-13}
$$

式中 $t - t_p$ 为火箭从近地点 $P$ 飞到某一点的时间， $E$ 为该点的偏近点角。火箭从 $K$ 点飞到 $b$ 点的时间即被动段飞行时间 $T_c$ 为

$$
\begin{array}{l} T _ {c} = \sqrt {\frac {a ^ {3}}{\mu}} \left[ \left(E _ {b} - E _ {k}\right) - e (\sin E _ {b} - \sin E _ {k}) \right] \\ = \sqrt {\frac {a ^ {3}}{\mu}} \left\{\left[ \cos^ {- 1} \frac {1 - \frac {r _ {0}}{a}}{e} \right] - \left[ \cos^ {- 1} \frac {1 - \frac {r _ {k}}{a}}{e} \right] \right. \\ - e \left[ \sin \left(\cos^ {- 1} \frac {1 - \frac {r _ {0}}{a}}{e}\right) - \sin \left(\cos^ {- 1} \frac {1 - \frac {r _ {k}}{a}}{e}\right) \right] \Bigg \} \tag {13.11-14} \\ \end{array}
$$

式中椭圆的偏心率的表达式是

$$
e = \left[ 1 - (2 - v _ {k}) v _ {k} \cos^ {2} \Theta_ {A} \right] ^ {\frac {1}{2}} \tag {13.11-15}
$$

定义椭圆的能量参数

$$
v _ {k} = v _ {k} ^ {2} / \frac {\mu}{r _ {k}} \tag {13.11-16}
$$

椭圆的半通径

$$
p = r _ {k} v _ {k} \cos^ {2} \Theta_ {A} \tag {13.11-17}
$$

和椭圆的长半轴

$$
a = \frac {p}{1 - e ^ {2}} \tag {13.11-18}
$$

现在，我们回到惯性球壳上，利用发射点 $O(O_{k}, O_{b})$ , 关机点的投影点 $K'$ , 落点 b 以及地心 $O_{E}$ 和北极 N 之间的几何关系, 用球面三角学中的正弦定理和余弦定理, 依次从球面三角形 $hO_{b}b, NO_{b}b, NK'b, NOK'$ 中, 推出计算射程 L 和落点横向偏差 H 的几何关系式

$$
\begin{array}{l} \mathscr {L} = r _ {0} \beta \\ H = r _ {0} \sin \beta \sin (\psi - \overline {{\psi}}) \\ \cos \beta = \sin \varphi_ {0} \sin \varphi_ {b} + \cos \varphi_ {0} \cos \varphi_ {b} \cos \lambda_ {b} \\ \sin \psi = \cos \varphi_ {b} \sin \lambda_ {b} / \sin \beta \\ \cos \psi = (\sin \varphi_ {b} - \cos \beta \sin \varphi_ {0}) / \sin \beta \cos \varphi_ {0} \\ \sin \varphi_ {b} = \sin \varphi_ {k} \cos \beta_ {c} + \cos \varphi_ {k} \sin \beta_ {c} \cos \psi_ {k} \\ \end{array}
$$

$$
\cos \left(\omega_ {E} T _ {c} + \lambda_ {b} - \lambda_ {k}\right) = \left(\cos \beta_ {c} - \sin \varphi_ {k} \sin \varphi_ {b}\right) / \cos \varphi_ {k} \cos \varphi_ {b}
$$

$$
\sin \left(\omega_ {E} T _ {c} + \lambda_ {b} - \lambda_ {k}\right) = \sin \beta_ {c} \sin \psi_ {k} / \cos \varphi_ {b}
$$

$$
\sin \psi_ {A} = \cos \varphi_ {0} \sin \psi_ {0} / \cos \varphi_ {k}
$$

$$
\cos \psi_ {A} = (\sin \varphi_ {k} \cos \beta_ {k} - \sin \varphi_ {0}) / \cos \varphi_ {k} \sin \beta_ {k}
$$

$$
\sin \left(\omega_ {E} t _ {k} + \lambda_ {k}\right) = \sin \varphi_ {0} \sin \beta_ {k} / \cos \varphi_ {k}
$$

$$
\cos \left(\omega_ {E} t _ {k} + \lambda_ {k}\right) = \left(\cos \beta_ {k} - \sin \varphi_ {0} \sin \varphi_ {k}\right) / \cos \varphi_ {0} \cos \varphi_ {k}
$$

$$
\sin \varphi_ {k} = \sin \varphi_ {0} \cos \beta_ {k} + \cos \varphi_ {0} \sin \beta_ {k} \cos \psi_ {0}
$$

$$
\psi_ {0} = \psi_ {a} + \gamma_ {k} \tag {13.11-19}
$$

至此，我们给出了用关机点参数计算射程和横向落点偏差的解析计算公式。注意到关机点的经度 $\lambda_{k}$ 是关机时间 $t_{k}$ 的函数，因而射程和横向偏差 H 也是 $t_{k}$ 的函数。对式(13.11-19)这一组相当复杂的非线性函数关系，我们可以写成函数关系的一般形式

$$
\mathcal {L} = \mathcal {L} (\boldsymbol {x} _ {k}, t _ {k}) \tag {13.11-20}
$$

$$
H = H \left(\boldsymbol {x} _ {k}, t _ {k}\right) \tag {13.11-21}
$$

式中

$$
\boldsymbol {x} _ {k} = \left(x _ {1 k}, x _ {2 k}, x _ {3 k}, x _ {4 k}, x _ {5 k}, x _ {6 k}\right) ^ {\tau} = \left(v _ {x k}, v _ {y k}, v _ {z k}, x _ {k}, y _ {k}, z _ {k}\right) ^ {\tau}
$$

若关机点参数都是标准值，那么导弹的射程就等于预定的射程

$$
\mathcal {L} (\overline {{{{\boldsymbol {x}}}}} _ {k}, \overline {{{{t}}}} _ {k}) = \overline {{{{\mathcal {L}}}}} \tag {13.11-22}
$$

落点的横向偏差 H 为零

$$
H (\overline {{{\boldsymbol {x}}}} _ {k}, t _ {k}) = \overline {{{H}}} = 0 \tag {13.11-23}
$$

当实际关机点参数偏离标准值时，实际的落点 $b$ 将偏离预定的目标 $\overline{b}$ 。由于主动段的干扰较小且有火箭控制系统的作用，因此关机点参数偏差一般属于小偏差范围。利用弹道摄动理论在标准关机点处将式(13.11-20)和(13.11-21)线性展开，就得到射程偏差 $\Delta \mathcal{L}$ 和落点横向偏差 $\Delta H$ 的线性近似表示式

$$
\Delta \mathcal {G} (t _ {k}) = (\boldsymbol {a}, \Delta \boldsymbol {x} (t _ {k})) + \frac {\partial \mathcal {L}}{\partial t _ {k}} \Delta t _ {k} \tag {13.11-24}
$$

$$
\Delta H (t _ {k}) = (\boldsymbol {b}, \Delta \boldsymbol {x} (t _ {k})) + \frac {\partial H}{\partial t _ {k}} \Delta t _ {k} \tag {13.11-25}
$$

式中符号 $(\cdot,\cdot)$ 表示向量的内积，而

$$
\boldsymbol {a} = \left[ \frac {\partial \mathscr {L}}{\partial x _ {1 k}}, \frac {\partial \mathscr {L}}{\partial x _ {2 k}}, \frac {\partial \mathscr {L}}{\partial x _ {3 k}}, \frac {\partial \mathscr {L}}{\partial x _ {4 k}}, \frac {\partial \mathscr {L}}{\partial x _ {5 k}}, \frac {\partial \mathscr {L}}{\partial x _ {6 k}} \right] ^ {\tau} \tag {13.11-26}
$$

$$
\boldsymbol {b} = \left[ \frac {\partial H}{\partial x _ {1 k}}, \frac {\partial H}{\partial x _ {2 k}}, \frac {\partial H}{\partial x _ {3 k}}, \frac {\partial H}{\partial x _ {4 k}}, \frac {\partial H}{\partial x _ {5 k}}, \frac {\partial H}{\partial x _ {6 k}} \right] ^ {\tau} \tag {13.11-27}
$$

关机点状态变量偏差 $\Delta\boldsymbol{x}(t_{k})$ 是指实际关机时刻 $(t_{k})$ 的状态量与标准关机时刻 $(\bar{t}_{k})$ 的标准值之差， $\Delta\boldsymbol{x}(t_{k})$ 表示全偏差。

$$
\Delta \boldsymbol {x} (t _ {k}) = \boldsymbol {x} (t _ {k}) - \overline {{{{\boldsymbol {x}}}}} (\overline {{{{t}}}} _ {k}) \tag {13.11-28}
$$

$$
\Delta t _ {k} = t _ {k} - \bar {t} _ {k} \tag {13.11-29}
$$

各偏导数 $\frac{\partial\mathscr{L}}{\partial x_{ik}},\frac{\partial H}{\partial x_{ik}},\frac{\partial\mathscr{L}}{\partial t_{k}},\frac{\partial H}{\partial t_{k}}(i=1,2,3,4,5,6)$ 的计算公式可由射程计算公式求出。当标准弹道确定之后，这些偏导数都是确定的常数。把式(13.11-28)和(13.11-29)代入式(13.11-24)，并将 $t_{k}$ 换成 t，得到射程偏差函数

$$
\Delta \mathcal {L} (t) = (\boldsymbol {a}, \boldsymbol {x} (t)) - (\boldsymbol {a}, \overline {{\boldsymbol {x}}} (\bar {t} _ {k})) + \frac {\partial \mathcal {L}}{\partial t _ {k}} (t - \bar {t} _ {k}) \tag {13.11-30}
$$

这是一个用 t 时刻的运动参数 $\boldsymbol{x}(t)$ 预测导弹射程偏差的公式, 可以看出 $\Delta\mathcal{D}(t)$ 是时间的单调递增函数, 在接近关机点时, $\Delta\mathcal{D}(t)$ 由负值通过零变为正值。式 (13.11-30) 是射程控制的基本公式。

式(13.11-24)和(13.11-25)描述的射程偏差 $\Delta\mathscr{L}$ 和横向偏差 $\Delta H$ 就是弹道式导弹主动段终端受控参数的基本公式。有时我们也用关机点参数在关机时刻的等时偏差 $\delta\boldsymbol{x}(t_{k})$ 来表示这些终端受控的参数

$$
\Delta \mathcal {L} (t _ {k}) = (\boldsymbol {a}, \delta \boldsymbol {x} (t _ {k})) + \mathcal {L} _ {k} \Delta t _ {k} \tag {13.11-31}
$$

$$
\Delta H (t _ {k}) = (\boldsymbol {b}, \delta \boldsymbol {x} (t _ {k})) + \dot {H} _ {k} \Delta t _ {k} \tag {13.11-32}
$$

式中

$$
\delta \boldsymbol {x} (t _ {k}) = \boldsymbol {x} (t _ {k}) - \overline {{{{\boldsymbol {x}}}}} (t _ {k}) \tag {13.11-33}
$$

$$
\dot {\mathcal {L}} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial \mathcal {L}}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k}) + \frac {\partial \mathcal {L}}{\partial t _ {k}} \tag {13.11-34}
$$

$$
\dot {H} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial H}{\partial x _ {i k}} \overline {{{{\boldsymbol {x}}}}} _ {i} (\bar {t} _ {k}) + \frac {\partial H}{\partial t _ {k}} \tag {13.11-35}
$$

因为关机时刻 $\Delta\mathcal{L}(t_{k})=0$ ，由式(13.11-31)可得

$$
\Delta t _ {k} = \frac {- 1}{\dot {\mathcal {L}} _ {k}} (\boldsymbol {a}, \delta \boldsymbol {x} (t _ {k})) \tag {13.11-36}
$$

将式(13.11-36)代入式(13.11-32)得到

$$
\Delta H (t _ {k}) = \left(\left[ \boldsymbol {b} - \frac {\dot {H} _ {k}}{\dot {\mathcal {L}} _ {k}} \boldsymbol {a} \right], \delta \boldsymbol {x} (t _ {k})\right) \tag {13.11-37}
$$

此式是横向制导系统终端受控参数的表达式，因而也是横向制导的基本方程。

现在我们再来考察发射人造卫星过程中的制导问题。首先讨论人造地球卫星的轨道参数计算方法。

人造地球卫星在惯性空间沿平面椭圆轨道飞行。卫星的运动规律与弹道导弹自由飞行段的运动规律是相同的。如果我们知道了卫星运载火箭主动段关机点（即卫星入轨点）的运动参数 $x_{k}$ 和时间 $t_{k}$ ，就可确定人造卫星在惯性空间的运动。通常采用“轨道根数”来描述卫星轨道。为了说明轨道根数的含义，我们建立地心惯性坐标系 $O_{E}-X_{E}Y_{E}Z_{E}$ （见图 13.11-3） $O_{E}$ 为地心， $Z_{E}$ 轴指向北极， $X_{E}$ 轴在赤道平面内指向惯性空间一固定点——春分点 $\gamma$ （春分点的位置可由天文年历查得）， $Y_{E}$ 轴在赤道平面内按右手坐标系确定。

卫星的轨道平面在地球表面截出一个大圆，此圆与赤道交于两点，当卫星从南向北穿过赤道平面时，对应的点称为升交点 $\Omega$ ，从北向南穿过赤道平面时，相应的点称为降交点 $\overline{O}$ 。能完全确定卫星轨道的六个轨道根数是：轨道长半轴 $a$ （或半通径 $p$ ）；偏心率 $e$ ；通过近地点的时间 $t_p$ ；轨道平面倾角 $i$ ；升交点赤经 $\Omega$ ；近地点幅角 $\omega$ 。升交点赤经 $\Omega$ 和轨道平面倾角 $i$ 确定轨道平面在惯性空间的位置，近地点幅角 $\omega$ 确定椭圆在轨道平面内的位置，半通径 $p$ 和偏心率 $e$ 确定椭圆的形状和大小。当六个轨道根数给定后，卫星在惯性空间中任一时刻的位置和速度即可完全确定。

根据已知轨道根数去确定卫星的位置和速度，是“卫星预报”所研究的问题。根据已知某些时刻卫星的位置和速度去确定轨道根数，是“卫星定轨”研究的问题。我们研究的是运载火箭的制导问题，其任务是将卫星准确送入预定轨道，即要控制关机时刻（入轨点）的位置和速度，使卫星的轨道根数等于预定值。这个问题与“定轨”问题关系密切。为了找出卫星轨道根数与关机点参数间的关系，我们先建立坐标系 $O_E - \xi \eta \zeta$ （见图 13.11-3），坐标原点为地心 $O_E, \xi$ 轴与过近地点的地心距矢径一致，在轨道平面内取 $\eta$ 轴垂直于 $\xi$ 轴， $\zeta$ 轴与卫星动量矩 $r_E \times v_E$ 的方向一 致，使 $O_{E}-\xi\eta\zeta$ 构成右手坐标系。三轴的单位矢量分别记为 $i_{x}, i_{y}, i_{z}$ 。

> 此处省略原书 **图 13.11-3**

如果在地心惯性坐标系中已知关机点的位置和速度 $r_{k}, v_{k}$ 则有

$$
\boldsymbol {i} _ {\xi} = \frac {\boldsymbol {r} _ {E} \times v _ {E}}{\| \boldsymbol {r} _ {E} \times v _ {E} \|} \tag {13.11-38}
$$

$$
\boldsymbol {r} _ {k} \times v _ {k} = \left| \begin{array}{c c c} \boldsymbol {i} _ {x _ {E}} & \boldsymbol {i} _ {y _ {E}} & \boldsymbol {i} _ {z _ {E}} \\ x _ {E} & y _ {E} & z _ {E} \\ \dot {x} _ {E} & \dot {y} _ {E} & \dot {z} _ {E} \end{array} \right| \tag {13.11-39}
$$

$$
\left\| \boldsymbol {r} _ {k} \times v _ {k} \right\| = \left[ \left(y _ {E} \dot {z} _ {E} - z _ {E} \dot {y} _ {E}\right) ^ {2} + \left(z _ {E} \dot {x} _ {E} - x _ {E} \dot {z} _ {E}\right) ^ {2} + \left(x _ {E} \dot {y} _ {E} - y _ {E} \dot {x} _ {E}\right) ^ {2} \right] ^ {\frac {1}{2}} \tag {13.11-40}
$$

由坐标系 $O_{E} - X_{E}Y_{E}Z_{E}$ 与坐标系 $O_{E} - \xi \eta \zeta$ 间的转换关系可知

$$
\dot {\boldsymbol {i}} _ {s} = \sin \Omega \sin \ddot {\boldsymbol {u}} _ {x _ {E}} - \cos \Omega \sin \ddot {\boldsymbol {u}} _ {y _ {E}} + \cos \ddot {\boldsymbol {u}} _ {z _ {E}} \tag {13.11-41}
$$

将式(13.11-39)，(13.11-40)和(13.11-41)代入式(13.11-38)可得出

$$
\frac {\mathbf {y} _ {E} \dot {z} _ {E} - z _ {E} \dot {y} _ {E}}{\| \mathbf {r} _ {E} \times v _ {E} \|} = \sin \Omega \sin i
$$

$$
\frac {\boldsymbol {x} _ {E} \dot {\boldsymbol {z}} _ {E} - z _ {E} \dot {\boldsymbol {x}} _ {E}}{\| \boldsymbol {r} _ {E} \times v _ {E} \|} = \cos \Omega \sin i
$$

$$
\frac {\boldsymbol {x} _ {E} \dot {\boldsymbol {y}} _ {E} - \boldsymbol {y} _ {E} \dot {\boldsymbol {x}} _ {E}}{\| \boldsymbol {r} _ {E} \times \upsilon_ {E} \|} = \cos i \tag {13.11-42}
$$

由式(13.11-42)即可确定角 $\Omega$ 及角 i。由椭圆基本关系知，半通径

$$
p = \frac {h ^ {2}}{\mu} = \frac {\| \boldsymbol {r} _ {E} \times v _ {E} \| ^ {2}}{\mu} \tag {13.11-43}
$$

偏心率为

$$
e = \left[ 1 + \left(v _ {E} ^ {2} - \frac {2 \mu}{r _ {E}}\right) \frac {p}{\mu} \right] ^ {\frac {1}{2}} \tag {13.11-44}
$$

式中

$$
v _ {E} ^ {2} = \dot {x} _ {E} ^ {2} + \dot {y} _ {E} ^ {2} + \dot {z} _ {E} ^ {2} \tag {13.11-45}
$$

$$
r _ {E} = (x _ {E} ^ {2} + y _ {E} ^ {2} + z _ {E} ^ {2}) ^ {\frac {1}{2}} \tag {13.11-46}
$$

由轨道方程

$$
r _ {E} = \frac {p}{1 + e \cos f _ {k}} \tag {13.11-47}
$$

和

$$
\dot {r} _ {E} = \sqrt {\frac {\mu}{p}} e \sin f _ {k} = \left(\boldsymbol {v} _ {E}, \frac {\boldsymbol {r} _ {E}}{r _ {E}}\right) = \frac {x _ {E} \dot {\boldsymbol {x}} _ {E} + y _ {E} \dot {\boldsymbol {y}} _ {E} + z _ {E} \dot {\boldsymbol {z}} _ {E}}{r _ {E}} \tag {13.11-48}
$$

可确定出关机点的真近点角 $f_{k}$ ，由

$$
\tan \frac {E _ {k}}{2} = \sqrt {\frac {1 - e}{1 + e}} \tan \frac {f _ {k}}{2} \tag {13.11-49}
$$

又可求出关机点的偏近点角 $E_{k}$ 。再由开普勒方程

$$
t _ {k} - t _ {p} = \sqrt {\frac {a ^ {3}}{\mu}} (E _ {k} - e \sin E _ {k}) \tag {13.11-50}
$$

就可求出 $t_{p}$ 。最后，若令升交点 $\Omega$ 处的地心矩矢径的单位矢量为 $\bar{\beta}$ ，则

$$
\overline {{{\beta}}} = \cos \Omega \boldsymbol {i} _ {x _ {E}} + \sin \Omega \boldsymbol {i} _ {y _ {E}} \tag {13.11-51}
$$

由

$$
\left[ \overline {{\beta}}, \frac {\boldsymbol {r} _ {E}}{r _ {E}} \right] = \frac {x _ {E} \cos \Omega + y _ {E} \sin \Omega}{r _ {E}} = \cos (\omega + f _ {k}) \tag {13.11-52}
$$

和

$$
\left\| \overline {{\beta}} \times \frac {\boldsymbol {r} _ {E}}{r _ {E}} \right\| = \frac {1}{r _ {E}} [ z _ {E} ^ {2} + (y _ {E} \cos \Omega - x _ {E} \sin \Omega) ^ {2} ] ^ {\frac {1}{2}} = \sin (\omega + f _ {k}) \tag {13.11-53}
$$

可确定 $\omega$ 角。至此得到了六个轨道根数与运载火箭关机点运动参数 $(r_{E}, v_{E}, t_{k})$ 之间的关系。类似于弹道式导弹射程偏差和横向落点偏差公式，我们也可以求出卫星轨道根数偏差与关机点运动参数偏差的线性化关系式，并作为运载火箭主动段的终端受控参数的状态方程。

然而对于不同用途的卫星，具体的受控参数并不一定需要用六个轨道根数来表示。而且某些运载火箭受到控制能力的限制，也不能使六个轨道根数都达到预 定值。通常是根据具体要求和可能对某些最重要的轨道参数进行控制，例如控制轨道周期 T，轨道平面倾角 i，近地点高度 $h_{p}$ ，远地点高度 $h_{a}$ ，入轨点星下点位置 $(\varphi_{k}, \lambda_{k})$ 等。下面给出用发射点惯性坐标系中运载火箭关机点的参数 $(x_{k}, t_{k})$ 计算这些常用的轨道参数的公式。

轨道周期

$$
T = 2 \pi \sqrt {\frac {a ^ {3}}{\mu}} \tag {13.11-54}
$$

在球面三角形 $N\Omega K'$ 中（见图 13.11-4)，应用正弦定理可求出轨道平面倾角 i （图中 $K'$ 为运载火箭入轨点在地球上的投影点）

$$
\cos i = \cos \varphi_ {k} \sin \psi_ {k} \tag {13.11-55}
$$

> 此处省略原书 **图 13.11-4**

近地点高度

$$
h _ {p} = \frac {p}{1 + e} - r _ {0} \tag {13.11-56}
$$

远地点高度

$$
h _ {a} = \frac {p}{1 - e} - r _ {0} \tag {13.11-57}
$$

以上公式中出现的椭圆长半轴 a，半通径 p，偏心率 e，关机点射向角 $\psi_{k}$ ，纬度 $\varphi_{k}$ ，经度 $\lambda_{k}$ 等用关机点参数 $x_{k}$ 、 $t_{k}$ 表示的计算公式，已在前面射程计算公式中给出。可以看出，除了入轨点经度 $\lambda_{k}$ 与关机时间 $t_{k}$ 有关外，其他参数都只是关机点运动参数 $x_{k}$ 的函数，所以上述轨道参数的一般表示式为

$$
T = T \left(\boldsymbol {x} _ {k}\right), \quad i = i \left(\boldsymbol {x} _ {k}\right), \quad h _ {p} = h _ {p} \left(\boldsymbol {x} _ {k}\right), \quad h _ {a} = h _ {a} \left(\boldsymbol {x} _ {k}\right)
$$

$$
\varphi_ {k} = \varphi_ {k} (\boldsymbol {x} _ {k}), \quad \lambda_ {k} = \lambda_ {k} (\boldsymbol {x} _ {k}, t _ {k}) \tag {13.11-58}
$$

利用摄动理论，得到轨道参数偏差的线性表示式

$$
\Delta T = \left(\boldsymbol {c}, \Delta \boldsymbol {x} \left(t _ {k}\right)\right), \quad \Delta i = \left(\boldsymbol {d}, \Delta \boldsymbol {x} \left(t _ {k}\right)\right), \quad \Delta h _ {p} = \left(\boldsymbol {e}, \Delta \boldsymbol {x} \left(t _ {k}\right)\right)
$$

$$
\Delta h _ {a} = (\boldsymbol {f}, \Delta \boldsymbol {x} (t _ {k})), \quad \Delta \varphi_ {k} = (\boldsymbol {g}, \Delta \boldsymbol {x} (t _ {k}))
$$

$$
\Delta \lambda_ {k} = (\boldsymbol {h}, \Delta \boldsymbol {x} (t _ {k})) + \frac {\partial \lambda_ {k}}{\partial t _ {k}} \Delta t _ {k} \tag {13.11-59}
$$

式中

$$
\boldsymbol {c} = \left[ \frac {\partial T}{\partial x _ {1 k}}, \frac {\partial T}{\partial x _ {2 k}}, \frac {\partial T}{\partial x _ {3 k}}, \frac {\partial T}{\partial x _ {4 k}}, \frac {\partial T}{\partial x _ {5 k}}, \frac {\partial T}{\partial x _ {6 k}} \right] ^ {\tau}
$$

$$
\boldsymbol {d} = \left[ \frac {\partial i}{\partial x _ {1 k}}, \frac {\partial i}{\partial x _ {2 k}}, \frac {\partial i}{\partial x _ {3 k}}, \frac {\partial i}{\partial x _ {4 k}}, \frac {\partial i}{\partial x _ {5 k}}, \frac {\partial i}{\partial x _ {6 k}} \right] ^ {\tau}
$$

$$
\boldsymbol {e} = \left[ \frac {\partial h _ {p}}{\partial x _ {1 k}}, \frac {\partial h _ {p}}{\partial x _ {2 k}}, \frac {\partial h _ {p}}{\partial x _ {3 k}}, \frac {\partial h _ {p}}{\partial x _ {4 k}}, \frac {\partial h _ {p}}{\partial x _ {5 k}}, \frac {\partial h _ {p}}{\partial x _ {6 k}} \right] ^ {\tau}
$$

$$
\boldsymbol {f} = \left[ \frac {\partial h _ {a}}{\partial x _ {1 k}}, \frac {\partial h _ {a}}{\partial x _ {2 k}}, \frac {\partial h _ {a}}{\partial x _ {3 k}}, \frac {\partial h _ {a}}{\partial x _ {4 k}}, \frac {\partial h _ {a}}{\partial x _ {5 k}}, \frac {\partial h _ {a}}{\partial x _ {6 k}} \right] ^ {\tau}
$$

$$
\boldsymbol {g} = \left[ \frac {\partial \varphi_ {k}}{\partial x _ {1 k}}, \frac {\partial \varphi_ {k}}{\partial x _ {2 k}}, \frac {\partial \varphi_ {k}}{\partial x _ {3 k}}, \frac {\partial \varphi_ {k}}{\partial x _ {4 k}}, \frac {\partial \varphi_ {k}}{\partial x _ {5 k}}, \frac {\partial \varphi_ {k}}{\partial x _ {6 k}} \right] ^ {\tau}
$$

$$
\boldsymbol {h} = \left[ \frac {\partial \lambda_ {k}}{\partial x _ {1 k}}, \frac {\partial \lambda_ {k}}{\partial x _ {2 k}}, \frac {\partial \lambda_ {k}}{\partial x _ {3 k}}, \frac {\partial \lambda_ {k}}{\partial x _ {4 k}}, \frac {\partial \lambda_ {k}}{\partial x _ {5 k}}, \frac {\partial \lambda_ {k}}{\partial x _ {6 k}} \right] ^ {\tau} \tag {13.11-60}
$$

所有这些偏导数都是由标准弹道、标准关机点所决定的常数。同样，也可用关机时刻关机点参数的等时偏差 $\delta\boldsymbol{x}(t_{k})$ ，表示这些轨道参数的偏差。

$$
\Delta T = (\boldsymbol {c}, \delta \boldsymbol {x} (t _ {k})) + \dot {T} _ {k} \Delta t _ {k}, \Delta i = (\boldsymbol {d}, \delta \boldsymbol {x} (t _ {k})) + \dot {I} _ {k} \Delta t _ {k}
$$

$$
\Delta h _ {p} = \left(\boldsymbol {e}, \delta \boldsymbol {x} \left(t _ {k}\right)\right) + \dot {h} _ {p _ {k}} \Delta t _ {k}, \Delta h _ {a} = \left(\boldsymbol {f}, \delta \boldsymbol {x} \left(t _ {k}\right)\right) + \dot {h} _ {a _ {k}} \Delta t _ {k}
$$

$$
\Delta \varphi_ {k} = (\boldsymbol {g}, \delta \boldsymbol {x} (t _ {k})) + \dot {\varphi} _ {k} \Delta t _ {k}, \Delta \lambda_ {k} = (\boldsymbol {h}, \delta \boldsymbol {x} (t _ {k})) + \dot {\lambda} _ {k} \Delta t _ {k} \tag {13.11-61}
$$

式中

$$
\dot {T} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial T}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k}), \quad \dot {I} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial i}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k})
$$

$$
\dot {h} _ {p k} = \sum_ {i = 1} ^ {6} \frac {\partial h _ {p}}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k}), \quad \dot {h} _ {a k} = \sum_ {i = 1} ^ {6} \frac {\partial h _ {a}}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k})
$$

$$
\dot {\varphi} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial \varphi_ {k}}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k}), \quad \dot {\lambda} _ {k} = \sum_ {i = 1} ^ {6} \frac {\partial \lambda_ {k}}{\partial x _ {i k}} \vec {x} _ {i} (\bar {t} _ {k}) + \frac {\partial \lambda_ {k}}{\partial t _ {k}} \tag {13.11-62}
$$

式(13.11-59)和式(13.11-61)是运载火箭制导的基本方程。可以看出，这些方程和弹道式导弹制导的基本方程完全类似。下面我们以弹道式导弹为例，根据本节中给出的基本方程式(13.11-30)，(13.11-37)来研究弹道火箭的制导问题。以式(13.11-30)为基础研究射程控制系统，以式(13.11-37)为基础研究横向制导系统。

#### 13.12 关机方程设计

弹道火箭的任务是将导弹的战斗部送到已知的目标，或者将有效载荷送入预定的运行轨道。当发射点和目标，或者卫星运行轨道参数确定之后，可以按照火箭发动机和弹体结构的额定参数，大气和地球引力场的标准参数，事先设计标准飞行弹道。如果在实际飞行中一切条件都和标准飞行条件一样，则制导系统非常简单，只需弹上计时机构在预定的关机时刻发出关闭发动机的信号就行了。因为发动机关闭之后导弹沿标准被动段弹道飞行，就能准确命中目标。但是，实际飞行条件总会偏离标准条件，例如发动机推力偏差、弹体结构参数偏差、大气条件偏差等，我们称这些偏差为作用于火箭上的干扰。在这些干扰作用下火箭不能沿标准弹道飞行，如果不加适当的制导，仍然按照预定标准关机时刻关机，必然出现关机点运动参数偏差 $\delta x(t_k)$ ，由式(13.11-24)和(13.11-25)知道，导弹的实际落点对预定目标将产生射程偏差 $\Delta \mathcal{A}(\bar{t}_k)$ 和横向偏差 $\Delta H(\bar{t}_k)$ 。在各种干扰存在的条件下，研究引导导弹准确命中目标的问题，就是导弹的制导问题。控制射程偏差为零的系统称为射程控制系统，控制横向偏差为零的系统称为横向制导系统。我们知道射程偏差是外干扰作用引起实际弹道偏离标准弹道造成的。式(13.11-24)是弹道参数偏差 $\Delta x(t_k)$ 、关机时间偏差 $\Delta t_k$ 与射程偏差 $\Delta \mathcal{A}(t_k)$ 间的数学关系，这个关系说明，只要参数偏差向量 $(\Delta x(t_k), \Delta t_k)^{\tau}$ 与偏导数向量 $(a, \partial \mathcal{A} / \partial t_k)^{\tau}$ 正交，就可使射程偏差为零。从弹道学的观点看，其物理实质是达到同一目标的被动段弹道可有无数条，或者说为达到同一射程 $\mathcal{G} = \mathcal{G}(x(t_k), t_k)$ ，式(13.11-20)有无穷多组解。我们只需求出标准值附近的任一组解，即在标准关机点附近选择一个实际关机点，使 $\Delta \mathcal{G}(t_k) = 0$ ，并不需要把导弹控制到标准关机点，使 $\Delta \mathcal{G}(\bar{t}_k) = 0$ 。显然，这样做将给制导系统的设计带来很大的方便。进一步研究式(13.11-30)发现，弹道参数 $x(t)$ （主要是 $v_x, v_y, x, y$ )是飞行时间 $t$ 的单调递增函数，而且当 $t < t_k$ 时有

$$
\left\{(\boldsymbol {a}, \boldsymbol {x} (\bar {t} _ {k})) + \frac {\partial \mathscr {L}}{\partial t _ {k}} \bar {t} _ {k} \right\} > \left\{(\boldsymbol {a}, \boldsymbol {x} (t)) + \frac {\partial \mathscr {L}}{\partial t _ {k}} t \right\} > 0 \tag {13.12-1}
$$

因而射程偏差函数 $\Delta\mathcal{A}(t)$ 在主动段飞行过程中是时间 t 的单调递增函数，而且最初是负值，逐渐增加到零再达到正值。 $\Delta\mathcal{A}(t_{k})=0$ 的时刻 $t_{k}$ ，就是关闭发动机使导弹开始自由飞行的时刻。因此射程控制归结为对关机时间的控制。

从控制系统的观点看，主动段射程控制系统还具有以下特点。首先，它是一个摄动预测制导系统。在弹道摄动原理的基础上得到的射程控制基本方程式(13.11-30),是一个用 t 时刻的系统状态变量 $\boldsymbol{x}(t)$ 预测落点射程偏差的公式，射程控制是根据这个预测值 $\Delta\mathcal{A}(t)$ 来进行的。其次，它是一个反馈控制系统，因为它的控制信号 $\Delta\mathcal{A}(t)$ 是用系统的状态变量 $\boldsymbol{x}(t)$ 计算出来的。但是它是一个特殊的状态 反馈控制系统, 当根据 $\boldsymbol{x}(t)$ 预测出的 $\Delta\mathcal{D}(t)<0$ 时, 射程控制系统不发出任何指令, 火箭发动机继续按预定程序工作, 当根据 $\boldsymbol{x}(t)$ 计算出 $\Delta\mathcal{D}(t_{k})=0$ 时, 发出关机指令, 关闭发动机。即这种反馈控制是通过让发动机继续工作或是停止工作来实现的。如果 $t_{k}$ 时刻根据系统的状态变量 $\boldsymbol{x}(t_{k})$ , 按自由飞行弹道预测的射程偏差为

$$
\Delta \mathcal {G} (t _ {k}) = (\boldsymbol {a}, \Delta \boldsymbol {x} (t _ {k})) + \frac {\partial \mathcal {L}}{\partial t _ {k}} \Delta t _ {k} = 0 \tag {13.12-2}
$$

则 $t_{k}$ 以后不需要发动机推力，火箭将在地球引力加速度作用下沿椭圆弹道命中目标。我们称发动机的推力加速度为控制加速度，地球引力加速度为零控加速度，则 $t_{k}$ 时满足约束条件

$$
\Delta \mathscr {L} (t _ {k}) = 0
$$

的状态可称为零控无偏状态。当 $\Delta\mathcal{D}(t)<0$ 时，火箭在发动机程序推力（即控制加速度）的作用下加速飞行，并且在 $\bar{t}_{k}$ 附近某时刻达到零控无偏状态 ( $\Delta\mathcal{D}(t_{k})=0$ )，截止推力（控制加速度为零），火箭沿零控弹道（自由飞行弹道）命中目标。

在主动段飞行过程中，用来选择火箭达到零控无偏状态 $\left(\Delta\mathcal{G}(t_{k})=0\right)$ 的时刻 $t_{k}$ 的方程称为关机方程。关机方程的设计是制导系统设计的主要任务。我们可以直接从射程控制的基本方程(13.11-30)出发，代入导航计算得到的系统状态变量 $\boldsymbol{x}(t)$ ,就可得出关机方程的一般形式

$$
\Delta \mathcal {L} (t) = \sum_ {i = 1} ^ {6} \frac {\partial \mathcal {L}}{\partial x _ {i}} x _ {i} (t) + \frac {\partial \mathcal {L}}{\partial t _ {k}} \Delta t _ {k} - \sum_ {i = 1} ^ {6} \frac {\partial \mathcal {L}}{\partial x _ {i}} \overline {{{\boldsymbol {x}}}} _ {i} (\bar {t} _ {k}) \tag {13.12-3}
$$

如前所述，这是一个有导航计算的，特殊的状态反馈预测制导系统的关机方程，简称为有导航计算的关机方程。然而仅仅为了控制关机，复杂的导航计算并不是必须的，因为控制关机只需要预测出

$$
\Delta \mathscr {L} (t _ {k}) = (\boldsymbol {a}, \Delta \boldsymbol {x} (t _ {k})) + \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k}
$$

并不一定需要像飞机和舰船导航系统那样，去求飞行过程中各点的位置和速度。我们可以利用摄动理论和状态变量方法来设计直接利用加速度表输出量进行反馈控制的关机方程。

首先，我们建立射程控制系统的状态方程。为了描述这个特殊的输出反馈控制系统的状态变量除了火箭质心运动的六个参数外，还可以引入一个描述关机控制的关机状态变量 $K(t)$ , 当 $K(t_{k}) = \overline{K}(\overline{t}_{k})$ 时: 发出关闭发动机的指令。描述关机状态变量 $K(t)$ 与系统输出信号（即加速度表测量的信号 $\dot{w}_{x}, \dot{w}_{y}, \dot{w}_{z}$ ) 的关系的微分方程

$$
\dot {K} = f \left(\dot {w} _ {x}, \dot {w} _ {y}, \dot {w} _ {z}\right) \tag {13.12-4}
$$

称为关机状态量方程。

注意到一般的控制系统设计的目的，是综合出满足一定控制指标的最优控制规律。然而在射程控制这个特殊系统中，控制加速度的形式已经给定了，即发动机推力按预定程序变化，需要加以控制的是发动机工作的时间，即让发动机工作或者让它从某时刻起关闭。关机方程就是用来选择发动机的关机时刻，设计者的任务就是要找出用系统输出量 $(\dot{w}_x,\dot{w}_y,\dot{w}_z)$ 表达的关机方程的形式。显然，只要我们找出关机状态量 $K(t)$ 的表达式，就可设计出关机方程。关机状态量方程(13.12-4)中函数 $f$ 的具体形式是不知道的，只有通过设计射程控制系统来确定。下面我们就来讨论这个问题。

射程控制系统的状态方程可由式(13.10-12)和(13.12-4)合并得到

$$
\dot {\boldsymbol {x}} = A \boldsymbol {x} + \boldsymbol {u} \tag {13.12-5}
$$

系统的状态变量

$$
\boldsymbol {x} = \left(x _ {1}, x _ {2}, x _ {3}, x _ {4}, x _ {5}, x _ {6}, x _ {7}\right) ^ {\tau} = \left(v _ {x}, v _ {y}, v _ {z}, x, y, z, K\right) ^ {\tau}
$$

驱动项

$$
\boldsymbol {u} = \left(\dot {w} _ {x} + d _ {x}, \dot {w} _ {y} + d _ {y}, \dot {w} _ {z} + d _ {z}, 0, 0, 0, f\right) ^ {\tau}
$$

系数矩阵为

$$
A = \left( \begin{array}{c c c c c c c} 0 & 0 & 0 & \frac {\partial g _ {x}}{\partial x} & \frac {\partial g _ {x}}{\partial y} & \frac {\partial g _ {x}}{\partial z} & 0 \\ 0 & 0 & 0 & \frac {\partial g _ {y}}{\partial x} & \frac {\partial g _ {y}}{\partial y} & \frac {\partial g _ {y}}{\partial z} & 0 \\ 0 & 0 & 0 & \frac {\partial g _ {z}}{\partial x} & \frac {\partial g _ {z}}{\partial y} & \frac {\partial g _ {z}}{\partial z} & 0 \\ 1 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 \end{array} \right)
$$

系统的测量方程，即加速度表的测量方程为

$$
\dot {w} _ {i} = \dot {v} _ {i} - g _ {i} (i = x, y, z) \tag {13.12-6}
$$

初始条件 $t_{0}=0,\quad v_{x}(0)=v_{x0},\quad v_{y}(0)=0,\quad v_{z}(0)=v_{z0}$

$$
x (0) = y (0) = z (0) = K (0) = 0 \tag {13.12-7}
$$

注意到，如果按条件 $K(t_k) = \overline{K}(\bar{t}_k)$ 关机，即在 $t_k$ 时刻系统达到零控无偏状态，故而 $\Delta \mathcal{G}(t_k) = 0$ 。因此 $K(t_k) = \overline{K}(\bar{t}_k)$ 关机 $\Leftrightarrow \Delta \mathcal{G}(t_k) = 0$ 。 (13.12-8)

由式(13.11-24)，(13.11-28)可知

$$
\Delta \mathcal {L} (t _ {k}) = \sum_ {i = 1} ^ {6} \frac {\partial \mathcal {L}}{\partial x _ {i k}} x _ {i} (t _ {k}) + \frac {\partial \mathcal {L}}{\partial t _ {k}} \Delta t _ {k} - \sum_ {i = 1} ^ {6} \frac {\partial \mathcal {L}}{\partial x _ {i k}} \overline {{x}} _ {i} (\bar {t} _ {k}) = 0 \tag {13.12-9}
$$

现取 $\overline{K} (\bar{t}_k) = \sum_{i = 1}^{6}\frac{\partial\mathcal{L}}{\partial x_{ik}}\overline{x}_i(\bar{t}_k)$ (13.12-10)

由式(13.12-8)，(13.12-9)和(13.12-10)可知，正确的关机控制必须使关机时刻 $t_{k}$ 的状态变量满足以下关系式

$$
J (t _ {k}) = \sum_ {i = 1} ^ {6} \frac {\partial \mathscr {L}}{\partial x _ {i}} x _ {i} (t _ {k}) + \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k} - K (t _ {k}) = 0 \tag {13.12-11}
$$

我们把式(13.12-11)作为关机方程的设计指标，如果这个指标得到满足，必然使 $\Delta\mathcal{D}(t_{k})=0$ 成立。于是我们的问题归结为，对系统式(13.12-5),选择关机状态变量 $K(t)$ ,使其在实际关机时刻 $(t_{k})$ 满足终端设计指标 $J(t_{k})=0$ 。

式(13.12-5)描述的射程控制系统, 是一个七维的线性系统, 设计指标式(13.12-11)只与主动段终端状态参数有关, 所以可以利用线性系统的伴随函数方法来进行设计。式(13.12-5)对应的伴随方程为

$$
- \dot {\lambda} = A ^ {\tau} \lambda , \quad \lambda \in R _ {7} \tag {13.12-12}
$$

由布利斯公式得到

$$
(\lambda , \boldsymbol {x}) \int_ {t _ {0}} ^ {t _ {k}} = \int_ {t _ {0}} ^ {t _ {k}} (\lambda , \boldsymbol {u}) d \tau \tag {13.12-13}
$$

令 $\lambda_{1}(t_{k},t_{k}) = \frac{\partial\mathcal{L}}{\partial v_{x k}},\quad \lambda_{2}(t_{k},t_{k}) = \frac{\partial\mathcal{L}}{\partial v_{y k}},\quad \lambda_{3}(t_{k},t_{k}) = \frac{\partial\mathcal{L}}{\partial v_{z k}}$

$$
\lambda_ {4} \left(t _ {k}, t _ {k}\right) = \frac {\partial \mathscr {L}}{\partial x _ {k}}, \quad \lambda_ {5} \left(t _ {k}, t _ {k}\right) = \frac {\partial \mathscr {L}}{\partial y _ {k}}, \quad \lambda_ {6} \left(t _ {k}, t _ {k}\right) = \frac {\partial \mathscr {L}}{\partial z _ {k}}
$$

$$
\lambda \left(t _ {k}, t _ {k}\right) = - 1 \tag {13.12-14}
$$

以式(13.12-14)为终端条件，解伴随方程(13.12-12),将得出的伴随函数代入式(13.12-13),并利用式(13.12-11)可得出

$$
\begin{array}{l} J (t _ {k}) = \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k} + \lambda_ {1} (t _ {0}, t _ {k}) v _ {x 0} + \lambda_ {3} (t _ {0}, t _ {k}) v _ {z 0} \\ + \int_ {t _ {0}} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , t _ {k}) (\dot {w} _ {x} + d _ {x}) + \lambda_ {2} (\tau , t _ {k}) (\dot {w} _ {y} + d _ {y}) + \lambda_ {3} (\tau , t _ {k}) (\dot {w} _ {z} + d _ {z}) \right. \\ + \lambda_ {7} (\tau , t _ {k}) f (\dot {w} _ {x}, \dot {w} _ {y}, \dot {w} _ {z}) \} d \tau = 0 \tag {13.12-15} \\ \end{array}
$$

由伴随方程(13.12-12)显然有

$$
\dot {\lambda} _ {7} = 0 \tag {13.12-16}
$$

所以 $\lambda_{7}(t,t_{k})\equiv\lambda_{7}(t_{k},t_{k})=-1$ (13.12-17)

式 $(13.12-15)$ 可化为

$$
\begin{array}{l} K (t _ {k}) = \int_ {0} ^ {t _ {k}} f (\dot {w} _ {x}, \dot {w} _ {y}, \dot {w} _ {z}) d \tau \\ = \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k} + \lambda_ {1} (t _ {0}, t _ {k}) v _ {x 0} + \lambda_ {3} (t _ {0}, t _ {k}) v _ {z 0} \\ + \int_ {0} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , t _ {k}) \dot {w} _ {x} (\tau) + \lambda_ {2} (\tau , t _ {k}) \dot {w} _ {y} (\tau) + \lambda_ {3} (\tau , t _ {k}) \dot {w} _ {z} (\tau) \right\} d \tau \\ \end{array}
$$

$$
+ \int_ {0} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , t _ {k}) d _ {x} + \lambda_ {2} (\tau , t _ {k}) d _ {y} + \lambda_ {3} (\tau , t _ {k}) d _ {z} \right\} d \tau \tag {13.12-18}
$$

利用分部积分法则，并注意到伴随方程(13.12-12)和 $\dot{\boldsymbol{w}}(t_{0})=0$ ,式(13.12-18)可化为

$$
\begin{array}{l} K (t _ {k}) = \frac {\partial \mathscr {L}}{\partial v _ {x k}} w _ {x} (t _ {k}) + \frac {\partial \mathscr {L}}{\partial v _ {y k}} w _ {y} (t _ {k}) + \frac {\partial \mathscr {L}}{\partial v _ {z k}} w _ {z} (t _ {k}) \\ + \int_ {0} ^ {t _ {k}} \left\{\lambda_ {4} (\tau , t _ {k}) w _ {x} (\tau) + \lambda_ {5} (\tau , t _ {k}) w _ {y} (\tau) + \lambda_ {6} (\tau , t _ {k}) w _ {z} (\tau) \right\} d \tau \\ + \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k} + \lambda_ {1} (t _ {0}, t _ {k}) v _ {x 0} + \lambda_ {3} (t _ {0}, t _ {k}) v _ {z 0} \\ + \int_ {0} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , t _ {k}) d _ {x} + \lambda_ {2} (\tau , t _ {k}) d _ {y} + \lambda_ {3} (\tau , t _ {k}) d _ {z} \right\} d \tau \tag {13.12-19} \\ \end{array}
$$

显然标准关机状态变量 $\overline{K}(\overline{t}_{k})$ 也可以表达成类似的形式

$$
\begin{array}{l} \overline {{{K}}} \left(\bar {t} _ {k}\right) = \frac {\partial \mathscr {L}}{\partial v _ {x k}} \bar {w} _ {x} \left(\bar {t} _ {k}\right) + \frac {\partial \mathscr {L}}{\partial v _ {y k}} \bar {w} _ {y} \left(\bar {t} _ {k}\right) + \frac {\partial \mathscr {L}}{\partial v _ {z k}} \bar {w} _ {z} \left(\bar {t} _ {k}\right) \\ + \int_ {0} ^ {\tau_ {k}} \left\{\lambda_ {4} (\tau , \bar {t} _ {k}) \overline {{{w}}} _ {x} (\tau) + \lambda_ {5} (\tau , t _ {k}) \overline {{{w}}} _ {y} (\tau) + \lambda_ {6} (\tau , t _ {k}) \overline {{{w}}} _ {z} (\tau) \right\} d \tau \\ + \lambda_ {1} \left(t _ {0}, \bar {t} _ {k}\right) v _ {x 0} + \lambda_ {3} \left(t _ {0}, \bar {t} _ {k}\right) v _ {z 0} \\ + \int_ {0} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , \bar {t} _ {k}) d _ {x} + \lambda_ {2} (\tau , \bar {t} _ {k}) d _ {y} + \lambda_ {3} (\tau , \bar {t} _ {k}) d _ {z} \right\} d \tau \tag {13.12-20} \\ \end{array}
$$

因而关机条件可表示为

$$
K (t _ {k}) - \overline {{{K}}} (\bar {t} _ {k}) = 0 \tag {13.12-21}
$$

再令

$$
\begin{array}{l} Q = \frac {\partial \mathscr {L}}{\partial t _ {k}} \Delta t _ {k} + \lambda_ {1} (t _ {0}, t _ {k}) v _ {x 0} + \lambda_ {3} (t _ {0}, t _ {k}) v _ {z 0} \\ + \int_ {0} ^ {t _ {k}} \left\{\lambda_ {1} (\tau , t _ {k}) d _ {x} + \lambda_ {2} (\tau , t _ {k}) d _ {y} + \lambda_ {3} (\tau , t _ {k}) d _ {z} \right\} d \tau \\ - \left[ \lambda_ {1} \left(t _ {0}, \bar {t} _ {k}\right) v _ {x 0} + \lambda_ {3} \left(t _ {0}, \bar {t} _ {k}\right) v _ {z 0} \right. \\ \left. + \int_ {0} ^ {\tau_ {k}} \left\{\lambda_ {1} (\tau , \bar {t} _ {k}) d _ {x} + \lambda_ {2} (\tau , \bar {t} _ {k}) d _ {y} + \lambda_ {3} (\tau , \bar {t} _ {k}) d _ {z} \right\} d \tau \right] \tag {13.12-22} \\ \end{array}
$$

Q 是关机时间偏差 $\Delta t_{k}$ 的函数, 因此可记为 $Q(\Delta t_{k})$ 。并且令

$$
\begin{array}{l} \overline {{{K}}} ^ {0} \left(\bar {t} _ {k}\right) = \frac {\partial \mathscr {L}}{\partial v _ {x k}} \bar {w} _ {x} \left(\bar {t} _ {k}\right) + \frac {\partial \mathscr {L}}{\partial v _ {y k}} \bar {w} _ {y} \left(\bar {t} _ {k}\right) + \frac {\partial \mathscr {L}}{\partial v _ {z k}} \bar {w} _ {z} \left(\bar {t} _ {k}\right) \\ + \int_ {0} ^ {\tau_ {k}} \left\{\lambda_ {4} (\tau , \bar {t} _ {k}) \overline {{{w}}} _ {x} (\tau) + \lambda_ {5} (\tau , \bar {t} _ {k}) \overline {{{w}}} _ {y} (\tau) + \lambda_ {6} (\tau , \bar {t} _ {k}) \overline {{{w}}} _ {z} (\tau) \right\} d \tau \tag {13.12-23} \\ \end{array}
$$

和

$$
K ^ {0} (t) = \frac {\partial \mathscr {L}}{\partial v _ {x k}} w _ {x} (t) + \frac {\partial \mathscr {L}}{\partial v _ {y k}} w _ {y} (t) + \frac {\partial \mathscr {L}}{\partial v _ {z k}} w _ {z} (t)
$$

$$
\begin{array}{l} + \int_ {0} ^ {t} \left\{\lambda_ {4} (\tau , t _ {k}) w _ {x} (\tau) + \lambda_ {5} (\tau , t _ {k}) w _ {y} (\tau) + \lambda_ {6} (\tau , t _ {k}) w _ {z} (\tau) \right\} d \tau \\ + Q (\Delta t _ {k}) \tag {13.12-24} \\ \end{array}
$$

关机条件式(13.12-21)可变换为

$$
K ^ {0} (t _ {k}) - \overline {{{{K}}}} ^ {0} (\bar {t} _ {k}) = 0 \tag {13.12-25}
$$

弹上制导计算机根据加速度表测量的火箭视加速度 $\dot{w}_{x}, \dot{w}_{y}, \dot{w}_{z}$ ，不断按式(13.12-24)计算出 $K^{0}(t)$ ，与由标准弹道决定的常量 $\overline{K}^{0}(\bar{t}_{k})$ 相比较，当满足式(13.12-25)时，发出关机指令，关闭发动机。由此，得到加速度表输出反馈的关机方程

$$
\Delta K ^ {0} (t) = K ^ {0} (t) - \overline {{{K}}} ^ {0} (\bar {t} _ {k}) \tag {13.12-26}
$$

和关机条件

$$
\Delta K ^ {0} \left(t _ {k}\right) = K ^ {0} \left(t _ {k}\right) - \overline {{{K}}} ^ {0} \left(\bar {t} _ {k}\right) = 0 \tag {13.12-27}
$$

#### 13.13 横向预测制导及最优控制

弹道式导弹主动段横向制导系统的任务是控制落点横向偏差。第 13.11 节中给出的横向偏差公式(13.11-37)是一个用 $t_k$ 时刻的系统状态变量 $x(t_k)$ 预测落点横向偏差的线性化公式。由于关机时间 $t_k$ 是按射程偏差 $\Delta \mathcal{D}(t_k) = 0$ 来选定的，因而 $t_k$ 时刻对应的落点横向偏差 $\Delta H(t_k)$ 不能通过选择 $t_k$ 来控制，只能通过对主动段弹道进行控制，才能使 $t_k$ 时刻的 $\Delta H(t_k) = 0$ 。注意到式(13.11-37)是落点横向偏差在关机点泰勒展开式的一阶项，它只在关机点附近才近似表示预测的落点横向偏差，但是到十分接近关机点才来控制火箭的弹道以消除主动段飞行过程中干扰作用累积的偏差 $\Delta H(t_k)$ ，往往为时过晚，在控制能力有限的情况下，会引起落点横向偏差，降低制导精度。因此必须在主动段飞行过程中求出合理的横向导引信号，及时控制火箭的飞行弹道，不断消除干扰的影响，使其在关机点处满足落点横向偏差 $\Delta H(t_k) = 0$ 的要求。

我们已经有了用 $t_{k}$ 时刻的运动参数预测落点横向偏差的公式(13.11-37)。现在还需要推导出用主动段飞行中任意时刻 t 的运动参数预测落点横向偏差 $\Delta H(t_{k})$ 的公式，我们记这个偏差为 $\Delta H(t_{k}, t)$ ，然后运用极大值原理综合出消除偏差 $\Delta H(t_{k}, t)$ 的最优控制规律。

第 13.10 节中已推导出弹道火箭主动段运动的摄动方程为

$$
\begin{array}{l} \delta \dot {\boldsymbol {x}} (t) = A (t) \delta \boldsymbol {x} (t) + B \delta \dot {\boldsymbol {w}} (t) \\ \delta \boldsymbol {x} (t _ {0}) = \delta \boldsymbol {x} _ {0} \\ \delta \dot {\boldsymbol {w}} (t) = \dot {\boldsymbol {w}} (t) - \overline {{{{\boldsymbol {w}}}}} (t) \tag {13.13-1} \\ \end{array}
$$

视加速度是由作用于火箭上除地球引力以外的力，即发动机推力和空气动力引起 的加速度，视加速度的偏差是由推力偏差、气动力偏差和火箭质量偏差等因素共同造成的，因而可将 $\delta\dot{w}$ 作为系统的干扰项。

弹道式导弹在主动段飞行过程中，由于各种干扰的作用，使实际飞行弹道偏离标准弹道，因此 $t$ 时刻之前干扰作用的效果直接反映在 $t$ 时刻的弹道参数偏差 $\delta x(t)$ 上，主动段“预测”的任务就是要用 $t$ 时刻的运动参数偏差 $\delta x(t)$ ，计算出落点横向偏差 $\Delta H(t_k, t)$ 。横向制导系统利用 $\Delta H(t_k, t)$ 形成 $t$ 时刻的反馈控制信号，以消除 $t$ 时刻之前干扰作用引起的落点横向偏差。显然， $t$ 时刻之后可能出现的干扰无法确知，所以在计算 $\Delta H(t_k, t)$ 时不予考虑，即是说从 $t$ 到 $t_k$ 的预测是按标准条件进行的。因而有

$$
\delta \dot {\boldsymbol {w}} (\tau) = 0, \quad \forall \tau \in (t, t _ {k} ] \tag {13.13-2}
$$

系统的摄动方程(13.13-1)变为齐次方程

$$
\delta \dot {\boldsymbol {x}} (t) = A (t) \delta \boldsymbol {x} (t), \quad t \in (t, t _ {k} ] \tag {13.13-3}
$$

我们的目的是由 $\delta\boldsymbol{x}(t)$ 计算 $\Delta H(t_{k}, t)$ ，而不是计算 $\delta\boldsymbol{x}(t_{k})$ 。由第 13.11 节可知，横向制导系统的终端受控参数 $\Delta H(t_{k})$ ，是关机点运动参数偏差 $\delta\boldsymbol{x}(t_{k})$ 各分量的线性组合，因而用 $\delta\boldsymbol{x}(t)$ 计算 $\Delta H(t_{k}, t)$ 的问题可用伴随函数的方法解决。式 (13.13-3) 的伴随方程为

$$
- \dot {\lambda} = A ^ {\tau} (t) \lambda \tag {13.13-4}
$$

由布利斯公式知

$$
(\lambda (t _ {k}), \delta \boldsymbol {x} (t _ {k})) = (\lambda (t), \delta \boldsymbol {x} (t)) \tag {13.13-5}
$$

令 $t=t_{k}$ 时刻的终端条件为

$$
\lambda (t _ {k}) = \left[ \boldsymbol {b} - \frac {\dot {H} _ {k}}{\dot {L} _ {k}} \boldsymbol {a} \right] \tag {13.13-6}
$$

解方程(13.13-4)，得出的伴随向量记为 $\lambda (t_k,t),t\in [t_0,t_k]$ ，将 $\lambda (t_k,t)$ 代入式(13.13-5)得

$$
\Delta H (t _ {k}, t) = \left[ \left(\boldsymbol {b} - \frac {\dot {H} _ {k}}{\dot {L} _ {k}} \boldsymbol {a}\right), \delta \boldsymbol {x} (t _ {k}) \right] = (\lambda (t _ {k}, t), \delta \boldsymbol {x} (t)) \tag {13.13-7}
$$

$\Delta H(t_{k},t)$ 表示由 t 时刻的运动参数偏差 $\delta x(t)$ 预测的落点横向偏差，或者看成 t 时刻以前的干扰引起的落点横向偏差。这种利用伴随函数方法进行的预测，建立在弹道摄动的基础上，我们称这种预测制导为摄动预测制导。因为 $\lambda(t_{k},t)$ 可以在导弹发射之前预先计算出来， $\delta x(t)$ 可由制导系统的导航计算实时给出，利用式 (13.13-7) 即可实时计算 $\Delta H(t_{k},t)$ 。用 $\Delta H(t_{k},t)$ 作为反馈控制信号，通过横向控制系统使 $\Delta H(t_{k},t)\rightarrow0$ ，即可消除飞行过程中干扰作用引起的横向偏差，从而保证在实际关机时刻 $\Delta H(t_{k})=0$ 。

和第 13.12 节一样，仅仅为了进行横向制导，复杂的导航计算并不是必须的。

我们利用摄动理论，可以推出直接用干扰测量值 $\delta\dot{w}$ 预测落点横向偏差 $\Delta H(t_{k},t)$ 的计算公式。对方程式(13.13-1)和伴随方程(13.13-4)运用布利斯公式

$$
(\lambda , \delta \boldsymbol {x}) \bigg | _ {t _ {0}} ^ {t _ {k}} = \int_ {t _ {0}} ^ {t _ {k}} (\lambda (\tau), B \delta \dot {\boldsymbol {w}} (\tau)) d \tau \tag {13.13-8}
$$

并注意到伴随方程(13.13-4)的终端条件仍然为

$$
\lambda \left(t _ {k}\right) = \boldsymbol {b} - \frac {\dot {H} _ {k}}{\dot {L} _ {k}} \boldsymbol {a}
$$

在不考虑初始条件的偏差的前提下, 即 $\delta x(t_{0})=0$ , 式(13.13-8)可化为

$$
\Delta H (t _ {k}) = (\lambda (t _ {k}), \delta \boldsymbol {x} (t _ {k})) = \int_ {t _ {0}} ^ {t _ {k}} (\lambda (t _ {k}, \tau), B \delta \dot {\boldsymbol {w}} (\tau)) d \tau \tag {13.13-9}
$$

再注意到由 t 到 $t_{k}$ 的预测是按标准条件进行的, 故干扰作用为零, 即

$$
\delta \dot {\boldsymbol {w}} (\tau) = 0, \quad \forall \tau \in (t, t _ {k} ] \tag {13.13-10}
$$

所以

$$
\Delta H (t _ {k}, t) = \int_ {t _ {0}} ^ {t} (\lambda (t _ {k}, \tau), B \delta \dot {\boldsymbol {w}} (\tau)) d \tau \tag {13.13-11}
$$

利用分部积分法，在不考虑初始干扰影响的情况下有

$$
\begin{array}{l} \Delta H (t _ {k}, t) = (\lambda (t _ {k}, t), \delta \boldsymbol {w} (t)) - \int_ {t _ {0}} ^ {t} (\dot {\lambda} (t _ {k}, \tau), B \delta \boldsymbol {w} (\tau)) d \tau \\ = \lambda_ {1} (t _ {k}, t) \delta w _ {x} (t) + \lambda_ {2} (t _ {k}, t) \delta w _ {y} (t) + \lambda_ {3} (t _ {k}, t) \delta w _ {z} (t) \\ + \int_ {t _ {0}} ^ {t} \left\{\lambda_ {4} (t _ {k}, \tau) \delta w _ {x} (\tau) + \lambda_ {5} (t _ {k}, \tau) \delta w _ {y} (\tau) + \lambda_ {6} (t _ {k}, \tau) \delta w _ {z} (\tau) \right\} d \tau \tag {13.13-12} \\ \end{array}
$$

上式是利用加速度表测量的信息计算落点横向偏差的基本公式。

伴随向量 $\lambda(t_{k}, t)$ 是随时间 t 变化的，实现起来比较复杂，在某些情况下可以采用简化的预测制导公式 $^{[16]}$ 。例如在式(13.11-37)中用 $\delta\boldsymbol{x}(t)$ 代替 $\delta\boldsymbol{x}(t_{k})$ 以后，即可得到最简单的计算公式

$$
\Delta H (t _ {k}, t) = \left[ \left(\boldsymbol {b} - \frac {\dot {H}}{\dot {L}} \boldsymbol {a}\right), \delta \boldsymbol {x} (t) \right] \tag {13.13-13}
$$

这种简化的物理意义在于，认为 $\delta\boldsymbol{x}(t)$ 中各分量互不相关地、一比一地外推到关机点。当 t 趋近于 $t_{k}$ 时，式(13.13-13)逐渐逼近式(13.13-7),在飞行过程中制导系统不断消除偏差 $\Delta H(t_{k},t)$ ,关机时刻如按式(13.13-13)实现了 $\Delta H(t_{k},t_{k})=0$ ,也就实现了所要求的终端条件。

由于 $b-\frac{\dot{H}}{\dot{L}}a$ 是常向量，以式(13.13-13)作为导引信号使制导计算变得十分简单，因而这类简化的预测制导公式曾得到广泛应用。值得注意的是，以上简化是有条件的，通常的运用条件为

$$
\frac {\partial H}{\partial v _ {i k}} \gg \frac {\partial H}{\partial i _ {k}}, (i = x, y, z) \tag {13.13-14}
$$

(2) $t_{k}-t$ 较小。 $t_{k}$ 为关机时间，t 为进行导引的时间。

由条件(1)可知，在落点横向偏差表达式(13.11-37)中, $\frac{\partial H}{\partial v_{ik}}\delta v_{i}(t_{k})(i=x,y,z)$ 是主要项，而 $\frac{\partial H}{\partial i_{k}}\delta i(t_{k})(i=x,y,z)$ 是次要项，再加上条件(2),即可忽略 t 时刻的速度偏差 $\delta v_{i}(t)$ 对关机时刻位置偏差的影响。通常在小偏差条件下,t 时刻的位置偏差对关机时刻的速度偏差 $\delta v_{i}(t_{k})$ 的影响也是可以忽略的。

当上述简化条件不成立时，应适当注意由 $\delta\boldsymbol{x}(t)$ 外推 $\delta\boldsymbol{x}(t_{k})$ 时速度偏差和位置偏差相互间的影响。实际上式(13.13-7)和(13.13-12)就是较好地考虑了这些影响的预测制导公式。根据对具体系统的全面考虑，还可以对式(13.13-7)和(13.13-12)作其他形式的简化，使其既保证制导精度又便于实现。

最后我们讨论一下如何应用最优控制的方法去达到预测制导的零控无偏状态。

弹道式导弹制导系统按式(13.13-7)，(13.13-12)或(13.13-13)计算出 $\Delta H(t_{k},t)$ 后，通过控制系统可以产生不同形式的控制加速度，改变火箭的质心运动以消除落点横向偏差。对这一消除偏差 $\Delta H(t_{k},t)$ 的控制过程，可以应用最优控制理论中的极大值原理，综合出最优控制。注意到我们研究最优制导系统时，目标集是主动段终端（即关机点）满足约束条件

$$
\Delta H (t _ {k}, t _ {k}) = (\lambda (t _ {k}, t _ {k}), \delta \boldsymbol {x} (t _ {k})) = 0 \tag {13.13-15}
$$

的状态集合，也可以是主动段飞行过程中满足约束条件

$$
\Delta H \left(t _ {k}, T\right) = \left(\lambda \left(t _ {k}, T\right), \delta \boldsymbol {x} \left(t _ {k}\right)\right) = 0, \quad T \in \left(t _ {0}, t _ {k} \right] \tag {13.13-16}
$$

的状态集合。显然，前者仅是后者的特例。我们称满足式(13.13-16)的状态为横向制导系统的“零控无偏状态”。由基本公式(13.13-5)可知

$$
\left. \left(\lambda \left(t _ {k}, t _ {k}\right), \delta \boldsymbol {x} \left(t _ {k}\right)\right) = \left(\lambda \left(t _ {k}, t\right), \delta \boldsymbol {x} (t)\right), \quad t \in \left(t _ {0}, t _ {k} \right] \right. \tag {13.13-17}
$$

如果在 t=T 时刻( $T\in(t_{0},t_{k}]$ )火箭的运动状态满足条件

$$
\Delta H (t _ {k}, T) = (\lambda (t _ {k}, T), \delta \boldsymbol {x} (T)) = 0 \tag {13.13-18}
$$

只要 T 时刻之后不出现新的干扰作用，则必有

$$
\Delta H (t _ {k}, \tau) \equiv 0, \quad \forall \tau \in [ T, t _ {k} ] \tag {13.13-19}
$$

因此，在 T 时刻之后，横向制导系统的反馈控制信号为零，火箭在不受干扰也不受横向控制加速度作用的情况下，将按标准条件飞行，并在预计关机时刻保证 $\Delta H(t_{k}, t_{k}) = 0$ 。所以我们主动段飞行过程中满足式(13.13-18)的飞行状态为零控无偏状态。从式(13.13-18)还可以看出，零控无偏状态是六维状态空间中的五维流形，因此也可称为零控无偏流形。按早期弹道式导弹横向制导系统中习用的术语“射面”来说，也可以称这个零控无偏流形为“广义活动射面”。只要导弹的运动状态参数达到这个射面，预测的落点横向偏差就为零，如果没有新的干扰，导 弹就沿广义活动射面飞行，不再需要标准状态之外的制导反馈控制。如果出现新的干扰，导弹又会偏离“射面”,横向制导系统将控制导弹，消除偏差以达到新时刻所建立的广义活动射面之内。可以看出，广义活动射面是随时间变化的五维流形。

对于具有标准弹道，并按摄动理论设计的弹道火箭制导系统来说，零控无偏状态代表了飞行控制过程中的标准状态。显然制导系统应尽量保持这种标准状态，尤其在关机点附近，应尽量减少弹道的扰动，使系统尽早达到标准状态并稳定地保持这种状态，对提高制导精度是有益的。对于某些弹道式火箭，若能尽早处于零控无偏状态，还将大大节省控制能量，这对某些情况来说是十分重要的。向零控无偏状态导引的最优控制指标，可以根据具体要求来确定。下面以最速控制指标为例，综合出闭环的最优控制律。

为了研究问题方便起见，将火箭主动段的摄动方程式(13.10-4)改写为

$$
\delta \dot {\boldsymbol {v}} (t) = G (t) \delta r (t) + \boldsymbol {u}
$$

$$
\delta \dot {\boldsymbol {r}} = \delta \boldsymbol {v}
$$

$$
\delta \boldsymbol {x} (t _ {0}) = \delta \boldsymbol {x} _ {0} = (\delta \boldsymbol {v} _ {0}, \delta \boldsymbol {r} _ {0}) ^ {\tau} \tag {13.13-20}
$$

式中

$$
\delta \boldsymbol {x} (t) = (\delta \boldsymbol {v} (t), \delta \boldsymbol {r} (t)) ^ {\tau} = (\delta v _ {x}, \delta v _ {y}, \delta v _ {z}, \delta x, \delta y, \delta z) ^ {\tau}
$$

表示火箭运动参数的偏差。控制加速度可写成

$$
\boldsymbol {u} (t) = f (t) \eta (t) \tag {13.13-21}
$$

$\eta(t)$ 为单位向量，表示控制加速度的方向。 $f(t)$ 表示控制加速度的大小。控制约束条件为

$$
0 \leqslant f (t) \leqslant \boldsymbol {F} (\text {常数}), \quad \| \eta (t) \| = 1 (\text {方向任意}) \tag {13.13-22}
$$

假定初始偏差为 $\delta x_{0}$ ，对应的预测落点横向偏差是

$$
\Delta H (t _ {k}, t _ {0}) = (\lambda (t _ {k}, t _ {0}), \delta \boldsymbol {x} (t _ {0})) \neq 0 \tag {13.13-23}
$$

控制性能指标为

$$
J = \int_ {t _ {0}} ^ {T} 1 d t \tag {13.13-24}
$$

目标集由下式确定

$$
\Delta H (t _ {k}, T) = (\lambda (t _ {k}, T), \delta \boldsymbol {x} (T)) = 0 \tag {13.13-25}
$$

要解决的问题是求满足方程(13.13-20)及约束条件式(13.13-22)和(13.13-25)，

使性能指标式(13.13-24)达到极小的最速控制 $\mathring{\boldsymbol{u}}(t)$ 。

我们已把横向制导系统的设计问题，化成了最速控制系统的设计问题。下面我们应用极大值原理来进行设计。

按最优控制理论，系统的哈密顿函数 H 为

$$
\mathcal {H} = \left(\boldsymbol {\psi} _ {1}, G (t) \delta \boldsymbol {r}\right) + \left(\boldsymbol {\psi} _ {1}, f \eta\right) + \left(\boldsymbol {\psi} _ {2}, \delta \boldsymbol {v}\right) - 1 \tag {13.13-26}
$$

伴随方程为

$$
\dot {\boldsymbol {\psi}} _ {1} = - \frac {\partial \mathcal {H}}{\partial \delta \boldsymbol {v}} = - \boldsymbol {\psi} _ {2}, \quad \dot {\boldsymbol {\psi}} _ {2} = - \frac {\partial \mathcal {H}}{\partial \delta \boldsymbol {r}} = - G ^ {\tau} (t) \boldsymbol {\psi} _ {1} \tag {13.13-27}
$$

横截条件为

$$
\boldsymbol {\psi} _ {1} (T) = \frac {\mu \partial (\lambda (t _ {k} , T) , \delta \boldsymbol {x} (T))}{\partial \delta \boldsymbol {v} (T)}, \quad \boldsymbol {\psi} _ {2} (T) = \frac {\mu \partial (\lambda (t _ {k} , T) , \delta \boldsymbol {x} (T))}{\partial \delta \boldsymbol {r} (T)} \tag {13.13-28}
$$

式中 $\mu$ 为待定常量, $\lambda(t_{k}, T)$ 是方程式(13.13-4)在终端条件式(13.13-6)下求出的伴随向量, 记

$$
\lambda (t _ {k}, t) = (\lambda^ {v} (t _ {k}, t), \lambda^ {r} (t _ {k}, t)) ^ {\tau}
$$

$$
\lambda^ {v} \left(t _ {k}, t\right) = \left(\lambda_ {1} \left(t _ {k}, t\right), \lambda_ {2} \left(t _ {k}, t\right), \lambda_ {3} \left(t _ {k}, t\right)\right) ^ {\tau}
$$

$$
\lambda^ {r} \left(t _ {k}, t\right) = \left(\lambda_ {4} \left(t _ {k}, t\right), \lambda_ {5} \left(t _ {k}, t\right), \lambda_ {6} \left(t _ {k}, t\right)\right) ^ {\tau} \tag {13.13-29}
$$

等式(13.13-25)可改写成

$$
(\lambda (t _ {k}, T), \delta \boldsymbol {x} (T)) = (\lambda^ {v} (t _ {k}, T), \delta \boldsymbol {v} (T)) + (\lambda^ {r} (t _ {k}, T), \delta \boldsymbol {r} (T)) = 0 \tag {13.13-30}
$$

由横截条件式(13.13-28)得到

$$
\boldsymbol {\psi} _ {1} (T) = \mu \lambda^ {v} (t _ {k}, T), \quad \boldsymbol {\psi} _ {2} (T) = \mu \lambda^ {r} (t _ {k}, T) \tag {13.13-31}
$$

注意到伴随方程式(13.13-27)和伴随方程式(13.13-4)是同一个方程的两种不同写法，于是可以得出

$$
\boldsymbol {\psi} _ {1} (t) = \mu \lambda^ {v} \left(t _ {k}, t\right), \quad \boldsymbol {\psi} _ {2} (t) = \mu \lambda^ {r} \left(t _ {k}, t\right) \tag {13.13-32}
$$

由极大值原理，为使控制指标 J 达到极小，应选取最优控制 $\hat{u}$ ,使哈密顿函数达到极大。因而最优控制 $\hat{u}$ 为

$$
\mathring {\boldsymbol {u}} (t) = F \frac {\boldsymbol {\psi} _ {1} (t)}{\| \boldsymbol {\psi} _ {1} (t) \|} = F \frac {\mu \lambda^ {v} \left(t _ {k} , t\right)}{| \mu | \cdot \| \lambda^ {v} \left(t _ {k} , t\right) \|} \tag {13.13-33}
$$

式(13.13-33)表明，最优控制加速度其数值应取最大值 F, 其方向或者与 $\lambda^{v}(t_{k}, t)$ 同向, 或者与 $\lambda^{v}(t_{k}, t)$ 反向。为了找出最优控制与初始状态变量 $\delta x_{0}$ 之间的关系, 我们将式(13.13-33)代入状态方程式(13.13-20)

$$
\delta \dot {\boldsymbol {v}} = G (t) \delta \boldsymbol {r} + \mathring {\boldsymbol {u}}, \quad \delta \dot {\boldsymbol {r}} = \delta \boldsymbol {v} \tag {13.13-34}
$$

设式 $(13.13-34)$ 的基本解阵为

$$
\Phi (t, s) = \left[ \begin{array}{l l} \Phi_ {1 1} (t, s) & \Phi_ {1 2} (t, s) \\ \Phi_ {2 1} (t, s) & \Phi_ {2 2} (t, s) \end{array} \right] \tag {13.13-35}
$$

方程(13.13-34)的解可表示为

$$
\left[ \begin{array}{l} \delta \boldsymbol {v} (t) \\ \delta \boldsymbol {r} (t) \end{array} \right] = \Phi (t, t _ {0}) \left[ \begin{array}{l} \delta \boldsymbol {v} (t _ {0}) \\ \delta \boldsymbol {r} (t _ {0}) \end{array} \right] + \int_ {t _ {0}} ^ {t} \Phi (t, s) \left[ \begin{array}{c} \mathring {\boldsymbol {u}} (s) \\ 0 \end{array} \right] d s \tag {13.13-36}
$$

将式(13.13-33)代入式(13.13-36)，并令 t=T，可得

$$
\left[ \begin{array}{l} \delta \boldsymbol {v} (T) \\ \delta \boldsymbol {r} (T) \end{array} \right] = \Phi (T, t _ {0}) \left[ \begin{array}{l} \delta \boldsymbol {v} (t _ {0}) \\ \delta \boldsymbol {r} (t _ {0}) \end{array} \right] + \frac {\mu}{| \mu |} \left[ \begin{array}{l} \int_ {t _ {0}} ^ {T} \Phi_ {1 1} (T, s) \frac {F \lambda^ {v} (t _ {k} , s)}{\| \lambda^ {v} (t _ {k} , s) \|} d s \\ \int_ {t _ {0}} ^ {T} \Phi_ {2 1} (T, s) \frac {F \lambda^ {v} (t _ {k} , s)}{\| \lambda^ {v} (t _ {k} , s) \|} d s \end{array} \right] \tag {13.13-37}
$$

再将式(13.13-37)代入式(13.13-30)得到

$$
\begin{array}{l} (\lambda (t _ {k}, T), \delta \boldsymbol {x} (T)) = (\lambda (t _ {k}, T), \Phi (T, t _ {0}) \delta \boldsymbol {x} (t _ {0})) \\ + \frac {\mu}{| \mu |} \Delta H ^ {u} (t _ {k}, T) = 0 \tag {13.13-38} \\ \end{array}
$$

式中

$$
\Delta H ^ {u} \left(t _ {k}, T\right) = \left[ \lambda \left(t _ {k}, T\right), \left( \begin{array}{l l} \int_ {t _ {0}} ^ {T} \Phi_ {1 1} (T, s) & \frac {F \lambda^ {v} \left(t _ {k} , s\right)}{\| \lambda^ {v} \left(t _ {k} , s\right) \|} d s \\ \int_ {t _ {0}} ^ {T} \Phi_ {2 1} (T, s) & \frac {F \lambda^ {v} \left(t _ {k} , s\right)}{\| \lambda^ {v} \left(t _ {k} , s\right) \|} d s \end{array} \right) \right] \tag {13.13-39}
$$

假设 x, y 分别表示两个 n 维向量, A 表示 n 阶方阵, $A^{*}$ 表示 A 的伴随矩阵, 于是有关系式

$$
(\boldsymbol {x}, A \boldsymbol {y}) = (A ^ {*} \boldsymbol {x}, \boldsymbol {y}) \tag {13.13-40}
$$

成立。利用式(13.13-40)，将式(13.13-38)右端第一项化为

$$
(\lambda (t _ {k}, T), \Phi (T, t _ {0}) \delta \boldsymbol {x} (t _ {0})) = (\Phi^ {*} (T, t _ {0}) \lambda (t _ {k}, T), \delta \boldsymbol {x} (t _ {0})) \tag {13.13-41}
$$

可以证明

$$
\Phi^ {*} (T, t _ {0}) = \Phi^ {\tau} (T, t _ {0}), \quad \lambda (t _ {k}, t _ {0}) = \Phi^ {\tau} (T, t _ {0}) \lambda (t _ {k}, T) \tag {13.13-42}
$$

利用式(13.13-41)和(13.13-42)，可将式(13.13-38)表示成

$$
\begin{array}{l} \Delta H (t _ {k}, T) = (\lambda (t _ {k}, T), \delta x (T)) \\ = (\lambda (t _ {k}, t _ {0}), \delta \boldsymbol {x} (t _ {0})) + \frac {\mu}{| \mu |} \Delta H ^ {u} (t _ {k}, T) \\ = \Delta H (t _ {k}, t _ {0}) + \frac {\mu}{| \mu |} \Delta H ^ {u} (t _ {k}, T) = 0 \tag {13.13-43} \\ \end{array}
$$

由 $\Delta H^{u}(t_{k},T)$ 的定义式(13.13-39)可知，由于在 $[t_0,T]$ 时间间隔内控制加速度 $\mathring{\pmb{u}} (t)$ 起作用，引起 $T$ 时刻运动参数变化，相应地 $T$ 时刻的预计落点横向偏差也要变化，其改变量为 $\Delta H^u (t_k,T)$ 。式(13.13-43)表明，初始状态 $\delta x_0$ 对应的预计落点横向偏差 $\Delta H(t_k,t_0)$ ，经 $[t_0,T]$ 区间内的控制加速度的作用完全消除了。由式(13.13-43)可知

$$
\mid \Delta H ^ {u} (t _ {k}, T) \mid = \mid \Delta H (t _ {k}, t _ {0}) \mid \tag {13.13-44}
$$

由式(13.13-44)可求出时间 T，由式(13.13-39)可求出 $\Delta H^{u}(t_{k}, T)$ ，由式(13.13-43)得到

$$
\frac {\mu}{| \mu |} = \frac {- \Delta H (t _ {k} , t _ {0})}{\Delta H ^ {u} (t _ {k} , T)} \tag {13.13-45}
$$

将式 $(13.13-45)$ 代入式 $(13.13-33)$ 可得最优控制

$$
\mathring {\boldsymbol {u}} (t) = - \frac {\Delta H (t _ {k} , t _ {0})}{\Delta H ^ {u} (t _ {k} , T)} \frac {\lambda^ {v} (t _ {k} , t)}{\| \lambda^ {v} (t _ {k} , t) \|} \boldsymbol {F} \tag {13.13-46}
$$

将控制过程中任意时刻 t 作为初始时刻, 可得到最优控制加速度的解

$$
\mathring {\boldsymbol {u}} (t) = - \frac {\Delta H (t _ {k} , t)}{\Delta H ^ {u} (t _ {k} , T)} \frac {\lambda^ {v} (t _ {k} , t)}{\| \lambda^ {v} (t _ {k} , t) \|} \boldsymbol {F} \tag {13.13-47}
$$

式(13.13-47)表明，向零控无偏状态导引的最速控制加速度，必须与向量 $\lambda^{v}(t_{k}, t)$ 平行，当 $\Delta H(t_{k}, t)/\Delta H^{u}(t_{k}, T)>0$ 时，取 $\lambda^{v}(t_{k}, t)$ 的负方向，当 $\Delta H(t_{k}, t)/\Delta H^{u}(t_{k}, T)<0$ 时，取 $\lambda^{v}(t_{k}, t)$ 的正方向。而且最速控制加速度的数值应取允许的最大值。控制加速度只在 $[t_{0}, T]$ 区间内起作用，T 时刻横向制导系统到达零控无偏流型，如无新的干扰作用，横向控制加速度则为零，火箭沿横向零控无偏流型飞到关机点，保证落点横向偏差 $\Delta H(t_{k})=0$ 。伴随向量 $\lambda(t_{k}, t)$ 可由系统的伴随方程在给定的终端条件下求解，而伴随方程和终端条件都是由火箭主动段的标准飞行条件确定的，因而最优控制加速度的平行方向 $\lambda^{v}(t_{k}, t)/\|\lambda^{v}(t_{k}, t)\|$ 是已知的，只随时间 t 而变化。当横向制导系统实时计算 $\Delta H(t_{k}, t), \Delta H^{u}(t_{k}, T)$ 时，按它们的符号即可完全确定最优控制加速度的方向。

### 13.14 第十三章的附录: 摄动系数的计算

F, G 和 H 是由方程组(13.1-14)所定义的。它们包含有参数 $\Sigma, \Lambda, \Delta$ 和 N。根据方程(13.1-2)和(13.1-13)所给的定义，这些参数可以写成下列形式

$$
\begin{array}{l} \Sigma = \frac {S _ {g}}{W} \\ \Lambda = \frac {g}{W} \frac {1}{2} \rho A C _ {L} \sqrt {v _ {r} ^ {2} + (v _ {\theta} + w) ^ {2}} \\ \Delta = \frac {g}{W} \frac {1}{2} \rho A C _ {D} \sqrt {v _ {r} ^ {2} + (v _ {\theta} + w) ^ {2}} \\ N = \frac {1}{l} \frac {1}{2} \rho A C _ {M} \left\{v _ {r} ^ {2} + (v _ {0} + w) ^ {2} \right\} \tag {13.A-1} \\ \end{array}
$$

其中的空气动力系数 $C_{L}, C_{D}$ 和 $C_{M}$ 都是冲角 $\alpha$ ，升降舵角 $\gamma$ ，马赫数 M 和雷诺数 Re 的函数：这些空气动力学参数与飞行路线的各个量显然有以下的关系

$$
\alpha = \beta - \tan^ {- 1} \left[ \frac {v _ {r}}{v _ {0} + w} \right], \quad M = \frac {V}{a (r)}, \quad \mathrm{Re} = \frac {\rho V l}{\mu (r)} \tag {13.A-2}
$$

其中 $a(r)$ 是空气的音速, $\mu(r)$ 是空气的黏性系数, 这两个量都是高度 r 的函数。在以下的计算中, 推力 s 只看作是高度的函数。我们也假定空气在各个高度上的 化学成分都与标准大气的情况相同; 只有密度 $\rho$ 和温度 T 与标准值不相同。所以, 在任意高度上 a 和 $\mu$ 的偏差都只是由于温度 T 的偏差而产生的。

对于 $\Sigma$ 来说

$$
\frac {\partial \Sigma}{\partial r} = \frac {g}{W} \frac {\partial S}{\partial r}, \quad \frac {\partial \Sigma}{\partial W} = - \frac {\Sigma}{W} \tag {13.A-3}
$$

所有其余的偏导数都是零。

对于 $\Lambda$ 来说

$$
\begin{array}{l} \frac {\partial \Lambda}{\partial r} = \Lambda \left\{\frac {1}{\rho} \frac {d \rho}{d r} \left[ 1 + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}} \right] + \frac {1}{V ^ {2}} \frac {d w}{d r} \left[ \left(\frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}} + 1\right) \right. \right. \\ \left. \times (v _ {0} + w) + \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \alpha} v _ {r} \right] - \frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} \frac {1}{a} \frac {d a}{d r} - \frac {\operatorname{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \operatorname{Re}} \frac {1}{\mu} \frac {d \mu}{d r} \Bigg \} \\ \end{array}
$$

$$
\frac {\partial \Lambda}{\partial v _ {r}} = \Lambda \frac {v _ {r}}{V ^ {2}} \left[ \frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}} + 1 - \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \alpha} \frac {v _ {0} + w}{v _ {r}} \right]
$$

$$
\frac {\partial \Lambda}{\partial v _ {0}} = \Lambda \frac {v _ {0} + w}{V ^ {2}} \left[ \frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}} + 1 + \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \alpha} \frac {v _ {r}}{v _ {0} + w} \right]
$$

$$
\frac {\partial \Lambda}{\partial \beta} = \Lambda \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \alpha}
$$

$$
\frac {\partial \Lambda}{\partial \gamma} = \Lambda \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \gamma}
$$

$$
\frac {\partial \Lambda}{\partial \rho} = \Lambda \frac {1}{\rho} \left(1 + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}}\right)
$$

$$
\frac {\partial \Lambda}{\partial T} = - \Lambda \left[ \frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} \frac {1}{2 T} + \frac {\operatorname{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \operatorname{Re}} \frac {1}{\mu} \frac {\partial \mu}{\partial T} \right]
$$

$$
\frac {\partial \Lambda}{\partial w} = \Lambda \frac {v _ {0} + w}{V ^ {2}} \left[ \frac {M}{C _ {L}} \frac {\partial C _ {L}}{\partial M} + \frac {\mathrm{Re}}{C _ {L}} \frac {\partial C _ {L}}{\partial \mathrm{Re}} + 1 + \frac {1}{C _ {L}} \frac {\partial C _ {L}}{\partial \alpha} \frac {v _ {r}}{v _ {0} + w} \right] = \frac {\partial \Lambda}{\partial v _ {0}}
$$

$$
\frac {\partial \Lambda}{\partial W} = - \frac {\Lambda}{W} \tag {13.A-4}
$$

只要在方程(13.A-4)中用 $\Delta$ 代替 $\Lambda$ ，以 $C_{D}$ 代替 $C_{L}$ 就可以得到 $\Delta$ 的各个偏导数。这里不再写出。对于 N 来说

$$
\begin{array}{l} \frac {\partial N}{\partial r} = N \left\{\frac {1}{\rho} \frac {d \rho}{d r} \left(1 + \frac {\mathrm{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \mathrm{Re}}\right) + \frac {1}{V ^ {2}} \frac {d w}{d r} \left[ \left(\frac {M}{C _ {M}} \frac {\partial C _ {M}}{\partial M} + \frac {\mathrm{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \mathrm{Re}} + 2\right) \right. \right. \\ \left. \times (v _ {0} + w) + \frac {1}{C _ {M}} \frac {\partial C _ {M}}{\partial \alpha} v _ {r} \right] - \frac {M}{C _ {M}} \frac {\partial C _ {M}}{\partial M} \frac {1}{a} \frac {d a}{d r} - \frac {\operatorname{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \operatorname{Re}} \frac {1}{\mu} \frac {d \mu}{d r} \Bigg \} \\ \end{array}
$$

$$
\frac {\partial N}{\partial v _ {r}} = N \frac {v _ {r}}{V ^ {2}} \left[ \frac {M}{C _ {M}} \frac {\partial C _ {M}}{\partial M} + \frac {\mathrm{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \mathrm{Re}} + 2 - \frac {1}{C _ {M}} \frac {\partial C _ {M}}{\partial \alpha} \frac {v _ {0} + w}{v _ {r}} \right]
$$

$$
\frac {\partial N}{\partial v _ {0}} = N \frac {v _ {0} + w}{V ^ {2}} \left[ \frac {M}{C _ {M}} \frac {\partial C _ {M}}{\partial_ {M}} + \frac {\mathrm{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \mathrm{Re}} + 2 + \frac {1}{C _ {M}} \frac {\partial C _ {M}}{\partial \alpha} \frac {v _ {r}}{v _ {0} + w} \right]
$$

$$
\begin{array}{l} \frac {\partial N}{\partial \beta} = N \frac {1}{C _ {M}} \frac {\partial C _ {M}}{\partial \alpha} \\ \frac {\partial N}{\partial \gamma} = N \frac {1}{C _ {M}} \frac {\partial C _ {M}}{\partial \gamma} \\ \frac {\partial N}{\partial \rho} = N \frac {1}{\rho} \left(1 + \frac {\mathrm{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \mathrm{Re}}\right) \\ \frac {\partial N}{\partial T} = - N \left[ \frac {M}{C _ {M}} \frac {\partial C _ {M}}{\partial M} \frac {1}{2 T} + \frac {\operatorname{Re}}{C _ {M}} \frac {\partial C _ {M}}{\partial \operatorname{Re}} \frac {1}{\mu} \frac {\partial \mu}{\partial T} \right] \\ \frac {\partial N}{\partial W} = \frac {\partial N}{\partial v _ {0}} \\ \frac {\partial N}{\partial I} = - \frac {N}{I} \tag {13.A-5} \\ \end{array}
$$

根据以上这些偏导数，系数 a, b, c 就不难算出

$$
\begin{array}{l} a _ {1} = \frac {\partial F}{\partial r} = \frac {\partial \Sigma}{\partial r} \sin \beta + \frac {d w}{d r} \Lambda + (v _ {0} + w) \frac {\partial \Lambda}{\partial r} - v _ {r} \frac {\partial \Delta}{\partial r} + \left[ \frac {v _ {0}}{r} \pm \Omega \right] ^ {2} \\ - 2 \frac {v _ {0}}{r} \left[ \frac {v _ {0}}{r} \pm \Omega \right] + 2 \frac {g}{r} \left[ \frac {r _ {0}}{r} \right] ^ {2} \\ \end{array}
$$

$$
a = \frac {\partial F}{\partial \beta} = \Sigma \cos \beta + (v _ {0} + w) \frac {\partial \Lambda}{\partial \beta} - v _ {r} \frac {\partial \Delta}{\partial \beta}
$$

$$
a _ {3} = \frac {\partial F}{\partial v _ {r}} = (v _ {0} + w) \frac {\partial \Lambda}{\partial v _ {r}} - \Delta - v _ {r} \frac {\partial \Delta}{\partial v _ {r}}
$$

$$
a _ {4} = \frac {\partial F}{\partial v _ {0}} = \Lambda + (v _ {0} + w) \frac {\partial \Lambda}{\partial v _ {0}} - v _ {r} \frac {\partial \Delta}{\partial v _ {0}} + 2 \left[ \frac {v _ {0}}{r} \pm \Omega \right]
$$

$$
a _ {5} = \frac {\partial F}{\partial \gamma} = (v _ {0} + w) \frac {\partial \Lambda}{\partial \gamma} - v _ {r} \frac {\partial \Delta}{\partial \gamma}
$$

$$
a _ {6} = \frac {\partial F}{\partial \rho} = (v _ {0} + w) \frac {\partial \Lambda}{\partial \rho} - v _ {r} \frac {\partial \Delta}{\partial \rho}
$$

$$
a _ {7} = \frac {\partial F}{\partial T} = (v _ {0} + w) \frac {\partial \Lambda}{\partial T} - v _ {r} \frac {\partial \Delta}{\partial T}
$$

$$
a _ {8} = \frac {\partial F}{\partial w} = \Lambda + (v _ {0} + w) \frac {\partial \Lambda}{\partial w} - v _ {r} \frac {\partial \Delta}{\partial w}
$$

$$
a _ {9} = \frac {\partial F}{\partial W} = \frac {\partial \Sigma}{\partial W} \sin \beta + (v _ {0} + w) \frac {\partial \Lambda}{\partial W} - v _ {r} \frac {\partial \Delta}{\partial W}
$$

$$
b _ {1} = \frac {\partial G}{\partial r} = \frac {\partial \Sigma}{\partial r} \cos \beta - v _ {r} \frac {\partial \Lambda}{\partial r} - \frac {d w}{d r} \Delta - (v _ {0} + w) \frac {\partial \Delta}{\partial r} + \frac {v _ {r} v _ {0}}{r ^ {2}}
$$

$$
b _ {2} = \frac {\partial G}{\partial \beta} = - \Sigma \sin \beta - v _ {r} \frac {\partial \Lambda}{\partial \beta} - (v _ {0} + w) \frac {\partial \Delta}{\partial \beta}
$$

$$
b _ {3} = \frac {\partial G}{\partial v _ {r}} = - \Lambda - v _ {r} \frac {\partial \Lambda}{\partial v _ {r}} - (v _ {0} + w) \frac {\partial \Delta}{\partial v _ {r}} - 2 \left[ \frac {1}{2} \frac {v _ {0}}{r} \pm \Omega \right]
$$

$$
b _ {4} = \frac {\partial G}{\partial v _ {0}} = - v _ {r} \frac {\partial \Lambda}{\partial v _ {0}} - \Delta - (v _ {0} + w) \frac {\partial \Delta}{\partial v _ {0}} - \frac {v _ {r}}{r}
$$

$$
b _ {5} = \frac {\partial G}{\partial \gamma} = - v _ {r} \frac {\partial \Lambda}{\partial \gamma} - (v _ {0} + w) \frac {\partial \Delta}{\partial \gamma}
$$

$$
b _ {6} = \frac {\partial G}{\partial \rho} = - v _ {r} \frac {\partial \Lambda}{\partial \rho} - (v _ {0} + w) \frac {\partial \Delta}{\partial \rho}
$$

$$
b _ {7} = \frac {\partial G}{\partial T} = - v _ {r} \frac {\partial \Lambda}{\partial T} - (v _ {0} + w) \frac {\partial \Delta}{\partial T}
$$

$$
b _ {8} = \frac {\partial G}{\partial w} = - v _ {r} \frac {\partial \Lambda}{\partial w} - \Delta - (v _ {0} + w) \frac {\partial \Delta}{\partial w}
$$

$$
b _ {9} = \frac {\partial G}{\partial W} = \frac {\partial \Sigma}{\partial W} \cos \beta - v _ {r} \frac {\partial \Lambda}{\partial W} - (v _ {0} + w) \frac {\partial \Delta}{\partial W}
$$

$$
\begin{array}{l} c _ {1} = \frac {\partial H}{\partial r} = - \frac {1}{r ^ {2}} \left[ \Sigma \cos \beta - v _ {r} \Lambda - (v _ {\theta} + w) \Delta - 2 v _ {r} \left(\frac {v _ {\theta}}{r} \pm \Omega\right) \right] \\ + \frac {1}{r} \left[ \frac {\partial \Sigma}{\partial r} \cos \beta - v _ {r} \frac {\partial \Lambda}{\partial r} - (v _ {0} + w) \frac {\partial \Delta}{\partial r} + \frac {d w}{d r} \Delta + 2 \frac {v _ {r} v _ {0}}{r ^ {2}} \right] + \frac {\partial N}{\partial r} \\ \end{array}
$$

$$
c _ {2} = \frac {\partial H}{\partial \beta} = \frac {1}{r} \left[ - \Sigma \sin \beta - v _ {r} \frac {\partial \Lambda}{\partial \beta} - (v _ {0} + w) \frac {\partial \Delta}{\partial \beta} \right] + \frac {\partial N}{\partial \beta}
$$

$$
c _ {3} = \frac {\partial H}{\partial v _ {r}} = \frac {1}{r} \left[ - \Lambda - v _ {r} \frac {\partial \Lambda}{\partial v _ {r}} - (v _ {0} + w) \frac {\partial \Delta}{\partial v _ {r}} - 2 \left(\frac {v _ {0}}{r} \pm \Omega\right) \right] + \frac {\partial N}{\partial v _ {r}}
$$

$$
c _ {4} = \frac {\partial H}{\partial v _ {0}} = \frac {1}{r} \left[ - v _ {r} \frac {\partial \Lambda}{\partial v _ {0}} - \Delta - (v _ {0} + w) \frac {\partial \Delta}{\partial v _ {0}} - 2 \frac {v _ {r}}{r} \right] + \frac {\partial N}{\partial v _ {0}}
$$

$$
c _ {5} = \frac {\partial H}{\partial \gamma} = \frac {1}{r} \left[ - v _ {r} \frac {\partial \Lambda}{\partial \gamma} - (v _ {0} + w) \frac {\partial \Delta}{\partial \gamma} \right] + \frac {\partial N}{\partial \gamma}
$$

$$
c _ {6} = \frac {\partial H}{\partial \rho} = \frac {1}{r} \left[ - v _ {r} \frac {\partial \Lambda}{\partial \rho} - (v _ {0} + w) \frac {\partial \Delta}{\partial \rho} \right] + \frac {\partial N}{\partial \rho}
$$

$$
c _ {7} = \frac {\partial H}{\partial T} = \frac {1}{r} \left[ - v _ {r} \frac {\partial \Lambda}{\partial T} - (v _ {0} + w) \frac {\partial \Delta}{\partial T} \right] + \frac {\partial N}{\partial T}
$$

$$
c _ {8} = \frac {\partial H}{\partial w} = \frac {1}{r} \left[ - v _ {r} \frac {\partial \Lambda}{\partial w} - \Delta - (v _ {0} + w) \frac {\partial \Delta}{\partial w} \right] + \frac {\partial N}{\partial w}
$$

$$
c _ {9} = \frac {\partial H}{\partial W} = \frac {1}{r} \left[ \frac {\partial \Sigma}{\partial W} \cos \beta - v _ {r} \frac {\partial \Lambda}{\partial W} - (v _ {0} + w) \frac {\partial \Delta}{\partial W} \right] + \frac {\partial N}{\partial W}
$$

$$
c _ {1 0} = \frac {\partial H}{\partial I} = \frac {\partial N}{\partial I} \tag {13.A-6}
$$

发动机关机以后，推力 S 就消失了。因此，在 $t > \bar{t}_{1}$ 时， $\Sigma$ 和 $\Sigma$ 的各个偏导数都等于零。

#### 13.15 参考文献

[1] 钱学森, 星际航行概论, 科学出版社, 1963.

[2] 林金, 变参数线性自动控制系统的外干扰完全补偿理论, 自动化学报, 1980, 1.

[3] 郭孝宽、岳丕玉，运载火箭的摄动预测制导，自动化学报，1979,3.

[4] 曹昌佑, 地球诸因素影响下命中和制导的计算与修正, 哈尔滨工程学院, 1962.

[5] Battin, R. H., Astronautical Guidance, McGraw-Hill Book Co., New York, 1964.

[6] Bliss, G. A., Mathematics for Exterior Ballistics, John Wiley & Sons, Inc., New York, 1944.

[7] Drenik, R., J. Franklin Inst. 251(1951), 423–436.

[8] Faurre, P., Navigation Inertielle Optimale et Filtrage Statistique, Dunod, Paris, 1971.

[9] Guided Missiles, Operation, Design and Theory, McGraw-Hill Book Co., Inc., New York, 1958.

[10] Korn, G. A. & Korn, T. M., Electronic Analog Computers, McGraw-Hill Book Go., Inc., New York, 1952.

[11] Locke, A. S., Guidance, D. Van Norstand Co., 1955. (制导, 屈其华译, 国防工业出版社, 1959.)

[12] Pitman, G.R., Inertial Guidance. Wiley, New York, 1962.

[13] Terger, T. T., System Preliminary Design, New York, 1960. (系统工程设计初步, 丁永湉、连桂森等译, 国防工业出版社, 1965.)

[14] Tsien, H. S. (钱学森), Adamson T. C. & Knuth, E. L., J. Amer. Rocket Soc., 22(1952), 192-199.

[15] Доброденский, Ю. П., Иванова, В. И., Поспелов Г. С., Автоматика Управляемых Снарядов, Оборонгиз, 1963.

[16] Ишлинский, А. Ю., Инерцальное Управление Баллистическими Ракетами, Наука, Москва, 1968.

[17] Кулебакин, В. С., Теория инвариантностн автоматических регулируемых и управляемых систем, Труды I Международного Конгресса IFAK, Москва, 1961.

[18] Остославский, И. В., Стражева, И. В., Динамика Полета, Устойчивость и Управляемость Летательная Аппаратов, Мащиностроение, Москва, 1965.

[19] Петров, Б. Н., Принцип инвариантности и условия его применения при расчете линейных и нелинейных систем, Труды I Международного Конгресса IFAK, Москва, 1961.

[20] Феодосьев, В. Н., Синярев, Г. Б., Введение в Ракетную Технику, Оборонгиз, Москва, 1960.
(火箭技术导论, 王根伟等译, 国防工业出版社, 1958.)

[21] Фридлендр, Г.О., Инерциальные Системы Навигации, Физматгиз, Москва, 1961.
