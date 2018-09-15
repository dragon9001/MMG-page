这里收录了零样本学习各个领域的最新文章。

- 20180612 CVPR-18 基于样本合成的广义的Zero-shot learning：[Generalized Zero-Shot Learning via Synthesized Examples](https://arxiv.org/abs/1712.03878)

- 20180623 CVPR-18 基于直推式无偏嵌入的零样本学习: [Transductive Unbiased Embedding for Zero-Shot Learning](https://arxiv.org/abs/1803.11320)
	- [我的解读](https://zhuanlan.zhihu.com/p/37891179)

- 20180623 CVPR-18 [Zero-Shot Visual Recognitionusing Semantics-Preserving Adversarial Embedding Network](https://arxiv.org/abs/1712.01928)
	- 文章利用GAN强制网络学习的视觉-语义特征能够重建图像，因而提高了所学特征的表现力
	- [中文解读](https://blog.csdn.net/feitianlzk/article/details/79910536)

- 20180623 CVPR-18 [Zero-Shot Visual Recognition
                    using Semantics-Preserving Adversarial Embedding Network](https://arxiv.org/abs/1712.01928)
	- 文章利用GAN强制网络学习的视觉-语义特征能够重建图像，因而提高了所学特征的表现力
	- [中文解读](https://blog.csdn.net/feitianlzk/article/details/79910536)

- 20180710 CVPR-10 [What Helps Where – And Why? Semantic Relatedness for Knowledge Transfer](https://link.zhihu.com/?target=http%3A//ieeexplore.ieee.org/document/5540121/)
	- 论文以零样本学习为例，在[AWA数据集](http://ieeexplore.ieee.org/document/5206594/)上探讨了语义与视觉两个Modality究竟借助怎样的知识库(Knowledge Base)才能更好地实现知识迁移(Knowledge transfer)，并将知识迁移到新任务（本文为Zero-shot Recognition）上。	
	- [我的解读,知乎专栏](https://zhuanlan.zhihu.com/p/39346361)

- 20180720 CVPR-11 [Evaluation of output embeddings for fine-grained image classification](https://link.zhihu.com/?target=http%3A//ieeexplore.ieee.org/document/7298911/)
	- 在零样本学习(ZSL)中，一个重要的问题是如何有效的从其他来源获取知识。现在通行的ZSL方法中。Word-Embedding/Attribute是主要的知识来源，统称为Semantic Embeddings。除了这两个知识离阿远，其他的知识来源也可能非常有效。本文在大规模数据集ILSVRC2010上，使用不同的Knowledge（Attribute或类别Hierarchy结构）来挖掘有效信息，并评估了这些Knowledge为分类任务带来的影响。
	- [我的解读，知乎专栏](https://zhuanlan.zhihu.com/p/40224345)

- 20180728 ICML-15 [Generative Moment Matching Networks](http://proceedings.mlr.press/v37/li15.pdf)
	- 在GAN发展热火朝天的当下，生成模型的其他方向显得有些势单力薄。GAN的一个薄弱环节在于Min-max Game问题的不易优化，该问题在WGAN中得到了较好的解决。WGAN核心思想即把判别器的Loss替换为衡量真实数据分布 P_r(x) 与生成数据分布 P_g(x) 的分布差异——Wasserstein距离。
	- 事实上，这种思路并非首先由WGAN提出，在2015年的ICML上，就有人用优化MMD(maximum mean discrepancy,一种度量两个数据集的差异的度量)的方式提出了不同于GAN的生成式模型——Generative Moment Matching Networks。
	- [我的解读，知乎专栏](https://zhuanlan.zhihu.com/p/40697096)
