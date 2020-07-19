# Recommendations with IBM

A capstone project during my Udacity Data Science Course that includes different kinds of recommendations: 
* Rank-based recommendations
* User-User Based Collaborative Filtering
* Content Based Recommendations
* Matrix Factorization (Single Value Decomposition) 


### Background

On the IBM Watson studio, various articles about Data Science can be obtained. The students receive CSV files with user-item interactions (which user read which article) and with information about the articles. 


### Files

* Recommendations_with_IBM.ipynb: Main file with the tasks and solutions
* project_tests.py: Python file with tests that are executed in the notebook to check the results
* Four pickle files: Files that are used by the project_tests.py and the notebook. 


### Tasks and recommendations


#### Rank-Based Recommendations

This recommendation gives back the top rated articles. "Top rated" means in this context most user-item interactions. This kind of recommendation is especially useful if we don't have any other information about the user's preferences. 


#### User-User Based Collaborative Filtering

This recommendation is based on finding similar users: Any user that has interacted with the same articles as the user, we are making recommendations for, can help us with finding new articles that could be of interest.

One drawback of recommendation system is that a new user, that didn't interact with any article before, cannot receive recommendations based on this system. 


#### Content Based Recommendations

##### Approach

1. This recommender tokenizes the text in a specific df_content column; I chose `doc_full_name`. (Function: get_tokens_content)
2. For each token, an additional column is generated; then these features are used to compute the dot_product matrix of all items. (Function: features_and_dot)
3. For a given article_id, the recommender looks for other article_ids with a high dot product and returns the article_ids and article_names. (Function: make_content_recs)

##### Improvements

* I have used the column `doc_full_name` for tokenization. However, I have not tried the other columns which may provide more specific information about the articles. 
* For tokenization, I removed punctuation from the text, however there are still some single words or letters ('g' or 'ost') which still exist and corrupt the dot product (e.g. a lot of article names have a 'g'). This could be improved with more Regex. 
* As "similar_idxs", I chose all articles, that have a higher dot product than the median of the specific article row. However, they are not sorted, which means that when chosing only the first 10 articles, other articles with a higher dot product may not be shown. 


#### Matrix Factorization¶

This technique uses Single Value Decomposition (SVD) and needs a certain number of latent features that describe certain users or articles (e.g. this user likes Data Science or this article is about Machine Learning). The use of SVD provides three different datasets that can be used to predict values and hence interactions. 

Unfortunately, SVD does not work if there are any NaNs in the datasets, which is where FunkSVD comes into play. 


### How to interact

Every contribution is welcome. I think there are many possibilities to improve the performance of the content based recommendation system (see above). 


### Acknowledgments

Thanks to the Udacity team for all the instructions. 


### Author

Maximilian Müller, Business Development Manager in the Renewable Energy sector. Now diving into the field of data analysis. 


### License

Copyright 2020 Maximilian Müller

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated 
documentation files (the "Software"), to deal in the Software without restriction, including without limitation the 
rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit 
persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the 
Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE 
WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR 
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR 
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

From opensource.org
