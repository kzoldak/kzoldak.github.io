---
layout: post
title: "Fitting a model to data."
comments: true
---

These are my notes on the following paper: [Data analysis recipes: Fitting a model to data](https://arxiv.org/pdf/1008.4686.pdf).


# Linear Model
$$ y=mx+b $$
where $$m$$ is slope and $$b$$ is the intercept of the line. 



# Likelihood, $$\mathcal{L}$$
The likelihood is the frequencey distribution for the observables evaluated at the observed data, $$y_i$$. It is also more commonly referred to as "the likelihood of the parameters", even though it is a function of both the data and the model parameters. 

$$
\mathcal{L} = 
$$

When maximizing the likelihood, the log-likelihood is easier to work with. This is often not explained, but here is why:


$$
\begin{equation}
\mathcal{L} = \prod^N_{i=1} p(y_i | x_i, \sigma_{yi}, m, b)
\end{equation}
$$


git add -A

git commit -m 'new'

git push origin master
