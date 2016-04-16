#####[返回学习笔记目录](./leaning_catalog.md/#目录)
####滤波

#####一、基本概念
滤波可以用于平滑和锐化，在这里主要讨论图像平滑化，平滑滤波器的主要目的是降低噪声和模糊处理。一个比较好的去噪滤波方式是既能很好的去除噪声又不使图像的轮廓和线条模糊。<br>
滤波从空间和频率的角度主要分为两大类：空域法和频域法<br>
* 空域法

		滤波这个词最开始是用于频域处理。但是现在也可以用空间滤波器（也叫空间掩模、核、模版和窗口）直接作用于图像本身成类似的平滑
		空间滤波器组成：一个邻域（一般是一个小矩形） + 对该邻域包围的图像像素执行的预定义操作
		空间滤波执行结果：产生一个新像素，其坐标等于邻域中心，像素值是滤波操作的结果。
		平滑线性滤波器的输出是滤波器模版邻域内的像素的简单平均值。所以也叫均值滤波器，也可以归为低通滤波器。
		空域法优缺点：优点就是简单直观。另外要强调的是，典型的随机噪声是由灰度级的急剧变化组成，所以均值滤波只能降低噪声，并不能完全除去噪声。
					缺点就是，因为图像边缘也是由图像灰度尖锐变化带来的特性，所以均值滤波会导致边缘模糊的负面效应。
		*除了平滑空间滤波器以外，还有锐化空间滤波器，这里我就不介绍了，有兴趣自己去了解
		*空间域的平滑滤波一般采用简单平均法进行，就是求邻近像素点的平均亮度值。邻域大小与平滑效果直接相关，越大平滑效果越好，但是输出图像也会越模糊。

* 频域法

		滤波指接受（通过）或拒绝一定的频率分量。比如通过低频的滤波器叫低通滤波器，通过高频的滤波器叫高通滤波器。
		图像经过二维傅立叶变换后，噪声频谱一般位于空间频率较高的区域，而图像本身的频率分量则处于空间频率较低的区域内，
		因此可以通过低通滤波器的方法，使高频分量受到抑制，从而实现图像平滑
		低通滤波器：
		1、理想滤波器
		
		2、布特沃斯滤波器
		   布特沃斯滤波器有一个参数，称为滤波器的"阶数"。
		   "阶数"较高时，接近于理想滤波器
		   "阶数"较低时，接近于高斯滤波器
		3、高斯滤波器
		
		*以上三种滤波器涵盖了从非常尖锐（理想）的滤波到非常平滑（高斯）的滤波范围。后面会着重介绍一下高斯滤波器的使用。

* 注：频域滤波与线性滤波具有一一对应的关系，但不可能用于非线性滤波。<br>
      空域滤波可以提供很多功能，线性滤波和非线性滤波都有应用。<br>
      低通滤波器用于平滑，高通滤波器用于锐化。

#####二、线性滤波
`BoxBlur` `Blur` `GaussianBlur` `medianBlur` `bilateralFilter`
* 常见线性滤波器： 
	* 低通滤波器 ： 允许低频率通过
	* 高通滤波器 ： 允许高频率通过
	* 带通滤波器 ： 允许一定范围频率通过
	* 带阻滤波器 ： 阻止一定范围频率通过并且允许其他频率通过
	* 全通滤波器 ： 允许所有频率通过，仅仅改变相位关系
	* 陷波滤波器 ： 阻止一个狭窄频率范围通过，是一种特殊带阻滤波器

* 邻域算子与线性邻域滤波

		邻域算子（局部算子）：利用给定像素周围的像素值来决定此像素最终输出值的一种算子。

* 方框滤波<br>
1、函数原型：
```cpp
CV_EXPORTS_W void boxFilter( InputArray src, OutputArray dst, int ddepth,
                             Size ksize, Point anchor = Point(-1,-1),
                             bool normalize = true,
                             int borderType = BORDER_DEFAULT );
```
2、参数说明：

* 均值滤波<br>
1、函数定义：
```cpp
void cv::blur( InputArray src, OutputArray dst,
           Size ksize, Point anchor, int borderType )
{
    boxFilter( src, dst, -1, ksize, anchor, true, borderType );
}
```
* 高斯滤波<br>
1、函数原型：
```cpp
CV_EXPORTS_W void GaussianBlur( InputArray src, OutputArray dst, Size ksize,
                                double sigmaX, double sigmaY = 0,
                                int borderType = BORDER_DEFAULT );
```

#####三、非线性滤波
* 中值滤波<br>
1、函数原型：
```cpp
CV_EXPORTS_W void medianBlur( InputArray src, OutputArray dst, int ksize );
```
* 双边滤波<br>
1、函数原型：
```cpp
CV_EXPORTS_W void bilateralFilter( InputArray src, OutputArray dst, int d,
                                   double sigmaColor, double sigmaSpace,
                                   int borderType = BORDER_DEFAULT );
```
