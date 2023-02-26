# Homework 2

## Problem 1 
### 1.1 
$p(y;\mathbf{q})=exp(\Sigma^K_{i=1}1\lbrace y=i\rbrace ln(Cq_i))=exp(\Sigma _{i=1}^K 1\lbrace y=i\rbrace ln\frac{q_i}{\Sigma^K_{j=1} q_j})$

set $t(y)=[1\lbrace y=1\rbrace,1\lbrace y=2\rbrace,..., 1\lbrace y=K\rbrace]^T$

Thus:

$p(y;\mathbf{q})=exp(\Sigma^K_{i=1}1\lbrace y=i\rbrace ln(Cq_i))=exp(\Sigma _{i=1}^K 1\lbrace y=i\rbrace ln\frac{q_i}{\Sigma^K_{j=1} q_j})=exp([ln \frac{q_1}{\Sigma^K_{i=1}q_i},ln \frac{q_2}{\Sigma^K_{i=1}q_i},...,ln \frac{q_K}{\Sigma^K_{i=1}q_i}]*t(y))$


So:
$b(y)=1$

$t(y)=[1\lbrace y=1\rbrace,1\lbrace y=2\rbrace,..., 1\lbrace y=K\rbrace]^T$

$\eta=[ln \frac{q_1}{\Sigma^K_{i=1}q_i},ln \frac{q_2}{\Sigma^K_{i=1}q_i},...,ln \frac{q_K}{\Sigma^K_{i=1}q_i}]^T$

$a(\eta)=0$


### 1.2
#### (2):
$\eta=w^Tx=log(\frac{1}{1-q})$
#### (3):
$h(x;w)=E_{y\sim p(y|x;W)}t(y)=E_{y\sim p(y|x;W)}y=q$


Since $\eta=w^Tx=log(\frac{q}{1-q})$, $q=\frac{1}{1+e^{-w^Tx}}$

Thus $h(x;w)=E_{y\sim p(y|x;W)}t(y)=E_{y\sim p(y|x;W)}y=q=\frac{1}{1+e^{-w^Tx}}$


### 1.3
#### (2):
$\eta=Wx=[ln \frac{q_1}{\Sigma^K_{i=1}q_i},ln \frac{q_2}{\Sigma^K_{i=1}q_i},...,ln \frac{q_K}{\Sigma^K_{i=1}q_i}]^T=[ln（Cq_1）,ln（Cq_2）,...,ln（Cq_k）]^T$
#### (3):
$h(x;w)=E_{y\sim p(y|x;W)}t(y)=E_{y\sim p(y|x;W)}y=T(y)=[Cq_1,Cq_2,...,Cq_n]^T$


Since $\eta=Wx=[ln（Cq_1）,ln（Cq_2）,...,ln（Cq_k）]^T$, $e^{w_1^Tx}=Cq_1,e^{w_2^Tx}=Cq_2,...,e^{w_K^Tx}=Cq_k$,Here $w_i$ means the i-th row in $W$

Thus $h(x;w)=E_{y\sim p(y|x;W)}t(y)=[Cq_1,Cq_2,...,Cq_n]^T=[e^{w_1^Tx},e^{w_2^Tx},...,e^{w_K^Tx}]$


### 1.4
$p(y;\lambda)=\frac{\lambda^yexp(-\lambda)}{y!}=\frac{1}{y!}*exp(ln\lambda * y -\lambda)$

Thus:
$b(y)=\frac{1}{y!}$

$\eta =ln\lambda=w^Tx,e^{w^Tx}=\lambda$

$t(y)=y$

$a(\eta)=\lambda$

$h(x;w)=E_{y\sim p(y|x;w)}t(y)=\lambda=e^{w^Tx}$

---------------------------    
## Problem 2

### 2.1

#### 1
we use $\boldsymbol{y} \in \mathbf{R}^K$

$\frac{\partial l}{\partial \boldsymbol{a}}=\frac{\partial l}{\partial \boldsymbol{z}}*\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{a}}=\frac{\partial -ln(\boldsymbol{z}^T\boldsymbol{y})}{\partial \boldsymbol{z}}*\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{a}}=-\frac{1}{\boldsymbol{z}^T\boldsymbol{y}}*\boldsymbol{y}*\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{a}}$


 for $\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{a}}$, we look at $i-th$ row:

 $\frac{\partial z_i}{\partial a_i}=\frac{\partial \frac{e^{a_i}}{\Sigma _k e^{a_k}}}{\partial a_i}=\frac{e^{a_i}*\Sigma _k e^{a_k}-e^{a_i}*e^{a_i}}{(\Sigma _k e^{a_k})^2}=z_i(1-z_i)$

 Thus:
 $\frac{\partial \boldsymbol{z}}{\partial \boldsymbol{a}}=\boldsymbol{z} \circ \boldsymbol{1-z}=[z_1(1-z_1),z_2(1-z_2),...,z_k(1-z_k)]^T$, $\circ$ means pointwise multiply,$\boldsymbol{1}$ means $[1,1,...,1]^T$

$\frac{\partial l}{\partial \boldsymbol{a}}=-\frac{1}{\boldsymbol{z}^T\boldsymbol{y}}*\boldsymbol{y}*[z_1(1-z_1),z_2(1-z_2),...,z_k(1-z_k)]^T=-(1-z_y)=\boldsymbol{1-z^Ty}$


#### 2
$\frac{\partial l}{\partial \boldsymbol{W^{(2)}}}=\frac{\partial l}{\partial \boldsymbol{a}}*\frac{\partial \boldsymbol{a}}{\partial \boldsymbol{W^{(2)}}}=\frac{\partial l}{\partial \boldsymbol{a}}*\boldsymbol{h^T}$


$\frac{\partial l}{\partial \boldsymbol{b^{(2)}}}=\frac{\partial l}{\partial \boldsymbol{a}}*\frac{\partial \boldsymbol{a}}{\partial \boldsymbol{b^{(2)}}}=\frac{\partial l}{\partial \boldsymbol{a}}$


#### 3
$\frac{\partial l}{\partial \boldsymbol{u}}=\frac{\partial l}{\partial \boldsymbol{a}} *\frac{\partial \boldsymbol{a}}{\partial \boldsymbol{u}}=\frac{\partial l}{\partial \boldsymbol{a}} *(\boldsymbol{W^{{2}}*H(u)})^T$

#### 4

$\frac{\partial l}{\partial \boldsymbol{W^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}*\frac{\partial \boldsymbol{u}}{\partial \boldsymbol{W^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}*\boldsymbol{x^T}$


$\frac{\partial l}{\partial \boldsymbol{b^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}*\frac{\partial \boldsymbol{u}}{\partial \boldsymbol{b^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}$



### 2.2
As we set $\boldsymbol{W^{(2)}}=0$, $\frac{\partial l}{\partial \boldsymbol{u}}=\frac{\partial l}{\partial \boldsymbol{a}} *(\boldsymbol{W^{{2}}*H(u)})^T=\boldsymbol{0}$,Thus $\frac{\partial l}{\partial \boldsymbol{W^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}*\boldsymbol{x^T}=\boldsymbol{0}$, $\frac{\partial l}{\partial \boldsymbol{b^{(1)}}}=\frac{\partial l}{\partial \boldsymbol{u}}=\boldsymbol{0}$

As the gradient of $\boldsymbol{W^{(2)},W^{(1)},b^{(1)}}$ all equals to zero or zero vectors, if we perform SGD, nothing will be added to the parameters we aiming to learn , which are $\boldsymbol{W^{(2)},W^{(1)},b^{(1)}}$.

### 2.3

$a=\boldsymbol{W^{(2)}u}+\boldsymbol{b^{(2)}}=\boldsymbol{W^{(2)}(W^{(1)}x+b^{(1)})}+\boldsymbol{b^{(2)}}=\boldsymbol{W^{(2)}W^{(1)}x+}+\boldsymbol{W^{(2)}b^{(1)}+b^{(2)}}$

$\boldsymbol{U=W^{(2)}W^{(1)}, v=W^{(2)}b^{(1)}+b^{(2)}}$


--------------------

## Problem 3
### 3.1
$w_{t+1}=w_{t}-\alpha*\frac{\partial L(w)}{\partial w}=w_{t}-\alpha * \Sigma_{i=1}^n(\phi(x_i)\phi(x_i)^Tw-\phi(x_i)y_i+\lambda w)=w_{t}-\alpha * (\Phi^T\Phi w-\Phi^T \boldsymbol{y}+\lambda w)$


$\Phi=[\phi(x_1)^T,\phi(x_2)^T,...,\phi(x_n)^T]^T,\Phi \in \boldsymbol{R}^{N*M}$


$\boldsymbol{y}=[y_1^T,y_2^T,...,y_n^T]^T,\boldsymbol{y} \in \boldsymbol{R}^{N}$

### 3.2
With $M$ too large and we are conducting gradient descent on all $N$ samples, the computation cost will be too large or even infeasible.


### 3.3
#### (1):
$w_0=\boldsymbol{0}$

We suppose if $w_t$ is a linear comination of $\phi(x_i)$, then $w_{t+1}$ will also be a linear combination of $\phi(x_i)$

$w_1=w_0+\alpha*\Sigma_{i=1}^n\phi(x_i)y_i=\alpha*\Sigma_{i=1}^n\phi(x_i)y_i=\Sigma_{i=1}^n\alpha y_i \phi(x_i)=\Sigma_{i=1}^n \beta_i^{(1)}\phi(x_i)$


$w_2=w_1-\alpha * \Sigma_{i=1}^n(\phi(x_i)\phi(x_i)^Tw_1-\phi(x_i)y_i+\lambda w_1)=(1-\alpha n\lambda)w_1-\alpha * \Sigma_{i=1}^n(\phi(x_i)\Sigma_{j=1}^n\beta_j^{(1)}\phi(x_i)^T\phi(x_j)-\phi(x_i)y_i)=(1-\alpha n\lambda)w_1-\Sigma_{i=1}^n\alpha *(\Sigma_{j=1}^n(\beta_j^{(1)}\phi(x_i)^T\phi(x_j))-y_i)*\phi(x_i)=\Sigma_{i=1}^n(1-\alpha n \lambda\beta_i^{(1)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(1)}\phi(x_i)^T\phi(x_j))-y_i))*\phi(x_i)$

As $\Sigma_{j=1}^n\beta_j^{(1)}\phi(x_i)^T\phi(x_j), y_i$ are scalars, $(1-\alpha n \lambda\beta_i^{(1)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(1)}\phi(x_i)^T\phi(x_j))-y_i))$ will also be scalar, which is $\beta_i^{(2)}$

$w_2=\Sigma_{i=1}^n \beta_i^{(2)}\phi(x_i)$

So the result works from $w_1$ to $w_2$

Now we suppose $w_t=\Sigma_{i=1}^n \beta_i^{(t)}\phi(x_i)$

$w_{t+1}=w_t-\alpha * \Sigma_{i=1}^n(\phi(x_i)\phi(x_i)^Tw_t-\phi(x_i)y_i+\lambda w_t)=(1-\alpha n\lambda)w_t-\alpha * \Sigma_{i=1}^n(\phi(x_i)\Sigma_{j=1}^n\beta_j^{(t)}\phi(x_i)^T\phi(x_j)-\phi(x_i)y_i)=(1-\alpha n\lambda)w_t-\Sigma_{i=1}^n\alpha *(\Sigma_{j=1}^n(\beta_j^{(t)}\phi(x_i)^T\phi(x_j))-y_i)*\phi(x_i)=\Sigma_{i=1}^n(1-\alpha n \lambda\beta_i^{(t)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(t)}\phi(x_i)^T\phi(x_j))-y_i))*\phi(x_i)$

As $\Sigma_{j=1}^n\beta_j^{(t)}\phi(x_i)^T\phi(x_j), y_i$ are scalars, $(1-\alpha n \lambda\beta_i^{(t)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(t)}\phi(x_i)^T\phi(x_j))-y_i))$ will also be scalar, which is $\beta_i^{(t+1)}$

$w_{t+1}=\Sigma_{i=1}^n \beta_i^{(t+1)}\phi(x_i)$

With induction proved, we can now assume as long as $w_t$ is a linear comination of $\phi(x_i)$, then $w_{t+1}$ will also be a linear combination of $\phi(x_i)$. With $w_0=\boldsymbol{0}$, which is $\Sigma_{i=1}^n 0*\phi(x_i)$, a linear comination of $\phi(x_i)$, all $w_t$ will be linear combination of $\phi(x_i)$


#### (2)
Use the induction we proved in (1), $w_{t+1}=\Sigma_{i=1}^n(1-\alpha n \lambda\beta_i^{(t)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(t)}\phi(x_i)^T\phi(x_j))-y_i))*\phi(x_i)$

$\beta_i^{(t+1)}=(1-\alpha n \lambda\beta_i^{(t)}- \alpha *(\Sigma_{j=1}^n(\beta_j^{(t)}\phi(x_i)^T\phi(x_j))-y_i))$


-----------------
## Problem 4
### 4.1
$w^*=\argmin_{w\in R^D}\Sigma_{i=1}^N -y_i\boldsymbol{w^Tx_i} +\lambda(\boldsymbol{w^Tw}-1)=\argmin_{w\in R^D}F(w)$

We find stationary point:

$\frac{\partial F(w)}{\partial w}=2\lambda \boldsymbol{w}-\Sigma_{i=1}^Ny_i\boldsymbol{x_i}=0$

$w^*=\frac{1}{2\lambda}\Sigma_{i=1}^Ny_i\boldsymbol{x_i}=\frac{1}{2\lambda}(\Sigma_{i:x_i\in C_1}x_i-\Sigma_{j:x_j\in C_{-1}}x_j)$


### 4.2

$||w^*||^2=||\frac{1}{2\lambda}(\Sigma_{i:x_i\in C_1}x_i-\Sigma_{j:x_j\in C_{-1}}x_j)||^2=1$

$\lambda=\frac{||\Sigma_{i:x_i\in C_1}x_i-\Sigma_{j:x_j\in C_{-1}}x_j||}{2}$

### 4.3

We can't use SGD since for each iteration , even if we pick one sample, we have to calculate the whole datapoints for the gradient and the gradient is same for all datapoints.





