# SemEvalTask3Subtask2

## Team Name- MLModeler5

## Introduction-
Framing is a phenomenon largely studied and debated in the social sciences, where, for example, researchers explore how news media shape debate around policy issues by deciding what aspects of an issue to emphasize, and what to exclude. 

The task focuses on extending the analytical functionalities of media analysis solutions to: automated detection of framing dimensions and persuasion techniques, and visualization of related statistics, etc..

## Subtask 2 : Framing Detection
The second Subtask focuses on Frame Detection. It requires us to develop a multi-label classifier to determine the frames (one or more) used in each article out of a pool of 14 domain-independent framing dimensions which are - Economic, Capacity and Resources, Fairness and Equality, Legality, Constitutionally and Jurisprudence, Policy Prescription and Evaluation, Crime and Punishment, Security and Defence, Health and Safety, Quality of Life, Cultural Identity, Political and, External Regulation and Reputation.

We consider 14 Frames: 
1. Economic
2. Capacity and resources
3. Morality
4. Fairness and equality
5. Legality, constitutionality and jurisprudence
6. Policy prescription and evaluation 
7. Crime and punishment 
8. Security and defense 
9. Health and safety 
10. Quality of life
11. Cultural identity 
12. Public opinion 
13. Political
14. External regulation and reputation

Each language provided in training and validation data has a folder with the articles and the labels associated with each article. We have onlu used worked on the English language Subtak-2.  The testing data doesn’t include the labels.

## Data Preprocessing
In the context of textual data, data preprocessing allows us to remove noise from the data like punctuation marks, emojis, links, etc. We used various libraries like nltk, spacy and nlpaug to preprocess the provided data. Data preprocessing involved tokenizing the text following which we removed punctuations, white space, individual letters and stopwords. The text was converted to lowercase and then lemmatized. To handle both unbalanced labels and to increase the training data we used nlpaug to augment the data. Parameters used in nlpaug were - “model_path=bert-base-cased”, “action=substitute” and “aug_max=3”. 

The training and the validation articles were used from the English language data only because there were no imbalanced classes and thus did not need additional data to solve this issue. The headlines and articles were preprocessed separately using Python libraries like NLTK and Spacy. We have used MultiLabelBinarizer to convert the comma-separated labels into a numerical binary matrix indicating the presence of a class label. We have used NLP Augmentation using the nlpaug library to increase the size of the training dataset. 

Only one preprocessed data set was used which included numbers.

## Models Used-
1. RoBERTa- We initialize the weights of the RoBERTa layer using “roberta-base” pretrained weights, with the number of labels equal to three or fourteen as per the subtasks requirements. The text data needs to be encoded before it is fed into the RoBERTa architecture. We tokenize and pad sentences to the maximum length as a part of our encoding process, the maximum length being 512. If the length of the sentence exceeds 512, it is truncated. The encoded sentences are then processed to yield contextually rich pre-trained embeddings which are passed through the RoBERTa transformer (TFRobertaForSequenceClassification) followed by a Dropout, Flatten and two Dense Layers. 

2. AlBERT- We initialize the weights of the ALBERT layer using “albert-base-v2” pretrained weights, with the number of labels equal to three or fourteen as per the subtasks requirements. The text data needs to be encoded before it is fed into the ALBERT architecture. We tokenize and pad sentences to the maximum length as a part of our encoding process, the maximum length being 512. If the length of the sentence exceeds 512, it is truncated. The encoded sentences are then processed to yield contextually rich pre-trained embeddings which are passed through the ALBERT transformer (TFAlbertForSequenceClassification) followed by a Dropout, Flatten and two Dense Layers. 

We used a sigmoid activation function for the final dense layer. The sigmoid function is used in this multilabel classification problem because the probabilities produced by a sigmoid function are independent, and are not constrained to sum to 1.0. That’s because the sigmoid function looks at each raw output value separately and thus it’s the optimal activation function of a multilabel classification problem. 

## Results-

<img width="662" alt="Screenshot 2023-02-27 at 14 41 49" src="https://user-images.githubusercontent.com/67748049/221521784-cec183e0-6743-41b6-b9e6-4d0fcaeda517.png">



