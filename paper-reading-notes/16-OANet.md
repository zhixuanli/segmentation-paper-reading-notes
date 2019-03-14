### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 17 | 16 | 50 |

## Paper Information
#### Paper Title : 
[An End-to-End Network for Panoptic Segmentation](https://arxiv.org/abs/1903.05027) 

#### Conference : 
CVPR 2019

#### Authors and Institutions
##### Authors
+ Huanyu Liu 1
+ Chao Peng 2
+ Changqian Yu 3
+ Jingbo Wang 4
+ Xu Liu 5
+ Gang Yu 2
+ Wei Jiang 1

##### Institutions
+ 1 Zhejiang University
+ 2 Megvii Inc. (Face++)
+ 3 Huazhong University of Science and Technology+ 4 Peking University
+ 5 The University of Tokyo


#### Official Codes
NO

#### Some articles to comprehend this paper

## Note
### Introduction to Panoptic segmentation
**Panoptic segmentation** is the combination of semantic segmentation and instance segmentation.

In this task, the stuff segmentation is employed to predict the amorphous regions (noted ***Stuff*** ), such as sky and grass, while the instance segmentation solves the countable objects (noted ***Thing*** ), such as people and cars.


Previous panoptic segmentation algorithms usually contain three separated components: 

+ the instance segmentation block
+ the stuff segmentation block
+ the merging block

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/17-OANet/01.png" width="80%" />
</div>

But this independent way is inefficient.

And the merging period has the challenge of overlapping. This paper proposed an end-to-end method to use one network to do the 2 tasks, and a new learnable mergin method.

### Introduction to Instance Segmentation
two main frameworks for instance segmentation:

+ the proposal-based methods: 
	+ first generate the object detection bounding boxes and then perform mask prediction on each box for instance segmentation.
+ segmentation-based methods

### About the OANet:

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/17-OANet/02.png" width="80%" />
</div>
We employ FPN as the backbone architecture for the end-to-end network.

### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
Traditionally, in panoptic segmentation algorithms, the instance and stuff segmentation blocks are independent without any feature sharing. This results in apparent **computational overhead**.

At the merging period, without the context information between the stuff and thing, the merge process will face the challenge of **overlapping relationships** between instances and stuff.

### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
+ We incorporate the instance segmentation and stuff segmentation **into one network**, which shares the backbone features but applies different head branches for the two tasks.
+ To solve the problem of overlapping relationship between object instances, we introduce a new algorithm called **Spatial Ranking Module**. This module learns the ranking score and offers an ordering accordance for instances.

### 3. Details about the experiment

#### 3.1 Which Datasets are used?



#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 Ablation Study



#### 3.5 What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)