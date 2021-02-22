# Human Activity Recognition

In this notebook, we are trying to predict the Activity of a user. As you can it is a Muliclassification Problem. This notebook is to build a model that can predict whether a person is `Laying`, `Standing` , `Sitting`, `Walking`, `Walking_upstairs`, or `Walking_downstairs`

Initially, the information in this dataset is the measurements from the accelerometer, gyroscope, magnetometer, and GPS of the smartphone. 

#### Data Information 
From the website: 

http://archive.ics.uci.edu/ml/datasets/Smartphone-Based+Recognition+of+Human+Activities+and+Postural+Transitions

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (`WALKING`, `WALKING_UPSTAIRS`, `WALKING_DOWNSTAIRS`, `SITTING`, `STANDING`, `LAYING`) wearing a smartphone <b>(Samsung Galaxy S II) </b> on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

### Let's talk about the features (columns)

We see, there are `563 individual features(columns)`. 

1. The features selected for this database come from the <b> accelerometer </b> and <b> gyroscope </b> 3-axial raw signals <b> tAcc-XYZ </b>. These time domain signals (prefix <b>'t'</b> to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. 


2. Similarly, the acceleration signal was then separated into body and gravity acceleration signals <b> (tBodyAcc-XYZ and tGravityAcc-XYZ) </b> using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 


3. Subsequently, the body linear acceleration and angular velocity were derived in time to obtain <b> Jerk signals (tBodyAccJerk-XYZ </b> and <b> tBodyGyroJerk-XYZ) </b>. Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm `(tBodyAccMag`, `tGravityAccMag`, `tBodyAccJerkMag`, `tBodyGyroMag`, `tBodyGyroJerkMag)`

`jerk is the rate at which an object's acceleration changes with respect to time`


4. Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing

`fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. `

(Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  


5. <b>'-XYZ' </b> is used to denote 3-axial signals in the X, Y and Z directions.

    - tBodyAcc-XYZ
    - tGravityAcc-XYZ
    - tBodyAccJerk-XYZ
    - tBodyGyro-XYZ
    - tBodyGyroJerk-XYZ
    - tBodyAccMag
    - tGravityAccMag
    - tBodyAccJerkMag
    - tBodyGyroMag
    - tBodyGyroJerkMag
    - fBodyAcc-XYZ
    - fBodyAccJerk-XYZ
    - fBodyGyro-XYZ
    - fBodyAccMag
    - fBodyAccJerkMag
    - fBodyGyroMag
    - fBodyGyroJerkMag`
    
    

6. The set of variables that were estimated from these signals are: 

    - `mean()`: Mean value
    - `std()`: Standard deviation
    - `mad()`: Median absolute deviation 
    - `max()`: Largest value in array
    - `min()`: Smallest value in array
    - `sma()`: Signal magnitude area
    - `energy()`: Energy measure. Sum of the squares divided by the number of values. 
    - `iqr()`: Interquartile range 
    - `entropy()`: Signal entropy
    - `arCoeff()`: Autorregresion coefficients with Burg order equal to 4
    - `correlation()`: correlation coefficient between two signals
    - `maxInds()`: index of the frequency component with largest magnitude
    - `meanFreq()`: Weighted average of the frequency components to obtain a mean frequency
    - `skewness()`: skewness of the frequency domain signal 
    - `kurtosis()`: kurtosis of the frequency domain signal 
    - `bandsEnergy()`: Energy of a frequency interval within the 64 bins of the FFT of each window.
    - `angle()`: Angle between to vectors.
    

7. Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

    `gravityMean
     tBodyAccMean
     tBodyAccJerkMean
     tBodyGyroMean
     tBodyGyroJerkMean`
 
 That's too much information. 
 
 
 ## What's our Plan?


### `Outline`

- <b>1. Read Dataset </b>


- <b>2. Datset Cleaning </b>
    - 2.1 Outliers
    - 2.2 Filling null values
    - 2.3 Check for data imbalance
    - 2.4 Correcting some feature names


   
- <b>3. Exploratory Data Analysis </b>


- <b>4. Data Preprocessing </b>
    - 4.1 Encoding categorical variables
    - 4.2 Normalization
    - 4.3 Split Training and testing
    
    
    
- <b>5. Models, Hyperparameter Tuning and Cross Validation</b>
    - 5.1 Logistic Regression 
    - 5.2 Naive Bayes 
    - 5.3 K-Nearest Neighbor
    - 5.4 Decision Tree
    - 5.5 Random Forest
    - 5.5 Support Vector Machine
    
    
