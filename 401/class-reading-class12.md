# **Reading Notes: Pandas**

---
---
---

## Why are these reading important?

```
Pandas is a premiere tool for data analysis. It can help manage, clean and analyze your data.
```

---

## [**Pandas in 10:**](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)

---

## [**Pandas - Getting Started:**](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)

---

## [**Corey Schafer - Pandas Tutorials:**](https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS)

---

## [**What is Pandas:**](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=391s)

---

## [**Master Pandas:**](https://towardsdatascience.com/be-a-more-efficient-data-scientist-today-master-pandas-with-this-guide-ea362d27386)

---

## **Reading Questions:**

1. Prompt: Explain the purpose and basic functionality of the Pandas library. What are some common operations that can be performed on data using Pandas, and how do they contribute to data analysis and manipulation?

  Solution: Panda's is an open source data handling and analysis library. It enables operations from data import, data management, analysis, refactoring, plotting, and data export; to name a few. Below are some of my panda's methods/function notes along with what they do.

```python
# how to make dataframe
dict0={"calories":[420,380,390],"duration":[50,40,45]}
df0 = pd.DataFrame(dict0,index=['day1','day2','day3'], columns=list("ABCD"))
#OR
df1 = pd.DataFrame({"A":np.array(),"B":pd.Series()})

# how to import data from file into dataframe
df_csv = pd.read_csv('data.csv')
df_json = pd.read_json('data.json')
#write dataframe to csv
df0.to_csv('file_name.csv')

#how to visualize portion or aspect of dataframe
df0.head() #access head to display default 5rows
df0.tail() #same but tail
df0.info() #access summary
df0.corr() #returns table with correlation 
df0.describe() #create stats description of each series
df0.dtypes #find dtypes of each series


#sort by column
df0.sort_values(by="column",ascending=True)

#select by column name
df0["column"]
#slice by index or index values
df0[0:3] or df0['2013':'2014']
#select single value equal to
df0.loc[dates[0],'column']
#slice with index values, inclusive
df0.loc['2013':'2014',["column1","column2"]]
#select by index
df0.iloc[3,:]
#slice by indices
df0.iloc[3:5,0:2]

#with square brackets and expressions
df0[df0["column"]>2]
df0[df0["column"].notna()]
df0[(df0["column1"] == 2) | (df0["column2"] == 3)]
#filter out cells, fill with NaN
df0[df0>2] 
#based on categories
df0[df0["column"].isin(["cat1","cat2"])]

#can concatenate with function from list
pieces = [df0[:3], df0[3:7], df0[7:]]
pd.concat(pieces axis=0)
#can merge dataframes with shared key
pd.merge(left, right, how="left", on="key")

#can perform calculations after grouping
df0.group_by("column1")
df0.group_by(["column1","column2"])
#can count the number within each group
df0.group_by('column1')['column1'].count()

#convert all elements of a column to lowercase
df0["column"].str.lower()
#split string 
df0['column'].str.split("_").str.get(0)
#conditional if string contains
df0[df0['column'].str.contains('target')]
#filter based on string length
df0[df0['column'].str.len()<10]
#replace strings 
df0['column']=df0['column'].replace({'male':'m','female':'f'})

#perform calculations and assign new values
df0["col2"] = df0["col1"] / df0['col0']

#how to rename columns
df1 = df0.rename(columns={"old_name": "new_name"})
#how to rename columns with function
df1 = df0.rename(columns=str.lower)
```

1. Prompt: What are the primary data structures in Pandas, and how do they differ in terms of use cases?

  Solution: Panda's utilize Series which are kind of like lists and Dataframes which are composed of Series as 'columns' in a spreadsheet. In terms of uses, think of Series being organized by type/topic such as gender(think a column specifying gender). Where Dataframes organize multiple instances/rows that can contain data with each Series/column.

1. Prompt: Describe the process of loading a dataset into a Pandas DataFrame. What are some common file formats that can be used, and which Pandas functions are utilized to read these formats?

  Solution: The file types it can read are CSV, Excel, JSON, SQL, HTML, Parquet, HDF5, Feather, Msgpack, SAS, Stata, Clipboard, and Fixed-With Format(fwf). The common syntax is as follows. 

```python
pd.read_<insert_file_type>('file_name.format')
```

---

## **What I want to learn more about:**

1. Where to start? I could use some help on pivot tables, when and where to use them.

---
---
---