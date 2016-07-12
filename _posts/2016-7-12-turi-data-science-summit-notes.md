---
layout: post
title: Live-blogging the 2016 Data Science Summit in SF
---
**July 12-13, 2016 @ The Fairmont Hotel**
I'll be live-blogging Turi's 2016 Data Science Summit in San Francisco, CA. Hopefully my notes are relatively easy to
understand! ***Note: Turi was formerly known as Dato, creators of SFrame and GraphLab Create***

# Keynote -- Carlos Guestrin -- CEO Turi, Amazon Professor of Machine Learning, University of Washington #
* <a href="https://twitter.com/guestrin?lang=en" target="_blank">@guestrin</a>
* Last year, Netflix spent $600 million on their AI team
* In 5 years, every application is going to be intelligent (will utilize some form of machine learning)

## Decision Trees Utilizing Node Decisions as non-linear Features for other models ##
* Transferable feature engineering

## What makes a ML platform agile? ##
* Turi now offers microservices (Turi predictive services) where you can utilize GraphLab Create
to deploy code to the cloud
* I'm guessing this would allow you to run ML models on GPUs?

### Updating Models ###
* Models are stale the moment they are trained
* Prediction accuracy can improve up to 40% by leveraging real-time feedback
* Common approaches to fast adaptation
    * Frequent retraining, high-latency
    * Online learning, not general and difficult to debug

### Online re-ranking ###
* Issue: preferences change depending on session
* Adaptive ML in production
    1. Train and deploy your model
    2. Online reranker black box
    3. Consume
* Online reranker uses activity data
* Train using non-linear data (like from decisions made by a decision tree model)

## Distributed deep learning ##
* Distributed training throughput increases linearly as number of GPUs increases
* Distributed training convergence time decreases linearly as number of GPUs increases
* Utilizing the Turi RPC layer via Python, you can get a 40-60% improvement in TensorFlow performance
over the standard RPC layer

## How can you trust your model? ##
* Netflix is trying to make customers more comfortable with an AI solution by making it real
to them
* For Doctors, they can make better decisions from recommender systems and can use the logic
and data behind the recommender systems to gain patient trust

### Training a model to predict wolf v. husky ###
* Only one mistake -- do you trust the model?
* What if you're having a husky festival and one single wolf shows up and kills someone!?
* Upon further investigation, Carlos showed that the wolf predictor was actually a snow predictor

### Famous 20 Newsgroups dataset ###
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

### Game of Thrones Predictor ###
* Predicting whether characters will be alive or dead
* Carlos' model predicted that Ned Stark would be alive in Season 2
* Factors / features include
    * He's from the House of Stark
    * How many dead relatives does he have?

## Must-haves for ML in production ##
* Maximize resources, reuse features
* Never stop learning
* When scaling matters
* Explain yourself, explain your modles
* Get away from the "my curve is better than your curve"

## Ameliorating the Annotation Bottleneck ##
Data programming, asynchronous deep learning
* non-"Dark Data" - spreadsheets, relational databases, etc.
* "Dark Data" - Valuable and hard to process data from scientific articles, documents, etc.
* Dark data processing was used for fighting human trafficking, partnering with law enforcement
agencies
* Some routine cases should be much easier
    * Simple classifiers and regression
    * Entity and relationship extraction
* **Challenge** - Make systems dramatically easier to use
    * Willing to give up expressive power
    * Non-CS PhD with a weekend to kill (i.e. hackathon)

## Rise of Automatic Feature Libraries ##
* Writing good features is painful
    * Many used default automatic feture libraries .. not great
    * Or deep learning
* Automatic feature libraries need large training sets, and creating such sets is expnsive
* ImageNet took years to build
* **Goal** - build large training sets using only standard tools

Note: I had to fix something that broke on my website at this point, so I stopped taking notes.

# Emily Fox -- Amazon Professor of Machine Learning, University of Washington #
**Machine Learning for Complex Time Series**
* Hidden Markup Models (HMM)
* Challenges:
    * Sementation into behaviors
    * Parameter per behaviour
    * How many behaviors?
* Problem appears in many domains, including: Parsing EEG data, other medical diagnostic data, etc.
* Bayesian HMM's
* When you have time segments ~ 2 million, parsing the dataset every time you want to reatrain
your model becomes infeasible
* Solution: brak into manageable segments
    * Naive - analyze separately
    * Smart
    * Something else I didn't catch
* Runtime = 1 hr

## Discover structure across "space" ##
* Collection of time series where there are a sparse set of of dependencies
* Cluster regionas based on underlying price dynamics
    * Discover groups of tracts with correlated dynamics
    * In the housing example, look at locations that are closely related to the location you
    are trying to predict
    * Marrying trends / features that are globally applicable versus locally applicable
* Cluster and correlate multiple time series
    * Challenge: unknown cluster structure = unknown @ blocks and size of each
    * Solution: Latent factor model + Bayesian nonparametrics
* Methods for relating high-dimensional time series
    * Approach 1: Clusters of time series = marginal independence
    * Approach 2: Graphical models = conditional independence
        * Motivation for this came from Magnetoenchephalography (MEG) time-series data
        * Transform time-series from the time domain to the frequency domain
        * Example: daily returns from a set of global stock indicies (shows a node graph representing
        what countries are related?)
    * Approach 3: Low-dimensional embedding of dynamics
        * MEG word classification task
        * Helmet with 102 sensors
        * More accurate than any other current method

# Jennifer Rose -- Professor @ Wesleyan #
**Increasing diversity in data science**
## Why do we need diversity in data science? ##
* When it comes time to tell the story of your data analysis, your background introduces
 bias, and if you have too many similar individuals in the same place, that bias can carry
 more weight than it would be in a more diverse working group
* Diversity:
   * Impacts the questions we ask in the first place
   * Ramps up creativity

## Method for increasing diversity ##
* Strategies for increasing diversity
    * Branch out to other disciplines
    * Evoke curiosity and passion through multidisciplinary project-based learning
* Project-based learning
    * Base the learning approach on a real-world problem
    * Superior to traditional appraoches in promoting deep thinking, knowledge retention, etc.
* At Wesleyan, they used a multidisciplinary approach where the students pick a topic that
interests them, pick a dataset, and deelop a research question that the seek to answer
* Weeks 1 and 2
    * Generate testable research question
    * Conduct a literature review
* Weeks 3 and 4
    * Stats software basics (SAS, R, Stata, SPSS)
    * Data management
    * Descriptive stats and graphing
* Week 5 though Week 10
    * Conduct bivariable and multivariable analyses
* Week 11 through Week 14
    * Interpreting results and drawing conclusions
    * Reconciling study limitations
    * Presenting findings
* **Just in time learning**
* <a href="http://passiondrivenstatistics.com" target="_blank">passiondrivenstatistics.com</a>
* This method of teaching resulted in enrolling significantly more under-prepresented students
than the traditional math statistics course
* Coursera's data analysis and interpretation track

# Interesting Tools and Research #
* Apache Arrow
* Myria
* Non-python stats tools (SAS, SPSS, R <--- **nope**)
* MusicDB - longitudinal analysis of music
* SeaFlow (might be interesting for Mark)
* Ashes CAMHD (ocean floor HD cameras that pass photos to data scientists for analytics)
    * Separating foreground and background using matrix factorization
