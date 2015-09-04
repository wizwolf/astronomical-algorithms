# 第4章 曲线拟合
  

  在很多情况下，天文观测得到的数据是一组包含很大数量的序列点图象，每一点用x值和y值定义。这就可能需要画一条通过这些点的最佳拟合曲线。

  有多种类型的曲线可以作为这些点的拟合曲线，如：直线、指数、多项式、对数曲线等。

  为了避免只对个别数据分析，需要进行最佳曲线拟合。考虑图1的N个数据点，它们的坐标是(X1,Y1)，(X2,Y2)...，(XN,YN)。假设这些值中的X是严格的精确值，Y的值是测量值(含有一些误差)。



  对于一个给定的X，如X1，对应的值Y1与曲线C上对应的Y值将存在一个差值。在图中，我们用D1表示这个差值，有时我们也称这个差值为偏差、误差或残差，它可能是正、负或零。类似的，X2...，XN，对应的差值为D2，....，DN。

  我们用D12 + D22 + ... + DN2 作为衡量曲线C拟合的“最佳”程度，这个值越小越好，越大则越不好。因此，我们做以下定义：任何一种类型的曲线，它们都有一个共同的特性，当ΣDi2最小时，称为最佳拟合曲线。注：∑指“取和”计算。

  一条曲线具有这一特性时，称之为“最小二乘拟合”，这样的曲线称为“最小二乘曲线”。

  正如上面说的，我们假设各个X的值是精确的。当然，有时候我们会考虑再对D1、D2...DN做一次最小二乘曲线拟合，不过，这不常用。

  在本章，我们将考虑一个重要情形：拟合为一条直线，数学上称之为“线性回归”。“回归”一词看起来有点陌生，因为计算最佳曲线没什么好“回归”的，最好的术语就是“曲线似合”，在直线情况下就是“线性曲线拟合”。

线性曲线拟合

  我们希望使用最小二乘法计算出以下线性方程的系数(斜率a以及y轴的截距b)：

  y = a*x + b   (4.1)

  a和b可以使用以下公式计算：



  式中N是数据点的个数。注意，以上两式具有相同的分母，∑指逐项加法计算(取和)。∑x指对所有的x值求和，∑y指对所以的y值求和，∑(x^2)指对所有x的平方求和。∑xy指对所有的积xy进行取和计算。应注意，∑xy 与 ∑x*∑y是不相同的(“积的和”与“和的积”是不同的)，同样(∑x)^2与∑(x^2)也是不相同的(“和的平方”与“平方的和”是不相同的)。

  有个有趣的天文应用，找出某个慧星亮度与它到太阳距离之间的关系。慧星的视星等m一般用以下公式表示：

  m = g + 5*logΔ + k * log r

  式中，Δ和r是距离，单位是天文单位，分别是慧星到地球和太阳的距离。log是以10为底的对数。绝对星等g和系数k须由天文观测数据间接推导，可以在一个足够长的时期内测星出星等m，然后再用适当方法计算(下文将使用最小二乘法算出g和k)。为了更精确，r的变化范围要足够大。对于每个m，相应的Δ和r须从星历表中推导出或者使用轨道要素计算出。

  在这种情况下，g和k是未知的。公式改写为：

  m - 5 logΔ = k * log r  + g

  它的形式与公式(4.1)相同，当我们写作 y = m - 5 logΔ，x = log(r)。我们把y称为“日心”星等，因为慧星到地球的距离变化效果已被移除。

----------------------------

例4.a：——表4.A是Wild2(1978b)周期慧星的可视星等，John Bortle提供的。对应的r和Δ已经利用轨道要素计算出。

  用x和y计算各个和项：∑x，∑y，∑x2以及∑xy。我们得到：

N=19
∑x  = 4.2805 ∑y  = 192.0400
∑x2 = 1.0031 ∑xy = 43.7943

因此，由公式(4.2)得 a = 13.67，b = 7.03

所以，这些观测值的最佳曲线拟合是：y = 13.67x + 7.03 或 m - 5 logΔ = 13.67 log r + 7.03

因此，周期慧星Wild2在1978年的星等为：m = 7.03 + 5 log Δ + 13.67 log r



--------------------------

关系系数(“互相关联程度”系数，概率论上称之为“相关系数”)

  一个“关系系数”是指两个变量相互联系程度的统计测量值。对于线性方程，关系系数是：



  这个系数介于+1到-1之间。如果值为+1或-1，说明x和y之间有完全的线性关系，所有的点(x,y)精确的在同一条直线上。如果 r = +1，y随x增加而增加(如图2)，如果 r = -1，也是一条直线，但y随x增加而减小(如图3)。

  当r=0，x和y之间就没有关系了(如图4)。不过，在实践中，当数据没有联系时，我们得到的r可能没有精确为0，这是由于一般会存在偶然因素，除非数据点无穷多个。

  当|r|在0到1之间，x和y之间存在一定的“趋势”，虽然它们之间没有严格的关系（如图5）。要注意，即使两个变是是严格的线性关系，但我们计算的r值却可能不是精确等于+1或-1，那是因为测量值存在误差。



  应当注意，r的值是一个带小数的值，它没有单位。

  r的正负号仅告诉我们y是随x增加的还是减小的。事实上重要的不是符号，而是r的大小，因为r的大小表示直线逼近的程度。

  需要强调的是，在任何情况下，计算值r是用来衡量数据点与函数(线性方程)的相关程度。因此，当r接近于0，那么两个变量之间几乎线性无关，然而这不一定说明它们之间没有一点关系，因为它们可之间可能存在某种非常精确的非线性关系。做为一个例子，我们考查以下几个点：

x	-4	-3	-2	-1	0	+1	+2
y	-6	-1	+2	+3	+2	-1	-6
  由公式(4.3)得r=0，而这些数据是精确的抛物线关系 y = 2 - 2x -x*x，如图6。



  还应指出，很高的“关系系数”(接近下+1或-1)，不一定直接说明变量之间的“物理”关系紧密。因此，如果考虑管理领域的一个足够大量的数据，我们可以在各精神病院的病床数量和电视接收机数量之间得到一个很高的“关系系数”。的确，它们具有很高的数学关系，但“物理”关系却是没有意义的。

------------------------------------

例4.b：——表4.B，给出1761年到1989年，22次太阳黑子最大的情况。x是时间间隔(单位是月)，从上一次太阳黑子最小算起。高度y是太阳黑子的最大值。

  我们得到：

∑x  = 1120   ∑y  = 2578.9    ∑xy = 122337.1
∑x2 = 60608  ∑y2 = 340225.91    N = 22

  然后由公式(4.2)和(4.1)得到：

  y = 244.18 - 2.49x  (4.4)





  方程(4.4)对应这22个点的最坐直线拟合。这些点和直线显示在图7。

  由公式(4.3)得 r = -0.767。这表明存在明显"关系"，r是负值表明x和y的关系是负的：太阳黑子活动，从一个最小值达到下一个最大值的时间越长，太阳黑子的最大值则越小。

--------------------------------

  要注意，正如统计学研究的，为了得到一个有意义的结果，样品要足够大。如果基于很小的样品数，我们得到“关系系数”接近于1或-1，那是没有“物理”意义的。当样品数很小时，我们可能偶然得到很大的“关系系数”。

--------------------------------

  作为一个练习，请证实比利时Uccle天文台的降雨量与太阳黑子的活动无关。使用表4.C提供的数据，其中：

  x = 每年明显的Zurich太阳黑子数量，
  y = Uccle每年的降雨量，单位是毫米

  答案：“关系系数”r=-0.064，这表时x和y之间没有关系。

  如果去掉最后两点，系数(从1901到1988年)为-0.027。



二次曲线拟合

  假设我们希望画一条逼近N个点的最佳二次曲线：

  y = ax2 + bx + c

 这是一个纵轴的抛物线。



---------------------------

一般曲线拟合 (多重线回归)

  最佳线性拟合的原理可以被扩展到其它函数，这个函数可以含有超过两个未知的线性系数。

  让我们考虑三个函数的线性组合的情况。假设我们已知：

  y = a f0(x) + b f1(x) + c f2(x)

  式中f0、f1和f2是三个关于x的已知函数，但系数a、b和c是未知的。此外，假设已知3个x对应的y值。那么系数a、b、c可按如下得到。



----------------------------

例4.c：——已知y表达为：

  y = a sin x + b sin 2x + c sin 3x

  并且y的值如下：



  我们把这道题留者。最后答案是：

  y = 1.2 sin x - 0.77 sin 2x + 0.39 sin 3x

  它的图像见上图。

  读者无须得到1.2、-0.77、+0.39的精确数，因为表中的y值只给出了4位有效数字。

----------------------------

  让我们考虑一种特殊的情况：

  y = ax2 + bx + c

  令：f0=x2，f1=x，f2=1

  这样算得 T = N (N是给定的点数)，Q=R，这样，由公式(4.7)就可推导出(4.5)和(4.6)，只是所用的字母符号不同。

  另一种特殊情况，考虑y=a*f(x)，只有一个未知系数。我们容易得到：

  a = Σy·f / Σf2    (4.8)

　

例4.d：

  y = a*sqrt(x)  (x>=0)

  寻找经过以下数据点的最佳曲线拟合：

x：	0	1	2	3	4	5
y：	0	1.2	1.4	1.7	2.1	2.2
  这里f(x)=sqrt(x)，所以Σf2只是简单的对x求和，由公式(4.8)得：a = 15.2437/15

  所以，所需的函数是：y = 1.016*sqrt(x)

　

参考资料

1.Helmut Alt, Angewandte Mathematik, Finanz-Mathematik, Statistik,Informatik fur UPN-Rechner, P.125(Vieweg,Braunschweig,1979).

2.国际天文联合会3177号通告(1978年2月24日)。