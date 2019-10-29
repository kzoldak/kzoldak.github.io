---
layout: post
title: "Fitting a model to data."
comments: true
---

These are my notes on the following paper: [Data analysis recipes: Fitting a model to data](https://arxiv.org/pdf/1008.4686.pdf).


# Linear Model
$$\begin{align} y=mx+b \end{align}$$

$$y=mx+b$$


${\displaystyle {\frac{1}{\sqrt{2\pi \sigma^{2}}}}e^{-{\frac {(x-\mu)^{2}}{2\sigma^{2}}}}}$


\begin{displaymath} y = mx+b \end{displaymath}

$$\begin{displaymath} y = mx+b \end{displaymath}$$

$\begin{displaymath} y = mx+b \end{displaymath}$


# Likelihood, $$\mathcal{L}$$
The likelihood is the frequencey distribution for the observables evaluated at the observed data, $$y_i$$. It is also (more commonly) referred to as "the likelihood of the parameters", eventhough it is a function of both the data and the model parameters. 



The likelihood of the parameters. Or, the frequencey distribution for the observables evaluated at the observed data $y_i$. The likelihood is a function of both the data and the model parameters. 

\begin{equaton}
\mathcal{L} = \product_{i=1}^N p(y_i|x_i, \sigma_{yi}, m, b)
\end{equation}


$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$



git add -A

git commit -m 'new'

git push origin master
