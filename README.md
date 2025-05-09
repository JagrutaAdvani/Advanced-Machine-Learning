## **Child Mind Institute — Problematic Internet Use**
Relating Physical Activity to Problematic Internet Use - https://www.kaggle.com/competitions/child-mind-institute-problematic-internet-use/

We participated in the Kaggle Competition titled “Child Mind Institute–Problematic Internet Use.” This repository contains all of our code used to explore, process, and model the data. The data is not included here because it is too large to upload on GitHub. It is available on the competition website though.

#### File descriptions:

1) DataExploration.ipynb: Notebook that we used to explore all the data. The plots in the EDA section of our blog are from here. The EDA also informed our data processing, so some of that processing is performed here, though it's repeated in our modeling files.
2) AcitgraphyProcessing.ipynb: This file includes some exploration of the actigraphy data as well as the creation of aggregate activity measures, such as the percentage of time spent sedentary.
3) Advanced_Actigraphy_Processing.ipynb: This file contains our attempt to utilize the actigraphy data better through autoencoding.
4) simple_reg_vs_classifier.ipynb: This file contains our first attempt at determining if regression or classification is better.
5) Advanced_Regression_Vs_Classification.ipynb: This file contains our more advanced attempt at determining if we should use regression or classification. We decided regression was better.
6) best_model.ipynb: This file contains all the methods we tried for pre-processing and our best model (multi-output regression using CATBoost and threshold optimization). The pre-processing settings can be changed at the top of the notebook. We used these settings to explore the best combination of methods that processed the data best according to cross-validation scores.


### Overview
Can you predict the level of problematic internet usage exhibited by children and adolescents, based on their physical activity? The goal of this competition is to develop a predictive model that analyzes children's physical activity and fitness data to identify early signs of problematic internet use. Identifying these patterns can help trigger interventions to encourage healthier digital habits.

* Start

Sep 19, 2024
* Close
Dec 19, 2024

### Description
In today’s digital age, problematic internet use among children and adolescents is a growing concern. Better understanding this issue is crucial for addressing mental health problems such as depression and anxiety.

Current methods for measuring problematic internet use in children and adolescents are often complex and require professional assessments. This creates access, cultural, and linguistic barriers for many families. Due to these limitations, problematic internet use is often not measured directly, but is instead associated with issues such as depression and anxiety in youth.

Conversely, physical & fitness measures are extremely accessible and widely available with minimal intervention or clinical expertise. Changes in physical habits, such as poorer posture, irregular diet, and reduced physical activity, are common in excessive technology users. We propose using these easily obtainable physical fitness indicators as proxies for identifying problematic internet use, especially in contexts lacking clinical expertise or suitable assessment tools.

This competition challenges you to develop a predictive model capable of analyzing children's physical activity data to detect early indicators of problematic internet and technology use. This will enable prompt interventions aimed at promoting healthier digital habits.

Your work will contribute to a healthier, happier future where children are better equipped to navigate the digital landscape responsibly.

### Acknowledgments
The data used for this competition was provided by the Healthy Brain Network, a landmark mental health study based in New York City that will help children around the world. In the Healthy Brain Network, families, community leaders, and supporters are partnering with the Child Mind Institute to unlock the secrets of the developing brain. In addition to the generous support provided by the Kaggle team, financial support has been provided by the California Department of Health Care Services (DHCS) as part of the Children and Youth Behavioral Health Initiative (CYBHI).

### Evaluation
Submissions are scored based on the quadratic weighted kappa, which measures the agreement between two outcomes. This metric typically varies from 0 (random agreement) to 1 (complete agreement). In the event that there is less agreement than expected by chance, the metric may go below 0.

To compute the quadratic weighted kappa, we construct three matrices, 𝑂
, 𝑊
, and 𝐸
, with 𝑁
 the number of distinct labels.

The matrix 𝑂
 is an 𝑁×𝑁
 histogram matrix such that 𝑂𝑖,𝑗
 corresponds to the number of instances that have an actual value 𝑖
 and a predicted value 𝑗
.

The matrix 𝑊
 is an 𝑁×𝑁
 matrix of weights, calculated based on the squared difference between actual and predicted values:

𝑊𝑖,𝑗=(𝑖−𝑗)2(𝑁−1)2

The matrix 𝐸
 is an 𝑁×𝑁
 histogram matrix of expected outcomes, calculated assuming that there is no correlation between values. This is calculated as the outer product between the actual histogram vector of outcomes and the predicted histogram vector, normalized such that 𝐸
 and 𝑂
 have the same sum.

From these three matrices, the quadratic weighted kappa is calculated as: 

𝜅=1−∑𝑖,𝑗𝑊𝑖,𝑗𝑂𝑖,𝑗∑𝑖,𝑗𝑊𝑖,𝑗𝐸𝑖,𝑗.

### Submission File
For each id in the test set, you must predict the corresponding sii (described on the Data page). The file should contain a header and have the following format:

### Dataset Description
The Healthy Brain Network (HBN) dataset is a clinical sample of about five-thousand 5-22 year-olds who have undergone both clinical and research screenings. The objective of the HBN study is to find biological markers that will improve the diagnosis and treatment of mental health and learning disorders from an objective biological perspective. Two elements of this study are being used for this competition: physical activity data (wrist-worn accelerometer data, fitness assessments and questionnaires) and internet usage behavior data. The goal of this competition is to predict from this data a participant's Severity Impairment Index (sii), a standard measure of problematic internet use.

Note that this is a Code Competition, in which the actual test set is hidden. In this public version, we give some sample data in the correct format to help you author your solutions. The full test set comprises about 3800 instances.

The competition data is compiled into two sources, parquet files containing the accelerometer (actigraphy) series and csv files containing the remaining tabular data. The majority of measures are missing for most participants. In particular, the target sii is missing for a portion of the participants in the training set. You may wish to apply non-supervised learning techniques to this data. The sii value is present for all instances in the test set.

### HBN Instruments
The tabular data in train.csv and test.csv comprises measurements from a variety of instruments. The fields within each instrument are described in data_dictionary.csv. These instruments are:

Demographics - Information about age and sex of participants.
Internet Use - Number of hours of using computer/internet per day.
Children's Global Assessment Scale - Numeric scale used by mental health clinicians to rate the general functioning of youths under the age of 18.
Physical Measures - Collection of blood pressure, heart rate, height, weight and waist, and hip measurements.
FitnessGram Vitals and Treadmill - Measurements of cardiovascular fitness assessed using the NHANES treadmill protocol.
FitnessGram Child - Health related physical fitness assessment measuring five different parameters including aerobic capacity, muscular strength, muscular endurance, flexibility, and body composition.
Bio-electric Impedance Analysis - Measure of key body composition elements, including BMI, fat, muscle, and water content.
Physical Activity Questionnaire - Information about children's participation in vigorous activities over the last 7 days.
Sleep Disturbance Scale - Scale to categorize sleep disorders in children.
Actigraphy - Objective measure of ecological physical activity through a research-grade biotracker.
Parent-Child Internet Addiction Test - 20-item scale that measures characteristics and behaviors associated with compulsive use of the Internet including compulsivity, escapism, and dependency.
Note in particular the field PCIAT-PCIAT_Total. The target sii for this competition is derived from this field as described in the data dictionary: 0 for None, 1 for Mild, 2 for Moderate, and 3 for Severe. Additionally, each participant has been assigned a unique identifier id.

### Actigraphy Files and Field Descriptions
During their participation in the HBN study, some participants were given an accelerometer to wear for up to 30 days continually while at home and going about their regular daily lives.

series_{train|test}.parquet/id={id} - Series to be used as training data, partitioned by id. Each series is a continuous recording of accelerometer data for a single subject spanning many days.

id - The patient identifier corresponding to the id field in train/test.csv.
step - An integer timestep for each observation within a series.
X, Y, Z - Measure of acceleration, in g, experienced by the wrist-worn watch along each standard axis.
enmo - As calculated and described by the wristpy package, ENMO is the Euclidean Norm Minus One of all accelerometer signals (along each of the x-, y-, and z-axis, measured in g-force) with negative values rounded to zero. Zero values are indicative of periods of no motion. While no standard measure of acceleration exists in this space, this is one of the several commonly computed features.
anglez - As calculated and described by the wristpy package, Angle-Z is a metric derived from individual accelerometer components and refers to the angle of the arm relative to the horizontal plane.
non-wear_flag - A flag (0: watch is being worn, 1: the watch is not worn) to help determine periods when the watch has been removed, based on the GGIR definition, which uses the standard deviation and range of the accelerometer data.
light - Measure of ambient light in lux. See ​​here for details.
battery_voltage - A measure of the battery voltage in mV.
time_of_day - Time of day representing the start of a 5s window that the data has been sampled over, with format %H:%M:%S.%9f.
weekday - The day of the week, coded as an integer with 1 being Monday and 7 being Sunday.
quarter - The quarter of the year, an integer from 1 to 4.
relative_date_PCIAT - The number of days (integer) since the PCIAT test was administered (negative days indicate that the actigraphy data has been collected before the test was administered).
sample_submission.csv - A sample submission file in the correct format. See the Evaluation page for more details.
