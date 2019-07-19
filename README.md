# CNN

INTRODUCTION:
In this tutorial we will walk through Convolutional Neural Network. This tutorial is inspired from the Udacity tutorial on CNN.
Convolutional Neural Network is a special type of deep neural network having alternative convolutional and pooling layers. For most image classification task, CNN are used. Instead of MLP which use fully connected layer, CNN use different layers to detect patters among images which are feed forwarded. CNN have sparsly connceted layers and accept matrix as an input while MLP accepts vectors as an input.

I will already assume that we have knowledge about MLP neural networks. If not, I would recommend to have a look on MLP first. There are tons of tutorials on MLP. In this tutorial we will walk through to create CNN on CIFAR-10 database. These images fall into ten categories.In this project we create a network which will be able to predict the class of a particular image. I will tell more about the layers in CNN and hyperparameters as we go along. Without further due, lets get started.

![CIFAR-10](https://github.com/JauraSeerat/CNN/blob/master/cifar_data.png)
 
To work on implementaion of CIFAR-10 database open up cifar.ipynb file in this repository.
Before implementing it, I would suggest to read below architecture and process to learn more about CNN

 *Architecture of CNN:*
 Instead of MLP, which uses linear, fully connected layers, In CNN we will use 
* Convolutional Layers
* Pooling layers

But wait.. What is Convoluational and Pooling layers. What they do? Why we use them?

For instance lets take an image of dog. We will observe that there are number of things like nose, mouth, teeth  etc. which help to detect that this is dog . All these are called features of dog. When we pass such an image through CNN, these features are extracted out with the help of filters. Filters are tensors of square shape like 3 by 3, 5 by 5. The filters are specified by the users and they move across top to bottom and left to right of an image. 

*Filters* are tensor which keep track of spatial information and learn to extract features like edge detection, smooth curve, etc. The major part is to detect edges in the images and these are detected by the filters. It help to filter out unwanted information to amplify images.  There are high-pass filters where the changes occur in intensity very quickly like from black to white pixel and vice-versa. 

![Filter Image](https://github.com/JauraSeerat/CNN/blob/master/Filters.gif)
Image by [Convolutional Neural Networks (CNN, or ConvNets ...](https://medium.com/@phidaouss/convolutional-neural-networks-cnn-or-convnets-d7c688b0a207)

Before going through the process further, lets stop for a bit and learn some terminologies.

* Convolutional Layer: It is thought of as a stack of filtered images. It breaks the image into different section and process it. 
* Maxpooling layers: It reduce the images size which is recieved from convolutional layer and keep the most active pixels. maxpooling layer is applied after the convolutional layer. 
* Fully-connected layer: Layer which accept input as vector and provides us an output.

![CNN Image](https://github.com/JauraSeerat/CNN/blob/master/CNN.png)
Image by [https://www.researchgate.net/figure/Convolutional-neural-network-CNN-architecture_fig3_317268111]

The filter convolue with the image to detect patterns and features. After the filter is passed over the image, a feature map is generated which can be taken through the activation function (example: ReLU) . Then we can add lot to filters to detect some more patterns and features. After passing image through convolutional layers and activation function. We pass it through pooling layer to see the pixels meet certain threshold so that they can carry on further. We just reiterate the process number of times of making convolutional layers, passing image to them , then process through activation function and pooling layer so that our image start detecting patterns. *Remember the more convolutional layers you include, the more complex patterns it will detect in terms of shape and color.*  Then finally the image is passed through fully connected layers and we will recieve an output. *It is always a good practice to add dropout layer in between linear layers to prevent overfitting.*

So this was a basic understanding of how images are feed forwarded into CNN and how it detect patterns. Lets jump into the code. Continued...
