### The progress of the reading plan: 
12 / 50

## Paper Information
#### Paper Title : 
[Large Kernel Matters——Improve Semantic Segmentation by Global Convolutional Network](http://openaccess.thecvf.com/content_cvpr_2017/papers/Peng_Large_Kernel_Matters_CVPR_2017_paper.pdf) 

#### Conference : 
CVPR 2017

#### Authors and Institutions
##### Authors
+ Chao Peng 1
+ Xiangyu Zhang 2
+ Gang Yu 2
+ Guiming Luo 1
+ Jian Sun 2

##### Institutions
+ 1 School of Software, Tsinghua University
+ 2 Megvii Inc. (Face++)

#### Inofficial Codes
[https://github.com/ycszen/pytorch-segmentation](https://github.com/ycszen/pytorch-segmentation)

#### Some articles to comprehend this paper


#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/02.png" width="80%" />
</div>

## Note
To address the contradictory aspects including classification and localization, GCN is proposed.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/01.png" width="80%" />
</div>

Instead of directly using larger kernel or global convolution, our GCN module employs a combination of 1  x k + k x 1 and k x 1 + 1 x k convolutions, which enables densely connections within a large k x k region in the feature map.

And computation cost is lower.


As a comparison, our Global Convolution Network significantly enlarges the VRF

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/03.png" width="80%" />
</div>

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
Classification and localization tasks are naturally contradictory. 

For the classification task, the models are required to be invariant to various transformations like translation and rotation. But for the localization task, models should be transformation-sensitive to locate each pixel.

The conventional semantic segmentation algorithms mainly target for the localization issue, which might decrease the classification performance.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
Global Convolutional Network (GCN) is proposed to deal with the above two challenges simultaneously.

+ **from the localization view:** fully convolutional to retain the localization performance and no fully-connected or global pooling layers should be used as these layers will discard the localization information;
+ **from the classification view:** large kernel size should be adopted in the network architecture to enable densely connections between feature maps and per-pixel classifiers, which enhances the capability to handle different transformations.

We introduce boundary refinement block to model the boundary alignment as a residual structure.

### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ PASCAL VOC 2012 (SBD)
+ Cityscapes


#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/04.png" width="70%" />
</div>

##### Global Convolutional Network — Large Kernel Matters
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/05.png" width="60%" />
</div>

(1) Are more parameters helpful?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/07.png" width="60%" />
</div>

(2) GCN vs. Stack of small convolutions
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/06.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/08.png" width="60%" />
</div>

(3) How GCN contributes to the segmentation results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/09.png" width="60%" />
</div>

##### Global Convolutional Network for Pretrained Model
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/11.png" width="60%" />
</div>

Change the module in original ResNet to GCN. We can safely conclude that GCN mainly helps to improvesegmentation performance, no matter in pretrained model or segmentation-specific structures.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/10.png" width="60%" />
</div>
#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/12.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/13.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/12-GCN/14.png" width="60%" />
</div>


### 4. Advantages (self-summary rather than the author's)
1. The design of larger kernel and boundary refinement is interesting and useful.


### 5. Disadvantages (self-summary rather than the author's)
1. I don't agree with saying classification and localization are contradictory. Because localization is reached by classification originally, in the field of detection and segmentation. It's helpful for telling story here, but not that big difference between them.