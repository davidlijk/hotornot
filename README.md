# Hot or Not? (An Analysis on Real-Time Hot-Word Removal)
## Executive Summary
### Problem Statement

Mainstream media or news broadcasting companies currently do not have an automated solution for censoring profanity in an individual’s speech.

In this analysis we will be building and comparing various hot-word detction models utilizing signal processing, source seperation, and binary classifcation for the purpose of real-time hot word detection. The primary purpose of this analysis is to see what signal processing features are the best predictors for a single hot word, and the secondary purpose of this analysis is to compare and contrast the time needed to process and predict from these models.

Hot word detection is a type of technology that listens for or activates when a specific "hot-word" is detected. Most common examples of this include activating google assistant by saying "hey google" or activating siri by saying "hey siri".

From this analysis, we wish to find out:
* Are time domain features or frequency domain features better predictors?
* How much accuracy can we gain from polynomial features, and at what cost of processing speed?
* Which machine learning model has the most accurate test predictions?
* Utilizing source separation, how much lag time would there be for real-time hot word removal?

The primary stakeholders for this analysis would be radio, media, or news broacasting companies looking into real-time hot-word removal systems, while the secondary stakeholders would be livestreaming companies looking to adhere to content rating systems.
### Dataset
In this analysis, we will be detecting the word `birthday` using a subset of birthday songs from the free music archive[2]:
https://freemusicarchive.org/music/Happy_Birthday_Song_Contest/The_New_Birthday_Song_Contest

We are using this collection of songs firstly because it is royalty free, and secondly because words that are sung by different individuals differ in pitch, tonality, duration, and enunciation. This creates a diverse set of observations for us to build our model on.
### Process/Approach
The process/approach we will be taking in this project will follow these steps:
1. Apply source seperation to obtain vocal tracks (spleeter[1])
2. Use google speech to text API to obtain where and when the word `birthday` appears in each vocal track.
3. Read vocal tracks into dataframe 
4. Create target variable using data obtained from google speech to text API
5. Utilize signal processing techniques to create features
6. Modeling
7. Model Comparison
8. Pseudo Deployment
9. Findings & Conclusion
### 1.4 Findings
These are the brief highlights of our findings:

* Time domain features are better predictors than frequency domain features.

* Gradient Boosting has the most accurate test predictions.

* Polynomial features had a 2% improvement for a runtime cost of around 45%.

* The lag time would be around 0.3 seconds for each second processed. This is not taking into account parallel processing, and is possible for further reduction by utilizing more efficient programming.
## Contents
1. Executive Summary
    * 1.1 Problem Statement
    * 1.2 Dataset
    * 1.3 Process/Approach
    * 1.4 Findings
2. Contents
3. Imports
4. Data Extraction
    * 4.1 Spleeter[1]
    * 4.2 Rename Vocal Tracks
    * 4.3 Check Sampling Frequency
    * 4.4 Convert Vocal Tracks to Dataframe
5. Target Mapping
6. Exploratory Data Analysis
7. Feature Engineering
8. Modeling
    * 8.1 Logistic Regression
    * 8.2 SVM
    * 8.3 Bagging
    * 8.4 Random Forest
    * 8.5 Extra Trees
    * 8.6 Adaboost
    * 8.7 Gradient Boosting
    * 8.8 XGBoost
9. Model Comparison
    * 9.1 Best Model
    * 9.2 Processing Speed Comparison
    * 9.3 Misclassifications
    * 9.4 Comparison of Coefficients
10. Pseudo Deployment
    * 10.1 Best Case
    * 10.2 Shortest Case
    * 10.3 Longest Case
11.Conclusion
    * 11.1 Findings
    * 11.2 Limitations
    * 11.3 Recommendations and Further Work
    * 11.4 References

## References
[1] Spleeter (https://github.com/deezer/spleeter)
@article{spleeter2020,
  doi = {10.21105/joss.02154},
  url = {https://doi.org/10.21105/joss.02154},
  year = {2020},
  publisher = {The Open Journal},
  volume = {5},
  number = {50},
  pages = {2154},
  author = {Romain Hennequin and Anis Khlif and Felix Voituret and Manuel Moussallam}
  title = {Spleeter: a fast and efficient music source separation tool with pre-trained models},
  journal = {Journal of Open Source Software},
  note = {Deezer Research}
}
[2] FMA Birthday Songs (https://freemusicarchive.org/music/Happy_Birthday_Song_Contest/The_New_Birthday_Song_Contest)
