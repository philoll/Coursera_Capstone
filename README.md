# Exploring Cuisines in Sydney and Melbourne

## Introduction

Australia is a nation of diverse cultures. With that comes a multitude of cuisines, which presents a challenge for any hungry soul looking to fill their stomach. For a tourist with their eye on food, Sydney and Melbourne are often on the top of their list of Australian cities to visit due to their abundance of restaurants - Sydney because of the diversity of cuisines on offer, and Melbourne because of the unique coffee culture [[1]](https://www.eater.com/2019/10/23/20918646/sydney-vs-melbourne-better-food-golden-century),[[2]](https://www.theage.com.au/politics/federal/dont-ask-which-city-has-better-food-20100108-lyex.html). But is this actually the case? In recent times, both Sydney and Melbourne have seen large numbers of family-run restaurants and cafes pop up, making the comparison a rather difficult one.

This leads to the question: is Sydney still the powerhouse for choice in cuisine, and is Melbourne still a coffee haven? This article aims to differentiate the two cities and to find out what each city truly has on offer.

It is hoped that this article can provide clarity for any budding foodie. It can also provide some insight for Sydney-siders and Melbournians on what is available in their backyard.

## Data

The analysis will utilise the following sets of data:

1. [Australian Suburbs Data](https://github.com/michalsn/australian-suburbs): Data in the form of a CSV file or JSON file. Provides a list of all areas in Australia at varying levels, from State, Local Government Area (LGA), and Suburb. In this analysis, LGAs that are listed as a part of Sydney and Melbourne will be extracted. This dataset also includes geocentric coordinates for each suburb. The data was gathered from the 2016 Census and compiled by Github user michalsn.

2. [Foursquare API](https://developer.foursquare.com/developer/): Provides the venue data for this analysis. Venue details such as venue name, location, and type will be extracted. Only venues that are classified as restaurant, cafe, or pub will be considered.

## Methods

All data analysis and modelling was performed using Python programming language in Google Colaboratory, an online Jupyter Notebook interface that allows for online computing using Google resources. The complete notebook can be found [here](https://github.com/philoll/Coursera_Capstone/blob/main/Exploring_Cuisines_in_Sydney_and_Melbourne.ipynb).

### Location Data

The location data was downloaded as a CSV file and imported into the notebook as a main dataframe for Australia. Two dataframes were extracted to summarise the details for all suburbs within the statistical areas of Greater Sydney and Greater Melbourne. The dataframes also included the geocentric coordinates for each suburb.

### Venue Data

For both Sydney and Melbourne, the venue data was retrieved from the Foursquare API. Functions were derived to call the Foursquare API for each suburb in the dataframes and to retrieve all the venues within a 500 metre radius of the suburb geocentric coordinates. For each venue, the name, coordinates, and category were extracted. Only venues that were listed in the food category were considered. Suburbs with less than 15 venues were discarded to avoid any problems that would occur in the modelling.

The venues were organised into new dataframes such that all the venues were grouped based on the venue category for each suburb through one hot encoding. The top three venue categories were then extracted for each suburb.

### Modelling

Cluster models were fitted to the venue category data for Sydney and Melbourne. A total of 5 clusters for each city were generated using the K-Means algorithm. Clusters were visualised using Folium maps. The venue categories present in each cluster was then analysed and compared between the two cities by descriptive methods.

## Results

### Sydney

For Sydney, a total of 13,976 venues in 660 suburbs were retrieved from the Foursquare API calls. Of these, 12,020 venues in 311 suburbs were in suburbs with 15 or more venues each.

Figure 1 shows a breakdown of the various types of venues in each cluster for Sydney. A total of 20 different venue types were grouped. For ease of understanding, the breakdown of each cluster has been summarised in Table 1.

![Most common venue types in Sydney.](/images/bar_sydney.png)

*Figure 1. Most common venue type for each suburb in Sydney as a proportion of all venues in each cluster.*

*Table 1. Summary of venue types in each cluster in Sydney.*

| Cluster | Most common venues | Assigned colour |
| --- | --- | --- |
| 0 | Take Away: Fast Food, Pizza, Middle Eastern | Dark purple |
| 1 | Cafés | Purple |
| 2 | Asian: Chinese, Vietnamese, Filipino | Pink |
| 3 | European and Asian: French, Italian, Indian, Thai | Orange |
| 4 | Cafés, Other Restaurants | Yellow |

Cafés were present in all clusters, with Clusters 1 and 4 consisting of mainly cafés. In addition to cafés, Cluster 4 also included some other restaurants of mixed cuisine. Cluster 0 is defined by take-away joints, namely fast food restaurants, pizza places, and Middle Eastern restaurants. Cluster 2 is defined by Asian cuisine and includes Chinese, Vietnamese, and Filipino restaurants. Cluster 3 is defined by a mix of European and Asian cuisines and includes French, Italian, Indian, and Thai restaurants.

The Sydney suburbs making up each cluster are marked on the map in Figure 2. Each cluster was assigned a different colour for easier interpretation. Take-away restaurants (Cluster 0, dark purple) is predominantly in the western part of Sydney, while café dominated suburbs (Clusters 1 and 4, purple and yellow) are mostly in the East, Inner West, North of Sydney. Suburbs with European and Asian cuisines (Clusters 2 and 3, pink and orange) are scattered throughout the city.

![Clusters in Sydney.](/images/map_sydney.png)

*Figure 2. Clusters generated for Sydney. Coloured circles represent the assigned cluster for each suburb in the analysis. Dark purple = Cluster 0; Purple = Cluster 1; Pink = Cluster 2; Orange = Cluster 3; Yellow = Cluster 4.*

### Melbourne

For Melbourne, a total of 7,900 venues in 355 suburbs were retrieved from the Foursquare API calls. Of these, 6,884 venues in 177 suburbs were in suburbs with 15 or more venues each.

Figure 3 shows a breakdown of the various types of venues in each cluster for Melbourne. A total of 15 different venue types were grouped. For ease of understanding, the breakdown of each cluster has been summarised in Table 2.

![Most common venue types in Melbourne.](/images/bar_melbourne.png)

*Figure 3. Most common venue type for each suburb in Melbourne as a proportion of all venues in each cluster.*

*Table 2. Summary of venue types in each cluster in Melbourne.*

| Cluster | Most common venues |
| --- | --- |
| 0 | Western and Asian: Australian, BBQ, Chinese, South Indian |
| 1 | Cafés, Other Restaurants |
| 2 | Cafés |
| 3 | Pizza, Bakery, Vietnamese |
| 4 | Cafés |

Similar to Sydney, cafés were present in all clusters, with Clusters 1, 2 and 5 consisting of cafés as the most common venue type. In addition to cafés, Cluster 1 also included some other restaurants of mixed cuisine. Cluster 0 is defined by Western and Asian cuisine and includes Australian, BBQ, Chines, and South Indian restaurants. Cluster 3 is defined by pizza places and bakeries, with a presence of Vietnamese restaurants included.

The Melbourne suburbs making up each cluster are marked on the map in Figure 4. Here, there is a mix of all cluster types throughout the city, with the exception of pizza places, bakeries, and Vietnamese restaurants (Cluster 3, orange) appearing to be only in the outskirts of Melbourne.

![Clusters in Melbourne.](/images/map_melbourne.png)

*Figure 4. Clusters generated for Melbourne. Coloured circles represent the assigned cluster for each suburb in the analysis. Dark purple = Cluster 0; Purple = Cluster 1; Pink = Cluster 2; Orange = Cluster 3; Yellow = Cluster 4.*

## Discussion

This report summarises the clustering of the most common venues by suburb in Sydney and Melbourne. It shows that: (1) cafés are present in all clusters and throughout both cities; (2) the clustering of take-away joints against restaurants in Sydney is location dependent while in Melbourne it is not; and (3) there is less variety of cuisines being the most common in the suburbs of Melbourne compared to Sydney.

### Location is a Factor

The disparity of cuisine type with location is apparent in the Sydney clustering analysis. Take-away joints are situated mainly in the west and south-west regions of Sydney while cafés are more present in the east and north. This can be attributed to the demographic making up these regions in Sydney, with mostly ethnic communities residing in the west and Caucasian communities residing in the east and north [[3]](https://www.abs.gov.au/websitedbs/D3310114.nsf/Home/census). The divide may indicate a difference in eating habits of the Sydney residents where people with lower incomes (West) are tend to select cheaper food options, while those on higher incomes (North) can afford to spend more. This divide does not appear in the Melbourne analysis, with fast food restaurants not even appearing as a top venue type suggesting the demographic in Melbourne is not significantly divided by geography.

### Café-Centric Nation

While Melbourne has typically been known as the café capital of Australia and is evident from the venue analysis reported here, it is apparent that cafés also make up a large portion of venues in Sydney. With changing attitudes and the introduction of social media, the brunch and coffee lifestyle has been on the rise.

### Limitations

The analysis reported here is not without some limitations. First, only suburbs with 15 or more listed venues within a radius of 500 metres were selected. Of course, some venues may not be within this search area, leading to an under-representation of restaurants in suburbs with a larger land area. To rectify this, analysis on the details of each venue should be conducted where the address is extracted instead of the geographic coordinates. Second, the clustering model utilised the top 3 venue types of each suburb. However, the summary analysis of these results was only performed on the top venue of each suburb. Attempts were made at including the 2nd and 3rd most common venue type in the summary, but that resulted into far too many cuisine types being displayed. Third, some data may be categorised incorrectly. According to the Foursquare API documentation, venues are categorised according to the most specific level of cuisine. It would be more advantageous to categorise venues more broadly to make the clustering cleaner. However, this requires greater effort in data preparation.

## Conclusion

Sydney and Melbourne are powerhouses of food, providing a wide selection of cuisines throughout both cities. Sydney has a large number of restaurants and cafés, but the ethnic divide dictates where these venues are located. Melbourne still remains the café capital of Australia with venues throughout the city.

## References

1. [Amelia McGuinness, An Incredibly Biased Argument for Just Traveling to Sydney, Eater](https://www.eater.com/2019/10/23/20918646/sydney-vs-melbourne-better-food-golden-century).

2. [Simon Thomsen, Don't ask which city has better food, The Age](https://www.theage.com.au/politics/federal/dont-ask-which-city-has-better-food-20100108-lyex.html).

3. [Australian Bureau of Statistics, Census](https://www.abs.gov.au/websitedbs/D3310114.nsf/Home/census).
