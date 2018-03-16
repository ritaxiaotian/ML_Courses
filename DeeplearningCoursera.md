
# Machine_Learning_Courses
Machine Learning Courses

## 1. Neural Networks and Deep Learning （Jan 30 complete）
### Week 1. Introduction to deep learning

### Week 2. Neural Networks Basics

Binary Classification, Logistic Regression, Cost Function, Gradient Descent, Vectorization, Broadcasting, etc.

### Week 3. Shallow neural networks

Neural Network Representation,  Activation functions, Derivatives of activation functions, Backpropagation, Random Initialization

### Week 4. Deep Neural Networks

Deep L-layer neural network, Forward Propagation in a Deep Network, Building blocks of deep neural networks, Forward and Backward Propagation, Parameters vs Hyperparameters, 

## 2. Improving Deep Neural Networks: Hyperparameter tuning, Regularization and Optimization （Feb 15 complete）
### Week 1. Practical aspects of Deep Learning

Train / Dev / Test sets,Bias / Variance, Basic Recipe for Machine Learning,Regularization,Dropout Regularization, Other regularization methods, Normalizing inputs, Vanishing / Exploding gradients, Weight Initialization for Deep Networks, Numerical approximation of gradients, Gradient checking, Gradient Checking Implementation Notes, Initialization, Regularization,Gradient Checking

### Week 2. Optimization algorithms

Mini-batch gradient descent,Understanding mini-batch gradient descent,Exponentially weighted averages, Understanding exponentially weighted averages,Bias correction in exponentially weighted averages, Gradient descent with momentum, RMSprop, Adam optimization algorithm, Learning rate decay,The problem of local optima

### Week 3. Hyperparameter tuning, Batch Normalization and Programming Frameworks


Tuning process, Using an appropriate scale to pick hyperparameters,Hyperparameters tuning in practice: Pandas vs. Caviar, Normalizing activations in a network, Fitting Batch Norm into a neural network,Batch Norm at test time, Softmax Regression, Training a softmax classifier, Deep learning frameworks, TensorFlow

## 3. Structuring Machine Learning Projects （Feb 9 complete）
### Week 1. ML Strategy (1)

Why ML Strategy,Orthogonalization,Single number evaluation metric,Satisficing and Optimizing metric,Train/dev/test distributions,Size of the dev and test sets,When to change dev/test sets and metrics,Why human-level performance?,Avoidable bias, Understanding human-level performance,Surpassing human-level performance,Improving your model performance

### Week 2. ML Strategy (2)

Carrying out error analysis,Cleaning up incorrectly labeled data,Build your first system quickly, then iterate,Training and testing on different distributions,Bias and Variance with mismatched data distributions,Addressing data mismatch,Transfer learning,Multi-task learning,What is end-to-end deep learning?,Whether to use end-to-end deep learning


## 4. Convolutional Neural Networks （Feb 25 COMPLETE）

### Week 1. Convolutional Neural Networks
**1.1 CONVOLVE** the original image matrix using a **kernel/ filter matrix** (6*6 conv 3*3 = (6-3+1)*(6-3+1))

vertical edge detection matix

    1 0 -1           

    1 0 -1      

    1 0 -1         

Horizontal edge detection

     1  1  1

     0  0  0
 
    -1 -1 -1

sobel filter

    1 0 -1

    2 0 -2

    1 2 -1

Deep learning

    w1 w2 w3

    w4 w5 w6

    w7 w8 w9

Let the neural nets learn the exact values of w (machine learning learning the parameters for edge detection)

#### 1.2 Padding:

n*n image matrix; f*f filter size: result in (n-f+1) * (n - f + 1) matrix.

Disadvantage:

1. shrinking output

2. throw away info from edge

Padding: (n + 2p - f + 1)

“Valid Convolution": No padding

"Same Convolution": Pad so that the output size is the same as the input size: p = (f - 1) / 2

**f is usually Odd**

#### 1.3 Strided Convolutions

Stride = 2 (instead of 1 for common convolution)


n*n image matrix; f*f filter size; padding p; stride s: result in ((n + 2p - f)/s + 1) * ((n + 2p - f)/s + 1)  matrix.

Acctually : cross correlation instead of convolution (since there is no flipping(vertical and horizontal flipping) of the filter matrix)

#### 1.4 Convolutions Over Volume

Convolutions on RGB images

Height * Width * Channels

(6*6*6 image matrix) Cov (3*3*3 filter) = (4*4 result)

#### 1.5 multiple filters
    horizontal edge detector
    
    vertical edge detector
    
    red color edge detector
    
    green color edge detector
    
    **summary**
    
    image: nh * nw * nc
    
    filter: f*f*f*nc
    
    (n-f+1) * (n - f + 1) * mc
    
    mc: number of filters
    
    If you have 10 filters that are 3*3*3 in one layer of a neural network, how many parameters does that layer have?
    
    For each filter: numer of parameters is 3*3*3 + bias = 28; for 10 fileters, parameters are 280


#### 1.6 One Layer of a Convolutional Network Example

    fll<sup>l</sup> = filter size
    pl = padding
    sl = stride
    ncl = number of filters
    input = (nH


#### 1.7 Simple Convolutional Network Example


### Week 2. Deep convolutional models: case studies




### Week 3. Object detection




### Week 4. Special applications: Face recognition & Neural style transfer
## 5. Sequence Models （Mar 1 - Mar. 15)
