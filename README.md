# Sentiment Analysis On IMDB Reviews
 
### Supervised by Tomasz Wiktorski
#### Project in Computer Science (DAT500), IDE, UiS 2021 



## Dataset Information

IMDb, is one of the largest databases for films, tv-shows, and similar content, people provide their valuable opinion on them every year. These reviews eventually play a huge role in the viewer's community. However, these reviews can sometime contain spoilers, and the user also marks them considering their functionality.


### Content

This dataset contains six json files. The original JSON files can be found in https://www.kaggle.com/ebiswas/imdb-review-dataset

## Dataset Stats:
* Total Records = 5, 571, 499
* Total Shows = 453, 528
* Users = 1, 699, 310
* Spoilers = 1, 186, 611

### Inspiration

Natural Language Processing & Sentiment Analysis
What's in a review? Is it positive or negative? IMDb reviews contain a lot of metadata that can be mined and used to infer meaning, business attributes, and sentiment.
In this project, we make the following key contributions:

* Use MRJob for Data Preprocessing and comparing performance of preprocessing using PySpark.
* To predict the analysis of each review given by the reviewers the IMDb system for every movie using different algorithms like TextBlob, Unsupervised analysis, using Vader,Logistic Regression with Count Vectorizer.
* Implement Logistic regression with Hashing TF-IDF usingMRJob and Pyspark.
* To compare performance in terms of processing time taken by each model between the two approaches (MRJobs andPySpark)
* To compare the accuracy of the sentiment predicted in each model based on the ratings provided by the reviewers.

## Requirements

We tried our best to implement every method from scratch. However in There are some general library requirements for some sections of the project and some are specific to individual methods. The general requirements are as follows.
* `numpy`
* `spacy`
* `nltk`
* `kaggle`
* `pyspark`
* `textblob`
* `CountVectorizer`
* `vaderSentiment`


The library requirements specific to some methods are:
* `keras` with `TensorFlow` backend for  MLP


## Steps


### To Run code with PySpark

To run all the code with preprocessing for pyspark on hadoop cluster fallow the following steps:
Dataset download:
* Install kaggle on master node: 
`pip install kaggle`

* Make hidden directory
`!mkdir -p ~/.kaggle`

* Copy your Kaggle API key 
`!cp kaggle.json ~/.kaggle/`

* Download dataset
`~/.local/bin/kaggle datasets download -d ebiswas/imdb-review-dataset`

* Unzip dataset:
`unzip -d imdb-review-dataset.zip imdb-review-dataset`

* Transfer data set in to HDFS file system 
`hadoop fs -put imdb-review-dataset/*.json /dis_materials`

* In final step just run jupyter notebook
run the Project_DAT500.ipynb notebook 


## To run Mrjob Approach Follow the Following step:

* Set the file path and name in the script according to your directory in `Review_Saperator.py` file and run. It will create a CSV file of reviews details only.
* run the `preprocessing.py` script on CSV file generated on the basis of above step.
* Now run `map_reduce_bow.py` script on the preprocessed csv file and store it in the file.  



### BaseLine Method

Run `map_reduce_bow.py` on the output CSV file from the preprocessing section. This will generate output file with predicted sentiments. `dictionary.py` is a file that contains all the negative and positive words which are included in `positive.txt` and `negative.txt`. `dictionary.py` is imported in the map-reduce implementation. It will create the sentemnet of each review which can be store into a file or print on the screen. 



## Conclusion

In this project we evaluated different approaches to the problem of sentiment analysis in Hadoop.The first approach. TextBlob sentiment polarity method is fast and has acceptable accuracy although it is not enough for a real-world usage as it is not very effective in identifying sentiments. Second approach is Unsupervised analysis using Vader model which gave very good accuracy however this improved accuracy is traded off by performance in the processing time. Third approach
used is ML approach for Classification model using Logistic regression where this approach was done in three ways using Hashing TF-IDF, Count vectorisation and N-Grams.Logistic regression using N-Grams had a longer processing time compared to Hashing TF-IDF and Count Vectorization but with a minimal difference in the accuracy of the prediction. We can conclude that performance in terms of processing of the lexicon based approaches were better compared to the Logistic regression approaches where in Vader gave a very good accuracy for the prediction compared to the accuracy of the TextBlob.










 






