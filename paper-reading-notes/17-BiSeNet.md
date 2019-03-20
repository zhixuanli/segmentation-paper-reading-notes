### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 18 | 17 | 50 |

## Paper Information
#### Paper Title : 
[BiSeNet: Bilateral Segmentation Network for Real-time Semantic Segmentation](https://arxiv.org/abs/1808.00897) 

#### Conference : 
ECCV 2018

#### Authors and Institutions
##### Authors
Changqian Yu, Jingbo Wang, Chao Peng, Changxin Gao, Gang Yu, Nong Sang

##### Institutions
+ 1 National Key Laboratory of Science and Technology on Multispectral Information Processing,School of Automation,Huazhong University of Science & Technology,China{changqian yu,cgao,nsang}@hust.edu.cn+ 2 Key Laboratory of Machine Perception, Peking University, China wangjingbo1219@pku.edu.cn+ 3 Megvii Inc. (Face++), China {pengchao,yugang}@megvii.com


#### Official Codes
[https://github.com/ycszen/TorchSeg](https://github.com/ycszen/TorchSeg)

#### Some articles to comprehend this paper
[旷视科技提出双向网络BiSeNet：实现实时语义分割](https://zhuanlan.zhihu.com/p/41475332)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/02.png" width="80%" />
</div>

## Note
There are mainly three approaches to accelerate the model.

1. Use cropping or resizing to restrict the input size, but the loss of spatial details is harmful to performance.
2. Prune the channels of the network.
3. ENet [25] proposes to drop the last stage of the model in pursuit of an extremely tight framework.
	+ With the downsampling operations in the last stage abandoned, the receptive field of the model is not enough to cover large objects.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/01.png" width="80%" />
</div>

To remedy the loss of spatial details, U-shape structure is utilized widely. But will have extra computation.

### About BiSeNet
Spatial path doesn't have a backbone, for reserving the details as much as possible.

Context path has a backbone.

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
+ Large spatial resolution is important for reserving details, but will decrease the inference speed.
+ Large receptive field, which means little spatial resolution, is necessary for semantic inforation.

This is a dilemma.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
a novel Bilateral Segmentation Network (BiSeNet):

+ Spatial Path: preserve the spatial information with high-resolution features
+ Context Path: sufficient receptive field by fast downsampling

Finnaly use a Feature Fusion Module to merge the features.

### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ Cityscapes
+ CamVid
+ COCO-Stuff


#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/05.png" width="80%" />
</div>

-----------------------------------------------------
<div  align="center">   
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/08.png" width="80%" />
</div>

-----------------------------------------------------
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/09.png" width="80%" />
</div>

-----------------------------------------------------
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/11.png" width="80%" />
</div>

-----------------------------------------------------
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/18-BiSeNet/13.png" width="80%" />
</div>

#### 3.5 What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)
Speed and performance


### 5. Disadvantages (self-summary rather than the author's)

#### 5.1 Something interesting:
[https://github.com/CoinCheung/BiSeNet](https://github.com/CoinCheung/BiSeNet)

#### 5.2 
It looks like an attention based simple version U-Net.