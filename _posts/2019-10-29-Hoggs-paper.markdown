---
layout: post
title: "Fitting a model to data."
comments: true
---

These are my notes on the following paper: [Data analysis recipes: Fitting a model to data](https://arxiv.org/pdf/1008.4686.pdf).

# Basic Idea of Fitting a Line to Data
In elementry school you learn to fit a line ($$y=mx+b$$) to data by eyeballing it. You draw a line that appears to place half of the data points above it and the other half below it (with the exception of those that happen to fall directly on it), while still following the pattern of the data points on the graph. However, it is a bit more complicated (but often too advanced for elementary aged kids) than just splitting the data in half. The primal idea behind basic line fitting is that you want to __minimize the distance__ between the data points and the line. If you understand the underlying concepts of fitting a line to data, then the procedures become clear. 

## Data set or sample
A data set is a compilation of $n$ total data points, and each individual data point in the set (or sample) is identified by its $$ith$$ position in the set. Instead of introducing them as $$d_1, d_2, ..., d_n$$, we instead introduce them using their x- and y-axis dimensions; $$(x_1, y_1), (x_2, y_2), ..., (x_n, y_n)$$. When referencing an individual data point with no particular preference, we often use $$(x_i, y_i)$$. The $$(x, y)$$ coordiantes should be familiar to you since these values are what you plot on a graph; (2,6) is x=2,y=6, move to the right 2 blocks and up 6 blocks. 

## Data's distribution about the line
If our data points all fall in a perfectly straight line (which never happens in reality), then the y-axis value of each respective x-axis value will follow the linear function: $$y_i = m x_i + b$$, where $$m$$ is the slope of the line and $$b$$ is the y-intercept (or just intercept). 

In reality, data points are though to be drawn from a truly straight line, but there are mechanisms that cause our observations to have uncertainties in those values. Therefore we get a set of data points which are scattered about that true line. We can't know this true line, and what we are actually doing when we fit a line to the data is attempting to estimate it (via its parameters). But we must estimate how these data points are scattered about the line, and this is done with the [normal (or Gaussian) distribution](https://en.wikipedia.org/wiki/Normal_distribution). We present the probability density function (PDF) of the normal distribution in a future section. 




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


$$ \ln(\mathcal{L}) = -\frac{n}{2}\ln(2\pi)- n\ln \sigma - \sum \frac{(y_i-y_{model})^2}{2\sigma^2} $$

or

$$ 
\ln(\mathcal{L}) = -\frac{1}{2} \left[ n\ln(2\pi) + 2 n \ln(\sigma) + \sum \left(\frac{y_i-y_{model}}{\sigma}\right)^2 \right]
$$

Since we have technically set up the probability function to be dependent on $$\sigma_{yi}$$, we should write the function as:

$$ 
\ln(\mathcal{L}) = -\frac{1}{2} \left[ n\ln(2\pi) + 2 n \ln(\sigma_{yi}) + \sum \left(\frac{y_i-y_{model}}{\sigma_{yi}}\right)^2 \right]
$$



# Bayes' Theorem
Here we write the most basic way to present Bayes' Theorem:

$$
p(\theta\mid D, I) = \frac{p(D \mid \theta, I) \ p(\theta \mid I)}{p(D\mid I)}
$$

where $$ p(\theta \mid D, I) $$ is the posterior probability, $$p(D \mid \theta, I)$$ is the likelihood (probability), $$ p(\theta \mid I) $$ is the prior probability distribution, and $$ p(D\mid I) $$ is a constant that arises from marginalizing the numerator over all parameters; it can be thought of as a normalization so that the posterior probability integrates (i.e., sums) to 1. That's all you really need to know about the denominator term. All terms in Bayes' theorm are probabilities. 

We use $$\theta$$ to represent all the model parameters. This includes all that are free to vary during the fit, both those you care about and those you do not. 
$I$ is short-hand for all the prior knowledge of the experiment, parameters and all, but holds no knowledge of the data (see prior section below since $$x_i$$ and $$\sigma_{yi}$$ are NOT treated as data here). 
$$D$$ stands for data, which in our case is really only the $$y_1, y_2, ..., y_N$$. 


## Prior
$I$ is short-hand for all the prior knowledge of the $$x_i$$ and the $$\sigma_{yi}$$ and everything else about the problem. Hogg et al. notes that $$x_i$$ and $$\sigma_{yi}$$ are consumed within the prior $$I$$ because they are NOT considered the data. They explain that there is a total asymmetry between $$x_i$$ and $$y_i$$ and the $$x_i$$ are considered to be part of the experimental design. They are inputs to an experiment that gets $$y_i$$ as its output. In data science practices, the $$X$$ matrix that holds the $$x_1, x_2, ..., x_N$$ data is called the features matrix and the $$Y$$ vector that holds the $$y_1, y_2, ..., y_N$$ data is called the response vector. This is because they are not treated as data, but features and a response of the experiment. Note that in Hogg et al, the so-called features matrix is $$\mathbf{A}$$ (see their Section 1) instead of $$\mathbf{X}$$, where they use $$\mathbf{X}$$ to represent the resulting parameters instead.





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
