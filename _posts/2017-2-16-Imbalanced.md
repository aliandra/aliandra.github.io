---
layout: post
title: Imbalanced Classes
thumbnail: /images/croton.jpg
---

dealing with imbalanced classes in a classification problem

![_config.yml]({{ site.baseurl }}/images/croton.jpg)

*Beautiful day at Croton Point Park*

 
While working on my first classification project, after spending days gathering, cleaning, exploring, and feature engineering my data, I was finally ready to throw it all in a model! I used sklearn's logistic regression to build the model, and once the training was done, checked the model's accuracy on my test data. I almost couldn't believe my eyes- 85% accuracy! And on my first try. I thought it was too good to be true... wait, is it too good to be true? I dove back into my data and realized that about 85% of my data belonged to one class. For this post I want to share what I learned about imbalanced classes.

An imbalanced class distribution occurs when classes are not represented equally in the dataset and there are significantly more observations belonging to one class. This may create a bias in your model since the classification algorithm will be trained on data largely influenced by one class. Most algorithms are accuracy driven and want to optimize the error rate (percentage of incorrect predictions). This means it will ignore the data distribution and treat all misclassification errors equally, potentially predicting the majority class in every example (which is what happened in my case). 

Here are some possible solutions:

### Random Oversampling
We can balance our classes by randomly selecting observations from the minority class to be replicated in the dataset. Basically we are adding additional copies of preexisting examples to the dataset to artificially balance the classes. The biggest drawbacks to this method is that it can promote overfitting where predictions on unseen data might be worse.

### Random Undersampling
Similar to oversampling, we can undersample by randomly selecting observations in the majority class to be included in the dataset, while leaving the other majority cases out. By ignoring some of the majority class examples, we can better balance the data. The main drawback with this technique is that we are throwing away potentially useful data. 

### Change Performance Metrics
When it comes to imbalanced data, using an accuracy metric can be misleading. Try looking at Precision (measures how many observations) and Recall() metrics instead. If you're a visual person like me, generate a Confusion Matrix.

When all else fails, get creative! Dig around on the internet and see what others have done to solve this problem. There are many other interesting methods I've read on StackOverflow and Quora such as generating synthetic observations, using informed undersampling, penalized models, and more. Happy Classifying!