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
This model predicts hERG blockade based on ligands which is of utmost importance in drug discovery. The model is a classification model which 
returns the probability that the compound inhibits hERG which was set at IC50 < 10 uM by the authors.The characteristics of the eos2ta5 model 
involve inputting a single compound for classification, which returns a single probability value (in float) as output 

## Installation
Tested on Ubuntu and Python version >=3.7 and <=3.11. 

### Using Ubuntu
- Install Ersilia's model. Link can be found [here](https://ersilia.gitbook.io/ersilia-book/ersilia-model-hub/installation)
-  Fetch the model
```
ersilia -v fetch eos2at5
```
- Serve the model
```
ersilia -v serve eos2at5
```
- Run Predictions using dataset that has SMILES as column
 ```
ersilia -v api run -i input.csv -o output.csv
```
### Using Google Collab
- Install Ersilia
```
#Installing Ersilia on Colab
%%capture
%env MINICONDA_INSTALLER_SCRIPT=Miniconda3-py37_4.12.0-Linux-x86_64.sh
%env MINICONDA_PREFIX=/usr/local
%env PYTHONPATH= "$PYTHONPATH:/usr/local/lib/python3.7/site-packages"
%env PIP_ROOT_USER_ACTION=ignore

!wget https://repo.anaconda.com/miniconda/$MINICONDA_INSTALLER_SCRIPT
!chmod +x $MINICONDA_INSTALLER_SCRIPT
!./$MINICONDA_INSTALLER_SCRIPT -b -f -p $MINICONDA_PREFIX

!python -m pip install git+https://github.com/ersilia-os/ersilia.git
!python -m pip install requests --upgrade
import sys

_ = sys.path.append("/usr/local/lib/python3.7/site-packages")
```

# WEEK 2: Task 1

## Testing of eos2ta5 model
The aim was to download, fetch, serve, and run prediction to test the model on Ersilia to know if it's working. The process was done using Esilia on Google Collab. I used a random dataset with 9 records that have SMILES columns to test model eos2ta5. The output can be found in the notebook folder. 
Link of the testing model notebook: [eos2ta5_model](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Notebook/Testing%20of%20model%20eos2ta5.ipynb)
- Summary: The output returns the following columns: keys, input, and probability. Hence, model eos2ta5 works perfectly well.

## Data Acquisition
This task aims to select a list of 1000 molecules from public repositories and make sure they are represented as standard SMILES.
I acquired the dataset to be used from the [PubChem database](https://pubchem.ncbi.nlm.nih.gov/classification/#hid=72). This dataset downloaded contains about 2265 rows with numerous fields. The SMILES column is titled "canonicalsmiles" in the dataset downloaded from PubChem. Since the SMILES was in canonical format, I decided to convert it to standardized smiles will be useful in running prediction
So I cleaned the dataset, filtered out unnecessary columns, and selected random 1000 records which can be found in this path
- [1000molecules.csv](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Input/1000molecules.csv) - contains a list of random 1000 molecules from the dataset downloaded from the PubChem database.
- Summary: The file cleaned has 1000 molecules and 3 fields namely: canonical smiles, inchikeys, and molecular weight.

## Predictions for 1000molecules file
The aim is to carry out a prediction on the 1000 molecules obtained from a public repository and evaluate the result using a scatter plot.
[1000molecules_prediction.csv](https://github.com/Ajoke23/eos2ta5-model-validation/blob/main/Data/Output/1000molecules_prediction.csv) - output of the predicted value using the 1000molecule data.


# References
[Publication](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-021-00541-z)
[Source Code](https://github.com/Abdulk084/CardioTox)
