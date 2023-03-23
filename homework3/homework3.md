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
2. Weighted average of Gini-impurity