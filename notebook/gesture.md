##基于手形特征的静态手势识别

###基本流程
![](https://github.com/hayifeng/Copter_Robot_ImageProcessing/raw/master/pictures/静态手势识别基本流程.png)
###一、灰度化处理

```cpp
void cvtColor(){
	Mat srcImg = imread("angelababy.jpg");
	Mat dstImg;

	cvtColor(srcImg,dstImg,CV_BGR2GRAY);	//BGR->GRAY
	cvtColor(srcImg,dstImg,CV_BGR2HSV);		//BGR->HSV

	namedWindow("before");
	namedWindow("after");
	imshow("before",srcImg);
	imshow("after",dstImg);
	waitKey();
}
```

###二、滤波（ 图像平滑化）

###三、灰度直方图

###四、图像二值化

###五、边缘检测

###六、轮廓提取

###七、手势特征提取

###八、手势分类识别
