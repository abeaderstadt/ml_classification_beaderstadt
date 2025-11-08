# Peer Review: Beth's Project 
[Notebook reviewed](https://github.com/BethSpornitz/ml-bethspornitz/blob/main/notebooks/midterm/classification_bethspornitz.ipynb) 

## 1. Clarity & Organization (Is the notebook structured and easy to follow?)
Beth’s notebook is super well structured and easy to follow. She explored two datasets really thoroughly, which is impressive. The workflow makes sense starting with data exploration, then feature selection, modeling, and finally evaluation. Code cells have helpful comments, and the visualizations, like the countplots, make it really easy to see what’s going on.  

*Improvement Suggestion:* Adding a short “Project Objective” section at the top would help readers immediately, so they know the goal of each dataset from the start.

## 2. Feature Selection & Justification (Do the chosen features make sense given the objectives?)

| Case | Features Used      |
|------|--------------------|
| 1    | Odor only          |
| 2    | Gill size only     |
| 3    | Odor + Gill size   |

The features chosen make sense given the classification goal. Beth did a solid job mapping categorical features and handling missing values. The countplots for the selected features also help explain why they were picked. 

*Improvement Suggestion:* Adding a small visualization showing how each feature relates to the target class could make the feature choice even clearer for readers. That said, using odor is already an obvious and sensible choice.

## 3. Model Performance & Comparisons (Are the results and comparisons clearly explained?)
Model results are presented clearly, including Decision Tree, SVM, and Neural Network models. Confusion matrices along with precision, recall, f1-score, and accuracy made it easy to compare performance. The explanations are easy to follow and point out which models do best, especially when odor is included. All three models perform really well. 

## 4. Reflection Quality (Are insights well thought out?)
Reflections are thoughtful, pointing out insights about feature influence and model performance. Beth also notes overfitting issues where relevant. The notebook shows she really understands both datasets and the classification task.  

*Improvement Suggestion:* Instead of a "Challenges Faced" section, a “Lessons Learned” section could make the final section even fuller, since there weren’t really major challenges.
