---
layout: post
title: Is Game Score still a relevant MLB metric?
subtitle: A closer look at the relevance of an aging metric
gh-repo: thomasj-s.github/io
---

## What is Game Score?

  Game Score is an MLB pitching metric developed in the 1980's to measure a pitcher's perfomance in any single game. The usefulness of this metric is argued to be of lesser significance in baseball as we know it today.  This is primarily because the offensive approach to the game has changed in recent years from contact hitting and moving runners base-to-base to trying to hit home runs as much as possible.

  In recent years, data has shown that the impact a home run has on the outcome of a game was statistically worth the gamble of trying to hit them more often.  This change has resulted in higher scoring games, more fly-outs, lower overall batting averages, and higher stats (such as Earned Runs Allowed) for pitchers.

  I thought it would be interesting to look deeper into this stat, one regarded by many to have lost its value, and see if it holds up in a different era of play.
  
## Average impact of Game Score rating on regular season

  I thought a good place to look for signifigance would be a simple win correlation: any team's 2019 average Game Score among its starting pitchers, measured against the teams win percentage for the season.
  
  Each dot on the chart below represents the intersection of a team's 2019 Average Game Score rating and its corresponding win percentage.  A red dot indicates that a team made the playoffs and a grey dot indicates one that did not.

![plot 1](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_1_vis_1.jpg?raw=true)

  The most obvious takeaway might be a positive relationship between average Game Score rating and average win percentage.  Not shocking.  
  
  If we apply some clustering techniques to the same data, though we gain valuable insight:
  
  ![plot 2](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build_project_1_vis_2.jpg?raw=true)
  
  Our graph clearly indicates something unseen before:  no team with an average Game Score of 50 or less finished with above a 50% win rate or made the playoffs.  The only exception to this trend is the Oakland A's, whose average Game Score of 49.8 still made the playoffs.
  
  
## Game Score impact on playoff series.

  Since there may be a relationship beween average Game Score and playoff appearance, I decided to run a "ttest", which would look for a mathematical relationship between the two.
  
~~~
from scipy.stats import ttest_ind
ttest_ind(teams_final2['2019 pitcher ratings'], teams_final2['Playoffs'])
~~~
This test returns two numbers, the most telling being our 'pvalue', which confirms that there is indeed a correlation between average Game Score and making the playoffs.
~~~
Ttest_indResult(statistic=113.26504811455703, pvalue=9.211662137550928e-70)
~~~

  After spending a while with my boiled-down playoff data, an insight that I did not expect came to light: of the nine series played in the 2019 MLB post-season, 8 were won by the team with a higher Game Score rating.
  
  ![plot 3](https://github.com/thomasj-s/thomasj-s.github.io/blob/master/_posts/build-project-1-vis-3%20(10).jpg?raw=true)
  
## Conclusion 
  
  1.  There was a positive relationship between average Game Score and average win percentage for the 2019 season.
  
  2.  No team with an average Game Score rating of below 50 won more than 50% of their games or made the playoffs.....beside the Oakland A's who finished out the year with a 
      49.8 average Game Score yet managed to make the playoffs.
  
  3.  There was a statistical correlation between average Game Score and making the playoffs.  
  
  4.  8 of 9 playoff series were won by the team with the higher average Game Score.
  
  5.  Our two world series teams for 2019 were the teas with the two highest average Game Score ratings in the MLB.
  
  Is Game Score still a relevant metric? I say yes.  Granted we only looked at one season of play, I would say we found some arguments to be had for the relevance of an ancient MLB metric.
  
  
  
  [Here](https://colab.research.google.com/drive/1Y9GQezf47T5TooBPUK6qjhGvzUHaGpW7?usp=sharing) is a link to the notebook where all of the work was done to produce this post.
  





