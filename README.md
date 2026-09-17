# ECE-2112-PA4
---
**Made by: Arabelle L. Ronquillo | 2ECE-D**

The content of this repository contains the Programming Assignment 4 for our course "Advanced Computer Programming," this A.Y. 2026-2027. This project covers three Python problems pertaining to Module 4 - Data Wrangling and Visualization.

---
# **Importing Pandas and Matplotlib**
```python
import pandas as pd
```
- Imports the Pandas Library and gives it the alias `pd`.
- This allows the use of Pandas functions like `pd.read_csv`, `iloc`, `loc`, etc.
```python
import matplotlib.pyplot as plt
```
- Imports Matplotlib and gives it the alias `plt`.
- This allows visualization such as `bar charts` and `subplots`.
---
#**Loading the Dataset**
```python
df = pd.read_excel('board2.xlsx')
df
```
- Loads the dataset `board.xlsx` into a DataFrame named `df`.
---
#**Computing the Average**
```python
df['Average'] = (df['Math']+df['GEAS']+df['Electronics']+df['Communication'])/4
df
```
- Creates a new column `Average` by computing the mean of the four exam subjects.
---
# **A. VISAYAS COMMUNICATION DATAFRAME**
```python
VisComm = df[(df['Hometown']=='Visayas') & (df['Track']=='Communication')][
    ['Name', 'Gender', 'Math', 'Electronics', 'Average']
    ]
print('Number of Rows: ', len(VisComm))
VisComm
```
- Filters students with `Hometown = Visayas` and `Track = Communication`.
- Keeps only the columns `Name`, `Gender`, `Math`, `Electronics`, and `Average`.
---
# **B. VISAYAS FEMALE DATAFRAME**
```python
VisFemale = df[(df['Hometown']=='Visayas') & (df['Gender']=='Female')][
    ['Name', 'Track', 'GEAS', 'Electronics', 'Average']
    ]
VisFemale
```
- Filters students with `Hometown = Visayas` and `Gender = Female`.
- Keeps only the columns `Name`, `Track`, `GEAS`, `Electronics`, and `Average`.
```python
VisFemale60 = VisFemale[VisFemale['Average']>=60]
VisFemale60
```
- Displays only the rows of VisFemale whose Average is at least 60.
---
# **C. CATEGORY-AVERAGE VISUALIZATION**
```python
Average_Track = df.pivot_table(index='Track', values = 'Average').reset_index()
Average_Track
```
```python
Average_Gender = df.pivot_table(index='Gender', values = 'Average').reset_index()
Average_Gender
```
```python
Average_Hometown = df.pivot_table(index='Hometown', values = 'Average').reset_index()
Average_Hometown
```
- Uses `pivot_table` to compute the average scores grouped by `Track`, `Gender`, and `Hometown`.
```python
plt.figure(figsize=(15,4))

plt.subplot(1,3,1)
plt.bar(Average_Track['Track'], Average_Track['Average'])
plt.title('Average by Track')
plt.xlabel('Track')
plt.ylabel('Average')

plt.subplot(1,3,2)
plt.bar(Average_Gender['Gender'], Average_Gender['Average'])
plt.xlabel('Gender')
plt.ylabel('Average')
plt.title('Average by Gender')

plt.subplot(1,3,3)
plt.bar(Average_Hometown['Hometown'], Average_Hometown['Average'])
plt.xlabel('Hometown')
plt.ylabel('Average')
plt.title('Average by Hometown')

plt.tight_layout()
```
- Creates one figure that contains three bar charts, which are `Average by Track`, `Average by Gender`, and `Average by Hometown`.
```python
print("Track with highest mean Average:", Average_Track.idxmax(), "\n")
print("Gender with highest mean Average:", Average_Gender.idxmax(), "\n")
print("Hometown with highest mean Average:", Average_Hometown.idxmax(), "\n")
```
- Prints concise statements identifying the category with the highest sample mean for each feature.
---

Thank you for reading!

To see the main Python program for Programming Assignment, click this [link](https://github.com/araronquillo/ECE-2112-PA4.git)  and download. Open on Jupyter Notebook, then run all cells.
