Download Link: https://assignmentchef.com/product/solved-cmput466-coding-1
<br>
<strong>Problem 1</strong>

Download: <a href="https://drive.google.com/open?id=1ZrLiXmk62pVDHyvmUEBztxgqJ3_0J-2m">Codebase</a>

In this coding problem, we will implement the closed-form solution to linear regression. The student will use matrix-vector representations for data representation and get some experience with data visualization. In addition, the student will explore the phenomenon of “regression to the mean.”

We generate data with two steps:

<ol>

 <li>Independently generate</li>

 <li>Rotate to a degree (e.g.,</li>

</ol>

The data generation is given by the generate_data(M, var1, var2, degree) function.

After data generation, we will obtain these two plots of data. In the second plot, the dashed line is where data are mostly generated around.

Now, we would like to do two linear regressions: 1. Predict y from x (denoted by x2y), and

<ol start="2">

 <li>Predict x from y (denoted by y2x).</li>

</ol>

<strong>To accomplish this, the student needs to implement the </strong>leastSquares(X, Y) <strong>function.</strong>

Note: In the function leastSquares(X, Y), X is simply the input and Y is simply the output. It is not related to x2y regression or y2x regression.

Then, we would like to use the learned models x2y and y2x to predict a series of points in (-4, 4) as input, and plot the input and the predicted output.

<strong>To accomplish this, the student needs to</strong>

<ol>

 <li>Implement feature augmentation, i.e., each data sample is concatenated with a dummy feature 1. Notice the augmented feature during prediction has to comply with that in training.</li>

 <li>Implement the prediction function model(X, w), where the definition of w should comply with that in the leastSquares</li>

 <li>Plot the learned models. Notice that a linear regression from is just a line. The student is required to plot x2y regression in red and y2x regression in green. And, these two models MUST be plotted in the same x-y coordinate system, with x being the horizontal axis and y being the vertical axis.</li>

</ol>

<strong>Submission:</strong>

In the PDF report (the only accepted format), the student should report:

<ul>

 <li>[20% for correct implementation of linear regression] With settings M = 5000, var1 = 1, var2 = 0.3, degree = 45, report the weight and bias for x2y and y2x regressions. The submission should be four numbers in two rows:</li>

</ul>

w_x2y    b_x2y w_y2x    b_y2x

Note: getting the above numbers correctly is a necessary (not sufficient) condition for correct implementation.

<ul>

 <li>[10%] Three plots of regression models in a row, each with var2 = 0.1, 0.3, 0.8, respectively. (Other settings remain intact: M = 5000, var1 = 1, degree = 45).</li>

 <li>[5%] A description of the phenomena found in 1) and 2).</li>

 <li>[15%] We now set var2 = 0.1, but experiment with different rotation degrees. The student should design a controlled experimental protocol, plot three figures in a row with different settings, and describe the findings.</li>

</ul>

Note: For 1) and 2), only give the result. Do NOT explain anything, because the setting is clear in the problem description. For 3) and 4), do NOT try to write an over-lengthy description merely to get high marks. On the contrary, an unnecessarily long report indicates poor representation skills and may result in mark deduction.

<strong>Lessons learned:</strong>

This experiment tells us that, even for the same data , predicting  from  is

different from predicting  from . This verifies what we learned in the first lecture: Formulating a machine learning task as a supervised or an unsupervised task, or how can we formulate a supervised task really <strong>depends on the task itself</strong>, i.e., what the goal of your prediction is.

<strong>Problem 2 </strong>

Download: <a href="https://drive.google.com/open?id=1US3esCMmV_T55efdHqGG5VTYrh4r4MmH">2a</a>, <a href="https://drive.google.com/open?id=1wz-zEqmzur0OPPh8Fnlut0j2Wbuvw8eL">2b</a>, <a href="https://drive.google.com/open?id=1xeLTGoDCZ0ec4yj8E-PTgcrhUk_HTpq5">2c</a>

In this problem, we will explore gradient descent optimization for linear regression, applied to the <a href="https://scikit-learn.org/stable/datasets/index.html#boston-dataset">Boston house price</a> prediction. The dataset is loaded by <strong>import </strong>sklearn.datasets <strong>as </strong>datasets

where sklearn is a popular machine learning toolkit. Unfortunately, in the coding assignment, we <strong>CANNOT </strong>use any other API functions in existing machine learning toolkits including sklearn. Again, we shall use linear algebra routines (e.g., numpy) for the assignment.

The dataset contains 506 samples, each with 13 features. We first randomly shuffle all samples, and then take 300 samples as the training set, 100 samples as the validation test, and 106 as the test set.

We normalize features and output by

We use mean square error as our <strong><em>loss </em></strong>to train our model. The measure of success, however, is the mean of the absolute difference between the predicted price and true price. Here, we call the measure of success the <strong><em>risk </em></strong>or <strong><em>error</em></strong>. This reflects how much money we would lose for a bad prediction. The lower, the better.

In other words, the training loss is

where we compute loss on the normalized output  and the prediction .

The measure of success (the lower, the better) is

Here, the risk is defined on the original output (thinking of it’s the real money).

Notice that we will use mini-batch gradient descent, and thus,  should be the number of samples in a batch.

<ul>

 <li>[30%] We implement the train-validation-test framework, where we train the model by mini-batch gradient descent, and validate model performance after each epoch. After reaching the maximum number of iterations, we pick the epoch that yields the best validation performance (the lowest risk), and test the model on the test set.</li>

</ul>

<strong>Without changing default hyperparameters</strong>, we report three numbers

<ol>

 <li>The number of epoch that yields the best validation performance, 2. The validation performance (risk) in that epoch, and</li>

 <li>The test performance (risk) in that epoch. and two plots:

  <ol>

   <li>The learning curve of the training loss, and</li>

   <li>The learning curve of the validation risk.</li>

  </ol></li>

</ol>

where x-axis is the number of epochs, and y-axis is training loss and validation risk, respectively.

<ul>

 <li>[10%] We now explore non-linear features in the linear regression model. In particular, we adopt point-wise quadratic features. Suppose the original features are</li>

</ul>

. We now extend it as .

At the same time, we tune -penalty to prevent overfitting by

The hyperparameter  should be tuned from the set {3, 1, 0.3, 0.1, 0.03, 0.01}.

Report the best hyperparameter , i.e., the one yields the best performance, and under this hyperparameter, the three numbers and two plots required in Problem 2(a). (c) [10%] Ask a meaningful scientific question on this task by yourself, design an experimental protocol, report experimental results, and draw a conclusion.