# read-12

## Pandas 
is a game-changer for data science and analytics, particularly if you came to Python because you were searching for something more powerful than Excel and VBA. Pandas uses fast, flexible, and expressive data structures designed to make working with relational or labeled data both easy and intuitive.

* Let’s start:
``` import pandas as pd ```
* Reading data
``` titanic = pd.read_csv("data/titanic.csv")```
* select specific columns from Dataframe
ex:
```
adult_names = titanic.loc[titanic["Age"] > 35, "Name"]
 adult_names.head()
 ```
**There are multiple rules to deal with data in panada just try to have a documentation and by practising, you will memorize them.
**REMEMBER**

- Getting data in to pandas from many different file formats or data sources is supported by read_* functions.

- Exporting data out of pandas is provided by different to_*methods.

- The head/tail/info methods and the dtypes attribute are convenient for a first check.

- When selecting subsets of data, square brackets [] are used.

- Inside these brackets, you can use a single column/row label, a list of column/row labels, a slice of labels, a conditional expression or a colon.

- Select specific rows and/or columns using loc when using the row and column names

- Select specific rows and/or columns using iloc when using the positions in the table

- You can assign new values to a selection based on loc/iloc.
Aggregation statistics can be calculated on entire columns or rows

- groupby provides the power of the split-apply-combine pattern

- value_counts is a convenient shortcut to count the number of entries in each category of a variable

-Sorting by one or more columns is supported by sort_values

- The pivot function is purely restructuring of the data, pivot_table supports aggregations

- The reverse of pivot (long to wide format) is melt (wide to long format)



 