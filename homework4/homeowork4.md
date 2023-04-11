# Homework 4
# Enyu Zhao 5848637841


## Problem 1
### 1.1
$P(Z_{T+1}=s|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} P(Z_{T+1}=s,Z_T=s'|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} P(Z_{T+1}=s|Z_T=s',X_{1:T}=x_{1:T})*P(Z_T=s'|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} \frac{P(Z_{T+1}=s|Z_T=s')*P(Z_T=s',X_{1:T}=x_{1:T})}{P(X_{1:T}=x_{1:T})}$
$=\Sigma_{s'} \frac{a_{s',s}*\alpha_{s'}(T)}{\Sigma_{s''} P(X_{1:T}=x_{1:T},Z_T=s'')}$
$=\Sigma_{s'} \frac{a_{s',s}*\alpha_{s'}(T)}{\Sigma_{s''} \alpha_{s''}(T)}$
### 1.2
$P(Z_{T+k}=s|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} P(Z_{T+k}=s,Z_{T+k-1}=s'|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} P(Z_{T+1}=s|Z_{T+k-1}=s',X_{1:T}=x_{1:T})*P(Z_{T+k-1}=s'|X_{1:T}=x_{1:T})$
$=\Sigma_{s'} a_{s',s}*P(Z_{T+k-1}=s'|X_{1:T}=x_{1:T})$


------------------------
## Problem 2




-------------------------------
## Problem 3
### 3.1
The parameters to be learned are $\sigma_{cd},\mu_{cd} , \theta_c$

### 3.2
The joint log-likelihood can be written as below:
$\Sigma_{n=1}^N ln(P(X=x_n,Y=y_n))=\Sigma_{n=1}^N lnP(Y=y_n)P(X=x_n|y=y_n)=\Sigma_{n=1}^N (ln\theta_{y_n}+\Sigma_{d=1}^D ln P(x_d=x_{nd}|Y=y_n))=\Sigma_{n=1}^N (ln\theta_{y_n}+\Sigma_{d=1}^D (ln \frac{1}{\sqrt{2\pi}\sigma_{cd}}-\frac{x_{nd}^2+\mu_{cd}^2-2x_{nd}\mu_{cd}}{2\sigma_{cd}^2}))$