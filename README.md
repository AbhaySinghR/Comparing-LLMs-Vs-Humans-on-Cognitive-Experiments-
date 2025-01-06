# LLM Memory Task Analysis


## Overview

This repository contains the implementation and results of an experiment designed to compare memory performance between humans and a Large Language Model (LLM), specifically LLaMA 3.1. The study evaluates various memory tasks such as free recall, cued recall, single recognition, and associative recognition to observe how closely the LLM mimics human responses. Below are the details of the experiment design, implementation, and findings.

Dataset: https://osf.io/dd8kp/

---

## Creating Task Blocks

### Task Design

For all the conditions or tasks that were administered to 462 human participants, corresponding task blocks were designed for the LLM. Each block represents a specific memory task and serves as a concise prompt to the model. Parameters such as temperature, `max_length`, and `max_new_tokens` were adjusted for each task to ensure accurate output generation based on the expected responses.

### Example Prompts

- **Free Recall Task:**
  - The prompt asks the model to memorize a set of words and then recall them without any cues.

![Example Prompt for Free Recall Task](image1.png)

- **Single Recognition Task:**
  - The prompt asks the model to recognize words from a list, distinguishing between previously studied words and new (foil) words. Each block is tailored for the respective task to test memory retention and recognition.

After creating individual blocks for each task, a combined block was constructed to simulate the experimental setup presented to human participants. The prompts for each condition were shuffled to introduce variability, similar to the human study.

---

## Running the Experiment

### Human Setup vs. LLM Setup

In the human study, participants were tested on 15 blocks, each consisting of five memory tasks. The LLM was subjected to a similar setup, looping through all 15 blocks to generate outputs for comparison with human results.

### Custom Parsers for Outputs

As LLMs often output extraneous text or repeat the prompt, custom parsers were created for each memory task to extract only the relevant answers. For example:

- **Free Recall Task:** The parser filters out repetitions and extraneous explanations, focusing solely on the recalled words.
- Prompts were designed to be concise to minimize garbage outputs and improve decoding.

**Reference:** [Hugging Face Discussion](https://discuss.huggingface.co/t/llama-2-7b-hf-repeats-context-of-question-directly-from-input-prompt-cuts-off-with-newlines/48250)

![Example Output Parser](image2.png)

---

## Comparison of Results: Humans vs. LLaMA

### Free Recall Task

For a sample of participants (Subjects 1-5) and all 15 blocks:
- **Human Results:** Dataframes containing human responses were used for comparison.
- **Model Results:** LLaMA outputs were processed and scored, penalizing spelling mistakes.

#### Observations

- The LLM performed better at recalling words than humans for the selected sample, even after penalizing spelling errors.

![Human Free Recall Results](humans_free_recall.png)  
![LLaMA Free Recall Results](llama_free_recall.png)

### Cued Recall Task

- The comparison shows similar trends, with LLaMA outperforming humans in accuracy for specific prompts.

![Human Cued Recall Results](humans_cued_recall.png)  
![LLaMA Cued Recall Results](llama_cued_recall.png)

### Single Recognition Task

Preliminary results indicate that LLaMA’s performance aligns closely with humans, with some discrepancies due to tokenization errors.

![Human Single Recognition Results](humans_single_recognition.png)  
![LLaMA Single Recognition Results](llama_single_recognition.png)

---

## Future Work

1. **Introduce Distractors:**
   - Add distractor tasks between memory blocks to better mimic real-world scenarios.

2. **Refine Parsers:**
   - Enhance custom parsers to handle diverse output formats and improve result accuracy.

3. **Prompt Engineering:**
   - Optimize prompts for clarity and brevity to reduce extraneous outputs and improve response quality.

4. **Handle Token Splits:**
   - Address tokenization issues where certain words are split, impacting the evaluation.

5. **Expand Testing:**
   - Complete associative recognition tasks and analyze results for the remaining memory blocks.

---

## Conclusion

Preliminary results suggest that LLaMA performs comparably to, and in some cases better than, humans on memory tasks. While the model demonstrates strong recall capabilities, further refinement in decoding and parser design is required for more accurate comparisons. Future iterations of this work will incorporate distractors and more robust parsing techniques to enhance experimental reliability.

---

## Repository Contents

- **Code:** Implementation of task blocks, parsers, and result comparison scripts.
- **Data:** Processed outputs for both human and LLaMA experiments.
- **Images:** Visualizations of results and prompts.

---

## Acknowledgments

This project was conducted during the winter break as part of an effort to explore LLMs’ memory capabilities. Further developments will be shared in subsequent updates.

---

Best Regards,  
Abhay

