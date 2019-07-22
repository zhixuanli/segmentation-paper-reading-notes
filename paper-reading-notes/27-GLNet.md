### The progress of the reading plan: 
| Index  |  All |
| :----: | :--: |
| 27 | 50 |

## Paper Information
#### Paper Title : 
[Collaborative Global-Local Networks for Memory-Efficient Segmentation ofUltra-High Resolution Images](https://arxiv.org/abs/1905.06368) 

#### Conference : 
CVPR 2019 Oral

#### Authors and Institutions
##### Authors
+ Wuyang Chen 1
+ Ziyu Jiang 1
+ Zhangyang Wang1
+ Kexin Cui 1
+ Xiaoning Qian 2

##### Institutions
Texas A&M University


#### Official Codes
[https://github.com/chenwydj/ultra_high_resolution_segmentation](https://github.com/chenwydj/ultra_high_resolution_segmentation)

#### Some articles to comprehend this paper


#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/05.png" width="80%" />
</div>

## Note
For ultra-high resolution images, use downsample for global branch and crop for local branch, and collaboratively merge the two branches.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/06.png" width="80%" />
</div>

### Key Words
ultra-high resolution; segmentation


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
Maintain the performance and GPU memory cost in the same time for ultra-high resolution images.

### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
Two braches with different strategies are proposed to merge global and local information in the same time.

### 3. Details about the experiment

#### 3.1 Which Datasets are used?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/02.png" width="80%" />
</div>

Examples:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/03.png" width="80%" />
</div>

#### 3.2 How is the experiment set up?
+ backbone: FPN+ResNet50
+ Adam
+ 1 1080Ti GPU


#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/08.png" width="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/09.png" width="80%" />
</div>

Through the code we can find the complexity of GLNET is very high.
+ Many layers of conv are deployed. The inference speed couldn't be too fast.
+ Timely delete the cache of former useless layers. This strategy can decrease many memory cost.

Merging the global and local feature, the performance change from 66.4 (global only) to 69.3, which is a very big advance.

**Local features can provide many "tiny" details but easily confused with appearance similiar classes.
Global features can distinguish the appearance similiar classes but can't focus on details. So merging them could be very useful.**

#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/27-GLNET/10.png" width="60%" />
</div>


### 4. Advantages (self-summary rather than the author's)
Memory and performance are both better, for merging the global and local braches.


### 5. Disadvantages (self-summary rather than the author's)
Not yet