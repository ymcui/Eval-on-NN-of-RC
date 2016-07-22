# Empirical Evaluation on Current Neural Networks on Cloze-style Reading Comprehension

**Note that, this repository will be updated irregularly**

##Introduction
This repository contains an empirical comparison on current neural networks on Cloze-style Reading Comprehension. The content only represent personal views on these works. Any discussions will be welcome. (Please go to `Issue` Tab)

##



##Training Details



##Overall Experimental Results
We only shows results on CNN/Daily Mail and Children's book story (CBTest NE/CN).
And only single model evaluation is showed.
For more results, such as ensemble performance, please directly refer to the related papers.

| System | CNN-V | CNN-T | DM-V | DM-T | CBT-NE-V | CBT-NE-T | CBT-CN-V | CBT-CN-T |
| :-------: | :-----: | :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: |  :-----: | 
| Deep LSTM Reader[^hermann] | 55.0 | 57.0 | - | - | - | - | - | - |
| Attentive Reader[^hermann] | 61.6 | 63.0 | - | - | - | - | - | - |
| Impatient Reader[^hermann] | 61.8 | 63.8 | - | - | - | - | - | - |



[^hermann]: Hermann et al., 2015



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
> (Cui et al., 2016) Consensus Attention-based Neural Networks for Chinese Reading Comprehension

https://arxiv.org/abs/1607.02250
> (Cui et al., 2016) Attention-over-Attention Neural Networks for Reading Comprehension

https://arxiv.org/abs/1607.04423
> (Li et al., 2016) Dataset and Neural Recurrent Sequence Labeling Model for Open-Domain Factoid Question Answering

https://arxiv.org/abs/1607.06275


##Contact
For any problems, please leave a message in the `Github Issues`.