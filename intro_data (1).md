# NYC Crime Data Analysis

## Introduction Problem

It is important to analize the crime data for the police system as well as the public so that we can know the trend and locations of the crimes in order to get preparied for them, or, more importantly, find ways to decrease the amount.

This project is trying to answer the following questions by analyzing the crime data of NYC:

1. What are the most common crime types? Which borough had the most crime number?
2. Did some of the efforts of the police system and the social education system work? What is the trend of crimes declined?
3. What is the crime trend during a year? which month is the peak of crime?
4. Which area has the most concentrated crime that needs special attention? Is this area related to it's economic prosperity?
5. Can the crime trend of 2020 be predicted? 

## About the DATA

The data was collected and will be used as follows:

| Data name | Collected from | Used for|
|:-----:|:----:|:----:|
|NYPD_Complaint_Data_Historic.csv | NY Open Data | Analize the crime features and trends|
|NYC venues information | Foursquare | Analize the relationship between crime and economic prosperity|

There are a lot of information in the Complaint Data, here we mainly focus on some of them to answer the questions, ie. date, description, borough name and location(latitude and longitute). 
The "date" is used for analize the number and trend. 
The crime type can be known from "description".
From "borough name" we can get the idea of which aera is more dangerous to draw the public's attention.
The"location" info can be used to get the visualization on maps.
In order to simply evaluate and visualize the economic prosperity, the Foursquare API is used to acquire venue information. The economic prosperity is evaluated based on the desicity of venues on the map when serching the whole city.


```python

```
