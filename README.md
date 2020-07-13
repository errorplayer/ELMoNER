# ELMoNER
#### 基于ELMo的中文实体标注
##### Chinese Named Entity Recognition Based on ELMo

#### 模型介绍
参考文献: `《Deep contextualized word representations》`  
ELMo模型图示  
![avatar](https://github.com/errorplayer/ELMoNER/blob/master/images/ELMo.png)  

ELMo的优势  
* ELMo能够学习到词汇用法的复杂性，比如语法、语义
* ELMo能够动态生成词向量，学习到不同上下文情况下的一词多义现象

出于学习的目的，我按照上图所示的结构搭建了网络，实现了多层+双向的LSTM网络结构  
模型只考虑了单字，无法处理长词，且在训练过程中，直接通过一层全连接层对生成的词向量进行实体标注，`训练得到的词向量不具有普适性，想要适配其他NLP任务还需要更复杂的训练 `   
`LSTM细胞的维度(hidden_size)`: 200  
`词语数量(vocab_size)`: 5000  
`单条语料的最大长度(max_length)`: 128  
`实体类别(entity_class)`: 共7类  

|  Entity  | 类名 |
| :---: | :---: |
|B-PER/I-PER| 人名 |
|B-LOC/I-LOC| 地名 |
|B-ORG/I-ORG| 机构名 |
|O| 非实体 |

`生成词向量时各层权重请移步test_modified.ipynb`


#### 效果展示  
详情查看`test_modified.ipynb`文件cell output


### 特别提醒
改变session之后，如果遇到有关variable scope问题， 可尝试restart kernel, 然后重新运行一遍，或许有帮助。
