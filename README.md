# UCSD ML/AI Capstone Project: Audio Data Download and ASR Model Transcription Testing

## Table of Contents

- [UCSD ML/AI Capstone Project: Audio Data Download and ASR Model Transcription Testing](#ucsd-mlai-capstone-project-audio-data-download-and-asr-model-transcription-testing)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Ideation and Development Process](#ideation-and-development-process)
    - [Project Ideation](#project-ideation)
    - [Research and Exploration](#research-and-exploration)
    - [Data Collection and Preprocessing](#data-collection-and-preprocessing)
    - [Model Testing Framework](#model-testing-framework)
    - [Deployment Strategy](#deployment-strategy)
    - [Final Implementation and Deployment](#final-implementation-and-deployment)
  - [Repositories Overview](#repositories-overview)
    - [yt\_dlp\_async](#yt_dlp_async)
    - [whisper\_chunk\_transcribe](#whisper_chunk_transcribe)
  - [Capstone Submission Process](#capstone-submission-process)
  - [Conclusion](#conclusion)

## Introduction

This project represents the culmination of my work for the UCSD ML/AI Capstone course, where the goal was to build a robust framework for testing Automatic Speech Recognition (ASR) models on audio data derived from YouTube and ESPN. The capstone project is divided into two main components: 

1. **Audio Data Download and Preprocessing**  
2. **ASR Model Transcription Testing Framework**

The primary objective was to improve the accuracy and efficiency of ASR models in transcribing baseball game commentary, using a custom dataset derived from YouTube and ESPN APIs.

## Ideation and Development Process

### Project Ideation

The initial concept for the capstone project emerged from the challenge of enhancing the real-time transcription of live audio, particularly in the sports domain. While ASR models like Whisper from OpenAI have demonstrated impressive results, one of the main limitations is the handling of proper nouns, event-specific jargon, and domain-specific vocabulary—especially when transcribing live commentary.

To address this, the project aimed to:

- **Download relevant audio data** from YouTube and ESPN, focusing on baseball commentary and related events.
- **Preprocess the data** to ensure it was properly cleaned, segmented, and aligned for transcription.
- **Implement a testing framework** to evaluate ASR model performance, specifically focusing on transcription accuracy, word error rates (WER), and the model's handling of domain-specific vocabulary.

### Research and Exploration

In the early stages, I conducted a survey of existing research and explored available solutions for improving ASR models. This involved experimenting with fine-tuning techniques and leveraging pre-trained models like OpenAI's Whisper. I also explored methods for efficiently collecting and processing large datasets, particularly from video sources like YouTube, to ensure data quality and consistency.

**Key Research Topics:**

- Fine-tuning Whisper for multilingual ASR
- QLoRA (Quantized Low-Rank Adaptation) to efficiently fine-tune large language models
- Existing work on ASR models in the sports domain, particularly baseball commentary

### Data Collection and Preprocessing

The data collection phase involved gathering approximately 350,000 baseball-related videos from YouTube using the `yt-dlp` library. Videos were filtered to ensure they were full-length games, in English, and included accurate metadata.

Once the data was collected, preprocessing tasks included:

- **Filtering and Normalization:** Ensuring consistent metadata across the dataset.
- **Cleaning:** Removing duplicates and handling missing data.
- **Audio Extraction:** Extracting audio from the video content and segmenting it for model input.

For this, I wrote the **yt_dlp_async** repository from scratch, which facilitates downloading YouTube videos asynchronously, along with helper functions for audio extraction and metadata management. [More details about this repository can be found here.](https://github.com/brettdavies/yt_dlp_async)

### Model Testing Framework

To evaluate the performance of ASR models, I created a testing framework that would allow for:

1. **Model Evaluation:** Comparing transcription results against a set of ground truth data, calculated as word error rate (WER) and accuracy.
2. **Dynamic Prompt Generation:** Incorporating domain-specific vocabulary into the prompts for Whisper, ensuring better performance on sports-related jargon.
3. **Segmented Audio Testing:** Splitting longer audio files into smaller chunks for efficient processing and evaluation.

This testing framework was built using the **whisper_chunk_transcribe** repository, which processes audio data and evaluates ASR model performance. [More details about this repository can be found here.](https://github.com/brettdavies/whisper_chunk_transcribe)

### Deployment Strategy

To deploy the model testing framework and ensure it could be used by others, I adopted several strategies:

- **Open-source Distribution:** I made the source code available on GitHub, including comprehensive documentation and setup instructions.
- **Dockerization:** To ensure the environment was consistent across different systems, I containerized the entire framework using Docker, allowing others to run the project seamlessly.
- **Continuous Integration (CI):** Integrated automated tests using GitHub Actions to ensure that changes made to the codebase did not break the core functionality.

The goal was to make the deployment process as simple as possible, allowing other researchers or developers to replicate or extend the project. The deployment plan is fully documented in the **Step 9: Deployment Method** [here](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%209%20-%20Pick%20Your%20Deployment%20Method.md).

### Final Implementation and Deployment

The final deployment involved packaging the application as a Docker container, pushing it to Docker Hub for easy access, and providing clear instructions for installation and usage. I also ensured that the code was version-controlled in a GitHub repository, allowing for open collaboration and contributions.

## Repositories Overview

### yt_dlp_async

This repository handles the downloading and preprocessing of YouTube videos. It provides tools to:

- Download videos asynchronously
- Extract audio and metadata
- Clean and prepare data for further processing

Key features include:
- Asynchronous data collection
- Metadata extraction and filtering
- Integration with external databases for storage

For more information, visit the [yt_dlp_async](https://github.com/brettdavies/yt_dlp_async) repository.

### whisper_chunk_transcribe

This repository is focused on evaluating and testing ASR models, particularly OpenAI's Whisper. It allows for:

- Audio segmentation and transcription testing
- Dynamic prompt generation for model fine-tuning
- Logging and reporting of model performance metrics

Key features include:
- Transcription chunking and segment handling
- Integration with Whisper for ASR
- Performance evaluation based on WER and accuracy

For more information, visit the [whisper_chunk_transcribe](https://github.com/brettdavies/whisper_chunk_transcribe) repository.

## Capstone Submission Process

Throughout the development of the capstone, I submitted various interim steps to track my progress and ensure I was adhering to best practices. These included:

- **Step 1: Planning** - [Read the planning document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%201%20-%20Planning.md)
- **Step 3: Project Proposal** - [Read the project proposal](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%203%20-%20Project%20Proposal.md)
- **Step 4: Survey Existing Research and Reproduce Solutions** - [Read the research document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%204%20-%20Survey%20Existing%20Research%20and%20Reproduce%20Available%20Solutions.md)
- **Step 5: Data Wrangling & Exploration** - [Read the data wrangling document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%205%20-%20Data%20Wrangling%20%26%20Exploration.md)
- **Step 7: Experiment With Various Models** - [Read the experiment document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%207%20-%20Experiment%20With%20Various%20Models.md)
- **Step 9: Deployment Method** - [Read the deployment strategy document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%209%20-%20Pick%20Your%20Deployment%20Method.md)
- **Step 10: Deployment Solution Architecture** - [Read the solution architecture document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%2010%20-%20Design%20Your%20Deployment%20Solution%20Architecture.md)
- **Step 11: Deployment Implementation** - [Read the implementation document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%2011%20-%20Deployment%20Implementation.md)
- **Step 12: Share Your Project with the World** - [Read the sharing document](https://github.com/brettdavies/ucsd-ml-ai-capstone/blob/main/Capstone%20Submissions/Step%2012%20-%20Share%20Your%20Project%20with%20the%20World.md)

Each of these steps documents the iterative process of building, testing, and deploying the model testing framework.

## Conclusion

This capstone project represents a comprehensive effort to enhance real-time transcription of baseball game commentary using ASR models. Through iterative development, I created a robust framework for collecting and preprocessing audio data, fine-tuning ASR models, and evaluating their performance. The project is fully documented, with clear instructions for installation and deployment.

By sharing this project with the community, I hope to contribute to the ongoing development of ASR systems, particularly in the sports domain, and provide a valuable resource for other developers and researchers looking to improve transcription accuracy.

---

**Note:** This README serves as an overview of the entire capstone project. To dive deeper into any aspect of the development, please refer to the relevant markdown files and repositories linked throughout.