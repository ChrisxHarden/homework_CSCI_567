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










