---
layout: post
title: Fitting a model to data.
comments: true
---

These are my notes on the following paper: [Data analysis recipes: Fitting a model to data](https://arxiv.org/pdf/1008.4686.pdf).


# Linear Model
$y=mx+b$


# Likelihood, $\mathcal{L}$
The likelihood of the parameters. Or, the frequencey distribution for the observables evaluated at the observed data $y_i$. The likelihood is a function of both the data and the model parameters. 

\begin{equaton}
\mathcal{L} = \product_{i=1}^N p(y_i|x_i, \sigma_{yi}, m, b)
\end{equation}