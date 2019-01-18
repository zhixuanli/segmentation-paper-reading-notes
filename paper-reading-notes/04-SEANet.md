### The progress of the reading plan: 
4 / 50

## Paper Information
#### Paper Title : 
Self-Ensembling Attention Networks: Addressing Domain Shift for Semantic Segmentation

(Not released to public yet)

#### Conference : 
AAAI 2019

#### Authors and Institutions
##### Authors
+ Yonghao Xu 1;2
+ Bo Du 1
+ Lefei Zhang 1
+ Qian Zhang 3
+ Guoli Wang 3
+ Liangpei Zhang 2

##### Institutions

+ 1 School of Computer Science , Wuhan University, Wuhan 430072, P. R. China.
+ 2 State Key Laboratory of Information Engineering in Surveying, Mapping, and Remote Sensing, Wuhan University, Wuhan 430079, P. R. China.
+ 3 Horizon Robotics, Inc., Beijing 100190, P. R. China.

#### Official Codes
[https://github.com/YonghaoXu/SEANet](https://github.com/YonghaoXu/SEANet)

#### Network Structure

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/04-SEAN-01.png" width="80%" height="80%" />
</div>


## Notes

This paper propose a self-ensembling structure that ensembling the learning ability of teacher network and student network in the same time.

The source domain images are only feed into the student networks, and the target domain images will be feed into both networks. Here, only the source domain images have the ground truth labels, and the target domain don't have.

**Attention modules** are used for focusing on the important areas to reduce the gap between the two domains.

The final loss function is composed by two components, the segmentation loss, defined by cross entropy loss that calculates the loss between the semantic segmentation results in source domain and its ground truth masks, and the consistency loss, defined by mean square error that measures the difference between the prediction map of student and teacher network.

The two networks have the same architecture, sounds like the siamese network.

Here we should notice that the teacher network doesn't participate in the back propagation, so its parameters are updated by the student network and its own parameters in the last iteration.

And we can find that, **the consistency loss** is not defined by measuring the difference between network predictions and the corresponding ground truth labels. The way it's defined, is helpful to make sure that the student network can learn from the target domain as well as the teacher network, when in the same time it's also learning from the source domain.

**I think the definition of the consistency loss to utilize the teacher network to supervise the student network to learning simultaneously from both domain is the most amazing idea in this paper.**



#### Useful small techniques summary

1. Stochastic Augmentation:  

   Stochastic augmentation is implemented for images in both source and target domains to increase the generalization ability of the model.

   It's derived from  [French, G.; Mackiewicz, M.; and Fisher, M. 2018. Self-ensembling for visual domain adaptation. In International Conference on Learning Representations (ICLR) .](https://openreview.net/pdf?id=rkpoTaxA-)

   Codes for reference: [https://github.com/Britefury/self-ensemble-visual-domain-adapt/blob/df4e9518d8a4ac2250bb919172651e5a9567861d/augmentation.py](https://github.com/Britefury/self-ensemble-visual-domain-adapt/blob/df4e9518d8a4ac2250bb919172651e5a9567861d/augmentation.py)

2. The exponential moving average method is used to update the parameters in the teacher network. This is helpful when you don't want some branch of network participate in the back propagation and you still want to update its parameters.

#### Key words:

Attention module, domain adaption

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve?

1. Pixel-level annotations are laborious to collect, so developing algorithms for adapting labeled data from source domain to target domain is important.
2. Domain shift phenomenon, which means the gap between adapting knowledge from source domain to target domain, is an important bad factor when applying the domain adaption method.

### 2. [Contribution] What's new in this paper?

1. Different from the previous  domain adaptation methods mainly utilize adversarial training to reduce the domain gap, this paper propose  a self-ensembling model which utilize the teacher network to learning from the target domain and supervise the student network to learn well from the two domains, which provide  a new and different viewpoint on how to learn domain-invariant features for semantic segmentation.
2. For different regions in the image usually correspond to different levels of domain gap, attention module is used to give more attention to  those noteworthy regions.


### 3. Details about the experiment
#### 3.1 Which Datasets are used?

+  target domain:  CITYSCAPES
+  source domain:  
  + SYNTHIA (Ros et al. 2016) 
    + SYNTHIARAND- CITYSCAPES subset that contains 9400 images with annotations which are compatible with CITYSCAPES dataset. The 16 common categories between SYNTHIA and CITYSCAPES are selected to make quantitative assessment. These classes are: road, sidewalk, building, wall, fence, pole, light, sign, vegetation, terrain, sky, person, rider, car, truck, bus, train, motorcycle, and bicycle.
  + GTA-5 (Richter et al. 2016)


#### 3.2 How is the experiment set up?

1. the backbone networks

we employ the DeepLab-v2 (Chen et al. 2018) with VGG-16 (Simonyan and Zisserman 2014) model pre-trained on ImageNet (Deng et al. 2009) and Pascal VOC datasets (Everingham et al. 2010) as the backbone networks.

#### 3.5 (Optional）What is the ranking of the experiment results?
Experiment results
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/04-SEAN-02.png" width="100%" height="100%" />
</div>

Visualization of results
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/04-SEAN-03.png" width="100%" height="100%" />
</div>

Attention visualization
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/04-SEAN-04.png" width="60%" height="60%" />
</div>

### 5. Disadvantages (self-summary rather than the author's)

+ Some representations are literally repeated for many times.
+ Ensembling network usually means ensembling many different networks to achieve the better performance. Here only one archetecture is used for both student and teacher networks. Maybe the term of "ensembling" is very not suitable here.
+ Experiments result on SYNTHIA datasets is not showed for comparing different methods.