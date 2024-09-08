<img width="629" alt="Screenshot 2024-09-07 at 11 39 20 PM" src="https://github.com/user-attachments/assets/21f6098f-3ad8-464d-ad4b-8a24498c8878"># Recipe Complexity and Ratings Analysis
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

