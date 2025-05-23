# freeCodeCamp_exercise1
My personal solutions to freeCodeCamp Pandas exercises

![rmotr](https://user-images.githubusercontent.com/7065401/52071918-bda15380-2562-11e9-828c-7f95297e4a82.png)
<hr style="margin-bottom: 40px;">

<img src="https://user-images.githubusercontent.com/7065401/58563302-42466a80-8201-11e9-9948-b3e9f88a5662.jpg"
    style="width:400px; float: right; margin: 0 40px 40px 40px;"></img>

# Exercises
## Bike store sales
![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)

## Hands on! 
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

%matplotlib inline
sales = pd.read_csv(
    'data/sales_data.csv',
    parse_dates=['Date'])
sales.head()
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### What's the mean of `Customers_Age`?
# your code goes here

Why don't you try with `.mean()`
sales['Customer_Age'].mean()
Go ahead and show a <b>density (KDE)</b> and a <b>box plot</b> with the `Customer_Age` data:
# your code goes here

sales['Customer_Age'].plot(kind='kde', figsize=(14,6))
sales['Customer_Age'].plot(kind='box', vert=False, figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### What's the mean of `Order_Quantity`?
# your code goes here

sales['Order_Quantity'].mean()
Go ahead and show a <b>histogram</b> and a <b>box plot</b> with the `Order_Quantity` data:
# your code goes here

sales['Order_Quantity'].plot(kind='hist', bins=30, figsize=(14,6))
sales['Order_Quantity'].plot(kind='box', vert=False, figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many sales per year do we have?
# your code goes here

sales['Year'].value_counts()
Go ahead and show a <b>pie plot</b> with the previous data:
# your code goes here

sales['Year'].value_counts().plot(kind='pie', figsize=(6,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many sales per month do we have?
# your code goes here

sales['Month'].value_counts()
Go ahead and show a <b>bar plot</b> with the previous data:
# your code goes here

sales['Month'].value_counts().plot(kind='bar', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Which country has the most sales `quantity of sales`?
# your code goes here

sales['Country'].value_counts().head(1)
sales['Country'].value_counts()
Go ahead and show a <b>bar plot</b> of the sales per country:
# your code goes here

sales['Country'].value_counts().plot(kind='bar', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Create a list of every product sold
# your code goes here

#sales.loc[:, 'Product'].unique()

sales['Product'].unique()
Create a **bar plot** showing the 10 most sold products (best sellers):
# your code goes here

sales['Product'].value_counts().head(10).plot(kind='bar', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Can you see any relationship between `Unit_Cost` and `Unit_Price`?

Show a <b>scatter plot</b> between both columns.
# your code goes here

sales.plot(kind='scatter', x='Unit_Cost', y='Unit_Price', figsize=(6,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Can you see any relationship between `Order_Quantity` and `Profit`?

Show a <b>scatter plot</b> between both columns.
# your code goes here

sales.plot(kind='scatter', x='Order_Quantity', y='Profit', figsize=(6,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Can you see any relationship between `Profit` per `Country`?

Show a grouped <b>box plot</b> per country with the profit values.
# your code goes here

sales[['Profit', 'Country']].boxplot(by='Country', figsize=(10,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Can you see any relationship between the `Customer_Age` per `Country`?

Show a grouped <b>box plot</b> per country with the customer age values.
# your code goes here

sales[['Customer_Age', 'Country']].boxplot(by='Country', figsize=(10,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Add and calculate a new `Calculated_Date` column

Use `Day`, `Month`, `Year` to create a `Date` column (`YYYY-MM-DD`).
# your code goes here

sales['Calculated_Date'] = sales[['Year', 'Month', 'Day']].apply(lambda x: '{}-{}-{}'.format(x[0], x[1], x[2]), axis=1)

sales['Calculated_Date'].head()
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Parse your `Calculated_Date` column into a datetime object
# your code goes here

sales['Calculated_Date'] = pd.to_datetime(sales['Calculated_Date'])

sales['Calculated_Date'].head()
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How did sales evolve through the years?

Show a <b>line plot</b> using `Calculated_Date` column as the x-axis and the count of sales as the y-axis.
# your code goes here

sales['Calculated_Date'].value_counts().plot(kind='line', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Increase 50 U$S revenue to every sale
# your code goes here

#sales['Revenue'] = sales['Revenue'] + 50

sales['Revenue'] += 50
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made in `Canada` or `France`?
# your code goes here

sales.loc[(sales['Country'] == 'Canada') | (sales['Country'] == 'France')].shape[0]
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many `Bike Racks` orders were made from Canada?
# your code goes here

sales.loc[(sales['Country'] == 'Canada') & (sales['Sub_Category'] == 'Bike Racks')].shape[0]
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made in each region (state) of France?
# your code goes here

france_states = sales.loc[sales['Country'] == 'France', 'State'].value_counts()

france_states
Go ahead and show a <b>bar plot</b> with the results:
# your code goes here

france_states.plot(kind='bar', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many sales were made per category?
# your code goes here

sales['Product_Category'].value_counts()
Go ahead and show a <b>pie plot</b> with the results:
# your code goes here

sales['Product_Category'].value_counts().plot(kind='pie', figsize=(6,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made per accessory sub-categories?
# your code goes here

accessories = sales.loc[sales['Product_Category'] == 'Accessories', 'Sub_Category'].value_counts()

accessories
Go ahead and show a <b>bar plot</b> with the results:
# your code goes here

accessories.plot(kind='bar', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made per bike sub-categories?
# your code goes here

bikes = sales.loc[sales['Product_Category'] == 'Bikes', 'Sub_Category'].value_counts()

bikes
Go ahead and show a <b>pie plot</b> with the results:
# your code goes here

bikes.plot(kind='pie', figsize=(6,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Which gender has the most amount of sales?
# your code goes here

sales['Customer_Gender'].value_counts()
sales['Customer_Gender'].value_counts().plot(kind='bar')
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many sales with more than 500 in `Revenue` were made by men?
# your code goes here

sales.loc[(sales['Customer_Gender'] == 'M') & (sales['Revenue'] == 500)].shape[0]
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Get the top-5 sales with the highest revenue
# your code goes here

sales.sort_values(['Revenue'], ascending=False).head(5)
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Get the sale with the highest revenue
# your code goes here

#sales.sort_values(['Revenue'], ascending=False).head(1)

cond = sales['Revenue'] == sales['Revenue'].max()

sales.loc[cond]
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### What is the mean `Order_Quantity` of orders with more than 10K in revenue?
# your code goes here

cond = sales['Revenue'] > 10_000

sales.loc[cond, 'Order_Quantity'].mean()
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### What is the mean `Order_Quantity` of orders with less than 10K in revenue?
# your code goes here

cond = sales['Revenue'] < 10_000

sales.loc[cond, 'Order_Quantity'].mean()
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made in May of 2016?
# your code goes here

cond = (sales['Year'] == 2016) & (sales['Month'] == 'May')

sales.loc[cond].shape[0]
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### How many orders were made between May and July of 2016?
# your code goes here

cond = (sales['Year'] == 2016) & (sales['Month'].isin(['May', 'June', 'July']))

sales.loc[cond].shape[0]
Show a grouped <b>box plot</b> per month with the profit values.
# your code goes here

profit_2016 = sales.loc[sales['Year'] == 2016, ['Profit', 'Month']]

profit_2016.boxplot(by='Month', figsize=(14,6))
![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

### Add 7.2% TAX on every sale `Unit_Price` within United States
# your code goes here

#sales.loc[sales['Country'] == 'United States', 'Unit_Price'] = sales.loc[sales['Country'] == 'United States', 'Unit_Price'] * 1.072

sales.loc[sales['Country'] == 'United States', 'Unit_Price'] *= 1.072
![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)
