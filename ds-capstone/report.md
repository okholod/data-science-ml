# Explore Coffee Shops in Minsk, Belarus

## Introduction

Coffee is the world’s most popular beverage, it’s a universal drink that appeals to the majority of the population, and inexpensive to prepare. Thanks to this popularity coffee shops are considered profitable businesses that are relatively easy to operate. However, while it may appear to be easy, opening a coffee shop business requires a lot of insight, research, and planning. 

Coffee shops are a great place to socialize: to meet friends, for informal meetings, or for students to catch up on schoolwork. Given the above having a great location is obviously very important for attracting customers. To be successful, you need the right location for your coffee shop. You probably want something centrally located, a place where people already gather. Moreover, while you may not have direct competitors, the substitutes also play an important role at filling the needs of your customers. Substitutes can include places like cafe or donut shops – or any fast food place that serves coffee.

Even, if you are franchising or buying an existing business the location is pre-selected but you should still do your research and decide whether the existing or selected location is a good one.

In this research I will focus on choosing a right location for a new coffe shop in Minsk, Belarus. I am going to analyze location statistics for existing coffee shops, indirectly count customers and visits using check-ins, and look at existing substitutes. 

## Data

I am going to leverage Foursquare as a main source of data in this study. Foursquare is a technology company that built a massive dataset of location data. Currently its location data is the most comprehensive out there, and quite accurate that it powers location data for many popular services like Apple Maps, Uber, Snapchat, Twitter and many others, and is currently being used by over 100,000 developers, and this number is only growing.

The Foursquare APIs will be used to extract the following informations:
* Locations of the existing coffee shops
* Details for existing coffee shops like number of checkins, number of unique users
* Locations and categories of substitute venues in *coffee* category

As a part of my analysis I am going to look at neighborhoods in Minsk. There are nine districts in the city, but this devision looks too coarse for our goals. At the same time, location of the post offices is well correlated with the distribution of the population, this information may be extracted from the official post service site: http://belpost.by/branch/post/otdeleniya-sviazi/

The neighborhoods address information will be used to define geographical coordinates using a geocoding service. Later this information will allow us to extract statistics data for every neighborhood using Foursquare APIs. I am going to explore, compare and cluster the neighborhoods to make suggestions on choosing the best locations for a new coffee shops.
