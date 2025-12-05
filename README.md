# Student Score Prediction Using Multiple Linear Regression
## Overview

This project applies a multiple linear regression model to predict students’ total scores using their continuous assessment (CA) and exam scores. The model was trained on the SS3 Physics dataset and later applied to the SS2 and SS1 datasets to evaluate its performance across multiple class levels. The workflow demonstrates data cleaning, feature normalization, debugging, model training, and prediction on new datasets.

## 1. Building the Model (SS3 Dataset)

The project began with the SS3 dataset, where the columns included 1st CA, 2nd CA, 3rd CA, combined CA score, exams, and total score. The “Total” column served as the target variable for the regression model.

During initial training, several issues were encountered:

Hidden spaces and inconsistent capitalization in column names prevented the model from fitting properly.

The feature names had to be cleaned using .str.strip() and regex-based spacing normalization.

Once cleaned, the model was successfully trained, achieving an R² score of 1, which reflected the perfectly linear structure of the dataset and its small size.

## 2. Applying the Model to SS2

The SS2 dataset was used to test the model’s generalization ability. Before prediction:

An extra “Name” column was removed because it was not part of the features used during training.

Column names were normalized again to ensure they matched the SS3 dataset exactly.

Once aligned, predictions were generated for SS2, and the predicted totals closely matched the actual totals, confirming the model’s accuracy and transferability.

## 3. Testing on SS1 Without the Total Column

To validate the model under stricter conditions, the SS1 dataset was intentionally created without the Total column. This was done to ensure the model did not rely on hidden or leaked target information during prediction.

Steps I took:

The dataset was loaded without the Total feature.

An empty “Total” column was appended only for structure, not used as input.

All columns were cleaned and normalized to match the original training format.

The trained SS3 model was used to generate predicted totals for SS1.

The results were outstanding—the predicted totals were almost identical to the original real totals, showing that the model correctly learned the underlying relationship between CA scores, exams, and the total score.

## 4. Key Takeaways

Consistent feature naming is essential in machine learning pipelines. Hidden spaces and capitalization differences were the main debugging challenges.

The model showed strong generalization, accurately predicting totals for both SS2 and SS1 datasets.

Removing the Total column from SS1 confirmed that the model was not accidentally exposed to target leakage.

The strong performance across datasets highlights a stable linear relationship in the score structure.

## 5. Conclusion

This project successfully demonstrates the end-to-end process of training a linear regression model, debugging data inconsistencies, and applying the model to entirely new datasets. The exceptionally close predictions across different class levels validate both the model and the preprocessing workflow. The project also reveals the importance of clean, consistent data in achieving reliable machine learning outcomes.
