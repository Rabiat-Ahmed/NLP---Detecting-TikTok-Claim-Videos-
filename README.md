## Plan

The goal of this project is to develop a machine learning model for classifying claims made in videos submitted to the platform using the video transcription text as the independent variable.

TikTok users have the ability to submit reports that identify videos that contain user claims. These reports identify contents that needs to be reviewed by moderators. The process generates a large number of user reports that are challenging to consider in a timely manner. The solution to this, is to develop a predictive model that can determine whether a video contains a claim or offers an opinion. With a successful predictive model, the backlog of user reports can be reduced and prioritized more efficiently. A "claim" refers to information that is either unsourced or from an unverified source while, an "opinion" refers to an individual's or group's personal belief or thought.

The plan is to implement tree-based models(decision tree, random forest and XGBoost) and then pick a champion model using the F1 score as the deciding metric.

The dataset used for this project contains synthetic data and was gotten from the Google Advanced Data Analytics Certificate Program on Coursera.

## Clean and Preprocess

The first step of this stage was to select the independent and dependent variables. After removing the null values and duplicates, the rows reduced to 19,012 from 19,362.  The target variable was encoded. The target variable is an approximately 50%-50% split, which is perfectly balanced.  Punctuations and stopwords were removed from the text and then converted to lowercase.

## Word Cloud

Below is the word cloud for claims 

<img width="717" height="400" alt="IMG-20250131-WA0000" src="https://github.com/user-attachments/assets/33e788c1-6e1d-41e1-b96c-39dabe06182e" />

Below is the word cloud for opinions

<img width="720" height="397" alt="IMG-20250131-WA0001" src="https://github.com/user-attachments/assets/08f51b9d-e992-4b07-9618-4c2157dff410" />

After the visualization, the text was converted into vectors with TF-IDF vectorizer.

## Construct and Interpret

**The approach:**

1. Split the data into training, validation, and test sets

2. Tune hyperparameters using cross-validation on the training set

3. Use all tuned models to predict on the validation set

4. Select a champion model based on performance on the validation set

5. Use champion model alone to predict on test set

The three models had great cross-validation scores indicating a good model performance. 

The models achieved almost perfect scores when used to predict on the validation set but the random forest model performed a little bit better than the decision tree model and XGBoost model using the F1 score as the deciding metric. The random forest model achieved an F1 score of 99.9%, while the decision tree model and XGBoost model achieved F1 scores of 99.8% and 99.7% respectively. So, the random forest is the champion model.

Below are the predicted scores of the three models on the validation set.

<img width="720" height="156" alt="three model prediction scores" src="https://github.com/user-attachments/assets/885237be-f2a5-4e37-b41b-d0b5b23b9a50" />

The champion model achieved 100% on all the metric scores when evaluated on the test set. The confusion matrix showed no missclassification.

<img width="701" height="162" alt="rf test scores" src="https://github.com/user-attachments/assets/4c7f3856-97bb-4353-abf9-3e403dd5247f" />

<img width="720" height="591" alt="confusion matrix" src="https://github.com/user-attachments/assets/73cb1080-b301-41c8-a61b-f12e717d6e46" />

## Conclusion

The random forest model appears to be a perfect final model
