## 实验结果

测试数据使用MPD中给出的数据

- 非匹配图片对2000组，成功提取1705组ROI，YOLO模型有效率85.25%
- 匹配图片对10000组，成功提取8702组ROI，YOLO模型有效率87.02%

## 原因分析

照片未检测到的原因主要是因为YOLO模型的识别精确度差异。以下是两种情况的示例：

### 情况一

原图片：
![原图片](1_0.jpg)

YOLO检测图片：
![YOLO检测图片](1_1.jpg)

### 情况二

原图片：
![原图片](2_0.jpg)

YOLO检测图片：
![YOLO检测图片](2_1.jpg)

## 计算阈值

阈值的计算我们尝试了两种聚类的算法，分别是k-means算法和DBSCAN算法，两种算法的结果如下：
k-means算法：
![k-means算法](k-means_plot.png)

DBSCAN算法：
![DBSCAN算法](dbscan_plot.png)
很容易看出，DBSCAN算法对于我们的数据拟合度较好，几乎没有not_matched数据通过，虽然筛掉了一些matched数据，但是对于一个验证项目而言，这样做的误匹配很低。

## 总结

在匹配图片对数据上进行检测，大于阈值0.5299 的样本数量为6540，识别成功率为75.15%，综合识别率为65.40%
非匹配图片对均不能通过阈值检测，淘汰率为100%。
