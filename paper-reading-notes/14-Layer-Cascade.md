### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 15 | 14 | 50 |

## Paper Information
#### Paper Title : 
[Not All Pixels Are Equal: Difficulty-Aware Semantic Segmentation via Deep Layer Cascade](https://arxiv.org/abs/1704.01344) 

#### Conference : 
CVPR 2017

#### Authors and Institutions
##### Authors
+ Xiaoxiao Li 1 
+ Ziwei Liu 1 
+ Ping Luo 2;1 
+ Chen Change Loy 1;2 
+ Xiaoou Tang 1;2

##### Institutions
+ 1 Department of Information Engineering, The Chinese University of Hong Kong+ 2 Shenzhen Key Lab of Comp. Vis. & Pat. Rec., Shenzhen Institutes of Advanced Technology, CAS, China


#### Official Codes
[https://github.com/liuziwei7/region-conv](https://github.com/liuziwei7/region-conv)

#### Some articles to comprehend this paper
+ [图像分割“Not All Pixels Are Equal: Difficulty-Aware Semantic Segmentation via Deep Layer Cascade”](https://blog.csdn.net/cv_family_z/article/details/72625048)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/01.png" width="120%" />
</div>

## Note

### How to divide different difficulties?
+ Easy Set(ES): correct classified confidence > 95%
+ Hard Set(HS): misclassified confidence > 95%
+ Moderate Set(MS): covers pixels that have classification scores smaller than 0.95

### Network
IRNet is turned into LC by dividing its different components as different stages.

In addition, we append two convolutional layers and a softmax loss at the end of each stage. 

In this case, the original IRNet with one loss function develops into multiple stages, where each stage has its own loss function. So multi-stage training is applied.

#### Details about stage-1:
In the first stage, given a 3x512x512 image I, stage-1 predicts a 21x64x64 segmentation label map L1, where each 21x1 column vector, denoted as $L^1_i ∊ R^{21x1}$, indicates the probabilities (confidence scores) of the i-th pixel belonging to 21 object categories in VOC respectively.

Using the softmax function to let $∑^{21}_{j=1}L^1_{ij}=1$.

If the maximum score of the i-th pixel, $l^1_i = max(L^1_i)$ and $l^1_i ∊$ {$L^1_{ij}|j=1...21$}, is larger than a threshold 𝝆, we accept its prediction and do not propagate it forward to stage-2.

#### Region Convolution
As presented above, stage-2 and -3 only calculate convolutions on those pixels that have been propagated forward.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/03.png" width="60%" />
</div>

So region convolution is used here.


## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/02.png" width="80%" />
</div>

Pixels in each classes are divided by three level of difficulties. And ES (easy set) occupies at least 30% pixels of most objects. The right one reveals that 70% pixels in HS are located at object boundaries, which have large ambiguity.

So we should focus on the hard set more.


### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
#### Contribution:
+ Layer Cascade (LC) approach is proposed to significantly **reduce computations** while improving the segmentation accuracies.
+ LC’s properties can be easily applied to many recent advanced network structures.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ PASCAL VOC 2012
+ Cityscapes

#### 3.2 How is the experiment set up?
Cascade Training:

Similar to the previous step, all stages are trained jointly, but different stages minimize their pixel-wise softmax losses with respect to different regions.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/04.png" width="60%" />
</div>

#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study and Results
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/05.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/06.png" width="70%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/07.png" width="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/08.png" width="60%" />
</div>

#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/09.png" width="90%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/10.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/15-Layer-Cascade/11.png" width="80%" />
</div>

### 4. Advantages (self-summary rather than the author's)
It reveals that some pixels are harder to be classified. But with the net going deeper, the recognition ablity also is increasing. It's hard to say the performance advance comes from the multi-stage method.


### 5. Disadvantages (self-summary rather than the author's)
+ After applying LC on Inception-ResNet-v2 (IRNet) [32], its speed and accuracy are improved by 42.8% and 1.7%, respectively. So the main contribution is on the speed, not the accuracy. But this idea is really interesting.

But I really believe the hard classes's samples are the bottleneck of semantic segmentation, not the edges of each object. So maybe a better method should be proposed.

### 6. Don't understand
Secondly, as feature maps with high resolution consume a large amount of GPU memory in the learning process, they limit the size of minibatch (e.g. 8), making the batch normalization (BN) layers [14] unstable (as which need to estimate sample mean and variance from the data in a mini-batch). We cope with this issue by simply fixing the values of all parameters in BNs. This strategy works well in practice.