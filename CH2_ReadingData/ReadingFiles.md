# Reading Files

This chapter describes reading data from various sources e.g. CSV, Tab Seperated, Databases and Internet. We will dive in examples for each category in Python languages.

## Reading CSV:Comma Seperated Values files

Comma seperated files are still one of the most used data transfer format around the globe due to its ease and availability under various system. CSV format is used for structural data where each observation is defined in rows while each attribute is defined in columns which are seperated by commas.

The sample data we used here is of CSV file available at (the sample data is IRIS data set available from [iris download page](https://osdn.net/projects/sfnet_irisdss/downloads/IRIS.csv/))


1. **Reading the CSV file using Python code, we can use `read_csv()` to read it into a DataFrame.**


```python
#import pandas library
import pandas as pd

#use pandas read_csv function to read the file
df = pd.read_csv('C:\\Users\\Azhar Husain\\Downloads\\iris_dataset.csv')

#using head function of pandas data frame to review top rows
df.head()
```

||SrNo|Sepal.Length|Sepal.Width|Petal.Length|Petal.Width|Species|
|---|---|------------|-----------|------------|-----------|-------|
|0|	1|	5.1|	3.5|	1.4|	0.2|	setosa|
|1|	2|	4.9|	3.0|	1.4|	0.2|	setosa|
|2|	3|	4.7|	3.2|	1.3|	0.2|	setosa|
|3|	4|	4.6|	3.1|	1.5|	0.2|	setosa|
|4|	5|	5.0|	3.6|	1.4|	0.2|	setosa|


Reading data without header line we can use header attribute in `read_csv()` function i.e setting `header=None`.

```python
#import pandas library
import pandas as pd

#use pandas read_csv function to read the file
df = pd.read_csv('C:\\Users\\Azhar Husain\\Downloads\\iris_dataset_without_header.csv', header=None)

#using head function of pandas data frame to review top rows
df.head()
```
||0|1|2|3|4|5|
|---|---|---|---|---|---|---|
|0|1|5.1|3.5|1.4|0.2|setosa|
|1|2|4.9|3|1.4|0.2|setosa|
|2|3|4.7|3.2|1.3|0.2|setosa|
|3|4|4.6|3.1|1.5|0.2|setosa|
|4|5|5|3.6|1.4|0.2|setosa|

Using `header=None` auto generates the data column numbers. Till now we are using `read_csv()` function to read comma seperated files, but there may be scenario when comma may not be the default seperator due to data or business requirements. So Python provides easy solution for such requirement.

2. **Reading non comma seperated files using `read_table()`**

```python
#import pandas library
import pandas as pd

#use pandas read_table function to read the file
df = pd.read_table('C:\\Users\\Azhar Husain\\Downloads\\iris_dataset_pipe_sep.txt', sep='|')

#using head function of pandas data frame to review top rows
df.head()
```
The `sep='|'` attribute is used defined the seperator in file, in our example it is pipe(|) delimiter.

||SrNo|Sepal.Length|Sepal.Width|Petal.Length|Petal.Width|Species|
|---|----|------------|-----------|------------|-----------|-------|
|0|	1|	5.1|	3.5|	1.4|	0.2|	setosa|
|1|	2|	4.9|	3.0|	1.4|	0.2|	setosa|
|2|	3|	4.7|	3.2|	1.3|	0.2|	setosa|
|3|	4|	4.6|	3.1|	1.5|	0.2|	setosa|
|4|	5|	5.0|	3.6|	1.4|	0.2|	setosa|


3. **Read text file without header using custom columns names**

Earlier above we have seen example of using `header=None` where python generates some default column titles as number. Still it is highly recommended to use well defined column names in data analysis for better reproducible research documents and analysis outcome. 

In python this can be done using `names=` attribute which define column names for each column, example of same code is given below.

```python
#import pandas library
import pandas as pd

#define column names array
column_names=['SrNo','Sepal.Length','Sepal.Width','Petal.Length','Petal.Width','Species']

#use pandas read_csv function to read the file
df = pd.read_csv('C:\\Users\\Azhar Husain\\Downloads\\iris_dataset_without_header.csv', names = column_names,header=None)

#using head function of pandas data frame to review top rows
df.head()
```
We have not displayed output here, as it is similar to the output in previous example.

4. **Readign data for sample rows only**

This technique of selecting sample records may not be very fascinating at start, but it is a handy tool to have a look at your data when data is very large. To accomplish this task we can use attribute `nrows=` in  `read_csv() or read_table()` method.

```python
#import pandas library
import pandas as pd

#use pandas read_csv function to read the file
df = pd.read_csv('C:\\Users\\Azhar Husain\\Downloads\\iris_dataset.csv', nrows=10)

#printing the whole data set
df
```
||SrNo|Sepal.Length|Sepal.Width|Petal.Length|Petal.Width|Species|
|---|---|---|---|---|---|---|
|0|1|5.1|3.5|1.4|0.2|setosa|
|1|2|4.9|3|1.4|0.2|setosa|
|2|3|4.7|3.2|1.3|0.2|setosa|
|3|4|4.6|3.1|1.5|0.2|setosa|
|4|5|5|3.6|1.4|0.2|setosa|
|5|6|5.4|3.9|1.7|0.4|setosa|
|6|7|4.6|3.4|1.4|0.3|setosa|
|7|8|5|3.4|1.5|0.2|setosa|
|8|9|4.4|2.9|1.4|0.2|setosa|
|9|10|4.9|3.1|1.5|0.1|setosa|


## Reading Excel Files

We have seen above sample of reading csv or text file using `read_csv and read_table` function of pandas. Sometimes it become more viable for user to share the data in spreadsheet format, for which best available option is Microsoft Excel. So even sharing of data in excel, due to size limitation and involved complexity is not very handy and practical but still it cant be ignored.

So python pandas provide very efficient mechanism to deal with excel files where data is provided in various sheets under single file. Here below we will explain basic examples of dealing with excel file but we highly recommend to go through documentation of this function.

The data used in this is example is available at [tableau sample data](https://community.tableau.com/docs/DOC-1236).

1. **Reading data from excel file where data is located in single sheet**


```python
import pandas as pd

#read data from excel file where Users is the sheet name in excel workbook
df= pd.ExcelFile('C:\\Users\\Azhar Husain\\Desktop\\data\\tableau_SuperstoreSales.xls').parse('Users')

df.head()
```

Another way of doing the same thing through `read_excel` method is.

```python
import pandas as pd

frame= pd.read_excel('C:\\Users\\Azhar Husain\\Desktop\\data\\tableau_SuperstoreSales.xls', sheetname='Users')

frame.head()
```

2. **Reading data from multiple sheets at once**

Before getting through this let us explore the requirements we have, this example is based on concept that you have common structured data which is divided into multiple sheets in a workbook. And we need to select data from all the sheets and then combine them together to form a single data set.

This example can not be handled using any single function call. Hence we have to manually create a code block or function if necessary for the same. Let us see the steps needed for this task to be accomplished.

a. Select excel file
b. Get the sheet names that are available in that Excel file
c. Read data from each excel sheet and store it in a data frame
d. Combine all data frames, to make a consolidated data frame.

So lets see our code first, dont be intimidated by it as we will dive in line by line after the code below.

```python
import pandas as pd

#final dataframe varibale declaration
finalData= pd.DataFrame()

#read excel file in python variable
xlfile= pd.ExcelFile('C:\\Users\\Azhar Husain\\Desktop\\data\\multisheet_data.xlsx')


# description of this code block is given the documents below
df = {sheet_name: xlfile.parse(sheet_name)
         for sheet_name in xlfile.sheet_names}

#combine all the data sets into one
finalData=pd.concat(df, ignore_index=True)

#count final rows in our case output was 572 rows
len(finalData.index)
```

## Code Explanation

1. `import pandas as pd`: Quite simple just importing our pandas library for later use in code.
2. `finalData= pd.DataFrame()` : Declaring an empty data frame to hold final combined result.
3. `xlfile= pd.ExcelFile('C:\\U...')` : Reading the excel file object in a variable
4. `df = {sheet_name: xlfile.parse(sheet_name) for sheet_name in xlfile.sheet_names}`

    To understand this code let us understand python collection. Python collection are classes to store multiple       values in a single object or variable. The most basic collection is array where you store data in a kind of        list like below
    
    
    `array_variable=['Item1','Item2','Item3']` : this varibale hold three items i.e. Item1, Item2 & Item3.
    
    Similarly python provide dictionary collection which is based on key value pair system
    
    `dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}` : this dictionary contain three items Name, Age & Class
    whose values are Zara, 7 and First respectively. Where strings before colon(:) are keys and after colon are its     values. 
    
    So in our code example `{sheet_name : ...}` sheet_name is key while anything to the right of colon is its          value.
    
    So our code execution logic will be like 
    
        1. `xlfile.sheet_names` will return array of sheet in our workbook i.e ['Sheet1','Sheet2','Sheet3']
        
        2. `for sheet_name in xlfile.sheet_names` will loop over sheet names array, so this loop will run thrice
        In first iteration it will make variable sheet_name='Sheet1', in second to 'Sheet2' and finally 'Sheet3'
        
        3. For each iteration `xlfile.parse(sheet_name)` will load data from excel workbook sheet (where excel sheet is the sheet stored in sheet_name variable) to a dataframe 
        
        4. The data frame loaded in previous step is assigned to collection with its key = sheet_name
        
     Finally after all iteration our result will be like 
     
     `{'Sheet1': dataframe1, 'Sheet2': dataframe2, 'Sheet3': dataframe3}` here values of keys are just descriptive and not original value. Originally a pandas data frame will reside in collection instead of dataframe1 and so on. 
     
     Then this collection is assigned to *df* variable
   
5. `finalData=pd.concat(df, ignore_index=True)` : This will append all the data one below the other and assign final result to finalData variable

6. `len(finalData.index)` : every pandas data frame has an index arrange to its each row. So here we can calculate length of index column to get total rows. *We are not using count function as count ignores null values in column.*