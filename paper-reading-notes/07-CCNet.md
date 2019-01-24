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
+ 1 School of EIC, Huazhong University of Science and Technology+ 2 Horizon Robotics+ 3 Beckman Institute, University of Illinois at Urbana-Champaign


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



### Key Words



## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
These attention-based methods need to generate huge attention maps to measure the relationships for each pixel-pair, whose complexity in time and space are both **O((HxW)x(HxW))**.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
A criss-cross attention module that only aggregate long-range pixel-wise contextual information in horizontal and vertical direction is proposed.

By serially stacking two criss-cross attention modules, it can collect contextual information from all pixels.

The decomposition greatly reduce the complexity in time and space to O((HxW)x(H+W-1)).


### 3. Details about the experiment

#### 3.1 Which Datasets are used?



#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?



#### 3.4 (Optional）How to divide training data and test data？



#### 3.5 (Optional）What is the ranking of the experiment results?



### 4. Advantages (self-summary rather than the author's)



### 5. Disadvantages (self-summary rather than the author's)
1. During the time of stacking, whether the complexity will be very big? Because O((HxW)x(H+W-1)) is for one attention module computation, but when passing all the criss-cross for ont postion, will not the complexity become huge?