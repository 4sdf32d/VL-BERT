# 中文多模态bert

bert的提出极大得推动了NLP的发展，但随着多模态任务的增多（这在很多企业中已经成为一种常见的任务），单纯的NLPBert已经无法满足需求。

后续看到了很多的paper也陆续都采用了transformer预训练多模态bert，但都基本是英文领域。

该项目主要是预训练中文的多模态Bert，也是为了以后的多模态任务提供基本的模型


 VL-BERT 


论文标题：VL-BERT: Pre-training of Generic Visual-Linguistic Representations
论文链接：https://arxiv.org/abs/1908.08530
源码链接：https://github.com/jackroos/VL-BERT

与上述两个模型相同，VL-BERT 在结构上依旧直接采用堆叠的 Transformer。如下图所示其在输入端与上述两个模型略有不同。


首先图像端的输入由以下几个编码的加和构成：a. Faster-RCNN所提取的区域图像特征和该区域在原图像中位置信息的拼；b. 位置编码；c. 片段编码；d. [IMG] 编码。

在文字端该模型的输入为正常 BERT 文字输入和整个图像特征的加和。同第二个模型相似，该模型分别在三个任务上进行预训练分别为：语言掩码、图像标签分类和图像语言匹配任务。

作者最后在 VCR, VQA, REC (Referring expression comprehension) 三个任务上测试模型，该模型都取得了最佳或者与最佳相当的表现。

## 实现逻辑
上述的paper都基本采用了COCO数据集，但中文领域很难找到能达到COCO规模的数据，因此打算将COCO的英文标注翻译为中文即可得到中文领域的数据集，会存在些翻译导致的偏差。

