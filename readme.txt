Student Name: Peter Ljubisic
Student ID: s4081442
Subject: Practical Data Science with Python
Assessment: Assignment 2
Data Set: Glass Identification

Instructions:

The Assignment2.ipynb file in this zip file contains the code that performed the analysis and modelling of the dataset specified above. To execute the code properly, there are a number of conditions that need to be followed:

- Copy the glass.csv file in the zip file to the working directory for Jupyter Notebook on this computer.

- Alternatively, the user can access to the glass identification data set from: https://archive.ics.uci.edu/dataset/42/glass+identification
The data is imported as a zip file named glass+identification.zip that contains four files. The files need to be extracted. The file of interest is glass.data which contains the data set used. Use whatever means (opening in Microsoft Excel, manually renaming .data to .csv, etc.) to change the file to a csv file named glass.csv. Save or copy glass.csv to the working directory for Jupyter Notebook on the computer.

- When running the code, there are some limitations to its modularity. Namely, the original dataset does not contain any values of 4 (float-processed vehicle glass) in the last column (the type of glass). It is critical for this code to work that no samples with a value of 4 in that column are added. By extension, the other values 1-7 in that column must have at least two corresponding samples, or the stratified train/test split algorithm won't work. The data types of each column must not be changed either, or any new columns added.

- When opening Assignment2.ipynb on Jupyter Notebook, simply restart the kernel and run all cells at once. The code should not have any issues if the above steps have been followed.