# ETL Pipeline with Jenkins

This project contains a Jenkinsfile for an Extract, Transform, Load (ETL) pipeline, designed to streamline data processing workflows.

## Overview

The pipeline is structured to perform the following steps:

1. **Environment Setup**: Specifies the execution environment, indicating the target environment for the data processing tasks.
2. **Extraction**: Extracts data from multiple sources. It includes parallel stages for extracting data from different sources concurrently.
3. **Transformation**: Applies data transformation operations, such as cleaning, filtering, and aggregating the extracted data.
4. **Loading**: Loads the transformed data into the target destination, such as a database or data warehouse.
5. **Input Check**: Prompts the user to verify if the data has been loaded correctly.
6. **Ambient Check**: Indicates the environment in which the pipeline is running, especially useful when deploying to different environments like development, testing, or production.
7. **Post-Execution Cleanup**: Ensures workspace cleanup after the pipeline execution, maintaining a clean environment for subsequent runs.

## Usage

To use this pipeline:

1. Configure the Jenkins job to point to this repository.
2. Customize the pipeline parameters and options as per your requirements.
3. Run the pipeline to execute the ETL tasks.

## Requirements

- Jenkins server
- Jenkins Pipeline plugin
