# Empirical Evaluation on Current Neural Networks on Cloze-style Reading Comprehension

**Note that, this repository will be updated irregularly.**

## Statement
**If you find this repository helpful, please press the star button. Moreover, if you would like to use or repost the content in this repository, please indicate the orignal author and source link.**


## Introduction
This repository contains an empirical comparison on current neural networks on Cloze-style Reading Comprehension. The content only represent PERSONAL views on these works. Any discussions will be welcome. (Please go to `Issue` Tab)

For those who are not familiar with this task, please read related papers, such as [Hermann et al., 2015](http://arxiv.org/abs/1506.03340).

## The Way of Generating Large-scale Training Data
Several Cloze-style reading comprehension datasets are readily available. Some general comparisons are given below.

| Dataset | Language | Genre | Blank<br />Type | Document | Query | Content |
| :------- | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| CNN/Daily Mail<br/>(Hermann et al., 2015) | English | news | NE | news article | summary w/<br/>a blank | train+valid<br/>+test |
| Children's Book Test (CBTest)<br/>(Hill et al., 2015) | English | story | NE, CN,<br/> V, P | 20 consecutive<br/>sentences | 21th sentence w/<br/>a blank | train+valid<br/>+test |
| People Daily<br/>(Cui et al., 2016a) | Chinese | news | NE, CN | news article w/<br/> a blank | the sentence that<br/>blank belongs to | train+valid<br/>+test |
| Children's Fairy Tale (CFT)<br/>(Cui et al., 2016a) | Chinese | story | NE, CN | story article w/<br/> a blank | the sentence that<br/>blank belongs to | test only<sup>1</sup>|
| Who did what<br/>(Onishi et al., 2016) | English | news | NE | news article | deleting an NE from the first sentence of the question article | N/A<sup>2</sup> |
| BookTest<br/>(Bajgar et al., 2016) | English | news | NE,CN | 20 consecutive<br/>sentences | 21th sentence w/<br/>a blank | train+valid<br/>+test |

> <sup>1</sup> contains one human evaluated test set
<br/>
<sup>2</sup> as this 'dataset' is made from LDC corpus (Gigaword), it is not available to the public unless licenced by LDC
<br/>
>**Abbreviation** 
NE: Named Entity, CN: Common Noun, V: Verb, P: Preposition

## Neural Architectures
In this section, the models will be compared with each other. As illustrated, the comment only represents my own views. Also note that, the evaluation **DO NOT** take the model performance into account, and it just shows the characteristics of the model itself.
> Rating will be in 1 ~ 5 stars, where 5★ means best, and 1★ means worst.<br/>
Take Kadlec et al., 2016 as an example, <br/>
in `Model efficiency`, I give a 5★, meaning the training speed is very fast;<br/>
in `Implementation complexity`, I give a 4★, meaning it is relatively easy to implement such a neural network;<br/>
in `Hyper-parameter`, I give a 4★, meaning there are fewer hyper-params that should be  defined by human. Note that, here the hyper-parameters are only indicating the params in neural network itself, not including such as layer dimension or something else.


| System | Core<br/>Architecture | Prediction<br/>Range<sup>1</sup> | Model<br/>Efficiency | Implementation<br/>Complexity | Hyper-<br/>parameter | Other<br/>tricks |
| :------- | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |
| Hermann et al., 2015 | Attention-<br/>based RNN | All words in<br/> document | ★★★ | ★★★ | ★★★★ | - |
| Hill et al., 2015 | Memory<br/>Network | All words in<br/> document | ★★★ | ★★ | ★★★ | self-<br/>supervision
| Kadlec et al., 2016 | Attention-<br/>based RNN | All words in<br/> document | ★★★★★ | ★★★★ | ★★★★ | - |
| Cui et al., 2016a | Attention-<br/>based RNN | All words in<br/> document | ★★★★ | ★★★★ | ★★★★ | - |
| Chen et al., 2016 | Attention-<br/>based RNN | Only Entities in<br/> document | ★★★ | ★★★★ | ★★★★ | - |
| Dhingra et al., 2016 | Attention-<br/>based RNN | - | ★★★ | ★★★ | ★★★ | - |
| Trischler et al., 2016 | Attention-<br/>based RNN | - | ★★ | ★★ | ★★ | - |
| Sordoni et al., 2016 | Attention-<br/>based RNN | All words in<br/> document | ★★★ | ★★ | ★★★ | - |
| Cui et al., 2016b | Attention-<br/>based RNN | All words in<br/> document | ★★★★ | ★★★ | ★★★★ | - |
| Weissenborn, 2016 | Attention-<br/>based RNN | Only Entities in<br/> document | ★★★ | ★★ | ★★★ | - | 
| Li et al., 2016 | Attention-<br/>based RNN<br/>+CRF | - | ★★★ | ★★ | ★★★ | - |
| Shen et al., 2016 | 
| Munkhdalai and Yu, 2016 | 


> <sup>1</sup> only shows the CNN/Daily Mail condition. In CBTest condition, all models only considers 10 candidates given in the datasets.


## Training Details
Here, I will have a brief comparison on the training details of each model, and hopefully you will have a better concept in parameter tuning.

| System | Embed<br/>Init| Hidden<br/>Type | Gradient<br/>Clip | Optimi-<br/>zation | Batch<br/>Size | Initial<br/>LR | Dropout | Imple-<br />mentation |
| :------- | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |
| Hermann et al., 2015 | rand | LSTM | - | RmsProp | 32 | 0.00005 | yes | - |
| Hill et al., 2015 | rand | LSTM | 5 or 10 | SGD | ? | RANGE | yes | - |
| Kadlec et al., 2016 | rand | GRU | 10 | ADAM | 32 | 0.001 | no | TH+B |
| Cui et al., 2016a | rand | GRU | 10 | ADAM | 32 | 0.0005 | yes | TH+K |
| Chen et al., 2016 | GloVe | LSTM | 10 | SGD | 32 | 0.1 | yes | - | 
| Dhingra et al., 2016 | word2vec | GRU | 10 | ADAM | 32 | 0.0005 | yes | TH+L |
| Trischler et al., 2016 | rand | GRU | - | ADAM | 32 | 0.001 | no | TH+K |
| Sordoni et al., 2016 | rand | GRU | 5 | ADAM | 32 | 0.001 | yes | TH+K |
| Cui et al., 2016b | rand | GRU | 5 | ADAM | 32 | 0.001 | yes | TH+K |
| Weissenborn, 2016 | GloVe | GRU | - | ADAM | 32 or 128 | 0.001 | yes | TF |
| Shen et al., 2016 | GloVe | GRU | - | ADAM | 64 | 0.0005 | yes | - |
| Li et al., 2016 | NNLM | LSTM | - | RmsProp | 120 | - | - | - |
| Bajgar et al., 2016 | rand | GRU | 10 | ADAM | 128 | 0.0005 | no | TH+B |
| Munkhdalai and Yu, 2016 | GloVe | LSTM | 15 | ADAM | 32 | 0.001 | yes | - | 

>**Abbreviation**
TH: Theano, B: Blocks, K: Keras, L: Lasagne, TF: TensorFlow

## Training Tips
I show several tips in training these neural network models, FYI.

1) Use adaptive learning algorithm, if you are not expertise in optimizing vanilla `SGD`. Use learning rate decay, even if you use adaptive learning algorithm, such as `ADAM`, `RmsProp` etc.

2) Reshuffle training data in every epoch (general tips)

3) Any neural network models that are based on AS Reader (Kadlec et al., 2016) should pay attention to the overfitting problem. Add `dropout` or `l2_regularization` to solve this problem. Also, it should be noted that using regularization will slow down the convergence speed.

4) Do not use big batch size. Typically, 32 is a good start. Note that, though bigger batch size lead to faster training, the convergence speed may not be also fast (general tips)

5) `GRU` typically shares the comparable performance with `LSTM`, so feel free to use either of them.

6) Use gradient clipping 5~10, when using `LSTM` or `GRU`. Gradient Exploding can sometimes happen, which is more dangerous than gradient vanishing!


## Leaderboard
In this part, I only show the results on CNN/Daily Mail and Children's book story Named Entity and Common Noun (short for CBT-NE and CBT-CN) datasets.
Only single model evaluation is showed here.
For more results, such as ensemble performance, please directly refer to the related papers.

The best result in each category is marked with bold face.

| System | CNN News<br/>Valid | CNN News<br/>Test | Daily Mail<br/>Valid | Daily Mail<br/>Test | CBT-NE<br/>Valid | CBT-NE<br/>Test | CBT-CN<br/>Valid | CBT-CN<br/>Test |
| :------- | :-----: | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: | 
| Deep LSTM Reader<sup>1</sup> | 55.0 | 57.0 | 63.3 | 62.2 | - | - | - | - |
| Attentive Reader<sup>1</sup> | 61.6 | 63.0 | 70.5 | 69.0 | - | - | - | - |
| Impatient Reader<sup>1</sup> | 61.8 | 63.8 | 69.0 | 68.0 | - | - | - | - |
| Human (ctx+query)<sup>2</sup> | - | - | - | - | - | *81.6* | - | *81.6* |
| MemNN(+self-sup)<sup>2</sup> | 63.4 | 66.8 | - | - | 70.4 | 66.6 | 64.2 | 63.0 |
| AS Reader<sup>3</sup> | 68.6 | 69.5 | 75.0 | 73.9 | 73.8 | 68.6 | 68.8 | 63.4 |
| CAS Reader<sup>8</sup> | 68.2 | 70.0 | - | - | 74.2 | 69.2 | 68.2 | 65.7 |
| Stanford AR<sup>4</sup> | 72.4 | 72.4 | 76.9 | 75.8 | - | - | - | - |
| GA Reader<sup>5</sup> | 73.0 | 73.8 | 76.7 | 75.7 | 74.9 | 69.0 | 69.0 | 63.9 |
| EpiReader<sup>7</sup> | 73.4 | 74.0 | - | - | 75.3 | 69.7 | 71.5 | 67.4 |
| Iterative Attention<sup>6</sup> | 72.6 | 73.3 | - | - | 75.2 | 68.6 | 72.1 | 69.2 |
| QANN<sup>10</sup> | - | 73.7 | - | 77.2 | - | 70.6 | - | - |
| ReasoNet<sup>13</sup> | 72.9 | 74.7 | 77.6 | 76.6 | - | - | - | - |
| NSE Adp. Com. <sup>15</sup> | - | - | - | - | 78.2 | 73.2 | 74.2 | 71.4 |
| Bi-ATT Flow<sup>16</sup> | **76.3** | **76.9** | **80.3** | **79.6** | - | - | - | - | 
| FG gate<sup>17</sup> | - | - | - | - | 79.1 | **75.0** | 75.3 | 72.0 |
| AoA Reader<sup>9</sup> | 73.1 | 74.4 | - | - | 77.8 | 72.0 | 72.2 | 69.4 |
| AoA Reader + rerank<sup>9</sup> | - | - | - | - | **79.6** | 74.0 | **75.7** | **73.1** |
| AS Reader<sup>14</sup><br/>(trained on BookTest)| - | - | - | - | *80.5* | *76.2* | *83.2* | *80.8* |


## Related Papers
You can either download the related papers from this repository or in the following links.
> 1. (Hermann et al., 2015) Teaching Machines to Read and Comprehend
<br/>http://arxiv.org/abs/1506.03340

> 2. (Hill et al., 2015) The Goldilocks Principle: Reading Children's Books with Explicit Memory Representations
<br/>http://arxiv.org/abs/1511.02301

> 3. (Kadlec et al., 2016) Text Understanding with the Attention Sum Reader Network
<br/>http://arxiv.org/abs/1603.01547

> 4. (Chen et al., 2016) A Thorough Examination of the CNN/Daily Mail Reading Comprehension Task
<br/>https://arxiv.org/abs/1606.02858

> 5. (Dhingra et al., 2016) Gated-Attention Readers for Text Comprehension
<br/>https://arxiv.org/abs/1606.01549

> 6. (Sordoni et al., 2016) Iterative Alternating Neural Attention for Machine Reading
<br/>https://arxiv.org/abs/1606.02245

> 7. (Trischler et al., 2016) Natural Language Comprehension with the EpiReader
<br/>https://arxiv.org/abs/1606.02270

> 8. (Cui et al., 2016a) Consensus Attention-based Neural Networks for Chinese Reading Comprehension
<br/>https://arxiv.org/abs/1607.02250

> 9. (Cui et al., 2016b) Attention-over-Attention Neural Networks for Reading Comprehension
<br/>https://arxiv.org/abs/1607.04423

> 10. (Dirk Weissenborn, 2016) Separating Answers from Queries for Neural Reading Comprehension
<br/>http://arxiv.org/abs/1607.03316

> 11. (Li et al., 2016) Dataset and Neural Recurrent Sequence Labeling Model for Open-Domain Factoid Question Answering
<br/>https://arxiv.org/abs/1607.06275

> 12. (Onishi et al., 2016) Who did What: A Large-Scale Person-Centered Cloze Dataset
<br/>http://arxiv.org/abs/1608.05457

> 13. (Shen et al., 2016) ReasoNet: Learning to Stop Reading in Machine Comprehension
<br/>https://arxiv.org/abs/1609.05284

> 14. (Bajgar et al., 2016) Embracing data abundance: BookTest Dataset for Reading Comprehension
<br/>https://arxiv.org/abs/1610.00956

> 15. (Munkhdalai and Yu, 2016) Reasoning with Memory Augmented Neural Networks for Language Comprehension
<br/>https://arxiv.org/abs/1610.06454

> 16. (Seo et al., 2016) Bi-directional attention flow for machine comprehension
<br/>http://arxiv.org/abs/1611.01603

> 17. (Yang et al., 2016) Words or Characters? Fine-grained Gating for Reading Comprehension
<br/>http://arxiv.org/abs/1611.01724


## Contact
For any problems, please leave a message in the `Github Issues`.


## Disclaimer
Any subjective comments in this repository only represents the idea of the owner (ymcui), and does not represent the claims of any organizations.