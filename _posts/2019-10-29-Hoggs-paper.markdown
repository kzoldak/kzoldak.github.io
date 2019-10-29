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
For this work we will assume that the data $$(x_i, y_i)$$ were drawn from a normal distribution (or Gaussian) with zero mean and known variance of $$\sigma_{yi}^2$$ about the model. The normal distribution's probability function (as given by [its Wikipedia Page](https://en.wikipedia.org/wiki/Normal_distribution)) is: 

$$
{\displaystyle f(x\mid \mu ,\sigma ^{2})={\frac {1}{\sqrt {2\pi \sigma ^{2}}}}e^{-{\frac {(x-\mu )^{2}}{2\sigma ^{2}}}}}
$$

where $$mu$$ is the mean, $$\sigma^2$$ is the variance, and $$\sigma$$ is the standard deviation. Since we have data that is normally distributed about a linear model ($$y=mx+b$$), we make the following substitutions: 
$$x \rightarrow y_i$$, 
$$\mu \rightarrow y_{model} = mx_i + b$$, and 
$$\sigma \rightarrow \sigma_{yi}$$. 

We now have:

$$
p(y_i \mid x_i, \sigma_{yi}, m, b) = \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{\left[y_i - y_{model}\right]^2}{2 \sigma_{yi}^2}\right) 
$$

$$
p(y_i \mid x_i, \sigma_{yi}, m, b) = \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{\left[y_i - (mx_i + b)\right]^2}{2 \sigma_{yi}^2}\right) 
$$

$$
p(y_i \mid x_i, \sigma_{yi}, m, b) = \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{\left[y_i - mx_i - b)\right]^2}{2 \sigma_{yi}^2}\right) 
$$

Notice that we also replaced f with p to match Hogg et al's paper. This helps to remind us that this function is representative of the probability of $$y_i$$ given the $$x_i$$ and model parameters. 



<!-- where $$ mx_i + b $$ represent the model estimates of $$y$$. I may refer to these as $$y_{model}$$ or $$ymodel$$. I may also refer to the y-axis data ($$y_i$$) as $$y_{data}$$ or $$ydata$$.  -->




# Likelihood, $$\mathcal{L}$$
The likelihood is the frequencey distribution for the observables evaluated at the observed data, $$y_i$$. It is also more commonly referred to as "the likelihood of the parameters", even though it is a function of both the data and the model parameters. The likelihood function is given by:

$$
\mathcal{L} = \prod^N_{i=1} p(y_i \mid x_i, \sigma_{yi}, m, b)
$$

where $$ p(y_i \mid x_i, \sigma_{yi}, m, b) $$ is the frequencey distribution (or the probability distribution we presented above) for Gaussian distributed data about a linear model. 
Plugging it into the likelihood:
$$
\mathcal{L} = \prod^N_{i=1} \frac{1}{\sqrt{2\pi\sigma_{yi}^2}} \exp\left(-\frac{(y_i - mx_i - b)^2}{2 \sigma_{yi}^2}\right) .
$$


When performing maximum likelihood estimation, the log-likelihood ($$\ln(\mathcal{L})$$) is used instead of the likelihood ($$\mathcal{L}$$). This is because the log-likelihood is easier to work with. The logarithmic product rule ($$ \log(xy) = \log(x) + \log(y) $$) allows products to be turned into sums, which are much easier to work with. 



$$
\ln(\mathcal{L}) = \sum^N_{i=1} p(y_i | x_i, \sigma_{yi}, m, b)
$$


$$ \ln(\mathcal{L}) = -\frac{n}{2}\ln(2\pi)- n\ln \sigma - \sum \frac{(x_i-\mu)^2}{2\sigma^2} $$

or

$$ \ln(\mathcal{L}) = -\frac{1}{2} \left[ n\ln(2\pi) + 2 n \ln \sigma + \sum \left(\frac{x_i-\mu}{\sigma}\right)^2$$




# Vector Form
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
