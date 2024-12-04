## **Fulton Hogan Roadworks Timing Project**

Chathurangi Godahewa Gamage - 46827070

Dury Kim - 44986585
        
Renata King - 45677452

Shantikrishna Panicker - 26037298 
        
date: 2024-09-27


### **Project Overview**

This project analyzes population data from telecommunications sources (Spark and Vodafone) to determine the best time to plan roadworks in high-traffic areas (Auckland, Wellington, and Christchurch CBDs). The goal is to provide population counts across Statistical Areas Level 2 (SA2) in New Zealand at different times.Conducting roadworks in CBD areas is often disruptive to businesses, costly due to traffic management, and potentially hazardous for workers in high-traffic zones. Fulton Hogan is particularly interested in minimizing disruptions and improving safety and efficiency by scheduling roadworks during periods when population density is at its lowest.

### **Objectives**

1. Evaluate Population Density Shifts: Using telecommunications data from Spark and Vodafone, this project assesses how population density changes over time in the CBD areas. By analyzing the data over different time periods, we can identify times when population density is significantly reduced, such as during school holidays or on certain days of the week.
2. Identify Optimal Times for Roadworks: The main goal is to identify periods when the population is low, such as weekends, evenings, or during holidays. These time windows could be used to plan roadworks, minimizing disruption to businesses and traffic in the CBD areas.
3. Comparative Analysis Between Cities: By comparing population movement data across Auckland, Wellington, and Christchurch, we aim to identify any geographical differences in traffic patterns that may affect the scheduling of roadworks. Understanding city-specific patterns allows for more precise planning based on local population behavior.
4. Delivering a Clean Data set: As part of the project, a clean, merged, and aggregated dataset is produced. This dataset includes the SA2 codes (Statistical Area Level 2), timestamps, geographical indicators, and the population counts from both Spark and Vodafone. The dataset is structured in a way that future analysis can be performed easily by Fulton Hogan’s data scientists.


### **Project Structure**
  

The repository contains several R scripts to clean, merge, and analyze the data:

1. 01_load_clean_data.R : Loads and cleans the Spark and Vodafone data, handling missing values and ensuring correct datetime formats.
2. 02_merge_sa2_data.R : Merges the cleaned population data with SA2 geographic information from the concordance files.
3. 03_aggregate_population_data.R : Aggregates population counts by SA2 codes and timestamps to compute total population for each region.
4. 04_export_final_data.R : Exports the final data set as a gzipped CSV file.


### **Data Sources**


- Telecommunications Data: Spark and Vodafone provided population counts by location and timestamp. These counts act as proxies for the population density in various areas. This is used to estimate real-time population shifts in different Statistical Areas (SA2).

- Geographical Concordance Files: Additional datasets, including SA2 concordance files, urban/rural indicators, and territorial authority codes, are used to map the telecommunications data to specific geographical regions. This allows for further analysis of how population density changes vary by region


### **Datasets**
  

The project uses the following data sets.

- sp_data.csv.gz : Spark telecommunications data, containing timestamps, SA2 codes, and population counts.
- vf_data.parquet : Vodafone telecommunications data, similar in structure to Spark data but in Parquet format.
- sa2_2023.csv : A concordance file containing mappings of SA2 codes to geographic descriptors (e.g., region names).
- urban_rural_to_indicator_2023.csv : Provides urban/rural indicators for each region.
- urban_rural_to_sa2_concord_2023.csv : Contains mappings between SA2 codes and urban/rural indicators.


### **Requirements (Run the Projects)**
  

1. First, Install and Load the required libraries

Load the libraries
library(dplyr)
library(readr)
library(lubridate)
library(arrow)  # To read Parquet files
library(tidyr)


2. Download and prepare the datasets

Ensure the following datasets are in working directory (or update the file paths in the code if necessary):

- sp_data.csv.gz (Spark data)
- vf_data.parquet (Vodafone data)
- sa2_2023.csv (SA2 concordance file)
- urban_rural_to_indicator_2023.csv (Urban/Rural Indicator)
- urban_rural_to_sa2_concord_2023.csv (Urban/Rural Concordance)

3. Run the Scripts in the following order

01.  01_load_clean_data.R: This script loads the Spark and Vodafone data, cleans the columns, handles missing values, and processes              timestamps
     Output: Cleaned Spark and Vodafone data.
02.  02_merge_sa2_data.R: This script merges the cleaned data with the SA2 concordance and urban/rural indicator datasets.
     Output: Population data with geographical information.
03.  03_aggregate_population_data.R: This script aggregates the population data by SA2 code and timestamp, calculating the total population      counts.
     Output: Aggregated population data.
04.  04_export_final_data.R: This script exports the final cleaned dataset as a gzipped CSV file.
     Output: final_combined_data_with_regions.csv.gz.


4. Expected output

After running all scripts, the final dataset (final_combined_data_with_regions.csv.gz) will contain:

- SA2 codes
- Timestamps
- Total population counts (from both Spark and Vodafone data)
- Geographical region information (urban/rural indicators)




