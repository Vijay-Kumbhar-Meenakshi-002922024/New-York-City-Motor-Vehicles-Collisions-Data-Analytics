# New-York-City-Motor-Vehicles-Collisions-Data-Analytics

## Problem Statement

Developed and built a data engineering solution that could integrate, process, and load this dataset from the NYC Open Data portal and the NYPD website into a consolidated data warehouse so that data analysts and scientists can quickly access and study it. In order to handle growing data volumes and a variety of data kinds while maintaining data integrity and adhering to data protection laws, the solution must be scalable, resilient, and secure. This data engineering solution's overarching objective is to empower our organization to make data-driven decisions, enhance customer engagement, and foster business expansion. It is possible for the general public to access statistical data on auto accidents. The data is updated on a monthly basis, and grouped by borough intersections, bridges, and tunnels.

## Key Takeaways

Built a data engineering pipeline that included data extraction, data cleansing, transformation, exploratory analysis, data visualization, and data flow orchestration of event data on the cloud, I used data from the NYC Open Data portal and NYPD Public Data to analyze the automobile and traffic accidents occurring in New York City.

## Dataset

**New York City Traffic Data/Motor Vehicle Collisions** - The project uses a variety of data sources, such as Open Data from crashes, vehicles, and people, as described below. The same data source provides all of the datasets and the data on motor vehicle collisions.

- [Motor Vehicle Collisions - Crashes](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95) - Details about the crash incident are available in the Motor Vehicle Collisions crash dataset. A crash occurrence is represented by each row. All police reports of motor vehicle collisions in NYC are included in the Motor Vehicle Collisions statistics. For collisions involving injuries, fatalities, or property damage totaling at least $1,000, a police report (MV104-AN) must be filed (https://www.nhtsa.gov/sites/nhtsa.dotgov/files/documents/ny_overlay_mv-104an_rev05_2004.pdf). It should be noted that the information is provisional and is subject to modification when the MV-104AN forms are updated in light of updated crash information.
  
- [Motor Vehicle Collisions - Vehicles](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Vehicles/bm4k-52h4) - Each vehicle involved in the collision is described in the Motor Vehicle Collisions vehicle dataset. A motor vehicle engaged in a collision is represented by each row. When crash reporting transitioned to an electronic method in April 2016, the data in this dataset began to accumulate.

- [Motor Vehicle Collisions - Person](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Person/f55k-p6yu) - The Motor Vehicle Collisions person dataset includes information on those who were in the accident. Each row represents a crash victim (driver, passenger, pedestrian, bicyclist, etc.). When crash reporting transitioned to an electronic system in April 2016, the data in this source began to accumulate.

## Data Description

This dataset consists of below metadata information:

|              Data Source             |   Rows   |   Columns   |  Update Frequency |   File Format  |
|:------------------------------------:|:--------:|:-----------:|:-----------------:|:--------------:|
|               Crashes                |   1.95M  |       29    |       Daily       |      csv       |
|               Vehicles               |   3.705M |       25    |       Daily       |      csv       |
|               Persons            	   |   4.90M  |       21    |       Daily       |      csv       |

## Tools 

Below tools have been utilized for the various segments involving Data Profiling, Modeling, Integration and BI Reporting and Visualizations:

<p align="center">
<img src="Img/Tools.png" alt="Tools">
</p>

# Data Modeling

This project utilizes ER/Studio Data Architect's potential for designing, illustrating, and overseeing data models and metadata within the database. ER/Studio has enabled the creation of conceptual, logical, and physical data models, facilitating the mapping of relationships and dependencies among them. The approach to data modeling has followed an iterative process involving design, reviews, feedback, and improvements, all aligned with the needs of the business and end-users.

<p align="center">  
  <br>
	<a href="#">
        <img src="Img/DimModel.jpg"> 
  </a>		
    <br>
	Dimensional Data Model - New York City Motor Vehicles Collisions
</p>
<br>

## Data Integration / ETL Pipeline

In this project, data is analysed, profiled, transformed and loaded into Microsoft SQL server by Talend and Alteryx. Data is collected from BigQuery and flat files (csv/tsv) and is moved to landing zones (Stage) in SQL Server.

The ETL process involved 2 layer of data landing, transformation and loading.
- **Landing or Staging Data Layer**: The data is extracted form source and staged into the SQL Server database. Here the main focus is to land the data from source with minimal transformation (as-is data load). Also, ETL Audit fields such as DI_PID, DI_Create_Date etc. were added to identify newly loaded or updated records by using audit columns.

	|              Schema                      |             Table  	   |
	|:----------------------------------------:|:-----------------------------:|
	|               NYC_MV                |    STG_NYC_MV_COLLISIONS_BIGQUERY  |
	|               NYC_MV                |    STG_NYC_MV_COLLISION_VEHICLES   |
	|               NYC_MV                |    STG_NYC_MV_COLLISION_PERSONS    |


	
