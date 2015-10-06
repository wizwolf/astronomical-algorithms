# 第7章 儒略日


  本章中我们将给出一种方法，将儒略历或格里高利历中的日期转换成相应的儒略日数（JD），以及反向转换。

概述

  儒略日数（简称儒略日），是指从公元 -4712 年开始连续计算日数得出的天数及不满一日的小数，通常记为 JD (**)。传统上儒略日的计数是从格林尼治平午，即世界时12点开始的。若以力学时（或历书时）为标尺，这种计数通常表达为“儒略历书日”，即JDE (**)，其中E只是一种表征，即按每天86400个标准秒长严格地计日。例如：

1977年4月26.4日 UT = JD 2443 259.9

1977年4月26.4日 TD = JDE 2443 259.9

  在下面将要描述的方法中，我们得考虑将其它历日换算为格里高利历日期。因而，1582年10月4日（儒略历）的下一日为1582年10月15日（格里高利历）。

  格里高利历并非在所有国家迅速得到一致采用，这一点在历史研究中要引起注意。例如在大不列颠，晚至公元1752年才变更历法，而土耳其则要等到1927年。

  儒略历由尤里乌斯·恺撒于公元前45年在罗马帝国创立，而其最终形式确立于公元8年前后，尽管如此，我们仍可以借助天文学家的演算无止境地向前推算儒略历。比如在这一系统中，我们可以说某次日食发生在公元前1203年8月28日，虽然在那个遥远的年代，罗马帝国根本还未被创建，而8月这个月份更有待设立。

  对于公元1年之前的年份如何计数，天文学家同历史学家并不一致。在本书中，“公元前”的年份以天文方法计数。这样，+1年的前一年为0年，再之前才是-1年。所以历史学家所说的公元前585年实际上是-584年。

  天文上以负数计数年份只是为算术目的起见。比如，在历史学计数中的，可被4整除的年份为儒略历闰年这个规则不再有效了。虽然像公元前1，5，9，13，…这些年份的确也在天文学上的闰年序列中，然而它们却被记为0，-4，-8，-12 …，它们都能被4整除。

  我们以INT(x)来表示数x的整数部分，即小数点前的整数。例如：

INT(7/4) = 1   INT(5.02) = 5

INT(8/4) = 2   INT(5.9999) = 5

  这里负数可能会造成些问题。在某些计算机或程序语言中，INT(x)为小于等于x的最大整数。那样的话就有INT(-7.83) = -8，因为-7的确比-7.83大。如果你的程序是javascript，取整函数是 Math.floor(x)，它返回小于等于x的最大整数。如果你用的是C++，那么用 (int)x 强制转换，得到是的整数部分。

  但在其它一些语言中，INT为所给数的整数部分，也即小数点前的部分。这样就有INT(-7.83) = -7，这被称为舍位(Truncation)。某些程序包含了这两项功能：表示前一种涵义的INT(x)以及TRUNC(x)。

  因此，对负数进行取整时要特别注意（对正数，二者所得结果一致）。在本书给出的算式中，INT的使用总是针对正数的。

儒略日的计算

  下面的方法对正数年和负数年都是有效的，负的儒略日数除外。

  设Y为给定年份，M为月份，D为该月日期（可以带小数）。

  若M > 2，Y和M不变，若 M =1或2，以Y–1代Y，以M+12代M，换句话说，如果日期在1月或2月，则被看作是在前一年的13月或14月。

  对格里高利历有 ：A = INT（Y/100）   B = 2 - A + INT(A/4)

  对儒略历，取 B = 0

  要求的儒略日即为：JD = INT(365.25(Y+4716))+INT(30.6001(M+1))+D+B-1524.5 （7.1）

  使用数值30.6取代30.6001才是正确的，但我们仍使用30.6001，以确保总能取得恰当的整数。事实上可用30.601甚至30.61来取代30.6001。例如，5乘30.6精确等于153，然而大多数计算机不能精确表示出30.6(参见第二章关于BCD的说明)，这导致得出一个152.999 9998的结果，它的整数部分为152，如此算出的JD就不正确了。

例7.a：计算1957年10月4.81日，即苏联发射第一颗人造卫星的日期相应的儒略日。

这里我们有 Y =1957，M = 10，D = 4.81。因 M > 2，则Y与M不变.

日期为格里高利历，于是算得：

A = INT(1957/100) = INT(19.57) = 19

B = 2-19+INT(19/4) = 2-19+4 = -13

JD = INT(365.25*6673)+INT(30.6001*11)+4.81-13-1524.5 = 2436116.31

例 7.b：计算333年1月27日12时相应的儒略日。

因 M = 1，有 Y = 333 -1 =332 且 M = 1 +12 =13；又因日期为儒略历日期，故 B = 0

JD = INT(365.25*5048)+INT(30.6001*14)+27.5+0-1524.5=1842713.0

下表列出了一些历日所对应的儒略日，可作测试程序之用。
 2000年 1月 1.5日 2451 545.0
 1987年 1月27.0日 2446 822.5
 1987年 6月19.5日 2446 966.0
 1988年 1月27.0日 2447 187.5
 1988年 6月19.5日 2447 332.0
 1900年 1月 1.0日 2415 020.5
 1600年 1月 1.0日 2305 447.5
 1600年12月31.0日 2305 812.5
  837年 4月10.3日 2026 871.8
-1000年 7月12.5日 1356 001.0
-1000年 2月29.0日 1355 866.5
-1001年 8月17.9日 1355 671.4
-4712年 1月 1.5日 0.0

·如果你只对1900年3月1日至2100年二月28日之间的日期感兴趣，那么在公式（7.1）中可取B = -13。

·在一些应用中需要知道某一给定年1月0.0日的儒略日JD0，它与上一年的12月31.0日是同一日。对格里高利历中的年份可按如下计算。

Y = year-1，  A=INT(Y/100)

JDo=INT(365.25Y)-A+INT(A/4)+1721424.5

特别地，对1901年至2099年间的年份，上式简化为：JDo=1721409.5+INT(365.25*(year-1))

闰年是如何设定的？

在儒略历中，能被4整除的年份为闰年，这一年有366天，其它年份为平年（365天）。

如900年和1236年为闰年，而750年和1429年为平年。

格里高利历法也采用这一规则，但下列年份除外：不能被400整除的百年为平年，如1700年，1800年，1900年和2100年。其余能被400整除的百年则为闰年，如1600年，2000年和2400年。

“修正儒略日”

  现代工作中有时会用到修正儒略日（Modified Julian Day, MJD），比如在提到人造卫星轨道根数时。对比儒略日，修正儒略日从格林威治时间平午夜开始计算，相当于：

  MJD = JD – 2400000.5

  因而MJD = 0.01指向的是1858年11月17日世界时0时。

由儒略日推算历日

下面的方法对正数年和负数年都是有效的，负儒略日数除外。

将JD加上0.5，令 Z 为其整数部分，F 为尾数（小数）部分。

若 Z < 2299161，取A = Z

若 Z 大于等于2299 161，计算 α=INT((Z-1867216.25)/36524.25) ，A=Z+1+α-INT(α/4)

然后计算
B = A+1524
C = INT((B-122.1)/365.25)
D = INT(365.25C)
E = INT((B-D)/30.6001)

该月日期（带小数部分）则为：d = B - D - INT(30.6001E) + F

月份m为：

  IF E < 14 THEN m = E – 1；

  IF E=14 or E=15 THEN m = E – 13

年份为y：

  IF m>2 THEN y = C – 4716

  IF m =1 or m=2 THEN y = C – 4715

  和公式(7.1)的情况一样，这个公式里求E时用的数30.6001不能代之以30.6，哪怕计算机没有先前所说的问题。否则，你得到的结果会是2月0日而不是1月31日，或者4月0日而不是3月31日。

例 7.c：计算JD 2436 116.31所对应的历日。

2436 116.31 + 0.5 = 2436 116.81

Z = 2436 116 且 F = 0.81

因 Z > 2299 161，故有：α = INT((2436116-1867216.25)/36524.25) = 15，A = 2436116+1+15-INT(15/4) = 2436129

于是我们求得：B = 2437653， C = 6637，D = 2437313， E = 11

该月日期 = 4.81

月份 m = E – 1 = 10 (因 E < 14 )

年份 = C – 4716 = 1957 (因 m > 2 )

因此，求得的日期为1957年11月4.81日。

练习：计算JD = 1842 713.0 和 JD = 1507 900.13 所对应的历日。答案：333年1月27.5日 和 -584年5月28.63日。

给定日期间的相隔天数

两个历日间的相隔天数可以通过计算它们相应的儒略日之差求得。

例 7.d — 周期彗星哈雷于1910年4月20日及1986年2月9日两次过近日点。这两次经过的时间间隔是多少？

1910年4月20.0日对应 JD 2418 781.5

1986年2月9.0日对应 JD 2446 470.5

其差值为27 689天。

练习：1991年7月11日之后恰相隔10 000天的日期。答案： 2018年11月26日。

星期几的问题

  给定日期是星期几可由以下方法获得 — 计算该日0时的儒略日，加上1.5，再除以7 ，所得余数将指示出星期几：若余数为0，则为星期日，1为星期一，2为星期二，3为星期三，4为星期四，5为星期五，6为星期六。

  儒略历到格里高利历的换算并不影响星期。因而，在1582年，10月4日星期四接下来的一天便是10月15日星期五。

例 7.e：找出1954年6月30日是星期几。

1954年6月30.0日对应 JD 2434 923.5

2434 923.5 + 1.5 = 2434 925

2434 925除以7所得的余数为3.

所以这一天是星期三。

年内的序数日

年内的序数日 N 可由以下公式得出：N = INT(275M/9) - K*INT((M+9)/12) + D - 30

此处 M 为月份，D为该月日期，闰年 K = 1，平年 K = 2

N取整数，自1月1日开始取值1，直至12月31日取值365（或闰年取值366）。

例 7.f 1978年11月14日。

平年 K=2，M = 11, D = 14, K = 2。得 N = 318

例 7.g 1988年4月22日。

闰年 K=1， M = 4， D = 22，K = 1。得 N = 113.

现在让我们考虑逆问题： 年内序数日N已知，要求相应的日期，M为月份，D为该月日期。下面的算法是由比利时民间天文协会的A. Pouplier发现的。

如上所述，令
K = 1 若为闰年
K = 2 若为平年
M = INT(9(K+N)/275+0.98)，若 N < 32 ，则令 M = 1
D = N – INT(275M/9) + K*INT((M+9)/12) + 30

参考书目

1、《Almanac for Computers for the Year 1978》第B2页，特区华盛顿，美国海军天文台，航海天文年历办公室。

2、A. Pouplier致Jean Meeus的信件， 1987年4月10日。




