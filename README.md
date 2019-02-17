# Paper-reading-notes
**segmentation paper reading notes**

## Semantic segmentation paper list reference: 
1. [语义分割 - Semantic Segmentation Papers](http://www.aiuai.cn/aifarm62.html)
2. [arXiv Search result: Semantic Segmentation](https://arxiv.org/search/advanced?advanced=&terms-0-operator=AND&terms-0-term=Semantic+Segmentation&terms-0-field=title&classification-computer_science=y&classification-physics_archives=all&classification-include_cross_list=include&date-filter_by=all_dates&date-year=&date-from_date=&date-to_date=&date-date_type=submitted_date&abstracts=show&size=50&order=-announced_date_first)
3. [A collection of AWESOME things about domain adaptation](https://github.com/zhaoxin94/awsome-domain-adaptation#semantic-segmentation)
4. [https://zhangbin0917.github.io/2018/09/18/Semantic-Segmentation/#more](https://zhangbin0917.github.io/2018/09/18/Semantic-Segmentation/#more)
5. [AAAI 19 Accepted_Papers](https://aaai.org/Conferences/AAAI-19/wp-content/uploads/2018/11/AAAI-19_Accepted_Papers.pdf)

   

## CATALOGS
1. [Summary of the semantic segmentation datasets](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#summary-of-the-semantic-segmentation-datasets)
	1. [PASCAL VOC 2012](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#1-pascal-voc-2012)
	2. [Semantic Boundaries Dataset (SBD)](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#2-semantic-boundaries-dataset-sbd)
	3. [PASCAL VOC 2012 augmented with SBD](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#3-pascal-voc-2012-augmented-with-sbd)
	4. [The COCO-Stuff dataset](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#4-the-coco-stuff-dataset)
	5. [PASCAL-Context Dataset](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#5-pascal-context-dataset)
	6. [Cityscapes Datasets](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#6-cityscapes-datasets)
	7. [PASCAL-$5^i$ (for shot learning)](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#7-pascal-5i-for-shot-learning)
	8. [SYNTHIA](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#8--synthia)
	9. [GTA-5](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#9--gta-5)
	10. [ADE20K](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Summary%20of%20the%20semantic%20segmentation%20datasets.md#10-ade20k)
2. [Paper Reading Template](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/PaperReadingTemplate.md)
3. [Experiment Result Collecting](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/Experiment%20Result%20Collecting.xlsx)
3. [语义分割-知识点总结](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/%E8%AF%AD%E4%B9%89%E5%88%86%E5%89%B2-%E7%9F%A5%E8%AF%86%E7%82%B9%E6%80%BB%E7%BB%93.md)
	+ [Depth-wise separable convolution](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/%E8%AF%AD%E4%B9%89%E5%88%86%E5%89%B2-%E7%9F%A5%E8%AF%86%E7%82%B9%E6%80%BB%E7%BB%93.md#1-depthwise-separable-convolution)
	+ [atrous convolution 带洞卷积](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/%E8%AF%AD%E4%B9%89%E5%88%86%E5%89%B2-%E7%9F%A5%E8%AF%86%E7%82%B9%E6%80%BB%E7%BB%93.md#2-atrous-convolution-%E5%B8%A6%E6%B4%9E%E5%8D%B7%E7%A7%AF)
	+ [Spatial pyramid pooling](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/%E8%AF%AD%E4%B9%89%E5%88%86%E5%89%B2-%E7%9F%A5%E8%AF%86%E7%82%B9%E6%80%BB%E7%BB%93.md#3-spatial-pyramid-pooling)
	+ [Xception model](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/others/%E8%AF%AD%E4%B9%89%E5%88%86%E5%89%B2-%E7%9F%A5%E8%AF%86%E7%82%B9%E6%80%BB%E7%BB%93.md#4-xception-model)

## Experiment Results
Experiment Results on Cityscapes testing set, collected by myself.

About the other datasets, please read this file: [Experiment Result Collecting.xlsx](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/others/Experiment%20Result%20Collecting.xlsx)

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/CityScape-exp-result.png" width="70%" height="70%" />
</div>

## PROGRESS

Details of the papers are collected in the notes. 
"My Rating" is my personal rating of these papers from 1-10, from bad to good.


| Index  |  Net Name | Conference | Papers Title | Note Links | Code | My Rating |
| :----: | :-------: | :--------: | :----------: | :--------: | :--: | :-------: |
| 01 | DeepLabV3+ | ECCV 2018 | [Encoder-Decoder with Atrous Separable Convolution for Semantic Image Segmentation](https://arxiv.org/abs/1802.02611) | [01-DeepLabV3+.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/01-DeepLabV3%2B.md) | [Official Code](https://github.com/tensorflow/models/tree/master/research/deeplab) | 8 |
| 02 | DANet | NO | [Dual Attention Network for Scene Segmentation](https://arxiv.org/abs/1809.02983) | [02-DANet.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/02-DANet.md) | [Official Code](https://github.com/junfu1115/DANet) | 7 |
| 03 | A-MCG | AAAI 2019 | [Attention-based Multi-Context Guiding for Few-Shot Semantic Segmentation](https://pdfs.semanticscholar.org/1216/eebb5a407b40eb46596073f0fd229acaea48.pdf) | [03-A-MCG network.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/03-A-MCG%20network.md) | NO | 5 |
| 04 | SEANet | AAAI 2019 | Self-Ensembling Attention Networks: Addressing Domain Shift for Semantic Segmentation | [04-SEANet.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/04-SEANet.md) | [Official Code](https://github.com/YonghaoXu/SEANet) | 6 |
| 05 | ExFuse | ECCV 2018 | [ExFuse: Enhancing Feature Fusion for Semantic Segmentation](https://arxiv.org/abs/1804.03821) | [05-ExFuse.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/05-ExFuse.md) | NO | 7 |
| 06 | OCNet | NO | [OCNet: Object Context Network for Scene Parsing](https://arxiv.org/abs/1809.00916) | [06-OCNet.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/06-OCNet.md) | [Official Code](https://github.com/PkuRainBow/OCNet.pytorch) | 4 |
| 07 | CCNet | NO | [CCNet: Criss-Cross Attention for Semantic Segmentation](https://arxiv.org/abs/1811.11721) | [07-CCNet.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/07-CCNet.md) | [Official Code](https://github.com/speedinghzl/CCNet) | 6 |
| 08 | DFN  | CVPR18 Spotlight | [Learning a Discriminative Feature Network for Semantic Segmentation](http://openaccess.thecvf.com/content_cvpr_2018/papers/Yu_Learning_a_Discriminative_CVPR_2018_paper.pdf) | [08-DFN.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/08-DFN.md) | [Inofficial Code](https://github.com/lxtGH/dfn_seg) | 6 |
| 09 | PSPNet | CVPR 2017 | [Pyramid Scene Parsing Network](http://openaccess.thecvf.com/content_cvpr_2017/papers/Zhao_Pyramid_Scene_Parsing_CVPR_2017_paper.pdf) | [09-PSPNet.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/09-PSPNet.md) | [Official Code](https://github.com/hszhao/PSPNet) | 3 |
| 10 | \ | Artificial Intelligence Review 2018 | [Recent progress in semantic image segmentation](https://arxiv.org/pdf/1809.10198) | [10-SegReview18.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/10-SegReview18.md) | NO | 4 |
| 11 | AAF | ECCV 2018 | [Adaptive Affinity Fields for Semantic Segmentation](http://openaccess.thecvf.com/content_ECCV_2018/papers/Jyh-Jing_Hwang_Adaptive_Affinity_Field_ECCV_2018_paper.pdf) | [11-AAF.md](https://github.com/zhixuanli/segmentation-paper-reading-notes/blob/master/paper-reading-notes/11-AAF.md) | [Official Code](https://github.com/twke18/Adaptive_Affinity_Fields) | * |