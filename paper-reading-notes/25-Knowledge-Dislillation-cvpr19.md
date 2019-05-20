### The progress of the reading plan: 
| Index  |  All |
| :----: | :--: |
| 25 | 50 |

## Paper Information
#### Paper Title : 
[Structured Knowledge Distillation for Semantic Segmentation](https://arxiv.org/abs/1903.04197) 

#### Conference : 
CVPR 2019

#### Authors and Institutions
##### Authors
+ Yifan Liu 1 
+ Ke Chen 2 
+ Chris Liu 2 
+ Zengchang Qin 3;4 
+ Zhenbo Luo 5 
+ **Jingdong Wang** 2

##### Institutions
+ 1 The University of Adelaide 
+ 2 Microsoft Research Asia 
+ 3 Beihang University
+ 4 Keep Labs, Keep Inc. 
+ 5 Samsung Research China

## Note
### Baseline Paper and network
First have a look at the improvement after knowledge distillation.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/01.png" width="60%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/02.png" width="60%" />
</div>

Knowledge distillation tries to use a cumbersome (complex, such as PSPNet) segmentation network T as a teacher to teach the learning process of a compact (lightweight, such as mobilenet) segmentation network S (student).

The former papers only used the pixel-wise distillation. Here two other methods are used.


### Improvement
Two distillation methods are presented:

+ pair-wise
+ holistic

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/03.png" width="80%" />
</div>

There are 3 loss applied to supervise respectively at the stage of feature map extracting, prediction and using GANs loss to supervise.

The similarity map is constructed by computing the similarity between two pixels.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/06.png" width="30%" />
</div>

Here the cosine distance is applied.

#### Details of the three distillation methods:

##### Pixel-wise:
KL divergence:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/04.png" width="30%" />
</div>

##### Pair-wise
squared difference
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/05.png" width="30%" />
</div>

##### Holistic
High-order relations between the segmentation maps produced by the two kind of networks.

Here the GAN part I'm not familiar.

### Ablation Study for proposed part
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/07.png" width="60%" />
</div>

1. ImN: Pretrained on ImageNet is really useful!

### Visualization of the result
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/25-Knowledge-Dislillation-cvpr19/08.png" width="80%" />
</div>
Look at the bottom row!

### My Summary
It's the first time to know how to do distillation, and it's really powerful and interesting. Maybe in a practical project when deploying on mobile phone I'll try it.