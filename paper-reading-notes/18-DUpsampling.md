### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 19 | 18 | 50 |

## Paper Information
#### Paper Title : 
[Decoders Matter for Semantic Segmentation: Data-Dependent Decoding Enables Flexible Feature Aggregation](https://arxiv.org/pdf/1903.02120) 

#### Conference : 
CVPR 2019

#### Authors and Institutions
##### Authors
+ Zhi Tian 1
+ Tong He 1 
+ Chunhua Shen 1 
+ Youliang Yan 2

##### Institutions
+ 1 The University of Adelaide, Australia 
+ 2 Noah’s Ark Lab, Huawei Technologies


#### In-official Codes
[https://github.com/LinZhuoChen/DUpsampling](https://github.com/LinZhuoChen/DUpsampling)

#### Some articles to comprehend this paper


#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/02.png" width="80%" />
</div>

## Note
The DUpsampling method:

+ data dependent
+ no need to constrain the resolution of features to be very high (like 1/4 or 1/8 ) that need to be upsampled

### 1. Beyond Bilinear: Datadependent Upsampling
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/03.png" width="80%" />
</div>

W is learned from the process of downsampling and recontruction of the GT label map.

$x = Pv; v_{hat} =Wx; $

For GT label map (high resolution) Y, v is the sub-region of it and x if a vector in lower-dimension.

$v_{hat}$ is the reconstructed GT label map.

And this learned W can be used to upsample the fused feature map.

### 2. Incorporating DUpsampling with Adaptivetemperature Softmax
Vanilla softmax function (looks like just normal softmax) is hard to converge when incorporating DUpsampling, and also has difficulty in producing sharp enough activation.

A parameter named temperature T is used here to sharpen/soften the activation of softmax and makes training converge much faster.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/11.png" width="50%" />
</div>

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
+ The overall strides of the encode must be reduced to get features in receptable resolution, for example from $1/{32}$ to $1/4$. Because bilinear upsampling method is data independent, and doesn't take account of the correlations of pixels.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
+ Use a data dependent method DUpsampling to replace the data independent method bilinear upsampling.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ PASCAL VOC
+ PASCAL Context


#### 3.2 How is the experiment set up?
+ ResNet-50 [12] and Xception-65 [6] as our backbone networks
+ “poly” as our learning rate policy
+ **All weights of newly added layers are initialized with Gaussiandistribution of variance 0.01**

#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study
+ same encoder
	+ The encoder yields the final feature maps with the 1/16 or 1/32 size of the original image.

##### 3.4.1 DUpsampling vs. Bilinear
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/04.png" width="80%" />
</div>

upper bound: using ground truth labels instead of raw images as the network input.

##### 3.4.2 Flexible aggregation of convolutional features
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/05.png" width="80%" />
</div>

Different level features fusing gain different results.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/07.png" width="80%" />
</div>

##### 3.4.3 Impact of adaptive-temperature softmax
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/08.png" width="80%" />
</div>

AMAZING!!!

#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/09.png" width="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/10.png" width="80%" />
</div>

### 4. Advantages (self-summary rather than the author's)
+ Much more reasonable and convictive than bilinear.
+ The adaptive-temperature softmax converge faster than vanilla softmax!

### 5. Disadvantages (self-summary rather than the author's)
The reconstruction process of low-resolution features to prediction may be not same to the process between low and high resolution gt labels.

So, maybe DUpsampling is not the premium solution.