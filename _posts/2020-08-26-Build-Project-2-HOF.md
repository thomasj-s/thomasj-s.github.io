---
layout: post
title: MLB Hall of Fame Predictions
subtitle: Can stats alone predict if a player will be inducted on their first ballot?
gh-repo: thomasj-s.github/io
---

## Imagine :

  That you wanted to create a machine learning model to predict if a player would be inducted to the Hall of Fame on their first ballot...
 
  What percentage of players make it on their first ballot?  Which stats would you consider?  How does the Hall of Fame work?  All of these are valid questions.  First we're going to need a goal, and some data.
  
  We will be using the Lahmans MLB database; More specifically, the Hall of Fame, Batting, and Pitching datasets to build a table of every Hall of Fame first time entry.  For each entry include select stats, and whether or not the player was inducted on that ballot entry.  We are going to build from a gambling application view where our goal is to be sure that a 'yes' is definitely a 'yes'. 
  
## Data Cleaning

  After boiling down our Hall of Fame dataset to only first time ballots, we want to begin populating it with offensive statistics from the batting dataset.  Certain statistics aren't already present such as batting average, slugging percentage, and career hits, but all the information is there to write functions and engineer these.  We hit our first roadbump here: Pitchers are on this list and we realize that we would have to build a separate model for pitchers, as their offensive stats would not be beneficial to the model in the same way that a position players pitching stats would not be beneficial to the model.  We decide to narrow this down to position players, and use our pitching dataset to filter out pitchers.  We run into a similar problem with managers, so we drop a few more.
  
  Our data is now more or less ready to use.  We have a dataset with all of our position players first entry, and the corresponding stats from the batting dataset and our own engineering. We have 771 entries, and a distribution in our target of 95% not inducted, and 5% inducted. 
  
## Modeling
  
  Since our problem is a binary classification problem that might include some non-monotonic relationships, we will be using iterations of a random forest model.  Our first model will be an 'out of the box' model, and our second model will include SMOTE'd data and hyperameter tunings.  We want to compare these two models and see which will hace a higher precision in predicting our minority class.
  
  Below is a confusion matrix for our first models predicions on our validation set.  
  ![plot 1](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_2_vis_1.jpg?raw=true)
  
  
  From this we can derive a validation precision of 85.7%, recall of 75% and an F-1 score of 80%. Considering that these are out of the box methods, these would be pretty good numbers; Though it still does not beat the 95% precision that our minority class baseline sets.
  
## Tuning

  Now that we have a goal to beat, lets tune our model.
  
  Our first step is to use SMOTE to sythesize more samples of our minority class to train our model on.  This should theoretically help the model dicsern between classes easier.  Our next step is to tune our random forest hyperamaters using GridsearchCV.  Done.
  
~~~
oversample = SMOTE(sampling_strategy=.5, k_neighbors=2, random_state=42)
xtrain_res, ytrain_res = oversample.fit_resample(xtrain_transformed, ytrain)
~~~

  We can take a look at the distribution plot below to get an idea of what SMOTE is doing to our data.
  
  ![plot 2](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_2_vis_3%20(1).jpg?raw=true)

  At this point, you may be sharing some of the thoughts I had at this point in the process : "All right!  With some more samples and tuned parameters we're definitely going to see an increase in our metrics!"  
  
  Not exactly.  Our metrics for the validation test on our second model were as follows: Precision of 75%, recall of 75%, and F-1 of 75%.  Our second model actually performs worse than our out of the box model.  We turn to some comparison plots to see exactly what is going on.  
  
  
