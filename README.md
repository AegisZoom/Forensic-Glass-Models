# Forensic Glass Classification: A Data Modelling Project

## COSC2670: Practical Data Science with Python

### Grade: 100%

## Introduction

This repository contains my work for the second assignment of COSC2670 in my Graduate Diploma of Data Science. 
The assessment was worth 30% of the final grade, and involved using a public dataset to build and evaluate
machine learning models. The objective was to simulate the traditional steps of a data science project:

1. Identify Research Goals
2. Identify and Retrieve Data
3. Data Preparation
4. Data Exploration
5. Data Modelling
6. Report Findings

For the purpose of the assignment, I had to select one of four potential projects with a dataset already supplied.
I selected the forensic glass sample dataset as it seemed the most intuitive of the four choices. In the upcoming
sections, I will explain how I applied this dataset to create classifiers that could predict the object associated
with a glass sample (e.g. windows, tableware, headlamps) based on the associated material properties with good accuracy. 
This page will provide a summary, but the 12-page pdf report details all procedures taken to executing this
project with extensive commentary on the results.

## Skills Used
- 💾 **Programming**:
Used Python 🐍 as the programming language, Jupyter Notebook as the IDE, and the NumPy, Pandas, Matplotlib, Seaborn, and Sklearn libraries. Programmed
the notebook to be scalable: it will still work if the forensic data is adjusted/updated.
- 🔮 **Data Modelling**:
Selected appropriate parameters for training k-Nearest Neighbours and Decision Tree classifying machine learning models using theoretical knowledge,
hill-climbing and automated procedures. Evaluated model effectiveness using confusion matrices, precision, recall, accuracy, and F1 scores.
- 📈 **Data Analysis**:
Performed statistical measures to identify trends in variables. Measures included mean, median, standard deviation, confidence intervals, and
outlier tests. Performed univariate and multivariate analyses to find trends and relationships in data.
- 📊 **Data Visualisation**:
Constructed histograms, pie charts, box plots, and scatter plots/matrices with trendlines as part of the exploration and analysis
of the data. Selected the appropriate visualisation methods based on the effectiveness of identifying and commmunicating trends and relationships in the data.
- 🧼 **Data Cleaning**:
Performed checks for datatypes, outliers, missing values, and impossible values using masks. Applied multivariate outlier detection techniques.
- 📐 **Problem-Solving**:
Applied a wide variety of techniques to each stage of the project to account for as many possibilities as possible. Selected appropriate techniques using a mixture
of strong theoretical knowledge and a natural intuition based on real life limitations.
- 🔍 **Debugging/Attention to Detail**:
Developed techniques and intuition for identifying glitches that produced abnormal results or errors in various stages of the project. Identified opportunities to
gather further insight into the data and model optimisation. Identified the presence and implications of trends, relationships, and outliers in the data.
- 📝 **Written Communication**:
Submitted a 12-page report of the development of the project at all stages, including background research, data cleaning procedures, exploration of trends and relationships in the
data, and the procedures to train, evaluate and optimise machine learning models.
- ⏰ **Time Management**:
Organised weekly schedules and deadlines for individual milestones with leeway for unexpected obstacles both related to and outside of the assessment, and prioritised developing the report alongside the programming portion of the assessment.
- 🔬 **Research**:
Extensively investigated techniques and solutions online to add advanced features to data visualisations. Performed background research in glass production to better understand the
chemical properties of glass before beginning the project.
- ⚛️ **Physics/Chemistry**:
Used my extensive background knowledge in physics and chemistry to guide the literature review, data cleaning and exploration stages to maximise model performance.

## Data Retrieval

As explained above, the purpose of this assessment was to create classification models for forensic glass data to classify them based on their material properties.
The following public dataset was used:

German, B. (1987). *Glass Identification* [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5WW2P](https://doi.org/10.24432/C5WW2P)

It can more simply be accessed from here:
[https://archive.ics.uci.edu/dataset/42/glass+identification](https://archive.ics.uci.edu/dataset/42/glass+identification) 

*This dataset was shared without modification, and no file in this repository is able to execute permanent modifications to the dataset in place of the original.
This dataset was shared and applied under the **Creative Commons Attribution 4.0 International License**, which can be accessed in the following link: 
[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)*


The first five rows of the dataset are shown below:

![Dataset](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/Dataset.PNG)

In short, the *Refractive Index* column measures the ability for the glass samples to bend light, and the columns containing the *%* character measure the proportion of oxides that contain that specific element. 
*Na %* for example specifies the proportion of Sodium Oxide formed on the surface of the glass sample. You can refer to the Periodic Table of Elements to see which letter corresponds to which chemical element.
Finally, the *Type of Glass* column simply states what object the glass shard is associated with. They are coded as numbers: a value of 1 means household window glass. For more details, see the report.

Therefore, the objective of the assessment is to construct machine learning models that predict the *Type of Glass* value using the *Refractive Index* and *%* columns.

## Data Cleaning

The following procedures were applied to check for data quality. Generously, the dataset was already cleaned but it was worthwhile to perform these operations for certainty.

- **Datatypes**: Checked that each variable was assigned the correct data type.
- **Missing Values**: Checked whether there were any missing values in each column. If there were any in the *%* columns for example, they could be imputed from knowing that
the sum of each row of percentages must be 100%.
- **Outliers**: Checked for theoretically possible values that might draw suspicion, including IDs greater than the number of samples and refractive index values of 1.
- **Duplicates**: Checked for duplicate IDs.
- **Multivariate Inconsistency**: Checked that the sum of *%* values per row was 100%, while allowing leeway for rounding errors.
- **Impossible Values**: Checked for negative IDs and percentages. Checked for percentages above 100%, refractive indexes below 1 (not physically possible), and
undefined values in the *Type of Glass* variable.

## Data Exploration Examples

A large number of visualisations were constructed to explore trends and relationships in the data. Only a few will be listed here, but the report and especially the Jupyter Notebook feature more data visualisations and commentary.

### Example 1: Refractive Index Histogram

![Histogram](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/RI_Histogram.PNG)

The above histogram was constructed to develop intuition for the spread of refractive indexes across the dataset. Paying attention to the scale of the x-axis, it is clear that
the refractive index between samples changes minimally, but does center around a value of 1.5184. The narrowness of the distribution and the presence of outliers opens the possibility that
the refractive index may be altered by the chemical composition of the glass, which is determined by the manufacturing process and thus the samples' commercial purpose. Similar histograms were developed for other variables.

### Example 2: (MgO %) vs (Type of Glass) Box Plot

![Box](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/MgO_Box.PNG)

The next step would then be to confirm if the purpose of the glassware affects chemical composition. Different glassware may require techniques to temper them against
blunt force for example. The box plot was selected as it is highly effective at comparing distributions of continuous variables between
classifications. For MgO specifically, it is shown to increase in presence on window glassware. Similar box plots were developed for the other oxides.

### Example 3: (CaO %) vs (Refractive Index) Scatter Plot

![Scatter](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/CaO_Scatter.PNG)

Now that it is shown that refractive indexes are prone to variance, and that different glassware contains different chemical compositions, the final step is to assess
links between chemical composition and refractive index. This scatter plot paints a clear relationship between Calcium presence and the refractive index of glass.

## Data Modelling

The final step was to construct classification models using the requisite knowledge earned in the previous step. The performance of the two best classification models are shown below. Models were trained using 60% of the data available,
while the remaining 40% were used for testing. The training and testing data samples were stratified by their classification, that way each sample category had a 60:40 split
between the training and testing sets to promote fairness in the model performance.

### k-Nearest Neighbours Classifier

![kNN](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/kNN.PNG)

This model used parameters of k = 1 and p = 1, where k = 1 means the model will classify each data point to that of the closest training data point in higher-dimension coordinate space, instead of an average of the nearest two or three. 
The abstract distance between data points is calculated using the Minkowski formula: 

$$dist(x, y) = \left(\sum_{i=1}^n |x_i-y_i|^p \right)$$<sup>1/p</sup>

Generally, models using data points in dimensions greater than 3 (such as (2, 1, 3, 4), which is 4-dimensional) work best with p = 1. In addition, model performance (in overall accuracy, recall, and precision) was improved by ignoring the *Na %* and *Ba %* variables of the dataset. The accuracy improved by 3%, 
recall improved by 3% and precision improved by 1% as a result.

### Decision Tree Classifier

![DT](https://github.com/AegisZoom/Forensic-Glass-Models/blob/main/Images/DT.PNG)

This classifier was optimised by pruning the number of decisions it could make to reach a classification. The decision tree model could at the maximum filter data seven times to a total of twelve potential outcomes, 
forming seven classifications. This optimisation lead to great increases in accuracy, precision, and recall compared to the models that used the default parameters largely due to correcting the overfitting behaviour. 
Unfortunately, the decision tree classifiers cannot compete with the k-Nearest Neighbours classifiers. This is not surprising however, as decision trees struggle with continuous variables.

## Files, Folders and Specifications

In this repository, *4081442.zip* contains the *Assignment2.ipynb*, *report.pdf*, *glass.csv*, and *readme.txt* files, which was the format used for submission.

The *Assignment2.ipynb* file contains all code produced for the purpose of this assessment in the Markdown format. As a result, there is significant commentary provided at all stages of the file to inform readers.  It is not recommened to re-run the notebook, as it is computationally intensive.
Because this project was completed recently, the code should operate smoothly with current versions of Python, Jupyter, and the relevant libraries.

The *report.pdf* file is the 12-page report discussing all outputs of the code, and all the steps above in complete detail. Any questions about my work would likely be answered in this extensive document.

The *readme.txt* file provides information on running and reproducing the outputs for new users.

The *glass.csv* file contains the dataset used for the purpose of this assessment.

The *Images* folder houses all images used to construct this page.
