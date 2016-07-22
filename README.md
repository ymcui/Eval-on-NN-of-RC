# Empirical Evaluation on Current Neural Networks on Cloze-style Reading Comprehension

**Note that, this repository will be updated irregularly**

##Introduction
This repository contains an empirical comparison on current neural networks on Cloze-style Reading Comprehension. The content only represent personal views on these works. Any discussions will be welcome. (Please go to `Issue` Tab)

##Neural Architectures



##Training Details
Here we will have a brief comparison on the training details of each model, and hopefully you will have a better concept in parameter tuning.

| System | Embed | Hidden | Grad_Clip | Opt. | Batch | Init-LR | Dropout | Others |
| :------- | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |
| Hermann et al., 2015 | rand | LSTM | - | RmsProp | 32 | 0.00005 | yes | - |
| Hill et al., 2015 | rand | LSTM | 5 or 10 | SGD | ? | RANGE | yes | - |
| Kadlec et al., 2016 | rand | GRU | 10 | ADAM | 32 | 0.001 | no | - |
| Cui et al., 2016a | rand | GRU | 10 | ADAM | 32 | 0.0005 | yes | - |
| Chen et al., 2016 | GloVe | LSTM | 10 | SGD | 32 | 0.1 | yes | - | 
| Dhingra et al., 2016 | word2vec | GRU | 10 | ADAM | 32 | 0.0005 | yes | - |
| Trischler et al., 2016 | rand | GRU | - | ADAM | 32 | 0.001 | no | - |
| Sordoni et al., 2016 | rand | GRU | 5 | ADAM | 32 | 0.001 | yes | - |
| Cui et al., 2016b | rand | GRU | 5 | ADAM | 32 | 0.001 | yes | - |
| Weissenborn, 2016 | GloVe | GRU | - | ADAM | 32 or 128 | 0.001 | yes | - |
| Li et al., 2016 | NNLM | LSTM | - | RmsProp | 120 | - | - | - |


##Overall Experimental Results
We only shows results on CNN/Daily Mail and Children's book story (CBTest NE/CN).
And only single model evaluation is showed.
For more results, such as ensemble performance, please directly refer to the related papers.

The best results are marked with bold face.

| System | CNN-V | CNN-T | DM-V | DM-T | CBT-NE-V | CBT-NE-T | CBT-CN-V | CBT-CN-T |
| :------- | :-----: | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: | 
| Deep LSTM Reader<sup>1</sup> | 55.0 | 57.0 | 63.3 | 62.2 | - | - | - | - |
| Attentive Reader<sup>1</sup> | 61.6 | 63.0 | 70.5 | 69.0 | - | - | - | - |
| Impatient Reader<sup>1</sup> | 61.8 | 63.8 | 69.0 | 68.0 | - | - | - | - |
| Human (ctx+query)<sup>2</sup> | - | - | - | - | - | *81.6* | - | *81.6* |
| MemNN(+self-sup)<sup>2</sup> | 63.4 | 66.8 | - | - | 70.4 | 66.6 | 64.2 | 63.0 |
| AS Reader<sup>3</sup> | 68.6 | 69.5 | 75.0 | 73.9 | 73.8 | 68.6 | 68.8 | 63.4 |
| CAS Reader<sup>4</sup> | 68.2 | 70.0 | - | - | 74.2 | 69.2 | 68.2 | 65.7 |
| Stanford AR<sup>5</sup> | 72.4 | 72.4 | 76.9 | 75.8 | - | - | - | - |
| GA Reader<sup>6</sup> | 73.0 | 73.8 | 76.7 | 75.7 | 74.9 | 69.0 | 69.0 | 63.9 |
| EpiReader<sup>7</sup> | 73.4 | 74.0 | - | - | 75.3 | 69.7 | 71.5 | 67.4 |
| Iterative Attention<sup>8</sup> | 72.6 | 73.3 | - | - | 75.2 | 68.6 | 72.1 | 69.2 |
| AoA Reader<sup>9</sup> | 73.1 | 74.4 | - | - | **77.8** | **72.0** | **72.2** | **69.4** |
| QANN<sup>10</sup> | - | 73.7 | - | 77.2 | - | 70.6 | - | - |
| Li et al., 2016 | **77.7** | **77.1** | **78.9** | **78.0** | - | - | - | - |

>**Reference**
Those marked by <sup>1</sup> are taken from Hermann et al., 2015;
<sup>2</sup> are taken from Hill et al., 2015;
<sup>3</sup> are taken from Kadlec et al., 2016;
<sup>4</sup> are taken from Cui et al., 2016a;
<sup>5</sup> are taken from Chen et al., 2016;
<sup>6</sup> are taken from Dhingra et al., 2016;
<sup>7</sup> are taken from Trischler et al., 2016;
<sup>8</sup> are taken from Sordoni et al., 2016;
<sup>9</sup> are taken from Cui et al., 2016b;
<sup>10</sup> are taken from Weissenborn, 2016.

##Related Papers
You can either download from this repository or in the following links.
> (Hermann et al., 2015) Teaching Machines to Read and Comprehend

http://arxiv.org/abs/1506.03340
> (Hill et al., 2015) The Goldilocks Principle: Reading Children's Books with Explicit Memory Representations

http://arxiv.org/abs/1511.02301
> (Kadlec et al., 2016) Text Understanding with the Attention Sum Reader Network

http://arxiv.org/abs/1603.01547
> (Chen et al., 2016) A Thorough Examination of the CNN/Daily Mail Reading Comprehension Task

https://arxiv.org/abs/1606.02858
> (Dhingra et al., 2016) Gated-Attention Readers for Text Comprehension

https://arxiv.org/abs/1606.01549
> (Sordoni et al., 2016) Iterative Alternating Neural Attention for Machine Reading

https://arxiv.org/abs/1606.02245
> (Trischler et al., 2016) Natural Language Comprehension with the EpiReader

https://arxiv.org/abs/1606.02270
> (Cui et al., 2016a) Consensus Attention-based Neural Networks for Chinese Reading Comprehension

https://arxiv.org/abs/1607.02250
> (Cui et al., 2016b) Attention-over-Attention Neural Networks for Reading Comprehension

https://arxiv.org/abs/1607.04423
> (Dirk Weissenborn, 2016) Separating Answers from Queries for Neural Reading Comprehension

http://arxiv.org/abs/1607.03316
> (Li et al., 2016) Dataset and Neural Recurrent Sequence Labeling Model for Open-Domain Factoid Question Answering

https://arxiv.org/abs/1607.06275


##Contact
For any problems, please leave a message in the `Github Issues`.