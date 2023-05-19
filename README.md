# **Analysis and Exploration of food recipes and online interactions** #

**Introduction**
The two data sets "RAW_recipes.csv" (size: 83782 rows by 12 columns) and "RAW_interactions.csv" (size:731927 by 5 columns) were combined into one data frame (Initial size: 234429 rows by 19 columns) for the analysis and exploration seen below. "RAW_recipes" is a data frame that contains various information about recipes on food.com (e.g number of steps, ingredients, nutrition facts, etc.), while interaction hold information regarding user interaction with these recipes on the website(e.g reviews, user rating, comments etc).

The main question explored in this endeavor is: *Do recipes with a 1-star average rating have a different distribution of the number of steps in the recipe than 5-star average recipes?*


# **Cleaning and EDA (Exploratory Data Analysis)** #
The first step in the cleaning and EDA process was combining the two datasets provided. Since the enteries in recipes are unique, a left merge was conducted so that each row from the interactions data frame corresponded to a recipe from the recipes data frame, allowing multiple rows with the same recipe but differing in their interaction information since interactions are with respect to a recipe. These data frames both have a shared column called "id" in recipes and "recipe_id" in interaction which have shared values corresponding to the same recipe, these columns were used for the merge. The second step in this section, was converting ratings stord as 0-stars to null values. This was done because on the website users are allowed to leave comments and reviews without giving a star rating, the csv filed stored these types of interactions with a 0. This was important to change, because these 0 start rating would drastically affect the average during statistcal analysis later one. Once these 0 values were converted to null values, the average score for each recipe was computed based off of the user ratings (null values are not factored into this mean calculation thus giving an accurate result). After completing these steps the columns 'more_than_1_rating', 'has_null_avg_rating', and 'has_description' were added to the data frame. The aformentioned mention columns all store True or False values which are later used to asses missingness and simply computations for statistically analysis. Lastly the columns 'recipe_id' and 'review' were dropped since 'recipe_id' is a duplicate of 'id' and the 'review' column was not needed for the types of analysis later conducted.


| name                                 |     id |   n_steps | description                                                                                                                                                                                                                                                                                                                                                                       |   rating |   avg_rating | more_than_1_rating   | has_null_avg_rating   | has_description   |
|:-------------------------------------|-------:|----------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------:|-------------:|:---------------------|:----------------------|:------------------|
| 1 brownies in the world    best ever | 333281 |        10 | these are the most; chocolatey, moist, rich, dense, fudgy, delicious brownies that you'll ever make.....sereiously! there's no doubt that these will be your fav brownies ever for you can add things to them or make them plain.....either way they're pure heaven!                                                                                                              |        4 |            4 | False                | False                 | True              |
| 1 in canada chocolate chip cookies   | 453467 |        12 | this is the recipe that we use at my school cafeteria for chocolate chip cookies. they must be the best chocolate chip cookies i have ever had! if you don't have margarine or don't like it, then just use butter (softened) instead.                                                                                                                                            |        5 |            5 | False                | False                 | True              |
| 412 broccoli casserole               | 306168 |         6 | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 |        5 |            5 | True                 | False                 | True              |
| 412 broccoli casserole               | 306168 |         6 | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 |        5 |            5 | True                 | False                 | True              |
| 412 broccoli casserole               | 306168 |         6 | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 |        5 |            5 | True                 | False                 | True              |                                                                                                      

# **Univariate analysis Histogram** #
<iframe src="Assets/Univariate_graph.html" width=800 height=600 frameBorder=0></iframe>

The histogram above shows the distrubtion of how many steps 1 star recipes have (red) compared to 5 star recipes (blue). At first glance the distributions seem to be similar however there is alot more 5 star enteries(99924) than 1 star (697), due to the small sample size it is tough to say whether one is very different than another. Average steps for 1 star is 10.49 while avgerage steps for 5 star is 10.16.

# **Bivariate analysis scatterplot** # 
<iframe src="Assets/Bivariate_graph.html" width=800 height=600 frameBorder=0></iframe>

The scatter plot above shows the relationship between average rating and number of steps. There seems to be a weak slighlty positive correlation between the two variables aprox 0.3. 


# **Interesting Aggregates** #


|     False |       True |
|----------:|-----------:|
| 0.940668  | 0.998367   |
| 0.0593324 | 0.00163268 |

The table above shows the distribution of recipes that have or do not have more than 1 rating with recipes that have or do not have a null average rating. This table shows that 99.8% of recipes that have more than 1 rating do not have a null average rating meanwhile only 94.1% of recipes with 1 rating do not have a null average rating. This suggests that most recipes from the data set that have no rating only have 1 review, had this not been accounted for in the cleaning these recipes would have been stored as 0 greatly affecting the analysis. 

# **Assesment of Missingness** #


# **NMAR (No Missing At Random) Analyisis**

# **Missingness dependency** #

# **Hypothesis testing** # 
