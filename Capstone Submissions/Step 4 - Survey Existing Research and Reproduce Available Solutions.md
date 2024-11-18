# Capstone Step 4: Survey Existing Research and Reproduce Available Solutions

## Instructions

Before starting to write any code and build your first model prototype for your Capstone, you will attempt to locate published research around or on the topic of your Capstone project. The goal is to understand what other researchers/engineers have built to solve a similar problem and reproduce their results when they publicly share their code. After you do this, discuss the results with your mentor and try to agree on the path/approach you will take to build your first prototype.

## Final List

**Fine-Tune Whisper For Multilingual ASR with 🤗 Transformers**

- [https://colab.research.google.com/drive/1bcf5oivXvKbLv9VUxfg-\_piILyHypIQm](https://colab.research.google.com/drive/1bcf5oivXvKbLv9VUxfg-_piILyHypIQm) 

**QLoRA: Efficient Fine-Tuning of Language Models**

- This project shows how to use QLoRA for low-rank adaptation of language models.  
- [GitHub \- huggingface/peft (QLoRA)](https://github.com/huggingface/peft)  
- [https://colab.research.google.com/drive/1vIjBtePIZwUaHWfjfNHzBjwuXOyU\_ugD?usp=sharing](https://colab.research.google.com/drive/1vIjBtePIZwUaHWfjfNHzBjwuXOyU_ugD?usp=sharing)  
- [https://colab.research.google.com/drive/1DOkD\_5OUjFa0r5Ik3SgywJLJtEo2qLxO?usp=sharing](https://colab.research.google.com/drive/1DOkD_5OUjFa0r5Ik3SgywJLJtEo2qLxO?usp=sharing)

**Hugging Face Optimum for Model Quantization**

- This repository offers tools for quantizing transformer models, including ASR models.  
- [https://medium.com/@daniel-klitzke/quantizing-openais-whisper-with-the-huggingface-optimum-library-30-faster-inference-64-36d9815190e0](https://medium.com/@daniel-klitzke/quantizing-openais-whisper-with-the-huggingface-optimum-library-30-faster-inference-64-36d9815190e0)   
- [GitHub \- huggingface/optimum](https://github.com/huggingface/optimum)  
- Potentially this NVIDIA specific fork  
  - [https://github.com/huggingface/optimum-nvidia](https://github.com/huggingface/optimum-nvidia)

**Distil-Whisper**

- [https://github.com/huggingface/distil-whisper?tab=readme-ov-file](https://github.com/huggingface/distil-whisper?tab=readme-ov-file)  
- [https://github.com/huggingface/distil-whisper/tree/main/training](https://github.com/huggingface/distil-whisper/tree/main/training)   
- [https://huggingface.co/distil-whisper](https://huggingface.co/distil-whisper)   
- [https://colab.research.google.com/github/sanchit-gandhi/notebooks/blob/main/Distil\_Whisper\_Benchmark.ipynb](https://colab.research.google.com/github/sanchit-gandhi/notebooks/blob/main/Distil_Whisper_Benchmark.ipynb) 

## First Pass

### To Reproduce

**whisper/notebooks/LibriSpeech.ipynb**

- [https://github.com/openai/whisper/blob/main/notebooks/LibriSpeech.ipynb](https://github.com/openai/whisper/blob/main/notebooks/LibriSpeech.ipynb)   
- BRETT: YES  
- DAVID: NO on 2nd pass

**Fine-Tune Whisper For Multilingual ASR with 🤗 Transformers**

- [https://colab.research.google.com/drive/1bcf5oivXvKbLv9VUxfg-\_piILyHypIQm](https://colab.research.google.com/drive/1bcf5oivXvKbLv9VUxfg-_piILyHypIQm)   
- BRETT: YES  
- DAVID: YES

**Whisper Fine Tuning demo**

- [https://colab.research.google.com/drive/1pFQWdun9QoiXc-ww4h7o2oMfCsgPrGgQ](https://colab.research.google.com/drive/1pFQWdun9QoiXc-ww4h7o2oMfCsgPrGgQ)   
- BRETT: YES  
- DAVID: NO on 2nd pass

**Whisper Large inference in 8-bit mode**

- [https://huggingface.co/blog/hf-bitsandbytes-integration](https://huggingface.co/blog/hf-bitsandbytes-integration)  
- [https://colab.research.google.com/drive/1EMOwwfm1V1fHxH7eT1LLg7yBjhTooB6j?usp=sharing](https://colab.research.google.com/drive/1EMOwwfm1V1fHxH7eT1LLg7yBjhTooB6j?usp=sharing)  
- BRETT: YES  
- DAVID: NO on 2nd pass

**Distil-Whisper large-v3 German**

- [https://huggingface.co/sanchit-gandhi/distil-whisper-large-v3-de-kd\#training-procedure](https://huggingface.co/sanchit-gandhi/distil-whisper-large-v3-de-kd#training-procedure)   
- DAVID: MAYBE

### Do Not Reproduce

**BALLGAME: A Corpus for Computational Semantics**

- [https://aclanthology.org/W11-0139.pdf](https://aclanthology.org/W11-0139.pdf)   
- No code available. Provided are the final paper and raw transcripts, but nothing to reproduce.

**Whisper Medium FLEURS Language Identification (deepspeed)**

- [https://huggingface.co/sanchit-gandhi/whisper-medium-fleurs-lang-id](https://huggingface.co/sanchit-gandhi/whisper-medium-fleurs-lang-id)  
- Not as relevant to my capstone as the ones above

**whisper/notebooks/Multilingual\_ASR.ipynb**

- [https://github.com/openai/whisper/blob/main/notebooks/Multilingual\_ASR.ipynb](https://github.com/openai/whisper/blob/main/notebooks/Multilingual_ASR.ipynb)   
- DAVID: NO

**Calculating WERs using Kincaid46 ([Speechmatics](https://www.speechmatics.com/company/articles-and-news/introducing-ursa-the-worlds-most-accurate-speech-to-text))**

- [https://colab.research.google.com/drive/1B8BtVepMyvlFuQQyv87AWKn\_UNkav6xu?usp=sharing](https://colab.research.google.com/drive/1B8BtVepMyvlFuQQyv87AWKn_UNkav6xu?usp=sharing)   
- DAVID: NO \- remember jiwer

## For Reference

**Whisper Fine-Tuning Event 🤗**

- [https://github.com/huggingface/community-events/tree/main/whisper-fine-tuning-event](https://github.com/huggingface/community-events/tree/main/whisper-fine-tuning-event) 

**whisperX**

- [https://github.com/m-bain/whisperX](https://github.com/m-bain/whisperX) 

**distil-whisper**

- [https://github.com/huggingface/distil-whisper](https://github.com/huggingface/distil-whisper) 

**How to prepare a speech recognition dataset using YouTube videos?**

- [https://tehreemfarooqi.medium.com/how-to-prepare-a-speech-recognition-dataset-using-youtube-videos-8aeefc663e43](https://tehreemfarooqi.medium.com/how-to-prepare-a-speech-recognition-dataset-using-youtube-videos-8aeefc663e43)   
- [https://github.com/TehreemFarooqi/Preparing-a-speech-recognition-dataset-using-YouTube-videos/blob/main/Data%20Preparation.ipynb](https://github.com/TehreemFarooqi/Preparing-a-speech-recognition-dataset-using-YouTube-videos/blob/main/Data%20Preparation.ipynb)   
- I will need to reproduce this or something similar to get more audio for the capstone. However, it does not seem necessary to reproduce it for this submission.

**TehreemFarooqi DeepSpeech-Transfer-Learning-for-local-languages**

- [https://github.com/TehreemFarooqi/DeepSpeech-Transfer-Learning-for-local-languages/blob/main/Transfer\_learning\_DeepSpeech.ipynb](https://github.com/TehreemFarooqi/DeepSpeech-Transfer-Learning-for-local-languages/blob/main/Transfer_learning_DeepSpeech.ipynb)   
- Doesn’t feel directly relevant to reproduce. Am keeping it for potential reference purposes in the future.

## Second Pass

Below are five resources each for model fine-tuning, pruning, quantization, and knowledge distillation, with a focus on inference optimization on edge devices and, where possible, targeting speech-to-text / ASR models such as Whisper.

### Model Fine-Tuning

**QLoRA: Efficient Fine-Tuning of Language Models**

- This project shows how to use QLoRA for low-rank adaptation of language models.  
- [GitHub \- huggingface/peft (QLoRA)](https://github.com/huggingface/peft)  
- [https://colab.research.google.com/drive/1vIjBtePIZwUaHWfjfNHzBjwuXOyU\_ugD?usp=sharing](https://colab.research.google.com/drive/1vIjBtePIZwUaHWfjfNHzBjwuXOyU_ugD?usp=sharing)  
- [https://colab.research.google.com/drive/1DOkD\_5OUjFa0r5Ik3SgywJLJtEo2qLxO?usp=sharing](https://colab.research.google.com/drive/1DOkD_5OUjFa0r5Ik3SgywJLJtEo2qLxO?usp=sharing)  
- BRETT: Yes  
- DAVID: Yes

**Fine-Tuning Whisper ASR with Hugging Face Transformers**

- This repository provides scripts for fine-tuning Whisper models for ASR tasks.  
- [GitHub \- huggingface/transformers (Whisper)](https://github.com/huggingface/transformers/tree/main/examples/pytorch/speech-recognition)  
- BRETT: MAYBE. Appears similar to the the links above.  
- DAVID: NO

**DeepSpeed?**

- BRETT: I can’t find any ASR / Whisper examples that utilize DeepSpeed  
- DAVID: NO

**Efficient Fine-Tuning with AdapterFusion**

- This example demonstrates using AdapterFusion to fine-tune large models efficiently.  
- [GitHub \- AdapterHub/adapter-transformers](https://github.com/Adapter-Hub/adapter-transformers)  
- BRETT: No. It doesn’t seem relevant.  
- DAVID: NO

### Model Pruning

**Structured Pruning of ASR Models**

- This repository explores structured pruning methods to optimize ASR models.  
- [https://developer.nvidia.com/tao-toolkit](https://developer.nvidia.com/tao-toolkit)  
- BRETT: Might be too much for this assignment.  
- DAVID: No. The toolkit is quite comprehensive. We only need one use case, but we have enough already.

**Magnitude-Based Pruning for Speech Recognition**

- BRETT: No examples utilizing magnitude-based pruning techniques for speech recognition models.  
- DAVID: NO

**Pruning with PyTorch**

- BRETT: No examples utilizing PyTorch.  
- DAVID: NO

**LTH for Whisper ASR Model**

- BRETT: No examples utilizing Lottery Ticket Hypothesis (LTH)  
- DAVID: NO

**SparseML: Model Pruning for Efficient Inference**

- This toolkit includes various pruning techniques for optimizing model inference.  
- [GitHub \- NeuralMagic/sparseml](https://github.com/NeuralMagic/sparseml)  
- BRETT: NO because SparseML appears to only work on CPUs  
- DAVID: NO

### Model Quantization

**Intel Neural Compressor: Quantization for ASR Models**

- This tool provides quantization methods to optimize ASR models for edge devices.  
- [GitHub \- intel/neural-compressor](https://github.com/intel/neural-compressor)  
- BRETT: This seems relevant  
- DAVID: No (only because I think that the following option is a better one)

**Hugging Face Optimum for Model Quantization**

- This repository offers tools for quantizing transformer models, including ASR models.  
- [https://medium.com/@daniel-klitzke/quantizing-openais-whisper-with-the-huggingface-optimum-library-30-faster-inference-64-36d9815190e0](https://medium.com/@daniel-klitzke/quantizing-openais-whisper-with-the-huggingface-optimum-library-30-faster-inference-64-36d9815190e0)   
- [GitHub \- huggingface/optimum](https://github.com/huggingface/optimum)  
- Potentially this NVIDIA specific fork  
  - [https://github.com/huggingface/optimum-nvidia](https://github.com/huggingface/optimum-nvidia)  
- BRETT: This seems relevant  
- DAVID: Yes

**Faster and Smaller Whisper: A Deep Dive into Quantization and Torch Compilation**

- In this blog post, we explain the techniques we used to enhance the performance of the PyTorch-based Whisper models by leveraging transformers, implementing a static cache, and utilizing torch.compile.  
- [https://mobiusml.github.io/whisper-static-cache-blog/](https://mobiusml.github.io/whisper-static-cache-blog/)   
- BRETT: YES  
- DAVID: No (Just because of the better option in this section)

**Whisper.cpp**

- whisper.cpp is an implementation of OpenAI’s Whisper automatic speech recognition (ASR) model, designed to be efficient and run on various hardware platforms  
- [https://github.com/ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp)   
- BRETT: GGML seems relevant?  
- DAVID: No (Just because of the better option in this section)

**Faster Whisper transcription Model Conversion to CTranslate2**

- faster-whisper is a reimplementation of OpenAI's Whisper model using CTranslate2, which is a fast inference engine for Transformer models.  
- [https://github.com/SYSTRAN/faster-whisper/blob/master/README.md\#model-conversion](https://github.com/SYSTRAN/faster-whisper/blob/master/README.md#model-conversion)   
- BRETT: Seems relevant  
- DAVID: No (Just because of the better option in this section)

**TensorFlow Model Optimization Toolkit**

- This toolkit supports various quantization techniques for TensorFlow models.  
- [GitHub \- tensorflow/model-optimization](https://github.com/tensorflow/model-optimization)  
- BRETT: This seems relevant but I am not sure if Keras and TF are relevant.  
- DAVID: TF and Keras are relevant DL frameworks, but there are better options in this case.

**Diving deeper into Quantization Realm : Introduction to PTQ and QAT**

- [https://iprathore71.medium.com/diving-deeper-into-quantization-realm-9c73e3172a3c](https://iprathore71.medium.com/diving-deeper-into-quantization-realm-9c73e3172a3c)   
- [https://huggingface.co/docs/optimum/v1.21.2/intel/openvino/optimization](https://huggingface.co/docs/optimum/v1.21.2/intel/openvino/optimization)   
- BRETT: QAT seems promising but I can’t find anything to replicate.  
- DAVID: NO

### Knowledge Distillation

**Distil-Whisper**

- [https://github.com/huggingface/distil-whisper?tab=readme-ov-file](https://github.com/huggingface/distil-whisper?tab=readme-ov-file)  
- [https://github.com/huggingface/distil-whisper/tree/main/training](https://github.com/huggingface/distil-whisper/tree/main/training)   
- [https://huggingface.co/distil-whisper](https://huggingface.co/distil-whisper)   
- [https://colab.research.google.com/github/sanchit-gandhi/notebooks/blob/main/Distil\_Whisper\_Benchmark.ipynb](https://colab.research.google.com/github/sanchit-gandhi/notebooks/blob/main/Distil_Whisper_Benchmark.ipynb)   
- BRETT: Seems relevant  
- DAVID: YES

**Speechcatcher**

- Speechcatcher is an open source toolbox for transcribing and translating speech from media files (audio/video). Speechcatcher models are trained using whisper as teacher and offer compact and small ASR models that run fast on CPUs too.  
- [https://github.com/speechcatcher-asr/speechcatcher](https://github.com/speechcatcher-asr/speechcatcher)  
- BRETT: Produces Kaldi format. Kaldi is significantly worse than Whisper.  
- DAVID: NO

**Speeding Up Text-To-Speech Diffusion Models by Distillation**

- This project provides a framework for distilling speech recognition models.  
- [https://developer.nvidia.com/blog/speeding-up-text-to-speech-diffusion-models-by-distillation/](https://developer.nvidia.com/blog/speeding-up-text-to-speech-diffusion-models-by-distillation/)   
- BRETT: No code available  
- DAVID: NO

