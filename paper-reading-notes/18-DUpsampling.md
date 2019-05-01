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
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/19-DUpsampling/11.png" width="80%" />
</div>

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
+ The overall strides of the encode must be reduced to get features in receptable resolution, for example from $1/{32}$ to $1/4$. Because bilinear upsampling method is data independent, and doesn't take account of the correlations of pixels.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
+ Use a data dependent method DUpsampling to replace the data independent method bilinear upsampling.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?



#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 Ablation Study



#### 3.5 What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)