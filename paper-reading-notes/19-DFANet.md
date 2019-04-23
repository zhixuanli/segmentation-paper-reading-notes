### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 21 | 19 | 50 |

## Paper Information
#### Paper Title : 
[DFANet: Deep Feature Aggregation for Real-Time Semantic Segmentation](https://arxiv.org/abs/1904.02216v1) 

#### Conference : 
CVPR 2019

#### Authors and Institutions
##### Authors
Hanchao Li, Pengfei Xiong, Haoqiang Fan, Jian Sun


##### Institutions
Megvii


#### Official Codes
NO

#### Some articles to comprehend this paper
[CVPR 2019 | 旷视实时语义分割技术DFANet：高清虚化无需双摄](https://www.jiqizhixin.com/articles/2019-04-08-8)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/02.png" width="80%" />
</div>

## Note
### Problem definition
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/01.png" width="80%" />
</div>

+ The structure a) learns feature on a high resolution image, which will increase the computation cost. And the communication between branches are lacking. (PS: Why do we need the communication???)
+ Structure b)  is usually time-consuming. (PS: and also could not focus on small objects because it can only enlarge the receptive field, but never reduce)
+ Structure c) the details are lost.
+ d) is used in this paper to pass through the low level features to the next backbone.

### Network
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/02.png" width="80%" />
</div>

It's basically a RNN structure, making the output of last module as the input of the next module, and the features from hidden layers of the last module are also passed to the same level of the next module. But RNN has forget gate to erase those useless features, and RNN only have one module being used repeatedly.

The most valuable part for me is the experiment part.
### Key Words
Cascade

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
SPP module can enrich features with multi-scale while leading a sharp increase of computation cost.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
A cascade structure is proposed to fuse multi-level features without increasing much computation cost.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ CityScapes
+ CamVid

#### 3.2 How is the experiment set up?
+ mini-batch stochastic gradient descent (SGD) with batch size 48, momentum 0.9 and weight decay 1e - 5
+ ”poly” learning rate policy


#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/03.png" width="80%" />
</div>


<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/04.png" width="80%" />
</div>
The kernel number of the hidden layer is important. The more, the better performence.


<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/05.png" width="80%" />
</div>
Backbone is not always helpful. With the feature going deep, the feature size will be very small and thus decrease the performance.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/06.png" width="80%" />
</div>
Although the third backbone is not very good at segmentation, but it's helpful when fusing these features from different layers.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/07.png" width="80%" />
</div>
The result is better for deeper backbone.

The FC layer is really important for increasing 4~6% of the performance.
#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/21-DFANet/08.png" width="80%" />
</div>

This table is very detailed. Listing the inputsize is very commendable here!


### 4. Advantages (self-summary rather than the author's)
Fast speed and pretty well performance, from excellent backbone and fusing method.

Many helpful details are shown in the paper. 👍

### 5. Disadvantages (self-summary rather than the author's)
+ This fusing approach is useful, but it really looks like RNN and FC attention helped a lot but the ablation study is lacking.