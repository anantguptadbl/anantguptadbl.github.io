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
The 6 major sections in understanding Adam Optimizer are the following
 *  Gradient
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
