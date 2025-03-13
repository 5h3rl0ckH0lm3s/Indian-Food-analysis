## Rationale & Objective:
- I have always been interested in culinary, since my childhood, especially in Indian cuisine. Luckily, I found this dataset on Kaggle based on the same.
- So I used Pandas and python to understand, assess, clean and organize the data and then perform the Univariate an Bivariate analysis on it to get some insightful findings from it.

## Summary of data:
- This is a dataset related to the cooking of 255 famous Indian dishes. It has the information about their Ingredients, cooking time, flavour, eating course and regionality in brevity.

### Column description:
- `name` : Most commonly known name of the dish.
- `ingredients` : Basic ingredients required to cook the dish.
- `diet` : The dish is veg or non-veg.
- `prep_time` : The time required to do the preparations before cooking the dish.
- `cook_time` : The time required to cook the dish after completing the preparation.
- `flavor_profile` : Flavour of the dish, whether it is sweet, spicy, bitter or ambiguous (marked as -1 in the initial dataset).
- `course` : Course of eating the dish, whether it is dessert, main course or a snack.
- `state` : The state to which the dish belongs, based on its origin or popularity.
- `region` : The region in India, to which the state belongs


## Problems in the dataset:
1. Dirty data:
- Missing data : There are some entries in the `prep_time`, `cook_time`, `flavor_profile`, `state` and `region` column that are marked as -1. This can be due to ignorance or ambiguity.
- Accuracy : There is no instance where the data can be said sharply inaccurate, but it may be ambiguous at some places in the state and region column. For instance, the origin of `Dal tadka` is not known and its popularity is in the entire north India, but `Punjab` is written in its `state` column. `Poha` is another example, which has unmatched popularity in `Madhya Pradesh`, but `Maharashtra` is written in its state column.
- Consistency : One could easily find the few places in the `diet` column where `veg` or `non veg` is written instead of `vegetarian` or `non vegetarian`.

2. Messy data:
   The `ingredients` column is difficult to be categorized under numerical or categorical data, which makes the data slightly messy.

## Data cleaning:

1. **Handling Missing values (and Outliers)**: There are some places in the data where `-1` is written. It implies missing data at some places and outliers (or ambiguous data) at some places. Following is my approach:
- In the `prep_time` and `cook_time` columns, the best that we can do is to replace missing values (-1) by average of the known prep and cook times.
- On analysing the missing (-1) entries in the `flavor_profile` column, I found that most of the dishes had no taste (like `Chapati`), or had a mild taste (like `Bhakri`) or the taste was subjective to the particular way of preparation. So I found it most appropriate to write `mild` flavour in those dishes.
- On analysing the missing (-1) entries in the `state` and `region` column, I observed that it is missing in the case of dishes that have some ambiguous origin state but are the most commonly eaten dishes in Pan India. So I concluded to write `Pan India` in the `state` column and `India` in the `region` column.

2. **Duplicate rows**: Remove them simply by dropping.
  
3. **Inconsistency**: This is present only at a few places in the `diet` column, where `veg` or `non veg` is written instead of `vegetarian` or `non vegetarian`. So I have to just replace it.

4. **Messy data**: As I stated about the data being a little messy due to the ingredients column, I decided to make another column `ingredient_count`. This column will keep the count of ingredients required for each dish, which will help in analysis.


## Exploratory data analysis:
### Findings of univariate analysis:
- More than half of the dishes have cooking and preparation time less than 1 hour.
- Maximum Indian dishes require only 4-5 basic ingredients.
- There is a lot more variety in Vegetarian food than Non vegetarian.
- Nearly half dishes are spicy. This tells that Indians love spicy food.
- Most dishes in the data were of main course and dessert.
- The western states had the highest count. This tells about the rich cuisine culture and prosperity in Western India.

### Findings of bivariate analysis:
- Cooking time and preparation time are slightly correlated.
- Number of ingredients is very weakly correlated with cooking or preparation time.
- Scatter plots tell that dishes having less ingredients are more likely of having more cooking or preparation time.
- Vegetarian dishes are more likely of longer cooking and preparation times.
- Sweets and spicy dishes have the maximum cooking time.

### findings of multivariate analysis:
- All starters are spicy and main course tends to contain dishes having all types of taste.
- The data also tells that the most non vegetarian dishes are from east and South India. This colludes with the fact that North west India has the highest percentage of Vegetarian people.
- The huge variety of vegetarian dishes and high percentage of vegetarian population makes India unique.
- Conclusively, this data tells that every part of India has its own culinary culture, making the culinary diversity of India unmatched.