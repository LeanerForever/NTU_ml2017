### Deep Learning

* the  ups and downs of deep learning

  ![history of deep learing](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\history of deep learing.PNG)

* Three steps for deep learning
  * step 1 : Construct a neural network
    * given a network structure, we define a function set.
    * we need to decide the network structure to let a good function in our function set 
    * approach: trial and errors + intuition or some advance approach like automatically ML
  * step 2 : design a goodness of function
    * find  the network parameters $\theta^*$ that minimize total loss $L$
  * step 3 : pick the best function 
    * gradient descent

* Why deep?![why deep](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\why deep.PNG)

### Backpropagation

____

excellent explanation by Lee !!

____

* first step:

  forward pass and store the caches

* second step

  backward by reverse and slightly change the forward neural network (really easy to understand)

* update the parameters

  ![backpropagation](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\backpropagation.PNG)

####    Hello word!

interesting pictures, I love it...

![keras](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\keras.PNG)



### Tips for training network

* Why appropriate batch size is  important to training?

  1.  minibatch takes both advantages of  matrix Operation and stochastic.
  2. batch size is usually set to 8,16,32 ....($2^n$), it related to the architecture of computer, but be care to not be too large to exceed the RAM of GPU.

* Do not always blame overfitting?

  1.   First, you need to verify that your network perform perfect on training sets but worse on testing/validation sets.
  2. some techniques for resolving overfitting:
     * regulariztion
     * dropout
     * early stopping

* Recipe of Deep learning:

  We need a scientific sequence to tune our network. During tuning process, we will encounter many problem. But some common problem has good approach to get over. Refer the following pics.

  ![recipe of deep learning](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\recipe of deep learning.PNG)

* Misconception: The deeper, the better?

  1. Deeper network will bring some overwhelming problems:  **gradient vanishing** & **gradient explosion**

  2.  Parameters closed to inputs update very small due to the smaller gradient while parameters closed to output converge faster but based on randomly early parameters.

     ![Gradient vanishing](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\Gradient vanishing.PNG)

     * How to understand such phenomenon ?

       My understanding: from the forward pass point of view, the next layer of neural will squeeze the input from last layer's out put when we using logistic activation. In another word, the deeper layer's outcome wouldn't change too much when we change the early layer's parameters, meaning we will get smaller derivatives to these parameters.

     * some techniques to mitigate this problem:
       1.  using ReLU activation
       2.  maxout

* Optimized gradient descent

  * Adagrad: using the first derivative to estimate second derivative
    $$
    w^{t+1} \leftarrow w^{t}-\frac{\eta}{\sqrt{\{\sum_{i=0}^{t}\left(g^{i}\right)^{2}}} g^{t}
    $$
    

  * RMSProp: revise the naive Adagrad

    ![RMSprop](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\RMSprop.PNG)

  * Momentum: from real physical world

    ![Momentum](C:\Users\ZhengTao\机器学习2017（李宏毅老师）\ML_pic\Momentum.PNG)

* L1 regularization & L2 regularization

  L1 regularization reduce or increase constant value each update, end of training, we will obtain a sparse result.

  L2 regularization will reduce the magnitude average.

