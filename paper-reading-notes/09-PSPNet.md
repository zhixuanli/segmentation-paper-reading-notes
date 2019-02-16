### The progress of the reading plan: 
09 / 50

## Paper Information
#### Paper Title : 
[Pyramid Scene Parsing Network](http://openaccess.thecvf.com/content_cvpr_2017/papers/Zhao_Pyramid_Scene_Parsing_CVPR_2017_paper.pdf) 

#### Conference : 
CVPR 2017

#### Authors and Institutions
##### Authors
+ Hengshuang Zhao 1
+ Jianping Shi 2 
+ Xiaojuan Qi 1 
+ Xiaogang Wang 1 
+ Jiaya Jia 1

##### Institutions
+ 1 The Chinese University of Hong Kong 
+ 2 SenseTime Group Limited


#### Official Codes
[https://github.com/hszhao/PSPNet](https://github.com/hszhao/PSPNet)

#### Slide
[Official Slide](http://image-net.org/challenges/talks/2016/SenseCUSceneParsing.pdf)

#### Some articles to comprehend this paper
[PSPnet：Pyramid Scene Parsing Network](https://blog.csdn.net/bea_tree/article/details/56678560)

#### Network Structure
PSPNet
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-PSPNet/01.png" width="100%" height="100%" />
</div>

## Note
The network structure is pretty simple, just concat features of different scales.
The way of cancatenation is different from Spatial Pyramid Pooling(SPP). SPP concats different scale features into a vector, but PSPNet clues them together, making the output feature thicker.

SPP:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/Spatial-pyramid-pooling-4.jpg" width="80%" height="80%" />
</div>

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
The current FCN based models are lacking of suitable strategy to utilize global scene category clues.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
Concatenating features of different scales to capture more global information.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ [PASCAL VOC 12 augmented](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#3-pascal-voc-2012-augmented-with-sbd)
+ [CityScapes](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#6-cityscapes-datasets)
+ [ADE20K](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#10-ade20k)


#### 3.2 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-PSPNet/03.png" width="80%" height="80%" />
</div>
Average pooling is better than max pooling.

Multi-scale pooling is helpful to capture more details.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-PSPNet/04.png" width="80%" height="80%" />
</div>
### 4. Advantages (self-summary rather than the author's)
1. The network structure is quite simple but powerful.


### 5. Disadvantages (self-summary rather than the author's)
1. Concatenating is helpful, but easier to bring more noise and redundancy.