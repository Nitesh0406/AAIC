Kids Measure Up! Learning Analysis 

List of Contents :
Description
Problem Statement
Source of Data
Business Objectives and Constrains
Data Overview
Features in the Dataset
Mapping Real World Problem to Machine Learning Problem
Performance Metric
Description
Early learning apps are now becoming very popular for kids (age 3-5 yrs) to learn the basic concepts like length, height , weight and colors etc. PCB Kids Measure app is one of the most popular learning apps across the United-State which is funded by the U.S. department of education. This App allows kids to learn in a fun way by playing games and watching video and can see their most favourite cartoon so they love to come again and again.

Data Science Bowl is the world's largest Data Science competition and announces a challenging task each year allowing competitors to solve problems for social good. PCB Kids Measure app is their fifth competition which is presented by Booz Allen Hamilton and Kaggle.
https://www.kaggle.com/c/data-science-bowl-2019/overview
problem Statement
The task is to predict the number of attempts that a child will take to pass the given Assessment using gameplay data.
Source of data
Data set is available in the form of four csv files which are train.csv, test.csv, specs.csv and train_labels.csv.
Refer : https://www.kaggle.com/c/data-science-bowl-2019/data
Business Objectives and Constrain
latency Requirement
No strict latency constrain but prediction within an hour is preferable.
Effect of misclassification
Misclassification will couse bad customer experience and it might recude number of installation_id in future.
Performance Objectives
Predict the data with correct class as many as possible with high precision and high recall.
Data Overview
Data is available in the form of four csv files and brief desciption is below :
train.csv
File size - 3.16 GB

Number of entry - 11.3 M

Number of Columns - 11 

Name of Columns - {'event_id','game_session','time_stamp','event_data','installation_id','event_count','event_code','game_time','title','type','world'}

Number of unique installation_id - 17000 

test.csv
File size - 379.87 MB

Number of entry - 1.1 M

Number of Columns - 11 

Name of Columns - {'event_id','game_session','time_stamp','event_data','installation_id','event_count','event_code','game_time','title','type','world'}

Number of unique installation_id - 1000 

specs.csv
File size - 399.29 KB 

Number of entry - 386 

Number of Columns - 3 

Name of Columns - {'event_id','info','arg'}

train_labels.csv
File size - 1.01 MB 

Number of entry - 17690 

Number of Columns - 7 

Name of Columns - {'game_session','installation_id','title','num_correct','num_incorrect','accuracy','accuracy_group'}

