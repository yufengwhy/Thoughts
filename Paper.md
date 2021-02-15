
$ \mathbf{w}_{t+1},\mathbf{v}_{t+1} $


$\left(\mathbf{w}_{t+1} \mathbf{v}_{t+1}\right)$

$\underset{\mathbf{w} \in \mathbb{R}^{d}, \mathbf{v} \in\{0,1\}^{n}}{\operatorname{argmin}}$

$\left(r(\mathbf{w})+\sum_{i=1}^{n} v_{i} f\left(\mathbf{x}_{i}, \mathbf{y}_{i} ; \mathbf{w}\right)-\frac{1}{K} \sum_{i=1}^{n} v_{i}\right)$

套路的论文千篇一律，有趣的论文万里挑一

1. Data Rejuvenation: Exploiting Inactive Training Examples for Neural Machine Translation [pdf](https://arxiv.org/abs/2010.02552)  
方法思路：  
0.提出inactive样本，是那些对模型效果有微弱或者负面影响的训练样本，1.用训练数据训练好模型，2.用模型对训练样本打分，得分最低的10%作为inactive样本，其他是active样本，3.用active样本训练一个模型来re-label inactive样本得到rejuvenated样本，4.用active+rejuvenated样本训练最终的模型，  
实验发现：  
1.Section4.2证明了inactive样本的存在，得分排序来找到inactive样本，去除最inactive的10%样本对模型效果有微弱提升证明找出inactive样本的合理性，inactive样本对于不同随机种子、模型大小、模型结构的一致性证明inactive样本是跟数据集相关，2.diversity跟inactive的差异，3.rejuvenate与现有的data manipulation(data diversification/denoising)方法互补，一起使用有更好的效果(4.4)，4.inactive样本难以学习，rejuvenate可以简化样本，使得学习稳定、加速、泛化好(5)，  
相关工作：  
1.data manipulation(data diversification/denoising/simplify)，2.sample re-weight/re-order，self-paced learning prefers easy examples, hard example mining exploits hard examples, and active learning emphasizes high variance examples；curriculum learning schedules the order of training examples according to their difﬁculty，3.data redundancy    
改进思路：  
1.直接用到推荐系统：找到最inactive的样本，然后re-label，再训练模型，2.sample weight通过学习relu(sigmoid(s))来过滤掉接近零的，或者像self-paced learning论文中交替优化，3.分析我们sample weight的分布，0-1间那些分布多寡，4.数据集的特性见附录Frequency rank训练集上目标item频次继续排列的名次，Coverage 被目标item对齐的item在x中占比，Uncertainty条件熵，  

$\left(\mathbf{w}_{t+1}, \mathbf{v}_{t+1}\right)=\underset{\mathbf{w} \in \mathbb{R}^{d}, \mathbf{v} \in\{0,1\}^{n}}{\operatorname{argmin}}\left(r(\mathbf{w})+\sum_{i=1}^{n} v_{i} f\left(\mathbf{x}_{i}, \mathbf{y}_{i} ; \mathbf{w}\right)-\frac{1}{K} \sum_{i=1}^{n} v_{i}\right)$
