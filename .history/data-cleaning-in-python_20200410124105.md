## Course
Datacamp: https://campus.datacamp.com/courses/data-cleaning-in-python

### How to clean your data
#### Data type
##### Check the data type. 
Convert to str, int or categorical, date accordingly.
`data[column_new] = data['column'].astype('category')`
`data[column_new] = data['column'].astype('int')`
`data[column_new] = data['column'].astype('str')`

Check the data type afterwards
`assert data['column'].dtype == 'int'`

##### Trimming
Trim your data. Example: '10 minutes'
`data[column_new] = data[column].str.strip('minutes')`

##### Out of Range 
Check if data range makes sense. Example: 'Death date in the future', 'Movie ratet at 11 (scale 1-10)'

Drop (Small amount of false entries)
`data[data['column'] > 5]`
Seeting custom min and max