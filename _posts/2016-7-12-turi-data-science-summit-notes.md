---
layout: post
title: Live-blogging the 2016 Data Science Summit in SF
---
I'll be live-blogging Turi's 2016 Data Science Summit in San Francisc, CA. Hopefully my notes are relatively easy to
understand!

# Turi Data Science Summit Notes #
**July 12-13, 2016 @ The Fairmont Hotel**
Turi was formerly known as Dato, creators of SFrame and GraphLab Create

## Keynote -- Carlos Guestrin -- CEO Turi, Amazon Professor of Machine Learning, University of Washington ##
* <a href="https://twitter.com/guestrin?lang=en" target="_blank">@guestrin</a>
* Last year, Netflix spent $600 million on their AI team
* In 5 years, every application is going to be intelligent (will utilize some form of machine learning)

### Decision Trees Utilizing Node Decisions as non-linear Features for other models
* Transferable feature engineering

### What makes a ML platform agile? ###
* Turi now offers microservices (Turi predictive services) where you can utilize GraphLab Create
to deploy code to the cloud
* I'm guessing this would allow you to run ML models on GPUs?

#### Updating Models ####
* Models are stale the moment they are trained
* Prediction accuracy can improve up to 40% by leveraging real-time feedback
* Common approaches to fast adaptation
    * Frequent retraining, high-latency
    * Online learning, not general and difficult to debug

##### Online re-ranking #####
* Issue: preferences change depending on session
* Adaptive ML in production
    1. Train and deploy your model
    2. Online reranker black box
    3. Consume
* Online reranker uses activity data
* Train using non-linear data (like from decisions made by a decision tree model)

### Distributed deep learning ###
* Distributed training throughput increases as number of GPUs increases
* Distributed training convergence time decreases as number of GPUs increases
* Utilizing the Turi RPC layer via Python, you can get a 40-60% improvement in TensorFlow performance
over the standard RPC layer

### How can you trust your model? ###
* Netflix is trying to make customers more comfortable with an AI solution by making it real
to them
* For Doctors, they can make better decisions from recommender systems and can use the logic
and data behind the recommender systems to gain patient trust

#### Training a model to predict wolf v. husky ###
* Only one mistake -- do you trust the model?
* Upon further investigation, Carlos showed that the wolf predictor was actually a snow predictor

#### Famous 20 Newsgroups dataset ####
* Most good predictions due to misleading features: email addresses, names
* Models can test well as far as training, test, and validation error, or whatever other
error benchmark you want to use, but how do we get intuitive trust
* Explanations help improve your model
* Mechanical Turk experiment
    * "In a few rounds of using a Mechanical Turk experiment, can I get as good or better
    performance than my 'gold standard' model"
    * Mechanical Turk lead to better results
* <a href="https://github.com/google/inception" target="_blank">Google Inception</a> -- explaining deep learning by showing the detected features that lead to a
prediction

#### Game of Thrones Predictor ####
* Predicting whether characters will be alive or dead
* Carlos' model predicted that Ned Stark would be alive in Season 2
* Factors / features include
    * He's from the House of Stark
    * How many dead relatives does he have?

### Must-haves for ML in production ###
* Maximize resources, reuse features
* Never stop learning
* When scaling matters
* Explain yourself, explain your modles
* Get away from the "my curve is better than your curve"