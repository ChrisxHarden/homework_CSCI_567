# Homework 4
# Enyu Zhao 5848637841


## Problem 1




## Problem 3
### 3.1
The parameters to be learned are $\sigma_{cd},\mu_{cd} , \theta_c$

### 3.2
The joint log-likelihood can be written as below:
$\Sigma_{n=1}^N ln(P(X=x_n,Y=y_n))=\Sigma_{n=1}^N lnP(Y=y_n)P(X=x_n|y=y_n)=\Sigma_{n=1}^N (ln\theta_{y_n}+\Sigma_{d=1}^D ln P(x_d=x_{nd}|Y=y_n))=\Sigma_{n=1}^N (ln\theta_{y_n}+\Sigma_{d=1}^D (ln \frac{1}{\sqrt{2\pi}\sigma_{cd}}-\frac{x_{nd}^2+\mu_{cd}^2-2x_{nd}\mu_{cd}}{2\sigma_{cd}^2}))$