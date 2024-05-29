地表覆盖产品动态更新系统

       这是一个地表覆盖产品动态系统，可以进行地表覆盖产品的研究，可以处理大量数据、同时基本上所以数据都可以在Google Earth Engine上找到，
速度很快，太原市Landsat数据在过滤后为30GB，可以在3至4小时内在Google Earth Engine服务器完成数据处理，
获得非常多的成果，其次，本系统还完全免费，可以在Google Earth Engine上免费运行。



系统特点：
（1）具有很好的可视化界面
（2）可以自行生成训练数据
（3）可以自由选择分类模型
（4）可以自由选择分类参数
（5）可以自由选择训练数据的时间
（6）全部代码完全开源，可以自行进行功能的修改和增删
（7）由于本系统的很多成果可以根据自己兴趣进行二次处理，获得自己想要的成果，
即不一定用来做地表覆盖更新，可以做地表覆盖物的稳定研究等等，故本系统可以分成多块根据自己的需要进行处理，
进行其他研究
（8）可以选择Landsat卫星5,7,8对感兴趣时间段内卫星图像进行观测，（只显示质量最好的图像进行显示）



系统可以获得的成果：
（1）感兴趣点的地表覆盖更新情况
（2）研究区域地表覆盖更新概率和地表覆盖更新次数
（3）研究区域地表覆盖第一次和最后一次更新的时间
（4）研究区域地表覆盖的最大更新幅度及其对应的时间
（5）研究区域规定时间内的地表覆盖开始更新和结束更新的次数
（6）研究区域的某时间段内的时空稳定区域
（7）通过3*3像素的侵蚀过滤得到的时空稳定的均匀图像
（8）研究区域的研究时间段内的任意一天的地表覆盖情况
（9）研究区域的研究时间段内的，任意时间段内的地表覆盖间的更新情况，
        例如：
       （1）地表覆盖1更新为2,3,4,5
       （2）地表覆盖1更新为2
       （3）地表覆盖2,3,4,5更新为1
（10）地表覆盖之间的更新面积（桑葚图绘制）（该部分需要自己在ArcMap进行处理，之后运行桑葚图代码生成桑葚图）




系统使用手册
一、有研究区域的Shapefile面文件和对应格式的训练数据
可以直接在Google Earth Engine上运行，
（1）首先在CCDC代码块运行，生成CCDC图像栈还有其他的一些成果数据，例如第一次地表覆盖更新时间，每个像素的更新次数。
（2）将训练数据和生成的CCDC图像栈传入classify代码块，生成各像素更新状态文件
（3）将第（2）步生成的文件传入landcover代码块，生成研究区域的研究时间内的任意时间的地表覆盖分类情况和地表覆盖之间的转换情况。

二、只有研究区域的Shapefile面文件，没有训练数据或者是不清楚训练数据的格式。

1.不清楚训练数据的格式
Feature Index	ASPECT (Float)	CID (Integer)	DEM_SLOPE (Float)	ELEVATION (Integer)	GREEN_AMPLITUDE (Float)	GREEN_AMPLITUDE2 (Float)	GREEN_AMPLITUDE3 (Float)	GREEN_COS (Float)	GREEN_COS2 (Float)	GREEN_COS3 (Float)	GREEN_INTP (Float)	GREEN_PHASE (Float)	GREEN_PHASE2 (Float)	GREEN_PHASE3 (Float)	GREEN_RMSE (Float)	GREEN_SIN (Float)	GREEN_SIN2 (Float)	GREEN_SIN3 (Float)	GREEN_SLP (Float)	NIGHT_LIGHTS (Float)	NIR_AMPLITUDE (Float)	NIR_AMPLITUDE2 (Float)	NIR_AMPLITUDE3 (Float)	NIR_COS (Float)	NIR_COS2 (Float)	NIR_COS3 (Float)	NIR_INTP (Float)	NIR_PHASE (Float)	NIR_PHASE2 (Float)	NIR_PHASE3 (Float)	NIR_RMSE (Float)	NIR_SIN (Float)	NIR_SIN2 (Float)	NIR_SIN3 (Float)	NIR_SLP (Float)	POPULATION (Float)	RAINFALL (Float)	RED_AMPLITUDE (Float)	RED_AMPLITUDE2 (Float)	RED_AMPLITUDE3 (Float)	RED_COS (Float)	RED_COS2 (Float)	RED_COS3 (Float)	RED_INTP (Float)	RED_PHASE (Float)	RED_PHASE2 (Float)	RED_PHASE3 (Float)	RED_RMSE (Float)	RED_SIN (Float)	RED_SIN2 (Float)	RED_SIN3 (Float)	RED_SLP (Float)	SWIR1_AMPLITUDE (Float)	SWIR1_AMPLITUDE2 (Float)	SWIR1_AMPLITUDE3 (Float)	SWIR1_COS (Float)	SWIR1_COS2 (Float)	SWIR1_COS3 (Float)	SWIR1_INTP (Float)	SWIR1_PHASE (Float)	SWIR1_PHASE2 (Float)	SWIR1_PHASE3 (Float)	SWIR1_RMSE (Float)	SWIR1_SIN (Float)	SWIR1_SIN2 (Float)	SWIR1_SIN3 (Float)	SWIR1_SLP (Float)	SWIR2_AMPLITUDE (Float)	SWIR2_AMPLITUDE2 (Float)	SWIR2_AMPLITUDE3 (Float)	SWIR2_COS (Float)	SWIR2_COS2 (Float)	SWIR2_COS3 (Float)	SWIR2_INTP (Float)	SWIR2_PHASE (Float)	SWIR2_PHASE2 (Float)	SWIR2_PHASE3 (Float)	SWIR2_RMSE (Float)	SWIR2_SIN (Float)	SWIR2_SIN2 (Float)	SWIR2_SIN3 (Float)	SWIR2_SLP (Float)	TEMPERATURE (Float)	TREE_COVER (Integer)	WATER_OCCURRENCE (Integer)	landcover (Integer)	system:index (String)	year (Integer)
属性太多，可以参考我上传的Shapefile点文件


2.没有训练数据
      1.运行CCDC代码块的检测地表覆盖更新的部分，获得CCD掩膜，在ArcMap中对研究数据进行裁剪，获得时空稳定数据
      2.对研究数据的各地表覆盖类别进行分离，生成训练点，生成的训练点的数量与地表覆盖的面积成正比。
      3.得到下列的Shapefile点数据（在ArcMap自行操作）
	Shapefile点数据的格式：
	（1）训练数据为Shapefile点文件
	（2）关键属性（只需要有这2个属性就能运行，注意属性名别打错，或者可以自己在代码设置属性名，这里是属性名（属性格式））：landcover (Integer)，year (Integer)
	这里的landcover对应的是地表覆盖的类型，例如：1对应水体，2对应森林。year的数字代表你使用的训练数据的年份，本系统只使用1年的训练数据。
       4.将该数据自行命名(建议英文+数字+下划线)，之后上传至Google Earth Engine的Assets中
在Google Earth Engine上运行CCDCTrainingPoint代码块处理第1步的Shapefile点文件，生成训练数据



各代码块功能：
CCDCNEW2：生成CCCD图像栈，并生成地表覆盖分类
observeLandsatImage：观测感兴趣区域的感兴趣时间段的卫星图像（自动显示图像质量最好的一张）
ui：界面代码
CCDCtrainingPoint：生成训练数据






声明，本系统绝大部分代码都是在Google Earth Engine的代码，Google Earth Engine的技术文档，CSDN的一些博客，还有Google的一些代码的基础上做的，
实际上，我本人做的部分不多，基本上只是根据个人需求对代码进行一些修改和增加。
下面是我参考的代码、博客、技术文档的地址。
https://github.com/parevalo/gee-ccdc-tools/blob/master/ccdcUtilities/results.js
https://gee-ccdc-tools.readthedocs.io/en/latest/lctutorial/training.html
https://doc.arcgis.com/zh-cn/arcgis-online/analyze/how-analyze-changes-using-ccdc-works.htm
https://www.openmrv.org/web/guest/w/modules/mrv/modules_2/continuous-change-detection-and-classification-ccdc#31-algorithm-description
https://www.youtube.com/watch?v=1moyd9qWwcw
https://google-earth-engine.com/Interpreting-Image-Series/Interpreting-Time-Series-with-CCDC/
https://google-earth-engine.com/
https://blog.csdn.net/qq_35591253/article/details/130105903?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171698760516800186537216%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171698760516800186537216&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-130105903-null-null.142^v100^pc_search_result_base3&utm_term=CCDC&spm=1018.2226.3001.4187
https://blog.csdn.net/qq_31988139/article/details/134658252?ops_request_misc=&request_id=&biz_id=102&utm_term=CCDC&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-134658252.142^v100^pc_search_result_base3&spm=1018.2226.3001.4187
CSDN参考了：此星光明，_养乐多_

因为参考的资料太多，有些资料来源可能没有贴出来，如果有遗漏，可以联系我进行增添。
