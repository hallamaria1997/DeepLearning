# DeepLearning
Repo for final project in Deep Learning DTU. 

The following descriptions instruct on how to use the code in this repo.

**prediction_generate_qa.ipynb**: This code generates the predictions using these four different combinations of model and evaluation datasets:

1. deepset/roberta-base-squad2-covid model and Covid-19 QA dataset
2. deepset/roberta-base-squad2-covid model and Covid-19 news dataset
3. deepset/roberta-base-squad2 model and Covid-19 QA dataset
4. deepset/roberta-base-squad2 model and Covid-19 news dataset
                           
To generate all these different combinations you need to switch the model variable and evaluation dataset creation. The current version uses the deepset/roberta-base-squad2 model and Covid-19 QA dataset. To change this comment out the ones in use and uncomment the ones are not in use. The evaluation dataset is altered under the caption "Evaluation dataset" and the model name is changed under the caption "Definition: MODEL, GPU, TOP_K, READER". 

These instructions along with the comments in the code should make this straight forward. Remember to alter the names of the files which you save to drive for different model+dataset combinations. The data used for this is all available under the same names as in the code in this repo. These csv files holding the predictions are then used for the performance assessment in the "evaluation_covidQA.ipynb" file. **If you don't have the time or focus to run the predictions they are available in the Evaluation folder under Predictions in this repo in CSV files.**

The predictions files are the following:
1.df_res_covid_squad_covidQA_top5.csv -- result of deepset/roberta-base-squad2-covid model and Covid-19 QA dataset
2.df_res_covid_squad_top5.csv -- result of deepset/roberta-base-squad2-covid model and Covid-19 news dataset
3.df_res_squad_coviddata_top5.csv -- result of deepset/roberta-base-squad2 model and Covid-19 QA dataset
4.df_res_squad_top5.csv -- result of deepset/roberta-base-squad2 model and Covid-19 news dataset 

For these different model combinations we run predictions using 6 different pipelines:
1. COVID-19 document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
2. COVID-19 document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
3. WIKI Simple document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
4. WIKI Simple document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
5. Elastic search document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
6. Elastic search document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.

**evaluation_covidQA.ipynb**: This notebook can be found in the evaluation folder, this code assesses the performance of the different model combinations. To do that we decided to use few different performance metrics. That is RougeL score, Rouge1 score, keyword analysis and TFIDF Cosine-Similarity. These evaluations were made on the predictions in the csv files that can also be found in the evaluation folder.

The Covid News dataset contained some outdated answers as it was created in 2020 early on in the pandemic. Therefore some cleanup of the answers was done for the Covid News dataset where we updated the true answer to reflect the current situation in the world. An example of answers that was updated is the answer to the question "Is there a vaccine for Covid-19?", in the dataset the answer is no but we now know that there is infact a vaccine for Covid-19. It was important to update these answers as our system is fetching possible contexts from current documents.  The code for this is also in "evaluation_covidQA.ipynb". 
                           
**demo_backend.ipynb**: This generates predictions for the demo we used for the presentation. It uses the WIKI API document store and the deepset/roberta-base-squad2-covid model since it is most likely to generate successful answers to common human COVID-19 questions. Link to demo: https://d42jgu7ysexg7zjh.anvil.app/OUGGLVAQTFBAT5NYIROIPGOZ . Run the notebook through and leave the last cell running while you want to ask questions in the demo.

                    
