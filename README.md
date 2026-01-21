# Climate Data Processing Tool

## Overview
The Climate Data Processing Tool is a web-based application designed to simplify the retrieval, processing, and export of daily precipitation data from CMIP6 climate projections. The tool automates climate data extraction and converts raw datasets into user-friendly formats, enabling researchers and practitioners to focus on analysis rather than data handling. The application integrates a Dash-based frontend with a Python backend powered by the Google Earth Engine (GEE) API to provide seamless access to the NEX-GDDP-CMIP6 dataset.

## Frontend Architecture
The frontend of the application is developed using Dash, a Python framework for building analytical web applications. Dash enables interactive user interfaces and integrates seamlessly with Plotly for interactive visualizations, while utilizing Flask for backend communication.

<img width="867" height="569" alt="image" src="https://github.com/user-attachments/assets/1e8094d4-81d4-47e5-941b-770dd249234c" />




### Key Features
- Station Input: Users can input station names along with their corresponding latitude and longitude coordinates for precise point-based climate data extraction.

<img width="916" height="558" alt="image" src="https://github.com/user-attachments/assets/c19516a5-7433-4e18-aca4-6b63a317c355" />



- Scenario and Date Range Selection: Users can select available climate scenarios such as Historical, SSP245, and SSP585 and specify a custom date range.

<img width="911" height="533" alt="image" src="https://github.com/user-attachments/assets/667d65fb-03b4-46ba-8e77-50a5606d3d59" />




- Climate Model Selection: A dropdown menu allows users to choose from multiple CMIP6 climate models available in the dataset.
<img width="915" height="549" alt="image" src="https://github.com/user-attachments/assets/afa4b226-0fe9-4cd2-ae61-aff7e1f540d5" />

- Data Download: Processed daily precipitation data can be downloaded in Excel-compatible formats (.xlsx or .csv).

<img width="827" height="500" alt="image" src="https://github.com/user-attachments/assets/758dd999-2d3f-4b70-a90f-94ceed3e3562" />


## Backend Architecture
The backend of the Climate Data Processing Tool is implemented in Python and integrated with the Google Earth Engine (GEE) API. The system accesses the NEX-GDDP-CMIP6 dataset, which contains statistically downscaled CMIP6 climate projections at a spatial resolution of approximately 27–28 km, eliminating the need for additional downscaling.

## Backend Workflow
Once the user selects the climate scenario, model, station location, and date range, the backend performs the following operations:

### Step 1: Data Retrieval
The backend connects to the Google Earth Engine cloud platform and filters the NEX-GDDP-CMIP6 dataset based on the selected scenario, climate model, date range, and station coordinates. Earth Engine efficiently handles large-scale climate data processing without local computational overhead.

### Step 2: Data Processing
Precipitation data retrieved from the dataset is originally provided in units of kg/m²/s. To ensure practical usability, the backend automatically converts the data into millimeters per day (mm/day) using the following conversion:

mm/day = (kg/m²/s) × 86,400


### Step 3: Data Organization
The processed precipitation data is organized into a chronological daily time series, ensuring that each precipitation value corresponds to its exact date within the selected time range. This structure allows users to directly analyze temporal precipitation trends without additional data manipulation.

### Step 4: Data Export
The finalized dataset is exported in CSV format, compatible with Excel and other data analysis tools. Each output file is automatically named using the following convention:

<Model>daily<StationName>_<StartYear-EndYear>.csv


## Automation and Usability
The entire backend workflow is fully automated. Users are not required to manually download, process, or convert climate datasets. By simply providing input parameters through the frontend interface, the system retrieves, processes, organizes, and exports the data in a ready-to-use format. This automation reduces processing time, minimizes human error, and improves reproducibility while maintaining ease of use for non-technical users.

## Intended Applications
The Climate Data Processing Tool is suitable for climate change impact studies, hydrological and flood modeling, water resources assessment, academic research, and climate scenario analysis.

## Summary
By combining an intuitive Dash-based frontend with a robust Google Earth Engine-powered backend, the Climate Data Processing Tool provides an efficient, reliable, and user-friendly solution for accessing and processing CMIP6 precipitation data. The application enables users to focus on scientific analysis and interpretation rather than technical data handling.
