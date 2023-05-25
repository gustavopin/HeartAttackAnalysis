# Project
This project will analyze health data to predict what caused the heart attack.
The data was collected at [Kaggle](https://www.kaggle.com/datasets/rashikrahmanpritom/heart-attack-analysis-prediction-dataset)
 - Some of the data was measured by [CDC](https://www.cdc.gov) and [Mayo Clinic](https://www.mayoclinic.org/)
 
# The Analysis
This project involves the analysis of hospital data of patients that had and hadn't Heart Attacks. It shows many parameters that can be linked to those occurencies and that can indicate the future occurency of one.

## Observation
There are only 303 people inside this dataset, so it does not represent the overall for the whole population, but some of those parameters can indicate serious health conditions and can not be overlooked.

## Data
As said before, the data was collected through Kaggle and revised using CDC and clinical websites to confirm minimums and maximums of the parameters.
All the meaning of the variables can be seen below:
 - age - age in years
 - sex - sex (1 = male; 0 = female)
 - cp - chest pain type (1 = typical angina; 2 = atypical angina; 3 = non-anginal pain; 0 = asymptomatic)
 - trtbps - resting blood pressure (in mm Hg)
 - chol - serum cholestoral in mg/dl
 - fbs - fasting blood sugar > 120 mg/dl (1 = true; 0 = false)
 - restecg - resting electrocardiographic results (1 = normal; 2 = having ST-T wave abnormality; 0 = hypertrophy)
 - thalach - maximum heart rate achieved
 - exang - exercise induced angina (1 = yes; 0 = no)
 - oldpeak - ST depression induced by exercise relative to rest
 - slp - the slope of the peak exercise ST segment (2 = upsloping; 1 = flat; 0 = downsloping)
 - ca - number of major vessels (0-3) colored by flouroscopy
 - thal - Thalium Stress Test result (2 = normal; 1 = fixed defect; 3 = reversable defect) - The results of this test will tell you about the flow of blood to your heart through your coronary arteries
 - output - 0 - no heart attack, 1 = had a heart attack
 
## Univariate
The first step was to look at the data as a whole and separate variable that aren't numerical (categorical variables) from those that are (continuous varibles).

This separation is important to better choose how to work with the variable.

Below we can see how the continuous variables can have a more matematical approach:

![Continuous Variables Table]('Images/continuous_table.png' Central Tendency Measures of Continuous Variables)

This table gives us important measures like minimum and maximum values for our numerical data (this will be important for the generation of graphics as we move on).

Means and medians will not be important because they will not reflect the our data, as an example we have cholesterol levels of 126 to 524. Looking at the mean value of 246, this would say that our patients are above the maximum value that woul be considered healthy (which is 200).

This composed image shows us how I managed to show those variables:

![Continuous Variables Graphics]('Images/continuous.png' Composed images of 4 continuous variables)

### Relative to this graphic we have:
For age: There are no young person in this data, everyone is at least 29 years old (looking at the table generated previously)
 - More than 200 people, of the 303, have less than 60 years old, and are considered adults. The other ~80 are elders between 60 and 77 years old (the maximun present within our data)
 - It is known that elderly people have more helth complications because of the deterioration of the cells.
 
For Blood Pressure: The normal blood pressures is within 100 and 125 measured through mm of HG (mercury). There are a couple of people that have less than 100 mm HG in their measure, this is known as hypotension, this can indicate and underlying problem that needs treatment.
 - The maximun pressure can be seen as 200, this is known as hypertension and can be linked to heart problems and extremely accute headaches
 - For cholesterol: this is the total cholesterol, summing LDL, HDL and VLDL and have values os 200 or less for healthy measures.
   - Excess of cholesterol can accumulate at the walls of vessels and can cause problems of circulation, heart attacks and vascular problems.
   - Almost 50 people had normal measures of cholesterol.
   - More than 175 people had readings exceeding the limits of cholesterol. The maximun being 524, which is too high.
     
For Maximun Heart Rate: By the [CDC](https://www.cdc.gov/physicalactivity/basics/measuring/heartrate.htm#:~:text=You%20can%20estimate%20your%20maximum,beats%20per%20minute%20(bpm).) we can calculate our maximun heart rate by our age, substracting it from 220.
 - This can be correlated directly with age, so as our data indicates, there are less people above 60 years old, so there are less measures of max heart rates between 60-100.

The variable 'oldpeak' is not included here because I could not find a minimum or maximum amount for it, just it's description as stated above.
 
### This next composed graphic is relative to our categorical variables:

![Categorical Variables Graphics]('Images/categorical.png' Composed images of categorical variables)

Looking individually at the univariate analysis of the categorical variables we have:
 - This data is composed of roughly 2/3 males
 - Most people did not have chest pain from exercises (exng)
 - Most people have no problems with their major vessels (showed by the number 0), but there are some marked with the number 4, which should not happen (this variable goes from 0 to 3)
 - There are more people with a number 2 chest pain, which is a atypical angina [(Is unpredictable and occurs at rest. Or the angina pain is worsening and occurs with less physical effort)](https://www.mayoclinic.org/diseases-conditions/angina/symptoms-causes/syc-20369373#:~:text=Angina%20pain%20is%20often%20described,that%20goes%20away%20with%20treatment.).
 - For Blood Sugar, roughly 1/6 of the people have a reading above 120mg/dl (the maximun amount).
 - Almost 50% of the people had results considered as hypertrophy of the ST-T waves in their eletrocardiographic, more than half had some abnormality in their readings (those abnormalities can had multiple explanations and can be linked with things that are not worrisome. The reading would need to be specified to have a better understanding).
 - The Slope is measured through exercise induced increments in heart rate. For results represented by the number 0, almost 25 patients had a downslope and more than 125 had a flat ST depression, depending on how attuned the downslope is and how was their hear rate, it could mean a severe cardiac problem. (correlate slp with heart rate).
 - The Thall test goes from 1 to 3 (2 being the normal result). The presence of a 0 could mean that those patients did not participate in this test or they have a irreversable defect in their coronary vessels. Most of the test subjects had a normal test, while less than 25 had a defect, but it was fixed, while almost 125 people had a defect, but it could be fixed. (this is another variable that can be compared to heart rate).
 
## Bivariate
To represent our bivariate analysis, I chose to use only the Correlation Matrix with outside information from the CDC and websites of clinics around the world that can give some explanation about the interaction of those paremeters. Here is the full correlation matrix:

![Correlation Matrix]('Images/corr_matrix.png' Correlation Matrix of all the variables)

For this correlation matrix:
 - The correlation coeficient have high numbers, even though the maximun is showed as 0.58.
 - The first one will talk here is the output: this parameter is relative to the people who had Heart Attacks. It has a high correlation with all other variables, except bloood sugar, but:
     - We can see that the correlation between the output and chol variable is low, but it is known that high cholesterol, as explained before, can accumulate in the major vessels' walls and create problems.
     - For the sugar, it's high concentration within the blood can damage vessels and nerves, and this damage can lead to heart problems, as indicated by [NIDDK](https://www.niddk.nih.gov/health-information/diabetes/overview/preventing-problems/heart-disease-stroke).
     - The restecg show a lower coeficient than the rest, it is viwed as ST-T wave abnormalities and, our data has less people with this kind of problem, but it has more people with hypertrophy, this variable alone can't indicade many things unless it is super attenueted. It varies with how relaxed, or not, the person is and it can be problematic if the equipment is not positioned right.
 - The variable Oldpeak and Slp are highly correlatable because both of them are measure through exercise induced methods. They show as negative 
     - The same can be seen with Exng variable and those two.
 - The high correlation between Thalachh and CP can be explained as: high heart rates can be very dangerous and cause some types of chest pain (tachycardia is one of the problems caused my high heart rates). 
 - Thall and Sex variable have a high correlation, but the thalium test only shows how well your blood is flowing and if the vessels have some kind of interruption, it is not linked to the sex of the person so it is probably a false correlation.
 - Ca is the number of major vessels with problems, so, the less vessels you have, less blood flows and more chest pain you have, so the correlation os CA and CP being 0,18 is fine and it is negative because they are inversely proportional.
 - Blood Pressure (trtbps) and age have a good correlation, this is due to the increase of the blood pressure rates as the persons ages.

## Conclusion
### Overall
This data is well structured and divided. There are a really great number of analysis that can be done with it, there is even the possibility of including machine learning to make predictions of heart attacks.

That being said, due to complications within my analysis, I had to start it over and I did not have sufficient time to make more analysis and/or implement a machine learn model to predict those problems. I started with the wrong questions and developed wrong analysis using this data. This serves as a reminder to always review the work before continuing something or it can become a snowball effect.

### About the Heart Attack Problem
The lack of young people within the data does not indicate that people under 19 years old can not have a Heart Attack, this just shows that the data can be improved if possible to broaden the age spectrum within it. Most of it is composed by adults, but 

Most of the data is composed by males, roughly 2/3 of it. To better know how this can affect the analysis, the ideal condition is to have a 50% male and 50% female so it can be separated equally.

The parameters that use the ST-T waves abnormalities are a great way to indicate the present of any problem that are treatable and/or can be avoided by exercise or better food habits.

As we can see within the correlation matrix above, the 'output' variable (this is to show the people that had heart attacks) has a high coeficient with most of the variables, excluding the fastening blood sugar and cholesterol (you can see a explanation for this above), those two are false correlations as they can aggravate situations or cause damage over time that leads to the heart problems. 

This alone can show the importance of those parameters to analyse heart problems. Most of those variables can indicate symptoms of a evolving heart attack and/or other heart/vascular problem and can indicate possible damage within the body that leads to those occurencies.

To predict an event like that is exceedingly difficult, as said before, the damage to lead to this problem can be developed over a long time, while it's results can happen within minutes. Using the other sources linked throughout this analysis, we can see that one parameter alone is not enough to define a attack like that, so I reinforce the importance of consulting with a doctor and doing many exams if any chest pain, difficult of breathing or leg failure is occuring.

This data does not show if the patients had some use of drugs, alcohol or tobacco (included second-hand smoking), as those can influence the occurencies too.