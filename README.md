# Continuous Unlearning Dataset

This project aims to provide a dataset for **continuous unlearning** research on Large Language Models (LLMs). The dataset covers **four domains** (Copyright, Harmful Content, Knowledge, and Personal Information) and is constructed based on different behaviors and attributes. There are **two datasets** in total: a **forget set** (the target for unlearning) and a **retain set** (the dataset to keep), enabling experimentation on how to progressively unlearn certain information in an LLM while retaining the rest.

---

## 1. Purpose of the Dataset

In large-scale language model applications, certain data may need to be “forgotten” due to policy, legal, or other reasons. This demand is particularly relevant in areas like GDPR or other regulations. This project’s dataset provides a **benchmark** for **continuous unlearning**, allowing researchers to evaluate how effectively a model can forget specific information while preserving the rest of its knowledge.

---

## 2. Data Collection and Sources

- **Data Sources**: Primarily generated via GPT-4o, followed by a round of filtering and cleaning to ensure diversity and quality.  
- **Filtering Process**:  
  1. Classify and label the generated texts according to the four domains.  
  2. Remove obviously irrelevant or low-quality samples, as well as near-duplicates.  
  3. Ensure coverage of different text lengths and varied topics.

---

## 3. Composition of the Dataset

### 3.1 Four Domains

1. **Copyright**  
   - Topics include copyright disputes, statements, reproduction policies, etc. Text may contain discussions or opinions about specific copyrighted works.

2. **Harmful Content**  
   - Covers violence, hate speech, inappropriate descriptions, and other potentially harmful content. Texts are moderately screened for sensitive topics.

3. **Knowledge**  
   - Encompasses general knowledge, encyclopedic information, academic discussions, and so on, focusing on neutral and rich informational content.

4. **Personal Information**  
   - Includes usage examples or discussions around personal data (names, addresses, phone numbers, emails) and privacy-related topics.
![Dataset_example](Dataset_example.png)
### 3.2 Dataset Split

- **Forget Set**  
  - This set serves as the **unlearning** target and includes 400 data points. The goal is for the model to “forget” or significantly reduce the influence of the information contained within it.  
  - Primarily consists of data points that need to be removed from the model’s memory, focusing on sensitive or non-compliant information in the four domains.

- **Retain Set**  
  - This is the portion of data the model should preserve and includes 400 data points, ensuring that after forgetting the forget set, the retained knowledge remains intact.  
  - Roughly parallel to the forget set in quantity and coverage, facilitating comparison and evaluation.

---

## 4. Preliminary Data Analysis

Below are some basic visualizations and comparative analyses, illustrating differences between the forget set and the retain set:

1. **Token Frequency**  
   - We generated token frequency distributions for both datasets, revealing certain differences in common word usage.

2. **Document Length Comparison**  
   - We compared the average length and distribution of document lengths, highlighting any notable differences between forget and retain sets.
![Token Frequency Distribution](token_distribution_comparison.png)
3. **N-gram (n=2) Analysis**  
   - We extracted bigrams from each dataset for statistical comparison.  
   - Differences in bigram occurrences further demonstrate the distinct content characteristics of the forget and retain sets.
![Max_2_gram_similarity](Max_2_gram_similarity.png)
---

## 5. Usage

1. **Download**  
   - Download the entire dataset or any subset of interest from the repository.

2. **Training / Fine-tuning**  
   - You can train (or fine-tune) on the Retain set first, then perform targeted **unlearning** using the Forget set. Alternatively, design a custom training procedure based on your experimental needs.

3. **Evaluation**  
   - Evaluate the model on various metrics such as token frequency, text quality, and inference results after “forgetting.” Compare these results against the initial model or a version trained without unlearning.

---

## 6. Acknowledgments

Special thanks to:

- **OpenAI & GPT-4** for providing the foundational model to generate text.  
