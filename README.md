# python_data_analysis

There are some examples using python to analyze data.


## Example 1
Requirement: find the name of students with the top 3 grades for each course

```
import pandas as pd
grade_results = pd.read_csv('grade_results.csv')

# Sort the DataFrame by course_name and grade in descending order
sorted_grades = grade_results.sort_values(by=['course_name', 'grade'], ascending=False)

# Group the sorted grades by course_name and retrieve the top 3 students for each group
top_students = sorted_grades.groupby('course_name').head(3)

# Print the Student_ID of students with top 3 grades for each Course_name
print(top_students[['Course_name', 'Student_ID']])
```


## Example 2
Requirement: left join tables A and B using ClientID

```
import pandas as pd

# Merge A and B using a left join based on the ClientID column
merged_table = pd.merge(A, B, left_on='ClientID', right_on='ClientID', how='left')

# Print the merged table
print(merged_table)
```

## Example 3
Requirement:
1) Standardise values in the Species column with all uppercase; 
2) filter dataset to only include rows with ‘SETOSA’ species; 
3) filter the dataset to only include numeric variables ;
4) add a new variable named Total.Length which is the sum of Sepal.Length and Petal.Length 

```
import pandas as pd
#  Standardize values in Species column with all uppercase
iris['Species'] = iris['Species'].str.upper()

# Filter dataset to only include rows with 'SETOSA' species
setosa = iris[iris['Species'] == 'SETOSA']

# Filter dataset to only include numeric variables
setosa_numeric = setosa.select_dtypes(include='number')

#  Add a new variable named Total.Length which is the sum of Sepal.Length and Petal.Length
setosa_numeric['Total.Length'] = setosa_numeric['Sepal.Length'] + setosa_numeric['Petal.Length']
```

## Example 4

Requirement: 
1. generate a data frame
2. add a new column “three” which is a series of [20, 40, 60] with index ['a', 'b', 'c'].
3. add a new column “four” which is the sum of “one” and “three”


```
# generate a data frame
import pandas as pd      
info = {'one': pd.Series([1, 2, 3, 4, 5], index=['a', 'b', 'c', 'd', 'e']),    
             'two': pd.Series([1, 2, 3, 4, 5, 6], index=['a', 'b', 'c', 'd', 'e', 'f'])}    
   
info = pd.DataFrame(info)

# Add a new column “three”
three_series = pd.Series([20, 40, 60], index=['a', 'b', 'c'])
info['three'] = three_series

# Add a new column “four”
info['four'] = info['one'] + info['three']

```


## Example 5

Requirement:
1. Create a data frame which has 5 rows and 3 columns, filled with random numbers
2. Column names are 'A', 'B' and 'C'.
3. Output the row for which the absolute value of column 'C' is the maximum

```
import pandas as pd
# Create a data frame
df = pandas.DataFrame(np.random.randn(5,3),columns=['A','B','C'])

# find the maximum absolute value in column ' '
max_abs_row = df.loc[abs(df['C']).idxmax()]

```



## lesson learned
1. These examples show some basic operations using Python to analyze data such as merging tables and finding the maximum in categories.
2. Apart from that, we can create a data frame and filter the dataset and add columns using some operation to clearly show features of the dataset.

