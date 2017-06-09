# Time Series with Recurrent Neural Nets (RNNs)

This is a school project for the IB031 - Introduction to Machine Learning.

The task is capturing seasonal patterns in time series using recurrent neural networks.  I made two different experiments.

## Data

### [Monthly sales of new one-family houses sold in th e USA since 1973](https://datamarket.com/data/set/22q8/monthly-sales-of-new-one-family-houses-sold-in-th-e-usa-since-1973#!ds=22q8&display=line)

The dataset contains 276 integer values, from Jan 1973 to Nov 1995 (including). 

There is an apparent annual seasonality in the data - peaks during springs, craters during winters.

## Experiments

The two experiments are in the form of standalone Jupyter notebooks, each one containing relevant text information, so here are just brief descriptions.

### Sequence Classification

In this experiment, I try to classify 12-length sequences of monthly sales of new one-family houses according to which month the sequence begins with (ranging from Jan to Dec).

The bidirectional LSTM is used - implementation from the popular [Keras](https://github.com/fchollet/keras) deep learning library.

After data augmentation, accuracy of ~ 70% on the test set is achieved.  Moreover, the model never confuses months beyond the neighborhooding ones.

### Time Series Modeling with Evolutionary Strategy

In this experiment, I implement GRU recurrent net from scratch as well a minimalistic model class that allows stacking multiple layers.

Inspired by [recent success of evolutionary strategies in reinforcement learning](https://blog.openai.com/evolution-strategies/), the model is trained to forecast monthly sales of ... with no backprop involved.  And it works.  :)

The model successfully model learns seasonal patterns, unfortunately only for a bunch of future years, then it fades into meaningless oscillation.

The code is rather short and there is a large room for improvements and further experimentation.  Using LSTM instead of GRU, adding more layers, ... it is all trivial.

## References

### Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling

Chung, J., Gulcehre, C., Cho, K., & Bengio, Y. (2014). [*Empirical evaluation of gated recurrent neural networks on sequence modeling*](https://arxiv.org/abs/1412.3555)

```
@article{chung2014empirical,
  title={Empirical evaluation of gated recurrent neural networks on sequence modeling},
  author={Chung, Junyoung and Gulcehre, Caglar and Cho, KyungHyun and Bengio, Yoshua},
  journal={arXiv preprint arXiv:1412.3555},
  year={2014}
}
```

### Long short-term memory

Hochreiter, S., & Schmidhuber, J. (1997). Long short-term memory. Neural computation, 9(8), 1735-1780.

```
@article{hochreiter1997long,
  title={Long short-term memory},
  author={Hochreiter, Sepp and Schmidhuber, Jurgen},
  journal={Neural computation},
  volume={9},
  number={8},
  pages={1735--1780},
  year={1997},
  publisher={MIT Press}
}
```