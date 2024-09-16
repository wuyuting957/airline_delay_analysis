# airline_delay_analysis
# analyze the correlation of airlines and delay 
library(tidyverse)
library(ggplot2)
lax_jfk_data<- read.csv("lax_to_jfk.csv")
View(lax_jfk_data)

class(lax_jfk_data$DepDelayMinutes)

#part 1
summarary_airline_delay<- lax_jfk_data %>%
  group_by(Reporting_Airline) %>%
  summarise(
    mean= mean(ArrDelayMinutes, na.rm= TRUE),
    std_dev= sd(ArrDelayMinutes, na.rm= TRUE))

#part 2
avg_delays<- lax_jfk_data %>%
  group_by(Reporting_Airline, DayOfWeek) %>%
  summarize(mean_delays= mean(ArrDelayMinutes))
  
