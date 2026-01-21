Climate Data Processing Tool
Overview

The Climate Data Processing Tool is a web-based application developed to facilitate efficient access, processing, and export of daily precipitation data derived from CMIP6 climate projections. The tool is designed to simplify the workflow of climate data extraction for researchers and practitioners by automating data retrieval, unit conversion, organization, and export into user-friendly formats.

The application integrates a Dash-based frontend with a Python backend powered by the Google Earth Engine (GEE) API, enabling seamless interaction with the NEX-GDDP-CMIP6 climate dataset.

Frontend Architecture

The frontend of the application is built using Dash, a Python framework for creating analytical web applications. Dash enables interactive user interfaces and is tightly integrated with Plotly for dynamic visualization, while leveraging Flask for backend communication.

Key Features

Station Input
Users can input station names along with their geographic coordinates (latitude and longitude), allowing precise extraction of climate data at point locations.

Scenario and Date Range Selection
The interface allows users to select available climate scenarios (e.g., Historical, SSP245, SSP585) and define custom date ranges for data extraction.

Climate Model Selection
A dropdown menu provides access to multiple CMIP6 climate models included in the dataset, enabling comparative analysis across models.

Data Download
After parameter selection, users can initiate data processing and download daily precipitation data in Excel-compatible format (.xlsx/.csv).

The frontend is designed to be intuitive and user-friendly, minimizing technical complexity for end users.

Backend Architecture

The backend of the Climate Data Processing Tool is implemented in Python, with direct integration of the Google Earth Engine (GEE) API. The system accesses the NEX-GDDP-CMIP6 dataset, which contains statistically downscaled CMIP6 climate projections at a spatial resolution of approximately 27–28 km, eliminating the need for additional downscaling.

Backend Workflow
Step 1: Data Retrieval

Upon user input, the backend connects to the GEE cloud platform and filters the NEX-GDDP-CMIP6 dataset based on:

Selected climate scenario

Selected climate model

Specified date range

Station coordinates

The Earth Engine platform enables efficient handling of large-scale climate datasets without local computational overhead.

Step 2: Data Processing

Precipitation data retrieved from the dataset is originally provided in units of kg/m²/s. To ensure practical usability, the backend automatically converts these values into millimeters per day (mm/day) using the following conversion:

mm/day = (kg/m²/s) × 86,400


This conversion is applied consistently across the selected date range.

Step 3: Data Organization

The processed precipitation data is systematically organized by date, ensuring a chronological daily time series. This structured format allows users to directly analyze temporal trends without additional data manipulation.

Step 4: Data Export

The finalized dataset is exported in CSV format, compatible with Excel and other data analysis tools. Each file is automatically named using the following convention:

<Model>_daily_<StationName>_<StartYear-EndYear>.csv


This naming structure ensures clarity and traceability of downloaded datasets.

Automation and Usability

A key strength of the application lies in its fully automated backend workflow. Users are not required to manually download, process, or convert climate data. By simply providing input parameters through the frontend interface, the system performs all required operations and delivers ready-to-use datasets.

This automation:

Reduces processing time

Minimizes user error

Improves reproducibility

Enhances accessibility for non-technical users

Intended Applications

The Climate Data Processing Tool is suitable for:

Climate change impact studies

Hydrological and flood modeling

Water resources assessment

Academic research and teaching

Climate scenario analysis
