第35章 一些行星现象的计算

 

  有两种不同的基本方法用于计算行星现象，如金星的最大距角、火星的“冲”：

  (i) 比较行星与太阳的精确位置。
  (ii)使用公式，并采用一些周期项对其修正。

  第一种方法有利于得到精确的结果，因为使用了高精度的天体位置坐标。不过，有个不便之处就是，需要有精确的星历表或精确的星历计算。

  第二种方法，可以快速的容易的执行任意一年的计算。结果不如第一种方法精确，但对于多数应用来说是足够的，如用于历史研究，甚至可以用于精确计算的首次估值(如迭代计算)。

  在本章，我们将提供水星到海王星的几种相对位置关系的公式：与太阳的“冲”、“会合”以及最大距角。

“冲”与“会合”

  从表35.A中的某一行，可以得到A、B、M0和M1的值。

  设Y是某一行星现象的时间估计，表达为带小数的年。使如1993.0表示1993年的年首，2028.5表示2028年的年中，等等。



  整数k接近于：(365.2425Y + 1721060 - A)/B    (35.1)

  应注意，k必须是整数，非整数是无意义的。依次的k，依次对应相应事件日期。k=0，对应2000年1月1日之后第一个，2000年之前k为负值。(其实365.2425*2000+1721060=2451545)。

  然后计算：JDEo = A + kB，  M = M0 + kM1

  JDEo是儒略历书日，对应行星“平相对位置(看做匀速圆周运动)”的发生时间，M是此刻地球的平近点角。

  接下来计算M、a、L、c、d、e、g等角度，用于周期项计算。

  M是带小数点的角度，单位是度。根据计算机或程序设计语言的需要，可以转到0到360度(通过加上或减去360度的整倍数)，还可以转到弧度制。

  T是2000年起算的儒略世纪数：T = (JDEo - 2451545)/36525，公元2000之后，T为正，之前为负。

  对于木星到海王星，还需计算以下几个角度：



  真相对位置发生时间JDE是：“平时间”JDEo + 周期项修正量。这些修正量详见表35.B，是关于角度M的周期项的和。由于行星轨道的世纪变化，周期项系数随时间缓变化，因此表中存在T和T的平方项。

  例如，水星的内会合，修正量是：

+ 0.0545 + 0.0002T
+ (-6.2008 + 0.0074T + 0.00003T2) sin M
+ (-3.2750 - 0.0197T + 0.00001T2) cos M
+ ( 0.4737 - 0.0052T - 0.00001T2) sin 2M
+ 等等...

  这种方法得到的已修正的时间，其一个儒略历书日(JDE)，因此是力学时尺度。可以减去ΔT(单位是天，参见第9章)转为基于UT时的标准儒略日(JD)。不过，在公元1500到2100年，-ΔT可以忽略。

  最后，利用标准程序(见第7章)，可以把JD转为日期格式。

例35.a ——计算1993年10月1日附近，水星的内会合。

  由表35.A的水星内会合部分，我们有：

  A = 2451612.023

  B = 115.8774771

  M0 = 63.5867

  M1 = 114.2088742

  从年首起算，10月1日是一年中3/4，因此 1993年10月1日 = 1993.75 = Y，由公式(35.1)得到-20.28，因此k=-20(记住，k必须是一个整数)。那么：

  JDEo = 2449294.473

  M = -2220°.5908 = +299°.4092

  T = -0.06162

  对表35.B中相关的部分(水星内会合)的周期项取和计算得+3.171，因此：

  JDE = JDEo + 3.171 = 2449297.644，对应 1993年11月6日3h TD，舍入到小时，这就是确切的时间。

例35.b ——计算2125年土星与太阳会合时间。

  表35.A的土星会合数据：

  A = 2451681.124

  B = 378.091904

  M0 = 131.6934

  M1 = 12.647487

  Y=2125.0(即2125年的年首)，由表达式(35.1)得到+120.39。因为我们查找2125年之后的首个土星——太阳会合，所以取k=+121，而不是+120。那么：

  JDEo = 2497430.244

  M = 1662°.0393 = 222°.0393

  T = +1.25627

  另外，对于土星，还要计算以下附加角度：

  a = 133°.95， b = 73°.97， c = 36°.18， d = 6°.53

  对表35.B(土星与太阳会合相关的数据)的项取和计算得+7.659，因此：

  JDE = JDEo + 7.659 = 2497437.903，对应 2125年8月26日10h TD。

  使用更精确的方法计算，得到的正确时刻是2125年8月26日11h TD。

水星和金星的最大距角

  为了计算水星或金星的最大距角发生的时刻，我们从最近的内会合开始。所以，我们按以上说明的方法计算k、JDEo、M和T。我们不计算真会合时刻，相反，我们使用表35.C的周期项计算水星“平”内会合的修正量，得到最大东或西距角发生的时刻。在同一表中，还提供了计算最大距角的周期项。

  别忘了，如果行星在太阳的东边，那么晚上在西边可视(太阳下山后，往西看，黄道附近可见星体)，如果行星距角是西(黄道附近，太阳西边)，那么早晨在东方可见星体，即太阳升起之前可清淅看到星体。

  行星到太阳的距角最大值的单位是“度”，是带小数的。最大距角指：在地心看，行星到太阳圆面中心的角距离，而不是二星体的地心黄道经的最大差值。行星到太阳的距角没有官方定义，我们可以考虑以下两种不同的定义：

  (a)星体到太阳圆面中心的角距离
  (b)星体与太阳圆面中心的地心黄经之间的差值

  这两种不同的定义均在天文文献中使用。1960年起，《天文历书》就已开始使有(a)定义，在1981年以后《天文年历》继承之。我们更喜欢这种定义。例如，金星在在“内会合”附近的可视性，主要和行星与太阳的角度差有关，而不是它们的黄经差。

  然而，法国天文学家使用(b)定义，例如，在它们的《Annuaire du Bureau des Longitudes》，第275页1900卷，我们看到：



  使用(a)定义与(b)定义，得到的结果会有些不同。例如，1990年8月11日，水星的最大距角：太阳和水星黄经的差值在15h UT时刻达到最大值(27°22')，结果如同《Annuaire du Bureau des Longitudes》第277页所讲到的。但是，最大角度差发生在21h，其值为27°25'。

例35.c ——找出1993年11月，水星西最大距角发生的时刻。

  我们从1993年11月的“内会合”开始计算，由此得到(参见例35.a)：

  JDEo = 2449294.473， M = 299°.4092， T = -0.06162

  把M和T的值代入表35.C的相应部分(水星，西最大距角)：

  修正量 = +19.665天，  距角 = 19°.7506

  因此，水星的西最大距角发生在：

    JDE = JDEo + 19.667 = 2449314.14

  对应 1993年11月22日15h TD，最大距角是19°.7506 = 19°45'。

结果的精度

  很明显，表35.B和35.C仅对有限的时间范围有效，即在公元2000年前后几千年内有效，而不是百万年！因此，不要把本章的方法用于公元-2000以前或公元4000年以后。

  对于现代时间，即公元1800到2000年，水星和金星现象发生时刻的误差小于1小时，土星、天王星和海王星2小时，火星3小时，木星4小时。

  可以预见，在公元-2000和4000年，最大可能误差会大一些。另一方面，如果计算的历元接近公元2000年，即1900到2100年，那么T^2项可以安全的忽略。

练习

  在以下情况下，测试你的程序；所以的时间是TD时间。

水星 内会合 1631年11月07日 07h  (a)
金星 内会合 1882年12月06日 17h  (b)
火星 “冲” 2729年09月09日 03h  (c)
木星 “冲”   -6年09月15日 07h  (d)
土星 “冲”   -6年09月14日 09h  (d)
天王 “冲” 1780年12月17日 14h  (e)
海王 “冲“ 1846年08月20日 04h  (f)

(a)第一次观测到水星经过日圆盘(Gassendi，在巴黎)
(b)公元2004以前，金星最后一次凌日。
(c)一次火星的近日“冲”
(d)木星和土星的“冲”时刻相差小于1天，在那年，在两行星之间出现三体会合。
(e)Willian Herschel发现天王星之前的3个月
(f)海王星被发现之前的1个月。













