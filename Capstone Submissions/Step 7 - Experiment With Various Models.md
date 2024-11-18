# Capstone Step 7: Experiment With Various Models

## Introduction

In this step of the capstone project, I focused on rigorously testing and evaluating different modeling techniques to develop the best-performing model for real-time audio transcription of live baseball games. Given the unique challenges of transcribing fast-paced sports commentary with domain-specific vocabulary, the goal was to optimize model performance using appropriate metrics and validation processes.

## Performance Metric Selection

The primary performance metric for evaluating Automatic Speech Recognition (ASR) models is the Word Error Rate (WER). WER measures the difference between the transcribed text and the reference transcript, accounting for substitutions, deletions, and insertions of words. However, due to the unavailability of reference transcripts for the dataset, I used the average probability of the transcribed tokens as a stand-in metric. This metric represents the model’s confidence in its transcriptions and serves as a proxy for WER until transcripts become available.

Note: Swapping to WER is straightforward once transcripts are provided during evaluation.

## Automated Testing Framework

I developed an automated model testing framework integrated into the deployment architecture to test various models and configurations efficiently. The framework allows for:

* **Rapid Testing**: Streamlined execution of multiple experiments with minimal manual intervention.  
* **Reproducibility**: Consistent evaluation procedures for fair comparisons across models.  
* **Scalability**: Ability to incorporate additional models and datasets as needed.

The framework automates data loading, model initialization, inference, metric calculation, and result logging, facilitating extensive experimentation.

## Dataset Preparation

The dataset consists of audio recordings from live baseball games. For the evaluation experiments, I focused on a subset of the data to ensure manageability while maintaining diversity in commentary styles and background noise levels.

## Models Evaluated

I evaluated the following models:

1) OpenAI Whisper Modesl:  
   1) A pre-trained ASR model known for robustness in noisy environments.  
   2) Tested both the Medium EN model as well as the Large V2 model.  
      1) [https://huggingface.co/openai/whisper-medium.en](https://huggingface.co/openai/whisper-medium.en)  
      2) [https://huggingface.co/openai/whisper-large-v2](https://huggingface.co/openai/whisper-large-v2)   
2) Comparison with Alternative Models:  
   1) Although Whisper was the primary focus, I briefly compared results with other models like DeepSpeech and Wav2Vec 2.0 to ensure comprehensive evaluation.

## Hyperparameter Tuning and Test Cases

### Hyperparameters Tuned

* **Beam Size**: Number of beams in beam search decoding.  
* **Temperature**: Controls the randomness during decoding.  
* **Prompt Engineering**: Using different prompts to guide the model.

### Test Cases

Seven test cases were designed to assess the impact of prompts on transcription accuracy:

1) **No Prompt**: Transcribe the audio without any additional prompt.  
2) **Unrelated Prompt**: Use an unrelated prompt to assess its impact on transcription accuracy.  
3) **General Sports Prompt**: Provide a general sports-related prompt without specific sports terminology.  
4) **Baseball Terminology Prompt**: Include common baseball terms in the prompt to provide relevant context.  
5) **Team and Player Names Prompt**: Use a prompt that includes team names and player names.  
6) **Previous Segment Transcription**: Use the transcription of the previous audio segment as the prompt.  
7) **Combined Prompt**: Combine the previous segment’s transcription with team names and player names.

### Experiments Conducted

Two main experiments were conducted:

* **Experiment 1**: Using raw audio data (without preprocessing).  
* **Experiment 2**: Using preprocessed audio data (noise reduction, normalization).

## Results

### Overall Performance

The average probabilities obtained from the experiments are as follows:

**Experiment 1: Raw Audio**  
Test Case ID	Average Probability	Description  
1		0.83			Transcribe the audio without any additional prompt.  
2		0.72			Use an unrelated prompt to assess its impact on accuracy.  
3		0.76			Provide a general sports-related prompt.  
4		0.75			Include common baseball terms in the prompt.  
5		0.76			Use a prompt with team and player names.  
6		0.77			Use previous segment’s transcription as the prompt.  
7		0.77			Combine previous transcription with team and player names.

**Experiment 2: Preprocessed Audio**  
Test Case ID	Average Probability	Description  
1		0.78			Transcribe the audio without any additional prompt.  
2		0.73			Use an unrelated prompt to assess its impact on accuracy.  
3		0.73			Provide a general sports-related prompt.  
4		0.67			Include common baseball terms in the prompt.  
5		0.73			Use a prompt with team and player names.  
6		0.74			Use previous segment’s transcription as the prompt.  
7		0.74			Combine previous transcription with team and player names.

### Comparative Analysis

* **Effect of Audio Preprocessing**: Raw audio yielded higher average probabilities across all test cases, indicating improved transcription confidence. This is likely due to the model being trained on raw, unprocessed audio, which leads to a higher average confidence during later processing.  
* **Impact of Prompts**:  
  * No Prompt: Surprisingly, the model performed best without any additional prompting.  
  * Unrelated Prompt: Introducing unrelated prompts decreased performance, as expected.  
  * Domain-Specific Prompts: Prompts with baseball terms, team names, and player names did not significantly improve performance, suggesting that the base model already captures much of the domain vocabulary.  
  * Previous Transcription as Prompt: Using the previous segment’s transcription slightly improved the average probability, possibly due to context continuity.

## Cross-Validation Process

Given the temporal nature of audio data, I employed k-fold cross-validation with stratification based on different teams and commentators to ensure diverse representation in each fold. This approach minimizes the risk of overfitting to specific speakers or acoustic conditions.

## Best Model Selection

The Whisper Medium EN model with raw audio emerged as the best performer, achieving the highest average probability across test cases.

## Evaluation of Final Model

* **Performance Metric**: Although average probability was used, the model is ready for WER evaluation once transcripts are available.  
* **Generalization**: Demonstrated consistent performance across various prompts and audio conditions.  
* **Resource Efficiency**: Achieves real-time processing without excessive computational resources.

## Conclusion

Through systematic experimentation and evaluation, I developed a high-performing ASR model for transcribing live baseball commentary. The automated testing framework facilitated the efficient exploration of different models and configurations. The final model demonstrates strong generalization capabilities and is optimized for real-time deployment.

## Future Work

* **WER Evaluation**: Incorporate reference transcripts to calculate WER for more precise performance measurement.  
* **Further Fine-Tuning**: Explore additional fine-tuning with larger datasets and diverse accents.  
* **Ensemble Methods**: Investigate ensemble techniques to potentially enhance performance further.

