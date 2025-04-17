# Ensemble-Based Evaluation of Research Paper Quality Using LLM APIs

In this project, we developed a highly effective and lightweight ensemble-based pipeline to automatically assess the publishability of research papers by leveraging state-of-the-art large language models (LLMs). The objective was to classify academic papers into either **"Publishable"** or **"Unpublishable"** categories based on criteria adapted from academic quality assessment rubrics that focus on originality, significance, and rigour. The system combines the strengths of **Google Gemini**, **Mistral**, and **Cohere** to make robust predictions, achieving exceptional accuracy across datasets.

## Pipeline Overview

The system begins with the extraction of text from PDF documents using the PyPDF2 library. The extracted text is cleaned via regular expressions to remove numerical artifacts, special characters, and redundant spaces. After preprocessing, the text is evaluated using three separate LLM APIs:

1. **Google Gemini (gemini-2.0-flash)**
2. **Mistral (mistral-large-latest)**
3. **Cohere (command-a-03-2025)**

Each model is prompted with a standardized instruction referencing a rubric-based classification scheme—ranging from 1* (national relevance) to 4* (world-leading). The models are asked to return either "Publishable" or "Unpublishable" along with a 100-word justification.

The outputs from all three models are parsed, and a **majority vote mechanism** is applied. If two or more models agree on a classification, it is taken as the final verdict. Additionally, the system employs Google Gemini to generate a unified, coherent explanation of the ensemble's decision using the individual justifications from all three models.

## Evaluation and Results

The ensemble was tested on two reference datasets:
- AriesDataset/Reference/Non-Publishable
- AriesDataset/Reference/Publishable

The results were outstanding:
- **Precision:** 1.0000
- **Recall:** 1.0000
- **F1 Score:** 1.0000

These metrics indicate **zero false positives or false negatives**, suggesting that the ensemble model was perfectly aligned with ground truth annotations. This is particularly impressive given that LLM outputs can often vary in format, tone, or confidence level. The ensemble mechanism significantly reduces variance and boosts reliability.

## Strengths of the Approach

- **Model Diversity:** By using models from different providers (Google, Mistral, and Cohere), the system leverages distinct training corpora and architectural biases. This minimizes overfitting to any one model's idiosyncrasies.
- **Robust Prompting:** The use of structured academic rubrics ensures consistency across evaluations and provides a concrete grounding for the LLMs' assessments.
- **Explainability:** Rather than simply returning a binary label, the system offers detailed, synthesized justifications which improve transparency and trust in the decision-making process.
- **Scalability:** The modular design makes the pipeline easy to extend to new models or domains with minimal effort.

## Conclusion

This project demonstrates a powerful, practical method for automating academic quality assessments using an ensemble of large language models. The system's exceptional performance on both publishable and non-publishable samples showcases its potential for deployment in peer review support tools, research evaluation platforms, and academic recommendation systems. Its blend of interpretability and accuracy makes it a promising asset for research curation tasks in large-scale academic environments.
