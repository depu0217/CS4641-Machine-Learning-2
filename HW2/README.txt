For the whole project instruction, it mainly covers three operation parts with Abagail packetage.

(1) For the two datasets, we have to split them into two parts (70% for training and 30% for testing) respectively, and the training dataset need to be split by 10% increment;
(2) Optimization the better parameters for specific algorithm;
(3) Using the optimal parameters from previous step, we then train the algorithm with the training dataset with 10% increment and test it with the reamining dataset. 
Therefore we can acquire the error rate (or accurate rate) of the algorithm. 

Instruction details for those three parts.
(1)--Data split--
1.Open the dataset that you want to split. 
2.By using the filter function of Weka, we can randomize the dataset at first by using the "Ramdomize" function, after that we use the "RemovePercentage" function to remove 
specific percentage of data away from the source dataset. Save it and label a meaningful name for it like "10%_training_dataset". And then, undo the previous operation, and 
do the same procedure again for a different percentage. By doing that, we can generate the split dataset for the purpose of drawing the learning curve.
that we want.

(2)--Parameter optimization--
Here, we use Decision tree/J48 as an example.
1.By setting this parameter to various values, we can experiment the degree of pruning -- minimal to aggressive -- and its effect on classification accuracy.  
In J48, this confidence level can be set by the 'confidenceFactor' parameter, in the pop-up window which appears after clicking in the text box to the right 
of the "Choose" button.  It is set to 0.25 by default.  If you change it to a smaller value, you can do more aggressive pruning, while a larger value will 
let you do minimal pruning.
2.You run J48 with the confidence factor 0.50, 0.45, 0.40, ... down to 0.125 (i.e., a decrement by 0.05; So you'll do a total of 10 runs).  Also be sure to set
the 'minNumObj' to 2, and make sure the 'reducedErrorPruning' is False and 'unpruned' False, along with all other parameters as indicated in the previous figure.
3.For each run, do the evaluation by 10-fold cross-validation.  In the "Weka Explorer" window, under "Test Options", select "Cross-validation" and set the number 
of folds to 10 (which is the default in Weka)
4.After each run, record the confidence factor, the size of the tree and the classification accuracy.
5.Do the same procedure for all datasets.

(3)--Test dataset performance--
1.Open the specific training dataset you saved before.(For example, 10% dataset)
2.Choose the classifier you want and optimized it with the parameters from previous steps. After that set up "Supplied test set" as your remaining test set. 
Then select the "Cross_validation" and "Folds = 10". Then click on "Start".
3.When the training data has been trained, righ click the result and select "Re-evaluate model on current test set". Then you will get both the training and testing results.
4.Redo the steps stated above till you get all the different percentage done.


--Cross-validation strategies--

The aim in cross-validation is to ensure that every example from the original dataset has the same chance of appearing in the training and testing set.
The basic protocols are n-fold cross-validation: divide the data up into  chunks and train  times, treating a different chunk as the holdout set each time.
