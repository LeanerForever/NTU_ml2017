### Where dose the error come from?

error comes from 2 sources : `bias` and `variance` 

### Bias and Variance of Estimator

sample N points:{$x_1,x_2,...,x_N$} , which come from such  a distribution: $E(x)=\mu,Var(x)=\sigma^2$

* the estimator of mean $\mu$

  $\hat\mu=\frac{1}{N} \sum_{i} x_{i}$ 

  then $E(\hat\mu) = \,u$,  $Var(\hat\mu) = \frac{\sigma^2}{N}$

* the estimator of variance $\sigma^2$ 

  $\hat\sigma^2 = \frac{1}{N} \sum_{i}\left(x_{i}-\hat\mu\right)^{2}$

  then $E(\hat\sigma^2) =\frac{N-1}{N} \sigma^{2} $( means such estimator is biased )

**The same happens for estimation of  function** 



![bias_variance](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\bias_variance.PNG)



Assume that $f^*$is the true function, and $\hat f $ is the estimated function. 

It's easy to image that an underfitted $\hat f$ has large bias and low variance. An overfitted  $\hat f $ is vice versa. It is illustrated in the following picture.



![bias_variance2](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\bias_variance2.PNG)

`sample model is less influenced by the sampled data`

![bias_variance3](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\bias_variance3.PNG)

The following picture is a good summary to answer the question:`where does error come from?`

![bias vs variance](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\bias vs variance.PNG)

___



### What to do with bias and variance?

* Diagnosis:

  * both large training errors and large testing errors

     $\longrightarrow$ large bias

  * small training errors but large testing errors

     $\longrightarrow$ large variance

* countermeasure:

  * large bias

     $\longrightarrow$ add more features, 

     $\longrightarrow$ more complex model

  * large variance

     $\longrightarrow$ collect or generate more data

     $\longrightarrow$ regularization ( `may increase the bias`)

___



### The insights that bias and variance give us when we choose to models

To prevent our model overfit to the testing set, we need split data into 3 parts: training set, validation set, and testing set. The common techniques people used to train their model is `cross validation` and `N-fold cross validation `.

![cross_validation](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\cross_validation.PNG)

![N fold CV](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\N fold CV.PNG)

____

### Classification: **Probabilistic Generative Model**

#### application:

* credit scoring
* medical diagnosis
* face recognition
* handwritten character recognition

#### How to do classification:

* classification as regression: hard to control and sophisticated to solve multi-classification problem.

* perceptron, SVM

* `probabilistic model`

  * Bayesian probability: 

  ![Bayesian probability](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\Bayesian probability.PNG)

  * Assumption: data are sampled from  Gaussian 	distribution
    $$
    f_{\mu, \Sigma}(x)=\frac{1}{(2 \pi)^{D / 2}} \frac{1}{|\Sigma|^{1 / 2}} \exp \left\{-\frac{1}{2}(x-\mu)^{T} \Sigma^{-1}(x-\mu)\right\}
    $$
    

    We need to estimate mean and covariance matrix through samples, but how?

    Answer is maximum likelihood estimation.

    Illustration is followed:

    ![MLE](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\MLE.PNG)
    $$
    \mu^{*}, \Sigma^{*}=\arg \max _{\mu, \Sigma} L(\mu, \Sigma)
    $$

  * The answer to the MLE  (remember it):
    $$
    \mu^{*}=\frac{1}{79} \sum_{n=1}^{79} x^{n} \quad \Sigma^{*}=\frac{1}{79} \sum_{n=1}^{79}\left(x^{n}-\mu^{*}\right)\left(x^{n}-\mu^{*}\right)^{T}
    $$
    

  * Once we have finished estimation of  $P\left(x | C_{1}\right)$ and $P\left(x | C_{2}\right)$, then we can do the computation based on Bayesian probability.

    ![Bayesian example](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\Bayesian example.PNG)

  * Usually if we using to many parameters to do the classification, we will overfit and have bad result on testing set. One solution to this problem is using linear estimation, which means we can assume that two categorical share same covariance matrix. The result is significantly improved.

    ![modified model](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\modified model.PNG)

  * The relationship between probabilistic generated model  and sigmoid function:

    Little complicate, I need refer to slides for details. General, sigmoid function is not  totally equal to probabilistic generated model.  **They are the same learning model, but with different assumption. Therefore they will obtain different result though they training the same model with the same data.** 

___

### Logistic regression

* What is logistic function?

![logistic](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\logistic.PNG)

* Assumption:

  ![LG_assumption](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\LG_assumption.PNG)

* Loss function:

  ![loss](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\loss.PNG)

* The comparison between Logistic regression and Linear regression:

  *  output range 
  * loss function

  ![comparsion](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\comparsion.PNG)

* Why don't we use square error instead of  cross entropy?

![1](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\1.PNG)

### Generative Vs Discriminative

* same model, different approach to optimize

  ![generativeVSdiscriminative](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\generativeVSdiscriminative.PNG)

* Difference:

  * Generative approach has an assumption about the data, it's decision is less influenced by data. (The assumption and data make decision together). While discriminative approach makes no assumption about the data distribution thus makes decision only by data.

    To conclude,  if the data set is small , noisy and biased, generative approach usually performs better. While when data set increases, the error in discriminative approach will decrease and perform better than generative approach .

![2](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\2.PNG)

#### multi-class classification

* softmax

#### Limitation of Logistic Regression

* single logistic regression&#39;s performance is limited,  example like XOR task.  We need make some transformation to the original data. To make such transformation automatically, we can cascade many layers of logistic regression. Such model is called deep network.  Cool~~~