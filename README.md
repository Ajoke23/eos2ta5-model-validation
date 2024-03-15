# eos2ta5-model-validation
This is Ersilia's week 2 task for Outreachy Summer 2024 contributors. This repository is a model validation for model eos2ta5

## Model Abstract
hERG channel blockage has been a problem in small molecules during drug development and the side effect of this blockade is the increased risk of cardiotoxicity.
This model tries to solve the problem of hERG blockage in small molecules by classifying druglike molecules as hERG blockers and hERG non-blockers. A druglike molecule is considered 
hERG blocker if the probability is >=0.5 and a non-blocker if the probability is <0.5.

## Model Characteristics
- EOS model ID: eos2ta5
- Slug: cardiotoxnet-herg
- Task: Classification
- Output: Probability
- Output Type: Float
- Interpretation: Probability that the compound inhibits hERG (IC50 < 10 uM)
 
## Summary of the model
This model predicts hERG blockade based on ligands which is of utmost importance in drug discovery. The model is a classification model which returns the probability that the compound 
inhibits hERG which was set at IC50 < 10 uM by the authors. The characteristics of the eos2ta5 model involve inputting a single compound for classification, which returns a single 
probability value (in float) as output.

## Installation
Tested on Ubuntu and Python version >=3.7 and <=3.11. 

### Using Ubuntu
- Install Ersilia's model. The link can be found [here](https://ersilia.gitbook.io/ersilia-book/ersilia-model-hub/installation)
-  Fetch the model
```
ersilia -v fetch eos2at5
```
- Serve the model
```
ersilia -v serve eos2at5
```
- Run Predictions using a dataset that has SMILES as a column
 ```
ersilia -v api run -i input.csv -o output.csv
```
### Using Google Collab
The process can be found [here](https://github.com/ersilia-os/ersilia/blob/master/notebooks/ersilia-on-colab.ipynb)

# WEEK 2: Task 1

## Testing of eos2ta5 model
The aim was to download, fetch, serve, and run prediction to test the model on Ersilia to know if it's working. The process was done using Esilia on Google Collab. I used a random dataset with 9 records that have SMILES columns to test model eos2ta5. The output can be found in the notebook folder. 
Link of the testing model notebook: [eos2ta5_model](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Notebook/Testing%20of%20model%20eos2ta5.ipynb)
- Summary: The output returns the following columns: keys, input, and probability. Hence, model eos2ta5 works perfectly well.

## Data Acquisition
This task aims to select a list of 1000 molecules from public repositories and ensure they are represented as standard SMILES.
I acquired the dataset from the [PubChem database](https://pubchem.ncbi.nlm.nih.gov/classification/#hid=72). This dataset downloaded contains about 2265 rows with numerous fields. The SMILES column is titled "canonicalsmiles" in the dataset downloaded from PubChem. Since the SMILES was in canonical format, I decided to convert it to standardized smiles, which will be useful in running prediction
So I cleaned the dataset, filtered out unnecessary columns, and selected random 1000 records which can be found in this path
- [Data Cleaning](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Notebook/Data%20Cleaning.ipynb) - code containing the cleaning process in Python
- [1000molecules.csv](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Input/1000molecules.csv) - contains a list of random 1000 molecules from the dataset downloaded from the PubChem database.
- Summary: The file cleaned has 1000 molecules and 3 fields namely: canonical smiles, inchikeys, and molecular weight.

## Predictions for 1000molecules file
The aim is to carry out a prediction on the 1000 molecules obtained from a public repository and evaluate the result using a scatter plot.
- [1000molecules_prediction.csv](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Output/1000molecules_prediction.csv) - output of the predicted value using the 1000molecule data.

## Result
To evaluate the result of the model, I set a threshold probability values of 0.5. So i classified my probability values as hERG blockers and hERG non blocker. The result is evualated in a scatterplot and barchat.
All the plot can be found in this [link](https://github.com/Ajoke23/eos2ta5-model-validation/tree/main/figures)

# WEEK 2: TASK 2
## Model Reproducibility
The aim is to reproduce the result obtained from the [Publication paper](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-021-00541-z)

## Data Acquisition
The data used to test the reproducibility of CardioTox was downloaded from the github page
- [external_test_pos.csv](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Model%20Reproducibility/external_test_set_pos.csv) - is the downloaded data gotten from the publication [GitHub Page](https://github.com/Abdulk084/CardioTox/blob/master/data/external_test_set_pos.csv)
- Summary: The file contains 44 records and two columns namely: ACTIVITY & smiles

## Prediction for the Dataset downloaded from the publication
The aim was to run a prediction on the ersilia model eos2ta5. I took the following steps to achieve the reproducibility output data.
1. Fetch the model eos2ta5 from docker using:
```
docker pull ersiliaos/eos2ta5:latest
```
2. Serve model eos2ta5 using:
```
ersilia -v serve eos2ta5
```
3. Ran prediction
```
ersilia -v api run -i external_test_pos.csv -o reproducibility_prediction_output.csv
```
- [reproducibility_prediction_output](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Model%20Reproducibility/reproducibility_prediction_output.csv) - output data gotten after making the prediction.
-  Summary: This returned output data contains 44 records and three columns namely: key, input, and probability.
  
## Reproducibility Process
The tool used is Jupyter Notebook and the code can be found [here](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Notebook/Model%20Reproducibility.ipynb)

## Result & Conclusion
I used the same evaluation criteria used in the publication paper to compare the results  and to know if the model is reproducible.
From this result:
![Result](https://github.com/Ajoke23/eos2ta5-model-validation/assets/71567200/51615d48-3635-45a6-9eca-f4350f378599)

Publication Result:
![cardiotox](https://github.com/Ajoke23/eos2ta5-model-validation/assets/71567200/6cd79857-e06e-4b63-b1c6-89be3ec59c84)

Using the same evaluation criteria to compare the two result, it is showm that they both have similar result. Hence, the model is reproducible.

# References
- [Publication](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-021-00541-z)
- [Source Code](https://github.com/Abdulk084/CardioTox)
