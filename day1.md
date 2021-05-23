## 机器翻译概述

思路1：

step1:先将中文句子进行分词，将各个词翻译为英文(translation model)

step2:将各个英文词汇进行排列组合，利用语言模型判断出最像人话的那个（相似度最高），即为翻译结果(language model)



缺点：1.翻译结果艰涩难懂

2.共有n!!种排列方式，需要极大算力，且消耗时间极长，复杂度为2^n，极为复杂



思路2：

viterb algorithm:

核心：动态规划

假设将中文设为事件C,讲英文设为事件E，则需找到max p(e|c)（条件概率，在C条件下E概的率的最大值）

设translation model 概率为p(c|e),language model 概率为P（e）,则由贝叶斯定理：
$$
p(e|c) = p(c|e) * p(e) / p(c)
$$
则只需求max p(e)*p(c|e)（二者同时考虑） 

优点：降低复杂度



语言模型(language model):

给定一句英文e，计算概率(e)

若符合英文语法，则p(e)高

若为随机语句，则p(e)低



翻译模型：

给定一堆<c,e>，计算p(f|e)

语义相似度高，则p(f|e)高

语义相似度低，则p(f|e)低



Decoding Algorithm

给定语言模型，翻译模型和f,找出最优的使得p(e)p(f|e)最大



联合概率

p(x1,x2,x3,x4)

=p(x1) * p(x2|x1)  * p(x3|x1,x2) * p(x4|x1,x2,x3)

上述式子不方便计算，故取近似值(Markov Assumptions)：

Uni - gram = p(x1) * p(x2) * p(x3) *p(x4)

Bi - gram = p(x1) * p(x2|x1) * p(x3|x2) * p(x4|x3)

Tri - gram = p(x1) * p(x2|x1) * p(x3|x1,x2) *p(x4|x1,x2,x3)



语言模型：

用途：判断p(A)与p(B)哪个更像人话（概率大的更像人话）

怎么计算p(.)

通过Uni - gram、Bi - gram、Tri - gram计算