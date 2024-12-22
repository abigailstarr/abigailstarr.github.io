# The Legality of Cannabis, by State, & its Relation to the Price of Marijuana and the Housing Market

**Project description:** This project explores the relationship between cannabis legality, prices, and the Housing Price Index (HPI) in U.S. states. Analysis suggests that while marijuana prices tend to decrease as nationwide availability increases, price is not heavily correlated with legalization status. Notably, states that allow the sale of recreational cannabis experienced faster-growing HPIs from 2015 to 2022. States permitting recreational cannabis also had higher HPIs at the start of 2015. Further research is needed to prove causation beyond observed correlations.

## 1. Initial Questions
- **Primary Question**: Does the legality of cannabis affect its price in U.S. states?
- **Secondary Question**: Is there evidence of a correlation between marijuana prices and the Housing Price Index (HPI)?

## 2. Initial Data
- **Libraries**: `pandas`, `numpy`, `altair`, `geojson`
- **Datasets**:
  - Cannabis price data for 2015 and 2022.
  - State demographic data.
  - HPI data from 1975 to 2021.

## 3. Methods & Analysis
- **Legal Status Geospatial Analysis**: using choropleth maps, visualized changes in legalization status between 2015 and 2022
- **Price Trends**: calculated percent changes in price (adjusted for inflation) across states and visualized using choropleth maps
- **HPI Changes**: identified patterns between HPI growth and cannabis legality and visualized using line and bar plots

<img src="images/marijuana_maps.png?raw=true"/>

## 4. Key Findings & Limitations
- **Findings**:
  - Cannabis prices have decreased nationwide, but with a weak correlation to legalization
  - States permitting recreational cannabis consumption initially had higher HPIs and experienced faster growth.
- **Limitations**:
  - Data quality; cannabis prices are self-reported
<br/>

<img src="images/hpi.png?raw=true"/>

## 5. Future Work
- Explore the potential correlation between legalization, taxation, and marijuana prices
- Extend analysis as more states legalize cannabis and data becomes more widely available
