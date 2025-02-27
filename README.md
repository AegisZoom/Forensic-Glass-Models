# Forensic Glass Classification: A Data Modelling Project

## COSC2670: Practical Data Science with Python

### Grade: 100%

## Introduction

This repository contains my work for the second assignment of COSC2670 in my Graduate Diploma of Data Science. 
The assessment was worth 30% of the final grade, and involved using a public data set to build and evaluate
machine learning models. The objective was to simulate the traditinal steps of a data science project:

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
This page will provide a summary, but *report.pdf* contains a 12-page report of all procedures taken to executing this
project in great detail.

## Skills Used
- 💾 **Programming**:
Used Python 🐍 as the programming language, Jupyter Notebook as the IDE, and the NumPy, Pandas, Matplotlib, Seaborn, and Sklearn libraries. Programmed
the notebook to be scalable: it will still work if the forensic data is adjusted/updated.
- 🔮 **Data Modelling**:
Selected appropriate parameters for training k-Nearest Neighbours and Decision Tree clustering machine learning models using theoretical knowledge
and hill-climbing and automated procedures. Evaluated model effectiveness using confusion matrices, precision, recall, accuracy, and F1 scores.
- 📈 **Data Analysis**:
- Performed statistical measures to identify trends in variables. Measures included mean, median, standard deviation, confidence intervals, and
outlier classification. Performed univariate and multivariate analyses to find trends and relationships in data.
- 📊 **Data Visualisation**:
Constructed histograms, pie charts, box plots, and scatter plots/matrices with trendlines as part of the exploration and analysis
of the data. Selected the appropriate visualisation methods based on the effectiveness of finding and commmunicating trends and relationships in the data.
- 🧼 **Data Cleaning**:
Performed checks for datatypes, outliers, missing values, and impossible values using masks. Applied multivariate outlier detection techniques.
- 📐 **Problem-Solving**:
Applied a wide variery of techniques to each stage of the project to account for as many possibilities as possible. Selected appropriate techniques using a mixture
of strong theoretical knowledge and a natural intuition based on real life limitations.
- 🔍 **Debugging/Attention to Detail**:
Developed techniques and intuition for identifying glitches that produced abnormal results or errors in various stages of the process. Identified opportunities to
gather further insight into data and model optimisation. Identified presence and implications of trends, relationships, and outliers in the data.
- 📝 **Written Communication**:
Submitted a 12-page report of the development of the project at all stages, including background research, data cleaning procedures, trends and relationships in the
data, and procedures to train, evaluate and optimise machine learning models.
- ⏰ **Time Management**:
Organised weekly schedules and deadlines for individual milestones with leeway for unexpected obstacles both related to and outside of the assessment, and prioritised developing the report alongside the programming portion of the assessment.
- 🔬 **Research**:
Extensively investigated techniques and solutions online to add advanced features to data visualisations. Performed background research in glass production to better understand
chemical properties of glass before beginning the project.
- ⚛️ **Physics/Chemistry**:
Used my extensive background knowledge in physics and chemistry to guide literature review, data cleaning and exploration stages to maximise model performance.

## Data Retrieval

As explained above, the purpose of this assessment was to create clustering models for forensic glass data to classify them based on their material properties.
The following public dataset was used:

German, B. (1987). *Glass Identification*. UCI Machine Learning Repository. [https://doi.org/10.24432/C5WW2P](https://doi.org/10.24432/C5WW2P)

It can more simply be accessed from here:
[https://archive.ics.uci.edu/dataset/42/glass+identification](https://archive.ics.uci.edu/dataset/42/glass+identification) 

The first five rows of the dataset is shown below:

![Dataset](https://github.com/AegisZoom/Forensic-Glass-Models/blob/Add-Files/Images/Dataset.PNG)

In short, the Refractive Index column measures the ability for the glass sample to bend light, and the columns contains the *%* character measure the proportion of oxides that contain that specific element. 
*Na %* for example specifies the proportion of Sodium Oxide formed on the surface of the glass sample. You can refer to the Periodic Table of Elements to see which letter corresponds to which chemical element.
Finally, the *Type of Glass* column simply states what object the glass shard is associated with. They are coded as numbers: a value of 1 means household window glass. For more details, see the report.

Therefore, the objective of the assessment is to construct machine learning models that predict the *Type of Glass* value using the *Refractive Index* and *%* columns.

## Data Cleaning

The following procedures were applied to check for data quality. Generously, the dataset was already cleaned but it was worthwhile to perform these operations for certainty.

- **Datatypes**: Checked that each variable was assigned the correct data type. This was true.

## Data Exploration Examples

A large number of visualisations were constructed to explore trends and relationships in the data. Only a few will be listed here, but the report and especially the Jupyter Notebook feature more data visualisations.

### Example 1: 
