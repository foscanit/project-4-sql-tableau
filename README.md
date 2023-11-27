# project-4-sql-tableau

# LANGUAGE ANALYTICS

# Overview

The aim of this project was to clean, preprocess and analyze four datasets, three of them from Kaggle and another one found in Github. These datasets contained information related to the current situation of world languages and the countries where they are or were spoken. I used this data to make some queries with MySQL in order to prove or disaprove my hypotheses. After that, I created some visualizations with Tableau to reinforce my conclusions.
<br>

# Requirements/Libraries Used:
This code was written in Python/Jupyter Notebook, using the following libraries:
<br>
- jupyter notebook
- MySQL
- Tableau
- numpy
- pandas
- matplotlib.pyplot
- seaborn
- pymysql
- sqlalchemy
- get pass
- os
- re
<br>
 

# Hypotheses:
<br>

## 1- Endangered languages are more concentrated in specific geographic regions.

## 2- Countries with higher population density tend to have a higher linguistic diversity.

## 3- Higher levels of urbanization in a country are associated with a shift towards dominant languages and a decline in the use of minority languages.

## 4- The type of political system in a country is related to the number of languages spoken, with democratic countries having higher linguistic diversity.

## 5- The current number of endangered languages in a country is correlated with the historical incidence of language extinction in that country and the presence of a dominant language from the top 10 most spoken languages in the world.

<br>

# Workflow/ Methodology:

## 1. Data exploring and preprocessing

First of all I imported the four datasets and I started to explore them. The first one was about endangered languages and it included information like the names of the countries where the languages are still spoken and the degree of endangerment for each of them. There was a column with the number of speakers, but it had a considerable amount of nulls or empty values, so I decided not to extract the information directly from there. 

The second dataset was a list of the most spoken languages in the world by the numbers of speakers. For this one, I created a function to convert the values of the number of speakers from objects to floats, in case I need it later on for the queries or for Tableau's visualisations. I save a new csv file with these changes. 

The third one contained a concised overview of all countries, sorted alphabetically, which included information such as coordinates, agricultural land, city capitals, etc. I dropped the columns that weren't necessary for my analysis and saved the new dataframe. 

The last dataset had only two columns: "Country" and "Languages spoken". In the second column, the values were usually long strings containing the registered languages for each country.  

So I decided to join the last two datasets on the "country" column and then I created another function to count the languages in the string for each country (column: "Language spoken"). Then I applied the results of this function to a new column, "count_languages", so that I could have an aproximate idea of how many registered languages were in each country for my further analysis. I saved a new csv file with the joined dataframe.


## 2. MySQL queries

This second phase of the project can be found in the notebook named "SQL". First, I established my five hypotheses and I imported three datasets: the one about endangered languages, the one with the world top spoken languages and the third one was a combination of World countries' details and Languages per country, as explained above. 

Then, I connected MySQLWorkbench with my Jupyter notebook and I created a database named "languages" with three tables. Right after I started the queries to analyze the data and try to solve my questions. 


## 3. Tableau's visualizations

Finally, I worked with Tableau in order to visualize the results of my queries:

https://public.tableau.com/app/profile/cl.udia.pintos.relat/viz/WorldLanguagesAnalytics/WorldLanguagesAnalytics#1

In the fifth and sixth visualizations, we can see some of the languages spoken in the countries with the highest and lowest populations. We can also observe that in the first case, there are a lot of unnamed languages and dialects, therefore a higher linguistic diversity in countries with higher populations, even if these languages are not recognized by the country. 



# 1- Endangered languages are more concentrated in specific geographic regions.

For this question, I selected the top 6 countries with more endangered languages. Then, I extracted the geographic regions and the coordinates for each country: The results were Northen America (USA), Central America (Mexico), South America (Brazil) and Eastern and Southern Asia (China, India and Indonesia).



# 2- Countries with higher population density tend to have a higher linguistic diversity.

In this case, I did three queries. First, I selected the top ten countries with more population. Then, I extracted the countries in which there were more registered languages (according to the column "count_langugaes"). Then I selected the 10 countries with lowest population and I could see that there were less registered languages per country. 
<br>


# 3- Higher levels of urbanization in a country are associated with a shift towards dominant languages and a decline in the use of minority languages.

Here, I extracted the 9 countries with the highest urban population and the highest urban land to check if most of the countries coincided. In addition, with a tableau visualization, I realized that most of the countries with the highest urban population are also the ones where the official language is one of the top 10 spoken languages. 

So this could indicate us that even though in these countries there may be a higher linguistic diversity, as we have seen above, there's also a tendency to prioritize the promotion of dominant languages, while marginalizing or discouraging the usage of minority languages. Moreover, again 7/9 of these countries are also the ones with more endangered languages. 


# 4- The type of political system in a country is related to the number of languages spoken, with democratic countries having higher linguistic diversity.

In this section, I selected the 10 countries with the highest democratic score, and I checked the column of 'count_languages' for each of them. Then, I calculated the average of the total languages spoken in these countries (labeled as "full democracies"). The result was 3.8.

After that, I selected the 10 countries with the worst democratic score (the ones labeled as "authoritarian"). Again, I calculated the average of their total languages and the result was 3.7. I realized there wasn't much difference in the linguistic diversity between these two groups so the policitical system may not be directly related to the number of spoken languages. 

Finally, I extracted again the top 10 countries with the highest count of endangered languages, and then with another query, I checked which form of government had each of these countries. From this, I concluded that that the type of countries where there are more vulnerables languages are flawed democracies, rather than authoritarian regimes. As a conclusion, we could say that flawed democracies usually have a deficiency in political measures designed to safeguard and preserve local languages.



# 5- The current number of endangered languages in a country is correlated with the historical incidence of language extinction in that country and the presence of a dominant language from the top 10 most spoken languages in the world.

For the last hypothesis, I did three queries. First, I extracted again the top 5 spoken languages in the wordl. Then, also again, I selected the 5 countries with more endangered languages. In the last query I checked in which 5 countries had been extincted more languages. By doing this, we can clearly see the correlation between the countries with more endangered countries, the coutries with more extinct languages and the top spoken languages. 

- English is the most dominant language in the world, and conclusively United States has become the top 1 country with both more extinct and vulnerable languages. 

- Mandarin is the second most dominant languages, and China is the fourth country with more exctinct languages. 

- Hindi is the third most dominant language, and India is also the third country with more endangered languages.

- Spanish is the fourth most dominant language, and Mexico is the fourth country with more endangered languages.

On the other hand, although this cannot be reflected in the query (but instead in my Tableau visualizations), portuguese is in the top 10 spoken languages; Brazil is the second country with more endangered languages and the fourth country with more extinct languages. 



# In Conclusion

### 1. In these regions, there is a higher concentration of endangered languages: Northern, Central, and Southern America, as well as Eastern and Southern Asia.

### 2. With the data provided from the dataset of spoken Languages per country, there's not an evident correlation between the count of registered languages and the population of each country. However, according to this data and our visualizations, we can see that there are a lot of unnamed languages and dialects, therefore a higher linguistic diversity, in the countries with the highest population.

### 3. The countries with the highest urban population are also the ones with more endangered languages. Also, their official languages are among the top 10 spoken languages in the world. 

### 4. We may think that the type of political system in a country is related to the number of languages spoken, with democratic countries having higher linguistic diversity. However, this analysis has showed that the type of countries where there are more vulnerables languages are flawed democracies, rather than authoritarian regimes.

### 5. The United States is the nation where the prevalence of a dominant language (English) has posed a threat to and caused the disappearance of the highest number of languages.

