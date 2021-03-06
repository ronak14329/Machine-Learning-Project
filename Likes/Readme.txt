============================================================
To Run Like_pred.py file, please fallow below steps
============================================================

1.Software Installations:

     Install python 2.7 version
          on ubuntu/linux: on terminal type: sudo apt-get install python
         
     Install scikit learn package
          on ubuntu/linux: on terminal type: pip install -U scikit-learn

     Install numpy package
          on ubuntu/linux: on terminal type: sudo apt-get install python-numpy
     Install scipy package
          on ubuntu/linux: on terminal type: sudo apt-get install python-scipy
           

2.Download 'Merge.csv' file to your local system or where ever you want to execute.

3.Run the program using terminal window: python Likes_pred.py
    It will ask you to enter the path for Merge.csv, then enter the location where you put the Merge.csv file on your system.
  
Results will display one by one....Done.


=========================================================================
Description of Code:
=========================================================================

This is a python code, that works on user-likes relation to predict gender, age and big 5 personality traits.

We have extracted the features of each LikeId/PageId given in Relation.csv file.

We have used FacebookGraphAPI explorer to extract features from each page.

We mainly extracted the Category of each page from a list of features available in Graph API.

We have created a separate database called Merge.csv, which contains 'userid' and corresponding 'category' 
- of page which he/she liked and how many times they liked that particular category type page.

We also merged the label columns from Profile.csv file to Merge.csv based on unique userid.

We have imported the Merge.csv file into the code.

Split the data set into 70-30% and applied different Machine learning algorithms.

Applied K Fold Cross validation using scikit learn KFold function.

In this code we have used KNN, Gaussian NaiveBayes, SVM and Random Forest Classifier. 

We got better results when we apply Random Forest compared to other algorithms.

Accuracy- Age-71%, Gender-69%

=========================================================================
Functions Description:
=========================================================================

def get_age_group(age): Return Corresponding Age-Bucket

def get_age_label(age): Return Corrseponding integer Label for Age-Bucket. Since,Most of Machine learning algorithms takes Integer label values.

def get_images_labels(path,index,training_set): Process the input data and retrun the training set as Vector instances of Lists and corresonding labels as a list of integers. 

def get_testdata(path,index,training_set): Same as above, Prepare a testing set of Vector Instances of Lists and corresponding labels.

randForest = RandomForestClassifier(n_estimators = 500, n_jobs = 1)  creating a classifier object using Random Forest or any other Algorithms.

randForest.fit(features,labels) : Train the Model with training set of vector lists and labels, which returned by 'get_images_labels()' function mentined above.
	
predFeature = randForest.predict(t_fet) : Pass the Prepared testing set for the trained model to predict labels. Returns a list of predicted labels.

accuracy = accuracy_score(t_labels,predFeature) : Measure accuracy Predicted vs actual label values.

def rmse(y,x): Returns the RMSE value for each of Big 5 personality traits predictions.

def split(data,ratio): Returns the partitioned set of training and testing set.

cv = cross_validation.KFold(len(features), n_folds=5, random_state=None) : This is a Built in function provided by scikit learn package, which is used to perfom k fold split on the data.

=================================================================================================
Results
=================================================================================================
When Applied K Fold Cross validation for Age and Gender classification, k=5 , 70-30% split

Accuracy for Age: 0.71011
Accuracy for Gender: 0.6987
RMSE error for Openness: 0.78
RMSE error for concientiousness: 0.75
RMSE error for Extravert: 0.88
RMSE error for Agreeableness: 0.74
RMSE error for neuroticism: 0.93





