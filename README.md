# Homicide - Data Analyzing and Visualization
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

   ```
      cat("First 5 rows in the data Set", "\n")
      df[1:5,]
      cat("\n")
      cat("Last 5 rows in the data set", "\n")
      df[-(1:52174),]
  ```


![first Rows and last rows](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/cef0620c-cd9a-4bc7-9123-2dd5e8565047)


Cleaning

```
na_counts <- colSums(is.na(df))
na_counts
```
![na counts](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/1399580f-63d2-4ea9-a280-73446cbd6509)

     
```
df$reported_date <- ymd(df$reported_date)
na_counts <- colSums(is.na(df))
na_counts
problem_rows_rpt_date <- df[is.na(df$reported_date),]
problem_rows_rpt_date
```
![datachange](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/0d11d59e-cc4e-4b69-91fe-8272b2cf4e37)

### Few Visualizations

```
ggplot(df2, aes(x = victim_age))+
scale_x_continuous(breaks = seq(0,105,2))+
geom_boxplot()+labs(title = "Distribution of Victim's Age", x = 'Age')+
theme(plot.title = element_text(face = "bold", hjust = 0.5, size = 15),
     axis.title.x = element_text(face = "bold", size = 14),
     axis.title.y = element_text(face = "bold", size = 14),
     axis.text.x = element_text(face = "bold", size = 10),
     axis.text.y = element_text(face = "bold", size = 10))
```


![box plot](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/b916eeb8-1ca6-4022-93d0-02f50c3f605a)

```
data_set %>% 
select(victim_race) %>% 
group_by(victim_race)%>% 
summarise(total_count = (count = n()))%>% 
ggplot(aes(x="", y = total_count, fill = victim_race ))+
geom_bar(stat = "identity",width = 6, color = 'white')+
coord_polar("y", start =0)+
geom_text(aes(label =scales::comma(total_count)), position = position_stack(vjust = 0.5))+
labs(title = "Total Victims By Race", x = NULL, y = NULL)+
theme_minimal()+
theme(axis.text.y = element_text(face = "bold", size =15))
```

![Pie chart](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/16167127-75ff-4873-9b03-b4387e6852b8)

```
data_set %>% 
ggplot(aes(x = victim_age, y = victim_race, fill = victim_race))+
geom_boxplot()+
scale_x_continuous(breaks =seq(4,64,2))+
labs(title = "Distribution of Victim Age by Race",  x = "Victim Age", y = "Victim Race")+
theme_minimal()+
theme(plot.title = element_text(face = "bold", hjust = 0.5, size = 15),
     axis.title.x = element_text(face = "bold", size = 14),
     axis.title.y = element_text(face = "bold", size = 14),
     axis.text.x = element_text(face = "bold", size = 10),
     axis.text.y = element_text(face = "bold", size = 10))
```

![boxplot2](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/35dd02aa-e8bc-42c1-a1e8-0cad50b716cd)

```
data_set %>%
  select(state) %>%
  group_by(state) %>%
  summarise(total_victims = n(), .groups = "drop") %>%
  arrange(desc(total_victims)) %>%
  ggplot(aes(y = reorder(state, total_victims), x = total_victims, fill = total_victims)) +
  geom_bar(stat = "identity") +
  scale_x_continuous(expand =c(0.005,0), breaks = seq(0,6000,250))+
  labs(title = "Total Victims by State",
       x = "Total Victims",
       y = "State") +
  theme_minimal() +
  theme(
      plot.title = element_text(hjust = 0.5),
        axis.title.y = element_blank(),
        axis.text.y = element_text(vjust = 0, face = 'bold', size = 12),
        axis.text.x = element_text(vjust = 0, face = 'bold', size = 12))
```


![Bar chart](https://github.com/Nilanka1982/Homicide-Data-Analyzing-Visualization/assets/66845038/a993b0e4-8f25-4615-af46-db75237b6994)

### Findings
* I did analysis for homicide data which was generated for time period  2007 - 2017 
* Maximum age of the data set shows as 102 and minimum shows as 0. - I see some Victim's ages are not possible to do the victim. May be typing mistake or wrong data collection. Should have some mentally and physical strength to do the victim.
* CA is the worst place according to the data set(most reported cases).
* CO is the calm place according to the data set(least reported cases).
* Victim_races = "black" is involved in most cases according to the data set information.
* I don't see a huge gap through the year for the victims. But I can say most cases were reported in 2016 and the least cases were reported in 2009.
* According to the data set's information 21748 remaining cases are still to be solved or to arrest.




