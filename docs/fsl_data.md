## Datasets for Zero shot learning
**数据集简介**

Zero-Shot Learning数据集用于建立 **视觉特征** 和 **语义特征** 的联系。因此，一个ZSL数据集既包含图像，也包含相应的语义特征。语义特征是一个向量，有如下几种形式：

- 属性（颜色、形状、大小等）
- 词向量 
- 文本描述

语义特征的特点是：**相似的图像具有相似的语义特征。**  现有ZSL方法即针对该特性进行建模。

---

### Animal With Attributes (AWA) [[AWA网址]](https://cvml.ist.ac.at/AwA/) [[AWA2网址]](https://cvml.ist.ac.at/AwA2/)
AWA数据集包含50种常见动物的**图像**与**属性**。其具体细节在论文[[Learning to detect unseen object classes by between-class attribute transfer]](http://ieeexplore.ieee.org/document/5206594/)中描述。

- 图像：AWA包含30475张(AWA2：37322张)图像，分为50个类别，每类别至少92张。这些图像来自Google, Microsoft, Yahoo and Flickr等搜索引擎的检索结果。其中重复、难以清晰辨认的检索结果被剔除，因此AWA是一个较为理想化的数据集。

- 语义信息：属性，**每个类别**标注了real-value属性，共85项属性。这些属性的值是由人类专家根据*relative strength of association*原则 **主观确定** ，其具体过程参见论文第4节。

--- 
### aPascal & Yahoo (APY) [[APY网址]](http://vision.cs.uiuc.edu/attributes/) 

APY数据集包含32种日常生活常见物体的**图像**、**Boundbox**与**属性**。其细节在论文[[Describing objects by their attributes]](http://ieeexplore.ieee.org/document/5206772/)[作者Ali Farhadi,YOLO通讯作者]中描述。

- 图像：APY包含15339个Boundbox图像(有的jpg文件含有多个boundbox)。是两个数据集aPascal(VOC 2008的一个子集,12695张)和aYahoo(2644张)的综合，包含了32种日常生活中常见的类别。其中20个类别来自于VOC2008:
	- **Person**: person
	- **Animal**: bird, cat, cow, dog, horse, sheep
	- **Vehicle**: aeroplane, bicycle, boat, bus, car, motorbike, train
	- **Indoor**: bottle, chair, dining table, potted plant, sofa, tv/monitor  
	12个类别来自于Yahoo:
	- **Animal**: donkey, monkey, goat, wolf, zebra, centaur
	- **Vehicle**: jetski, carriage
	- **Indoor**: mug, bag
	- **Outdoor**: statue, building

- 语义信息：属性，**每张图片**标注了64种常见属性，0-1属性，表示某个特性存在或不存在，用土耳其机器人标注获得。

- 注意事项：
	- [APY网址]中的VOC2008链接失效，请使用[[VOC2008-new]](http://pascallin.ecs.soton.ac.uk/challenges/VOC/voc2008/)
	- APY包含许多噪声，其中Person类别（来自VOC2008）的图像达到了5071张。因此ZSL已经逐步弃用这个数据集。

- 论文的启示：
	- 0. 泛化问题在Few shot问题当中依然存在，但是并不能用传统的Variance来刻画。 
	- 1. 提出了Correlation问题，指出一个刻画attr过拟合的指标。 
	- 2. 用特征x去学习属性a，学到的映射是依赖于数据集的。本文提出了解决这一依赖的方法。
	- 3. Discriminative属性是提升泛化能力的关键，但是数据集中只给出了64维semantic属性。
	- 4. 属性和feature map的某个局部是有对应关系的。许多时候“摩托车”出现了“皮肤”这一属性(见图8和6.1.2节)，是因为所选图片的Boundbox中还包含了人。

---
### The Caltech-UCSD Birds-200-2011 Dataset (CUB) [[数据集地址]](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) [增强数据集[CUB+Sentences]](https://drive.google.com/open?id=0B0ywwgffWnLLZW9uVHNjb2JmNlE)

CUB数据集包含200种北美地区常见的鸟类,包含**图像**、**Segmentation**、**Boundbox**与**属性**。其细节在技术报告[[Caltech-UCSD Birds 200]](http://www.vision.caltech.edu/visipedia/papers/WelinderEtal10_CUB-200.pdf)和[[The Caltech-UCSD Birds-200-2011 Dataset]](http://authors.library.caltech.edu/27452/1/CUB_200_2011.pdf)中描述。

- 图像：CUB包含11788张图像。包含了200种不同的北美鸟类照片。图像还包含了Segmentation和Boundbox的标注。以及给出了鸟类各部位（啄、左翼、右翼、左眼、右眼）的中心位置(没有Boundbox)。

- 语义信息：属性，**每张图片**标注了312维的0-1属性（本质是28维离散取值的属性转化成的one-hot向量），1表示某个特性存在(0不存在)。这些属性涵盖了鸟类的各部位的颜色和形状。每个属性还给出了人工标注的犹豫时间和确信程度。

- 外部信息：数据集为**每张图片**提供了10个句子的描述。详见：[论文[Learning Deep Representations of Fine-Grained Visual Descriptions.]](http://ieeexplore.ieee.org/document/7780382/)。文中使用text based CNN+RNN将句子向量化。

---
### FLO [数据集地址](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/) [增强数据集[Flower+Sentences]](https://drive.google.com/open?id=0B0ywwgffWnLLcms2WWJQRFNSWXM)

FLO数据集包含102种英国常见的花,包含**图像**、**Segmentation**、**文本描述**。其细节在论文报告[[Automated Flower Classification over a Large Number of Classes]](http://www.robots.ox.ac.uk/~vgg/publications/papers/nilsback08.pdf)中描述。

- 图像：FLO包含8189张图片, 102个类别的不同种类的花。每类有40到258张的图片。图片样例详见[这里](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/categories.html)

- 语义信息：FLO**不提供属性**


- 外部信息：数据集为**每张图片**提供了10个句子的描述。详见：[论文[Learning Deep Representations of Fine-Grained Visual Descriptions.]](http://ieeexplore.ieee.org/document/7780382/)。文中使用text based CNN+RNN将句子向量化。

---
### Dogs [数据集地址](http://vision.stanford.edu/aditya86/ImageNetDogs/)

Dogs数据集包含113种常见的狗,包含**图像**、**Boundbox**。其细节在论文[[Novel dataset for Fine-Grained Image Categorization]](http://people.csail.mit.edu/khosla/papers/fgvc2011.pdf)中描述。

- 图像:Dogs包含19499张图片，113个类别的狗狗。数据来源于ImageNet当中所有包括狗的类别，小于200x200的图像被剔除。其中重复、难以清晰辨认的检索结果被剔除，因此Dogs是一个较为理想化的数据集。


- 语义信息：Dogs**不提供属性**，通常使用Label的Word2vec代替，或WordNet的Hierarchical Embedding作为语义信息。

- 数据集特性：Dogs不同于CUB和Flowers，该数据集上，Word2vec并不能很好的描述语义信息，反而BoW(某种狗对于的Wiki文档的BoW)能够较好地描述。参见论文[[Evaluation of output embeddings for fine-grained image classification]](http://ieeexplore.ieee.org/document/7298911/)

---

### Scene UNderstanding (SUN) Attribute [SUN attribute数据集地址](http://cs.brown.edu/~gmpatter/sunattributes.html)


SUN Attribute 是一个场景数据集，包含**图像**和**属性**

SUN是一个大规模数据集[完整SUN数据集地址](http://vision.princeton.edu/projects/2010/SUN/)，用于Zero-shot Learning的是该数据集的一个子集，称为SUN attribute。该子集包含707类不同场景，其场景之间存在3层[树形隶属关系](http://vision.princeton.edu/projects/2010/SUN/hierarchy/)。其细节参见论文：[[The SUN Attribute Database: Beyond Categories for Deeper Scene Understanding]](https://link.springer.com/content/pdf/10.1007%2Fs11263-013-0695-z.pdf)

- 图像：707类，14140张图像，每类20张。

- 语义信息：**每张图像属性**：102维，包含材质、表面性质、光照、档次、空间排布等，**离散取值：0，1/3，2/3，1**。
	- 离散取值的产生方式：3个标注者进行0-1属性标注，对其标注结果取平均得到上述离散取值。

- 适应任务：场景分类、ZSL、Caption、基于文本的search、Image parsing、Image Descriptor。
- 论文启示：
-
	- 讲解了标注的详细过程——如何剔除不可靠的标注。
	- 图11讲解了feature对预测属性的贡献。
	- 5.2第二段重申了属性相关的问题
	- 5.2对图15的解释是很好的定性分析的例子。
	- 6揭示了良好属性的性质：1.相互独立 2.与label一致。
		- 有没有可能做正交变换，得到一组正交基。其物理意义由原基的线性组合系数在Word2Vec空间中找。
	- 6.1.1 最后一段，预测Attr和真实attr之间存在GAP，这又是一个Variance和Bias的问题。
	- 6.1.2 倒数第三段，证实classifier需要知道全部类别的attr
	- 第7节讲解了用于自动标注。
	- 相对属性可能有用 
- ImageNet 21K
- ImageNet 1K
