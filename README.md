## README -- Eugene's modification to the Retrieval-Based Conversational Model in Tensorflow (Ubuntu Dialog Corpus)  
Here's how things work. I cloned the repo at https://github.com/dennybritz/chatbot-retrieval, which runs the LSTM model.
Primarily, I used git reset --hard e5e2f1ab85d557735ee6d00cd886abe8f320d8fa in order to go a version of the code that had only TensorFlow 0.9 Everything in this folder is Python 3 and TensorFlow 0.9.  
If you want to train on the Ubuntu corpus, just follow the instructions at https://github.com/augmenthq/DataMining/blob/master/EDA_Notebooks/Eugene/WildML_EC2_Setup_and_AMI.ipynb  

### Running script  
If you want to perform the analysis on our own data, follow the below steps:  

In the folder 'scripts', make a folder called 'data' and put in the output files from ubuntu-ranking-dataset-creator repo inside 'scripts/data': train.csv, valid.csv, and test.csv.  

python prepare_data.py # while inside 'scripts' folder, run this line, which will create some files that are optimized for running the neural net.  
mv data .. # move 'data' folder to be outside of 'scripts' folder
cd .. # move to the outer folder, so you should be in 'chatbot-retrieval' folder

python udc_train.py # this code will never stop running. The author of this code suggests that 20,000 steps is good enough

python udc_test.py --model_dir=... # for example: python udc_test.py --model_dir=runs/143241231

python udc_predict.py --model_dir=...

---



## Retrieval-Based Conversational Model in Tensorflow (Ubuntu Dialog Corpus)

#### [Please read the blog post for this code](http://www.wildml.com/2016/07/deep-learning-for-chatbots-2-retrieval-based-model-tensorflow)

#### Overview

The code here implements the Dual LSTM Encoder model from [The Ubuntu Dialogue Corpus: A Large Dataset for Research in Unstructured Multi-Turn Dialogue Systems](http://arxiv.org/abs/1506.08909).

#### Setup

This code uses Python 3 and Tensorflow >= 0.9. Clone the repository and install all required packages:

```
pip install -U pip
pip install numpy scikit-learn pandas jupyter
```

#### Get the Data


Download the train/dev/test data [here](https://drive.google.com/open?id=0B_bZck-ksdkpVEtVc1R6Y01HMWM) and extract the acrhive into `./data`.


#### Training

```
python udc_train.py
```


#### Evaluation

```
python udc_test.py --model_dir=...
```


#### Evaluation

```
python udc_predict.py --model_dir=...
```
