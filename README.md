# Machine-Learning-Bias
Identify bias in Machine Learning algorithm and reduce the same using different techniques. 
 
<b>Background:</b><br> 
Globally, organizations are adopting various machine learning algorithms to take day to day business decisions like whom to give credit card? Who will default next? Who will buy their products, What should we sell to a particular type of customer etc. These algorithms are very handy to take business decisions but at the same time one must ask- Are these algorithm transparent or do they create biases towards certain group of people? This is exactly I am going to explore in this analysis.
<br><br>
<b>Objective of the analysis: 
<br>To evaluate <br>
1. To evaluate whether a machine learning algorithm is biased towards certain group of people?
2. What type of biases our model is creating?
3. How to reduce these biases from our model?
 </b>
<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Problem%20statement.PNG">
 <br>Figure: Problem Statement
 </p>
 <b><br>
About available data:</b><br>
For our analysis, we are going to use the criminal dataset from Propublica https://github.com/propublica/compas-analysis/.For more information about how data is acquired and treated please refer to their website- https://www.propublica.org/article/how-we-analyzed-the-compas-recidivism-algorithm
<br>Data Collection Period: January 1, 2013 to September 9, 2014

<b>Exploratory Analysis on important variables</b><br>
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
In order to evaluate machine learning bias, we will 
<ol><li>First, create an algorithm to predict crime re-offenders.
  <li> Identify discrimination (biases) in our data and model.
    <li> Remove these discrimination (biases) from our model.
      </ol>
  
 <b> How biases are treated? </b><br>
 We have used Themis-ML (https://github.com/cosmicBboy/themis-ml) package to identify and remove biases. The following are the models and their descriptions:
 <ol><li> Baseline (BB): Train a model on all input variables, including protected attributes.
 <li> Remove Protected Attribute (RPA): Train a model on input variables without protected attributes. This is the naive fairness-aware approach.
  <li> Reject-Option Classiﬁcation (ROC): Train a model using the Reject-option Classiﬁcation method.
   <li> Additive Counterfactually Fair Model (ACF): Train a model using the Additive Counterfactually Fair method.
</ol>
Models RPA, ROC and ACF are different ways in Themis-ml packge to treat biases in our model.
<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Classifier%20outputs.PNG">
 <br>Figure: Classifier Outputs (Tabular).
 </p>

<br><b>Conclusion:</b><br>
The mean difference score between male and female groups is 0.17 i.e. male are 17% more likely to re-offend as compared to female. Also, the mean difference between African-American and Caucasians is 0.22 i.e. African-Americans are 22% more likely to re-offend as compared to Caucasians.
 <b>Thus, we conclude that - <u>Through data, biases (discriminations) against men and African-Americans are injected to our model.</u></b><br>
 Now, how should we treat these biases. For this, we ran RPA, ROC and ACF models as decribed in the above section. Following are the mean differences and auc scores of these models.
<p align="center"><img src="https://github.com/kpratikin/Machine-Learning-Bias/blob/master/Output.PNG">
 <br>Figure: Fainess and utility tradeoff
 </p>

From the above graph, we can observe that there is a trade-off between the fairness (mean-difference) and the utility (accuracy) scores.
For classifiers B and RPA, the accuracy is high and the mean-difference is also high. It tells us that though prediction power of our model is high, it is biased towards one group of people.
And for ROC and ACF classifiers, as the mean difference is decreasing, it is dragging the accuracy along with it (trade-off). This indicates that as we treat biases, auc scores will decrease (i.e. prediction power will decrease).

<b>Ideally, we would prefer that the mean difference should be low (which tell us about fairness) and the accuracy (i.e. utility) to be high (i.e. our model is fair and able to correctly predict the outcomes).</b> 

So, if we directly interpet the the Baseline clasifier, we are unkowingly creating bias towards certain group of people (in our case men and African-Americans). As shown above, if we ran ACF classifier, we are able to reduce the mean difference significantly while keeping auc score at high level. Thus, reducing biases from our model and at the same time keeping the prediction power of our model high. 

Thus, the above analysis shows that if there is historical bias in your data,  your model will tend to generate those biases. As a decision maker, one should always check whether your algorithm is creating such discriminations against certain group of people. If yes, one should take necessary steps to reduce such biases from the model. One such approach is shown above.

<br><b>References:</b>
<ol><li>Santa Clara University: MSIS 2631- Machine Learning with R & Python Course – Dr. Sanjeev Das.
<li>Propublica : https://www.propublica.org/datastore/dataset/compas-recidivism-risk-score-data-and-analysis
<li> Propublica Github site: https://github.com/propublica/compas-analysis/
