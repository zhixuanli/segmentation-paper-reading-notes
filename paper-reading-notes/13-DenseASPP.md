### The progress of the reading plan: 
| Index  |  Semantic Seg | All |
| :----: | :-------: | :-------: |
| 14 | 13 | 50 |

## Paper Information
#### Paper Title : 
[DenseASPP for Semantic Segmentation in Street Scenes](http://openaccess.thecvf.com/content_cvpr_2018/papers/Yang_DenseASPP_for_Semantic_CVPR_2018_paper.pdf) 

#### Conference : 
CVPR 2018

#### Authors and Institutions
##### Authors
+ Maoke Yang 
+ Kun Yu 
+ Chi Zhang 
+ Zhiwei Li 
+ Kuiyuan Yang


##### Institutions
DeepMotion Inc.


#### Official Codes
[https://github.com/DeepMotionAIResearch/DenseASPP](https://github.com/DeepMotionAIResearch/DenseASPP)

#### Some articles to comprehend this paper
[语义分割--(DenseASPP )DenseASPP for Semantic Segmentation in Street Scenes](https://blog.csdn.net/u011974639/article/details/80844304)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/14-DenseASPP/01.png" width="100%" />
</div>

## Note
This paper belongs to the branch of enrich the information of features. Though the struture seems easy, but this kind of method is really useful.


### Key Words

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
+ Atrous convolution is proposed to enlarge the size of reception field and dicrease the cost of computing simultaneously.
+ ASPP is proposed to concatenate feature maps generated by atrous convolution with different dilation rates.

But when high resolution images are used as the input of segmentation methods, the size of reception field never becomes big enough. And large enough dilation ratio will decrease the power of model. 

Therefore, it is important to design a network structure that is able to encode multi-scale information, and simultaneously achieves a large enough receptive field size.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/14-DenseASPP/02.png" width="80%" />
</div>

PS: deeper network will have bigger receptive field, so actually I'dont think it's a big problem.
### 2. [Contribution / Method] What's new in this paper? / How does this paper solve the above problems?
The network structure is neat and articulate. 

Multi-grid features are merged together to get bigger receptive field and in the same time remaining the rich information.


### 3. Details about the experiment

#### 3.1 Which Datasets are used?
+ CityScapes


#### 3.2 How is the experiment set up?



#### 3.3 What's the evaluation metric?
mIoU


#### 3.4 Ablation Study



#### 3.5 What is the ranking of the experiment results?
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/14-DenseASPP/03.png" width="80%" />
</div>


### 4. Advantages (self-summary rather than the author's)
1. This idea is very simple, but write such a long paper is hard. It's good for us to read this papaer carefully for many times.
2. The experiment contains in this paper is really comprehensive.
3. The charts are beautiful!


### 5. Disadvantages (self-summary rather than the author's)
1. Different level of layers contain different amount of information. So may be some layer is more important than the other layers. If we add the attention module here, the better performance will be reached.
2. Further more, for faster computation, we can take apart the kernel of atrous convolution from kxk to kx1 and 1xk.