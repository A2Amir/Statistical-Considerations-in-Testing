# Statistical Considerations in Testing

 You might think that the importance of statistics in experiment design lies only in analyzing the results of an experiment but in reality there's actually more importance for statistics in your experimental design rather than just coming in at the end.  

As known Factors like how much data  we will need before we can judge our experiment's success on solid grounds and the size of the effect that you want to see can have a major effect on how much data you need to collect and how long it will take before you get your results In this Repos  

* you'll learn about how statistical techniques can help you answer questions related to setting up an experiment. 

* you'll learn about some tricky pitfalls that can come as a part of enlightened outcomes of an experiment. 


## 1. [Statistical Significance](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/v/idea-behind-hypothesis-testing)

 In most experiments, If the probability of something  that happened by chance is less than 5% or less than 1% then the probability would definitely significant. please check out [this notebook](https://github.com/A2Amir/Statistical-Considerations-in-Testing/blob/master/code/Statistical_Significance.ipynb) to get more onformation. 


## 2. Practical Significance

Even if an experiment result shows a statistically significant difference in an evaluation metric between control and experimental groups, that does not necessarily mean that the experiment was a success. If there are any costs associated with deploying a change, those costs might outweigh the benefits expected based on the experiment results. **Practical significance refers to the level of effect that you need to observe in order for the experiment to be called a true success and implemented in truth**. Not all experiments imply a practical significance boundary, but it's an important factor in the interpretation of outcomes where it is relevant.

**If you consider the confidence interval for an evaluation metric statistic against the null baseline and practical significance bound, there are a few cases that can come about:**

(Below, m0 indicates the null statistic value, dmin the practical significance bound, and the blue line the confidence interval for the observed statistic. We assume that we're looking for a positive change, ignoring the negative equivalent for dmin.)

* **Confidence interval is fully in practical significance region:**
 
  If the confidence interval for the statistic does not include the null or the practical significance level, then the experimental manipulation can be concluded to have a statistically and practically significant effect. It is clearest in this case that the manipulation should be implemented as a success.
 
    <p align="center">
   <img src="imgs/1.PNG" height="100" weight="250"/>
   <p align="center">
    
    
* **Confidence interval completely excludes any part of practical significance region:**
 
  If the confidence interval does not include any values that would be considered practically significant, this is a clear case for us to not implement the experimental change. This includes the case where the metric is statistically significant, but whose interval does not extend past the practical significance bounds. With such a low chance of practical significance being achieved on the metric, we should be wary of implementing the change.
 
    <p align="center">
   <img src="imgs/2.PNG" height="100" weight="250"/>
   <p align="center">
    
* **Confidence interval includes points both inside and outside practical significance bounds:**
 
  This leaves the trickiest cases to consider, where the confidence interval straddles the practical significance bound. In each of these cases, there is an uncertain possibility of practical significance being achieved. In an ideal world, you would be able to collect more data to reduce our uncertainty, reducing the scenario to one of the previous cases. Outside of this, you'll need to consider the risks carefully in order to make a recommendation on whether or not to follow through with a tested change. Your analysis might also reveal subsets of the population or aspects of the manipulation that do work, in order to refine further studies or experiments.
 
    <p align="center">
   <img src="imgs/3.PNG" height="100" weight="250"/>
   <p align="center">

## 3. [Experiment Size](https://www.youtube.com/watch?v=QBONLUp7i28)

We can use the knowledge of our desired practical significance boundary to plan out our experiment by knowing how many observations we need in order to detect our desired effect to our desired level of reliability, we can see how long we would need to run our experiment and whether or not it is feasible. please check out [this notebook](https://github.com/A2Amir/Statistical-Considerations-in-Testing/blob/master/code/Experiment_Size.ipynb) to get more onformation. 


## 3. Using Dummy Tests

When it comes to designing an experiment, it might be useful to run a **dummy test** as a predecessor to or as part of that process. **In a dummy test, you will implement the same steps that you would in an actual experiment to assign the experimental units into groups. However, the experimental manipulation won't actually be implemented, and the groups will be treated equivalently**.

There are multiple reasons to run a dummy test:
* First, a dummy test can expose if there are any errors in the randomization or assignment procedures. A short dummy test can be worth the investment if an invariant metric is found to have a statistically significant difference, or if some other systematic bias is identified, because it can help avoid larger problems down the line. 
    <p align="center">
   <img src="imgs/5.PNG" height="300" weight="500"/>
   <p align="center">
* A second reason to run a dummy test is to collect data on metrics' behaviors. If historic data is not enough to predict the outcome of recorded metrics or allow for experiment duration to be computed, then a dummy test can be useful for getting baselines.

Of course, performing a dummy test requires an investment of resources, the most important of which is time. If time is of the essence, then you may need to just go ahead with the experiment, keeping an eye on invariant metrics for any trouble. An alternative approach is to perform a hybrid test. In the A/B testing paradigm, this can take the form of an A/A/B test. That is, we split the data into three groups: two control and one experimental. A comparison between control groups can be used to learn about null-environment properties before making inferences on the effect of the experimental manipulation.
