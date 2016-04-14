## 飞行器和机器人图像处理学习记录
依托于互联网+比赛， 然后我在飞行器和机器人项目组中都负责有图像处理任务，本文档作为我的整个学习记录。<br>
开发平台：`win8` `OpenCV` `VS2013`
###飞行器项目-项目要求
    本次比赛飞行器在应用上要实现的主要功能是巡逻侦察，在图像处理方面主要实现的功能有：
    1、行人检测，在此基础上累计行人数目
    2、车辆检测，在此基础上累计车辆数目
    3、车牌识别
###机器人项目-项目要求
    对于互联网+比赛，机械臂主要需要实现的功能是远程控制机械臂，都是基于手势识别。
    手势识别方案：
    1、基于数据手套
      电位器进行手指角度值的获取，MUP6050提取手臂在空间上移动的姿态。
    2、基于视觉
      采用OpenCV机器视觉库，进行手势识别。
###目录
* [OpenCV学习笔记](./notebook/leaning/leaning_catalog.md)

* [静态手势识别](./notebook/gesture.md)

* 车牌识别

* 行人检测

* 车辆检测

###参考资料
####链接
* OpenCV官网    [http://opencv.org/](http://opencv.org/)
* OpenCV学习日文网站    [http://opencv.jp/cookbook/index.html#](http://opencv.jp/cookbook/index.html#)
* OpenCV中文论坛    [http://www.opencv.org.cn/](http://www.opencv.org.cn/)
* 毛星云博客-OpenCV教程     [http://blog.csdn.net/zhmxy555/article/category/1923021](http://blog.csdn.net/zhmxy555/article/category/1923021)
* 中国知网      [http://www.cnki.net/](http://www.cnki.net/)

####参考书
* 《OpenCV编程入门》 毛星云
* 《数字图像处理》Rafael C. Gonzalez, Richard E. Woods
* 《机器视觉》 伯特霍尔德.霍恩
* 《学习OpenCV》
