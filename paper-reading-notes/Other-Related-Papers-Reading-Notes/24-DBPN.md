### The progress of the reading plan: 
| Index  |  All |
| :----: | :--: |
| 24 | 50 |

## Paper Information
#### Paper Title : 
[Deep Back-Projection Networks For Super-Resolution](http://openaccess.thecvf.com/content_cvpr_2018/papers/Haris_Deep_Back-Projection_Networks_CVPR_2018_paper.pdf) 

#### Conference : 
CVPR 2018

#### Authors and Institutions
##### Authors
+ Muhammad Haris 1
+ Greg Shakhnarovich 2
+ Norimichi Ukita 1

##### Institutions
+ 1 Toyota Technological Institute, Japan 
+ 2 Toyota Technological Institute at Chicago, United States

## Note
### Baseline Paper and network
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/01.png" width="80%" />
</div>

Four kinds of deep upsampling methods:
1. interpolation to large size first, then pass conv
2. conv first, finally upsampling
3. conv and upsampling iteratively, gradually grow to SR size
4. [This paper] iteratively upsample and downsample, and finally concat all features after upsampling.

### Improvement and benefit
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/03.png" width="80%" />
</div>

Use dense connection to enhance the original DBPN, named as D-DBPN.

The details of up and down module:
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/02.png" width="80%" />
</div>

### Ablation Study for proposed part
#### up and down module set
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/04.png" width="80%" />
</div>

T is the number of up and down module set.

+ S: T=2
+ M: T=4
+ L: T=6

#### dense connection
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/07.png" width="80%" />
</div>

### Visualization of Result
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/05.png" width="80%" />
</div>

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/24-DBPN/06.png" width="80%" />
</div>

### My Summary
1. For each time when passing upsampling and down-sampling stage, the feature going to be processed is becoming stronger and having richer information.
	+ But going through so many stages looks like abundant, so in SRFBN(cvpr 19), the author simplify this progress to a RNN like structure to decrease the model size.
2. Upsampling helps to enlarge the size of the object in origin feature which can help the convolutional layer to "see more clearly", and downsampling helps to enlarge the receptive field size to cover bigger size object.
3. Dense connection doesn't help a lot. The meaning of residence shows when the inner layers haven't learn features well and residence can replace the weak feature to maintain the representative ability.