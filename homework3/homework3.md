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



