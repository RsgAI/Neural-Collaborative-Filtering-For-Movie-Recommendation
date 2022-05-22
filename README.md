
---
# *<center>Neural Collaborative Filtering For Movie Recommendation</center>*

*In this project, neural collaborative filtering method is applied to a small part of the [MovieLens Latest Dataset](https://grouplens.org/datasets/movielens/latest/ "Permalink For Latest Dataset").
The original dataset was used by adapting it to the model type to be used to train different recommendation models(Binary Classification, Categorical Classification, Regression).*

*In this project, The use of the embedding layer is exemplificated. 
Using models that produce different output types on the same problem, the use of different types of [ANN](https://en.wikipedia.org/wiki/Artificial_neural_network "Wikipedia") Models is briefly mentioned.
Predictions are based on User-Item Collaborative Filtering Method.*

---

### *Dataset*
In this context, the [**MovieLens Latest Dataset**](https://grouplens.org/datasets/movielens/latest/ "Permalink For Latest Dataset"), which is a popular dataset, is used.

- [**All MovieLens Datasets**](https://grouplens.org/datasets/movielens/ "All Datasets")
---

### *Version*

- _Python Version: **3.7.4**_
- _Numpy Version: **1.16.5**_
- _Pandas Version: **0.25.1**_
- _Tensorflow Version: **2.0.0**_
- _Sklearn Version: **0.21.3**_

---

### *Model*

- As a result of the research, it was decided that models with _Dual Embedding_ layer and _Matrix Factorization_ layer should be preferred in order to get the best results in **Neural Collaborative Filtering** applications
(see [**Neural Collaborative Filtering Pdf**](https://arxiv.org/pdf/1708.05031.pdf "arxiv.org pdf Link")). For this reason, the determined _Neural Collaborative Filtering_ model was used without changing it except for the necessary changes.
This model is trained with the same dataset adapted to different classification types and the results are evaluated.

---

# *<center>Notebooks</center>*

---

## *Data Preparation*

### - Preparation

1. **Preparation1:** First Step of data preperation process. Reading data from csv file, dataset is shrinking,
unused attributes and unrated movies are deleted. Ids are reset and data is saved as _pkl_ files for future use.
**_RawData_** _(Rating.pkl, Movie.pkl)_ is created in this notebook.
See <ins>_/DataPreparation/Preparation1.ipynb_</ins> file for details.
2. **Preparation2:** Data is prepared for training, based on the most primitive type of relationship between users and movies.
This relationship is based only on interactions. **[0, 1]** - _['Not Interacted', 'Interacted']_. Two different datasets are creating in this notebook. One of them has only interacted pairs as input.
It is the dataset named InteractedOnly. The other one has a sample of not interacted pairs as input. It is the dataset named NotInteractedSample.
**_BinaryInteraction_** datasets consist of these two datasets.
Datasets  organized as Training, Validation and Test data, saved as _pkl_ files for future use.
See <ins>_/DataPreparation/Preparation2.ipynb_</ins> file for details.
3. **Preparation3:** Data is prepared for training, based on a simple binary relationship. **[** _**0** : Movie Rated by user less than 3, **1** : Movie Rated by user greater than or equal to 3_ **]** - **[0, 1]** - _['Not Liked', 'Liked']_.
Two different datasets are creating in this notebook. One of them has only observed pairs as input. It is the dataset named ObservedOnly.
The other one has a small sample of not observed pairs labeled as _0 ('Not Liked')_ for input. It is the dataset named UnobservedSample.
Some researches and scientists consider this as a valid technique (e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma")).
**_BinaryLike_** datasets consist of these two datasets.
Datasets  organized as Training, Validation and Test data, saved as _pkl_ files for future use.
See <ins>_/DataPreparation/Preparation3.ipynb_</ins> file for details.
4. **Preparation4:** Data is prepared for training, based on a categorical relationship. **[** _**0** : Movie Rated by user less than 2, **1** : Movie Rated by user greater than or equal to 2 and less than 4, **2** : Movie Rated by user greater than or equal to 4_ **]** - **[0, 1, 2]** - _['Hated', 'Not Liked', 'Liked']_.
Two different datasets are creating in this notebook. One of them has only categorized pairs as input. It is the dataset named CategorizedOnly.
The other one has a small sample of not categorized pairs labeled as _0 ('Hated')_ for input. It is the dataset named NotCategorizedSample.
Some researches and scientists consider this as a valid technique (e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma")).
**_CategoricalLike_** datasets consist of these two datasets.
Datasets  organized as Training, Validation and Test data, saved as _pkl_ files for future use.
See <ins>_/DataPreparation/Preparation4.ipynb_</ins> file for details.
5. **Preparation5:** Data is prepared for training, based on _Rating Based_ relationship. Ratings are decimals in the range **[0.5, 5]** that continue to increase by **0.5**. Two different datasets are creating in this notebook.
One of them has only rated pairs as input. It is the dataset named RatedOnly. The other one has small sample of not rated pairs consider with **0.0** _(Less than Minimum score for rating)_ scores. It is the dataset named UnratedSample.
Some researches and scientists consider this as a valid technique (e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma")).
**Min-Max normalization** applied both datasets. So the ratings are converted to continuous decimals in the range **[0, 1]**. 
**_RatingBased_** datasets consist of these two datasets.
Datasets  organized as Training, Validation and Test data, saved as _pkl_ files for future use.
Since this is thought to be the best approach, the focus will be on models trained with _Rating Based_ data during the training phase.
See <ins>_/DataPreparation/Preparation5.ipynb_</ins> file for details.

### - Qualification

1. **QualityCheck1:** The quality of both _BinaryInteraction_ datasets was checked and any necessary improvements are made.
Especially the representation of users and movies in the training dataset has been improved.
Datasets reorganized as Training, Validation and Test data, saved as _pkl_ file for future use.
See <ins>_/DataPreparation/QualityCheck1.ipynb_</ins> file for details.
2. **QualityCheck2:** The quality of both _BinaryLike_ datasets was checked and any necessary improvements are made.
Especially the representation of users and movies in the training dataset has been improved.
Datasets reorganized as Training, Validation and Test data, saved as _pkl_ file for future use.
See <ins>_/DataPreparation/QualityCheck2.ipynb_</ins> file for details.
3. **QualityCheck3:** The quality of both _CategoricalLike_ datasets was checked and any necessary improvements are made.
Especially the representation of users and movies in the training dataset has been improved.
Datasets reorganized as Training, Validation and Test data, saved as _pkl_ file for future use.
See <ins>_/DataPreparation/QualityCheck3.ipynb_</ins> file for details.
4. **QualityCheck4:** The quality of both _RatingBased_ datasets was checked and any necessary improvements are made.
Especially the representation of users and movies in the training dataset has been improved.
Datasets reorganized as Training, Validation and Test data, saved as _pkl_ file for future use.
See <ins>_/DataPreparation/QualityCheck4.ipynb_</ins> file for details.
5. **QualityCheck5:** Quality checked of all datasets. _Null values_ and _Duplicates_ checked, _User_ and _Movie sizes_ checked. _UserIds_ and _MovieIds_ checked.
See <ins>_/DataPreparation/QualityCheck5.ipynb_</ins> file for details.

___

## *Training*

1. **Training1:** In this notebook file, a _Binary Classification Model_ is trained with the _BinaryInteraction InteractedOnly_ dataset. Results are visualized in charts.
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_InteractedOnlyModel_** directory.
_BinaryInteraction InteractedOnly_ dataset contains only interacted pairs which means there is no negative output in training dataset.
Therefore, the model tended to produce positive results for all inputs.
The test results look pretty good too, since there are no negative results in validatin and test data either.
So, it was concluded that this dataset should not be used for the recommendation system.
See <ins>_/Training/Training1.ipynb_</ins> file for details.
2. **Training2:** In this notebook file, a _Binary Classification Model_ is trained with the _BinaryInteraction NotInteractedSample_ dataset. Results are visualized in charts.
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_NotInteractedSampleModel_** directory.
Although _BinaryInteraction NotInteractedSample_ dataset is more useful than the _BinaryInteraction InteractedOnly_ dataset
It is not a good dataset for the recommendation system.
Users may not have liked a movie they watched or users may like a movie they haven't watched.
Users should be offered movies that they might like, and the user-item relationship should be based on like.
Since this project is a movie recommendation system, although the training test results look good, this dataset is also useless.
See <ins>_/Training/Training2.ipynb_</ins> file for details.
3. **Training3:** In this notebook file, a _Binary Classification Model_ is trained with the _BinaryLike ObservedOnly_ dataset. Results are visualized in charts.
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_ObservedOnlyModel_** directory.
_BinaryLike ObservedOnly_ dataset contains labeled _[0, 1]_ - _['Not Liked', 'Liked']_ pairs.
Since _BinaryLike ObservedOnly_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
See <ins>_/Training/Training3.ipynb_</ins> file for details.
4. **Training4:** In this notebook file, a _Binary Classification Model_ is trained with the _BinaryLike UnobservedSample_ dataset. Results are visualized in charts.
_BinaryLike UnobservedSample_ dataset contains labeled _[0, 1]_ - _['Not Liked', 'Liked']_ pairs.
But also has a small sample of not observed pairs labeled as _0 ('Not Liked')_.
some researches and scientists consider this as a valid technique.
(e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma")).
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_UnobservedSampleModel_** directory.
Since _BinaryLike UnobservedSample_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
See <ins>_/Training/Training4.ipynb_</ins> file for details.
5. **Training5:** In this notebook file, a _Categorical Classification Model_ is trained with the _CategoricalLike CategorizedOnly_ dataset. Results are visualized in charts.
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_CategorizedOnlyModel_** directory.
_CategoricalLike CategorizedOnly_ dataset contains labeled _[0, 1, 2]_ - _['Hated', 'Not Liked', 'Liked']_ pairs.
Since _CategoricalLike CategorizedOnly_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
See <ins>_/Training/Training5.ipynb_</ins> file for details.
6. **Training6:** In this notebook file, a _Categorical Classification Model_ is trained with the _CategoricalLike NotCategorizedSample_ dataset. Results are visualized in charts.
_CategoricalLike NotCategorizedSample_ dataset contains labeled _[0, 1, 2]_ - _['Hated', 'Not Liked', 'Liked']_ pairs.
But also has a small sample of not categorized pairs labeled as _0 ('Hated')_.
some researches and scientists consider this as a valid technique.
(e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma")).
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_NotCategorizedSampleModel_** directory.
Since _CategoricalLike NotCategorizedSample_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
See <ins>_/Training/Training6.ipynb_</ins> file for details.
7. **Training7:** In this notebook file, a _Regression Model_ is trained with the _RatingBased RatedOnly_ dataset. Results are visualized in charts.
_RatingBased RatedOnly_ dataset contains continues rating value for each interacted pairs.
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_RatedOnlyModel_** directory.
Since _RatingBased RatedOnly_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
Since the dataset has a continuous rating score _Mean Squared Error function_ is used as _loss_ function.
Metrics are also being changed as the problem turns into a _Regression_ problem.
See <ins>_/Training/Training7.ipynb_</ins> file for details.
8. **Training8:** In this notebook file, a _Regression Model_ is trained with the _RatingBased UnratedSample_ dataset. Results are visualized in charts.
_RatingBased UnratedSample_ dataset contains continues rating value for each interacted pairs and a small sample of not interacted pairs Rated as _0.0 (Smaller than min rating)_.
Some researches and scientists consider this as a valid technique.
(e.g: [**Neural Collaborative Filtering**](https://towardsdatascience.com/neural-collaborative-filtering-96cef1009401 "by Abhishek Sharma"))
Obtained models are saved as _h5_ files by naming them with epoch numbers under the **_UnratedSampleModel_** directory.
Since _RatingBased UnratedSample_ dataset provides a valid criterion for like.
It can be a useful dataset for the recommendation system.
Since the dataset has a continuous rating score _Mean Squared Error function_ is used as _loss_ function.
_Metrics_ are also being changed as the problem turns into a _Regression_ problem.
See <ins>_/Training/Training8.ipynb_</ins> file for details.

---

## *Prediction Preparation*
1. **PredictPreparation1:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_InteractedOnlyModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation1.ipynb_</ins> file for details.
2. **PredictPreparation2:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_NotInteractedSampleModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation2.ipynb_</ins> file for details.
3. **PredictPreparation3:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_ObservedOnlyModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation3.ipynb_</ins> file for details.
4. **PredictPreparation4:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_UnobservedSampleModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation4.ipynb_</ins> file for details.
5. **PredictPreparation5:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_CategorizedOnlyModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation5.ipynb_</ins> file for details.
6. **PredictPreparation6:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_NotCategorizedSampleModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation6	.ipynb_</ins> file for details.
7. **PredictPreparation7:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_RatedOnlyModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation7.ipynb_</ins> file for details.
8. **PredictPreparation8:** In this notebook file, 
two tables are created to show the reliability of the recommendations to be made.
A _Model Table_ to show **_UnratedSampleModel_**'s metrics over training, validation and test data.
A _Lookup Table_ to show user representations and the correct predictions _The Model_ made for the user.
Tables will provide extra information about the _Predictions_.
See <ins>_/PredictPreparation/PredictPreparation8.ipynb_</ins> file for details.

---

## *Prediction*
1. **Perdiction1:** In this notebook, movie recommendations are made to two different predetermined users by using both _Binary Classification_ models _InteractedOnlyModel_ and _NotInteractedSampleModel_.
According to the predictions of _InteractedOnlyModel_ and _NotInteractedSampleModel_, six different recommendations are made for each user.
See <ins>_/Perdiction/Perdiction1.ipynb_</ins> file for details.
2. **Perdiction2:** In this notebook, movie recommendations are made to two different predetermined users by using both _Binary Classification_ models _ObservedOnlyModel_ and _UnobservedSampleModel_.
According to the predictions of _ObservedOnlyModel_ and _UnobservedSampleModel_, six different recommendations are made for each user.
See <ins>_/Perdiction/Perdiction2.ipynb_</ins> file for details.
3. **Perdiction3:** In this notebook, movie recommendations are made to two different predetermined users by using both _Categorical Classification_ models _CategorizedOnlyModel_ and _NotCategorizedSampleModel_.
According to the predictions of _CategorizedOnlyModel_ and _NotCategorizedSampleModel_, six different recommendations are made for each user.
See <ins>_/Perdiction/Perdiction3.ipynb_</ins> file for details.
4. **Perdiction4:** In this notebook, movie recommendations are made to two different predetermined users by using both _Regression_ models _RatedOnlyModel_ and _UnratedSampleModel_.
According to the predictions of _RatedOnlyModel_ and _UnratedSampleModel_, six different recommendations are made for each user.
See <ins>_/Perdiction/Perdiction4.ipynb_</ins> file for details.

- _**Note:** All prediction notebooks, have Markdown lines with detailed explanations, including the philosophy of the recommendations.
In these notebooks, answers to the questions of why and how are given.
Therefore, it is highly recommended to examine the prediction notebooks._
---
- _**Note:** All data and model files are deleted with their folders to save memory.
If notebook files are wanted to be run, the <ins>ratings.csv</ins> and <ins>movies.csv</ins> files in the
[**MovieLens Latest Dataset**](https://grouplens.org/datasets/movielens/latest/ "Permalink For Latest Dataset")
must be copied to the
<ins>/Data/csv/25M/</ins> 
path.
Non-existent folders must be created and notebook files must be run in the specified order._
---
## <center>_I'd Be Glad If You Report Any Mistakes You Notice._</center>
---