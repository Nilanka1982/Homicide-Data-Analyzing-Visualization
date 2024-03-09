# Homicide - Data Analyzing Visualization
### Project Overview

Purpose of This Data analysis project is to identyfing peak values of the variable , identifying any trned of the variables, comparisons of the factors under one variable( How many female and male involed to the victims).

### Data Sourse
Homicide data  set - From Kaggle

### Tool
- I used R programming here to Import , Manipulation, Cleaning, and Visualization

### Data Cleaning
1. Data Loading.
2. Investigating all varibles and identifying missing data and datas with wrong data type.
3. Handling Missing values.
4. Converting to the Correct Data Type. (Data Formatting)
5. Removing error Data with error data type.

   Data loading
   ```df <- read.csv('/kaggle/input/homicides/homicide-data.csv')```

   #### investigating
   
   ```head(df)```
   ![head](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/6e17f292-e1cf-424d-b8c3-97dc286c260d)

   ```summary(df)```

   
![summary](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/c7009f2e-de51-4413-bdb1-0e2d9cd344ad)

   ```cat("First 5 rows in the data Set", "\n")
      df[1:5,]
      cat("\n")
      cat("Last 5 rows in the data set", "\n")
      df[-(1:52174),]
  ```


![first Rows and last rows](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/cef0620c-cd9a-4bc7-9123-2dd5e8565047)


   #### Cleaning

     ```na_counts <- colSums(is.na(df))
        na_counts
     ```
