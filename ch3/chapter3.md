#第1章 信号与系统的基本概念 2
#第2章 线性时不变系统的时域分析 2
# 第3章连续时间信号与系统的傅立叶分析
## 目      录

- ### §3.0 引言 2
  - ### §3.0.1 上一章内容概述 2
  - ### §3.0.2 本章目标 2
- ### §3.1 连续时间LTI系统对复指数信号的响应 2
- ### §3.2 周期信号的表示：连续时间傅立叶级数 3
  - ### §3.2.1 成谐波关系的复指数线性组合 3
  - ### §3.2.2 周期信号傅立叶级数表示中系数的确定 4
- ### §3.3 周期信号的傅立叶级数近似与傅立叶级数的收敛 6
- ### §3.4 非周期信号的表示：连续时间傅立叶变换 6
  - ### §3.4.1 非周期信号傅立叶变换表示式的导出 6
  - ### §3.4.2 傅立叶变换的收敛 7
  - ### §3.4.3 连续时间傅立叶变换举例 7
- ### §3.5 周期信号与连续时间傅立叶变化 8
  - ### §3.5.1 非周期信号傅立叶变换在周期信号中的应用 8
  - ### §3.5.2 周期信号的傅立叶变换 9
- ### §3.6 连续时间傅立叶变换的性质 10
  - ### §3.6.1 傅立叶变换对的表示 10
  - ### §3.6.2 线性 10
  - ### §3.6.3 对称性 10
  - ### §3.6.4 时移性质 11
  - ### §3.6.5 微分和积分性质 11
  - ### §3.6.6 时间和频率的尺度变换性质 12
  - ### §3.6.7 对偶性 12
  - ### §3.6.8 帕斯瓦尔(Parseval)定理 13
- ### §3.7 卷积性质 14
  - ### §3.7.1 卷积性质的数学证明 14
  - ### §3.7.2 卷积性质的另一种理解 14
  - ### §3.7.3 一个例子 14
- ### §3.8 调制性质 15
- ### §3.9 傅立叶变换与傅立叶级数的性质及基本傅立叶变换对列表 16
- ### §3.10 用线性常系数微分方程表征的系统的频率响应 16
  - ### §3.10.1 频率响应概念 16
  - ### §3.10.2 已知数学方程得求解 16
  - ### §3.10.3 电路系统得频域求解 17

## 3.0　引言
- §3.0.1　上一章内容概述
1)	我们已知可将离散信号用一组移位单位脉冲的加权和来表示 $$ x[n]=\sum_{k=-\infty}^{+\infty} x[k]\delta[n-k] $$
2)	对应输出，也可以用单位脉冲响应跟输入信号的卷积和来表示  $$ y[n]=\sum_{k=-\infty}^{+\infty} x[k]h[n-k] $$
3)	同样的，整个连续信号则可以用一组移位单位冲激函数的加权积分来表示；输出信号则用输入信号与单位冲激响应的卷积积分来表示；
4)	一个LTI系统的特性完全由它的单位冲激响应来决定
-  §3.0.2　本章目标
1)	上一章用单位冲激/脉冲函数作为基本信号来表示其他信号
2)	本章用复指数信号作为基本信号，先将信号用这些基本信号的线性组合来表示，这就是傅立叶级数和傅立叶变换
3)	再来求系统的响应及其他特性；
## 3.1　连续时间LTI系统对复指数信号的响应
1)	LTI系统对于对复指数信号的响应也是同样一个复指数信号，只是在幅度上有点变化，即 ${\it e}^{st} \to {\mit H}(s){\it e}^{st}$，H(s)一般是s的函数
2)	一个信号，若系统对该信号的输出响应仅是一个常数乘以该输入，则该信号称为系统的*特征函数*，而幅度因子H(s)称为*特征值*。
3)	 $x(t)={\it e}^{st}$就是一个特征函数，证明如下：$y(t)=h(t)*x(t)=\int_{-\infty}^{+\infty} h(\tau)x(t-\tau)\ {\rm d}\tau=\int_{-\infty}^{+\infty} h(\tau){\it e}^{s(t-\tau)}\ {\rm d}\tau={\it e}^{st}\int_{-\infty}^{+\infty} h(\tau){\it e}^{-st}\ {\rm d}\tau=H(s){\it e}^{st}$
 
4)	任何复指数函数$ {\it e}^{st} $就是LTI系统的特征函数，$H(s)=\int_{-\infty}^{+\infty} h(\tau){\it e}^{-st}\ {\rm d}\tau$ 就是跟$ {\it e}^{st} $有关的特征值
5)	对于信号 $x(t)=a_1{\it e}^{s_1t}+a_2{\it e}^{s_2t}+a_3{\it e}^{s_3t}$ ，系统对于每个分量的响应分别是：

 $a_1{\it e}^{s_1t} \to a_1{\mit H}(s_1){\it e}^{s_1t}$

 $a_2{\it e}^{s_2t} \to a_2{\mit H}(s_2){\it e}^{s_2t}$

 $a_3{\it e}^{s_3t} \to a_3{\mit H}(s_3){\it e}^{s_3t}$

6)	那么根据LTI系统的叠加性，有 $y(t)=a_1{\mit H}(s_1){\it e}^{s_1t}+a_2{\mit H}(s_2){\it e}^{s_2t}+a_3{\mit H}(s_3){\it e}^{s_3t}$ 
7)	更一般的情况是$$\sum_{k} a_k{\it e}^{s_kt} \to \sum_{k} a_k{\mit H}(s_k){\it e}^{s_kt}$$ ，由此可见，对于一个LTI系统而言，如果我们得知各个特征值H(sk)，那么系统对于一个由复指数函数线性组合构成的输入的响应就可以直接求得。
8)	接下来的问题是：
- a)	什么样的信号可以用复指数的线性组合来表示；
- b)	如何表示？
9)	当s＝jw时，为傅立叶级数或傅立叶变换，当s=σ+jw时，则是拉普拉斯变换，本章首先研究傅立叶级数。
## 3.2　周期信号的表示：连续时间傅立叶级数
- §3.2.1　成谐波关系的复指数线性组合
1)	周期复指数信号：$x(t)={\it e}^{st}={\it e}^{jw_0t}$ ，对应复指数信号集$\phi_k(t)={\it e}^{jkw_0t}$ k=0,$\pm$1,$\pm$ 2......  ，这些信号中每一个都有一个基波角频率，它是$w_0$的倍数。
2)	一个周期信号可以表示成 ，也是周期函数，这是一个级数表示形式。（级数：数列各项依次用加号加起来求和，就形成无穷级数，其中的每一项叫通项）叫傅立叶级数。
- A)	k＝0，就是直流或者常数项$a_0$；
- B)	k=1或-1，就是基波分量或一次谐波分量； $a_1{\it e}^{jw_1t}+a_{-1}{\it e}^{-jw_0t}$
- C)	k=2或-2，就是二次谐波分量；
- D)	依次类推；
3)	例：一个周期信号x(t)，其基波周期为2π，写成(1)式为$x(t)=\sum_{k=-\infty}^{+\infty} a_k{\it e}^{jk2πt}$，其中有$\lbrace a_0=1, a_1=a_{-1}=\frac{1}{4}, a_2=a_{-2}+\frac{1}{3}, a_3=a_{-3}+\frac{1}{2}$ ，写出x(t)的表达式。
- A)	解， $x(t)={\it e}^{j0}+\frac{1}{4}{\it e}^{j2πt}+\frac{1}{4}{\it e}^{j(-2π)t}+\frac{1}{2}{\it e}^{j4πt}+\frac{1}{2}{\it e}^{j(-4π)t}+\frac{1}{2}{\it e}^{j6πt}+\frac{1}{4}{\it e}^{j(-6π)t}$
B)$=1+\frac{1}{2}\cos2πt+\cos4πt+\frac{2}{3}\cos6πt$
- §3.2.2　周期信号傅立叶级数表示中系数的确定
 1)	$ x(t)=\sum_{k=-\infty}^{+\infty} a_k{\it e}^{jkw_0t} $ 是周期信号的傅立叶级数表示，那么这些系数$a_k$是如何确定的？
 2)	上式两边乘以${\it e}^{-jkw_0t}$ ，得 $ x(t){\it e}^{-jkw_0t}=\sum_{k=-\infty}^{+\infty} a_k{\it e}^{jkw_0t}{\it e}^{-jkw_0t} $
 3)	再两边从0到$T_0$＝2π/$ω_0$积分，有$\int_0^{T_0} {x(t){\it e}^{-jn\omega_0 t}} \ {\rm d}t$ =$\int_0^{T_0} \sum_{k=-\infty}^{+\infty} {a_k{\it e}^{jkw_0t}{\it e}^{jk-w_0t}} \ {\rm d}t$ ，其中$T_0$是基波周期。
 4)	将上式右边交换求和与积分顺序后有$\int_0^{T_0} {x(t)}{\it e}^{-jnw_0t} \ {\rm d}t =\sum_{k=-\infty}^{+\infty}a_k[\int_0^{T_0}{\it e}^{j(k-n)w_0t}\ {\rm d}t] $ 
 5)	我们先求出右边积分。
- A)	若k=n，则积分结果为$T_0$；
- B)	若k<>n，则 $\int_0^{T_0} {\it e}^{j(k-n)\omega_0t} \ {\rm d}t=\frac{1}{j(k-n)w_0}{\it e}^{j(k-n)\omega_0t}|_0^{T_0}$
 
6)	(2)式变成：$\int_0^{T_0} {x(t)}{\it e}^{-jnw_0t} \ {\rm d}t=a_nT_0$ ，右边只留下k=n的结果，其余均为0
7)	所以级数的系数为：$a_n=\frac{1}{T_0}\int_0^{T_0} {x(t)}{\it e}^{-jnw_0t} \ {\rm d}t$ 
8)	另外，这个积分区间只要是连续的一个周期内即可，不一定要从0-$T_0$，所以周期信号的傅立叶级数公式有
- A)	      分析公式$a_n=\frac{1}{T_0}\int_{T_0} {x(t)}{\it e}^{jk-w_0t} \ {\rm d}t$
- B)	      综合公式$x(t)=\sum_{k=-\infty}^{+\infty} a_k{\it e}^{jkw_0t}$
9)	举例：
- A)	例1：求信号x(t)=sin($w_0t$)傅立叶级数的系数
- a)	解：x(t)=sin($w_0$t)＝$\frac{1}{2j}{\it e}^{j\omega_0t}-\frac{1}{2j}{\it e}^{-j(2\omega_0t)}$ ，所以对应的傅立叶级数为$$\begin{cases}a_1=\frac{1}{2j} ,& \\ a_{-1}=\frac{-1}{2j}, &\\ a_k=0,k \neq \pm1 \end{cases}$$
 
- B)	例2：求信号$x(t)=1+\sin\omega_0t+2\cos\omega_0t+cos(2\omega_0t+\frac{\pi}{4})$ 傅立叶级数的系数。
- a)	解： $$x(t)=1+\frac{1}{2j}({\it e}^{j\omega_0t}-{\it e}^{-j\omega_0t})+({\it e}^{j\omega_0t}+{\it e}^{-j\omega_0t})+\frac{1}{2}[{\it e}^{j(2\omega_t+\pi/4}+{\it e}^{-j(2\omega_t+\pi/4)}]$$
$$ x(t)=1+(1+\frac{1}{2j}){\it e}^{j\omega_0t}+(1-\frac{1}{2j}){\it e}^{-j\omega_0t}+(\frac{1}{2}{\it e}^{j\pi/4}{\it e}^{j2\omega_0t})+(\frac{1}{2}{\it e}^{-j\pi/4}{\it e}^{-j2\omega_0t})$$
有：$a_0=1,a_1=1-\frac{1}{2j},a_{-1}=1+\frac{1}{2j}，a_2=\sqrt{2}/4(1+j),a_{-2}=\sqrt{2}/4(1-j)$
其余 $a_k$=0,|k|>2
- C)	例3：对于一个周期性的方波，$x(t)=\begin{cases}1,|t|<T_1 & \\ 0,T_1<|t|<T_0/2 \end {cases}$，周期为$T_0$，如图所示（奥本海默P135图4.7），求其对应的傅立叶级数的系数
- a)	解：当k＝0时，有$a_0=\frac{1}{T_0}\int_{-T_0/2}^{T_0/2} {x(t)} \ {\rm d}t=\frac{1}{T_0}\int_{-T_0}^{T_0},t=\frac{T_1}{T_0}$ ，
- b)	k<>0时，有$a_k=\frac{1}{T_0} \int_{-T_0/2}^{T_0/2} {x(t)}{\it e}^{-jkw_0t} \ {\rm d}t=\frac{1}{T_0}\int_{-T_0}^{T_0} {\it e}^{-jkw_0t} \ {\rm d}t=\frac{T_1}{T_0}$ ，
 
也即有$a_k=\frac{2\sin(k\omega_0T_1)}{k\omega_0T_0}$ ，参见课本P13图1－27Sa(t)波形，只是差个系数
- c)	$a_k=\frac{2\sin(k\omega_0T_1)}{k\pi}=\frac{\omega_0T_1}{\pi}Sa(k\omega_0T_1)=\frac{\omega_0T_1}{\pi}Sa(kT_1)|{\omega=k\omega_0}$ ，此处注意两点：$a_0$也可以包含在内；ak就是Sa在几个离散点的取值，具体密度由$w_0$决定。
- D)	周期性锯齿脉冲信号、周期性三角脉冲信号和周期半余弦波信号的例子见课本P83，此处略。
§3.3　周期信号的傅立叶级数近似与傅立叶级数的收敛
1)	上节说明了周期信号可以用傅立叶级数表示，其系数的计算公式也推导出来，那么是不是所有的周期信号都可以用傅立叶级数表示呢？怎么样的信号才能用傅立叶级数表示呢？
2)	狄里赫利条件：
- A)	在任何周期内x(t)必须绝对可积，也即 $\int_{T_0} |x(t)| \ {\rm d}t<{\infty}$
- B)	在x（t）的任何周期内，其最大值赫最小值的数目有限，也即在任意有限区域内，x（t）的起伏是有限的
- C)	x(t)在任何有限区域内，只有有限个不连续点，而且在这些不连续点上，函数必须是有限值。
## 3.4　非周期信号的表示：连续时间傅立叶变换
- §3.4.1　非周期信号傅立叶变换表示式的导出
1)	我们考查一个非周期信号x(t)，如图所示（奥本海默第一版，P143图4.12(a),(b)），如何求其傅立叶变换
2)	将信号x(t)进行周期延拓，得到信号 ，周期为T0，在-T0/2到T0/2区间内，有 ，T0>2T1，如图(b)
3)	根据上节说明，可以将$\check{x}(t)$ 表示为傅立叶级数 $$ f(n)= \begin{cases} \check{x}(t)= \sum_{k=-\infty}^{+\infty} a_k{\it e}^{jkw_0t}, &  \\ a_k=\frac{1}{T_0} \int_{-T_0/2}^{T_0/2} \check{x}(t){\it e}^{-jkw_0t},t, &  \end{cases} $$
4)	因为在$-T_0$/2到$T_0$/2区间内，有$\check{x}(t)$代入上式，即有$a_k=\frac{1}{T_0} \int_{-T_0/2}^{T_0/2} x(t){\it e}^{-jkw_0t},t=a_k=\frac{1}{T_0} \int_{-\infty}^{+\infty} x(t){\it e}^{-jkw_0t},t$
 
5)	由此得到$T_0a_k$的包络为：$T_0a_k=X(j\omega)$=$\int_{-\infty}^{+\infty} x(t){\it e}^{-jkw_0t}\ {\rm d}t$ ，具体取值主要是在 这些离散点上，离散点取值的密度，取决于$T_0或者w_0$，用图表示。这个包络就叫做x(t)的傅立叶变换。
6)	根据上面得到的傅立叶级数系数公式，可得 $\check{x}(t)=\sum_{k=-\infty}^{+\infty}\frac{1}{T_0}X(jk\omega_0) {\it e}^{jk\omega_0t}\omega_0=2\pi/T_0=\frac{1}{2\pi}\sum_{k=-\infty}^{+\infty}\frac{1}{T_0}X(jk\omega_0) {\it e}^{jk\omega_0t}\omega_0$
 
7)	随着$T_0\rightarrow$无穷大，$\check{x}(t)\rightarrow{x(t)}，w_0\rightarrow0$，右边就变成一个积分，就有
 
8)	就有傅立叶变换对，下式称为傅立叶变换或傅立叶积分，上式称为傅立叶反变换$$ f(n)= \begin{cases} x(t)=\frac{1}{2\pi}  \int_{-\infty}^{+\infty} X(j\omega){\it e}^{-j\omega t},\omega \\ X(j\omega)= \int_{-\infty}^{+\infty} x(t){\it e}^{-jkwt} \ {\rm d}t \end{cases} $$
 ，X(jw)就叫x(t)的频谱，也即是x(t)相应的各个频率分量。
- §3.4.2　傅立叶变换的收敛
1)	在推导上面公式时，x(t)也是有一定限制的，而非任意，否则，就不能求出其傅立叶变换中的那个积分
2)	满足什么条件呢？也就是跟傅立叶级数系数求解中相似的，需要满足狄里赫利条件，即（课本P89）
- A)	x(t)绝对可积，即$ \int_{-\infty}^{+\infty} |x(t)|,t<{\infty} $；
- B)	在任何有限区域内，x（t）只有有限个最大值和最小值；
- C)	在任何有限区域内，x（t）有有限个不连续点，并且每一个不连续点都必须是有限值；
- §3.4.3　连续时间傅立叶变换举例
1)	例1：求信号$x(t)={\it e}^{-at}\mu(t)$ 的傅立叶变换，其中a>0。（若a<0，该信号就不是绝对可积，就没有对应的傅立叶变换）
- A)	解： $X(j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jkwt} \ {\rm d}t =\int_0^{+\infty} {\it e}^{-at}{\it e}^{-jkwt }\ {\rm d}t=\frac{-1}{a+j\omega} {\it e}^{-(a+j\omega)t}|_0^{+\infty}$
- B)	=$\frac{1}{1+j\omega}$ ，a>0
2)	例2：求信号$x(t)={\it e}^{-a|t|}$ 的傅立叶变换
- A)	解：$X(j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jkwt} \ {\rm d}t =\int_0^{+\infty} {\it e}^{-at}{\it e}^{-jkwt},t+\int_0{-\infty}^0 {\it e}^{-at}{\it e}^{-jkwt} \ {\rm d}t$  
- B)	 =$\frac{1}{a+j\omega}+\frac{1}{a-j\omega}=\frac{2a}{a^2+\omega^2}$
3)	例3：求单位冲激函数的频谱：
- A)	解： $X(j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jkwt} \ {\rm d}t=\int_{-\infty}^{+\infty} \delta(t){\it e}^{-jkwt}\ {\rm d}t=1$
- B)	单位冲激信号的频谱是涵盖全频段的。
4)	例4：求矩形脉冲信号的频谱$$ x(t)= \begin{cases} 1, |t|<T_1 \\  0,|t|>T_1 \end{cases} $$ 
- A)	解：  $X(j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jwt}\ {\rm d}t=\int_{-T_1}^{T_1} {\it e}^{-jwt}\ {\rm d}t=2\frac{\sin wT_1}{\omega}$
- B)	如图所示（奥本海默P146图4.17）
5)	例5：已知信号频谱X（jw），求原始信号X（jw）=$ \begin{cases} 1, |\omega|<T_1 \\  0,|\omega|>T_1 \end{cases}$， 
- A)	解，利用傅立叶反变换公式，得 x(t)=$\int_{-w}^{w} {\it e}^{-jwt},\omega=\frac{\sin Wt}{\pi t}$
- B)	通过例4例5，我们发现时域和频域变换之间存在着很有意思的对偶关系。x(t)$\longleftrightarrow$X(jw)的波形可以互相变换
## 3.5　周期信号与连续时间傅立叶变化
- §3.5.1　非周期信号傅立叶变换在周期信号中的应用
1)	非周期信号的傅立叶变换公式对$ \begin{cases} x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty} X(jw){\it e}^{jwt},w X(jw)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jwt},t\end{cases} $
 
2)	在求周期信号傅立叶变换时候的问题
- A)	对于周期为T的信号x(t)=x(t+T)，如 在一个周期内有x(t)=$ \begin{cases} 1,-T_1<t<T_1 0,T>|t|>T_1\end{cases} $ ，如图所示
- B)	按照这个方法求傅立叶变换时 X（jw）=$\int_{-\infty}^{+\infty} x(t){\it e}^{-jwt}\ {\rm d}t$=$...\int_{-T-T_1}^{-T+T_1} {\it e}^{-jwt}\ {\rm d}t+\int_{-T_1}^{T_1} {\it e}^{-jwt}\ {\rm d}t+\int_{T-T_1}^{T+T_1} {\it e}^{-jwt}\ {\rm d}t$
 这个就比较复杂，难求
- §3.5.2　周期信号的傅立叶变换
1)	考虑一下傅立叶级数的表示方法，最好跟这个对应起来
2) $x(t)=\sum_{k=-\infty}^{+\infty} a_k{\it e}^{jkw_0t}$ ，其中 $\omega_0=2\pi/T$
3)	我们考虑频谱（傅立叶变换）的一个冲激：$X(j\omega)=2\pi\delta(\omega-\omega_0)$ ，那么根据傅立叶反变换，我们可以求得该傅立叶变换对应的原信号为：$x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty} X(jw){\it e}^{-jwt}\ {\rm d}w=\frac{1}{2\pi}\int_{-\infty}^{+\infty} 2\pi\delta(\omega-\omega_0){\it e}^{-jwt}\ {\rm d}w=\int_{-\infty}^{+\infty} \delta(\omega-\omega_0){\it e}^{-jwt}\ {\rm d}w={\it e}^{-jwt}$ 
 
 
4)	由此可见，如果我们设计一个在频谱上的冲激串，这些冲激串的线性组合构成一个频谱：$X(j\omega)=\sum_{k=-\infty}^{+\infty} 2\pi a_k\delta(\omega-\omega_0)$，则经过傅立叶反变换后，得到时域函数为x(t)=$\sum_{k=-\infty}^{+\infty} 2\pi a_k{\it e}^{jk\omega_0t}$
 
5)	如果上述频谱上冲激串前系数正好是周期信号傅立叶级数的系数的话，我们显然可以发现，这个频谱就是原始信号x(t)的傅立叶变换
6)	例1：求信号$x(t)=\cos(\omega_0t)$ 的频谱
- A)	解：x(t)的傅立叶级数的系数为$a_1$=a-1=1/2，所以x（t）对应的频谱为$X(j\omega)=\frac{1}{2}\delta(\omega-\omega_0)+\frac{1}{2}\delta(\omega+\omega_0)$
 
7)	例2：求一个周期性冲激串$x(t)==\sum_{k=-\infty}^{+\infty} \delta(t-kT)$的频谱。
- A)	解：这个信号是周期的，周期为T；其对应的傅立叶级数的系数为
- $a_k=\frac{1}{T}\int_{-T/2}^{T/2} \delta(t){\it e}^{-jkw_0t},t$
 
- B)	代入上面的式子，即可得对应的频谱为：$X(j\omega)=\frac{2\pi}{T}\sum_{k=-\infty}^{+\infty} \delta(\omega-\frac{2\pi k}{T})$ 
## 3.6　连续时间傅立叶变换的性质
- §3.6.1　傅立叶变换对的表示
1)	现在我们有：$ \begin{cases} x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty} X(jw){\it e}^{jwt}\ {\rm d}w X(jw)=\int_{-\infty}^{+\infty} x(t){\it e}^{-jwt}\ {\rm d}t\end{cases} $ ，对于x(t)和X(jw)，是一个变换对
2)	所以我们以后也写成：X(jw)=F{x(t)} ，x(t)= $F^{-1}{X(jw)}$
3)	对于整个变换对，也写成$x(t)\longleftrightarrow F X(j\omega)$ ，注意：左边是时域函数，右边是频域函数，不能写反，若写反，则上面的F要变成$F_{-1}$
4)	例1：$\frac{1}{a+j\omega}=F^{-1}{{\it e}^{-at}\mu(t)},a>0$ 
5)	例2： ${\it e}^{-at}\mu(t)=F{\frac{1}{a+j\omega}},a>0$  6)	例3： $\frac{1}{a+j\omega}\longleftrightarrow F {\it e}^{-at}\mu(t),a>0$ 
§3.6.2　线性
1)	若有$x_1(t)\longleftrightarrow F X_1(j\omega) x_2(t)\longleftrightarrow F X_2(j\omega)$，则$ax_1(t)+bx_2(t)\longleftrightarrow FaX_1(j\omega)+bX_2(j\omega)$
2)	两个信号线性组合的傅立叶变换是单个信号变换的线性组合。
3)	证明略。
- §3.6.3　对称性
1)	若x(t)是一个实时间函数，则有$X(-j\omega)=X*(j\omega)$,(1)，这叫共轭对称性
2)	证明：$X * (j\omega)=[\int_{-\infty}^{+\infty} x(t){\it e}^{-jwt}\ {\rm d}t] * $=$\int_{-\infty}^{+\infty} x(t) * {\it e}^{jwt}\ {\rm d}t $，因为x(t)是实函数，有$x * (t)=x(t)x_1$，所以有$X * (j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{jwt}\ {\rm d}t=X(-j\omega)$
3)	将X(jw)用直角坐标形式表示，即X(jw)=Re{X(jw)}+jIm{X(jw)}，那么当x(t)为实函数时，根据(1)式，有
- A)	Re{X(jw)}=Re{X(-jw)}
- B)	Im{X(jw)}=-Im{X(-jw)}
- C)	也即，X（jw）的实部实频率的偶函数，虚部是频率的奇函数
- D)	同样道理，若将X(jw)用极坐标形式给出，则模是w的偶函数，幅角是x的奇函数
4)	若x(t)是实的，而且为偶函数，则有$X(-j\omega)=\int_{-\infty}^{+\infty} x(t){\it e}^{jwt}\ {\rm d}t\tau=-t=\int_{-\infty}^{+\infty} x(-\tau){\it e}^{-jw\tau}\ {\rm d}\tau x(\tau)=x(-\tau)=\int_{-\infty}^{+\infty} x(\tau){\it e}^{-jw\tau}\ {\rm d}\tau=X(j\omega)$ 
 ，加上共轭对称性，我们就可以知道X(jw)不仅是偶函数，而且是实函数。
5)	若x(t)是实的，而且为奇函数，则有X（jw）是纯虚数，而且是奇函数。
6)	以上的这些结论对傅立叶级数也同样成立，此处略（具体见奥本海默第一版P154-P155）
- §3.6.4　时移性质
1)	若有$x(t)\longleftrightarrow F X(j\omega)$ ，则有$x(t-t_0)\longleftrightarrow F X(j\omega)$  
2)	证明：$F{X(t-t_0)}=\int_{-\infty}^{+\infty} x(t-t_0){\it e}^{-jwt}\ {\rm d}t\sigma=t-t_0=\int_{-\infty}^{+\infty} x(\sigma){\it e}^{-jw(\sigma+t_0)}\ {\rm d}\sigma={\it e}^{-jwt}X(j\omega)$ 
3)	该性质说明：信号在时间上的位移，并没有改变其频谱的模，而只是在频谱上有一个相移，而且引入的相移跟w成线性关系，也即是线性相移。
- §3.6.5　微分和积分性质
1)	微分性质，傅立叶反变换公式两边对t求导，即得：$  \frac{{\rm d}u(t)}{{\rm d}t} \rightarrow=\frac{1}{2\pi}\int_{-\infty}^{+\infty} j\omega X(j\omega){\it e}^{j\omega t}\ {\rm d}\omega$ ，所以有：$  \frac{{\rm d}u(t)}{{\rm d}t} \longleftrightarrow F j\omega X(j\omega)$
2)	 $u(t)\longleftrightarrow F$ $\frac{1}{j\omega}+\pi\delta(\omega)$
3)	由此推出积分性质：$\int_{-\infty}^{t} x(\tau),\tau\longleftrightarrow F\frac{1}{j\omega}X(j\omega)+\pi{X(0)}\tau(\omega)$
4)	我们先看u(t)的推导：
- a)	先将u(t)分解成奇部和偶部，ev(t)=(u(t)+u(-t))/2，od(t)=(u(t)-u(-t))/2，即u(t)=1/2+(u(t)-1/2)
- b)	先考虑奇部$o_d$(t)= u(t)-1/2的频谱。设其频谱为$O_d$(jw)，因为$ \frac{{\rm d}o_d(t)}{{\rm d}t} = \frac{{\rm d}u(t)}{{\rm d}t}=\tau(t)  $ ，由微分性质，可得：
 ，所以有$O_d(jw)=1/jw$
- c)	再考虑偶部ev(t)=1/2，根据在周期信号傅立叶变换时的概念，我们有
F{1/2}=πδ(w)
- d)	所以u(t)的傅立叶变换就是奇部和偶部傅立叶变换之和，也即：$\mu(t)\longleftrightarrow F\frac{1}{j\omega}X(j\omega)+\pi X(0)\delta(\omega)$
 
5)	接着根据后面的卷积性质，我们就可以得到积分性质，卷积性质为$y(t)=h(t)*x(t)\longleftrightarrow FY(j\omega)=H(j\omega)X(j\omega)$
 
6)	根据这个性质，我们可知$\int_{-\infty}^{t} x(\tau),\tau=x(t)*\mu(t) ，而x(t)\longleftrightarrow F X(j\omega)$ ，$\mu(t)\longleftrightarrow F \frac{1}{j\omega}+\pi\delta(\omega)$，所以有$\int_{-\infty}^{t} x(\tau),\tau \longleftrightarrow F X(j\omega)(\frac{1}{j\omega}+\pi\delta(\omega))$，也即 $\int_{-\infty}^{t} x(\tau),\tau \longleftrightarrow F \frac{1}{j\omega}X(j\omega)+\pi X(0)\delta(\omega)$
- §3.6.6　时间和频率的尺度变换性质
1)	若有：$x(t)\longleftrightarrow F X(j\omega)$ ，则有$x(at)\longleftrightarrow F \frac{1}{|a|}X(\frac{\omega}{a})$ 
2)	证明：主要是利用变量替换τ=at.$F{x(at)}=\int_{-\infty}^{+\infty} x(at){\it e}^{-j\omega t},t\begin{cases}
        1/a \int_{-\infty}^{+\infty}x(\tau){\it e}^{-j(w/a)\tau},\tau ,a>0
        1/a \int_{-\infty}^{+\infty}x(\tau){\it e}^{-j(w/a)\tau},\tau ,a>0 
        \end{cases}$ 
        =1/|a|X(\frac{w}{a})$
 
3)	这个特性说明了时间压缩和频率压缩之间的相反关系。当时间压缩（a>1）时，对应信号的频谱展宽；而在时间上伸展时，则频谱压缩
- a)	理解：当磁带快放时，正常的声音我们听起来也很尖，说明信号的频率变高，那就是频谱在高频部分增多，也就是将原频谱展宽
- b)	同理，在磁带慢放时，正常的声音都会变成低音，说明信号的频率变低，那就是频谱在低频部分增多，也就是将原频谱压缩
- §3.6.7　对偶性
1)	从傅立叶变换和反变换的公式中，我们也看出它们在形式上非常相近，它们之间存在这某种对称性，这就是所谓傅立叶变换的对称性。(附图奥本海默第一版P158图4.27)
2)	 $\begin{cases}
       x(t)=\frac{1}{2\pi} \int_{-\infty}^{+\infty}X(j\omega){\it e}^{jwt},\omega ...(1)
       X(j\omega)=\int_{-\infty}^{+\infty}x(t){\it e}^{-jwt},t ...(2)
        \end{cases}$ 
      
3)	我们考查下列积分式 $f(u)=\int_{-\infty}^{+\infty}g(v){\it e}^{juv},v$
- a)	若u＝w，v＝t，则上式就是傅立叶变换公式，即 ，也即 $f(\omega)=F{g(t)},g(t)\longleftrightarrow F f(w)$
- b)	若u=t，v＝w，则对应傅立叶反变换公式，有$f(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty} F(j\omega){\it e}^{-j\omega t},\omega=\int_{-\infty}^{+\infty} g(\omega){\it e}^{-j\omega t},\omega=\int_{-\infty}^{+\infty} g(-\omega){\it e}^{j\omega t},\omega$
 
所以：g(-w)=(1/2π)F(jw)，也即$ f(t)\longleftrightarrow F 2\pi g(-\omega)$
4)	总结，所谓对偶性，就是：如果有$x(t)\longleftrightarrow F X(j\omega)$ ，则有$X(t)\longleftrightarrow F 2\pi x(-j\omega)$ 
5)	例1：求下列信号的傅立叶变换 $x(t)=\frac{2}{t^2+1}$
- a)	解：由以前知识我们知道$x(t)={\it e}^{-|t|}$ 对应的傅立叶变换是$X(j\omega)=\frac{2}{w^2+1}$ ，也即 ，现在要求X(t)对应的傅立叶变换，根据对偶性，应该有$X(t)\longleftrightarrow F 2\pi x(-j\omega)$  ，则X(t)对应的傅立叶变换为 $2\pi x(-j\omega)=2\pi{\it e}^{-|-w|}=2\pi{\it e}^{-|w|}$
6)	很多地方都对应着对偶性，同学们自己要多观察，多练习。
- §3.6.8　帕斯瓦尔(Parseval)定理
1)	若$x(t)\longleftrightarrow F X(j\omega)$ ，则$ \int_{-\infty}^{+\infty} {|x(t)|}^2,t=\frac{1}{2\pi}\int_{-\infty}^{+\infty} {|X(j\omega)|}^2,\omega$
- 2)	证明：$ \int_{-\infty}^{+\infty} {|x(t)|}^2,t$=$ \int_{-\infty}^{+\infty} x(t) * x(t),t$=$ \int_{-\infty}^{+\infty} x(t)[\frac{1}{2\pi} \int_{-\infty}^{+\infty}X(j\omega){\it e}^{j\omega t},\omega]^,t$ 
 ，交换积分顺序，有$=\frac{1}{2\pi} \int_{-\infty}^{+\infty}X(j\omega)\int_{-\infty}^{+\infty} x(t){\it e}^{-j\omega t},t,\omega=\frac{1}{2\pi} \int_{-\infty}^{+\infty}X*(j\omega)X(j\omega),t=\frac{1}{2\pi} \int_{-\infty}^{+\infty}|X(j\omega)|^2,\omega$
 
3)	一个信号的能量，可以从其时域的积分进行计算，也可以按照每单位频率内的能量（ ）在整个频率范围内积分得到，而 叫信号的能量谱密度
## 3.7　卷积性质
- §3.7.1　卷积性质的数学证明
1)	性质公式：$y(t)=h(t)*x(t)\longleftrightarrow F Y(j\omega)=H(j\omega)X(j\omega)$ ，两个信号卷积的频谱，是各自频谱的乘积，简言之：时域卷积对应频域相乘
2)	数学证明：
- a)	根据卷积积分定义，有 $y(t)=\int_{-\infty}^{+\infty}x(\tau)h(t-\tau)\ {\rm d}\tau$
- b)	y(t)的傅立叶变换为Y(jw)：$Y(j\omega)=F{y(t)}=\int_{-\infty}^{+\infty}[\int_{-\infty}^{+\infty}x(\tau)h(t-\tau)\ {\rm d}\tau]{\it e}^{-jwt}\ {\rm d}t$ 
- c)	交换积分顺序，有=$\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}x(\tau)h(t-\tau){\it e}^{-jwt}\ {\rm d}t\ {\rm d}\tau=\int_{-\infty}^{+\infty}x(\tau)[\int_{-\infty}^{+\infty}h(t-\tau){\it e}^{-jwt}\ {\rm d}t]\ {\rm d}\tau$
 
- d)$=\int_{-\infty}^{+\infty}x(\tau){\it e}^{-jwt}H(j\omega)\ {\rm d}\tau=H(j\omega)\int_{-\infty}^{+\infty}x(\tau){\it e}^{-jwt}\ {\rm d}\tau=H(j\omega)X(j\omega)$	 
- 3.7.2　卷积性质的另一种理解
1)	性质推导，也可以从指数信号的特征函数角度来理解和推导，具体见课本P105，此处略，最后结果是一致的
2)	卷积性质是系统频域分析里最重要的理论基础，可以将信号卷积转换成频域上相乘的方法，所以单独列出一节
3)	周期卷积相关概念也请同学们自学课本P105最后一段开始部分。
- §3.7.3　一个例子
1)	设一个系统的冲激响应为$h(t)={\it e}^{-at}\mu(t)$ ，a>0系统输入为$x(t)={\it e}^{-bt}\mu(t)$,b>0 ，求系统的输出；
2)	根据以前的解法，y(t)＝x(t)*h(t)直接进行时域卷积即可
3)	现在用卷积性质解
- a)	由以前解，可得：$H(j\omega)=\frac{1}{a+j\omega} ，X(j\omega)=\frac{1}{b+j\omega}$
- b)	Y(jw)=H(jw)X(jw)=$ \frac{1}{a+j\omega}\frac{1}{b+j\omega}$
- c)	若a<>b,
- i.	则用待定系数法， $Y(j\omega)= \frac{A}{a+j\omega}+\frac{B}{b+j\omega}$，A(b+jw)+B(a+jw)=1，根据实部虚部相等，得$\begin{cases}
        A+B=0
        Ab+Ba=1
        \end{cases}
        \rightarrow 
        \begin{cases}
        A=1/b-a
        B=-1/B-A
        \end{cases}$ 
- ii.	所以 $Y(jw)=\frac{1}{b-1}(\frac{1}{a+jw}-\frac{1}{b+jw})$
- iii.	利用反变换，得 $y(t)=\frac{1}{b-1}({\it e}^{-at}+{\it e}^{-bt})\mu(t)$
- d)	若a=b，则 $Y(jw)=\frac{1}{(a+jw)^2}$
- i.	经过整理，我们有$\frac{1}{(a+jw)^2}=j \frac{{\rm d}(\frac{1}{a+j\omega})}{{\rm d}\omega}  $
- ii.	将傅立叶变换公式两边对w求导，得 ，所以有$  \frac{{\rm d}X(jw)}{{\rm d}\omega} =\int_{-\infty}^{+\infty}-jtx(t){\it e}^{-jwt},t$
- iii.	因为 ，根据上性质，有$-jtx(t)\longleftrightarrow F  \frac{{\rm d}X(jw)}{{\rm d}\omega} $，两边乘以-j，有 $t{\it e}^{-at}\mu(t)\longleftrightarrow F j \frac{{\rm d}(\frac{1}{a+j\omega})}{{\rm d}\omega}  $
- iv.	所以有 $y(t)=t{\it e}^{-at}\mu(t)$
## 3.8　调制性质
1)	卷积性质是时域卷积可以转换为频域相乘，那么根据对偶原理，我们可以得到时域相乘可以转换为频域卷积，这就变成调制性质
2)	调制性质：r(t)=s(t)p(t)$\longleftrightarrow FR(jw)=\frac{1}{2\pi}S(j\omega)*P(jw)$
3)	一个信号被另一个信号去乘，叫做一个信号去调制另一个信号的振幅，因此两个信号相乘叫幅度调制。（此处画载波和调制波信号及调制后信号三张图），所以叫调制性质。
4)	证明：由已知，得，$p(t)\longleftrightarrow FP(jw)$ ，根据对偶性，有$S(jt)\longleftrightarrow F 2\pi s(-w) ， P(jt)\longleftrightarrow F 2\pi p(-w)$
5)	利用卷积性质，有S(jt)*P(jt)$\longleftrightarrow$4π2s(-w)p(-w)
6)	再对上式用对偶性质，有$4\pi^2s(-t)p(-t)\longleftrightarrow F 2\pi S(-jw)* P(-jw)$ ，因为有$x(-t)\longleftrightarrow FX(-jw)$ ，所以上式就相当于：$s(t)p(t)\longleftrightarrow F\frac{1}{2\pi}S(jw)*P(jw)$ 
7)	例1：已知信号s(t)得频谱为如图所示（奥本海默第一版P167图4.30），另有一个信号p(t)=cos$w_0$t，求两者相乘后得频谱
- a)	解：现在要求y(t)=s(t)p(t)得频谱，而已知s(t)的频谱，那么还得知道p(t)的频谱，而根据周期信号傅立叶变换方法，可得P(jw)为对应频率的冲激。且幅度为对应的傅立叶级数的系数，所以$P(jw)=πδ(w-w_0)+πδ(w+w_0)，假设w_0>w_1
- b)	所以Y(jw)=(1/2π)S(jw)*P(jw)=1/2S(w-w_0)+1/2S(w+w_0)$如图所示（奥本海默第一版P167图4.30）


- c)	所谓幅度调制，就是将信号的频谱进行搬移（通过几次搬移后，将信号放到合适传输的中心频率上），其实现的方法就是乘法器，将载波和原始信号相乘
- §3.9　傅立叶变换与傅立叶级数的性质及基本傅立叶变换对列表
具体见课本P106到109，主要有三大类性质：
1)	傅立叶变换性质
2)	连续时间傅立叶级数性质
3)	基本信号的傅立叶变换对
4)	此处略
## 3.10　用线性常系数微分方程表征的系统的频率响应
- §3.10.1　频率响应概念
1)	我们知道，一个LTI系统对于输入信号${\it e}^{st}$ ，其输出信号为$H(s){\it e}^{st}$ ，当s＝jw时，就变成${\it e}^{jwt}\rightarrow H(jw){\it e}^{jwt}$ ，其中$H(jw)=\int_{-\infty}^{+\infty}h(\tau){\it e}^{-jw\tau}\ {\rm d}\tau$ 。系统单位冲激h(t)的傅立叶变换H(jw)就是当频率为w的复指数信号通过一个线性时不变系统时，其复数振幅所经受的变化。因此一般也叫做系统的频率响应。
2)	所以系统框图一般也表示为： ，从时域角度，输出是输入信号与单位冲激响应的卷积，从频域角度，输出信号的频谱是输入信号频谱与系统频率响应的卷积
- a)	y(t)=x(t)*h(t)
- b)	Y(jw)=X(jw)*H(jw)
- §3.10.2　已知数学方程的求解
1)	已知系统方程，求频率响应；
- a)	例1：全部初始条件为零的一个LTI系统，由如下方程给出，求其频响和单位冲激响应$ \frac{{\rm d}y(t)}{{\rm d}t} +ay(t)=x(t),a>0$. 
- i.	解：两边进行傅立叶变换，即得：(jw)Y(jw)+aY(jw)=X(jw) 
- ii.	$H(jw)=\frac{Y(jw)}{X{jw}}=\frac{1}{a+jw}$ ，a>0
- iii.	而当a>0时，H(jw)对应的单位冲激响应也是收敛的，为 $h(t)={\it e}^{-at}\mu(t)$
- b)	例2：全部初始条件为零的一个LTI系统，由如下方程给出，求其频响和单位冲激响应$ \frac{{\rm d}^2y(t)}{{\rm d}t^2} +4\frac{{\rm d}y(t)}{{\rm d}t} +3y(t)=\frac{{\rm d}x(t)}{{\rm d}t} t+2x(t)$。 
- i.	解，同上，我们可得$H(jw)=\frac{Y(jw)}{X(jw)}=\frac{jw+2}{(jw)^2+4(jw)+3} $，接下来求单位冲激响应的话，就用部分分式法和待定系数法展开;
- ii.	有 $H(jw)=\frac{jw+2}{(jw)^2+4(jw)+3}=\frac{1/2}{jw+1}+\frac{1/2}{jw+3} $
- iii.	所以$h(t)=\frac{1}{2}{\it e}^{-t}u((t)+ \frac{1}{2}{\it e}^{-t}u((t)+\frac{1}{2}{\it e}^{-3t}u((t)$
2)	已知系统方程和输入，求系统输出；
- a)	例3：求例2系统的输出，如果输入为 $x(t)={\it e}^{-t}u(t)$
- b)	解，根据上面方法，有$Y(jw)=X(jw)H(jw)^{X(jw)=\frac{1}{1+jw}}=\frac{jw+2}{(jw+1)^2(jw+3)}$ 
- c)	这种部分分式展开方法为：$Y(jw)=\frac{A_11}{jw+1}+\frac{A_12}{(jw+1)^2}+\frac{A_21}{jw+3}$ ，可以解得待定系数为A11=1/4,A12=1/2,A21=-1/4，所以 $Y(jw)=\frac{1/4}{jw+1}+\frac{1/2}{(jw+1)^2}-\frac{1/4}{jw+3}$
- d)	所以 $y(t)=(\frac{1}{4}{\it e}^{-t}+\frac{1}{2}t{\it e}^{-t}-\frac{1}{4}{\it e}^{-3t})u(t)$
- §3.10.3　电路系统的频域求解
1)	大量的电路系统是由放大器、加法器、电阻、电容和电感等线性单元电路和器件所组成，可以很方便的在频域进行分析。定义复阻抗$R(jw)=\frac{U(jw)}{I(jw)}$ 
2)	列出初始静止时的时域电路方程：$
        \begin{cases}
        电阻u_R(t)=Ri_R(t) 
        电容i_c(t)=C  \frac{{\rm d}u_c(t)}{{\rm d}t}
        电感u_L(t)=L\frac{{\rm d}i_L(t)}{{\rm d}t} 
        \end{cases}
$ 
3)	对该方程两边求傅立叶变换，得 $
        \begin{cases}
      电阻U_R(jw)=RI_R(jw) \\
      电容I_c(t)=jwCU_C(jw)
      电感C_L(jw)=jwLI_L(jw)
        \end{cases}
$ 
4)	所以得到三种元器件的复阻抗为 ， $
        \begin{cases}
      电阻R(jw)=R \\
      电容R(jw)=1/jwC
      电感R(jw)=jwL
        \end{cases}
        $可以将这些复阻抗作为电阻直接代入电路方程。
5)	例：对于RC电路（加上图，课本P116页图3－22,加上数值，使RC=1/2），如果输入是一个阶跃信号，求系统输出。
- a)	解：输出端电压方程为：$V_C(jw)=\frac{1/jwC}{1/jwC+R}X(jw)$ 
- b)	所以 $H(jw)=\frac{V_C(jw)}{X(jw)}=\frac{1/jwC}{1/jwC+R}X(jw) =\frac{1}{1+jwRC}=\frac{2}{2+jw}$
- c)	 $X(jw=\frac{1}{jw}+\pi\delta(\omega)$
- d)	 $V_C(jw)=\frac{2}{2+jw}(\frac{1}{jw}+\pi\delta(\omega))=\frac{2}{(2+jw)jw}+\frac{2}{2+jw}\pi\delta(\omega)$
- e)=$\frac{1}{jw}-\frac{1}{2+jw}+\pi\delta=(\frac{1}{jw}+\pi\delta)-\frac{1}{2+jw}$	 
- f)	求得傅立叶反变换为： $v_C(t)=(1-{\it e}^{-2t})u(t)$
```flow
st=>start:Start
e=>end:End
op1=>operation:My Operation
sub1=>subroutine:MySubroutine
cond=>condition:Yes or No?
io=>inputoutput:catch something...
st->op1->cond
cond(yes)->io->e
cond(no)->sub(right)->op1
```