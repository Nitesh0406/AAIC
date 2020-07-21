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

Features in the data set
This reference blog helps me alot to understand the features of the data set.
https://medium.com/@boxinthemiddle/pbs-kids-measure-up-learning-analytics-part-1-9facbdafcdb5
train.csv and test.csv
Field Name	Description
event_id	Randomly generated unique identifier for the event type. Maps to event_id column in specs table. Total number of unique event _id is 384.
game_session	game_session is randomly generated id for specific installation_id. Game_session will not change until the user regines And when he/she comes to play next time a new session will be allotted to them.
time_stamp	it is the record of the actual time when the game was playing and the time is in the format of yyyy-mm-ddThh:mm:ss.mmmZ.
event_data	Semi-structured JSON formatted string containing the events parameters. Default fields are: event_count
installation_id	Unique for each installation and it represent a user.
event_count	Counts of number of games played after starting game_session
event_code	Identifier of the event 'class'. Unique per game, but may be duplicated across games. E.g. event code '2000' always identifies the 'Start Game' event for all games. Extracted from event_data.
game_time	Time in milliseconds since the start of the game session. Extracted from event_data.
title	Title of the game or video.
type	Media type of the game or video. Possible values are:
Game - game is task based . In order to go on to the next level a user has to 
finish the task for that level.
Clip - user will finish the task where concept or rules are explained in a 
short video.
Activity - This is comparatively long where children do not have any specific 
task . They can finish the activity when they are done.
Assessment - The user will reach an assessment after finishing several games 
, clips and activity. Assessment can be thought of as a fun exam where 
user will use all the skills which they have learnt in previous.
worls	Specific set of measurement.
None - At the apps start screen
TREETOPCITY - for height and length retaled skills.
MAGMAPEAK - for capacity related skills.
CRYSTALCAVES - for weights related skills
specs.csv
This file contains specification of various event types.
Field Name	Description
event_id	Global unique identifier for the event type. Joins to event_id column in events table.
info	Description of the event
args	JSON formatted string of event arguments. Each argument contains:
name - Argument name.
type - Type of the argument (string, int, number, object, array).
info - Description of the argument.
train_labels.csv
The file train_labels.csv has been provided to show how these groups would be computed on the assessments in the training set. Assessment attempts are captured in event_code 4100 for all assessments except for Bird Measurer, which uses event_code 4110. If the attempt was correct, it contains "correct":true.
Field Name	Description
game_session	game_session is randomly generated id for specific installation_id. Game_session will not change until the user regines And when he/she comes to play next time a new session will be allotted to them.
installation_id	Unique for each installation and it represent a user.
title	Title of the game or video.
num_correct	number of True(correct) counts for an Assessment event having event_code = 4100 and 4110. Only bird measurer Assessment has event_code 4110
num_incorrect	number of False(incorrect) counts for an Assessment event having event_code = 4100 and 4110. Only bird measurer Assessment has event_code 4110
accuracy	it is ratio of num_correct and (num_correct + num_incorrect)
accuracy_group	The outcomes in this competition are grouped into 4 groups 
(labeled accuracy_group in the data):
3: the assessment was solved on the first attempt
2: the assessment was solved on the second attempt
1: the assessment was solved after 3 or more attempts
0: the assessment was never solved
Mapping Real world problem to Machine Learning problem
Type of Machine Learning Problem
This is multiclass classification task. For given query data we need to predict the number of attempts that the user will take to pass the assessment and decide accuracy_group accordingly.
Performance Metrics (Quadratic Weighted Kappa (QWK))
Final score is evaluated using quadratic weighted kappa (QWK) which is measure of agreement between actual and predicted class. The range of this metric is generally 0 to 1. If QWK is 1 means actual and predicted class matches perfectly and if QWK is 0 means agreement happened by chance. QWK value can also take negative value which means the prediction is worse than by chance. QWK is calculated by
Number of classes is 𝑁=4
N
=
4
 in this task
𝜅=1−∑𝑖,𝑗𝑤𝑖,𝑗𝑂𝑖,𝑗∑𝑖,𝑗𝑤𝑖,𝑗𝐸𝑖,𝑗
κ
=
1
−
∑
i
,
j
w
i
,
j
O
i
,
j
∑
i
,
j
w
i
,
j
E
i
,
j
where 𝑤𝑖,𝑗
w
i
,
j
 is
𝑤𝑖,𝑗=(𝑖−𝑗)2(𝑁−1)2
w
i
,
j
=
(
i
−
j
)
2
(
N
−
1
)
2
𝑂
O
 is N-by-N matrix which is nothing but confusion matrix. Actual_value_counts and predicted_value_counts are 1-by-N dimensional vector which is histogram of actula class and predicted class . 𝐸
E
 is N-by-N matrix which is outer product of Actual_value_counts,predicted_value_counts.
https://www.kaggle.com/aroraaman/quadratic-kappa-metric-explained-in-5-simple-steps
