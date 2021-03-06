第27章 时差

  [许剑伟 于家里 2008年4月21日]

  由于轨道离心率以及月球及行星的摄动，造成地球的的日心黄经不是均匀变化的，所以太阳在黄道上运行不是均速的。另外，太阳在黄道上运动而不是在天赤道上运动。由于这两个原因，造成太阳的赤经也不是均匀变化的。

  我们可以假想一个太阳(第一假想太阳)沿道黄道均速运动，并且在近地点和远地点与真太阳重合。我们再假想一个太阳(第二假想太阳)沿道天赤道均速运动，并且在分点处与前面那个假想太阳重合。第二假想太阳叫做平太阳，从定义得知它的赤经增加的速度是均匀的，这就是说，平太阳运动没有周期项，但含有长期项τ2、τ3...

  当平太阳经过观测者的子午圈时，是平正午，当真太阳经过子午圈是真正午。“时差(时间方程)”是视时间与平时间的差，换句话说，它是真太阳与平太阳的时角。

  根据以上定义，给定时刻的时角由下式计算：

  E = Lo - 0°.0057183 - α + Δψ·cosε  (27.1)

  式中，Lo是太阳平黄经。根据VSOP87理论(见第31章)，我们有以式(单位是度)：

  Lo = 280.4664567 + 360007.6982779τ + 0.03032028τ2 + τ3/49931 - τ4/15299 - τ5/1988000    (27.2)

  式中的τ是J2000.0=JDE 2451545.0起算的略儒千年(365250个历书日)数，Lo应化简为0到360度的值。

  在法国年历和旧的教科书中，“时差”被定义为相反的符号，因此等于平时间减去视时间。

  (译者注：赤道平太阳用赤经度量，黄道平太阳用黄经度量，根据定义，它们的起算点均是平分点。由于赤道平太阳与黄道平太阳的运动速度相等，黄道平太阳黄经等赤道平太阳赤经，黄道平太阳黄经就是我们所说的太阳平黄经。时差 = 赤道平太阳的赤经 - 真太阳赤经 = 太阳平黄经 - 真太阳赤经。当然具体计算法还应注意光行差与章动)

  在公式(27.1)中，常数0°.0057183是黄经光行差(-20".49552)与转到FK5系统的修正值(-0".09033)的和。α是以考虑了光行差和章动的太阳的视赤经。Δψ是黄经章动，ε是黄赤交角，把视赤经(Date分点起算的)的坐标参考转为Date平分点时候，Δψ*cos(ε)项是必需的，这样“视赤经”与平黄经Lo的参考点相同。



  在公式(27.1)中，如果Lo、α、Δψ的单位是度，那么“时差(时间方程)”E的单位也是度，乘以4以后则转为“分”单位。

  “时差”E的值可能是正或负。如果E>0，那么真太阳比平太阳先经过观测者的子午圈。

  “时差”E的绝对值总是小于20分。如果|E|明显太大，则应加上或减去24小时。

-------------------------------

例27.a：——计算1992年10月13日0h力学时的“时差”

  这个日期对应JDE=2448908.5，由此得到：

τ= (JDE - 2451545.0)/365250 = -0.007218343600

Lo= -2318°.192807 = +201°.807193

  从例24.b，得到该时刻的如下参数：

 α = 198°.378178
Δψ= +15".908 = +0°.004419
 ε = 23°.4401443

  因此，由公式(27.1)得：

  E = +3°.427351 = 13.70940分钟 = +13m 42s.6

----------------------------

  做为一种选择，低精度的“时差”可使用Smart提供的以下方法得到。

  E = y sin 2Lo - 2e sin M + 4ey sin M cos 2Lo - (y2/2) sin 4Lo - (5/4 e2) sin 2M    (27.3)

  式中：

  y = tan2(ε/2)，ε是黄赤交角

  Lo = 太阳平黄经

  e = 地球轨道离心率

  M = 太阳平近点角

  ε、Lo、e和M的值可分别由(21.2)、(27.2)或(24.2)、(24.4)、(24.3)得到。

  公式(27.3)得到E的单位是弧度。这个结果应转为度，然后除以15得到带小数的小时数。

-------------------------

例27.b：和上例一样，计算1992年10月13.0TD = JDE 2448908.5的“时差”。

  我们依次得到：

T = -0.072183436
e = 0.016711651
ε= 23°.44023
M = 278°.99396
Lo= 201°.80720
y = 0.0430381

  由公式27.3得到：E = +0.059825557弧度 = +3.427752度 = +13分42.7秒

--------------------------------

  “时差”在一年中的变化曲线是众所周知的，在很多天文书籍中可以找到。目前，这个曲线在2月11日达到最小值，在11月3日达到最大值，而第二极大和极小值分别发生在5月14日和6月26日。

  然而，“时差”曲线在几个世纪内逐渐变化，因为黄赤交角、地球轨道离心率以及轨道近日点黄经都在缓慢地变化。下图显示了公元前3000年到公元4000年，每间隔1000年的“时差”曲线。纵坐标每格单位是5分钟，横坐标对应E=0。横坐标每格是一个季节(3个月)，左边开始于1月。例如，我们看到，之后的2月的最小值是很深的。



  在公元1600到2100年，“时差”的极值的变化显示于表27.A。这些数据是“平”值：假设地球在黄道上做不受摄动的运动，并且没有考虑章动。

  在公元1246，太阳近地点与冬至重合，“时差”的周年变化曲线相对横轴是上下对称的：2月最小与11月最大值的绝值是一样的，5月次最大值与7月最小值的绝值也是一样的，详见表中的最后一行。



------------------------------

参考资料

1、W.M.Smart，《球面天文学》教科书；剑桥大学出版社(1956)，第149页。
