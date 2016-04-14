####[返回](../README.md/#目录)
##基于手形特征的静态手势识别

###基本流程
![](http://i4.piimg.com/f69854036f6b5d51.png)
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
