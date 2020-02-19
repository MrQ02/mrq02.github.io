---
layout: page
title: "Roadmap"
date: 2019-12-11 22:29:53 +0900
permalink: /roadmap/
header-includes:
- \usepackage{amsmath}
---
**Data Science (AI)**
- [**Machine Learning**](#ML)
- [**Deep Learning**](#DL)
- [**Reinforcement Learning**](#RL)
- [**Artificial Intelligence**](#AI)
- [**Probability & Statistics**](#PS)

**Economics & Finance (Quantitative)**
- [**Econometrics**](#Econ)
- [**Quantitative Finance**](#quant)
- [**Game Theory**](#game)

**Mathematics**
- [**Real Analysis**](#reala)
- [**Complex Analysis**](#compa)
- [**Functional Analysis**](#funca)
- [**Optimization**](#opt)

&emsp;
<a name="ML"></a>
### Machine Learning

- **Supervised Learning**

    - **Regression**
    
        - [Linear Regression](/ML/linreg/)
        - [Generalized Linear Models (GLM)](/ML/GLM/)
        - Nonlinear Regression  
        <br/>
    - **Classification**
    
        - [Logistic Regression](/ML/logreg/)
        - [Gaussian Discriminant Analysis (GDA)](/ML/GDA/)
        - Naive Bayes Classifier
        - Perceptron
        - [Support Vector Machine (SVM)](/ML/SVM/)
        - k-Nearest Neighbor (k-NN)
        - Decision Trees
        - Boosting  
<br/>
- **Unsupervised Learning (Clustering)**  

    - BIRCH
    - CURE
    - Hierarchical
    - k-means
    - Expectation-Maximization (EM)
    - DBSCAN
    - OPTICS
    - Mean-shift  
<br/>
- Dimensionality Reduction  

    - Factor Analysis
    - PCA
    - ICA
    - CCA
    - LDA
    - NMF
    - t-SNE  
<br/>
- Graphical Models 

    - Bayesian Network
    - Conditional Random Field
    - Hidden Markov  
<br/>
- Association Rules

    - Apriori
    - ECLAT
    - FP-growth  
<br/>
- Theory

    - Bias-Variance Tradeoff
    - (Computational) Learning Theory
    - Empirical Risk Minimization (ERM)
    - Occam Learning
    - PAC Learning
    - VC Theory  

&emsp;
### <a name="DL"></a>Deep Learning

- [**Basics of NN**](/DL/ANN/)
    
    - [Neural Network Representation](/DL/ANN/#nn)
    - [Activation Functions](/DL/ANN/#af)
    - Training
        - [Forward Propagation](/DL/ANN/#fp)
        - [Backward Propagation](/DL/ANN/#bp)
        - Example: [Forward & Backward Step: Stochastic](/DL/ANN/#fbss)
        - Example: [Forward & Backward Step: Mini-batch](/DL/ANN/#fbsb)
        - [Reverse Differentiation](/DL/ANN/#rd)
    - [Gradient Descent](/DL/ANN/#gd)  
<br/>
- [**Improvements**](/DL/imp/)

    - [Train/Test Split](/DL/imp/#split)
    - [Initialization](/DL/imp/#init)
    - [Data Fitting](/DL/imp/#fit) with refined [procedure](/DL/imp/#pro)
    - [Regularization](/DL/imp/#reg)
        - Regularization on LogReg
            - [L2 Regularization](/DL/imp/#L2)
            - [L1 Regularization](/DL/imp/#L1)
        - [Regularization on NN](/DL/imp/#nnreg)
        - [Dropout](/DL/imp/#dp)
        - [Data Augmentation](/DL/imp/#da)
        - [Early Stopping](/DL/imp/#es)
        - [Orthogonalization](/DL/imp/#og)
        - [Feature Scaling (normalization)](/DL/imp/#norm)
        - [Gradient Checking](/DL/imp/#gc)
    - [Optimization](/DL/imp/#op)
        - [Mini-Batch Gradient Descent](/DL/imp/#mbgd)
        - Gradient Descent with Momentum
            - [Exponentially Weighted (Moving) Average](/DL/imp/#ema)
                - [Bias Correction](/DL/imp/#bc)
            - [Momentum](/DL/imp/#m)
        - [RMSprop](/DL/imp/#rmsprop)
        - [Adam](/DL/imp/#adam)
        - [Learning Rate Decay](/DL/imp/#lrd)
        - [Problems with optimization](/DL/imp/#po)
    - [Hyperparameter Tuning](/DL/imp/#hpt)
    - [Batch Normalization](/DL/imp/#bn)  
<br/>
- [**CNN**](/DL/CNN/)

    - Basics of CNN
        - [Intuition of CNN](/DL/CNN/#cnn)
        - [General Formula of Convolution](/DL/CNN/#formula)
        - [CNN Layers](/DL/CNN/#layers)
            - Convolution
            - [Pooling](/DL/CNN/#pool)
            - [Fully Connected](/DL/CNN/#fc)
    - CNN Examples
        - [LeNet-5](/DL/CNN/#lenet)
        - [AlexNet](/DL/CNN/#alexnet)
        - [VGG](/DL/CNN/#vgg)
        - Inception
            - [ResNets](/DL/CNN/#res)
            - [1x1 Conv](/DL/CNN/#nin)
            - [The Inception](/DL/CNN/#inception)
        - [Conv1D & Conv3D](/DL/CNN/#conv1d)
    - [Object Detection](/DL/CNN/#od)
        - Bounding Box
        - Landmark Detection
        - Sliding Windows
        - Intersection over Union
        - [YOLO (You Only Look Once)](/DL/CNN/#yolo)
            - Non-Max Suppression
            - Anchor Boxes
        - [R-CNN](/DL/CNN/#rcnn) (to be continued)
    - [Face Recognition](/DL/CNN/#fr)
        - [Siamese Network](/DL/CNN/#sn)
            - [Triplet Loss](/DL/CNN/#tl)
            - [Binary Classification](/DL/CNN/#bc)
        - [Neural Style Transfer](/DL/CNN/#nst)  
<br/>
- [**RNN**](/DL/RNN/)

    - Basics of RNN

&emsp;
<a name="RL"></a>
### Reinforcement Learning

&emsp;
<a name="AI"></a>
### Artificial Intelligence

&emsp;
<a name="PS"></a>
### Probability & Statistics

&emsp;
<a name="Econ"></a>
### Econometrics

&emsp;
<a name="quant"></a>
### Quantitative Finance

- **Financial Foundations**
    - [Products & Markets](/quant/promar/)
    - [Derivatives](/quant/basicd)
    - [Assets](/quant/assets/)
- **Mathematical Foundations**
    - [Stochastic Calculus](/quant/stocalc)
    - [Black-Scholes Model](/quant/bsm)
- **Numerical Methods**
- **Advanced Topics**