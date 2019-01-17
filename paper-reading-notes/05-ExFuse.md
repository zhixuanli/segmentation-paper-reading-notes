### The progress of the reading plan: 
05 / 50

## Paper Information
#### Paper Title : 
[ExFuse: Enhancing Feature Fusion for Semantic Segmentation](https://arxiv.org/abs/1804.03821) 

#### Conference : 

ECCV 2018


#### Authors and Institutions
##### Authors

+ Zhenli Zhang 1
+ Xiangyu Zhang 2
+ Chao Peng 2
+ Dazhi Cheng 3
+ Jian Sun 2

##### Institutions

+ 1 Fudan University
+ 2 Megvii Inc. (Face++)
+ 3 Beijing Institute of Technology

#### Official Codes

NO

#### Official Instruction (Chinese)
[ECCV 2018 | 旷视科技提出ExFuse——优化解决语义分割特征融合问题](https://mp.weixin.qq.com/s?__biz=MzA3NjIzMTk0NA==&mid=2651647950&idx=1&sn=13e0795b1bfc7f992e883593b14c3bb3&chksm=849c2ba9b3eba2bfa185f73e978a7c693ee08910c50d627582dfabeea3057c2328abd68930b3&scene=21#wechat_redirect)


#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/05-ExFuse-01.png" width="80%" height="80%" />
</div>


## Note
Enhance the feature fusing method of U-Net structure semantic segmentation methods by introducing more semantic concepts into low-level features and by embedding more spatial information into high-level features.


### Key Words
Feature Fusing


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
A lot of methods fuse low-level but high-resolution features and high-level low-resolution features don't considering the large semantic or resolution gap between low and high level features.
If low level feature does't have any high level semantic information, then it will contain many noises and become a burden when fusing with high level feature, and vice versa.
In other words, feature fusion could be enhanced **by introducing more semantic concepts into low-level features or by embedding more spatial information into high-level features**.

### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
1. introduce more semantic information into low-level features
	+ layer rearrangement
	+ semantic supervision
	+ semantic embedding branch
2. embed more spatial information into high-level features
	+ explicit channel resolution embedding
	+ densely adjacent prediction


### 3. Details about the experiment

#### 3.1 Which Datasets are used?



#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 (Optional）How to divide training data and test data？



#### 3.5 (Optional）What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)
+ Comparing ExFuse with the atrous convolution, which can keep the resolution while going deeper layers, is important.
+ The writing is too tricky. 

For example, 

> feature maps close to semantic supervisions (e.g. classication loss) tend to encode more

Here the semantic supervisions actually means the high level layers.

> To make low-level features (res-2 or res-3) 'closer' to the supervisions, one straight-forward approach is to arrange more layers in the early stages rather than the latter.

Actually, here the author changed the structure of ResNeXt network, to dicrease the amount of building blocks from {3; 4; 23; 3} to {8; 8; 9; 8}, which means the amount of hiden layers is less. So naturally more the low-level layers are closer to the high level layers.

I suggest that neat and clear representations should be used in writing, or misleading may be happen.

+ About the "Semantic Embedding Branch"

> However, if the low-level feature contains little semantic information, it is insucient to recover the semantic resolution.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/05-ExFuse-02.png" width="80%" height="80%" />
</div>

I don't agree with the author. The low level feature has only very few semantic infomation, and most of it is the struture information.
The semantic information, should be in the charge of high level information. That's why we fuse the low and high level features.

So, the low level feature here, is not becoming richer of information. Actually it's becoming poorer. 

Because when we look at the struture of the "Semantic Embedding Branch", we can find that the low level feature map is multiplying element-wisely with the upsampled high level feature. And the high level feature contains many semantic informations. The information of whether two pixels are belonging to the same class is included in it. We can regard it as an attention map or a mask, the value it including implies each position in the low level feature is the boundary or not.

After the multiplication, the noises in the low level feature are decreased, by preserving the boundaries and discarding those inplace noisy values. Just look the following image.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/05-ExFuse-03.png" width="80%" height="80%" />
</div>

**Refinement is actually what happened here.**

So may we can design a structure to refine the low level feature to decrease its noise specifically.
