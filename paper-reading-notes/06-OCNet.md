### The progress of the reading plan: 
06 / 50

## Paper Information
#### Paper Title : 
[OCNet: Object Context Network for Scene Parsing](https://arxiv.org/abs/1809.00916) 

#### Conference : 
NO

#### Authors and Institutions
##### Authors
+ Yuhui Yuan
+ Jingdong Wang

##### Institutions
Microsoft Research

#### Official Codes
[https://github.com/PkuRainBow/OCNet.pytorch](https://github.com/PkuRainBow/OCNet.pytorch)

#### Articals for understanding
In Chinese, by the OCNet's author.

[Object Context：通往更好的场景分割算法 （以及最新的Fast-OCNet）](https://zhuanlan.zhihu.com/p/43902175)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/06-OCNet-01.png" width="80%" height="80%" />
</div>

## Note


### Key Words
object context pooling (OCP) scheme; robust


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
1. Existing representative works mainly exploit the context formed from spatially nearby or sampled pixels. The region of the pixel context is the limitation of the segemtation performance.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
Object context map is proposed to aggregate pixels belonging to the same class. This OCP module can be combined with may structures such as ASPP and Pyramid Pooling.
The object context map can be regarded as an attention mechanism that for each pixel to pay attention to the pixels in the same class. This also can be considered as a pooling progress.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/06-OCNet-02.png" width="80%" height="80%" />
</div>


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ Cityscapes+ ADE20K
+ LIP


#### 3.2 How is the experiment set up?
Online hard example mining (OHEM), multi-scale (Ms), left-right flipping (Flip), and fine-tune and training with validation set (w/ Val) methods are used to further boost the performance.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/06-OCNet-03.png" width="80%" height="80%" />
</div>

#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 (Optional）How to divide training data and test data？



#### 3.5 (Optional）What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/06-OCNet-04.png" width="80%" height="80%" />
</div>

Better than DANet is impressive !!!

I really doubt about the auxillary methods such as OHEM, Ms, and Flip improved too much performance of the OCNet.


### 4. Advantages (self-summary rather than the author's)
1. The object context map which can be considered as a auxilary tool to redistribute the importance of each pixels. The figure of object context map is very impressive.
2. It's really a smart behaviour to combine the ASPP and Parymid Pooling module (PPM).


### 5. Disadvantages (self-summary rather than the author's)
1. The statement of the problems in the existing works is not very clear.
2. What is "representation vectors" and "query transform function" and "the key transform function"? What is the range of the variable i in equation 1? Details of the key equation is not fully illustrated.
3. Comparing with DANet, OCNet lacks the attention of channel. But OCNet has a clearer illustration of the "position module".
4. Comparing with BiSeNet make me feel embarrassed for the BiSeNet is a real-time method.
5. ASPP is the better version of the PPM module, this relationship is not showed in the paper.