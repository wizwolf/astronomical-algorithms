第40章 行星圆面被照亮的比例及星等



  从地球上看，行星圆面被照亮部分的比例，可由下式计算：

  k = ( 1 + cos i )/2    (40.1)

  式中i是相位角，它由下式计算：

  cos i = ( r2 + Δ2 - R2 ) / (2rΔ)

  式中r是行星到太阳的距离，Δ是它到地球的距离，R是日地距离，全部使用天文单位。

  联立这两个公式，得：

  k = ( (r+Δ)2 - R2 )/(4rΔ)      (40.2)

  如果行星的位置已经使用第32章的“第一种方法”得到，那么我们有(使用原来的符号)：

  cos i = ( R - Ro cos B cos (L - Lo) )/Δ      (40.3)   或者

  cos i = ( x cos B cos L + y cos B sin L +z sin B )/Δ    (40.4)

  行星被照亮的边缘的中心的位置角，可以使用第51章月亮的计算方法。

例40.a ——计算1992年12月20日0h TD，金星圆面被照亮部分的比例。

  在“例32.a”中，我们已得到该时刻的参数：

  r = 0.724604 (原处是R)， R = 0.983824 (原处是Ro)， Δ = 0.910947

  因此，利用公式(40.2)，k=0.647。

  或者，使用“例32.a”中的：Lo和Ro(来自A式)，L、B、R(来自B式)，x、y、z(来自C式)，及Δ=0.910947，再利用公式(40.3)和(40.4)，这两式均得到cos(i)=0.29312，因此k=0.647，与上面的相同。

-----------------------

  对于水星和金星，k的值在0到1之间。对于火星，k的值从不小于0.838(大约)。对于木星，相位角i总是小于12度，因此k的值在0.989到1之间变化。对于土星，i的值总是小于6.5度，所以从地球上看，该行星的k值仅在0.997到1之间变化。

-----------------------

  在金星的情况下，k可以使用以下方法估算。

  利用公式(21.1)计算出T。那么：

  V = 261°.51 + 22518°.443T

  M = 177°.53 + 35999°.050T

  M'=  50°.42 + 58517°.811T

  W = V + 1°.91 sin M + 0°.78 sin M'

Δ2 = 1.52321 + 1.44666 cos W (Δ>0)

  k = ( (0.72333+Δ)2 - 1 )/(2.89332Δ)

  另外，金星距角ψ的估值是：cosψ = (Δ2 + 0.4768)/(2Δ)

例40.b —— 和例40.a一样，但我们现在使用上面描术的估算法。

  我们依次得到：



  正确的值参见“例40.a”，是0.647。

--------------------------

行星的星等

  从地球上看，某时刻行星的视(恒星)星等依赖于：行星到地球的距离Δ、它到太阳的距离(r)以及相位角(i)。对于土星，星等还与土星环的状态有关。

  G.Muller的公式基于1877到1891年的观测，曾在天文年历中使用多年。以下是可视星等的数值表达：



  式中i的单位是度；r和Δ的单位是天文单位，对数计算是以10为底的。对于土星，ΔU和B与土星环有关，在第44章中定义；注意，ΔU和B应为正值，ΔU单位是度。(做为估算，相位角i可能用ΔU替换)。

  当然，Muller的表达式并不完美。例如，对于木星，没有考虑相位角效果。土星的公式中，在阳的地平纬度B'在行星环之上没有考虑；当B和B'符号相反，环的暗的一边朝向地球，但Muller没有考虑这种情况。

  在任何情况下，这样计算的星等应舍入到0.1，舍入到0.01是没有意义的。例如，火星本来的亮度的差异可达0.3星等，火星的一些区域的暗纹比其它区域多，所以一些行星的亮度与它们朝向我们的表面有关。极帽变化和较大的沙尘暴也会影响星等。对于木星和土星，还有变化的大气现象等。

例40.c ——1992年12月20.0 TD 金星的星等。

  从例40.a，我们有：r = 0.724604， Δ = 0.910947， cos i = 0.29312

  因此 i=72.96度。

  由Muller的金星公式得：星等 = -3.8。

例40.d —— 1992年12月16.0 TD 土星的星等。

  从例44.a，我们有：r = 9.867882， B = 16.442度， Δ = 10.464606，ΔU = 4.198度

  由Muller的土星公式得：星等 = +0.9。

------------------------

  自从1984年，美国《天文年历》使用了其它计算行星可视星等的公式，并申明这些新的表达式是“D.L.Harris建立的”。事实上，在他的论文[3]中，Harris并没有提供新的表达式。

  对于水星和金星，Harris(其论文的第277和288页)只是提到表达式是法国天文学家A.Danjon推导的。Harris讲到绝对星等和相位系数的值是他人创建的，而他自已并没有打算或给了新的表达式。

  如果r、Δ(天文单位)、i(度单位)与前面所述的一样，1984年开始，《天文年历》使用的新的表达式是：



  小行星的星等详见第32章。

参考资料

1、《天文历书的补充解释》(伦敦，1961)，第314页。
2、1984年《天文年历》(华盛顿)，第L8页；以及以后的卷。
3、Danjon Harris，"行星及某某星(原文看不清)的光度测量和色度测量"，第8章(第272ff页)...(原文看不清)