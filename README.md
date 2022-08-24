## Hi! 
This time let's talk about classification.
I think it's not worth explaining what classification is. But how it works is interesting.

Code https://github.com/MariaSultanbekova/computer_vision_projects/blob/main/dog's_breed_classification/dog's_breed_classification.ipynb

The classification neural network consists of a sequence of convolutional layers. 
It receives the image tensor, reduces its size, but at the same time increases the number of channels.
Here many people have a question, where did the additional channels come from?

![head](https://github.com/MariaSultanbekova/computer_vision_projects/blob/main/dog's_breed_classification/convolution_process.jpg)

At the beginning we have a 3-channel tensor, an image in RGB format.The convolutional layer then applies filters, which are masks.
Let's say we are looking for a cat in the image, the filters will be masks of whiskers, 
ears and tails, that is, they will look for characteristic features of the object. After applying each filter (mask) we get the tensor channel.
Therefore, the tensor after convolution has more channels.

----------------------------------------------------------------------------

We discussed how a simple classification neural network works. But the model that is now used everywhere is a little more complicated.

The idea is that we want to create a deep stack of convolutional layers to get as many useful features as possible. But with an increase in the number of layers, we will face the problem of a disappearing/increasing gradient.

To solve the problem, a concept called a residual network was introduced in this architecture. That is, we skip a certain amount of information every two layers of the network.

![head](https://github.com/MariaSultanbekova/computer_vision_projects/blob/main/dog's_breed_classification/residual_block.png)

The advantage of adding this type of connection skip is that if any layer degrades the performance of the architecture, it will be skipped by regularization.

## Model Training
To try to solve the classification task, I took a dataset with many dog breeds. Pre-processed the data, added augmentation to increase the dataset. 
I took the pre-trained Resnet-50 model, froze the layers in front of the classifier (stopped the gradient propagation), and trained only it.

![head](https://github.com/MariaSultanbekova/computer_vision_projects/blob/main/dog's_breed_classification/dogs_prediction.png)

Here's what happened as a result
