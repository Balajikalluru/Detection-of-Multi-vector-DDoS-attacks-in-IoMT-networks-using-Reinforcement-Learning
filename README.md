# Detection of Multi-vector DDoS Attacks in IoMT Networks using Reinforcement Learning

This project focuses on detecting multi-vector DDoS attacks using reinforcement learning (RL) for feature selection. Unlike traditional detection systems that rely on fixed rule sets or static thresholds, this approach adaptively selects the most relevant subset of features by training an RL agent to maximize classification accuracy. The pipeline includes complete data cleaning, preprocessing, and normalization across multiple DDoS traffic types (ICMP, TCP, SYN, UDP) and benign flows.

## Approach:

- Merged and labeled real-world network traffic data from five distinct sources, covering both benign and multiple DDoS vectors.

- Applied extensive preprocessing—renaming, numeric conversion, null imputation, duplicate removal, scaling—to prepare high-quality input for modeling.

- Partitioned the dataset into three parts to simulate distributed learning.

- Trained a separate Q-learning agent on each partition:
  - Each agent iteratively selects feature subsets.
  - Trains a RandomForest classifier per subset.
  - Receives rewards based on model accuracy.
  - Updates Q-values to learn optimal feature combinations.

- Combined the knowledge (Q-values) from the three agents into a unified model using reinforcement learning techniques.

- Sent the combined model back to each agent, allowing them to further refine their learning and improve performance over successive iterations.

- After reaching a performance threshold, extracted the best-performing feature subset (~23 features) for training the final classification model.

- Evaluated detection performance using standard metrics (accuracy, precision, recall, F1-score), focusing on multiclass detection of attack types.

#### NOTE: 
- The datasets used in this project are too large to upload here. However, you can find the CIC IOMT datasets by searching on Google. These datasets can be downloaded and utilized for your own projects
