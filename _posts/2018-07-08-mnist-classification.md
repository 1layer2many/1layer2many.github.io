---
layout: post
title: MNIST dataset classification using Keras
subtitle: Including a basic introduction to CNN...
# gh-repo: daattali/beautiful-jekyll
# gh-badge: [star, fork, follow]
tags: [keras, mnist, cnn]
comments: false
---

It's been a while since my last (and first) post. So to formally publish my first post, let's review the basics of neural nets with a look into MNIST classification using the Keras library. But before we dive into the nitty gritty of Keras, let's take a look at how convolutional neural nets.

## What are neural nets?

According to wiki:

> "A neural network is either a biological neural network, made up of real biological neurons, or an artificial neural network, for solving artificial intelligence problems."

But what does that actually mean? Basically, a neural net or, in our case, an artificial neural net is meant operate similar to biological neural networks in our brain. Neurons represent the most basic units of a neural net. Every neuron is connected to multiple neurons, which work together to process an input and generate an output based on the parameters learned by the neurons.

But neurons need to learn to process its input in order to

![neural_net](https://res.cloudinary.com/dirqzbilx/image/upload/v1563976132/neural_net_basic_nivx6h.png){: .center-block :}


You can write regular [markdown](http://markdowntutorial.com/) here and Jekyll will automatically convert it to a nice webpage.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](http://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Here is some bold text**

## Here is a secondary heading

Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |


How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!


Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.