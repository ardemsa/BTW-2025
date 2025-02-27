# BTW-2025-LLMs-for-adversarial-Attacks-in-Text-to-SQL
Paper: **Utilising Large Language Models for Adversarial Attacks in Text-to-SQL: A Perpetrator and Victim Approach**

# A Appendix
This appendix provides additional visualisations and performance comparisons supporting the analysis conducted in the main chapters of the paper "Utilising Large Language Models for Adversarial Attacks in Text-to-SQL: A Perpetrator and Victim Approach".

## A.1 Distribution Analysis of Adversarial Attacks
This subsection presents insights in the distributions of attak metrics for different levels of adversarial perturbations.

![image](https://github.com/user-attachments/assets/639cd02f-a82e-45f3-a248-8b2fda195113)
Distributions of attack metrics: (left) Damerau-Levenshtein distance for character-level attacks, (center) semantic similarity for word-level attacks, and (right) semantic similarity for sentence-level attacks.


## A.2 Overview Text-to-Text and Text-to-SQL
We propose a two-step framework to evaluate the robustness of Text-to-SQL models against adversarial attacks. This involves (1) the generation of adversarial text queries using two Perpetrator LLMs and (2) the evaluation of the robustness of three Text-to-SQL models, which serve as Victim LLMs, against these queries.
![image](https://github.com/user-attachments/assets/40d80f06-f84c-4ddc-aacc-7a7da5d1445f)

The Text-to-Text pipeline (orange) is responsible for the generation of adversarial text queries, while the Text-to-SQL pipeline (green) focuses on the generation of SQL queries and evaluates how robust the Victim models are in response to those adversarial inputs. 

## A.3 Prompt Design 
### Prompt Design for character-, word-, and sentence-level attacks
![image](https://github.com/user-attachments/assets/07bba726-2b94-4a76-a810-d0a53a13cad6)

### Prompt Design: Character-level adversarial attacks
To simulate human typing errors, we established specific rules within the task description as seen below, that are based on the findings from paper _"How are spelling errors generated and corrected?:
A study of corrected and uncorrected spelling errors using keystroke logs"_
![image](https://github.com/user-attachments/assets/d0bd688f-ea22-4286-b74c-57a5307c006a)

### Prompt Design: SQL Formatting
For the evaluation of Text-to-SQL models, it is important that the SQL queries generated by these models are formatted consistently to ensure accurate evaluation against a official SQL Test Suite, since every Victim model is trained on different formats. However, in practice, we have identified several formatting issues in the SQL queries generated by these models that require pre-processing, in order to standardise them.
![image](https://github.com/user-attachments/assets/7714cb16-f7b8-4418-97c0-38f38be624a5)
The types of errors observed from intermediate results include unnecessary quotation marks, where some queries included extraneous quotation marks around identifiers and keywords, for example \"keyword\" instead of keyword. Added to that, queries often include line breaks, that made them harder to evaluate in a Test Suite that expects a single-line query format. Additional white spaces are not necessary for the logic of the query and lead to inconsistent formatting. These and other formatting issues are illustrated in the SQL Query Formatting Prompt above. To address these issues, we implement a pre-processing step using an LLM, the meta-llama/Meta-Llama-3-70B-Instruct


## A.4 Performance Comparisons of Victim Models

### Performance comparison of the llama-base model under Mixtral8x7B adversarial attacks at the character-, word-, and sentence-levels with and without context

<img width="624" alt="image" src="https://github.com/user-attachments/assets/16d3e3ad-33a8-45c7-9299-a6052edfe73c">

### Performance comparison of the llama-base model under Mixtral8x7B adversarial attacks at the character-, word-, and sentence-levels with and without context

<img width="625" alt="image" src="https://github.com/user-attachments/assets/ce57615f-43d0-4f7a-9fb2-1010ad109445">



### Performance comparison of the llama-spider model under Llama3 adversarial attacks at the character-, word-, and sentence-levels with and without context


<img width="526" alt="image" src="https://github.com/user-attachments/assets/dee8eaea-9b23-43cf-a115-9c047fb84ddc">

### Performance comparison of the llama-spider model under Mixtral8x7B adversarial attacks at the character-, word-, and sentence-levels with and without context

<img width="530" alt="image" src="https://github.com/user-attachments/assets/fc85fbb2-8b16-44b3-a9d5-eed60dd913a3">

### Performance comparison of the llama-spider-plus model under Llama3 adversarial attacks at the character-, word-, and sentence-levels with and without context

<img width="605" alt="image" src="https://github.com/user-attachments/assets/c66b765a-65b6-4b37-a50c-16899240e5e3">

### Performance comparison of the llama-spider-plus model under Mixtral8x7B adversarial attacks at the character-, word-, and sentence-levels with and without context

<img width="605" alt="image" src="https://github.com/user-attachments/assets/03b81c68-825a-4ba1-a317-dd24dd5cb449">
