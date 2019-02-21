# 从全球坐标系统到uber h3

## 一、 引言

## 二、全球坐标系统
### 1 坐标系
人们对地理位置表达的探索从来没有停止过，通常对于空间位置我们可以通过空间坐标系来对位置进行唯一的表达，最常用的空间坐标系有三种：
* 空间直角坐标系
* 柱面坐标系
* 球坐标系

根据不同的用途，选择相应的坐标系来表达空间位置。如下图，设M为空间内一点，其直角坐标为M(x,y,z)，点M在xoy面上的投影P的极坐标为r,θ，则r,θ,z就叫点M的柱面坐标。
![直角坐标系和柱面坐标系](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/342ac65c1038534304e1d15d9313b07eca8088a4.jpg)
球坐标系(r,θ,φ)定义了球体，它以坐标原点为参考点，由方位角、仰角和距离构成。如下图所示，即是一个球坐标系，r为距离，θ为仰角，φ为方位角。
![球坐标系](https://raw.githubusercontent.com/sadnessly/MarkdownPhotos/master/pic/86c0460e2f881850a75eac2f5e0b7d07.png)
同时，三种坐标系可以相互转换，如直角坐标和球坐标之间的转换：
* 直接坐标转球坐标
$${r}=\sqrt{x^2 + y^2 + z^2}$$

$${\theta}=\arctan \left( \frac{\sqrt{x^2 + y^2}}{z} \right)=\arccos \left( {\frac{z}{\sqrt{x^2 + y^2 + z^2}}} \right)$$

$${\phi}=\arctan \left( {\frac{y}{x}} \right) $$

* 球坐标转直角坐标

$$x=r \sin\theta \cos\phi$$

$$y=r \sin\theta \sin\phi$$

$$z=r \cos\theta$$

### 2 地球坐标系
对于地球，地球的形状类似于一个椭球体，因此主要使用的坐标系则是直角坐标系和球坐标系。
#### （1）地球直角坐标系
地球直角坐标系的定义是：原点O与地球质心重合，Z轴指向地球北极，X轴指向地球赤道面与格林尼治子午圈的交点，Y轴在赤道平面里与XOZ构成右手坐标系。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/7a899e510fb30f24acc736fbc295d143ac4b03ed.jpg)
#### （2）地球大地坐标系
除了直角坐标外，由于地球是类球体，因此球坐标也是表达地球位置的直观和简洁的方式。地球大地坐标系就是一种特殊的球坐标系。由于人类生活在地球表面，无需表达地球内部的点，因此仅需要表达地球球面上的点。如下图我们可以想象，若地球是一个标准的球体，地球半径是一个固定值，因此只用方位角和仰角即经度和纬度就可以对地球表面的位置进行表达。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d02.png)
但是实际上地球的形状并非一个标准的球体，其实际形状类似于这样：
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/v2-ac5458d366778d818ab572b30c7ca0dd_hd.jpg)
因此除了需要经纬度外，还需要一个距离来表达。地球大地坐标系则是用来表述地球上点的位置的一种地区坐标系统。它采用一个十分近似于地球自然形状的参考椭球作为描述和推算地面点位置和相互关系的基准面。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-155357@2x.png)
大地纬度、大地经度和大地高分别用大写英文字母B、L、H表示。沿法线至椭球面的距离为该点的大地高。
目前常用的也是全球定位系统使用的大地坐标系是WGS 84参考系。WGS84包含一套地球的标准经纬坐标系、一个用于计算原始海拔数据的参考椭球体，和一套用以定义海平面高度的引力等势面数据。


###3 地图投影
当我们需要在纸面或者屏幕上显示地球时，就需要将三维的球体转换为二维的平面，即将地球球面坐标转化为平面坐标。简单的说投影坐标系是地理坐标系+投影过程。
投影所需要的必要条件是：
* 任何一种投影都必须基于一个椭球（地球椭球体）
* 将球面坐标转换为平面坐标的过程（投影算法）。

对于球体来说，不能直接将球面完整和准确的展开在平面上，因此若要将地球展现在二维平面上，就需要某些损失精确度的方式来表达。因此需要用投影的方式对地球进行展示。投影顾名思义，是用光线照射物体，在某个面上得到的影子，即把地球表面的任意点，利用一定数学法则，转换到地图平面上的理论和方法。书面概念化定义：地图投影就是指建立地球表面上的点与投影平面上点之间的一一对应关系的方法。即建立之间的数学转换公式。它将作为一个不可展平的曲面即地球表面投影到一个平面的基本方法，保证了空间信息在区域上的联系与完整。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d04.png)
然而对球表面进行投影就会带来一定的精度损失，如下图所示，这个投影过程将产生投影变形，而且不同的投影方法具有不同性质和大小的投影变形。根据投影变形的性质主要将变形分为面积、角度、长度。根据不同地图的绘制需求，选择相对合适的投影，保证地图的主要使用用途不因为变形而造成不可用。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d05.png)
####（1）投影分类
根据投影面形状、位置等对地图投影进行分类：
* 投影面和地轴的关系：
1 正轴投影（投影面的中心线与地轴平行）
2 斜轴投影（投影面的中心线与地轴斜交）
3 横轴投影（投影面的中心线与地轴垂直）
* 投影面形状：
1 圆锥投影 （投影中纬线为同心圆圆弧，经线为圆的半经）
2 圆柱投影 （投影中纬线为一组平行直线，经线为垂直于纬线的另一组平行直线，且两相邻经线之间的距离相等）
3 方位投影 （投影中纬线为同心圆，经线为圆的半径，且经线间的夹角等于地球面上相应的经差）
此外，还有伪圆锥投影，伪圆柱投影，伪方位投影，多圆锥投影等
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d06.png)

* 投影面和地球面的关系：
1 切投影 (投影面和地球球面相切)
2 割投影 (投影面和地球球面相割)
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-164851@2x.png)

如何将三维球体在变形较小的情况下表现在二维平面上就是相对困难的问题。常用的转换方式，比如将球体投影在圆柱、圆锥或是平面上，且根据所需不同的位置经度要求，可以选择变形相对较小的方式进行投影。如下图中的正轴圆柱投影（即墨卡托投影）在赤道附近的变形最小，即可以用此种投影表示赤道赤道附近的地区，这样的变形最小。而用这种投影方式表示地球两极不合适，会有很大的变形。
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-164536@2x.png)

用我们平时用到的电子地图举例（图自https://thetruesize.com）
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/6309329-dc454555912d15c8.png)
如果将中国移动到俄罗斯的位置,中国的面积会变得比原先大很多
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/6309329-bfe9191ded07ff65.png)

####(2) 球心投影
球心投影是方位投影之一。以球心O为投射中心，把球面上的P点投射到它的切平面上的投影法。它是最有用的投影方法之一，17世纪中叶开始使用。它能把球面上的大圆，投射成直线。常用于导航、测绘航线、寻找星座与星体。还可用来制作日晷，因此亦称日晷投影。而平面与球体有且仅有一个切点，将地球表面上的点投影在平面上。如下图，若计算球心点到地图的距离，则有计算公式：
$${\displaystyle r(d)=R\,\tan {\frac {d}{R}}}$$

R为球心到切点的距离，即球半径，而d代表球面上的两个点的球面距离，r为这两个点投影在平面的真实距离。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d08.png)

这种投影，形状变形从中心向外逐渐增大；距中心点 30 度范围内的变形较小。面积变形随距中心距离的增加而增大；以中心点为圆心 30 度半径范围内的变形较小，从中心向外，方向都是准确的。Uber H3的20面体投影即使用了球心投影作为其投影方式，中心点到最大顶点的角度为37度，变形相对较小。
