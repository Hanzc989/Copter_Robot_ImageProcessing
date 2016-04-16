#####[返回学习笔记目录](./leaning_catalog.md/#目录)
####颜色空间转换
#####颜色空间
也叫[颜色模型](http://baike.baidu.com/link?url=OPAa5xlTEK1f_zui9WWGJuk_AKQ3gtKb6H1bR2hwdd6oOO-ZNqcX5ZL5hCm_tkSAQOmVWWvVoN-6aNrAiPOQnq)，是描述使用一组值（通常使用三个、四个值或者颜色成分）表示颜色方法的抽象数学模型

#####颜色有关基本概念
* 色相(Hum)

		是色彩的基本属性，就是平常所说的颜色名称，如红色、黄色等。
		色相指的是色彩的外相，是在不同波长的光照射下，人眼所感觉不同的颜色。

* 饱和度(Saturation)

		是指色彩的纯度，越高色彩越纯，低则逐渐变灰，取0-100%的数值。

* 明度(Lightness)

		指颜色的亮度，不同的颜色具有不同的明度。比如黄色就比蓝色的明度高。
		注：颜色中明度和亮度的区别：
		亮度与物体表面的色彩反射的光量有关。而明度是一个心理颜色概念，以亮度为基础但不等同于亮度。
		从某一角度讲，明度描述色彩可能更客观。

* 对比度

		对比度是画面黑与白的比值，也就是从黑到白的渐变层次。比值越大，从黑到白的渐变层次就越多，从而色彩表现越丰富。
		对比度对视觉效果的影响非常关键，一般来说对比度越大，图像越清晰醒目，色彩也越鲜明艳丽；
		而对比度小，则会让整个画面都灰蒙蒙的。
		增加图片的对比度后，黑白反差增大。

#####OpenCV颜色空间转换函数
1、函数原型：<br>
```cpp
CV_EXPORTS_W void cvtColor( InputArray src, OutputArray dst, int code, int dstCn = 0 );
```
2、参数说明：<br>
* src	:	输入图像
* dst	:	输出图像
* code	:	颜色空间转换标示符。请参考取值列表：[enum cv::ColorConversionCodes](http://docs.opencv.org/3.0.0/d7/d1b/group__imgproc__misc.html#ga4e0972be5de079fed4e3a10e24ef5ef0)

		常用取值：
		1、RGB->Gary(RGB转换为灰度图):	COLOR_RGB2GARY	COLOR_GARY2RGB	COLOR_RGBA2GARY		COLOR_GARY2RGBA
			RGB2GARY可以记为RGB to GARY，即RGB转换为GARY，其他值的记忆方法类似。A代表alpha通道，该通道决定图像透明度。
		2、RGB->HSV:	COLOR_RGB2HSV		COLOR_HSV2RGB
		3、RGB->HLS:	COLOR_RGB2HLS		COLOR_HLS2RGB
		4、RGB->BGR:	COLOR_RGB2BGRA		COLOR_BGRA2RGBA

* dstCn	:	目标图像的通道数

		默认值为0，表示目标图像取源图像的通道数。
想深入了解颜色空间转换具体实现，可以参考：[Color conversions](http://docs.opencv.org/3.0.0/de/d25/imgproc_color_conversions.html)

3、应用举例：<br>
举一个最简单的颜色空间转换例子，将输入的彩色图转换为灰度图和HSV图。
```cpp
#include <opencv2/imgproc/imgproc.hpp>
#include <opencv2/highgui/highgui.hpp>

using namespace cv;

void main(void){

	Mat srcImg = imread("angelababy.jpg");
	Mat garyImg, hsvImg;

	cvtColor(srcImg, garyImg, CV_RGB2GRAY);		//RGB->GRAY
	cvtColor(srcImg, hsvImg, CV_RGB2HSV);		//RGB->HSV

	namedWindow("原始图");
	namedWindow("灰度图");
	namedWindow("HSV");

	imshow("原始图", srcImg);
	imshow("灰度图", garyImg);
	imshow("HSV", hsvImg);

	waitKey();
}
```
4、运行结果：<br>
![原始图](http://i3.piimg.com/2fa38040bc980230t.jpg "原始图")	![灰度图](http://i3.piimg.com/46711cda6ce58608t.jpg "灰度图")	![HSV](http://i3.piimg.com/1355fee6ba86ac8ct.jpg "HSV")
