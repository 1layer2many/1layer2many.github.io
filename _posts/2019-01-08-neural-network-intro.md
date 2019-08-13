---
layout: post
title: A look into the working of GANs...
subtitle: ...and a dive into some of its implementations
bigimg: /img/banner.jpg
tags: [gan, cnn]
comments: false
---

```python
def create_disc_model():
    model = Sequential()

    model.add(Conv2D(filters=64, kernel_size=3, padding='same', strides=(2,2), 
            name='conv_layer_1', input_shape=(dim, dim, num_channels)))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Dropout(0.4))

    model.add(Conv2D(filters=64, kernel_size=3, padding='same', strides=(2,2),
            name='conv_layer_2'))
    model.add(LeakyReLU(alpha=0.2))
    model.add(Dropout(0.4))
  
    model.add(Flatten())
    model.add(Dense(1, activation='sigmoid'))
    model.compile(optimizer=keras.optimizers.Adam(lr=0.0002, beta_1=0.5),
            loss='binary_crossentropy',
            metrics=['accuracy'])

    return model
```
It's been a while since my last (and first) post. So to formally publish my first post, let's review the basics of neural nets with a deeper look into their architecture. But before we dive into the nitty gritty, let's take a look at how neural nets work at a top level.

## What are neural nets?

According to wiki...

> "A neural network is either a biological neural network, made up of real biological neurons, or an artificial neural network, for solving artificial intelligence problems."

But what does that actually mean? Basically, an artificial neural network (referred to as neural network henceforth) is meant to operate similar to biological neural networks in our brain. Neurons represent the most basic units of a neural net. An artificial neuron that receives a signal can process it and then signal additional neurons connected to it, which work together to recognize patterns that may be present in the input signals.

Neural networks can be used to extract features that can then be fed to other algorithms like clustering, classification and regression. Here, we will concentrate on the classification part of neural networks. Like most things in this universe, neurons need to learn to make sense of the input signals in order to be able to predict results. Thus any network needs to be trained on labeled dataset before it can be used to properly classify data. But before that, let's have a look at a neural network:

{% include image.html url="https://res.cloudinary.com/dirqzbilx/image/upload/v1563976132/neural_net_basic_nivx6h.png" description="Fig 1. A 2-layer neural net" %}

Figure 1 represents a 2-layer neural network. The number of layers constitute of the input and the hidden layers, with the output layer not counted in the layer count. The layers between input and output layers constitute the hidden layers, with every layer consisting of multiple neurons. These layers are hidden since they aren't visible as the output. Shallower networks such as the one show in figure 1 can only learn a certain number of features, leading to inaccurate predictions. With increasing number of hidden layers, the depth of the network increases resulting in what is known as **deep neural networks**. Modern neural network architectures almost exclusively use deep neural networks as they can learn a huge number of features provided enough data, helping increase the quality of the prediction made.

Now let's take a look at how a single neuron works.

{% include image.html url="https://res.cloudinary.com/dirqzbilx/image/upload/v1563991782/ann_node_h9282e.png" description="Fig 2. A neuron in a typical neural net" %}

As can be seen in figure 2, there's a weight associated with each input. When a neuron gets activated, it computes its state by summing over all the incoming inputs multiplied by its corresponding connection weight. There is a bias term (usually set to 1) associated with every neuron (along with it's own trainable weight). This makes sure that even with all-zero inputs, there's a non-zero probability of activation in the neuron. 

Following it's computation, the state passes through the neuron's activation function. Since the state is just a value at this point, the activation function helps make use of this value to determine an output. The activation function achieves this by normalizing the state value and then deciding whether or not to fire the successive neuron based on a threshold value.
 
One can also notice the transfer function to be a linear function, which means that the state is just a linear combination of the input variables. This isn't really useful as linear functions would effectively reduce the entire network to a single layered one. Hence, we make use of what we call non-linear activation functions. Non-linear activation functions can map the complexities of the given data which help the network in learning many interesting features. There are a variety of activation functions that are employed in architectures today with a variety of benefits, but that would be beyond the scope of this post. Maybe another post?

Anyhow, **training** a neural network then means calibrating the weights associated with the neurons by repeating two key steps, namely **forward** and **back propagation**. During forward propagation, we apply a set of weights to the input at each "layer" and calculate an output. There are various techniques of **initializing** the weights, the details of which can be found [here](https://www.deeplearning.ai/ai-notes/initialization/). Proper initialization can help speed up the convergence of the optimizer towards global minima. Meanwhile during back propagation, we measure the error between the obtained and actual output and adjust the weights accordingly so as to decrease the error margin.

{% include image.html url="https://res.cloudinary.com/dirqzbilx/image/upload/e_grayscale,q_100/v1564208820/forward_back_prop_rptvzl.png" description="Fig 3. Forward and backward propagation example for a 2-layer network" %}

Neural networks repeat both forward and back propagation until the weights are calibrated to accurately predict correct output. Similar to forward propagation, back propagation calculations occurs at each "layer". We begin by changing the weights between the hidden layer and the output layer and proceed to propagate the effects towards the initial layers. The change in weight is acquired by finding the derivative of the activation function, which gives us the rate of change at that function. Weight changes for preceding layer can be calculated from the output layer using **chain rule**. Over multiple iterations (or epochs), the network converges towards the global minimum leading to better predictions.

Following the training phase, the learned parameters are then used to make predictions. The prediction phase is structurally quite similar to the training phase, with two major differences. Firstly, unlike training, prediction is done in a single iteration as we aren't interested in the feedback from the prediction. The second difference follows from the first difference in that the error isn't back propagated through the network. The output of the network can be modified according to specific requirements by adding a final layer, which can be either discreet or continuous in nature.

These concepts briefly constitute the concepts relating to a neural network, which should be enough to get you started with various types of neural networks. Of course, things are much more complicated than what can be put together in this post. I'll put together another post with essential materials that should be just enough to get you started. But that should be it for this post. I hope you found this and the other articles on this blog to be helpful. Until next time then.  
