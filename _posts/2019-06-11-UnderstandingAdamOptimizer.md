---
layout: post
title:  "Understanding Adam Optimizer"
date:   2018-12-28 09:19:39 +0000
categories: Optimizers
---

Optimizers are the backbone of any machine learning algorithm, be it a simple Linear Regression OLS or be it GAN's, and RESNETs etc
I would like to discuss one of the  Optimizers that has become very popular nowadays **Adam Optimizer**

### Inspiration
If you are able to understand and code up the optimizers, you get a good understanding of hyper parameter tuning

### Methodology

Let us consider a simple Linear Regression problem statement for this example

<img height="300" width="300" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Linear_regression.svg/1280px-Linear_regression.svg.png">
 * **Equation**
For the above image, the representative equation is 
<img src="https://latex.codecogs.com/svg.latex?\Large&space;y=w.x" title="Linear Regression Example"/>

 * **Objective Function**
The Objective function gets translated to <img src="https://latex.codecogs.com/svg.latex?\Large&space;\min\sum_{i}^{n}{(y_i-wx_i)}^2" title="OLS Objective Function"/> <br/>

 *  **Gradient**
Gradient calculation in mathematical terms means, finding the derivative of your Objective Function w.r.t the variable that you are trying to calculate
<img src="https://latex.codecogs.com/svg.latex?\Large&space;Gradient=\frac{d}{dw}\min\sum_{i}^{n}{(y_i-wx_i)}^2" title="Differentiate Objective Function 1"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;\frac{d}{dw}\min{(y-w.x)}^2" title="Differentiate Objective Function 2"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;2{(y-wx)}\frac{d}{dw}{-w.x}" title="Differentiate Objective Function 3"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;If\hspaceE={(y-wx)}" title="Differentiate Objective Function 4"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;Gradient\hspace=\hspace-2Ex" title="Differentiate Objective Function 4"/>

```python
    error= y - np.matmul(x,weights.T)
    gradient = - np.matmul(x.T,error)
```
* **Moment 1** <br/>
Moment 1 is a moving average of the prior gradient values. There is a slight twist here. There are two contributions here
  * Prior Moment : There is a large weight assigned to the prior moment
  * Current Gradient : There is a small weight assigned to the current gradient
  
``` python
 moment1 = (beta1 * moment1) + ( 1 - beta1) * gradient
```

* **Moment 2** <br/>
Moment 2 is a moving average of the prior gradient values squared. There is a slight twist here too. There are two contributions here
  * Prior Moment : There is a large weight assigned to the prior moment
  * Current Gradient : There is a small weight assigned to the current gradient

``` python
 moment2 = (beta2 * moment2) + ( 1 - beta2) * np.power(gradient,2)
```

 *  **Moment 1 Scaling**
 *  **Moment 2 Scaling**
 *  **Weight updates**
 


 * **Final Code**

``` python
# Adam Optimizer

# Sample Data
y=np.array([1,2,3,4,5,6,7,8,9,10]).reshape(10,1)
x=np.array([[2,4,6,8,10,12,14,16,18,20],[3,6,9,12,15,18,21,24,27,30]]).reshape(10,2)

# Weight Initialization
weights=np.random.rand(2).reshape(1,2)

alpha=0.0001
beta1=0.9
beta2=0.999
epsilon = 1.000000 / np.power(10,8)
moment1=np.zeros(x.shape[1]).reshape(2,1)
moment2=np.zeros(x.shape[1]).reshape(2,1)

for iterationCount in range(1000000):
    error= y - np.matmul(x,weights.T)
    gradient = - np.matmul(x.T,error)
    moment1 = (beta1 * moment1) + ( 1 - beta1) * gradient
    moment2 = (beta2 * moment2) + ( 1 - beta2) * np.power(gradient,2)
    moment1hat = moment1 / ( 1 - np.power(beta1,iterationCount+1))
    moment2hat = moment2 / ( 1 - np.power(beta2,iterationCount+1))
    weights = weights - ((alpha * moment1hat) / ( np.sqrt(moment2hat) + epsilon )).T
    if(iterationCount % 10000 ==0):
        print("epoch {0} RMSE Error {1}".format(iterationCount,np.sum(np.power(error,2))/x.shape[0]))
    if((np.sum(np.power(error,2))/x.shape[0]) < 1):
        break
```

 * **Analysis**

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
