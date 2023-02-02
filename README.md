# Sandbox for ML (Machine Learning) and AI (Artificial Intelligence)
Experiments in Artificial Intelligence (AI) and Machine Learning (ML) on AWS and Azure

## Azure Auto Machine Learning (Auto ML)
https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02-module-02.html

## Regression model (with Azure Machine Learning Designer)
https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02a-create-regression-model.html

### Evalute Regression model
1. Mean Absolute Error (MAE): The average difference between predicted values and true values. This value is based on the same units as the label, in this case dollars. The lower this value is, the better the model is predicting.
2. Root Mean Squared Error (RMSE): The square root of the mean squared difference between predicted and true values. The result is a metric based on the same unit as the label (dollars). When compared to the MAE (above), a larger difference indicates greater variance in the individual errors (for example, with some errors being very small, while others are large).
3. Relative Absolute Error (RAE): A relative metric between 0 and 1 based on the absolute differences between predicted and true values. The closer to 0 this metric is, the better the model is performing. Like RSE, this metric can be used to compare models where the labels are in different units.
4. Relative Squared Error (RSE): A relative metric between 0 and 1 based on the square of the differences between predicted and true values. The closer to 0 this metric is, the better the model is performing. Because this metric is relative, it can be used to compare models where the labels are in different units.
5. Coefficient of Determination (**R2**): This metric is more commonly referred to as **R-Squared**, and summarizes how much of the variance between predicted and true values is explained by the model. The closer to 1 this value is, the better the model is performing.

## Classification model (with Azure Machine Learning Designer)
https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02b-create-classification-model.html

### Evaluate Classification model thru Confusion Matrix
1. Accuracy: The number of correct predictions (true positives + true negatives) divided by the total number of predictions.
2. Precision: The number of the cases classified as positive that are actually positive: the number of true positives divided by (the number of true positives plus false positives).
3. Recall: The fraction of positive cases correctly identified: the number of true positives divided by (the number of true positives plus false negatives).
4. F1 Score: An overall metric that essentially combines precision and recall.
