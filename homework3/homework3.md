# Homework 3
# Enyu Zhao 5848637841

## Problem 1
### Problem 1.1:
1. Left child of T1:
   -  classification error:$50/(150+50)=0.25$
   -  entropy:$\frac{50}{150+50} ln \frac{50}{150+50}+\frac{150}{150+50} ln \frac{150}{150+50}=0.56$
   -  Gini impurity:$\frac{50}{150+50} (1-\frac{50}{150+50})+\frac{150}{150+50} (1-\frac{150}{150+50})=0.38$
2. Right child of T1:
   -  classification error:$50/(150+50)=0.25$
   -  entropy:$\frac{50}{150+50} ln \frac{50}{150+50}+\frac{150}{150+50} ln \frac{150}{150+50}=0.56$
   -  Gini impurity:$\frac{50}{150+50} (1-\frac{50}{150+50})+\frac{150}{150+50} (1-\frac{150}{150+50})=0.38$
3. Left child of T2:
   -  classification error:$0$
   -  entropy:$\frac{0}{100+0} ln \frac{0}{100+0}+\frac{100}{100+0} ln \frac{100}{100+00}=0$
   -  Gini impurity:$\frac{0}{100+0} (1-\frac{0}{100+00})+\frac{100}{100+0} (1-\frac{100}{100+00})=0$

4. Right child of T2:
   -  classification error:$100/(100+200)=0.33$
   -  entropy:$\frac{100}{100+200} ln \frac{100}{100+200}+\frac{200}{100+200} ln \frac{200}{100+200}=0.64$
   -  Gini impurity:$\frac{100}{100+200} (1-\frac{100}{100+200})+\frac{200}{100+200} (1-\frac{200}{100+200})=0.44$


### Problem 1.2:
1. Conditional Entropy:
   1. T1:$\frac{200}{400}*0.56+\frac{200}{400}*0.56=0.56$
   2. T2:$\frac{100}{400}*0+\frac{300}{400}*0.64=0.48$
2. Weighted average of Gini-impurity:
   1. T1:$\frac{200}{400}*0.38+\frac{200}{400}*0.38=0.38$
   2. T2:$\frac{100}{400}*0+\frac{300}{400}*0.44=0.33$
3. Weighted average of classification error:
   1. T1:$\frac{200}{400}*0.25+\frac{200}{400}*0.25=0.25$
   2. T2:$\frac{100}{400}*0+\frac{300}{400}*0.33=0.25$

Considering all metrics, T2 is a better split for it has less conditional entropy and weighted average of gini-impurity. 


-----------------------------------------------
# Problem 2
### Problem 2.1
As $\epsilon _t$ is fixed , we set $g(\beta _t)=\epsilon _t(e^{\beta _t}-e^{-\beta _t})+e^{-\beta _t}$ and find the optimal $\beta _t$ by setting the gradient of $g(\beta _t)$ equals 0.


$g'(\beta _t)=\epsilon _t(e^{\beta _t}+e^{-\beta _t})-e^{-\beta _t}=0$
$\epsilon _t*e^{\beta _t}=e^{-\beta _t}*(1-\epsilon _t)$
$e^{\beta _t}=e^{-\beta _t}*(\frac{1}{\epsilon _t}-1)$
$\beta_t=-\beta_t+ln(\frac{1}{\epsilon _t}-1)$
$\beta_t=\frac{1}{2}*ln(\frac{1-\epsilon _t}{\epsilon _t})$


### Problem 2.2
From the algorithm, we learn that $\Sigma _{n:h_t(x_n)\neq y_n} D_{t+1}(n)+\Sigma _{n:h_t(x_n)= y_n} D_{t+1}(n)=1=\Sigma _{n:h_t(x_n)\neq y_n} D_{t}(n)+\Sigma _{n:h_t(x_n)= y_n} D_{t}(n)$

$\Sigma _{n:h_t(x_n)\neq y_n} D_{t+1}(n)=\Sigma _{n:h_t(x_n)\neq y_n} D_{t}(n)*e^{\beta _t}=\Sigma _{n:h_t(x_n)\neq y_n} D_{t}(n)*e^{\frac{1}{2}*ln(\frac{1-\epsilon _t}{\epsilon _t})}=(\frac{1-\epsilon _t}{\epsilon _t})^{\frac{1}{2}}*\Sigma _{n:h_t(x_n)\neq y_n} D_{t}(n)=(\frac{1-\epsilon _t}{\epsilon _t})^{\frac{1}{2}}*\epsilon _t=\sqrt{(1-\epsilon _t)*\epsilon _t}$


$\Sigma _{n:h_t(x_n)= y_n} D_{t+1}(n)=\Sigma _{n:h_t(x_n)= y_n} D_{t}(n)*e^{-\beta _t}=\Sigma _{n:h_t(x_n)= y_n} D_{t}(n)*e^{-\frac{1}{2}*ln(\frac{1-\epsilon _t}{\epsilon _t})}=(\frac{1-\epsilon _t}{\epsilon _t})^{-\frac{1}{2}}*\Sigma _{n:h_t(x_n)= y_n} D_{t}(n)=(\frac{\epsilon _t}{1-\epsilon _t})^{\frac{1}{2}}*(1-\epsilon _t)=\sqrt{(1-\epsilon _t)*\epsilon _t}=\Sigma _{n:h_t(x_n)\neq y_n} D_{t+1}(n)=1-\Sigma _{n:h_t(x_n)\neq y_n} D_{t+1}(n)$

So we can prove that $\Sigma _{n:h_t(x_n)\neq y_n} D_{t+1}(n)=\frac{1}{2}$

-------------------------------

## Problem 3
### Problem 3.1
We can try to solve this problem by using KKT conditions.

We set $F(q)=-\Sigma _{k=1}^K a_klnq_k$, and we want to minimize it. We then set the largrangian of the problem as $L(q)=-\Sigma _{k=1}^Ka_klnq_k+\Sigma _{k=1}^K(-\lambda _kq_k)+c_1(\Sigma _{k=1}^K q_k-1)+c_2(1-\Sigma _{k=1}^K q_k), s.t. \lambda_k \geq 0, c_1,c_2\geq 0$

Then by using KKT condtions, the stationary condition provides:

$\frac{\partial L(q)}{\partial q_k}=-\frac{a_k}{q_k}-\lambda_k+c_1-c_2=0$

The complementary slackness provides:
$-\lambda_kq_k=0,c_1(\Sigma _{k=1}^K q_k-1)=0,c_2(1-\Sigma _{k=1}^K q_k)=0$

As $\Sigma _{k=1}^K q_k=1$, the value of $c_1,c_2$ won't affect the solution and we set $c_1\neq c_2$.

Then if $\lambda_k\neq0,q_k=0$, thus $ln q_k=-\infty$ and since all $a_k\in R^+, F(q)=+\infty$ we can't minimize it. So $q_k\neq 0$, thus $\lambda_k=0$

So $\frac{a_k}{q_k}=c_1-c_2, \forall k\in{1,2,...,K}$,$\frac{a_1}{q_1}=\frac{a_2}{q_2}=...=\frac{a_K}{q_K}$

Thus $q_k=\frac{a_k}{\Sigma_{k=1}^Ka_k}$



### Problem 3.2
$\Sigma _{k=1}^K(q_kb_k-q_klnq_k);$
We can try to solve this problem by using KKT conditions.

We set $F(q)=\Sigma _{k=1}^K(q_klnq_k-q_kb_k)$, and we want to minimize it. We then set the largrangian of the problem as $L(q)=\Sigma _{k=1}^K(q_klnq_k-q_kb_k)+\Sigma _{k=1}^K(-\lambda _kq_k)+c_1(\Sigma _{k=1}^K q_k-1)+c_2(1-\Sigma _{k=1}^K q_k), s.t. \lambda_k \geq 0, c_1,c_2\geq 0$

Then by using KKT condtions, the stationary condition provides:

$\frac{\partial L(q)}{\partial q_k}=lnq_k-b_k+1-\lambda_k+c_1-c_2=0$

The complementary slackness provides:
$-\lambda_kq_k=0,c_1(\Sigma _{k=1}^K q_k-1)=0,c_2(1-\Sigma _{k=1}^K q_k)=0$

As $\Sigma _{k=1}^K q_k=1$, the value of $c_1,c_2$ won't affect the solution$.

Then if $\lambda_k\neq0,q_k=0$, thus $ln q_k=-\infty$ and since  $\frac{\partial L(q)}{\partial q_k}=lnq_k-b_k+1-\lambda_k+c_1-c_2=0$ can't be satisfied.

So $lnq_k=-1+c_1-c_2, \forall k\in{1,2,...,K}$,$\frac{q_1}{e^{b_1}}=\frac{q_2}{e^{b_2}}=...=\frac{q_K}{e^{b_K}}$

Thus $q_k=\frac{e^{b_k}}{\Sigma_{k=1}^Ke^{b_k}}$



--------------------------------------
## Porblem 4
### Problem 4.1
1. For $\omega_k$, as $\Sigma_n \Sigma_k \gamma_{nk}lnN(x_n|\mu _k, \Sigma_k)$ doesn't include $\omega_k$，we only need to consider $\Sigma_n \Sigma_k \gamma_{nk}ln\omega _k$

   $\Sigma_n \Sigma_k \gamma_{nk}ln\omega _k=\Sigma_k \Sigma_n \gamma_{nk}ln\omega _k=\Sigma_k ln\omega_k \Sigma_n \gamma_{nk}$

   By using result from 3.1, since$\Sigma_n \gamma_{nk}>0$ we know that $\omega_k=\frac{\Sigma_n \gamma_{nk}}{\Sigma_k\Sigma_n \gamma_{nk}}=\frac{\Sigma_n \gamma_{nk}}{\Sigma_n\Sigma_k \gamma_{nk}}=\frac{\Sigma_n \gamma_{nk}}{\Sigma_n}=\frac{\Sigma_n \gamma_{nk}}{N}$
2. For $\mu_k, \Sigma_k$, as $\Sigma_n \Sigma_k \gamma_{nk}ln\omega _k$ doesn't include $\mu_k, \Sigma_k$, we only need to consider $\Sigma_n \Sigma_k \gamma_{nk}lnN(x_n|\mu _k, \Sigma_k)$. We find the solution of the problem by using KKT conditions in Lagrangian duality. And as the constraints have nothing to do with $\mu_k, \Sigma_k$, we don't need to consider them in stationary conditions.
   
   $\frac{\partial \Sigma_n \Sigma_k \gamma_{nk}lnN(x_n|\mu _k, \Sigma_k)}{\partial \mu_k}=\frac{\partial \Sigma_n \gamma_{nk}ln[\frac{\omega_k}{(\sqrt{2\pi}^D|\Sigma_k|^{\frac{1}{2}})}*exp(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \mu_k}=\frac{\partial \Sigma_n \gamma_{nk}ln[\frac{\omega_k}{(\sqrt{2\pi}^D|\Sigma_k|^{\frac{1}{2}})}]+\gamma_{nk}ln[exp(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \mu_k}=\frac{\partial \Sigma_n \gamma_{nk}(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))}{\partial \mu_k}=\Sigma_n\gamma_{nk}*(-\frac{1}{2}*(-2\Sigma_k^{-1}(x_n-\mu_k)))=\Sigma_n\gamma_{nk}*(\Sigma_k^{-1}(x_n-\mu_k))=0$

   Thus $\mu_k=\frac{\Sigma_n\gamma_{nk}x_n}{\Sigma_n\gamma_{nk}}$

   $\frac{\partial \Sigma_n \Sigma_k \gamma_{nk}lnN(x_n|\mu _k, \Sigma_k)}{\partial \Sigma_k}=\frac{\partial \Sigma_n \gamma_{nk}ln[\frac{\omega_k}{(\sqrt{2\pi}^D|\Sigma_k|^{\frac{1}{2}})}*exp(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \Sigma_k}=\frac{\partial \Sigma_n \gamma_{nk}[ln\frac{\omega_k}{(\sqrt{2\pi}^D)}-ln|\Sigma_k|^{\frac{1}{2}}+(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \Sigma_k}=\frac{\partial \Sigma_n \gamma_{nk}[-\frac{1}{2}ln|\Sigma_k|+(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \Sigma_k}=0=\frac{\partial \Sigma_n \gamma_{nk}[-\frac{1}{2}ln|\Sigma_k|+(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \Sigma_k^{-1}}*\frac{\partial \Sigma_k^{-1}}{\partial \Sigma_k}$

   So, $\frac{\partial \Sigma_n \gamma_{nk}[-\frac{1}{2}ln|\Sigma_k|+(-\frac{1}{2}(x_n-\mu_k)^T\Sigma_k^{-1}(x_n-\mu_k))]}{\partial \Sigma_k^{-1}}=0=\Sigma_n\gamma_{nk}*\frac{1}{2}(\Sigma_k^T-(x_n-\mu_k)(x_n-\mu_k)^T)$

   Thus $\Sigma_k=\frac{\Sigma_n\gamma_{nk}(x_n-\mu_k)(x_n-\mu_k)^T}{\Sigma_n\gamma_{nk}}$

### Problem 4.2
