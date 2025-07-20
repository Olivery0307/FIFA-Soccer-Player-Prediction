# FIFA Soccer Player Position Prediction
## 📖 About The Project
This project uses data from the FIFA 22 video game to predict the optimal field position for a soccer player (Forward, Midfielder, or Defender) based on their in-game attributes. The goal was to build an interpretable model that could not only make accurate predictions but also reveal which player skills are most influential in determining their best position. The README file serves as a consise introduction of this project. For more details, please read the report.pdf attached in this repository.

This analysis serves as a practical tool for FIFA players creating a custom player in "Career Mode" or for anyone interested in understanding the statistical archetypes of different soccer positions.

The project follows a complete data analysis lifecycle:

- Data Preprocessing: Selecting relevant attributes and engineering features from a large dataset.

- Exploratory Data Analysis: Investigating correlations between player skills.

- Model Building & Selection: Evaluating multiple classification models (Decision Tree, KNN, Neural Network) and selecting the most appropriate one based on performance and interpretability.

- Insight Generation: Deriving clear, actionable rules from the final model to define the characteristics of each position.

## 🛠️ Methodology
**1. Data Source**<br />
The analysis was performed on the player_22.csv dataset, which contains statistics for 19,329 professional soccer players from the FIFA 22 video game. The dataset includes 110 attributes covering physical characteristics, skill ratings, and player positions.

**2. Data Preprocessing**<br />
To prepare the data for modeling, the following steps were taken:

- Feature Selection: Reduced the initial 110 attributes to 27 key variables, focusing on physical traits (height, weight) and core skill categories (attacking, skill, movement, power, defending).

- Feature Engineering: To reduce dimensionality while retaining information, attributes within the five main skill categories were averaged to create composite scores (e.g., attacking_average, defending_average). This was justified by the positive correlations observed among attributes within the same category.

- Target Variable Simplification: The 17 unique player positions were grouped into three primary roles: Defender, Forward, and Midfielder. Goalkeepers were excluded from the analysis due to their distinct and non-comparable skill sets.

**3. Model Selection & Development**<br />
A Decision Tree Classifier was chosen as the primary model. While other models like K-Nearest Neighbors and Neural Networks achieved slightly higher accuracy (up to ~80%), the Decision Tree was selected for its high interpretability. The ability to understand why a prediction was made was a key project objective.

The model was built as follows:

- The data was split into a 70% training set and a 30% testing set.

- The tree was pruned using GridSearch to find optimal hyperparameters (max_leaf_nodes=20, min_samples_leaf=100) to prevent overfitting.

- The final model produced a clear set of rules for classifying players based on their attributes.

## 📈 Results & Key Findings<br />
The final pruned Decision Tree model achieved a 73.47% accuracy on the test set, significantly outperforming both the naïve rule (41%) and random classification (33%).

The model revealed that the defending_average score is the single most important attribute for determining a player's position.

Key Classification Rules:
- Defenders: Primarily identified by high defending scores (>49). Interestingly, higher skill scores were often correlated with higher defending scores, indicating overall player quality.

- Forwards: Characterized by low defending scores (<29) and high power scores. Height was also a factor, with taller players more likely to be classified as forwards.

- Midfielders: Occupied the statistical middle ground, with defending scores typically between 29 and 49. This reflects their role as versatile players who contribute to both defense and attack.

A confusion matrix showed that the model was most accurate at identifying Defenders and least accurate with Midfielders, which aligns with the "in-between" nature of the midfield position.



## 💼 Business Implications & Applications
This project demonstrates the ability to translate a business question ("What is a player's best position?") into a data-driven solution. The model has several practical applications:

- For Gamers: FIFA players can use the model's rules as a guide when creating a custom player in "Career Mode" to ensure their attribute allocation aligns with their desired position.

- For Analysts: The project serves as a case study in using classification models to understand archetypes within a dataset, a technique applicable to customer segmentation, product categorization, and more.

- For Sports Analytics: While based on game data, the model provides a framework for how real-world player performance data could be used to identify underrated players or suggest new positions for versatile athletes.
