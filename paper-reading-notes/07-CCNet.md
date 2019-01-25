### The progress of the reading plan: 
07 / 50

## Paper Information
#### Paper Title : 
[CCNet: Criss-Cross Attention for Semantic Segmentation](https://arxiv.org/abs/1811.11721) 

#### Conference : 
NO yet

#### Authors and Institutions
##### Authors
+ Zilong Huang 1
+ Xinggang Wang 1
+ Lichao Huang 2
+ Chang Huang 2 
+ Yunchao Wei 3
+ Wenyu Liu 1

##### Institutions
+ 1 School of EIC, Huazhong University of Science and Technology
+ 2 Horizon Robotics
+ 3 Beckman Institute, University of Illinois at Urbana-Champaign


#### Official Codes
[https://github.com/speedinghzl/CCNet](https://github.com/speedinghzl/CCNet)

#### Network Structure

Overview of the proposed CCNet for semantic segmentation.
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-01.png" width="80%" height="80%" />
</div>

Diagrams of two attention-based context aggregation methods.
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-02.png" width="80%" height="80%" />
</div>

## Note
RCCA: recurrent criss-cross attention module

Why there must exist at least 2 RCCA module?

Because when we only have 1 RCCA module, then after passing the module, each position only captures the relationship between the positions in the same column and same row.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-05.png" width="20%" height="20%" />
</div>

A simple example, after the first RCCA module, the value in position C contains the information of A and D. 

And in the same time, the value in A contains the information of B and C.

So after the second RCCA module, position C can capture the relationship between C and B indirectly by computing the distance with the new value in position A.


### Key Words
Complexity; Efficient


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
These attention-based methods need to generate huge attention maps to measure the relationships for each pixel-pair, whose complexity in time and space are both **O((HxW)x(HxW))**.

This paper aims to reduce the complexity of time and space.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
A criss-cross attention module that only aggregate long-range pixel-wise contextual information in horizontal and vertical direction is proposed.

By serially stacking two criss-cross attention modules, it can collect contextual information from all pixels.

The decomposition greatly reduce the complexity in time and space to O((HxW)x(H+W-1)).


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ [Cityscapes Datasets](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#6-cityscapes-datasets)
+ [ADE20K](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#10-ade20k)
+ COCO (for instance segmentation)


#### 3.2 How is the experiment set up?
+ backbone: the ImageNet pre-trained ResNet-101
	+ remove the last two down-sampling operations and employ dilated convolutions in the subsequent convolutional layers
	+ the size of the final feature map size is 1/8 of the input image
+ we replace the standard Batchnorm with InPlace-ABN to the mean and standard-deviation of BatchNorm across multiple GPUs. 
+ poly learning rate policy
	+ the initial learning rate is multiplied by the following fomula with power = 0.9.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-06.png" width="20%" height="20%" />
</div>


#### 3.3 What's the evaluation metric?
+ mIoU (mean of class-wise intersection over union) for Cityscapes and ADE20K
+ standard COCO metrics Average Precision (AP) for COCO


#### 3.4 Ablation studies
The effect of attention module
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-09.png" width=60%" height="60%" />
</div>

Comparison of context aggregation approaches on Cityscapes validation set
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-10.png" width="60%" height="60%" />
</div>


#### 3.5 What is the ranking of the experiment results?

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-08.png" width="80%" height="80%" />
</div>

Though CCNet doesn't achieve the higest performance on CityScapes, but it's really fast.

State-of-the-art Comparison experiments on ADE20K validation set.
<div  align="center">
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-12.png" width="60%" height="60%" />
</div>

Results of object detection and instance segmentation on COCO.
<div  align="center">
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-13.png" width="60%" height="60%" />
</div>



Comparison of Non-local module and RCCA
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-11.png" width="60%" height="60%" />
</div>

Visualization of Attention Map:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-14.png" width="80%" height="80%" />
</div>


### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)
1. Consider the example in Note Section, at the second RCCA module, when computing C, A is used twice but B is used just once when computing A. So maybe A makes more affect to C than B does. It's unreasonable for B maybe more important for C than A.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/07-CCNet-05.png" width="20%" height="20%" />
</div>