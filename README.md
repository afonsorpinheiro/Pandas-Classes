# Pandas-Classes
Pandas classes prep works

'The Replit code of the session on Pandas is below'

import pandas as pd

listings_df = pd.read_csv('AB_NYC_2019.csv')

print(listings_df.shape)
print(listings_df.columns)
print(listings_df.dtypes)
print(listings_df.head())
print(listings_df.tail())

'Ways to check the data is clean - it tells us how many rows have a blank value'

print(listings_df.isnull().sum())

'We can drop some columns we find not relevant for our analysis'

columns_to_drop = ['id','host_name','last_review']

listings_df.drop(columns_to_drop,axis = "columns", inplace = True)

print(listings_df.head())

'some of the columns that have float values have NaN (Not a Number) in their columns and this means the operators such as sum, mean etc wont work. We need to fix this by using the fillna function and replace the NaN by 0'

listings_df.fillna({'reviews_per_month':0},inplace = True)

print(listings_df.head())

'How to select any columns from your dataset'

print(listings_df[['name','price']])

'Or how to select rows using index, looking into the firts 8 lines'

print(listings_df[0:8][['name','price']]

'Boolean indexing'

print(listings_df['price'] < 100)

'How to keep only the ones below 100'

print(listings_df[listings_df['price'] < 100])

'Exploratory Data Analysis. Lets now use some exercises to check the results'
'1. What are the 10 most reviewed listings'

print(listings_df.nlargest(10,'number_of_reviews'))


'2. What are the new york neighborhood groups with listings'

print(listings_df['neighbourhood_group'].unique())
print(listings_df['room_type'].unique())

'3. How many listings per neighborhood group'

print(listings_df['neighbourhood_group'].value_counts())

'4. What are the top 10 neighborhoods with Airbnb listings'

print(listings_df['neighbourhood'].value_counts().head(10))

'5. Add a dotplot with Matlib library which is embedded in pandas'

print(listings_df['neighbourhood'].value_counts().head(10).plot(kind='bar'))
plt.show()
