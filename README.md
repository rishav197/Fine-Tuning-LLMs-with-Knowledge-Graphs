# Fine-Tuning-LLMs-with-Knowledge-Graphs

 ## Domain Description:
 The domain selected for the task is Biomedical domain, specifically considering
 the Human Disease Ontology of which numerous variational knowledge graphs are
 available at URL.

 ## Defining the Task and Knowledge Graph:
 a) The NLP task our fine-tuned LLM will consider is the classification of a textual
 description of any human disease into its scientific disease name.
 b) The HDO (Human Disease Ontology) knowledge graph has a single-hierarchy
 nature and contains information for any disease, such as its definition (the
 description), the synonyms (other frequently used names), and some unique
 scientific codes given to them, and the data is available in formats such as .owl,
 .xml, .json etc.

 ## Preprocessing the Knowledge Graph Data
 a) Data Formation: The information such as disease definition, synonyms and
 scientific codes are combined together to form an attribute “text_sequence” and
 take the disease names to form the attribute “label”, and a dataframe is created.
 b) Data Augmentation: Since the data is constructed from a knowledge graph, it
 contains no duplicates and hence all the 14,081 entries are unique. So the data
 is augmented, where new samples (~5000) are introduced to allow for a diverse
 set of samples, and the data is shuffled to account for minimal losses during
 training of the LLM.
 c) Data Cleaning: The attribute “text_sequence” is cleaned with the removal of
 stopwords, punctuations along with the lowercasing of the text.
The final prepared data is represented as follows:
![prepared_data](https://github.com/rishav197/Fine-Tuning-LLMs-with-Knowledge-Graphs/blob/main/images/img1.jpg)


 ## Model Selection and Training Preparations
 a) Initializing the BERT (base-uncased) tokenizer and model, pretrained on a
 large corpus of English Data.
 b) The “text_sequences” and “label” attributes are tokenized and appropriate
 padding with attention masks are applied to ensure consistency in encodings.
 c) The dataset is split into a 3:1 ratio of Train-Val, and appropriate data loaders
 are initialized for the fine-tuning process.
 d) The parameters selected for the training are:
 ○ Num_epochs = 10
 ○ Learning Rate = 2e- 5
 ○ Batch Size = 16
 ○ Optimizer = AdamW

 ## Fine-Tuning and Results
 The model is trained utilizing the GPU and the training losses seem to decrease
 while the validation losses seem to increase for some epochs and then decrease
 again (after epoch 8) as can be seen below, which indicates that the training
 needs to be more efficient, which could be either done with the selection of best
 parameters through hyperparameter tuning, or with the appropriate modifications
 to the data, since it contains very high number (more than 80%) of unique labels.
