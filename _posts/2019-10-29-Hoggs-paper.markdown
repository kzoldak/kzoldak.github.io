---
layout: post
title: "Fitting a model to data."
comments: true
---

These are my notes on the following paper: [Data analysis recipes: Fitting a model to data](https://arxiv.org/pdf/1008.4686.pdf).


# Linear Model
$$ 
y=mx+b 
$$
where $$m$$ is slope and $$b$$ is the intercept of the line. 


# Gaussian Distribution's PDF
For this work we will assume that the data $$(x_i, y_i)$$ were all drawn from a standard normal distribution (i.e., Gaussian with zero mean)

$$
p(y_i \mid x_i, \sigma_{yi}, m, b) = \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{\left[y_i - (mx_i + b)\right]^2}{2 \sigma_{yi}^2}\right)
$$




# Likelihood, $$\mathcal{L}$$
The likelihood is the frequencey distribution for the observables evaluated at the observed data, $$y_i$$. It is also more commonly referred to as "the likelihood of the parameters", even though it is a function of both the data and the model parameters. 

$$
\mathcal{L} = \prod^N_{i=1} p(y_i \mid x_i, \sigma_{yi}, m, b)
$$

where $$ p(y_i \mid x_i, \sigma_{yi}, m, b) $$ is the frequencey distribution. In our case, lets use the standard normal (i.e., Gaussian) distribution.

$$
p(y_i \mid x_i, \sigma_{yi}, m, b) = \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{(y_i - (mx_i + b))^2}{2 \sigma_{yi}^2}\right)
$$

When maximizing the likelihood ($$\mathcal{L}$$), the log-likelihood ($$\ln(\mathcal{L})$$) is easier to work with. The reason for this is that the logarithmic product rule ($$ \log(xy) = \log(x) + \log(y) $$) turns products into sums, and sums are much easier to work with. 


$$
\mathcal{L} = \prod^N_{i=1} p(y_i | x_i, \sigma_{yi}, m, b)
$$


$$
\begin{equation}
\qquad 
\mathbf{Y}=
\begin{bmatrix}
y_{1} \\
y_{2} \\
\vdots \\
y_{N}
\end{bmatrix}
\end{equation}
$$

$$
\begin{equation}
\qquad 
\mathbf{A}=
\begin{bmatrix}
1 & x_{1}\\ 
1 & x_{2}\\
\vdots \\ 
1 & x_{N}
\end{bmatrix}
\end{equation}
$$

$$
\begin{equation}
\mathbf{C}=
\begin{bmatrix}
\sigma_{y_1}^2 & 0 & \ldots & 0 \\ 
0 & \sigma_{y_2}^2 & \ldots & 0 \\
0 & 0 & \ddots & 0 \\ 
0 & 0 & \ldots & \sigma_{y_N}^2 
\end{bmatrix}
\end{equation}
$$


git add -A

git commit -m 'new'

git push origin master
