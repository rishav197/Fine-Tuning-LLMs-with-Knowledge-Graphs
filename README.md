# Fine-Tuning-LLMs-with-Knowledge-Graphs

 ## Domain Description:
 The domain selected for the task is Biomedical domain, specifically considering
 the Human Disease Ontology of which numerous variational knowledge graphs are
 available at URL.

 ## Defining the Task and Knowledge Graph:
 a) The NLP task our fine-tuned LLM will consider is the classification of a textual description of any human disease into its scientific disease name.<br>
 b) The HDO (Human Disease Ontology) knowledge graph has a single-hierarchy nature and contains information for any disease, such as its definition (the description), the synonyms (other frequently used names), and some unique scientific codes given to them, and the data is available in formats such as .owl,
 .xml, .json etc.

 ## Preprocessing the Knowledge Graph Data
 a) Data Formation: The information such as disease definition, synonyms and scientific codes are combined together to form an attribute “text_sequence” and take the disease names to form the attribute “label”, and a dataframe is created.<br>
 b) Data Augmentation: Since the data is constructed from a knowledge graph, it contains no duplicates and hence all the 14,081 entries are unique. So the data is augmented, where new samples (~5000) are introduced to allow for a diverse set of samples, and the data is shuffled to account for minimal losses during training of the LLM.<br>
 c) Data Cleaning: The attribute “text_sequence” is cleaned with the removal of stopwords, punctuations along with the lowercasing of the text.<br>
The final prepared data is represented as follows:<br>
![prepared_data](https://github.com/rishav197/Fine-Tuning-LLMs-with-Knowledge-Graphs/blob/main/images/img1.jpg)


 ## Model Selection and Training Preparations
 a) Initializing two models BioBERT and BERT (base-uncased) tokenizer and model, pretrained on a large corpus of English Data.<br>
 b) The “text_sequences” and “label” attributes are tokenized and appropriate padding with attention masks are applied to ensure consistency in encodings.<br>
 c) The dataset is split into a 85:15 ratio of Train-Test, and appropriate data loaders are initialized for the fine-tuning process.<br>
 d) The parameters selected for the training are:<br>
 ○ Num_epochs = 10<br>
 ○ Learning Rate = 2e- 5<br>
 ○ Batch Size = 16<br>
 ○ Optimizer = AdamW



## Fine-Tuning Results
 The models are trained utilizing the GPU and the training losses seem to
 decrease for both the models.
 The final model testing results are as follows:<br>
![Model_results](https://github.com/rishav197/Fine-Tuning-LLMs-with-Knowledge-Graphs/blob/main/images/img2.jpg)


## Conclusion:
 While the accuracy for both models are comparable and possess very similar
 results, BioBERT still outperforms BERT, the reason being that it was designed for the
 biomedical domain purposes, and pre trained on tasks specific to the biological
 terminology, rather than more general text based, which is the base for the BERT
 model. In both the cases, the fine-tuning of LLMs on knowledge graphs proved to be
 beneficial.

