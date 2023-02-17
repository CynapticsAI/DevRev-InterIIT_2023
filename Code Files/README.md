# Code Files
## DevRev High Prep PS - Inter IIT Tech Meet 11.0
### IIT Indore (Team 53)

--- 

## **Instructions for finetuning Cross-Encoder model using *Finetuning CrossEncoder.ipynb* file**

Run the following sections in the below given order:
1. **Finetuning script for Cross-encoder**: To import required packages
2. **Data Extraction and Pre-Processing**: To download training data from gdown and pre-process it. Enter the split ratio for training, validation and test (By default it is [80, 10, 10])
3. **Model**: To load the crossencoder model and start fine-tuning it. Enter the hugging face cross encoder model card name. Specify the fine-tuning parameters- train_batch_size and num_epochs

---

## **Instructions for finetuning DELADE using *DeLADE Finetuning.ipynb* file:**

Run the following sections in the below given order:
1. **Variables**: Enter the split ratio for training, validation and test (By default it is [80, 10, 10])
2. **Imports**: To install and import required modules
3. **Preprocessing code for input data**: To pre-process the input data for training
4. **Training**: To initiate training. You may change the following parameters-
     * **save_steps**: save checkpoint after these many iterations
     * **per_device_train_batch_size**: training batch size
     * **learning_rate**: training learning rate
     * **q_max_len**: max length of the question
     * **p_max_len**: max length of the paragraph
     * **num_train_epochs**: number of epochs
     * **seed**: for reproducibility
     
---

## **Instructions for running *Inference Script.ipynb* file**

Run the following sections in the below given order:
1. **Variables**: Provide the path to the paragraph csv, theme interval csv and question_answer csv to the variables para_data_path, theme_path and ques_data_path respectively (By default the paths of **Stage-2** data are set)
The path for saving predictions is given by the variable *result_path* (by default the predictions will be saved at `/content/result.csv`)
2. **Imports**: To install and import required modules

Further, if the inference is to be done only on *DevRev* theme only, run the following sections in the below given order:

3. **Conversion to beir format (For Questions on DevRev Theme)**
4. **Delade generate embeddings**
5. **Delade load embeddings**
6. **Load QA base**
8. **Load Cross Encoder**
9. **Evaluation at k=3 (For Questions on DevRev Theme Only)**

If the inference is to be done on complete provided data, run the following sections in the below given order:

3. **Conversion to beir format section**
4. **Delade generate embeddings**
5. **Delade load embeddings**
6. **Load QA base**
7. **Load Cross Encoder**
8. **Evaluation at k=3**

---

## **Instructions for calculating performance metrics using *Evaluation Script.ipynb* file:**

Run the following sections in the below given order:
1. **File Generation and Preprocessing**: Provide the path to the paragraph csv and question_answer csv under the variables para_data and question_ans (by default the paths of **Stage-1** data are set). *cwd* is automatically set to your current working directory. `finalprocessed.csv` will be generated
2. **Evaluation Files(4 CSVs) Generation**: To generate the four CSVs for evaluation. These files would be saved in the *Final_data folder*
3. **Variables**: The path for saving predictions can be modified under the variable *result_path* (By default the predictions will be saved as `result.csv`)
4. **Imports**: To install and import required modules
5. **Conversion to beir format**: The input data will be converted to beir format as an initialisation step for DeLADE
6. **Delade generate embeddings**
7. **Delade load embeddings**
8. **Load QA base**
9. **Load Cross Encoder**

Further, if the evaluation is to be done without caching run-

10. **Evaluation at k=3**: The evaluation metrics will be printed as output to the last cell of this section

if the evaluation is to be done with caching run-

10. **Evaluation at k=3(with caching)**: The evaluation metrics and percent questions cached will be printed as output to the last cell of this section

---

## **Instructions for generating synthetic data using *Synthetic Data Generation.ipynb* file:**

Run the following sections in the below given order:
1. **Imports**: To install and import required modules
2. **File Generation**: To combine and pre-process paragraph data and question-answer data
3. **Model Imports**: To load Question Answering, Question Generation and Backtranslating Models
4. **Functions**: To define Helper functions
5 **Dataset Creation**: For Answerable Questions Data and Unanswerable Question Generation. The synthetic data will be saved as 'synthetic_data.csv'

---

## Instructions for QA Finetuning and Evaluation using *Finetune_QA.ipynb* file:

Run the following sections in the below given order:
1. **File Generation and Preprocessing**:
2. **Imports**: To install and import required modules
3. **Variables**: There are 3 modes:
- *ft+eval_same*: Finetune QA and evaluate on the same dataset
- *ft+eval_custom*: Finetune QA and evaluate on different dataset
- *eval_only*: No finetuning. Only evaluate QA
Define the train, validation and test split (By default it is [80, 20, 0])
Set *data_path* as path to the data csv upon which training/validation is required to be done
Set *data_path_eval* as path to the data csv to evaluate the checkpoint in save_path_eval
Checkpoints are saved at the path assigned to *save_path*

For *ft+eval_same* and *ft+eval_custom* modes, run all the section.
For *eval_only* mode, skip the Finetuning section

Download the Model checkpoints(Cross Encoder) from the [link](https://drive.google.com/drive/folders/1M0YSuwNUawHx51aeEaFXBpm56cklxOTS?usp=share_link)

Download the Model checkpoints(QA Model) from the [link](https://drive.google.com/drive/folders/1sSHApFT8JPFn9Wo5uHsYPaQxHLhf5F7M?usp=share_link)

The link to the Data Files can be found [here](https://drive.google.com/drive/folders/1nmBN7Dwmo125CvXp8Cav2SnwyaoBINxl?usp=share_link)

---

## **Instructions for Optimization and Evaluation of QA Model using _QA_Model_Optimization+Evaluation.ipynb_ file:**

Run the following sections in the below given order:
1. **Variables**: Change the model_name variable(Huggingface Model Card) and m variable(for saving)
2. **Imports**: To perfom the neccesary imports
3. **Loading Base**: To load the Question Answering Model and Tokenizer and Get its layers for optimization.
4. Run One of the Required Optimization Steps
* **Pruning**: Prunes the Model's Linear and Embedding Layers
* **Quantization**: Performs Quantization
* **Dynamic Quantization**: Performs Dynamic(Intel Version) Quantization
5. **Prediction**: Get the Predictions and Compute the F1 and QA score, By Default it gets prediction on 1000 Questions from Squadv2 on 327 themes.

---
