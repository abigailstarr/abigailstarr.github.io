## Using Airbnbs to Cluster Chicagoland

**Project description:** This project combines geospatial analysis with machine learning tools to compare Airbnb listings and the related socioeconomic qualities of the areas they inhabit. Specifically, I question whether clustering Chicagoland communities by Aribnb characteristics such as price and host rating would produce homogenous or heterogenous socioeconomic regions. The analysis suggests a positive correlation between the density and quality of Airbnb listings and the socioeconomic well-being of a neighborhood.

### 1. Initial Data
- **Libraries**: `geopandas`, `pandas`, `numpy`, `scipy`, `sklearn`, `shapely`
- **Datasets**:
  - Airbnb data from Inside Airbnb (2015).
  - Socioeconomic and population data from the Chicago Data Portal and GeoDa (2010 to 2015)

### 2. Exploratory Data Analysis
- community areas missing Airbnb data were excluded from the analysis, but notably were located exclusively in the southwest of Chicago
- created a point probability map to identify areas with more or fewer Airbnbs than expected

```python
#compute average intensity & expected value
airbnbs["areakm2"] = airbnbs.geometry.area / 10**6
average_intensity = airbnbs["num_spots"].sum() / airbnbs["areakm2"].sum()
airbnbs["expected"] = average_intensity * airbnbs["areakm2"]

#create conditions for point probability map
airbnbs['pointprob'] = poisson.pmf(airbnbs['num_spots'], 
                                    airbnbs['expected'])

conds = [(airbnbs['num_spots'] > airbnbs['expected']) & (airbnbs['pointprob'] < 0.05),
            (airbnbs['num_spots'] < airbnbs['expected']) & (airbnbs['pointprob'] < 0.05)]
airbnbs['map_cond'] = np.select(conds,
                            ['More than expected', 'Less than expected'], 
                            default='Non-significant')
```

<img src="images/expected_number.png?raw=true"/>

### 3. Clustering Results
- K-means clustering (optimal K=6) and agglomerative hierarchical clustering (AGNES) produced highly similar clusters
- clusters were named based on defining Airbnb characteristics and showed distinct socioeconomic characteristics, i.e.:
  - **Cluster #1: Few Spots; Cheap with Poor Host Reviews**: higher hardship index than average, residents earn about $10,000 less per year than the average
  - **Cluster #2: Hundreds of Spots; Expensive with Picky Host**: extremely low hardship index, residents earn about $30,000 more per year than the average 

<img src="images/airbnbs.png?raw=true"/>

### 4. Key Findings & Future Work
- there is a positive correlation between Airbnb density and quality and neighborhood affluence
- community areas with more Airbnbs & a higher standard of living are located largely on the north side of Chicago
- future researchers should collect/analyze more recent data to determine if the observed patterns continue post-pandemic and the subsequent migration from cities

