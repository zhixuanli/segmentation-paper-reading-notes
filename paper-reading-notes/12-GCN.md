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



#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 Ablation Study



#### 3.5 What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)
1. The design of larger kernel and boundary refinement is interesting and useful.


### 5. Disadvantages (self-summary rather than the author's)
1. I don't agree with saying classification and localization are contradictory. Because localization is reached by classification originally, in the field of detection and segmentation. It's helpful for telling story here, but not that big difference between them.