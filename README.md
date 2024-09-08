# Recipe Complexity and Ratings Analysis
#### Name(s): Tan Bao Tin Nguyen

## Introduction
#### The recipe interactions and data setscentral to this analysis. Dataset 1: RAW_interactions csv — User-item interactions: designed for things like clicks on the “like” button or purchase rates(version 0), ratings (version 1), and reviews. The second dataset RAW_recipes. csv, which contains the complete data for recipes like ingredient count, steps to prepare and nutritional values. These resources provide an unusual window into user behavior and preference, at least for cooking and recipe selection.

### Why This Matters
#### Recipe developers, food bloggers and even recipe apps should know how slightly complex recipes compromise on user satisfaction. It may also help others in creating and presenting recipe types that are typically rated higher. Like, do less complex recipes more or is easier make them simpler that's why people like them and are willing to spend typically a time on the menue whose reward seems higher? That would give us insight into factors that make a recipe popular.


## Question
#### Is there a relationship between the complexity of a recipe (number of steps and ingredients) and user ratings (satisfaction) for that recipe?
#### Why?: Such queries mesmerize me since they are about how cooking achieve at home satisfaction can be influenced by the complexity of a recipe. Complexity of a recipe shows itself in two main ways: in the number of ingredients and in the number of preparation steps. A recipe that has numerous steps may take longer, need more skills, whereas one that has many ingredients may have varieties of taste and modes of cooking. Considering these aspects will help us know if increasing complexity advantages or disadvantages an individual’s general kitchen experience.

### Relevant Columns
#### From RAW_recipes.csv:
##### id: The unique identifier for each recipe, which links to the recipe_id in the interactions dataset.
##### n_steps: The number of steps in the recipe, representing its complexity.
##### n_ingredients: The number of ingredients in the recipe, another measure of complexity.
#### From RAW_interactions.csv:
##### recipe_id: Links to the id in the recipes dataset, connecting user interactions to specific recipes.
##### rating: The rating given by the user for the recipe, which will serve as the measure of user satisfaction.

### Number of Rows
#### The RAW_interactions.csv dataset contains 731927 rows, which represents individual user interactions (ratings and reviews).
#### The RAW_recipes.csv dataset contains 83782 rows, each representing a unique recipe.

## Data Cleaning and Exploratory Data Analysis
### Univariate Analysis
<img width="629" alt="Screenshot 2024-09-07 at 11 39 20 PM" src="https://github.com/user-attachments/assets/2f60ccb0-580b-483a-86e5-cd0d55f92db7">
<img width="545" alt="Screenshot 2024-09-07 at 11 40 01 PM" src="https://github.com/user-attachments/assets/51fbcd69-f320-405d-81ae-530e61ce1b59">
<img width="542" alt="Screenshot 2024-09-07 at 11 40 09 PM" src="https://github.com/user-attachments/assets/3e254db9-d4d6-444c-a970-261bfa5dabce">
<img width="544" alt="Screenshot 2024-09-07 at 11 40 18 PM" src="https://github.com/user-attachments/assets/6e88698e-edfa-4eb2-b660-ee2cdeb448be">
<img width="534" alt="Screenshot 2024-09-07 at 11 40 39 PM" src="https://github.com/user-attachments/assets/1b89afed-0433-462c-96d7-d569e2027d52">

## Bivariate Analysis
<img width="567" alt="Screenshot 2024-09-07 at 11 48 59 PM" src="https://github.com/user-attachments/assets/9589aa4a-81fa-4d8e-bcce-0ae322bf29fc">
<img width="571" alt="Screenshot 2024-09-07 at 11 49 04 PM" src="https://github.com/user-attachments/assets/dd78d963-67b9-4347-ad5b-dbef24e8145b">

## Interesting Aggregates

![download (4)](https://github.com/user-attachments/assets/3d70e503-8fc3-406d-8838-6b7483435ba9)
![download (5)](https://github.com/user-attachments/assets/9f0582e5-626f-4b65-bf53-da5f0737fbbc)

## Step 3: Assessment of Missingness
#### Considering the `RAW_interactions.csv` dataset, absence of some ratings can be regarded as **NMAR**. For example, people who’ve not rated may have chosen not to give scores for recipes they didn’t like or haven’t completed which means that missingness relates to hidden factors (dissatisfaction). Also, there is a need for more data like survey results explaining why users don’t leave ratings.

![download (6)](https://github.com/user-attachments/assets/8c3e09fa-c5c2-42ef-ba7c-ad827292cd76)

#### After running a permutation test, we found that the p-value was 1 (no difference). This suggests that the missingness of the `rating` column is no dependent on the number of ingredients in the recipe. Therefore, it appears that the number of ingredients does not affect whether a user leaves a rating for a recipe.

## Step 4: Hypothesis Testing
### Hypotheses
#### Null Hypothesis (H₀): The average rating for recipes with a high number of ingredients is the same as the average rating for recipes with a low number of ingredients.

#### Alternative Hypothesis (H₁): The average rating for recipes with a high number of ingredients is higher than the average rating for recipes with a low number of ingredients.

![download (7)](https://github.com/user-attachments/assets/a44d95c4-84a6-44f8-83a9-c8f5cc540c0e)

#### Conclusion: the observed difference of -0.024 and a p-value of 1.0 implying that there is no meaningful difference in the average ratings between recipes that are characterized by many ingredients and those with few ingredients. Indeed, this negative observed difference indicates that recipes with less number of ingredients may have a little bit higher rating (but this discrepancy is insignificant). A p-value of 1 suggests that throughout all permutations the differences in average rating could be equal or greater than the observed difference; hence, not statistically significant.

## Step 5: Framing a Prediction Problem
### Prediction Problem:
#### I will predict whether a recipe receives a high rating (defined as 4 or 5 stars) based on the number of steps, ingredients, and other recipe characteristics.

## Step 6: Baseline Model

#### My basic approach is a logistic regression model which takes into consideration number of steps and ingredients to predict if a dish will get high rating (4 or 5 stars). Since these parameters were numerical we have transformed them with the help of StandardScaler before fitting the model.
#### In terms of accuracy, it means that the system recognized 60% right recipes when tested against it; 0.6 on test set means that 60% were classified correctly by our model. Thus, analyzing confusion matrix as well as classification report demonstrates that the algorithm works quite good but nevertheless there is still a room for enhancing its precision and recall indicating that possibly more features or more complicated one should be used.

## Step 7: Final Model
#### I enhanced our model by adding new features and tuning hyperparameters. An interaction term between the number of ingredients and steps was created to better capture recipe complexity. Cooking times were also bucketized into categories to see if preparation time influences ratings.

#### I used a Random Forest Classifier and hyperparameter tuning. I achieved an accuracy of 62%, which is an improvement over the baseline model's accuracy of 60%. The model shows better precision and recall for both classes.

## Step 8: Fairness Analysis
### Hypotheses:
### Null Hypothesis (H₀): The model’s precision for Group X (simple recipes) and Group Y (complex recipes) is the same. Any difference is due to random chance.

### Alternative Hypothesis (H₁): The model’s precision for Group X is different (either higher or lower) than for Group Y.
![download (8)](https://github.com/user-attachments/assets/1509f288-e34e-4e1c-8c8e-8f9466d63959)

### Hypotheses:
### Null Hypothesis (H₀): The model’s precision for Group X (simple recipes) and Group Y (complex recipes) is the same. Any difference is due to random chance.

### Alternative Hypothesis (H₁): The model’s precision for Group X is different (either higher or lower) than for Group Y.
