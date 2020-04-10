## Course
Datacamp: https://campus.datacamp.com/courses/data-cleaning-in-python

## Imports
Use the following imports to ensure executability of all commands
`import datetime as dt`
`import pandas as pd`

### How to clean your data
#### Data type
##### Check the data type.
Print data types
``

Convert to str, int or categorical, date accordingly.
`data[column_new] = data['column'].astype('category')`
`data[column_new] = data['column'].astype('int')`
`data[column_new] = data['column'].astype('str')`
`data[column_new] = data['column'].astype('datetime')`

Check the data type afterwards
`assert data['column'].dtype == 'int'`

##### Trimming
Trim your data. Example: '10 minutes'
`data[column_new] = data[column].str.strip('minutes')`

##### Out of Range 
Check if data range makes sense. Example: 'Death date in the future', 'Movie ratet at 11 (scale 1-10)'

Drop (Small amount of false entries)
`data = data[data['rating'] <= 5]`
`assert data['rating'].max() <= 5`

Setting custom min and max. Example: If rating above 5 set 5 instead
`data.loc[data['rating'] > 5, 'rating'] = 5`
`assert data['rating'].max() <= 5 #no ouput = true`
