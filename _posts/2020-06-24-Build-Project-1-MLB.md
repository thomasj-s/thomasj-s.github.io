---
layout: post
title: Is 'Game Score' still a relevant MLB metric?
subtitle: A closer look at the relevance of an aging metric
gh-repo: thomasj-s.github/io
---

## What is Game Score?

  Game Score is an MLB pitching metric developed in the 1980's to measure a pitchers perfomance in any single game. The usefulness of this metric is argued to be of lesser signifigance in baseball as we know it today.  This is primarily because the offensive approach to the game has changed in recent years from contact hitting and moving runners base-to-base, to trying to hit home runs as much as possible.

  Data began to show in recent years that the impact of a home run on the outcome of a game was statistically worth the gamble of trying to hit them more often.  This has resulted in higher scoring games, more fly-outs, lower overall batting averages, and higher stats such as ERA (Earned runs allowed) for pitchers.

  I thought it would be interesting to take a look at a stat regarded by many to have lost its value, and see if it holds up in a different era of play.
  
## Average game-score rating impact on regular season

  I thought a good place to look for signifigance would be a simple win correlation. Any teams 2019 average Game Score among its starting pitchers, measured against the teams win percentage for the season.
  
  Each dot on the chart below represents the intersect of a teams 2019 Average Game Score rating, and the win percentage the team finished the season with.  A red dot indicates that the team made the playoffs, and a grey dot indicates did not make playoffs.

![plot 1](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_1_vis_1.jpg)

  My first takeaway is a definite positive relation between average Game Score rating, and average win percentage.  Not shocking.  
  
  My second takeaway, is that there is not an apparent relationship between average Game Score rating, and whether or not a team made the playoffs.  The playoff teams range from below average to very high in average Game Score rating, and there are many teams who did not make the playoffs that had high Game Score ratings.
  
  Since I was not convinced fully that there was not a correlation between Game Score rating and making the playoffs I decided to go one step further.  I ran a "ttest" which 

![plot 2](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_1_vis_2.jpg)

