---
layout: page
title: "News Review"
date: 2020-12-15 22:40:00 +0900
permalink: /Blog/
header-includes:
- \usepackage{amsmath}
---
<br>
2020/12/15: [*Tiny four-bit computers are now all you need to train AI.*](https://www.technologyreview.com/2020/12/11/1014102/ai-trains-on-4-bit-computers/)  **MIT Technology Review**

Well, surprise, surprise. After a long time of witnessed over-saturation in the theoretical part of deep learning, we finally have some major breakthrough in the hardware part - reducing the number of bits for data representation from 16 bits to only 4 bits. This simply means that all the numerical values throughout the entire deep learning process have to be between -8 and 7.

Yes, yes, this is just rescaling, or so would you think. However, what is new about this rescaling is that it is applied onto every numerical range that you could possibly have. The author gave an example that when you have the output range from an activation function changing from 0.2~0.9 to 0.1~0.7 in the next round of training, this rescaling is applied onto both ranges. Yes, so basically you will always have the range -8~7, either stretched or shrinked. Even if you have a logarithmic scale, they will still rescale it to -8~7. Simple and convenient isn't it?

They ran the 4-bit training multiple times on various kinds of tasks. There was still a loss of accuracy but a significant improvement in computation speed and energy consumption. It will be released in the industry in about 3-4 years.

This is my first news review at late night. God I gotta wake up early for my job tmrw. To be honest, I do not have any opinion on this. Good that it can enhance computation and energy efficiency, but how dramatic is the influence? I don't know. Man I should read econ news or more "sparkling" tech news rather than this. IBM is the one getting the benefits anyway.

&emsp;

2020/12/16: [*The way we train AI is fundamentally flawed*](https://www.technologyreview.com/2020/11/18/1012234/training-machine-learning-broken-real-world-heath-nlp-computer-vision/)  **MIT Technology Review**

Thank you for this news Mr. Will. **Data shift** is an issue where our AI models are only adapted to the training data but not various types of data (which is actually the case in real life). However, **underspecification** is an essential issue from economics: Causal Inference. Yes, how do you know that your observations represent THE explanatory variables? Surprisingly, this is a very widely observed issue in AI applications nowadays.

Why does this issue exist? Well, our current training process for all AI models requires reaching a high accuracy on the test set. If they pass, they are good to be released. However, how do you know which model is better than another in various cases that are slightly different from each other? D'Amour suggested more testing with different datasets taken from the real world. It is costly, and the conclusion remains uncertain.

I have no comment about this article. It is just educational to me that there is this issue of underspecification.