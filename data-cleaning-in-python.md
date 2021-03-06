## Course
Datacamp: https://campus.datacamp.com/courses/data-cleaning-in-python

### Imports
Use the following imports to ensure executability of all commands\
`import datetime as dt`\
`import pandas as pd`

### How to clean your data
#### Data type
Print data types\
`data.dtypes`

Convert to str, int or categorical, date accordingly.\
`data[column_new] = data['column'].astype('category')`\
`data[column_new] = data['column'].astype('int')`\
`data[column_new] = data['column'].astype('str')`\
`data[column_new] = pd.to_datetime(data['column'])`

Check the data type afterwards\
`assert data['column'].dtype == 'int'`
`assert data['column'].dtype == 'datetime64[ns]'`

#### Trimming
Trim your data. Example: '10 minutes'\
`data[column_new] = data[column].str.strip('minutes')`

#### Range 
Check if data range makes sense. Example: 'Death date in the future', 'Movie ratet at 11 (scale 1-10)'

Drop (Small amount of false entries)\
`data = data[data['rating'] <= 5]`\
`assert data['rating'].max() <= 5`

`today = dt.date.today()`\
`data = data[data['date'] < today]`

Setting custom min and max. Example: If rating above 5 set 5 instead\
`data.loc[data['rating'] > 5, 'rating'] = 5`\
`assert data['rating'].max() <= 5 #no ouput = true`

`today = dt.date.today()`\
`data.loc[data['date'] > today, 'date'] = today`\
`assert data['date'].max().date() <= today #no ouput = true`

#### Duplicates
All values for each column are the same or just one is different. \
Example: 'Name, Address are the same but the eye color is different'\
`data.head()`\
`duplicates = data.duplicated(subset = ['column1', 'column2', 'column3'], keep = False)`\
`data[duplicates].sort_values(by = 'column1')`

Drop if all values are the same\
`data.drop_duplicates(inplace = True)`

Group if most values are the same\
`summaries = {'column1': 'max', 'column2': 'mean', 'column3': 'min'}`\
`data = data.groupby(by = ['column1', 'column2', 'column3']).agg(summaries).reset_index()`

Check if duplicates removed (should not return anything)\
`duplicates = data.duplicated(subset = ['column1', 'column2', 'column3'], keep = False)`\
`data[duplicates].sort_values(by = 'column1')`
