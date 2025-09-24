# Is the Squirrel Grounded? (Predicting Squirrel Behavior)

## Introduction: 
In this project I plan on using machine learning to predict whether a squirrel is above ground(in a tree ) or not based on these features within the dataset.. I also plan on using machine learning to determine the color of the squirrels.
I decided on this dataset and topic because I found squirrels very interesting when I was younger and I thought it would be fun to work with this dataset. While I don’t believe this solves any real world problems, I know I would have loved to know where to look for squirrels when I visited my family in New York.

## Project Goals: 
I plan on using binary classification to determine whether a squirrel is on the ground or not. The second part will be using multiclassification to determine the color of a squirrel

## Dataset: 
In 2018 the city of new york created a squirrel census.
2018 Central Park Squirrel Census - Squirrel Data | NYC Open Data

## Machine Learning Models: 
### Binary classification: Decision Tree. 
I chose decision trees because I thought it would do the best with the versatile data I had, and they are very robust.
### Multi Classification: KNN, Random Forest. 
I chose KNN at first because they are adaptable. I also thought that squirrel  color would be determined more by location and grouping them together by location than they were. After running the KNN I saw a lot of issues arise and decided to switch to Random Forest which are better at dealing with large class imbalances

## Evaluations: 
I used all of the following to verify performance: Accuracy, precision, confusion matrix, train/test split, validation curve and, a classification report

## Challenges: 
 The most challenging part of this assignment was between cleaning the data set and the multi-class classification. Both of these things were difficult because the data I was using was very unrefined. Most of it was self-reported by random people so there were some weird quirks. Because of this some of the features I wanted to use were unfortunately unusable. 
  To start, some of the columns' answers affected the answers in other columns. For instance if ‘Above Ground Sighter Measure’ was FALSE then ‘Location’ had to be ‘Below Ground’.  I attempted to fill in the information that was missing but it led to far too many issues especially considering the fact that ‘Above Ground Sighter Measure’ had two data types (ints and booleans). I ended up dropping almost all the rows with missing values for those two features. There were a lot of other quirks that caused issues during the cleaning but that was the most notable one.
	The other issue I ran into was class imbalance, which I had anticipated, but not to the degree that it was. Both of  the target classes I used had imbalance, but the  imbalance in ‘Primary Fur Color’ was especially bad (83% were grey, 13% were cinnamon, and 3.5% were black).  I did many things to improve the class balance depending on the model (i.e. class weights, RandomOversampler). But what I was doing was causing overfitting. So it took a really long time to find the balance between all the performance metrics

## Results:
### Binary Classification (Decision Tree):
This model ran well without extensive hyperparameter tuning. So I decided to focus on the effects of removing unimportant features.
Initial run:
Accuracy: .81
Precision: .66
While there was not a large improvement between I learned a lot about what to do when removing features and I was able to carry those findings into my multiclass classification

### Multi-class Classification
#### KNN(initial attempt):
The first model I used was KNN and it did very poorly but after some tweaking( adjusting for class imbalance, and adjusting hyperparameters)  I was able to get a result 
Accuracy: .776

| Fur Color | Precision | Recall |
|-----------|-----------|--------|
| Black     | .08       | .12    |
| Cinnamon  | .36       | .16    |
| Gray      | .85       | .90    |

#### KNN( feature reduction)
After removing some of the features I found that there was an improvement in most areas, but it did worse in others
Accuracy: .765

| Fur Color | Precision | Recall |
|-----------|-----------|--------|
| Black     | .9        | .17    |
| Cinnamon  | .34       | .15    |
| Gray      | .85       | .89    |

After this run I decided to switch models as Random Forest is much better at dealing with large class imbalances

#### Random Forest(initial run):
The first version of Random Forest I made did worse than KNN, but after messing with the hyperparameters (increased n_estimators, max depth, min_sample_split; decreased min_sampled_leaf) I got  better results than KNN. 
Accuracy: .775

| Fur Color | Precision | Recall |
|-----------|-----------|--------|
| Black     | .29       | .21   |
| Cinnamon  | .33       | .41    |
| Gray      | .88       | .86    |


#### Random Forest (Final Model):
In the second version of random forest I changed the class weights and removed unimportant features and I saw a large improvement. Overfitting did improve slightly
Accuracy: .96, 
| Fur Color | Precision | Recall |
|-----------|-----------|--------|
| Black     | 1.00      | 1.00   |
| Cinnamon  | .82       | .88    |
| Gray      | .98       | .97    |

I do think there was overfitting when it came to black but the other two results were good enough where it was at that I thought this was a good stopping point. 
X and Y(Longitude and Latitude) were the biggest indicator of what color the squirrel was so the model. So now with this data I can tell people where to look for different squirrels

## Conclusion: 
My Project was relatively simple, but I did several things that I felt would make it more difficult while also being an interesting learning experience for myself. I have learned a lot from this class and this project. 
I think any improvements I make to this project would require more and better data at my experience level. If I were to get better data I would love to also incorporate a model that would tell people what squirrels would be doing at specific times ( the time data was too vague and there were too many missing values in the activity data for me to do this).
