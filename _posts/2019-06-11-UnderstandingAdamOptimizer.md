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

<img src="https://www.google.com/url?sa=i&source=images&cd=&ved=2ahUKEwjWo7HqtuHiAhUaU30KHX_jCVAQjRx6BAgBEAU&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FOrdinary_least_squares&psig=AOvVaw2wbF62AkGJALM-IefYvBQ8&ust=1560342473867397">

For the above image, the equation is laid down in the following manner

<img src="https://latex.codecogs.com/svg.latex?\Large&space;y=w.x" title="Linear Regression Example"/>

Objective function gets translated to
<img src="https://latex.codecogs.com/svg.latex?\Large&space;\min\sum_{i}^{n}{(y_i-wx_i)}^2" title="OLS Objective Function"/>
where n = number of rows

The 6 major sections in understanding Adam Optimizer are the following
 *  Gradient
Gradient calculation in mathematical terms means, finding the derivative of your Objective Function w.r.t the variable that you are trying to calculate
<img src="https://latex.codecogs.com/svg.latex?\Large&space;\frac{d}{dw}\min\sum_{i}^{n}{(y_i-wx_i)}^2" title="Differentiate Objective Function 1"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;\frac{d}{dw}\min{(y-w.x)}^2" title="Differentiate Objective Function 2"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;2{(y-wx)}\frac{d}{dw}{-w.x}" title="Differentiate Objective Function 3"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;If\hspaceE={(y-wx)}" title="Differentiate Objective Function 4"/>
<img src="https://latex.codecogs.com/svg.latex?\Large&space;Gradient\hspace=\hspace-2Ex" title="Differentiate Objective Function 4"/>

 *  Moment 1

 *  Moment 2
 *  Moment 1 Scaling
 *  Moment 2 Scaling
 *  Weight updates
 

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
