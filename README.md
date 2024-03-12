# eos2ta5-model-validation
This is Ersilia's week 2 task for Outreachy Summer 2024 contributors. This repository is a model validation for model eos2ta5

## Summary of the model
This model predicts hERG blockade based on ligands which is of utmost importance in drug discovery. The model is a classification model which 
returns the probability that the compound inhibits hERG which was set at IC50 < 10 uM.
The characteristics of the eos2ta5 model involve inputting a single compound for classification, which returns a single probability value (in float)
as output 

# WEEK 2: Task 1

## Testing of eos2ta5 model
The aim was to download, fetch,serve and run prediction so as to test the model on Ersilia to know if it's working. The process was done using Esilia on google collab. I used a random dataset with 9 records that has SMILES column to test model eos2ta5. The output can be found in the notebook folder titled as Testing
## Data Acquisition
The detailed explanation can be found under the readme.md section in the folder section


