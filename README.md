# DeepLearning
Repo for final project in Deep Learning DTU. 

The following descriptions instruct on how to use the code in this repo.

**prediction_generate_qa.ipynb**: This code generates the predictions using these four different combinations of model and evaluation datasets:

1. deepset/roberta-base-squad2-covid model and Covid-19 QA dataset
2. deepset/roberta-base-squad2-covid model and Covid-19 news dataset
3. deepset/roberta-base-squad2 model and Covid-19 QA dataset
4. deepset/roberta-base-squad2 model and Covid-19 news dataset
                           
To generate all these different combinations you need to swtch the model variable and evaluation dataset creation. The current version uses the deepset/roberta-base-squad2 model and Covid-19 QA dataset. To change this comment out the ones in use and uncomment the ones are not in use. The evaluation dataset is altered under the caption "Evaluation dataset" and the model name is changed under the caption "Definition: MODEL, GPU, TOP_K, READER". 

These instructions along with the comments in the code should make this straight forward. Remember to alter the names of the files which you save to drive for different model+dataset combinations. The data used for this is all available under the same names as in the code in the data folder in this repo. These csv files holding the predictions are then used for the performance assessment in the "performance_metrics.ipynb" file. **If you don't have the time or focus to run the predictions they are available in the Evaluation folder in this repo.**

For these different model combinations we run predictions using 6 different pipelines:
1. COVID-19 document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
2. COVID-19 document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
3. WIKI Simple document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
4. WIKI Simple document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
5. Elastic search document store, TF-IDF retriever, which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.
6. Elastic search document store, BM25 retriever which retrievs the top 10 documents from the document store, FarmReader predicting 5 answers.

**evaluation_covidQA.ipynb**(SIGGA): This notebook can be found int the evaluation folder along with the predictions generated from prediction_generate.ipynb on different evaluation datasets. This code assesses the performnce of the different model combinations. The predictions generated from prediction_generate.ipynb code that are used for the performance metrics are available in the Evaluation folder in this repo.

This code evalates the different model combinations. To evaluate the models we decided to try few different performance metrics. That is RougeL score, Rouge1 score, keyword analysis and TFIDF.

**prediction_cleanup.ipynb**(Magnea): Cleanup of bad questions from evaluation datasets. In order to obtain a fair assessment of the models capabilities a human inspections was conducted. 

This code DADAADADA
                           
**demo_backend.ipynb**: This generates predictions for the demo we used for the presentation. It uses the WIKI API document store and the deepset/roberta-base-squad2-covid model since it is most likely to generate successful answers to common human COVID-19 questions. Link to demo: https://d42jgu7ysexg7zjh.anvil.app/OUGGLVAQTFBAT5NYIROIPGOZ . Run the notebook through and leave the last cell running while you want to ask questions in the demo.

                    
