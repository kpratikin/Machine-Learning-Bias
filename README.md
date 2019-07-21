# Machine-Learning-Bias
Identify bias in ML algorithm and reduce the same using different techniques. 
 
<b>Background:</b><br> 
Globally, organizations are adopting various machine learning algorithms to take day to day business decisions like whom to give credit card? Who will default next? Who will buy their products, What should we sell to a particular type of customer etc. These algorithms are very handy to take business decisions but one should ask- Are these algorithm transparent or do they create bias towards certain group of people? This is exactly we are going to explore in this analysis.

<br><br>
<b>Objective of the analysis: 
<br>To evaluate <br>
1. To evaluate whether a machine learning algorithm is biased against certain group of people?  
 </b>
 
 <b><br>
About available data:</b><br>
For our analysis, we are going to use the criminal dataset from propublica github page https://github.com/propublica/compas-analysis/
<br> For more information about how data is acquired and treated please refer to their website- https://www.propublica.org/article/how-we-analyzed-the-compas-recidivism-algorithm
<br>Data Collection Period: January 1, 2013 to September 9, 2014

<p align="center"><img src="https://github.com/kpratikin/BOPS_Project/blob/master/Data%20availiability%20and%20timeline.PNG">
 <br>Figure: Data Timeline
 </p>
 
<b>Methodology for evaluating the bias</b><br>

In order to evaluate machine learning bias, we will 
<ol><li>First, create an algorithm to prdict crime re-offenders.
  <li> Identify discrimination (biases) in our data and model.
    <li> Remove these descrimination (bias) from our model.
      </ol>
<p align="center"><img src="https://github.com/kpratikin/BOPS_Project/blob/master/timeline%20and%20treatment.PNG">
 <br>Figure: Timeperiod
 </p>

<p align="center"><img src="https://github.com/kpratikin/BOPS_Project/blob/master/impact%20of%20bops.PNG">
 <br>Figure: Difference in Difference approach to capture 'Impact of BOPS on sales'
 </p>


<br><b>Analysis:</b>
Refer code - https://github.com/kpratikin/BOPS_Project/blob/master/BOPS.rmd

<br><b>Conclusion & Suggestions:</b><br>
Our analysis of the impact of BOPS strategy on online sales and returns shows that online sales and returns do not increase with the implementation of this strategy. It rather decreases. 

<p align="center"><img src="https://github.com/kpratikin/BOPS_Project/blob/master/Conclusion.PNG">
 </p>


One of the anticipated reason behind this decrease is ‘Channel-Shift’ effect i.e. after checking the product online, customers are visiting nearby stores to buy that product, instead of buying it online. This corroborates with the consumer behavior phenomenon i.e. research online, purchase offline. Because of this effect, we may be observing decrease in online sales/returns but if we include offline sales/returns data in our analysis, we may observe that there is net increase in sales/returns. Therefore, we recommend to include offline store data for the analysis to come up with the net impact of the BOPS on overall sales and return instead of focusing on one channel.

<br><b>References:</b>
<ol><li>Santa Clara University: MSIS 2631- Machine Learning with R & Python Course – Dr. Sanjeev Das.
<li>Propublica : https://www.propublica.org/datastore/dataset/compas-recidivism-risk-score-data-and-analysis
<li> Propublica Github site: https://github.com/propublica/compas-analysis/
