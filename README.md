# kp-anonymity

## Datasets
- [Sales transactions over a year - UCI](https://archive.ics.uci.edu/ml/datasets/Sales_Transactions_Dataset_Weekly#)
- [News social feedback over eight months - UCI](https://archive.ics.uci.edu/ml/datasets/News+Popularity+in+Multiple+Social+Media+Platforms)

## Requirements
```
python3 -m pip install -r requirements.txt
```
- numpy==1.18.1
- pandas==1.0.3
- loguru==0.5.1
- saxpy==1.0.1.dev167 (https://github.com/seninp/saxpy)
- pathlib==1.0.1
- matplotlib==3.2.2

## How to launch the tool 
```
[*] usage: python3 kp-anonymity.py k_value p_value paa_value dataset_path dataset_output_path
```
### Explain Parameters
- k_value (value of k-anonymity)
- p_value (value of p-anonymity, pattern)
- paa_value (To reduce the dimensionality of patterns) [more on this](https://vigne.sh/posts/piecewise-aggregate-approx/)

## Example
```
python3 kp-anonymity.py 10 2 5 Dataset/Input/Sales_Transaction_Dataset_Weekly_Final.csv Dataset/Anonymized/output.csv
```
## Time Utility
To compare time scalability of **naive** approach vs **kapra** approach, launch the *test* utility:
```
cd Utility
./test.sh
```
## Repository Structure
- **Dataset**: it contains the datasets used in my tests
    - **Input**: input datasets for the tool
    - **Anonymized**: store the output of the tool
- **Paper**: it contains the two paper studied for this project, [Utility-Based Anonymization for Privacy Preservation with Less Information Loss](https://www.cs.sfu.ca/~jpei/publications/localrecoding-sigkddExp06.pdf) and [Supporting Pattern-Preserving Anonymization for Time-Series Data](https://ieeexplore.ieee.org/document/6095556).
- **Utility**: it contains scripts for verify time efficiency and clean output
- **kp-anonymity.py**: main tool, implement naive and kapra algorithm
- **node.py**: manage the create-tree phase of both algorithms
- **dataset_anonymized.py**: manage the printing and anonymized value replacing of the output dataset
- **create_dataset.py**: script for generating subdataset of the News Social Dataset, used for measure time scalability of both algorithms  
- **requirements.txt**: list of necessary packages
