第29章:开普勒方程



  有多种方法计算星体(行星、小行星、慧星)在某一给定时刻的绕日运动轨道上的位置。
    —— 数值积分法,此法已超出本书讲述的范围。
    —— 使用第31章的方法,计算一些周期项的和,进而获得星体的黄道坐标。
    —— 利用第32章的方法,从星体的轨道要素计算出星体的位置。
  其中,使用最后一种方法,我们需找出星体的真近点角。可以通过球解开普勒方程得到,也可以使用序列表达式得到(见第32章的"中心方程")。



  图1表示半个椭圆轨道，太阳在椭圆的焦点S上，椭圆的另一个焦点是F。直线AP是长轴。C是远日点A与近日点P之间的中点，也是F与S的中点。
  假设某一时刻，移动的星体位置在K点，那么SK就是此刻天体的径向量，记为r，它的单位是天文单位。真近点角(v)是角KSP，它是从日心看，天体移动的角度(从近点起算)。半长轴CP通常表示为a，单位是天文单位。轨道的离心率e=CS/CP，对于椭圆，e介于0到1之间。近日距离和远日距离通常分别表示为q和Q。在近日点，v=0°，r=q，在远日点v=180°，r=Q。因此有以下公式：
    距离CS = ae
    距离SP = q = a*(1-e) 近日点距离
    距离SA = Q = a*(1+e) 远日点距离
    距离PA = 2a =q+Q
  现在我们考虑图2中的虑构的行星或慧星K'，它的轨道是围绕太阳的圆，做均速运动，周期与真行星或慧K相同。同是假设，虑构天体在P'(该点在SP上)时，真天体在P点。过一段时间后，虚天体在K'点，真天体在K点，那么此刻v=∠PSK称为真近点角，M=∠PSK'称为平近点角。




  换句话说，平近点角指把星体看作均速圆周运动时，星体到近点的角距离。
  由以上定义，不难发现，当星体在近点时，M=0°，当真星体绕日一周时，M=360°。
  如果已知平近点角M和离心率e，要如何求真近点v呢？除了第32章的使用周期序列的方法，还有一种方法就是求解开普勒方程。
  在这个问题上，我们需引入一个辅助角E，称为偏近点角。它的几何定义见图1。虚线圆的直径是AP，做辅线KQ垂直AP，角PCQ就是偏近点角。
  当星体在近日点时，v、E、M都是0°，在近点附近，真星体移动速度最快，快于平近点角。星体从近点移到远点的过程中，v>M，以因为M始终介于v和M之间，所以有0°<M<E<v<180°，在远日点M=E=v=180°，在回到近点的过程中，v<M。
  当E已知，v可获得：
    tan(v/2) = sqrt((1+e)/(1-e))*tan(E/2) ……29.1式
  这样，径矢r可由以下任一表达式算出：
    r = a*(1-e*cos(E))          ……29.2式
     r = a*(1-e*e)/(1+e*cos(v))  ……29.3式
    r = q*(1+e)/(1+e*cos(v))    ……29.4式
  接下来我们来考虑求偏近点角E的问题。
  开普勒方程是：
    E = M+e*sin(E)  ……29.5式
  这个方程要求角的是E，但这是个超越方程，不能真接求解。我们将解释三种迭代法球E，最后还给出一个近似求E的公式。

第一种方法：
  式29.5的M、E应表达为弧度单位。大多数程序设计语言都使用弧度制。如果使用角度模式计算正余弦值，那么e应乘上π/180，令乘上这个数以后的e为eo，那么开普勒方程变为：
    E = M+eo*sin(E) ……29.6式
  这样，我们就可用“角度”来计算了。
  为了解29.6式，选找一个适当的E的估值，那么通过29.6式计算后，将得到一个更精确的E的新估值。重复以上计算，直到获得所需的精度为止。这一计算过程可利用计算机自动进行。E的初始估值可以使用E=M，由此得运算过程如下：
  E0 = M
  E1 = M + e*sin(E0)
  E2 = M + e*sin(E1)
  E3 = M + e*sin(E2)
  ……
  E0、E1、E2、E3…，逐个精度不断提高。

  例29.a ——计算开普勒方程，e=0.100，M=5°，精度要求0.000001度。
  先计算eo
    eo = 0.100*π/180 = 5°.72957795
  则开普勒方程变为
    E = 5 + 5.72957795*sin(E)
  式中全部使用角度制计算。起步E=M=5°，这样就取得如下E的过程值
    5.499366
    5.549093
    5.554042
    5.554535
    5.554584
    5.554589
    5.554589
  因此，所需的结果是E = 5°.554589
  这种方法非常简单并总是收敛的。当e比较小时，基本没问题。然而，迭代次数是随首e的增加而增加的。例如，e=0.990，M=2°时，迭代过程中E的值如下：
  2.000000   15.168909   24.924579   29.813009
  3.979598   16.842404   25.904408   30.200940
  5.936635   18.434883   26.780556   30.533515
  7.866758   19.937269   27.557863   30.817592
  9.763644   21.341978   28.242483       …
 11.619294   22.643349   28.841471
 13.424417   23.837929   29.362399
  在进行了50次迭代后，结果是32°.345452，仍达不到正确值32°.361007，误差还大于0.01度。
  图3表示计算精度为10^-9度时，所需的迭代次数三维图，底面坐标是离心率e和平近点角。


  我们看到，当e接近1时，平近点角在0度到180度范围时，所需的迭代次数很大。
  我们注意到，图的底部有一个直线“谷”。这个“谷”线是：点（e=0，M=90°）到点（e=1,M=π/2-1=32°42')，这就是说，对于给定的e，存在一个特殊的平近点角Mo，计算它时所需的迭代次数最小：
  Mo=π/2-e,单位弧度。
  当M偏离Mo(在“谷”的两边)，迭代次数增加。例如：e=0.75时Mo=47.03度，要达到0.000001度所据的迭代次数是：
  M    次数         M     次数
  5°       51          60°         11
  10°      37          70°         12
  20°      23          90°         21
  30°     15         110°         32
  40°       9         130°         43
  47°       5         150°         54
  55°       8         170°         59
  一个有趣的事实是，当M介于Mo与180度时，迭代过程中E的值在真值附近振动。例如：e=0.75，M=70°,迭代计算结果如下：
  70°.000000  起始值
  110.380316   偏大
  110.281870   偏小
  110.307524   偏大
  110.300850   偏小
  110.302587   偏大
  110.302135   偏小
  ……

第二种方法：
  当轨道离心率e大于0.4或0.5时，第一种方法收敛速度很慢，可以考虑更好的迭代公式：
    E1 = E0 + (M + e*sin(E0) - E0) / (1 - e*cos(E0)) ……29.7式
  式中E0是上一次迭代取得的值。在这个公式中，M,E0及E1均为弧度。如果要用角度单位计算，式中的e应换为eo=180*e/π。
  使用该式，任需多次迭代。
  请注意一下29.6式与29.7式的不同。前者直接算出迭代修正后的的E1，后者则由两部分购成，即E0和修正量组成，二者之和就是修正后的E1。
  起步：E0=M=5°，得到以下计算过程：
         E0                  修正量                 E1
    5.000000000     +0.554616193     5.554616193
    5.554616193     -0.000026939     5.554589254
    5.554589254     -0.000000001     5.554589253
  在这种情况下，三次迭代就可达到0.000000001的精度。
  我们求角不同e和M的开普勒方程，见表29.A，第1列是e，第2列是近点角M，第3列是正确的E，第4列和第5列分别是用第一种方法和第二种方法计算所需的迭代次数。起步估值为E=M。计算时取12位有效位数，一直迭代到比上一次值的差值小于0.000001度为止。
      表29.A
--------------------------------
  e     M     E        (1)   (2)
--------------------------------
 0.1    5°  5.554589    6     2
 0.2    5    6.246908    9     2
 0.3    5    7.134960   12     2
 0.4    5    8.313903   16     2
 0.5    5    9.950063   21     2
 0.6    5   12.356653   28     3
 0.7    5   16.356653   39     3
 0.8    5   22.656579   52     4
 0.9    5   33.344447   58     5
 0.99   5   45.361023   50    11
 0.99   1   24.725822  150     8
 0.99  33   89.722155    6     5
--------------------------------
  很明显，不管是第一种方法还是第二种方法，一般说e的值越大，所需的迭代次数越多。但第二种方法是这三种方法中所需迭代次数最少的。当e<0.3时，第一种方法是最好的，因为我们更喜欢第一种简单的迭代公式（迭代次数仅5—10），而不喜欢第二种复杂的公式（虽然他仅需迭代2次）。仅当e的值比较大时，才考虑使用第二种方法。
  在某些情况下，第一种方法可能失效。见上表中的最后第二行，当e=0.99，M=1度时，所需的迭代次数至少是150次。
  最后，表29.A显示，对于给定的精度要求，所需的的迭代次数不完全依靠e和M，仍然存在某些奇异问题，从表中的最后两行看，在e已非常接近1时，第一种方法却仅需迭代仅需6次。
  虽然公式29.7支持很大的离心率e，但仍可能出问题，在HP-85电脑上，我们处用公式29.7执行了一些计算，每次计算时，起步值为E=M。表29.B给出了三种情况下E逐步求精的过程，E的单位是度。
      表29.B
---------------------------------------------------
 e=0.99  M=2°              e=0.999  M=6°          e=0.999  M=7°
-------------      --------------    --------------
 188.700250865      930.352114752     832.86912333
 90.0043959725      418.384869795     275.954959759
 58.7251974236     -345.064633754    -87.610596019
 41.762008288       10182.3247508    -48.5623921307
 34.1821261793      1840.68260539    -11.225108839
 32.4485414136     -5573.41581953     340.962715254
 32.361223124      -2776.37618814    -5996.93473678
 32.3610074734     -478.97469399     -2079.96780001
 32.3610074722     -185.902957505     511.49423506
 32.3610074722     -86.6958017962     257.391360843
                   -48.9711628749     5.969894505
                   -14.7148241705     1094.05946279
                    168.189220986    -33606.763133
                    92.1098260913    -12599.3759885
                    64.2252288664     11889243.763
                    52.7106850572     3642203.90477
                    49.7106850572    -432120.48862
                    49.5699983807    -145379.711482
                    49.5696248567     142691.415319
                    49.5696248539     56806.8295471
                                      ……
---------------------------------------------------
  在第一列中(e=0.99，M=2度），起步为E=2度。第一次迭代得到E=188.7度，偏离正确解太远了。但下来的迭代值90度、59度、42度，之后就速迅收敛了。当到了第8次迭代，精度就达到了0.00004角秒。
  在第二列中(e=0.999，M=6度)，首次迭代得到了一个十分异常的值，几乎是个随机的突变值。刚开始始基本无法收敛，直到第13次迭代（值为168度），才开始快速收敛。
  在第三列中(e=0.999，M=7度)，前20步跟本不收敛，直到47步（表中未给出）才得到正确值52.2702615。
  在同的e=0.999，却有显著的不同，把M=7度，换为M=7.01度，则只需迭7次就可得到正确的E。
  HP-85计算机的有效位数是12位。如果使用其它计算机，迭代次数则有所不同。用HP-67计算机（只有10有效数字）同样计算表中的第二列情况（e=0.999，M=6度），迭代过程如下：
     930.3621195
     418.3848584
    -345.0649049
   10182.69391
    1883.665232
    -162.6729360
     -85.06198931
     -47.82386405
     -13.18454655
     211.0527629
      84.65261970
      60.76546811
      51.35803706
      49.62703439
      49.56968687
      49.56962485
      49.56962485
  与29.B表作个有趣的对比。在第三次迭代后，它与HP-85的计算的差值仅0.00027度，下一次迭代，差值达0.37度，再下一个达43度。不过，最终还是收敛了。
  显然，当e很大时，公式29.7只保证局部收敛。当e很大时，迭代过程中，E随机的在正确值前后跳变，仅当有机会跳入“正确值附近”，然后才开始收敛。
  图4是一个三维图形，表示计算精度要求为10^-9度时利用29.7式所需的迭代次数，底面坐标为离心率e和平近点角。和以前的一样，起步计算时E=M。图中左边的角落，e=1，M=0度，这是个危险区域，图5则放大显示了该曲域。我们看到很多密集的高峰，e或M的微小变化将造成达到所需精度的迭代次数大为不同。




  因此，当e很大M很小时，使用式29.7是非常让人担心的。在某些情况下，计算过程中有溢出的危险，因为分母的数有可能非常接近于0。
  这个问题可通过适当选择M的值来解决，一个良好的M的值由Mikkola找到了（式中为弧度单位）：
    α = (1-e)/(4*e+0.5)       β = M/(8*e+1)
    z = sqrt3(β±sqrt(β*β+α^3))，式中sqrt3表示开3方,α^3表示α的3次方
  式中的±号选择与β的正负号相同。注意：立方根下的数值可能是负数，造成电脑计算出错，此问题读者可自行解决。
  接下来计算：   so = z-α/2          s = so - 0.078*so^5/(1+e)
  那么，公式29.7的更好的起步值是：
    E = M+e*(3*s - 4*s^3) ……29.8式
  这一计算适用于上述的“危险区域”，也就是|M|<30度，且0.975<e<1时。在范围之外，起步值使用E=M即可。
  图6表示：使用29.7公式计算，起步使用29.8式，为了达到10^9次方精度时所需的迭代次数。
 
  第三种方法：
  Roger Sinnott设计了一种使用二分法求解E的方法。二分法在第5章已经提到。这个过程是绝对可靠的，当是e=0到1的任意数，它总能收敛到机器所能支持的精度。以下的程序中E表示轨道的离心率，M是平近点角，单位是弧度。程序的结果是偏近点角，单位也是弧度。
  要得到10位精度，需二分33次。在16位的BASIC语言中，程序的行号为180的那个循环语句，可增加为53次。最小循环次数要求是：3.32乘以所需的精度位数，其中3.32=1/log10(2)。
  100 PI=3.14159265359
  110 F=SGN(M) : M=ABS(M)/(2*PI)
  120 M=(M-INT(M))*2*PI*F
  130 IF M<0 THEN M=M+2*PI
  140 F=1
  150 IF M>PI THEN F=-1
  160 IF M>PI THEN M=2*PI-M
  170 E0=PI/2 : D=PI/4
  180 FOR J=1 TO 33
  190 M1=E0-E*SIN(E0)
  200 E0=E0+D*SGN(M-M1) : D=D/2
  210 NEXT J
  220 E0=E0*F

  第四种方法：
  公式：tan(E) = sin(M) / (cos(M) -e ) ……29.9式
  它可计算E的近似值，并且仅当e的值比较小时才是有效的。
  与例29.a的数据一样，用29.9式得到
    tan(E) = 0.08715574/0.89619470 = 0.09725090
  即E=5.554599度，准确值是5.554589，所以此时误差仅0".035。但在相同离心率时，M=82度，误差约为35"。
  使用29.9式的最大误差是
    e=0.15时  0.0327度
    e=0.20时  0.0783度
    e=0.25时  0.1552度
    e=0.50时  1.42度
    e=0.99时  24.7度
  对于地球，e=0.0167，误差将小于0".2。在这种情况下，公式29.9是可以被安全使用的，除非精度要求很高。
