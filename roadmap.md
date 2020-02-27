---
layout: page
title: "Roadmap"
date: 2019-12-11 22:29:53 +0900
permalink: /roadmap/
header-includes:
- \usepackage{amsmath}
---
**Artificial Intelligence**
- [**Machine Learning**](#ML) (or Statistical Learning or Data Mining or whatever)
- [**Deep Learning**](#DL)
- [**Reinforcement Learning**](#RL)
- [**Artificial Intelligence**](#AI)

**Economics & Finance**
- [**Mathematical Economics**](#mathecon)
- [**Econometrics**](#econo)
- [**Quantitative Finance**](#quant)
- [**Game Theory**](#game)

**Mathematics**
- [**Probability & Statistics**](#PS)
- [**Complex Analysis**](#compa)
- [**Functional Analysis**](#funca)
- [**Optimization**](#opt)

&emsp;
<a name="ML"></a>
### Machine Learning

- **Supervised Learning**

    - **Regression**
    
        - [Linear Regression](/ML/reg/#linreg)
            - [Locally Weighted Linear Regression](/ML/reg/#lwr)
            - [Newton's Method](/ML/reg/#newton)
        - [Generalized Linear Models (GLM)](/ML/reg/#glm)
            - [Bernoulli Distribution](/ML/reg/#bernoulli)
            - [Gaussian Distribution](/ML/reg/#gaussian)
            - [Poisson Distribution](/ML/reg/#poisson)
            - [Gamma Distribution](/ML/reg/#gamma)
            - [Beta Distribution](/ML/reg/#beta)
            - [Dirichlet Distribution](/ML/reg/#dirichlet)
            - [Method of Constructing GLMs](/ML/reg/#construct)  
    <br/>
    - **Classification**
    
        - [Logistic Regression](/ML/reg/#logreg)
        - [Softmax Regression](/ML/reg/#softmax)
        - [Generative Learning Algorithms](/ML/GLA/)
            - [Gaussian Discriminant Analysis](/ML/GLA/#gda)
            - [Naive Bayes Classifier](/ML/GLA/#nb)
                - [Laplace Smoothing](/ML/GLA/#laplace)
        - [Support Vector Machine (SVM)](/ML/SVM/)
            - [Functional & Geometric Margins](/ML/SVM/#margin)
            - [Lagrange Duality](/ML/SVM/#lagrange)
            - to be continued...
        - Perceptron
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

References:
* ColumbiaX. <a href="https://www.edx.org/micromasters/columbiax-artificial-intelligence" target="__blank">Artificial Intelligence MicroMasters Program</a>. edX Inc.
* Andrew Ng. <a href="https://see.stanford.edu/Course/CS229" target="__blank">CS229 - Machine Learning</a>. Stanford University.
* Mitchell, T. <a href="http://www.cs.cmu.edu/~tom/10701_sp11/lectures.shtml" target="__blank">10-701 - Machine Learning</a>. Carnegie Mellon University.


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
        - [Intuition of Sequence Models](/DL/RNN/#intsm)
        - [Intuition of RNN](/DL/RNN/#intrnn)
        - [RNN Types](/DL/RNN/#layers)
        - [Language Model](/DL/RNN/#lm)
    - [RNN Variations](/DL/RNN/#var)
        - [GRU](/DL/RNN/#gru)
        - [LSTM](/DL/RNN/#lstm)
        - [Bidirectional RNN](/DL/RNN/#birnn)
        - [Deep RNN](/DL/RNN/#drnn)
    - Word Embeddings
        - [One-hot representation](/DL/RNN/#ohr)
        - [Featurized representation](/DL/RNN/#fr)
        - [Learning 1: Word2Vec](/DL/RNN/#word2vec)
        - [Learning 2: Negative Sampling](/DL/RNN/#negsam)
        - [Learning 3: GloVe](/DL/RNN/#glove)
    - Sequence Modeling
        - [Sentiment Classification](/DL/RNN/#sent)
        - [Sequence to Sequence](/DL/RNN/#seq2seq)
        - [Beam Search](/DL/RNN/#beam)
        - [Bleu Score](/DL/RNN/#bleu)
        - [Attention Model](/DL/RNN/#attention)  

References:
* Andrew Ng. <a href="https://www.coursera.org/specializations/deep-learning" target="__blank">Deep Learning Specialization</a>. Coursera Inc.
* Goodfellow, I. Bengio, Y. Courville, A. <a href="http://www.deeplearningbook.org/" target="__blank">Deep Learning</a>. MIT Press.

&emsp;
<a name="RL"></a>
### Reinforcement Learning

&emsp;
<a name="AI"></a>
### Artificial Intelligence

&emsp;
<a name="mathecon"></a>
### Mathematical Economics (経済数学)

- [Mathematics for Economics: 経済数学](../../assets/keizai.pdf)

Claim: This chapter is an English-translated summary of the book "経済数学" published by Keio University in order for me to learn Japanese in order to take Japanese-taught Math courses.

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