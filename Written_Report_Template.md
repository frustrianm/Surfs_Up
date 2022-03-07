# Surf's Up with Advanced Data Storage and Retrieval - FRM'S Tec Data Bootcamp Challenge 9

## Overview of statistical analysis
After the analysis performed with W.Avy through Oahu's conditions to become a successfull business spot for the surf and ice cream shop, we want to make sure that such shop could survive the stational changes and deliver a constant and year round income. We will proceed to make another analysis to gather information of the opposite months of summer and winter to provide W. Avy with a concrete answer on whether the shop will suffer due to extremely different tempreature conditions, or will the shop thrive no matter the season.


## Results
- June Temperatures
```
# 1. Import the sqlalchemy extract function.
from sqlalchemy import extract

# 2. Write a query that filters the Measurement table to retrieve the temperatures for the month of June. 
june_results = []

june_results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==6)

#  3. Convert the June temperatures to a list.
june_results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==6).all()

# 4. Create a DataFrame from the list of temperatures for the month of June. 
june_df=pd.DataFrame(june_results, columns=['date','June Temps'])

# 5. Calculate and print out the summary statistics for the June temperature DataFrame.
june_df.describe()
```
  ![June Temps](https://user-images.githubusercontent.com/96660344/156980172-5e4d47b9-1706-43d5-b3a8-c6fb78642353.png)


- December Temperatures
```
# 6. Write a query that filters the Measurement table to retrieve the temperatures for the month of December.
dec_results = []

dec_results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==12)

# 7. Convert the December temperatures to a list.
dec_results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==12).all()

# 8. Create a DataFrame from the list of temperatures for the month of December. 
dec_df=pd.DataFrame(dec_results, columns=['date','December Temps'])

# 9. Calculate and print out the summary statistics for the Decemeber temperature DataFrame.
dec_df.describe()
```
  ![December Temps](https://user-images.githubusercontent.com/96660344/156980199-94077725-189f-4e8a-a944-26e5308f79ad.png)

- Main Insights
  -  Standard deviation account to 0.5 between both months.
  -  Maximum temperatures for both months only vary for 2°.
  -  Less data entries on month December, but due to the slight differente in standard deviation we can assume that december entries are correctly representing the complete data set.


## Summary
- On its maximum temperatues both months present almost no changes, but in minimum temperatue conditions a change of 8° is presented, meaning december (winther month) is cooler and further financial analysis is needed to be performed, since ice cream and surfing matters won't be as successfull in winter as in summer due to this temperature drop.

- Additional Query 1

- Additional Query 2
