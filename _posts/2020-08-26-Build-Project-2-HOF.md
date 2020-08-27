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
  
