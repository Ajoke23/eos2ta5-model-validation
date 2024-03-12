# eos2ta5-model-validation
This is Ersilia's week 2 task for Outreachy Summer 2024 contributors. This repository is a model validation for model eos2ta5

## Summary of the model
This model predicts hERG blockade based on ligands which is of utmost importance in drug discovery. The model is a classification model which 
returns the probability that the compound inhibits hERG which was set at IC50 < 10 uM.
The characteristics of the eos2ta5 model involve inputting a single compound for classification, which returns a single probability value (in float)
as output 

# WEEK 2: Task 1

## Testing of eos2ta5 model
The aim was to download, fetch,serve and run prediction so as to test the model on Ersilia to know if it's working. The process was done using Esilia on google collab. I used a random dataset with 9 records that has SMILES column to test model eos2ta5. The output can be found in the notebook folder. 
Link of the testing model notebook: [eos2ta5_model](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Notebook/Testing%20of%20model%20eos2ta5.ipynb)
- Summary: The output retuns the probability of the SMILES column which is a commpound. Hence, model eos2ta5 works perfectly well.

## Data Acquisition
The aim of this task is to select a list of 1000 molecules from public repositories and make sure they are represented as standard SMILES.
I acquired the dataset to be used from pubchem database. This dataset downloaded was a bit large (about 81.26 mb) with about 114,289 rows which contains SMILES columns. So I cleaned the dataset and selected random 1000 records which can be found in this path
1000molecules.csv- contains a list of 1000 moelcules from pubchem database.
- Summary: The file cleaned has 1000 molecules and 3 fields namely: canonicalsmiles, inchikeys and molecular weight.

## Predictions for 1000molecules file
