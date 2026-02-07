os module
os is a built-in Python module that lets you interact with your operating system.
You can do things like:
List files in a folder
Check your current working directory
Create folders, delete files, etc.
2️⃣ os.listdir()
listdir() is a function in the os module.
It lists all files and folders in a directory.
Example:
import os

# List files in the current folder
print(os.listdir())  
Output might be:
['.config', 'raw_sales_data.csv', 'sample_data']
✅ This tells you exactly what files are in your workspace.
Optional: List files in a specific folder
print(os.listdir('/content'))
/content is the default folder in Colab where files are stored.
3️⃣ Why it’s useful
Before you try to load a CSV, it’s smart to check the filename and folder:
import os
print(os.listdir('/content'))  # Make sure 'raw_sales_data.csv' is there
This prevents FileNotFoundError when using pd.read_csv().
###
df dataframe
After head(), always run info(). You’ll immediately know:
Which columns have missing values (NaN)
Which are numeric vs text
How many rows you have

3️⃣ What we learn about your data
Numeric columns:
QUANTITYORDERED, PRICEEACH, SALES, MSRP, QTR_ID, MONTH_ID, YEAR_ID
Can be used for math, calculations, outlier detection
Text columns (object):
CUSTOMERNAME, CITY, STATE, COUNTRY, PRODUCTLINE, etc.
Cannot do math on them, but useful for filtering, grouping, categories
Columns with missing values (important for cleaning):
ADDRESSLINE2 → most values missing
STATE → only 1337/2823 filled
POSTALCODE → some missing
TERRITORY → some missing
4️⃣ Next step in screening / cleaning
For numeric columns → we can fill missing values with median (if any)
For text columns → we can drop rows with missing values or fill with placeholder
Remove duplicates → if any
✅ Summary: df.info() gives you a quick health check of your dataset:
How many rows / columns
Which columns are numeric vs text
Where the missing values are
If you want, we can move to the next function df.describe() to see summary statistics for numeric columns, which is the first step in identifying outliers.
###
💡 Today’s Python + Pandas Learning Summary
1️⃣ Load your CSV
Use Pandas to load your CSV file into a DataFrame:
import pandas as pd
df = pd.read_csv("raw_sales_data.csv", encoding='latin1')
df (or any variable name you like) now represents your dataset in memory.
2️⃣ Inspect your data — first view
df.head() → shows the first 5 rows and all columns (or truncated if too many):
df.head()
Useful to quickly see columns, data types, sample values.
3️⃣ Inspect data structure
df.info() → shows all columns, data types, non-null counts, and number of rows:
df.info()
Helps you identify:
Numeric vs text columns
Missing values (NaN)
Total rows and columns
4️⃣ Understand rows vs columns
Rows → horizontal entries (each order line in your dataset)
Columns → vertical fields (ORDERNUMBER, SALES, CITY, etc.)
Column indexing in df.info() starts at 0
df.shape  # Shows total rows x columns
df.columns  # List all column names
5️⃣ Missing values
From df.info() you can see which columns are incomplete:
STATE → 1337/2823 non-null
ADDRESSLINE2 → 302/2823 non-null
POSTALCODE, TERRITORY → partially missing
This is important for data cleaning.
6️⃣ Column types
Numeric → can do math / screening:
QUANTITYORDERED, PRICEEACH, SALES, MSRP, QTR_ID, MONTH_ID, YEAR_ID
Text (object) → for filtering / categories:
CUSTOMERNAME, CITY, STATE, COUNTRY, PRODUCTLINE, etc.
7️⃣ Key Points
df.head() → first glance at data
df.info() → structural overview + missing values
Columns are numbered from 0
Rows × columns can be checked with df.shape
Missing values must be handled before analysis
✅ Next Steps for Practice
Use df.describe() to get summary statistics of numeric columns
Identify outliers in numeric columns (SALES, PRICEEACH, etc.)
Handle missing values and duplicates
Compute new columns (Revenue, profit, etc.)
Visualize data with plots (matplotlib)
