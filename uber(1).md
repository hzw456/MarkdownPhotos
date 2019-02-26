# 全球坐标系统
## 一、引子
在电影流浪地球中，我们常常能看到这样的场景，地球在逐渐靠近木星。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190223-215940@2x.png" width="300" hegiht="200" align=center />

以及在玻璃上描绘出的地球和木星的轮廓，我们都能了解到一个常识，即地球是圆的，或者至少是类似球体的行星。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190223-221827@2x.png" width="300" hegiht="200" align=center />

可当我们再看到屏幕上全球救援队消息的时候，却发现世界地图是这样的，一个长方形的世界。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/v2-504f5b96874a21ce296295feed51ac8e_hd.jpg" width="300" hegiht="200" align=center />

这好像和我们的认知也是一样的，因为我们常看到的世界地图诸如这样

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/world5.jpg" width="300" hegiht="200" align=center />

亦或是这样，都类似长方形的地图的。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/世界地图颜色-亚洲在中心-108063303.jpg" width="300" hegiht="200" align=center />

我们还会看到下面这样的世界地图，会发现中国的形状与之前地图中的都不一样,这是为什么呢？

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/40064157-color-blank-world-map.jpg" width="300" hegiht="200" align=center />


## 二、全球坐标系统

在讲这个问题之前，先来聊一下全球坐标系统。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/v2-48aec397b3ab14d4fe1c136677783d18_hd.jpg" width="300" hegiht="200" align=center />

地理位置的重要性无需多言，与每个人的生活息息相关。如何确定空间中任意一点的位置呢？我们通过在空间中引入坐标系来确定位置。通过坐标系的标定即可获得某个点所在的地理位置。对于地球，全球坐标系统（Global Coordinate System，GCS）则是表达地球的标准坐标系统。

![直角坐标系和柱面坐标系](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/270478-3d6b5152f8b2ea08.jpg)

### 1 空间坐标系
最常用的空间坐标系有三种：
* 空间直角坐标系：
  
    也称笛卡尔坐标系，过定点O，作三条互相垂直的数轴，它们都以O为原点且一般具有相同的长度单位.这三条轴分别叫做x轴(横轴）、y轴(纵轴)、z轴(竖轴)；统称坐标轴.通常把x轴和y轴配置在水平面上，而z轴则是铅垂线；它们的正方向要符合右手规则，这样就构成了一个笛卡尔坐标。

![直角坐标系和柱面坐标系](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/a8ec8a13632762d0d57d6e89abec08fa513dc641.jpg)
* 柱面坐标系:
  
  设M(x,y,z)为空间内一点，并设点M在xoy面上的投影P的极坐标为r,θ，则这样的三个数r, θ,z就叫点M的柱面坐标。

![直角坐标系和柱面坐标系](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/342ac65c1038534304e1d15d9313b07eca8088a4.jpg)
* 球坐标系：
  
  是一种利用球坐标(r,θ,φ)表示一个点 p 在三维空间的位置的三维正交坐标系，球坐标系(r,θ,φ)定义了球体，它以坐标原点为参考点，由方位角、仰角和距离构成。如下图所示，即是一个球坐标系，r为距离，θ为仰角，φ为方位角。

![球坐标系](https://raw.githubusercontent.com/sadnessly/MarkdownPhotos/master/pic/86c0460e2f881850a75eac2f5e0b7d07.png)

同时，三种坐标系可以相互转换，如直角坐标和球坐标之间的转换：
* 直角坐标转球坐标
  
$${r}=\sqrt{x^2 + y^2 + z^2}$$

$${\theta}=\arctan \left( \frac{\sqrt{x^2 + y^2}}{z} \right)=\arccos \left( {\frac{z}{\sqrt{x^2 + y^2 + z^2}}} \right)$$

$${\phi}=\arctan \left( {\frac{y}{x}} \right) $$

* 球坐标转直角坐标

$$x=r \sin\theta \cos\phi$$

$$y=r \sin\theta \sin\phi$$

$$z=r \cos\theta$$

### 2 地球坐标系
对于地球，地球的形状类似于一个椭球体，因此主要使用的坐标系是直角坐标系和球坐标系。
#### （1）地球直角坐标系
地球直角坐标系的定义是：原点O与地球质心重合，Z轴指向地球北极，X轴指向地球赤道面与格林尼治子午圈的交点，Y轴在赤道平面里与XOZ构成右手坐标系。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/7a899e510fb30f24acc736fbc295d143ac4b03ed.jpg)

#### （2）地球大地坐标系
除了直角坐标外，由于地球是类球体，因此球坐标也是表达地球位置更直观和简洁的方式。地球大地坐标系就是一种特殊的球坐标系。方位角和仰角类比于地球的经度和纬度。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d02.png)

实际上地球的形状并非一个标准的球体，其形状类似于这样：

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/v2-ac5458d366778d818ab572b30c7ca0dd_hd.jpg)

因此除了需要经纬度外，还需要一个距离来表达。地球大地坐标系则是用来表述地球上点的位置的一种地区坐标系统。它采用一个十分近似于地球自然形状的参考椭球作为描述和推算地面点位置和相互关系的基准面。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-155357@2x.png)

大地纬度、大地经度和大地高分别用大写英文字母B、L、H表示。沿法线至椭球面的距离为该点的大地高。
通过空间坐标来我们就可以对地理位置进行唯一的表达，最常用的全球坐标就是wgs84坐标系（World Geodetic System 1984），WGS84包含一套地球的标准经纬坐标系、一个用于计算原始海拔数据的参考椭球体，和一套用以定义海平面高度的引力等势面数据。

## 三、地图投影
对于球体来说，由于表面是一个曲面，因此无法完全将球面完整和准确的展开在平面上，因此若要将地球展现在二维平面上，就需要某些损失精确度的方式来表达。如同桔子皮一般，无法展开成平面。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190222-154741%402x.png" width="300" hegiht="200" align=center />

因此当我们需要在纸面或者屏幕上显示地球时，就需要将地球球面坐标（三维）转化为平面坐标（二维）。简单的说投影坐标系是地理坐标系+投影过程。
投影所需要的必要条件是：
* 任何一种投影都必须基于一个椭球（地球椭球体）
* 将球面坐标转换为平面坐标的过程（投影算法）。

因此需要用投影的方式对地球进行展示。投影顾名思义，是用光线照射物体，在某个面上得到的影子，即把地球表面的任意点，利用一定数学法则，转换到地图平面上的理论和方法，保证了空间信息在区域上的联系与完整。如下图是不同投影方式对球体投影展开的不同方式。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190222-160212@2x.png)

然而对球表面进行投影就会带来一定的精度损失，如下图所示，由于平面不能很好的贴合地球曲面，因此这个投影过程将产生投影变形。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d05.png" width="400" hegiht="200" align=center />

### 1投影分类
如何将三维球体在变形较小的情况下表现在二维平面上呢？不同的投影方法具有不同性质和大小的投影变形。常用的转换方式，比如将球体投影在圆柱、圆锥或是平面上，且根据所需投影的位置不同，选择变形相对较小的方式进行投影。根据投影变形的性质主要将变形分为面积、角度、长度。根据不同地图的绘制需求，选择不同的投影类型，保证地图的主要使用用途不因为变形而造成不可用。根据投影面形状、位置等对地图投影进行分类：
* 投影面和地轴的关系：

        1 正轴投影（投影面的中心线与地轴平行）
        2 斜轴投影（投影面的中心线与地轴斜交）
        3 横轴投影（投影面的中心线与地轴垂直）

* 投影面形状：
  
        1 圆锥投影 （投影中纬线为同心圆圆弧，经线为圆的半经）
        2 圆柱投影 （投影中纬线为一组平行直线，经线为垂直于纬线的另一组平行直线，且两相邻经线之间的距离相等）
        3 方位投影 （投影中纬线为同心圆，经线为圆的半径，且经线间的夹角等于地球面上相应的经差）
如下图所示：

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/86c0460e2f881850a75eac2f5e0b7d06.png)

<!-- * 投影面和地球面的关系：
1 切投影 (投影面和地球球面相切)
2 割投影 (投影面和地球球面相割)
![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-164851@2x.png) -->

我们常看到的世界地图即是正轴圆柱投影（即墨卡托投影），在赤道附近的变形最小，地球两极变形最大。这实际上就解释了世界地图为什么一般都是类似长方形的，当地球投影在圆柱面上时，对表面进行展开，即是一个长方形的地图。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/WX20190220-164536@2x.png)

如下图的世界地图（图自https://thetruesize.com）可以看到北极和南极地区的变形程度非常大。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/6309329-dc454555912d15c8.png)

同时，由于中国离赤道相对于俄罗斯较近，因此变形程度较小。如果将中国移动到俄罗斯的位置,中国的面积就会变得比原先大很多。

![enter image description here](https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/6309329-bfe9191ded07ff65.png)

这就可以解释上述的另一个问题，为什么世界地图有些看起来是不一样的。选择的投影方式的不同，就会造成地图的变形程度不同。

## 下期预告
了解了以上知识后，下一篇将介绍UBER H3，其精妙的投影方式使得在兼顾投影变形小的同时，也能很方便的进行投影计算，在打车等的很多领域中使用。使用H3的六边形格子系统很方便的进行供需情况的管理，使用动态调价、司机引导等多种手段对市场进行优化。

<img src="https://github.com/sadnessly/MarkdownPhotos/raw/master/pic/image12.png" width="300" hegiht="200" align=center />

