### The progress of the reading plan: 
| Index | All |
| :----:| :-: |
| 23 | 50 |

## Paper Information
#### Paper Title : 
[CASENet: Deep Category-Aware Semantic Edge Detection](http://openaccess.thecvf.com/content_cvpr_2017/papers/Yu_CASENet_Deep_Category-Aware_CVPR_2017_paper.pdf) 

#### Conference : 
CVPR 2017

#### Authors and Institutions
##### Authors
+ Zhiding Yu
+ Chen Feng 
+ Ming-Yu Liu
+ Srikumar Ramalingam

##### Institutions
+ Carnegie Mellon University
+ Mitsubishi Electric Research Laboratories (MERL)

#### Official Codes
+ [http://www.merl.com/research/license#CASENet](http://www.merl.com/research/license#CASENet)

#### Some articles to comprehend this paper
NO

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/04.png" width="80%" />
</div>

## Note
This is the first semantic edge detection paper I have read.

The following is the illustration of this task.
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/01.png" width="80%" />
</div>

The output of this task is K predicted maps for K classes. 

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/02.png" width="80%" />
</div>

### Channel Rearrangement
The authors believes that for features of hidden layers, top is more important than bottom.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/03.png" width="80%" />
</div>

(a) is a very basic network. (b) fuses features from multi-layers but the number of features from bottom is the same to top, which is K.

So CASENet rearranges the channel number to ensure the importance of top layer.

### New concatenation method
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/05.png" width="80%" />
</div>

1. The stack way (we always use)
2. The sliced way
3. The new shared way

Ablation study on the concatenation methods is lacked in this paper.

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
The imbalance of feature importance when fusing features from different layers.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
+ Rearrange the output channel number of each layer from "K-K-K-K" to "1-1-1-K"
+ Proposed shared concatenation instead of sliced way.

### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ SBD
+ CityScapes

#### 3.2 How is the experiment set up?
\


#### 3.3 What's the evaluation metric?
F-measure (MF) at optimal dataset scale (ODS), and average precision (AP) for each class


#### 3.4 Ablation Study
NO


#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/23-CASENet/07.png" width="80%" />
</div>


### 4. Advantages (self-summary rather than the author's)
+ Attention is not popular in 2017, and this work add this hand craft channel attention, which is very impressive.
+ New feature fusing method. Maybe an auto rearrangement is better here.


### 5. Disadvantages (self-summary rather than the author's)
NO