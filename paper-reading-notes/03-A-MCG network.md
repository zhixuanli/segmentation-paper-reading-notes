### The progress of the reading plan: 
3 / 50

## Paper Information
#### Paper Title : 
[Attention-based Multi-Context Guiding for Few-Shot Semantic Segmentation](https://www.google.com.hk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=2ahUKEwiq9NOzpuXfAhUKybwKHSrBDTkQFjABegQIABAC&url=https%3A%2F%2Fpdfs.semanticscholar.org%2F1216%2Feebb5a407b40eb46596073f0fd229acaea48.pdf&usg=AOvVaw2z0pB6k3R4zdgLhFZiQcFM) 

#### Conference : 
AAAI 2019

#### Authors and Institutions
##### Authors
+ Tao Hu 1;2,
+ Pengwan Yang 2, 
+ Chiliang Zhang 3, 
+ Gang Yu 4, 
+ Yadong Mu 2, 
+ Cees G. M. Snoek 1##### Institutions+ 1 University of Amsterdam, the Netherlands+ 2 Peking University, China+ 3 Tsinghua University, China+ 4 Megvii Inc. (Face++), China
#### Official Codes
NO 

#### Network Structure
![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-network.png)

Conv-LSTM module:
![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-network-conv-lstm.png)

RAM module:
![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-network-RAM.png)

## Five questions about this paper:

### 1. [Problem Definition / Motivation] What problem is this paper trying to solve? 
In the methods of few-shot semantic segmentation, there are some problems exists:
1. When guiding the support branch to query branch, the utilization of the support feature is in efficient.
2. The optimization on a large dataset is impossible for amount of the support and query data is often very small.
3. For multi-shot semantic segmentation, the fusion method, which is always the logical or operation in traditional way, lacks in exploring the inner relationship between different support images.

### 2. [Contribution] What's new in this paper? 
The proposed A-MCG network, has three contributions to solve the above problems:
1. Multi-scale context features between the support and query braches are integrated for more efficient utilization.
2. The Residual Attention Module(RAM) (Wang et al. 2017) is used here to make the concentration on the target class easier, avoiding to optimize on a large dataset.
3. Conv-LSTM (Xingjian et al. 2015) is incorporated for better fusing multi-shot support feature.

### 3. Details about the experiment
#### 3.1 Which Datasets are used?
[PASCAL-$5^i$ (Shaban et al. 2017)](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#7-pascal-5i-for-shot-learning)

#### 3.2 How is the experiment set up?

###### Training (some important details)
+ ImageNet pretrained ResNet
+ Xavier initialization for A-MCG module weight initialization
+ Layer Normalization (Ba, Kiros, and Hinton 2016) is utilized in our Conv-LSTM for speeding up convergence

#### 3.3 What's the evaluation metric?
mean intersection over union(mIoU)

#### 3.4 Ablation Study
The ablation study in this paper is very intact.

1. Multi-Context Guiding(MCG) architecture:
	+ fusion width. Fusion width is the channel number in the MCG branch
	+ multi-context pattern: For example, context-45 means that only features from Res-4, Res-5 are used for fusion.

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-exp1.png)

2. Attention Mechanism
	+ Spatial Attention: RAM method
	+ Channel Attention: SENet (Hu, Shen, and Sun 2018)

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-exp2.png)

3. Conv-LSTM

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-exp3.png)

#### 3.5 Experiment Results

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-exp4.png)

baseline: ResNet101-FCN

### 4. Advantages (self-summary rather than the author's)

1. Using Conv-LSTM as the fusion method is better:

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/A-MCG-exp5.png)

2. Multi level merging is common, but useful here.
3. Channel attention is not very helpful, and sometime will decrease the performance. But spatial attention is benifitial here.

### 5. Disadvantages (self-summary rather than the author's)
Some naive thoughts:

1. When comparing with OSLSM and co-FCN, the backbone is different. VGG is used for OSLSM and co-FCN but ResNet101 is used for A-MCG. As far as we know, ResNet101 is much better than VGG. And the baseline is ResNet101-FCN, it's structure is too simple. Actually using ResNet101 pretrained on ImageNet to be the backbone of OSLSM and co-FCN, and let them be the baselines, may be a fairer comparison.
2. The A-MCG network looks too complicated for imposing of so much techniques.