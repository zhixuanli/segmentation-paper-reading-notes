### The progress of the reading plan: 
11 / 50

## Paper Information
#### Paper Title : 
[Adaptive Affinity Fields for Semantic Segmentation](http://openaccess.thecvf.com/content_ECCV_2018/papers/Jyh-Jing_Hwang_Adaptive_Affinity_Field_ECCV_2018_paper.pdf) 

#### Conference : 
ECCV 2018

#### Authors and Institutions
##### Authors
+ Tsung-Wei Ke
+ Jyh-Jing Hwang
+ Ziwei Liu
+ Stella X. Yu

##### Institutions
UC Berkeley / ICSI

#### Official Codes
[https://github.com/twke18/Adaptive_Affinity_Fields](https://github.com/twke18/Adaptive_Affinity_Fields)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/01.png" width="80%" height="80%" />
</div>

## Note
1. Most methods treat semantic segmentation as a pixel-wise classification task, but when foreground and background pixels are close or mixed together, these methods will fundamentally lack the spatial discrimination power.
2. Image segmentation has highly correlated outputs among the pixels. Formulating it as an independent pixel labeling problem not only makes the pixel level classification unnecessarily hard, but also leads to artifacts and spatially incoherent results. **That's why structure modeling method like CRF are so useful to incorporate structure information into segmentation**.

(But actually the relationship between each pixel and the others are used by many STOA methods, such as DANet.)

AAF is proposed to structure modeling by matching the relations between neighbouring pixels in the label space, it can be seen as a region-wise supervision method.

###  1. From Pixel-wise Supervision to Region-wise Supervision

#### About [Cross-Entropy](https://ml-cheatsheet.readthedocs.io/en/latest/loss_functions.html)

Pixel-wise cross-entropy loss is most often used in CNNs for semantic segmentation. It implicitly assumes that the relationships between pixels can be learned as the effective receptive field increases with deeper layers.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/cross_entropy.png" width="50%" height="50%" />
</div>

<div  align="center"> 
Image from [ml-cheatsheet](https://ml-cheatsheet.readthedocs.io/en/latest/loss_functions.html)
</div>

Such a unary loss does not take the semantic label correlation and scene structure into account. This kind of inter-class and inner-class pixel relationships are informative and can be integrated into learning as structure reasoning.

The **region-wise loss** is proposed to integrate these intrinsic pixel relationships. It takes the neighbors $N_{y_i}$ of a pixel $i$ in to account.



The overall objective:

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/03.png" width="60%" height="60%" />
</div>

### 2.  Affinity Field Loss Function

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/04.png" width="90%" />
</div>

We define pairwise pixel affinity based not on the image, but on ground-truth label map. There are two types of label relationships between a pair of pixels: whether their labels are the same or different.

+ a grouping force: encourages network predictions at i and j to be similar
+ a separating force: pushes apart their label predictions

The loss function:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/02.png" width="80%" height="80%" />
</div>

### 3. Adaptive Kernel Sizes from Adversarial Learning
Region-wise supervision often requires a preset kernel size for CNNs, but we cannot expect one kernel size fits all categories.

So diffent field will have different kernel size.

### 4. The AAF loss function
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/07.png" width="60%" height="80%" />
</div>

and 
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/05.png" width="80%" height="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/06.png" width="50%" height="80%" />
</div>

### Key Words

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
There have been two main lines of efforts at incorporating structural reasoning into semantic segmentation: CRF and GAN.

CRF enforces label consistency between pixels measured by the similiarity in visual appearance, but it's time-consuming and sensitive to visual appearance changes.

GAN makes the predicted label map tested by a discriminator network on whether it resembles ground truth label maps in the training set. But it's very hard to train, particularly proning to model instability and mode collapses.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/02.png" width="80%" height="80%" />
</div>

To solve the problem of sensitive to visual appearance changes and hard to training, AAF is proposed.
### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
AAF is proposed to capture and match the semantic relations between neighbouring pixels in the label space.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ PASCAL VOC 2012
+ Cityscapes
+ GTA5


#### 3.2 How is the experiment set up?
1. GAN’s Adversarial Learning.
2. Pixel Embedding.
3. CRF-based Processing.



#### 3.3 What's the evaluation metric?
+ pixel-wise mIoU：all existing semantic segmentation works adopted
+ instance-wise mIoU
	+ pixel-wise mIoU metric is often biased toward large objects, we introduce the instance-wise mIoU to alleviate the bias, which allow us to evaluate fairly **the performance on smaller objects**.
+ boundary detection metrics


#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/08.png" width="80%" height="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/09.png" width="80%" height="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/10.png" width="80%" height="80%" />
</div>


#### 3.5 What is the ranking of the experiment results?

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/11-AAF/11.png" width="80%" height="80%" />
</div>

### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)
+ Lacks of results on Cityscapes test set
+ Lacks of comparision with other STOA methods and actually the performance is not very well, according to the result on the PASCAL VOC test set (pixel level)

