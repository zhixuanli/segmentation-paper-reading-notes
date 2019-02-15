### The progress of the reading plan: 
08 / 50

## Paper Information
#### Paper Title : 
[Learning a Discriminative Feature Network for Semantic Segmentation](http://openaccess.thecvf.com/content_cvpr_2018/papers/Yu_Learning_a_Discriminative_CVPR_2018_paper.pdf) 

#### Conference : 

CVPR 2018 **Spotlight**

#### Authors and Institutions
##### Authors
+ Changqian Yu 1
+ Jingbo Wang 2 
+ Chao Peng 3 
+ Changxin Gao 1
+ Gang Yu 3 
+ Nong Sang 1

##### Institutions
+ 1 Key Laboratory of Ministry of Education for Image Processing and Intelligent Control, School of Automation, Huazhong University of Science and Technology+ 2 Key Laboratory of Machine Perception, Peking University+ 3 Megvii Inc. (Face++)


#### Official Codes
[Inofficial Code1](https://github.com/lxtGH/dfn_seg)
[Inofficial Code2](https://github.com/whitesockcat/Discriminative-Feature-Network)

#### Some articles to comprehend this paper
[Official in Chinese | 旷视科技Face++提出用于语义分割的判别特征网络DFN](https://zhuanlan.zhihu.com/p/36540674)
[论文阅读 - Learning a Discriminative Feature Network for Semantic Segmentation (CVPR2018)](https://zhangbin0917.github.io/2018/06/19/Learning-a-Discriminative-Feature-Network-for-Semantic-Segmentation/)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/01.png" width="100%" height="100%" />
</div>

## Note
### 1
To remedy the imbalance of different classes, focal loss [22] is used here to supervise the output of the Border Network.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/04.png" width="25%" height="25%" />
</div>


$p_k$ is the estimated probability for class k.
**Reference**
+ [22] T.-Y. Lin, P. Goyal, R. Girshick, K. He, and P. Doll´ar. Focal loss for dense object detection. In IEEE International Conference on Computer Vision, 2017.

### 2
We use a parameter lamada to balance the segmentation loss $l_s$ and the boundary loss $l_b$:

$L = l_s + lamada * l_b$


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
Intra-class inconsistency and inter-class indistinction is two important problems in semantic segmentation.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/02.png" width="60%" height="60%" />
</div>

### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
1. intra-class inconsistency problem: a Smooth Network with Channel Attention Block and global average pooling to select the more discriminative features.
	+ multi-scale features are used to enrich the information: U-net structure
	+ global average pooling is used to capture the global information
	+ CAB is designed to use the high level information to guide the low layer.
2. inter-class indistinction: To amplify the distinction of features, a Border Network is proposed to make the bilateral features of boundary distinguishable with deep semantic boundary supervision.

Using Canny algorithm on the semantic ground truth to obtain the supervisory signal, which is used to refine the low stage feature.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ PASCAL VOC 2012
+ Cityscapes


#### 3.2 How is the experiment set up?
+ multi-scale data augmentation

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/05.png" width="60%" height="60%" />
</div>

**Data augmentation is necessary!**

#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation study
**Smooth Network**

Detailed performance comparison of our proposed Smooth Network. RRB: refinement residual block. GP: global pooling branch. CAB: channel attention block. DS: deep supervision.
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/06.png" width="60%" height="60%" />
</div>
We can find that the biggest improvementa are coming from RRB, GP and CAB.


**Border Network**

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/07.png" width="60%" height="60%" />
</div>

The improvement of BN is not as big as RRB, GP and CAB.


<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/09.png" width="60%" height="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/10.png" width="60%" height="60%" />
</div>
#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/11.png" width="60%" height="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/12.png" width="60%" height="60%" />
</div>


### 4. Advantages (self-summary rather than the author's)
This paper was accepted as the spotlight paper in CVPR 2018. Here are some reasons I think important:
1. The ablation study is sufficient.
2. The idea of refinement the low stage feature (DS: deep supervision) is interesting. Though DS doesn't improve a lot performance, just 0.43% according to Table 2, this idea is easy to touch the reviewers and readers.



### 5. Disadvantages (self-summary rather than the author's)
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/09-DFN/08.jpg" width="60%" height="60%" />
</div>

The parameter lamada actually can be set to some value(like 0) at first, and gradually be learned to a proper position during the learning.