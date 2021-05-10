Data wrangling and visualisation to find themes and patterns in species' conservations status.

# BIODIVERSITY IN NATIONAL PARKS

### INTRODUCTION

A data analysis report focusing on the conservation status of endangered species in USA’s National Parks with the aim to investigate patters, which could indicate 
why certain species become endangered.

It is widely understood that numerous human activities contribute to species becoming threatened. Typically, there are multiple causes at play that include 
“habitat destruction, fragmentation, and degradation, pollution, introduction of non-native species, disease, climate change, and over-exploitation”.  [1]

National Parks are well-protected landscapes that contain forested areas, water sources, and seashores. Their function is to help sustain and recover at-risk 
species of plants and animals in order to prevent their extinction. “At-risk species include those listed under the Endangered Species Act; state-, locally-, and 
tribal-listed species; and other native species that are of special management concern including rare, declining, sensitive, endemic, or unique species.” [2]

[1] “Saving Endangered Species: A Case Study Using Global Amphibian Declines”, Croteau, E. & Mott, C. L. (2011) Saving Endangered Species: A Case Study Using 
Global Amphibian Declines. Nature Education Knowledge 4(4):9;
[2] The National Park Service, U.S. Department of the Interior.

### SCOPE

#### GOALS

1. Identify themes and patterns that correlate with whether certain species of animals and plants become extinct.

#### ACTIONS

1. Use the findings to inform further research into current human-driven animal and plant extinction issues.

#### DATA

- There are 4 columns in the “species” dataframe, containing 5,824 samples.

category               		object
scientific_name        	object
common_names          	 object
conservation_status    	object
dtype: 			object 
    
unique categories: ['Mammal', 'Bird', 'Reptile', 'Amphibian', 'Fish', 'Vascular Plant', 'Nonvascular Plant'] 
number of unique scientific names: 5541 
number of unique common names:  5504
unique conservations status: [NaN, 'Species of Concern', 'Endangered', 'Threatened', 'In Recovery'] 

- Some unique scientific names are repeated more than once under different common names:

    - There are 265 unique scientific names that have 2 entries with different common name entires;
    - There are 9 unique scientific names that have 3 entries with different common name entries.

  For some of those repeat cases, the conservation status is different, while for others, only the common name is different. Where the conservation status does 
  not change but only the common name is different, those entries are treated as duplicates and are removed.
  
-  There are missing fields in the "species" dataframe in conservation status column, denoted as NaN. Out of 5,824 samples, there are only 191 samples that have a 
non-NaN conservation status recorded. Of those 191, 11 are removed as duplicates, leaving 180 samples. There are no missing fields in any other column.
  
- There are 3 columns in the “observations” dataframe, containing 23,296 samples.

scientific_name    	object
park_name          	object
observations        	int64
dtype: 		object 

number of unique scientific names:  5541
unique park names: ['Great Smoky Mountains National Park', 'Yosemite National Park', 'Bryce National Park', 'Yellowstone National Park']

- In the "observations" dataframe, there is typically only 1 observation entry for each unique National Park. For some species, however, there are multiple entries 
of observations for each National Park:

    - There are 5,267 unique species with only 4 recorded observations (1 for each unique national park); 
    - There are 265 unique species with 8 recorded observations;
    - There are 9 unique species with 12 recorded observations.

  For those species with multiple observations per unique National Park, it could be that those observations were made at different time periods and can provide 
  insight into how certain populations are growing or declining over time. However, there is no timestamp for any observation, nor is there any indication whether 
  repeat observations for a given National Park include the previously counted animals/ plants.

  Moreover, the species that have 12 observations recorded (3 for each National Park) are those that were listed under 3 different common names in the 'species' 
  dataframe.

- There are no missing fields in any column of the "observations" dataframe.

#### ANALYSIS

1.1 Bar chart of species in each category
1.2 Bar chart of species in each category that have a conservation status
1.3 Proportion of species with a conservation status to the total number of listed species in each category
2.1 Bar chart of unique species in each category by conservation status
2.2 As 2.1 but stacked for better visuals
3.1 Pie chart of proportions of each conservation status
4.1, 4.2, 4.3, 4.4 Box plot distributions of species observations for each conservation status in each national park

### DISCUSSION & EVALUATION

- Figure 1.1 shows a bar chart of all the unique species recorded in the dataframes. It can be seen that the vast majority of species in the dataframe are Vascular 
Plants, while the fewest number of species belong to the categories Reptile and Amphibian.

- Of those species that have a recorded conservation status, the largest proportion are Birds, followed by Vascular Plants and Mammals. This can be seen in 
Figure 1.2. Overall, there are only 180 animals that have a recorded conservation status out of the entire dataframe, which limits the extent to which endangerment 
and extinction patterns can be identified. Figure 1.3 further highlights this by showing the proportions of species with a known conservation status in each 
species category. In the case of Reptiles, Amphibians, Fish, and Nonvascular Plans, the proportion is so small, that it cannot be visibly seen on the chart.

- Figures 2.2 further splits the species categories by conservation status. The Mammals category has the largest proportion of ‘endangered’ unique species 
(6 species), followed by Bird (4 species) and Fish (3 species). A small amount of ‘endangered’ unique species belong to the Amphibian and Vascular Plant category 
(1 species each). Overall, there are 15 different ‘endangered’ unique species recorded in the data.

 Fish have 4 species labeled as ‘threatened’, while Mammals, Amphibians, and Vascular Plants each have 2 species with this label. 

 The vast majority of animals are labeled as ‘species of concern’. The largest proportion belongs to the Bird category (68 species), followed by Vascular Plants 
 (43 species), and Mammal (22 species). All categories have of animals have their largest proportion labeled as ‘species of concern’.

 A small proportion of animals are labeled as ‘in recovery’. The belong to the Bird category (3 species) and Mammal category (1 species). None of other categories 
 represent animals with this status.

- Figure 3.1 shows a pie chart of all the categories combined, split by conservation status. ‘Species of Concern’ make up 83.89% of the data, while ‘endangered’ 
and ‘threatened’ account for 8.33% and 5.56% respectively.

- Figures 4.1 through 4.4 show box plot distributions of species count , split by conservation status for each National Park. For Bryce National Park (Figure 4.1), 
the ‘Species of Concern’ status is the most spread out, containing species that have a recorded count ranging from 49 to 135 (152 as outlier). The median count in 
this category in Bryce National Park is 94. This indicates that there are potentially other factors that contribute to a species being labeled as ‘species of 
concern’ other than merely the number of observations.

 For the ‘in recovery’ status, the median observation count is lower than for ’species of concern’ at 92, possibly owing to the fact that this category contains 
 much less data.

 The ‘threatened’ and ‘endangered’ status labels have median observation counts of 46 and 25 respectively, with distributions behaving much more predictably than 
 for the other two statuses.

 For the other three National Parks, a similar picture evolves. The ‘species of concern’ distribution is spread out and overlaps the ‘in recovery’ status 
 distribution.

### CONCLUSIONS

- The analysis of the 180 animals with a recorded conservation status indicates that while there are more Mammals labeled as ‘endangered’, Fish are more likely 
than Mammals to be ‘endangered’, with 27.3% of species that are Fish being labeled as ‘endangered’. Meanwhile, only 19.4% of species in the Mammals category have 
the ‘endangered’ status.

- For the ‘threatened’ status, the Fish has the greatest number of species being labeled as such, while also being the category where animals are most likely to 
be labeled ‘threatened’ (36.4%). This is followed in second place by Amphibians, where 28.6% of Amphibians are ‘threatened’.

- The Bird, Vascular Plant, and Mammal categories, all have relatively high numbers of ‘species of concern’. Yet, Nonvascular Plants and Reptiles have a 100% of 
their animals labeled as such. Vascular Plants have 93.5% of their species, and Bird have 90.7% of the species labeled as ‘species of concern’.

- Birds have the greatest number and most likelihood of species being ‘in recovery’.

- Overall, it could be said that Fish is the most affected category, having the highest likelihood of animals being ‘endangered’ or ‘threatened’. Mammals are also 
badly affected, having the highest raw number of species with the ‘endangered’ status. Birds have the highest proportion of ‘species of concern’ animals of all 
the categories, followed by Vascular Plants and Mammals in second and third places respectively. 


