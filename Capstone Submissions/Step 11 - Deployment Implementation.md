# Capstone Step 11: Deployment Implementation

## Introduction

This final article details the Deployment Implementation of the data collection and model testing framework applications, building upon the previously outlined deployment plan and architecture. The focus is on transforming production-ready code into fully deployed applications, ensuring all components function cohesively in a production environment. This includes implementing data pipelines, logging and monitoring, containerizing the application, and providing a well-documented command-line interface.

### GitHub Repository

The production-ready code is available in the following two public GitHub repositories:

[https://github.com/brettdavies/yt\_dlp\_async](https://github.com/brettdavies/yt_dlp_async)  
[https://github.com/brettdavies/whisper\_chunk\_transcribe](https://github.com/brettdavies/whisper_chunk_transcribe) 

The two repositories include comprehensive instructions in the README and docker.md documentation on how to install, build, and run the applications.

## Implementation Details

### Data Pipeline Implementation

**Data Acquisition Module**

* Functionality: Implements connectors to various data sources, including APIs, databases, and file systems.  
* Implementation:  
  * Developed classes for each data source type, following the Factory Design Pattern to instantiate the appropriate connector based on user input.  
  * Implemented asynchronous data fetching using asyncio to improve performance when concurrently retrieving data from multiple sources.  
* Storage:  
  * Raw data is stored in the /data directory, with a structured subdirectory system to organize data by source and date.  
  * Implemented checks to ensure data integrity during storage, using temporary storage and not moving to the final directory until the file is confirmed to have been downloaded completely.

**Data Processing Module**

* Functionality: Performs data cleaning, normalization, and feature extraction.  
* Implementation:  
  * Utilized Pandas and NumPy for data manipulation.  
  * Created a pipeline using Scikit-learn’s Pipeline class to chain processing steps, making adding or modifying steps easy.  
  * Supported custom processing functions, allowing users to plug in custom data transformation logic.  
* Storage:  
  * Processed data is stored in the /data/completed directory.  
  * Metadata about processing steps is saved alongside the data for reproducibility.

**Model Evaluation Module**

* Functionality: Evaluates user-provided machine learning models against the raw and processed data.  
* Implementation:  
  * Standardized evaluation metrics are implemented, including accuracy and confidence.  
    * Enabled users to define custom evaluation metrics.  
* Artifact Storage:  
  * Evaluation results are stored in the database.

### Logging and Monitoring

* Logging Framework: Used Loguru logging module configured with a custom formatter.  
* Log Levels:  
  * DEBUG: Detailed information, typically of interest only when diagnosing problems.  
  * INFO: Confirmation that things are working as expected.  
  * WARNING: An indication that something unexpected happened.  
  * ERROR: Due to a more serious problem, the application has not been able to perform some function.  
* Log Handlers:  
  * Console handler for real-time feedback.  
  * File handler to write logs to /logs/\[module name\].log.  
* Error Handling:  
  * Implemented try-except blocks with logging for exceptions.  
  * Provided meaningful error messages to the user, with suggestions for corrective actions.

### Containerization with Docker

* Docker Images:  
  * Created a Dockerfile for the applications using a lightweight Python base image (python:3.9-slim).  
  * Utilized multi-stage builds to optimize the final image size.  
* Docker Compose:  
  * Wrote a docker-compose.yml file to orchestrate the application’s services.  
* Volumes and Networking:  
  * Configured Docker volumes to persist data and logs outside of containers.  
  * Exposed necessary ports for database access.  
* Scripts:  
  * Provided shell scripts (docker-entrypoint.sh, run-in-docker.sh) to simplify Docker operations for the user.

## User Interface

### User Interface

* CLI Tool:  
  * Developed a command-line interface using Fire, allowing users to interact with the application without writing code.  
* Commands include ability to acquire, process, and evaluate.

### Testing and Validation

* Integration Tests:  
  * Tested the data flow between modules.  
  * Validated the end-to-end process from data acquisition through completion of model evaluation.

### Documentation

* README:  
  * Provided step-by-step instructions on installation, setup, and usage.  
  * Included examples of commands and expected outputs.  
* Code Documentation:  
  * Docstrings are used throughout the codebase.  
  * Documentation is hosted in the docs/ directory.  
* Tutorials:  
  * Provided a blog-style article in the repository’s /docs folder, explaining use cases and benefits.

## How to Run the Application

### Prerequisites

* Install Docker  
  * Docker Compose is optional  
* Ensure ports 5432, and 443 are available on your machine.

### Steps

	1\.	Clone the Repository  
	2\.	Access the Documentation  
	3\.	Build the Docker Image  
	4\.	Run the Application  
	5\.	Use the CLI  
	6\.	Stop the Application

## Code Organization and Documentation

* Project Structure:  
  * Below is the detailed folder structure for the yt\_dlp\_async repository:  
    yt\_dlp\_async/  
    ├── dist/  
    ├── docker/  
    │   ├── docker-compose.yml  
    │   ├── docker-entrypoint.sh  
    │   ├── docker.md  
    │   ├── Dockerfile  
    │   └── run-in-docker.sh  
    ├── docs/  
    │   └── (documentation files)  
    ├── yt\_dlp\_async/  
    │   ├── video\_id.py  
    │   ├── video\_metadata.py  
    │   ├── video\_file.py  
    │   ├── video\_download.py  
    │   ├── utils.py  
    │   ├── e\_events.py  
    │   ├── metadata.py  
    │   ├── db\_schema.sql  
    │   └── database.py  
    ├── .env  
    ├── LICENSE  
    ├── poetry.lock  
    ├── poetry.toml  
    ├── pyproject.toml  
    └── README.md  
      
  * Below is the detailed folder structure for the whisper\_chunk\_transcribe repository:  
    whisper\_chunk\_transcribe/  
    ├── dist/  
    ├── docker/  
    │   ├── docker-compose.yml  
    │   ├── docker-entrypoint.sh  
    │   ├── docker.md  
    │   ├── Dockerfile  
    │   └── run-in-docker.sh  
    ├── docs/  
    │   └── (documentation files)  
    ├── whisper\_chunk\_transcribe/  
    │   ├── audio\_processing.py  
    │   ├── database.py  
    │   ├── db\_populate\_data.sql  
    │   ├── db\_schema.sql  
    │   ├── espn\_database.py  
    │   ├── espn\_db\_schema.sql  
    │   ├── espn\_events.py  
    │   ├── experiment\_runner.py  
    │   ├── helper\_classes.py  
    │   ├── helper\_determine\_prompt\_length\_tokens.py  
    │   ├── helper\_player\_team\_names.py  
    │   ├── helper\_update\_prompt\_terms.py  
    │   ├── logger\_config.py  
    │   ├── metadata.py  
    │   ├── prepare\_audio.py  
    │   ├── process\_audio\_wrapper.py  
    │   ├── transcription\_processor.py  
    │   ├── transcription\_wrapper.py  
    │   └── utils.py  
    ├── .env  
    ├── poetry.lock  
    ├── poetry.toml  
    ├── pyproject.toml  
    ├── README.md  
    └── update\_whisper.sh

* Code Quality:  
  * Followed PEP 8 style guidelines.  
  * Used type hints for better readability and error checking.  
  * Included docstrings for all functions and classes.  
* Instructions:  
  * The README provides clear instructions on setting up the environment, running the application, and troubleshooting common issues.  
  * Configuration files are well-documented, with examples of config files provided.

## Conclusion

The data collection and model testing framework have been successfully deployed, transforming production-ready code into a functional application. By implementing robust data pipelines, comprehensive logging, containerization, and a user-friendly CLI, the framework is now accessible to users across different environments. The application is thoroughly documented, tested, and ready for use, aligning with best practices in software engineering and machine learning operations.

Note: For any issues or questions, please refer to the GitHub repository or open an issue for support.  
