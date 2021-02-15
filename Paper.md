套路的论文千篇一律，有趣的论文万里挑一

1. Data Rejuvenation: Exploiting Inactive Training Examples for Neural Machine Translation [pdf](https://www.aclweb.org/anthology/2020.emnlp-main.176.pdf)  
思路：1.用训练数据训练好模型，2.用模型对训练样本打分，得分最低的10%作为inactive样本，其他是active样本，3.用active样本训练一个模型来re-label inactive样本得到rejuvenated样本，4.用active+rejuvenated样本训练最终的模型，  
定义：inactive样本是那些对模型效果有微弱或者负面影响的训练样本，   
实验发现：1.Section4.2证明了inactive样本的存在，得分排序来找到inactive样本，去除最inactive的10%样本对模型效果有微弱提升证明找出inactive样本的合理性，inactive样本对于不同随机种子、模型大小、模型结构的一致性证明inactive样本是跟数据集相关，2.diversity跟inactive的差异，3.rejuvenate与现有的data manipulation(data diversification/denoising)方法互补，一起使用有更好的效果(4.4)，4.inactive样本难以学习，rejuvenate可以简化样本，使得学习稳定、加速、泛化好(5)，  
相关工作：  
