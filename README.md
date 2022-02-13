# Kaggle Jigsaw Rate Severity of Toxic Comments 7th place solution (Naoism's models)
- This is the repository of [naoism](https://www.kaggle.com/naoism) part in the 7th place solution of [Jigsaw Rate Severity of Toxic Comments](https://www.kaggle.com/c/jigsaw-toxic-severity-rating/).
- The discription of this solution is available [here](https://www.kaggle.com/c/jigsaw-toxic-severity-rating/discussion/306366).
- The inference notebook in the competition is available [here](https://www.kaggle.com/columbia2131/jigsaw-team-ensemble-006-fix/notebook).

# Hardware
I used 2 different machines.
1. Google Colaboratory(Colab) Pro
2. Kaggle notebook

# Environment(Google Colab Pro)
Please install the following packages for each code.
- exp1004.ipynb
```python
!pip -q install transformers==4.5.1
```

- exp4001.ipynb & exp4003.ipynb
```python
!pip -q install transformers==4.16.2
!pip -q install sentencepiece==0.1.96
```

# Data
- Jigsaw Rate Severity of Toxic Comments
  - Please download data to ./input from https://www.kaggle.com/c/jigsaw-toxic-severity-rating/data and unzip it.
- Toxic Comment Classification Challenge (https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/)
  - Please download data to ./input/jigsaw_1st from https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/data and unzip it.
  - Please download jigsaw-toxic-comment-classification-challenge/PseudoLabelDataset.csv to ./input/jigsaw_1st from https://www.kaggle.com/columbia2131/puseudolabelingjigsaw.
- context_toxicity (https://github.com/ipavlopoulos/context_toxicity)
  - Please download context_toxicity/PseudoLabelDataset_CCC.csv to ./input from https://www.kaggle.com/columbia2131/puseudolabelingjigsaw.


# Model download
I used 2 pretrained models that are publicly available in [Hugging Face](https://huggingface.co/). 
- roberta-large: https://huggingface.co/roberta-large
- multilingual-toxic-xlm-roberta: https://huggingface.co/unitary/multilingual-toxic-xlm-roberta


# Preprocess
We built models based on "validation_data.csv" provided in this competition, and then inferred the text of "Toxic Comment Classification Challenge" and "context_toxicity", and used the results as training data to build a new model. (Pseudo labeling)

- Models built based on "validation_data.csv": https://www.kaggle.com/columbia2131/jigsaw-exp019-toxic-xlm-roberta
- "context_toxicity" dataset created by above models: https://www.kaggle.com/naoism/jigsaw2021-pseudo-context-toxicity

All pseudo labeling dataset: https://www.kaggle.com/columbia2131/puseudolabelingjigsaw

# Train
- All model(exp1004.ipynb, exp4001.ipynb, exp4003.ipynb) were trained on Google Colab Pro. 
- When you run expXXXX.ipynb, . /output/expXXXX and . /output/expXXXX_seed1 and . /output/expXXXX_seed2 will be created. Each directory will contain the model, the inference results (more_df.csv, less_df.csv) for each column (more_toxic, less_toxic) of validation_data.csv, and the train.log file.
- The only difference between expXXXX, expXXXX_seed1 and expXXXX_seed2 is that they are run with different random seed.