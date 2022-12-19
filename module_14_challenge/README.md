# Module 14 Challenge - Algorithmic Trading

* *The Jupyter Notebook file containing all code may be found in the folder titled ```Code``` under the filename ```machine_learning_trading_bot``` The report is as follows below.*

* *Also please note that the images do not appear to be showing on github. Opening the file in VS Code does however show all images. I have been unable to find the cause of this issue*

![](images/bot.jpg)

## Report

### Tune the Baseline Trading Algorithm

#### Step 1
*Slice data into different periods, rerun the notebook with the updated parameters and record the results*

**Parameters that were updated**

* *18 Months*

Updating the ending period for the training data with an offset of 18 months instead of 3 months did not provide any benefit as no short sell signals were generated. Instead, only long buy signals were computed by the algorithm.

* *1 Month*

The offset period was then instead changed to be 1 month. This method generated a sporadic result which, while not appearing as neat as the initial result from the 3 month window, did generate slightly greater returns.

**1 Month**
![](images/1%20month.PNG)

The 3 month strategy has an 'actual returns' range between just over 0.96% up to about 1.05%, whilst the new strategy utilising the 1 month window displayed an 'actual returns' range of 1% to just under 1.06%.

* *2 & 6 Month*

A 6 month window was then also tried, however the results were much lower and disregarded. Likewise, a 2 month window was also tested to similarly produce less impressive results as compared with the 1 month window's actual returns.

**Question: What impact resulted from increasing or decreasing the training window?**

Increasing the training window had the effect of generating a strategy which provided lower returns. Conversely, decreasing the training window had the opposite effect, and it was found that of the time window's that were tested (1 month, 2 month, 3 month, 6 month and 18 month) the most impressive actual returns were achieved by the shortest window of 1 month.

#### Step 2
*Adjust one or both of the SMA input features, rerun the notebook with these updates and record the results*

*Note: the training window was returned to 3 month in order to preserve this experiement's accuracy*

**Original Conditions:**

Short Window = 4

Long Window = 100

**Test 1:**

Short Window = 2

Long Window = 100

**Test 2:**

Short Window = 4

Long Window = 250

**Test 3:**

Short Window = 5

Long Window = 150

**Test 4:**

Short Window = 1

Long Window = 50

**Original Conditions Returns:**
![](images/3%20month.PNG)

**Results**
* Test 1

*Produced no visible improvement to both strategy and actual returns:*
![](images/Test%201.PNG)

* Test 2

*Both strategy and actual returns appear to have decreased, and thus this investment strategy would not be recommended:*
![](images/Test%202.PNG)

* Test 3

*This strategy also appears to not be as impressive as the strategy employing the initial conditions. Returns also appear to be decreasing over time:*
![](images/Test%203.PNG)

* Test 4

*A very impressive result, with actual returns closely matching strategy returns, and returns also increasing over time. This configurations of window sizes would certainly be the one to employ as it is much improved over the original conditions:*
![](images/Test%204.PNG)

**Question: What impact resulted from increasing or decreasing either or both of the SMA windows?**

Mediocre changes in the relative window sizes for both short and long windows with respect to the original window sizes of 4 and 100, respectively, were found to not produce worthwhile results in terms of generating greater cumulative returns. Increasing the long window size to 250 in test 2 also did not produce an attractive result. It was instead found that drastically reducing the short and long window sizes to 1 and 50, respectively, generated better returns, and thus it would appear that for this set of data, using smaller window sizes would increase the machine learning algorithm's capability to better predict favourable investment outcomes.

#### Step 3
*Save a PNG image of the cumulative product of the actual vs. strategy returns and document the conclusion*

**Experiement:**

Combining a 1 month offset with the favourable intial window sizes of 1 for short and 50 for long was also tested, however the result was not as profitable as with the new window size conditions coupled with the previous, 3 month window.

**Conclusion:**

The ideal set of parameters that produced the most improved trading algorithm returns were as follows:

Date Offset = 3 months

Short Window = 1

Long Window = 50

*The result appears to be an improvement on the original test conditions and would be the recommended choice for this dataset:*
![](images/Test%204.PNG)

### Evaluate a New Machine Learning Classifier

*Chosen Classifier - LogisticRegression*

**Question: Did this new model perform better or worse than the provided baseline model? Did this new model perform better or worse than your tuned trading algorithm?**

**Cumulative Product of Actual vs. Strategy Returns using LogisticRegression**
![](images/LogisticRegression.PNG)

Implementing the LogisticRegression machine learning module did not infact produde results that were better than what was previously achieved. The tuned trading algorithm performed considerably better and would be the correct choice for real world implementation.

### Evaluation Report

To summarise, a trading algorithm was established and baseline results were generated from whence improvements may be innovated, with initial conditions being the time offset of 3 months for the training data, and SMA short and long windows of 4 and 100, respectively.

*Cumulative product graph displaying strategy vs. actual returns using the baseline conditions:*
![](images/3%20month.PNG)

Various alterations to these initial conditions were then tested, with the standout, most improved results being generated from a 3 month time offset coupled with a short SMA window of 1 and a long SMA window of 50.

While the 1 month time offset was found to generate greater returns whilst using the initial SMA window periods, combining this offset condition with the updated window sizes did not produce better results than the aforementioned ideal combination incorporating the 3 month time offset.

A logistic regression model was then also tested using LogisticRegression from SK Learn and compared against the tuned algorithm, and it was found that this too did not produce results as profitable and favourable as the finely tuned algorithm.

*The cumulative product graph displaying strategy vs. actual returns using LogisticRegression:*
![](images/LogisticRegression.PNG)

*The cumulative product graph displaying strategy vs. actual returns for the ideal combination of initial conditions:*
![](images/Test%204.PNG)

---

Navpreet Nat | 19th December 2022