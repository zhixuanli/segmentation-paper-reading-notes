### The progress of the reading plan: 
| Index  |  All |
| :----: | :--: |
| 28 | 50 |

## Paper Information
#### Paper Title : 
[Accel: A Corrective Fusion Network for Efficient Semantic Segmentation on Video](http://www.samvitjain.com/accel/)

#### Conference : 
CVPR 2019 Oral

#### Authors and Institutions
##### Authors
+ Samvit Jain 
+ Xin Wang 
+ Joseph E. Gonzalez

##### Institutions
University of California, Berkeley

#### Official Codes
[https://github.com/SamvitJ/Accel](https://github.com/SamvitJ/Accel)

#### Some articles to comprehend this paper


#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/28-Accel/02.png" width="80%" />
</div>

## Note
Use optical flow to wrap the feature of last frame, and merge that with the feature of current frame.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/28-Accel/01.png" width="80%" />
</div>

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
Efficiency and performance couldn't be well in the same time for video semantic segmentation.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
**Reuse the feature of last frame**, going through the wrapping of optical flow, and finally merged with feature of current frame. 


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ CityScapes
+ CamVid

#### 3.2 How is the experiment set up?
Pretrained on ImageNet, respectively finetuned the backbone and optical flow extractor on the dataset. And finally joint training to learn weight of score fusion layers.


#### 3.3 What's the evaluation metric?
+ mIoU
+ Inference time

#### 3.4 Ablation Study
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/28-Accel/08.png" width="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/28-Accel/09.png" width="80%" />
</div>

#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/28-Accel/05.png" width="80%" />
</div>

The baseline is not STOA. Where is BiSeNet and ICNet??

### 4. Conclusions
The structure is very simple. And it looks faster and could get higher performance. But the comparision is unfair.
