# Predict-party-affiliation-Democrat-or-Republican
## **Task project:**
Predict party affiliation ('Democrat' or 'Republican') based on how they are voted by US House of Representatives Congressmen

## **Introduction:** 
I'll be working with a dataset obtained from the UCI Machine Learning Repository consisting of votes made by US House of Representatives Congressmen. My goal will be to predict their party affiliation ('Democrat' or 'Republican') based on how they voted on certain key issues. 

## **Structure dataset:** 
   1. Class Name: 2 (democrat, republican)
   2. handicapped-infants: 2 (y,n)
   3. water-project-cost-sharing: 2 (y,n)
   4. adoption-of-the-budget-resolution: 2 (y,n)
   5. physician-fee-freeze: 2 (y,n)
   6. el-salvador-aid: 2 (y,n)
   7. religious-groups-in-schools: 2 (y,n)
   8. anti-satellite-test-ban: 2 (y,n)
   9. aid-to-nicaraguan-contras: 2 (y,n)
  10. mx-missile: 2 (y,n)
  11. immigration: 2 (y,n)
  12. synfuels-corporation-cutback: 2 (y,n)
  13. education-spending: 2 (y,n)
  14. superfund-right-to-sue: 2 (y,n)
  15. crime: 2 (y,n)
  16. duty-free-exports: 2 (y,n)
  17. export-administration-act-south-africa: 2 (y,n)

(*) Missing Attribute Values: Denoted by "?" <br />
(**) y: voted for the key issue and 'n' mean the oposite.

## **Guidelines:** 
(I recommend you read my guideline along with Democrat or Republican.ipynb)
A. Preprocessing data
1. My data is lack of header -> import and create header for it. There are 16 subjects (key issues) for voting (as mention above)
2. Base on the result it look like only 392 data points out of 6960 is missing (around 5,6%) but if we use .dropnan function nearly half of total observation is removed cause this function delete entire rows which have missing values -> drop them all is unacceptable -> Ideally, inpute missing value using SimpleImputer
3. Before fill in missing ones, I converted all 'y' or 'n' into 1 or 0 cause The KNeighborsClassifier in sklearn is designed to work with numeric data only
4. Impute missing data (Note: there is some problems when I use SimpleImputer with pandas DataFrames -> I have to change it to Numpy arrays and drop header again) then after that I convert it back to pandas DataFrames (for vizualization)

B. Fit/train model 
1. As I said before, KNeighborsClassifier work with numeric data -> encode target 'party' using LabelEncoder() (1: republican, 0: democrat).
2. The accuracy for my model is 94,83% for training dataset and 97,7% for testing dataset, which is quite good.

C. Make a prediction
1. A random unlabeled data point has been generated for predicting and is available to you as X_new (unseen data)
- You can still use the .predict() method on the X that was used to fit the model (imagine like you do an exercise with the result has already presented to you), but it is not a good indicator.
- You will use your classifier to predict the label for this new data point, as well as on the training data X that the model has already seen
2. The predicted result need to be converted from numeric value (1 & 0) to 'republican' or 'democrat' by using for-in and if-else
