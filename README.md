# Biodiversity in National Parks

The purpose of this project is to analyze biodiversity data from the National Parks Service, particularly around various species observed in different national park locations.


## Data Collection

Files : `species`, `observations`

For my data mining I used two sources: [kaggle](https://www.kaggle.com/nationalparkservice/park-biodiversity?select=species.csv) data repository and the national Park Service species list database [The National Park Service](https://irma.nps.gov/NPSpecies), database is managed and updated by staff at individual national parks and the systemwide Inventory and Monitoring department.


## EDA

###  Exploring the species data a little more in depth

Firstly, finding the number of distinct species in the data. In the column scientific_name we have 5,541 unique species. Vascular plants are by far the largest share of species with 4,470 in the data with reptiles being the fewest with 79. Moreover, Conservation_status column has 4 categories, Species of Concern, Endangered, Threatened, In Recovery, and nan values. Furthermore, There are 5,633 nan values which means that they are species without concerns. On the other hand there are 161 species of concern, 16 endangered, 10 threatened, and 4 in recovery. Ultimately, the Observations dataset has only 4 national parks but there are 3,314,739 sightings in 7 days... that's a lot of observations!


### Analysis

Analyzing the data after the initial exploration.

The column conservation_status has several possible values:

- Species of Concern: declining or appear to be in need of conservation
- Threatened: vulnerable to endangerment in the near future
- Endangered: seriously at risk of extinction
- In Recovery: formerly Endangered, but currently neither in danger of extinction throughout all or a significant portion of its range

In the exploration, a lot of nan values were detected. These values will need to be converted to No Intervention.

<img width="681" alt="table" src="https://user-images.githubusercontent.com/26355917/146958754-5e1fc07a-4f12-4be9-bfaf-e9d443d82950.png">

Next, checking the different categories that are nested in the conservation_status column except for the ones that do not require an intervention. For those in the Endangered status, 7 were mammals and 4 were birds. In the In Recovery status, there were 3 birds and 1 mammal, which could possibly mean that the birds are bouncing back more than the mammals.

<img width="589" alt="chart" src="https://user-images.githubusercontent.com/26355917/146958768-29016397-b5de-4b2e-a32b-9834b00da8e7.png">




### In conservation do we have certain types of species are more likely to be endangered?

To check if certain types of species are more likely to be endangered, Created a new column called is_protected including any species that had a value other than No Intervention. Then grouped by their category and is_protected to show the break down of each species type and protection status. 
It's easy now to see that Birds, Vascular Plants, and Mammals have a higher absolute number of species protected. Simultaneously, the rate of protection for each category exhibits in the data ~17 percent of mammals were under protection, as well as ~15 percent of birds.

<img width="463" alt="table" src="https://user-images.githubusercontent.com/26355917/146961660-135c7dce-ad14-4378-b85e-7550f6af6fb0.png">



### Statistical Significance

This section will run some chi-squared tests to see if different species have statistically significant differences in conservation status rates. The results from the chi-squared test returns 0.69 p-value. The standard p-value to test statistical significance is 0.05. For the value retrieved from this test, the value of 0.69 is much larger than 0.05. In the case of mammals and birds there doesn't seem to be any significant relationship between them i.e. the variables independent.
In the second test is between Reptile and Mammal. This time the p-value is 0.039 which is below the standard threshold of 0.05 the difference between reptile and mammal is statistically significant. Mammals are shown to have a statistically significant higher rate of needed protection compared with Reptiles.

### Species in Parks

Analyzing the data from the conservationists. Firstly, looking at the common names from species to get an idea of the most prevalent animals in the dataset. The data will be need to be split up into individual names and hence cleaned up duplicate words in each row since they should no be counted more than once per species, and then collapsed the into one list for easier use. From this analysis, it seems that Bat occurred 23 times while Shrew came up 18 times.

<img width="175" alt="table" src="https://user-images.githubusercontent.com/26355917/146963926-7b824e04-10b6-4237-b10e-f3562dc55042.png">

The total number of bats observed in each park over 7 days are in the table below. Yellowstone National Park seems to have the largest with 8,362 observations and the Great Smoky Mountains National Park having the lowest with 2,411. In the table below each park broken down by protected bats vs. non-protected bat sightings. It seems that every park except for the Great Smoky Mountains National Park has more sightings of protected bats than not. This could be considered a great sign for bats.

<img width="455" alt="table" src="https://user-images.githubusercontent.com/26355917/146964631-8e84fcc9-510a-42b9-a1cb-3755947911e0.png">

The Great Smoky Mountains National Park might need to beef up there efforts in conservation as they have seen more non-protected species.

<img width="872" alt="chart" src="https://user-images.githubusercontent.com/26355917/146964895-fdae594f-97ff-46d5-bb81-af03335a1c6b.png">


### Conclusions

The project was able to make several data visualizations and inferences about the various species in four of the National Parks that comprised this data set.

- The vast majority of species were not part of conservation.(5,633 vs 191)
- Mammals and Birds had the highest percentage of being in protection.
- While mammals and Birds did not have significant difference in conservation percentage, mammals and reptiles exhibited a statistically significant difference.
- Bats occurred the most number of times and they were most likely to be found in Yellowstone National Park.
