## Introduction

[Open Problems - Multimodal Single-Cell Integration](https://www.kaggle.com/competitions/open-problems-multimodal/discussion/366392)



## Result

- Private: 0.770   38/1266
- Public:  0.813    86/1266



##  Solution

### Preprocess

- Citeseq
  - raw data after log1p was reduced to 1024 dimensions by SVD and use the top 75 dimensions.
  - On the other hand, the data of important columns were preserved.
- Multiome
  - The input data was reduced to 4096 dimensions by SVD and use the top 48 dimensions(In my experiment, the more dimensions of dimensionality reduction, the better the result).
  - Input target reduced to 512 dimensions by SVD.

### Training

- Citeseq
  - GroupKFold by donor.
  - 1dcnn model inspired by [tmp's previous solution](https://www.kaggle.com/competitions/lish-moa/discussion/202256).
  - Pearson correlation coefficient was used for the Loss function.
- Multiome
  - GroupKFold by donor and random KFold(better on both CV and private LB).
  - Parameter tunning on [All in one : CITEseq & Multiome with Keras.](https://www.kaggle.com/code/pourchot/all-in-one-citeseq-multiome-with-keras)



## What I learned

- How to deal with 100 GBytes of data when I only have 32G memory
- Processing of high dimension structured data.