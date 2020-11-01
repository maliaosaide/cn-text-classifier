# cn-text-classifier
## 文本数据挖掘————文本聚类实验

>实验数据

实验数据来源于多个新闻网站爬取的新闻, 包含教育类510篇, 游戏类231篇, 医疗类388篇, 体育类412篇.
这部分数据从网上直接下载。


>实验步骤

文本聚类的一般步骤是:
1. 文本预处理
包含分段分句, jieba分词及去停用词等 
2. 语料向量化或词袋化
本实验使用了 `sklearn` 的 TF-IDF 相关包
3. 文本降维
常见的降维有 PCA 主成分降维, TSVD 截断奇异值分解降维, t-SNE降维等, 本实验使用 PCA 降维, t-SNE 更适用于图像和视频等降维, 速度较慢.
4. 应用聚类算法并调参
5. (可选)结果可视化及聚类效果评判 
聚类结果可视化已在 `visualizer.py` 中实现, 鉴于 DBSCAN 有识别噪声的能力, 在该实验中单独加入噪声可视化.   
聚类效果评判分为外部信息指标和内部信息指标, 外部信息指标依靠标注好的数据 `src/labeled_data.csv`。

评估指标主要有：
1. 调整后的 Rand 指数（Adjusted Rand Index，ARI）
2. Fowlkes-Mallows 指数
3. 轮廓系数（Silhouette Coefficient ）
4. Calinski-Harabaz 指数

>实验结果预览

**K-Means 聚类实验**
![K-Means](https://upload-images.jianshu.io/upload_images/5530017-81f526af29d27a13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```shell
------K-Means Experiment-------
adjusted_rand_score: 0.993424
FMI: 0.986693
Silhouette: 0.393411
 CHI: 610.098391
------End------
```

**Birch 聚类实验**
![Birch](https://upload-images.jianshu.io/upload_images/5530017-fd9b85232307e60e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```shell
-------Birch Experiment-------
adjusted_rand_score: 0.984727
FMI: 0.972753
Silhouette: 0.392115
 CHI: 607.003290
------End------
```

**DBSCAN 聚类实验**
![DBSCAN](https://upload-images.jianshu.io/upload_images/5530017-7673094ee2fb30d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```shell
------DBSCAN Experiment-------
adjusted_rand_score: 0.906213
FMI: 0.872378
Silhouette: 0.381767
CHI: 427.804137
Estimated number of noise points: 109 
------End------
```
**补充 Sing-Pass 聚类实验**

>内师大文本数据挖掘————聚类分析实验

