# Machine-Learning-Bias
Identify bias in ML algorithm and reduce the same using different techniques. 
 
<b>Background:</b><br> 
Globally, organizations are adopting various machine learning algorithms to take day to day business decisions like whom to give credit card? Who will default next? Who will buy their products, What should we sell to a particular type of customer etc. These algorithms are very handy to take business decisions but one should ask- Are these algorithm transparent or do they create bias towards certain group of people? This is exactly we are going to explore in this analysis.

<br><br>
<b>Objective of the analysis: 
<br>To evaluate <br>
1. To evaluate whether a machine learning algorithm is biased towards certain group of people?  
 </b>
<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Problem%20statement.PNG">
 <br>Figure: Problem Statement
 </p>
In order to evaluate machine learning bias, we will 
<ol><li>First, create an algorithm to prdict crime re-offenders.
  <li> Identify discrimination (biases) in our data and model.
    <li> Remove these descrimination (bias) from our model.
      </ol>

 <b><br>
About available data:</b><br>
For our analysis, we are going to use the criminal dataset from propublica https://github.com/propublica/compas-analysis/.For more information about how data is acquired and treated please refer to their website- https://www.propublica.org/article/how-we-analyzed-the-compas-recidivism-algorithm
<br>Data Collection Period: January 1, 2013 to September 9, 2014

<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Re-offenders.PNG">
 <br>Figure: Distribution of one time offenders and re-offenders
 </p>
 
 <p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Race.PNG">
 <br>Figure: Distribution of data as per race.
 </p>
 
 <p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Sex.PNG">
 <br>Figure: Distribution of data as per gender.
 </p>

<b>Methodology for evaluating the bias</b><br>
We have used 'Mean difference score' between majority class and protected class to determine whether model is biased towards protected class or not.

<br><b>Analysis:</b>
Refer code - https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Project_Final.ipynb

<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Output.PNG">
 <br>Figure: Fainess and utility tradeoff
 </p>
 
 <p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Classifier%20outputs.PNG">
 <br>Figure: Classifier Outputs (Tabular)
 </p>


<br><b>Conclusion:</b><br>
For the bias to be treated, there is a trade-off to be made between the fairness and the utility.
Ideally, we would prefer for the mean difference to be low and the accuracy to be high. However, as we can see in the graph, although for B and RPA classifiers the accuracy is high, the mean-difference is also high.

And for ROC and ACF, as the mean difference is decreasing, it is dragging the accuracy along with it.

So, with this trade off, we think ACF is th best classifier to go ahead with as the mean difference is significantly lower than B and RPA, however, the accuracy does not seem to drop that much.
(This tradeoff depends on one's own trade-off conditions as it changes across datasets and also the problem statement we are dealing with)

<br><b>References:</b>
<ol><li>Santa Clara University: MSIS 2631- Machine Learning with R & Python Course – Dr. Sanjeev Das.
<li>Propublica : https://www.propublica.org/datastore/dataset/compas-recidivism-risk-score-data-and-analysis
<li> Propublica Github site: https://github.com/propublica/compas-analysis/
