# Exploring Cuisines in Sydney and Melbourne

## Introduction

Australia is a nation of diverse cultures. With that comes a multitude of cuisines, which presents a challenge for any hungry soul looking to fill their stomach. For a tourist with their eye on food, Sydney and Melbourne are often on the top of their list of Australian cities to visit due to their abundance of restaurants - Sydney because of the diversity of cuisines on offer, and Melbourne because of the unique coffee culture. But is this actually the case? In recent times, both Sydney and Melbourne have seen large numbers of family-run restaurants and cafes pop up, making the comparison a rather difficult one.

This leads to the question: is Sydney still the powerhouse for choice in cuisine, and is Melbourne still a coffee haven? This article aims to differentiate the two cities and to find out what each city truly has on offer.

It is hoped that this article can provide clarity for any budding foodie. It can also provide some insight for Sydney-siders and Melbournians on what is available in their backyard.

## Data

The analysis will utilise the following sets of data:

1. [Australian Suburbs Data](https://github.com/michalsn/australian-suburbs): Data in the form of a CSV file or JSON file. Provides a list of all areas in Australia at varying levels, from State, Local Government Area (LGA), and Suburb. In this analysis, LGAs that are listed as a part of Sydney and Melbourne will be extracted. This dataset also includes geocentric coordinates for each suburb. The data was gathered from the 2016 Census and compiled by Github user michalsn.

2. [NSW Local Government Areas - Geoscape Administrative Boundaries](https://data.gov.au/data/dataset/f6a00643-1842-48cd-9c2f-df23a3a1dc1e): 2019 Geospatial boundary data for NSW Local Government Areas, including those in Greater Sydney. This will be used for plotting and for retrieving the geocentric coordinates of each LGA.

3. [Vic Local Government Areas - Geoscape Administrative Boundaries](https://data.gov.au/data/dataset/bdf92691-c6fe-42b9-a0e2-a4cd716fa811): 2019 Geospatial boundary data for Victoria Local Government Areas, including those in Greater Melbourne. This will be used for plotting and for retrieving the geocentric coordinates of each LGA.

4. [Foursquare API](https://developer.foursquare.com/developer/): Provides the venue data for this analysis. Venue details such as venue name, location, and type will be extracted. Only venues that are classified as restaurant, cafe, or pub will be considered.
