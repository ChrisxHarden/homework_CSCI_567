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


## Problem 2







