# Sign-Language-Digits

## Context
Sign languages (also known as signed languages) are languages that use manual communication to convey meaning. This can include simultaneously employing hand gestures, movement, orientation of the fingers, arms or body, and facial expressions to convey a speaker's ideas. Source: https://en.wikipedia.org/wiki/Sign_language

## Content

Details of datasets:
Image size: 64x64
Color space: Grayscale
File format: npy
Number of classes: 10 (Digits: 0-9)
Number of participant students: 218
Number of samples per student: 10
Details of datasets in GitHub Repo:
Repo: github.com/ardamavi/Sign-Language-Digits-Dataset

Image size: 100x100
Color space: RGB
Acknowledgements
Sign Language Digits Dataset
Dataset GitHub Page: github.com/ardamavi/Sign-Language-Digits-Dataset
By Turkey Ankara Ayrancı Anadolu High School Students
Turkey Ankara Ayrancı Anadolu High School's Sign Language Digits Dataset
This dataset prepared by our school students.

## Project executives:
Zeynep Dikle & Arda Mavi
Turkey Ankara Ayrancı Anadolu High School Students

## For Development:
Processing Dataset:
For processing the dataset, look up Arda Mavi's GitHub Gist: gist.github.com/ardamavi/get_dataset.py

## Inspiration
What is that person saying?


## My Approach :

1. Using CNN:
input----------filter-------------------output

n $\times$ n----*----f $\times$ f --------$[\frac{n+2p-f}{s} + 1] \times [\frac{n+2p-f}{s} + 1]$

![Screenshot 1](pic1.png?raw=true "Optional Title 1")

2. Using Logisitic Regression :
-> As you can see, we have 348 images and each image has 4096 pixels in image train array.
-> Also, we have 62 images and each image has 4096 pixels in image test array.
-> Then take transpose of weight matrix :
![Screenshot 1](pic2.jpeg?raw=true "Optional Title 1")
   
    Parameters are weight and bias.
    Weights: coefficients of each pixels
    Bias: intercept
    z = (w.t)x + b => z equals to (transpose of weights times input x) + bias
    In an other saying => z = b + px1w1 + px2w2 + ... + px4096*w4096
    y_head = sigmoid(z)
    Sigmoid function makes z between zero and one so that is probability. You can see sigmoid function in computation graph.

        Parameters are weight and bias.
        Weights: coefficients of each pixels
        Bias: intercept
        z = (w.t)x + b => z equals to (transpose of weights times input x) + bias
        In an other saying => z = b + px1w1 + px2w2 + ... + px4096*w4096
        y_head = sigmoid(z)
        Sigmoid function makes z between zero and one so that is probability. You can see sigmoid function in computation graph.
    Why we use sigmoid function?
        It gives probabilistic result
        It is derivative so we can use it in gradient descent algorithm (we will see as soon.)
    Lets make example:
        Lets say we find z = 4 and put z into sigmoid function. The result(y_head) is almost 0.9. It means that our classification result is 1 with 90% probability.
    Now lets start with from beginning and examine each component of computation graph more detailed.


  Initializing parameters

    As you know input is our images that has 4096 pixels(each image in x_train).
    Each pixels have own weights.
    The first step is multiplying each pixels with their own weights.
    The question is that what is the initial value of weights?
        There are some techniques that I will explain at artificial neural network but for this time initial weights are 0.01.
        Okey, weights are 0.01 but what is the weight array shape? As you understand from computation graph of logistic regression, it is (4096,1)
        Also initial bias is 0.
    Lets write some code. In order to use at coming topics like artificial neural network (ANN), I make definition(method).
Forward Propagation

    The all steps from pixels to cost is called forward propagation
        z = (w.T)x + b => in this equation we know x that is pixel array, we know w (weights) and b (bias) so the rest is calculation. (T is transpose)
        Then we put z into sigmoid function that returns y_head(probability). When your mind is confused go and look at computation graph. Also equation of sigmoid function is in computation graph.
        Then we calculate loss(error) function.
        Cost function is summation of all loss(error).
        Lets start with z and the write sigmoid definition(method) that takes z as input parameter and returns y_head(probability)

    Initialize parameters weight and bias
    Forward propagation
    Loss function
    Cost function
    Backward propagation (gradient descent)
    Prediction with learnt parameters weight and bias
    Logistic regression with sklearn


2-Layer Neural Network

    Size of layers and initializing parameters weights and bias
    Forward propagation
    Loss function and Cost function
    Backward propagation
    Update Parameters
    Prediction with learnt parameters weight and bias
    Create Model


