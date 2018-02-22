
# ML_Courses
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
**CONVOLVE** the original image matrix using a **kernel/ filter matrix** (6*6 conv 3*3 = (6-3+1)*(6-3+1))

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

### Week 2. Deep convolutional models: case studies




### Week 3. Object detection




### Week 4. Special applications: Face recognition & Neural style transfer
## 5. Sequence Models （Mar 1 - Mar. 15)
